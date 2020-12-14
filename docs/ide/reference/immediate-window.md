---
title: Direktfenster
description: Hier erfahren Sie mehr über die Verwendung des Direktfensters zum Debuggen und Auswerten von Ausdrücken, Ausführen von Anweisungen und Ausgeben von Variablenwerten.
ms.custom: SEO-VS-2020
ms.date: 02/25/2019
ms.topic: reference
dev_langs:
- VB
f1_keywords:
- VS.ImmediateWindow
helpviewer_keywords:
- design-time expression evaluation
- Immediate window
- first-chance exception notifications
ms.assetid: d33e7937-73f3-4c69-9df0-777a8713c6f2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 342a2a34528134ed1174058b6701c77c9217fc63
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617018"
---
# <a name="immediate-window"></a>Direktfenster

Das **Direktfenster** wird zum Debuggen und Auswerten von Ausdrücken, Ausführen von Anweisungen und Ausgeben von Variablenwerten verwendet. Mit dem **Direktfenster** werden Ausdrücke durch Erstellen und Verwenden des derzeit ausgewählten Projekts ausgewertet.

Um das Fenster **Direkt** anzuzeigen, öffnen Sie ein Projekt zur Bearbeitung und wählen dann **Debuggen** > **Windows** > **Direkt** oder drücken **STRG**+**ALT**+**I**. Alternativ können Sie auch im **Befehlsfenster****Debug.Immediate** eingeben.

Das **Direktfenster** unterstützt IntelliSense.

## <a name="display-the-values-of-variables"></a>Anzeigen der Werte von Variablen

Das **Direktfenster** ist besonders beim Debuggen einer App nützlich. Um beispielsweise den Wert der Variablen `varA` zu überprüfen, können Sie den [Print-Befehl](../../ide/reference/print-command.md) verwenden:

```cmd
>Debug.Print varA
```

Das Fragezeichen (?) ist ein Alias für `Debug.Print`, sodass dieser Befehl auch wie folgt eingegeben werden kann:

```cmd
? varA
```

Beide Versionen dieses Befehls geben den Wert der Variablen `varA` zurück.

> [!TIP]
> Wenn Sie einen Visual Studio-Befehl im Fenster **Direkt** ausgeben, müssen Sie dem Befehl ein Größer-als-Zeichen (>) voranstellen. Wechseln Sie zum [Befehlsfenster](command-window.md), wenn Sie mehrere Befehle eingeben möchten.

## <a name="design-time-expression-evaluation"></a>Ausdrucksauswertung zur Entwurfszeit

Sie können das Fenster **Direkt** verwenden, um eine Funktion oder Unterroutine zur Entwurfszeit auszuführen.

### <a name="execute-a-function-at-design-time"></a>Ausführen einer Funktion zur Entwurfszeit

1. Kopieren Sie den folgenden Code, und fügen Sie ihn in eine Visual Basic-Konsolenanwendung ein:

   ```vb
   Module Module1

       Sub Main()
           MyFunction(5)
       End Sub

       Function MyFunction(ByVal input as Integer) As Integer
           Return input * 2
       End Function

   End Module
   ```

2. Klicken Sie im Menü **Debuggen** auf **Windows** > **Direkt**.

3. Geben Sie `?MyFunction(2)` im Fenster **Direkt** ein, und drücken Sie die **EINGABETASTE**.

    Über das Fenster **Direkt** wird `MyFunction` ausgeführt und `4` angezeigt.

Wenn die Funktion oder die Unterroutine einen Breakpoint enthält, unterbricht Visual Studio die Ausführung an der entsprechenden Stelle. Sie können dann die Debuggerfenster verwenden, um den Programmzustand zu überprüfen. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Debugging at Design Time (Exemplarische Vorgehensweise: Debuggen zur Entwurfszeit)](../../debugger/walkthrough-debugging-at-design-time.md).

Die Ausdrucksauswertung zur Entwurfszeit ist nicht für Projekttypen verfügbar, die das Starten einer Ausführungsumgebung erfordern, z.B. Visual Studio-Tools für Office-Projekte, Webprojekte, Projekte für intelligente Geräte und SQL-Projekte.

