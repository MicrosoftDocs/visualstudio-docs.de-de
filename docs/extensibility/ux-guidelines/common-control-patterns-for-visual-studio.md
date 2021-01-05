---
title: Allgemeine Steuerelement Muster für Visual Studio | Microsoft-Dokumentation
description: Erfahren Sie, wie die allgemeinen Visual Studio-Steuerelemente den Windows-Desktop Interaktions Richtlinien und den besonderen Situationen folgen, die diese Richtlinien ergänzen.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3c1caccebf1dc14146bef214a4d33e1216243780
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715885"
---
# <a name="common-control-patterns-for-visual-studio"></a>Allgemeine Steuerelementmuster für Visual Studio
## <a name="common-controls"></a><a name="BKMK_CommonControls"></a> Allgemeine Steuerelemente

### <a name="overview"></a>Übersicht
Allgemeine Steuerelemente bilden die Mehrzahl der Benutzeroberfläche in Visual Studio. Die meisten allgemeinen Steuerelemente, die in der Visual Studio-Benutzeroberfläche verwendet werden, sollten den [Windows-Desktop Interaktions Richtlinien](/windows/desktop/uxguide/controls) Dieses Thema ist spezifisch für Visual Studio und behandelt spezielle Situationen oder Details, die diese Windows-Richtlinien ergänzen.

#### <a name="common-controls-in-this-topic"></a>Allgemeine Steuerelemente in diesem Thema

- [Scrollleisten](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)

- [Eingabefelder](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)

- [Kombinations Felder und Dropdown Listen](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)

- [Kontrollkästchen](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)

- [Optionsfelder](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)

- [Gruppieren von Frames](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)

