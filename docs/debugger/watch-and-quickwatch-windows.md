---
title: Festlegen einer Überwachung für Variablen | Microsoft-Dokumentation
description: Während des Debuggens werden Ihnen unter „Überwachung“ und „Schnellüberwachung“ Variablen und Ausdrücke angezeigt. Unter „Überwachung“ können mehrere Variablen angezeigt werden, während unter „Schnellüberwachung“ nur eine Variable angezeigt wird. Dies ist nur im Unterbrechungsmodus möglich.
ms.custom: SEO-VS-2020, seodec18
ms.date: 10/11/2018
ms.topic: how-to
f1_keywords:
- vs.debug.watch
helpviewer_keywords:
- debugging [Visual Studio], Watch window
- expressions [debugger], evaluating
- variables [debugger], evaluating
- expression evaluation
- registers, evaluating
- debugging [Visual Studio], expression evaluation
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d13ee6163ebe8cf0f706cbe95e7451c2ebc7c411
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149481"
---
# <a name="watch-variables-with-watch-windows-and-quickwatch"></a>Überwachen von Variablen mit Überwachungsfenstern und Schnellüberwachung

Beim Debuggen können Sie Fenster des Typs **Überwachen** und **Schnellüberwachung** verwenden, um Variablen und Ausdrücke zu überwachen. Die Fenster sind nur während einer Debugsitzung verfügbar.

In Fenstern des Typs **Überwachen** können während des Debuggens mehrere Variablen gleichzeitig angezeigt werden. Im Dialogfeld **Schnellüberwachung** wird jeweils eine einzelne Variable angezeigt. Dieses Dialogfeld muss geschlossen werden, bevor das Debuggen fortgesetzt werden kann.

> [!NOTE]
> Wenn Sie zum ersten Mal versuchen, Code zu debuggen, sollten Sie [Debuggen für Einsteiger](../debugger/debugging-absolute-beginners.md) sowie [Debugverfahren und -tools](../debugger/write-better-code-with-visual-studio.md) lesen, bevor Sie diesen Artikel durchgehen.

## <a name="observe-variables-with-a-watch-window"></a>Beobachten von Variablen mit einem Überwachungsfenster

Sie können mehrere Fenster des Typs **Überwachen** öffnen und mehrere Variablen in einem **Überwachen**-Fenster beobachten.

Wenn Sie beispielsweise eine Überwachung der Werte von `a`, `b` und `c` im folgenden Code festlegen möchten, gehen Sie folgendermaßen vor:

```C++
int main()
{
    int a, b, c;
    a = 1;
    b = 2;
    c = 0;

    for (int i = 0; i < 10; i++)
    {
        a++;
        b *= 2;
        c = a + b;
    }

    return 0;
}

```

1. Legen Sie einen Haltepunkt in der Zeile `c = a + b;` fest. Dazu klicken Sie auf den linken Rand und wählen **Debuggen** > **Haltepunkt ein/aus** aus, oder Sie drücken **F9**.

1. Starten Sie das Debuggen. Dazu wählen Sie den grünen Pfeil für **Starten** oder **Debuggen** > **Debuggen starten** aus, oder drücken Sie **F5**. Die Ausführung wird am Haltepunkt angehalten.

1. Öffnen Sie ein Fenster des Typs **Überwachen**. Dazu wählen Sie **Debuggen** > **Fenster** > **Überwachen** > **Überwachen 1** aus, oder drücken Sie **STRG**+**ALT**+**W** > **1**.

   Sie können weitere Fenster des Typs **Überwachen** öffnen, indem Sie die Fenster **2**, **3** oder **4** auswählen.

1. Wählen Sie im Fenster **Überwachen** eine leere Zeile aus, und geben Sie Variable `a` ein. Führen Sie die gleichen Schritte für `b` und `c` aus.

   ![Überwachen von Variablen](../debugger/media/watchvariables.png "Überwachen von Variablen")

