---
title: GUIDs und IDs von Visual Studio-Menüs | Microsoft-Dokumentation
description: Zeigen Sie eine Liste von GUID-und ID-Werten für die Menüs und Gruppen in der Visual Studio-Menüleiste an, die in der integrierten Entwicklungsumgebung (IDE) von Visual Studio enthalten ist.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio menus
- visual studio groups
- id
- existing menus
- guid
- menus
ms.assetid: 84639d86-dd21-4b35-9988-6bb654162488
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bd2bdc047ddd5a568aca01ed99b6148b0f288faa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970269"
---
# <a name="guids-and-ids-of-visual-studio-menus"></a>GUIDs und IDs von Visual Studio-Menüs
In diesem Artikel werden die GUID-und ID-Werte der Menüs und Gruppen in der Visual Studio-Menüleiste aufgelistet. Diese Werte werden in *vsct* -Dateien definiert, die als Teil des Visual Studio SDK installiert werden. Weitere Informationen finden Sie unter [IDE-definierte Befehle, Menüs und Gruppen](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

 Weitere Informationen zum Arbeiten mit Objekten integrierter Entwicklungsumgebung (Integrated Development Environment, IDE), die in *vsct* -Dateien definiert sind, finden Sie unter [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md).

 Die-GUID wird in den Menüs und Gruppen in der Visual Studio-Menüleiste verwendet `guidSHLMainMenu` . Die Menüleiste selbst hat eine ID von `IDM_VS_TOOL_MAINMENU` .

## <a name="groups-on-the-visual-studio-menu-bar"></a>Gruppen in der Visual Studio-Menüleiste
 Zum Hinzufügen eines Menüs zur Menüleiste legen Sie eine dieser Gruppen als übergeordnetes Element fest.

|Group|id|
|-----------|--------|
|Datei/Bearbeitung/Ansicht|IDG_VS_MM_FILEEDITVIEW|
|Umgestaltung|IDG_VS_MM_REFACTORING:|
|Project|IDG_VS_MM_PROJECT|
|Erstellen|IDG_VS_MM_BUILDDEBUGRUN|
|Format/Tools|IDG_VS_MM_TOOLSADDINS|
|Fenster/Hilfe/Community|IDG_VS_MM_WINDOWHELP|
|Add-Ins|IDG_VS_MM_MACROS|
|Vollscreenbar|IDG_VS_MM_FULLSCREENBAR|

## <a name="menus-on-the-visual-studio-menu-bar"></a>Menüs in der Visual Studio-Menüleiste
 Zum Hinzufügen einer Gruppe zu einem vorhandenen Visual Studio-Menü legen Sie eines der folgenden Menüs als übergeordnetes Element fest. Untermenüs sind nicht in dieser Liste enthalten.

|Menü|id|
|----------|--------|
|Datei|IDM_VS_MENU_FILE|
|Bearbeiten|IDM_VS_MENU_EDIT|
|Sicht|IDM_VS_MENU_VIEW|
|Refactoring|IDM_VS_MENU_REFACTORING|
|Project|IDM_VS_MENU_PROJECT|
|Erstellen|IDM_VS_MENU_BUILD|
|Format|IDM_VS_MENU_FORMAT|
|Tools|IDM_VS_MENU_TOOLS|
|Erweiterungen|IDM_VS_MENU_EXTENSIONS|
|Fenster|IDM_VS_MENU_WINDOW|
|Add-Ins|IDM_VS_MENU_ADDINS|
|Community|IDM_VS_MENU_COMMUNITY|
|Hilfe|IDM_VS_MENU_HELP|

## <a name="groups-on-visual-studio-menus"></a>Gruppen in Visual Studio-Menüs
 In den folgenden Listen sind die Gruppen aufgeführt, die direkt aus Menüs in der Visual Studio-Menüleiste abgeleitet werden. Die schnellste Möglichkeit, einem Visual Studio-Menü einen Befehl hinzuzufügen, besteht darin, eine dieser Gruppen als übergeordnetes Element festzulegen. Gruppen, die von Untermenüs abgeleitet werden, werden in diesem Abschnitt nicht angezeigt.

### <a name="file-menu-groups"></a>Datei Menü Gruppen

|Group|id|
|-----------|--------|
|Neu/offen|IDG_VS_FILE_FILE|
|Hinzufügen|IDG_VS_FILE_ADD|
|Lösung|IDG_VS_FILE_SOLUTION|
|Sonstiges|IDG_VS_FILE_MISC|
|Speichern|IDG_VS_FILE_SAVE|
|Umbenennen|IDG_VS_FILE_RENAME|
|Browser|IDG_VS_FILE_BROWSER|
|Drucken|IDG_VS_FILE_PRINT|
|Zuletzt verwendet|IDG_VS_FILE_MRU|
|Move|IDG_VS_FILE_MOVE|
|Beenden|IDG_VS_FILE_EXIT|

### <a name="edit-menu-groups"></a>Menü Gruppen bearbeiten

|Group|id|
|-----------|--------|
|Rückgängig/Wiederholen|IDG_VS_EDIT_UNDOREDO|
|Ausschneiden/Kopieren/Einfügen|IDG_VS_EDIT_CUTCOPY|
|Select|IDG_VS_EDIT_SELECT|
|GoTo|IDG_VS_EDIT_GOTO|
|Suchen|IDG_VS_EDIT_FIND|
|erzwingen|IDG_VS_EDIT_OBJECTS|
|OLE-Verben|IDG_VS_EDIT_OLEVERBS|
|Befehlszeile|IDG_VS_EDIT_COMMANDWELL|

### <a name="refactor-menu-groups"></a>Umgestalten von Menü Gruppen

|Group|id|
|-----------|--------|
|Allgemein|IDG_REFACTORING_COMMON|
|Erweitert|IDG_REFACTORING_ADVANCED|

### <a name="view-menu-groups"></a>Menü Gruppen anzeigen

|Group|id|
|-----------|--------|
|Formular Code|IDG_VS_VIEW_FORMCODE|
|Browser|IDG_VS_VIEW_BROWSER|
|Definieren von Sichten|IDG_VS_VIEW_DEFINEVIEWS|
|Windows|IDG_VS_VIEW_WINDOWS|
|Architekten Fenster|IDG_VS_VIEW_ARCH_WINDOWS|
|Organisations Fenster|IDG_VS_VIEW_ORG_WINDOWS|
|Code Browser|IDG_VS_VIEW_CODEBROWSENAV_WINDOWS|
|Entwicklungsfenster|IDG_VS_VIEW_DEV_WINDOWS|
|Symbolleisten|IDG_VS_VIEW_TOOLBARS|
|Symbole|IDG_VS_VIEW_SYMBOLNAVIGATE|
|Navigieren|IDG_VS_VIEW_NAVIGATE|
|Small Navigate|IDG_VS_VIEW_SMALLNAVIGATE|
|Objektkatalog|IDG_VS_VIEW_OBJBRWSR|
|Befehlszeile|IDG_VS_VIEW_COMMANDWELL|
|Eigenschaftenseiten|IDG_VS_VIEW_PROPPAGES|
|Aktualisieren|IDG_VS_VIEW_REFRESH|

### <a name="project-menu-groups"></a>Projekt Menü Gruppen

|Group|id|
|-----------|--------|
|Sonstige hinzufügen|IDG_VS_PROJ_MISCADD|
|Hinzufügen|IDG_VS_PROJ_ADD|
|Ordner|IDG_VS_PROJ_FOLDER|
|Entladen/erneut laden|IDG_VS_PROJ_UNLOADRELOAD|
|Verweis|IDG_VS_PROJ_REFERENCE|
|Optionen|IDG_VS_PROJ_OPTIONS|
|Einstellungen|IDG_VS_PROJ_SETTINGS|

### <a name="build-menu-groups"></a>Build-Menü Gruppen

|Group|id|
|-----------|--------|
|Lösung|IDG_VS_BUILD_SOLUTION|
|Auswahl|IDG_VS_BUILD_SELECTION|
|Profilgesteuerte Optimierung|IDG_VS_PGO_SELECTION|
|Sonstiges|IDG_VS_BUILD_MISC|
|Abbrechen|IDG_VS_BUILD_CANCEL|

### <a name="tools-menu-groups"></a>Menü Gruppen "Extras"

|Group|id|
|-----------|--------|
|Befehlszeile|IDG_VS_TOOLS_CMDLINE|
|Codeausschnitte|IDG_VS_TOOLS_SNIPPETS|
|Objekt Teilmenge|IDG_VS_TOOLS_OBJSUBSET|
|Optionen|IDG_VS_TOOLS_OPTIONS|
|Weitere 2|IDG_VS_TOOLS_OTHER2|
|Externe Tools|IDG_VS_TOOLS_EXT_TOOLS|
|Externe Anpassungen|IDG_VS_TOOLS_EXT_CUST|

### <a name="window-menu-groups"></a>Fenstermenü Gruppen

|Group|id|
|-----------|--------|
|Neu|IDG_VS_WINDOW_NEW|
|Andocken/schließen|IDG_VS_DOCKCLOSE|
|Andocken/ausblenden|IDG_VS_DOCKHIDE|
|Anordnen|IDG_VS_WINDOW_ARRANGE|
|Navigation|IDG_VS_WINDOW_NAVIGATION|
|List|IDG_VS_WINDOW_LIST|

### <a name="help-menu-groups"></a>Hilfe Menü Gruppen

|Group|id|
|-----------|--------|
|Beispiele|IDG_VS_HELP_SAMPLES|
|Support|IDG_VS_HELP_SUPPORT|
|Info|IDG_VS_HELP_ABOUT|

## <a name="submenus-of-visual-studio-menus"></a>Untermenüs von Visual Studio-Menüs
 In der folgenden Hierarchie werden die Untermenüs angezeigt, die den Menüs in der Visual Studio-Menüleiste zugeordnet sind. Da nur eine Gruppe ein Menü als übergeordnetes Element aufweisen kann, muss jedes Untermenü aus einer Gruppe in einem Menü abgeleitet werden, anstatt direkt aus dem Menü. Weitere Informationen über die Beziehung zwischen Menüs, Gruppen und Untermenüs finden [Sie unter Hinzufügen eines Untermenüs zu einem Menü](../../extensibility/adding-a-submenu-to-a-menu.md).

> [!NOTE]
> Die Namen der Menüs in der Visual Studio-Menüleiste werden in dieser Hierarchie nicht separat angezeigt, da Sie von der Benennungs Konvention für Gruppen in der IDE abgeleitet werden können, wie im folgenden gezeigt: *IDG_VS_ \<Menu Name\> _ \<Group Name\>*.

|Übergeordnete Gruppe|Untermenü|Untergeordnete Gruppen|
|------------------|-------------|------------------|
|IDG_VS_FILE_FILE|IDM_VS_CSCD_NEW|IDG_VS_FILE_NEW_CASCADE|
||IDM_VS_CSCD_OPEN|IDG_VS_FILE_OPENP_CASCADE|
|||IDG_VS_FILE_OPENF_CASCADE|
|IDG_VS_FILE_ADD|IDM_VS_CSCD_ADD|IDG_VS_FILE_ADD_PROJECT_NEW|
|||IDG_VS_FILE_ADD_PROJECT_EXI|
|IDG_VS_FILE_MRU|IDM_VS_CSCD_FILEMRU|IDG_VS_FILE_FMRU_CASCADE|
||IDM_VS_CSCD_PROJMRU|IDG_VS_FILE_PMRU_CASCADE|
|IDG_VS_FILE_MOVE|IDM_VS_CSCD_MOVETOPRJ|IDG_VS_FILE_MOVE_CASCADE|
|||IDG_VS_FILE_MOVE_PICKER|
|IDG_VS_VIEW_DEV_WINDOWS|IDM_VS_CSCD_FINDRESULTS|IDG_VS_WNDO_FINDRESULTS|
||IDM_VS_CSCD_WINDOWS|IDG_VS_VIEW_CALLBROWSER|
|||IDG_VS_WNDO_OTRWNDWS1... 6|
|||IDG_VS_WNDO_WINDOWS2|
|IDG_VS_VIEW_TOOLBARS|IDM_VS_CSCD_COMMANDBARS||
|IDG_VS_EDIT_GOTO|IDM_VS_EDITOR_FIND_MENU||
|IDG_VS_EDIT_OBJECTS|IDM_VS_CSCD_MNUDES|IDG_VS_MNUDES_INSERT|
|||IDG_VS_MNUDES_EDITNAMES|
||IDM_VS_CSCD_OLEVERBS|IDG_VS_EDIT_OLEVERBS|
|IDG_VS_BUILD_SELECTION|IDM_VS_CSCD_BUILD|IDG_VS_BUILD_CASCADE|
|||IDG_VS_BUILD_PROJPICKER|
||IDM_VS_CSCD_REBUILD|IDG_VS_REBUILD_CASCADE|
|||IDG_VS_REBUILD_PROJPICKER|
||IDM_VS_CSCD_PROJONLY|IDG_VS_PROJONLY_CASCADE|
||IDM_VS_CSCD_CLEAN|IDG_VS_CLEAN_CASCADE|
|||IDG_VS_CLEAN_PROJPICKER|
||IDM_VS_CSCD_DEPLOY|IDG_VS_DEPLOY_CASCADE|
|||IDG_VS_DEPLOY_PROJPICKER|
|IDG_VS_PGO_SELECTION|IDM_VS_CSCD_PGO_BUILD|IDG_VS_PGO_BUILD_CASCADE_BUILD|
|||IDG_VS_PGO_BUILD_CASCADE_RUN|

## <a name="see-also"></a>Weitere Informationen
- [GUIDs und IDs von Visual Studio-Symbolleisten](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)
- [GUIDs und IDs von Visual Studio-Befehlen](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)
- [Vsct-Dateien (Visual Studio-Befehls Tabelle)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
