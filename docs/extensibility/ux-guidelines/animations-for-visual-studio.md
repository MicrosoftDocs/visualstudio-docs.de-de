---
title: Animationen für Visual Studio | Microsoft-Dokumentation
description: Erfahren Sie mehr über Regeln, mit denen konsistente und benutzerfreundliche Animations Stile in der Visual Studio-IDE sichergestellt werden.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c86b033986511100415989e76f4f1e6ef7702f10
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715950"
---
# <a name="animations-for-visual-studio"></a>Animationen für Visual Studio
## <a name="animation-fundamentals"></a>Grundlagen der Animation

### <a name="animation-best-practices-in-visual-studio"></a>Bewährte Methoden für Animationen in Visual Studio
Befolgen Sie diese Regeln, um konsistente und benutzerfreundliche Animations Stile in der Visual Studio-IDE sicherzustellen.

- **Seien Sie selektiv.** Beschränken Sie Animationen auf solche, die bestimmte Zwecke erfüllen.

- **Zeitliche Steuerung und Geschwindigkeit sind wichtig** , um sicherzustellen, dass die Übergänge schnell und natürlich sind:

  - Vervollständigen Sie alle animierten Übergänge innerhalb einer halben Sekunde (500 Millisekunden).

  - Animationen, die häufig auftreten würden, müssen schnell genug sein, um den Workflow des Benutzers nicht zu unterbrechen. Sehen Sie sich die Animation in einer Schleife an, und passen Sie die zeitliche Steuerung an, bis Sie richtig ist

  - Animationen sollten nicht so schnell oder jarrert sein, dass Sie schwer zu verstehen sind, aber nicht so langsam sind, dass Sie eine ungeduldige Umstellung auf die Beendigung des Übergangs machen.

  - Verwenden Sie Variablen zeitliche Steuerung, um die Wichtigkeit hervorzuheben. Wenn Sie z. b. durch eine Sequenz von Elementen in einem Klassendiagramm navigieren, werden die Übergänge zwischen den Elementen durchlaufen, um sich auf wichtige Elemente zu konzentrieren.

- **Verwenden Sie die schrittweise nichtlineare** Beschleunigung von einem Zustand in einen anderen, wodurch eine gute und natürliche Bewegung geschaffen wird.

- Verwenden Sie nach Möglichkeit **eine feine Animation** , wenn Sie auf den Mauszeiger zeigen, um interaktive Elemente mit der Maus anzuzeigen.

- Wenn Sie sich sehr auf Animationen in ihren Features verlassen, **Stellen Sie eine Möglichkeit bereit, diese** lokal (für alle ihre Features) als Option im Dialogfeld Extras **> Optionen** zu deaktivieren.

- Es **sollte immer nur eine Animation** vorhanden sein, und es sollte nur eine Information vermittelt werden. Es kann verwirrend sein, mehrere Objekte zu verschieben oder zu übermitteln.

- **Die Feinheit ist wichtig.** In den meisten Fällen ist es nicht erforderlich, dass die Animation eine Benutzer Aufmerksamkeit erfordert, um ihren Zweck zu erfüllen. Feine Änderungen an zeitlichen Steuerung, Sequenzierung und Verhalten können die Wahrnehmung erheblich beeinträchtigen und den Unterschied zwischen einer effektiven und ineffektiven Animation ausmachen.

- Wenn Sie Animationen verwenden, um auf etwas zu achten, **sollten Sie sicherstellen, dass es sich lohnt, den** Gedanken Aufwand des Benutzers zu unterbrechen.

- **Beim Anzeigen von Fortschritt oder Status** durch Animation:

  - Hiermit wird die Status Verschiebung nicht mehr angezeigt, wenn der zugrunde liegende Prozess nicht voranschreitet

  - Unterscheiden sie unbestimmt Prozesse von bestimmte.

  - Stellen Sie sicher, dass eine Animation identifizierbare Abschluss-und Fehlerzustände aufweist.

  - Minimieren Sie die Verwendung von Effekt Animationen, die den Status anzeigen, und stellen Sie sicher, dass Sie einen echten Wert haben, indem Sie zusätzliche Informationen zur tatsächlichen Verwendung Beispiele sind vorübergehende Statusänderungen und Notfälle.

