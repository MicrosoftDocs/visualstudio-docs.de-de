---
title: MSBuild-Antwortdateien | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- response files, MSBuild
- MSBuild, response files
- MSBuild, .rsp files
- .rsp files
ms.assetid: 9f53987b-20ee-470a-ab62-fce997bb5e15
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 44d6e3c77fee53b15ec8d18cb74fd7355ee101a8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "89315147"
---
# <a name="msbuild-response-files"></a>MSBuild-Antwortdateien

Anwortdateien (*RSP*-Dateien) sind Textdateien, die Schalter für die *MSBuild.exe*-Befehlszeile enthalten. Die Schalter können sich entweder in unterschiedlichen Zeilen oder in nur einer Zeile befinden. Den Befehlszeilen wird ein **#** -Symbol vorangestellt. Der **@** -Schalter wird verwendet, um eine andere Antwortdatei an *MSBuild.exe* zu übergeben.

## <a name="msbuildrsp"></a>MSBuild.rsp

Die automatische Antwortdatei ist eine besondere *RSP*-Datei, die *MSBuild.exe* automatisch beim Erstellen eines Projekts verwendet. Diese Datei (*MSBuild.rsp*) muss sich in demselben Verzeichnis befinden, in dem sich *MSBuild.exe* befindet, um gefunden werden zu können. Sie können diese Datei bearbeiten, um die Standardschalter für die Befehlszeile auf *MSBuild.exe* festzulegen. Wenn Sie z.B. bei jeder Projekterstellung dieselbe Protokollierung verwenden, können Sie *MSBuild.rsp* den Schalter **-logger** hinzufügen, damit *MSBuild.exe* die Protokollierung bei jeder Projekterstellung verwendet.

## <a name="directorybuildrsp"></a>Directory.Build.rsp

In Version 15.6 und höher durchsucht MSBuild übergeordnete Verzeichnisse des Projekts nach einer Datei namens *Directory.Build.rsp*.  Dies kann in einem Quellcoderepository nützlich sein, um Standardargumente während Befehlszeilenbuilds anzugeben.  Dies kann ebenfalls verwendet werden, um die Befehlszeilenargumente der gehosteten Builds anzugeben.

## <a name="see-also"></a>Weitere Informationen

- [MSBuild-Referenz](../msbuild/msbuild-reference.md)
- [Befehlszeilenreferenz](../msbuild/msbuild-command-line-reference.md)
