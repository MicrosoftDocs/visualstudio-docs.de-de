---
title: Eigenschaften von Geometrie Formen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.geometryshape
helpviewer_keywords:
- Domain-Specific Language, geometry shape
ms.assetid: 3993a23e-eab3-4ceb-b475-c395d5992bfc
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 10b6d282475d3298f15319d89684f9b042bee5f6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671401"
---
# <a name="properties-of-geometry-shapes"></a>Eigenschaften geometrischer Formen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mithilfe von Geometrie Formen können Sie angeben, wie Instanzen von Domänen Klassen in einer domänenspezifischen Sprache angezeigt werden. Weitere Informationen finden Sie unter [Definieren einer domänenspezifischen Sprache](../modeling/how-to-define-a-domain-specific-language.md). Weitere Informationen zur Verwendung dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Geometrie Formen verfügen über die Eigenschaften, die in der folgenden Tabelle aufgeführt sind.

|Eigenschaft|BESCHREIBUNG|Standard|
|--------------|-----------------|-------------|
|Füllfarbe|Die Füllfarbe dieser Form.|White|
|Füllverlaufs Modus|Der Füllmodus für den Füllmodus dieser Form (horizontal, vertikal, vorwärts Diagonal, rückwärts diagonal oder keine).|Horizontal|
|Geometrie|Die Geometrie dieser Form (Rechteck, abgerundetes Rechteck, Ellipse oder Kreis).|Rechteck|
|Hat Standard Verbindungspunkte|Wenn `True` , verwendet die Form die oberen, unteren, linken und rechten Verbindungspunkte im generierten Designer.|Falsch|
|Umriss Farbe|Die Kontur Farbe dieser Form.|Schwarz|
|Umriss Strich Stil|Der Umriss Strich Stil dieser Form (Solid, Dash, dot, DashDot, DashDotDot oder Custom).|Basis|
|Kontur Stärke|Die Gliederungs Stärke dieser Form.|0,03125|
|Textfarbe|Die Farbe, die für Text-Decorator verwendet wird, die dieser Form zugeordnet sind.|Schwarz|
|Zugriffsmodifizierer|Der Zugriffsmodifizierer der-Klasse (Public oder Internal).|Öffentlich|
|Benutzerdefinierte Attribute|Wird verwendet, um der Quell Code Klasse Attribute hinzuzufügen, die für diese Form generiert werden.|\<none>|
|Generiert doppelte abgeleitete|Gibt `True` an, dass sowohl eine Basisklasse als auch eine partielle Klasse (zur Unterstützung der Anpassung durch über schreibungen) generiert werden. Weitere Informationen finden Sie unter Überschreiben [und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|Falsch|
|Hat benutzerdefinierten Konstruktor|Gibt `True` an, dass ein benutzerdefinierter Konstruktor im Quellcode bereitgestellt wird. Weitere Informationen finden Sie unter Überschreiben [und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|Falsch|
|Vererbungs Modifizierer|Beschreibt die Art der Vererbung der Quell Code Klasse, die aus der Form ( `none` `abstract` oder) generiert wird `sealed` .|Keine|
|Basis Geometrie Form|Die Basisklasse dieser Form.|(none)|
|Name|Der Name dieser Form.|Aktueller Name|
|Namespace|Der Namespace, der mit dieser Form verbunden ist.|Aktueller Namespace|
|QuickInfo-Typ|Wie die QuickInfo definiert wird (Fixed, Variable oder None). Wenn Sie festgelegt ist, wird der Wert der `Fixed Tooltip Text` Eigenschaft als QuickInfo verwendet. wenn die Variable ist, wird die QuickInfo in benutzerdefiniertem Code definiert.|Keine|
|Notizen|Informelle Notizen, die diesem Element zugeordnet sind.|\<none>|
|Anfängliche Höhe|Anfängliche Höhe dieser Form in Zoll.|1|
|Anfängliche Breite|Anfängliche Breite dieser Form in Zoll.|1.5|
|Verfügbar gemachte Füllfarbe als Eigenschaft<br /><br /> Offen gelegter Füllverlaufs Modus<br /><br /> Verfügbar gemachte Umriss Farbe als Eigenschaft<br /><br /> Darstellung des Gliederungs Bindestrich Stils als Eigenschaft<br /><br /> Verfügbar gemachte Gliederungs Stärke als Eigenschaft<br /><br /> Macht Textfarbe verfügbar.|Wenn `True` der Wert ist, kann der Benutzer die angegebene Eigenschaft einer Form festlegen. Um dies festzulegen, klicken Sie mit der rechten Maustaste auf die Form Definition, und **Klicken Sie auf**verfügbar machen|Falsch|
|BESCHREIBUNG|Die Beschreibung, die zum Dokumentieren des generierten Designers verwendet wird.|\<none>|
|Anzeigename|Der Name, der im generierten Designer für diese Form angezeigt wird.|\<none>|
|Fester QuickInfo-Text|Der Text, der für eine fixierte QuickInfo verwendet wird.|\<none>|
|Hilfsschlüsselwort|Das Schlüsselwort, das zum Indizieren der F1-Hilfe für diese Form verwendet wird.|\<none>|

## <a name="see-also"></a>Weitere Informationen
 [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
