---
title: Projekt Modell-Kernkomponenten | Microsoft-Dokumentation
description: Dieser Artikel enthält Beschreibungen der Schnittstellen und Dienste, die im Projekt Modell Kern identifiziert werden, sowie der Schnittstellen und Dienste, die Objekten zugeordnet sind.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6aeb24b2aee5b0abb3e5d803004ba97725bb707
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876895"
---
# <a name="project-model-core-components"></a>Hauptkomponenten eines Projektmodells
Die folgenden Tabellen erweitern das Projekt Modell. Die Tabellen enthalten kurze Beschreibungen der im Modell identifizierten Schnittstellen und Dienste sowie der Schnittstellen und Dienste, die bestimmten Objekten zugeordnet sind. Außerdem beschreiben die Tabellen weitere Schnittstellen, die bei der Erstellung und Wartung von Projekten optional sind, abhängig von den Anforderungen des jeweiligen Projekt Typs.

 Weitere Informationen finden Sie [unter unterstützen von Symbol-Browsing Tools](../../extensibility/internals/supporting-symbol-browsing-tools.md).

### <a name="package-object"></a>Paket Objekt

|Schnittstelle|Kommentare|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|Initialisiert ein VSPackage in der IDE und stellt seine Dienste der IDE zur Verfügung.|

### <a name="project-factory-object"></a>Projektfactory-Objekt

|Schnittstelle|Kommentare|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Verwaltet das Erstellen neuer Projekte und das Öffnen vorhandener Projekte.|

### <a name="project-objects"></a>Projekt Objekte

|Schnittstellen|Kommentare|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Verwaltet das Hinzufügen und Entfernen von Projekt Elementen, öffnet Editoren und verwaltet die Zuordnung zwischen den einzelnen dokumentmonikern und `VSITEMID` . Erbt von `IVsProject` und `IVsProject2` .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Verwaltet Navigations-und Anzeigeeigenschaften und stellt Ereignisse bereit.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Ermöglicht Befehlsausführung ähnlich der von `IOleCommandTarget` für Befehle wie Ausschneiden und umbenennen, die nur angewendet werden, wenn sich der Fokus auf Projektmappen-Explorer befindet.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Dient als primäre Befehls Ziel Schnittstelle für eine Projekt Hierarchie. Dabei handelt es sich um die Standardschnittstelle zum Abfragen von Objekten für den Befehlsstatus oder den Status und die Ausführung von Befehlen. Verfügbar, wenn Sie nicht im Projektfenster den Fokus haben.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Koordiniert die Persistenz des Projekt Zustands. In der Regel wird der Projektstatus als Projektdatei gespeichert, kann aber an Speichersysteme angepasst werden, die nicht Datei basiert sind.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|Ermöglicht dem Projekt, alle Aspekte der Persistenz für die zugehörigen Projekt Elemente als Dateien auf Datenträgern oder Objekten in anderen Speichersystemen zu verwalten. Die- `IVsPersistHierarchyItem2` Schnittstelle wird für Elemente verwendet, die die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> Schnittstelle nicht implementieren.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Koordiniert Interaktionen mit der Quell Code Verwaltung.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Ermöglicht es-Projekten, Konfigurationsinformationen zu verwalten.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Verwaltet Projekt Konfigurationsobjekte, z. b. Debug-/Releasekonfigurationen. Build-, Bereitstellungs-und Debugvorgänge werden über Projekt Konfigurationsobjekte koordiniert.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Wird von Hierarchien implementiert, um die Lösch-(destruktiven) oder Entfernungs Optionen (nicht destruktiv) für Hierarchie Elemente zu steuern. Ruft die Abfrage Schnittstelle in der Schnittstelle `IVsHierarchyDeleteHandler` von der-Schnittstelle auf `IVsHierarchy` .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|Stellt die Implementierungs Option bereit, mit der das-Objekt, das die-Schnittstelle unterstützt, `IVsCfgProvider2` in einer anderen com-Identität als das Projekt Objekt vorhanden ist `IVsHierarchy`|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Optionale Schnittstelle, die implementiert wird, um das Projekt von anderen Entwicklern erweiterbar zu machen. Die- `IVsProjectStartupServices` Schnittstelle ermöglicht einem Drittanbieter-VSPackage, eine GUID zu registrieren, die in der Projektdatei gespeichert wird, sodass Sie bei jedem Laden des Projekts die Dienst-GUID des Drittanbieters in die Projektdatei laden und `QueryService` für diese GUID anrufen.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Wird von Quell Hierarchien in einem `UIHierarchy` Fenster implementiert, um Zwischenablage Vorgänge wie Ausschneiden, kopieren und einfügen zu koordinieren. Verwenden `AdviseClipboardHelperEvents` Sie die Schnittstelle zum Registrieren von Zwischenablage Ereignissen.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Stellt Informationen zu einem gezogenen Element relativ zu seiner Datenquelle während eines Drag & Drop-Vorgangs in einem UI-Hierarchie Fenster bereit. Wird von der- `IVsHierarchy` Schnittstelle aufgerufen.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Stellt Informationen zu einem gezogenen Element relativ zum Ablage Ziel während eines Drag & Drop-Vorgangs in einem UI-Hierarchie Fenster bereit. Wird von der- `IVsHierarchy` Schnittstelle aufgerufen.|

