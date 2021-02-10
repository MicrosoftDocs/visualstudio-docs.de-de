---
title: 'Gewusst wie: Erstellen eines standardmäßigen Phong-Shaders'
description: Erfahren Sie, wie mit dem Shader-Designer und der Directed Graph Shader Language (DGSL) ein Beleuchtungsshader erstellt wird, der das klassische Phong-Beleuchtungsmodell implementiert.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c7c69da8-142b-4d3b-9be9-4be0d5970b25
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b5319526da9aa59951729389749e53f3df65b643
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99915721"
---
# <a name="how-to-create-a-basic-phong-shader"></a>Vorgehensweise: Erstellen eines Standard-Phong-Shaders

In diesem Artikel wird veranschaulicht, wie der Shader-Designer und die Directed Graph Shader Language (DGSL) zum Erstellen eines Beleuchtungsshaders verwendet wird, der das klassische Phong-Beleuchtungsmodell implementiert.

## <a name="the-phong-lighting-model"></a>Das Phong-Beleuchtungsmodell

Das Phong-Beleuchtungsmodell erweitert das Lambert-Beleuchtungsmodell, indem es Glanzlichter hinzufügt, die die reflektierenden Eigenschaften einer Oberfläche simulieren. Die glänzende Komponente sorgt für zusätzliche Beleuchtung aus den gleichen diffusen Lichtquellen, die im Lambert-Beleuchtungsmodell verwendet werden. Jedoch wird sein Beitrag zur endgültigen Farbe unterschiedlich verarbeitet. Aufgrund der Beziehung zwischen der Blickrichtung, der Richtung der Lichtquellen und der Ausrichtung der Oberfläche, wirken sich Glanzlichter auf jede Oberfläche in der Szene unterschiedlich aus. Es ist ein Produkt aus der glänzenden Farbe, der Glanzkraft und Ausrichtung der Oberfläche sowie der Farbe, Intensität und Ausrichtung der Lichtquelle. Oberflächen, die die Lichtquelle direkt auf den Betrachter reflektieren, erhalten die maximale Glanzwirkung, während Oberflächen, die die Lichtquelle vom Betrachter weglenken, keine Wirkung erhalten. Unter dem Phong-Beleuchtungsmodell werden eine oder mehrere glänzende Komponenten kombiniert, um die Farbe und Intensität des Glanzlichts für jeden Punkt auf dem Objekt festzulegen und werden anschließend zum Ergebnis des Lambert-Beleuchtungsmodells hinzugefügt, um die endgültige Farbe des Pixels zu erzeugen.

Weitere Informationen zum Lambert-Beleuchtungsmodell finden Sie unter [Vorgehensweise: Erstellen eines einfachen Lambert-Shaders](../designers/how-to-create-a-basic-lambert-shader.md) beschrieben.

Bevor Sie beginnen, stellen Sie sicher, dass das Fenster **Eigenschaften** und die **Toolbox** angezeigt werden.

1. Erstellen Sie einen Lambert-Shader wie unter [Vorgehensweise: Erstellen eines einfachen Lambert-Shaders](../designers/how-to-create-a-basic-lambert-shader.md) beschrieben.

2. Trennen Sie den Knoten **Lambert** vom Knoten **Endgültige Farbe**. Klicken Sie auf das Terminal **RGB** des Knotens **Lambert** und anschließend auf **Link aufheben**. Dadurch wird Platz für den Knoten geschaffen, der im nächsten Schritt hinzugefügt wird.

3. Fügen Sie einen Knoten **Hinzufügen** in das Diagramm ein. Klicken Sie in der **Toolbox** unter **Mathematik** auf **Hinzufügen**, und verschieben Sie es auf die Entwurfsoberfläche.

4. Fügen Sie einen Knoten **Glanz** in das Diagramm ein. Klicken Sie in der **Toolbox** unter **Hilfsprogramme** auf **Glanz**, und verschieben Sie es auf die Entwurfsoberfläche.

