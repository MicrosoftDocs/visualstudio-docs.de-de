---
title: 'Exemplarische Vorgehensweise: Bereitstellen eines Projekts Aufgabenliste Definition | Microsoft-Dokumentation'
description: Verwenden Sie in dieser exemplarischen Vorgehensweise Visual Studio zum Erstellen, anpassen, Debuggen und Bereitstellen einer SharePoint-Liste, um Projektaufgaben zu verfolgen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0be8eed2dc41ad433c0e0514dfd34e3c6e3d7193
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/24/2020
ms.locfileid: "95970428"
---
# <a name="walkthrough-deploy-a-project-task-list-definition"></a>Exemplarische Vorgehensweise: Bereitstellen einer Aufgabenlisten Definition für Projekte

In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie mit [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] eine SharePoint-Liste erstellen, anpassen, Debuggen und bereitstellen, um Projektaufgaben zu verfolgen.

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Voraussetzungen

- Unterstützte Editionen von Microsoft Windows und SharePoint.

- Visual Studio 2017 oder Azure DevOps Services.

## <a name="create-a-sharepoint-list"></a>Erstellen einer SharePoint-Liste

Erstellen Sie ein SharePoint-Listen Projekt, und ordnen Sie die Listen Definition Aufgaben zu.

1. Öffnen Sie das Dialogfeld **Neues Projekt** , erweitern Sie den Knoten **SharePoint** , und wählen Sie dann den Knoten **2010** aus.

2. Wählen Sie im Bereich **Vorlagen** die Vorlage **SharePoint 2010-Projekt** aus, benennen Sie das Projekt **projecttasklist**, und wählen Sie dann die Schaltfläche **OK** aus.

     Der Assistent zum Anpassen von **SharePoint** wird angezeigt.

3. Geben Sie die lokale SharePoint-Website an, die Sie für das Debugging verwenden, wählen Sie das Optionsfeld **als Farm Lösung** bereitstellen aus, und klicken Sie dann auf die Schaltfläche **Fertig** stellen

4. Öffnen Sie das Kontextmenü für das Projekt, und wählen **Add** Sie dann  >  **Neues Element** hinzufügen aus.

5. Wählen Sie im Bereich **Vorlagen** die **Liste** Vorlage aus, und klicken Sie dann auf die Schaltfläche **Hinzufügen** .

     Der Assistent zum Anpassen von **SharePoint** wird angezeigt.

6. Geben Sie im Feld **welchen Namen möchten Sie für die Liste anzeigen? den Namen** **Project Aufgabenliste** ein.

7. Wählen Sie das Optionsfeld **nicht anpassbare Liste basierend auf einem vorhandenen Listentyp aus** , und wählen Sie dann in der Liste **Tasks** aus, und klicken Sie dann auf die Schaltfläche **Fertig** stellen.

     Die Liste, das Feature und das Paket werden in **Projektmappen-Explorer** angezeigt.

## <a name="add-an-event-receiver"></a>Hinzufügen eines Ereignis Empfängers

In der Aufgabenliste können Sie einen Ereignis Empfänger hinzufügen, der automatisch das Fälligkeitsdatum und die Beschreibung der Aufgabe festlegt. Das folgende Verfahren fügt der Listen Instanz einen einfachen Ereignishandler als Ereignis Empfänger hinzu.

1. Öffnen Sie das Kontextmenü für den Projekt Knoten, wählen Sie **Hinzufügen** aus, und wählen Sie dann **Neues Element** aus.

2. Wählen Sie in der Liste der SharePoint-Vorlagen die Vorlage **Ereignis Empfänger** aus, und nennen Sie Sie **projecttasklisteventreceiver**.

     Der Assistent zum Anpassen von **SharePoint** wird angezeigt.

3. Wählen Sie auf der Seite **Ereignis Empfänger Einstellungen auswählen** die Option **Element Ereignisse** als Ereignis Empfängertyp auflisten in der Liste **welche Art von Ereignis Empfänger möchten Sie auflisten aus** .

4. Wählen Sie in der Liste **welches Element soll die Ereignis Quelle sein aus die** Option **Tasks** aus.

