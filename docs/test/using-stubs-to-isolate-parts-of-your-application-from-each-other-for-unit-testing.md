---
title: Verwenden von Stubs, um Teile der App für Tests zu isolieren
description: Informationen über einen Stub, einen kleinen Codeabschnitt, der während des Tests an die Stelle einer anderen Komponente tritt. Durch die Verwendung eines Stubs werden konsistente Ergebnisse zurückgegeben.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
dev_langs:
- CSharp
- VB
ms.openlocfilehash: eeb7b981dcaec97d52c24ea40476f0bec84e608e
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/24/2020
ms.locfileid: "95598561"
---
# <a name="use-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing"></a>Verwenden von Stubs, um für Komponententests Teile der Anwendung voneinander zu trennen

*Stub-Typen* gehören zu einer von zwei Technologien des Microsoft Fakes-Frameworks. Sie können damit eine Komponente, die Sie testen, einfacher von den anderen aufgerufenen Komponenten isolieren. Ein Stub ist ein kleiner Codeabschnitt, der während des Tests an die Stelle einer anderen Komponente tritt. Der Vorteil eines Stubs liegt darin, dass dieser konsistente Ergebnisse zurückgibt und so das Schreiben des Tests erleichtert. Außerdem können Sie Tests ausführen, auch wenn die anderen Komponenten noch nicht funktionieren.

Eine Übersicht und ein Schnellstartleitfaden für Fakes finden Sie unter [Isolieren von getestetem Code mithilfe von Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md).

Zur Verwendung von Stubs muss die Komponente so geschrieben werden, dass sie nur Schnittstellen und keine Klassen zum Verweis auf andere Teile der Anwendung verwendet. Dies ist eine bewährte Designpraktik, da die Wahrscheinlichkeit gering ist, dass Änderungen in einem Teil des Codes auch Änderungen in einem anderen Teil erfordern. Zu Testzwecken können Sie eine reale Komponente durch einen Stub ersetzen.

Im Diagramm soll die StockAnalyzer-Komponente getestet werden. Sie verwendet normalerweise eine andere Komponente, den RealStockFeed. RealStockFeed gibt jedoch bei jedem Aufruf seiner Methoden unterschiedliche Ergebnisse zurück. Daher ist es schwierig, den StockAnalyzer zu testen.  Ersetzen Sie ihn während des Tests durch eine andere Klasse, dem StubStockFeed.

![Real- und Stub-Klassen beziehen sich auf die gleiche Schnittstelle](../test/media/fakesinterfaces.png)

Da Stubs darauf beruhen, dass Sie Ihren Code auf diese Weise strukturieren, verwenden Sie in der Regel Stubs, um einen Teil der Anwendung von einem anderen zu isolieren. Zum Isolieren dieses Teils von anderen Assemblys wie *System.dll*, die Sie nicht steuern können, werden normalerweise Shims verwendet. Weitere Informationen finden Sie unter [Verwenden von Shims, um für Komponententests die Anwendung von anderen Assemblys zu trennen](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md).

## <a name="how-to-use-stubs"></a>Verwendung von Stubs

### <a name="design-for-dependency-injection"></a>Entwurf für Zielabhängigkeit

