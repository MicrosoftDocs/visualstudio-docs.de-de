---
title: Eigenschaften von Elementen in UML-Komponenten Diagrammen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.componentdiagram.shapes.properties
helpviewer_keywords:
- component diagrams, properties
- UML, element properties
ms.assetid: fa0a9460-6675-4642-aa00-50f8719a892d
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 39350a9e1d340651f8e15de109ecf61eb98996bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671450"
---
# <a name="properties-of-elements-on-uml-component-diagrams"></a>Eigenschaften von Elementen in UML-Komponentendiagrammen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jedes Element in einem UML-Komponentendiagramm hat Eigenschaften. Um die Eigenschaften eines Elements anzuzeigen, klicken Sie mit der rechten Maustaste auf das Element im Diagramm oder im **UML-Modell-Explorer** , und klicken Sie dann auf **Eigenschaften**. Die Eigenschaften werden im **Eigenschaften** Fenster angezeigt.

> [!NOTE]
> In diesem Thema werden die Eigenschaften von Elementen in UML-Komponentendiagrammen behandelt. Weitere Informationen zum Lesen von UML-Komponenten Diagrammen finden Sie unter [UML-Komponenten Diagramme: Referenz](../modeling/uml-component-diagrams-reference.md). Weitere Informationen zum Zeichnen von UML-Komponenten Diagrammen finden Sie unter [UML-Komponenten Diagramme: Richtlinien](../modeling/uml-component-diagrams-guidelines.md).

## <a name="properties-of-elements"></a>Eigenschaften von Elementen

|Eigenschaft|Standard|Element|BESCHREIBUNG|
|--------------|-------------|-------------|-----------------|
|**Name**|Ein Standardname|All|Bezeichnet das Element.|
|**Qualifizierter Name**|Namespace :: Name|All|Bezeichnet das Element eindeutig.<br /><br /> Dem Namen einer Komponente oder eines Typs wird der qualifizierte Name des Pakets vorangestellt, in dem die Komponente bzw. der Typ enthalten ist.<br /><br /> Dem Namen eines Teils oder Ports wird der qualifizierte Name der Komponente vorangestellt, die Besitzer des Teils bzw. Ports ist.|
|**Arbeitselemente**|0 zugeordnet|All|Die Anzahl von Arbeitselemente, die diesem Element zugeordnet sind. Informationen zum Zuordnen von Arbeitsaufgaben finden Sie unter [Verknüpfen von Modellelementen und Arbeits Elementen](../modeling/link-model-elements-and-work-items.md).|
|**Beschreibung**|(none)|All|Hier können Sie allgemeine Anmerkungen zum Element eingeben.|
|**Farbe**|(Standardeinstellung für den Typ)|Komponente, Teil, Delegierung, Teilassembly|Die Farbe der Form. Im Gegensatz zu anderen Eigenschaften ist dies die Farbe der Form und nicht des Modellelements, das von der Form angezeigt wird.|
|**Wird indirekt instanziiert**|Richtig|Komponente|Die Komponente ist nur als Entwurfsartefakt vorhanden. Zur Laufzeit sind nur ihre Teile vorhanden.|
|**Ist abstrakt**|Falsch|Komponente|Die Komponentendefinition kann nur als Verallgemeinerung verwendet werden, von der spezifischere Komponenten abgeleitet werden können.|
|**Sichtbarkeit**|Öffentlich|Komponente, Teil, Port|**Public** -Global sichtbar.<br /><br /> **Paket** -sichtbar innerhalb des Pakets.<br /><br /> **Privat** -sichtbar innerhalb der besitzenden Komponente.<br /><br /> **Geschützt** : sichtbar für Komponenten, die vom Besitzer abgeleitet werden.|
|**Type**|Typ bei der Erstellung|Teil<br /><br /> Port|Der Typ eines Teils ist eine Komponente oder Klasse.<br /><br /> Der Typ eines Ports ist eine Schnittstelle.|
|**Multiplizität**|1|Teil<br /><br /> Port|Gibt an, wie viele Instanzen des angegebenen Typs einen Teil der übergeordneten Komponente bilden.<br /><br /> `1` -genau 1.<br /><br /> `0..1` -One oder None.<br /><br /> `*` -eine Auflistung einer beliebigen Zahl.<br /><br /> `n..m` : eine Auflistung von zwischen n und m Instanzen.|
|**Is Behavior**|Falsch|Port|Wenn „true“, werden Meldungen an diesen Port von Aktivitäten oder Vorgängen behandelt, die als Teil der Komponente statt als Teile des Teils beschrieben werden.|
|**Is Service**|Falsch|Port|Wenn „true“, ist dieser Port Teil der veröffentlichten Schnittstelle dieser Komponente.|
|**LinkedPackage**|Modell|Diagramm|Der Standardnamespace für diesem Diagramm hinzugefügte Elemente.|

## <a name="see-also"></a>Weitere Informationen
 [UML-Anwendungsfall Diagramme: Referenz](../modeling/uml-use-case-diagrams-reference.md) [UML-Anwendungsfall Diagramme: Richtlinien](../modeling/uml-use-case-diagrams-guidelines.md)
