---
title: Projektmappenfilter in MSBuild
description: Dieser Artikel erläutert Projektmappenfilter und zeigt, wie eine Projektmappenfilterdatei mit MSBuild erstellt wird.
ms.date: 07/28/2020
ms.topic: reference
helpviewer_keywords:
- MSBuild, solution filters
- solution filters [MSBuild]
author: ghogen
ms.author: ghogen
manager: jmartens
monikerRange: '>= vs-2019'
ms.openlocfilehash: 4a5c764ad9ea4190df5e533926671dbd88c53b8b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937835"
---
# <a name="solution-filters-in-msbuild"></a>Projektmappenfilter in MSBuild

Projektmappenfilterdateien sind JSON-Dateien mit der Erweiterung *.slnf*, die angeben, welche der Projekte in einer Projektmappe erstellt oder geladen werden sollen. Ab MSBuild 16.7 können Sie MSBuild in der Projektmappenfilterdatei aufrufen, um die Projektmappe mit aktivierter Filterung zu erstellen. 

> [!NOTE]
> Die Projektmappenfilterdatei reduziert die Menge an Projekten, die geladen oder erstellt werden, und vereinfacht das Format. Die Projektmappendatei ist weiterhin erforderlich.

## <a name="build-a-solution-filter-from-the-command-line"></a>Erstellen eines Projektmappenfilters von der Befehlszeile

Beim Erstellen einer Projektmappenfilterdatei von der Befehlszeile wird exakt dieselbe Syntax wie beim Erstellen einer Projektmappendatei verwendet. Geben Sie statt der Projektmappe, die mit aktivierter Filterung erstellt werden soll, die Projektmappenfilterdatei an:

```console
msbuild [options] solutionFilterFile.slnf
```

Sie können wie sonst auch Schalter und zusätzliche Eigenschaften anfügen. Hilfreiche Informationen finden Sie in der [MSBuild-Befehlszeilenreferenz](msbuild-command-line-reference.md). Dieser Befehl erstellt die gefilterten Projekte sowie alle davon abhängigen Projekte. Beim Erstellen eines Projektmappenfilters von der Befehlszeile befolgt MSBuild automatisch Abhängigkeiten. MSBuild erstellt ein Projekt, wenn es im Filter angegeben ist oder wenn von einem erstellten Projekt auf ein anderes Projekt verwiesen wird.

## <a name="solution-filter-files"></a>Projektmappen-Filterdateien

Sie können Visual Studio für die Arbeit mit Projektmappenfilterdateien verwenden. Beim Öffnen eines Projektmappenfilter in Visual Studio werden die nicht geladenen Projekte ebenso angezeigt wie die geladenen. Außerdem können Sie weitere Projekte laden, um sie für die Erstellung auszuwählen. Sie können alle Projekte laden, von deren Erstellung die ursprünglichen Projekte abhängig sind, dies ist jedoch nicht erforderlich. Weitere Informationen finden Sie unter [Gefilterte Projektmappen](../ide/filtered-solutions.md).

Der Projektmappenfilter muss sich nicht im selben Ordner befinden wie die Projektmappe. Der Pfad zur Projektmappendatei ist relativ zum Speicherort der Projektmappenfilterdatei. Die Pfade zu den einzelnen Projekten sind relativ zur Projektmappendatei selbst und müssen mit den Projektpfaden in der Projektmappendatei übereinstimmen. Das folgende Beispiel veranschaulicht die Verwendung von relativen Pfaden:

```json
{
  "solution": {
    "path": "..\\..\\Documents\\GitHub\\msbuild\\MSBuild.sln",
    "projects": [
      "src\\Build.OM.UnitTests\\Microsoft.Build.Engine.OM.UnitTests.csproj"
    ]
  }
}
```

Die umgekehrten Schrägstriche in Pfaden müssen verdoppelt werden, da einer der Schrägstriche als Escapezeichen dient.

## <a name="example"></a>Beispiel

Hier sehen Sie ein Beispiel für eine gefilterte Projektmappe in Visual Studio:

![Screenshot einer gefilterten Projektmappe in Visual Studio](media/solution-with-filter.png)

In dieser Projektmappe wird ClassLibrary1 sowohl von ProjectA als auch von ProjectB verwendet und ist daher als Projektverweis aufgeführt.

Hier sehen Sie den von Visual Studio generierten Projektmappenfilter:

```json
{
  "solution": {
    "path": "MyApplication.sln",
    "projects": [
      "MyApplication\\MyApplication.csproj",
      "ProjectA\\ProjectA.csproj"
    ]
  }
}
```

Wenn Sie in diesem Beispiel den Erstellungsprozess mit aktivierter Filterung ausführen (mit dem Befehl `MSBuild [options] MyFilter.slnf`), erstellt MSBuild MyApplication und ProjectA, weil diese in der Projektmappenfilterdatei explizit aufgeführt sind. Im Rahmen des Erstellungsprozesses für ProjectA erstellt MSBuild auch ClassLibrary1, weil ProjectA davon abhängt.  ProjectB wird nicht erstellt. (Hierbei wird ein bereinigter Build vorausgesetzt. Wenn zuvor bereits Projekte erstellt wurden, gelten die üblichen Regeln für das Überspringen von Projekten, die bereits auf dem neuesten Stand sind.)

## <a name="see-also"></a>Siehe auch

- [Gefilterte Projektmappen](../ide/filtered-solutions.md)
- [MSBuild-Befehlszeilenreferenz](msbuild-command-line-reference.md)
