---
title: Arbeitsbereichs Erstellung in Visual Studio | Microsoft-Dokumentation
description: Erfahren Sie mehr über den Extender, der indizierte und Datei Kontext Daten für einen Arbeitsbereich bereitstellt, um ein offenes Ordner Szenario zu unterstützen
ms.custom: SEO-VS-2020
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: e44c2398b873bbca95c971ae1b44ac3de831b2ae
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877103"
---
# <a name="workspace-build"></a>Arbeitsbereichbuild

Die Buildunterstützung in Szenarios für [Offene Ordner](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) erfordert, dass ein Extender [indizierte](workspace-indexing.md) und [Datei Kontext](workspace-file-contexts.md) Daten für den [Arbeitsbereich](workspaces.md)sowie die auszuführende Buildaktion bereitstellt.

Im folgenden finden Sie einen Überblick darüber, was Ihre Erweiterung benötigt.

## <a name="build-file-context"></a>Builddateikontext

- Anbieterfactory
  - `ExportFileContextProviderAttribute` Attribut mit `supportedContextTypeGuids` als alle anwendbaren `string` Konstanten aus `BuildContextTypes`
  - Implementiert `IWorkspaceProviderFactory<IFileContextProvider>`
  - Datei Kontext Anbieter
    - Zurückgeben eines `FileContext` für jeden unterstützten Buildvorgang und jede Konfiguration
      - Extraktion von `contextType` aus <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes>
      - `context` implementiert <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> mit der- `Configuration` Eigenschaft als Buildkonfiguration (z. b `"Debug|x86"` `"ret"` ., oder, `null` Falls nicht zutreffend). Verwenden Sie alternativ eine Instanz von <xref:Microsoft.VisualStudio.Workspace.Build.BuildConfigurationContext> . Der Konfigurations Wert **muss** mit der Konfiguration aus dem Daten Wert für indizierte Dateien identisch sein.

## <a name="indexed-build-file-data-value"></a>Datenwert der indizierten Builddatei

- Anbieterfactory
  - `ExportFileScannerAttribute` Attribut mit `IReadOnlyCollection<FileDataValue>` als unterstützter Typ
  - Implementiert `IWorkspaceProviderFactory<IFileScanner>`
- Dateiscanner auf `ScanContentAsync<T>`
  - Gibt Daten zurück, wenn `FileScannerTypeConstants.FileDataValuesType` das Typargument ist.
  - Gibt einen Datei Datenwert für jede Konfiguration zurück, die mit erstellt wurde:
    - `type` as `BuildConfigurationContext.ContextTypeGuid`
    - `context` als Buildkonfiguration (z `"Debug|x86"` . b `"ret"` ., oder, `null` Falls nicht zutreffend). Dieser Wert **muss** mit der Konfiguration aus dem Datei Kontext identisch sein.

## <a name="build-file-context-action"></a>Datei Kontext Aktion erstellen

- Anbieterfactory
  - `ExportFileContextActionProvider` Attribut mit `supportedContextTypeGuids` als alle anwendbaren `string` Konstanten aus `BuildContextTypes`
  - Implementiert `IWorkspaceProviderFactory<IFileContextActionProvider>`
- Aktions Anbieter für `IFileContextActionProvider.GetActionsAsync`
  - Gibt einen zurück `IFileContextAction` , der mit dem angegebenen Wert übereinstimmt. `FileContext.ContextType`
- Datei Kontext Aktion
  - Implementiert `IFileContextAction` und <xref:Microsoft.VisualStudio.Workspace.Extensions.VS.IVsCommandItem>
  - `CommandGroup` Rückgabe von Eigenschaften `16537f6e-cb14-44da-b087-d1387ce3bf57`
  - `CommandId` ist `0x1000` für Build, `0x1010` for Rebuild oder `0x1020` for clean

>[!NOTE]
>Da der `FileDataValue` indiziert werden muss, wird zwischen dem Öffnen des Arbeitsbereichs und dem Punkt, an dem die Datei auf vollständige Buildfunktionen überprüft wird, eine gewisse Zeitspanne angezeigt. Die Verzögerung wird beim ersten Öffnen eines Ordners angezeigt, weil kein zuvor zwischen gespeicherter Index vorhanden ist.

## <a name="reporting-messages-from-a-build"></a>Melden von Meldungen aus einem Build

Der Build kann auf eine von zwei Arten Informationen, Warnungen und Fehlermeldungen an Benutzer überweisen. Die einfache Möglichkeit ist die Verwendung von <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> und die Bereitstellung eines <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage> , wie folgt:

```csharp
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Build;

private static void OutputBuildMessage(IWorkspace workspace)
{
    IBuildMessageService buildMessageService = workspace.GetBuildMessageService();

    if (buildMessageService != null)
    {
      // Example error build message. See the documentation for BuildMessage for more information.
      var message = new BuildMessage()
      {
          Type = BuildMessage.TaskType.Error,
          Code = "MY1001",
          TaskText = "This is a sample error",
          ProjectFile = "buildfile.bld",
          File = "sourcefile.src"
          LogMessage = $"This is sample text that will only go to the Build output window pane.\n"

          // And any other properties to set
      };

      buildMessageService.ReportBuildMessages(new BuildMessage[] { message });
    }
}
```

`BuildMessage.Type` und `BuildMessage.LogMessage` steuern das Verhalten, bei dem dem Benutzerinformationen angezeigt werden. `BuildMessage.TaskType`Bei einem anderen Wert als `None` wird ein **Fehlerliste** Eintrag mit den angegebenen Details erzeugt. `LogMessage` wird im Bereich **Build** des Fensters **Ausgabe** Tool immer ausgegeben.

Alternativ können Erweiterungen direkt mit dem Bereich **Fehlerliste** oder **Build** interagieren. In Versionen vor Visual Studio 2017, Version 15,7, ist ein Fehler vorhanden, bei dem das- `pszProjectUniqueName` Argument von <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane2.OutputTaskItemStringEx2*> ignoriert wird.

>[!WARNING]
>Aufrufer von `IFileContextAction.ExecuteAsync` können beliebige zugrunde liegende Implementierungen für das Argument bereitstellen `IProgress<IFileContextActionProgressUpdate>` . Rufen Sie niemals `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` direkt auf. Zurzeit gibt es keine allgemeinen Richtlinien für die Verwendung dieses Arguments. diese Richtlinien können jedoch geändert werden.

## <a name="build-related-apis"></a>Erstellen verwandter APIs

- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> stellt buildkonfigurationsdetails bereit.
- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> zeigt <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage> Benutzer an.

## <a name="tasksvsjson-and-launchvsjson"></a>tasks.vs.json und launch.vs.js

Weitere Informationen zum Erstellen einer tasks.vs.jsoder launch.vs.jsin einer Datei finden Sie unter [Anpassen von Build-und debugtasks](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

## <a name="next-steps"></a>Nächste Schritte

* [Language Server-Protokoll](language-server-protocol.md) : erfahren Sie, wie Sie Sprachserver in Visual Studio integrieren.