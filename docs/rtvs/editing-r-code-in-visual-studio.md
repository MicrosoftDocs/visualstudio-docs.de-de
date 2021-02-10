---
title: Bearbeiten von R-Code
description: Visual Studio stellt eine speziell auf R zugeschnittene Bearbeitungsoberfläche bereit und behält zugleich alle Features und die Möglichkeit zum Verwenden von Erweiterungen bei.
ms.date: 11/05/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 4aea7f5371dc425a77e10b64a9389571b06f80b4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885858"
---
# <a name="edit-r-code-in-visual-studio"></a>Bearbeiten von R-Code in Visual Studio

R Tools für Visual Studio (RTVS) schneidet das Bearbeiten in Visual Studio speziell auf R zu, ohne dass Funktionen oder der Einsatz von Erweiterungen eingeschränkt werden. (Wenn Sie z.B. Vim-Schlüsselbindungen bevorzugen, können Sie die kostenlose [VsVim-Erweiterung](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim) aus dem Visual Studio Marketplace herunterladen.)

Über die in diesem Artikel behandelten Features hinaus stehen außerdem [IntelliSense](r-intellisense.md), [Linting](linting-r-code.md), [Codeausschnitte](code-snippets-for-r.md) und [R-Markdown](rmarkdown-with-r-in-visual-studio.md) zur Verfügung.

## <a name="syntax-highlighting"></a>Syntaxhervorhebung

Sie können mit RTVS Teile Ihres Codes (z.B. Zeichenfolgen, Kommentare und Schlüsselwörter) nicht nur farblich hervorheben, sondern auch Links in Kommentaren:

![Farben für Syntax für R-Code](media/editing-syntax-colors.png)

Wenn Sie Schriftarten und bestimmte Hervorhebungsfarben anpassen möchten, klicken Sie auf den Befehl **Extras** > **Optionen**, navigieren Sie zu **Umgebung** > **Schriftarten und Farben**, und ändern Sie dort im Feld **Elemente anzeigen** die Einstellungen für Elemente, die mit R-Code in Verbindung stehen:

![Optionen für Schriftarten und Farben für R-Code](media/editing-syntax-colors-options.png)

Außerdem unterstreicht Visual Studio Syntaxfehler im Editor:

![Hervorheben von Syntaxfehlern in R-Code](media/editing-syntax-error.png)

