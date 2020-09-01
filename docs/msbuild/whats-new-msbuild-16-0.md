---
title: Neuerungen in MSBuild 16.0 | Microsoft-Dokumentation
ms.date: 03/11/2019
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 48fc1a02ad34a3d5229ead0da79c0f6fa781670e
ms.sourcegitcommit: de98ed7edc81383e47b87ae6e61143fbbbe7bc56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2020
ms.locfileid: "88711650"
---
# <a name="whats-new-in-msbuild-160"></a>Neuerungen in MSBuild 16.0

In diesem Artikel werden die aktualisierten Funktionen und Eigenschaften in MSBuild 16.0 beschrieben. Die detaillierten Versionshinweise finden Sie unter [MSBuild 16.0](https://github.com/microsoft/msbuild/releases/tag/v16.0.461.62831).

## <a name="changed-path"></a>Geänderter Pfad

 MSBuild wird im Ordner *\Current* der jeweiligen Version von Visual Studio installiert, die ausführbaren Dateien befinden sich im Unterordner *\Bin*. Beispielsweise lautet der Pfad zu *MSBuild.exe* bei der Installation mit Visual Studio 2019 Community *C:\Programme (x86)\Microsoft Visual Studio\2019\Community\MSBuild\Current\Bin\MSBuild.exe*. Sie können das folgende PowerShell-Modul verwenden, um nach MSBuild zu suchen: [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell).

## <a name="changed-properties"></a>Geänderte Eigenschaften

 Die folgenden MSBuild-Eigenschaften wurden aufgrund der neuen Versionsnummer aktualisiert.

- `MSBuildToolsVersion` für diese Version der Tools ist „Current“. Die Assembly-Version ist 15.1.0.0 und entspricht somit der von Visual Studio 2017.

- `VisualStudioVersion` für diese Version der Tools ist „16.0“.

## <a name="updates"></a>Updates

MSBuild (und Visual Studio) zielt jetzt auf .NET Framework 4.7.2 ab. Wenn Sie die neuen MSBuild-API-Funktionen verwenden möchten, müssen Sie ebenfalls ein Upgrade Ihrer Assembly durchführen, wobei vorhandener Code aber weiterhin funktionsfähig bleibt.

## <a name="see-also"></a>Siehe auch

- [MSBuild](../msbuild/msbuild.md)
