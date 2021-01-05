---
title: Layout für Visual Studio | Microsoft-Dokumentation
description: Erfahren Sie mehr über das Layout für Visual Studio-Dialogfelder, einschließlich nicht-Themen Dialogfeldern und neuen Dialogfeldern mit Design.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3e6c90831c39f0e378dd9060397c68592ec73384
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863662"
---
# <a name="layout-for-visual-studio"></a>Layout für Visual Studio
Die Mehrzahl der Visual Studio-Dialogfelder sind das [Layout des Hilfsprogramm-Dialog](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout)Felds, bei dem es sich um die Dialogfelder mit dem standardmäßigen [Windows-Desktop-Dialog](/windows/desktop/uxguide/win-dialog-box) Wenn Visual Studio zum Aktualisieren seiner Benutzeroberfläche wechselt, haben einige der spezifischere Dialoge einen neuen Entwurf, der Sie als Produkt definierende Oberfläche festlegt. Diese Design [Dialogfelder](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) haben eine Design Darstellung.

## <a name="utility-dialog-layout"></a><a name="BKMK_UtilityDialogLayout"></a> Layout des hilfsprogrammdialog

- Alle Steuerelemente innerhalb eines hilfsprogrammdialogfelds sollten oben/links beginnen und nach unten fließen.

- Zentrieren Sie niemals Steuerelemente in einem Dialogfeld, um einen großen Bereich auszufüllen.

