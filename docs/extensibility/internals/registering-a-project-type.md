---
title: Registrieren eines Projekt Typs | Microsoft-Dokumentation
description: Erfahren Sie mehr über das Erstellen von Registrierungs Einträgen, die Visual Studio das erkennen und arbeiten mit dem neuen Projekttyp ermöglichen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], new project registry entries
- registry, new project types
- registration, new project types
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 893f59aa9e99d990623e0c8383c12bbffbc4a510
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944510"
---
# <a name="registering-a-project-type"></a>Registrieren eines Projekttyps
Wenn Sie einen neuen Projekttyp erstellen, müssen Sie Registrierungseinträge erstellen, die es ermöglichen, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] den Projekttyp zu erkennen und zu bearbeiten. Diese Registrierungseinträge werden in der Regel mithilfe einer Registrierungs Skriptdatei (. rgs) erstellt.

 Im folgenden Beispiel stellen die Anweisungen aus der Registrierung Standard Pfade und-Daten bereit, sofern zutreffend, gefolgt von einer Tabelle, die Einträge aus dem Registrierungs Skript für jede Anweisung enthält. Die Tabellen stellen die Skript Einträge und zusätzliche Informationen zu den-Anweisungen bereit.

> [!NOTE]
> Die folgenden Registrierungsinformationen sind ein Beispiel für den Typ und die Zwecke der Einträge in den Registrierungs Skripts, die Sie schreiben, um den Projekttyp zu registrieren. Die tatsächlichen Einträge und ihre Verwendungsmöglichkeiten variieren je nach den spezifischen Anforderungen Ihres Projekt Typs. Überprüfen Sie die verfügbaren Beispiele, um eine zu finden, die dem Projekttyp ähnelt, den Sie entwickeln, und überprüfen Sie dann das Registrierungs Skript für dieses Beispiel.

 Die folgenden Beispiele stammen aus HKEY_CLASSES_ROOT.

## <a name="example-1"></a>Beispiel 1

```
\.figp
   @="FigPrjFile"
   "Content Type"="text/plain"
\.figp\ShellNew
   "NullFile"=""
\FigPrjFile
   @="Figure Project File"
\DefaultIcon
   @="<Visual Studio SDK installation path>\\9.0VSIntegration\\SomeFolder\\FigPkgs\\FigPrj\\Debug\\FigPrj.dll,-206"
\shell\open
   @="&Open in Visual Studio"
\shell\open\command
   @="devenv.exe \"%1\""
```

|Name|Typ|Daten|BESCHREIBUNG|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`FigPrjFile`|Name und Beschreibung der Projekttyp Dateien mit der Erweiterung. figp.|
|`Content Type`|REG_SZ|`Text/plain`|Der Inhaltstyp für die Projektdateien.|
|`NullFile`|REG_SZ|`Null`||
|`@`|REG_SZ|`%MODULE%,-206`|Standard Symbol, das für das Projekt dieses Typs verwendet wird. Die% Module%-Anweisung wird in der Registrierung am Standard Speicherort der Projekttyp-dll abgeschlossen.|
|`@`|REG_SZ|`&Open in Visual Studio`|Standardanwendung, in der dieser Projekttyp geöffnet wird.|
|`@`|REG_SZ|`devenv.exe "%1"`|Der Standardbefehl, der ausgeführt wird, wenn ein Projekt dieses Typs geöffnet wird.|

 Die folgenden Beispiele stammen aus HKEY_LOCAL_MACHINE und befinden sich in der Registrierung unter dem Schlüssel [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\99.0Exp\Packages].

## <a name="example-2"></a>Beispiel 2

```
\{ACEF4EB2-57CF-11D2-96F4-000000000000} (The CLSID for the VSPackage)
   @="FigPrj Project Package"
   "InprocServer32"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\                      Debug\\FigPrj.dll"
   "CompanyName"="Microsoft"
   "ProductName"="Figure Project Sample"
   "ProductVersion"="9.0"
   "MinEdition"="professional"
   "ID"=dword:00000001
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\SatelliteDLL
   "DllName"="FigPrjUI.dll"
   "Path"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\Debug\\"
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\Automation
   "FigProjects"=""
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\AutomationEvents
   "FigProjectsEvents"="Returns the FigProjectsEvents Object"
   "FigProjectItemsEvents"="Returns the FigProjectItemsEvents Object"
```

