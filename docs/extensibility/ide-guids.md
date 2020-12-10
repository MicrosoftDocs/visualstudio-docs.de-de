---
title: IDE-GUIDs | Microsoft-Dokumentation
description: Die VSConstants-Klasse veröffentlicht eine Reihe von GUIDs einiger Teile der IDE. In diesem Artikel werden die GUIDs aufgelistet.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- GUIDs, integrated development environment
- IDE, GUIDs
ms.assetid: d31a0f97-b7be-4fb5-a942-8ba4527bc068
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 66a79a24225fe2abbb27611e041295711e6e3b38
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "96993470"
---
# <a name="ide-guids"></a>IDE-GUIDs

Die- <xref:Microsoft.VisualStudio.VSConstants> Klasse veröffentlicht GUIDs einiger Teile der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE), wie in der folgenden Tabelle aufgeführt.

## <a name="core-systems"></a>Kernsysteme

|Konstante|GUID|
|--------------|----------|
|<xref:Microsoft.VisualStudio.VSConstants.CLSID.HtmDocData_guid>|62c81794-a9ec-11D0-8198-00a0c91bbee3|
|<xref:Microsoft.VisualStudio.VSConstants.VsPackageGuid.HtmlEditorPackage_guid>|1b437d20fi8fe-11d2-a6ae-00104bcc7269|
|<xref:Microsoft.VisualStudio.VSConstants.VsLanguageServiceGuid.HtmlLanguageService_guid>|58e975a0-fi8fe-11d2-a6ae-00104bcc7269|
|<xref:Microsoft.VisualStudio.VSConstants.CLSID.MiscellaneousFilesProject_guid>|A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3|
|<xref:Microsoft.VisualStudio.VSConstants.CLSID.SolutionItemsProject_guid>|D1DCDB85-C5E8-11d2-BFCA-00C04F990235|
|<xref:Microsoft.VisualStudio.VSConstants.CLSID.VsEnvironmentPackage_guid>|DA9FB551-C724-11d0-AE1F-00A0C90FFFC3|
|<xref:Microsoft.VisualStudio.VSConstants.VsEditorFactoryGuid.HtmlEditor_guid>|C76D83F8-A489-11D0-8195-00A0C91BBEE3|
|<xref:Microsoft.VisualStudio.VSConstants.VsEditorFactoryGuid.TextEditor_guid>|8b382828-6202-11d1-8870-0000-Dienst-D2|

## <a name="broadly-visible-components"></a>Allgemein sichtbare Komponenten

|Konstante|GUID|
|--------------|----------|
|<xref:Microsoft.VisualStudio.VSConstants.CLSID.VsUIHierarchyWindow_guid>|7d960b07-7af8-11D0-8e5e-00a0c911005a|
|<xref:Microsoft.VisualStudio.VSConstants.VsEditorFactoryGuid.ExternalEditor_guid>|8137c9e8-35fe-4af2-87b0-de3c45f 395fd|
|Microsoft.VisualStudio.VSConstants.SID_SUIHostCommandDispatcher|e69cd190-1276-11d1-9f64-00a0c911004f|
|Microsoft.VisualStudio.VSConstants.SID_SVsGeneralOutputWindowPane|65482c72-DEFA-41b7-902c-11c091889c83|

## <a name="files-virtual-and-physical-folders-and-subprojects"></a>Dateien, virtuelle und physische Ordner und unter Projekte

|Konstante|GUID|
|--------------|----------|
|<xref:Microsoft.VisualStudio.VSConstants.ItemTypeGuid.PhysicalFile_guid>|6bb5f8ee-4483-11d3-8bcf-00c04f8ec28c|
|<xref:Microsoft.VisualStudio.VSConstants.ItemTypeGuid.PhysicalFolder_guid>|6bb5f8ef-4483-11d3-8bcf-00c04f8ec28c|
|<xref:Microsoft.VisualStudio.VSConstants.ItemTypeGuid.SubProject_guid>|EA6618E8-6E24-4528-94BE-6889FE16485C|
|<xref:Microsoft.VisualStudio.VSConstants.ItemTypeGuid.VirtualFolder_guid>|6bb5f8f0-4483-11d3-8bcf-00c04f8ec28c|

## <a name="ui-contexts"></a>UI-Kontexte

|Konstante|GUID|
|--------------|----------|
|<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.CodeWindow_guid>|8fe2df1d-e0da-4ebe-9d5c-415d40e487b5|
|<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid>|adfc4e61-0397-11d1-9f4e-00a0c911004f|
|<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.DesignMode_guid>|adfc4e63-0397-11d1-9f4e-00a0c911004f|
|<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Dragging_guid>|b706f393-2e5b-49e7-9e2e-b1825f639b63|
|<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>|adfc4e65-0397-11d1-9f4e-00a0c911004f|
|<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.FullScreenMode_guid>|adfc4e62-0397-11d1-9f4e-00a0c911004f|
|<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.NoSolution_guid>|adfc4e64-0397-11d1-9f4e-00a0c911004f|
|<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid>|adfc4e60-0397-11d1-9f4e-00a0c911004f|
|<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>|f1536ef8-92ec-443c-9ed7-fdadf150da82|
|<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>|93694fa0-0397-11d1-9F & 4E-00a0c911004f|
|<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>|adfc4e66-0397-11d1-9f4e-00a0c911004f|

## <a name="output-pane"></a>Ausgabebereich