5. Fügen Sie die Glanzwirkung hinzu. Verschieben Sie das Terminal **Ausgabe** des Knotens **Glanz** auf das Terminal **X** des Knotens **Hinzufügen**. Verschieben Sie anschließend das Terminal **Ausgabe** des Knotens **Lambert** auf das Terminal **Y** des Knotens **Hinzufügen**. Diese Verbindungen kombinieren die gesamten diffusen und glänzenden Farbeinwirkungen für das Pixel.

6. Verbinden Sie den berechneten Farbwert mit der endgültige Farbe. Verschieben Sie das Terminal **Ausgabe** des Knotens **Hinzufügen** auf das Terminal **RGB** des Knotens **Endgültige Farbe**.

   In der folgenden Abbildung wird das fertige Shader-Diagramm sowie eine Vorschau eines Teekannenmodells gezeigt, auf dem der Shader angewandt wurde.

> [!NOTE]
> Es wurde eine orangene Farbe durch die Verwendung des Parameters **MaterialDiffuse** des Shaders sowie ein metallfarbenes Finish durch die Verwendung der Parameter **MaterialSpecular** und **MaterialSpecularPower** angegeben, um den Effekt des Shaders in dieser Abbildung besser zu veranschaulichen. Weitere Informationen zu Materialparameter finden Sie im Abschnitt „Vorschau von Shader verwenden“ unter [Shader-Designer](../designers/shader-designer.md).

![Shader-Diagramm und eine Vorschau seiner Effekte](../designers/media/digit-lighting-graph.png)

Bestimmte Formen sorgen vielleicht für bessere Vorschauen für einige Shader. Weitere Informationen zur Verwendung der Vorschau von Shadern im Shader-Designer finden Sie im Abschnitt „Vorschau von Shadern verwenden“ unter [Shader-Designer](../designers/shader-designer.md).

In der folgenden Abbildung wird der auf ein 3D-Modell angewendete Shader dargestellt, der in diesem Dokument beschrieben wurde. Die Eigenschaft **MaterialSpecular** ist auf (1,00, 0,50, 0,20, 0,00) festgelegt und seine Eigenschaft **MaterialSpecularPower** auf 16.

> [!NOTE]
> Die Eigenschaft **MaterialSpecular** bestimmt das erkennbare Finish des Oberflächenmaterials. Eine hochglänzende Oberfläche wie Glas oder Kunststoff besitzt tendenziell eine helle weiß glänzende Farbe. Eine Oberfläche aus Metall hat tendenziell eine glänzende Farbe ähnlich ihrer diffusen Farbe. Eine Oberfläche mit Satin-Finish hat tendenziell eine dunkelgrau glänzende Farbe.
>
> Die Eigenschaft **MaterialSpecularPower** bestimmt, wie intensiv die Glanzlichter sind. Hohe Glanzkräfte simulieren stumpfere, lokalisiertere Glanzlichter. Sehr niedrige Glanzkräfte simulieren intensive, auffällige Glanzlichter, die die Farbe der ganzen Oberfläche übersättigen und verbergen können.

![Phong-Beleuchtung in einem Modell](../designers/media/digit-lighting-model.png)

Weitere Informationen zum Anwenden eines Shaders auf ein 3D-Modell finden Sie unter [Vorgehensweise: Anwenden eines Shaders auf ein 3D-Modell](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Weitere Informationen

- [Vorgehensweise: Anwenden eines Shaders auf ein 3D-Modell](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Vorgehensweise: Exportieren eines Shaders](../designers/how-to-export-a-shader.md)
- [Vorgehensweise: Erstellen eines einfachen Lambert-Shaders](../designers/how-to-create-a-basic-lambert-shader.md)
- [Shader-Designer](../designers/shader-designer.md)
- [Shader-Designer-Knoten](../designers/shader-designer-nodes.md)