|Name|Typ|Daten|BESCHREIBUNG|
|----------|----------|----------|-----------------|
|`@` (Standard)|REG_SZ|`FigPrj Project VSPackage`|Lokalisier barer Name dieses registrierten VSPackages (Projekttyp).|
|`InprocServer32`|REG_SZ|`%MODULE%`|Der Pfad der Projekttyp-dll. Die IDE lädt diese DLL und übergibt die VSPackage-CLSID an `DllGetClassObject` , um <xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory> das Objekt zu erstellen <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> .|
|`CompanyName`|REG_SZ|`Microsoft`|Name des Unternehmens, das den Projekttyp entwickelt hat.|
|`ProductName`|REG_SZ|`Figure Project Sample`|Der Name für den Projekttyp.|
|`ProductVersion`|REG_SZ|`9.0`|Versionsnummer der Projekttyp Version.|
|`MinEdition`|REG_SZ|`professional`|Die Edition des VSPackages, das registriert wird.|
|`ID`|REG_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|Der Paket Lade Schlüssel für das Projekt-VSPackage. Der Schlüssel wird überprüft, wenn ein Projekt geladen wird, nachdem die Umgebung gestartet wurde.|
|`DllName`|REG_SZ|`%RESOURCE_DLL%`|Der Dateiname der Satelliten-DLL, die lokalisierte Ressourcen für den Projekttyp enthält.|
|`Path`|REG_SZ|`%RESOURCE_PATH%`|Der Pfad der Satelliten-DLL.|
|`FigProjectsEvents`|REG_SZ|Siehe Anweisung für Wert.|Bestimmt die für dieses Automatisierungs Ereignis zurückgegebene Text Zeichenfolge.|
|`FigProjectItemsEvents`|REG_SZ|Siehe Anweisung für Wert.|Bestimmt die für dieses Automatisierungs Ereignis zurückgegebene Text Zeichenfolge.|

 Alle folgenden Beispiele befinden sich in der Registrierung unter dem Schlüssel [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].

## <a name="example-3"></a>Beispiel 3

```
\{C061DB26-5833-11D2-96F5-000000000000} (The CLSID for projects of this type)
   @="FigPrj Project"
   "DisplayName"="#2"
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"
   "ProjectTemplatesDir"="C:\\Program Files\\VSIP 9.0\\EnvSDK\\FigPkgs\\                           FigPrj\\FigPrjProjects"
   "ItemTemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                           FigPrjProjectItems"
   "DisplayProjectFileExtensions"="#3"
   "PossibleProjectExtensions"="figp"
   "DefaultProjectExtension"=".figp"
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\1       (Folder 1 contains settings for Open Files filters.)
   @="#4"
   "CommonOpenFilesFilter"=dword:00000000
   "CommonFindFilesFilter"=dword:00000000
   "NotAddExistingItemFilter"=dword:00000000
   "FindInFilesFilter"=dword:00000000
   "NotOpenFileFilter"=dword:00000000
   "SortPriority"=dword:000003e8
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\2
      (Folder 2 contains settings for Find in Files filters.)
   @="#5"
   "CommonOpenFilesFilter"=dword:00000000
   "CommonFindFilesFilter"=dword:00000000
   "NotAddExistingItemFilter"=dword:00000001
   "FindInFilesFilter"=dword:00000001
   "NotOpenFileFilter"=dword:00000000
   "SortPriority"=dword:000003e8
\{C061DB26-5833-11D2-96F5-000000000000}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (Second GUID indicates the registered project type for the Add Items templates.)
   @="#6"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"
   "SortPriority"=dword:00000064
```

