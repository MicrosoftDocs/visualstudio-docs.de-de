---
title: 'CA1018: Attribute mit AttributeUsageAttribute markieren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
helpviewer_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 256fc281b27c483f1dda0317f7d2695fa36c47f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535056"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018: Attribute mit AttributeUsageAttribute markieren.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|MarkAttributesWithAttributeUsage|
|CheckId|CA1018|
|Category|Microsoft. Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Das- <xref:System.AttributeUsageAttribute?displayProperty=fullName> Attribut ist für das benutzerdefinierte Attribut nicht vorhanden.

## <a name="rule-description"></a>Beschreibung der Regel
 Wenn Sie ein benutzerdefiniertes Attribut definieren, markieren Sie es mithilfe von, <xref:System.AttributeUsageAttribute> um anzugeben, an welcher Stelle im Quellcode das benutzerdefinierte Attribut angewendet werden kann. Die Bedeutung und die beabsichtigte Verwendung eines Attributs bestimmen die gültigen Positionen des Attributs im Code. Beispielsweise können Sie ein Attribut definieren, mit dem die Person identifiziert wird, die für die Verwaltung und Erweiterung der einzelnen Typen in einer Bibliothek zuständig ist, und dass die Verantwortlichkeit immer auf der Typebene zugewiesen wird. In diesem Fall sollten Compiler das-Attribut für Klassen, Enumerationen und Schnittstellen aktivieren, diese aber nicht für Methoden, Ereignisse oder Eigenschaften aktivieren. Organisations Richtlinien und-Prozeduren würden vorschreiben, ob das Attribut für Assemblys aktiviert werden soll.

 Die- <xref:System.AttributeTargets?displayProperty=fullName> Enumeration definiert die Ziele, die Sie für ein benutzerdefiniertes Attribut angeben können. Wenn Sie weglassen <xref:System.AttributeUsageAttribute> , ist das benutzerdefinierte Attribut für alle Ziele gültig, wie durch den `All` Wert der- <xref:System.AttributeTargets> Enumeration definiert.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, geben Sie Ziele für das-Attribut an, indem Sie verwenden <xref:System.AttributeUsageAttribute> . Siehe folgendes Beispiel.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Sie sollten einen Verstoß gegen diese Regel beheben, anstatt die Meldung auszuschließen. Auch wenn das Attribut erbt <xref:System.AttributeUsageAttribute> , sollte das-Attribut vorhanden sein, um die Code Verwaltung zu vereinfachen.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel werden zwei Attribute definiert. `BadCodeMaintainerAttribute` lässt die Anweisung falsch <xref:System.AttributeUsageAttribute> `GoodCodeMaintainerAttribute` aus und implementiert das-Attribut, das weiter oben in diesem Abschnitt beschrieben wird. Beachten Sie, dass die-Eigenschaft für `DeveloperName` die Entwurfs Regel [CA1019: Accessoren für Attribut Argumente definiert](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) werden muss und aus Gründen der Vollständigkeit eingeschlossen ist.

 [!code-csharp[FxCop.Design.AttributeUsage#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeUsage/cs/FxCop.Design.AttributeUsage.cs#1)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeUsage/vb/FxCop.Design.AttributeUsage.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1019: Accessoren für Attributargumente definieren.](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1813: Nicht versiegelte Attribute vermeiden.](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Weitere Informationen
 [Attribute](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)
