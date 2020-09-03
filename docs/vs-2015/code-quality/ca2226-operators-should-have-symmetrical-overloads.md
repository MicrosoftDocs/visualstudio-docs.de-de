---
title: 'CA2226: Operatoren sollten symmetrische über Ladungen aufweisen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
helpviewer_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
ms.assetid: d202401a-ea14-4559-b15e-0ea4f5b68789
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 430a8d3cfd3b8ced45b60bd9dc70211711886d43
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540568"
---
# <a name="ca2226-operators-should-have-symmetrical-overloads"></a>CA2226: Operatoren sollten symmetrische Überladungen aufweisen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|OperatorsShouldHaveSymmetricalOverloads|
|CheckId|CA2226|
|Category|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Ein Typ implementiert den Gleichheits- oder Ungleichheitsoperator, ohne den entgegengesetzten Operator zu implementieren.

## <a name="rule-description"></a>Beschreibung der Regel
 Es gibt keine Umstände, in denen entweder Gleichheit oder Ungleichheit auf Instanzen eines Typs anwendbar ist und der umgekehrte Operator nicht definiert ist. Typen implementieren in der Regel den Ungleichheits Operator, indem Sie den negiert-Wert des Gleichheits Operators zurückgeben.

 Der c#-Compiler gibt einen Fehler bei Verstößen gegen diese Regel aus.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie die Gleichheits-und Ungleichheits Operatoren, oder entfernen Sie die vorhandene, die vorhanden ist.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel. Der Typ funktioniert nicht in einer Weise, die mit übereinstimmt [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .

## <a name="related-rules"></a>Verwandte Regeln
 [CA1046: Gleichheitsoperator für Referenztypen nicht überladen.](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: Operatorüberladungen weisen benannte Alternativen auf.](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2224: Equals beim Überladen von Gleichheitsoperatoren überschreiben.](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: GetHashCode beim Überschreiben von Equals überschreiben.](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals.](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
