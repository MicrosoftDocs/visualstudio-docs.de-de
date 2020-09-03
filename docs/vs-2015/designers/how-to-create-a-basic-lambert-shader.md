---
title: 'Vorgehensweise: Erstellen eines Lambert-Shaders | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: ec5c10fb-9600-4240-8280-d59451ea1d68
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 038b3e7db7f1e3b79ee3e41b6e256216a39b91bd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664557"
---
# <a name="how-to-create-a-basic-lambert-shader"></a>Gewusst wie: Erstellen eines Lambert-Shaders
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Dokument wird gezeigt, wie der Shader-Designer und die Directed Graph Shader Language (DGSL) zum Erstellen eines Beleuchtungsshaders, der das klassische Lambert-Beleuchtungsmodell implementiert, verwendet wird.

 In diesem Dokument werden die folgenden Aktivitäten veranschaulicht:

- Hinzufügen von Knoten in ein Shader-Diagramm

- Trennen der Knoten

- Verbinden der Knoten

## <a name="the-lambert-lighting-model"></a>Das Lambert-Beleuchtungsmodell
 Das Lambert-Beleuchtungsmodell umfasst gerichtete und Umgebungsbeleuchtung, um Objekte in einer 3D-Szene zu schattieren. Die Umgebungskomponenten sorgen für die Basis der Beleuchtung in der 3D-Szene. Die Richtungskomponente sorgen für zusätzliche Beleuchtung von einer gerichteten (weit entfernten) Lichtquelle. Umgebungsbeleuchtung wirkt sich auf alle Oberflächen in der Szene gleich aus, unabhängig von deren Ausrichtung. Für eine bestimmte Oberfläche ist es ein Produkt aus der Umgebungsfarbe der Oberfläche sowie der Farbe und Intensität des Umgebungslichts in der Szene. Gerichtete Beleuchtung wirkt sich auf jede Oberfläche in der Szene unterschiedlich aus, je nach Ausrichtung der Oberfläche in Bezug auf die Richtung der Lichtquelle. Es ist ein Produkt aus der diffusen Farbe und Ausrichtung der Oberfläche sowie der Farbe, Intensität und Ausrichtung der Lichtquelle. Oberflächen, die direkt auf die Lichtquelle zeigen, erhalten die maximale Einwirkung, während Oberflächen, die direkt weg zeigen, keine Einwirkung erhalten. Unter dem Lambert-Beleuchtungsmodell werden die Umgebungskomponente und eine oder mehrere Richtungskomponenten kombiniert, um die gesamte diffuse Farbeinwirkung für jeden Punkt am Objekt festzulegen.

 Bevor Sie beginnen, stellen Sie sicher, dass das Fenster **Eigenschaften** und die **Toolbox** angezeigt werden.

#### <a name="to-create-a-lambert-shader"></a>So erstellen Sie einen Lambert-Shader

1. Erstellen Sie einen DGSL-Shader, mit dem Sie arbeiten können. Wie Sie dem Projekt einen DGSL-Shader hinzufügen, erfahren Sie im Abschnitt „Erste Schritte“ unter [Shader-Designer](../designers/shader-designer.md)

2. Trennen Sie den Knoten **Farbpunkt** vom Knoten **Endgültige Farbe**. Klicken Sie auf das Terminal **RGB** des Knotens **Farbpunkt** und anschließend auf **Link aufheben**. Lassen Sie das Terminal **Alpha** verbunden.

3. Fügen Sie einen Knoten **Lambert** in das Diagramm ein. Klicken Sie in der **Toolbox** unter **Hilfsprogramme** auf **Lambert**, und verschieben Sie es auf die Entwurfsoberfläche. Der Lambert-Knoten berechnet anhand der Umgebungs- und diffusen Lichtparameter die gesamte diffuse Lichteinwirkung des Pixels.

4. Verbinden Sie den Knoten **Farbpunkt** mit dem Knoten **Lambert**. Verschieben Sie im Modus **Auswählen** das Terminal **RGB** des Knotens **Farbpunkt** auf das Terminal **Diffuses Licht** des Knotens **Lambert**. Diese Verbindung versorgt den Lambert-Knoten mit der interpolierten diffusen Farbe des Pixels.

5. Verbinden Sie den berechneten Farbwert mit der endgültige Farbe. Verschieben Sie das Terminal **Ausgabe** des Knotens **Lambert** auf das Terminal **RGB** des Knotens **Endgültige Farbe**.

   In der folgenden Abbildung wird das fertige Shader-Diagramm sowie eine Vorschau eines Teekannenmodells gezeigt, auf dem der Shader angewandt wurde.

> [!NOTE]
> Es wurde eine orangene Farbe durch die Verwendung des Parameters **MaterialDiffuse** des Shaders angegeben, um den Effekt des Shaders in dieser Abbildung besser veranschaulichen. Ein Spiel oder eine Anwendung kann diesen Parameter verwenden, um für jedes Objekt einen eindeutigen Farbwert bereitzustellen. Weitere Informationen zu Materialparameter finden Sie im Abschnitt „Vorschau von Shader verwenden“ unter [Shader-Designer](../designers/shader-designer.md).

 ![Shader-Diagramm und eine Vorschau seiner Effekte](../designers/media/digit-lambert-effect-graph.png "Ziffern-Lambert-Effect-Graph")

 Bestimmte Formen sorgen vielleicht für bessere Vorschauen für einige Shader. Weitere Informationen zum Anzeigen einer Vorschau von Shadern im Shader-Designer finden Sie im Abschnitt Vorschau von Shadern im [Shader-Designer](../designers/shader-designer.md).

 In der folgenden Abbildung wird der Shader gezeigt, der, wie in diesem Dokument beschrieben, auf ein 3D-Modell angewandt wurde.

 ![Lambert-Beleuchtung in einem Modell](../designers/media/digit-lambert-effect-result.png "Digit-Lambert-Effect-result")

 Weitere Informationen zum Anwenden eines Shaders auf ein 3D-Modell finden Sie unter Gewusst [wie: Anwenden eines Shaders auf ein 3D-Modell](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Weitere Informationen
 [Vorgehensweise: Anwenden eines Shaders auf ein 3D-Modell Gewusst](../designers/how-to-apply-a-shader-to-a-3-d-model.md) [wie: Exportieren eines Shaders](../designers/how-to-export-a-shader.md) Gewusst [wie: Erstellen eines einfachen Phong-Shader](../designers/how-to-create-a-basic-phong-shader.md) -Shader- [Designer](../designers/shader-designer.md) - [Knotens](../designers/shader-designer-nodes.md)
