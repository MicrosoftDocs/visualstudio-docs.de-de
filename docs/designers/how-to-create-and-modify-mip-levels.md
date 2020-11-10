---
title: 'Gewusst wie: Erstellen und Ändern von MIP-Ebenen'
description: Erfahren Sie, wie Sie die Bildbearbeitung verwenden, um MIP-Ebenen für den Detailgrad des Texturraums zu generieren und zu ändern.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: f64d4369-2307-4175-a39a-2e45506f7fa1
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b97b57adb6fd87fa539e9dae7c37d6c5c8f2ddd6
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2020
ms.locfileid: "93134445"
---
# <a name="how-to-create-and-modify-mip-levels"></a>Vorgehensweise: Erstellen und Ändern von MIP-Ebenen
Dieses Dokument veranschaulicht, wie Sie die **Bildbearbeitung** verwenden, um *MIP-Ebenen* für den Detaillierungsgrad (LOD) des Texturraums zu generieren und zu ändern.

## <a name="generating-mip-levels"></a>Generieren von MIP-Ebenen
*Mipmapping* ist eine Technik, die verwendet wird, um Renderingvorgänge zu beschleunigen und Aliasingartefakte auf strukturierten Objekten zu reduzieren, indem mehrere Kopien einer Textur in unterschiedlichen Größen vorberechnet und gespeichert werden. Jede als MIP-Ebene bezeichnete Kopie hat die halbe Breite und halbe Höhe der vorherigen Kopie. Wenn eine Textur auf der Oberfläche eines Objekts gerendert wird, wird die MIP-Ebene, die am ehesten dem Bildraumbereich der strukturierten Oberfläche entspricht, automatisch ausgewählt. Das bedeutet, dass die Grafikhardware übergroße Texturen nicht filtern muss, um für eine konsistente visuelle Qualität zu sorgen. Die Arbeitsspeicherkosten zum Speichern der MIP-Ebenen sind zwar ca. 33 Prozent höher als für die Originaltextur allein, die Leistungssteigerung und die bessere Bildqualität rechtfertigen diese Kosten jedoch.

#### <a name="to-generate-mip-levels"></a>So generieren Sie MIP-Ebenen

1. Erstellen Sie wie unter [Vorgehensweise: Erstellen einer Basistextur](../designers/how-to-create-a-basic-texture.md) beschrieben eine Basistextur. Um bestmögliche Ergebnisse zu erzielen, geben Sie eine Textur an, deren Breite und Höhe der Potenz 2 entsprechen, z. B. 256, 512, 1024 usw.

2. Generieren Sie die MIP-Ebenen. Klicken Sie auf der Symbolleiste des **Bildbearbeitungsmodus** auf **Erweitert** > **Extras** > **MIPS generieren**.

     Beachten Sie, dass die Schaltflächen **Zur nächsten MIP-Ebene wechseln** und **Zur vorherigen MIP-Ebene wechseln** jetzt auf der Symbolleiste **Bildbearbeitungsmodus** angezeigt werden. Wenn das Fenster **Eigenschaften** angezeigt wird, beachten Sie auch, dass die schreibgeschützten Eigenschaften **Mip-Ebene** und **Anzahl der Mip-Ebenen** nun in den Bildeigenschaften angezeigt werden.

## <a name="modifying-mip-levels"></a>Ändern von MIP-Ebenen
Um Spezialeffekte zu erzielen oder die Bildqualität auf bestimmten Detailebenen zu erhöhen, können Sie jede MIP-Ebene einzeln ändern. Beispielsweise können Sie einem strukturierten Objekt ein anderes Erscheinungsbild in einem bestimmten Abstand geben (größerer Abstand entspricht kleineren MIP-Ebenen). Oder Sie können sicherstellen, dass Texturen, die Text oder Symbole enthalten, sogar auf kleineren MIP-Ebenen lesbar bleiben.

#### <a name="to-modify-an-individual-mip-level"></a>So ändern Sie eine einzelne MIP-Ebene

1. Wählen Sie die MIP-Ebene aus, die Sie ändern möchten. Klicken Sie auf der Symbolleiste **Bildbearbeitungsmodus** auf die Schaltflächen **Zur nächsten MIP-Ebene wechseln** und **Zur vorherigen MIP-Ebene wechseln** , um zwischen den MIP-Ebenen zu navigieren.

2. Nachdem Sie die MIP-Ebene ausgewählt haben, die Sie ändern möchten, können Sie die Zeichenwerkzeuge verwenden, um sie zu ändern, ohne den Inhalt anderer MIP-Ebenen zu ändern. Die Zeichenwerkzeuge sind auf der Symbolleiste **Bildbearbeitung** verfügbar. Nachdem Sie ein Tool ausgewählt haben, können Sie seine Eigenschaften im Fenster **Eigenschaften** ändern. Informationen zu den Zeichentools und ihren Eigenschaften finden Sie unter [Bildbearbeitung](../designers/image-editor.md).

> [!NOTE]
> Wenn eine Änderung der Inhalte der einzelnen MIP-Ebenen (wie zum Erreichen bestimmter Effekte) nicht erforderlich ist, wird empfohlen, Mipmaps zur Buildzeit aus der Quelltextur zu generieren. Dies hilft, sicherzustellen, dass MIP-Ebenen synchron mit der Quelltextur bleiben, da Änderungen an einer MIP-Ebene nicht automatisch an andere Ebenen weitergegeben werden. Weitere Informationen zum Erstellen von Mipmaps zur Buildzeit finden Sie unter [Vorgehensweise: Erstellen einer Textur, die Mipmaps enthält](../designers/how-to-export-a-texture-that-contains-mipmaps.md).

## <a name="see-also"></a>Weitere Informationen

- [Vorgehensweise: Erstellen einer Basistextur](../designers/how-to-create-a-basic-texture.md)
