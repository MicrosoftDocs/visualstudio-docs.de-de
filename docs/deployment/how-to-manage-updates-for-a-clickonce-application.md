---
title: Verwalten von Aktualisierungen für eine ClickOnce-Anwendung | Microsoft-Dokumentation
description: Erfahren Sie mehr über Optionen zum automatischen oder programmgesteuerten Suchen nach Updates für Ihre ClickOnce-Anwendungen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.Update
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, managing applications
- ClickOnce deployment, updates
- updating data, ClickOnce
- application updates
ms.assetid: a3f23f05-e7f1-4620-b23c-2d68f9643684
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 03b8b3899a90588ca747ca93c0ff6bd7279e1bec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900554"
---
# <a name="how-to-manage-updates-for-a-clickonce-application"></a>Vorgehensweise: Verwalten von Updates für eine ClickOnce-Anwendung
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungen können automatisch oder Programm gesteuert nach Updates suchen. Als Entwickler haben Sie viele Flexibilität bei der Angabe, wann und wie Update Überprüfungen durchgeführt werden, ob Updates obligatorisch sind und wo die Anwendung nach Updates suchen soll.

 Sie können die Anwendung so konfigurieren, dass nach Updates vor dem Start der Anwendung oder in festgelegten Intervallen nach dem Start der Anwendung gesucht wird. Außerdem können Sie eine mindestens erforderliche Version angeben. Das heißt, dass ein Update installiert wird, wenn die Version des Benutzers niedriger als die erforderliche Version ist.

 Sie können die Anwendung so konfigurieren, dass Sie Programm gesteuert auf Grundlage eines Ereignisses, z. b. einer Benutzer Anforderung, nach Updates sucht. In diesem Thema wird erläutert, wie Sie Code schreiben, der mithilfe der-Klasse nach Updates auf der <xref:System.Deployment.Application.ApplicationDeployment> Grundlage eines Ereignisses sucht, um Programm gesteuert nach Updates zu suchen.

 Sie können Ihre Anwendung auch an einem Speicherort bereitstellen und von einem anderen Standort aus aktualisieren. Weitere Informationen finden Sie im Verfahren "so geben Sie einen anderen Update Speicherort an".

 Weitere Informationen finden Sie unter [Auswählen einer Strategie für die ClickOnce-Aktualisierung](../deployment/choosing-a-clickonce-update-strategy.md).

 Das Aktualisierungs Verhalten wird im Dialogfeld **Anwendungs Updates** verwaltet, das auf der Seite **veröffentlichen** des **Projekt-Designers** verfügbar ist.

### <a name="to-check-for-updates-before-the-application-starts"></a>So suchen Sie nach Updates, bevor die Anwendung gestartet wird

1. Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer** im Menü **Projekt** auf **Eigenschaften**.

2. Klicken Sie auf die Registerkarte **Veröffentlichen**.

3. Klicken Sie auf die Schaltfläche **Updates** , um das Dialogfeld **Anwendungs Updates** zu öffnen.

4. Vergewissern Sie sich, dass im Dialogfeld **Anwendungs Updates** das Kontrollkästchen **Anwendung sollte nach Updates suchen** aktiviert ist.

5. Wählen Sie im Abschnitt **Wählen Sie aus, wann die Anwendung nach Updates suchen soll aus** , **bevor die Anwendung gestartet** wird. Dadurch wird sichergestellt, dass Benutzer, die mit dem Netzwerk verbunden sind, immer die Anwendung mit den neuesten Updates ausführen.

### <a name="to-check-for-updates-in-the-background-after-the-application-starts"></a>Suchen nach Updates im Hintergrund nach dem Start der Anwendung

1. Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer** im Menü **Projekt** auf **Eigenschaften**.

2. Klicken Sie auf die Registerkarte **Veröffentlichen**.

3. Klicken Sie auf die Schaltfläche **Updates** , um das Dialogfeld **Anwendungs Updates** zu öffnen.

4. Vergewissern Sie sich, dass im Dialogfeld **Anwendungs Updates** das Kontrollkästchen **für die Anwendung auf Updates prüfen** ausgewählt ist.

5. Wählen Sie im **Abschnitt wählen Sie aus, wann die Anwendung nach Updates suchen soll aus**, **nachdem die Anwendung gestartet** wurde. Die Anwendung wird auf diese Weise schneller gestartet, und es wird im Hintergrund nach Updates gesucht, und der Benutzer wird nur benachrichtigt, wenn ein Update verfügbar ist. Nach der Installation werden Updates erst wirksam, wenn die Anwendung neu gestartet wird.

