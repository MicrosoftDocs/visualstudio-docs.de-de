---
title: Remote Bereitstellung, Veröffentlichung & Upgrade von SharePoint-Lösungen
titleSuffix: ''
description: Bereitstellen, veröffentlichen und Upgraden von Sandkasten-SharePoint-Lösungen an einem Remote Standort oder einer lokalen SharePoint-Website.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- remote deployment [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, remote deployment
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ab301f11ffdae03564f05388dfbba55a90d12391
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913683"
---
# <a name="how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server"></a>Vorgehensweise: bereitstellen, veröffentlichen und Aktualisieren von SharePoint-Lösungen auf einem Remote Server
  Zusätzlich zur Bereitstellung von SharePoint-Lösungen auf dem lokalen System können Sie Sandbox-SharePoint-Lösungen an Remote Standorten oder auf lokalen SharePoint-Websites veröffentlichen. Beim Remote Publishing Vorgang wird die *wsp* -Datei auf den SharePoint-Server kopiert, die Projekt Mappe installiert und dann die Aktivierung der Lösung ermöglicht. Sie können auch eine Remote Installation einer SharePoint-Lösung aktualisieren, nachdem Änderungen vorgenommen wurden.

## <a name="to-publish-a-sandboxed-sharepoint-solution-to-a-remote-sharepoint-server"></a>So veröffentlichen Sie eine Sandkasten-SharePoint-Lösung auf einem SharePoint-Remote Server

1. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für das Sandkasten-SharePoint-Projekt, das Sie veröffentlichen möchten, und wählen Sie dann **veröffentlichen** aus.

2. Wählen Sie im Dialogfeld **veröffentlichen** die Options Schaltfläche **auf der SharePoint-Website veröffentlichen** aus, und geben Sie dann eine URL für eine Online Publishing Site ein, z `https://mytestsite.sharepoint.microsoftonline.com` . b.:.

3. Wählen Sie die Seite projektmappenkatalog **Öffnen im Browser nach dem Veröffentlichen** aus, um die Liste der Lösungen nach der Veröffentlichung auf der Seite **Lösungs** Katalog anzuzeigen.

4. Klicken Sie auf die Schaltfläche **Veröffentlichen**.

5. Melden Sie sich beim Remote Server an, wenn eine Benutzerauthentifizierung erforderlich ist.

     Der Veröffentlichungs Fortschritt wird im **Ausgabe** Fenster von Visual Studio angezeigt. Wenn der Prozess abgeschlossen ist, wird die Projektmappendatei (*. wsp*) auf dem Remote-SharePoint-Server installiert. Es muss jedoch noch aktiviert werden, bevor es in SharePoint verwendet werden kann.

6. Wählen Sie auf **der Seite** projektmappenkatalog die SharePoint-Anwendung aus, und wählen Sie dann im Menüband die Schaltfläche **aktivieren** aus.

7. Wählen Sie im Dialogfeld Projekt Mappe **aktivieren** auf dem Menüband die Schaltfläche **aktivieren** erneut aus.

     Die Spalte **Status** auf der Seite **Lösungs** Katalog gibt an, dass die Anwendung aktiv ist.

## <a name="to-upgrade-a-sandboxed-sharepoint-solution-on-a-remote-sharepoint-server"></a>So aktualisieren Sie eine Sandkasten-SharePoint-Lösung auf einem SharePoint-Remote Server
 Wenn bereits eine Sandkasten-SharePoint-Projekt Mappe auf einem Remote Server veröffentlicht wurde, können Sie mit dem folgenden Verfahren ein Upgrade durchführen, nachdem Sie die Anwendung in geändert haben [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

1. Benennen Sie das SharePoint-Paket in um [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Zu diesem Zweck können Sie in **Projektmappen-Explorer** das Paket öffnen. Es wird im **Paket-Explorer** angezeigt.

2. Ändern Sie im **Paket-Explorer** im Feld **Name** den Namen des Pakets in einen eindeutigen Namen.

3. Speichern Sie das Projekt.

4. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für das Projekt, und wählen Sie dann **veröffentlichen** aus.

5. Wählen Sie im Dialogfeld **veröffentlichen** die Options Schaltfläche **auf der SharePoint-Website veröffentlichen** aus, und geben Sie dann, wenn die URL für den Remote Server, auf dem die Lösung gespeichert ist, den Wert ein.

6. Wählen Sie die Seite projektmappenkatalog **Öffnen im Browser nach dem Veröffentlichen** aus, um die Liste der Lösungen nach der Veröffentlichung auf der Seite **Lösungs** Katalog anzuzeigen.

7. Klicken Sie auf die Schaltfläche **Veröffentlichen**.

8. Melden Sie sich beim Remote Server an, wenn eine Benutzerauthentifizierung erforderlich ist.

     Wenn Sie sich kürzlich am Remote Server angemeldet haben, ist die Authentifizierung möglicherweise nicht erforderlich.

     Wenn die ältere Version der Anwendung, die denselben Namen hat, auf dem SharePoint-Server noch vorhanden ist, erhalten Sie eine Fehlermeldung, dass bereits ein Paket mit demselben Namen auf dem SharePoint-Server vorhanden ist. Sie müssen das Paket vor der Veröffentlichung in einen eindeutigen Namen umbenennen.

9. Wählen Sie die neue Anwendung in SharePoint aus, und wählen Sie dann im Menüband die Schaltfläche **Upgrade** aus.

10. Wählen Sie im Dialogfeld Projekt Mappe **Aktualisieren** im Menüband erneut die Schaltfläche **Upgrade** aus. In der Spalte **Status** auf der Seite **Lösungs** Katalog sollte nun angezeigt werden, dass die Anwendung aktiv ist.

     Die alte Version der Lösung wird deaktiviert, die neue Version der Lösung wird mit den Daten aus der alten Lösung aktualisiert, und die neue Lösung wird in SharePoint aktiviert.

## <a name="see-also"></a>Weitere Informationen
- [Vorgehensweise: Bereitstellen und Veröffentlichen einer SharePoint-Lösung auf einer lokalen SharePoint-Website](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)
- [Erstellen von SharePoint-Lösungs Paketen](../sharepoint/creating-sharepoint-solution-packages.md)
- [Vorgehensweise: Anpassen eines SharePoint-Lösungs Pakets](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Vorgehensweise: Hinzufügen und Entfernen von Features und Elementen zu einem Paket mit dem Paket-Designer](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
