---
title: Exportieren und Speichern von Code Maps
description: Erfahren Sie, wie Sie Code Maps als Teil eines Visual Studio-Projekts, als Bild oder als XPS-Datei speichern können.
ms.custom: SEO-VS-2020
ms.date: 05/16/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 324f8fe7ee34f469d31ad1ce6cf6bd25ab97f225
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899816"
---
# <a name="share-code-maps"></a>Freigeben von Code Maps

Code Maps können als Teil eines Visual Studio-Projekts, als Bild oder als XPS-Datei gespeichert werden.

## <a name="share-a-code-map-with-other-visual-studio-users"></a>Freigeben einer Code Map für andere Visual Studio-Benutzer

Verwenden Sie das Menü **Datei** , um die Code Map zu speichern.

- oder -

Um die Zuordnung als Teil eines bestimmten Projekts zu speichern, wählen Sie auf der Karten Symbolleiste die Option  >  **Move \<CodeMapName> . dgml in** freigeben aus, und wählen Sie dann das Projekt aus, in dem Sie die Zuordnung speichern möchten.

![Verschieben einer Zuordnung in ein anderes Projekt](../modeling/media/codemapsmovemapmenu.png)

Visual Studio speichert die Karte als *dgml* -Datei, die Sie für andere Benutzer von Visual Studio Enterprise und Visual Studio Professional freigeben können.

> [!NOTE]
> Vergewissern Sie sich, dass alle Gruppen erweitert sind, alle ausgeblendeten Knoten und gruppenübergreifenden Links angezeigt werden, und rufen Sie alle gelöschten Knoten ab, die andere in der Code Map sehen sollen, bevor Sie eine Code Map für Benutzer von Visual Studio Professional freigeben. Andernfalls können andere Benutzer diese Elemente nicht sehen.
>
> Wenn Sie eine Code Map speichern, die sich in einem Modellierungsprojekt befindet oder von einem Modellierungsprojekt an einen anderen Speicherort kopiert wurde, tritt möglicherweise der folgende Fehler auf:
>
> " *Dateiname* kann nicht außerhalb des Projektverzeichnisses gespeichert werden. Verknüpfte Elemente werden nicht unterstützt."
>
> Der Fehler wird zwar von Visual Studio angezeigt, die Version wird aber dennoch gespeichert. Erstellen Sie die Code Map außerhalb des Modellierungsprojekts, um diesen Fehler zu vermeiden. Sie können es anschließend am gewünschten Speicherort speichern. Es wird nicht funktionieren, die Datei einfach an eine andere Position in der Projektmappe zu kopieren und dort zu speichern.

## <a name="export-a-code-map-as-an-image"></a>Exportieren eines Code Map als Image

Wenn Sie eine Code Map als Image exportieren, können Sie Sie in andere Anwendungen kopieren, z. b. Microsoft Word oder PowerPoint.

1. Wählen Sie auf der Code Map Symbol Leiste die Option  >  **e-Mail als Bild** freigeben oder **Bild kopieren** aus.

2. Fügen Sie das Bild in eine andere Anwendung ein.

## <a name="export-the-map-as-an-xps-file"></a>Exportieren der Zuordnung als XPS-Datei

Wenn Sie eine Code Map als XPS-Datei exportieren, können Sie Sie in XML-oder XAML-Viewern wie Internet Explorer sehen.

1. Wählen Sie auf der Code Map Symbol Leiste  >  **e-Mail als Portables XPS** freigeben oder **als Portables XPS speichern** aus.

2. Durchsuchen Sie nach dem Ort, an dem die Datei gespeichert werden soll.

3. Benennen Sie die Code Map. Stellen Sie sicher, dass das Feld **Dateityp** auf **XPS-Dateien ( \* . Xps)** festgelegt ist. Wählen Sie **Speichern** aus.

## <a name="see-also"></a>Weitere Informationen

- [Zuordnen von Abhängigkeiten zu Code Maps](../modeling/map-dependencies-across-your-solutions.md)
