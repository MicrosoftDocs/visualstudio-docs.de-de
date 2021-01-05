---
title: UX Essentials für Visual Studio | Microsoft-Dokumentation
description: Lesen Sie diese bewährten Methoden für die Benutzer Darstellung für neue Features, die Sie für Visual Studio entwickeln, einschließlich Informationen zur Bildschirmauflösung.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 616837c358c804198818df659cb7b7ee76716305
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2021
ms.locfileid: "97864050"
---
# <a name="ux-essentials-for-visual-studio"></a>UX Essentials für Visual Studio

## <a name="best-practices"></a>Bewährte Methoden

### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. seien Sie in der Visual Studio-Umgebung einheitlich.

- Befolgen Sie die vorhandenen [Interaktionsmuster](interaction-patterns-for-visual-studio.md) innerhalb der Shell.

- Entwerfen Sie Features, die mit der visuellen Sprache der Shell und den [handwerklichen Anforderungen](evaluation-tools-for-visual-studio.md)übereinstimmen.

- Verwenden Sie freigegebene Befehle und Steuerelemente, wenn Sie vorhanden sind.

- Informieren Sie sich über die Visual Studio-Hierarchie und die Art und Weise, wie Sie den Kontext festlegt und

### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. verwenden Sie den Umgebungs Dienst für Schriftarten und Farben.

- Die Benutzeroberfläche sollte die aktuelle Einstellung der [Umgebungs Schriftart](fonts-and-formatting-for-visual-studio.md) beachten, es sei denn, Sie ist für die Anpassung auf der Seite Schriftarten und Farben im Dialogfeld Optionen verfügbar.

- Benutzeroberflächen Elemente müssen den [vscolor-Dienst](colors-and-styling-for-visual-studio.md)verwenden, wobei freigegebene Umgebungs Token oder featurespezifische Token verwendet werden.

### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. machen Sie alle Bilder konsistent mit dem neuen vs-Stil.

- Befolgen Sie die Entwurfs Prinzipien von Visual Studio für Symbole, Glyphen und andere Grafiken.

- Platzieren Sie keinen Text in grafischen Elementen.

### <a name="4-design-from-a-user-centric-perspective"></a>4. entwerfen Sie aus einer Benutzer zentrierten Perspektive.

- Erstellen Sie den Task Ablauf vor den einzelnen Features darin.

- Machen Sie sich mit ihren Benutzern vertraut, und machen Sie das Wissen in ihrer Spezifikation explizit.

- Wenn Sie die Benutzeroberfläche überprüfen, sollten Sie die gesamte Benutzeroberfläche sowie die Details auswerten.

- Entwerfen Sie die Benutzeroberfläche, sodass Sie unabhängig vom Gebiets Schema oder der Sprache funktionsfähig und attraktiv bleibt.

## <a name="screen-resolution"></a>Bildschirmauflösung

### <a name="minimum-resolution"></a>Mindestauflösung

- Die minimale Auflösung für Visual Studio 2015 beträgt **1.280 x 720**. Dies bedeutet, dass es *möglich* ist, Visual Studio mit dieser Auflösung zu verwenden, obwohl dies möglicherweise nicht optimal ist. Es gibt keine Garantie dafür, dass alle Aspekte bei Auflösungen kleiner als 1280X720 verwendet werden können.

- Die Zielauflösung für Visual Studio ist **1366x768**. Dies ist die niedrigste Lösung, bei der wir eine *gute* Benutzerfunktion versprechen.

- Die anfängliche Dialogfeld Höhe sollte **kleiner als 700 Pixel** sein, sodass Sie in die minimale Auflösung des IDE-Frames bei 96 dpi passt.

### <a name="high-density-displays"></a>Anzeige mit hoher Dichte
 Die Benutzeroberfläche in Visual Studio muss gut in allen dpi-Skalierungsfaktoren funktionieren, die von Windows standardmäßig unterstützt werden: 150%, 200% und 250%.

## <a name="anti-patterns"></a>Antimuster
 Visual Studio enthält viele Beispiele für die Benutzeroberfläche, die unseren Richtlinien und bewährten Methoden folgen. Um konsistent zu sein, nehmen Entwickler häufig an den Entwurfsmustern der Design-Benutzeroberfläche ähnlich, wie Sie es erstellen. Obwohl dies ein guter Ansatz ist, der uns dabei hilft, Konsistenz bei der Interaktion von Benutzern und dem visuellen Design zu erzielen, werden die Features gelegentlich mit einigen Details ausgeliefert, die aufgrund von Zeit Plan Einschränkungen oder der Mängel Priorisierung nicht unsere Richtlinien erfüllen. In diesen Fällen möchten wir nicht, dass Teams eines dieser "Antimuster" kopieren, da Sie eine schlechte oder inkonsistente Benutzeroberfläche innerhalb der Visual Studio-Umgebung verbreiten.

### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>Erforderliche Felder/Einstellungen werden standardmäßig im Fehlerzustand angezeigt.

#### <a name="feature-team-goals"></a>Funktionsteam Ziele

- Warnen Sie die Benutzer, dass Sie ein Element hinzugefügt haben, das konfiguriert werden muss.

