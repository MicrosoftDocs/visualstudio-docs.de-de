---
title: Erstellen von Weiterleitungsprotokollierungen | Microsoft-Dokumentation
description: Erstellen Sie MSBuild-Weiterleitungsprotokollierungen, um die Protokollierungseffizienz zu verbessern. Dazu wählen Sie die Ereignisse aus, die Sie beim Erstellen von Projekten überwachen möchten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, forwarding loggers
- MSBuild, logging
ms.assetid: 3aebf9c8-b62c-4cb2-b2d6-8cdfcd369a24
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0ffe175d9ea73640cae1197fe91656d3565525f6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901363"
---
# <a name="create-forwarding-loggers"></a>Erstellen von Weiterleitungsprotokollierungen

Weiterleitungsprotokollierungen verbessern die Protokollierungseffizienz, da Sie wählen können, welche Ereignisse Sie gerne protokollieren möchten, wenn Sie Projekte auf einem System mit mehreren Prozessoren erstellen. Wenn Sie Weiterleitungsprotokollierungen aktivieren, können Sie vermeiden, dass nicht benötigte Ereignisse die zentrale Protokollierung überlasten, die Buildzeit verlangsamen und dafür sorgen, dass das Protokoll unübersichtlich wird.

 Sie können entweder zuerst die <xref:Microsoft.Build.Framework.IForwardingLogger>-Schnittstelle und dann manuell die Methode implementieren oder die <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger>-Klasse und deren vorkonfigurierte Methoden verwenden, um eine Weiterleitungsprotokollierung zu erstellen. (Letztere Methode sollte für die meisten Anwendungen ausreichend sein.)

## <a name="register-events-and-respond-to-them"></a>Registrieren von Ereignissen und Reaktion auf diese

 Eine Weiterleitungsprotokollierung sammelt Informationen zu Buildereignissen, die von der zweiten Build-Engine gemeldet werden. Bei dieser Build-Engine handelt es sich um einen Workerprozess, der von dem Hauptbuildprozess während eines Builds auf einem System mit mehreren Prozessoren erstellt wird. Anschließend wählt die Weiterleitungsprotokollierung anhand Ihrer Anweisungen Ereignisse aus, die sie an die zentrale Protokollierung weiterleitet.

 Sie müssen Weiterleitungsprotokollierungen registrieren, damit diese Ereignisse behandeln, die Sie gerne überwachen möchten. Protokollierungen müssen die <xref:Microsoft.Build.Utilities.Logger.Initialize%2A>-Methode außer Kraft setzen, um sich für Ereignisse zu registrieren. Jetzt beinhaltet diese Methode einen optionalen `nodecount`-Parameter, der auf die Anzahl von Prozessoren in dem System festgelegt werden kann. (Der Standardwert ist 1.)

 Sie können beispielsweise Ereignisse wie <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> oder <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> überwachen.

 In einer Umgebung mit mehreren Prozessoren ist es sehr wahrscheinlich, dass Ereignismeldungen nicht in der richtigen Reihenfolge empfangen werden. Aus diesem Grund müssen Sie die Ereignisse überprüfen, indem Sie in der Weiterleitungsprotokollierung den Ereignishandler verwenden und ihn so programmieren, dass er bestimmen kann, welche Ereignisse an den Redirectordienst übergeben werden sollen, damit dieser sie an die zentrale Protokollierung weiterleitet. Dafür können Sie die <xref:Microsoft.Build.Framework.BuildEventContext>-Klasse verwenden, die jeder Meldung angefügt wird, um so die Identifizierung von Ereignissen, die Sie weiterleiten möchten, zu vereinfachen und anschließend die Namen der Ereignisse an die <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger>-Klasse (oder an eine Unterklasse dieser Klasse) zu übergeben. Wenn Sie diese Methode verwenden, ist keine spezielle Codierung erforderlich, um Ereignisse weiterzuleiten.

## <a name="specify-a-forwarding-logger"></a>Angeben einer Weiterleitungsprotokollierung

 Nachdem aus einer Weiterleitungsprotokollierung eine Assembly erstellt wurde, müssen Sie MSBuild mitteilen, diese während der Builderstellung zu verwenden. Verwenden Sie dafür die Optionen `-FileLogger`, `-FileLoggerParameters` und `-DistributedFileLogger` mit *MSBuild.exe* zusammen. Die Option `-FileLogger` teilt *MSBuild.exe* mit, dass die Protokollierung direkt angefügt ist. Der Schalter `-DistributedFileLogger` deutet darauf hin, dass eine Protokolldatei pro Knoten vorhanden ist. Verwenden Sie den Schalter `-FileLoggerParameters`, um Parameter für die Weiterleitungsprotokollierung festzulegen. Weitere Informationen zu diesen Optionen und anderen Optionen von *MSBuild.exe* finden Sie unter [Command-line reference (Befehlszeilenreferenz)](../msbuild/msbuild-command-line-reference.md).

## <a name="multi-processor-aware-loggers"></a>Multiprozessorfähige Protokollierungen

 Wenn Sie ein Projekt auf einem System mit mehreren Prozessoren erstellen, überlappen die Buildmeldungen der Prozessoren nicht automatisch in einer einheitlichen Sequenz. Stattdessen müssen Sie mit der <xref:Microsoft.Build.Framework.BuildEventContext>-Klasse, die an jede Meldung angefügt wird, das Gruppieren von Meldungen als Priorität festlegen. Weitere Informationen zur Builderstellung mit mehreren Prozessoren finden Sie unter [Logging in a Multi-Processor Environment (Protokollierung in einer Umgebung mit mehreren Prozessoren)](../msbuild/logging-in-a-multi-processor-environment.md).

## <a name="see-also"></a>Weitere Informationen:

- [Erhalten von Buildprotokollen](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Buildprotokollierungen](../msbuild/build-loggers.md)
- [Protokollierung in einer Multiprozessorumgebung](../msbuild/logging-in-a-multi-processor-environment.md)