1. Setzen Sie das Debuggen fort, indem Sie nach Bedarf **Debuggen** > **Einzelschritt** auswählen oder **F11** drücken, um fortzufahren. Die Variablenwerte im Fenster **Überwachen** ändern sich, während Sie die `for`-Schleife durchlaufen.

>[!NOTE]
>Nur für C++:
>- Möglicherweise müssen Sie den Kontext eines Variablennamens oder eines Ausdrucks, der einen Variablennamen verwendet, qualifizieren. Mit dem Kontext sind die Funktion, die Quelldatei oder das Modul gemeint, in der bzw. dem eine Variable enthalten ist. Wenn Sie den Kontext qualifizieren müssen, verwenden Sie die Syntax des [Kontextoperators (C++)](../debugger/context-operator-cpp.md) für **Name** im Fenster **Überwachen**.
>
>- Sie können Registernamen und Variablennamen mithilfe von **$\<register&nbsp;name>** oder **@\<register&nbsp;name>** zum **Namen** im Fenster **Überwachen** hinzufügen. Weitere Informationen finden Sie unter [Pseudovariables](../debugger/pseudovariables.md).

## <a name="use-expressions-in-a-watch-window"></a>Verwenden von Ausdrücken in einem Überwachungsfenster

Sie können jeden vom Debugger erkannten gültigen Ausdruck in einem **Überwachen**-Fenster beobachten.

Beispielsweise können Sie für den im vorherigen Abschnitt gezeigten Code den Mittelwert der drei Werte ermitteln, indem Sie `(a + b + c) / 3` im Fenster **Überwachen** eingeben:

![Überwachen eines Ausdrucks](../debugger/media/watchexpression.png "Überwachen eines Ausdrucks")

Die Regeln zum Auswerten von Ausdrücken im Fenster **Überwachen** entsprechen im Allgemeinen den Regeln zum Auswerten von Ausdrücken in der Codesprache. Wenn ein Ausdruck einen Syntaxfehler aufweist, können Sie den gleichen Compilerfehler wie im Code-Editor erwarten. Beispielsweise erzeugt ein Tippfehler im vorherigen Ausdruck den folgenden Fehler im Fenster **Überwachen**:

![Fehler beim Überwachen eines Ausdrucks](../debugger/media/watchexpressionerror.png "Fehler beim Überwachen eines Ausdrucks")

Im Fenster **Überwachen** wird möglicherweise ein Kreis mit zwei Wellenlinien angezeigt. Dieses Symbol bedeutet, dass der Debugger den Ausdruck aufgrund einer möglichen threadübergreifenden Abhängigkeit nicht auswertet. Für die Auswertung des Codes müssen andere Threads in der App vorübergehend ausgeführt werden. Da Sie sich aber im Unterbrechungsmodus befinden, sind alle Threads in der App normalerweise angehalten. Wenn die vorübergehende Ausführung anderer Threads zugelassen wird, kann dies unerwartete Auswirkungen auf den Zustand der App haben, und der Debugger ignoriert möglicherweise Ereignisse wie z. B. Haltepunkte und Ausnahmen für diese Threads.

::: moniker range=">= vs-2019" 
## <a name="search-in-the-watch-window"></a>Suchen im Überwachungsfenster

Sie können mithilfe der Suchleiste oberhalb der einzelnen Fenster nach Schlüsselwörtern in den Spalten „Name“, „Wert“ und „Typ“ im Fenster **Überwachen** suchen. Drücken Sie die EINGABETASTE, oder wählen Sie einen der Pfeile aus, um eine Suche auszuführen. Zum Abbrechen einer laufenden Suche wählen Sie das Symbol „x“ in der Suchleiste aus.

Mit den Pfeilen nach links und rechts (UMSCHALT+F3 bzw. F3) können Sie zwischen gefundenen Übereinstimmungen navigieren.

![Suchen im Überwachungsfenster](../debugger/media/ee-search-watch.png "Suchen im Überwachungsfenster")

