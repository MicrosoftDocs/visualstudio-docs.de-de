---
title: Auto-und lokale Fenster | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.autos
- vs.debug.locals
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- debugger, variable windows
- debugging [Visual Studio], variable windows
ms.assetid: bb6291e1-596d-4af0-9f22-5fd713d6b84b
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 261c0c0bd8b48634c8d24d56ee4df7ea3bbcf135
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161735"
---
# <a name="autos-and-locals-windows"></a>Fenster „Auto“ und „Lokal“
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das Fenster **Auto** (beim Debuggen, **STRG + ALT + V, A**oder **Debuggen / Fenster / Auto**) und das Fenster **Lokal** (beim Debuggen, **STRG + ALT + V, L**, oder **Debuggen / Fenster / Lokal**) sind hilfreich, wenn Sie beim Debuggen Variablenwerte sehen möchten. Im Fenster **Lokal** werden die Variablen angezeigt, die im lokalen Gültigkeitsbereich definiert sind, der in der Regel der Funktion oder Methode entspricht, die derzeit ausgeführt wird. Im Fenster **Auto** werden Variablen angezeigt, die in der Nähe der aktuellen Zeile (die Stelle, an der der Debugger angehalten wurde) verwendet werden. Welche Variablen genau angezeigt werden, unterscheidet sich in verschiedenen Sprachen. Weitere Informationen finden im folgenden Abschnitt What variables appear in the Autos Window? weiter unten.  
  
 Weitere Informationen zum grundlegenden Debuggen finden Sie unter [Getting Started with the Debugger](../debugger/getting-started-with-the-debugger.md).  
  
