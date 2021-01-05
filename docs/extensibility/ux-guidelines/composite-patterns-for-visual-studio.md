---
title: Zusammengesetzte Muster für Visual Studio | Microsoft-Dokumentation
description: Erfahren Sie mehr über wichtige zusammengesetzte Muster für Konsistenz in Visual Studio. Zusammengesetzte Muster kombinieren Interaktions-und Entwurfs Elemente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e48ecfb2-f4b5-4d3a-b4a2-7a4d62fa4ec0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 719ce0ac88761599fbed7da90643fd8a9d79db69
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715820"
---
# <a name="composite-patterns-for-visual-studio"></a>Zusammengesetzte Muster für Visual Studio
Zusammengesetzte Muster kombinieren Interaktions-und Entwurfs Elemente in unterschiedlichen Konfigurationen. Zu den wichtigsten zusammengesetzten Mustern in Visual Studio in Bezug auf die Konsistenz gehören:

- [Datenvisualisierung](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_DataVisualization)

- [On-Object-Benutzeroberfläche und Peer](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

- [Auswahl Modelle](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

- [Persistenz und Speichern von Einstellungen](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

- [Fingereingabe](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)

## <a name="data-visualization"></a><a name="BKMK_DataVisualization"></a> Datenvisualisierung

### <a name="overview"></a>Übersicht
 Diagramme sind eine visuelle Methode zum Aggregieren und Visualisieren von Daten, um die Entscheidungsfindung zu verbessern. Sie können Benutzer bei vielen Daten unterstützen, aber es kann nur wenig gemeint sein, was zu tun hat und was eine Aktion erfordern könnte.

 Der Benutzer profitiert von einem Diagramm, wenn eine der folgenden Bedingungen zutrifft:

- Soll das Diagramm Benutzern helfen, Aufgaben zu identifizieren, auf die Sie reagieren können?

- Ermöglicht das Diagramm Benutzern das Vorhersagen von möglichen Änderungen?

- Soll das Diagramm Benutzern helfen, Trends zu erkennen und Muster zu identifizieren?

- Ermöglicht das Diagramm Benutzern, bessere Entscheidungen zu treffen?

- Hilft das Diagramm dabei, eine bestimmte Frage zu beantworten, die Benutzer im angegebenen Kontext haben können?

#### <a name="general-rules-for-charts"></a>Allgemeine Regeln für Diagramme

- Daten eindeutig bezeichnen. Abbildungen ohne Erklärung sind nur schöne Bilder.

- Starten Sie Achsen bei Null, um verzerrte Proportionen zu vermeiden. Zeilenlänge und Balken Größe sind wichtige visuelle Hinweise zum Verständnis der Beziehungen zwischen Datenpunkten.

- Erstellen Sie Diagramme, nicht infographics. Infographics sind Kunst Darstellungen von Daten, und Ihr Hauptziel ist das visuelle Storytelling. Diagramme können (und sollten) visuell ansprechend sein, aber lassen Sie die Daten für sich selbst sprechen.

- Vermeiden Sie Schrägen, schrägen Balkendiagrammen, Kontrast-Hashmarkierungen und andere Infografik-Berührungen.

- Verwenden Sie 3D-Effekte nicht als dekoratives Element. Verwenden Sie Sie nur, wenn Sie für die Fähigkeit des Benutzers, die Informationen zu verstehen, wirklich von Bedeutung sind.

- Vermeiden Sie die Verwendung mehrerer Zeilen und Füllungen, da diese Art von Diagramm durch mehr als zwei Farben schwer lesbar und ordnungsgemäß interpretiert werden kann.

- Verwenden Sie kein Diagramm (oder eine beliebige Abbildung) als alleinige Methode zum Verständnis eines Konzepts oder zum interagieren mit Daten. Dies stellt Probleme für Benutzer mit Sehbehinderungen dar.

- Verwenden Sie keine Diagramme als kostenlose oder dekorative Elemente auf einer Seite. Anders ausgedrückt: Wenn ein Diagramm keinen Wert hinzufügt oder Benutzern hilft, ein Problem zu lösen, sollten Sie es nicht verwenden.

### <a name="chart-types"></a>Diagrammtypen
 Zu den in Visual Studio verwendeten Diagrammtypen gehören Balkendiagramme, Liniendiagramme, ein geändertes Kreis Diagramm, das als Ring Diagramm oder "Ring Diagramm", Zeitachsen, Punkt Diagramme (auch als "Cluster Diagramme" bezeichnet) und Gantt-Diagramme bezeichnet werden. Jeder Diagrammtyp eignet sich für die Kommunikation mit anderen Arten von Informationen.

### <a name="other-charting-considerations"></a>Weitere Überlegungen zu Diagramm

#### <a name="color"></a>Farbe
 Es gibt eine bestimmte Palette von Diagramm Farben, die für die Verwendung in Visual Studio definiert sind. Die Palette ist für die Haupttypen der Farbblindheit zugänglich, und die Farben können auch dann unterschieden werden, wenn Sie als sehr schmale Farb Scheiben verwendet werden. Sie können diese Farben in beliebiger Kombination für beliebige Diagramm-oder Diagrammtypen in der Benutzeroberfläche verwenden. Sie müssen nicht alle sieben Farben verwenden, wenn Sie nicht die vielen unterschiedlichen Farben benötigen. Diese Farben wurden nicht für die Verwendung mit beliebigen Vordergrund Elementen entworfen. Platzieren Sie Text oder Symbole nicht oberhalb dieser Farben. Diese Farbtöne sollten hart codiert und für die Benutzeranpassung unter Extras **> Optionen** verfügbar gemacht werden (siehe verfügbar machen [von Farben für Endbenutzer](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)).

|Muster|Hex|RGB|
|------------|---------|---------|
|![Farbmuster 71B252](../../extensibility/ux-guidelines/media/0711_71b252.png "0711_71B252")|#71B252|113178, 82|
|![Farbmuster BF3F00](../../extensibility/ux-guidelines/media/0711_bf3f00.png "0711_BF3F00")|#BF3F00|191, 63, 0|
|![Farbmuster FCB714](../../extensibility/ux-guidelines/media/0711_fcb714.png "0711_FCB714")|#FCB714|252183, 20|
|![Farbmuster 903F8B](../../extensibility/ux-guidelines/media/0711_903f8b.png "0711_903F8B")|#903F8B|144, 63139|
|![Farbmuster 117AD1](../../extensibility/ux-guidelines/media/0711_117ad1.png "0711_117AD1")|#117AD1|17.122.209|
|![Farbmuster 79D7F2](../../extensibility/ux-guidelines/media/0711_79d7f2.png "0711_79D7F2")|#79D7F2|121.215.242|
|![Farbmuster B5B5B5](../../extensibility/ux-guidelines/media/0711_b5b5b5.png "0711_B5B5B5")|#B5B5B5|181.181.181|

## <a name="on-object-ui-and-peeking"></a><a name="BKMK_OnObjectUI"></a> On-Object-Benutzeroberfläche und Peer
 In diesem Abschnitt erhalten Sie einen Kontext für peeking, auch bekannt als Code Peek-Sicht, eine Art von Benutzeroberfläche, die für Visual Studio eindeutig ist.

### <a name="overview"></a>Übersicht

- Die Benutzeroberfläche auf dem Objekt sollte dem Benutzer mehr Informationen oder Interaktivität zur Verfügung gestellt werden, ohne die Hauptaufgabe zu beeinträchtigen.

- Das Hauptmuster für die Benutzeroberfläche auf dem Objekt in Visual Studio wird als "Informationen zum Zeitpunkt der Aufmerksamkeit" bezeichnet.

- Die on-Object-Benutzeroberfläche in Visual Studio ist entweder Inline oder Gleit Komma und entweder dauerhaft oder vorübergehend.

  - Code Peek-Sicht, eine Art von Objekt-Benutzeroberfläche in Visual Studio, ist Inline und dauerhaft.

  - Codelta ens, ein Typ der on-Object-Benutzeroberfläche in Visual Studio, ist unverankert und vorübergehend

  Wenn Sie wissen, wie ein Code Ausschnitt funktioniert, oder wenn Sie Details zu diesem Code finden, ist es oft erforderlich, dass ein Entwickler den Kontext wechselt und zu anderem Inhalt oder einem anderen Fenster wechselt. Diese Kontext Verschiebungen können Unterbrechungen aufweisen, da Benutzer den Fokus auf Ihre ursprüngliche Aufgabe verlieren können, wenn Sie Ihr Hauptfenster verlassen. Außerdem kann es schwierig sein, diesen ursprünglichen Kontext wieder zu machen, insbesondere wenn das Wechseln von Fenstern dazu geführt hat, dass der ursprüngliche Code von einer anderen Benutzeroberfläche verdeckt wird.

  Die on-Object-Benutzeroberfläche folgt einem Muster mit dem Namen "Informationen zum Zeitpunkt der Aufmerksamkeit". Mithilfe dieser Meldungen, Popup Fenster und Dialogfelder erhalten Benutzer zusätzliche, relevante Informationen, die eine Erläuterung oder Interaktivität hinzufügen, ohne den Fokus auf Ihre Hauptaufgabe zu verlieren. Beispiele für die Benutzeroberfläche auf dem Objekt sind Popup Fenster, die angezeigt werden, wenn ein Benutzer mit dem Mauszeiger auf ein Symbol im Benachrichtigungsbereich bewegt wird, die rote Wellenlinie unter einem falsch geschriebenen Wort und die in Visual Studio 2013 eingeführte Peek-Ansicht.

### <a name="decision-points"></a>Entscheidungspunkte
 In Visual Studio gibt es mehrere Möglichkeiten, dieses Muster von Informationen zum Zeitpunkt der Aufmerksamkeit zu verwenden. Die Auswahl des richtigen Mechanismus und die Implementierung in einer konsistenten, vorhersehbaren Weise ist für die gesamte Leistung von entscheidender Bedeutung. Andernfalls kann es vorkommen, dass Benutzern eine verwirrende oder inkonsistente Benutzerfunktion angezeigt wird, die den Fokus von dem eigentlichen Inhalt beeinträchtigt.

#### <a name="relationships-between-master-and-detail-content"></a>Beziehungen zwischen Master-und Detail Inhalt
 Die Informationen zum Zeitpunkt der Betrachtung werden verwendet, um eine Beziehung zwischen dem Inhalt, auf den der Benutzer fokussiert ist (der "Master"-Inhalt), und zusätzlichen verwandten Inhalten (dem "Detail"-Inhalt) anzuzeigen. In diesem Muster ist der Detail Inhalt eindeutig mit dem Inhalt verknüpft, mit dem der Benutzer arbeitet. er kann in der Nähe des Master Inhalts angezeigt werden. Ergänzende Informationen oder Informationen, die nicht zusammengefasst werden können, ohne den Master Inhalt zu überstehen, sollten einem anderen Muster folgen, z. b. einem Tool Fenster.

- Zeigen Sie den Detail Inhalt **immer** in unmittelbarer Nähe zum Master Inhalt an.

- Stellen Sie **immer** sicher, dass der Detail Inhalt den Benutzern weiterhin den Fokus auf dem Master Inhalt ermöglicht. Die beste Möglichkeit, dies zu erreichen, besteht häufig darin, den Detail Inhalt so nah wie möglich am Master Inhalt zu gestalten. Hierzu können Sie den Detail Inhalt in einem Popup Fenster neben dem Master Inhalt rendern oder den Detail Inhalt Inline unterhalb des Master Inhalts rendern.

- Verwenden Sie **niemals** die Informationen zu dem Zeitpunkt, an dem der Benutzer den Master Inhalt entfernt hat. Wenn Benutzer den Detail Inhalt separat anzeigen müssen, machen Sie eine explizite Aktion verfügbar, die dem Benutzer ermöglicht, dies zu tun.

#### <a name="design-details"></a>Entwurfs Details
 Nachdem Sie festgestellt haben, dass die Benutzeroberfläche auf dem Objekt die richtige Wahl ist, gibt es vier wichtige Entwurfs Überlegungen:

1. **Persistenz:** wird erwartet, dass der Inhalt dauerhaft oder vorübergehend ist?
   Möchten Benutzer die Informationen sichtbar machen, um auf Sie zu verweisen oder mit Ihnen zu interagieren? Oder sollen die Benutzer schnell einen Blick auf die Informationen haben und dann mit der Hauptaufgabe fortfahren?

2. **Inhaltstyp:** ist der Inhalt Informations-, Handlungs-oder Navigations bedingt?
   Benötigt der Benutzer zusätzliche Details zum Master Inhalt? Muss der Benutzer eine Aufgabe ausführen, die sich auf den Master Inhalt auswirkt? Oder muss der Benutzer an eine andere Ressource weitergeleitet werden?

3. **Indikatortyp:** ist ein Umgebungs Indikator sinnvoll?
   Können die Informationen auf nützliche Weise zusammengefasst werden, ohne den Master Inhalt zu überfordern?

4. **Gesten:** welche Gesten werden verwendet, um die Benutzeroberfläche aufzurufen und zu verwerfen?
   Wie wird der Benutzer den Detail Inhalt anzeigen und ihn dann Absenden? Gibt es einen Wert für das Hinzufügen einer Geste, wie z. b. das anheten zum Wechseln zwischen vorübergehenden und permanenten Zuständen

   Jeder dieser vier Entscheidungspunkte wirkt sich auf die Hauptkomponenten der Benutzeroberfläche auf dem-Objekt aus.

### <a name="on-object-ui-components"></a>On-Object-UI-Komponenten

1. Typ des Containers (Content Presenter)

    - Gleitkomma

    - Inline

2. Inhaltstyp

    - Information: statische oder dynamische Daten

    - Handlungsfähig: Befehle, die den Master Inhalt ändern

    - Navigation: Links, die den Benutzer zu einem anderen Fenster oder einer anderen Anwendung, z. b. MSDN, machen

3. Gesten

    - Aufruf

    - Bestätigen

    - Anheften

    - Andere Interaktionen

4. Persistenz-und Commit-Modell

    - Transient (vorübergehend)

    - Durable

    - Automatic

    - Bei Bedarf

5. Umgebungs Indikatoren (optional)

    - Wellenlinie unterstrichen

    - Smarttagsymbol

    - Weitere Umgebungs Indikatoren

#### <a name="container-content-presenter-type"></a>Typ des Containers (Content Presenter)
 Es stehen zwei Hauptoptionen zur Verfügung, mit denen Sie Inhalte zum Zeitpunkt der Aufmerksamkeit präsentieren können:

1. **Inline:** ein Inline Presenter, wie z. b. die Peek-Ansicht, die im Visual Studio 2013 Code-Editor eingeführt wurde, ermöglicht neuen Inhalt durch Verschieben von vorhandenem Inhalt.

    - **Bevorzugen** Sie Inline-Moderatoren, wenn Sie erwarten, dass Benutzer einen beträchtlichen Zeitraum aufwenden möchten, der sich auf den vorhandenen Inhalt bezieht oder mit ihm interagiert.

    - **Vermeiden** Sie die Verwendung von Inline-Moderatoren, wenn Sie erwarten, dass Benutzer die Informationen, die Sie präsentieren, anzeigen und dann mit der Hauptaufgabe mit minimaler Unterbrechung fortfahren.

2. **Floating:** ein unverankerter Presenter wird so nah wie möglich am ausgewählten Inhalt positioniert, aber das Layout des vorhandenen Inhalts wird nicht geändert. Es können verschiedene Strategien eingesetzt werden, z. b. das Anzeigen eines Gleit Komma Inhalts Bereichs über dem nächstliegenden Leerraum für das ausgewählte Symbol.

    - **Bevorzugen** Sie unverankerte Presenter, wenn Sie erwarten, dass Benutzer die Informationen, die Sie präsentieren, anzeigen möchten, und fahren Sie mit der Hauptaufgabe mit minimaler Unterbrechung fort.

    - **Vermeiden** Sie unverankerte Presenter, wenn Sie erwarten, dass Benutzer einen beträchtlichen Zeitraum aufwenden möchten, der sich auf den vorhandenen Inhalt bezieht oder mit ihm interagiert.

#### <a name="content-type"></a>Inhaltstyp
 Es gibt drei Haupttypen von Inhalten, die in jedem Benutzeroberflächen Container von Objekten angezeigt werden können. Eine beliebige Kombination dieser Informationstypen kann angezeigt werden. Die drei Typen lauten wie folgt:

1. **Information:** die meisten auf dem Objekt basierenden UI-Container zeigen eine Art von Informationsinhalten an. Der Inhalt kann Informationen zum aktuellen Zustand der Umgebung darstellen, oder er kann Informationen über einen potenziellen zukünftigen Zustand der Umgebung darstellen. Beispielsweise könnte Sie verwendet werden, um die Auswirkung eines bestimmten Befehls, z. b. ein Refactoring, auf den vorhandenen Code anzuzeigen.

    - Verwenden Sie **immer** die kanonische Darstellung der Informationen, die Sie anzeigen. Code sollte z. b. wie Code aussehen, mit Syntax Hervorhebung vollständig Aussehen und die vom Benutzer festgelegte Schriftart und andere Umgebungseinstellungen berücksichtigen.

    - Es empfiehlt sich **immer** , Aktionen über den Informationsinhalt zu unterstützen, die möglich wären, wenn die gleichen Informationen als Master Inhalt angezeigt werden. Wenn Sie z. b. vorhandenen Code in einem Benutzeroberflächen Container für ein Objekt darstellen, sollten Sie unbedingt die Möglichkeit zum Durchsuchen und Ändern des Codes unterstützen.

    - Verwenden Sie **immer** eine andere Hintergrundfarbe, wenn Sie Informationsinhalte präsentieren, die einen potenziellen zukünftigen Zustand darstellen.

2. Umsetzbare Elemente: einige Benutzeroberflächen Container von Objekten bieten die Möglichkeit, Aktionen über den Master Inhalt auszuführen, z. b. durch das Ausführen eines Umgestaltungs Vorgangs.

    - Positionieren Sie Aktions fähige Befehle **immer** separat vom Informationsinhalt.

    - Aktivieren und deaktivieren Sie Aktionen gegebenenfalls **immer** .

    - Lesen Sie **stets** die Standardrichtlinien für das darstellen von Befehlen in Dialogfeldern.

    - **Behalten Sie** die Anzahl der Aktionen, die in einem Objekt für die Benutzeroberfläche von Objekten verfügbar gemacht werden, auf einem absoluten Minimalwert. Die Interaktion mit der Benutzeroberfläche auf dem Objekt sollte eine leichte, schnelle Oberfläche sein. Der Benutzer sollte keine Energie für die Verwaltung des Objekts für die Benutzeroberfläche von Objekten selbst aufwenden müssen.

    - Beachten Sie **immer** , wie und wann ein Objekt-UI-Container geschlossen oder verworfen wird. Eine bewährte Vorgehensweise besteht darin, dass jede Aktion, die den Dialog zwischen dem Master-und dem Detail Inhalt abschließt, auch den Benutzeroberflächen Container auf dem Objekt schließen sollte, wenn diese Aktion aufgerufen wird.

3. Navigation **:** einige Benutzeroberflächen Container von Objekten enthalten Links, die den Benutzer zu einem anderen Fenster oder einer anderen Anwendung machen, z. b. Öffnen eines MSDN-Artikels im Webbrowser des Benutzers.

    - Stellen Sie **immer** eine beliebige Navigations Verknüpfung mit "Open" voran, damit Benutzer nicht überrascht werden, wenn Sie zu einem anderen Inhalt navigiert werden.

    - Trennen Sie **immer** Navigationslinks von handlungsfähigen Links.

#### <a name="ambient-indicators-optional"></a>Umgebungs Indikatoren (optional)
 Umgebungs Indikatoren können sehr fein sein, z. b. Text, der aus dem restlichen Code in einer Kontrastfarbe dargestellt wird, oder offensichtlich, einschließlich Tickersymbolen wie Wellenlinien und smarttagsymbole. Umgebungs Indikatoren vermitteln die Verfügbarkeit zusätzlicher, relevanter Informationen. Im Idealfall bieten Sie nützliche Informationen, auch wenn der Benutzer nicht mit ihnen interagieren muss.

- Positionieren Sie **immer** einen Umgebungs Indikator, sodass er den Benutzer nicht ablenkt oder überlastet. Wenn es nicht möglich ist, einen Umgebungs Indikator in einer solchen Weise zu positionieren, sollten Sie eine andere Lösung in Erwägung gezogen.

- Positionieren Sie den Umgebungs Indikator **immer** so nah wie möglich an dem Inhalt, mit dem er verknüpft ist.

- Versuchen Sie **immer** , einen Indikator zu erstellen, der die verfügbaren Informationen zusammenfasst. Geben Sie ggf. die Anzahl der verfügbaren Datenelemente an (z. b. "3 Verweise" anstatt einfach "Verweise"), oder stellen Sie sich eine andere Möglichkeit vor, die Daten zusammenzufassen.

  - In Fällen, in denen die Daten für einen Indikator nicht immer berechnet und angezeigt werden können, sollten Sie beim Berechnen der Werte sofort progressives Feedback bereitstellen. Sie können z. b. Änderungen animieren, die Aktualisierungen der verfügbaren Daten widerspiegeln, ähnlich der Art, wie die e-Mail-Live-Kachel auf Windows Phone aktualisiert wird, wenn die Anzahl der ungelesenen e-Mails zunimmt.

- Fügen Sie **niemals** mehr Indikatoren hinzu, als ein Benutzer für einen bestimmten Teil des Inhalts Zutun kann. Umgebungs Indikatoren sollten nützlich sein, ohne dass eine Interaktion mit dem Benutzer erforderlich ist. Indikatoren verlieren ihr Ambiente, wenn Sie über einen Überlauf und andere Verwaltungs Steuerungen verfügen, die Sie in die Ansicht bringen müssen.

#### <a name="gestures"></a>Gesten
 Ein wichtiger Aspekt, der es dem Benutzer ermöglicht, den Fokus auf den Master Inhalt aufrechtzuerhalten, besteht darin, die richtigen Gesten zum Öffnen und verwerfen der zusätzlichen Detail Inhalte zu unterstützen.

- Verlangen Sie **immer** , dass der Benutzer eine explizite Geste ausführt, um den zusätzlichen Inhalt zu öffnen. Häufige offene Gesten sind:

  - **Hover:** Quick Infos oder nicht interaktiver Informationsinhalt

  - **Expliziter Befehl:** Inline Presenter

  - **Doppelklicken Sie auf den Umgebungs Indikator:** Codelta ens-Popup Fenster

- Verwerfen Sie **immer** den Detail Inhalt, wenn der Benutzer die ESC-Taste drückt.

- Denken Sie **immer** an den Kontext der Benutzeroberfläche auf dem Objekt. Bei Inhalts Referenten, die eine Interaktion innerhalb des Containers ermöglichen, sollten Sie sorgfältig überlegen, ob zusätzliche Informationen zu Hover angezeigt werden sollen, was für den Workflow des Benutzers wahrscheinlich unterbrochen wird.

- Zeigen Sie **niemals** Inhalt auf dem Mauszeiger an, der bearbeitbar oder Benutzerinteraktion ist. Dieses Verhalten kann die Benutzer beeinträchtigen, wenn Sie versuchen, den Cursor über den Detail Inhalt zu bewegen, da das Standardverhalten für eine QuickInfo sofort geschlossen werden soll, wenn sich der Cursor nicht mehr über dem Master Inhalt befindet, der ihn erzeugt hat.

## <a name="selection-models"></a><a name="BKMK_SelectionModels"></a> Auswahl Modelle

### <a name="overview"></a>Übersicht
 Ein Auswahl Modell ist der Mechanismus, der verwendet wird, um Vorgänge für ein oder mehrere Objekte anzuzeigen und zu bestätigen, die in der Benutzeroberfläche von Interesse sind. In diesem Thema werden die Interaktionsmuster der Auswahl in Visual Studio-Dokument-Editoren erläutert: Text-Editoren, Entwurfs Oberflächen und Modellierungs Oberflächen.

 Benutzer müssen eine Möglichkeit haben, Visual Studio mitzuteilen, woran Sie arbeiten, und Visual Studio muss vorhersagbares Feedback an Benutzer über das, was Sie läuft, beantworten. Unterschiede oder eine Fehlkommunikation zwischen dem Benutzer und der Benutzeroberfläche können dazu führen, dass der Benutzer keine Aktion bemerkt, was unbeabsichtigte Folgen haben kann. Der Fehler wird häufig so lange unbemerkt, bis dem Benutzer angezeigt wird, dass etwas fehlt oder geändert wurde. Auswahl Modelle sind daher eine der kritischsten Teile des Entwurfs von Benutzeroberflächen. Obwohl Auswahl Modelle in Visual Studio mit Windows konsistent sind, gibt es geringfügige Abweichungen.

 In Visual Studio unterscheiden sich die Auswahl Modelle je nach Kontext, in dem die Interaktion stattfindet. Die Auswahl kann in vier Typen von Objekten erfolgen:

- Text

- Grafikobjekte

- Listen und Strukturen

- Raster

  Innerhalb dieser Objekte gibt es drei Arten von Auswahlmöglichkeiten:

- Zusammenhängenden

- Zusammenhang losen

- Region

#### <a name="scope"></a>`Scope`
 Die wichtigste Komponente der Auswahl ist die Sicherstellung, dass der Benutzer weiß, in welchem Fenster Sie arbeiten (Aktivierung) und wo sich der Fokus befindet (Auswahl). Visual Studio erweitert die Fenster Verwaltungsfunktionen in Windows, das Aktivierungs Schema ist jedoch identisch: bei der Interaktion mit einem Fenster wird der Fokus auf das Fenster erweitert. Visual Studio verfügt über zwei Indikatoren für die Aktivierung: einen für Dokument Fenster und einen für Tool Fenster.

 Für Dokument Fenster wird das aktive Fenster durch eine Registerkarte des Dokument Fensters angezeigt, die sich im Vordergrund befindet und seine Hintergrundfarbe ändert:

 ![Aktive Registerkartenauswahl in Visual Studio](../../extensibility/ux-guidelines/media/0713-01_activetab.png "0713-01_ActiveTab")

 **Aktive Registerkarten Auswahl**

 Für Tool Fenster wird das aktive Fenster durch eine Änderung der Farbe für den Titelleisten Bereich des Tool Fensters angezeigt:

 ![Aktive Toolfensterauswahl in Visual Studio](../../extensibility/ux-guidelines/media/0713-02_activetoolwindow.png "0713-02_ActiveToolWindow")

 **Aktives Tool Fenster, das die primäre Auswahl eines Knotens anzeigt**

 ![Inaktive Toolfensterauswahl in Visual Studio](../../extensibility/ux-guidelines/media/0713-03_inactivetoolwindow.png "0713-03_InactiveToolWindow")

 **Inaktives Tool Fenster, das die latente Auswahl des Knotens anzeigt**

 Sobald ein Fenster aktiv ist, wird der Fokus gemäß den Auswahl Modellen angezeigt, die in diesem Abschnitt der Richtlinien beschrieben werden.

#### <a name="context"></a>Kontext
 Visual Studio wurde entwickelt, um ein starkes Konzept des Kontexts beizubehalten und zu verfolgen, wo der Benutzer arbeitet. Es ist nur ein Fenster aktiv, unabhängig davon, ob es sich um ein Tool-oder Dokument Fenster handelt. Das oberste Dokument Fenster behält jedoch immer eine latente Auswahl bei. Obwohl der Fokus möglicherweise in einem Tool Fenster liegt, wird im Dokument Fenster, das zuletzt aktiv war, eine Auswahl angezeigt, auch wenn der Status inaktiv ist. Dadurch wird der Kontext des Benutzers in dem Dokument beibehalten, das bearbeitet wurde, und es wird angezeigt, dass Visual Studio seinen Zustand beibehalten hat, damit Sie sich nahtlos zwischen Tool Fenstern und Dokument Fenstern bewegen und wechseln können.

### <a name="text-selection"></a>Markieren von Text
 Visual Studio-Editoren, die streng Text sind, wie z. b. der integrierte Text-Editor, verwenden dasselbe Textauswahl Modell und die gleiche Darstellung, die auf der Seite [Maus und Zeiger](/windows/desktop/uxguide/inter-mouse) der Windows-Benutzeroberflächen-Interaktions Richtlinien auf MSDN beschrieben werden. Der Eingabefokus im Text-Editor wird durch einen senkrechten Strich, der als Einfügemarke bezeichnet wird, angegeben. Die Einfügemarke ist ein einzelnes Pixel, das als umgekehrter Wert dargestellt wird. Der Wert wird gemäß der Rate festgelegt **, die in** der Systemsteuerung auf der Registerkarte **Geschwindigkeit** des **Tastatur** -Applets festgelegt ist.

#### <a name="contiguous-and-disjoint-selection"></a>Zusammenhängende und nicht zusammenhängende Auswahl
 Die Auswahl im Text-Editor ist nur zusammenhängend. Nicht zusammenhängende Text Auswahlen sind nicht zulässig, sollten jedoch in grafischen Objekt-Editoren adressiert werden. Wenn sich der Mauszeiger des Benutzers über einem Textbereich befindet, wird der Cursor in einen I-Beam geändert. Bei einem Mausklick wird die Einfügemarke im Text-Editor an der Position des Links angezeigt. Wenn die Maustaste gedrückt wird, wird eine Auswahl hervorgehoben. Wenn Sie die Maustaste loslassen, wird die Auswahl Markierung beendet.

#### <a name="region-selection-box-selection"></a>Regions Auswahl (Feldauswahl)
 Visual Studio unterstützt die Auswahl von Regionen im Text-Editor. Dies wird als Feldauswahl bezeichnet. Mithilfe der Feldauswahl kann der Benutzer einen Textbereich auswählen, der nicht dem regulären Textstream folgt. Wie bei der standardmäßigen Textauswahl muss die Auswahl zusammenhängend sein. Die Feldauswahl wird initiiert, indem Sie die Alt-Taste gedrückt halten, während Sie mit der Maus ziehen. Die Feldauswahl kann auch initiiert werden, indem Sie die Alt-Taste und die UMSCHALTTASTE gedrückt halten, während Sie die Pfeiltasten verwenden, um den Bereich der Auswahl anzugeben. Bei der Feldauswahl wird die normale Auswahl Markierung verwendet, und der Cursor für die Einfügemarke wird am Ende des Auswahl Bereichs blinkt angezeigt.

 ![Regionale &#40;Feld&#41; Auswahl in Visual Studio](../../extensibility/ux-guidelines/media/0713-04_boxselection.png "0713-04_BoxSelection")

 **Auswahl der Region (Box) in Visual Studio**

#### <a name="text-selection-appearance"></a>Darstellung der Text Auswahl
 Die Farben, die für die aktive und inaktive Auswahl im Editor verwendet werden, können angepasst werden. Zum Anpassen der visuellen Darstellung des Editors kann ein Benutzer zu den **Tools > Optionen** wechseln und dann unter **Umgebung > Schriftarten und Farben > Text-Editor** suchen.

### <a name="graphical-selection"></a>Grafische Auswahl

#### <a name="interaction"></a>Interaktion
 Die grafische Objektauswahl kann komplex sein und hängt von einer Reihe von Faktoren ab:

- **Das primäre Auswahl Modell des Editors.** Editoren mit grafischen Objekten können auch zum Bearbeiten von Text oder Raster verwendet werden. Der Editor kann z. b. ein textbasierter Editor sein, der auch die Platzierung von grafischen Objekten unterstützt, z. b. den Visual Studio XAML-Designer. Die Unterstützung mehrerer Objekttypen kann Einfluss darauf haben, wie der Benutzergruppen auswählt, die aus unterschiedlichen Objekttypen besteht.

- **Unterstützung für primäre und sekundäre Auswahl Zustände.** Ein Editor kann einen primären und sekundären Auswahl Status bereitstellen, sodass Objekte in Unison bearbeitet, aufeinander abgestimmt, geändert und so weiter angepasst werden können.

- **Direkte Bearbeitungs Unterstützung.** Editoren können auch den Inhalt ihrer grafischen Objekte bearbeiten. Eine Rechteck Form kann z. b. auch Text im Inneren enthalten, der vom Benutzer geändert werden kann. Außerdem kann dieser Text zentriert oder bündig sein. Die direkte Bearbeitung umfasst eine ausführlichere Ebene der Benutzerinteraktion und erfordert daher einen geeigneten Satz visueller Hinweise, um dem Benutzer Zustandsinformationen zu präsentieren.

#### <a name="mouse-interaction"></a>Maus Interaktion

|Eingabe|Ergebnis|
|-----------|------------|
|Klicken Sie auf ein nicht ausgewähltes Objekt|Wählt das-Objekt aus und zeigt eine gestrichelte Linie und Auswahl Handles an, wenn die Größe des Objekts geändert werden kann.|
|Klicken Sie auf ein ausgewähltes Objekt|Aktiviert die direkte Bearbeitung, wenn das Objekt dies unterstützt. Wenn Sie außerhalb des Objekts klicken, wird der direkte Bearbeitungsmodus deaktiviert.|
|Doppelklicken Sie auf ein Objekt.|Öffnet den Code hinter dem-Objekt zur Bearbeitung und fügt ggf. ggf. einen Standard Ereignishandler ein.|
|Zeigen Sie auf ein Objekt.|Ändert den Zeiger auf den Verschiebe Cursor. Die Darstellung des Objekts, z. b. seine Helligkeit oder Farbe, kann sich ändern.|
|Auf ein Auswahl Handle zeigen|Ändert den Zeiger auf den Cursor zum Ändern der Größe. Bei Objekten, die die Rotation unterstützen, können einige Auswahl Handles den Zeiger auf einen drehenden Cursor ändern, da der Zeiger anders positioniert ist (z. b. weiter entfernt), was auf das Auswahl Handle folgt.|
|Ziehen|Auch wenn das-Objekt nicht zuvor ausgewählt ist, wird der Zeiger auf den Verschiebe Cursor geändert und das-Objekt verschoben.|
|Editor verliert den Fokus|Deaktiviert den direkten Bearbeitungsmodus, obwohl das-Objekt den Inhalt und die Darstellung während des letzten Vorgangs/Auswahl Zustands beibehält.|
|Objektauswahl|Wird durch einen Rahmen, eine gepunktete Linie oder eine andere visuell getrennte Behandlung angezeigt, um die Grenze des Objekts hervorzuheben.|
|Ändern der Größe eines ausgewählten Objekts|Wird durch Auswahl Handles angegeben.<br /><br /> Ein Objekt, dessen Größe geändert werden kann, verfügt über acht Handles, die jede Richtung darstellen, in der die Größe geändert werden kann. Es können weniger Handles verwendet werden, wenn die Größe des Objekts nur in bestimmten Richtungen geändert werden kann. Wenn der Benutzer ein Objekt mit einer Größe von bis zu acht Handles aufpasst, werden möglicherweise vier Handles verwendet. Die Zieh Größen sollten an den Fensterrahmen und die Edge-Metriken gebunden werden, wobei die **GetSystemMetrics** -API-Funktion proportional zur Bildschirmauflösung ist.<br /><br /> ![Handles zum Ändern der Größe](../../extensibility/ux-guidelines/media/0713-05_resizehandles.png "0713-05_ResizeHandles")|
|Drehen eines ausgewählten Objekts|![Handles zum Drehen](../../extensibility/ux-guidelines/media/0713-06_rotate.png "0713-06_Rotate")|

#### <a name="keyboard-interaction"></a>Tastatur Interaktion

|Eingabe|Ergebnis|
|-----------|------------|
|Registerkarte|Verschiebt den Fokus Indikator in die logische Reihenfolge von Objekten im Editor. Dies ist möglicherweise von links nach rechts oder von oben nach unten abhängig vom **TabIndex** -Eigenschafts Wert (oder Äquivalent), der Reihenfolge der Objekt Erstellung und dem allgemeinen Zweck des Editors. UMSCHALT + TAB kehrt die Richtung des Fokus Indikators um.|
|LEERTASTE|Aktiviert den Schwenk Modus, während der Tastatur Strich beibehalten wird. Zusätzliche Maus Eingaben sind erforderlich, um die Position des Viewports zu schwenken.|
|STRG+LEERTASTE|Aktiviert den Zoommodus, während der Tastatur Strich beibehalten wird. Zusätzliche Maus Eingaben sind erforderlich, um den Zoomfaktor zu vergrößern und zu verkleinern.|
|STRG + ALT + Minus Zeichen|Verringert den Zoomfaktor um eine Ebene.|
|STRG + ALT + Plus Zeichen|Erhöht den Zoomfaktor um eine Ebene.|
|UMSCHALT oder STRG|Fügt der Auswahlgruppe das-Objekt hinzu. Mit STRG können Sie Objekte auch einzeln aus der Auswahlgruppe entfernen.|
|EINGABETASTE|Führt den Standardbefehl für das-Objekt aus (in der Regel geöffnet oder bearbeitet).|
|F2|Aktiviert die direkte Bearbeitung für das-Objekt.|
|Pfeiltasten|Verschiebt die ausgewählten Objekte in der Richtung der Pfeiltaste in kleine Inkremente (z. b. 1 Pixel gleichzeitig).|
|STRG + Pfeiltasten|Verschiebt die ausgewählten Objekte in der Richtung der Pfeiltaste in größeren Inkrementen (z. b. 10 Pixel gleichzeitig).|
|UMSCHALT + Pfeiltasten|Ändert die Größe der ausgewählten Objekte in der jeweiligen Richtung in kleinen Schritten (z. b. 1 Pixel gleichzeitig).|
|STRG + UMSCHALT + Pfeiltasten|Ändert die Größe der ausgewählten Objekte in der jeweiligen Richtung in größeren Schritten (z. b. 10 Pixel gleichzeitig).|

 Wenn Benutzer Steuerelemente direkt bearbeiten, ist es möglicherweise sinnvoll, die Größe von Objekten mit Benutzereingaben automatisch zu ändern. Wenn der Benutzer z. b. ein Label-Steuerelement bearbeitet, sollte die Bezeichnung vergrößert werden, um den Text anzuzeigen, den der Benutzer soeben eingegeben hat. Wenn dies nicht der Fall ist, muss der Benutzer die Größe des Steuer Elements nach dem Bearbeiten des Texts manuell ändern. Wenn der Benutzer über viele Steuerelemente verfügt, wird dies zu einer unproduktiven Aufgabe.

#### <a name="graphical-containers"></a>Grafische Container
 In einigen Fällen stellen grafische Editoren Container für andere grafische Objekte bereit, wie z. b. das Windows Forms Panel-Steuerelement oder das Raster Layout-Steuerelement im HTML-Designer. Wenn der Editor Container für andere grafische Objekte bereitstellt, sollte das folgende Auswahl Modell nur für den Container verwendet werden (Objekte innerhalb des Containers folgen dem Standardmodell, wie oben beschrieben):

|Eingabe|Ergebnis|
|-----------|------------|
|Klicken Sie einfach auf den Container.|Wählt das Container Objekt aus, ohne direkt eines der enthaltenen Objekte auszuwählen. Der Container kann mit der Standard Maus und der Tastatureingabe (wie oben beschrieben) verschoben und/oder seine Größe angepasst werden. Enthaltene Objekte werden in Relation zum Container verschoben, aber enthaltene Objekte werden nicht in der Größe geändert, es sei denn, Sie sind auch direkt ausgewählt.|
|Zeigen Sie auf den Begrenzungs Bereich des Containers.|Schaltet die Maus in den Verschiebe Cursor, um anzugeben, dass der Container verschoben werden kann.|
|Ziehen Sie den Begrenzungs Bereich des Containers.|Ändert die Maus zum Verschiebe Cursor und verschiebt den Container (und die enthaltenen Objekte in). Der Container kann nicht verschoben werden, ohne zuerst mit einem einzigen Mausklick ausgewählt zu werden.|
|Klicken Sie mit der Maustaste auf ein Objekt innerhalb des Containers.|Deaktiviert den Container (sofern ausgewählt) und wählt nur das angeklickte Objekt aus.|
|UMSCHALT + Klicken oder Strg + Klick für ein enthaltenes Objekt und/oder einen Container|Fügt der vorhandenen Auswahl oder Auswahlgruppe das angeklickte Objekt hinzu. Wenn das angeklickte Objekt bereits ein Mitglied der Auswahlgruppe ist, wird es aus der Auswahlgruppe entfernt.|

 Die enthaltenen Objekte sollten dem Standardauswahl Modell entsprechen, wie im vorherigen Abschnitt beschrieben. Vor dem Testen der Benutzerfreundlichkeit des Windows Forms-Designers erwarteten Benutzer den nahtlosen Zugriff auf die enthaltenen Objekte ohne dazwischenliegende Schritte (durch das Containment-Objekt festgelegt).

#### <a name="disjoint-and-region-selections"></a>Disjunkt und Regions Auswahl
 Grafische Objekt-Editoren sollten eine nicht zusammenhängende Auswahl unterstützen. Beachten Sie, dass diese Grafik die Darstellung des Steuer Elements für Visual Studio nicht anzeigt. Ausführliche visuelle Spezifikationen finden Sie unter [grafische Objektauswahl](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_GraphicalObjectSelectionAppearance) Darstellung.

 ![Auswahl nicht zusammenhängender Bereiche und Regionen](../../extensibility/ux-guidelines/media/0713-07_disjointregionselectors.png "0713-07_DisjointRegionSelectors")

 **Nicht zusammenhängende Auswahl**

 Grafische Editoren sollten auch die Regions Auswahl mit einem Auswahl Indikator für den Marquee-Typ bereitstellen. Wenn der grafische Editor andere Objekttypen (z. b. Text) unterstützt, ist die Regions Auswahl abhängig von den Einschränkungen dieser anderen Objekttypen möglicherweise nicht möglich.

 ![Laufschriftauswahl](../../extensibility/ux-guidelines/media/0713-08_marqueeselection.png "0713-08_MarqueeSelection")

 **Laufschriftauswahl**

#### <a name="primary-and-secondary-selections"></a>Primäre und sekundäre Auswahl
 Einige grafische Objekt-Editoren ermöglichen es dem Benutzer, Objekte in Gruppen zu bearbeiten oder auszurichten. In diesem Fall muss das Konzept der primären und sekundären Auswahl eingeführt werden. Bei der primären Auswahl handelt es sich um das Objekt, auf das alle anderen Objekte bei Gruppen Vorgängen reagieren. Das Objekt, das der Benutzer zuerst auswählt, wird das primäre Steuerelement, und nachfolgende Auswahl wird zur sekundären Auswahl. Die primäre Auswahl weist eine eindeutige visuelle Behandlung der sekundären Auswahl (n) auf, um anzugeben, welches Objekt primär ist:

 ![Primär- und Sekundärauswahl](../../extensibility/ux-guidelines/media/0713-09_primarysecondary.png "0713-09_PrimarySecondary")

 **Primäre Auswahl mit zwei sekundären Auswahlen**

#### <a name="graphical-object-selection-appearance"></a><a name="BKMK_GraphicalObjectSelectionAppearance"></a> Darstellung der grafischen Objektauswahl
 Die Auswahl Handles sind Quadrate, die in einem rechteckigen Muster um das umgebende Feld des Objekts gezeichnet werden. Das folgende Diagramm zeigt Beispiele für die verschiedenen Zustände, die ein grafisches Objekt mit handle, Größenanpassung und direkt Bearbeitung aufweisen kann. Die Größe der Handles sollte mithilfe der **GetSystemMetrics** -API an die Fensterrahmen-und Edge-Metriken gebunden werden.

| State | Darstellung | Visuelle Details |
|-------------------------|---------------| - |
| **Nicht markiert** | Standard | ![Status der Standardschaltfläche](../../extensibility/ux-guidelines/media/0713-10_defaultstate.png "0713-10_DefaultState") |
| **Primäre Auswahl** | Geändert | ![Primäre Auswahl mit Handles zum Ändern der Größe](../../extensibility/ux-guidelines/media/0713-11_primaryresize.png "0713-11_PrimaryResize") |
| **Primäre Auswahl** | Nicht in der Größe geändert | ![Primäre Auswahl ohne Handles zum Ändern der Größe](../../extensibility/ux-guidelines/media/0713-13_primarynoresize.png "0713-13_PrimaryNoResize") |
| **Primäre Auswahl** | Gesperrt | ![Primäre Auswahl gesperrt](../../extensibility/ux-guidelines/media/0713-15_primarylocked.png "0713-15_PrimaryLocked") |
| **Sekundäre Auswahl** | Geändert | ![Sekundäre Auswahl mit Handles zum Ändern der Größe](../../extensibility/ux-guidelines/media/0713-17_secondaryresize.png "0713-17_SecondaryResize") |
| **Sekundäre Auswahl** | Nicht in der Größe geändert | ![Sekundäre Auswahl ohne Handles zum Ändern der Größe](../../extensibility/ux-guidelines/media/0713-19_secondarynoresize.png "0713-19_SecondaryNoResize") |
| **Sekundäre Auswahl** | Gesperrt | ![Sekundäre Auswahl gesperrt](../../extensibility/ux-guidelines/media/0713-21_secondarylocked.png "0713-21_SecondaryLocked") |
| **UI-aktiv** | Standard | ![Benutzeroberfläche im aktiven Status](../../extensibility/ux-guidelines/media/0713-23_uiactive.png "0713-23_UIActive") |

### <a name="view-selection-models"></a>Anzeigen von Auswahl Modellen

#### <a name="tree-view"></a>Strukturansicht
 Die Auswahl in einer Strukturansicht wird mit einer einfachen Hervorhebung angezeigt. Wenn der Benutzer auf einen Knoten Namen oder ein Knoten Symbol klickt, wird der Knoten ausgewählt. Die dreieckigen Symbole links vom Knoten erweitern oder verkleinern das Struktur Steuerelement, haben jedoch keine Auswirkungen auf die Auswahl des Benutzers, mit einer Ausnahme: beim Reduzieren eines übergeordneten Knotens, wenn sich die Auswahl auf einem untergeordneten Knoten dieses Knotens befindet, wird die Auswahl zum übergeordneten Knoten verschoben.

 ![Typische Strukturansicht in Visual Studio](../../extensibility/ux-guidelines/media/0713-25_treeview.png "0713-25_TreeView")

 **Typische Strukturansicht in Visual Studio**

 Struktur Ansichten können zusammenhängende und nicht zusammenhängende Auswahl auch über mehrere Ebenen in der Struktur hinweg unterstützen. An sichtbaren Struktur Knoten muss eine zusammenhängende oder disjunkt mehrfache Auswahl getroffen werden. Wenn ein Knoten reduziert ist, geht die zusammenhängende Auswahl verloren, und der reduzierte Knoten erhält die Auswahl. Auf diese Weise kann der Benutzer die Knoten sehen, die von einem Vorgang betroffen sind. Wenn Knoten reduziert werden, ist es unklar, welche Knoten betroffen sind.

 Wenn ein übergeordneter Knoten ausgewählt ist, sollte der Vorgang auf das übergeordnete Element angewendet werden. es gibt jedoch Fälle, in denen es sinnvoll ist, einen Vorgang für das übergeordnete Element und alle untergeordneten Elemente anzuwenden. Stellen Sie in diesem Fall während des Vorgangs zusätzliche Benutzeroberflächen bereit, z. b. ein Kontrollkästchen oder ein Bestätigungs Dialogfeld, um die Option "auf alle untergeordnete Elemente anwenden" explizit für den Benutzer bereitzustellen.

##### <a name="renaming"></a>Umbenennen
 Wenn das Umbenennen von Knoten in der Struktur unterstützt wird, sollte das Umbenennen direkt erfolgen. Der direkte Vorgang sollte in allen Tree-Steuerelementen in Visual Studio der Standard sein. Geben Sie einen RENAME-Befehl an, mit dem der direkte Bearbeitungsmodus sofort aktiviert wird, wobei die Textauswahl den vollständigen Namen des Knotens abdeckt und Benutzereingaben akzeptiert. Wenn der Knoten eine Datei darstellt, sollte der Dateiname die Erweiterung enthalten. Die Auswahl Markierung sollte nur den Text des Datei namens und nicht die Erweiterung enthalten.

|Eingabe|Ergebnis|
|-----------|------------|
|Eingabetaste|Commitvorgang|
|ESC-Taste|Bricht den Umbenennungs Vorgang ab.|
|Klicken außerhalb des direkten Bearbeitungsbereichs|Commitvorgang|
|Rückgängig|Einfaches Rückgängigmachen zum Abbrechen des Umbenennungs Vorgangs|

#### <a name="selection-within-lists-and-grid-controls"></a>Auswahl in Listen und Raster Steuerelementen
 Das Schlüsselkonzept in der Listen Auswahl besteht darin, dass es zeilenbasiert ist, d. h., wenn eine Auswahl getroffen wird, wird die gesamte Zeile als Einheit ausgewählt. Im Gegensatz dazu können Raster zulassen, dass bestimmte Zellen ausgewählt werden, ohne dass sich dies auf andere Aspekte der Zeile auswirkt. Raster können auch eine Hierarchie von geschposteten Zeilen enthalten (z. b. in einem treegrid-Element), die das auswählen und entfernen ganzer Zweige der Hierarchie durch Interaktion mit den übergeordneten Zeilen ermöglichen. Die Auswahl in Listen wird durch eine einfache Hervorhebungs Farbe für die gesamte Daten Zeile angezeigt. Der Fokus wird durch einen mit einem Pixel gepunkteten Rahmen um die aktuelle bearbeitbare Zeile oder Zelle dargestellt (Zeile, wenn alle Zellen schreibgeschützt sind).

> [!NOTE]
> **Fokus** und **Auswahl** sind unterschiedliche Konzepte. Der *Fokus* ist ein Hinweis darauf, welches Benutzeroberflächen Element als Ziel verwendet wird, Eingaben zu empfangen, die nicht explizit an ein anderes Objekt weitergeleitet werden, während sich die *Auswahl* auf den Zustand der Einbindung eines Objekts in eine Gruppe von Objekten bezieht, für die nachfolgende Vorgänge stattfinden.

 Die Auswahl in Listen kann zusammenhängend, zusammenhängend oder Region sein. Wenn Mehrfachauswahl zulässig ist, sollten zusammenhängende und nicht zusammenhängende Auswahl immer unterstützt werden, während die Unterstützung für die Regions Auswahl (Box) optional ist. Die Regions Auswahl wird durchziehen in den Leerraum des Listen Texts initiiert.

| Object | Auswahl |
|--------|------------|
| Liste | Zusammenhängenden |
| Liste | Zusammenhang losen |
| Liste | Region |

 Wenn Sie in einer Liste auf einmal klicken, wird die Zeile mit dem Klick angezeigt. Wenn der Benutzer auf eine Listen Zelle klickt, die eine direkte Bearbeitung unterstützt, wird die Zelle auch sofort für die direkte Bearbeitung aktiviert. Andernfalls wird die gesamte Zeile sofort ausgewählt und eine Hervorhebung angezeigt.

 Das Ziehen im Listen Text hat eine der folgenden drei Dinge:

- Initiiert eine Regions Auswahl, wenn Sie von der Liste unterstützt wird und sich der Mauszeiger in Leerraum befindet.

- Initiiert einen Drag & Drop-Vorgang, wenn die Listen Zelle oder Zeile als Zieh Quelle unterstützt.

- Wählt die aktuelle Zeile aus.

##### <a name="in-place-editing"></a>Direkte Bearbeitung
 Wenn eine direkte Bearbeitung zulässig ist, gibt es zwei grundlegende Modelle: einfaches Bearbeitungs Steuerelement und Eigenschaften Auswahl. Mit einem einfachen Bearbeitungs Steuerelement wird der Inhalt hervorgehoben und ist für Benutzereingaben bereit, sobald die direkte Bearbeitung aktiviert ist. Wenn eine Eigenschaften Auswahl implementiert ist, wird die Schaltfläche, die die Eigenschaften Auswahl aufruft, angezeigt, sobald der direkte Bearbeitungsmodus aktiviert ist, und die aktuelle Auswahl wird nicht hervorgehoben. Die Auswahl Schaltfläche sollte in der Zelle rechtsbündig sein. Direkte Bearbeitungs Beispiele finden Sie im **Eigenschaften Fenster** und **Aufgabenliste** in Visual Studio.

##### <a name="keyboard-support"></a>Tastaturunterstützung
 Die Tastatur Unterstützung für die Auswahl in Listen und Raster folgt den Windows-Standard Konventionen:

- Die Pfeiltasten navigieren in der Liste und wählen jede Zeile/Zelle aus, bei der der Fokus verschoben wird.

- Umschalt + Pfeil führt eine zusammenhängende Auswahl in der Richtung der Pfeiltasten aus.

- Strg + Pfeil gefolgt von Leertaste schaltet zwischen hinzufügen und Entfernen von Listenelementen aus der Auswahl, wodurch eine zusammenhängende Auswahl erstellt wird.

- Bei Raster, die schalte Hierarchien enthalten, wird durch die nach-rechts-Taste eine übergeordnete Zeile erweitert, und die nach-links-Taste wird eins reduziert.

- Mit der Tab-Taste wird der Fokus zwischen den Zellen in der aktuellen Zeile verschoben, wenn die Zellen bearbeitet werden können.

- Die EINGABETASTE führt den Standardbefehl für das Element in der Liste aus (häufig **geöffnet**).

- Mit der F2-Taste wird die direkte Bearbeitung für die aktuell ausgewählte Zelle aktiviert.

## <a name="persistence-and-saving-settings"></a><a name="BKMK_PersistenceAndSavingSettings"></a> Persistenz und Speichern von Einstellungen

### <a name="overview"></a>Übersicht
 Obwohl jede Softwarekomponente in Visual Studio in der Regel für den eigenen Zustand und die Persistenz verantwortlich ist, speichert Visual Studio automatisch Einstellungen in einigen Fällen, z. b. mit Fenstergrößen und Positionen. Die folgende Tabelle ist eine Kombination aus automatisch gespeicherten Einstellungen und Einstellungen, für die ein expliziter Benutzer oder eine programmierte Aktion erforderlich ist.

|Object|Was soll gespeichert werden?|Zeitpunkt der Speicherung|Speicherort|
|------------|------------------|------------------|-------------------|
|Auswählbares Objekt (z. b. eine Codezeile)|Ein Haltepunkt in einer Codezeile.<br /><br /> Eine Benutzer Verknüpfung, die der Codezeile zugeordnet ist.|Beim Speichern des Projekts|Die **Benutzer Optionsdatei (. suo)** für das Projekt|
|Dialog|Der Speicherort des Dialog Felds, wenn es verschoben wurde.<br /><br /> Die Ansicht, die der Benutzer zuletzt im Dialogfeld verwendet hat.|Beim Schließen des Dialog Felds<br /><br /> Wenn die Visual Studio-Sitzung beendet wird|Im Arbeitsspeicher<br /><br /> Registrierung in **HKEY_CURRENT_USER**|
|Fenster|Größe und Position des Fensters|Wenn das Fenster geschlossen wird<br /><br /> Wenn sich der Visual Studio-Modus ändert<br /><br /> Wenn die Visual Studio-Sitzung beendet wird|Die **Benutzer Optionsdatei (. suo)** für das Projekt<br /><br /> Benutzerdefinierte Optionsdatei für Fenster Einstellungen|
|Dokument|Die aktuelle Auswahl im Dokument.<br /><br /> Die Ansicht des Dokuments.<br /><br /> Die letzten Orte, die der Benutzer besucht hat.|Wenn das Dokument gespeichert wird|Die **Benutzer Optionsdatei (. suo)** für das Projekt|
|Project|Verweise auf Dateien<br /><br /> Verweise auf Verzeichnisse auf dem Datenträger<br /><br /> Verweise auf andere Software<br /><br /> Komponenten<br /><br /> Zustandsinformationen zum Projekt selbst|Beim Speichern des Projekts|Die Projektdatei.|
|Lösung|Verweise auf Projekte<br /><br /> Verweise auf Dateien|Beim Speichern des Projekts oder der Projekt Mappe|Die Projektmappendatei **(. sln)**|
|Einstellungen in den **Tools > Optionen**|Tastatur Anpassungen<br /><br /> Anpassen von Symbolleisten<br /><br /> Farbschemas|Wenn das Dialogfeld " **Tools > Optionen** " geschlossen wird<br /><br /> Wenn die Visual Studio-Sitzung beendet wird|Registrierung in **HKEY_CURRENT_USER**|

 Wie der Benutzer ausgeführt wird, und wann er ausgeführt wird, legt fest, ob eine Einstellung im Speicher (während der Sitzung) gespeichert, auf dem Datenträger gespeichert wird (Sitzungs übergreifend als Registrierungs Einstellung), als Teil der Projekt-oder Projektmappendatei selbst als Teil der **Projektmappenoptionen (. suo)** oder als benutzerdefinierte Einstellungsdatei, die nur von dieser Softwarekomponente bekannt ist. In der obigen Tabelle werden mehrere Ereignisse angezeigt, bei denen Einstellungen gespeichert werden können. Es gibt jedoch weitere Zeiten, in denen Sie möglicherweise den Zustand speichern möchten:

- Wenn der Benutzer den Speicherort innerhalb eines Dialog Felds oder Fensters ändert

- Wenn der Benutzer den Fokus auf ein anderes Fenster überträgt

- Wenn der Benutzer vom Entwurfs-in den Debugmodus wechselt

- Wenn sich der Benutzer bei seinem Konto anmeldet

- Wenn der Computer in den Ruhezustand wechselt oder heruntergefahren wird

- Wenn der Computer bzw. die Festplatte neu formatiert und erneut eingerichtet werden muss

### <a name="window-configurations"></a>Fenster Konfigurationen
 Bei einer Fenster Konfiguration handelt es sich um die grundlegende Darstellung der Entwicklungsumgebung. dabei handelt es sich um ein Schema, das aus der Liste der vorhandenen Tool Fenster und der Art der Anordnung besteht. Bei Windows, das von der IDE (IDE-Fenster) verwaltet wird, werden die Layoutinformationen pro Benutzer persistent gespeichert. Wenn ein Benutzer also die IDE öffnet, wird das Fenster Layout genauso wie bei der letzten Erstellung von Visual Studio angezeigt. Der Zustand und die Position von IDE-Fenstern werden in einer benutzerdefinierten Optionsdatei im XML-Format beibehalten. Tool Fenster, die von Paketen erstellt werden, die in die IDE geladen werden, speichern Ihre Zustandsinformationen in der Registrierung und können für jeden Benutzer gelten.

#### <a name="profile-specific-layouts"></a>Profil spezifische Layouts
 Jedes Profil umfasst Tool Fensterlayouts, die auf eine Weise organisiert werden, die bestimmten Entwickler-Personas vertraut ist (Visual C++ Entwickler die **Projektmappen-Explorer** auf der linken Seite der IDE sehen, während c#-Entwickler erwarten, dass die **Projektmappen-Explorer** auf der rechten Seite angezeigt wird. Profil spezifische Fensterlayouts werden geladen, wenn der Benutzer beim Start ein Profil auswählt. Ein Paket Autor sollte das Fenster Layout ermitteln, das sich am besten für die Benutzerfreundlichkeit eignet. dabei ist zu beachten, dass Änderungen, die der Benutzer an der Fenster Konfiguration vornimmt, dann persistent gespeichert werden.

## <a name="touch-input"></a><a name="BKMK_TouchInput"></a> Fingereingabe
 Benutzer verwenden zunehmend Microsoft-Entwicklungsprodukte auf Touchscreen-Geräten. Es gibt jedoch Barrieren, die die Verwendung von Entwicklungs Tools auf Touchscreen-Geräten erschweren. Benutzer erwarten, dass unsere Produkte eine zuverlässige und präzise Berührungs Funktion bereitstellen. Die Zielsetzung dieser Richtlinien besteht darin, Entscheidungen darüber zu informieren, welche Berührungs Funktionen integriert werden müssen, und um eine konsistente Berührungs Funktion in Visual Studio und zugehörigen Produkten zu fördern.

### <a name="levels-of-experience"></a>Erfahrungsebenen
 Die folgenden Erfahrungsebenen dienen als Leitfaden, um Teams bei der Entscheidung zu unterstützen, welche Berührungs Funktionen basierend auf den gewünschten Investitionen in Bezug auf Ihre Investition angeboten werden.

- Die **grundlegende** Vorgehensweise ist für Teams, die Berührungs Funktionen bereitstellen möchten, sodass keine unzustellbaren Enden der Arbeit vorhanden sind.

- Die **optimierte** Benutzer Funktionalität ist für Teams, die die gängigsten Berührungs Funktionen bereitstellen möchten (z. b. solche, die normalerweise in Internetbrowser Anwendungen verfügbar sind).

- Die **erhöhte Benutzerfreundlichkeit** ist für Teams vorgesehen, die Funktionen wie Gesten oder andere optionale Funktionen hinzufügen möchten, die Ihre Anwendung als Toucheingabe anzeigen können.

||Grundlegende Funktionen|Optimierte Darstellung|Erweiterte Darstellung|
|-|----------------------|--------------------------|-------------------------|
|**Ermöglicht Benutzern das...**|Korrigieren von Code und Projektmappen-/Projektebene ohne unzustellende Elemente|Ausführen von Wartungs-, refactors-und Navigationsaufgaben|Arbeiten Sie mit Sicherheit in einer konsistenten, intuitiven und flüssigen Erfahrung|
|**Editor**|Berühren von schwenken und Auswahl<br /><br /> ScrollBar-Fingereingabe zum Springen und drücken der STRG-Taste|Zoom vergrößern<br /><br /> Schneller Bildlauf<br /><br /> Auswahl<br /><br /> Einfache Verwendung des Kontextmenüs||
|**Top-Tool Fenster**|Listen schwenken<br /><br /> Elementauswahl<br /><br /> ScrollBar-Fingereingabe zum Springen und drücken der STRG-Taste|Einfaches scrollen und Auswahl einfacher Elemente||
|**Windowing**||Fenstergröße ändern<br /><br /> Schnellzugriff||
|**Dokument gut**||Einfache Navigation zwischen geöffneten Dateien||
|**Gesten**||Sicherstellen, dass allgemeine Gesten in der IDE funktionieren|Gesten basierte Aktionen<br /><br /> Unterstützung von Drag & amp; Drop und Designern|
|**Weitere Überlegungen**|||Benutzerdefinierte Bildschirmtastatur|

#### <a name="gestures"></a>Gesten
 Gesten bieten Benutzern eine Verknüpfung mit Befehlen, die andernfalls eine kompliziertere Interaktion erfordern. Lesen Sie die Windows-Richtlinien zu [häufigen Touchgesten für Desktop Anwendungen](/windows/desktop/wintouch/windows-touch-gestures-overview), und befolgen Sie diese Anleitung für die meisten Gesten, einschließlich einfacher Gesten wie Schwenken und Zoomen.
