---
title: Eigenschaften von Domänenklassen
description: Erfahren Sie mehr über die verschiedenen Eigenschaften von Domänen Klassen, z. b. Zugriffsmodifizierer, benutzerdefinierte Attribute und generierte doppelte abgeleitete
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain class
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cc86f04841a819423bc45c9220d6de80a5340b2d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99916001"
---
# <a name="properties-of-domain-classes"></a>Eigenschaften von Domänenklassen
Domänen Klassen verfügen über die in der folgenden Tabelle aufgeführten Eigenschaften. Weitere Informationen zu Domänen Klassen finden Sie Untergrund Legendes zu [Modellen, Klassen und Beziehungen](../modeling/understanding-models-classes-and-relationships.md). Weitere Informationen zur Verwendung dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer Domain-Specific Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Eigenschaft|BESCHREIBUNG|Standard|
|-|-|-|
|Zugriffsmodifizierer|Die Zugriffsebene der Domänenklasse (`public` oder `internal`).|`public`|
|Benutzerdefinierte Attribute|Wird verwendet, um der Quell Code Klasse Attribute hinzuzufügen, die von dieser Domänen Klasse generiert werden.|\<none>|
|Generiert doppelte abgeleitete|Gibt `True` an, dass sowohl eine Basisklasse als auch eine partielle Klasse (zur Unterstützung der Anpassung durch über schreibungen) generiert werden. Weitere Informationen finden Sie unter Überschreiben [und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Hat benutzerdefinierten Konstruktor|Gibt `True` an, dass ein benutzerdefinierter Konstruktor im Quellcode bereitgestellt wird. Weitere Informationen finden Sie unter Überschreiben [und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Vererbungs Modifizierer|Beschreibt die Art der Vererbung der Quell Code Klasse, die von der Domänen Klasse ( `none` oder) generiert wird `abstract` `sealed` .|`none`|
|Basisklasse|Wenn diese Domänen Klasse abgeleitet ist, der Name der Basisklasse.|\<none>|
|Name|Der Name dieser Domänen Klasse.|Aktueller Name|
|Namespace|Der Namespace dieser Domänen Klasse.|Aktueller Namespace|
|Notizen|Informelle Notizen, die dieser Domänen Klasse zugeordnet sind.|\<none>|
|BESCHREIBUNG|Die Beschreibung, die verwendet wird, um die Benutzeroberfläche des generierten Designers zu dokumentieren.|\<none>|
|Anzeigename|Der Name, der im generierten Designer für diese Domänen Klasse angezeigt wird.|\<none>|
|Hilfsschlüsselwort|Das optionale Schlüsselwort, das zum Indizieren der F1-Hilfe für diese Domänen Klasse verwendet wird.|\<none>|

## <a name="see-also"></a>Weitere Informationen

- [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](/previous-versions/bb126564(v=vs.100))