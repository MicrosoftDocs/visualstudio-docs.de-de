---
title: Auswertungs Tools für Visual Studio | Microsoft-Dokumentation
description: Verwenden Sie diese Prüfliste, um die Qualität der Benutzer Qualität für visuelle und Interaktions Details für neue Features, die Sie für Visual Studio entwerfen
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f6f20074b3609bce8e661baed5fded1d0d367c53
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952017"
---
# <a name="evaluation-tools-for-visual-studio"></a>Auswertungstools für Visual Studio
## <a name="craftsmanship-checklist-for-visual-studio"></a>Handwerkliche Prüfliste für Visual Studio
 Verwenden Sie diese Prüfliste, um die Qualität der Benutzer Qualität für visuelle und Interaktions Details auszuwerten

### <a name="overview"></a>Übersicht

- Stellen Sie sicher, dass alle Befehle Feedback geben, das den Benutzern mitteilt, dass Ihre Befehle durchgeführt wurden.

- Vergewissern Sie sich, dass alle Elemente und Steuerelemente der Benutzeroberfläche in allen Designs und im hoher Kontrast Modus sichtbar sind.

- Stellen Sie sicher, dass die aktive und aktive Auswahl immer unterscheiden, sowohl im Standard-als auch im hoher Kontrast Modus.

- Vergewissern Sie sich, dass der Fokus immer sichtbar und offensichtlich ist.

### <a name="performance"></a>Leistung

- Vergewissern Sie sich, dass eine Art von "ausgelastet" angezeigt wird, wenn ein Befehl mehr als eine Sekunde benötigt.

- Vergewissern Sie sich, dass bei einem Befehl, der mehr als 10 Sekunden dauert, eine explizite Statusanzeige angezeigt wird, die entweder festgelegt (bevorzugt) oder unbestimmt ist.

### <a name="ui-text"></a>UI-Text

- Stellen Sie sicher, dass alle Bezeichnungen Satz-oder titelfall sind und dass kein Text vollständig klein geschrieben ist.

    ||Richtig|Falsch|
    |-|-------------|---------------|
    |**Befehls Text (alle)**|Satzfall:<br /><br /> **Verzeichnisname:**|Verzeichnis Name:|
    |**Schaltflächen Text (Client)**|Titelfall:<br /><br /> **[Als Standard festlegen]**|als Standard festlegen|
    |**Schaltflächen Text (Online)**|Satzfall:<br /><br /> **[Als Standard festlegen]**||

- Stellen Sie sicher, dass alle Bezeichnungen außer Gruppen Kopfzeilen und Schaltflächen mit einem Doppelpunkt enden und dem Steuerelement vorangestellt sind, mit dem Sie gekoppelt werden.

- Überprüfen Sie, ob Schaltflächen, Befehle und Befehls Verknüpfungen, die die Benutzeroberfläche zum Erfassen von Benutzereingaben starten, mit Auslassungs Punkten **[...]**.

  Beispiele:

  - Eine **[Advanced...]** -Schaltfläche in einem Dialogfeld.

  - Die Befehlsoptionen im Menü Extras (Extras **> Optionen**) sollten keine Ellipsen erhalten, da der Zweck des Befehls durch das Starten des Dialog Felds selbst ist.

- Vergewissern Sie sich, dass die Benutzeroberfläche keine Abkürzungen enthält, außer den branchenüblichen Bedingungen. Beispielsweise muss weder HTML noch TCP/IP ausgeschrieben werden, obwohl OOM (nicht genügend Arbeitsspeicher) und PII (persönlich identifizierbare Informationen) sein sollten.

### <a name="keyboard-access"></a>Tastaturzugriff

- Stellen Sie sicher, dass es eine Möglichkeit gibt, die einzelnen Aufgaben mit der Tastatur auszuführen. Dies erfolgt in der Regel über den Tastatur Zugriff für jedes Steuerelement, aber bei einigen sehr visuellen Bereichen ist eine Problem Umgehung wie das Wechseln zur Code Ansicht akzeptabel.

- Vergewissern Sie sich, dass Sie die Steuerelemente in einer logischen Reihenfolge (von links nach rechts und von oben nach unten) durchlaufen können. Diese Vorgehensweise ist zwar für die meisten Steuerelemente eine bewährte Methode, aber nicht für alle Steuerelemente erforderlich. Stellen Sie beispielsweise sicher, dass Optionsfeld-Steuerelemente in einer Gruppe mit einem einzelnen Tabstopp-Stopp angezeigt werden.

