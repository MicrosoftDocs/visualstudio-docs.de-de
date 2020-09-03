---
title: 'CA1504: Irreführende Feldnamen überprüfen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ReviewMisleadingFieldNames
- CA1504
helpviewer_keywords:
- CA1504
- ReviewMisleadingFieldNames
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d375b64bbc877cb377157f13b3e4cfa7c7cf1592
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547874"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504: Irreführende Feldnamen überprüfen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|Category|Microsoft. Wartbarkeit|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Der Name eines Instanzfelds beginnt mit "S_", oder der Name eines `static` - `Shared` Felds (in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) beginnt mit "M_".

## <a name="rule-description"></a>Beschreibung der Regel
 Feldnamen, die mit "S_" beginnen, werden von vielen Benutzern statischen Daten zugeordnet. Ebenso sind Feldnamen, die mit "M_" beginnen, mit Instanzdaten (Member) verknüpft. Um leichter verwalteten Code zu erhalten, sollten Namen allgemeinen verwendeten Konventionen entsprechen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, benennen Sie das Feld um, indem Sie das entsprechende Präfix verwenden. Alternativ dazu können Sie das Feld mit dem aktuellen Suffix einverstanden machen, indem Sie den-Modifizierer hinzufügen oder entfernen `static` .

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.
