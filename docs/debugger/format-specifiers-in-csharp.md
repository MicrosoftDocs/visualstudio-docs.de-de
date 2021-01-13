---
title: Formatbezeichner im Debugger (C#) | Microsoft-Dokumentation
description: Verwenden Sie einen Formatbezeichner, um das Format zu ändern, in dem ein Wert im Überwachungsfenster angezeigt wird. Dieser Artikel bietet Details zur Verwendung.
ms.custom: SEO-VS-2020
ms.date: 11/21/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- expressions [C#], formatting values
- variables [debugger], watch variable symbols
- symbols, watch variable formatting
- QuickWatch dialog box, using format specifiers
- specifiers, watch variable format
- QuickWatch dialog box, format specifiers in C#
- specifiers
- watch variable symbols
- Watch window, format specifiers in C#
- format specifiers, debugger
- debugger, format specifiers recognized by
ms.assetid: 345c8589-5f36-4d34-a58c-e56271687dd6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a832bcee3f722cabaedcb3ac0672dbe09a4e77c4
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/24/2020
ms.locfileid: "97761211"
---
# <a name="format-specifiers-in-c-in-the-visual-studio-debugger"></a>Formatbezeichner in C# im Visual Studio-Debugger
Sie können mit Formatbezeichnern das Format ändern, in dem ein Wert im Fenster **Überwachen** angezeigt wird. Formatbezeichner können im **Direktfenster**, im Fenster **Befehl**, in [Ablaufverfolgungspunkten](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints) und in den Quellcodefenstern verwendet werden. Wenn Sie einen Ausdruck in diesen Fenstern anhalten, wird das Ergebnis in einem [DataTip](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) im angegebenen Format angezeigt.

Um einen Formatbezeichner zu verwenden, geben Sie den Variablenausdruck ein, gefolgt von einem Komma und dem entsprechenden Bezeichner.

## <a name="set-format-specifiers"></a>Festlegen von Formatbezeichnern
Wir verwenden den folgenden Beispielcode:

```csharp
{
    int my_var1 = 0x0065;
    int my_var2 = 0x0066;
    int my_var3 = 0x0067;
}
```

Fügen Sie beim Debuggen dem Fenster **Überwachung** die Variable `my_var1` hinzu, **Debuggen** > **Fenster** > **Überwachung** > **Überwachen 1**. Klicken Sie dann mit der rechten Maustaste auf die Variable, und wählen Sie **Hexadezimale Anzeige** aus. Im Fenster **Überwachung** wird jetzt der Wert 0x0065 angezeigt. Um diesen Wert als ganze Dezimalzahl und nicht als ganze Hexadezimalzahl anzuzeigen, geben Sie in der Spalte **Name** nach dem Variablennamen den Dezimalformatbezeichner **, d** ein. In der Spalte **Wert** wird jetzt **101** angezeigt.

![Screenshot: Visual Studio-Überwachungsfenster mit einer Zeile, die „my_var1, d“ mit dem Wert „101“ und dem Typ „int“ enthält](../debugger/media/watchformatcsharp.png)

::: moniker range=">= vs-2019" 

Sie können eine Liste der verfügbaren Formatbezeichner anzeigen und Formatbezeichner darin auswählen, indem Sie an den Wert im Fenster **Überwachung** ein Komma (,) anfügen. 

![FormatSpecCSharp](../debugger/media/vs-2019/format-specs-csharp.png "FormatSpecCSharp")

::: moniker-end

## <a name="format-specifiers"></a>Formatbezeichner
In der folgenden Tabelle werden die C#-Formatbezeichner für den Visual Studio-Debugger beschrieben.

|Bezeichner|Format|Ursprünglicher Wert in "Überwachen"|Anzeige|
|---------------|------------|--------------------------|--------------|
|ac|Erzwingt die Auswertung eines Ausdrucks. Dies kann nützlich sein, wenn die implizite Auswertung von Eigenschaften sowie implizite Funktionsaufrufe deaktiviert sind.|Meldung „Implizite Funktionsevaluierung durch den Benutzer deaktiviert“|\<value>|
|T|Ganze Dezimalzahl|0x0065|101|
|dynamic|Zeigt das angegebene Objekt mit einer dynamischen Ansicht an.|Zeigt alle Member des Objekts einschließlich der dynamischen Ansicht an.|Zeigt nur die dynamische Ansicht an.|
|h|Ganze Hexadezimalzahl|61541|0x0000F065|
|nq|Zeichenfolge ohne Anführungszeichen|"Meine Zeichenfolge"|Meine Zeichenfolge|
|nse|Gibt das Verhalten an, nicht das Format. Wertet den Ausdruck ohne Nebeneffekte aus. Wenn der Ausdruck nicht interpretiert werden kann und sich nur durch eine Auswertung auflösen lässt (z. B. als Funktionsaufruf), wird stattdessen ein Fehler angezeigt.|Nicht zutreffend|Nicht zutreffend|
|hidden|Zeigt alle öffentlichen und nicht öffentlichen Member an.|Zeigt öffentliche Member an.|Zeigt alle Member an.|
|raw|Zeigt ein Element so an, wie es im Knoten für Rohdatenelemente dargestellt wird. Nur für Proxyobjekte gültig.|Wörterbuch\<T>|Rohdatenansicht von Dictionary\<T>|
|results|Wird mit einer Variablen eines Typs verwendet, durch den „IEnumerable“ oder „IEnumerable\<T>“ implementiert wird; normalerweise das Ergebnis eines Abfrageausdrucks. Zeigt nur die das Abfrageergebnis enthaltenden Member an.|Zeigt alle Member an.|Zeigt die Member an, die die Bedingungen der Abfrage erfüllen.|

## <a name="see-also"></a>Siehe auch
- [Fenster „Überwachen“ und „Schnellüberwachung“](../debugger/watch-and-quickwatch-windows.md)
- [Autos and Locals windows (Fenster „Auto“ und „Lokal“)](../debugger/autos-and-locals-windows.md)