- [Textsteuerelemente](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

- [Schaltflächen und Hyperlinks](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

- [Strukturansichten](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)

#### <a name="visual-style"></a>Visueller Stil
Beim Formatieren von Steuerelementen sollten Sie zunächst beachten, ob die Steuerelemente in der Benutzeroberfläche verwendet werden. Steuerelemente auf der Standardbenutzer Oberfläche sind eine Benutzeroberfläche ohne Design und müssen dem [normalen Windows-Desktop Stil](/windows/desktop/uxguide/controls)folgen, d. h., Sie werden nicht erneut mit Vorlagen versehen und sollten in Ihrer Standard Steuerelement Darstellung angezeigt werden.

- **Standard Dialogfelder (Hilfsprogramm):** nicht mit dem Design. Nicht neu erstellen. Standardeinstellungen für Steuerelement Stil verwenden.

- **Tool Fenster, Dokument-Editoren, Entwurfs Oberflächen und Themen Dialogfelder:** Verwenden Sie eine spezielle Darstellung des Designs mit dem Farb Dienst.

### <a name="scroll-bars"></a><a name="BKMK_Scrollbars"></a> Scrollleisten
 Bild Lauf leisten sollten [gängige Interaktionsmuster für Windows](/windows/desktop/Controls/about-scroll-bars) -Bild Lauf leisten befolgen, es sei denn, Sie werden mit Inhaltsinformationen ergänzt, wie im Code-Editor.

### <a name="input-fields"></a><a name="BKMK_InputFields"></a> Eingabefelder
 Befolgen Sie für ein typisches Interaktions Verhalten die [Windows-Desktop Richtlinien für Textfelder](/windows/desktop/uxguide/ctrl-text-boxes).

#### <a name="visual-style"></a>Visueller Stil

- Eingabefelder sollten nicht in hilfsprogrammdialogfeldern formatiert werden. Verwenden Sie die intrinsische grundlegende Formatvorlage für das Steuerelement.

- Themen Eingabefelder sollten nur in Themen Dialogfeldern und Tool Fenstern verwendet werden.

#### <a name="specialized-interactions"></a>Spezialisierte Interaktionen

- Schreibgeschützte Felder haben einen grauen (deaktivierten) Hintergrund, aber den Standard-Vordergrund (aktiv).

- Erforderliche Felder müssen **\<Required>** als Wasserzeichen enthalten sein. Sie sollten die Hintergrundfarbe nur in seltenen Fällen ändern.

- Fehlerüberprüfung: siehe [Benachrichtigungen und Fortschritt für Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md) .

- Eingabefelder sollten an den Inhalt angepasst werden, sodass Sie nicht an die Breite des Fensters angepasst werden, in dem Sie angezeigt werden, und die Länge eines Langenfelds, wie z. b. eines Pfades, beliebig anpassen. Die Länge ist möglicherweise ein Hinweis für den Benutzer von Einschränkungen, die angibt, wie viele Zeichen im Feld zulässig sind.

     ![Falsche Länge des Eingabe Felds: Es ist unwahrscheinlich, dass der Name so lang ist.](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707-01_IncorrectInputFieldControl")<br />Falsche Länge des Eingabe Felds: Es ist unwahrscheinlich, dass der Name so lang ist.

     ![Richtige Länge des Eingabe Felds: das Eingabefeld ist eine angemessene Breite für den erwarteten Inhalt.](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707-02_CorrectInputFieldControl")<br />Richtige Länge des Eingabe Felds: das Eingabefeld ist eine angemessene Breite für den erwarteten Inhalt.

### <a name="combo-boxes-and-drop-down-lists"></a><a name="BKMK_ComboBoxesAndDropDowns"></a> Kombinations Felder und Dropdown Listen
Befolgen Sie für ein typisches Interaktions Verhalten die [Windows-Desktop Richtlinien für Dropdown Listen und Kombinations Felder](/windows/desktop/uxguide/ctrl-drop).

#### <a name="visual-style"></a>Visueller Stil

- Ordnen Sie das Steuerelement in den hilfsprogrammdialogfeldern nicht neu an. Verwenden Sie die intrinsische grundlegende Formatvorlage für das Steuerelement.

- In der Benutzeroberfläche für die Benutzeroberfläche folgen Kombinations Felder und Dropdown Listen den Standarddesigns für die Steuerelemente.

#### <a name="layout"></a>Layout
Kombinations Felder und Dropdown Listen sollten entsprechend dem Inhalt angepasst werden, sodass Sie nicht an die Breite des Fensters angepasst werden können, in dem Sie angezeigt werden, und die Länge eines Langenfelds, wie z. b. eines Pfades, nicht willkürlich entsprechen.

![Falsch: die Dropdown-Breite ist zu lang für den Inhalt, der angezeigt wird.](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707-03_IncorrectDropDownLayout")<br />Falsch: die Dropdown-Breite ist zu lang für den Inhalt, der angezeigt wird.

![Richtig: das Dropdown-Format ist so groß, dass es das Übersetzungs Wachstum zulässt, jedoch nicht unnötig lange.](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707-04_CorrectDropDownLayout")<br />Richtig: das Dropdown-Format ist so groß, dass es das Übersetzungs Wachstum zulässt, jedoch nicht unnötig lange.

### <a name="check-boxes"></a><a name="BKMK_CheckBoxes"></a> Kontrollkästchen
Für ein typisches Interaktions Verhalten befolgen Sie die [Windows-Desktop Richtlinien für Kontrollkästchen](/windows/desktop/uxguide/ctrl-check-boxes).

#### <a name="visual-style"></a>Visueller Stil

- Ordnen Sie das Steuerelement in den hilfsprogrammdialogfeldern nicht neu an. Verwenden Sie die intrinsische grundlegende Formatvorlage für das Steuerelement.

- In der Benutzeroberfläche für die Benutzeroberfläche folgen Kontrollkästchen den Standarddesigns für die Steuerelemente.

#### <a name="specialized-interactions"></a>Spezialisierte Interaktionen

- Wenn Sie mit einem Kontrollkästchen interagieren, darf kein Dialogfeld angezeigt werden, oder Sie navigieren zu einem anderen Bereich.

- Richten Sie Kontrollkästchen mit der Baseline der ersten Textzeile aus.

     ![Falsch: das Kontrollkästchen ist auf den Text ausgerichtet.](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707-05_IncorrectCheckBoxAlign")<br />Falsch: das Kontrollkästchen ist auf den Text ausgerichtet.

     ![Richtig: das Kontrollkästchen ist an der ersten Textzeile ausgerichtet.](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707-06_CorrectCheckBoxAlign")<br />Richtig: das Kontrollkästchen ist an der ersten Textzeile ausgerichtet.

### <a name="radio-buttons"></a><a name="BKMK_RadioButtons"></a> Options Felder
Befolgen Sie für ein typisches Interaktions Verhalten die [Windows-Desktop Richtlinien für](/windows/desktop/uxguide/ctrl-radio-buttons)Options Felder.

#### <a name="visual-style"></a>Visueller Stil
Formatieren Sie in hilfsprogrammdialogfeldern keine Options Felder. Verwenden Sie die intrinsische grundlegende Formatvorlage für das Steuerelement.

#### <a name="specialized-interactions"></a>Spezialisierte Interaktionen
Es ist nicht erforderlich, einen Gruppen Rahmen zu verwenden, um Options Felder einzuschließen, es sei denn, Sie müssen die Gruppen Unterscheidung in einem engen Layout beibehalten.

### <a name="group-frames"></a><a name="BKMK_GroupFrames"></a> Gruppieren von Frames
Befolgen Sie für ein typisches Interaktions Verhalten die [Windows-Desktop Richtlinien für Gruppen Frames](/windows/desktop/uxguide/ctrl-group-boxes).

#### <a name="visual-style"></a>Visueller Stil
In hilfsprogrammdialogfeldern sollten Sie keine Gruppen Rahmen formatieren. Verwenden Sie die intrinsische grundlegende Formatvorlage für das Steuerelement.

#### <a name="layout"></a>Layout

- Es ist nicht erforderlich, einen Gruppen Rahmen zu verwenden, um Options Felder einzuschließen, es sei denn, Sie müssen die Gruppen Unterscheidung in einem engen Layout beibehalten.

- Verwenden Sie niemals einen Gruppen Rahmen für ein einzelnes Steuerelement.

- Es ist manchmal akzeptabel, anstelle eines Gruppen Frame Containers eine horizontale Regel zu verwenden.

## <a name="text-controls"></a><a name="BKMK_TextControls"></a> Text Steuerelemente

### <a name="static-text-fields"></a>Statische Textfelder

Ein statisches Textfeld stellt schreibgeschützte Informationen dar und kann vom Benutzer nicht ausgewählt werden. Vermeiden Sie die Verwendung für Text, den der Benutzer möglicherweise in die Zwischenablage kopiert. Allerdings kann der schreibgeschützte statische Text geändert werden, um eine Zustandsänderung widerzuspiegeln. Im folgenden Beispiel wird der statische Text des Ausgabe namens unter der Informationsgruppe geändert, sodass Änderungen an dem obigen Textfeld des Stamm Namespace vorgenommen werden.

Es gibt zwei Möglichkeiten, statische Textinformationen anzuzeigen.

Statischer Text kann in einem Dialogfeld ohne Kapselung eigenständig sein, wenn kein Gruppierungs Konflikt vorliegt. Entscheiden Sie, ob die zusätzlichen Zeilen eines Felds wirklich erforderlich sind. Ein Beispiel ist die Anzeige eines Verzeichnis Pfads in einem von einer Gruppenzeile erstellten Abschnitt, wie unten dargestellt:

![Statische Textinformationen in Text Steuerelementen](../../extensibility/ux-guidelines/media/DisplayingStaticText.png "DisplayingStaticText.png")<br />Statische Textinformationen in Text Steuerelementen

In einem Dialogfeld, in dem andere gruppierte Bereiche vorhanden sind und die Einkapselung der Informationen eine bessere Lesbarkeit ermöglicht, und wenn ein Abschnitt ausgeblendet oder angezeigt werden kann (wie im Bereich **Eigenschaftenfenster** Beschreibung), oder wenn Sie mit einer ähnlichen Benutzeroberfläche konsistent sein möchten, platzieren Sie den statischen Text in einem Feld. Dieses Gruppenfeld muss eine einzelne Regel sein und mit den folgenden Farben angezeigt werden `ButtonShadow` :

![Statischer Text in der Eigenschaftenfenster](../../extensibility/ux-guidelines/media/PropertiesWindow.png "PropertiesWindow.png")<br />Statischer Text in der Eigenschaftenfenster

### <a name="read-only-text-box"></a>Schreib geschütztes Textfeld

Dadurch kann der Benutzer den Text im Feld auswählen, aber nicht bearbeiten. Diese Textfelder werden vom üblichen 3D-Meißel mit einem Füll Zeichen begrenzt `ButtonShadow` .

Ein Textfeld kann aktiv (bearbeitbar) werden, wenn ein Benutzer ein zugeordnetes Steuerelement ändert, z. b. das Aktivieren/Deaktivieren eines Kontrollkästchens oder das auswählen/deaktivieren eines Options Felds. Beispielsweise wird auf der Seite Extras- **&gt; Optionen** unten das Textfeld **Startseite** aktiviert, wenn das Kontrollkästchen **Standard verwenden** deaktiviert ist.

![Schreib geschütztes Textfeld, in dem inaktive und aktive Zustände angezeigt werden](../../extensibility/ux-guidelines/media/ReadOnlyTextBox.png "ReadOnlyTextBox.png")<br />Schreib geschütztes Textfeld, in dem inaktive und aktive Zustände angezeigt werden

### <a name="using-text-in-dialogs"></a>Verwenden von Text in Dialogfeldern

Wichtige Richtlinien für Text in Dialogfeldern:

- Bezeichnungen für Textfelder, Listenfelder und Frames in unthemendialogfeldern beginnen mit einem Verb, haben nur ein ursprüngliches Großbuchstaben im ersten Wort und enden mit einem Doppelpunkt.

    > Text Steuerelemente in Design Dialogfeldern folgen den [Richtlinien für Windows-Desktop-UX](/windows/desktop/uxguide/top-violations) und nehmen keine Interpunktions Zeichen entgegen, mit Ausnahme von Fragezeichen in Hilfe Links.

- Die Bezeichnungen für Kontrollkästchen und Options Schaltflächen beginnen mit einem Verb, einem ersten Haupt Kapital auf dem ersten Wort und haben keine endinterpunktions Zeichen.

- Bezeichnungen für Schaltflächen, Menüs, Menü Elemente und Registerkarten enthalten in jedem Wort (titelfall) Anfangs Hauptstädte.

- Die Bezeichnungs Terminologie sollte mit ähnlichen Bezeichnungen in anderen Dialogfeldern übereinstimmen.

- Wenn möglich, muss ein Writer/Editor den Text schreiben oder genehmigen, bevor er für die Implementierung an den Entwickler weitergeleitet wird.

- Alle Steuerelemente sollten Bezeichnungen aufweisen, außer in besonderen Fällen, in denen die Tabstopps ausreichen.
Verwenden Sie bei Bedarf Hilfstext.

### <a name="helper-text"></a>Hilfetext

In Dialogfeldern enthalten, um dem Benutzer zu helfen, den Zweck des Dialogs nachzuvollziehen oder anzugeben, welche Aktion ausgeführt werden soll. Hilfetext sollte nur bei Bedarf verwendet werden, um die Verwendung von einfachen Dialogfeldern zu vermeiden. Die zwei Varianten von Hilfstext sind Dialog und Wasserzeichen.

Befolgen Sie die allgemeinen Speicherorte für Hilfetext, und stellen Sie eine selektive Einführung in neue Bereiche Häufige Szenarien für Hilfstext:

- Hilfetext in Dialogfeldern, um zusätzliche Richtung für die Interaktion mit einem komplexen Dialogfeld zu erhalten.

- Wasserzeichen Text in leeren Tool Fenstern oder in Dialogfeldern, um zu erläutern, warum kein Inhalt sichtbar ist.

- Ein Beschreibungs Bereich, wie unten im **Eigenschaftenfenster**.

- Wasserzeichen Text in einem leeren Editor, um zu erläutern, welche Aktion der Benutzer für den Einstieg ausführen sollte.

### <a name="dialog-helper-text"></a>Dialogfeld-Hilfetext

Ein Benutzeroberflächen-Designer kann helfen, zu bestimmen, wann Hilfetext geeignet ist. Der Designer kann festlegen, wo Hilfetext und der allgemeine Inhalt angezeigt werden. Benutzerunterstützung kann den eigentlichen Text schreiben/bearbeiten.

### <a name="watermarks"></a>Wasserzeichen

Dialogfelder profitieren von etwas anderen Grenz Richtlinien für Wasserzeichen. Da ein Dialog mit vielen Benutzeroberflächen Elementen (Bezeichnungen, Hinweis Text, Schaltflächen und anderen Container Steuerelementen mit Text) als ausgelastet angezeigt werden kann, werden Wasserzeichen in dunklen grauen (vscolor:) besser angezeigt `ButtonShadow` . In der Regel wird ein Wasserzeichen innerhalb eines Steuer Elements angezeigt, wie z. b. ein Listenfeld mit weißem Hintergrund (vscolor: `Window` ).

- Der Text wird in Dunkelgrau (vscolor: `ButtonShadow` ) angezeigt. Wenn das Wasserzeichen jedoch in einem mittelgrauen oder anderen farbigen (vscolor: `ButtonFace` ) Hintergrund angezeigt wird und die Lesbarkeit von Bedeutung ist, gehen Sie mit schwarzem Text (vscolor: `WindowText` ).

- Wasserzeichen können zentriert oder linksbündig angezeigt werden. Anwenden von Standard Entwurfs Regeln, wenn Ausrichtungs Entscheidungen getroffen werden. Das Wasserzeichen kann nicht im Hintergrund ausgewählt werden.

![Wasserzeichen Textbeispiel](../../extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />Wasserzeichen Textbeispiel

### <a name="context-specific-dynamic-text"></a>Kontext spezifischer (dynamischer) Text

Dynamischer Text kann auf zwei Arten in einem Dialogfeld oder in einer nicht modalen Benutzeroberfläche verwendet werden: entweder als dynamische Bezeichnung oder als dynamischer Inhalt.

- Dynamische Bezeichnung: eine gängige Verwendung von dynamischem Text befindet sich in beschreibenden Bereichen, die weitere Informationen für das ausgewählte Element bieten, z. b. in einem Dialogfeld, das eine Liste von Elementen und Eigenschaften für die Elemente enthält, die in einem Raster rechts angezeigt werden. Die Bezeichnung für das Eigenschaften Raster ist möglicherweise dynamisch, sodass das Raster auf der rechten Seite Informationen für dieses bestimmte Element anzeigt, wenn ein Element auf der linken Seite ausgewählt wird.

- Dynamischer Text: kann in Fällen nützlich sein, in denen Sie auf diese Weise bestimmte Informationen und keine allgemeinen Informationen anzeigen müssen, aber es sollte darauf geachtet werden, dass Sie nicht überlastet werden.

Wenn Sie möchten, dass Benutzer die Informationen kopieren können, sollte sich der dynamische Text in einem schreibgeschützten Textfeld befinden.

## <a name="buttons-and-hyperlinks"></a><a name="BKMK_ButtonsAndHyperlinks"></a> Schaltflächen und Hyperlinks

### <a name="overview"></a>Übersicht
Schaltflächen und Link Steuerelemente (Hyperlinks) müssen [grundlegende Windows-Desktop-Anleitungen](/windows/desktop/uxguide/ctrl-links) für die Verwendung, die Formulierung, die Größenanpassung und den Abstand befolgen.

### <a name="choosing-between-buttons-and-links"></a>Auswählen zwischen Schaltflächen und Links
Normalerweise wurden Schaltflächen für Aktionen verwendet, und Hyperlinks wurden für die Navigation reserviert. Schaltflächen können in allen Fällen verwendet werden, aber die Rolle von Verknüpfungen wurde in Visual Studio erweitert, sodass Schaltflächen und Verknüpfungen unter bestimmten Bedingungen austauschbar sind.

Verwendung von Befehls Schaltflächen:

- Primäre Befehle

- Anzeigen von Fenstern, die verwendet werden, um Eingaben zu erfassen oder auszuwählen, selbst wenn es sich um sekundäre Befehle handelt

- Zerstörerische oder nicht rückgängig-Aktionen

- Verpflichtungs Schaltflächen innerhalb von Assistenten und Seiten Flüssen

Vermeiden Sie Befehls Schaltflächen in Tool Fenstern oder, wenn Sie mehr als zwei Wörter für die Bezeichnung benötigen. Links können über längere Bezeichnungen verfügen.

 Verwendung von Verknüpfungen:

- Navigation zu einem anderen Fenster, Dokument oder einer Webseite

- Situationen, die eine längere Bezeichnung oder einen kurzen Satz zum Beschreiben der Absicht der Aktion erfordern

- Enge Bereiche, in denen eine Schaltfläche die Benutzeroberfläche überlastet, vorausgesetzt, dass die Aktion nicht destruktiv oder nicht rückgängig

- Aufheben der hervorgehoben sekundärer Befehle in Situationen, in denen viele Befehle vorhanden sind

#### <a name="examples"></a>Beispiele
![Befehls Verknüpfungen, die in der Info Leiste nach einer Statusmeldung verwendet werden](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703-01_CommandLinkInfobar")<br />Befehls Verknüpfungen, die in der Info Leiste nach einer Statusmeldung verwendet werden

![Links im CodeLens-Popup](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703-02_LinksInCodeLens")<br />Links im CodeLens-Popup

![Links, die für sekundäre Befehle verwendet werden, bei denen Schaltflächen zu viel Aufmerksamkeit erregen](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703-03_LinksAsSecondaryCommands")<br />Links, die für sekundäre Befehle verwendet werden, bei denen Schaltflächen zu viel Aufmerksamkeit erregen

### <a name="common-buttons"></a>Allgemeine Schaltflächen

#### <a name="text"></a>Text
Befolgen Sie die Richtlinien zum Schreiben von [Benutzeroberflächen Text und-Terminologie](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).

#### <a name="visual-style"></a>Visueller Stil

##### <a name="standard-unthemed"></a>Standard (ohne Design)
Die meisten Schaltflächen in Visual Studio werden in hilfsprogrammdialogfeldern angezeigt und sollten nicht formatiert werden. Sie sollten die Standarddarstellung von Schaltflächen entsprechend der von dem Betriebssystem vorgegebenen Schaltflächen widerspiegeln.

##### <a name="themed"></a>Artikeln
In einigen Fällen können Schaltflächen in der formatierten Benutzeroberfläche verwendet werden, und diese Schaltflächen müssen entsprechend formatiert werden. Weitere Informationen zu Design Steuerelementen finden Sie unter [Dialog](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) Felder.

### <a name="special-buttons"></a>Sonderschaltflächen

#### <a name="browse-buttons"></a>Durchsuchen... Parab
**[Durchsuchen...]** Schaltflächen werden in Raster, Dialogfeldern und Tool Fenstern und anderen Benutzeroberflächen Elementen verwendet. Sie zeigen eine Auswahl an, die dem Benutzer beim Ausfüllen eines Werts in ein Steuerelement hilft. Es gibt zwei Variationen dieser Schaltfläche: Long und Short.

![Die lange Schaltfläche [Durchsuchen...]](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703-04_BrowseLong")<br />Die lange Schaltfläche [Durchsuchen...]

![Die Schaltfläche mit den Auslassungs Punkten, nur kurz [...]](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703-05_BrowseShort")<br />Die Schaltfläche mit den Auslassungs Punkten, nur kurz [...]

Verwendung der kurzen Schaltfläche mit Auslassungs Punkten:

- , Wenn mehr als eine lange Schaltfläche **[Browse...]** in einem Dialogfeld vorhanden ist, z. b. Wenn mehrere Felder das Durchsuchen erlauben. Verwenden Sie die Schaltfläche Short **[...]** , um die verwirrenden Zugriffstasten zu vermeiden, die in dieser Situation erstellt wurden (**&Browse** und **B&URCHSUCHEN** im gleichen Dialogfeld).

- In einem engen Dialogfeld oder wenn es keinen sinnvollen Platz zum Platzieren der Long-Schaltfläche gibt.

- , Wenn die Schaltfläche in einem Raster Steuerelement angezeigt wird.

Richtlinien für die Verwendung der Schaltfläche:

- Verwenden Sie keine Zugriffstaste. Um über die Tastatur darauf zuzugreifen, muss der Benutzer die Tab-Taste aus dem angrenzenden Steuerelement aufrufen. Stellen Sie sicher, dass die Aktivier Reihenfolge ist, dass jede Schaltfläche Durchsuchen unmittelbar nach dem Feld fällt, das Sie ausfüllen wird Verwenden Sie niemals einen Unterstrich unterhalb des ersten Zeitraums.

- Legen Sie die Eigenschaft **Name** des Microsoft-Active Accessibility (MSAA) auf **Durchsuchen...** (einschließlich der Auslassungs Punkte) fest, damit Sprachausgaben Sie als "Durchsuchen" und nicht als "Punkt-Punkt-Punkt" oder "Zeitraum-Zeitraum-Periode" lesen. Bei verwalteten Steuerelementen bedeutet dies, dass die **AccessibleName** -Eigenschaft festgelegt wird.

- Verwenden Sie niemals eine Schaltfläche mit den Auslassungs Punkten **[...]** , außer eine Aktion zum Durchsuchen. Wenn Sie z. b. eine Schaltfläche **[New...]** benötigen, aber nicht genug Platz für den Text, muss das Dialogfeld neu gestaltet werden.

##### <a name="sizing-and-spacing"></a>Größe und Abstand
![Größenanpassung [Durchsuchen...] Schaltflächen: die Standardversion ist 75 x 23 Pixel, die kurze Version ist 26x 23 Pixel.](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703-06_BrowseSizing")<br />Festlegen der Größe für Schaltfläche [Durchsuchen...]

![Abstand [Durchsuchen...] Schaltflächen: Abstand zwischen verknüpften Steuerelementen und Standard-Such Schaltfläche 7 Pixel, Abstand zwischen verknüpften Steuerelementen und kurzer Durchsuchen-Schaltfläche](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703-07_BrowseSpacing")<br />Festlegen der Abstände für Schaltfläche [Durchsuchen...]

#### <a name="graphical-buttons"></a>Grafische Schaltflächen
Einige Schaltflächen sollten immer ein grafisches Bild verwenden und nie Text enthalten, um Speicherplatz zu sparen und Lokalisierungs Probleme zu vermeiden. Diese werden häufig in Feld-pickern und anderen sortierbaren Listen verwendet.

> [!NOTE]
> Benutzer müssen zu diesen Schaltflächen wechseln (es sind keine Zugriffstasten vorhanden). Platzieren Sie Sie daher in einer sinnvollen Reihenfolge. Ordnen Sie die- `name` Eigenschaft der Schaltfläche der Aktion zu, die Sie annimmt, damit die Bildschirm Sprachausgabe die Schaltflächen Aktion korrekt interpretiert.

| Funktion | Schaltfläche |
| --- | --- |
| Hinzufügen | ![Grafische Schaltfläche "Hinzufügen"](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703-08_ButtonAdd") |
| Entfernen | ![Grafische Schaltfläche "Entfernen"](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703-09_ButtonRemove") |
| Alle hinzufügen | ![Grafische Schaltfläche "Alles hinzufügen"](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703-10_ButtonAddAll") |
| Alle entfernen | ![Grafische Schaltfläche "Alle entfernen"](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703-11_ButtonRemoveAll") |
| Nach oben | ![Grafische Schaltfläche "Nach oben"](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703-12_ButtonMoveUp") |
| Nach unten | ![Grafische Schaltfläche "Nach unten"](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703-13_ButtonMoveDown") |
| Löschen | ![Grafische Schaltfläche "Löschen"](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703-14_ButtonDelete") |

##### <a name="sizing-and-spacing"></a>Größe und Abstand
Die Größenanpassung für grafische Schaltflächen ist identisch mit der Kurzversion der Schaltfläche **[Durchsuchen...]** (26x23 Pixel):

![Darstellung eines grafischen Bilds auf der Schaltfläche mit und ohne transparente Farbe](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703-15_GraphicalButtonSpacing")<br />Darstellung eines grafischen Bilds auf der Schaltfläche mit und ohne transparente Farbe

### <a name="hyperlinks"></a>Hyperlinks
Hyperlinks eignen sich gut für Navigations basierte Aktionen wie das Öffnen eines Hilfe Themas, modalen Dialog Felds oder Assistenten. Wenn ein Hyperlink für einen Befehl verwendet wird, sollte immer eine sichtbare und spürbare Änderung der Benutzeroberfläche angezeigt werden. Im Allgemeinen werden Aktionen, die für eine Aktion (z. b. speichern, Abbrechen und löschen) ausgeführt werden, besser über eine Schaltfläche kommuniziert.

#### <a name="writing-style"></a>Schreibstil
Befolgen Sie die [Anleitungen zum Windows-Desktop für die Benutzeroberfläche](/windows/desktop/uxguide/text-ui). Verwenden Sie nicht "Weitere Informationen zu", "Weitere Informationen zu" oder "Hilfe zu diesem" formulieren. Stattdessen können Sie Text in Bezug auf die primäre Frage des Hilfe Inhalts verknüpfen. Beispiel: "**Gewusst wie Hinzufügen eines Servers zum Server-Explorer?**"

#### <a name="visual-style"></a>Visueller Stil

- Hyperlinks sollten immer [den vscolor-Dienst](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)verwenden. Wenn ein Hyperlink nicht ordnungsgemäß formatiert ist, blinkt er nach der aktiven oder nach dem Besuch eine andere Farbe.

- Fügen Sie Unterstriche nicht in den Ruhezustand des Steuer Elements ein, es sei denn, der Link ist ein Satz Fragment innerhalb eines vollständigen Satzes, wie in einem Wasserzeichen

- Unterstriche sollten nicht auf Hover angezeigt werden. Stattdessen ist das Feedback an den Benutzer, dass der Link aktiv ist, eine geringfügige Farbänderung und der entsprechende Link Cursor.

## <a name="tree-views"></a><a name="BKMK_TreeViews"></a> Struktur Ansichten

Struktur Ansichten bieten eine Möglichkeit, komplexe Listen in über-und untergeordneten Gruppen zu organisieren. Ein Benutzer kann übergeordnete Gruppen erweitern oder reduzieren, um zugrunde liegende untergeordnete Elemente anzuzeigen oder auszublenden. Alle Elemente in einer Strukturansicht können ausgewählt werden, um weitere Aktionen bereitzustellen.

### <a name="tree-view-visual-style"></a><a name="BKMK_TreeViewVisualStyle"></a> Visueller Stil der Strukturansicht

#### <a name="expanders"></a>Expander
Strukturansicht-Steuerelemente sollten dem Expander-Entwurf entsprechen, der von Windows und Visual Studio verwendet wird. Jeder Knoten verwendet ein Expander-Steuerelement, um zugrunde liegende Elemente anzuzeigen oder auszublenden. Die Verwendung eines Expander-Steuer Elements bietet Konsistenz für Benutzer, die möglicherweise unterschiedliche Struktur Ansichten in Windows und Visual Studio sehen.

![Richtig: ordnungsgemäße Art des Struktur Ansichts Knotens mithilfe eines Expander-Steuer Elements](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Richtig: ordnungsgemäße Art des Struktur Ansichts Knotens mithilfe eines Expander-Steuer Elements

![Falsch: falscher Stil des Struktur Ansichts Knotens](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705-2_TreeViewIncorrect1")<br />Falsch: falscher Stil des Struktur Ansichts Knotens

#### <a name="selection"></a>Auswahl
Wenn ein Knoten innerhalb der Strukturansicht ausgewählt ist, sollte die Hervorhebung auf die gesamte Breite des Strukturansicht-Steuer Elements erweitert werden. Dadurch können Benutzer die ausgewählten Elemente eindeutig identifizieren. Auswahl Farben sollten das aktuelle Visual Studio-Design widerspiegeln.

![Richtig: die Hervorhebung des ausgewählten Knotens ist für die gesamte Breite des Strukturansicht-Steuer Elements geeignet.](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Richtig: die Hervorhebung des ausgewählten Knotens ist für die gesamte Breite des Strukturansicht-Steuer Elements geeignet.

![Falsch: die Hervorhebung des ausgewählten Knotens passt nicht zur gesamten Breite des Strukturansicht-Steuer Elements.](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705-3_TreeViewIncorrect2")<br />Falsch: die Hervorhebung des ausgewählten Knotens passt nicht zur gesamten Breite des Strukturansicht-Steuer Elements.

#### <a name="icons"></a>Symbole
Symbole sollten nur in Strukturansicht-Steuerelementen verwendet werden, wenn Sie bei der visuellen Identifizierung von Unterschieden zwischen Elementen helfen. Im Allgemeinen sollten Symbole nur in heterogenen Listen verwendet werden, in denen die Symbole Informationen enthalten, um die Elementtypen zu unterscheiden. In einer homogenen Liste können Symbole häufig als Rauschen angesehen werden und sollten vermieden werden. In diesem Fall kann das Gruppensymbol (übergeordnetes Element) den Typ der darin enthaltenen Elemente übermitteln. Eine Ausnahme von dieser Regel wäre, wenn das Symbol dynamisch ist und verwendet wird, um den Zustand anzugeben.

#### <a name="scroll-bars"></a>Bildlaufleisten
Scrollleisten sollten immer ausgeblendet werden, wenn der Inhalt in das Strukturansicht-Steuerelement passt. Scrollleisten können in einem Bild lauffähigen Fenster ausgeblendet oder semitransparent sein und angezeigt werden, wenn das Fenster, das die Strukturansicht enthält, den Fokus besitzt, oder wenn der Mauszeiger auf die Strukturansicht zeigt.

![Vertikale und horizontale Schiebe leisten werden angezeigt, da der Inhalt die Begrenzungen des Strukturansicht-Steuer Elements überschritten hat.](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705-4_Scrollbars")<br />Vertikale und horizontale Schiebe leisten werden angezeigt, da der Inhalt die Begrenzungen des Strukturansicht-Steuer Elements überschritten hat.

### <a name="tree-view-interactions"></a><a name="BKMK_TreeViewInteractions"></a> Interaktionen mit Strukturansicht

#### <a name="context-menus"></a>Kontextmenüs
In einem Struktur Ansichts Knoten können Untermenüoptionen in einem Kontextmenü angezeigt werden. Dies tritt normalerweise auf, wenn ein Benutzer mit der rechten Maustaste auf ein Element geklickt oder die Menü Taste auf einer Windows-Tastatur gedrückt hat, auf der das Element ausgewählt ist. Es ist wichtig, dass der Knoten den Fokus erhält und ausgewählt wird. Dadurch kann der Benutzer identifizieren, zu welchem Element das Untermenü gehört.

![Das Element, das das Kontextmenü generiert hat, erhält den Fokus, um den Benutzer zu benachrichtigen, welches Element ausgewählt wurde.](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705-5_ContextMenu")<br />Das Element, das das Kontextmenü generiert hat, erhält den Fokus, um den Benutzer zu benachrichtigen, welches Element ausgewählt wurde.

#### <a name="keyboard"></a>Tastatur
Die Strukturansicht sollte die Möglichkeit bieten, Elemente auszuwählen und Knoten mithilfe der Tastatur zu erweitern bzw. zu reduzieren. Dadurch wird sichergestellt, dass die Navigation unsere Barrierefreiheits Anforderungen erfüllt.

##### <a name="tree-view-control"></a>Strukturansicht-Steuerelement
Visual Studio-Struktur Steuerelemente sollten der allgemeinen Tastaturnavigation folgen:

- **Pfeil nach oben:** Elemente durch Verschieben der Struktur auswählen

- **Pfeil nach unten:** Elemente durch Verschieben in der Struktur auswählen

- **Rechter Pfeil:** Erweitern eines Knotens in der Struktur

- **Pfeil nach links:** Reduzieren eines Knotens in der Struktur

- **EINGABETASTE:** Initiieren, laden, ausgewähltes Element ausführen

##### <a name="trid-tree-view-and-grid-view"></a>"Did" (Strukturansicht und Rasteransicht)
Ein-Steuerelement ist ein komplexes Steuerelement, das eine Strukturansicht innerhalb eines Rasters enthält. Beim erweitern, reduzieren und Navigieren in der Struktur sollten dieselben Tastaturbefehle wie für eine Strukturansicht berücksichtigt werden, mit den folgenden Ergänzungen:

- **Rechter Pfeil:** Erweitern Sie einen Knoten. Nachdem der Knoten erweitert wurde, sollte er weiterhin zur nächsten Spalte auf der rechten Seite navigieren. Die Navigation sollte am Ende der Zeile angehalten werden.

- **Registerkarte:** Navigiert zur nächsten Zelle auf der rechten Seite.  Am Ende der Zeile wird die Navigation mit der nächsten Zeile fortgesetzt.

- **UMSCHALT + TAB:** Navigiert zur nächsten Zelle auf der linken Seite.  Am Anfang der Zeile wird die Navigation mit der äußersten rechten Zelle in der vorherigen Zeile fortgesetzt.

![Ein-Steuerelement in Visual Studio](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705-6_Trid")<br />Ein-Steuerelement in Visual Studio
