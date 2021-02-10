---
title: CreateCSharpManifestResourceName-Aufgabe | Microsoft-Dokumentation
description: Verwenden Sie die MSBuild-Aufgabe „CreateCSharpManifestResourceName“, um anhand eines RESX-Dateinamens oder einer anderen Ressource einen C#-Manifestnamen zu erstellen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CreateCSharpManifestResourceName task
- CreateCSharpManifestResourceName task [MSBuild]
ms.assetid: 2ace88c1-d757-40a7-8158-c1d3f5ff0511
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3406a5f61c9a4aa1c9e2a3c6388741c3ae0fa0f0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901453"
---
# <a name="createcsharpmanifestresourcename-task"></a>CreateCSharpManifestResourceName-Aufgabe

Erstellt einen Manifestnamen im C#-Stil aus einem angegebenen *RESX*-Dateinamen oder aus einer anderen Ressource.

## <a name="parameters"></a>Parameter

 Die folgende Tabelle beschreibt die Parameter der Aufgabe [CreateCSharpManifestResourceName](../msbuild/createcsharpmanifestresourcename-task.md).

| Parameter | Beschreibung |
| - | - |
| `ManifestResourceNames` | Schreibgeschützter <xref:Microsoft.Build.Framework.ITaskItem> `[]`-Ausgabeparameter<br /><br /> Die resultierenden Manifestnamen |
| `ResourceFiles` | Erforderlicher `String`-Parameter.<br /><br /> Der Name der Ressourcendatei, über die der C#-Manifestname erstellt werden soll. |
| `RootNamespace` | Optionaler `String`-Parameter.<br /><br /> Der Stammnamespace der Ressourcendatei, der normalerweise aus der Projektdatei übernommen wird. Kann `null` sein. |
| `PrependCultureAsDirectory` | Optionaler `Boolean`-Parameter.<br /><br /> Wenn der Wert `true` ist, wird der Name der Kultur als Verzeichnisname unmittelbar vor dem Manifestressourcennamen hinzugefügt. Der Standardwert ist `true`. |
| `ResourceFilesWithManifestResourceNames` | Optionaler schreibgeschützter `String`-Ausgabeparameter<br /><br /> Gibt den Namen der Ressourcendatei zurück, die jetzt den Manifestressourcennamen enthält |

## <a name="remarks"></a>Hinweise

 Die Aufgabe [CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md) bestimmt den richtigen Manifestressourcennamen, der einer bestimmten *RESX*- oder einer anderen Ressourcendatei zugewiesen werden soll. Die Aufgabe stellt einen logischen Namen für eine Ressourcendatei bereit und fügt sie dann an einen Ausgabeparameter als Metadatenelement an.

 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Weitere Informationen

- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
