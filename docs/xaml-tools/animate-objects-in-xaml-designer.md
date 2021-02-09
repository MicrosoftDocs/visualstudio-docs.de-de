---
title: Animieren von Objekten im XAML-Designer
titleSuffix: Blend for Visual Studio
description: Erfahren Sie, wie Sie eine Animation in Blend für Visual Studio erstellen, indem Sie ein Storyboard mit einer Zeitachse und Keyframes verwenden, um ein Objekt in XAML-Designer zu animieren.
ms.custom: SEO-VS-2020
ms.date: 07/31/2019
ms.topic: how-to
ms.assetid: fb88fa26-e835-47f5-9771-2f279441c83c
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: 162ed3ddb7e8f71a14c9dd8415500cc845316e82
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889251"
---
# <a name="animate-objects-in-xaml-designer"></a>Animieren von Objekten im XAML-Designer

Mit Blend für Visual Studio können Sie ganz einfach kurze Animationen erstellen, die Objekte verschieben oder sie ein-und ausblenden.

Zum Erstellen einer Animation benötigen Sie ein *Storyboard*. Ein Storyboard enthält eine oder mehrere *Zeitachsen*. Legen Sie auf einer Zeitachse *Keyframes* fest, um Änderungen an den Eigenschaften zu markieren. Beim Ausführen der Animation interpoliert Blend für Visual Studio dann die Eigenschaftsänderungen im festgelegten Zeitraum. Das Ergebnis ist ein reibungsloser Übergang. Sie können jede Eigenschaft animieren, die zu einem Objekt gehört, sogar nicht visuelle Eigenschaften.

Die folgenden Abbildungen zeigen ein Storyboard mit dem Namen **Storyboard1**. Die Zeitachse enthält Keyframes, die die x- und y-Position eines Rechtecks markieren. Wenn diese Animation ausgeführt wird, wird das Rechteck nahtlos von einer Position zu einer anderen verschoben.

![Storyboard für Animation in Blend für Visual Studio](media/storyboard-timeline.png)

## <a name="create-an-animation"></a>Erstellen einer Animation

1. Um ein Storyboard zu erstellen, wählen Sie die Schaltfläche **Storyboardoptionen** im Fenster **Objekte und Zeitachse** und dann **Neu** aus.

   ![Hinzufügen eines Storyboards in Blend für Visual Studio](media/new-storyboard.png)

2. Geben Sie im Dialogfeld **Storyboardressource erstellen** einen Namen für das Storyboard ein.

3. Fügen Sie in der Designansicht im Bereich **Objekte** ein Rechteck unten links auf der Seite hinzu.

   ![Rechteck im Bereich „Objekte“ im XAML-Designer](media/add-rectangle.PNG)

4. Bewegen Sie im Fenster **Objekte und Zeitachse** den gelben Zeitzeiger auf **3** Sekunden.

   ![Zeitindikator in der Zeitachse](media/timeline-indicator.PNG)

5. Ziehen Sie das Rechteck in der Designansicht der Seite auf die rechte Seite der Seite.

6. Drücken Sie **Wiedergeben**, um zu sehen, wie sich das Rechteck von der linken zur rechten Seite der Seite bewegt.

Experimentieren Sie mit anderen Änderungen am Rechteck zu unterschiedlichen Zeitpunkten. Beispielsweise können Sie im Eigenschaftenfenster die Füllfarbe ändern oder die Ausrichtung umkehren.

## <a name="see-also"></a>Weitere Informationen

- [Erstellen einer Benutzeroberfläche mit Blend für Visual Studio](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md)
