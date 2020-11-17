---
title: Bereitstellen, veröffentlichen, & aktualisieren von SharePoint-Lösungs Paketen
description: Bereitstellen, veröffentlichen und Aktualisieren von SharePoint-Lösungs Paketen. Passen Sie den Bereitstellungs Prozess an. Veröffentlichen von Paketen auf einem Remote Server oder einem lokalen Server.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SharePointProjectPropertyTab
- VS.SharePointTools.Project.Publishing
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ab97efc82575c31c8e05b73063c2b53a09691d2d
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672664"
---
# <a name="deploy-publish-and-upgrade-sharepoint-solution-packages"></a>Bereitstellen, veröffentlichen und Aktualisieren von SharePoint-Lösungs Paketen
  Nachdem Sie eine SharePoint-Projekt Mappe in Visual Studio entwickelt haben, können Sie die zugehörige Paketdatei (. wsp) entweder auf einem lokalen SharePoint-Server bereitstellen oder auf einem Remote-oder lokalen SharePoint-Server veröffentlichen. Wenn Sie die Dateien bereitstellen, können Sie anpassen, wie die Paketdateien (. wsp) bereitgestellt werden.

> [!NOTE]
> Zurzeit können nur Sandbox-Lösungen auf Remote-SharePoint-Servern veröffentlicht werden. Weitere Informationen finden Sie unter [Überlegungen zu Sandkasten Lösungen](../sharepoint/sandboxed-solution-considerations.md).

## <a name="deploy-publish-and-upgrade"></a>Bereitstellen, veröffentlichen und aktualisieren
 Bereit *Stellung bezieht sich auf das* Kopieren einer aus einem SharePoint-Projekt erstellten SharePoint-Projektmappendatei auf einen lokalen Host. In einer bereitgestellten Lösung können Sie die Bereitstellungs Schritte konfigurieren, wie z. b. das wieder verwenden des Internetinformationsdienste (IIS)-Pools, das Aktivieren der Lösung nach der Bereitstellung usw. Verwenden Sie zum Bereitstellen **des Befehls den** Befehl Bereitstellen im Menü **Build** . Weitere Informationen finden Sie unter Gewusst [wie: Bearbeiten einer SharePoint-Bereitstellungs Konfiguration](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) und Gewusst [wie: Bereitstellen und Veröffentlichen einer SharePoint-Lösung auf einer lokalen SharePoint-Website](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).

 *Veröffentlichung* bezieht sich auf das Hochladen einer Sandkasten-SharePoint-Projektmappendatei auf eine Remote-SharePoint-Website. Das heißt, eine Site befindet sich auf einem anderen System. Sie können auch eine SharePoint-Sandkasten Projektmappendatei auf einer lokalen SharePoint-Website veröffentlichen. unabhängig davon, ob die Website, auf der veröffentlicht wurde, lokal oder Remote ist, können Sie die Bereitstellungs Schritte nicht konfigurieren.

 Das *Upgrade* bezieht sich auf das Aktualisieren einer vorhandenen Remote oder lokal veröffentlichten SharePoint-Lösung. Nachdem Sie Änderungen an der SharePoint-Projekt Mappe in Visual Studio vorgenommen haben, ändern Sie den Paket Dateinamen der Projekt Mappe, veröffentlichen Sie die Projekt Mappe erneut, und aktualisieren Sie die Projekt Mappe nach der erfolgreichen erneuten Veröffentlichung. Wenn Sie eine lokal veröffentlichte Lösung erneut veröffentlichen, können Sie die vorhandene Projektmappendatei überschreiben.

## <a name="deploy-packages"></a>Bereitstellen von Paketen
 Sie können Paketdateien für den SharePoint-Server auf dem Entwicklungs Computer zum Testen und Debuggen bereitstellen. Sie können auch eine Paketdatei erstellen, die Sie auf einem anderen Computer installieren können, indem Sie im Dialogfeld **veröffentlichen** auf das Optionsfeld in **Datei System veröffentlichen** klicken. Das Paket wird erstellt und in den angegebenen lokalen Dateipfad kopiert. Zum Bereitstellen einer SharePoint-Lösung auf dem lokalen Server verwenden Sie **den Befehl bereit** stellen im Menü **Build** . Weitere Informationen finden Sie unter Gewusst [wie: Bereitstellen und Veröffentlichen einer SharePoint-Lösung auf einer lokalen SharePoint-Website](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).

 Informationen zum Bereitstellen einer Listen Definition, zum Hinzufügen eines Ereignis Empfängers und zum Verwenden des Funktions-Designers und des Paket-Designers finden Sie unter Exemplarische Vorgehensweise: bereitstellen [einer Aufgabenlisten Definition für Projekte](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md).

