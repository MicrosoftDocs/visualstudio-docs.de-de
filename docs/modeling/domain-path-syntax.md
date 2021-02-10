---
title: Domänenpfadsyntax
description: Erfahren Sie mehr über die Domänen Pfad Syntax und wie DSL-Definitionen eine XPath-ähnliche Syntax verwenden, um nach bestimmten Elementen in einem Modell zu suchen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, domain path
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c11776576d00306e4b0f3de5e7ff830037c1fefd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935156"
---
# <a name="domain-path-syntax"></a>Domänenpfadsyntax
In DSL-Definitionen wird eine XPath-artige Syntax für die Suche nach bestimmten Elementen in einem Modell verwendet.

 In der Regel ist es nicht erforderlich, direkt mit dieser Syntax zu arbeiten. Wenn sie in DSL-Details oder im Eigenschaftenfenster angezeigt wird, können Sie auf den nach unten weisenden Pfeil klicken und den Pfad-Editor verwenden. Der Pfad wird jedoch in dieser Form im Feld angezeigt, nachdem Sie den Editor verwendet haben.

 Ein Domänenpfad weist die folgende Form auf:

 *Beziehungsname.Eigenschaftenname/!Rolle*

 ![CommentReferencesSubjects-Verweisbeziehung](../modeling/media/dsl_reference.png)

 Die Syntax durchläuft die Baumstruktur des Modells. Die Domänen Beziehung **commentreferencessubjects** in der obigen Abbildung hat z. b **. eine** betreffrolle. Das Pfad Segment **/! Subjett** gibt an, dass der Pfad für Elemente abgeschlossen ist, auf die über die **Themen** Rolle zugegriffen wird.

 Jedes Segment beginnt mit dem Namen einer Domänenbeziehung. Wenn der Durchlauf von einem Element zu einer Beziehung erfolgt, wird das Pfad Segment als *Relationship. PropertyName* angezeigt. Wenn der Hop von einem Link zu einem Element erfolgt, wird das Pfad Segment als *Beziehung/! RoleName*.

 Die Syntax eines Pfads wird durch Schrägstriche unterteilt. Jedes Pfadsegment ist entweder ein Hop von einem Element zu einem Link (einer Instanz einer Beziehung) oder von einem Link zu einem Element. Pfadsegmente treten häufig paarweise auf. Ein Pfadsegment steht für einen Hop von einem Element zu einem Link, und das nächste Segment steht für einen Hop vom Link zum Element am anderen Ende. (Jeder Link kann auch die Quelle oder das Ziel der Beziehung selbst sein.)

 Der Name, den Sie für den Hop vom Element zum Link verwenden, ist der Wert von `Property Name` der Rolle. Der Name, den Sie für den Hop vom Link zum Element verwenden, ist der Zielrollenname.

## <a name="see-also"></a>Weitere Informationen

- [Grundlagen von Modellen, Klassen und Beziehungen](../modeling/understanding-models-classes-and-relationships.md)
