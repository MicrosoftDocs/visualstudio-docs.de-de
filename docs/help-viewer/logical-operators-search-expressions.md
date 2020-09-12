---
title: Logische Operatoren in Such Ausdrücken (Help Viewer)
ms.custom: SEO-VS-2020
ms.date: 11/02/2017
ms.topic: reference
helpviewer_keywords:
- Help Viewer, logical operators in search
- logical operators in search [Help Viewer]
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9daceca2540a2da61a46e12a458c012ce7851001
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/11/2020
ms.locfileid: "90038633"
---
# <a name="logical-and-advanced-operators-in-search-expressions"></a>Logische und erweiterte Operatoren in Suchausdrücken

Sie können logische Operatoren und erweiterte Such Operatoren verwenden, um die Suche nach Hilfe Inhalten in **Help Viewer**zu verfeinern.

## <a name="logical-operators"></a>Logische Operatoren

Mit logischen Operatoren können Sie angeben, wie viele Suchausdrücke in einer Suchabfrage kombiniert werden sollen. In der folgenden Tabelle werden die logischen Operatoren AND, OR, NOT und NEAR veranschaulicht.

|Suchen nach|Verwendung|Beispiel|Ergebnis|
|-------------------|---------|-------------|------------|
|Beide Begriffe im gleichen Artikel|UND|dib UND palette|Themen, die sowohl „Dib“ als auch „Palette“ enthalten.|
|Einer der Begriffe in einem Artikel|oder|Raster ODER Vektor|Themen, die entweder „Raster“ oder „Vektor“ enthalten.|
|Erster Begriff ohne den zweiten Begriff im gleichen Artikel|NICHT|„Betriebssystem“ NICHT DOS|Themen, die „Betriebssystem“ aber nicht „DOS“ enthalten.|
|Beide Begriffe nah beieinander in einem Artikel|NEAR|Benutzer NAH Kernel|Themen mit „Benutzer“ in der Nähe von „Kernel“.|

> [!IMPORTANT]
> Sie müssen logische Operatoren in Großbuchstaben eingeben, damit sie von der Suchmaschine erkannt werden.

## <a name="advanced-operators"></a>Erweiterte Operatoren

Mit erweiterten Suchoperatoren können Sie Ihre Suche nach Inhalt optimieren, indem Sie festlegen, in welchem Bereich des Artikels nach dem Suchbegriff gesucht werden soll. In der folgenden Tabelle werden die vier verfügbaren erweiterten Suchoperatoren veranschaulicht.

|Suchen nach|Verwendung|Beispiel|Ergebnis|
|-------------------|---------|-------------|------------|
|Ein Begriff im Titel des Artikels|`title:`|`title:binaryreader`|Themen, die „Binaryreader“ im Titel enthalten.|
|Eine Benennung in einem Codebeispiel|`code:`|`code:readdouble`|Themen, die „readdouble“ in einem Codebeispiel enthalten.|
|Eine Benennung in einem Beispiel einer spezifischen Programmiersprache|`code:vb:`|`code:vb:string`|Themen, die „string“ in einem Visual Basic-Codebeispiel enthalten.|
|Ein Artikel, der einem bestimmten Indexschlüsselwort zugeordnet ist|`keyword:`|`keyword:readbyte`|Themen, die dem Index-Schlüsselwort „readbyte“ zugeordnet sind.|

> [!IMPORTANT]
> Sie müssen erweiterte Suchoperatoren mit einem abschließenden Doppelpunkt eingeben. Es dürfen sich keine Leerzeichen zwischen dem Suchoperator und dem Doppelpunkt befinden, damit die Suchmaschine diesen erkennen kann.

### <a name="programming-languages-for-code-examples"></a>Programmiersprachen für Codebeispiele

Mit dem Operator `code:` können Sie nach Inhalt von einer der Programmiersprachen suchen. Verwenden Sie einen der folgenden Programmiersprachenwerte, um Beispiele für eine bestimmte Programmiersprache zurückzugeben:

|Programmiersprache|Suchoperatorsyntax|
| - |---------|
|Visual Basic|`code:vb`<br/>`code:visualbasic`|
|C#|`code:c#`<br/>`code:csharp`|
|C++|`code:cpp`<br/>`code:c++`<br/>`code:cplusplus`|
|F#|`code:f#`<br/>`code:fsharp`|
|JavaScript|`code:javascript`<br/>`code:js`|
|XAML|`code:xaml`|

> [!NOTE]
> Der Operator `code:` findet nur Inhalt, der mit einem Programmiersprachenbezeichner markiert ist, und keinen Inhalt, der generisch als Code markiert ist.

## <a name="see-also"></a>Weitere Informationen

- [Vorgehensweise: Suchen nach Themen](../help-viewer/find-topics.md)
- [Microsoft Help Viewer](../help-viewer/overview.md)