- Zeichnen Sie die Aufmerksamkeit des Benutzers auf die Bereiche, für die eine Eingabe erforderlich ist.

#### <a name="anti-pattern-solution"></a>Antipattern-Lösung
 Sobald der Benutzer eine Aktion initiiert hat und bevor er die Aufgabe abgeschlossen hat, platzieren Sie die Symbole für kritische Symbole direkt neben den Bereichen, die konfiguriert werden müssen.

#### <a name="example-manifest-designer-declarations"></a>Beispiel: Manifest-Designer-Deklarationen
 Wenn Sie der Liste eine Deklaration hinzufügen, wird diese sofort in einen Fehlerzustand versetzt, der beibehalten wird, bis der Benutzer die erforderlichen Eigenschaften festlegt.

 In diesem Fall besteht ein zusätzliches Problem, da das Symbol, das für die Warnung verwendet wird, ein " &times; "-Symbol enthält, sodass das allgemeine Entfernungs Symbol nicht daneben verwendet werden kann. Folglich verwendet die Benutzeroberfläche eine Entfernungs Schaltfläche, ein eher umständlich-Steuerelement.

 ![Wenn die Benutzeroberfläche standardmäßig in einen Fehlerzustand versetzt wird, ist dies ein Visual Studio-Antimuster.](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti-Muster")<br />Wenn die Benutzeroberfläche standardmäßig in einen Fehlerzustand versetzt wird, ist dies ein Visual Studio-Antimuster.

#### <a name="alternatives"></a>Alternativen

Eine bessere Lösung für dieses Problem ist Folgendes:

- Ermöglicht dem Benutzer das Hinzufügen einer Deklaration ohne Warnung und das anschließende verschieben direkt, um Eigenschaften für das Element festzulegen.

- Fügen Sie das Warnsymbol (Goldene Dreiecks) hinzu, wenn der Fokus vom Element bewegt wird, z. b., um der Liste eine weitere Deklaration hinzuzufügen oder um Registerkarten im Designer zu ändern.

- Wenn der Benutzer versucht, die Registerkarten vor dem Festlegen der Eigenschaften für eine beliebige Deklaration zu ändern, wird ein Dialogfeld angezeigt, in dem die Anwendung nicht erstellt wird (oder was die Auswirkungen hat), bis die Warnungen aufgelöst werden Wenn der Benutzer das Dialogfeld schließt und die Registerkarten trotzdem ändert, wird der Registerkarte Deklarationen ein Symbol ("kritisch" oder "Warnung") hinzugefügt.

### <a name="multiple-clicks-to-dismiss-ui"></a>Mehrere Klicks zum Verwerfen der Benutzeroberfläche

#### <a name="feature-team-goals"></a>Funktionsteam Ziele
 Erlauben Sie dem Benutzer nicht, die Benutzeroberfläche zu verwerfen, ohne zuvor den Erläuterungstext zu sehen.

#### <a name="anti-pattern"></a>Antimuster
 Das Team, das die Video Verknüpfungen an verschiedenen Stellen in der vs-Benutzeroberfläche einfügt, entschied sich für das gängige Muster der " &times; "-Schaltfläche "Schließen" und der QuickInfo-Erklärung, wie von UX angegeben, und implementiert stattdessen eine Dropdown-und "nicht mehr anzeigen"

#### <a name="example-video-links-in-team-explorer"></a>Beispiel: Video Verknüpfungen in Team Explorer
Wenn Sie den Benutzer zwingen, erklärenden Text zu lesen, bevor die Benutzeroberfläche fehlt, ist es ein Antimuster in Visual Studio. Ordnungsgemäß entworfen, Video Links sollten eine QuickInfo mit zusätzlichen Informationen zu Hover anzeigen, und durch Klicken auf " &times; " sollte die Nachricht verworfen werden, ohne dass eine weitere Interaktion erforderlich ist.

 ![Anti&#45;Muster für erklärenden Text &#45; falsch](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleklicks")<br />Falsches Video Link Muster

Anstatt eine einfache Schaltfläche "Schließen" (ein Klick) zu verwenden, wird der Benutzer gezwungen, zwei Klicks zu verwenden, um die Benutzeroberfläche einfach an jedem Ort zu verwerfen, an dem die Video Links angezeigt werden.

Der richtige Entwurf für diese Situation besteht darin, das Muster zu befolgen, das Internet Explorer, Office und Visual Studio gemeinsam ist: bei dem Mauszeiger kann der Benutzer die QuickInfo-Beschreibung sehen und mit einem Klick die Benutzeroberfläche ausblenden.

 ![Anti&#45;Muster für erklärenden Text &#45; richtig](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Enatorytextanti-Pattern-correct")<br />Richtiges Video Link Muster

### <a name="using-command-bars-for-settings"></a>Verwenden von Befehls leisten für Einstellungen

**Abbildung A** stellt dieses Antimuster dar: das Platzieren einer Einstellung unterhalb einer Befehls Schaltfläche, die für mehr als nur den Befehl gilt. In dieser Skizze sind neben dem Debuggen auch Befehle vorhanden – wie z. b. in Browser anzeigen, starten ohne Debugging und schrittweise Anleitung –, die die ausgewählte Einstellung berücksichtigt.

![Abbildung A: Antimuster der Befehlsleiste](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti-Pattern-figurea")<br />Abbildung A: Antimuster der Befehlsleiste

Ein etwas besseres, aber dennoch nicht wünschenswert ist das Einfügen von Einstellungen dieses Typs in die Symbolleisten (siehe **Abbildung B**). Wenn Split-Schaltflächen weniger Platz beanspruchen und daher eine Verbesserung gegenüber Dropdown-Vorgängen zur Folge haben, verwenden beide Entwürfe immer noch eine Symbolleiste, um etwas zu fördern, das eigentlich kein Befehl ist.

![Abbildung B: besser, aber immer noch ein Befehls leisten-Antimuster](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti-Pattern-figureb")<br />Abbildung B: besser, aber immer noch ein Befehls leisten-Antimuster

Im richtigen Ansatz in **Abbildung C** ist die Einstellung an eine Reihe von Befehlen gebunden. Es wird keine globale Einstellung festgelegt, und wir wechseln einfach zwischen vier Befehlen. Dies ist die einzige Situation, in der Befehle in der Symbolleiste zulässig sind.

![Abbildung C: korrekte Verwendung des Visual Studio-Befehls leisten Musters](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti-Pattern-figurec")<br />Abbildung C: korrekte Verwendung des Visual Studio-Befehls leisten Musters

### <a name="control-anti-patterns"></a>Steuerelement-Antimuster
 Einige Antimuster sind einfach falsche Verwendung oder Darstellung eines Steuer Elements oder einer Gruppe von Steuerelementen.

#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>Unterstreichung der Verwendung als Gruppen Bezeichnung, nicht als Hyperlink
 Das unterstreichen von Text sollte nur für Hyperlinks verwendet werden.

 **Schlechtem**\
 ![Unterstrichener Text, der kein Hyperlink ist, ist ein Visual Studio-Antimuster.](../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "0102-g_GroupLabelIncorrect")<br />Unterstrichener Text, der kein Hyperlink ist, ist ein Visual Studio-Antimuster.

 **Glück**\
 ![Ordnungsgemäß formatiert, nicht Hyperlink-Text wird in der Umgebungs Schriftart ungeschmückt angezeigt.](../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "0102-h_GroupLabelCorrect")<br />Ordnungsgemäß formatiert, nicht Hyperlink-Text wird in der Umgebungs Schriftart ungeschmückt angezeigt.

#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>Wenn Sie auf ein Kontrollkästchen klicken, wird ein Popup Dialogfeld angezeigt.
 Wenn Sie im Assistenten "Windows Azure-Anwendung veröffentlichen" auf das Kontrollkästchen "Remotedesktop für alle Rollen aktivieren" klicken, wird sofort ein Popup Dialogfeld mit einem Visual Studio-Antimuster angezeigt. Außerdem wird das Kontrollkästchen Feld nach der Auswahl nicht mit einem Kontrollkästchen aufgefüllt, einem weiteren Interaktions-Antimuster.

 ![Das Einrichten eines Dialog Felds nach dem Klicken auf ein Kontrollkästchen ist ein Visual Studio-Antimuster.](../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "0102-i_CheckboxPopup")<br />Das Einrichten eines Dialog Felds nach dem Klicken auf ein Kontrollkästchen ist ein Visual Studio-Antimuster.

### <a name="hyperlink-anti-patterns"></a>Antimuster für Hyperlink
 Das folgende Beispiel enthält zwei Antimuster:

1. Der Vordergrund, der rot bei hover wird, bedeutet, dass die richtige freigegebene Farbe aus dem Schriftart Dienst nicht verwendet wird.

2. "Weitere Informationen" ist nicht der passende Text für einen Link zu einem konzeptionellen Thema. Das Ziel des Benutzers ist nicht, mehr zu erfahren, sondern die Auswirkungen ihrer Wahl zu verstehen.

   ![Das Ignorieren des Color-Dienes und die Verwendung von "Weitere Informationen" für Hyperlinks sind Visual Studio-Antimuster.](../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "0102-j_HyperlinkIncorrect")<br />Das Ignorieren des Color-Dienes und die Verwendung von "Weitere Informationen" für Hyperlinks sind Visual Studio-Antimuster.

**Bessere Lösung:** Stellen Sie die Frage ein, die der Benutzer durch Klicken auf den Link Fragen würde. Zum Beispiel:

- Funktionsweise von Windows Azure-Diensten

- Wann benötige ich ein Windows Azure Mobile Services-Projekt?

#### <a name="using-click-here-for-links"></a>Verwenden von "Click here" für Links
 Hyperlinks sollten selbst beschreibend sein. Es ist ein Antimuster für die Verwendung von "Click here" oder einer beliebigen ähnlichen Variation.

 **Schlecht:** "Klicken Sie hier, um Anweisungen zum Erstellen eines neuen Projekts zu finden."

 **Gut:** "Gewusst wie erstellen Sie ein neues Projekt?"
