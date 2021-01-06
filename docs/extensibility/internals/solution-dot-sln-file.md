---
title: Lösung (. Sln)-Datei
description: Erfahren Sie mehr über die SLN-Datei, bei der es sich um eine der Dateien handelt, die Zustandsinformationen für ein Projekt in Visual Studio verwaltet.
ms.custom: SEO-VS-2020
ms.date: 03/15/2019
ms.topic: conceptual
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 903b33d72d3a97eb4ed3f7ad0bc865999bee54cf
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877506"
---
# <a name="solution-sln-file"></a>Projektmappendatei (. sln)

Eine Lösung ist eine Struktur zum Organisieren von Projekten in Visual Studio. Die Lösung verwaltet die Zustandsinformationen für Projekte in zwei Dateien:

- SLN-Datei (Text basiert, Shared)

- SUO-Datei (binäre, benutzerspezifische Projektmappenoptionen)

Weitere Informationen zu suo-Dateien finden Sie unter [Solution User Options (. Suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md).

Wenn das VSPackage als Ergebnis eines referenzierten in der SLN-Datei geladen wird, ruft die Umgebung <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> auf, um in der SLN-Datei zu lesen.

Die SLN-Datei enthält textbasierte Informationen, die die Umgebung verwendet, um die Name-Wert-Parameter für die persistenten Daten und die Projekt-VSPackages zu suchen und zu laden, auf die verwiesen wird. Wenn ein Benutzer eine Projekt Mappe öffnet, durchläuft die Umgebung `preSolution` die `Project` Informationen, und `postSolution` in der SLN-Datei, um die Projekt Mappe, die Projekte in der Projekt Mappe und alle beibehaltenen Informationen, die an die Lösung angefügt sind, zu laden.

Die Datei jedes Projekts enthält zusätzliche Informationen, die von der Umgebung gelesen werden, um die Hierarchie mit den Elementen dieses Projekts aufzufüllen. Die Daten Persistenz der Hierarchie wird vom Projekt gesteuert. Die Daten werden normalerweise nicht in der SLN-Datei gespeichert, obwohl Sie die Projektinformationen absichtlich in die SLN-Datei schreiben können, wenn Sie sich dafür entscheiden. Weitere Informationen zur Persistenz finden Sie unter [Projekt Persistenz](../../extensibility/internals/project-persistence.md) und [Öffnen und Speichern von Projekt Elementen](../../extensibility/internals/opening-and-saving-project-items.md).

## <a name="file-header"></a>Dateiheader

Der Header einer SLN-Datei sieht wie folgt aus:

::: moniker range="vs-2017"

```
Microsoft Visual Studio Solution File, Format Version 12.00
# Visual Studio 15
VisualStudioVersion = 15.0.26730.15
MinimumVisualStudioVersion = 10.0.40219.1
```

### <a name="definitions"></a>Definitionen

`Microsoft Visual Studio Solution File, Format Version 12.00`\
Standard Header, der die Dateiformat Version definiert.

`# Visual Studio 15`\
Die Hauptversion von Visual Studio, die (zuletzt) diese Projektmappendatei gespeichert hat. Diese Informationen steuern die Versionsnummer im Lösungs Symbol.

`VisualStudioVersion = 15.0.26730.15`\
Die Vollversion von Visual Studio, von der (zuletzt) die Projektmappendatei gespeichert wurde. Wenn die Projektmappendatei mit einer neueren Version von Visual Studio gespeichert wird, die die gleiche Hauptversion aufweist, wird dieser Wert nicht aktualisiert, um die Abwanderung in Projektmappendateien zu verringern.

`MinimumVisualStudioVersion = 10.0.40219.1`\
Die minimale (älteste) Version von Visual Studio, mit der diese Projektmappendatei geöffnet werden kann.

::: moniker-end

::: moniker range=">=vs-2019"

```
Microsoft Visual Studio Solution File, Format Version 12.00
# Visual Studio Version 16
VisualStudioVersion = 16.0.28701.123
MinimumVisualStudioVersion = 10.0.40219.1
```

### <a name="definitions"></a>Definitionen

`Microsoft Visual Studio Solution File, Format Version 12.00`\
Standard Header, der die Dateiformat Version definiert.

`# Visual Studio Version 16`\
Die Hauptversion von Visual Studio, die (zuletzt) diese Projektmappendatei gespeichert hat. Diese Informationen steuern die Versionsnummer im Lösungs Symbol.

`VisualStudioVersion = 16.0.28701.123`\
Die Vollversion von Visual Studio, von der (zuletzt) die Projektmappendatei gespeichert wurde. Wenn die Projektmappendatei mit einer neueren Version von Visual Studio gespeichert wird, die die gleiche Hauptversion aufweist, wird dieser Wert nicht aktualisiert, um die Änderung in der Datei zu verringern.

`MinimumVisualStudioVersion = 10.0.40219.1`\
Die minimale (älteste) Version von Visual Studio, mit der diese Projektmappendatei geöffnet werden kann.

::: moniker-end

## <a name="file-body"></a>Datei Text

Der Text einer SLN-Datei besteht aus mehreren Abschnitten mit der Bezeichnung `GlobalSection` , wie folgt:

```
Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1", "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"
EndProject
Global
  GlobalSection(SolutionNotes) = postSolution
  EndGlobalSection
  GlobalSection(SolutionConfiguration) = preSolution
       ConfigName.0 = Debug
       ConfigName.1 = Release
  EndGlobalSection
  GlobalSection(ProjectDependencies) = postSolution
  EndGlobalSection
  GlobalSection(ProjectConfiguration) = postSolution
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.ActiveCfg = Debug|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.Build.0 = Debug|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.ActiveCfg = Release|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.Build.0 = Release|x86
  EndGlobalSection
  GlobalSection(ExtensibilityGlobals) = postSolution
  EndGlobalSection
  GlobalSection(ExtensibilityAddIns) = postSolution
  EndGlobalSection
EndGlobal
```

Zum Laden einer Projekt Mappe führt die Umgebung die folgenden Aufgaben aus:

1. Die Umgebung liest den globalen Abschnitt der SLN-Datei und verarbeitet alle markierten Abschnitte `preSolution` . In dieser Beispieldatei gibt es eine solche Anweisung:

   ```
   GlobalSection(SolutionConfiguration) = preSolution
        ConfigName.0 = Debug
        ConfigName.1 = Release
   ```

   Wenn die Umgebung das `GlobalSection('name')` Tag liest, ordnet Sie den Namen mithilfe der Registrierung einem VSPackage zu. Der Schlüssel Name muss in der Registrierung unter [HKLM \\<Application ID Registry root \> \solutionpersistence\aggregateguids] vorhanden sein. Der Standardwert der Schlüssel ist die Paket-GUID (REG_SZ) des VSPackage, das die Einträge geschrieben hat.

2. Die Umgebung lädt das VSPackage, ruft das `QueryInterface` VSPackage für die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> Schnittstelle auf und ruft die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> Methode mit den Daten im-Abschnitt auf, damit das VSPackage die Daten speichern kann. Die Umgebung wiederholt diesen Vorgang für jeden `preSolution` Abschnitt.

3. Die Umgebung durchläuft die Projekt Beibehaltungs Blöcke. In diesem Fall ist ein Projekt vorhanden.

   ```
   Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",
   "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"
   EndProject
   ```

   Diese Anweisung enthält die eindeutige Projekt-GUID und die Projekttyp-GUID. Diese Informationen werden von der Umgebung verwendet, um die Projektdateien zu suchen, die zur Projekt Mappe gehören, und das VSPackage, das für jedes Projekt erforderlich ist. Die Projekt-GUID wird an weitergegeben, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> um das spezifische VSPackage zu laden, das mit dem Projekt verknüpft ist, und das Projekt wird dann vom VSPackage geladen. In diesem Fall ist das VSPackage, das für dieses Projekt geladen wird, Visual Basic.

   Jedes Projekt kann eine eindeutige Projekt Instanz-ID persistent speichern, damit auf Sie nach Bedarf von anderen Projekten in der Projekt Mappe zugegriffen werden kann. Wenn sich die Projekt Mappe und die Projekte unter Quell Code Verwaltung befinden, sollte der Pfad zum Projekt im Idealfall relativ zum Pfad der Projekt Mappe sein. Wenn die Projekt Mappe zum ersten Mal geladen wird, dürfen sich die Projektdateien nicht auf dem Computer des Benutzers befinden. Wenn die Projektdatei auf dem Server relativ zur Projektmappendatei gespeichert ist, ist es relativ einfach, die Projektdatei zu finden und auf den Computer des Benutzers zu kopieren. Anschließend werden die restlichen Dateien kopiert und geladen, die für das Projekt benötigt werden.

4. Basierend auf den Informationen, die im Projektabschnitt der SLN-Datei enthalten sind, lädt die Umgebung jede Projektdatei. Das Projekt selbst ist dann dafür verantwortlich, die Projekt Hierarchie aufzufüllen und alle in der Tabelle befindlichen Projekte zu laden.

5. Nachdem alle Abschnitte der SLN-Datei verarbeitet wurden, wird die Projekt Mappe in Projektmappen-Explorer angezeigt und kann vom Benutzer geändert werden.

Wenn ein VSPackage, das ein Projekt in der Projekt Mappe implementiert, nicht geladen werden kann, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> wird die-Methode aufgerufen, und jedes andere Projekt in der Projekt Mappe erhält die Möglichkeit, Änderungen zu ignorieren, die Sie möglicherweise beim Laden vorgenommen haben. Wenn Analyse-Fehler auftreten, werden so viele Informationen wie möglich in den Projektmappendateien beibehalten, und in der Umgebung wird ein Dialogfeld angezeigt, in dem der Benutzer darauf gewarnt wird, dass die Lösung beschädigt ist

Wenn die Projekt Mappe gespeichert oder geschlossen wird, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> wird die-Methode aufgerufen und an die-Hierarchie übergeben, um festzustellen, ob an der Projekt Mappe Änderungen vorgenommen wurden, die in die SLN-Datei eingegeben werden müssen. Ein NULL-Wert, der an in übermittelt wird, gibt an, `QuerySaveSolutionProps` <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS> dass Informationen für die Lösung persistent gespeichert werden. Wenn der Wert nicht NULL ist, gelten die beibehaltenen Informationen für ein bestimmtes Projekt, das durch den Zeiger auf die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Schnittstelle bestimmt wird.

Wenn Informationen gespeichert werden sollen, wird die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> Schnittstelle mit einem Zeiger auf die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> Methode aufgerufen. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> -Methode wird dann von der Umgebung aufgerufen, um die Name-Wert-Paare aus der `IPropertyBag` Schnittstelle abzurufen und die Informationen in die SLN-Datei zu schreiben.

`SaveSolutionProps` -und- `WriteSolutionProps` Objekte werden rekursiv von der Umgebung aufgerufen, um Informationen abzurufen, die von der Schnittstelle gespeichert werden, `IPropertyBag` bis alle Änderungen in die SLN-Datei eingegeben wurden. Auf diese Weise können Sie sicherstellen, dass die Informationen mit der Lösung persistent gespeichert werden und beim nächsten Öffnen der Lösung verfügbar sind.

Jedes geladene VSPackage wird aufgezählt, um festzustellen, ob es Elemente enthält, die in der SLN-Datei gespeichert werden sollen. Es ist nur während der Ladezeit, dass die Registrierungsschlüssel abgefragt werden. Die Umgebung kennt alle geladenen Pakete, da Sie sich im Speicher befinden, wenn die Projekt Mappe gespeichert wird.

Nur die SLN-Datei enthält Einträge in den `preSolution` `postSolution` Abschnitten und. Die SUO-Datei enthält keine ähnlichen Abschnitte, da diese Informationen für die Lösung erforderlich sind, um ordnungsgemäß geladen zu werden. Die SUO-Datei enthält benutzerspezifische Optionen, z. b. private Notizen, die nicht für die Freigabe oder Platzierung in der Quell Code Verwaltung vorgesehen sind.

## <a name="see-also"></a>Weitere Informationen

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- [Datei mit Benutzeroptionen in Projektmappen (SUO)](../../extensibility/internals/solution-user-options-dot-suo-file.md)
- [Lösungen](../../extensibility/internals/solutions-overview.md)