#### <a name="animation-donts"></a>"Animation":

- Verwenden Sie keine kleinen Bewegungen (Bewegung bei geringem Speicherbedarf). Bevorzugen und Ändern von verschiebenden Objekten.

- Verwenden Sie Animationen nicht, die über einen großen Bereich der Bildschirmfläche stattfinden. Unabhängig von der Größe ist dieser Animationsstil für den Benutzer von ablenkend.

- Verwenden Sie keine Animationen, die nicht mit dem Objekt verknüpft sind, mit dem sich der Benutzer derzeit im Fokus befindet.

- Verwenden Sie keine Animationen, bei denen eine Benutzerinteraktion erforderlich ist, um den Zustand zurückzusetzen, z. b. das Erzwingen der Reaktion des Benutzers auf eine blinkende Benachrichtigung, um das Blinken anzuhalten. Die Interaktion mit Ihnen sollte in irgendeiner Weise ausreichen, um Sie zu verwerfen.

Weitere Informationen zu Anwendungen für diese bewährten Methoden finden Sie unter [animationsmuster](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).

### <a name="animation-metrics"></a>Animations Metriken

- Das System sollte in weniger als 10 Millisekunden sichtbar auf Benutzer Gesten reagieren.

- Animierte Übergänge sollten nicht länger als 500 Millisekunden dauern.

- Eine Möglichkeit, Übergänge zu kompensieren, die längere Zeit erfordern, besteht darin, Sie in zwei Teile zu unterteilen. Der erste Teil einer Animation könnte z. b. der leere Inhalts Container (bis zu 500 Millisekunden), gefolgt von dem Inhalt, der in den Container ausgeblendet wird (bis zu 500 Millisekunden) sein.

- Für Ladezeiten, die berechnet werden können, wird eine Determinante Statusanzeige (Prozentsatz der Fortschrittsanzeige) bevorzugt.

- Für Ladezeiten, die nicht berechnet werden können, ist ein ausgelasteter Indikator wie ein Cursor oder eine eingebettete spinanimation (Lade-oder Arbeits Indikator) geeignet.

### <a name="animation-as-communicator"></a>Animation als Communicator
In der Visual Studio-Benutzeroberfläche funktioniert Animation nur als Kommunikations Tool.  Sie wird verwendet, um eine Vielzahl von Informationen zu kommunizieren, wie z. b. strukturelle Änderungen in der Benutzeroberfläche (z. b. Wenn ein Menü geöffnet oder geschlossen wird). Mithilfe der Animation können Sie das zeitabhängige Verhalten komplexer Systeme visualisieren, wie z. b. die Visualisierung des Installations Fortschritts. Animationen können auch verwendet werden, um auf Warnungen und Benachrichtigungen aufmerksam zu machen.

 UI-Animationen funktionieren in der Regel auf vier Arten: visualisieren, berücksichtigen, simulieren und Reaktionszeiten/Fortschrittsindikatoren.

#### <a name="visualize"></a>Visualisieren
Animation kann die dreidimensionale Natur von Objekten hervorheben und es Benutzern erleichtern, ihre räumliche Struktur visuell darzustellen. Um dies zu erreichen, muss die Animation das Objekt möglicherweise in einem vollständigen Kreis drehen, Sie langsam hin-und Herdrehen, oder das Objekt näher anweisen und seine Größe leicht erhöhen, um das Rollover oder den Fokus hervorzuheben.

Obwohl dreidimensionale Objekte mit dem Benutzer Steuerelement verschoben werden können, sollte der Designer im Voraus (Programm gesteuert oder manuell) bestimmen, wie eine Bewegung am besten animiert werden kann, die ein optimales Verständnis des Objekts bietet. Diese programmierte Animation kann dann vom Benutzer aktiviert werden, indem der Cursor über dem Objekt platziert wird, während benutzergesteuerte Bewegungen erfordern, dass der Benutzer wissen muss, wie das Objekt bearbeitet wird. Beschränken Sie die Bewegung auf eine einzelne Achse oder Ausrichtung auf eine Uhrzeit. Skalieren, drehen oder übersetzen, aber nicht mehr als eins gleichzeitig ausführen.

