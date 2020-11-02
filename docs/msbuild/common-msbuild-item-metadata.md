---
title: Gemeinsame MSBuild-Elementmetadaten | Microsoft-Dokumentation
description: Erfahren Sie mehr über optionale Elementmetadaten, die für einige MSBuild-SDKs oder -Ziele eine Bedeutung haben, jedoch nicht für jedes Element standardmäßig festgelegt sind.
ms.custom: SEO-VS-2020
ms.date: 07/13/2020
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- msbuild, common item metadata
- item metadata (MSBuild)
ms.assetid: 9857505d-ae15-42f1-936d-6cd7fb9dd276
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 152967fb99442b58d96016e10d8899b57ef35bf6
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796589"
---
# <a name="common-msbuild-item-metadata"></a>Gemeinsame MSBuild-Elementmetadaten

Die folgende Tabelle beschreibt optionale Elementmetadaten, die für einige MSBuild-SDKs oder -Ziele eine Bedeutung haben, aber nicht für jedes Element standardmäßig festgelegt sind. Sie können diese Metadaten festlegen, um das Buildverhalten zu beeinflussen. Dies funktioniert aber nur, wenn das von Ihnen verwendete SDK oder Ziel diese erkennen.

| Elementmetadaten | SDKs | Beschreibung |
|---------------| ------- | -------------|
|%(Link)| Alle |Das Visual Studio-Projektsystem verwendet `Link`-Metadaten (sofern vorhanden), um zu ändern, welche Elemente in der Projektstruktur angezeigt werden. Sie können eine Datei in einen anderen logischen Ordner im **Projektmappen-Explorer** platzieren.<br />Darüber hinaus verwendet die `AssignTargetPath`-Aufgabe `Link`, um zu bestimmen, an welche Stelle im Ausgabeverzeichnis eine Datei kopiert werden soll, wenn es sich um ein kopiertes Element handelt.|
|%(LinkBase)| .NET Core SDK | Hiermit wird der Ordner festgelegt, der für `Link`-Metadaten für Elementgruppen verwendet werden soll. |

## <a name="see-also"></a>Siehe auch

- [Gemeinsame MSBuild-Projekteigenschaften](../msbuild/common-msbuild-project-properties.md)
- [Gemeinsame MSBuild-Projektelemente](../msbuild/common-msbuild-project-items.md)
- [Bekannte MSBuild-Elementmetadaten](msbuild-well-known-item-metadata.md)