6. Aktivieren Sie im Abschnitt geben Sie an, **wie häufig die Anwendung nach Updates suchen soll** die Option **jedes Mal aktivieren, wenn die Anwendung** ausgeführt wird (Standard), oder **Aktivieren Sie alle** , und geben Sie eine Zahl und ein Zeitintervall ein.

### <a name="to-specify-a-minimum-required-version-for-the-application"></a>So geben Sie eine mindestens erforderliche Version für die Anwendung an

1. Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer** im Menü **Projekt** auf **Eigenschaften**.

2. Klicken Sie auf die Registerkarte **Veröffentlichen**.

3. Klicken Sie auf die Schaltfläche **Updates** , um das Dialogfeld **Anwendungs Updates** zu öffnen.

4. Vergewissern Sie sich, dass im Dialogfeld **Anwendungs Updates** das Kontrollkästchen **Anwendung sollte nach Updates suchen** aktiviert ist.

5. Aktivieren Sie das Kontrollkästchen **mindestens erforderliche Version für diese Anwendung angeben** , und geben Sie dann die Nummern für **Haupt**-und **neben** Version, **Build** und **Revision** für die Anwendung ein.

### <a name="to-specify-a-different-update-location"></a>So geben Sie einen anderen Aktualisierungs Speicherort an

1. Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer** im Menü **Projekt** auf **Eigenschaften**.

2. Klicken Sie auf die Registerkarte **Veröffentlichen**.

3. Klicken Sie auf die Schaltfläche **Updates** , um das Dialogfeld **Anwendungs Updates** zu öffnen.

4. Vergewissern Sie sich, dass im Dialogfeld **Anwendungs Updates** das Kontrollkästchen **Anwendung sollte nach Updates suchen** aktiviert ist.

5. Geben Sie im Feld **Update Speicherort** den Update Speicherort mit einer voll qualifizierten URL unter Verwendung des Formats *http://Hostname/ApplicationName* oder eines UNC-Pfads im Format *\\ \server\applicationname* ein, oder klicken Sie auf die Schaltfläche **Durchsuchen** , um nach dem Aktualisierungs Speicherort zu suchen.

### <a name="to-check-for-updates-programmatically"></a>So suchen Sie Programm gesteuert nach Updates

1. Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer** im Menü **Projekt** auf **Eigenschaften**.

2. Klicken Sie auf die Registerkarte **Veröffentlichen**.

3. Klicken Sie auf die Schaltfläche **Updates** , um das Dialogfeld **Anwendungs Updates** zu öffnen.

4. Vergewissern Sie sich, dass im Dialogfeld **Anwendungs Updates** das Kontrollkästchen **Anwendung sollte nach Updates suchen** deaktiviert ist. (Optional können Sie dieses Kontrollkästchen aktivieren, um Programm gesteuert nach Updates zu suchen und die ClickOnce-Laufzeit zu überprüfen, ob Updates automatisch überprüft werden.)

5. Geben Sie im Feld **Update Speicherort** den Update Speicherort mit einer voll qualifizierten URL unter Verwendung des Formats *http://Hostname/ApplicationName* oder eines UNC-Pfads im Format *\\ \server\applicationname* ein, oder klicken Sie auf die Schaltfläche **Durchsuchen** , um nach dem Aktualisierungs Speicherort zu suchen. Der Aktualisierungs Speicherort ist der Ort, an dem die Anwendung nach einer aktualisierten Version von sich selbst sucht.

6. Erstellen Sie eine Schaltfläche, ein Menü Element oder eine andere Benutzeroberfläche in einem Windows Form, die Benutzer auswählen, um nach Updates zu suchen. Über den-Ereignishandler dieses Elements können Sie eine Methode zum Suchen und Installieren von Updates abrufen. Ein Beispiel für Visual Basic-und Visual c#-Code für eine solche Methode finden Sie unter Gewusst [wie: Programm gesteuertes suchen nach Anwendungs Updates mithilfe der ClickOnce-Bereitstellungs-API](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md).

7. Erstellen Sie Ihre Anwendung.

## <a name="see-also"></a>Weitere Informationen
- <xref:System.Deployment.Application.ApplicationDeployment>
- [Application updates dialog box (Dialogfeld „Anwendungsupdates“)](/previous-versions/visualstudio/visual-studio-2010/axw1fa38(v=vs.100))
- [Auswählen einer Strategie für die ClickOnce-Aktualisierung](../deployment/choosing-a-clickonce-update-strategy.md)
- [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)
- [Gewusst wie: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [Vorgehensweise: Programmgesteuertes Suchen nach Anwendungsupdates mit der API für die ClickOnce-Bereitstellung](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)
