---
title: 'CA1815: Überschreiben von Gleichheits-und-Operatoren für Werttypen Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1815
- OverrideEqualsAndOperatorEqualsOnValueTypes
helpviewer_keywords:
- OverrideEqualsAndOperatorEqualsOnValueTypes
- CA1815
ms.assetid: 0a8ab3a3-ee8e-46f7-985d-dcf00c89363b
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fc5dc311fd85af2b6a0eb3e29e9932614ca55193
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543909"
---
# <a name="ca1815-override-equals-and-operator-equals-on-value-types"></a>CA1815: Equals und Gleichheitsoperator für Werttypen überschreiben.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|OverrideEqualsAndOperatorEqualsOnValueTypes|
|CheckId|CA1815|
|Category|Microsoft. Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein öffentlicher Werttyp wird nicht überschrieben <xref:System.Object.Equals%2A?displayProperty=fullName> oder implementiert den Gleichheits Operator (= =) nicht. Diese Regel überprüft keine Enumerationen.

## <a name="rule-description"></a>Beschreibung der Regel
 Bei Werttypen verwendet die geerbte Implementierung von <xref:System.Object.Equals%2A> die Reflektionsbibliothek und vergleicht den Inhalt aller Felder. Reflection ist rechenintensiv, und das Überprüfen eines jeden Felds auf Gleichheit ist eventuell unnötig. Wenn Sie davon ausgehen, dass Benutzer Instanzen vergleichen oder sortieren oder Sie als Hash Tabellenschlüssel verwenden, sollte der Werttyp implementieren <xref:System.Object.Equals%2A> . Wenn Ihre Programmiersprache Operatorüberladung unterstützt, sollten Sie ebenso eine Implementierung der Gleichheits- und Ungleichheitsoperatoren bereitstellen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, stellen Sie eine Implementierung von bereit <xref:System.Object.Equals%2A> . Implementieren Sie den Gleichheits Operator, wenn dies möglich ist.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn Instanzen des Werttyps nicht miteinander verglichen werden.

## <a name="example-of-a-violation"></a>Beispiel für eine Verletzung

### <a name="description"></a>BESCHREIBUNG
 Das folgende Beispiel zeigt eine Struktur (Werttyp), die gegen diese Regel verstößt.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Performance.OverrideEqualsViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.OverrideEqualsViolation/cs/FxCop.Performance.OverrideEqualsViolation.cs#1)]

## <a name="example-of-how-to-fix"></a>Beispiel für das Beheben von

### <a name="description"></a>BESCHREIBUNG
 Im folgenden Beispiel wird der vorherige Verstoß durch Überschreiben <xref:System.ValueType.Equals%2A?displayProperty=fullName> und Implementieren der Gleichheits Operatoren (= =,! =) korrigiert.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Performance.OverrideEqualsFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.OverrideEqualsFixed/cs/FxCop.Performance.OverrideEqualsFixed.cs#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2224: Equals beim Überladen von Gleichheitsoperatoren überschreiben.](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2231: Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals.](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

 [CA2226: Operatoren sollten symmetrische Überladungen aufweisen.](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

## <a name="see-also"></a>Weitere Informationen
 <xref:System.Object.Equals%2A?displayProperty=fullName>
