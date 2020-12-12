---
title: Eigenschaften von Decorators
description: Erfahren Sie, dass Decorator Symbole, Text oder Erweiterungs-/Reduzierern sind, die auf Formen oder Connectors im Diagramm angezeigt werden können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, decorators
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef863d0d3dab394c2ca427a27d039c19e5921a51
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97360832"
---
# <a name="properties-of-decorators"></a>Eigenschaften von Decorators
Decoratoren sind Symbole, Text oder Erweiterungs-/reduzierungschevd, die auf Formen oder Connectors im Diagramm angezeigt werden können. Die folgenden Tabellen zeigen die Eigenschaften für die drei Arten von Decorator-Objekten. Einige Eigenschaften werden nur in Form-Decorator oder nur in Connector-Decorator-Zeichen angezeigt.

 Weitere Informationen finden Sie unter Vorgehens [Weise beim Definieren einer Domain-Specific Sprache](../modeling/how-to-define-a-domain-specific-language.md). Weitere Informationen zur Verwendung dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer Domain-Specific Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="expandcollapse-decorator"></a>Decorator erweitern/reduzieren

|Eigenschaft|BESCHREIBUNG|Standard|
|-|-|-|
|DisplayName|Der Name des Decorators, der im generierten Designer angezeigt wird.|Erweitern des aufklappen-Decorators|
|Name|Der Name des Decorators.|ExpandCollapseDecorator|
|Hinweise|Informelle Notizen, die diesem Decorator zugeordnet sind.|\<none>|
|Horizontal Offset|Der horizontale Offset relativ zur Standardposition des Decorator-in Zoll. (Nur bei Formen)|0|
|VerticalOffset|Der vertikale Offset relativ zur Standardposition des Decorator-in Zoll. (Nur bei Formen)|0|
|Offsetfromline|Der Offset des Decorators von der Linie relativ zu seiner Standardposition in Zoll. (Nur für Connectors.)|0|
|Offsetfromshape|Der Offset des Decorator-Konstruktors von der Form relativ zu seiner Standardposition in Zoll. (Nur für Connectors.)|0|
|Position|Die Standardposition des Decorator-Konstruktors.|SourceTop|

## <a name="icon-decorator"></a>Symboldecorator

|Eigenschaft|BESCHREIBUNG|Standard|
|-|-|-|
|DefaultIcon|Der Pfad der Symbol-oder Bilddatei, die angezeigt werden soll.|\<none>|
|DisplayName|Der Name des Decorator-Designers, der im generierten Designer angezeigt werden soll.|Symboldecorator|
|Name|Der Name des Decorators.|IconDecorator|
|Hinweise|Informelle Notizen, die dem Decorator zugeordnet sind.|\<none>|
|Horizontal Offset|Der horizontale Offset relativ zur Standardposition des Decorator-in Zoll. (Nur bei Formen)|0|
|VerticalOffset|Der vertikale Offset relativ zur Standardposition des Decorator-in Zoll. (Nur bei Formen)|0|
|Offsetfromline|Der Offset des Decorators von der Linie relativ zu seiner Standardposition in Zoll. (Nur für Connectors.)|0|
|Offsetfromshape|Der Offset des Decorator-Konstruktors von der Form relativ zu seiner Standardposition in Zoll. (Nur für Connectors.)|0|
|Position|Die Standardposition des Decorator-Konstruktors.|SourceTop|

## <a name="textdecorator"></a>TextDecorator

|Eigenschaft|BESCHREIBUNG|Standard|
|-|-|-|
|DefaultText|Der Standardtext, der angezeigt werden soll.|Label|
|DisplayName|Der Name des Decorator-Designers, der im generierten Designer angezeigt werden soll.|Label|
|FontSize|Der Schrift Grad für den Text, der im Decorator angezeigt wird.|8|
|FontStyle|Der Schriftart Stil für den Text, der im Decorator angezeigt wird.|Regulär|
|Name|Der Name des Decorators.|Label|
|Hinweise|Informelle Notizen, die dem Decorator zugeordnet sind.|\<none>|
|Horizontal Offset|Der horizontale Offset relativ zur Standardposition des Decorator-in Zoll. (Nur bei Formen)|0|
|VerticalOffset|Der vertikale Offset relativ zur Standardposition des Decorator-in Zoll. (Nur bei Formen)|0|
|Offsetfromline|Der Offset des Decorators von der Linie relativ zu seiner Standardposition in Zoll. (Nur für Connectors.)|0|
|Offsetfromshape|Der Offset des Decorator-Konstruktors von der Form relativ zu seiner Standardposition in Zoll. (Nur für Connectors.)|0|
|Position|Die Standardposition des Decorator-Konstruktors.|TargetBottom|

## <a name="see-also"></a>Siehe auch

- [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](/previous-versions/bb126564(v=vs.100))