|Name|Typ|Daten|BESCHREIBUNG|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`FigPrj Project`|Standardname der Projekte dieses Typs.|
|`DisplayName`|REG_SZ|`#%IDS_PROJECT_TYPE%`|Die Ressourcen-ID des Namens, der von der Satelliten-DLL abgerufen werden soll, die unter Packages registriert ist.|
|`Package`|REG_SZ|`%CLSID_Package%`|Die Klassen-ID des VSPackage, das unter "Packages" registriert ist.|
|`ProjectTemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Standardpfad der Projektvorlagen Dateien. Dies sind die Dateien, die von der neuen Projektvorlage angezeigt werden.|
|`ItemTemplatesDir`|REG_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|Standardpfad der Projekt Element-Vorlagen Dateien. Dies sind die Dateien, die von der Vorlage Neues Element hinzufügen angezeigt werden.|
|`DisplayProjectFileExtensions`|REG_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|Ermöglicht der IDE das Implementieren des Dialog Felds **Öffnen** .|
|`PossibleProjectExtensions`|REG_SZ|`figp`|Wird von der IDE verwendet, um zu bestimmen, ob das geöffnete Projekt von diesem Projekttyp (projektfactory) verarbeitet wird. Das Format für mehr als einen Eintrag ist eine durch Semikolons getrennte Liste. Beispiel: "vdproj; VDP".|
|`DefaultProjectExtension`|REG_SZ|`.figp`|Wird von der IDE als standardmäßige Dateinamenerweiterung für den Save as-Vorgang verwendet.|
|`Filter Settings`|REG_DWORD|Verschiedene Informationen finden Sie in der folgenden Tabelle unter Anweisungen und Kommentare.|Diese Einstellungen werden verwendet, um die verschiedenen Filter zum Anzeigen von Dateien in Benutzeroberflächen-Dialogfeldern festzulegen.|
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Ressourcen-ID für Element Vorlagen hinzufügen.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Der Pfad der Projekt Elemente, die im Dialogfeld für die Vorlage " **Neues Element hinzufügen** " angezeigt werden.|
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Bestimmt die Sortierreihenfolge im Struktur Knoten von Dateien, die im Dialogfeld **Neues Element hinzufügen** angezeigt werden.|

 In der folgenden Tabelle werden die im vorherigen Codesegment verfügbaren Filteroptionen aufgeführt.

|Filter Option|BESCHREIBUNG|
|-------------------|-----------------|
|`CommonFindFilesFilter`|Gibt an, dass der Filter einer der allgemeinen Filter im Dialogfeld **in Dateien suchen** ist. Die allgemeinen Filter sind in der Filterliste aufgeführt, bevor die Filter als "Allgemein" gekennzeichnet sind.|
|`CommonOpenFilesFilter`|Gibt an, dass es sich bei dem Filter um einen der allgemeinen Filter im Dialogfeld **Datei öffnen** handelt. Die allgemeinen Filter sind in der Filterliste aufgeführt, bevor die Filter als "Allgemein" gekennzeichnet sind.|
|`FindInFilesFilter`|Gibt an, dass der Filter einer der Filter im Dialogfeld **in Dateien suchen** ist und nach den allgemeinen Filtern aufgeführt wird.|
|`NotOpenFileFilter`|Gibt an, dass der Filter nicht im Dialogfeld " **Datei öffnen** " verwendet wird.|
|`NotAddExistingItemFilter`|Gibt an, dass der Filter nicht im Dialogfeld **Vorhandenes Element** hinzufügen verwendet wird.|

 Wenn für einen Filter mindestens eines dieser Flags festgelegt ist, wird der Filter standardmäßig im Dialogfeld **Vorhandenes Element hinzufügen** und im Dialogfeld **Datei öffnen** nach dem Auflisten der allgemeinen Filter verwendet. Der Filter wird im Dialogfeld **in Dateien suchen** nicht verwendet.

 Alle folgenden Beispiele befinden sich in der Registrierung unter dem Schlüssel [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].

## <a name="example-4"></a>Beispiel 4

```
{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4} (The CLSID for Enterprise Projects)
\{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (CLSID for projects of this type)
   @="#7"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPrj\\FigPrjProjects"
   "SortPriority"=dword:00000029
   "NewProjectDialogOnly"=dword:00000000
```

|Name|Typ|Daten|BESCHREIBUNG|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|Ressourcen-ID für neue Projektvorlagen.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Standardpfad für Projekte des registrierten Projekt Typs.|
|`SortPriority`|REG_DWORD|`41 (x29)`|Legt die Sortierreihenfolge der im Dialogfeld "neue Projekte" angezeigten Projekte fest.|
|`NewProjectDialogOnly`|REG_DWORD|`0`|der Wert 0 gibt an, dass Projekte dieses Typs nur im Dialogfeld Neues Projekt angezeigt werden.|

 Alle folgenden Beispiele befinden sich in der Registrierung unter dem Schlüssel [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].

## <a name="example-5"></a>Beispiel 5

```
\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3} (CLSID for Miscellaneous Files projects)
   @="Miscellaneous Files Project"
\AddItemTemplates\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1
                                 (CLSID for Figures Project projects)
   @="#6"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"
   "SortPriority"=dword:00000064