Die Kategorie visualisieren umfasst die Aspekte von Daten, Beziehungen, Status, Struktur, Sequenz und Zeit.

##### <a name="data"></a>Daten
Veranschaulichen komplexer und variabler Informationen:

- Durchlaufen von Informations Visualisierungen wie Diagrammen und Diagrammen

- Schrittweise Anleitung für eine Sequenz, eine Tour und Paging

- Aufrufen von Details, zeigen und hervorheben spezifischer Informationen

- Überlagern von Details und zusätzlichen Informationen oberhalb eines Elements mit Fokus

- Morphung von einer Struktur oder Organisations Darstellung zu einer anderen

- Darstellen von Änderungen im Zeitverlauf mithilfe von Zeit Schiebereglern, Jog-und-Shuttle-Rädern und Transport Steuerelementen (Wiedergabe, anhalten und anhalten)

##### <a name="relationships"></a>Beziehungen

- Veranschaulichen, wie Elemente zueinander zueinander stehen oder welche Elemente mit einem bestimmten Element in Beziehung stehen

- Hierarchien und über-und untergeordnete Beziehungen anzeigen

- Ein Element erzeugt ein weiteres

- Ein Element wird zu einem anderen Element minimiert.

- Ein Element, das zu einem anderen Element gehört.

##### <a name="state"></a>State

- Inhalts Aktualisierungen

- Benutzer Fokus und-Auswahl

- Fortschritt

- Errors

##### <a name="structure"></a>Struktur

- Pivotieren der Struktur auf einem Knoten

- Neuausrichtung

- Minimieren und maximieren, erweitern und reduzieren

##### <a name="sequence"></a>Sequenz

- Bildschirm Sequenz

- Flipping durch Bilder

##### <a name="time"></a>Time

- Anzeigen von Änderungen im Zeitverlauf, im Zeitablauf und im Screencast

- In Papierkorb verschieben, rückgängig machen und wiederholen

- Wiederherstellungs Status wiederherstellen

#### <a name="attract-attention"></a>Aufmerksamkeit erregen
Wenn das Ziel darin besteht, die Aufmerksamkeit des Benutzers auf ein einzelnes Element von mehreren zu zeichnen oder den Benutzer auf aktualisierte Informationen aufmerksam zu machen, ist möglicherweise eine Animation geeignet. Beispielsweise kann Ihre Anwendungs Startseite eine Schaltfläche "erste Schritte" verwenden, die nach dem Laden der Seite nach oben verschoben wird.

Als Regel verfolgt das letzte verschiebende Element auf dem Bildschirm die Aufmerksamkeit des Benutzers.  In einer Reihe animierter Elemente folgt die Aufmerksamkeit des Benutzers dem letzten verschiebenden Objekt.

##### <a name="alert"></a>Warnung

- Benachrichtigen des Benutzers, eingreifen und Anzeigen des Fortschritts

- Anzeigen, dass etwas ordnungsgemäß oder falsch ausgeführt wird oder Fortschritt-oder Fortschritts Änderungen angezeigt werden

- Auffordern von Benutzern während einer Aufgabe, wie z. b. Online nach weiteren Informationen oder Kennenlernen der aktuellen Aufgabe

##### <a name="notifications"></a>Benachrichtigungen

- Benachrichtigen des Benutzers über einen Fehlerzustand

- Unterbrechen Sie den Benutzer, um zu sehen, ob er an einer anderen Person teilnehmen möchte.

- Benachrichtigen Sie den Benutzer sanft, dass ein Prozess abgeschlossen oder geändert wurde, z. b. Wenn ein Download abgeschlossen ist.

