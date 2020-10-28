---
title: Übersicht über den XAML-Designer
description: Erfahren Sie mehr über die Benutzeroberfläche und die Features des XAML-Designer in Blend für Visual Studio, das eine visuelle Oberfläche bereitstellt, die Sie beim Entwerfen von XAML-basierten Apps unterstützt.
ms.custom: SEO-VS-2020
ms.date: 03/03/2020
ms.topic: conceptual
f1_keywords:
- VS.XamlDesigner
- VS.DevicePanel
- VS.XamlEditor
- VS.DocumentOutline
- Blend.Start.Dev12
ms.devlang: CSharp
ms.assetid: c54969a7-d75a-4a35-9b37-af7a596a7c24
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 73e7fb0b3216baa960a1b69302fe43161e311399
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796783"
---
# <a name="create-a-ui-by-using-xaml-designer"></a>Erstellen einer Benutzeroberfläche mit dem XAML-Designer

Der XAML-Designer in Visual Studio und Blend für Visual Studio bietet eine visuelle Oberfläche, die Sie beim Entwerfen von XAML-basierten apps wie WPF und UWP unterstützt. Sie können Benutzeroberflächen für Ihre Apps erstellen, indem Sie Steuerelemente aus dem Fenster Toolbox (Fenster „Objekte“ in Blend für Visual Studio) ziehen und Eigenschaften im Eigenschaftenfenster festlegen. Sie können XAML-Code auch direkt in der XAML-Ansicht bearbeiten.