- Stellen Sie sicher, dass alle Steuerelemente über Bezeichnungen verfügen und dass jede Bezeichnung über einen mnetmonischen verfügt (Ausnahmen enthalten einige nicht beschriftete Steuerelemente, die möglicherweise einem bezeichneten Steuerelement auf der Registerkarte folgen).

- Stellen Sie sicher, dass keine mnetmonischen Konflikte vorhanden sind.

### <a name="fonts"></a>Schriftarten

- Überprüfen Sie, ob alle Schriftarten (Gesicht, Größe, Farbe) konsistent verwendet werden und die Hierarchie beibehalten wird.

- Überprüfen Sie, ob alle Benutzeroberflächen Elemente den Umgebungs Schriftart Dienst verwenden. (Siehe [Schriftarten und Formatierung für Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md))

     Um zu überprüfen, ob der Dienst verwendet wird, wechseln Sie zu Extras **> Optionen > Schriftarten und Farben**. Wählen Sie in der Dropdown Liste "Einstellungen" die Option Umgebungs Schriftart aus, und ändern Sie die Schriftart in etwas unterschiedlich (z. b. Harrington oder Comic-Sans), und legen Sie die Größe auf 12 pt fest Klicken Sie dann auf „OK“. Möglicherweise müssen Sie die IDE neu starten, aber die meisten Benutzeroberflächen werden sofort geändert. Bereiche, bei denen die Schriftart Änderung auch beim Neustart nicht übernommen wird, werden nicht in der Umgebungs Schriftart verwendet.

- Überprüfen Sie, ob die vom Dienst abgeleiteten Schriftarten (z. b. Fett oder erweiterter Text) ihre Größe und Formatierung in Relation zum "normalen" Text behalten, wenn der Schrift Grad der Umgebung geändert wird.

- Vergewissern Sie sich, dass aufgrund erweiterter Schriftarten keine Clippingfehler vorhanden sind. Schriftarten, die abgeschnitten werden, sind wahrscheinlich das Ergebnis von Steuerelementen mit fester Höhe oder Containern mit fester Höhe.

### <a name="dialogs"></a>Dialogfelder

- Vergewissern Sie sich, dass der Dialog Titel mit dem Befehl identisch ist, der ihn gestartet hat.

- Stellen Sie sicher, dass alle Standard Steuerelemente mit dem Betriebssystem konsistent sind: Hintergrundfarbe ist Standard, und keine Steuerelemente sollten über eine besondere Umgestaltung verfügen, die Sie von Standard Steuerelementen unterscheidet.

- Überprüfen Sie, ob die Ränder innerhalb des Formulars 12 Pixel betragen sollten und ob Sie einheitlich und konsistent erscheinen sollen.

- Überprüfen Sie, ob Dialogfelder zentriert innerhalb der IDE-Shell oder im Fenster angezeigt werden, das Sie erzeugt hat

- Wenn dies sinnvoll ist, sollten die Größe der Dialoge geändert werden können. Bei Dialogfeldern, deren Größe geändert werden kann, überprüfen Sie, dass bei der Größenänderung die Größe der entsprechenden Steuerelemente geändert werden muss, während andere Teile des Dialog Felds konstant bleiben.

- Überprüfen Sie, ob in der Größe in den Dialogfeldern die Größe geändert werden kann (Größe, Speicherort, Erweiterung von Dialogfeld Steuerelementen usw.).

- Vergewissern Sie sich, dass in der Titelleiste kein Symbol vorhanden ist.

- Vergewissern Sie sich, dass in der Titelleiste keine Schaltflächen Minimieren und maximieren vorhanden sind.

#### <a name="dialog-operation-buttons-vs-client-only"></a>Schaltflächen für den Dialog Vorgang (nur vs-Client)

- Überprüfen Sie, ob die Vorgangs Schaltflächen in dieser Reihenfolge vorliegen: **OK**, **Abbrechen**, **anwenden**.

- Vergewissern Sie sich, dass die Schaltflächen **OK** und **Abbrechen** die Standardgröße von 75 x 23 Pixel sind.

- Vergewissern Sie sich, dass die Schaltflächen **OK** und **Abbrechen** unabhängig von der Länge der Zeichenfolge dieselbe Größe haben.

- Wenn die Bezeichnung für eine Vorgangs Schaltfläche erfordert, dass die Schaltfläche größer als Standard ist, überprüfen Sie, ob die entsprechende Schaltfläche **Abbrechen** die gleiche Größe hat.

- Überprüfen Sie, ob zwischen Schaltflächen und zugeordneten Steuerelementen ein Abstand von 6 Pixeln besteht.

