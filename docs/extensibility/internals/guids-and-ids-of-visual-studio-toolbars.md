---
title: GUIDs und IDs von Visual Studio-Symbolleisten | Microsoft-Dokumentation
description: Anzeigen einer Liste von GUID-und ID-Werten für die Symbolleisten und die darin enthaltenen Gruppen, die in der integrierten Entwicklungsumgebung (IDE) von Visual Studio enthalten sind.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio groups
- toolbars
- visual studio toolbar
- id
- toolgar group
- tool window toolbar
- guid
ms.assetid: c9cacd57-9225-450f-a9ac-cbf3168ea844
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b44cda401faa0d7e34bf9ce7579aa3cca026fa13
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480381"
---
# <a name="guids-and-ids-of-visual-studio-toolbars"></a>GUIDs und IDs von Visual Studio-Symbolleisten
In diesem Thema werden die GUID-und ID-Werte der Symbolleisten aufgelistet, die in der integrierten Entwicklungsumgebung (IDE) von Visual Studio enthalten sind, sowie die darin enthaltenen Gruppen. Diese Werte werden in *vsct* -Dateien definiert, die als Teil des Visual Studio SDK installiert werden. Weitere Informationen finden Sie unter [IDE-definierte Befehle, Menüs und Gruppen](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

> [!NOTE]
> Viele der für Visual Studio verfügbaren Symbolleisten werden nicht von Visual Studio definiert, und ihre GUID-und ID-Werte sind nicht öffentlich. In diesem Thema werden nur Symbolleisten aufgelistet, die in den *vsct* -Dateien von Visual Studio SDK definiert sind.

 Weitere Informationen zum Arbeiten mit IDE-Objekten, die in *vsct* -Dateien definiert sind, finden Sie unter [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md).

 Die Standard Symbolleisten, die von der Visual Studio-IDE bereitgestellt werden, verwenden die GUID `guidSHLMainMenu` , außer wenn anderweitig mithilfe der-Syntax angegeben wird `GUID:ID` .

## <a name="ide-toolbars"></a>IDE-Symbolleisten
 Die folgenden Symbolleisten werden von der Visual Studio-IDE bereitgestellt. Symbolleisten können angezeigt werden, indem Sie **im Menü Extras im** Untermenü **Toolbars** ausgewählt werden. Symbolleisten in Tool Fenstern sind nicht in diesem Abschnitt enthalten.

 Nur Gruppen können direkt von Symbolleisten abgeleitet werden. Um eine Gruppe hinzuzufügen, legen Sie das übergeordnete Element auf die GUID und die ID der Symbolleiste fest. Um einer Symbolleiste eine Schaltfläche hinzuzufügen, legen Sie das übergeordnete Element auf der Symbolleiste auf eine Gruppe fest.

|Symbolleiste|ID|
|-------------|--------|
|Standard|IDM_VS_TOOL_STANDARD|
|Erstellen|IDM_VS_TOOL_BUILD|
|Text-Editor|IDM_VS_TOOL_TEXTEDITOR|
|Debug|guidvsdebuggroup: IDM_DEBUG_TOOLBAR|
|Debugspeicherort|guidvsdebuggroup: IDM_DEBUG_CONTEXT_TOOLBAR|

### <a name="special-toolbars"></a>Besondere Symbolleisten
 Diese Symbolleisten werden von der Visual Studio-IDE definiert, Sie dienen jedoch spezialisierten Funktionen und dienen nicht zum Hosten von Befehls Gruppen.

|Symbolleiste|ID|
|-------------|--------|
|Befehl zum Hinzufügen|IDM_VS_TOOL_ADDCOMMAND|
|Nicht definiert|IDM_VS_TOOL_UNDEFINED|
|XML-Schema|IDM_VS_TOOL_SCHEMA|
|XML-Daten|IDM_VS_TOOL_DATA|

## <a name="groups-on-the-ide-toolbars"></a>Gruppen auf den IDE-Symbolleisten
 Wenn Sie einer Standard Symbolleiste eine Schaltfläche hinzufügen möchten, legen Sie eine der folgenden Gruppen als übergeordnetes Element fest. Die Gruppen werden nach übergeordneter Symbolleiste sortiert.

### <a name="standard-toolbar-groups"></a>Standard Symbolleisten Gruppen

|Name|id|
|----------|--------|
|Speichern/Öffnen|IDG_VS_TOOLSB_SAVEOPEN|
|Ausschneiden/Kopieren|IDG_VS_TOOLSB_CUTCOPY|
|Rückgängig/Wiederholen|IDG_VS_TOOLSB_UNDOREDO|
|Ausführen/erstellen|IDG_VS_TOOLSB_RUNBUILD|
|Suchen|IDG_VS_TOOLSB_SEARCH|
|Windows|IDG_VS_TOOLSB_WINDOWS|
|Neue Fenster|IDG_VS_TOOLSB_NEWWINDOWS|
|Laden/Speichern|IDG_VS_WINDOWUI_LOADSAVE|
|Maßstab|IDG_VS_TOOLSB_GAUGE|

### <a name="build-toolbar-groups"></a>Erstellen von Symbolleisten Gruppen

|Name|id|
|----------|--------|
|Buildleiste|IDG_VS_BUILDBAR|
|Abbrechen|IDG_VS_BUILD_CANCEL|

### <a name="text-editor-toolbar-groups"></a>Text-Editor-Symbolleisten Gruppen

|Name|id|
|----------|--------|
|Completion|IDM_VS_TOOL_TEXTEDITOR|
|Einziehen|IDG_VS_EDITTOOLBAR_INDENT|
|Anmerkungen|IDG_VS_EDITTOOLBAR_COMMENT|
|Lesezeichen|IDG_VS_EDITTOOLBAR_TEMPBOOKMARKS|

### <a name="debug-toolbar-groups"></a>Debug-Symbolleisten Gruppen

|Name|id|
|----------|--------|
|Ausführung|IDM_DEBUG_TOOLBAR|
|Schrittweises Ausführen|IDG_DEBUG_TOOLBAR_STEPPING|
|Überwachen|IDG_DEBUG_TOOLBAR_WATCH|
|Windows|IDG_DEBUG_TOOLBAR_WINDOWS|

### <a name="debug-location-toolbar-groups"></a>Symbolleisten Gruppen Debugspeicherort

|Name|id|
|----------|--------|
|Debugspeicherort|IDG_DEBUG_CONTEXT_TOOLBAR|

## <a name="tool-window-toolbars"></a>Symbolleisten des Toolfensters
 Symbolleisten können direkt in der IDE oder in Tool Fenstern (z. b. **Projektmappen-Explorer**) angezeigt werden. Da Tool Fenster nicht in *vsct* -Dateien definiert sind, haben Tool Fenster-Symbolleisten keine übergeordneten Elemente. Stattdessen werden Sie in den Code eingefügt. In der folgenden Tabelle werden die Symbolleisten angezeigt, die in den Tool Fenstern in der IDE angezeigt werden, sowie die Befehls Gruppen, die Sie enthalten.

> [!NOTE]
> Symbolleisten und Gruppen verwenden die GUID `guidSHLMainMenu` , außer wenn Sie anderweitig mithilfe der GUID: ID-Syntax angegeben wird. Wenn eine GUID für eine Symbolleiste angegeben ist, gilt sie auch für die Gruppen, die von dieser Symbolleiste abgeleitet werden.

|Tool Fenster|Symbolleiste|Gruppen|
|-----------------|-------------|------------|
|Projektmappen-Explorer|IDM_VS_TOOL_PROJWIN|IDG_VS_PROJ_TOOLBAR1.. 5@@|
|Server-Explorer|guid_SE_MenuGroup: IDM_SE_TOOLBAR_SERVEREXPLORER|IDG_SE_TOOLBAR_REFRESH|
|Eigenschaften|IDM_VS_TOOL_PROPERTIES|IDG_VS_PROPERTIES_SORT<br /><br /> IDG_VS_PROPERTIES_PAGES|
|Klassenansicht|IDM_VS_TOOL_CLASSVIEW|IDG_VS_CLASSVIEW_FOLDERS<br /><br /> IDG_VS_CLASSVIEW_SEARCH<br /><br /> IDG_VS_CLASSVIEW_SETTINGS|
|Klassenansicht|IDM_VS_TOOL_CLASSVIEW_GO|IDG_VS_CLASSVIEW_SEARCH2|
|Objektkatalog|IDM_VS_TOOL_OBJBROWSER|IDG_VS_OBJBROWSER_SUBSETS<br /><br /> IDG_VS_OBJBROWSER_SEARCH<br /><br /> IDG_VS_OBJBROWSER_ADDREFERENCE<br /><br /> IDG_VS_OBJBROWSER_BROWSERSETTINGS|
|Objektkatalog|IDM_VS_TOOL_OBJECT_BROWSER_GO|IDG_VS_OBJBROWSER_SEARCH2|
|Output|IDM_VS_TOOL_OUTPUTWINDOW|IDG_VS_OUTPUTWINDOW_SELECT<br /><br /> IDG_VS_OUTPUTWINDOW_GOTO<br /><br /> IDG_VS_OUTPUTWINDOW_NEXTPREV<br /><br /> IDG_VS_OUTPUTWINDOW_CLEAR<br /><br /> IDG_VS_OUTPUTWINDOW_WORDWRAP|
|Suchen und Ersetzen|IDM_VS_TOOL_UNIFIEDFIND|IDG_VS_FINDTAB<br /><br /> IDG_VS_REPLACETAB|
|Suchergebnisse: 1|IDM_VS_TOOL_FINDRESULTS1|IDG_VS_FINDRESULTS1_GOTO<br /><br /> IDG_VS_FINDRESULTS1_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS1_CLEAR<br /><br /> IDG_VS_FINDRESULTS1_STOPFIND|
|Suchergebnisse 2|IDM_VS_TOOL_FINDRESULTS2|IDG_VS_FINDRESULTS2_GOTO<br /><br /> IDG_VS_FINDRESULTS2_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS2_CLEAR<br /><br /> IDG_VS_FINDRESULTS2_STOPFIND|
|Codeausschnitt|IDM_VS_TOOL_SNIPPETMENUS|IDG_VS_SNIPPET_REPL<br /><br /> IDG_VS_SNIPPET_REF<br /><br /> IDG_VS_SNIPPET_PROP|
|Lesezeichen|IDM_VS_TOOL_BOOKMARKWIND|IDG_VS_BWNEWFOLDER<br /><br /> IDG_VS_BWNEXTBM<br /><br /> IDG_VS_BWNEXTBMF<br /><br /> IDG_VS_BWENABLE<br /><br /> IDG_VS_BWDELETE|
|Aufgabenliste|IDM_VS_TOOL_TASKLIST|IDG_VS_TASKLIST_PROVIDERLIST|
|Benutzeraufgaben|IDM_VS_TOOL_USERTASKS|IDG_VS_TASKLIST_PROVIDERLIST<br /><br /> IDG_VS_USERTASKS_EDIT|
|Fehlerliste|IDM_VS_TOOL_ERRORLIST|IDG_VS_ERRORLIST_ERRORGROUP<br /><br /> IDG_VS_ERRORLIST_WARNINGGROUP<br /><br /> IDG_VS_ERRORLIST_MESSAGEGROUP|
|Aufrufbrowser|IDM_VS_TOOL_CALLBROWSER1.. Uhr|IDG_VS_TOOLBAR_CALLBROWSER1_ACTIONS<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_TYPE<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_CBSETTINGS|
|Haltepunkte|guidvsdebuggroup: IDM_BREAKPOINTS_WINDOW_TOOLBAR|IDG_BREAKPOINTS_WINDOW_NEW<br /><br /> IDG_BREAKPOINTS_WINDOW_DELETE<br /><br /> IDG_BREAKPOINTS_WINDOW_ALL<br /><br /> IDG_BREAKPOINTS_WINDOW_VIEW<br /><br /> IDG_BREAKPOINTS_WINDOW_EDIT<br /><br /> IDG_BREAKPOINTS_WINDOW_COLUMNS|
|Disassemblierung|guidvsdebuggroup: IDM_DISASM_WINDOW_TOOLBAR|IDG_DISASM_WINDOW_TOOLBAR|
|Arbeitsspeicher 1-4|guidvsdebuggroup: IDM_MEMORY_WINDOW_TOOLBAR1... 0:|IDG_MEMORY_EXPRESSION1.. 0:<br /><br /> IDG_MEMORY_COLUMNS1.. 0:|
|Prozesse|guidvsdebuggroup: IDM_ATTACHED_PROCS_TOOLBAR|IDG_ATTACHED_PROCS_EXECCNTRL IDG_ATTACHED_PROCS_STEPPING<br /><br /> IDG_ATTACHED_PROCS_EXECCNTRL2<br /><br /> IDG_ATTACHED_PROCS_ATTACH<br /><br /> IDG_ATTACHED_PROCS_COLUMNS|

## <a name="see-also"></a>Siehe auch
- [Hinzufügen eines Menü Controllers zu einer Symbolleiste](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)
- [Hinzufügen einer Symbolleiste zu einem Tool Fenster](../../extensibility/adding-a-toolbar-to-a-tool-window.md)
- [GUIDs und IDs von Visual Studio-Menüs](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)
