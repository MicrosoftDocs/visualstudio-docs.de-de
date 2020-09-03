---
title: 'Fehler: Fehler beim Debuggen, da die integrierte Windows-Authentifizierung nicht aktiviert ist | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.webdbg_ntlm_authn_not_enabled
dev_langs:
- FSharp
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: 6027cd94-74cf-470f-b7ce-6f6b68bc56ba
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 89afba591899b626863b0157f6d9d955d46e46cf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851916"
---
# <a name="error-debugging-failed-because-integrated-windows-authentication-is-not-enabled"></a>Fehler: Fehler beim Debuggen, da die integrierte Windows-Authentifizierung nicht aktiviert ist
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der Benutzer, der die Debuganforderung gestellt hat, konnte aufgrund eines Authentifizierungsfehlers nicht authentifiziert werden. Dies kann beim Versuch, eine Webanwendung oder einen XML-Webdienst in Einzelschritten auszuführen, auftreten. Eine Ursache dieses Fehlers besteht darin, dass die integrierte Windows-Authentifizierung nicht aktiviert ist. Um sie zu aktivieren, führen Sie die Schritte in "So aktivieren Sie die integrierte Windows-Authentifizierung" aus.  
  
 Wenn die integrierte Windows-Authentifizierung aktiviert ist und der Fehler immer noch auftritt, besteht die Ursache möglicherweise darin, dass **Hashwertauthentifizierung für Windows-Domänenserver** aktiviert ist. In diesem Fall sollten Sie sich mit dem Netzwerkadministrator in Verbindung setzen.  
  
### <a name="to-enable-integrated-windows-authentication"></a>So aktivieren Sie die integrierte Windows-Authentifizierung  
  
1. Melden Sie sich über ein Administratorkonto beim Webserver an.  
  
2. Klicken Sie auf **Start** und anschließend auf **Systemsteuerung**.  
  
3. Doppelklicken Sie in der **Systemsteuerung** auf **Verwaltung**.  
  
4. Doppelklicken Sie auf **Internetinformationsdienste**.  
  
5. Klicken Sie auf den Webserverknoten.  
  
     Unterhalb des Servernamens wird der Ordner **Websites** geöffnet.  
  
6. Sie können die Authentifizierung für alle Websites oder für einzelne Websites konfigurieren. Um die Authentifizierung für alle Websites zu konfigurieren, klicken Sie mit der rechten Maustaste auf den Ordner **Websites**, und klicken Sie anschließend auf **Eigenschaften**. Wenn Sie die Authentifizierung für eine einzelne Website konfigurieren möchten, öffnen Sie den Ordner **Websites**, klicken Sie mit der rechten Maustaste auf die gewünschte Website, und klicken Sie anschließend auf **Eigenschaften**.  
  
     Das Dialogfeld **Eigenschaften** wird angezeigt.  
  
7. Klicken Sie auf die Registerkarte **Verzeichnissicherheit**.  
  
8. Klicken Sie im Abschnitt **Anonymer Zugriff und Authentifizierungssteuerung** auf **Bearbeiten**.  
  
     Das Dialogfeld **Authentifizierungsmethoden** wird angezeigt.  
  
9. Wählen Sie unter **Authentifizierter Zugriff** die Option **Integrierte Windows-Authentifizierung** aus.  
  
10. Klicken Sie auf **OK**, um das Dialogfeld **Authentifizierungsmethoden** zu schließen.  
  
11. Klicken Sie auf **OK**, um das Dialogfeld **Eigenschaften** zu schließen.  
  
12. Schließen Sie das Fenster **Internetinformationsdienste**.  
  
### <a name="to-enable-integrated-windows-authentication-in-windows-vistaiis-7"></a>So aktivieren Sie die integrierte Windows-Authentifizierung unter Windows Vista/IIS 7  
  
1. Melden Sie sich über ein Administratorkonto beim Webserver an.  
  
2. Aktivieren Sie die Windows-Authentifizierung und die IIS6-Verwaltungskompatibilität, wenn diese nicht bereits aktiviert wurden, indem Sie folgende Schritte ausführen:  
  
    1. Klicken Sie auf **Start**, klicken Sie auf **Systemsteuerung**, und klicken Sie dann auf **Programme**.  
  
    2. Klicken Sie unter **Programme und Funktionen** auf **Windows-Funktionen ein- oder ausschalten**.  
  
         Das Dialogfeld Benutzerzugriffssteuerung wird angezeigt und fordert Ihre Bestätigung zum Fortfahren an.  
  
    3. Klicken Sie auf **Weiter**.  
  
         Das Dialogfeld Windows-Funktionen wird angezeigt.  
  
    4. Erweitern Sie in der Funktionsliste den Knoten **Internetinformationsdienste**.  
  
    5. Erweitern Sie unter **Internetinformationsdienste** den Knoten **WWW-Dienste**.  
  
    6. Klicken Sie unter **WWW-Dienste** auf **Sicherheit**.  
  
    7. Klicken Sie auf **Windows-Authentifizierung**.  
  
    8. Erweitern Sie unter **Internetinformationsdienste** den Knoten **Webverwaltungstools**.  
  
    9. Erweitern Sie unter **Webverwaltungstools** den Knoten **Kompatibilität mit der IIS 6-Verwaltung**, und aktivieren Sie das Kontrollkästchen **Kompatibilität mit IIS 6-Metabasis und IIS 6-Konfiguration**.  
  
    10. Wählen Sie unter **Webverwaltungstools** die **IIS-Managementkonsole** aus, und klicken Sie auf **OK**.  
  
    11. Starten Sie den Computer neu, damit die Änderungen wirksam werden.  
  
3. Klicken Sie auf **Start** und anschließend auf **Systemsteuerung**.  
  
4. Klicken Sie auf **Klassische Ansicht**, und doppelklicken Sie anschließend auf **Verwaltung**.  
  
5. Doppelklicken Sie in der Spalte **Name** auf **Internetinformationsdienste-Manager**.  
  
6. Erweitern Sie in der Spalte **Verbindungen** den Knoten für den Server.  
  
     Unterhalb des Servernamens wird der Ordner **Websites** geöffnet.  
  
7. Erweitern Sie den Knoten **Websites**, und klicken Sie auf die Website, für die Sie die integrierte Windows-Authentifizierung aktivieren möchten.  
  
8. Der Titel des mittleren Bereichs wird in den Namen der ausgewählten Website geändert. Doppelklicken Sie in diesem Bereich unter der Überschrift **IIS** auf **Authentifizierung**.  
  
     Der Titel des Bereichs wird in **Authentifizierung** geändert.  
  
9. Klicken Sie im Bereich **Authentifizierung** in der Spalte **Name** mit der rechten Maustaste auf **Windows-Authentifizierung**, und klicken Sie anschließend auf **Aktivieren**.  
  
10. Schließen Sie das Fenster **Internetinformationsdienste-Manager**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Debuggen von Webanwendungen: Fehler und Problembehandlung](../debugger/debugging-web-applications-errors-and-troubleshooting.md)   
 [Microsoft Digest Authentifizierung](https://msdn2.microsoft.com/library/Aa378744.aspx)   
 [Ausführen von Webanwendungen unter Windows Vista mit IIS 7.0 und Visual Studio](https://msdn.microsoft.com/library/262a82ac-dd0e-4096-86c6-fb463e88be66)