Wenn Sie die Suche mehr oder weniger gründlich durchführen möchten, verwenden Sie die Dropdownliste **Suchtiefe** am oberen Rand des Fensters **Überwachen**, um auszuwählen, wie viele Ebenen tief in geschachtelten Objekten gesucht werden soll. 

## <a name="pin-properties-in-the-watch-window"></a>Anheften von Eigenschaften im Überwachungsfenster

>[!NOTE]
> Diese Funktion wird in .NET Core 3.0 oder höher unterstützt.

Mit dem Tool **Anheftbare Eigenschaften** können Sie Objekte schnell anhand ihrer Eigenschaften im Überwachungsfenster überprüfen.  Um dieses Tool zu verwenden, zeigen Sie auf eine Eigenschaft, und wählen Sie das daraufhin angezeigte Anheften-Symbol aus. Sie können auch mit der rechten Maustaste klicken und im resultierenden Kontextmenü die Option **Member als Favorit anheften** auswählen.  Dadurch wird diese Eigenschaft in der Eigenschaftenliste des Objekts an oberste Stelle gesetzt, und der Eigenschaftsname und -wert wird in der Spalte **Wert** angezeigt.  Wenn Sie eine Eigenschaft lösen möchten, wählen Sie das Anheften-Symbol erneut aus, oder wählen Sie im Kontextmenü die Option **Member als Favorit lösen** aus.

![Anheften von Eigenschaften im Überwachungsfenster](../debugger/media/basic-pin-watch.gif "Anheften von Eigenschaften im Überwachungsfenster")

Sie können beim Anzeigen der Eigenschaftenliste des Objekts im Überwachungsfenster auch Eigenschaftsnamen umschalten und nicht angeheftete Eigenschaften herausfiltern.  Sie können auf beide Optionen zugreifen, indem Sie die Schaltflächen auf der Symbolleiste oberhalb des Überwachungsfensters auswählen.

::: moniker-end

### <a name="refresh-watch-values"></a><a name="bkmk_refreshWatch"></a> Aktualisieren von Überwachungswerten

Beim Auswerten eines Ausdrucks wird möglicherweise ein Aktualisierungssymbol (kreisförmiger Pfeil) im Fenster **Überwachen** angezeigt. Das Aktualisierungssymbol weist auf einen Fehler oder einen veralteten Wert hin.

Klicken Sie zum Aktualisieren des Werts auf das Aktualisierungssymbol, oder drücken Sie die LEERTASTE. Der Debugger versucht, den Ausdruck neu auszuwerten. Je nachdem, warum der Wert nicht ausgewertet wurde, kann es sein, dass Sie den Ausdruck nicht neu auswerten wollen oder können.

Zeigen Sie auf das Aktualisierungssymbol, oder sehen Sie in der Spalte **Wert** nach, um zu erfahren, warum der Ausdruck nicht ausgewertet wurde. Dies kann u.a. folgende Gründe haben:

- Beim Auswerten des Ausdrucks ist ein Fehler aufgetreten (wie im vorherigen Beispiel). Möglicherweise ist ein Timeout aufgetreten, oder eine Variable liegt außerhalb des gültigen Bereichs.

