---
title: R-Arbeitsbereiche
description: Steuern des Ausführungsorts von R-Code mithilfe von Workspaces in Visual Studio.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 3627a8944941fc77bb9b19fe3dd0a1549f41892a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961585"
---
# <a name="control-where-r-code-runs-with-workspaces"></a>Steuern, wo R-Code mit Arbeitsbereichen ausgeführt wird

Mit einem Arbeitsbereich in R Tools für Visual Studio (RTVS) lässt sich konfigurieren, wo eine R-Sitzung ausgeführt wird (lokal oder auf Remotecomputern). Das Ziel ist, Ihnen in beiden Fällen die Arbeit auf einer vergleichbaren Benutzeroberfläche zu ermöglichen, sodass Sie leistungsfähigere cloudbasierte Computer nutzen können.

Verwenden Sie zum Öffnen des Fensters **Arbeitsbereiche** den Befehl **R Tools** > **Windows** > **Arbeitsbereiche**,oder drücken Sie **STRG**+**9**.

![Fenster „Arbeitsbereiche“ in R Tools für Visual Studio (VS 2017)](media/workspaces-window.png)

Das grüne Häkchen in diesem Fenster gibt den aktiven Arbeitsbereich an, mit dem RTVS verbunden ist. Der blaue Pfeil legt den aktiven Arbeitsbereich fest. Über das Einstellungssymbol (Zahnrad) rechts neben jedem Arbeitsbereich können Sie den Namen, den Speicherort und die Befehlszeilenargumente ändern. Mit dem roten X wird ein manuell hinzugefügter Arbeitsbereich entfernt.

## <a name="save-and-reset-a-workspace"></a>Speichern und Zurücksetzen eines Arbeitsbereichs