- Vergewissern Sie sich, dass die Schaltflächen **OK** und **Abbrechen** nicht über mnetmonics (Zugriffsschlüssel, die durch einen unterstrichenen Buchstaben definiert sind)

- Vergewissern Sie sich, dass eine Schaltfläche (normalerweise **OK**) standardmäßig den Fokus besitzt.

- Überprüfen, ob **ESC** das Dialogfeld abbricht

- Vergewissern Sie sich, dass die **Eingabe** Taste die Standard Schaltfläche ausführt, wenn sich der Fokus nicht in einem Steuerelement befindet

- Vergewissern Sie sich, dass die Schaltflächen **OK** und **Abbrechen** in der unteren rechten Ecke des Dialog Felds positioniert sind. In seltenen Fällen ist es akzeptabel, dass Sie in der oberen rechten Ecke vertikal gestapelt werden.

- Vergewissern Sie sich, dass die vertikale Konfiguration nur verwendet wird, wenn sich andere Schaltflächen in horizontaler Ausrichtung im Dialogfeld befinden.

### <a name="control-standards"></a>Steuerelement Standards

#### <a name="general"></a>Allgemein

- Vergewissern Sie sich, dass, sofern möglich, gute Standardwerte vorhanden sind, um die Benutzerinteraktion zu beschleunigen und Benutzer zu einem sicheren oder allgemeinen Ergebnis zu leiten.

- Vergewissern Sie sich, dass sich die Standard Steuerelemente auf die gleiche Weise Verhalten, damit die Benutzer wissen, was auf der Grundlage der früheren Benutzer

#### <a name="label-controls"></a>Label-Steuerelemente

- Stellen Sie sicher, dass jedes Steuerelement über eine Bezeichnung verfügt und dass jede Bezeichnung visuell mit dem Steuerelement gekoppelt ist (in der Regel innerhalb eines 4-6-Pixel Bereichs) und sich näher an Ihrem entsprechenden Steuerelement als bei anderen Steuerelementen befindet.

- Vergewissern Sie sich, dass Bezeichnungen linksbündig mit dem linken Rand des Steuer Elements positioniert sind, wenn Sie oberhalb und horizontal zentriert positioniert sind, sodass die Baseline der Bezeichnung an der Baseline des Eingabe Texts ausgerichtet ist, wenn Sie links positioniert ist.

- Stellen Sie sicher, dass, wenn mehrere gestapelte Bezeichnungen und Eingabe Steuerelemente auf der linken Seite eines Steuer Elements positioniert sind, die Bezeichnungen nach links und eine gleichmäßige Entfernung vom Rand des Dialog Felds, nie nach rechts und ein gleicher Abstand zu den Steuerelementen. Paare sollten gleichmäßig verteilt werden, es sei denn, Sie benötigen zusätzlichen Abstand zum Angeben der Gruppierung.

#### <a name="input-controls-text-boxes-and-combo-boxes"></a>Eingabe Steuerelemente (Textfelder und Kombinations Felder)

- Vergewissern Sie sich, dass bei Verwendung der standardmäßigen Umgebungs Schriftart die Anzeige Höhe für Textfelder, Kombinations Felder und Schaltflächen alle 23 Pixel beträgt.

- Wenn der Hinweis Text verwendet wird, vergewissern Sie sich, dass die Farbe `Environment.ControlEditHintText` mit dem Farb Dienst auf festgelegt ist.

- Wenn das Feld ein Pflichtfeld ist, das als solches identifiziert werden muss, überprüfen Sie Folgendes:

  - der Hintergrund ist auf festgelegt, `Environment.ControlEditRequiredBackground` und der Vordergrund ist auf festgelegt. `Environment.ControlEditRequiredHintText`

  - Es gibt einen Hinweis Text im Steuerelement, der als **" \<Required> "** angezeigt wird.

#### <a name="button-controls"></a>Schaltflächen-Steuerelemente

- Vergewissern Sie sich, dass die Schaltflächen eine minimale Größe von 75 x 23 Pixel haben, es sei denn, Sie können länger

- Stellen Sie sicher, dass die Schaltflächen die linken und rechten Ränder von 3-5 Pixeln aufweisen, sowie die Auffüll Zeichen für den Inhalt.

- Es ist zulässig, anstelle einer Schaltfläche **[Durchsuchen...]** (oder einer ähnlichen Funktionalität) eine kleine Quadrat Schaltfläche mit nur einer Ellipse **[...]** zu verwenden. Vergewissern Sie sich bei Verwendung, dass die Schaltfläche 23x23 groß ist.