5. Aktivieren Sie in der Liste der zu behandelnden Ereignisse das Kontrollkästchen neben **einem hinzugefügten Element**, und wählen Sie dann die Schaltfläche **Fertig** stellen aus.

     Dem Projekt wird ein neuer Ereignis Empfänger Knoten mit einer Codedatei mit dem Namen **projecttasklisteventreceiver** hinzugefügt.

6. Fügen Sie der- `ItemAdded` Methode in der Codedatei **projecttasklisteventreceiver** Code hinzu. Jedes Mal, wenn eine neue Aufgabe hinzugefügt wird, wird der Aufgabe ein Standard Fälligkeitsdatum und eine Beschreibung hinzugefügt. Das Standard Fälligkeitsdatum ist der 1. Juli 2009.

     [!code-vb[SPProjectTaskList#1](../sharepoint/codesnippet/VisualBasic/projecttasklist1/projecttasklisteventreceiver/projecttasklisteventreceiver.vb#1)]
     [!code-csharp[SPProjectTaskList#1](../sharepoint/codesnippet/CSharp/projecttasklist/projecttasklisteventreceiver/projecttasklisteventreceiver.cs#1)]

## <a name="customize-the-project-task-list-feature"></a>Anpassen des Features der Projektaufgaben Liste

Wenn Sie eine SharePoint-Lösung erstellen, erstellt Visual Studio automatisch Funktionen für die Standard Projekt Elemente. Sie können die Einstellungen für die Projektaufgaben Liste für die SharePoint-Website mithilfe des Funktions-Designers anpassen.

1. Erweitern Sie in **Projektmappen-Explorer** den Knoten **Features**.

2. Öffnen Sie das Kontextmenü für **Feature1**, und wählen Sie dann **Ansicht-Designer** aus.

3. Geben Sie im Feld **Titel** den Namen **Project Aufgabenliste Feature** ein.

4. Wählen Sie in der Liste **Bereich** die Option **Web** aus.

5. Geben Sie im Fenster **Eigenschaften** **1.0.0.0** als Wert für die Eigenschaft **Version** ein.

## <a name="customize-the-project-task-list-package"></a>Anpassen des Projektaufgaben Listen Pakets

Wenn Sie ein SharePoint-Projekt erstellen, fügt Visual Studio dem Paket automatisch die Features hinzu, die die Standard Projekt Elemente enthalten. Mithilfe des Paket-Designers können Sie die Einstellungen für die Projektaufgaben Liste für die SharePoint-Website anpassen.

1. Öffnen Sie in **SolutionExplorer** das Kontextmenü für das **Paket**, und wählen Sie dann **Ansicht-Designer** aus.

2. Geben Sie im Feld **Name den Namen** **projecttasklistpackage** ein.

3. Aktivieren Sie das Kontrollkästchen **Webserver zurücksetzen** .

## <a name="build-and-test-the-project-task-list"></a>Erstellen und Testen der Projektaufgaben Liste

Wenn Sie das Projekt ausführen, wird die SharePoint-Website geöffnet. Sie müssen jedoch manuell zum Speicherort der Aufgabenliste navigieren.

1. Drücken Sie die Taste **F5** , um die Projektaufgaben Liste zu erstellen und bereitzustellen.

     Die SharePoint-Website wird geöffnet.

2. Wählen Sie die Registerkarte **Start** aus.

3. Wählen Sie in der linken Rand Leiste den **Aufgabenliste Link Project** aus.

     Die Seite Projekt Aufgabenliste wird angezeigt.

4. Wählen Sie auf der Registerkarte **Listen Tools** die Registerkarte **Elemente** aus.

5. Wählen Sie in der Gruppe **Elemente** die Schaltfläche **Neues Element** aus.

6. Geben Sie **task1** in das Textfeld **Titel** ein.

7. Klicken Sie auf die Schaltfläche **Speichern** .

     Nachdem der Standort aktualisiert wurde, wird der Task **task1** mit einem Fälligkeitsdatum von 7/1/2009 angezeigt.

8. Wählen Sie **task1** aus.

     Die detaillierte Ansicht der Aufgabe wird angezeigt, und die Beschreibung zeigt "Dies ist eine wichtige Aufgabe".

## <a name="deploy-the-project-task-list"></a>Bereitstellen der Projektaufgaben Liste

Nachdem Sie die Projektaufgaben Liste erstellt und getestet haben, können Sie Sie auf dem *lokalen System* oder einem *Remote System* bereitstellen. Beim lokalen System handelt es sich um den Computer, auf dem Sie die Lösung entwickelt haben, während es sich bei einem Remote System um einen anderen Computer handelt.

### <a name="to-deploy-the-project-task-list-to-the-local-system"></a>So stellen Sie die Projektaufgaben Liste auf dem lokalen System bereit

Wählen Sie in der Visual Studio-Menüleiste erstellen Projekt Mappe **Erstellen** aus  >  **Deploy Solution**.

Visual Studio wieder verwendet den IIS-Anwendungs Pool, zieht alle vorhandenen Versionen der Projekt Mappe zurück, kopiert die Projektmappenpaketdatei (*. wsp*) nach SharePoint und aktiviert dann seine Features. Sie können jetzt die Projekt Mappe in SharePoint verwenden. Weitere Informationen zu Bereitstellungs Konfigurationsschritten finden Sie unter Gewusst [wie: Bearbeiten einer SharePoint-Bereitstellungs Konfiguration](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).

### <a name="to-deploy-the-project-task-list-to-a-remote-system"></a>So stellen Sie die Projektaufgaben Liste auf einem Remote System bereit

1. Wählen Sie in der Visual Studio-Menüleiste die Option **Build**  >  **veröffentlichen** aus.

2. Klicken Sie im Dialogfeld **veröffentlichen** auf das Optionsfeld **in Datei System veröffentlichen** .

     Sie können den Zielort im Dialogfeld **veröffentlichen** ändern, indem Sie auf das ![Symbol](../sharepoint/media/ellipsisicon.gif "Symbol "Ellipse"") mit den Auslassungs Punkten mit den Auslassungs Punkten klicken und dann zu einem anderen Speicherort navigieren.

3. Klicken Sie auf die Schaltfläche **Veröffentlichen**.

     Eine *wsp* -Datei wird für die Projekt Mappe erstellt.

4. Kopieren Sie die *wsp* -Datei auf das Remote-SharePoint-System.

5. Verwenden Sie den PowerShell- `Add-SPUserSolution` Befehl, um das Paket auf der Remote-SharePoint-Installation zu installieren. (Verwenden Sie für Farm Lösungen den `Add-SPSolution` Befehl.)

     Beispiel: `Add-SPUserSolution C:\MyProjects\ProjectTaskList\ProjectTaskList\bin\Debug\ProjectTaskList.wsp`.

6. Verwenden Sie den PowerShell- `Install-SPUserSolution` Befehl, um die Lösung bereitzustellen. (Verwenden Sie für Farm Lösungen den `Install-SPSolution` Befehl.)

     Beispiel: `Install-SPUserSolution -Identity ProjectTaskList.wsp -Site http://NewSiteName`.

     Weitere Informationen zur Remote Bereitstellung finden [Sie unter Verwenden von Lösungen](/previous-versions/office/developer/sharepoint-2010/ee534972(v=office.14)) und hinzufügen und Bereitstellen von [Lösungen mit PowerShell in SharePoint 2010](http://www.dotnetmafia.com/blogs/dotnettipoftheday/archive/2009/12/02/adding-and-deploying-solutions-with-powershell-in-sharepoint-2010.aspx).

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Anpassen und Bereitstellen von SharePoint-Lösungen finden Sie in den folgenden Themen:

- [Exemplarische Vorgehensweise: Erstellen einer Websitespalte, eines Inhaltstyps und einer Liste für SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)

- [Vorgehensweise: Erstellen eines Ereignisempfängers](../sharepoint/how-to-create-an-event-receiver.md)

- [Windows PowerShell für SharePoint Server 2010](/powershell/module/sharepoint-server)

## <a name="see-also"></a>Weitere Informationen
[Packen und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
