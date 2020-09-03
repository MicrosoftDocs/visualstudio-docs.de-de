---
title: 'CA1306: Gebiets Schema für Datentypen festlegen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1306
- SetLocaleForDataTypes
helpviewer_keywords:
- CA1306
- SetLocaleForDataTypes
ms.assetid: 104297b2-5806-4de0-a8d9-c589380a796c
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: edd1d6a7623f96f03403883ee2585d245414bb3b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539021"
---
# <a name="ca1306-set-locale-for-data-types"></a>CA1306: Gebietsschema für Datentypen festlegen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|SetLocaleForDataTypes|
|CheckId|CA1306|
|Category|Microsoft. Globalization|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine Methode oder ein Konstruktor hat mindestens eine <xref:System.Data.DataTable?displayProperty=fullName> <xref:System.Data.DataSet?displayProperty=fullName> -Instanz oder eine-Instanz erstellt und nicht explizit die Locale-Eigenschaft ( <xref:System.Data.DataTable.Locale%2A?displayProperty=fullName> oder) festgelegt <xref:System.Data.DataSet.Locale%2A?displayProperty=fullName> .

## <a name="rule-description"></a>Beschreibung der Regel
 Das Gebiets Schema bestimmt kulturspezifische Präsentationselemente für Daten, z. b. für numerische Werte, Währungssymbole und die Sortierreihenfolge verwendete Formatierung. Wenn Sie ein oder ein erstellen <xref:System.Data.DataTable> <xref:System.Data.DataSet> , sollten Sie das Gebiets Schema explizit festlegen. Standardmäßig ist das Gebiets Schema für diese Typen die aktuelle Kultur. Für Daten, die in einer Datenbank oder Datei gespeichert sind und Global gemeinsam genutzt werden, sollte das Gebiets Schema normalerweise auf die invariante Kultur () festgelegt werden <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName> . Wenn Daten über Kulturen hinweg freigegeben werden, kann die Verwendung des Standard Gebiets Schemas bewirken, dass der Inhalt von <xref:System.Data.DataTable> oder <xref:System.Data.DataSet> falsch dargestellt oder interpretiert wird.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, legen Sie explizit das Gebiets Schema für das <xref:System.Data.DataTable> oder fest <xref:System.Data.DataSet> .

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn die Bibliothek oder Anwendung für eine begrenzte lokale Zielgruppe verwendet wird, die Daten nicht freigegeben werden oder wenn die Standardeinstellung das gewünschte Verhalten in allen unterstützten Szenarios ergibt.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel werden zwei- <xref:System.Data.DataTable> Instanzen erstellt.

 [!code-csharp[FxCop.Globalization.DataTable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DataTable/cs/FxCop.Globalization.DataTable.cs#1)]

## <a name="see-also"></a>Weitere Informationen
 <xref:System.Data.DataTable?displayProperty=fullName> <xref:System.Data.DataSet?displayProperty=fullName>
 <xref:System.Globalization.CultureInfo?displayProperty=fullName>
 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>
 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>