#### <a name="simulate"></a>Simulieren
Diese Kategorie bezieht sich auf die Physizität und Dimensionalität.

- Veranschaulichen, wo Objekte stammen oder wo Sie zu

- Erweitern und reduzieren oder öffnen und schließen

- Schwenken, scrollen und seitenumdrehungen

- Stapeln und z-Reihenfolge

- Karussell und Akkordeon

- Flippen und Rotieren der Benutzeroberfläche

#### <a name="response-and-progress-indicators"></a>Antwort-und Fortschrittsindikatoren
Status Indikatoren haben einige wichtige Vorteile:

- Sowohl bestimmte als auch unbestimmte Status Indikatoren versichern den Benutzer, dass das System nicht abgestürzt ist und an diesem Problem arbeitet.

- Determinate-Indikatoren vermitteln dem Benutzer einen Eindruck davon, wie weit die Aktion fortgeschritten ist, und das Gefühl, dass Sie näher an die Fertigstellung gelangen.

## <a name="animation-patterns"></a><a name="BKMK_AnimationPatterns"></a> Animationsmuster

### <a name="overview"></a>Übersicht
Animationen in Visual Studio dienen dazu, eine bestimmte Funktion zu verarbeiten, ohne die Benutzerproduktivität zu beeinträchtigen. Im Allgemeinen sollten Animationen in Visual Studio wie folgt lauten:

- Klein und unaufdringlich

- Natürlich und realistisch

- Geringfügige und verhaltene

- Schnell und effizient

- Gelockert, nicht eilig

Diese Abbildung zeigt die Animations Stile, die für Visual Studio empfohlen werden. Es werden keine Animationen oder feine Animationen wie das Ausblenden/ausblenden der am häufigsten verwendeten Animationen verwendet. Es gibt eine eingeschränkte Anwendung von Bewegungs Animationen wie expand und Contract, X und Y Positionsänderung und Drehung.

![Empfohlene Animationsstile für Visual Studio](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "1202-a_VSAnimStyles")<br />Empfohlene Animationsstile für Visual Studio

#### <a name="appear-and-disappear"></a>Anzeigen und ausblenden
Bei diesem Muster wechselt ein Element von Visible zu out-of-View und Back ohne Übergangs Animation.

![Animation mit dem Anschein und verschwinden](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "1202-b_AppearAndDisappear")<br />Animation mit dem Anschein und verschwinden

##### <a name="correct-usage"></a>Korrekte Verwendung
Neue Benutzeroberflächen Elemente, die sofort angezeigt oder ausgeblendet werden müssen, damit der Benutzer weder abgelenkt noch versperrt ist. Außerdem kann es vorkommen, dass langsam verschiebende Animationen als Drag & amp; Drop angesehen werden.

##### <a name="incorrect-usage"></a>Falsche Verwendung
Fälle, in denen die Benutzeroberfläche so abrupt erscheint, dass der Benutzer nicht weiß, was passiert ist, und das Hinzufügen einer Animation wäre bei der kontextbezogenen Darstellung hilfreich

##### <a name="animation-properties"></a>Animations Eigenschaften
Die Zeitverzögerung beträgt in der Regel null Sekunden.

##### <a name="examples"></a>Beispiele
- Tool Fenster automatisch ausblenden

- Tastatur aktivierte Editor-Benutzeroberfläche, wie z. b. IntelliSense und Parameter Hilfe

- Code Bereiche zum Erweitern und reduzieren

#### <a name="fade-in-and-fade-out"></a>Einblenden und ausblenden
Bei diesem Muster geht ein UI-Element von nicht sichtbar (0% Deckkraft) zu sichtbar (100% Deckkraft) oder umgekehrt.

![Einblenden und Ausblenden der Animation](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "1202-c_FadeInFadeOut")<br />Einblenden und Ausblenden der Animation

