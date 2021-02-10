---
title: Benachrichtigungen und Fortschritt für Visual Studio | Microsoft-Dokumentation
description: Erfahren Sie mehr über verschiedene Möglichkeiten, um Benutzer darüber zu informieren, was in Visual Studio in Bezug auf Ihre Software Entwicklungsaufgaben passiert.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bac47ee29029bdcccb5c248bc8e366376b5aed0d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931655"
---
# <a name="notifications-and-progress-for-visual-studio"></a>Benachrichtigungen und Fortschritt für Visual Studio
## <a name="notification-systems"></a><a name="BKMK_NotificationSystems"></a> Benachrichtigungs Systeme

### <a name="overview"></a>Übersicht
 Es gibt mehrere Möglichkeiten, den Benutzer darüber zu informieren, was in Visual Studio in Bezug auf die Software Entwicklungsaufgaben passiert.

 Beim Implementieren beliebiger Benachrichtigungs Arten:

- **Halten Sie die Anzahl der Benachrichtigungen auf die minimale** effektive Anzahl. Benachrichtigungs Meldungen sollten für die meisten Visual Studio-Benutzer oder Benutzer eines bestimmten Features bzw. featurebereichs gelten. Eine übermäßige Verwendung von Benachrichtigungen kann den Benutzer ggf. beeinträchtigen oder die erkannte Benutzerfreundlichkeit des Systems beeinträchtigen.

- **Stellen Sie sicher, dass Sie klare, Handlungs relevante Nachrichten präsentieren** , mit denen der Benutzer den entsprechenden Kontext aufrufen kann, um komplexere Auswahlmöglichkeiten zu treffen und weitere Maßnahmen zu ergreifen.

- **Stellen Sie synchrone und asynchrone Nachrichten entsprechend dar.** Synchrone Benachrichtigungen deuten darauf hin, dass eine sofortige Aufmerksamkeit erforderlich ist, z. b. Wenn ein Webdienst abstürzt oder eine Code Ausnahme ausgelöst wird. Der Benutzer sollte über diese Situationen sofort informiert werden, wenn die Eingabe erforderlich ist, z. b. in einem modalen Dialogfeld. Asynchrone Benachrichtigungen sind solche, die dem Benutzer bekannt sein sollten, die aber nicht sofort ausgeführt werden müssen, z. b. Wenn ein Buildvorgang abgeschlossen oder eine Website Bereitstellung abgeschlossen wurde. Diese Nachrichten sollten mehr Ambiente aufweisen und den Aufgaben Fluss des Benutzers nicht unterbrechen.

- **Verwenden Sie modale Dialogfelder nur, wenn dies notwendig ist, um zu verhindern, dass der Benutzer weitere Aktionen durchführen muss,** bevor die Nachricht bestätigt oder eine Entscheidung im Dialogfeld

- **Entfernen Sie Ambient-Benachrichtigungen, wenn Sie nicht mehr gültig sind.** Verlangen Sie nicht, dass der Benutzer eine Benachrichtigung verwerfen muss, wenn er bereits Maßnahmen ergriffen hat, um das Problem zu beheben, über das Sie benachrichtigt wurden.

- **Beachten Sie, dass Benachrichtigungen zu falschen Korrelationen führen können.** Benutzer können davon ausgehen, dass eine oder mehrere ihrer Aktionen eine Benachrichtigung ausgelöst haben, wenn es tatsächlich keine kausale Beziehung gab. Löschen Sie in der Benachrichtigungs Meldung den Kontext, den-Fehler und die Quelle der Benachrichtigung.

### <a name="choosing-the-right-method"></a>Auswählen der richtigen Methode
 Verwenden Sie diese Tabelle, um Sie bei der Auswahl der richtigen Methode zum Benachrichtigen des Benutzers über Ihre Nachricht zu unterstützen.

