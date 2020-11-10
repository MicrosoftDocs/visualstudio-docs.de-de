---
title: 'Vorgehensweise: Erstellen eines einfachen 3D-Modells'
description: Erfahren Sie, wie der Modell-Editor zum Erstellen eines einfachen 3D-Modells verwendet wird, einschließlich des Hinzufügens von Objekten zu einer Szene, des Übertragen einer Auswahl und anderer Aktivitäten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: a0d97966-2df8-449b-a8cf-5a19684dc773
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 924b990e1626842778c0b3577ddb25a53a4eb910
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2020
ms.locfileid: "93134602"
---
# <a name="how-to-create-a-basic-3d-model"></a>Vorgehensweise: Erstellen eines einfachen 3D-Modells

In diesem Artikel wird gezeigt, wie der Modell-Editor zum Erstellen eines einfachen 3D-Modells verwendet wird. Folgende Aktivitäten werden beschrieben:

- Hinzufügen von Objekten in einer Szene

- Flächen und Kanten auswählen

- Übertragen der Auswahl

- Verwenden der Tools **Unterteilen von Flächen** und **Extrudieren von Flächen**

- Verwenden des Befehls **Triangulieren**

## <a name="create-a-basic-3d-model"></a>Erstellen eines einfachen 3D-Modells
Sie können den Modell-Editor zum Erstellen und Ändern von 3D-Modellen und -Szenen für Ihre Spiele und Apps verwenden. Die folgenden Schritte zeigen, wie Sie den Modell-Editor verwenden, um ein vereinfachtes 3D-Modell eines Hauses zu erstellen. Ein vereinfachtes Modell kann als Ersatz für die endgültigen Grafikobjekte verwendet werden, die noch erstellt werden. Es dient als ein Gitter zur Kollisionserkennung oder als ein Modell mit niedrigen Details, das verwendet wird, wenn ein Objekt, das es darstellt, zu weit weg ist, um von detaillierterem Rendering zu profitieren.

Das Modell sollte dann etwa so aussehen:

![Das abgeschlossene Modell des vereinfachten Hauses](../designers/media/gfx_model_demo_house_final.png)

Bevor Sie beginnen, stellen Sie sicher, dass das Fenster **Eigenschaften** und die **Toolbox** angezeigt werden.

### <a name="to-create-a-simplified-3d-model-of-a-house"></a>Erstellen eines vereinfachten 3D-Modells eines Hauses

1. Erstellen Sie ein 3D-Modell, mit dem Sie arbeiten können. Weitere Informationen zum Hinzufügen eines Modells zu Ihren Projekten finden Sie im Abschnitt „Erste Schritte“ unter [Modell-Editor](../designers/model-editor.md).

2. Fügen Sie einen Würfel in die Szene ein. Wählen Sie im Fenster **Toolbox** unter **Formen****Würfel** aus und verschieben Sie ihn auf die Entwurfsoberfläche.

3. Wechseln Sie zur Flächenauswahl. Klicken Sie auf der Symbolleiste des Modell-Editors auf **Fläche auswählen**.

4. Unterteilen Sie die Oberseite des Würfels. Klicken Sie im Flächenauswahlmodus den Würfel einmal an, um ihn auswählen zu können. Klicken Sie anschließend auf die Oberfläche des Würfels, um die Anfangsfläche auszuwählen. Klicken Sie auf der Symbolleiste des Modell-Editors auf **Fläche unterteilen**. Dadurch werden neue Schnittpunkte auf der Oberfläche des Würfels hinzugefügt, die ihn in vier gleichgroße Teile aufteilen.

    ![Die Oberseite des Würfels wurde unterteilt](../designers/media/gfx_model_demo_house_subdiv.png)

5. Extrudieren Sie zwei angrenzende Seiten des Würfels, z.B. die Vorderseite und die rechte Seite. Klicken Sie im Flächenauswahlmodus den Würfel einmal an, um ihn zu aktivieren, und klicken Sie anschließend auf eine Seite des Würfels. Halten Sie **STRG** gedrückt, klicken Sie auf eine andere Seite des Würfels, die an der zuerst ausgewählten Seite angrenzt, und klicken anschließend auf der Symbolleiste des Editors auf **Extrude face** (Fläche extrudieren).

    ![Die Seiten des Würfels wurden extrudiert](../designers/media/gfx_model_demo_house_extrude.png)

6. Erweitern Sie eine der Extrusionen. Wählen Sie eine der Flächen aus, die sie gerade extrudiert haben, und klicken in der Symbolleiste des Modell-Editors anschließend auf das Tool **Verschieben**. Bewegen Sie den Verschiebungsmanipulator in die gleiche Richtung wie die Extrusion.

    ![Eine Seite des Würfels wurde noch weiter extrudiert.](../designers/media/gfx_model_demo_house_extend.png)

7. Triangulieren Sie das Modell. Klicken Sie auf der Symbolleiste des Modell-Editors auf **Erweitert** > **Extras** > **Triangulieren**.

8. Erstellen Sie das Dach des Hauses. Wechseln Sie zum Kantenauswahlmodus, indem Sie auf der Symbolleiste des Modell-Editors auf **Kante auswählen** klicken. Klicken Sie anschließend auf den Würfel, um ihn zu aktivieren. Halten Sie **STRG** gedrückt, während Sie die Kanten auswählen, die hier gezeigt werden:

    ![Die Kanten, die die Spitze des Dachs bilden sollen](../designers/media/gfx_model_demo_house_edges.png)

    Nachdem die Kanten ausgewählt sind klicken sie auf der Symbolleiste des Modell-Editors auf **Verschieben** und bewegen Sie den Verschiebungsmanipulator nach oben, um das Dach des Hauses zu erstellen.

   Das Modell des vereinfachten Hauses ist abgeschlossen. Hier ist noch einmal das fertige Modell, bei dem eine flache Schattierung angewandt wurde.

   ![Das abgeschlossene Modell des vereinfachten Hauses](../designers/media/gfx_model_demo_house_final.png)

   Im nächsten Schritt können Sie einen Shader auf dieses 3D-Modell anwenden. Weitere Informationen finden Sie unter [Vorgehensweise: Anwenden eines Shaders auf ein 3D-Modell](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Weitere Informationen

- [Vorgehensweise: Modellieren eines 3D-Geländes](../designers/how-to-model-3-d-terrain.md)
- [Modell-Editor](../designers/model-editor.md)
- [Shader-Designer](../designers/shader-designer.md)
