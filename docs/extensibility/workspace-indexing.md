---
title: Arbeitsbereichindizierung in Visual Studio | Microsoft-Dokumentation
description: Erfahren Sie mehr über die arbeitsbereichindizierung, die Sammlung und persistente Speicherung von Daten zur Unterstützung umfassender IDE-Features für einen geöffneten Ordner Arbeitsbereich.
ms.custom: SEO-VS-2020
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 6b5c069ce3ae993f2d2371bffae3ac58b286fa70
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877051"
---
# <a name="workspace-indexing"></a>Arbeitsbereichindizierung

In einer Projekt Mappe sind Projektsysteme für das Bereitstellen von Funktionen für das Erstellen, Debuggen, das Suchen von **goto** -Symbolen und vieles mehr verantwortlich. Projektsysteme können dies tun, da Sie die Beziehung und Funktionen von Dateien innerhalb eines Projekts verstehen. Der Arbeitsbereich " [Ordner öffnen](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) " benötigt die gleichen Erkenntnisse, um auch umfangreiche IDE-Features bereitzustellen. Die Sammlung und persistente Speicherung dieser Daten ist ein Prozess namens arbeitsbereichindizierung. Diese indizierten Daten können durch eine Reihe von asynchronen APIs abgefragt werden. Extender können an dem Indizierungsprozess teilnehmen, indem Sie die bereitstellen <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScanner> , die bestimmte Dateitypen verarbeiten können.

## <a name="types-of-indexed-data"></a>Typen von indizierten Daten

Es gibt drei Arten von Daten, die indiziert werden. Beachten Sie, dass der von Datei Scannern erwartete Typ mit dem vom Index deserialisierten Typ abweicht.

|Daten|Datei Scannertyp|Index Abfrage Ergebnistyp|Verwandte Typen|
|--|--|--|--|
|Referenzen|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfo>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfoType>|
|Symbole|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinition>|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinitionSearchResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.ISymbolService>sollte anstelle von für Abfragen verwendet werden. `IIndexWorkspaceService`|
|Datenwerte|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataValue>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataResult`1>||

## <a name="querying-for-indexed-data"></a>Abfragen indizierter Daten

Für den Zugriff auf persistente Daten sind zwei asynchrone Typen verfügbar. Der erste ist bis <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceData> . Er bietet grundlegenden Zugriff auf die Daten der einzelnen Dateien `FileReferenceResult` und `FileDataResult` und speichert die Ergebnisse zwischen. Die zweite ist die, die keine Zwischenspeicherung <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceService> verwendet, sondern mehr Abfragefunktionen ermöglicht.

```csharp
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Indexing;

private static IIndexWorkspaceData GetCachedIndexedData(IWorkspace workspace)
{
    // Gets access to indexed data wrapped in a cache.
    return workspace?.GetIndexWorkspaceDataService()?.CreateIndexWorkspaceData();
}

private static IIndexWorkspaceService GetDirectIndexedData(IWorkspace workspace)
{
    // Gets direct access to indexed data.
    // Can also be casted to IIndexWorkspaceService2.
    return workspace?.GetIndexWorkspaceService();
}
```

## <a name="participating-in-indexing"></a>Beteiligung an der Indizierung

Die arbeitsbereichindizierung folgt ungefähr der folgenden Reihenfolge:

1. Ermittlung und Persistenz von Dateisystem Entitäten im Arbeitsbereich (nur bei der ersten öffnenden Überprüfung).
1. Pro Datei wird der übereinstimmende Anbieter mit der höchsten Priorität aufgefordert, nach `FileReferenceInfo` s zu suchen.
1. Pro Datei wird der übereinstimmende Anbieter mit der höchsten Priorität aufgefordert, nach `SymbolDefinition` s zu suchen.
1. Pro Datei werden alle Anbieter nach s gestellt `FileDataValue` .

Erweiterungen können einen Scanner exportieren, indem Sie `IWorkspaceProviderFactory<IFileScanner>` den Typ mit implementieren und exportieren <xref:Microsoft.VisualStudio.Workspace.Indexing.ExportFileScannerAttribute> . Das `SupportedTypes` Attribut Argument muss ein oder mehrere Werte aus sein <xref:Microsoft.VisualStudio.Workspace.Indexing.FileScannerTypeConstants> . Ein Beispiel für einen Scanner finden Sie im vs [SDK-Beispiel.](https://github.com/Microsoft/VSSDK-Extensibility-Samples/blob/master/Open_Folder_Extensibility/C%23/SymbolScannerSample/TxtFileSymbolScanner.cs)

> [!WARNING]
> Exportieren Sie keinen Dateiscanner, der den- `FileScannerTypeConstants.FileScannerContentType` Typ unterstützt. Sie wird nur für interne Microsoft-Zwecke verwendet.

In erweiterten Situationen kann eine Erweiterung eine beliebige Gruppe von Dateitypen dynamisch unterstützen. Anstatt den MEF-Export `IWorkspaceProviderFactory<IFileScanner>` zu exportieren, kann eine Erweiterung exportieren `IWorkspaceProviderFactory<IFileScannerProvider>` . Wenn die Indizierung beginnt, wird dieser Factorytyp importiert, instanziiert und seine- <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScannerProvider.GetSymbolScannersAsync%2A> Methode aufgerufen. `IFileScanner` Instanzen, die einen beliebigen Wert von unterstützen `FileScannerTpeConstants` , werden berücksichtigt, nicht nur Symbole.

## <a name="next-steps"></a>Nächste Schritte

* [Arbeitsbereiche und Sprachdienste](workspace-language-services.md) : erfahren Sie, wie Sie Sprachdienste in einen geöffneten Ordner Arbeitsbereich integrieren.
* Der [Arbeitsbereich Build](workspace-build.md) : der Ordner wird geöffnet und unterstützt Buildsysteme wie MSBuild und Makefiles.