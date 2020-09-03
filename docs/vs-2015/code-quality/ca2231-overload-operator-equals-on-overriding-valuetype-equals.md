---
title: 'CA2231: der Überladungs Operator ist gleich beim Überschreiben von ValueType. ist. Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OverloadOperatorEqualsOnOverridingValueTypeEquals
- CA2231
- OverrideOperatorEqualsOnOverridingValueTypeEquals
helpviewer_keywords:
- OverloadOperatorEqualsOnOverridingValueTypeEquals
- CA2231
ms.assetid: 114c0161-261a-40ad-8b2c-0932d6909d2a
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f01495e4238461d0b1dfe5a13a208b528df1581f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540295"
---
# <a name="ca2231-overload-operator-equals-on-overriding-valuetypeequals"></a>CA2231: Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|OverloadOperatorEqualsOnOverridingValueTypeEquals|
|CheckId|CA2231|
|Category|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Ein Werttyp überschreibt, <xref:System.Object.Equals%2A?displayProperty=fullName> aber implementiert den Gleichheits Operator nicht.

## <a name="rule-description"></a>Beschreibung der Regel
 In den meisten Programmiersprachen gibt es keine Standard Implementierung des Gleichheits Operators (= =) für Werttypen. Wenn Ihre Programmiersprache Operator Überladungen unterstützt, sollten Sie die Implementierung des Gleichheits Operators in Erwägung gezogen. Das Verhalten sollte mit dem von identisch sein <xref:System.Object.Equals%2A> .

 Der Standard Gleichheits Operator kann nicht in einer überladenen Implementierung des Gleichheits Operators verwendet werden. Dies führt zu einem Stapelüberlauf. Um den Gleichheits Operator zu implementieren, verwenden Sie die Object. gleich-Methode in der Implementierung. Beispiel:

```vb
If (Object.ReferenceEquals(left, Nothing)) Then
    Return Object.ReferenceEquals(right, Nothing)
Else
    Return left.Equals(right)
End If
```

```csharp
if (Object.ReferenceEquals(left, null))
    return Object.ReferenceEquals(right, null);
return left.Equals(right);
```

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie den Gleichheits Operator.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken. Es wird jedoch empfohlen, nach Möglichkeit den Gleichheits Operator anzugeben.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird ein Typ definiert, der gegen diese Regel verstößt.

 [!code-csharp[FxCop.Usage.EqualsGetHashCode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.EqualsGetHashCode/cs/FxCop.Usage.EqualsGetHashCode.cs#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1046: Gleichheitsoperator für Referenztypen nicht überladen.](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: Operatorüberladungen weisen benannte Alternativen auf.](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226: Operatoren sollten symmetrische Überladungen aufweisen.](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224: Equals beim Überladen von Gleichheitsoperatoren überschreiben.](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: GetHashCode beim Überschreiben von Equals überschreiben.](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

## <a name="see-also"></a>Weitere Informationen
 <xref:System.Object.Equals%2A?displayProperty=fullName>