- Der Ausdruck enthält einen Funktionsaufruf, der einen Nebeneffekt in der App auslösen könnte. Informationen dazu finden Sie unter [Nebeneffekte von Ausdrücken](#bkmk_sideEffects).

- Die automatische Auswertung von Eigenschaften und impliziten Funktionsaufrufen ist deaktiviert.

Wenn das Aktualisierungssymbol angezeigt wird, weil die automatische Auswertung von Eigenschaften und impliziten Funktionsaufrufen deaktiviert ist, können Sie diese Option aktivieren, indem Sie **Eigenschaftenauswertung und andere implizite Funktionsaufrufe zulassen** unter **Extras** > **Optionen** > **Debuggen** > **Allgemein** auswählen.

Die Verwendung des Aktualisierungssymbols kann mit folgenden Schritten veranschaulicht werden:

1. Deaktivieren Sie unter **Extras** > **Optionen** > **Debuggen** > **Allgemein** das Kontrollkästchen **Eigenschaftenauswertung und andere implizite Funktionsaufrufe zulassen**.

1. Geben Sie den folgenden Code ein, und legen Sie im Fenster **Überwachen** eine Überwachung für die Eigenschaft `list.Count` fest.

   ```csharp
   static void Main(string[] args)
   {
       List<string> list = new List<string>();
       list.Add("hello");
       list.Add("goodbye");
   }
   ```

1. Beginnen Sie mit dem Debuggen. Im Fenster **Überwachen** wird in etwa die folgende Meldung angezeigt:

   ![Aktualisieren der Überwachung](../debugger/media/refreshwatch.png "Aktualisieren der Überwachung")

1. Klicken Sie zum Aktualisieren des Werts auf das Aktualisierungssymbol, oder drücken Sie die LEERTASTE. Der Debugger wertet den Ausdruck erneut aus.

### <a name="expression-side-effects"></a><a name="bkmk_sideEffects"></a> Nebeneffekte von Ausdrücken

Die Auswertung bestimmter Ausdrücke kann zur Änderung des Werts einer Variablen führen oder sich anderweitig auf den Zustand der App auswirken. Die Auswertung des folgenden Ausdrucks ändert beispielsweise den Wert von `var1`:

```csharp
var1 = var2
```

Dieser Code kann einen [Nebeneffekt](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)) verursachen. Nebeneffekte können das Debuggen erschweren, da sie die Funktionsweise der App ändern.

Ein Ausdruck mit Nebeneffekten wird nur bei der ersten Eingabe ausgewertet. Danach ist der Ausdruck im Fenster **Überwachen** ausgegraut, und weitere Auswertungen sind deaktiviert. In der QuickInfo oder der Spalte **Wert** wird erklärt, dass der Ausdruck einen Nebeneffekt bewirkt. Sie können eine erneute Auswertung erzwingen, indem Sie auf das Aktualisierungssymbol klicken, das neben dem Wert angezeigt wird.

Eine Möglichkeit, die Angabe von Nebeneffekten zu verhindern, ist das Deaktivieren der automatischen Funktionsauswertung. Deaktivieren Sie unter **Extras** > **Optionen** > **Debuggen** > **Allgemein** die Option **Eigenschaftenauswertung und andere implizite Funktionsaufrufe zulassen**.

Nur für C#: Wenn die Auswertung von Eigenschaften oder impliziten Funktionsaufrufen deaktiviert ist, können Sie die Auswertung erzwingen, indem Sie den **ac**-Formatmodifizierer zu einer Variablen unter **Name** im Fenster **Überwachen** hinzufügen. Weitere Informationen finden Sie unter [Formatieren von Spezifizierern in C#](../debugger/format-specifiers-in-csharp.md).

## <a name="use-object-ids-in-the-watch-window-c-and-visual-basic"></a><a name="bkmk_objectIds"></a> Verwenden von Objekt-IDs im Überwachungsfenster (C# und Visual Basic)

Manchmal möchten Sie das Verhalten eines bestimmten Objekts beobachten. Beispielsweise möchten Sie ein Objekt nachverfolgen, auf das eine lokale Variable verweist, nachdem diese Variable den Gültigkeitsbereich verlassen hat. In C# und Visual Basic können Sie Objekt-IDs für bestimmte Instanzen von Verweistypen erstellen und diese im Fenster **Überwachen** und in Haltepunktbedingungen verwenden. Die Objekt-ID wird von den Debugdiensten der CLR (Common Language Runtime) generiert und dem Objekt zugeordnet.

> [!NOTE]
> Objekt-IDs erstellen schwache Verweise, die nicht verhindern, dass das Objekt in die Garbage Collection aufgenommen wird. Sie gelten nur für die aktuelle Debugsitzung.

Im folgenden Code erstellt die `MakePerson()`-Methode eine `Person` anhand einer lokalen Variable:

```csharp
class Person
{
    public Person(string name)
    {
        Name = name;
    }
    public string Name { get; set; }
}

public class Program
{
    static List<Person> _people = new List<Person>();
    public static void Main(string[] args)
    {
        MakePerson();
        DoSomething();
    }

    private static void MakePerson()
    {
        var p = new Person("Bob");
        _people.Add(p);
    }

    private static void DoSomething()
    {
        // more processing
         Console.WriteLine("done");
    }
}
```

Um den Namen von `Person` in der `DoSomething()`-Methode zu ermitteln, können Sie im Fenster **Überwachen** einen Verweis auf die Objekt-ID von `Person` hinzufügen.

1. Legen Sie im Code nach der Erstellung des `Person`-Objekts einen Haltepunkt fest.

1. Beginnen Sie mit dem Debuggen.

1. Wenn die Ausführung am Haltepunkt angehalten wird, öffnen Sie das Fenster **Lokal**. Dazu wählen Sie **Debuggen** > **Fenster** > **Lokal** aus.

1. Klicken Sie im Fenster **Lokal** mit der rechten Maustaste auf die Variable `Person`, und wählen Sie dann **Objekt-ID erstellen** aus.

   Es sollte ein Dollarzeichen ( **$** ) mit einer Nummer im Fenster **Lokal** angezeigt werden. Dies ist die Objekt-ID.

1. Fügen Sie die Objekt-ID dem Fenster **Überwachen** hinzu, indem Sie mit der rechten Maustaste auf die Objekt-ID klicken und **Überwachung hinzufügen** auswählen.

1. Legen Sie einen anderen Haltepunkt in der `DoSomething()`-Methode fest.

1. Debuggen fortsetzen. Wenn die Ausführung in der `DoSomething()`-Methode anhält, wird im Fenster **Überwachen** das `Person`-Objekt angezeigt.

   > [!NOTE]
   > Wenn Sie die Eigenschaften des Objekts anzeigen möchten (z. B. `Person.Name`), müssen Sie die Eigenschaftenauswertung aktivieren. Dazu wählen Sie **Extras** > **Optionen** > **Debuggen** > **Allgemein** > **Eigenschaftenauswertung und andere implizite Funktionsaufrufe zulassen** aus.

## <a name="dynamic-view-and-the-watch-window"></a>Dynamische Ansicht und das Überwachungsfenster

