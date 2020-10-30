---
title: Ändern des Stils von Objekten
titleSuffix: Blend for Visual Studio
description: Erfahren Sie, wie Sie den Stil von Objekten in Blend für Visual Studio ändern, indem Sie Pinsel anwenden, visuelle Zustände festlegen und wiederverwendbare Stile und Vorlagen anwenden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cfe54db27a16d95904412b5e1181d589ed2fcde8
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046786"
---
# <a name="modify-the-style-of-objects-in-blend-for-visual-studio"></a>Ändern des Stils von Objekten in Blend für Visual Studio

Die einfachste Möglichkeit zum Anpassen eines Objekts ist das Festlegen von Eigenschaften im Bereich **Eigenschaften** .

Wenn Sie Einstellungen oder Gruppen von Einstellungen erneut verwendet werden, erstellen Sie eine wieder verwendbare Ressource. Dies könnte ein *Stil* , eine *Vorlage* oder etwas so einfaches wie eine benutzerdefinierte Farbe sein. Sie können auch ein Steuerelement unterschiedlich basierend auf seine Status anzeigen. Beispielsweise wird eine Schaltfläche grün, wenn der Benutzer darauf klickt.

## <a name="brushes-modify-the-appearance-of-an-object"></a>Pinsel: Ändern des Erscheinungsbilds einen Objekts

Anwenden eines Pinsels bei einem Objekt, dessen Darstellung geändert werden soll.

### <a name="paint-a-repeating-image-or-pattern-on-an-object"></a>Zeichnen Sie ein sich wiederholendes Bild oder ein Muster für ein Objekt

Zeichnen Sie ein sich wiederholendes Bild oder ein Muster für ein Objekt mithilfe des *Kacheleffekts* .

Zum Erstellen eines Kacheleffekts erstellen Sie zunächst die Ressourcen *Bildpinsel* , *Zeichenpinsel* oder *visueller Pinsel* .

Erstellen Sie einen Bildpinsel mithilfe eines Bildes. Die folgenden Abbildungen zeigen den Bildpinsel, den Bildpinsel mit Kacheleffekt und den gekippten Bildpinsel.

![Bildpinsel](../designers/media/81f84f56-906d-456b-8288-d77da1e01e31.png) ![Bildpinsel gekachelt](../designers/media/d3782ca8-64da-47a4-a095-c6cdd0fa47a2.png) ![Bildpinsel gespiegelt](../designers/media/38ae3691-f3f1-4a1e-82ca-c7fa164bf56e.png)

Erstellen Sie einen Zeichenpinsel mithilfe eines Vektors, indem Sie z. B. einen Pfad oder eine Form zeichnen. Die folgenden Abbildungen zeigen den Bildpinsel, den Bildpinsel mit Kacheleffekt und den gekippten Bildpinsel.

![Zeichenpinsel](../designers/media/197666ac-ef57-4c5c-9779-669e991a00a5.png) ![Zeichenpinsel gekachelt](../designers/media/ba09cda3-4cee-40ba-b3d4-edc032158bdc.png) ![Zeichenpinsel gespiegelt](../designers/media/15bf6021-620c-4490-9eae-086153d3f14f.png)

Erstellen Sie einen visuellen Pinsel aus einem Steuerelement, z. B. einer Schaltfläche. Die folgenden Abbildungen zeigen den visuellen Pinsel und den visuellen Pinsel mit Kacheleffekt.

![Visueller Pinsel](../designers/media/fb6c90e0-153c-48fe-b563-e601beac6227.png) ![Visueller Pinsel gekachelt](../designers/media/e261b99f-7d8f-4d91-bc84-19c7beccc255.png)

## <a name="styles-and-templates-create-a-consistent-look-and-feel-across-controls"></a>Stile und Vorlagen: Erstellen eines konsistenten Aussehens und Verhaltens für Steuerelemente

Sie entwerfen die Darstellung und das Verhalten eines Steuerelements einmal und wenden diesen Entwurf auf andere Steuerelemente an, sodass Sie sie nicht einzeln verwalten müssen.

**Sollten Sie einen Stil verwenden?** Wenn Sie nur die Standardeigenschaften (beispielsweise die Farbe einer Schaltfläche) festlegen möchten, verwenden Sie einen *Stil* . Auch wenn Sie einen Stil angewendet haben, können Sie ein Steuerelement ändern.

**Sollten Sie eine Vorlage verwenden?** Wenn Sie die Struktur des Steuerelements ändern möchten, verwenden Sie eine *Vorlage* . Stellen Sie sich vor, Grafiken oder Logos in eine Schaltfläche zu konvertieren. Ein Steuerelement kann nicht geändert werden, nachdem Sie eine Vorlage angewendet haben.

### <a name="create-a-template-or-style"></a>Erstellen einer Vorlage oder eines Stils

Es gibt zwei Möglichkeiten, eine Vorlage zu erstellen. Sie können ein Objekt auf der Zeichenfläche in ein Steuerelement konvertieren oder Sie können Ihre Vorlage auf ein vorhandenes Steuerelement stützen.

Um jedes Objekt in eine Steuerelementvorlage zu konvertieren, wählen Sie das Objekt, und klicken Sie dann auf das Menü **Extras** und wählen Sie **In Steuerelement konvertieren** .

