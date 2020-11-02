---
title: CPPClean-Aufgabe | Microsoft-Dokumentation
description: In diesem Artikel wird die CPPClean-Aufgabe beschrieben, die zum Löschen der temporären Dateien verwendet wird, die MSBuild beim Erstellen eines C++-Projekts erstellt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.task.cppclean
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), CPPClean task
- CPPClean task (MSBuild (C++))
ms.assetid: b62a482e-8fb5-4999-b50b-6605a078e291
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b8f59b66ab1fc117a29d7ed8db2d380b4b11b437
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796107"
---
# <a name="cppclean-task"></a>CPPClean-Aufgabe

Löscht die temporären Dateien, die MSBuild erstellt, wenn ein C++-Projekt erstellt wird. Das Löschen von Builddateien wird *Bereinigen* genannt.

## <a name="parameters"></a>Parameter

 In der folgenden Tabelle werden die Parameter der **CPPClean** -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|**DeletedFiles**|Optionaler `ITaskItem[]`-Ausgabeparameter.<br /><br /> Definiert ein Array von MSBuild-Ausgabedateielementen, die von Aufgaben verbraucht und ausgegeben werden können|
|**DoDelete**|Optionaler **Boolean** -Parameter.<br /><br /> Wenn der Wert `true` ist, werden temporäre Builddateien bereinigt.|
|**FilePatternsToDeleteOnClean**|Erforderlicher `String`-Parameter.<br /><br /> Gibt eine durch ein Semikolon getrennte Liste von Dateierweiterungen von zu bereinigenden Dateien an|
|**FilesExcludedFromClean**|Optionaler `String`-Parameter.<br /><br /> Gibt eine durch ein Semikolon getrennte Liste von Dateien an, die nicht bereinigt werden sollen|
|**FoldersToClean**|Erforderlicher `String`-Parameter.<br /><br /> Gibt eine durch ein Semikolon getrennte Liste von Verzeichnissen an, die bereinigt werden sollen. Sie können einen vollständigen oder einen relativen Pfad angeben, und der relative Pfad kann ein Platzhaltersymbol (*) enthalten.|

## <a name="see-also"></a>Weitere Informationen

- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