##### <a name="correct-usage"></a>Korrekte Verwendung
Dies ist die am häufigsten empfohlene Benutzeroberflächen Animation. Dies ist ein feiner Effekt, der das Interesse erhöht, ohne den Flow zu unterbrechen. In einigen Fällen erkennt der Benutzer möglicherweise nicht einmal, dass eine Animation vorhanden ist, die ein reibungsloses und fließendes UI-System wahrnimmt.

##### <a name="animation-properties"></a>Animations Eigenschaften

- Opacity wird gestartet: 0% für die Einblendung, 100% für das Ausblenden

- Endkraft: 100% für die Einblendung, 0% für das Ausblenden

- Dauer: 200 Millisekunden eigenständig, 100 Millisekunden, wenn Sie als Teil einer Kombinations Animationssequenz verwendet werden

- Beschleunigungs Stil: Sinus-INOUT

##### <a name="examples"></a>Beispiele

- Tool Fenster automatisch ausblenden

- Menü öffnen und schließen

- Hintergrund-und Vordergrund Registerkarten Übergänge

#### <a name="color-blend-from-a-to-b"></a>Farbmischung von A zu B
Bei diesem Muster ändert sich ein UI-Element von Farbe a in Farbe B.

![Farb Blend-Animation](../../extensibility/ux-guidelines/media/1202-d_colorblend.png "1202-d_ColorBlend")<br />Farb Blend-Animation

##### <a name="correct-usage"></a>Korrekte Verwendung
Als animierter Übergang, wenn ein Benutzeroberflächen Element die Farbe von einem Kontext oder Zustand in einen anderen ändert.

##### <a name="animation-properties"></a>Animations Eigenschaften

- Start Farbe: UI-spezifisch

- Endfarbe: UI-spezifisch

- Dauer: 200 Millisekunden eigenständig, 100 Millisekunden, wenn Sie als Teil einer Kombinations Animationssequenz verwendet werden

- Beschleunigungs Stil: Sinus-INOUT

##### <a name="examples"></a>Beispiele

- Statusübergänge für Dokument Fenster (aktiv, zuletzt aktiv und inaktiv)

- Statusübergänge für Tool Fenster (fokussiert und ohne Fokus)

#### <a name="expand-and-contract"></a>Erweitern und Vertrag
Bei diesem Muster wird ein Benutzeroberflächen Element in X, Y oder beide Richtungen erweitert.

![Erweitern und Vertrags Animation](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "1202-e_ExpandContract")<br />Erweitern und Vertrags Animation

##### <a name="correct-usage"></a>Korrekte Verwendung
Als animierter Übergang, wenn ein UI-Element die Größe von einem Kontext in einen anderen ändert.

##### <a name="animation-properties"></a>Animations Eigenschaften

- X-Skala:% oder bestimmte Dimension (in Pixel)

- Y-Skala:% oder bestimmte Dimension (in Pixel)

- Ankerposition: im Allgemeinen von links nach rechts (für Sprachen von links nach rechts) oder von rechts nach rechts (für Sprachen von rechts nach links)

- Dauer: 200 Millisekunden eigenständig, 100 Millisekunden, wenn Sie als Teil einer Kombinations Animationssequenz verwendet werden

##### <a name="examples"></a>Beispiele

- Architektur-Explorer-Panel erweitern und reduzieren

- Visual Studio 2017-Start Seitenelement erweitern und reduzieren

#### <a name="x-y-position-change"></a>Änderung der X-Y-Position
Bei diesem Muster ändert ein Benutzeroberflächen Element seine X-oder Y-Position oder beides.

![Animation der X-Y-Positionsänderung](../../extensibility/ux-guidelines/media/1202-f_xypositionchange.png "1202-f_XYPositionChange")<br />Animation der X-Y-Positionsänderung

##### <a name="correct-usage"></a>Korrekte Verwendung
Als animierter Übergang, wenn ein Benutzeroberflächen Element die Position von einem Kontext in einen anderen wechselt.

##### <a name="animation-properties"></a>Animations Eigenschaften

- Start X und Y-Position: UI-spezifisch

- Ende der X-und Y-Position: UI-spezifisch

- Animations Pfad: keine