Wenn Sie Ihre Vorlage basierend auf einem vorhandenen Steuerelement erstellen möchten, wählen Sie ein Objekt auf der Zeichenfläche. Klicken Sie dann oben auf der Zeichenfläche auf die Breadcrumb-Schaltfläche, wählen Sie dann **Vorlage bearbeiten** und danach **Kopie bearbeiten** oder **Leere erstellen** .

![Menü „Vorlage bearbeiten“](../designers/media/5ebdb33f-aad2-4c10-a328-5e8b04c56a36.png)

Um einen Stil zu erstellen, wählen Sie das Objekt, und wählen Sie dann im Menü **Objekt****Stil bearbeiten** und dann **Eine Kopie bearbeiten** oder **Leer erstellen** .

- Wählen Sie **Kopie bearbeiten** , um mit dem Standardstil oder der Vorlage des Steuerelements zu beginnen.

- Wählen Sie **Leere erstellen** , um von Grund auf neu zu starten.

Die Option **aktuelle bearbeiten** wird nur angezeigt, wenn Sie einen Stil oder eine Vorlage bearbeiten, die Sie bereits erstellt haben. Sie erscheint nicht für ein Steuerelement, das immer noch eine Standardvorlage für das System verwendet.

Im Dialogfeld **Stilressource erstellen** können Sie entweder den Stil oder die Vorlage so benennen, dass sie später verwendet werden kann, oder Sie können den Stil oder die Vorlage auf alle Steuerelemente des Typs anwenden.

![Dialogfeld „Stilressource erstellen“](../designers/media/4818ee6a-ce60-4b79-91c8-3b1871829eea.png)

> [!NOTE]
> Sie können keine Stile oder Vorlagen für jede Art von Steuerelement erstellen. Wenn ein Steuerelement diese nicht unterstützt, wird die Breadcrumb-Schaltfläche nicht oberhalb der Zeichenfläche angezeigt.
> Um zum Bearbeitungsbereich des Hauptdokuments zurückzukehren, klicken Sie auf **Bereich zurücksetzen auf** ![Symbol für das Zurücksetzen des Bereichs](../designers/media/55844eb3-ed98-4f20-aa66-a6f5b23eeb2b.png).

### <a name="apply-a-style-or-template-to-a-control"></a>Anwenden von Stilen oder Vorlagen für ein Steuerelement

Klicken Sie mit der rechten Maustaste auf ein Objekt im Fenster [Objekte und Zeitachsen](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md#objects-and-timeline-window), und wählen Sie **Vorlage bearbeiten** und dann **Ressource anwenden** aus.

![Menü „Ressource anwenden“](../designers/media/dc12debc-7711-47d9-84ce-10322a384397.png)

### <a name="restore-the-default-style-or-template-of-a-control"></a>Wiederherstellen des Standardstils oder der Vorlage eines Steuerelements

Wählen Sie das Steuerelement aus, und suchen Sie im **Eigenschaftenfenster** ** die Eigenschaft **Stil** oder **Vorlage** . Klicken Sie auf **Erweiterte Optionen** und dann auf **Zurücksetzen** im Kontextmenü.

## <a name="visual-states"></a>Visueller Zustand

Mit visuellen Zuständen können Sie das Erscheinungsbild eines Steuerelements basierend auf dessen Status ändern. Steuerelemente können über unterschiedliche visuelle Darstellungen basierend auf Benutzerinteraktionen verfügen. Beispielsweise kann eine Schaltfläche grün werden, wenn ein Benutzer darauf klickt, oder Sie können eine Animation ausführen. Sie verkürzen oder verlängern die Zeit zwischen visuellen Zustände mithilfe von Übergängen.

![Mouseoverzustand](../designers/media/a95c671a-5639-40b9-83db-1e6b214330d5.png)

**Sehen Sie sich ein kurzes Video an:** ![Wiedergabeschaltfläche](../designers/media/bldadminconsoleinitialconfigicon.PNG) [Verwalten des Zustands der WPF-Steuerelemente](https://www.youtube.com/watch?v=m0PlkF5i6uw).

## <a name="resources-create-colors-styles-and-templates-and-reuse-them-later"></a>Ressourcen: Künftige erneute Verwendung von Farben, Stilen und Vorlagen

Sie können fast alles in Ihrem Projekt in eine Ressource konvertieren. Eine Ressource ist ein Objekt, das an unterschiedlichen Stellen in Ihrer Anwendung wiederverwendet werden kann. Sie können z. B. eine Farbe einmal erstellen, sie in eine Ressource konvertieren und dann diese Farbe auf mehrere Objekte anwenden. Um die Farbe aller dieser Objekte zu ändern, ändern Sie einfach die Farbressource.

![Schaltfläche „Farbe in Ressource konvertieren“](../designers/media/89203705-cf66-46e0-b153-52a23cd744f7.png) ![Dialogfeld „Farbressource erstellen“](../designers/media/6bff8b19-3cd5-41a0-bbf9-ff65532d5aae.png)

## <a name="see-also"></a>Weitere Informationen

- [Erstellen einer Benutzeroberfläche mit Blend für Visual Studio](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md)