In der Standardeinstellung speichert RTVS den Zustand von Arbeitsbereichen beim Schließen und erneuten Öffnen eines Projekts nicht. Sie können dieses Verhalten jedoch über die [Arbeitsbereichsoptionen](options-for-r-tools-in-visual-studio.md#workspace) ändern.

Mit dem Befehl **R Tools** > **Sitzung** > **Zurücksetzen** und über die Symbolleistenschaltfläche „Zurücksetzen“ im interaktiven Fenster wird der Zustand von Arbeitsbereichen auch jederzeit zurückgesetzt. Bei Remotearbeitsbereichen wird beim Zurücksetzen das Benutzerprofil gelöscht, das bei der ersten Anmeldung beim Remoteserver erstellt wurde. Dadurch werden effektiv alle Dateien gelöscht, die dort gesammelt wurden.

## <a name="local-workspaces"></a>Lokale Arbeitsbereiche

Die Liste lokaler Arbeitsbereiche führt alle R-Interpreter auf, die auf Ihrem Computer installiert sind.

RTVS versucht, automatisch alle installierten Versionen von R zu erkennen, indem der **HKEY_LOCAL_MACHINE\Software\R-Core\\** -Registrierungsschlüssel beim Start von Visual Studio durchsucht wird. Da diese Überprüfung nur beim Start ausgeführt wird, müssen Sie Visual Studio neu starten, wenn Sie einen neuen R-Interpreter installieren.

RTVS erkennt möglicherweise keine R-Interpreter, die auf nicht standardmäßige Weise installiert wurden (z.B. durch Kopieren von Dateien in einen Ordner statt eines Installationsprogramms). Erstellen Sie in diesem Fall wie folgt einen neuen lokalen R-Arbeitsbereich:

1. Wählen Sie im Fenster „Arbeitsbereiche“ die Schaltfläche **Hinzufügen** aus.
1. Geben Sie einen Namen für den neuen Arbeitsbereich ein.
1. Geben Sie den Pfad zum R-Stammordner, der den *bin*-Ordner mit den Interpreter enthält, und optionale Befehlszeilenargumente ein, damit der Interpreter beim Start von RTVS übergeben wird.
1. Wählen Sie **Speichern** aus, wenn Sie fertig sind.

![Einen neuen Arbeitsbereich hinzufügen](media/workspaces-add-new.png)

## <a name="remote-workspaces"></a>Remotearbeitsbereiche

Mit Remotearbeitsbereichen können Sie auf einem Remotecomputer eine Verbindung zu einer R-Sitzung herstellen. (Informationen zum Konfigurieren eines Computers für diesen Zweck finden Sie unter [Einrichten von Remotearbeitsbereichen](setting-up-remote-r-workspaces.md).)

Remotearbeitsbereiche werden nicht automatisch von Visual Studio erkannt. Deshalb müssen Sie sie manuell mithilfe der Schaltfläche **Hinzufügen** im Fenster „Arbeitsbereiche“ hinzufügen, wie im vorherigen Abschnitt beschrieben. Geben Sie in diesem Fall statt eines lokalen Pfads den URI des Remotecomputers ein.

> [!Important]
> Remotearbeitsbereiche werden über einen URI identifiziert, der *das HTTPS-Protokoll verwenden* muss, damit die Vertraulichkeit und Integrität der Kommunikation mit dem Remotecomputer gewährleistet wird. Visual Studio stellt keine Verbindung mit einem Remotecomputer her, der HTTPS nicht unterstützt.

> [!Note]
> Remotearbeitsbereiche befinden sich in der Vorschau. Wir arbeiten für ein künftiges Release an einer besseren Implementierung des Problems bei der Dateisynchronisierung und freuen uns über Ihre Ideen und Ihr Feedback.

## <a name="remote-workspace-logon"></a>Anmeldung bei einem Remotearbeitsbereich

Sie benötigen einen Benutzernamen und ein Kennwort, um sich im Remotearbeitsbereich anzumelden.

### <a name="logon-to-windows-workspace"></a>Melden Sie sich im Windows-Arbeitsbereich an

Wenn Ihr Remotecomputer für die Verwendung Ihres Domänenkontos eingerichtet ist, können Sie Ihre Domänenanmeldung verwenden, um Zugriff auf einen Remotearbeitsbereich zu erhalten. Wenn das nicht der Fall ist, müssen Sie das `machine-name\username`-Format für die Anmeldung über ein Computerkonto auf dem Remotecomputer verwenden.

### <a name="logon-to-linux-workspace"></a>Anmeldung bei einem Linux-Arbeitsbereich

Verwenden Sie das `<<unix>>\username`-Format, um sich bei einem Linux-Konto anzumelden. Wenn Sie zum Beispiel ein Konto mit dem Namen `ruser` besitzen, müssen Sie den Benutzernamen als `<<unix>>\ruser` eingeben.

## <a name="switch-between-workspaces"></a>Wechseln zwischen Arbeitsbereichen

RTVS ist immer nur an einen Arbeitsbereich gebunden. Der gebundene Arbeitsbereich wird durch ein kleines grünes Häkchen im Fenster „Arbeitsbereiche“ angezeigt. Standardmäßig wird RTVS mit dem letzten lokalen Arbeitsbereich verbunden, den Sie in einer vorherigen Sitzung geöffnet haben.

Um den aktiven Arbeitsbereich zu ändern, wählen Sie den blauen Pfeil neben dem gewünschten Arbeitsbereich aus. Daraufhin werden Sie zum Speichern der Sitzung aufgefordert, der aktuelle Arbeitsbereich wird beendet, und es wird zum neuen Arbeitsbereich gewechselt.

> [!Tip]
> Wählen Sie zur Deaktivierung der Speicheraufforderung den Befehl **R Tools** > **Optionen** aus, und legen Sie die Option **Vor dem Arbeitsbereichswechsel Bestätigungsdialogfeld anzeigen** auf `No` fest. Informationen finden Sie unter [R Tools for Visual Studio options (Optionen in R Tools für Visual Studio)](options-for-r-tools-in-visual-studio.md#workspace).

Wenn Sie versuchen, zu einem lokalen Arbeitsbereich zu wechseln, der deinstalliert oder in einem nicht verfügbaren Remotearbeitsbereich installiert wurde, kann RTVS auch mit gar keinem Arbeitsbereich verbunden sein. Infolge wird möglicherweise ein Fehler angezeigt, wenn Sie im interaktiven Fenster Code eingeben oder versuchen, den Code auf andere Weise auszuführen:

![Fehler, wenn kein Arbeitsbereich mit RTVS verbunden ist](media/workspaces-disconnected-interactive-window.png)

Um dies zu korrigieren, wechseln Sie im Fenster „Arbeitsbereiche“ zu einem anderen Arbeitsbereich. Wenn kein Arbeitsbereich verfügbar ist, müssen Sie einen R-Interpreter installieren. Sie können auch versuchen, Visual Studio neu zu starten, falls Sie während der Ausführung von Visual Studio einen Interpreter installiert haben.

### <a name="switch-to-a-remote-workspace"></a>Wechseln zu einem Remotearbeitsbereich

RTVS fordert Sie bei der ersten Verbindungserstellung mit einem Remotearbeitsbereich zur Eingabe von Anmeldeinformationen auf und speichert die Anmeldeinformationen dann (mithilfe des sicheren Schließfachs für Anmeldeinformationen) für späteren Sitzungen im Cache. Kommunikation mit dem Remoteserver erfolgt sicher über HTTPS (erforderlich).

Je nach Serverkonfiguration wird bei der Verbindungserstellung die folgende Zertifikatwarnung angezeigt: „The security certificate presented by the Remote R Services does not allow us to prove that you are indeed connecting to the machine (name)“ (Anhand des von den Remote-R Services vorgelegten Sicherheitszertifikats können wir nicht nachweisen, dass Sie tatsächlich eine Verbindung mit dem Computer (Name) herstellen).

![Selbstsignierte Zertifikatwarnung beim Verbinden mit einem Remotearbeitsbereich](media/workspaces-remote-self-signed-certificate-warning.png)

Das Zertifikat ist ein Dokument, das vom Computer, mit dem Sie eine Verbindung herstellen möchten, an RTVS übergeben wird. Das Zertifikat enthält ein Feld, das den URI des Computers identifiziert. Die Warnung wird angezeigt, wenn RTVS einen Konflikt zwischen dem URI im Zertifikat und dem zum Verbinden mit dem Computer verwendeten URI erkennt, und gibt an, dass die Sicherheit des Servers möglicherweise gefährdet ist.

Diese Warnung wird aber auch angezeigt, wenn statt eines vertrauenswürdigen Anbieters ein *selbstsigniertes Zertifikat* zur Aktivierung von HTTPS auf einem Remotecomputer verwendet wurde. Weitere Informationen finden Sie unter [Einrichten von Remotearbeitsbereichen](setting-up-remote-r-workspaces.md).

## <a name="directories-on-local-and-remote-computers"></a>Verzeichnisse auf lokalen und Remotecomputern

Wenn Sie einen neuen R-Interpreter in einem lokalen Arbeitsbereich starten, lautet Ihr aktuelles Arbeitsverzeichnis standardmäßig *%userprofile%\Documents*. Sie können dieses Verzeichnis jederzeit mithilfe der Befehle **R Tools** > **Arbeitsverzeichnis** ändern, oder indem Sie einen Rechtsklick auf ein Projekt im Projektmappen-Explorer von Visual Studio machen und Befehle wie **Arbeitsverzeichnis hier festlegen** auswählen.

Auf Remotecomputern erstellt RTVS bei der ersten Verbindungserstellung zu dem Server automatisch ein Benutzerprofil anhand Ihrer Anmeldeinformationen, damit das Arbeitsverzeichnis in diesem Profil der *Documents*-Ordner ist. Der Ordner wird für alle nachfolgenden Remotesitzungen verwendet, die die gleichen Anmeldeinformationen verwenden.

Daher kann sich der exakte Speicherort, an dem Ihr Code ausgeführt wird, bei lokalen und Remotearbeitsbereichen unterscheiden. Verwenden Sie dann in Ihrem Code immer relative Pfade zu Datendateien o.ä., damit Ihr Code arbeitsbereichübergeifend portabel ist.

Beachten Sie außerdem, dass bei Remotearbeitsbereichen alle Dateien im Arbeitsverzeichnis für ein Benutzerprofil sitzungsübergreifend beibehalten werden. Wie bereits erwähnt, können Sie diese Dateien mit dem Befehl **R Tools** > **Sitzung** > **Zurücksetzen** löschen (oder über die Schaltfläche „Zurücksetzen“ im interaktiven Fenster), wenn Sie einen Remotearbeitsbereich verwenden. Durch diesen Befehl wird das Benutzerprofil erneut vom Server gelöscht. Beim Wiederherstellen der Verbindung wird auch das Profil wiederhergestellt.

## <a name="copy-project-files-to-remote-workspaces"></a>Kopieren von Projektdateien in Remotearbeitsbereiche

Beim Arbeiten mit R-Projekten in Visual Studio hat der lokale Computer immer die neuesten Projektdateien, selbst wenn Sie einen Remotearbeitsbereich verwenden. Das bedeutet, dass wenn Sie ein Projekt in Visual Studio öffnen (in der Regel bedeutet dies, eine Projektmappe mit einem Projekt zu öffnen), nimmt RTVS an, dass sich der Inhalt des Projekts vollständig auf dem lokalen Computer befindet. Der Remotearbeitsbereich ist im Grunde nur ein temporärer Host für die Projektdateien und die Codeausgabe. Dies bedeutet beispielsweise, dass beim Laden einer Datei mithilfe von `source` im interaktiven Fenster die Datei bereits mit dem angegebenen Pfad auf dem Remotecomputer oder im aktuellen Arbeitsverzeichnis des R-Remoteinterpreters vorhanden sein muss (festgelegt mit der `setwd()`-Funktion).

Dateien werden wie folgt auf den Remoteserver kopiert:

- Damit Sie über das interaktive Fenster remote mit Dateien arbeiten können, müssen Sie diese Dateien (oder das Projekt) zunächst manuell mit einem Rechtsklick im Projektmappen-Explorer kopieren und **Quelle ausgewählt** auswählen. Einzelne Dateien werden in das Arbeitsverzeichnis auf dem Server kopiert. Beim Kopieren eines Projekts erstellt RTVS einen Projektordner.

- Sie können Dateien auch kopieren, indem Sie sie im Projektmappen-Explorer und dann die Option **Ausgewählte Datei(en) einbinden** auswählen. Durch diese Aktion werden sie in das interaktive Fenster geladen und dort ausgeführt. Wenn die Sitzung mit einem Remotecomputer verbunden ist, werden die Dateien zuerst dorthin kopiert.

- Wenn RTVS mit einem Remotearbeitsbereich verbunden ist und Sie die Taste **F5** drücken, **Debuggen** > **Debugging starten** auswählen oder die Ausführung Ihres Codes auf andere Weise starten, kopiert RTVS die Projektdatei standardmäßig automatisch in den Remotearbeitsbereich (Informationen zur Steuerung dieses Verhaltens finden Sie weiter unten).

- Alle Dateien, die bereits auf dem Server vorhanden sind, werden überschrieben.

> [!Note]
> Da RTVS nicht alle R-Funktionsaufrufe zuverlässig abfangen kann, werden Dateien durch das Aufrufen von Funktionen wie `source()` oder `runApp()` (für Shiny-Anwendungen) über das interaktive Fenster *nicht* in den Remotearbeitsbereich kopiert.

Ob RTVS bei der Ausführung eines Projekts Dateien kopiert, und welche Dateien kopiert werden, wird über die [Projekteigenschaften](r-projects-in-visual-studio.md#project-properties) gesteuert. Wählen Sie zum Öffnen dieser Seite den Menübefehl **Projekt** >  **(Name) Eigenschaften** aus, oder klicken Sie mit der rechten Maustaste im Projektmappen-Explorer auf das Projekt, und wählen Sie **Eigenschaften** aus.

![Ausführungsregisterkarte der Projekteigenschaften mit den Einstellungen für die Übertragung von Dateien](media/workspaces-remote-file-transfer-filter-settings.png)

Hier bestimmt die Eigenschaft **Transfer files on run** (Dateien bei der Ausführung übertragen), ob RTVS Projektdateien automatisch kopiert. Der Wert der **Dateien für die Übertragung** filtert dann genau, welche Dateien übertragen werden. Standardmäßig werden nur *R*-, *RMD*-, *SQL*-, *MD*- und *CPP*-Dateien kopiert. Mit diesem Verhalten wird vermieden, dass versehentlich große Datendateien mit jeder Ausführung auf den Server kopiert werden.

## <a name="copy-files-from-a-remote-workspace"></a>Kopieren von Dateien aus einem Remotearbeitsbereich

Wenn Ihr R-Skript auf dem Server Dateien generiert, können Sie diese Dateien mithilfe der `rtvs::fetch_file`-Funktion zurück auf den Client kopieren. Diese Funktion akzeptiert mindestens den Remotepfad zur Datei, die Sie auf den Computer kopieren möchten, und optional den Pfad auf Ihrem Computer. Wenn Sie keinen Pfad angeben, wird die Datei in Ihren Ordner *%userprofile%\Downloads* kopiert.