## <a name="looking-at-objects-in-the-autos-and-locals-windows"></a>Betrachten von Objekten in den Fenstern „Auto“ und „Lokal“  
 Arrays und Objekte werden in den Fenstern „Auto“ und „Lokal“ als Struktursteuerelemente angezeigt. Klicken Sie auf den Pfeil links neben dem Variablennamen, damit die Ansicht erweitert wird, sodass m die Felder und Eigenschaften angezeigt werden. Dies ist ein Beispiel für ein <xref:System.IO.FileStream>-Objekt im Fenster **Lokale Variablen**:  
  
 ![Lokale&#45;FILESTREAM](../debugger/media/locals-filestream.png "Lokale Variablen, FileStream")  
  
## <a name="what-variables-appear-in-the-autos-window"></a>Welche Variablen werden im Fenster „Auto“ angezeigt?  
 Sie können das Fenster **Auto** für C#-, Visual Basic- und C++-Code verwenden. Das Fenster **Auto** unterstützt weder JavaScript noch F#-.  
  
 In c# und Visual Basic zeigt das Fenster Auto alle Variablen an **, die in** der aktuellen oder vorherigen Zeile verwendet werden. Angenommen, Sie deklarieren vier Variablen und legen diese wie folgt fest:  
  
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
  
 Wenn Sie einen Haltepunkt in der Zeile `c = 3`festgelegt haben und den Debugger ausführen, sieht das Fenster **Auto** wie folgt aus, wenn die Ausführung angehalten wird:  
  
 ![Auto&#45;CSharp](../debugger/media/autos-csharp.png "Auto, C#")  
  
 `c` hat den Wert 0, weil die Zeile `c = 3` noch nicht ausgeführt wurde.  
  
 In C++ werden im Fenster **Auto** die Variablen angezeigt, die in den letzten drei Zeilen vor der aktuellen Zeile (die Zeile, in der die Ausführung angehalten wurde) verwendet werden. Angenommen, Sie deklarieren sechs Variablen:  
  
```cpp  
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
  
 Wenn Sie einen Haltepunkt in der Zeile `e = 5;` festgelegt haben und den Debugger ausführen, sieht das Fenster **Auto** wie folgt aus, wenn die Ausführung angehalten wird:  
  
 ![Auto&#45;CPLUS](../debugger/media/autos-cplus.png "Autos-Cplus")  
  
 Sie sehen, dass die Variable „e“ nicht initialisiert ist. Dies liegt daran, dass der Code in der Zeile `e = 5;` noch nicht ausgeführt wurde.  
  
 In bestimmten Fällen können Sie auch die Rückgabewerte von Funktionen und Methoden sehen. Weitere Informationen finden im folgenden Abschnitt [View return values of method calls](#bkmk_returnValue) .  
  
## <a name="view-return-values-of-method-calls"></a><a name="bkmk_returnValue"></a> View return values of method calls  
 In .NET- und C++-Code können Sie Rückgabewerte auswerten, wenn Sie einen Methodenaufruf als Prozedurschritt oder bis zum Rücksprung ausführen. Diese Funktion ist nützlich, wenn das Ergebnis eines Methodenaufrufs nicht in einer lokalen Variablen gespeichert wird, etwa wenn eine Methode als Parameter oder Rückgabewert einer anderen Methode verwendet wird.  
  
 Im folgenden C#-Code werden die Rückgabewerte von zwei Funktionen hinzugefügt:  
  
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
  
 Legen Sie einen Haltepunkt in der Zeile int `x = sumVars(a, b) + subtractVars(c, d);` fest.  
  
 Starten Sie das Debuggen, und drücken Sie **F10 (Prozedurschritt)**, wenn die Ausführung am ersten Haltepunkt angehalten wird. Daraufhin sollte Folgendes im Fenster **Auto** zu sehen sein:  
  
 ![AutosReturnValueCSharp2](../debugger/media/autosreturnvaluecsharp2.png "AutosReturnValueCSharp2")  
  
## <a name="why-are-variable-values-sometimes-red-in-locals-and-autos-windows"></a>Warum sind Variablenwerte im Fenster „Lokal“ oder „Auto“ manchmal rot?  
 Gelegentlich stellen Sie fest, dass der Wert einer Variablen im Fenster **Lokal** oder **Auto** rot angezeigt wird. Dies ist ein Variablenwert, der seit der letzten Auswertung geändert wurde. Die Änderung kann aus einer vorherigen Debugsitzung stammen oder daran liegen, dass der Wert im Fenster geändert wurde.  
  
## <a name="changing-the-numeric-format-of-a-variable-window"></a>Ändern des numerischen Formats eines Variablenfensters  
 Das standardmäßige numerische Format ist das Dezimalformat, Sie können dies aber in das Hexadezimalformat ändern. Klicken Sie mit der rechten Maustaste im Fenster **Lokal** oder **Auto** , und wählen Sie **Hexadezimale Anzeige**aus. Die Änderung wirkt sich auf alle Debuggerfenster aus.  
  
## <a name="editing-a-value-in-a-variable-window"></a>Bearbeiten eines Werts in einem Variablenfenster  
 Sie können die Werte der meisten Variablen bearbeiten, die in den Fenstern **Auto**, **Lokal**, **Überwachen**und **Schnellüberwachung** angezeigt werden. Informationen zu den Fenstern **Überwachen** und **Schnellüberwachung** finden Sie unter [Watch and QuickWatch Windows](../debugger/watch-and-quickwatch-windows.md). Doppelklicken Sie einfach auf den Wert, den Sie ändern möchten, und fügen Sie den neuen Wert hinzu.  
  
 Sie können Sie einen Ausdruck für einen Wert eingeben, etwa `a + b`. Der Debugger akzeptiert im die meisten gültigen Sprachausdrücke.  
  
 In nativem C++-Code müssen Sie möglicherweise den Kontext eines Variablennamens qualifizieren. Weitere Informationen finden Sie unter [context-Operator (C++)](../debugger/context-operator-cpp.md).  
  
 Allerdings sollten Sie Vorsicht walten lassen, wenn Sie Werte ändern. Mögliche Probleme:  
  
- Die Auswertung bestimmter Ausdrücke kann zur Änderung des Werts einer Variablen führen oder sich auf den Programmzustand auswirken. Wird beispielsweise `var1 = ++var2` ausgewertet, wird der Wert von `var1` und `var2`geändert.  
  
     Ausdrücke, die eine Änderung von Daten bewirken, haben [Nebeneffekte](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)), die zu unerwarteten Ergebnissen führen können, wenn Sie sich der Effekte nicht bewusst sind. Vergewissern Sie sich, dass Sie die Folgen einer solchen Änderung kennen, bevor Sie sie vornehmen.  
  
- Das Bearbeiten von Gleitkommawerten kann aufgrund der Dezimal-zu-Binär-Konvertierung von Nachkommastellen zu geringfügigen Ungenauigkeiten führen. Auch eine scheinbar harmlose Bearbeitung kann Änderungen in einigen der unwichtigsten Bits einer Gleitkommavariable bewirken.  
  
## <a name="debug-location-toolbar"></a>Symbolleiste „Debugspeicherort“  
 Sie können die Symbolleiste **Debugspeicherort** verwenden, um die gewünschte Funktion, den gewünschten Thread oder den gewünschten Prozess auszuwählen. Legen Sie einen Haltepunkt fest, und starten Sie das Debuggen. (Wenn diese Symbolleiste nicht angezeigt wird, können Sie sie aktivieren, indem Sie auf einen leeren Bereich der Symbolleiste klicken. Sie sollten die Liste der Symbolleisten sehen. Wählen Sie **Debugspeicherort**aus.) Wenn der Haltepunkt erreicht ist, wird die Ausführung angehalten, und Sie können die Symbolleiste „Debugspeicherort“ sehen, die die unterste Zeile in der folgenden Grafik ist:  
  
 ![DebugLocationToolbar](../debugger/media/debuglocationtoolbar.png "DebugLocationToolbar")  
  
 Sie können den Kontext auch zu anderen Funktionsaufrufen, Threads oder Prozessen wechseln, indem Sie im Fenster **Aufrufliste** , **Threads** oder **Prozesse** auf das Element doppelklicken.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Debuggerfenster](../debugger/debugger-windows.md)
