---
title: Shader-Designer-Knoten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: f5192fbd-c78f-40a8-a4d4-443209610268
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b7526da10262003c9d086fdf1d74d065aac2d406
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664128"
---
# <a name="shader-designer-nodes"></a>Shader-Designer-Knoten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Artikel in diesem Dokumentationsabschnitt enthalten Informationen zu verschiedenen Shader-Designer-Knoten, die Sie zum Erstellen von grafischen Effekten verwenden können.

## <a name="nodes-and-node-types"></a>Knoten und Knotentypen
 Der Shader-Designer stellt visuelle Effekte als Diagramm dar. Diese Diagramme werden aus Knoten erstellt, die speziell ausgewählt werden und so miteinander verbunden sind, dass der gewünschte Effekt erreicht wird. Jeder Knoten stellt entweder eine Information oder eine mathematische Funktion dar. Außerdem stellen die Verbindungen dieser Knoten miteinander dar, wie die Informationen durch das Diagramm fließen, um ein Ergebnis zu erzielen. Der Shader-Designer stellt sechs verschiedene Knotentypen (Filter, Texturknoten, Parameter, Konstanten, Hilfsprogrammknoten und Berechnungsknoten) und einige individuelle Knoten bereit, die zu jedem Typ gehören. Diese Knoten und Knotentypen werden in anderen Artikeln beschrieben, die zu diesem Bereich gehören (vgl. die Links am Ende dieses Dokuments).

## <a name="node-structure"></a>Knotenstruktur
 Alle Knoten bestehen aus einer Kombination aus gemeinsamen Elementen. Jeder Knoten verfügt auf der rechten Seite über mindestens ein Ausgabeterminal (außer Farbknoten, die die Ausgabe des Shaders darstellen). Knoten, die Berechnungs- oder Textursampler darstellen, verfügen auf der linken Seite über Eingabeterminals. Knoten, die Informationen darstellen, haben hingegen keine Eingabeterminals. Ausgabeterminals sind mit den Eingabeterminals verbunden, damit sie Informationen von einem Knoten an einen anderen verschieben können.

### <a name="promotion-of-inputs"></a>Heraufstufung von Eingaben
 Da der Shader-Designer letztendlich HLSL-Quellcode generieren muss, damit der Effekt in einem Spiel oder einer App verwendet werden kann, sind Shader-Designerknoten Teil der Regeln zur Typerweiterung, die HLSL verwendet. Da die Grafikhardware hauptsächlich mit Gleitkommawerten arbeitet, ist die Typerweiterung zwischen verschiedenen Typen (z.B. von `int` auf `float` oder von `float` auf `double`) eher ungewöhnlich. Da Grafikhardware den gleichen Vorgang auf mehrere Informationspakete gleichzeitig anwendet, findet eine andere Art der Heraufstufung statt, bei der kürzere Eingabewerte erweitert werden, um sie an die längsten Eingabewerte anzugleichen. Auf welche Weise die Eingabe verlängert wird hängt von deren Typ und dem Vorgang an sich ab:

- **Wenn der kleinere Typ ein Skalarwert ist, dann:**

     Ist der Wert des Skalars in einen Vektor repliziert, der die gleiche Größe hat wie die größere Eingabe. Beispielsweise wird die Skalareingabe 5,0 zum Vektor (5,0, 5,0, 5,0), wenn die längste Eingabe des Vorgangs ein Drei-Elemente-Vektor ist, unabhängig davon, um welchen Vorgang es sich handelt.

- **Wenn es sich bei dem kleineren Typ um einen Vektor handelt und der Vorgang multiplikativ ist (\*, /, %, etc.), dann:**

     Wird der Wert des Vektors in die führenden Elemente eines Vektors kopiert, der der Größe der größeren Eingabe entspricht, und die nachstehenden Elemente sind auf 1,0 festgelegt. Beispielsweise wird die Vektoreingabe (5,0, 5,0) zum Vektor (5,0, 5,0, 1,0, 1,0), wenn er von einem Vier-Elemente-Vektor multipliziert werden soll. Dabei bleiben jeweils die dritten und vierten Elemente der Ausgabe erhalten, indem das neutrale Element der Multiplikation 1,0 verwendet wird.

- **Wenn es sich bei dem kleineren Typ um einen Vektor handelt und der Vorgang additiv ist (+, –, etc.), dann:**

     Der Wert des Vektors wird in die führenden Elemente eines Vektors kopiert, der der Größe der größeren Eingabe entspricht, und die nachstehenden Elemente sind auf 0,0 festgelegt. Beispielsweise wird die Vektoreingabe (5,0, 5,0) zum Vektor (5,0, 5,0, 0,0, 0,0), wenn er von einem Vier-Elemente-Vektor multipliziert werden soll. Dabei bleiben jeweils die dritten und vierten Elemente der Ausgabe erhalten, indem die additive Identität 0,0 verwendet wird.

## <a name="related-topics"></a>Verwandte Themen

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[Konstante Knoten](../designers/constant-nodes.md)|Beschreibt Knoten, die Sie verwenden können, um Literalwerte und interpolierte Informationen zu Vertexzuständen in Shader-Berechnungen darzustellen. Vertexzustände werden interpoliert und unterscheiden sich daher in jedem Pixel: Jede Pixel-Shader-Instanz empfängt eine andere Version der Konstanten.|
|[Parameter Knoten](../designers/parameter-nodes.md)|Beschreibt Knoten, die Sie zur Darstellung der Kameraposition, Materialeigenschaften, Lichtparameter, Zeit und andere Informationen zum App-Status in Shader-Berechnungen verwenden können.|
|[Textur Knoten](../designers/texture-nodes.md)|Beschreibt die Knoten, die Sie verwenden können, um verschiedene Texturtypen und Geometrien abzufragen und Texturkoordinaten auf gewöhnliche Weise zu erzeugen oder zu transformieren.|
|[Mathematische Knoten](../designers/math-nodes.md)|Beschreibt die Knoten, die Sie verwenden können, um algebraische, logische, trigonometrische und andere mathematische Vorgänge durchzuführen, die den HLSL-Anweisungen direkt zugeordnet werden.|
|[Hilfsprogrammknoten](../designers/utility-nodes.md)|Beschreibt die Knoten, die Sie verwenden können, um allgemeine Lichtberechnungen und andere allgemeine Vorgänge durchzuführen, die den HLSL-Anweisungen direkt zugeordnet werden.|
|[Filter Knoten](../designers/filter-nodes.md)|Beschreibt die Knoten, die Sie verwenden können, um die Textur- und Farbfilterung durchzuführen.|