- Dauer: 200 Millisekunden eigenständig, 100 Millisekunden, wenn Sie als Teil einer Kombinations Animationssequenz verwendet werden

- Beschleunigungs Stil: Sinus-INOUT

##### <a name="example"></a>Beispiel
Neuanordnen von Registerkarten

#### <a name="rotate"></a>Rotate
Bei diesem Muster wird das UI-Element rotiert.

![Animation der UI-Element Rotation](../../extensibility/ux-guidelines/media/1202-g_rotate.png "1202-g_Rotate")<br />Animation der UI-Element Rotation

##### <a name="correct-usage"></a>Korrekte Verwendung
Nur für den Status Indikator "unbestimmtes drehen".

##### <a name="animation-properties"></a>Animations Eigenschaften

- Grad der Drehung: 360

- Dreh Mittelpunkt: Mitte des Objekts

- Dauer: kontinuierlich

##### <a name="example"></a>Beispiel
Unbestimmtes Status Indikator (spinvorgänge)

### <a name="common-shell-ui-actions-and-recommended-animations"></a>Allgemeine shellbenutzeroberflächenaktionen und empfohlene Animationen

#### <a name="tab-open"></a>Registerkarte geöffnet
![Animation mit geöffneten Registerkarten](../../extensibility/ux-guidelines/media/1202-h_tabopen.png "1202-h_TabOpen")<br />Animation mit geöffneten Registerkarten

- Stil: wird angezeigt

- Dauer: null Sekunden

#### <a name="tab-close"></a>Tab schließen
![Animation "Tab schließen"](../../extensibility/ux-guidelines/media/1202-i_tabclose.png "1202-i_TabClose")<br />Animation "Tab schließen"

- Stil: X-Positionsänderung

- Dauer: 200 Millisekunden

#### <a name="tab-reorder"></a>Neuanordnen von Registerkarten
![Animation "Neu anordnen" in Visual Studio](../../extensibility/ux-guidelines/media/1202-j_tabreorder.png "1202-j_TabReorder")<br />Animation zur Neuanordnung von Registerkarten

- Stil: X-Positionsänderung

- Dauer: 200 Millisekunden

#### <a name="close-floating-document"></a>Unverankerte Dokumente schließen
![Animation für unverankerte Dokumente schließen](../../extensibility/ux-guidelines/media/1202-k_closefloatingdocument.png "1202-k_CloseFloatingDocument")<br />Animation für unverankerte Dokumente schließen

- Stil: wird angezeigt

- Dauer: 200 Millisekunden

#### <a name="window-state-transition"></a>Fenster Zustandsübergang
![Animation des Fenster Zustands Übergangs](../../extensibility/ux-guidelines/media/1202-l_windowstatetransition.png "1202-l_WindowStateTransition")<br />Animation des Fenster Zustands Übergangs

- Stil: um mit anderen Fenstern konsistent zu sein, lassen Sie das aktuelle Betriebssystem die Animation close Animation definieren.

- Dauer: 200 Millisekunden

#### <a name="menu-open"></a>Menü geöffnet
![Animation "Menü öffnen"](../../extensibility/ux-guidelines/media/1202-m_menuopen.png "1202-m_MenuOpen")<br />Animation "Menü öffnen"

- Stil: einblenden

- Dauer: 200 Millisekunden

#### <a name="menu-close"></a>Menü schließen
![Animation zum Schließen des Menüs](../../extensibility/ux-guidelines/media/1202-n_menuclose.png "1202-n_MenuClose")<br />Animation zum Schließen des Menüs

- Stil: Ausblenden

- Dauer: 200 Millisekunden

#### <a name="auto-hide-tool-window-reveal"></a>Tool Fenster automatisch ausblenden
![Tool Fenster automatisch ausblenden: Animation anzeigen](../../extensibility/ux-guidelines/media/1202-o_autohidetoolwindowreveal.png "1202-o_AutoHideToolWindowReveal")<br />Tool Fenster automatisch ausblenden: Animation anzeigen

- Stil: wird angezeigt

- Dauer: null Sekunden
