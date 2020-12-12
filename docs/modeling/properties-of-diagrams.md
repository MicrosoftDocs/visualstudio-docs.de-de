---
title: Eigenschaften von Diagrammen
description: Hier finden Sie Informationen zu Diagrammen und zum Festlegen von Eigenschaften, die angeben, wie Diagramme im generierten Designer angezeigt werden.
ms.custom: SEO-VS-2020
ms.date: 10/31/2018
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe27eb7dcfb8a984fceaee0700e1df44b6de4ef1
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361949"
---
# <a name="properties-of-diagrams"></a>Eigenschaften von Diagrammen
Sie können Eigenschaften festlegen, die angeben, wie Diagramme im generierten Designer angezeigt werden. Beispielsweise können Sie im Diagramm eine Standardfarbe für Text angeben.

 Weitere Informationen finden Sie unter [Definieren einer domänenspezifischen Sprache](../modeling/how-to-define-a-domain-specific-language.md). Weitere Informationen zur Verwendung dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

 In der folgenden Tabelle sind die Eigenschaften von Diagrammen aufgeführt.

|Eigenschaft|BESCHREIBUNG|Standard|
|-|-|-|
|Füllfarbe|Die Füllfarbe für das Diagramm.|White|
|Textfarbe|Die Farbe des Texts, der im Diagramm angezeigt wird.|Schwarz|
|Zugriffsmodifizierer|Der Zugriffsmodifizierer der-Klasse (Public oder Internal).|Öffentlich|
|Benutzerdefinierte Attribute|Wird verwendet, um der generierten Code Klasse Attribute hinzuzufügen.|\<none>|
|Generiert doppelte abgeleitete|Gibt `True` an, dass sowohl eine Basisklasse als auch eine partielle Klasse (zur Unterstützung der Anpassung durch über schreibungen) generiert werden. Weitere Informationen finden Sie unter über [schreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|Falsch|
|Hat benutzerdefinierten Konstruktor|Gibt `True` an, dass ein benutzerdefinierter Konstruktor im Quellcode bereitgestellt wird. Weitere Informationen finden Sie unter über [schreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|Falsch|
|Vererbungs Modifizierer|Beschreibt die Art der Vererbung der Quell Code Klasse, die aus dem Diagramm generiert wird ( `none` , `abstract` oder `sealed` ).|Keine|
|Basis Diagramm|Die Basisklasse dieses Diagramms.|(none)|
|Name|Der Name dieses Diagramms.|Aktueller Name|
|Namespace|Der Namespace, der mit diesem Diagramm verbunden ist.|Aktueller Namespace|
|Dargestellte Klasse|Die Stamm Domänen Klasse, die dieses Diagramm darstellt.|Aktuelle Stamm Klasse, falls zutreffend|
|Hinweise|Informelle Notizen, die diesem Element zugeordnet sind.|\<none>|
|Macht die Füllfarbe als Eigenschaft verfügbar.|Wenn `True` der Wert ist, kann der Benutzer die Füllfarbe des Diagramms des generierten Designers festlegen. Klicken Sie zum Festlegen dieser Eigenschaft mit der rechten Maustaste auf die Form Diagramm, und klicken **Sie auf verfügbar machen.**|Falsch|
|Macht Textfarbe als Eigenschaft verfügbar.|Wenn `True` der Wert ist, kann der Benutzer die Textfarbe des Diagramms im generierten Designer festlegen. Klicken Sie zum Festlegen dieser Eigenschaft mit der rechten Maustaste auf die Form Diagramm, und klicken **Sie auf verfügbar machen.**|Falsch|
|Beschreibung|Die Beschreibung, die zum Dokumentieren des generierten Designers verwendet wird.|\<none>|
|Anzeigename|Der Name, der im generierten Designer für dieses Diagramm angezeigt wird.|\<none>|
|Hilfsschlüsselwort|Das Schlüsselwort, das zum Indizieren der F1-Hilfe für dieses Diagramm verwendet wird.|\<none>|

## <a name="see-also"></a>Siehe auch

[Glossar für domänenspezifische Sprach Tools](/previous-versions/bb126564(v=vs.100))