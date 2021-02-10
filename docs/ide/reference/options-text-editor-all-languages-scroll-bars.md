---
title: Optionen, Text-Editor, Alle Sprachen, Scrollleisten
description: Hier erfahren Sie, wie Sie mit der Seite „Scrollleisten“ im Abschnitt „Alle Sprachen“ das Standardverhalten der Scrollleisten des Code-Editors in Visual Studio ändern.
ms.custom: SEO-VS-2020
ms.date: 10/25/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.All_Languages.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.Basic.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.CSharp.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.CoffeeScript.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.CSS.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.Dockerfile.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.F%2523.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.HQL.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.HTML.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.HTMLX.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.JavaScript.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.TypeScript.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.JSON.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.LESS.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.ResJSON.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.SCSS.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.SQL_Server_Tools.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.StreamAnalytics.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.U-SQL.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.XAML.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.XML.ScrollBars
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c9f9b53807d0ae2160798f29b98fa315c43c330c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841970"
---
# <a name="options-text-editor-all-languages-scroll-bars"></a>Optionen, Text-Editor, Alle Sprachen, Scrollleisten
Mit diesem Dialogfeld können Sie das Standardverhalten der Scrollleiste des Code-Editors ändern. Wählen Sie zum Anzeigen dieser Optionen unter **Tools** den Menüpunkt **Optionen** aus. Erweitern Sie innerhalb des Ordners **Text-Editor** den Unterordner **Alle Sprachen**, und wählen Sie dann **Scrollleisten** aus.

> [!CAUTION]
> Auf dieser Seite werden die Standardoptionen für alle Entwicklungssprachen festgelegt. Beim Zurücksetzen einer Option in diesem Dialogfeld werden die Optionen für Scrollleisten in allen Sprachen auf die hier ausgewählten Optionen zurückgesetzt. Um die Optionen in „Text-Editor“ für nur eine Sprache zu ändern, erweitern Sie den Unterordner für diese Sprache, und wählen Sie seine Optionsseiten aus.

## <a name="show-horizontal-scroll-bar"></a>Horizontale Scrollleiste anzeigen

Wenn diese Option aktiviert ist, wird eine horizontale Scrollleiste angezeigt, mit der Sie von Seite zu Seite scrollen können, um Elemente anzuzeigen, die außerhalb des Anzeigebereichs des Editors liegen. Wenn keine horizontalen Scrollleisten verfügbar sind, können Sie die Cursortasten verwenden.

## <a name="show-vertical-scroll-bar"></a>Vertikale Scrollleiste anzeigen

Wenn diese Option aktiviert ist, wird eine vertikale Scrollleiste angezeigt, mit der Sie nach oben und nach unten scrollen können, um Elemente anzuzeigen, die außerhalb des Anzeigebereichs des Editors liegen. Wenn keine vertikalen Scrollleisten verfügbar sind, können Sie die BILD-AUF- oder BILD-AB-Taste oder Cursortasten verwenden.

## <a name="display"></a>Anzeige

### <a name="show-annotations-over-vertical-scroll-bar"></a>Anmerkungen über vertikaler Scrollleiste anzeigen

Wählen Sie aus, ob die vertikale Scrollleiste die folgenden Anmerkungen anzeigen soll:

- Änderungen
- Markierungen
- Fehler
- Position der Einfügemarke

> [!TIP]
> Die Option **Markierungen anzeigen** umfasst Haltepunkte und Lesezeichen.

Probieren Sie es aus, indem Sie eine umfangreiche Codedatei öffnen und Text ersetzen, der an mehreren Stellen in der Datei vorkommt. Die Bildlaufleiste zeigt die Auswirkungen der Ersetzungen an. Sie können also Änderungen rückgängig machen, wenn ein Element nicht ersetzt werden soll.

Informationen zur Bedeutung der verschiedenen Farben und Symbole beim Bearbeiten von Code finden Sie in unserem Blogbeitrag [Verbesserte Scrollleiste](/archive/blogs/cdnstudents/visual-studio-tips-and-tricks-enhanced-scroll-bar).

## <a name="behavior"></a>Verhalten

Die Scrollleiste verfügt über zwei Modi: den Leistenmodus und den Zuordnungsmodus.

### <a name="use-bar-mode-for-vertical-scroll-bar"></a>Leistenmodus für vertikale Scrollleiste verwenden

Im *Leistenmodus* werden Anmerkungsindikatoren auf der Scrollleiste angezeigt. Wenn Sie auf die Scrollleiste klicken, wird die Seite nach oben oder unten gescrollt, der Cursor springt aber nicht an die entsprechende Stelle in der Datei.

### <a name="use-map-mode-for-vertical-scroll-bar"></a>Zuordnungsmodus für vertikale Scrollleiste verwenden

Wenn Sie im *Zuordnungsmodus* auf eine Position in der Scrollleiste klicken, springt der Cursor zu dieser Position in der Datei, anstatt nur eine Seite nach oben oder unten zu scrollen. Codezeilen werden als Miniaturbild auf der Scrollleiste angezeigt. Sie können auswählen, wie breit die Zuordnungsspalte ist, indem Sie einen Wert in **Quellübersicht** auswählen. Um eine größere Vorschau des Codes zu aktivieren, wenn Sie den Mauszeiger auf der Zuordnung positionieren, wählen Sie die Option **Vorschau-QuickInfo anzeigen** aus. Zugeklappte Bereiche werden anders schattiert und durch einen Doppelklick aufgeklappt.

> [!TIP]
> Sie können die Miniaturcodeansicht im Zuordnungsmodus deaktivieren, indem Sie **Quellübersicht** auf **Aus** festlegen. Wenn **Vorschau-QuickInfo anzeigen** ausgewählt ist, sehen Sie immer noch eine Vorschau des Codes an dieser Stelle, wenn Sie den Mauszeiger auf der Scrollleiste positionieren, und der Mauszeiger springt immer noch zu dieser Stelle in der Datei, wenn Sie klicken.

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: Anpassen der Scrollleiste](../how-to-track-your-code-by-customizing-the-scrollbar.md)