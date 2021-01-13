---
title: Untersuchen von Variablen über die Fenster „Auto“ und „Lokale Variablen“ | Microsoft-Dokumentation
description: Untersuchen von Variablen in den Fenstern „Auto“ und „Lokale Variablen“ während des Debuggens in Visual Studio. In den Fenstern Auto und Lokale Variablen werden Variablenwerte während des Debuggens angezeigt.
ms.custom: SEO-VS-2020, seodec18
ms.date: 10/18/2018
ms.topic: how-to
f1_keywords:
- vs.debug.autos
- vs.debug.locals
helpviewer_keywords:
- debugger, variable windows
- debugging [Visual Studio], variable windows
ms.assetid: bb6291e1-596d-4af0-9f22-5fd713d6b84b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b57c27d038193a5c73bee48814a2aa457a94b6a6
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/24/2020
ms.locfileid: "97760912"
---
# <a name="inspect-variables-in-the-autos-and-locals-windows"></a>Untersuchen von Variablen über die Fenster „Auto“ und „Lokale Variablen“

In den Fenstern **Auto** und **Lokale Variablen** werden Variablenwerte während des Debuggens angezeigt. Die Fenster sind nur während einer Debugsitzung verfügbar. Im Fenster **Auto** werden die Variablen angezeigt, die in der Nähe des aktuellen Haltepunkts verwendet werden. Im Fenster **Lokale Variablen** werden Variablen angezeigt, die im lokalen Gültigkeitsbereich definiert sind, der in der Regel aus der aktuellen Funktion oder Methode besteht.

> [!NOTE]
> Wenn Sie zum ersten Mal versuchen, Code zu debuggen, sollten Sie [Debuggen für Einsteiger](../debugger/debugging-absolute-beginners.md) sowie [Debugverfahren und -tools zum Schreiben von besserem Code](../debugger/write-better-code-with-visual-studio.md) lesen, bevor Sie diesen Artikel durchgehen.

 Das Fenster **Auto** ist für C#-, Visual Basic-, C++- und Python-Code, aber nicht für JavaScript oder F# verfügbar.

Wenn Sie das Fenster **Auto** während des Debuggens öffnen möchten, klicken Sie auf **Debuggen** > **Fenster** > **Auto**, oder drücken Sie **STRG**+**ALT**+**V** > **A**.

Wenn Sie das Fenster **Lokale Variablen** während des Debuggens öffnen möchten, klicken Sie auf **Debuggen** > **Fenster** > **Lokale Variablen**, oder drücken Sie **ALT**+**4**.

> [!NOTE]
> Dieses Thema gilt für Visual Studio unter Windows. Informationen zu Visual Studio für Mac finden Sie unter [Datenvisualisierungen](/visualstudio/mac/data-visualizations).

## <a name="use-the-autos-and-locals-windows"></a>Verwenden der Fenster „Auto“ und „Lokale Variablen“

Arrays und Objekte werden in den Fenstern **Auto** und **Lokale Variablen** als Struktursteuerelemente angezeigt. Klicken Sie auf den Pfeil links neben dem Variablennamen, damit die Ansicht erweitert wird und die Felder und Eigenschaften angezeigt werden. Dies ist ein Beispiel für ein <xref:System.IO.FileStream?displayProperty=fullName>-Objekt im Fenster **Lokale Variablen**:

![Screenshot des Fensters „Lokale Variablen“, wobei die Datei auf den Wert „System.IO.FileStream“ festgelegt ist.](../debugger/media/locals-filestream.png)

Ein roter Wert im Fenster **Lokale Variablen** oder **Auto** bedeutet, dass sich der Wert seit der letzten Auswertung geändert hat. Die Änderung kann aus einer vorherigen Debugsitzung stammen oder daran liegen, dass Sie den Wert im Fenster geändert haben.

Das Standardzahlenformat in Debuggerfenstern ist das Dezimalformat. Wenn Sie es jedoch auf das Hexadezimalformat umstellen möchten, klicken Sie mit der rechten Maustaste in das Fenster **Lokale Variablen** oder **Auto**, und wählen Sie **Hexadezimale Anzeige** aus. Die Änderung wird in allen Debuggerfenstern übernommen.

## <a name="edit-variable-values-in-the-autos-or-locals-window"></a>Bearbeiten von Variablenwerten in den Fenstern „Lokale Variablen“ oder „Auto“

Die meisten Werte in den Fenstern **Auto** und **Lokale Variablen** lassen sich bearbeiten, indem Sie darauf doppelklicken und einen neuen Wert eingeben.

Sie können Sie einen Ausdruck für einen Wert eingeben, etwa `a + b`. Der Debugger akzeptiert im die meisten gültigen Sprachausdrücke.

In nativem C++-Code müssen Sie möglicherweise den Kontext eines Variablennamens qualifizieren. Weitere Informationen finden Sie unter [Kontextoperator (C++)](../debugger/context-operator-cpp.md).

