---
title: CreateVisualBasicManifestResourceName-Aufgabe | Microsoft-Dokumentation
description: Verwenden Sie die MSBuild-Aufgabe „CreateVisualBasicManifestResourceName“, um anhand eines RESX-Dateinamens oder einer anderen Ressource einen Visual Basic-Manifestnamen zu erstellen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CreateVisualBasicManifestResourceName task
- CreateVisualBasicManifestResourceName task [MSBuild]
ms.assetid: 251c47b9-de32-414b-a138-bf45290af12e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ba80c4d52491a70a7bb8e294c9dd6ca2c9664ec3
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796731"
---
# <a name="createvisualbasicmanifestresourcename-task"></a>CreateVisualBasicManifestResourceName-Aufgabe

Erstellt einen Manifestnamen im Visual Basic-Stil aus einem angegebenen *RESX* -Dateinamen oder aus einer anderen Ressource.

## <a name="parameters"></a>Parameter

 In der folgenden Tabelle werden die Parameter der Aufgabe [CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md) beschrieben.

| Parameter | Beschreibung |
| - | - |
| `ManifestResourceNames` | Schreibgeschützter <xref:Microsoft.Build.Framework.ITaskItem> `[]`-Ausgabeparameter<br /><br /> Die resultierenden Manifestnamen |
| `ResourceFiles` | Erforderlicher `String`-Parameter.<br /><br /> Der Name der Ressourcendatei, über die der Visual Basic-Manifestname erstellt werden soll. |
| `RootNamespace` | Optionaler `String`-Parameter.<br /><br /> Der Stammnamespace der Ressourcendatei, der normalerweise aus der Projektdatei übernommen wird. Kann `null` sein. |
| `PrependCultureAsDirectory` | Optionaler `Boolean`-Parameter.<br /><br /> Wenn der Wert `true` ist, wird der Name der Kultur als Verzeichnisname unmittelbar vor dem Manifestressourcennamen hinzugefügt. Der Standardwert ist `true`. |
| `ResourceFilesWithManifestResourceNames` | Optionaler schreibgeschützter `String`-Ausgabeparameter<br /><br /> Gibt den Namen der Ressourcendatei zurück, die jetzt den Manifestressourcennamen enthält |

## <a name="remarks"></a>Hinweise

 Die Aufgabe [CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md) bestimmt den richtigen Manifestressourcennamen, der einer bestimmten *RESX* - oder einer anderen Ressourcendatei zugewiesen werden soll. Die Aufgabe stellt einen logischen Namen für eine Ressourcendatei bereit und fügt sie dann an einen Ausgabeparameter als Metadatenelement an.

 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Weitere Informationen

- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
