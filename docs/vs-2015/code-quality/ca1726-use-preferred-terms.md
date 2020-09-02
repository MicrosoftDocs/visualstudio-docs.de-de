---
title: 'CA1726: bevorzugte Begriffe verwenden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UsePreferredTerms
- CA1726
helpviewer_keywords:
- UsePreferredTerms
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 96e0614bc5c08c83008af4e67a2aa865f08f74f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547809"
---
# <a name="ca1726-use-preferred-terms"></a>CA1726: Bevorzugte Begriffe verwenden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Dokumentation zu Visual Studio finden Sie unter [CA1726: bevorzugte Begriffe verwenden](/visualstudio/code-quality/ca1726-use-preferred-terms).

|Element|value|
|-|-|
|TypName|UsePreferredTerms|
|CheckId|CA1726|
|Category|Microsoft.Naming|
|Unterbrechende Änderung|Unterbrechen: beim Auslösen für Assemblys<br /><br /> Nicht unterbrechend: beim Auslösen für Typparameter|

## <a name="cause"></a>Ursache
 Der Name eines extern sichtbaren Bezeichners schließt einen Begriff ein, für den ein alternativer, bevorzugter Begriff vorhanden ist. Alternativ enthält der Name den Begriff Flag oder Flags.

## <a name="rule-description"></a>Beschreibung der Regel
 Diese Regel analysiert einen Bezeichner in Token. Jedes einzelne Token und jede zusammenhängende Kombination aus Dual Token wird mit Begriffen verglichen, die in die Regel und im veralteten Abschnitt von benutzerdefinierten Wörterbüchern integriert sind. In der folgenden Tabelle sind die Begriffe, die in die Regel integriert sind, und Ihre bevorzugten Alternativen aufgeführt.

|Veralteter Begriff|Bevorzugter Begriff|
|-------------------|--------------------|
|`Arent`|`AreNot`|
|`Cancelled`|`Canceled`|
|`Cant`|`Cannot`|
|`ComPlus`|`EnterpriseServices`|
|`Couldnt`|`CouldNot`|
|`Didnt`|`DidNot`|
|`Doesnt`|`DoesNot`|
|`Dont`|`DoNot`|
|`Flag` oder `Flags`|Es gibt keinen Ersetzungs Begriff. Darf nicht verwendet werden.|
|`Hadnt`|`HadNot`|
|`Hasnt`|`HasNot`|
|`Havent`|`HaveNot`|
|`Indices`|`Indexes`|
|`Isnt`|`IsNot`|
|`LogIn`|`LogOn`|
|`LogOut`|`LogOff`|
|`Shouldnt`|`ShouldNot`|
|`SignOn`|`SignIn`|
|`SignOff`|`SignOut`|
|`Wasnt`|`WasNot`|
|`Werent`|`WereNot`|
|`Wont`|`WillNot`|
|`Wouldnt`|`WouldNot`|
|`Writeable`|`Writable`|

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ersetzen Sie den Begriff durch den bevorzugten Alternativen Begriff.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrückt eine Warnung aus dieser Regel nur, wenn der Name des Bezeichners beabsichtigt ist und sich nicht auf den bevorzugten Begriff, sondern speziell auf den ursprünglichen Begriff bezieht.

## <a name="related-rules"></a>Verwandte Regeln
 [Benennungs Warnungen](../code-quality/naming-warnings.md)
