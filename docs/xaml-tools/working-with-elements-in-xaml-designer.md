---
title: Arbeiten mit Elementen im XAML-Designer
description: Erfahren Sie, wie Sie mit Elementen in der XAML-Designer in Visual Studio oder Blend für Visual Studio arbeiten.
ms.custom: SEO-VS-2020
ms.date: 05/14/2018
ms.topic: conceptual
ms.assetid: a29690bf-f212-4ac6-a77a-adc53d14102e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 1af793ec7ecd741de1fc1b4bb1cb48dbf2ef32f3
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047126"
---
# <a name="work-with-elements-in-xaml-designer"></a>Arbeiten mit Elementen im XAML-Designer

Sie können Ihrer App in XAML im Code oder unter Verwendung des XAML-Designers Elemente hinzufügen (Steuerelemente, Layouts und Formen). Dieses Thema beschreibt, wie Elemente im XAML-Designer in Visual Studio oder in Blend für Visual Studio verwendet werden.

## <a name="add-an-element-to-a-layout"></a>Hinzufügen eines Elements zu einem Layout

*Layout* ist der Prozess der Größenanpassung und Positionierung von Elementen in einer Benutzeroberfläche. Um visuelle Elemente zu positionieren, müssen Sie sie in einen [Bereich](xref:Windows.UI.Xaml.Controls.Panel) eines Layouts einfügen. Ein `Panel` verfügt über eine untergeordnete Eigenschaft, die eine Auflistung von [FrameworkElement](xref:Windows.UI.Xaml.FrameworkElement)-Typen ist. Sie können verschiedene untergeordnete `Panel`-Elemente wie z.B. [Canvas](xref:Windows.UI.Xaml.Controls.Canvas), [StackPanel](xref:Windows.UI.Xaml.Controls.StackPanel) und [Grid](xref:Windows.UI.Xaml.Controls.Grid) verwenden, um sie als Layoutcontainer zu nutzen und auf einer Seite zu positionieren und anzuordnen.

Standardmäßig wird ein `Grid`-Bereich als Layoutcontainer der obersten Ebene innerhalb einer Seite oder eines Formulars verwendet. Sie können Layoutbereiche, Steuerelemente oder andere Elemente innerhalb der obersten Ebene des Seitenlayouts hinzufügen.

Wenn Sie in XAML-Designer einem Layout ein Element hinzufügen möchten, müssen Sie einen der folgenden Schritte ausführen:

- Doppelklicken Sie auf ein Element in der **Toolbox** (oder wählen Sie ein Element in der Toolbox aus, und drücken **Sie die Eingabe** Taste).

- Ziehen Sie ein Element aus der **Toolbox** auf die Zeichenfläche.

- Klicken Sie in der **Toolbox** auf eines der Zeichenwerkzeuge (z.B. [Ellipse](xref:Windows.UI.Xaml.Shapes.Ellipse) oder [Rechteck](xref:Windows.UI.Xaml.Shapes.Rectangle)), und zeichnen Sie dann ein Element im aktiven Bereich.

## <a name="change-the-layering-order-of-elements"></a>Ändern der Ebenenreihenfolge von Elementen

Gibt es zwei Elemente auf der Zeichenfläche im XAML-Designer, wird ein Element vor dem anderen in der Ebenenreihenfolge angezeigt. Am unteren Rand der Liste der Elemente befindet sich im Fenster "Dokument Gliederung" das vorderste Element (mit Ausnahme von, wenn die **ZIndex** -Eigenschaft für ein Element festgelegt ist). Wenn Sie ein Element in eine Seite, ein Formular oder einen Layoutcontainer einfügen, wird das Element automatisch vor anderen Elementen im aktiven Containerelement platziert. Um die Reihenfolge von Elementen zu ändern, können Sie die **Reihenfolge** -Befehle verwenden oder die Elemente in der Objektstruktur im Dokumentgliederungsfenster verschieben.

Wenn Sie Ebenenreihenfolge ändern möchten, müssen Sie einen der folgenden Schritte ausführen:

- Ziehen Sie im Fenster **Dokumentgliederung** die Elemente nach oben oder unten, um die gewünschte Ebenenreihenfolge zu erstellen.

- Klicken Sie mit der rechten Maustaste auf das Element im Dokumentgliederungsfenster oder auf der Zeichenfläche, für das Sie die Ebenenreihenfolge ändern möchten, zeigen Sie auf **Reihenfolge** , und klicken Sie dann auf eine der folgenden Optionen:

  - **In den Vordergrund** , um das Element in der Reihenfolge ganz nach vorne zu verschieben.

  - **Eine Ebene nach vorne** , um das Objekt eine Ebene in der Reihenfolge nach vorne zu holen.

  - **Eine Ebene nach hinten** , um das Objekt eine Ebene in der Reihenfolge nach hinten zu verschieben.

  - **In den Hintergrund** , um das Element hinter alle anderen Elemente in der Reihenfolge zu verschieben.

