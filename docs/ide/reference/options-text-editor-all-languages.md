---
title: Optionen, Text-Editor, Alle Sprachen
description: Hier erfahren Sie, wie Sie mithilfe der Seite „Allgemein“ im Abschnitt „Alle Sprachen“ das Standardverhalten des Code-Editors in Visual Studio ändern.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.General
- VS.ToolsOptionsPages.Text_Editor.ResJSON.General
- VS.ToolsOptionsPages.Text_Editor.All_Languages.General
- VS.ToolsOptionsPages.Text_Editor.Basic.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.General
- VS.ToolsOptionsPages.Text_Editor.C/C++.General
- VS.ToolsOptionsPages.Text_Editor.CoffeeScript.General
- VS.ToolsOptionsPages.Text_Editor.CSS.General
- VS.ToolsOptionsPages.Text_Editor.Dockerfile.General
- VS.ToolsOptionsPages.Text_Editor.F#.General
- VS.ToolsOptionsPages.Text_Editor.Fsharp.General
- VS.ToolsOptionsPages.Text_Editor.HQL.General
- VS.ToolsOptionsPages.Text_Editor.HTML.General
- VS.ToolsOptionsPages.Text_Editor.HTML_(Web_Forms).General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.General
- VS.ToolsOptionsPages.Text_Editor.JSON.General
- VS.ToolsOptionsPages.Text_Editor.LESS.General
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.General
- VS.ToolsOptionsPages.Text_Editor.SCSS.General
- VS.TOOLSOPTIONSPAGES.TEXT_EDITOR.SQL_SERVER_TOOLS.GENERAL
- VS.ToolsOptionsPages.Text_Editor.StreamAnalytics.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.General
- VS.ToolsOptionsPages.Text_Editor.U-SQL.General
- VS.ToolsOptionsPages.Text_Editor.XAML.General
- VS.ToolsOptionsPages.Text_Editor.XML.General
helpviewer_keywords:
- Text Editor Options dialog box
- statement completion
- word wrap
- General dialog box
- line numbers
- virtual space
ms.assetid: 49ee7306-9d46-4170-850f-a1716171752d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0b507f79aa4afb1bd5d2f56893d2e32aae0db4c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905574"
---
# <a name="options-dialog-box-text-editor--all-languages"></a>Dialogfeld „Optionen“: Text-Editor \> Alle Sprachen

Mit diesem Dialogfeld können Sie das Standardverhalten des Code-Editors ändern. Diese Einstellungen gelten auch für andere Editoren, die auf dem Code-Editor basieren, z.B. die Quellansicht des HTML-Designers. Um das Dialogfeld zu öffnen, klicken Sie auf **Optionen** im Menü **Tools**. Erweitern Sie innerhalb des Ordners **Text-Editor** den Unterordner **Alle Sprachen**, und klicken Sie dann auf **Allgemein**.

> [!CAUTION]
> Auf dieser Seite werden die Standardoptionen für alle Entwicklungssprachen festgelegt. Denken Sie daran, dass beim Zurücksetzen einer Option in diesem Dialogfeld die allgemeinen Optionen in allen Sprachen auf die hier ausgewählten Optionen zurückgesetzt werden. Um die Optionen in „Text-Editor“ für nur eine Sprache zu ändern, erweitern Sie den Unterordner für diese Sprache, und wählen Sie seine Optionsseiten aus.

Wenn eine Option auf der Seite der allgemeinen Optionen für manche, aber nicht alle, Programmiersprachen aktiviert wurde, wird ein ausgegrautes Häkchen angezeigt.

## <a name="statement-completion"></a>Anweisungsabschluss

**Elemente automatisch auflisten**

Wenn aktiviert, werden Popuplisten verfügbarer Member, Eigenschaften, Werte oder Methoden von IntelliSense angezeigt, während Sie eine Eingabe machen. Wählen Sie ein Element aus der Popupliste aus, um es in Ihren Code einzufügen. Wenn Sie diese Option auswählen, wird die Option **Erweiterte Member ausblenden** aktiviert

**Erweiterte Member ausblenden**

Wenn aktiviert, werden die Popuplisten zur Anweisungsvervollständigung verkürzt, da nur die am häufigsten verwendeten Elemente angezeigt werden. Die anderen Elemente werden aus der Liste gefiltert.

**Parameterinformationen**

Wenn diese Option aktiviert ist, wird die vollständige Syntax der aktuellen Deklaration oder Prozedur mit allen verfügbaren Parametern unter der Einfügemarke im Editor angezeigt. Der nächste zuweisbare Parameter ist fett hervorgehoben.