Navigieren Sie unter [Editor-Optionen](#editor-options) zur Einstellung **Erweitert** > **Syntaxüberprüfung**, um dieses Verhalten zu ändern.

## <a name="edit-and-organize-code"></a>Bearbeiten und Organisieren von Code

Bei der Codeeingabe stellt RTVS die automatische Vervollständigung bereit, wie Sie auf der [IntelliSense](r-intellisense.md) nachlesen können. Außerdem nimmt es automatische Formatierungen vor, wie etwa das Schließen von Klammern:

![Animation der Inlineformatierung](media/editing-inline-formatting.gif)

Wenn Sie Aufrufe von Funktionen eingeben, die über viele Parameter verfügen, sollten Sie die Parameter aufreihen, damit der Code leichter lesbar ist. RTVS erinnert sich an den Einzug Ihres Satzes von Parametern und wendet diesen Einzug auf alle folgenden Zeilen an:

![Animation des automatischer Einzugs](media/editing-auto-indentation.gif)

Um dieses Verhalten zu ändern, schauen Sie sich die [Editor-Optionen](#editor-options) für die Gruppe **Tabs** an.

Mit reduzierbaren Codebereichen können Sie Teile des Codes im Editor für eine gewisse Zeit ausblenden. Visual Studio erstellt automatisch verschiedene Bereiche für Sie, genauso wie für Anweisungen mit mehreren Zeilen, es sei denn, die Option **Erweitert** > **Gliederung** > **Codegliederung** ist deaktiviert.

Um selbst einen Bereich zu erstellen, umschließen Sie den gewünschte Code mit Kommentaren, die auf `---` enden. Mit den kleinen Steuerelementen „+/-“ links vom Code können Sie dann den Bereich erweitern bzw. reduzieren:

![Erstellen eines reduzierbaren Bereichs mithilfe von Kommentaren](media/editing-collapsible-regions.gif)

Visual Studio fügt standardmäßig Leerzeichen ein, wenn Sie die **TAB-TASTE** drücken. Wie Sie dieses Verhalten ändern, wird in [Options, Text Editor, Tabs (Optionen, Text-Editor, Registerkarten)](../ide/reference/options-text-editor-all-languages.md) beschrieben.

## <a name="code-navigation"></a>Codenavigation

Mit der Codenavigation können Sie schnell auf den Quellcode Ihres R-Programm und dessen Bibliotheken zugreifen. Diese Funktionen tragen dazu bei, dass Sie im Arbeitsfluss bleiben, ohne dass Sie Ihren Code manuell durchsuchen müssen.

Die **Gehe zu Definition** springt schnell zu einer Funktionsdefinition oder öffnet einen kleinen Inline-Editor zum Lesen des Quellcodes einer Bibliotheksfunktion. Klicken Sie einfach mit der rechten Maustaste auf die relevante Funktion, und wählen Sie **Gehe zu Definition** aus, oder zeigen Sie mit dem Cursor auf die Funktion, und drücken Sie **F12**.

Dieser Befehl öffnet ein neues Editor-Fenster, das den Quellcode für die Funktion enthält. Der Cursor ist praktischerweise direkt am Anfang der Funktionsdefinition platziert.

Die **Peek-Definition**, die über das Kontextmenü oder **ALT**+**F12** aufgerufen werden kann, fügt einen schreibgeschützten, durchscrollbaren Bereich ein, der den Quellcode der Funktion unter dem Funktionsaufruf enthält:

![Animation für die Peek-Definition](media/editing-peek-definition.gif)

## <a name="send-code-to-the-interactive-window"></a>Senden von Code an das interaktive Fenster

Viele Entwickler schreiben Code bevorzugt im Editor und senden diesen dann an das [interaktive Fenster](interactive-repl-for-r-in-visual-studio.md) zum sofortigen Testen (dies wird auch als „Lesen, Auswerten, Ausgeben“-Schleife oder REPL bezeichnet). Wenn Sie **STRG**+**EINGABETASTE** im R-Editor drücken, wird die aktuelle Zeile an das interaktive Fenster gesendet, wonach der Cursor in die nächste Zeile gesetzt wird. Somit können Sie mit **STRG**+**EINGABETASTE** effektiv aus dem Editor durch den Code navigieren.

Außerdem können Sie Code auswählen und **STRG**+**EINGABE** drücken, um den gesamten Abschnitt anzuwenden. Alternativ könne Sie auch mit der rechten Maustaste auf die Auswahl klicken und **In interaktivem Fenster ausführen** auswählen.

## <a name="format-code"></a>Formatcode

Die automatische Formatierung von Visual Studio speichert den von Ihnen geschriebenen und von Ihnen im Editor eingefügten Code, und zwar so wie durch Ihre Einstellungen vorgegeben. Sie können auch ein Element auswählen, rechtsklicken und dann **Auswahl formatieren** auswählen (**STRG**+**K**,**F**), um diese Einstellungen zu übernehmen. Wenn Sie z.B. eine Funktionsdefinition komplett in einer Zeile haben:

```R
f<-function  (a){  return(a + 1) }
```

Wenn Sie die Formatierung anwenden, wird es so bereinigt, dass es:

```R
f <- function(a) { return(a + 1) }
```

Klicken Sie auf **Bearbeiten** > **Erweitert** > **Dokument formatieren** (**STRG**+**E**,**D**), um die gesamte Codedatei neu zu formatieren.

Die automatische Formatierung ist ein anderer Vorgang, der rückgängig gemacht werden kann. Wenn Sie z.B. Code in den Editor einfügen und eine Formatierung anwenden, können Sie auf **Bearbeiten** > **Rückgängig machen** klicken oder **STRG**+**Z** drücken, um die Formatierung rückgängig zu machen. Wenn Sie dann erneut auf **Rückgängig machen** drücken, wird das Einfügen aufgehoben.

Formatierungsoptionen (einschließlich der Deaktivierung der Formatierung) werden über **Extras** > **Optionen** auf der Registerkarte **Text-Editor** > **R** > **Erweitert** festgelegt. Sie können mit dem Befehl **R Tools** > **Editor-Optionen** direkt zu dieser Seite navigieren. Alternativ können Sie auch im Editor rechtsklicken und auf **Formatierungsoptionen** klicken. Weitere Informationen finden Sie im Abschnitt [Editor-Optionen](#editor-options).

## <a name="inserting-roxygen-comments"></a>Einfügen von Roxygen-Kommentaren

RTVS bietet eine Verknüpfung zum Generieren von [Roxygen](https://cran.r-project.org/web/packages/roxygen2/index.html)-Kommentaren mit den Parameternamen einer Funktion. Geben Sie einfach `###` in einer leeren Zeile oberhalb der Funktionsdefinition ein:

![Animation des Einfügens eines Roxygen-Kommentars](media/editing-roxygen-comments.gif)

## <a name="editor-options"></a>Editor-Optionen

Editor-spezifische Optionen werden über den Befehl **Extras** > **Optionen**, das Navigieren zu **Text-Editor** > **R** oder über den Kurzbefehl **R Tools** > **Editor-Optionen** festgelegt.

Optionen auf den Registerkarten **Allgemein**, **Scrollleisten** und **Registerkarten** sind nicht für R spezifisch, sondern sind recht allgemeine Einstellungen für Visual Studio, die in allen Sprachen verfügbar sind, und die pro Sprache angewendet werden. Details finden Sie in den folgenden Artikeln:

- [Optionen, Text-Editor, Alle Sprachen](../ide/reference/options-text-editor-all-languages.md)
- [Verfolgen von Code durch Anpassen der Scrollleiste](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)
- [Optionen, Text-Editor, Registerkarten](../ide/reference/options-text-editor-all-languages-tabs.md)

Optionen auf der Registerkarte **R** > **Erweitert** sind für RTVS spezifisch:

| Gruppieren | Option | Standard | Beschreibung |
| --- | --- | --- | --- |
| Formatierung | Automatische Formatierung | Ein | Formatiert Code während der Eingabe neu. Wirkt sich nicht auf die Befehle **Auswahl formatieren** oder **Dokument formatieren** aus. |
| | Expanded braces | Aus | Platziert eine öffnende { in eine neue Zeile |
| | Beim Einfügen formatieren | Ein | Wendet die Formatierung beim Einfügen an |
| | Format scope on } | Ein | Formatiert den Bereich, nachdem eine schließende } eingegeben wurde |
| | Space after comma | Ein | Platziert ein Leerzeichen hinter Kommas |
| | Space after keyword | Ein | Platziert ein Leerzeichen hinter Schlüsselwörter wie `if`, `while` und `repeat` |
| | Space before { | Ein | Platziert ein Leerzeichen vor eine öffnende { |
| | Spaces around = | Ein | Platziert Leerzeichen vor und hinter einem Gleichzeichen |
| IntelliSense | Commit on Enter key | Aus | Übernimmt die Auswahl der automatischen Vervollständigung, wenn die **EINGABETASTE** gedrückt wird |
| | Commit on Space key | Aus | Übernimmt die Auswahl der automatischen Vervollständigung, wenn die **LEERTASTE** gedrückt wird|
| | Vervollständigungsliste beim ersten Zeichen | Ein | Zeigt eine Vervollständigungsliste bei den ersten eingegebenen Zeichen. Wenn dies deaktiviert ist, wird eine Vervollständigungsliste mit **Bearbeiten** > **IntelliSense** > **Member auflisten** angezeigt (**STRG**+**J**). |
| | Vervollständigungsliste beim Drücken der **TAB-TASTE** | Aus | Ruft eine Vervollständigungsliste auf, wenn Sie ein oder mehrere Zeichen eingeben und dann die **TAB-TASTE** drücken. |
| | Match gibt den Argumentnamen teilweise ein | Aus | Wenn Sie in einem Funktionsaufruf Argumentnamen eingeben, zeigt die Signaturhilfe eine Beschreibung der Arguments an, dass am besten passt. |
| Interaktives Fenster | Syntax-Prüfung in der R-Konsole | Aus | Wendet die Syntaxüberprüfung im interaktiven Fenster an Die Syntaxüberprüfung funktioniert bei Anweisungen mit mehreren Zeilen möglicherweise nicht ordnungsgemäß. |
| Gliedern | Code outlining | Ein | Erstellt automatisch reduzierbare Codebereiche für Bereiche mit Anweisungen mit mehreren Zeilen |
| Syntax check | Syntaxfehler anzeigen | Ein | Aktiviert die automatische Syntaxüberprüfung von Code |
