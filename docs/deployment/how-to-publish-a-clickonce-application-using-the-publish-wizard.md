---
title: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten
description: Erfahren Sie mehr über die Verwendung des Veröffentlichungs-Assistenten, um Ihre ClickOnce-Anwendung für Benutzer verfügbar zu machen, einschließlich der zu verwendenden Veröffentlichungs Eigenschaften.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, publishing
- deploying applications [ClickOnce], Publish wizard
- Windows applications, ClickOnce deployments
- publishing, ClickOnce
ms.assetid: 2e4aa67c-4445-4f7b-9e03-9acb95829127
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 252d029e7e2e5b9b5dfe27b2fb1cd72e1c09b473
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349879"
---
# <a name="how-to-publish-a-clickonce-application-using-the-publish-wizard"></a>Vorgehensweise: Veröffentlichen einer ClickOnce-Anwendung mit dem Veröffentlichungs-Assistenten
Wenn Sie eine ClickOnce-Anwendung für Benutzer bereitstellen möchten, müssen Sie sie auf einer Dateifreigabe oder unter einem Dateipfad, auf einem FTP-Server oder einem Wechselmedium veröffentlichen. Sie können die Anwendung mit dem Veröffentlichungs-Assistenten veröffentlichen. Für die Veröffentlichung stehen im **Projekt-Designer** auf der Seite **Veröffentlichen** zusätzliche Eigenschaften zur Verfügung. Weitere Informationen finden Sie unter [Publishing ClickOnce applications (Veröffentlichen von ClickOnce-Anwendungen)](../deployment/publishing-clickonce-applications.md).

Bevor Sie den Webpublishing-Assistenten ausführen, sollten Sie die Veröffentlichungseigenschaften entsprechend festlegen. Wenn Sie z.B. einen Schlüssel zum Signieren der ClickOnce-Anwendung angeben möchten, können Sie dies im **Projekt-Designer** auf der Seite **Signierung** vornehmen. Weitere Informationen finden Sie unter [sichere ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md).

> [!NOTE]
> Wenn Sie mit ClickOnce mehrere Versionen einer Anwendung installieren, verschiebt die Installation frühere Versionen der Anwendung in einen Ordner namens " *Archive* " an dem von Ihnen angegebenen Veröffentlichungsort. Durch dieses Archivieren älterer Versionen wird sichergestellt, dass im Installationsverzeichnis keine Ordner älterer Versionen verbleiben.

