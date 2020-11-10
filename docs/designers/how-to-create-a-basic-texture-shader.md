---
title: 'Gewusst wie: Erstellen eines Basistextur-Shaders'
description: Erfahren Sie, wie Sie mit dem Shader-Designer und der Directed Graph Shader Language (DGSL) einen Ein-Textur-Shader erstellen, der die endgültige Farbe auf die RGB- und Alphawerte aus der Textur festlegt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 5af113fb-6415-4be0-8b23-10fddb10e80a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 93696dfe9fbf3b8db1d4be137ced6798b3a60aae
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2020
ms.locfileid: "93134497"
---
# <a name="how-to-create-a-basic-texture-shader"></a>Vorgehensweise: Erstellen eines Basistexturshaders

In diesem Artikel wird erläutert, wie der Shader-Designer und die Directed Graph Shader Language (DGSL) zum Erstellen eines Ein-Textur-Shaders verwendet wird. Dieser Shader legt die endgültige Farbe direkt auf die RGB- und Alphawerte fest, die von der Textur bezogen werden.

## <a name="create-a-basic-texture-shader"></a>Erstellen eines Basistexturshaders

Sie können einen grundlegenden, Ein-Textur-Shader implementieren, indem die Farb- und Alphawerte direkt in die endgültige Farbe geschrieben werden.

Bevor Sie beginnen, stellen Sie sicher, dass das Fenster **Eigenschaften** und die **Toolbox** angezeigt werden.

1. Erstellen Sie einen DGSL-Shader, mit dem Sie arbeiten können. Wie Sie dem Projekt einen DGSL-Shader hinzufügen, erfahren Sie im Abschnitt „Erste Schritte“ unter [Shader-Designer](../designers/shader-designer.md)

2. Löschen Sie den Knoten **Punktfarbe**. Wählen Sie im Modus **Auswählen** den Knoten **Farbpunkt** aus, und klicken Sie anschließend in der Menüleiste auf **Bearbeiten** > **Löschen**. Dadurch wird Platz für den Knoten geschaffen, der im nächsten Schritt hinzugefügt wird.

3. Fügen Sie einen Knoten **Textursample** in das Diagramm ein. Klicken Sie in der **Toolbox** unter **Textur** auf **Textursample** , und verschieben Sie es auf die Entwurfsoberfläche.

4. Fügen Sie einen Knoten **Texturkoordinate** in das Diagramm ein. Klicken Sie in der **Toolbox** unter **Textur** auf **Texturkoordinate** , und verschieben Sie es auf die Entwurfsoberfläche.

5. Wählen Sie eine Textur zum Anwenden aus. Klicken sie im Modus **Auswählen** auf den Knoten **Textursample** , und geben Sie im Fenster **Eigenschaften** die zu verwendende Textur an, indem Sie die Eigenschaft **Dateiname** verwenden.

6. Machen Sie die Textur öffentlich verfügbar. Klicken Sie auf den Knoten **Textursample** , und stellen Sie im Fenster **Eigenschaften** die Eigenschaft **Zugriff** auf **Öffentlich**. Sie können nun die Textur von einem anderen Tool wie dem **Modell-Editor** festlegen.

7. Verbinden Sie die Texturkoordinaten mit dem Textursample. Verschieben Sie im Modus **Auswählen** das Terminal **Ausgabe** des Knotens **Texturkoordinate** auf das Terminal **UV** des Knotens **Textursample**. Diese Verbindung prüft die Textur an den angegebenen Koordinaten.

8. Verbinden Sie das Textursample mit der endgültigen Farbe. Verschieben Sie das Terminal **RGB** des Knotens **Textursample** auf das Terminal **RGB** des Knotens **Endgültige Farbe**. Verschieben Sie anschließend das Terminal **Alpha** des Knotens **Textursample** auf das Terminal **Alpha** des Knotens **Endgültige Farbe**.

In der folgenden Abbildung wird das fertige Shader-Diagramm sowie eine Vorschau eines Würfels gezeigt, auf dem der Shader angewandt wurde.

> [!NOTE]
> In dieser Abbildung wird eine Ebene als Vorschauform verwendet, und eine Textur wurde angegeben, um den Effekt des Shaders besser zu veranschaulichen.

![Shader-Diagramm und eine Vorschau seiner Effekte](../designers/media/digit-texture-effect.png)

Bestimmte Formen sorgen vielleicht für bessere Vorschauen für einige Shader. Weitere Informationen zur Verwendung der Vorschau von Shadern im Shader-Designer finden Sie unter [Shader-Designer](../designers/shader-designer.md).

## <a name="see-also"></a>Weitere Informationen

- [Vorgehensweise: Anwenden eines Shaders auf ein 3D-Modell](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Image Editor](../designers/image-editor.md)
- [Shader-Designer](../designers/shader-designer.md)
- [Shader-Designer-Knoten](../designers/shader-designer-nodes.md)