## <a name="customize-the-deployment-process"></a>Anpassen des Bereitstellungs Prozesses
 In der folgenden Tabelle werden die beiden Bereitstellungs Konfigurationen angezeigt, die Sie beim Debuggen und Bereitstellen einer SharePoint-Lösung verwenden können.

|Bereitstellungskonfiguration|Beschreibung|
|------------------------------|-----------------|
|Standard|Die Standard Bereitstellungs Konfiguration. Die folgenden Bereitstellungs Schritte werden ausgeführt:<br /><br /> 1. führen Sie den Befehl vor der Bereitstellung aus.<br />2. verwenden Sie den IIS-Anwendungs Pool.<br />3. ziehen Sie die Lösung zurück.<br />4. Fügen Sie eine Lösung hinzu.<br />5. Aktivieren Sie Features.<br />6. führen Sie den Befehl nach der Bereitstellung aus.<br /><br /> Wenn ein Paket deinstalliert wird, werden die folgenden Schritte ausgeführt.<br /><br /> 1. verwenden Sie den IIS-Anwendungs Pool.<br />2. ziehen Sie die Lösung zurück.|
|Keine Aktivierung|Bei dieser Bereitstellungs Konfiguration werden die gleichen Schritte wie bei der Standardkonfiguration ausgeführt, der Aktivierungs Schritt wird jedoch ausgelassen.|

 Sie können eigene Bereitstellungs Konfigurationen erstellen, um einen einzelnen Schritt abzuschließen oder die Reihenfolge der Schritte im Bereitstellungs Prozess zu ändern. Weitere Informationen finden Sie unter [Vorgehensweise: Bearbeiten einer SharePoint-Bereitstellungskonfiguration](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).

 Sie können auch Befehle hinzufügen, die vor und nach der Bereitstellung ausgeführt werden. Weitere Informationen finden Sie unter Gewusst [wie: Festlegen von SharePoint-Bereitstellungs Befehlen](../sharepoint/how-to-set-sharepoint-deployment-commands.md).

## <a name="publish-packages-to-a-remote-or-local-server"></a>Veröffentlichen von Paketen auf einem Remote Server oder einem lokalen Server
 Wenn Sie eine Sandkasten-SharePoint-Projekt Mappe auf einem Remote Server veröffentlichen möchten, wählen Sie in der Menüleiste die Option **Erstellen** und **veröffentlichen** aus, und wählen Sie dann im Dialogfeld **veröffentlichen** die Options Schaltfläche in **SharePoint-Website veröffentlichen** aus, und geben Sie die URL des Remote Servers an, z `https://someremoteserver.sharepoint.microsoftonline.com` . b..

 Wählen Sie zum Veröffentlichen einer SharePoint-Lösung auf einem lokalen Server im Dialogfeld **veröffentlichen** das Optionsfeld in **Datei System veröffentlichen** aus, und geben Sie einen lokalen System Pfad an.

 Nachdem eine Projekt Mappe erfolgreich in SharePoint veröffentlicht wurde, wird Sie in der **Lösungs Galerie** angezeigt, in der Sie Sie aktivieren können. Weitere Informationen finden Sie unter Vorgehens [Weise: bereitstellen, veröffentlichen und Aktualisieren von SharePoint-Lösungen auf einem Remote Server](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

### <a name="upgrade-published-packages"></a>Aktualisieren veröffentlichter Pakete
 Wenn Sie Änderungen an einem SharePoint-Projekt in Visual Studio nach der Veröffentlichung vornehmen, muss das veröffentlichte Paket aktualisiert werden, um die Änderungen einzuschließen. Ein Paket muss einen eindeutigen Namen aufweisen, um es erfolgreich zu aktualisieren. Wenn auf der SharePoint-Website ein Paket mit demselben Namen gefunden wird, das beim Aktualisieren einer vorhandenen Anwendung auftreten kann, werden Sie durch einen Fehler auf den Dateinamen Konflikt benachrichtigt, und Sie können das Paket umbenennen. Nach der erneuten Veröffentlichung wird das neue Paket auf der SharePoint-Website angezeigt, und Sie können ein Upgrade durchgeführt werden. Ein aktualisiertes Paket aktualisiert die Lösung mithilfe von Daten aus dem älteren Paket und aktiviert die Lösung dann in SharePoint. Weitere Informationen finden Sie unter Vorgehens [Weise: bereitstellen, veröffentlichen und Aktualisieren von SharePoint-Lösungen auf einem Remote Server](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

## <a name="see-also"></a>Siehe auch
- [Packen und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
