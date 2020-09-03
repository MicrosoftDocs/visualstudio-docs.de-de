---
title: 'CA1822: Member als statisch markieren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkMembersAsStatic
- CA1822
helpviewer_keywords:
- MarkMembersAsStatic
- CA1822
ms.assetid: 743f0af7-41d1-4852-8d97-af0688b31118
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2416eb24c21ef0e61bdb6db3de66c892e1eb699f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545339"
---
# <a name="ca1822-mark-members-as-static"></a>CA1822: Member als statisch markieren.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Dokumentation zu Visual Studio finden Sie unter [CA1822: Markieren](/visualstudio/code-quality/ca1822-mark-members-as-static)von Membern als statisch.

|Element|value|
|-|-|
|TypName|MarkMethodsAsStatic|
|CheckId|CA1822|
|Category|Microsoft. Performance|
|Unterbrechende Änderung|Nicht unterbrechend: Wenn der Member außerhalb der Assembly nicht sichtbar ist, unabhängig von der Änderung, die Sie vornehmen.<br /><br /> Nicht unterbrechend: Wenn Sie das Element nur mit dem-Schlüsselwort in einen Instanzmember ändern `this` .<br /><br /> Unterbrechen: Wenn Sie den Member von einem Instanzmember in einen statischen Member ändern und dieser außerhalb der Assembly sichtbar ist.|

## <a name="cause"></a>Ursache
 Ein Member, der nicht auf Instanzdaten zugreift, ist nicht als statisch gekennzeichnet (Shared in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ).

## <a name="rule-description"></a>Beschreibung der Regel
 Member, die nicht auf Instanzdaten zugreifen oder keine Instanzmethoden aufrufen, können als static markiert werden (Shared in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]). Danach gibt der Compiler nicht virtuelle Aufrufsites an diese Member aus. Durch das Ausgeben von nicht virtuellen-Aufrufsites wird für jeden-Befehl, der sicherstellt, dass der aktuelle Objekt Zeiger nicht NULL ist, zur Laufzeit eine Überprüfung verhindert. Dies kann zu einer messbaren Leistungssteigerung bei Leistungs sensiblem Code werden. In einigen Fällen stellt der Fehler beim Zugriff auf die aktuelle Objektinstanz ein Problem mit der Richtigkeit dar.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Markieren Sie den Member als statisch (oder freigegeben [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ), oder verwenden Sie "This"/"Me" im Methoden Text, falls zutreffend.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel für den zuvor gelieferten Code zu unterdrücken, dessen Behebung eine Breaking Change wäre.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1811: Nicht aufgerufenen privaten Code vermeiden.](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: Nicht instanziierte interne Klassen vermeiden.](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1804: Nicht verwendete lokale Variablen entfernen.](../code-quality/ca1804-remove-unused-locals.md)
