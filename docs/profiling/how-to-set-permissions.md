---
title: Festlegen von Berechtigungen | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie ein Administrator eines Computers einem Benutzer oder einer Gruppe, die über keine Berechtigungen eines Administrators verfügt, die für die Profilerstellung erforderlichen Sicherheitsberechtigungen gewähren kann.
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profiling, setting permissions
- security [Visual Studio ALM], setting permissions
- permissions [Visual Studio ALM], profiling
- profiling tools, setting profiling permissions
- performance tools, setting profiling permissions
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2ab51b317164b8f2e828e0327021fb595574583c
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721995"
---
# <a name="how-to-set-permissions"></a>Vorgehensweise: Festlegen von Berechtigungen

In diesem Artikel wird beschrieben, wie ein Administrator eines Computers die erforderlichen Sicherheitsberechtigungen für die Profilerstellung für einen Benutzer oder eine Gruppe, die keine Administratorberechtigungen auf diesem Computer haben, gewährt.

Ein grundlegendes Sicherheitsprinzip gibt an, dass die Anwendung mit nicht mehr als den Berechtigungen ausgeführt werden soll, die sie benötigen. Dieses Prinzip gilt auch für Benutzer. Wenn Benutzer vollständig wirksam werden können, wenn sie als Mitglieder der Benutzergruppe anstelle der Administratorgruppe angemeldet sind, sollten sie keine Administratorberechtigungen erteilt bekommen. Die erste Prozedur, "So erstellen Sie ein Benutzerkonto mit Benutzerberechtigungen", beschreibt das Erstellen eines Benutzerkontos für ein Mitglied der Benutzergruppe.

Mitglieder der Benutzergruppe benötigen Zugriff auf die Ordner und Dateien auf dem Datenträger, die mit anderen Mitgliedern des Teams gemeinsam verwendet werden. Die zweite Prozedur, „So erteilen Sie den Zugriff auf gemeinsam genutzte Projektdateien“, beschreibt, wie Sie diesen Zugriff gewähren.

Mitglieder der Benutzergruppe können die Profilerstellungstools ausführen, wenn ein Administrator ihnen Zugriff auf die Softwaretreiber für die Profilerstellungsgstools erteilt. Die letzte Prozedur, „So erteilen Sie den Zugriff auf den Treiber für die Profilerstellung“, beschreibt, wie Sie den Zugriff auf diesen Treiber gewähren.

> [!NOTE]
> Sie benötigen Administratorberechtigungen, um die Schritte in diesen Prozeduren ausführen zu können.

## <a name="to-create-a-user-account-that-has-user-permissions"></a>So erstellen Sie ein Benutzerkonto mit Benutzerberechtigungen

1. Klicken Sie mit der rechten Maustaste auf **Arbeitsplatz** und anschließend auf **Verwalten**.

     Das Fenster **Computerverwaltung** wird geöffnet.

2. Erweitern Sie **Lokale Benutzer und Gruppen**.

3. Klicken Sie mit der rechten Maustaste auf den Ordner **Benutzer** und anschließend auf **Neuer Benutzer**.

     Das Dialogfeld **Neuer Benutzer** wird angezeigt.

4. Füllen Sie die Felder im Dialogfeld mit den Informationen für das Benutzerkonto aus, das Sie gerade erstellen. Geben Sie ein Passwort ein. Optional: Wählen Sie das Kontrollkästchen aus, das erfordert, dass der Benutzer das Passwort bei der nächsten Anmeldung ändert.

5. Klicken Sie auf **Erstellen** und anschließend auf **Schließen**.

     Der neue Benutzer wird in der Benutzergruppe erscheinen, eine Gruppe von Benutzern, die nicht über Administratorberechtigungen verfügen.

## <a name="to-grant-access-to-shared-project-files"></a>So erteilen Sie den Zugriff auf gemeinsam genutzte Projektdateien