>[!CAUTION]
>Bevor Sie Änderungen an Werten und Ausdrücken vornehmen, sollten Sie die Konsequenzen genau kennen. Solche Änderungen können bspw. zu folgenden Problemen führen:
>
>- Die Auswertung bestimmter Ausdrücke kann zur Änderung des Werts einer Variablen führen oder sich auf den Programmzustand auswirken. Wird beispielsweise `var1 = ++var2` ausgewertet, wird der Wert von `var1` und `var2` geändert. Diese Ausdrücke haben sogenannte [Nebenwirkungen](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Nebenwirkungen können unerwartete Ergebnisse verursachen, wenn Sie sich ihrer Existenz nicht bewusst sind.
>
>- Das Bearbeiten von Gleitkommawerten kann aufgrund der Dezimal-zu-Binär-Konvertierung von Nachkommastellen zu geringfügigen Ungenauigkeiten führen. Auch eine scheinbar harmlose Änderung kann die Bits einer Gleitkommavariable ändern.

::: moniker range=">= vs-2019" 
## <a name="search-in-the-autos-or-locals-window"></a>Suchen im Fenster „Auto“ oder „Lokale Variablen“

Sie können mithilfe der Suchleiste oberhalb der Fenster **Auto** und **Lokale Variablen** nach Schlüsselwörtern in den Spalten „Name“, „Wert“ und „Typ“ suchen. Drücken Sie auf EINGABE, oder klicken Sie auf einen der Pfeile, um eine Suche auszuführen. Zum Abbrechen einer laufenden Suche wählen Sie das Symbol „x“ in der Suchleiste aus.

Mit den Pfeilen nach links und rechts (UMSCHALT+F3 bzw. F3) können Sie zwischen gefundenen Übereinstimmungen navigieren.

![Suche im Fenster „Lokale Variablen“](../debugger/media/ee-search-locals.png "Suche im Fenster „Lokale Variablen“")

Über das Drop-down-Menü **Tiefer suchen** am oberen Rand der Fenster **Auto** und **Lokale Variablen** können Sie die Gründlichkeit der Suche festlegen, indem Sie auswählen, in wie vielen Ebenen von geschachtelten Objekten gesucht werden soll. 

## <a name="pin-properties-in-the-autos-or-locals-window"></a>Anheften von Eigenschaften in den Fenstern „Auto“ oder „Lokale Variablen“

> [!NOTE]
> Dieses Feature wird für .NET Core 3.0 und höher unterstützt.

Mit dem Tool **Anheftbare Eigenschaften** können Sie Objekte schnell anhand ihrer Eigenschaften in den Fenstern „Auto“ und „Lokale Variablen“ überprüfen.  Zum Starten dieses Tools müssen Sie auf eine Eigenschaft zeigen und auf das daraufhin angezeigte Anheften-Symbol klicken. Sie können auch mit der rechten Maustaste auf die Eigenschaft klicken und dann im angezeigten Kontextmenü auf die Option **Member als Favorit anheften** klicken.  Dadurch wird diese Eigenschaft in der Eigenschaftenliste des Objekts an oberste Stelle gesetzt, und der Eigenschaftsname und -wert wird in der Spalte **Wert** angezeigt.  Wenn Sie eine Eigenschaft loslösen möchten, klicken Sie noch einmal auf das Anheftsymbol, oder klicken Sie im Kontextmenü auf die Option **Member als Favorit lösen**.

![Anheften von Eigenschaften im Fenstern „Lokale Variablen“](../debugger/media/basic-pin.gif "Anheften von Eigenschaften im Fenstern „Lokale Variablen“")

Sie können beim Anzeigen der Eigenschaftenliste des Objekts in den Fenstern „Auto“ und „Lokale Variablen“ auch Eigenschaftsnamen umschalten und nicht angeheftete Eigenschaften herausfiltern.  Sie können auf die einzelnen Optionen zugreifen, indem Sie in der Symbolleiste oberhalb der Fenster „Auto“ und „Lokale Variablen“ auf die Schaltflächen klicken.

![Filter für als Favorit markierte Eigenschaften](../debugger/media/filter-pinned-properties-locals.png "Filter für als Favorit markierte Eigenschaften")
![Eigenschaftsnamen umschalten](../debugger/media/toggle-property-names.gif "Eigenschaftsnamen umschalten")

::: moniker-end

## <a name="change-the-context-for-the-autos-or-locals-window"></a>Ändern des Kontexts für das Fenster „Auto“ oder „Lokale Variablen“

Mithilfe der Symbolleiste **Debugspeicherort** können Sie eine gewünschte Funktion oder einen gewünschten Thread oder Prozess auswählen, der den Kontext für die Fenster **Auto** und **Lokale Variablen** ändert.

Die Symbolleiste **Debugspeicherort** wird aktiviert, indem Sie auf den leeren Teil des Symbolleistenbereich klicken und **Debugspeicherort** aus dem Drop-down-Menü auswählen oder auf **Ansicht** > **Symbolleisten** > **Debugspeicherort** klicken.

Legen Sie einen Haltepunkt fest, und starten Sie das Debuggen. Wenn der Debugger am Haltepunkt ankommt, wird die Ausführung angehalten. Die genaue Stelle im Code wird in der Symbolleiste **Debugspeicherort** angezeigt.

![Symbolleiste „Debugspeicherort“](../debugger/media/debuglocationtoolbar.png "Symbolleiste „Debugspeicherort“")

## <a name="variables-in-the-autos-window-c-c-visual-basic-python"></a><a name="bkmk_whatvariables"></a> Variablen im Fenster „Auto“ (C#, C++, Visual Basic, Python)

Je nach Codesprache werden verschiedene Variablen im Fenster **Auto** angezeigt.

- In C# und Visual Basic wird im Fenster **Auto** jede Variable angezeigt, die in der aktuellen oder vorherigen Zeile verwendet wird. In C#- oder Visual Basic-Code deklarieren Sie z. B. die folgenden vier Variablen:

   ```csharp
       public static void Main()
       {
          int a, b, c, d;
          a = 1;
          b = 2;
          c = 3;
          d = 4;
       }
   ```

   Legen Sie den Haltepunkt auf die Zeile `c = 3;` fest, und starten Sie den Debugger. Wenn die Ausführung angehalten wird, wird Folgendes im Fenster **Auto** angezeigt:

   ![Screenshot des Fensters „Auto“ mit auf 0 festgelegtem Wert „c“.](../debugger/media/autos-csharp.png)

   `c` hat den Wert 0 (Null), weil die Zeile `c = 3` noch nicht ausgeführt wurde.

- In C++ werden im Fenster **Auto** die Variablen angezeigt, die in den letzten drei Zeilen vor der Zeile verwendet wurden, in der die Ausführung angehalten wurde. In C++-Code deklarieren Sie z. B. sechs Variablen:

   ```C++
       void main() {
           int a, b, c, d, e, f;
           a = 1;
           b = 2;
           c = 3;
           d = 4;
           e = 5;
           f = 6;
       }
   ```

    Legen Sie den Haltepunkt auf die Zeile `e = 5;` fest, und führen Sie den Debugger aus. Wenn die Ausführung beendet wird, wird Folgendes im Fenster **Auto** angezeigt:

    ![Screenshot des Fensters „Auto“, in dem die Zeile hervorgehoben ist, die den ganzzahligen Wert „c“ (int) mit einem Wert von 3 anzeigt.](../debugger/media/autos-cplus.png)

    Die Variable `e` wurde deinitialisiert. Dies liegt daran, dass die Zeile `e = 5` noch nicht ausgeführt wurde.

## <a name="view-return-values-of-method-calls"></a><a name="bkmk_returnValue"></a> View return values of method calls
 In .NET- und C++-Code können Sie Rückgabewerte im Fenster **Auto** untersuchen, wenn Sie in einem Methodenaufruf einen Prozedurschritt oder einen Rücksprung ausführen. Das Anzeigen der Rückgabewerte eines Methodenaufrufs kann nützlich sein, wenn die Werte nicht in lokalen Variablen gespeichert werden. Eine Methode kann als Parameter oder als Rückgabewert einer anderen Methode verwendet werden.

 Im folgenden C#-Code werden z. B. die Rückgabewerte von zwei Funktionen hinzugefügt:

```csharp
static void Main(string[] args)
{
    int a, b, c, d;
    a = 1;
    b = 2;
    c = 3;
    d = 4;
    int x = sumVars(a, b) + subtractVars(c, d);
}

private static int sumVars(int i, int j)
{
    return i + j;
}

private static int subtractVars(int i, int j)
{
    return j - i;
}
```

So lassen Sie die Rückgabewerte der Methodenaufrufe `sumVars()` und `subtractVars()` im Fenster „Auto“ anzeigen:

1. Legen Sie einen Haltepunkt in der Zeile `int x = sumVars(a, b) + subtractVars(c, d);` fest.

1. Starten Sie das Debuggen, und klicken Sie auf **Prozedurschritt**, oder drücken Sie **F10**, wenn die Ausführung am Haltepunkt angehalten wird. Daraufhin sollten folgende Rückgabewerte im Fenster **Auto** angezeigt werden:

  ![Auto, Rückgabewert C#](../debugger/media/autosreturnvaluecsharp2.png "Auto, Rückgabewert C#")

## <a name="see-also"></a>Siehe auch

- [Was bedeutet „Debuggen“?](../debugger/what-is-debugging.md)
- [Debugging techniques and tools (Debugverfahren und -tools)](../debugger/write-better-code-with-visual-studio.md)
- [Ein erster Blick auf den Visual Studio-Debugger](../debugger/debugger-feature-tour.md)
- [Debuggerfenster](../debugger/debugger-windows.md)