## <a name="settings"></a>Einstellungen

**Virtuellen Bereich aktivieren**

Wenn dieses Option aktiviert ist und **Zeilenumbruch** deaktiviert wurde, können Sie mit der Maus im Code-Editor auf eine beliebige Stelle nach einem Zeilenende klicken und mit der Eingabe beginnen. Diese Funktion kann verwendet werden, um Kommentare immer an derselben Stelle neben dem Code einzufügen.

**Zeilenumbruch**

Wenn aktiviert, wird der Teil einer Zeile, der über den horizontal sichtbaren Bereich des Editors hinausgeht, automatisch in der nächsten Zeile angezeigt. Wenn Sie diese Option auswählen, wird die Option **Visuelle Symbole für Zeilenumbruch** anzeigen aktiviert.

> [!NOTE]
> Die Funktion **Virtueller Bereich** ist deaktiviert, wenn **Zeilenumbruch** aktiviert ist.

**Visuelle Symbole für Zeilenumbruch anzeigen**

Wenn aktiviert, wird beim Umbruch einer langen Zeile auf eine zweite Zeile ein Indikator in Form eines Rückwärtspfeils angezeigt.

![LineBreakSymbol-Bildschirmabbildung](../../ide/reference/media/linebreak.gif)

Deaktivieren Sie diese Option, wenn Sie diese Indikatoren nicht anzeigen möchten.

> [!NOTE]
> Diese zur Erinnerung dienenden Pfeile werden weder gedruckt noch dem Code hinzugefügt. Sie dienen lediglich als Hinweis.

**Zeilennummern**

Wenn aktiviert, wird eine Zeilennummer neben jeder Codezeile angezeigt.

> [!NOTE]
> Diese Zeilennummern werden weder gedruckt noch dem Code hinzugefügt. Sie dienen lediglich als Hinweis.

**Einfaches Klicken für URLs aktivieren**

Wenn aktiviert, nimmt der Cursor die Form einer Hand an, wenn er im Editor über eine URL bewegt wird. Sie können auf die URL klicken, um die angegebene Seite im Webbrowser anzuzeigen.

**Navigationsleiste**

Wenn aktiviert, wird die **Navigationsleiste** am oberen Rand des Code-Editors angezeigt. Mit den Dropdownlisten **Objekte** und **Member** können Sie ein bestimmtes Objekt in Ihrem Code auswählen, seine Member auswählen und zur Deklaration des ausgewählten Members im Code-Editor navigieren.

**Befehle zum Ausschneiden oder Kopieren bei fehlender Auswahl auf leere Zeilen anwenden**

Diese Option legt das Verhalten des Editors fest, wenn Sie die Einfügemarke in einer leeren Zeile positionieren, keine Auswahl vornehmen und anschließend einen Kopier- oder Ausschneidevorgang ausführen.

- Wenn diese Option aktiviert ist, wird die Leerzeile kopiert oder ausgeschnitten. Beim anschließenden Einfügen wird eine neue leere Zeile eingefügt.

- Wenn diese Option deaktiviert ist, entfernt das Ausschneiden leere Zeilen. Die Daten in der Zwischenablage werden allerdings beibehalten. Wenn Sie deshalb anschließend den Befehl „Einfügen“ verwenden, wird der zuletzt in die Zwischenablage kopierte Inhalt eingefügt. Wenn Sie zuvor nichts kopiert haben, wird kein Inhalt eingefügt.

Wenn eine Zeile nicht leer ist, hat diese Einstellung keine Auswirkungen auf den Kopier- oder Ausschneidevorgang. Wenn nichts ausgewählt ist, wird die gesamte Zeile kopiert oder ausgeschnitten. Beim anschließenden Einfügen werden der Text der gesamten Zeile sowie das Zeilenendezeichen eingefügt.

> [!TIP]
> Zur Unterscheidung von Zeilen mit Einzug und Leerzeilen können Indikatoren für Leerzeichen, Tabulatoren und Zeilenenden angezeigt werden. Wählen Sie dazu im Menü **Bearbeiten** die Option **Erweitert** und anschließend **Leerstelle anzeigen** aus.

## <a name="see-also"></a>Siehe auch

- [Optionen, Text-Editor, Alle Sprachen, Registerkarten](../../ide/reference/options-text-editor-all-languages-tabs.md)
- [Allgemein, Umgebung, Optionen (Dialogfeld)](../../ide/reference/general-environment-options-dialog-box.md)
- [Verwenden von IntelliSense](../../ide/using-intellisense.md)
