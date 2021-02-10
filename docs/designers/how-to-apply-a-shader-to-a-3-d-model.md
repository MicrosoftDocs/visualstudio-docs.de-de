---
title: 'Vorgehensweise: Anwenden eines Shaders auf ein 3D-Modell'
description: Erfahren Sie, wie der Modell-Editor verwendet wird, um einen Directed Graph Shader Language-Shader (DGSL) auf ein 3D-Modell anzuwenden, um es visuell ansprechend zu gestalten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: a3877bd6-abd8-4a9d-842c-6848b6c2f335
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bdaf4b86bfc773df678c03875a9ec260cd72084f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917080"
---
# <a name="how-to-apply-a-shader-to-a-3d-model"></a>Vorgehensweise: Anwenden eines Shaders auf ein 3D-Modell

In diesem Artikel wird erläutert, wie der Modell-Editor verwendet wird, um einen Directed Graph Shader Language-Shader (DGSL) auf ein 3D-Modell anzuwenden.

## <a name="apply-a-shader-to-a-3d-model"></a>Anwenden eines Shaders auf ein 3D-Modell

Sie können einen Shadereffekt auf ein 3D-Modell anwenden, um es visuell ansprechender zu gestalten.

Bevor Sie beginnen, stellen Sie sicher, dass das Fenster **Eigenschaften** angezeigt wird.

1. Beginnen Sie mit einer 3D-Szene, die mindestens ein Modell enthält. Wenn keine geeignete 3D-Szene vorhanden ist, erstellen Sie eine wie unter [Vorgehensweise: Erstellen eines einfachen 3D-Modells](../designers/how-to-create-a-basic-3-d-model.md) beschrieben. Sie müssen ebenso über einen DGSL-Shader verfügen, den Sie auf das Modell anwenden können. Wenn Sie über keinen geeigneten Shader verfügen, erstellen Sie einen wie es in [Vorgehensweise: Erstellen eines einfachen Farbshaders](../designers/how-to-create-a-basic-color-shader.md), und stellen Sie sicher, dass er in einer Datei gespeichert wurde, bevor Sie fortfahren.

2. Wählen Sie im Modus **Auswählen** das Modell aus, auf das Sie den Shader anwenden möchten. Anschließend legen Sie im Fenster **Eigenschaften** unter der Eigenschaft **Dateiname** in der Eigenschaftsgruppe **Effekt** den DGSL-Shader fest, den Sie auf das Modell anwenden möchten.

Hier finden Sie ein Modell, bei dem der grundlegende Farbeffekt angewendet wurde:

![3D-Szene zur Darstellung eines einfachen Farbeffekts](../designers/media/digit-3d-model-effect.png)

Nachdem Sie einen Shader auf ein Modell angewendet haben, können Sie es im Shader-Designer durch Auswählen des Modells öffnen und anschließend die Schaltfläche „Ellipse“ (**...**) im Fenster **Eigenschaften** unter der Eigenschaft **(Erweitert)** der Eigenschaftsgruppe **Effekt** auswählen.

## <a name="see-also"></a>Weitere Informationen

- [Vorgehensweise: Erstellen eines einfachen 3D-Modells](../designers/how-to-create-a-basic-3-d-model.md)
- [Vorgehensweise: Erstellen eines einfachen Farbshaders](../designers/how-to-create-a-basic-color-shader.md)
- [Modell-Editor](../designers/model-editor.md)
- [Shader-Designer](../designers/shader-designer.md)