- Ändern Sie die **ZIndex** -Eigenschaft im **Layout** -Abschnitt im Eigenschaftenfenster. Bei überlappenden Elementen hat die **ZIndex** -Eigenschaft Vorrang vor der Reihenfolge der Elemente, die im Dokumentgliederungsfenster angezeigt werden. Ein Element mit einem höheren **ZIndex** -Wert wird im Vordergrund angezeigt, wenn sich Elemente überlappen.

## <a name="change-the-alignment-of-an-element"></a>Ändern der Ausrichtung eines Objekts

Sie können Elemente auf der Zeichenfläche mit Menübefehlen oder durch Ziehen von Elementen an Ausrichtungslinien ausrichten.

Eine Ausrichtungslinie ist ein visueller Hinweis, mit dem *Sie ein Element* relativ zu anderen Elementen in der APP ausrichten können.

So richten Sie zwei oder mehr Elemente mithilfe der Menübefehle aus:

1. Wählen Sie die Elemente aus, welche Sie ausrichten möchten. Sie können mehr als ein Element auswählen, indem Sie die **STRG** -Taste gedrückt halten, während Sie die Elemente auswählen.

2. Wählen Sie eine der folgenden Eigenschaften unter **Horizontale Ausrichtung** im **Layout** -Abschnitt des Eigenschaftenfensters aus: **Links** , **Mitte** , **Rechts** oder **Strecken** .

3. Wählen Sie eine der folgenden Eigenschaften unter **Vertikale Ausrichtung** im **Layout** -Abschnitt des Eigenschaftenfensters aus: **Oben** , **Mitte** , **Unten** oder **Strecken** .

Wenn Sie zwei oder mehr Elemente in XAML-Designer mithilfe von Ausrichtungslinien ausrichten möchten, ziehen Sie in einem Layout mit mindestens zwei Elementen eines der Elemente (oder ändern Sie die Größe), sodass der Rand auf ein anderes Element ausgerichtet ist.