Um Stubs zu verwenden, muss die Anwendung so entwickelt werden, dass die verschiedenen Komponenten nicht voneinander, sondern nur von Schnittstellendefinitionen abhängen. Anstatt zur Kompilierzeit verknüpft zu werden, erfolgt die Verbindung von Komponenten zur Laufzeit. Dieses Muster hilft bei der Erstellung von Software, die stabil und einfach zu aktualisieren ist, da Änderungen eher nicht über Komponentenbegrenzungen hinweg weitergegeben werden. Es empfiehlt sich, dieses Muster anzuwenden, auch wenn Sie keine Stubs verwenden. Wenn Sie neuen Code schreiben, können Sie problemlos dem Muster zur [Abhängigkeitseinfügung](https://en.wikipedia.org/wiki/Dependency_injection) folgen. Wenn Sie Tests für vorhandene Software schreiben, müssen Sie diese möglicherweise umgestalten. Sollte das nicht möglich sein, können Sie stattdessen Shims verwenden.

Beginnen wir diese Erläuterung mit einem anschaulichen Beispiel – dem Beispiel im Diagramm. Die StockAnalyzer-Klasse liest die Aktienkurse aus und generiert einige interessante Ergebnisse. Sie verfügt über einige öffentliche Methoden, die getestet werden sollen. Um dieses Beispiel möglichst einfach zu halten, sehen wir uns hier nur eine der Methoden an – und zwar eine sehr einfache – die zur Meldung des aktuellen Preises einer bestimmten Aktie. Es soll ein Komponententest dieser Methode geschrieben werden. Im Folgenden sehen Sie einen ersten Entwurf des Tests:

```csharp
[TestMethod]
public void TestMethod1()
{
    // Arrange:
    var analyzer = new StockAnalyzer();
    // Act:
    var result = analyzer.GetContosoPrice();
    // Assert:
    Assert.AreEqual(123, result); // Why 123?
}
```

```vb
<TestMethod()> Public Sub TestMethod1()
    ' Arrange:
    Dim analyzer = New StockAnalyzer()
    ' Act:
    Dim result = analyzer.GetContosoPrice()
    ' Assert:
    Assert.AreEqual(123, result) ' Why 123?
End Sub
```

Ein Problem mit diesem Test wird sofort offensichtlich: Aktienkurse variieren, und daher schlägt die Assertion normalerweise fehl.

Ein weiteres Problem könnte darin bestehen, dass die vom StockAnalyzer verwendete StockFeed-Komponente noch in Entwicklung ist. Dies ist der erste Entwurf des Codes der zu testenden Methode:

```csharp
public int GetContosoPrice()
{
    var stockFeed = new StockFeed(); // NOT RECOMMENDED
    return stockFeed.GetSharePrice("COOO");
}
```

```vb
Public Function GetContosoPrice()
    Dim stockFeed = New StockFeed() ' NOT RECOMMENDED
    Return stockFeed.GetSharePrice("COOO")
End Function
```

Bislang kompiliert diese Methode möglicherweise nicht oder löst eventuell eine Ausnahme aus, da die StockFeed-Klasse noch nicht fertig ausgearbeitet ist. Beide Probleme werden durch die Schnittstelleneinfügung behandelt. Die Schnittstelleneinfügung wendet folgende Regel an:

Der Code der Komponenten Ihrer Anwendung sollte niemals explizit auf eine Klasse in einer anderen Komponente verweisen, weder in einer Deklaration noch in einer `new`-Anweisung. Stattdessen sollten Variablen und Parameter mit Schnittstellen deklariert werden. Komponenteninstanzen sollten nur vom Container der Komponente erstellt werden.

- „Komponente“ bedeutet eine Klasse oder eine Gruppe von Klassen, die Sie gemeinsam entwickeln und aktualisieren. Eine Komponente ist in der Regel der Code in einem Visual Studio-Projekt. Es ist nicht so wichtig, Klassen innerhalb einer Komponente zu entkoppeln, da sie gleichzeitig aktualisiert werden.

- Es ist auch nicht so wichtig, die Komponenten von den Klassen einer relativ stabilen Plattform wie *System.dll* zu entkoppeln. Schnittstellen für alle diese Klassen zu schreiben würde den Code überlasten.

Sie können den StockAnalyzer-Code von StockFeed durch Verwendung einer Schnittstelle wie folgt entkoppeln:

```csharp
public interface IStockFeed
{
    int GetSharePrice(string company);
}

public class StockAnalyzer
{
    private IStockFeed stockFeed;
    public StockAnalyzer(IStockFeed feed)
    {
        stockFeed = feed;
    }
    public int GetContosoPrice()
    {
        return stockFeed.GetSharePrice("COOO");
    }
}
```

```vb
Public Interface IStockFeed
    Function GetSharePrice(company As String) As Integer
End Interface

Public Class StockAnalyzer
    ' StockAnalyzer can be connected to any IStockFeed:
    Private stockFeed As IStockFeed
    Public Sub New(feed As IStockFeed)
        stockFeed = feed
    End Sub
    Public Function GetContosoPrice()
        Return stockFeed.GetSharePrice("COOO")
    End Function
End Class
```

In diesem Beispiel wird StockAnalyzer eine Implementierung von einem IStockFeed bei dessen Erstellung übergeben. In der fertigen Anwendung würde der Initialisierungscode die Verbindung ausführen:

```csharp
analyzer = new StockAnalyzer(new StockFeed());
```

Es gibt flexiblere Methoden für die Ausführung dieser Verbindung. Beispielsweise könnte der StockAnalyzer ein Factoryobjekt akzeptieren, das verschiedene Implementierungen von IStockFeed unter unterschiedlichen Bedingungen instanziieren kann.

### <a name="generate-stubs"></a>Stubs generieren

Sie haben die Klasse, die Sie testen möchten, von den anderen verwendeten Komponenten entkoppelt. Die Entkopplung macht Ihre Anwendung nicht nur robuster und flexibler, sie ermöglicht auch die Herstellung einer Verbindung für Testzwecke zwischen den zu testenden Komponenten und den Stubimplementierungen der Schnittstellen.

Sie können die Stubs einfach wie gewohnt als Klassen schreiben. Microsoft Fakes bietet eine dynamischere Methode zur Erstellung des für jeden Test am besten geeigneten Stubs.

Um Stubs zu verwenden, müssen Sie zuerst Stub-Typen aus den Schnittstellendefinitionen generieren.

#### <a name="add-a-fakes-assembly"></a>Hinzufügen eines Fakes-Assemblys

1. Im **Projektmappen-Explorer**: 
    - Erweitern Sie für ein älteres .NET Framework-Projekt (kein SDK-Format) den Knoten **Verweise** Ihres Projekts für den Komponententest.
    ::: moniker range=">=vs-2019"
    - Erweitern Sie bei einem Projekt im SDK-Format für .NET Framework oder .NET Core unter **Assemblys**, **Projekte** oder **Pakete** den Knoten **Abhängigkeiten**, um die gewünschte Assembly zu finden, die Sie als Fakes-Assembly verwenden möchten.
    ::: moniker-end
    - Wenn Sie in Visual Basic arbeiten, müssen Sie auf der Symbolleiste im **Projektmappen-Explorer** auf **Alle Dateien anzeigen** klicken, um den Knoten **Verweise** anzuzeigen.

2. Wählen Sie die Assembly aus, in der die Klassendefinitionen enthalten sind, für die Sie Shims erstellen möchten. Wenn Sie z.B. einen Shim für **DateTime** erstellen möchten, klicken Sie auf **System.dll**.

3. Wählen Sie im Kontextmenü **Fakes-Assembly hinzufügen** aus.

### <a name="write-your-test-with-stubs"></a>Den Test mit Stubs schreiben

```csharp
[TestClass]
class TestStockAnalyzer
{
    [TestMethod]
    public void TestContosoStockPrice()
    {
      // Arrange:

        // Create the fake stockFeed:
        IStockFeed stockFeed =
             new StockAnalysis.Fakes.StubIStockFeed() // Generated by Fakes.
                 {
                     // Define each method:
                     // Name is original name + parameter types:
                     GetSharePriceString = (company) => { return 1234; }
                 };

        // In the completed application, stockFeed would be a real one:
        var componentUnderTest = new StockAnalyzer(stockFeed);

        // Act:
        int actualValue = componentUnderTest.GetContosoPrice();

        // Assert:
        Assert.AreEqual(1234, actualValue);
    }
    ...
}
```

```vb
<TestClass()> _
Class TestStockAnalyzer

    <TestMethod()> _
    Public Sub TestContosoStockPrice()
        ' Arrange:
        ' Create the fake stockFeed:
        Dim stockFeed As New StockAnalysis.Fakes.StubIStockFeed
        With stockFeed
            .GetSharePriceString = Function(company)
                                       Return 1234
                                   End Function
        End With
        ' In the completed application, stockFeed would be a real one:
        Dim componentUnderTest As New StockAnalyzer(stockFeed)
        ' Act:
        Dim actualValue As Integer = componentUnderTest.GetContosoPrice
        ' Assert:
        Assert.AreEqual(1234, actualValue)
    End Sub
End Class
```

Das Besondere hierbei ist die `StubIStockFeed`-Klasse. Der Microsoft Fakes-Mechanismus generiert eine Stubklasse für jeden öffentlichen Typ in der Assembly, auf die verwiesen wird. Der Name der Stubklasse wird vom Namen der Schnittstelle abgeleitet. Dabei ist "`Fakes.Stub`" das Präfix, und die Parametertypnamen werden angefügt.

Stubs werden auch für die Getter und Setter von Eigenschaften, für Ereignisse sowie für generische Methoden generiert.

### <a name="verify-parameter-values"></a>Überprüfen von Parameterwerten

Sie können überprüfen, ob die richtigen Werte übergeben werden, wenn Ihre Komponente eine andere Komponente aufruft. Sie können entweder eine Assertion im Stub einfügen, oder Sie können den Wert und speichern und ihn im Hauptteil des Tests überprüfen. Beispiel:

```csharp
[TestClass]
class TestMyComponent
{
    [TestMethod]
    public void TestVariableContosoPrice()
    {
        // Arrange:
        int priceToReturn = 345;
        string companyCodeUsed = "";
        var componentUnderTest = new StockAnalyzer(new StockAnalysis.Fakes.StubIStockFeed()
            {
               GetSharePriceString = (company) =>
                  {
                     // Store the parameter value:
                     companyCodeUsed = company;
                     // Return the value prescribed by this test:
                     return priceToReturn;
                  };
            };

        // Act:
        int actualResult = componentUnderTest.GetContosoPrice();

        // Assert:
        // Verify the correct result in the usual way:
        Assert.AreEqual(priceToReturn, actualResult);

        // Verify that the component made the correct call:
        Assert.AreEqual("COOO", companyCodeUsed);
    }
...
}
```

```vb
<TestClass()> _
Class TestMyComponent
    <TestMethod()> _
    Public Sub TestVariableContosoPrice()
        ' Arrange:
        Dim priceToReturn As Integer = 345
        Dim companyCodeUsed As String = ""
        Dim stockFeed As New StockAnalysis.Fakes.StubIStockFeed()
        With stockFeed
            ' Implement the interface's method:
            .GetSharePriceString = _
                Function(company)
                    ' Store the parameter value:
                    companyCodeUsed = company
                    ' Return a fixed result:
                    Return priceToReturn
                End Function
        End With
        ' Create an object to test:
        Dim componentUnderTest As New StockAnalyzer(stockFeed)

        ' Act:
        Dim actualResult As Integer = componentUnderTest.GetContosoPrice()

        ' Assert:
        ' Verify the correct result in the usual way:
        Assert.AreEqual(priceToReturn, actualResult)
        ' Verify that the component made the correct call:
        Assert.AreEqual("COOO", companyCodeUsed)
    End Sub
...
End Class
```

## <a name="stubs-for-different-kinds-of-type-members"></a>Stubs für verschiedene Arten von Typmembern

### <a name="methods"></a>Methoden

Wie im Beispiel beschrieben, kann ein Stub für Methoden ausgeführt werden, indem ein Delegat an eine Instanz der Stubklasse angefügt wird. Der Name des Stub-Typs wird von den Namen der Methode und der Parameter abgeleitet. Beispielsweise bei Angabe der folgenden `IMyInterface`-Schnittstelle und `MyMethod`-Methode:

```csharp
// application under test
interface IMyInterface
{
    int MyMethod(string value);
}
```

Es wird ein Stub an `MyMethod` angefügt, der immer 1 zurückgibt:

```csharp
// unit test code
var stub = new StubIMyInterface ();
stub.MyMethodString = (value) => 1;
```

Wenn Sie keinen Stub für eine Funktion bereitstellen, generiert Fakes eine Funktion, die den Standardwert des Rückgabetyps zurückgibt. Bei Zahlen ist der Standardwert 0, bei Klassentypen `null` (C#) oder `Nothing` (Visual Basic).

### <a name="properties"></a>Eigenschaften

Getter oder Setter für Eigenschaften werden als separate Delegaten verfügbar gemacht. Es kann ein separater Stub für diese Delegaten ausgeführt werden. Ziehen Sie zum Beispiel die `Value`-Eigenschaft von `IMyInterface` in Erwägung:

```csharp
// code under test
interface IMyInterface
{
    int Value { get; set; }
}
```

Wir fügen Delegaten an den Getter und Setter von `Value` an, um eine Auto-Eigenschaft zu simulieren:

```csharp
// unit test code
int i = 5;
var stub = new StubIMyInterface();
stub.ValueGet = () => i;
stub.ValueSet = (value) => i = value;
```

Wenn Sie keine Stubmethoden für den Setter oder den Getter einer Eigenschaft bereitstellen, generiert Fakes einen Stub, der Werte speichert, sodass die Stubeigenschaft wie eine einfache Variable funktioniert.

### <a name="events"></a>Ereignisse

Ereignisse werden als Delegatfelder verfügbar gemacht. Daher kann jedes Ereignis, für das ein Stub ausgeführt wird, einfach durch Aufruf des dahinter liegenden Ereignisfelds ausgelöst werden. Betrachten wir die folgende Schnittstelle, für die ein Stub ausgeführt werden soll:

```csharp
// code under test
interface IWithEvents
{
    event EventHandler Changed;
}
```

Um das `Changed`-Ereignis auszulösen, wird einfach der dahinter liegende Delegat aufgerufen:

```csharp
// unit test code
  var withEvents = new StubIWithEvents();
  // raising Changed
  withEvents.ChangedEvent(withEvents, EventArgs.Empty);
```

### <a name="generic-methods"></a>Generische Methoden

Es ist möglich, einen Stub mit generischen Methoden aufzurufen, indem ein Delegat für alle gewünschten Instanziierungen der Methode bereitgestellt wird. Betrachten Sie beispielsweise die folgende Schnittstelle, die eine generische Methode enthält:

```csharp
// code under test
interface IGenericMethod
{
    T GetValue<T>();
}
```

Sie können einen Test schreiben, mit dem ein Stub für die `GetValue<int>`-Instanziierung ausgeführt wird:

```csharp
// unit test code
[TestMethod]
public void TestGetValue()
{
    var stub = new StubIGenericMethod();
    stub.GetValueOf1<int>(() => 5);

    IGenericMethod target = stub;
    Assert.AreEqual(5, target.GetValue<int>());
}
```

Ruft der Code `GetValue<T>` mit einer anderen Instanziierung auf, würde der Stub einfach das Verhalten aufrufen.

### <a name="stubs-of-virtual-classes"></a>Stubs von virtuellen Klassen

In den vorherigen Beispielen wurden die Stubs aus Schnittstellen generiert. Sie können Stubs auch aus einer Klasse generieren, die über virtuelle oder abstrakte Member verfügt. Beispiel:

```csharp
// Base class in application under test
    public abstract class MyClass
    {
        public abstract void DoAbstract(string x);
        public virtual int DoVirtual(int n)
        { return n + 42; }
        public int DoConcrete()
        { return 1; }
    }
```

In dem Stub, der aus dieser Klasse generiert wird, können Sie Delegatmethoden für `DoAbstract()` und `DoVirtual()`, aber nicht für `DoConcrete()` festlegen.

```csharp
// unit test
  var stub = new Fakes.MyClass();
  stub.DoAbstractString = (x) => { Assert.IsTrue(x>0); };
  stub.DoVirtualInt32 = (n) => 10 ;
```

Wenn Sie keinen Delegaten für eine virtuelle Methode bereitstellen, kann Fakes entweder das Standardverhalten bereitstellen oder die Methode in der Basisklasse aufrufen. Legen Sie die `CallBase`-Eigenschaft zum Aufrufen der Basismethode wie folgt fest:

```csharp
// unit test code
var stub = new Fakes.MyClass();
stub.CallBase = false;
// No delegate set - default delegate:
Assert.AreEqual(0, stub.DoVirtual(1));

stub.CallBase = true;
// No delegate set - calls the base:
Assert.AreEqual(43,stub.DoVirtual(1));
```

## <a name="debug-stubs"></a>Debuggen von Stubs

Die Stub-Typen wurden entwickelt, um einen reibungslosen Debugvorgang zu gewährleisten. Standardmäßig wird der Debugger angewiesen, sämtlichen generierten Code zu überspringen und die benutzerdefinierten Memberimplementierungen, die an den Stub angefügt wurden, direkt in Einzelschritten auszuführen.

## <a name="stub-limitations"></a>Einschränkungen für Stubs

- Methodensignaturen mit Zeigern werden nicht unterstützt.

- Für versiegelte Klassen oder statische Methoden kann kein Stub ausgeführt werden, da Stub-Typen auf dem Dispatch von virtuellen Methoden basieren. Verwenden Sie in solchen Fällen Shim-Typen, so wie in [Verwenden von Shims, um für Komponententests die Anwendung von anderen Assemblys zu trennen](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md) beschrieben.

## <a name="change-the-default-behavior-of-stubs"></a>Ändern des Standardverhaltens von Stubs

Jeder generierte Stub-Typ enthält eine Instanz der `IStubBehavior`-Schnittstelle (durch die `IStub.InstanceBehavior`-Eigenschaft). Das Verhalten wird aufgerufen, wenn ein Client einen Member ohne angefügten benutzerdefinierten Delegaten aufruft. Wenn das Verhalten nicht festgelegt wurde, wird die Instanz verwendet, die durch die `StubsBehaviors.Current`-Eigenschaft zurückgegeben wird. Standardmäßig gibt diese Eigenschaft ein Verhalten zurück, das eine `NotImplementedException`-Ausnahme auslöst.

Das Verhalten kann jederzeit durch Festlegen der `InstanceBehavior`-Eigenschaft auf jede beliebige Stub-Instanz geändert werden. Beispielsweise ändert der folgende Ausschnitt ein Verhalten, das keine Aktion ausführt oder den Standardwert des Rückgabetyps zurückgibt: `default(T)`:

```csharp
// unit test code
var stub = new StubIFileSystem();
// return default(T) or do nothing
stub.InstanceBehavior = StubsBehaviors.DefaultValue;
```

Das Verhalten kann auch global für alle Stubobjekte, für die das Verhalten nicht festgelegt wurde, durch Festlegung der `StubsBehaviors.Current`-Eigenschaft geändert werden:

```csharp
// Change default behavior for all stub instances
// where the behavior has not been set.
StubBehaviors.Current = BehavedBehaviors.DefaultValue;
```

## <a name="see-also"></a>Weitere Informationen

- [Isolieren von getestetem Code mithilfe von Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)