|Methode|Verwendung|Nicht verwenden|
|------------|---------|----------------|
|[Dialogfelder für modale Fehlermeldungen](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|Verwenden Sie, wenn eine Benutzer Antwort erforderlich ist, bevor Sie fortfahren.|Verwenden Sie nicht, wenn es nicht erforderlich ist, den Benutzer zu blockieren und den Flow zu unterbrechen. Vermeiden Sie die Verwendung von modalen Dialogfeldern, wenn es möglich ist, die Nachricht in einer anderen, weniger eindringlichen Weise anzuzeigen.|
|[IDE-Statusleiste](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|Verwenden Sie, wenn Ambient-Textinformationen zum Status eines Prozesses vorhanden sind.|Verwenden Sie nicht allein. Wird am besten in Verbindung mit einem anderen Feedback Mechanismus verwendet.|
|[Eingebettete Infoleiste](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|Verwenden Sie in einem Tool Fenster oder Dokument Fenster, um den Fortschritt, den Fehlerzustand, Ergebnisse und/oder Aktions Informationen zu benachrichtigen.|Verwenden Sie nicht, wenn die Informationen für den Speicherort der Info Leiste nicht relevant sind.<br /><br /> Nicht außerhalb eines Dokuments/Tool Fensters verwenden.|
|[Maus Cursor Änderungen](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|Kann verwendet werden, um zu benachrichtigen, dass ein Prozess fort läuft. Wird auch verwendet, um zu benachrichtigen, dass eine Statusänderung in der Maus vorliegt, z. b. wenn der Drag & Drop-Vorgang ausgeführt wird oder sich der Mauszeiger in einem bestimmten Modus befindet (z. b. im Zeichnungsmodus).|Verwenden Sie für kurze Statusänderungen nicht, oder wenn das geleert des Cursors wahrscheinlich ist (z. b., wenn es an Teile eines längeren Prozesses und nicht an den gesamten Prozess gebunden ist).|
|[Status Indikatoren](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|Verwenden Sie, wenn Sie den Fortschritt (entweder bestimmte oder unbestimmt) melden müssen. Es gibt eine Vielzahl von Status Indikator Typen und eine spezifische Verwendung für jeden. Siehe Status [Indikatoren](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators).||
|[Visual Studio-Benachrichtigunsfenster](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|Das Benachrichtigungsfenster ist nicht öffentlich erweiterbar. Es wird jedoch verwendet, um eine Reihe von Nachrichten über Visual Studio zu kommunizieren, einschließlich kritischer Probleme mit Ihrer Lizenz und Informations Benachrichtigungen über Updates für Visual Studio oder Pakete.|Verwenden Sie nicht für andere Benachrichtigungs Typen.|
|[Fehlerliste](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|Wenn sich das Problem direkt auf die aktuell geöffnete Lösung des Benutzers bezieht (Fehler/Warnung/Info), müssen Sie möglicherweise eine Aktion für den Code ausführen.<br /><br /> Hierzu gehören beispielsweise:<br /><br /> -Compilernachrichten (Fehler/Warnung/Info)<br /><br /> -Code Analyse-/Diagnosenachrichten zum Code<br /><br /> -Erstellen von Nachrichten<br /><br /> Eignet sich möglicherweise für Probleme im Zusammenhang mit den Projekt-oder Projektmappendateien, berücksichtigt jedoch zuerst eine Projektmappen-Explorer-Angabe.|Verwenden Sie nicht für Elemente, die keine Beziehung zum geöffneten Projektmappencode des Benutzers haben.|
|Editor-Benachrichtigungen: Glühbirne|Verwenden Sie, wenn eine Korrektur verfügbar ist, um ein Problem zu beheben, das in der geöffneten Datei vorhanden ist.<br /><br /> Beachten Sie, dass Glühbirnen auch zum Hosten schneller Aktionen verwendet werden soll, die bei Bedarf für den Code des Benutzers ausgeführt werden, wie z. b. refacktoren, aber in diesem Fall wird nicht "Benachrichtigungs Stil" angezeigt.|Verwenden Sie nicht für Elemente, die keine Beziehung zu der geöffneten Datei haben.|
|Editor-Benachrichtigungen: Wellenlinien|Verwenden Sie, um den Benutzer auf ein Problem mit einer bestimmten Spanne des geöffneten Codes zu benachrichtigen (z. b. eine rote Wellenlinie für Fehler).|Verwenden Sie nicht für Elemente, die sich nicht auf eine bestimmte Spanne Ihres geöffneten Codes beziehen.|
|[Eingebettete Status leisten](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|Wird verwendet, um den Status im Zusammenhang mit Inhalt oder Prozess innerhalb eines bestimmten Tool Fensters, Dokument Fensters oder Dialogfensters bereitzustellen.|Verwenden Sie nicht für allgemeine Produkt Benachrichtigungen, Prozesse oder Elemente, die keine Beziehung zum Inhalt innerhalb des jeweiligen Fensters haben.|
|[Windows-Info Bereichs Benachrichtigungen](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|Verwenden Sie, um Benachrichtigungen für Out-of-proc-Prozesse oder Begleit Anwendungen zu verwenden.|Verwenden Sie nicht für Benachrichtigungen, die für die IDE relevant sind.|
|[Benachrichtigungs Blasen](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|Verwenden Sie, um einen Remote Prozess zu benachrichtigen oder **außerhalb** der IDE zu wechseln.|Verwenden Sie nicht als Mittel zum Benachrichtigen des Benutzers von Prozessen **innerhalb** der IDE.|

### <a name="notification-methods"></a>Benachrichtigungs Methoden

#### <a name="modal-error-message-dialogs"></a><a name="BKMK_ModalErrorMessageDialogs"></a> Dialogfelder für modale Fehlermeldungen
 Ein modales Fehlermeldungs Dialogfeld wird verwendet, um eine Fehlermeldung anzuzeigen, die die Bestätigung oder Aktion des Benutzers erfordert.

 ![Modale Fehlermeldung](../../extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "0901-01_ModalErrorMessage")

 **Ein modales Fehlermeldungs Dialogfeld, das den Benutzer über eine ungültige Verbindungs Zeichenfolge für eine Datenbank**

#### <a name="ide-status-bar"></a><a name="BKMK_IDEStatusBar"></a> IDE-Statusleiste
 Die Wahrscheinlichkeit, dass Benutzer den Status leisten Text bemerken, korreliert mit der gesamten Computerumgebung und der Windows-Plattform. Die Visual Studio-Kundenbasis ist tendenziell in beiden Bereichen zu sehen, auch wenn fachkundige Windows-Benutzer möglicherweise Änderungen in der Statusleiste übersehen. Daher wird die Statusleiste am besten zu Informationszwecken oder als redundanter Hinweis für Informationen verwendet, die an anderer Stelle angezeigt werden. Alle wichtigen Informationen, die der Benutzer sofort auflösen muss, sollten in einem Dialogfeld oder im Benachrichtigungs Tool Fenster bereitgestellt werden.

 Die Visual Studio-Statusleiste ist so konzipiert, dass verschiedene Arten von Informationen angezeigt werden können. Es ist in Bereiche für Feedback, Designer, Statusanzeige, Animation und Client unterteilt.

 Der Feedback Bereich und der Designer Bereich sind immer sichtbar. Die Statusanzeige und die Animations Bereiche sind immer dynamisch und basieren auf dem Benutzer Kontext. Der Designer Bereich hat eine statische Breite, die durch die Länge der Zeichenfolge bestimmt wird, die von einer begleitenden Ressource für die Textnachricht abgerufen wird. Dadurch kann die Größe der Lokalisierung geändert werden, ohne dass eine Codeänderung erforderlich ist. In englischer Sprache beträgt die Breite dieser Zeichenfolge ungefähr 220 Pixel. Der Designer Bereich verhält sich normal, und der Feedback Bereich nimmt den verbleibenden Speicherplatz auf.

 Außerdem wird die Statusleiste hervorgehoben, um einen visuellen Interessen-und Funktionswert durch die Kommunikation verschiedener IDE-Statusänderungen, wie z. b. wenn sich die IDE im Debugmodus befindet,

 ![Farbänderungen für IDE-Statusleiste](../../extensibility/ux-guidelines/media/0901-02_idestatusbar.png "0901-02_IDEStatusBar")

 **Farben der IDE-Statusleiste**

#### <a name="embedded-infobar"></a><a name="BKMK_EmbeddedInfobar"></a> Eingebettete Info Leiste
 Eine Info Leiste kann im oberen Bereich eines Dokument Fensters oder Tool Fensters verwendet werden, um den Benutzer über einen Zustand oder eine Bedingung zu informieren. Es können auch Befehle angeboten werden, damit der Benutzer problemlos Maßnahmen ergreifen kann. Die Info Leiste ist ein Standardmäßiges shellsteuerelement. Erstellen Sie keine eigenen, die agieren und mit anderen in der IDE inkonsistent erscheinen. Weitere Informationen zur Implementierung finden Sie in den [infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars) und Anleitungen zur Verwendung.

 ![Eingebettete Infoleiste](../../extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "0901-03_EmbeddedInfobar")

 **Eine in ein Dokument Fenster eingebettete Info Leiste, die den Benutzer darüber informiert, dass sich die IDE im Verlaufs bezogenen Debugmodus befindet, und der Editor antwortet nicht auf die gleiche Weise wie im standarddebugmodus.**

#### <a name="mouse-cursor-changes"></a><a name="BKMK_MouseCursorChanges"></a> Maus Cursor Änderungen
 Wenn Sie den Mauszeiger ändern, verwenden Sie Farben, die an den vscolor-Dienst gebunden sind und dem Cursor bereits zugeordnet sind. Cursor Änderungen können zum Angeben eines laufenden Vorgangs sowie für Trefferzonen verwendet werden, in denen der Benutzer auf ein Ziel zeigt, das gezogen, abgelegt oder zum Auswählen eines Objekts verwendet werden kann.

 Verwenden Sie den ausgelasteten/Wait-Mauszeiger nur, wenn die gesamte verfügbare CPU-Zeit für einen Vorgang reserviert werden muss, sodass der Benutzer keine weiteren Eingaben Ausdrücken kann. In den meisten Fällen, in denen die Verwendung von Multithreading durch gut geschriebene Anwendungen verhindert, sollte es selten vorkommen, wenn Benutzer an anderen Vorgängen gehindert werden.

 Beachten Sie, dass Cursor Änderungen als redundanter Hinweis für Informationen an anderer Stelle nützlich sind. Verlassen Sie sich nicht auf eine Cursor Änderung als einzige Art der Kommunikation mit dem Benutzer, insbesondere, wenn Sie versuchen, etwas zu vermitteln, das für den Benutzer wichtig ist.

#### <a name="progress-indicators"></a><a name="BKMK_NotSysProgressIndicators"></a> Status Indikatoren
 Status Indikatoren sind wichtig, um dem Benutzer Feedback während der Prozesse zu geben, die mehr als ein paar Sekunden dauern müssen. Status Indikatoren können direkt (in der Nähe des Startpunkts der aktuell ausgeführten Aktion), in einer eingebetteten Statusleiste, in einem modalen Dialogfeld oder in der Statusleiste von Visual Studio angezeigt werden. Befolgen Sie die Anleitungen in den Status [Indikatoren](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators) bezüglich ihrer Verwendung und Implementierung.

#### <a name="visual-studio-notifications-window"></a><a name="BKMK_VSNotificationsToolWindow"></a> Visual Studio-Benachrichtigungsfenster
 Das Visual Studio-Benachrichtigungsfenster benachrichtigt Entwickler über Lizenzierung, Umgebung (Visual Studio), Erweiterungen und Updates. Benutzer können einzelne Benachrichtigungen verwerfen oder bestimmte Benachrichtigungs Typen ignorieren. Die Liste der ignorierten Benachrichtigungen wird auf der Seite **Tools > Optionen** verwaltet.

 Das Benachrichtigungsfenster ist zurzeit nicht erweiterbar.

 ![Visual Studio-Benachrichtigunsfenster](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901-06_VSNotificationsWindow")

 **Visual Studio-Benachrichtigungs Tool Fenster**

#### <a name="error-list"></a><a name="BKMK_ErrorList"></a> Fehlerliste
 Eine Benachrichtigung in der Fehlerliste weist auf Fehler und Warnungen hin, die während der Kompilierung und des Buildprozesses aufgetreten sind, und ermöglicht dem Benutzer, im Code zu diesem spezifischen Code Fehler zu navigieren.

 ![Fehlerliste](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "0901-08_ErrorList")

 **Fehlerliste in Visual Studio**

#### <a name="embedded-status-bars"></a><a name="BKMK_EmbeddedStatusBars"></a> Eingebettete Status leisten
 Da die IDE-Statusleiste dynamisch ist, wenn der Client Regions Kontext auf das aktive Dokument Fenster festgelegt ist und die Informationen im Kontext und/oder in den System Antworten des Benutzers aktualisiert werden, ist es schwierig, eine kontinuierliche Anzeige der Informationen beizubehalten oder den Status für langfristige asynchrone Prozesse anzugeben. Die IDE-Statusleiste eignet sich z. b. nicht für Benachrichtigungen über Test Lauf Ergebnisse für mehrere Ausführungen und/oder sofort Handlungs relevante Elementauswahl. Es ist wichtig, diese Statusinformationen im Kontext des Dokuments oder Tool Fensters beizubehalten, in dem der Benutzer eine Auswahl trifft oder einen Prozess startet.

 ![Eingebettete Statusleiste](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "0901-09_EmbeddedStatusBar")

 **Eingebettete Statusleiste in Visual Studio**

#### <a name="windows-tray-notifications"></a><a name="BKMK_WindowsTray"></a> Windows-Info Bereichs Benachrichtigungen
 Der Windows-Benachrichtigungsbereich befindet sich neben der Systemuhr auf der Windows-Taskleiste. Viele Hilfsprogramme und Softwarekomponenten stellen Symbole in diesem Bereich bereit, sodass der Benutzer ein Kontextmenü für systemweite Aufgaben, z. b. das Ändern der Bildschirmauflösung oder das Abrufen von Software Updates, abrufen kann.

 Benachrichtigungen auf Umgebungs Ebene sollten im Benachrichtigungs-Hub von Visual Studio und nicht im Windows-Benachrichtigungsbereich angezeigt werden.

#### <a name="notification-bubbles"></a><a name="BKMK_NotificationBubbles"></a> Benachrichtigungs Blasen
 Benachrichtigungs Blasen können als Informations Informationen in einem Editor oder Designer oder als Teil des Windows-Benachrichtigungs Bereichs angezeigt werden. Der Benutzer spürt diese Blasen als Probleme auf, die Sie später auflösen können. Dies ist ein Vorteil für nicht kritische Benachrichtigungen. Blasen sind für wichtige Informationen ungeeignet, die der Benutzer sofort lösen muss. Wenn Sie Benachrichtigungs Blasen in Visual Studio verwenden, befolgen Sie die [Anleitungen für den Windows-Desktop für Benachrichtigungs Blasen](/windows/desktop/uxguide/mess-notif).

 ![Benachrichtigungssprechblase](../../extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "0901-07_NotificationBubbles")

 **Benachrichtigungsblase im Windows-Benachrichtigungsbereich, der für Visual Studio verwendet wird**

## <a name="progress-indicators"></a><a name="BKMK_ProgressIndicators"></a> Status Indikatoren

### <a name="overview"></a>Übersicht
 Status Indikatoren sind ein wichtiger Bestandteil eines Benachrichtigungs Systems, um dem Benutzer Feedback zu geben. Sie informieren den Benutzer, wenn Prozesse und Vorgänge ausgeführt werden. Zu den bekannten Indikator Typen zählen Status leisten, drehende Cursor und animierte Symbole. Der Typ und die Platzierung einer Statusanzeige sind abhängig vom Kontext, einschließlich der gemeldeten Informationen und der Zeit, zu der der Prozess oder Vorgang abgeschlossen wird.

#### <a name="factors"></a>Faktoren
 Um zu ermitteln, welcher Indikator Typ geeignet ist, müssen Sie die folgenden Faktoren ermitteln.

1. **Zeitliche Steuerung:** Zeitspanne, die der Vorgang dauert

2. **Modalität:** gibt an, ob der Vorgang für die Umgebung modal ist (sperrt die Benutzeroberfläche, bis der Prozess beendet ist).

3. **Persistent/vorübergehend:** gibt an, ob das Endergebnis des Status zu einem späteren Zeitpunkt gemeldet und/oder angezeigt werden muss.

4. **Determinate/unbestimmte Zeit:** gibt an, ob die Endzeit des Vorgangs und der Fortschritt berechnet werden können.

5. **Grafik-/textspeicherort:** gibt an, ob der Fortschritt oder Prozess Inline, im Nachrichtentext oder in einem bestimmten Steuerelement (z. b. in der Strukturansicht) aufgezeichnet wird.

6. **Near:** gibt an, ob sich der Fortschritt in der Nähe der Benutzeroberfläche befinden soll, mit der er verknüpft ist. (Beispielsweise kann es sich in der Statusleiste befinden, die möglicherweise weit entfernt ist oder sich in der Nähe der Schaltfläche befinden muss, die den Prozess gestartet hat?)

#### <a name="determinate-progress"></a>Determinate des Fortschritts

|Fortschritts Typen|Verwendung|Notizen|
|-------------------|-------------------------|-----------|
|Statusanzeige (determinate)|Erwartete Dauer >5 Sekunden.<br /><br /> Kann eine Textbeschreibung der Prozessdetails einschließen.|Betten Sie **keinen** Text in die Animation ein.|
|Infoleiste|Messaging in Verbindung mit kontextbezogener Benutzeroberfläche. Siehe [Info leisten](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).<br /><br /> Kann eine Textbeschreibung der Prozessdetails einschließen.|Verwenden Sie **nicht** mehrere Info leisten, wenn Sie mehrere Prozesse angeben müssen. Verwenden Sie stattdessen gestapelte Status leisten.|
|Ausgabefenster|Vorübergehende Benachrichtigung: Prozess auf App-Ebene, nach dem der Benutzer Details **überprüfen** möchte.|Verwenden Sie **nicht** , wenn der Benutzer später auf Daten verweisen muss.|
|Protokolldatei|In Kombination mit einer vorübergehenden Benachrichtigung in Fällen, in denen es wichtig ist, nach Abschluss Details zu **Speichern** .||
|Statusleiste|Vorübergehende Benachrichtigung: Prozess auf App-Ebene, von dem der Benutzer nach Abschluss keine weiteren Details **benötigt** .<br /><br /> Enthält eine eingebettete Statusanzeige.<br /><br /> Kann eine Textbeschreibung der Prozessdetails einschließen.||

#### <a name="indeterminate-progress"></a>Unbestimmter Status

|Fortschritts Typen|Verwendung|Notizen|
|-------------------|-------------------------|-----------|
|Statusanzeige (unbestimmt)|Erwartete Dauer >5 Sekunden.<br /><br /> Kann eine Textbeschreibung der Prozessdetails einschließen.|Betten Sie **keinen** Text in die Animation ein.|
|Ameisen (animierte horizontale Punkte)|Roundtrip zum Server.<br /><br /> Wird in der Nähe des Kontext Punkts über den übergeordneten Container platziert.|**Verwenden Sie nicht,** wenn der gesamte Container nicht übergeordnet ist.|
|Spinner (Fortschritts Ring)|Der Prozess, der der kontextbezogenen Benutzeroberfläche zugeordnet ist, oder, wenn Speicherplatz berücksichtigt wird<br /><br /> Kann eine Textbeschreibung der Prozessdetails einschließen.||
|Infoleiste|Messaging in Verbindung mit kontextbezogener Benutzeroberfläche. Siehe [Info leisten](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).|Verwenden Sie **nicht** mehrere Info leisten, wenn Sie mehrere Prozesse angeben müssen. Verwenden Sie stattdessen gestapelte Status leisten.|
|Ausgabefenster|Vorübergehende Benachrichtigung: Prozess auf App-Ebene, über den der Benutzer nach Abschluss Details **prüfen** möchte.|Verwenden Sie **nicht** , um Informationen zu erhalten, die Sitzungs übergreifend beibehalten werden müssen.|
|Protokolldatei|In Kombination mit einer vorübergehenden Benachrichtigung in Fällen, in denen es wichtig ist, nach Abschluss Details zu **Speichern** .||
|Statusleiste|Vorübergehende Benachrichtigung: Prozess auf App-Ebene, von dem der Benutzer nach Abschluss keine weiteren Details **benötigt** .<br /><br /> Schließt die eingebettete Statusleiste ein.<br /><br /> Kann eine Textbeschreibung der Prozessdetails einschließen.||

### <a name="progress-indicator-types"></a>Fortschrittsindikator Typen

#### <a name="progress-bars"></a>Status anzeigen

##### <a name="indeterminate"></a>Unbestimmten
 ![Unbestimmte Statusanzeige](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901-04_Indeterminate")

 **Unbestimmte Statusanzeige**

 "Unbestimmt" bedeutet, dass der allgemeine Fortschritt eines Vorgangs oder Prozesses nicht bestimmt werden kann. Verwenden Sie für Vorgänge, die einen unbegrenzten Zeitraum erfordern oder auf eine unbekannte Anzahl von Objekten zugreifen, unbeschränkte Status leisten. Verwenden Sie eine Textbeschreibung, um zu beobachten, was passiert. Verwenden Sie Timeouts, um zeitbasierte Vorgänge zu Grenzen. Unbeendete Status leisten verwenden Animationen, um anzuzeigen, dass der Fortschritt ausgeführt wird, aber es werden keine weiteren Informationen bereitgestellt. Wählen Sie nicht nur basierend auf dem möglichen Mangel an Genauigkeit eine unbestimmte Statusanzeige aus.

##### <a name="determinate"></a>Bestimmte
 ![Determinate der Statusanzeige](../../extensibility/ux-guidelines/media/0901-05_determinate.png "0901-05_Determinate")

 **Determinate der Statusanzeige**

 "Determinate" bedeutet, dass ein Vorgang oder ein Prozess einen begrenzten Zeitraum erfordert, auch wenn diese Zeitspanne nicht genau vorhergesagt werden kann. Geben Sie den Abschluss eindeutig an. Lassen Sie eine Statusanzeige nicht zu 100 Prozent wechseln, es sei denn, der Vorgang wurde abgeschlossen. Die determinate der Statusanzeige Animation wechselt von 0 nach rechts von 0 bis 100%.

 Verschieben Sie die Statusanzeige niemals rückwärts während eines Vorgangs. Der Balken sollte sich stetig vorwärts bewegen, wenn der Vorgang beginnt und 100% erreicht, wenn er endet. Der Punkt der Statusanzeige besteht darin, den Benutzern einen Überblick darüber zu verschaffen, wie lange der gesamte Vorgang dauert, unabhängig davon, wie viele Schritte ausgeführt werden.

##### <a name="concurrent-reporting-stacked-progress-bars"></a>Gleichzeitige Berichterstellung (gestapelte Status leisten)
 Wenn ein Vorgang lange Zeit in Anspruch nimmt (möglicherweise mehrere Minuten), werden möglicherweise zwei Status leisten verwendet, eine, die den Gesamtfortschritt eines Vorgangs anzeigt, und eine andere für den Fortschritt des aktuellen Schritts. Wenn ein Setup Programm z. b. viele Dateien kopiert, kann eine Statusanzeige verwendet werden, um anzugeben, wie lange der gesamte Prozess dauert, während eine Sekunde angeben kann, welcher Prozentsatz der aktuellen Datei oder des Verzeichnisses kopiert wird. Melden Sie nicht mehr als fünf gleichzeitige Vorgänge oder Prozesse mithilfe von gestapelten Status leisten. Wenn Sie über mehr als fünf gleichzeitige Vorgänge oder Prozesse zum Melden verfügen, verwenden Sie ein modales Dialogfeld mit der Schaltfläche Abbrechen, und melden Sie die Status Details an den Ausgabefenster.

##### <a name="textual-descriptions"></a>Textbeschreibungen
 Verwenden Sie eine Textbeschreibung, um die Vorgänge und die geschätzte Zeit bis zum Abschluss zu begleiten. Wenn es nicht möglich ist, zu bestimmen, wie lange ein Vorgang dauert, kann es besser sein, Feedback zu geben, anstatt eine Statusanzeige zu erhalten.

 Visual Studio bietet eine Standardstatus Anzeige in der Statusleiste, die von jedem in Visual Studio integrierten Produkt verwendet werden kann. Bei Textbeschreibungen der Vorgänge, die während der Animation der Statusanzeige auftreten, kann der Text der Statusleiste aktualisiert werden.

#### <a name="other-progress-indicators"></a>Weitere Status Indikatoren

##### <a name="ants-animated-horizontal-dots"></a>Ameisen (animierte horizontale Punkte)
 ![Ant-Elemente zum Fortschritt](../../extensibility/ux-guidelines/media/0903-01_ants.png "0903-01_Ants")

 "Ameisen", animierte horizontale Punkte, stellen einen visuellen Verweis für einen unbestimmten Roundtrip-Server Prozess bereit.

##### <a name="spinner-progress-ring"></a>Spinner (Fortschritts Ring)
 ![Drehelement zum Fortschritt](../../extensibility/ux-guidelines/media/0903-02_spinner.png "0903-02_Spinner")

 Der Spinner (auch als "Fortschritts Ring" bezeichnet) ist eine unbestimmende Statusanzeige, die hauptsächlich in Bezug auf die kontextabhängige Benutzeroberfläche verwendet wird. Zeigen Sie einen Spinner in unmittelbarer Nähe zum zugehörigen Inhalt an, wie z. b. einen Header der Textkategorie, ein Messaging oder ein Steuerelement.

##### <a name="cursor-feedback"></a>Cursor Feedback
 Stellen Sie für Vorgänge, die zwischen 2-7 Sekunden dauern, Cursor Feedback bereit. In der Regel bedeutet dies, dass der vom Betriebssystem bereitgestellte warte Cursor verwendet wird. Anleitungen hierzu finden Sie im MSDN-Artikel [Cursor. Wait-Eigenschaft](/dotnet/api/system.windows.input.cursors.wait).

#### <a name="progress-indicator-locations"></a>Status Indikator Speicherorte

##### <a name="status-bar"></a>Statusleiste
 Die Statusleiste gibt Ihrer Anwendung einen Ort zum Anzeigen von Nachrichten und nützliche Informationen für den Benutzer, ohne die Arbeit des Benutzers zu unterbrechen. Der Status für den Fortschritt wird in der Regel am unteren Rand eines Fensters angezeigt. er enthält eine Meldung zum Measure des Status in Kombination mit einem Statusanzeige Indikator.

 ![Statusleiste mit Fortschrittsleiste](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903-03_StatusBarProgressBar")

 **Statusleiste mit Fortschrittsleiste**

 ![Statusleiste mit Meldungen](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903-04_StatusBarMessage")

 **Status Leiste mit Textbeschreibung**

##### <a name="infobar"></a>Infoleiste
 Ähnlich wie bei der Statusleiste bietet die Info Leiste kontextbezogene Benachrichtigungen und Messaging, die auch mit unbestimmten Status Indikatoren gekoppelt werden können, wie z. b. der Statusanzeige oder dem Spinner. Die Info Leiste sollte keinen granularitätsstatus bereitstellen oder die Fortschrittsanzeige bestimmen. Siehe [Info leisten](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).

 ![Infoleiste mit Fortschrittsanzeige und Meldungen](../../extensibility/ux-guidelines/media/0903-05_infobar.png "0903-05_InfoBar")

 **Info Leiste mit Statusanzeige und Textbeschreibung**

 ![Infoleiste in einem Fenster](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903-06_InfoBarInWindow")

##### <a name="inline"></a>Inline
 Die Inline Statusanzeige kann von einem beliebigen Status Lade-Typ dargestellt werden. In der Regel wird die Statusanzeige mit Messaging gekoppelt, dies ist jedoch nicht zwingend erforderlich.

 ![Inline-Drehelement zum Fortschritt](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903-07_InlineSpinner")

 **Spinner in Kombination mit Textbeschreibung**

 ![Gestapelte Inline-Fortschrittsleisten](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903-08_InlineStackedProgress")

 **Festlegen von gestapelten Status leisten**

 ![Inline-Fortschrittsmeldungen](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903-09_InlineText")

 **Inline Text Server-Explorer: wird aktualisiert...**

##### <a name="tool-windows"></a>Toolfenster
 Die globale Statusanzeige wird durch eine unbestimmtes Statusanzeige dargestellt, die direkt unterhalb der Symbolleiste positioniert ist.

 ![Globale unbestimmte Fortschrittsleiste](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903-23_GlobalIndeterminate")

 **Team Explorer globale Statusanzeige "unbegrenzt"**

##### <a name="dialogs"></a>Dialogfelder
 Dialoge können beliebige Status Lade Typen enthalten. Status Indikatoren können mit Messaging gekoppelt werden, und es werden mehrere Ebenen der Fortschrittsanzeige kombiniert, um differenzierte und unter Prozesse darzustellen.

 ![Dialogfeld mit mehreren Arten von Fortschrittsanzeigen](../../extensibility/ux-guidelines/media/0903-11_dialog.png "0903-11_Dialog")

 **Visual Studio-Dialogfeld mit gleichzeitigen Prozessen und mehreren Fortschrittsindikator Typen**

 ![Dialogfeld mit Fortschrittsanzeige und Meldungen](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "0903-12_Dialog2")

 **Visual Studio-Dialogfeld mit Fortschritts Lade-und Messaging Inline-Befehlsausführung**

##### <a name="document-well"></a>Dokument gut
 Das Dokument ist in Kombination mit Steuerelementen in der Lage, mehrere Fortschritts Lade Typen anzuzeigen.

 ![Fortschrittsmeldungen in Dokument](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "0903-13_DocumentWell")

 **Unbestimmte Statusanzeige unterhalb der Symbolleiste**

##### <a name="output-window"></a>Ausgabefenster
 Das Fenster Ausgabe eignet sich für die Verarbeitung von Prozessfortschritt und fortlaufender Status Status über Inline-Textnachrichten. Sie sollten die Status Leiste zusammen mit der Status Berichterstellung für Ausgabefenster verwenden.

 ![Fortschrittsmeldungen in Ausgabefenster](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903-14_OutputWindow")

 **Ausgabefenster mit fortlaufendem Prozessstatus und Wait-Messaging**

## <a name="infobars"></a><a name="BKMK_Infobars"></a> Info leisten

### <a name="overview"></a>Übersicht
 Mit Info leisten erhält der Benutzer einen Indikator, der in der Nähe ihrer Aufmerksamkeit liegt, und die Verwendung des freigegebenen Info Leiste-Steuer Elements gewährleistet die Konsistenz bei visueller Darstellung und Interaktion.

 ![Info Leiste](../../extensibility/ux-guidelines/media/0904-01_infobar.png "0904-01_Infobar")

 **Info leisten in Visual Studio**

#### <a name="appropriate-uses-for-an-infobar"></a>Geeignete Verwendungsmöglichkeiten für eine Info Leiste

- , Um dem Benutzer eine nicht blockierende, aber wichtige Meldung zu vermitteln, die für den aktuellen Kontext relevant ist.

- So geben Sie an, dass sich die Benutzeroberfläche in einem bestimmten Zustand oder einer bestimmten Bedingung befindet, die Auswirkungen auf die Interaktion hat

- So Benachrichtigen Sie den Benutzer, dass Probleme erkannt wurden, z. b. Wenn eine Erweiterung Leistungsprobleme verursacht

- So bieten Sie dem Benutzer eine Möglichkeit, mühelos Maßnahmen zu ergreifen, z. b. wenn der Editor erkennt, dass eine Datei über gemischte Registerkarten und Leerzeichen verfügt

##### <a name="do"></a>Führen Sie Folgendes aus:

- Halten Sie den Text der Info Leiste kurz und an den Punkt.

- Halten Sie den Text auf Verknüpfungen und Schaltflächen als prätiv.

- Stellen Sie sicher, dass die "action"-Optionen, die Sie für Benutzer bereitstellen, minimal sind und nur erforderliche Aktionen

##### <a name="dont"></a>Tue nicht:

- Verwenden Sie eine Info Leiste, um Standard Befehle anzubieten, die in einer Symbolleiste platziert werden sollen.

- Verwenden Sie eine Info Leiste anstelle eines modalen Dialog Felds.

- Erstellen Sie eine unverankerte Nachricht außerhalb eines Fensters.

- Verwenden Sie mehrere Info leisten an mehreren Positionen innerhalb desselben Fensters.

#### <a name="can-multiple-infobars-show-at-the-same-time"></a>Können mehrere Info leisten gleichzeitig angezeigt werden?
 Ja, mehrere Info leisten können gleichzeitig angezeigt werden. Sie werden in der Reihenfolge First-Come und first-served angezeigt, wobei die erste Infoleiste oben und zusätzliche Info leisten unten angezeigt werden.

 Der Benutzer erhält maximal drei Info leisten gleichzeitig. Danach wird der Info Leiste-Bereich scrollfähig, wenn weitere Info leisten verfügbar sind.

### <a name="creating-an-infobar"></a>Erstellen einer Info Leiste
 Die Info Leiste hat vier Abschnitte von links nach rechts:

- **Symbol:** An dieser Stelle würden Sie jedes Symbol hinzufügen, das Sie für die Info Leiste anzeigen möchten, z. b. ein Warnsymbol.

- **Text:** Sie können Text hinzufügen, um den Benutzer des Szenarios bzw. der Situation zu beschreiben, der in zusammen mit Links im Text enthalten ist, falls erforderlich. Denken Sie daran, den Text kurz zu halten.

- **Aktionen:** Dieser Abschnitt sollte Links und Schaltflächen für Aktionen enthalten, die der Benutzer in der Info Leiste ausführen kann.

- **Schaltfläche Schließen:** Der letzte Abschnitt rechts kann eine Schaltfläche Schließen aufweisen.

#### <a name="creating-a-standard-infobar-in-managed-code"></a>Erstellen einer Standard Infoleiste in verwaltetem Code
 Die Infobar Model-Klasse kann zum Erstellen einer Datenquelle für eine Info Leiste verwendet werden. Verwenden Sie einen dieser vier Konstruktoren:

```
public InfoBarModel(IEnumerable<IVsInfoBarTextSpan> textSpans, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);

```

```
public InfoBarModel(string text, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);

```

```
public InfoBarModel(IEnumerable<IVsInfoBarTextSpan> textSpans, IEnumerable<IVsInfoBarActionItem> actionItems, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);

```

```
public InfoBarModel(string text, IEnumerable<IVsInfoBarActionItem> actionItems, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);
```

 Hier ist ein Beispiel, das ein Infobar Model mit Text mit einem Hyperlink, einer Aktions Schaltfläche und einem Symbol erstellt.

 ![Infoleiste mit Hyperlink](../../extensibility/ux-guidelines/media/0904-02_infobarhyperlink.png "0904-02_InfobarHyperlink")

```
var infoBar = new InfoBarModel(
    textSpans: new[]
    {
        new InfoBarTextSpan("This is a "),
        new InfoBarHyperlink("hyperlink"),
        new InfoBarTextSpan(" InfoBar.")
    },
    actionItems: new[]
    {
        new InfoBarButton("Click Me")
    },
    image: KnownMonikers.StatusInformation,
    isCloseButtonVisible: true);

```

#### <a name="creating-a-standard-infobar-in-native-code"></a>Erstellen einer Standard Infoleiste in nativem Code
 Implementieren Sie die ivsinfobar-Schnittstelle, um eine Info Leiste aus nativem Code bereitzustellen.

```
public interface IVsInfoBar
{
    IVsInfoBarActionItemCollection ActionItems { get; }
    ImageMoniker Image { get; }
    bool IsCloseButtonVisible { get; }
    IVsInfoBarTextSpanCollection TextSpans { get; }
}

```

#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>Erhalten eines Info Leiste-UIElement über eine Info Leiste
 Die infobarmodel-oder ivsinfobar-Implementierung ist ein Datenmodell, das in ein UIElement-Element umgewandelt werden muss, damit es in der Benutzeroberfläche angezeigt wird. Ein UIElement kann mit dem Dienst svsinfobaruifactory/ivsinfobaruifactory abgerufen werden.

```
private bool TryCreateInfoBarUI(IVsInfoBar infoBar, out IVsInfoBarUIElement uiElement)
{
    IVsInfoBarUIFactory infoBarUIFactory = serviceProvider.GetService(typeof(SVsInfoBarUIFactory)) as IVsInfoBarUIFactory;
    if (infoBarUIFactory == null)
    {
        uiElement = null;
        return false;
    }

    uiElement = infoBarUIFactory.CreateInfoBar(infoBar);
    return uiElement != null;
}
```

### <a name="placement"></a>Platzierung
 Info leisten können an einem oder mehreren der folgenden Speicherorte angezeigt werden:

- Toolfenster

- Innerhalb einer Dokument Registerkarte

> [!IMPORTANT]
> Es ist möglich, eine Info Leiste zu positionieren, um eine Nachricht über den globalen Kontext zu senden. Dies wird zwischen Symbolleisten und Dokument hervorragend angezeigt. Dies wird nicht empfohlen, da dies Probleme mit "Sprung und Ruck" der IDE verursacht und daher vermieden werden sollte, wenn dies nicht unbedingt erforderlich und angemessen ist.

#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>Platzieren einer Info Leiste in einem ToolWindowPane
 Mithilfe der ToolWindowPane. addinfobar (ivsinfobar)-Methode kann einem Tool Fenster eine Infoleiste hinzugefügt werden. Diese API kann entweder ivsinfobar (von dem infobarmodel eine Standard Implementierung ist) oder ein ivsuielement-Element hinzufügen.

#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>Platzieren einer Info Leiste in einem Dokument oder einem nicht-ToolWindowPane
 Verwenden Sie die VSFPROPID_InfoBarHost-Eigenschaft, um den ivsinfobarhost für den Frame zu erhalten, und fügen Sie dann das Info Leiste-UIElement hinzu, um eine Infoleiste in einem IVsWindowFrame zu platzieren.

```
private void AddInfoBar(IVsWindowFrame frame, IVsUIElement uiElement)
{
    IVsInfoBarHost infoBarHost;
    if (TryGetInfoBarHost(frame, out infoBarHost))
    {
        infoBarHost.AddInfoBar(uiElement);
    }
}
private bool TryGetInfoBarHost(IVsWindowFrame frame, out IVsInfoBarHost infoBarHost)
{
    object infoBarHostObj;
    if (ErrorHandler.Failed(frame.GetProperty((int)__VSFPROPID7.VSFPROPID_InfoBarHost, out infoBarHostObj)))
    {
        infoBarHost = null;
        return false;
    }

    infoBarHost = infoBarHostObj as IVsInfoBarHost;
    return infoBarHost != null;
}

```

#### <a name="placing-an-infobar-in-the-main-window"></a>Platzieren einer Info Leiste im Hauptfenster
 Um eine Info Leiste im Hauptfenster zu platzieren, verwenden Sie den VSSPROPID_MainWindowInfoBarHost des IVsShell-Diensts, um das Hauptfenster ivsinfobarhost zu erhalten, und fügen Sie dann das Info Leiste-UIElement hinzu.

### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>Weiß ich, wann der Benutzer in meiner Infobar Aktionen durchführt?
 Ja, wir werden jede Ereignis Aktion an den Info Leiste-Autor zurückgeben. Der Info Leiste-Autor kann dann auf der Grundlage der Benutzer Auswahl in der Info Leiste Aktionen in der IDE durchführen. Info leisten werden automatisch vom Host entfernt, auf dessen Schaltfläche "Schließen" geklickt wurde. es sind jedoch weitere Schritte erforderlich, wenn andere Info leisten nach dem Schließen entfernt werden müssen. Telemetrie muss auch unabhängig von jeder Infobar protokolliert werden.

#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>Empfangen von Info Leiste-Ereignissen in einem ToolWindowPane
 ToolWindowPane verfügt über zwei Ereignisse für Info leisten. Das infobarclosed-Ereignis wird ausgelöst, wenn eine Info Leiste im ToolWindowPane geschlossen wird. Das infobaraktionitemgeklickt-Ereignis wird ausgelöst, wenn auf einen Link oder eine Schaltfläche in der Info Leiste geklickt wird.

#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>Empfangen von Info Leiste-Ereignissen direkt aus dem UIElement
 Ivsinfobaruielement.-Empfehlung kann verwendet werden, um Ereignisse direkt aus dem UIElement-Element einer Infobar zu abonnieren. Durch das Implementieren von ivsinfobaruievents kann der Autor schließen-und Click-Ereignisse empfangen.

```
public interface IVsInfoBarUIEvents
{
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);
}

```

## <a name="error-validation"></a><a name="BKMK_ErrorValidation"></a> Fehlerüberprüfung
 Wenn ein Benutzerinformationen eingibt, die nicht zulässig sind, z. b. Wenn ein erforderliches Feld ausgelassen wird oder wenn Daten im falschen Format eingegeben werden, ist es besser, die Steuerelement Validierung oder das Feedback in der Nähe des Steuer Elements zu verwenden, anstatt ein blockierendes Popup Fehler Dialogfeld zu verwenden

### <a name="field-validation"></a>Feldprüfung
 Die Formular-und Feld Validierung besteht aus drei Komponenten: einem-Steuerelement, einem-Symbol und einer QuickInfo. Obwohl mehrere Steuerelement Typen dies verwenden können, wird ein Textfeld als Beispiel verwendet.

 ![Die Feld Validierung &#40;leer&#41;](../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905-01_FieldValidation")

 Wenn das Feld erforderlich ist, sollte Wasserzeichen Text angegeben werden, **\<Required>** und der Feld Hintergrund sollte hellgelb (vscolor:) sein, `Environment.ControlEditRequiredBackground` und der Vordergrund sollte grau (vscolor: `Environment.ControlEditRequiredHintText` ) lauten:

 ![Feldüberprüfung mit Beschriftung "Erforderlich"](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905-02_FieldValidationRequired")

 Das Programm kann ermitteln, ob sich das Steuerelement in einem *ungültigen Inhalt* befindet, wenn der Fokus auf ein anderes Steuerelement verschoben wird oder wenn der Benutzer auf eine [OK] Commit-Schaltfläche klickt oder wenn der Benutzer das Dokument oder das Formular speichert.

 Wenn der ungültige Inhalts Zustand festgelegt wird, wird ein Symbol entweder im Steuerelement oder direkt daneben angezeigt. Eine QuickInfo, die den Fehler beschreibt, sollte auf dem Mauszeiger auf das Symbol oder das Steuerelement zeigen. Außerdem sollte ein 1-Pixel-Rahmen um das Steuerelement angezeigt werden, das den ungültigen Zustand erstellt.

 ![Layoutspezifikationen für Feldüberprüfung](../../extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905-03_LayoutSpecs")

 **Layoutspezifikationen für die Feld Validierung**

#### <a name="acceptable-variations-for-icon-location"></a>Akzeptable Variationen der Symbol Position
 Es gibt unzählige einmalige Fälle, in denen Benutzer über Validierungs Fehler informiert werden müssen. Wenn Sie den Steuerungstyp und die Konfiguration der Benutzeroberfläche berücksichtigen, wählen Sie die für Ihre Situation geeignete Symbolplatzierung aus.

 ![Zulässige Positionen für Symbolplatzierung](../../extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905-04_IconLocation")

 **Akzeptable Variationen für Symbol Speicherorte für Feld Validierung**

#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>Validierung, die einen Roundtrip zu einer Server-oder Netzwerkverbindung erfordert
 In einigen Fällen ist ein Roundtrip zum Server erforderlich, um den Inhalt zu überprüfen, und es ist wichtig, den Status des Benutzers, überprüft und Fehler anzuzeigen. Die folgende Abbildung zeigt ein Beispiel für diesen Fall und die empfohlene Benutzeroberfläche.

 ![Validierung mit Roundtrip zu einem Server](../../extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905-05_RoundTrip")

 **Validierung mit Roundtrip zu einem Server**

 Beachten Sie, dass ausreichend freier Speicherplatz auf der rechten Seite des-Steuer Elements bereitgestellt werden muss, um die "Überprüfung..." und wiederholen Sie den Text.

#### <a name="in-place-warning-text"></a>Direkter Warn Text
 Wenn genügend Platz zur Verfügung steht, um die Fehlermeldung in der Nähe des Steuer Elements in einem Fehlerzustand zu platzieren, empfiehlt es sich, die QuickInfo allein zu verwenden.

 ![Warnung in&#45;Ort](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905-06_InPlaceWarning")

 **Direkter Warn Text**

#### <a name="watermarks"></a>Wasserzeichen
 Manchmal befindet sich ein gesamtes Steuerelement oder Fenster in einem Fehlerzustand. Verwenden Sie in dieser Situation ein Wasserzeichen, um den Fehler anzugeben.

 ![Wasserzeichen](../../extensibility/ux-guidelines/media/0905-07_watermark.png "0905-07_Watermark")

 **Überprüfung des Wasserzeichen Felds**