|Konstante|GUID|
|--------------|----------|
|<xref:Microsoft.VisualStudio.VSConstants.OutputWindowPaneGuid.BuildOutputPane_guid>|1bd8a850-02d1-11d1-bee7-00a0c913d1f 8|
|<xref:Microsoft.VisualStudio.VSConstants.OutputWindowPaneGuid.DebugPane_guid>|FC076020-078A-11D1-A7DF-00A0C9110051|
|<xref:Microsoft.VisualStudio.VSConstants.OutputWindowPaneGuid.GeneralPane_guid>|3c24d581-5591-4884-a571-9fe89915cd64|
|<xref:Microsoft.VisualStudio.VSConstants.OutputWindowPaneGuid.SortedBuildOutputPane_guid>|2032b126-7c8d-48ad-8026-0e0348004fc0|
|<xref:Microsoft.VisualStudio.VSConstants.OutputWindowPaneGuid.StoreValidationPane_guid>|54065c74-1b11-4249-9ea7-5540d1a6d528|
|Microsoft.VisualStudio.VSConstants.SID_SVsGeneralOutputWindowPane|65482c72-DEFA-41b7-902c-11c091889c83|

## <a name="command-sets-and-properties"></a>Befehls Sätze und Eigenschaften

|Konstante|GUID|
|--------------|----------|
|Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97|5efc7975-14bc-11CF-9b2b-00aa00573819|
|Microsoft.VisualStudio.VSConstants.GUID_VsUIHierarchyWindowCmds>|60481700-078b-11d1-aaf8-00a0c9055a90|

## <a name="iunknown"></a>IUnknown

|Konstante|GUID|
|--------------|----------|
|<xref:Microsoft.VisualStudio.VSConstants.IID_IUnknown>|00000000-0000-0000-C000-000000000046|

## <a name="task-list-guids"></a>Aufgabenlisten-GUIDs

|Konstante|GUID|
|--------------|----------|
|<xref:Microsoft.VisualStudio.VSConstants.VsTaskListView.All>|1880202e-FC20-11d2-8bb1-00c04f8ec28c|
|<xref:Microsoft.VisualStudio.VSConstants.VsTaskListView.CheckedTasks>|18802036-FC20-11d2-8bb1-00c04f8ec28c|
|<xref:Microsoft.VisualStudio.VSConstants.VsTaskListView.CommentTasks>|18802034-FC20-11d2-8bb1-00c04f8ec28c|
|<xref:Microsoft.VisualStudio.VSConstants.VsTaskListView.CompilerTasks>|18802033-FC20-11d2-8bb1-00c04f8ec28c|
|<xref:Microsoft.VisualStudio.VSConstants.VsTaskListView.CurrentFileTasks>|18802035-FC20-11d2-8bb1-00c04f8ec28c|
|<xref:Microsoft.VisualStudio.VSConstants.VsTaskListView.HTMLTasks>|36ac1c0d-FE86-11d2-8bb1-00c04f8ec28c|
|<xref:Microsoft.VisualStudio.VSConstants.VsTaskListView.ShortcutTasks>|18802030-FC20-11d2-8bb1-00c04f8ec28c|
|<xref:Microsoft.VisualStudio.VSConstants.VsTaskListView.UncheckedTasks>|18802037-FC20-11d2-8bb1-00c04f8ec28c|
|<xref:Microsoft.VisualStudio.VSConstants.VsTaskListView.UserTasks>|1880202f-FC20-11d2-8bb1-00c04f8ec28c|
|<xref:Microsoft.VisualStudio.VSConstants.CLSID.VsTaskList_guid>|BC5955D5-aa0d-11d0-a8c5-00a0c921a4d2|
|<xref:Microsoft.VisualStudio.VSConstants.VsPackageGuid.VsTaskListPackage_guid>|4a9b7e50aa16-11D0-a8c5-00a0c921a4d2|

## <a name="component-selector-page-guids"></a>GUIDs der Komponentenauswahl Seite

|Konstanten|GUID|
|---------------|----------|
|Microsoft.VisualStudio.VSConstants.GUID_COMClassicPage|9a341d96-5a64-11d3-bff9-00c04f990235|
|Microsoft.VisualStudio.VSConstants.GUID_COMPlusPage|9a341d95-5a64-11d3-bff9-00c04f990235|
|Microsoft.VisualStudio.VSConstants.GUID_SolutionPage|9a341d97-5a64-11d3-bff9-00c04f990235|

## <a name="miscellaneous-shell-guids"></a>Sonstige shellguids

|Konstanten|GUID|
|---------------|----------|
|<xref:Microsoft.VisualStudio.VSConstants.CLSID.VsCfgProviderEventsHelper_guid>|99913l1f -1ee3-11d1-8a6e-00c04f 682e21|
|<xref:Microsoft.VisualStudio.VSConstants.VsPackageGuid.VsDocOutlinePackage_guid>|21af45b0-ffa5-11D0-b63f-00a0c922e851|
|Microsoft.VisualStudio.VSConstants.SID_SVsToolboxActiveXDataProvider|35222106-BB44-11D0-8c46-00c04fc2aae2|

## <a name="see-also"></a>Weitere Informationen

- [COM-Konstanten in verwaltetem Code](../extensibility/com-constants-in-managed-code.md)
- [IDE-Konstanten](../extensibility/ide-constants.md)
- [IDE-definierte Befehle zum Erweitern von Project s ystems](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