- Wenn mehr als eine **[Browse...]** -Schaltfläche in einem Dialogfeld vorhanden ist, überprüfen Sie, ob die gekürzte Version (Ellipsis-only **[...]**) für alle verwendet wird.

- Vergewissern Sie sich, dass die Schaltflächen mit den Auslassungs Punkten **[...]** nicht über einen mnetmonic verfügen. Wenn sich der Fokus auf dem Eingabe Steuerelement daneben befindet, sollte eine Registerkarte den Fokus auf die Schaltfläche mit den Auslassungs Punkten bewegen.

- Vergewissern Sie sich, dass Schaltflächen, Befehle und Befehls Verknüpfungen, die eine sekundäre Benutzeroberfläche starten, mit der mehr Benutzereingaben erfasst werden, mit Auslassungs Zeichen **[...]** enden müssen

#### <a name="hyperlinks"></a>Links

- Stellen Sie sicher, dass ein Hyperlink-Steuerelement nicht rot blinkt Dies ist ein Indikator, dass der Color-Dienst nicht verwendet wird.

- Überprüfen Sie, ob die folgenden vs-Farben verwendet werden

  - `Environment.ControlLinkText`

  - `Environment.ControlLinkTextHover`

  - `Environment.ControlLinkTextPressed`

- Stellen Sie sicher, dass Hyperlinks ohne Unterstreichung angezeigt werden, wenn Sie nicht in einen Absatz eingebettet sind

#### <a name="check-boxes"></a>Kontrollkästchen

- Wenn ein Kontrollkästchen mehrzeiligen Text enthält, überprüfen Sie, ob das Feld an der ersten Textzeile ausgerichtet und nicht über alle Zeilen hinweg vertikal zentriert ist.

- Vergewissern Sie sich, dass die Kontrollkästchen immer auf eine binäre Auswahl hinweisen und nicht durch den Benutzer navigieren oder neue Fenster oder Seiten öffnen.

- Wenn ein Kontrollkästchen eine Option anzeigt, die mit einem Eingabe Steuerelement verknüpft ist, stellen Sie sicher, dass es linksbündig positioniert ist, und schließen Sie dieses Steuerelement, um dessen Beziehung anzugeben.

- Überprüfen Sie, ob ein Kontrollkästchen **nie** als Mittel zum Aktivieren des gesamten Inhalts eines Dialog Felds oder einer Seite verwendet wird.

#### <a name="group-boxes"></a>Gruppen Felder

- Vergewissern Sie sich, dass ein Dialogfeld kein einzelnes Gruppenfeld enthält, das den gesamten Inhalt des Dialog Felds enthält.

- Vergewissern Sie sich, dass in jedem Gruppenfeld mindestens zwei Steuerelemente vorhanden sind.

- Selten sollten mehr als zwei Gruppen Felder in einem Dialogfeld vorhanden sein.

- Stellen Sie sicher, dass keine Gruppen Felder für ein Netz vorhanden sind.

### <a name="icons"></a>Symbole

- Stellen Sie sicher, dass Symbole im Design "dunkel" ordnungsgemäß umgekehrt angezeigt werden.

- Stellen Sie sicher, dass alle Symbole auf grundlegenden Konzepten basieren.

- Vergewissern Sie sich, dass jedes Symbol eindeutig und leicht zu erkennen ist und nicht mehr als zwei Konzepte enthält (ohne Statusmodifizierer/Sprache).

- Überprüfen Sie, ob das Basis Symbol innerhalb des leer Zeichens zentriert angezeigt wird.

- Vergewissern Sie sich, dass alle Symbole im hoher Kontrast Modus lesbar angezeigt werden.

- Stellen Sie sicher, dass alle verwendeten Farben den Farb Verwendungs Standards entsprechen.

- Stellen Sie sicher, dass keine Symbole (Ränder) um Symbole vorhanden sind. (Falls vorhanden, sollte der Halo der Hintergrundfarbe der angrenzenden Benutzeroberfläche entsprechen.)

### <a name="touch-enabled-ui"></a>Touchscreen-aktivierte Benutzeroberfläche

- Überprüfen Sie, ob interaktive Steuerelemente groß genug sind, um problemlos touchfähig zu sein, mindestens **23x23 Pixel** groß

- Vergewissern Sie sich, dass die am häufigsten verwendeten Steuerelemente mindestens **40 x 40 Pixel** groß sind.

- Überprüfen, ob interaktive Steuerelemente mindestens **5 Pixel Abstand** zwischen Ihnen aufweisen
