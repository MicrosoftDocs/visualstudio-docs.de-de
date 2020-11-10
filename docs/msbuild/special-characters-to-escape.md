---
title: Sonderzeichen mit Escapezeichen | Microsoft-Dokumentation
description: Erfahren Sie mehr darüber, dass Sonderzeichen nur dann mit Escapezeichen versehen werden müssen, wenn sie im verwendeten Kontext eine besondere Bedeutung haben.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- special characters to escape
- msbuild, special characters to escape
ms.assetid: 5b5172c3-41e4-4f38-a16f-2aeac831a5fc
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 433e762bf68b6a3956616e0ccccc229bca8f86b9
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048274"
---
# <a name="special-characters-to-escape"></a>Sonderzeichen mit Escapezeichen

Sonderzeichen müssen nur dann mit Escapezeichen versehen werden, wenn sie eine besondere Bedeutung in dem Kontext haben, in dem sie verwendet werden. Beispielsweise ist das Sternchen (*) nur in den "Include"- und "Exclude"-Attributen einer Elementdefinition oder in einem Aufruf von <xref:Microsoft.Build.Tasks.CreateItem> ein Sonderzeichen. In allen anderen Fällen wird das Sternchen als einfaches Sternchen behandelt. Obwohl sie Sternchen nicht überall in Projektdateien mit Escapezeichen versehen müssen, kann dies auch nicht schaden.

 Verwenden Sie die Notation %\<xx> anstelle des Sonderzeichens, wobei \<xx> den Hexadezimalwert des ASCII-Zeichens darstellt. Wenn Sie ein Sternchen (*) als Literalzeichen verwenden möchten, verwenden Sie z. B. den Wert `%2A`.

 Es folgt die vollständige Liste der Sonderzeichen mit Escapezeichen:

|Zeichen|ASCII-Codierung|Beschreibung|
|---------|----------|-----------|
|%|%25|Prozentzeichen, für Verweise auf Metadaten verwendet.|
|$|%24|Dollarzeichen, für Verweise auf Eigenschaften verwendet.|
|@|%40|At-Zeichen, für Verweise auf Elementlisten verwendet.|
|(|%28|Öffnende runde Klammer, in Listen verwendet.|
|)|%29|Schließende runde Klammer, in Listen verwendet.|
|;|%3B|Semikolon, ein Listentrennzeichen.|
|?|%3F|Fragezeichen, ein Platzhalterzeichen beim Beschreiben einer Dateispezifikation im Include/Exclude-Abschnitt eines Elements.|
|* |%2A|Sternchen, ein Platzhalterzeichen beim Beschreiben einer Dateispezifikation im Include/Exclude-Abschnitt eines Elements.|

> [!NOTE]
> In einigen Szenarios müssen Sie doppelte gerade Anführungszeichen (") möglicherweise mit Escapezeichen versehen, beispielsweise bei der Verwendung solcher Zeichen innerhalb eines `Exec`-Tasks.

## <a name="see-also"></a>Siehe auch

- [How to: Escapesonderzeichen in MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md)
- [MSBuild-Referenz](../msbuild/msbuild-reference.md)