Einige Skriptsprachen (z. B. JavaScript oder Python) verwenden eine dynamische Typzuweisung oder das [Duck-Typing](https://en.wikipedia.org/wiki/Duck_typing), und .NET-Sprachen ab Version 4.0 unterstützen Objekte, die in den normalen Debugfenstern nur schwer beobachtet werden können.

Im Fenster **Überwachen** werden diese Objekte als dynamische Objekte angezeigt, die aus Typen erstellt werden, die die <xref:System.Dynamic.IDynamicMetaObjectProvider>-Schnittstelle implementieren. Knoten für dynamische Objekte zeigen die dynamischen Member der dynamischen Objekte an, ermöglichen jedoch keine Bearbeitung der Memberwerte.

Um Werte im Fenster **Dynamische Ansicht** zu aktualisieren, wählen Sie das [Aktualisierungssymbol](#bkmk_refreshWatch) neben dem Knoten für dynamische Objekte aus.

Wenn Sie nur das Fenster **Dynamische Ansicht** für ein Objekt anzeigen möchten, fügen Sie einen **dynamic**-Formatspezifizierer hinter dem Namen des dynamischen Objekts im Fenster **Überwachen** hinzu:

- Für C#: `ObjectName, dynamic`
- Für Visual Basic: `$dynamic, ObjectName`

>[!NOTE]
>- Der C#-Debugger wertet die Werte im Fenster **Dynamische Ansicht** nicht automatisch erneut aus, wenn Sie zur nächsten Codezeile wechseln.
>- Der Visual Basic-Debugger führt automatisch eine Aktualisierung für Ausdrücke durch, die über das Fenster **Dynamische Ansicht** hinzugefügt werden.
>- Wenn Sie die Member einer **dynamischen Ansicht** auswerten, kann das zu [Nebenwirkungen](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)) führen.

**Führen Sie die folgenden Schritte aus, um eine neue Überwachungsvariable einzufügen, die ein Objekt in ein dynamisches Objekt umwandelt:**

1. Klicken Sie mit der rechten Maustaste auf ein untergeordnetes Element einer **dynamischen Ansicht**.
1. Wählen Sie **Überwachung hinzufügen** aus. `object.name` wird zu `((dynamic) object).name` und in einem neuen **Überwachen**-Fenster angezeigt.

Der Debugger fügt außerdem dem Fenster **Auto** einen untergeordneten Knoten **Dynamische Ansicht** des Objekts hinzu. Um das Fenster **Auto** zu öffnen, wählen Sie während des Debuggens die Option **Debuggen** > **Fenster** > **Auto** aus.

Die **dynamische Ansicht** verbessert auch das Debuggen für COM-Objekte. Wenn der Debugger ein in **System.__ComObject** umschlossenes COM-Objekt erreicht, fügt er einen Knoten **Dynamische Ansicht** für das Objekt hinzu.

## <a name="observe-a-single-variable-or-expression-with-quickwatch"></a>Beobachten einer einzelnen Variablen oder eines Ausdrucks mit der Schnellüberwachung

Sie können die **Schnellüberwachung** zum Beobachten einer einzelnen Variablen verwenden.

Sehen Sie sich beispielsweise den folgenden Code an:

```csharp
static void Main(string[] args)
{
    int a, b;
    a = 1;
    b = 2;
    for (int i = 0; i < 10; i++)
    {
        a = a + b;
    }
}
```

Zum Beobachten der Variablen `a` gehen Sie folgendermaßen vor:

1. Legen Sie einen Haltepunkt in der Zeile `a = a + b;` fest.

1. Beginnen Sie mit dem Debuggen. Die Ausführung wird am Haltepunkt angehalten.

1. Wählen Sie die Variable `a` im Code aus.

1. Wählen Sie **Debuggen** > **Schnellüberwachung** aus, drücken Sie **UMSCHALT**+**F9**, oder klicken Sie mit der rechten Maustaste, und wählen Sie **Schnellüberwachung** aus.

   Das Dialogfeld **Schnellüberwachung** wird angezeigt. Die Variable `a` befindet sich im Feld **Ausdruck** und weist als **Wert** die Zahl **1** auf.

   ![Variable der Schnellüberwachung](../debugger/media/quickwatchvariable.png "Variable der Schnellüberwachung")

1. Wenn Sie einen Ausdruck mithilfe der Variablen auswerten möchten, geben Sie einen Ausdruck wie `a + b` in das Feld **Ausdruck** ein, und wählen Sie **Neu auswerten** aus.

   ![Ausdruck der Schnellüberwachung](../debugger/media/quickwatchexpression.png "Ausdruck der Schnellüberwachung")

1. Wenn Sie die Variable oder den Ausdruck aus **Schnellüberwachung** dem Fenster **Überwachen** hinzufügen möchten, wählen Sie **Überwachung hinzufügen** aus.

1. Wählen Sie **Schließen** aus, um das Fenster **Schnellüberwachung** zu schließen. (**Schnellüberwachung** ist ein modales Dialogfeld, d. h., Sie können den Debugvorgang nicht fortsetzen, solange es geöffnet ist.)

1. Debuggen fortsetzen. Sie können die Variable im Fenster **Überwachen** beobachten.

## <a name="see-also"></a>Siehe auch
- [Was bedeutet „Debuggen“?](../debugger/what-is-debugging.md)
- [Debugging techniques and tools (Debugverfahren und -tools)](../debugger/write-better-code-with-visual-studio.md)
- [Ein erster Blick auf den Visual Studio-Debugger](../debugger/debugger-feature-tour.md)
- [Debuggerfenster](../debugger/debugger-windows.md)