### <a name="design-time-expression-evaluation-in-multi-project-solutions"></a>Ausdrucksauswertung zur Entwurfszeit in Projektmappen mit mehreren Projekten

Beim Festlegen des Kontexts für die Ausdrucksauswertung zur Entwurfszeit verweist Visual Studio auf das aktuell ausgewählte Projekt im Projektmappen-Explorer. Wenn im Projektmappen-Explorer kein Projekt ausgewählt ist, versucht Visual Studio, die Funktion anhand des Startprojekts auszuwerten. Wenn die Funktion im aktuellen Kontext nicht ausgewertet werden kann, wird eine Fehlermeldung angezeigt. Wenn Sie versuchen, eine Funktion in einem Projekt auszuwerten, das nicht das Startprojekt für die Projektmappe ist, und eine Fehlermeldung angezeigt wird, wählen Sie das Projekt im Projektmappen-Explorer aus, und wiederholen Sie die Auswertung.

## <a name="enter-commands"></a>Eingeben von Befehlen

Sie müssen das Größer-als-Zeichen (>) eingeben, wenn Sie Visual Studio-Befehle im Fenster **Direkt** angeben. Verwenden Sie die **NACH-OBEN**- und **NACH UNTEN**-TASTEN, um durch Ihre zuvor verwendeten Befehle zu scrollen.

|Aufgabe|Lösung|Beispiel|
|----------|--------------|-------------|
|Auswerten eines Ausdrucks.|Stellen Sie dem Ausdruck ein Fragezeichen (?) voran.|`? a+b`|
|Vorübergehendes Wechseln vom Direktmodus in den Befehlsmodus (zum Ausführen eines einzelnen Befehls).|Geben Sie den Befehl ein, und stellen Sie ihm ein Größer-als-Zeichen (>) voran.|`>alias`|
|Wechseln Sie zum Befehlsfenster.|Geben Sie im Fenster `cmd` ein, und stellen Sie dem Befehl ein Größer-als-Zeichen (>) voran.|`>cmd`|
|Wechseln Sie wieder zum Direktfenster.|Geben Sie in das Fenster `immed` ohne das Größer-als-Zeichen (>) ein.|`immed`|

## <a name="mark-mode"></a>Markierungsmodus

Wenn Sie im Fenster **Direkt** auf eine zuvor ausgegebene Zeile klicken, schalten Sie automatisch in den Markierungsmodus um. Auf diese Weise können Sie den Text vorheriger Befehle wie in einem beliebigen anderen Text-Editor markieren, bearbeiten, kopieren und in die aktuelle Zeile einfügen.

## <a name="examples"></a>Beispiele

Im folgenden Beispiel werden vier Ausdrücke und die dazugehörigen Ergebnisse im **Direktfenster** für ein Visual Basic-Projekt veranschaulicht.

```cmd
j = 2
Expression has been evaluated and has no value

? j
2

j = DateTime.Now.Day
Expression has been evaluated and has no value

? j
26
```

## <a name="first-chance-exception-notifications"></a>Ausnahmebenachrichtigungen (erste Chance)

Bei einigen Einstellungskonfigurationen werden Ausnahmebenachrichtigungen (erste Chance) im Fenster **Direkt** angezeigt.

### <a name="toggle-first-chance-exception-notifications-in-the-immediate-window"></a>Ein- bzw. Ausblenden von Ausnahmebenachrichtigungen (erste Chance) im Fenster „Direkt“

1. Klicken Sie im Menü **Ansicht** auf **Weitere Fenster** und dann auf **Ausgabe**.

2. Klicken Sie mit der rechten Maustaste auf den Textbereich des **Ausgabefensters**, und aktivieren bzw. deaktivieren Sie dann die Option **Ausnahmemeldungen**.

## <a name="see-also"></a>Weitere Informationen

- [Navigieren im Code mit dem Debugger](../../debugger/navigating-through-code-with-the-debugger.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Erster Einblick in den Debugger](../../debugger/debugger-feature-tour.md)
- [Exemplarische Vorgehensweise: Debuggen zur Entwurfszeit](../../debugger/walkthrough-debugging-at-design-time.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
- [Verwenden von regulären Ausdrücken in Visual Studio](../../ide/using-regular-expressions-in-visual-studio.md)