- Verwenden Sie für den gesamten Dialog Text die Schriftart Umgebung. Wenn Sie eine visuelle Spezifikation schreiben, geben Sie die Umgebungs Schriftart an, anstatt eine bestimmte Schriftart und Größe auszuwählen. Siehe [die Umgebungs Schriftart](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

- Verwenden Sie konsistenten Steuerungs Abstände und Platzierung, um das Ziel der Qualität in der Hand zu haben.

- Dialogfelder können von einer größeren Anzahl von Steuerelementen, einer eindeutigen Gegenüberstellung von Steuerelementen oder beidem komplexer werden. In diesen komplexen Situationen sollten Sie ausreichenden Raum zwischen Steuerelement Gruppierungen zulassen, um dem Benutzer einen logischen Ablauf zum analysieren zu geben.

### <a name="utility-dialog-layout-examples"></a>Layoutbeispiele für das Hilfsprogramm
 Alle Dimensionen werden als Pixel ausgedrückt.

 ![Dialogfeldabstände für Beschriftungen über Steuerelementen](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801-a_UtilitySpacingAbove")

 **Abbildung 08,01-a: Abstands Richtlinien für hilfsprogrammdialoge mit Bezeichnungen oberhalb der Steuerelemente**

 ![Dialogfeldabstände für Beschriftungen links neben Steuerelementen](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801-b_UtilitySpacingLeft")

 **Abbildung 08,01-b: Abstands Richtlinien für hilfsprogrammdialoge mit Bezeichnungen Links von Steuerelementen**

### <a name="layout-details"></a>Layoutdetails

#### <a name="margins"></a>Ränder

- Alle Dialogfelder sollten über einen 12-Pixel-Rahmen um alle Kanten verfügen.

- Die Ränder innerhalb eines Gruppen Rahmens müssen zwischen dem Rand des Frames 9 Pixel betragen.

- Die Ränder innerhalb eines Registerkarten-Steuer Elements sollten 6 Pixel vom Rand des Registerkarten-Steuer Elements sein.

#### <a name="command-buttons"></a>Befehls Schaltflächen

- Befehls Schaltflächen wirken sich auf den Dialog Frame aus, nicht auf den Inhalt. Sie sollten in der unteren rechten Ecke abgelegt werden und sollten über ausreichend Variablen Bereich verfügen, um die Schaltflächen eindeutig voneinander zu trennen.

- Wenn im Dialogfeld horizontale Schaltflächen verwendet werden, ist die Alternative Befehls Schaltflächen Konfiguration ein vertikaler Stapel rechts oben. Siehe [innere Befehls](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) Schaltflächen weiter unten.

- Der Leerraum auf der linken Seite der Befehls Schaltflächen (unten links/Mitte des Dialog Felds) wird als Teil des "Bands" der Dialogfeld-Vorgangs Steuerelemente betrachtet. Der einzige Schritt, der in diesen Bereich eingreifen sollte, ist ein Hilfelink, der für die gesamte Aufgabe oder das gesamte Dialogfeld relevant ist.

- Befehls Schaltflächen sollten 75 x 23 Pixel betragen.

- Befehls Schaltflächen sollten 6 Pixel voneinander getrennt sein.

  ![Grundlegende Ausrichtung von Steuerelementen](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801-c_ButtonAlign")

  **Abbildung 08,01-c: grundlegende Schaltflächen Ausrichtung**

#### <a name="labels"></a>Bezeichnungen

- Alle Bezeichnungen linksbündig ausrichten.

- Bei Bezeichnungen, die sich oberhalb eines Steuer Elements befinden, sollten Sie sich genau mit dem darunter liegenden Steuerelement ausrichten, und der untere Teil der Bezeichnung sollte 5 Pixel oberhalb des oberen Rands des anderen Steuer Elements (z. b. ein Kombinations Feld) sein.

- Bei Bezeichnungen, die sich Links von Steuerelementen befinden, beträgt die Mindestbreite zwischen der Bezeichnung und dem Eingabe Steuerelement 10 Pixel. Eine implizite zweite Spalte sollte eingerichtet werden, um die Textfelder, Kombinations Felder oder andere Steuerelemente auszurichten.

- Bezeichnungen sind Satz Buchstaben, gefolgt von einem Doppelpunkt. Siehe [Textstil](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).

#### <a name="distance-between-controls"></a>Abstand zwischen Steuerelementen
 Stapel Steuerelemente in angemessener Weise. Es gibt keine absolute Richtlinie für den Abstand zwischen gestapelten Steuerelementen. Die enge zwischen den Steuerelementen kann zwischen den Dialogfeldern leicht abweichen. Der empfohlene Abstand beträgt 20 Pixel für vertikale Steuerelement-/bezeichnungspaare und 9 Pixel für horizontale Steuer-/bezeichnungspaare. Der minimale Steuerelement Abstand für horizontale Paare beträgt 6 Pixel.

 ![Empfohlener Abstand zwischen Steuerelementen](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801-d_ControlDistance")

 **Abbildung 08,01-d: Empfehlungen für den Abstand zwischen Steuerelementen**

#### <a name="control-indentation"></a>Steuerelement Einzug
 Wenn Steuerelemente geschachtelt sind, richten Sie innere Steuerelemente horizontal am linken Rand des Steuer Elements oberhalb ein, normalerweise die Bezeichnung.

 ![Ausrichtung von verschachtelten Steuerelementen](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801-e_ControlAlign")

 **Abbildung 08,01-e: Ausrichtung des eingebundenen Steuer Elements**

#### <a name="control-width"></a>Steuerelement Breite
 Die Breite eines Textfelds oder anderer ähnlicher Steuerelemente sollte nicht länger als die durchschnittliche Eingabe für das Feld sein. Das durchschnittliche englische Wort beträgt fünf Zeichen. Beispielsweise sollte ein Textfeld, das einen langen Pfadnamen erfordert, so lang sein, wie das horizontale Layout zulässt, während eine Dropdown Liste für Platt Form Namen nur eine Länge haben sollte, die den längsten Eintrag zulässt.

#### <a name="helper-text"></a>Hilfetext

- Ein Dialogfeld kann Hilfstext anzeigen, der weitere Informationen zum Zweck des Dialog Felds enthält. Dies befindet sich normalerweise im oberen Bereich und kann 1-2 Sätze sein.

- Die Zeilenlänge sollte eine bequeme Breite sein, damit ein Benutzer Sie analysieren und lesen können. Ein mittleres Dialogfeld darf nicht mehr als 550 Pixel breit sein.

#### <a name="interior-command-buttons"></a><a name="BKMK_InteriorCommandButtons"></a> Innere Befehls Schaltflächen
 In komplexeren Dialogfeldern kann ein internes Steuerelement über eigene verknüpfte Schaltflächen verfügen, die sich darauf auswirken können, wo sich die Commit-Schaltflächen des Dialog Felds befinden.

- Verwenden Sie eine vertikale Ausrichtung (Spalte) von inneren Schaltflächen, wenn **OK** / **Abbrechen** in der unteren rechten Ecke horizontal ausgerichtet ist.

- Verwenden Sie eine horizontale Ausrichtung (Zeile) von inneren Schaltflächen, wenn **OK** / **Abbrechen** in der oberen rechten Ecke vertikal ausgerichtet ist. Diese Situation ist weniger häufig.

- Die innere Schaltflächen Größe sollte auf die Standard Schaltflächen Größe von 75 x 23 Pixel abzielen, sofern möglich, die Größe der Schaltflächen **OK** / **Abbrechen** entspricht. Wenn die Schaltfläche durch eine Schaltflächen Bezeichnung die Standard Schaltflächen Größe überschreitet, sollten die anderen Schaltflächen in diesem Satz an der größeren Größe ausgerichtet werden.

  ![Horizontale Schaltflächen "OK" und "Abbrechen"](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801-f_HorizOKCan")

  **Abbildung 08,01-f: vertikale innere Schaltflächen mit horizontaler OK/Abbruch**

  ![Vertikale Schaltflächen "OK" und "Abbrechen"](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801-g_VertOKCan")

  **Abbildung 08,01-g: horizontale innere Schaltflächen mit vertikaler OK/Abbruch**

#### <a name="browse-button"></a>[Durchsuchen...] gedrückt
 **[Durchsuchen...]** Schaltflächen, die einem Textfeld folgen, müssen "Browse..." vollständig, einschließlich der Auslassungs Punkte. Wenn der Leerraum leer ist oder mehrere **[Browse...]** -Schaltflächen auf dem Bildschirm vorhanden sind, kann die Schaltfläche auf das Auslassungs Zeichen reduziert werden.

## <a name="themed-dialog-layout"></a><a name="BKMK_ThemedDialogLayout"></a> Layout des Design Layouts
 Themen Dialogfelder in Visual Studio haben ein helleres Aussehen und bieten mehr Leerraum. Typografie bietet mehr Akzente und Interesse, bietet mehr öffnenden Zeilenabstand und eine Variation von Schriftgrößen und Gewichtungen. Nach Möglichkeit wurden Chrome-und Titelleisten reduziert oder entfernt. Das Layout dieser Dialogfelder sollte diesem grundlegenden Muster folgen:

1. Der Hintergrund des Dialog Felds ist weiß.

2. Es gibt einen 1-Pixel-Regel Rahmen in einem grauen Mittelwert.

3. Der Dialog Titel befindet sich nicht mehr in einer Titelleiste, sondern bietet visuelle Interessen und Akzente in einer größeren Punktgröße. (Weitere Informationen finden Sie im Abschnitt Schriftart size im [Textstil](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).)

4. Bezeichnungen, die mit zusätzlichem Text gekoppelt sind, z. b. eine Beschreibung, sollten **Umgebungs Schriftart und Fett** formatiert sein.

5. Innere Spalten werden durch eine 1-Pixel-Regel in hellgrau voneinander getrennt.

6. Standard Verknüpfungen haben keinen Unterstrich. Der Hover-und der gedrückte Status haben eine Farbänderung Plus unterstrich.

7. Commit-Schaltflächen (wie **OK** / **Abbrechen**) befinden sich in der unteren rechten Ecke.

### <a name="themed-dialog-layout-examples"></a>Beispiele für layoutdialogfelder
 ![Dialogfeldlayout mit angewendetem Design](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801-h_ThemedDialog")

 **Abbildung 08,01-h: Dialogfeld "Thema"**

 ![Dialogfeldabmessungen mit angewendetem Design](../../extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801-i_ThemedDialogDimensions")

 **Abbildung 08,01-i: Dialogfeld-Dimensionen**

 ![Dialogfeldschriftarten mit angewendetem Design](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801-j_ThemedDialogFonts")

 **Abbildung 08,01-j: Dialogfeld "Schriftarten"**

 ![Dialogfeldfarben mit angewendetem Design](../../extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801-k_ThemedDialogColors")

 **Abbildung 08,01-k: Dialog-Farben mit Design**

## <a name="see-also"></a>Weitere Informationen
- [Anwendungsmuster für Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)
- [Steuerelemente (Windows)](/windows/desktop/uxguide/controls)
- [Dialog Felder (Fenster)](/windows/desktop/uxguide/win-dialog-box)
