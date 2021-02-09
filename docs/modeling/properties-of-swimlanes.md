---
title: Eigenschaften von Verantwortlichkeitsbereichen
description: Erfahren Sie, wie Verantwortlichkeits Bereiche ein Diagramm in vertikale oder horizontale Bereiche aufteilen und wie Sie andere Formen definieren können, die innerhalb von Verantwortlichkeits Bereichen angezeigt werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.swimlane
helpviewer_keywords:
- Domain-Specific Language, swimlane
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 61994a25b5fa862a2014e2dd5b57a0c47130e6ba
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882985"
---
# <a name="properties-of-swimlanes"></a>Eigenschaften von Verantwortlichkeitsbereichen
Sie können einem Diagramm Verantwortlichkeits Bereiche hinzufügen. Swimlanes unterteilen ein Diagramm in vertikale oder horizontale Bereiche. Sie können andere Formen definieren, die in Swimlanes angezeigt werden. Weitere Informationen finden Sie unter Vorgehens [Weise beim Definieren einer Domain-Specific Sprache](../modeling/how-to-define-a-domain-specific-language.md). Weitere Informationen zur Verwendung dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer Domain-Specific Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Swimlanes verfügen über die Eigenschaften, die in der folgenden Tabelle aufgeführt sind.

|Eigenschaft|Beschreibung|Standard|
|-|-|-|
|Füllfarbe für Text|Die Füllfarbe für den Text der swimlane.|Weiß|
|Füllfarbe für Header|Die Füllfarbe für den Header der swimlane.|DarkGray|
|Trennzeichen Farbe|Die Farbe der Trennlinie.|Hellgrau|
|Trennlinien Stil|Der Stil der Trennlinie ( `Solid` , `Dash` , `Dot` , `DashDot` , `DashDotDot` oder `Custom` ).|`Dash`|
|Trennzeichen Stärke|Die Stärke der Trennlinie in Zoll.|0,03125|
|Textfarbe|Die Farbe, die für Text-Decorator verwendet wird, die dieser Swimlane zugeordnet sind.|Schwarz|
|Zugriffsmodifizierer|Die Zugriffsebene der Klasse ( `public` oder `internal` ).|Öffentlich|
|Benutzerdefinierte Attribute|Wird verwendet, um der Code Klasse Attribute hinzuzufügen, die von dieser Swimlane generiert werden.|\<none>|
|Generiert doppelte abgeleitete|Gibt `True` an, dass sowohl eine Basisklasse als auch eine partielle Klasse (zur Unterstützung der Anpassung durch über schreibungen) generiert werden. Weitere Informationen finden Sie unter Überschreiben [und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|Falsch|
|Hat benutzerdefinierten Konstruktor|Gibt `True` an, dass ein benutzerdefinierter Konstruktor im Quellcode bereitgestellt wird. Weitere Informationen finden Sie unter Überschreiben [und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|Falsch|
|Vererbungs Modifizierer|Beschreibt die Art der Vererbung der Quell Code Klasse, die aus der Swimlane ( `none` `abstract` oder) generiert wird `sealed` .|Keine|
|Grund Verantwortlichkeits Bereich|Die Basisklasse dieser swimlane.|(none)|
|Name|Der Name dieser swimlane.|Aktueller Name|
|Namespace|Der Namespace, der mit dieser Swimlane verbunden ist.|Aktueller Namespace|
|QuickInfo-Typ|Wie die QuickInfo definiert wird ( `fixed` , `variable` oder `none` ). Wenn `fixed` , dann wird der Wert der- `Fixed Tooltip Text` Eigenschaft verwendet. Wenn `variable` , dann wird die QuickInfo in benutzerdefiniertem Code definiert.|\<none>|
|Notizen|Informelle Notizen, die dieser Swimlane zugeordnet sind.|\<none>|
|Ausrichtung|Horizontale oder vertikale Ausrichtung.|Vertical|
|Anfängliche Höhe|Die Anfangshöhe dieser Swimlane in Zoll. Gilt nur für horizontale Swimlanes.|0|
|Anfängliche Breite|Die ursprüngliche Breite dieser Swimlane in Zoll. Gilt nur für vertikale Swimlanes.|0|
|Macht Textfarbe verfügbar.|Wenn `True` der Wert ist, kann der Benutzer die Farbe einer Swimlane im generierten Designer festlegen. Um dies festzulegen, klicken Sie mit der rechten Maustaste auf die Form Verantwortlichkeits Bereich und **Klicken auf verfügbar machen.**|Falsch|
|Beschreibung|Wird verwendet, um den generierten Designer zu dokumentieren.|\<none>|
|Anzeigename|Der Name, der im generierten Designer angezeigt wird, um auf diese Swimlane-Klasse zu verweisen.|\<none>|
|Fester QuickInfo-Text|Der Text, der für eine fixierte QuickInfo verwendet wird.|\<none>|
|Hilfsschlüsselwort|Das Schlüsselwort, das zum Indizieren der F1-Hilfe für diese Swimlane verwendet wird.|\<none>|

## <a name="see-also"></a>Weitere Informationen

- [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](/previous-versions/bb126564(v=vs.100))