> [!NOTE]
> Die angezeigten Dialogfelder und Menübefehle können sich je nach den aktiven Einstellungen oder der verwendeten Version von den in der Hilfe beschriebenen unterscheiden. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Reset settings (Zurücksetzen der Einstellungen)](../ide/environment-settings.md#reset-settings).

## <a name="to-publish-to-a-file-share-or-path"></a>So veröffentlichen Sie auf einer Dateifreigabe oder unter einem Pfad

1. Wählen Sie im **Projektmappen-Explorer** das Anwendungsprojekt aus.

2. Klicken Sie im Menü **Erstellen** auf **Publish** *Projektname* veröffentlichen.

    Der Webpublishing-Assistent wird angezeigt.

3. Geben Sie auf der Seite **Wo möchten Sie die Anwendung veröffentlichen?** eine gültige FTP-Server-Adresse oder einen gültigen Dateipfad mithilfe eines der gezeigten Formate ein, und klicken Sie dann auf **Weiter**.

4. Wählen Sie auf der Seite **Wie werden Benutzer die Anwendung installieren?** den Speicherort aus, auf den Benutzer beim Installieren der Anwendung zugreifen:

   - Wenn die Installation über eine Website durchgeführt werden soll, klicken Sie auf **Von einer Website** , und geben Sie eine URL ein, die dem im vorherigen Schritt eingegebenen Dateipfad entspricht. Klicken Sie auf **Weiter**. (Diese Option wird normalerweise verwendet, wenn eine FTP-Adresse als Veröffentlichungsort angegeben werden soll. Der direkte Download per FTP wird nicht unterstützt. Daher müssen Sie hier eine URL eingeben.)

   - Wenn die Installation direkt über die Dateifreigabe durchgeführt werden soll, klicken Sie auf **Von UNC-Pfad oder Dateifreigabe** , und klicken Sie dann auf **Weiter**. (Hiermit können Veröffentlichungsorte im Format *c:\deploy\myapp* oder *\\\server\myapp* verwendet werden.)

   - Wenn die Installation über Wechselmedien durchgeführt werden soll, klicken Sie auf **Von CD-ROM oder DVD-ROM** , und klicken Sie dann auf **Weiter**.

5. Wählen Sie auf der Seite **Wird die Anwendung offline verfügbar sein?** die gewünschte Option aus:

   - Falls die Anwendung auch ausgeführt werden soll, wenn der Benutzer vom Netzwerk getrennt ist, klicken Sie auf **Yes, this application will be available online or offline** (Ja, diese Anwendung ist online und offline verfügbar). Im **Startmenü** wird eine Verknüpfung für die Anwendung erstellt.

   - Wenn die Anwendung direkt vom Ort der Veröffentlichung gestartet werden soll, klicken Sie auf **Nein, diese Anwendung ist nur online verfügbar.** Es wird keine Verknüpfung im **Startmenü** erstellt.

     Klicken Sie zum Fortfahren auf **Weiter** .

6. Klicken Sie auf **Fertig stellen** , um die Anwendung zu veröffentlichen.

    Der Veröffentlichungsstatus wird im Statusinfobereich angezeigt.

## <a name="to-publish-to-a-cd-rom-or-dvd-rom"></a>So veröffentlichen Sie auf einer CD-ROM oder DVD-ROM

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Anwendungsprojekt, und klicken Sie dann auf **Eigenschaften**.

    Der **Projekt-Designer** wird angezeigt.

2. Klicken Sie auf die Registerkarte **Veröffentlichen** , um im **Projekt-Designer** die Seite **Veröffentlichen** zu öffnen, und klicken Sie auf die Schaltfläche **Veröffentlichungs-Assistent**.

    Der Webpublishing-Assistent wird angezeigt.

3. Geben Sie auf der Seite **Wo möchten Sie die Anwendung veröffentlichen?** den Dateipfad oder den FTP-Speicherort an, an dem die Anwendung veröffentlicht wird, zum Beispiel: *d:\deploy*. Klicken Sie dann auf **Weiter** , um den Vorgang fortzusetzen.

4. Klicken Sie auf der Seite **Wie werden Benutzer die Anwendung installieren?** auf **Von CD-ROM oder DVD-ROM** , und klicken Sie dann auf **Weiter**.

   > [!NOTE]
   > Falls Sie die Installation ausgeführt werden soll, wenn die CD-ROM in das Laufwerk eingelegt wird, öffnen Sie im **Projekt-Designer** die Seite **Veröffentlichen** und klicken auf die Schaltfläche **Optionen**. Wählen Sie in den **Veröffentlichungsoptionen** des Assistenten dann die Option **Bei CD-Installationen automatisch Setup starten, wenn CD eingelegt wird** aus.

5. Wenn Sie Ihre Anwendung auf einer CD-ROM veröffentlichen, können Sie dennoch Updates auf einer Website zur Verfügung stellen. Wählen Sie auf der Seite **Die Anwendung überprüft folgenden Speicherort auf Updates** eine Updateoption aus:

   - Wenn die Anwendung nach Updates sucht, klicken Sie auf **Die Anwendung überprüft folgenden Speicherort auf Updates** und geben den Speicherort ein, an dem Updates veröffentlicht werden. Der Speicherort kann ein Dateipfad, eine Website oder ein FTP-Server sein.

   - Wenn die Anwendung nicht nach Updates sucht, klicken Sie auf **Anwendung sucht nicht nach Updates**.

     Klicken Sie zum Fortfahren auf **Weiter** .

6. Klicken Sie auf **Fertig stellen** , um die Anwendung zu veröffentlichen.

    Der Veröffentlichungsstatus wird im Statusinfobereich angezeigt.

   > [!NOTE]
   > Wenn die Veröffentlichung abgeschlossen ist, benötigen Sie einen CD-Rekorder oder einen DVD-Rekorder, um die Dateien von dem in Schritt 3 angegebenen Speicherort auf CD-ROM oder DVD-ROM zu kopieren.

## <a name="see-also"></a>Weitere Informationen

- [ClickOnce-Sicherheit und-Bereitstellung](../deployment/clickonce-security-and-deployment.md)
- [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md)
- [Bereitstellen einer Office-Projekt Mappe mithilfe von ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)