1. Suchen Sie in Windows Explorer (oder Datei-Explorer) nach den Stamm der Ordnerstruktur für die Projektdateien, von diesem Benutzer verwendet und vom Projektteam freigegeben werden.

     Der Pfad dieses Ordners könnte folgendermaßen aussehen:

    ```cmd
    D:\ourProject
    ```

2. Klicken Sie mit der rechten Maustaste auf den Ordner und anschließend auf **Eigenschaften**.

     Daraufhin wird das Dialogfeld **\<folder name>-Eigenschaften** angezeigt.

3. Klicken Sie auf die Registerkarte **Sicherheit** .

4. Klicken Sie auf den Namen eines Benutzerkontos im Feld **Gruppen- oder Benutzernamen**.

5. Aktivieren Sie im Feld **Berechtigungen für \<user name>** das Kontrollkästchen für **Vollzugriff**.

6. Klicken Sie auf **OK**.

     Erteilt dem Benutzer die Berechtigung für die freigegebene Ordnerstruktur, die mit dem in Schritt 5 ausgewählten Ordner beginnt.

## <a name="to-grant-access-to-the-profiling-driver"></a>So erteilen Sie den Zugriff auf den Treiber für die Profilerstellung

1. Öffnen Sie eine Eingabeaufforderung als Administrator.

2. Wechseln Sie zu folgendem Verzeichnis:

    ```cmd
    <drive>:\Program Files\Microsoft Visual Studio 14\Team Tools\Performance Tools
    ```

3. Führen Sie den folgenden Befehl aus:

    ```cmd
    vsperfcmd /admin:driver,start /admin:service,start
    ```

     Dieser Befehl installiert und startet den Treiber für die Profilerstellungstools.

     Dieser Befehl startet den Profilerstellungstreiber und -dienst so, dass Benutzer ohne Administratorrechte Profilerstellungsfunktionen verwenden können, die in ihrem Benutzerprozessbereich verfügbar sind. Nur ein Administrator kann den Befehl ausführen; und es wird bei Benutzern ohne Administratorrechte fehlschlagen.

     Beachten Sie, dass die Effekte in diesem Schritt nach dem Neustart des Computers rückgängig gemacht werden, es sei denn, Sie führen auch den letzten Schritt in dieser Prozedur aus.

4. Führen Sie den Befehl aus, um den Zugriff auf die Funktionalität des Profilerstellungstreibers durch einen Benutzer oder eine Gruppe zu gewähren, die keinen Administratorzugriff auf den Computer haben:

    ```cmd
    vsperfcmd /admin:security,allow,<right[,right],<user name|group name>
    ```

     Dieser Befehl gewährt dem \<user name>- oder \<group name>-Konto den Zugriff auf die Profilerstellungstools. Mit der Option \<right> werden die Profilerstellungsfunktionen bestimmt, auf die der Benutzer zugreifen kann. Mit der Option \<right> können folgende Werte festgelegt werden:

    - FullAccess – ermöglicht den Zugriff auf alle Profilerstellungsmethoden, einschließlich dem Erfassen von Leistungsdaten von Diensten, dem Sampling und der sitzungsübergreifenden Profilerstellung.

    - SampleProfiling – ermöglicht den Zugriff auf Sampling-Profilerstellungsmethoden.

    - CrossSession – ermöglicht den Zugriff auf die sitzungsübergreifende Profilerstellung, die für Profilerstellungsdienste erforderlich ist.

5. Optional: Um die Ergebnisse der vorherigen Schritte nach dem Computerneustart zu erhalten, führen Sie den folgenden Befehl ein:

    ```cmd
    vsperfcmd /admin:driver,autostart,on
    ```

   Die angegebenen Benutzer werden nun nach der Anmeldung in der Lage sein, die Profilerstellungstools ohne Administratorberechtigungen zu verwenden.

## <a name="see-also"></a>Siehe auch

[Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)
[VSPerfCmd](../profiling/vsperfcmd.md)
[Profilerstellung und Sicherheit in Windows Vista](../profiling/profiling-and-windows-vista-security.md)
