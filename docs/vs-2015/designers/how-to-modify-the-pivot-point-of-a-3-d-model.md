---
title: 'Vorgehensweise: Ändern des Pivotpunkts eines 3D-Modells | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: c20b4ec8-29f5-4ca5-bc39-d4548ca6f573
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: baeae2af825edc6a0032445288de7311b1ab1ae1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664403"
---
# <a name="how-to-modify-the-pivot-point-of-a-3-d-model"></a>Gewusst wie: Ändern des Pivotpunkts eines 3D-Modells
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Dokument wird gezeigt, wie der Modell-Editor zum Ändern des *Pivotpunkts* eines 3D-Modells verwendet wird. Der Pivotpunkt ist der Punkt im Raum, der das mathematische Zentrum des Objektes für Rotation und Skalierung definiert.

 In diesem Dokument wird die folgende Aktivität veranschaulicht:

- Ändern der Pivotpunkt eines Objekts

## <a name="modifying-the-pivot-point-of-a-3-d-model"></a>Ändern der Pivotpunkt eines 3D-Modells
 Sie können den Ursprung eines 3D-Modells durch Ändern seines Pivotpunkts neu definieren.

 Stellen Sie sicher, dass das Fenster **Eigenschaften** und die **Toolbox** angezeigt werden.

#### <a name="to-modify-the-pivot-point-of-a-3-d-model"></a>So ändern Sie den Pivotpunkt eines 3D-Modells

1. Beginnen Sie mit einem vorhandenen 3D-Modell, z. b. dem, das in Gewusst [wie: Erstellen eines 3D-Basismodells](../designers/how-to-create-a-basic-3-d-model.md)beschrieben wird.

2. Gehen Sie in den Pivot-Modus. Klicken Sie zum Aktivieren des Pivot-Modus auf der Symbolleiste **Model-Editor-Modus** auf **Pivot-Modus**. Es erscheint ein Feld um die Schaltfläche **Pivot-Modus**, der angibt, dass der Modell-Editor sich nun im Pivot-Modus befindet. Vorgänge wie die Verschiebung beeinflussen im Pivot-Modus den Pivotpunkt des Objektes anstatt der Struktur des Objektes im Raum.

3. Ändern Sie den Pivotpunkt des Objekts. Klicken Sie im Modus **Auswählen** auf das Objekt und anschließend auf der Symbolleiste des **Modell-Viewers** auf das Tool **Verschieben**. Ein Feld, das den Pivotpunkt darstellt, wird auf der Entwurfsoberfläche angezeigt. Verschieben Sie das Feld, um den Pivotpunkt des Objekts zu ändern.

    Durch das Verschieben des Felds können Sie den Pivopunkt in alle drei Dimensionen verschieben. Zum Verschieben des Pivotpunkts entlang einer Achse, verschieben Sie den Pfeil, der dieser Ache entspricht Das Feld und die Pfeile wechseln in eine gelbe Farbe, um die Achse anzugeben, die von der Verschiebung betroffen sind.

    Sie können auch den Pivotpunkt angeben, indem Sie die Eigenschaft **Pivot-Bewegung** im Fenster **Eigenschaften** verwenden.

   > [!TIP]
   > Sie können den Effekt des neuen Pivotpunkts durch Rotieren des Objekts betrachten. Verwenden Sie zum Drehen des Objekts das Tool **Drehen**, oder ändern Sie die Eigenschaft **Drehung**.

   Hier finden Sie ein Modell, dass einen geänderten Pivotpunkt hat:

   ![Modell eines Hauses mit einem geänderten Pivotpunkt](../designers/media/digit-modified-model.png "Digit-modified-Model")

## <a name="see-also"></a>Weitere Informationen
 Gewusst [wie: Erstellen eines einfachen 3D-Modell Modell-](../designers/how-to-create-a-basic-3-d-model.md) [Editors](../designers/model-editor.md)