### <a name="configuration-object"></a>Konfigurationsobjekt

|Schnittstellen|Kommentare|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Stellt Informationen zu einer-Konfiguration bereit.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Ermöglicht es-Projekten, Konfigurationsinformationen zu verwalten.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Ermöglicht das Ausführen eines Projekts unter der Steuerung des Debuggers.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Wird von Bereitstellungs Projekten implementiert, die Bereitstellungs Vorgänge für andere Projekte ausführen.|

### <a name="configuration-builder-object"></a>Configuration Builder-Objekt

|Schnittstellen|Kommentare|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Verwaltet den Buildvorgang einer Projektkonfiguration.|

### <a name="additional-project-objects"></a>Zusätzliche Projekt Objekte

|Schnittstellen|Kommentare|
|----------------|--------------|
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|Zeigt die Element Eigenschaften im **Eigenschaften** Fenster an.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Zeigt Ausgaben für die Bereitstellung an.|

 Die folgende Tabelle enthält eine kurze Beschreibung der Dienste, die im Projekt Modell identifiziert werden.

### <a name="services"></a>Dienste

|Dienst|Kommentare|
|-------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Wird von VSPackages verwendet, die Projekttypen implementieren, um zu registrieren, ob Ihre projektfactory mit der IDE vorhanden ist. Das VSPackage muss `QueryService` für diesen Dienst aufrufen und seine projektfactory registrieren, wenn die- `IVsPackage::SetSite` Methode aufgerufen wird. Wenn die- `SetSite` Methode nicht aufgerufen wird, wird das Projekt nicht instanziiert.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Bietet Zugriff auf die interne, integrierte Darstellung der aktuellen Projekt Mappe der IDE, z. b. die Möglichkeit, Projekte aufzulisten, neue Projekte zu erstellen, die Projektänderungen zu beachten usw.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|Wird von Projekten aufgerufen, die an der Quell Code Verwaltung teilnehmen möchten.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Verwaltet eine Tabelle mit geöffneten Dokumenten, um zu bestimmen, ob ein oder mehrere Projekt Elemente bereits geöffnet sind.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Enthält die Schnittstellen und Methoden, die aufgerufen werden, um ein Projekt Element tatsächlich mithilfe des Standard-Editors oder eines bestimmten Editors zu öffnen.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Muss von allen Projekten aufgerufen werden, wenn Sie Elemente hinzufügen, entfernen oder umbenennen.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Verwaltet Änderungen an einer Datei oder einem Verzeichnis und benachrichtigt Clients, wenn ausgewählte Dateien auf dem Datenträger geändert wurden.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Muss von allen Projekten und Editoren aufgerufen werden, bevor Sie Elemente geändert oder gespeichert werden.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Verwaltet die Reihenfolge von Build-und Bereitstellungs Vorgängen für Projekt Konfigurationen.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Bietet Zugriff auf Low-Level-Debugger-Dienste, die für die meisten debuggingsteuerelemente|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|Ermöglicht VSPackages den Zugriff auf Informationen über die aktuelle Auswahl und ermöglicht die Kommunikation mit dem **Eigenschaften** Fenster.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Bietet grundlegende IDE-Funktionen, wie z. b. die Möglichkeit zum Erstellen und Auflisten von Tool Fenstern oder Dokument Fenstern oder zum Melden eines Fehlers an den Benutzer.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|Bietet Zugriff auf die Statusleiste der IDE.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|Wird verwendet, um das Automatisierungs Modell zu implementieren. In Ihrem Projekt Modell wird ein Properties-Objekt zurückgegeben, mit dem Sie eine Instanz dieses Objekts erstellen können.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Wird zum Implementieren von Zwischenablage Ereignissen für das Project-Objekt in der Hierarchie verwendet. `SVsUIHierWinClipboardHelper` mit können Sie Ausschneide-, Kopier-und Einfügevorgänge ordnungsgemäß behandeln.|

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Prüfliste: Erstellen neuer Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Nicht im Build: Verwenden von HierUtil7-Projektklassen zum Implementieren eines Projekt Typs (C++)](/previous-versions/bb166212(v=vs.100))
- [Unterstützen von Tools zum Durchsuchen von Symbolen](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Elemente eines Projektmodells](../../extensibility/internals/elements-of-a-project-model.md)