```

|Name|Typ|Daten|BESCHREIBUNG|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|Keine|Standardwert, der angibt, dass die folgenden Einträge für die Projekt Einträge für verschiedene Dateien gelten.|
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Der Wert der Ressourcen-ID für die Vorlagen Dateien zum Hinzufügen neuer Elemente.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Standardpfad der Elemente, die im Dialogfeld **Neues Element hinzufügen** angezeigt werden.|
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Legt die Sortierreihenfolge für die Anzeige im Struktur Knoten des Dialog Felds **Neues Element hinzufügen** fest.|

 Das folgende Beispiel befindet sich in der Registrierung unter dem Schlüssel [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Menus].

## <a name="example-6"></a>Beispiel 6

```
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"
```

 Der Menüeintrag zeigt die IDE auf die Ressource, die zum Abrufen der Menü Informationen verwendet wurde. Wenn diese Daten in der Menü Datenbank zusammengeführt wurden, wird der gleiche Schlüssel im Abschnitt "mengegemergt" der Registrierung hinzugefügt. Das VSPackage sollte nichts im Abschnitt "mengegemergt" direkt ändern. Im Datenfeld in der folgenden Tabelle sind drei durch Trennzeichen getrennte Felder vorhanden. Das erste Feld identifiziert den vollständigen Pfad einer Menü Ressourcen Datei:

- Wenn das erste Feld weggelassen wird, wird die Menü Ressource aus der Satelliten-DLL geladen, die durch die VSPackage-GUID identifiziert wird.

  Das zweite Feld identifiziert eine Menü Ressourcen-ID des Typs ctmenu:

- Wenn die Ressourcen-ID angegeben wird und der Dateipfad vom ersten Parameter bereitgestellt wird, wird eine Menü Ressource aus dem vollständigen Dateipfad geladen.

- Wenn die Ressourcen-ID angegeben wird, der Dateipfad jedoch nicht ist, wird die Menü Ressource aus der Satelliten-DLL geladen.

- Wenn der vollständige Dateipfad angegeben wird und die Ressourcen-ID weggelassen wird, wird die zu ladende Datei als CTO-Datei erwartet.

  Das letzte Feld identifiziert die Versionsnummer für die ctmenu-Ressource. Sie können das Menü erneut zusammenführen, indem Sie die Versionsnummer ändern.

|Name|Typ|Daten|BESCHREIBUNG|
|----------|----------|----------|-----------------|
|% CLSID_Package%|REG_SZ|`,1000,1`|Die Ressource, mit der die Menü Informationen abgerufen werden sollen.|

 Alle folgenden Beispiele befinden sich in der Registrierung unter dem Schlüssel [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\NewProjectTemplates].

```
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)
   @="#7"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"
   "SortPriority"=dword:00000029
   "NewProjectDialogOnly"=dword:00000000
```

|Name|Typ|Daten|BESCHREIBUNG|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|Ressourcen-ID-Wert für die Abbildungen Projekt neue Projektvorlagen.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Der Standardpfad des Verzeichnisses für neue Projekte. Elemente in diesem Verzeichnis werden im Dialogfeld **Assistent für neue Projekte** angezeigt.|
|`SortPriority`|REG_DWORD|`41 (x29)`|Legt die Reihenfolge fest, in der Projekte im Struktur Knoten des Dialog Felds **Neues Projekt** angezeigt werden.|
|`NewProjectDialogOnly`|REG_DWORD|`0`|der Wert 0 gibt an, dass Projekte dieses Typs nur im Dialogfeld **Neues Projekt** angezeigt werden.|

 Das folgende Beispiel befindet sich in der Registrierung unter dem Schlüssel [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\InstalledProducts].

```
\FiguresProductSample
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"
   "UseInterface"=dword:00000001
```

|Name|Typ|Daten|BESCHREIBUNG|
|----------|----------|----------|-----------------|
|`Package`|REG_SZ|`%CLSID_Package%`|Die Klassen-ID des registrierten VSPackages.|
|`UseInterface`|REG_DWORD|`1`|der Wert 1 gibt an, dass die Benutzeroberfläche verwendet wird, um mit diesem Projekt zu interagieren. 0 gibt an, dass keine UI-Schnittstelle vorhanden ist.|

 Die VSZ-Dateien, die neue Projekttypen steuern, enthalten häufig einen RELATIVE_PATH Eintrag. Dieser Pfad ist relativ zum Pfad, der unter "\productdir Entry of the Project Type" im folgenden Setup Schlüssel angegeben ist:

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup

 Die Projektvorlagen für Enterprise Frameworks fügen beispielsweise die folgenden Registrierungseinträge hinzu:

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup\EF\ProductDir = c:\Programme\Microsoft Visual studio\enterpriseframeworks\

 Das heißt, wenn Sie einen PROJECT_TYPE = EF-Eintrag in die VSZ-Datei einschließen, sucht die Umgebung Ihre VSZ-Dateien im zuvor angegebenen productdir-Verzeichnis.

## <a name="see-also"></a>Weitere Informationen
- [Prüfliste: Erstellen neuer Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Elemente eines Projektmodells](../../extensibility/internals/elements-of-a-project-model.md)
- [Erstellen von Projektinstanzen mithilfe von Projektfactorys](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
