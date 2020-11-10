---
title: Isolieren von getestetem Code mithilfe von Microsoft Fakes
ms.date: 06/03/2020
ms.topic: how-to
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
dev_langs:
- VB
- CSharp
ms.openlocfilehash: e837b1a0e9a1d8fe06342352e4eedf5ce0fa9117
ms.sourcegitcommit: f2bb3286028546cbd7f54863b3156bd3d65c55c4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2020
ms.locfileid: "93325950"
---
# <a name="isolate-code-under-test-with-microsoft-fakes"></a>Isolieren von getestetem Code mithilfe von Microsoft Fakes

Mit Microsoft Fakes isolieren Sie den zu testenden Code, indem Sie andere Teile der Anwendung durch *Stubs* oder *Shims* ersetzen. Dabei handelt es sich um kurze Codes, die von den Tests kontrolliert werden. Wenn Sie den Code für die Tests isolieren, wissen Sie beim Fehlschlagen des Tests, dass die Ursache im isolierten Code und nicht an anderer Stelle liegt. Mit Stubs und Shims können Sie den Code auch dann testen, wenn andere Teile der Anwendung noch nicht funktionieren.

Es gibt zwei Arten von Fakes:

- Ein [Stub](#get-started-with-stubs) tauscht eine Klasse gegen einen kleinen Ersatz aus, der die gleiche Schnittstelle implementiert.  Um Stubs verwenden zu können, müssen Sie die Anwendung so entwerfen, dass jede Komponente nur von Schnittstellen abhängt und nicht von anderen Komponenten. (Mit "Komponente" ist eine Klasse oder eine Gruppe von Klassen gemeint, die zusammen entworfen und aktualisiert werden und in der Regel in einer Assembly enthalten sind.)

- Ein [Shim](#get-started-with-shims) ändert den kompilierten Code der Anwendung zur Laufzeit, damit anstelle des angegebenen Methodenaufrufs der vom Test bereitgestellte Shimcode ausgeführt wird. Mit Shims können Sie Aufrufe von Assemblys ersetzen, die nicht geändert werden können, wie zum Beispiel .NET-Assemblys.

![Fakes ersetzen andere Komponenten](../test/media/fakes-2.png)

**Anforderungen**

- Visual Studio Enterprise
- Ein .NET Framework-Projekt
::: moniker range=">=vs-2019"
- Die Unterstützung von Projekten im .NET Core- und SDK-Format ist in Visual Studio 2019 Update 6 als Vorschaufeature enthalten und in Update 8 standardmäßig aktiviert. Weitere Informationen finden Sie unter [Microsoft Fakes für .NET Core- und SDK-Projekte](/visualstudio/releases/2019/release-notes#microsoft-fakes-for-net-core-and-sdk-style-projects).
::: moniker-end

> [!NOTE]
> - Die Profilerstellung mit Visual Studio ist nicht für Tests verfügbar, die Microsoft Fakes verwenden.

## <a name="choose-between-stub-and-shim-types"></a>Auswählen zwischen Stub- und Shim-Typen
In der Regel lässt sich ein Visual Studio-Projekt als Komponente betrachten, da die Klassen gleichzeitig entwickelt und aktualisiert werden. Sie können Stubs und Shims für Aufrufe verwenden, die das Projekt an andere Projekte in der Projektmappe oder an andere Assemblys, auf die das Projekt verweist, richtet.

Als allgemeine Richtlinie verwenden Sie Stubs für Aufrufe in der Visual Studio-Projektmappe und Shims für Aufrufe von anderen Assemblys, auf die verwiesen wird. Dies liegt daran, dass es in der eigenen Projektmappe ratsam ist, die Komponenten zu entkoppeln, indem Schnittstellen so definiert werden, dass Stubs erforderlich sind. Externe Assemblys wie *System.dll* hingegen werden in der Regel nicht mit separaten Schnittstellendefinitionen bereitgestellt, sodass Sie stattdessen Shims verwenden müssen.

Weitere Überlegungen:

**Leistung** Shims werden langsamer ausgeführt, da der Code zur Laufzeit neu geschrieben wird. Die Leistung von Stubs wird nicht auf diese Weise beeinträchtigt. Sie sind so schnell, wie es bei virtuellen Methoden möglich ist.

**Statische Methoden, versiegelte Typen:** Sie können Stubs nur verwenden, um Schnittstellen zu implementieren. Daher können Stubtypen für folgende Methoden nicht verwendet werden: statische Methoden, nicht virtuelle Methoden, versiegelte virtuelle Methoden, Methoden in versiegelten Typen usw.

**Interne Typen** Stubs und Shims können mit internen Typen verwendet werden, die verfügbar gemacht werden, indem das Assemblyattribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> verwendet wird.

**Private Methoden** Shims können Aufrufe von privaten Methoden ersetzen, wenn alle Typen auf der Methodensignatur sichtbar sind. Stubs können nur sichtbare Methoden ersetzen.

**Schnittstellen und abstrakte Methoden:** Stubs stellen Implementierungen von Schnittstellen und abstrakten Methoden bereit, die in den Tests verwendet werden können. Shims können Schnittstellen und abstrakte Methoden nicht instrumentieren, da sie über keine Methodentexte verfügen.

Im Allgemeinen empfiehlt es sich, Stubtypen zu verwenden, um eine Isolierung von den Abhängigkeiten in der Codebase zu erzielen. Sie erreichen dies, indem Sie die Komponenten hinter den Schnittstellen ausblenden. Shimtypen können verwendet werden, um eine Isolierung von Drittanbieterkomponenten zu erzielen, die keine testfähige API bereitstellen.

## <a name="get-started-with-stubs"></a>Erste Schritte mit Stubs
Eine ausführlichere Beschreibung finden Sie unter [Use stubs to isolate parts of your application from each other for unit testing (Verwenden von Stubs, um Teile der Anwendung für Komponententests voneinander zu isolieren)](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md).

1. **Einfügen von Schnittstellen**

     Um Stubs verwenden zu können, müssen Sie den zu testenden Code so schreiben, dass Klassen in einer anderen Komponente der Anwendung nicht explizit erwähnt werden. Mit "Komponente" sind eine oder mehrere Klassen gemeint, die zusammen entworfen und aktualisiert werden und in der Regel in einem Visual Studio-Projekt enthalten sind. Variablen und Parameter sollten über Schnittstellen deklariert werden, und Instanzen anderer Komponenten sollten durch eine Factory übergeben oder erstellt werden. Wenn StockFeed eine Klasse in einer anderen Komponente der Anwendung ist, wäre dies ein negatives Beispiel:

     `return (new StockFeed()).GetSharePrice("COOO"); // Bad`

     Definieren Sie stattdessen eine Schnittstelle, die von der anderen Komponente und auch durch einen Stub für Testzwecke implementiert werden kann:

    ```csharp
    public int GetContosoPrice(IStockFeed feed) => feed.GetSharePrice("COOO");
    ```

    ```vb
    Public Function GetContosoPrice(feed As IStockFeed) As Integer
     Return feed.GetSharePrice("COOO")
    End Function

    ```

2. **Hinzufügen von Fakes-Assemblys**

   1. Im **Projektmappen-Explorer** : 
       - Erweitern Sie für ein älteres .NET Framework-Projekt (kein SDK-Format) den Knoten **Verweise** Ihres Projekts für den Komponententest.
       ::: moniker range=">=vs-2019"
       - Erweitern Sie bei einem Projekt im SDK-Format für .NET Framework oder .NET Core unter **Assemblys** , **Projekte** oder **Pakete** den Knoten **Abhängigkeiten** , um die gewünschte Assembly zu finden, die Sie als Fakes-Assembly verwenden möchten.
       ::: moniker-end
       - Wenn Sie in Visual Basic arbeiten, müssen Sie auf der Symbolleiste im **Projektmappen-Explorer** auf **Alle Dateien anzeigen** klicken, um den Knoten **Verweise** anzuzeigen.
   2. Wählen Sie die Assembly aus, in der die Klassendefinitionen enthalten sind, für die Sie Shims erstellen möchten. Wenn Sie z.B. einen Shim für **DateTime** erstellen möchten, klicken Sie auf **System.dll**.

   3. Wählen Sie im Kontextmenü **Fakes-Assembly hinzufügen** aus.

3. Erstellen Sie in den Tests Instanzen des Stubs, und stellen Sie Code für dessen Methoden bereit:

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

    Das Besondere hierbei ist die `StubIStockFeed`-Klasse. Der Microsoft Fakes-Mechanismus generiert für jede Schnittstelle in der Assembly, auf die verwiesen wird, eine Stubklasse. Der Name der Stubklasse wird vom Namen der Schnittstelle abgeleitet. Dabei ist `Fakes.Stub` das Präfix, und die Parametertypnamen werden angefügt.

    Stubs werden auch für die Getter und Setter von Eigenschaften, für Ereignisse sowie für generische Methoden generiert. Weitere Informationen finden Sie unter [Use stubs to isolate parts of your application from each other for unit testing (Verwenden von Stubs, um Teile der Anwendung für Komponententests voneinander zu isolieren)](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md).

## <a name="get-started-with-shims"></a>Erste Schritte mit Shims
(Eine ausführlichere Beschreibung finden Sie unter [Use shims to isolate your application from other assemblies for unit testing (Verwenden von Shims, um die Anwendung für Komponententests von anderen Assemblys zu isolieren)](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md).)

Angenommen, die Komponente enthält Aufrufe von `DateTime.Now`:

```csharp
// Code under test:
    public int GetTheCurrentYear()
    {
       return DateTime.Now.Year;
    }
```

Da die richtige Version ungünstigerweise bei jedem Aufruf einen anderen Wert zurückgibt, möchten Sie während der Tests ein Shim für die `Now`-Eigenschaft durchführen.

Für Shims müssen Sie den Anwendungscode nicht ändern und ihn auch nicht auf bestimmte Weise schreiben.

1. **Hinzufügen von Fakes-Assemblys**

     Öffnen Sie im **Projektmappen-Explorer** die Verweise des Komponententestprojekts, und wählen Sie den Verweis auf die Assembly mit der Methode aus, für die Sie einen Fake durchführen möchten. In diesem Beispiel befindet sich die `DateTime`-Klasse in *System.dll*.  Um die Verweise in einem Visual Basic-Projekt anzuzeigen, wählen Sie **Alle Dateien anzeigen** aus.

     Wählen Sie **Fakes-Assembly hinzufügen** aus.

2. **Hinzufügen eines Shims zu einem ShimsContext**

    ```csharp
    [TestClass]
    public class TestClass1
    {
            [TestMethod]
            public void TestCurrentYear()
            {
                int fixedYear = 2000;

                // Shims can be used only in a ShimsContext:
                using (ShimsContext.Create())
                {
                  // Arrange:
                    // Shim DateTime.Now to return a fixed date:
                    System.Fakes.ShimDateTime.NowGet =
                    () =>
                    { return new DateTime(fixedYear, 1, 1); };

                    // Instantiate the component under test:
                    var componentUnderTest = new MyComponent();

                  // Act:
                    int year = componentUnderTest.GetTheCurrentYear();

                  // Assert:
                    // This will always be true if the component is working:
                    Assert.AreEqual(fixedYear, year);
                }
            }
    }
    ```

    ```vb
    <TestClass()> _
    Public Class TestClass1
        <TestMethod()> _
        Public Sub TestCurrentYear()
            Using s = Microsoft.QualityTools.Testing.Fakes.ShimsContext.Create()
                Dim fixedYear As Integer = 2000
                ' Arrange:
                ' Detour DateTime.Now to return a fixed date:
                System.Fakes.ShimDateTime.NowGet = _
                    Function() As DateTime
                        Return New DateTime(fixedYear, 1, 1)
                    End Function

                ' Instantiate the component under test:
                Dim componentUnderTest = New MyComponent()
                ' Act:
                Dim year As Integer = componentUnderTest.GetTheCurrentYear
                ' Assert:
                ' This will always be true if the component is working:
                Assert.AreEqual(fixedYear, year)
            End Using
        End Sub
    End Class
    ```

    Shimklassennamen werden gebildet, indem dem ursprünglichen Typnamen `Fakes.Shim` vorangestellt wird. Parameternamen werden dem Methodennamen angefügt. (Sie müssen keine Assemblyverweise zu System.Fakes hinzufügen.)

Im vorherigen Beispiel wird ein Shim für eine statische Methode verwendet. Um einen Shim für eine Instanzmethode zu verwenden, schreiben Sie `AllInstances` zwischen den Typnamen und den Methodennamen:

```vb
System.IO.Fakes.ShimFile.AllInstances.ReadToEnd = ...
```

(Es gibt keine Assembly „System.IO.Fakes“, auf die verwiesen werden kann. Der Namespace wird vom Shim-Erstellungsprozess generiert. Sie können jedoch „using“ oder „import“ auf die übliche Weise verwenden.)

Sie können Shims auch für bestimmte Instanzen, für Konstruktoren und für Eigenschaften erstellen. Weitere Informationen finden Sie unter [Use shims to isolate your application from other assemblies for unit testing (Verwenden von Shims, um die Anwendung für Komponententests von anderen Assemblys zu isolieren)](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md).

## <a name="using-microsoft-fakes-in-the-ci"></a>Verwenden von Microsoft Fakes in der CI

### <a name="microsoft-fakes-assembly-generation"></a>Generieren einer Microsoft Fakes-Assembly
Da für Microsoft Fakes Visual Studio Enterprise benötigt wird, setzt das Generieren von Fakes-Assemblys voraus, dass Sie Ihr Projekt mit der [Visual Studio-Buildaufgabe](/azure/devops/pipelines/tasks/build/visual-studio-build?view=azure-devops) kompilieren.

::: moniker range=">=vs-2019"
> [!NOTE]
> Alternativ können Sie Ihre Fakes-Assemblys in die CI einchecken und den [MSBuild-Aufgabe](../msbuild/msbuild-task.md?view=vs-2019) verwenden. In diesem Fall müssen Sie sicherstellen, dass Sie über einen Assemblyverweis zur generierten Fakes-Assembly in Ihrem Testprojekt verfügen, ähnlich dem folgenden Codeausschnitt:

```xml
<Project Sdk="Microsoft.NET.Sdk">
    <ItemGroup>
        <Reference Include="FakesAssemblies\System.Fakes.dll">
    </ItemGroup>
</Project>
```

Dieser Verweis muss insbesondere in Projekten im SDK-Format (.NET Core und .NET Framework) manuell hinzugefügt werden, weil Assemblyverweise Ihrem Testprojekt jetzt implizit hinzugefügt werden. Wenn Sie diesen Ansatz nutzen, müssen Sie dafür sorgen, dass die Fakes-Assembly bei einer Änderung der übergeordneten Assembly aktualisiert wird.
::: moniker-end

### <a name="running-microsoft-fakes-tests"></a>Ausführen von Microsoft Fakes-Tests
Solange Microsoft Fakes-Assemblys im konfigurierten Verzeichnis `FakesAssemblies` vorhanden sind (standardmäßig `$(ProjectDir)FakesAssemblies`), können Sie Tests unter Verwendung der [vstest-Aufgabe](/azure/devops/pipelines/tasks/test/vstest?view=azure-devops) ausführen.

::: moniker range=">=vs-2019"
Für verteilte Tests mit der [vstest-Aufgabe](/azure/devops/pipelines/tasks/test/vstest?view=azure-devops) für .NET Core-Projekte unter Verwendung von Microsoft Fakes wird Visual Studio 2019 Update 9 Preview `20201020-06` oder höher benötigt.
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="transitioning-your-net-framework-test-projects-that-use-microsoft-fakes-to-sdk-style-net-framework-or-net-core-projects"></a>Umstellen Ihrer .NET Framework-Testprojekte mit Verwendung von Microsoft Fakes auf .NET Framework- oder .NET Core-Projekte im SDK-Format
Für eine Umstellung auf .NET Core sind minimale Änderungen in Ihrem .NET Framework-Setup für Microsoft Fakes erforderlich. Folgende Fälle müssen berücksichtigt werden:
- Wenn Sie eine benutzerdefinierte Projektvorlage verwenden, müssen Sie sicherstellen, dass diese im SDK-Format vorliegt und in ein kompatibles Zielframework kompiliert wird.
- Bestimmte Typen sind in verschiedenen Assemblys in .NET Framework und .NET Core vorhanden (beispielsweise wird `System.DateTime` in `System`/`mscorlib` in .NET Framework und in `System.Runtime` in .NET Core verwendet). In einem solchen Szenario müssen Sie die Assembly für Fakes ändern.
- Wenn ein Assemblyverweis auf eine Fakes-Assembly und das Testprojekt vorhanden ist, wird möglicherweise eine der folgenden ähnliche Warnung zu einem fehlenden Verweis angezeigt:
  ```
  (ResolveAssemblyReferences target) ->
  warning MSB3245: Could not resolve this reference. Could not locate the assembly "AssemblyName.Fakes". Check to make sure the assembly exists on disk.
  If this reference is required by your code, you may get compilation errors.
  ```
  Diese Warnung ist auf erforderliche Änderungen an der Fakes-Generierung zurückzuführen und kann ignoriert werden. Die Meldung kann durch das Entfernen des Assemblyverweises aus der Projektdatei vermieden werden, weil Verweise jetzt während des Builds implizit hinzugefügt werden.
::: moniker-end

## <a name="microsoft-fakes-support"></a>Microsoft Fakes-Unterstützung 
### <a name="microsoft-fakes-in-older-projects-targeting-net-framework-non-sdk-style"></a>Microsoft Fakes in älteren Projekten mit .NET Framework als Ziel (kein SDK-Format)
- Das Generieren von Microsoft Fakes-Assemblys wird in Visual Studio Enterprise 2015 und höher unterstützt.
- Microsoft Fakes-Tests können mit allen verfügbaren Microsoft.TestPlatform-NuGet-Paketen ausgeführt werden.
- Code Coverage wird für Testprojekte mit Verwendung von Microsoft Fakes in Visual Studio Enterprise 2015 und höher unterstützt.

### <a name="microsoft-fakes-in-sdk-style-net-framework-and-net-core-projects"></a>Microsoft Fakes in .NET Framework- und .NET Core-Projekten mit SDK-Format
- Das Generieren von Microsoft Fakes-Assemblys ist in Visual Studio Enterprise 2019 Update 6 als Vorschaufeature enthalten und in Update 8 standardmäßig aktiviert.
- Microsoft Fakes-Tests für Projekte mit .NET Framework als Ziel können mit allen verfügbaren Microsoft.TestPlatform-NuGet-Paketen ausgeführt werden.
- Microsoft Fakes-Tests für Projekte mit .NET Core als Ziel können mit Microsoft.TestPlatform-NuGet-Paketen der Version [16.8.0-preview-20200921-01](https://www.nuget.org/packages/Microsoft.TestPlatform/16.8.0-preview-20200921-01) und höher ausgeführt werden.
- Code Coverage wird für .NET Framework-Testprojekte mit Verwendung von Microsoft Fakes in Visual Studio Enterprise 2015 und höher unterstützt.
- Die Unterstützung von Code Coverage für .NET Core-Testprojekte mit Verwendung von Microsoft Fakes befindet sich derzeit in der Entwicklung.


## <a name="in-this-section"></a>In diesem Abschnitt
[Verwenden von Stubs, um für Komponententests Teile der Anwendung voneinander zu trennen](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md)

[Verwenden von Shims, um zu Komponententests die Anwendung von anderen Assemblys zu trennen](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md)

[Codegenerierung, Kompilierung und Benennungskonventionen in Microsoft Fakes](../test/code-generation-compilation-and-naming-conventions-in-microsoft-fakes.md)
