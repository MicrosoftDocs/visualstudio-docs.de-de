---
title: 'CA1804: nicht verwendete lokale Variablen entfernen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1804
- RemoveUnusedLocals
helpviewer_keywords:
- RemoveUnusedLocals
- CA1804
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4bd57d76acd0c46e39bb2c01449146715abc0666
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543883"
---
# <a name="ca1804-remove-unused-locals"></a>CA1804: Nicht verwendete lokale Variablen entfernen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|RemoveUnusedLocals|
|CheckId|CA1804|
|Category|Microsoft. Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine Methode deklariert eine lokale Variable, verwendet jedoch nicht die Variable, außer möglicherweise als Empfänger einer Zuweisungsanweisung. Zur Analyse durch diese Regel muss die getestete Assembly mit Debuginformationen erstellt werden, und die zugehörige Programm Datenbankdatei (. pdb) muss verfügbar sein.

## <a name="rule-description"></a>Beschreibung der Regel
 Nicht verwendete lokale Variablen und unnötige Zuweisungen vergrößern die Assembly unnötig und beeinträchtigen die Leistung.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie die lokale Variable, oder verwenden Sie Sie. Beachten Sie, dass der c#-Compiler, der in enthalten ist, nicht [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] verwendete lokale Variablen entfernt, wenn die `optimize` Option aktiviert ist.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrückt eine Warnung aus dieser Regel, wenn die Variable vom Compiler ausgegeben wurde. Es ist auch sicher, eine Warnung aus dieser Regel zu unterdrücken oder die Regel zu deaktivieren, wenn die Leistung und die Codewartung keine Haupt Bedenken darstellen.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt mehrere nicht verwendete lokale Variablen.

 [!code-csharp[FxCop.Performance.UnusedLocals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals/cs/FxCop.Performance.UnusedLocals.cs#1)]
 [!code-vb[FxCop.Performance.UnusedLocals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals/vb/FxCop.Performance.UnusedLocals.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1809: Übermäßige lokale Variablen vermeiden.](../code-quality/ca1809-avoid-excessive-locals.md)

 [CA1811: Nicht aufgerufenen privaten Code vermeiden.](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: Nicht instanziierte interne Klassen vermeiden.](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: Nicht verwendete Parameter überprüfen.](../code-quality/ca1801-review-unused-parameters.md)