Fortgeschrittene Benutzer können den [XAML-Designer](https://github.com/microsoft/xaml-designer-extensibility/blob/master/documents/xaml-designer-extensibility-migration.md) auch anpassen.

> [!NOTE]
> Xamarin. Forms unterstützt keinen XAML-Designer. Wenn Sie xamarin. Forms-XAML-Benutzeroberflächen anzeigen und bearbeiten möchten, während die app ausgeführt wird, verwenden Sie XAML Hot Neuladen für xamarin. Forms. Weitere Informationen finden Sie auf der Seite [XAML-Hot-Upload für xamarin. Forms (Vorschau)](/xamarin/xamarin-forms/xaml/hot-reload/) .

## <a name="xaml-designer-workspace"></a>XAML-Designer-Arbeitsbereich

Der Arbeitsbereich im XAML-Designer besteht aus mehreren visuellen Schnittstellenelementen. Dazu gehören die *Zeichenfläche* (die visuelle Designoberfläche), der XAML-Editor, das Fenster „Dokumentgliederung“ (Fenster „Objekte und Zeitachse“ in Blend for Visual Studio) und das Eigenschaftenfenster. Um den XAML-Designer zu öffnen, klicken Sie mit der rechten Maustaste auf eine XAML-Datei im **Projektmappen-Explorer** und wählen Sie **Ansicht-Designer** aus.

Der XAML-Designer stellt eine XAML-Ansicht und eine synchronisierte Entwurfsansicht des gerenderten XAML-Markups Ihrer App bereit. Mit einer XAML-Datei, die in Visual Studio oder Blend für Visual Studio geöffnet ist, können Sie zwischen Designansicht und XAML-Ansicht wechseln, indem Sie die Registerkarten **Entwurf** und **XAML** verwenden. Sie können die Schaltfläche **Bereiche austauschen**![Schaltfläche „Bereiche austauschen“ im XAML-Designer](media/swap-panes.PNG) verwenden, um festzulegen, welches Fenster im Vordergrund angezeigt wird: entweder die Zeichenfläche oder der XAML-Editor.

### <a name="design-view"></a>Entwurfsansicht

In der Designansicht ist das Fenster, welches die Zeichenfläche enthält, das aktive Fenster, und Sie können es als primäre Arbeitsoberfläche verwenden. Sie können damit eine Seite in Ihrer App visuell gestalten, indem Sie Elemente hinzufügen, zeichnen oder ändern. Weitere Informationen finden Sie unter [Arbeiten mit Elementen im XAML-Designer](../xaml-tools/working-with-elements-in-xaml-designer.md). Diese Abbildung zeigt die Zeichenfläche in der Entwurfsansicht.

![Entwurfsansicht XAML-Designer](media/xaml-artboard.png)

Diese Funktionen sind auf der Zeichenfläche verfügbar:

**Ausrichtungslinien**

Ausrichtungs Linien sind *Ausrichtungs Grenzen* , die als rot gestrichelte Linien angezeigt werden, um anzuzeigen, wann die Ränder von Steuerelementen ausgerichtet sind oder wenn Text Basis Linien ausgerichtet werden. Ausrichtungsgrenzen werden nur angezeigt, wenn **Andocken an Ausrichtungslinien** aktiviert ist.

**Rasterschienen**

Rasterschienen werden verwendet, um Zeilen und Spalten in einem [Rasterbereich](xref:Windows.UI.Xaml.Controls.Grid) zu verwalten. Sie können Zeilen und Spalten erstellen und löschen, und Sie können jeweils ihre relative Breite und Höhe anpassen. Die vertikale Rasterschiene, die auf der linken Seite der Zeichenfläche angezeigt wird, wird für Zeilen verwendet, und die horizontale Linie, die oben angezeigt wird, wird für Spalten verwendet.

**Rasterfunktionsindikatoren**

Ein Rasteradorner wird als Dreieck angezeigt, an das eine vertikale oder horizontale Linie auf der Rasterschiene angefügt ist. Wenn Sie einen Rasteradorner ziehen, werden die Breiten und Höhen von benachbarten Spalten oder Zeilen aktualisiert, während Sie die Maus verschieben.

Rasteradorner werden verwendet, um die Breite und Höhe der Zeilen und Spalten eines Rasters zu steuern. Sie können eine neue Spalte oder Zeile hinzufügen, indem Sie in die Rasterschienen klicken. Wenn Sie eine neue Zeilen- oder Spaltenlinie für einen Rasterbereich hinzufügen, der mindestens zwei Spalten oder Zeilen enthält, wird außerhalb der Schiene eine Minisymbolleiste angezeigt, in der Sie die Breite und die Höhe genau festlegen können. In der Minisymbolleiste können Sie die Größenanpassungsoptionen für Zeilen und Spalten des Rasters festlegen.

![Rasteradorner in XAML-Designer](media/grid-adorner.png)

**Handles zum Ändern der Größe**

Handles zur Größenänderung werden auf ausgewählten Steuerelementen angezeigt und ermöglichen Ihnen das Ändern der Größe des Steuerelements. Wenn Sie die Größe eines Steuerelements ändern, werden normalerweise die Werte für die Höhe und Breite angezeigt, um Ihnen bei der Größenfestlegung des Steuerelements behilflich zu sein. Weitere Informationen zum Bearbeiten von Steuerelementen in der **Designansicht** finden Sie unter [Arbeiten mit Elementen im XAML-Designer](../xaml-tools/working-with-elements-in-xaml-designer.md).

**Ränder**

Der Begriff "Rand" bezeichnet den fest definierten Abstand zwischen der Kante eines Steuerelements und der Kante seines Containers. Sie können die Ränder eines Steuer Elements festlegen, indem Sie die [Rand](xref:Windows.UI.Xaml.FrameworkElement.Margin) -Eigenschaften unter **Layout** im **Eigenschaften** Fenster verwenden.

**Randfunktionsindikatoren**

Sie können Randadorner verwenden, um die Ränder eines Elements relativ zu dessen Layoutcontainer zu ändern. Wenn ein Randfunktionsindikator geöffnet ist, wird kein Rand festgelegt, und der Randfunktionsindikator zeigt eine unterbrochene Kette an. Wenn der Rand nicht festgelegt wird, verbleiben Elemente an Ort und Stelle, wenn die Größe des Layoutcontainers zur Laufzeit geändert wird. Wenn ein Randadorner geschlossen ist, zeigt ein Randadorner eine nicht unterbrochene Kette an, und Elemente verschieben sich mit dem Rand, während der Layoutcontainer zur Laufzeit angepasst wird (der Rand bleibt unverändert).

**Elementhandles**

Sie können ein Element ändern, indem Sie die Elementhandles verwenden, die auf der Zeichenfläche angezeigt werden, wenn Sie den Mauszeiger über die Ecken des blauen Felds, welches ein Element umgibt, bewegen. Mit diesen Handles können Sie das Element drehen, dessen Größe ändern, es spiegeln, verschieben oder ihm einen Eckradius hinzufügen. Das Symbol für das Elementhandle variiert je nach Funktion und ändert sich je nach der genauen Position des Zeigers. Wenn Sie die Elementhandles nicht sehen, stellen Sie sicher, dass das Element ausgewählt ist.

In der **Entwurfsansicht** sind zusätzliche Zeichenflächenbefehle im unteren linken Fensterbereich verfügbar, wie hier gezeigt wird:

![Entwurfsansicht-Befehle](media/xaml-design-view-controls.png)

Diese Befehle sind auf dieser Symbolleiste verfügbar:

**Zoom**

Zoom ermöglicht es Ihnen, die Entwurfsoberfläche zu skalieren. Sie können mit dem Zoom die Größe von 12,5 % bis 800 % ändern oder Optionen wie **Auswahl anpassen** und **Alle anpassen** auswählen.

**Ausrichtungsgitter anzeigen/ausblenden**

Zeigt das Ausrichtungsgitter an, das die Rasterlinien anzeigt, oder blendet es aus. Rasterlinien werden verwendet, wenn Sie entweder **Andocken an Rasterlinien** oder **Andocken an Ausrichtungslinien** aktivieren.

**Andocken an Rasterlinien ein/aus**

Wenn das Ausrichten **an Gitternetz Linien** aktiviert ist, wird ein Element tendenziell an den nächstgelegenen horizontalen und vertikalen Gitternetz Linien ausgerichtet, wenn Sie es auf die Zeichenfläche ziehen.

**Hintergrund der Zeichenfläche umschalten**

Schaltet zwischen einem hellen und einem dunklen Hintergrund um.

**Andocken an Ausrichtungslinien ein/aus**

Mit Ausrichtungslinien können Sie Steuerelemente relativ zu anderen Steuerelementen ausrichten. Wenn **Andocken an Ausrichtungslinien** aktiviert ist, wenn Sie ein Steuerelement relativ zu anderen Steuerelementen ziehen, werden Ausrichtungsgrenzen angezeigt, wenn die Kanten und der Text von einigen Steuerelementen horizontal oder vertikal ausgerichtet werden. Eine Ausrichtungsgrenze wird als rot-gestrichelte Linie angezeigt.

**Projektcode deaktivieren**

Deaktiviert den [Projektcode](debugging-or-disabling-project-code-in-xaml-designer.md), z.B. benutzerdefinierte Steuerelemente und Wertkonverter, und lädt den Designer neu.

### <a name="xaml-view"></a>XAML-Ansicht

In der **XAML** -Ansicht ist das Fenster mit dem XAML-Editor das aktive Fenster, und der XAML-Editor ist Ihr primäres Entwicklungstool. Die Extensible Application Markup Language (XAML) stellt ein deklaratives, auf XML basierendes Vokabular bereit, mit dem die Benutzeroberfläche einer Anwendung festgelegt werden kann. Die XAML-Ansicht enthält IntelliSense und automatische Formatierung, Syntaxhervorhebung und Tagnavigation. In der folgenden Abbildung wird die XAML-Ansicht mit einem geöffneten IntelliSense-Menü dargestellt:

![XAML-Ansicht](media/xaml-editor.png)

## <a name="document-outline-window"></a>Fenster Dokumentgliederung

Das Fenster „Dokumentgliederung“ in Visual Studio ist ähnelt dem Fenster [Objekte und Zeitachsen](creating-a-ui-by-using-blend-for-visual-studio.md#objects-and-timeline-window) in Blend für Visual Studio. Mit der Dokumentgliederung können Sie die folgenden Aufgaben ausführen:

- Anzeigen der hierarchischen Struktur aller Elemente auf der Zeichenfläche.

- Wählen Sie Elemente aus, damit Sie Sie ändern können. Beispielsweise können Sie Sie in der Hierarchie verschieben oder deren Eigenschaften im Eigenschaftenfenster festlegen. Weitere Informationen finden Sie unter [Arbeiten mit Elementen im XAML-Designer](../xaml-tools/working-with-elements-in-xaml-designer.md).

- Erstellen und Ändern von Vorlagen für Elemente, welche Steuerelemente sind.

- [Erstellen von Animationen](animate-objects-in-xaml-designer.md) (nur Blend für Visual Studio).

Um das Dokument Gliederungs Fenster in Visual Studio anzuzeigen, wählen Sie in **View** der Menüleiste die Option  >  **Weitere Windows** -  >  **Dokument** Gliederung anzeigen aus.
Um das Fenster Objekte und Zeitachsen in Blend für Visual Studio anzuzeigen, wählen Sie in der Menüleiste Dokument Gliederung **anzeigen** aus  >  **Document Outline** .

![Screenshot: Fenster „Dokumentgliederung“ in Visual Studio](media/document-outline-window.png)

Die Hauptansicht im Fenster „Dokumentgliederung/Objekte und Zeitachse“ zeigt die Hierarchie eines Dokuments in einer Baumstruktur an. Sie können den hierarchischen Charakter der Dokumentgliederung verwenden, um das Dokument mit unterschiedlicher Detailliertheit zu überprüfen und um Elemente einzeln oder in Gruppen zu sperren und auszublenden. Die folgenden Optionen sind im Fenster Dokument Gliederung/Objekte und Zeitachsen verfügbar:

**Ein-/ausblenden**

Zeigt Zeichenflächenelemente an oder blendet sie aus. Wird als Auges dargestellt, wenn es eingeblendet wird. Sie können auch **STRG** + **h** drücken, um ein Element auszublenden, und **UMSCHALT** + **STRG** + **h** , um es anzuzeigen.

**Sperren/Entsperren**

Sperrt oder entsperrt Zeichenflächenelemente. Gesperrte Elemente können nicht geändert werden. Es wird ein Vorhängeschloss angezeigt, wenn ein Element gesperrt ist. Sie können auch **STRG** + **l** drücken, um ein Element zu sperren, und **UMSCHALT** Taste + **STRG** + **l** , um es zu entsperren.

**Bereich zurücksetzen auf**

Über Option oben im Fenster „Dokumentgliederung/Objekte und Zeitachse“, die das Symbol eines Nach-Oben-Pfeils zeigt, gelangen Sie an den vorherigen Bereich zurück. Die Vergrößerung des Bereichs ist nur möglich, wenn Sie sich im Bereich eines Stils oder einer Vorlage befinden.

## <a name="properties-window"></a>Eigenschaftenfenster

Im Fenster **Eigenschaften** können Sie Eigenschaftswerte für Steuerelemente festlegen. Das Fenster sieht so aus:

![Eigenschaftenfenster](media/xaml-designer-properties-window.png)

Am oberen Rand des Fensters " **Eigenschaften** " befinden sich verschiedene Optionen:

- Sie können den Namen des aktuell ausgewählten Elements im Feld **Name** ändern.
- In der linken oberen Ecke gibt es ein Symbol, welches das aktuell ausgewählte Element darstellt.
- Um die Eigenschaften nach Kategorie oder alphabetisch zu sortieren, klicken Sie auf **Kategorie** , **Name** oder auf **Quelle** in der Liste **Anordnen nach** .
- Um die Liste der Ereignisse für ein Steuerelement zu sehen, klicken Sie auf die Schaltfläche **Ereignisse** . Es wird ein Blitz angezeigt.
- Wenn Sie nach einer Eigenschaft suchen möchten, beginnen Sie mit der Eingabe des Namens der Eigenschaft im Suchfeld. Im Fenster **Eigenschaften** werden die Eigenschaften angezeigt, die mit Ihrer Suche übereinstimmen, während Sie Ihre Eingabe vornehmen.

Einige Eigenschaften ermöglichen es Ihnen, erweiterte Eigenschaften festzulegen, indem Sie eine Nach-Unten-Schaltfläche auswählen.

Rechts von jedem Eigenschaftenwert befindet sich ein *Eigenschaftenmarker* , der als Feldsymbol angezeigt wird. Die Anzeige des Eigenschaftenmarkers weist darauf hin, ob es eine Datenbindung oder eine Ressource gibt, die auf die Eigenschaft angewendet wurde. Beispielsweise zeigt ein weißes Feldsymbol einen Standardwert an, ein schwarzes Feldsymbol zeigt in der Regel an, dass eine lokale Ressource angewendet wurde, und ein oranges Feld zeigt in der Regel an, dass eine Datenbindung angewendet wurde. Wenn Sie auf den Eigenschaftenmarker klicken, können Sie zur Definition eines Stils navigieren, den Datenbindungs-Generator öffnen oder die Ressourcenauswahl öffnen.

Weitere Informationen zur Verwendung von Eigenschaften und zur Behandlung von Ereignissen finden Sie unter [Einführung in Steuerelemente und Muster](/windows/uwp/design/controls-and-patterns/controls-and-events-intro).

## <a name="see-also"></a>Weitere Informationen:

- [Arbeiten mit Elementen im XAML-Designer](../xaml-tools/working-with-elements-in-xaml-designer.md)
- [So erstellen Sie eine Ressource und wenden Sie an](../xaml-tools/how-to-create-and-apply-a-resource.md)
- [Exemplarische Vorgehensweise: Bindung an Daten im XAML-Designer](../xaml-tools/walkthrough-binding-to-data-in-xaml-designer.md)
