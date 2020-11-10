---
title: MSBuild-Sonderzeichen | Microsoft-Dokumentation
description: Erfahren Sie mehr über die MSBuild-Sonderzeichen zur besonderen Verwendung in spezifischen Kontexten sowie dazu, wann und wie Sie diese Zeichen mit einem Escapezeichen versehen.
ms.custom: SEO-VS-2020
ms.date: 06/12/2019
ms.topic: conceptual
helpviewer_keywords:
- escape characters
- escape
- MSBuild Escape Characters
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 67de0c2e5aa35fa3a1f54e26f425f4b0916cb428
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93049112"
---
# <a name="msbuild-special-characters"></a>MSBuild-Sonderzeichen

MSBuild reserviert einige Zeichen für die besondere Verwendung in spezifischen Kontexten. Sie müssen diese Zeichen nur mit einem Escapezeichen versehen, wenn Sie sie in dem für sie reservierten Kontext in ihrer ursprünglichen Bedeutung verwenden möchten. Beispielsweise hat ein Sternchen nur in den Attributen `Include` und `Exclude` einer Elementdefinition und im Zusammenhang mit Aufrufen von `CreateItem` eine besondere Bedeutung. Wenn aber ein Sternchen in diesen Kontexten wirklich als Sternchen angezeigt werden soll, müssen Sie es mit einem Escapezeichen versehen. In allen anderen Kontexten müssen Sie lediglich auf die Sternchentaste drücken, wenn ein Sternchen angezeigt werden soll.

 Verwenden Sie die Syntax %\<xx>>, um ein Sonderzeichen mit einem Escapezeichen zu versehen. Hierbei stellt \<xx>> den Hexadezimalwert des ASCII-Zeichens dar. Weitere Informationen finden Sie unter [Vorgehensweise: Escapesonderzeichen in MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).

## <a name="special-characters"></a>Sonderzeichen

 In der folgenden Tabelle werden Sonderzeichen für MSBuild aufgeführt:

|**Zeichen**|**ASCII**|**Reservierte Nutzung**|
|-------------------|---------------|------------------------|
|%|%25|Verweisen auf Metadaten|
|$|%24|Verweisen auf Eigenschaften|
|@|%40|Verweisen auf Elementlisten|
|'|%27|Bedingungen und andere Ausdrücke|
|;|%3B|Listentrennzeichen|
|?|%3F|Platzhalterzeichen für Dateinamen in `Include`- und `Exclude`-Attributen|
|*|%2A|Platzhalterzeichen für Dateinamen in `Include`- und `Exclude`-Attributen|

## <a name="see-also"></a>Siehe auch

- [Weiterführende Konzepte](../msbuild/msbuild-advanced-concepts.md)
- [Elemente](../msbuild/msbuild-items.md)