Wenn die Kanten ausgerichtet sind, wird eine *Ausrichtungsgrenze* angezeigt, um die Ausrichtung anzugeben. Die Ausrichtungsgrenze ist eine rot-gestrichelte Linie. Ausrichtungsgrenzen werden nur angezeigt, wenn **Andocken an Ausrichtungslinien** aktiviert ist. Eine Abbildung der Zeichenfläche, die eine Ausrichtungsgrenze zeigt, finden Sie unter [Erstellen einer Benutzeroberfläche mit dem XAML-Designer](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

## <a name="change-an-elements-margins"></a>Ändern der Ränder eines Elements

Die Ränder im XAML-Designer bestimmen den Umfang des Leerraums, der sich um einem Element auf der Zeichenfläche befindet. Ränder geben beispielsweise den Raum zwischen den äußeren Kanten eines Elements und den Grenzen eines `Grid`-Bereichs an, welcher das Element enthält. Ränder geben auch den vorhandenen Raum zwischen Elementen an, die in einem `StackPanel` enthalten sind.

So ändern Sie die Ränder eines Elements im Eigenschaftenfenster:

1. Wählen Sie das Element aus, dessen Ränder Sie ändern möchten.

2. Ändern Sie im Eigenschaftenfenster unter **Layout** den Wert (in Pixel oder in geräteunabhängigen Einheiten von etwa 1/96 Zoll) für die gewünschten **Ränder** -Eigenschaften: **Oben** , **Links** , **Rechts** oder **Unten** .

Wenn Sie auf der Zeichenfläche die Ränder eines Elements relativ zu dessen Layoutcontainer ändern möchten, klicken Sie auf die *Rand-Adorner* , die um das Element angezeigt werden, wenn es ausgewählt ist und sich in einem Container befindet. Eine Abbildung der Rand-Adorner finden Sie unter [Erstellen einer Benutzeroberfläche mit dem XAML-Designer](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

Wenn ein Randfunktionsindikator geöffnet ist, sei es vertikal oder horizontal, dann ist besagter Rand noch nicht festgelegt. Wenn ein Randfunktionsindikator geschlossen ist, dann ist besagter Rand festgelegt.

Wenn Sie ein Rand-Adorner öffnen und der gegenüberliegende Rand nicht festgelegt ist, wird der gegenüberliegende Rand auf den richtigen Wert gemäß der Position des Elements auf der Zeichenfläche festgelegt. Für gegenüberliegende Ränder wie die Ränder **Links** und **Rechts** wird stets mindestens eine Eigenschaft festgelegt.

> [!IMPORTANT]
> Elemente, die innerhalb irgendwelcher Layoutcontainers platziert werden, wie beispielsweise ein [Canvas](xref:Windows.UI.Xaml.Controls.Canvas), haben keine Randfunktionsindikatoren. Elemente, die innerhalb eines [StackPanel](xref:Windows.UI.Xaml.Controls.StackPanel) platziert werden, haben Funktionsindikatoren für entweder die linken und rechten Ränder oder für die oberen und unteren Ränder, abhängig von der Ausrichtung des `StackPanel`.

## <a name="group-and-ungroup-elements"></a>Gruppieren von Elementen und Gruppierung aufheben

Durch die Gruppierung von zwei oder mehr Elementen im XAML-Designer wird ein neuer Layoutcontainer erstellt und die betreffenden Elemente innerhalb dieses Containers platziert. Durch die gemeinsame Platzierung von zwei oder mehr Elementen in einem Layoutcontainer wird Ihnen ermöglicht, die Gruppe einfach auszuwählen, zu bewegen und zu transformieren, so als ob die Elemente innerhalb dieser Gruppe ein Element wären. Die Gruppierung ist auch zur Bestimmung von Elementen nützlich, die in irgend einer Weise im Verhältnis zueinander stehen, wie die Schaltflächen, die ein Navigationselement ergeben. Wenn Sie die Gruppierung für Elemente aufheben, löschen Sie einfach den Layoutcontainer, welcher die Elemente enthielt.

So gruppieren Sie Elemente in einem neuen Layoutcontainer:

1. Wählen Sie die Elemente aus, welche Sie gruppieren möchten. (Um mehrere Elemente auszuwählen, halten Sie die **STRG-TASTE** gedrückt, während Sie auf die Elemente klicken.)

2. Klicken Sie mit der rechten Maustaste auf die ausgewählten Elemente, zeigen Sie auf **Gruppieren in** , und klicken Sie dann auf den Typ des Layoutcontainers, in dem die Gruppe platziert werden soll.

    > [!TIP]
    > Wenn Sie [Viewbox](xref:Windows.UI.Xaml.Controls.Viewbox), [Border](xref:Windows.UI.Xaml.Controls.Border) oder [ScrollViewer](xref:Windows.UI.Xaml.Controls.ScrollViewer) auswählen, um Ihre Objekte zu gruppieren, werden die Objekte in einem neuen [Rasterpanel](xref:Windows.UI.Xaml.Controls.Grid) in [Viewbox](xref:Windows.UI.Xaml.Controls.Viewbox), [Border](xref:Windows.UI.Xaml.Controls.Border) oder [ScrollViewer](xref:Windows.UI.Xaml.Controls.ScrollViewer) platziert. Wenn Sie die Gruppierung von Elementen in einem dieser Layoutcontainer aufheben, werden nur [Viewbox](xref:Windows.UI.Xaml.Controls.Viewbox), [Border](xref:Windows.UI.Xaml.Controls.Border) oder [ScrollViewer](xref:Windows.UI.Xaml.Controls.ScrollViewer) gelöscht, und der Bereich [Raster](xref:Windows.UI.Xaml.Controls.Grid) wird beibehalten. Löschen Sie den `Grid`-Bereich, heben Sie die Gruppierung der Elemente erneut auf.

Wenn Sie die Gruppierung von Elementen aufheben möchten, klicken Sie mit der rechten Maustaste auf die Gruppierung, die Sie aufheben möchten, und klicken Sie dann auf **Gruppierung aufheben** . Sie können Elemente auch durch einen Rechtsklick auf ausgewählte Elemente im Dokumentgliederungsfenster und durch Klicken auf **Gruppieren in** oder **Gruppierung aufheben** gruppieren bzw. die Gruppierung aufheben.

## <a name="reset-the-element-layout"></a>Zurücksetzen des Elementlayouts

Sie können Standardwerte für bestimmte Layouteigenschaften eines Elements wiederherstellen, indem Sie die Befehlen zum Zurücksetzen von Layouts verwenden. Mit diesem Befehl können Sie den Rand, die Ausrichtung, die Breite, Höhe sowie Größe eines Elements zurücksetzen, entweder für jedes Element einzeln oder zusammen.

Um das Element Layout zurückzusetzen, klicken Sie mit der rechten Maustaste auf das Element im Dokument Gliederungs Fenster oder auf der Zeichenfläche, und wählen Sie dann **Layout**  >  **Zurücksetzen** *propertyName* aus, wobei *propertyName* die Eigenschaft ist, die Sie zurücksetzen möchten (oder wählen Sie **Layout**  >  **Zurücksetzen alle** , um alle Layouteigenschaften für das Element zurückzusetzen)

## <a name="see-also"></a>Weitere Informationen

- [Erstellen einer Benutzeroberfläche mit dem XAML-Designer](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
