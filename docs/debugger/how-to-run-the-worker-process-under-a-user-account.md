---
title: Ausführen eines Workerprozesses unter einem Benutzerkonto | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie Ihren Computer so einrichten, dass Sie den ASP.NET-Workerprozess („aspnet_wp.exe“ oder „w3wp.exe“) unter einem Benutzerkonto in Visual Studio ausführen können.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- user accounts, aspnet_wp.exe
- ASP.NET, debugging Web applications
- tools, aspnet_wp.exe
- ASP.NET, tools
- aspnet_wp.exe
ms.assetid: b58e97b1-e62a-4318-aea4-52276ea20735
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 24dc3be78534610492dfada954f74a883808b40b
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148688"
---
# <a name="how-to-run-the-worker-process-under-a-user-account"></a>Vorgehensweise: Ausführen des Workerprozesses unter einem Benutzerkonto
Um Ihren Computer so einzurichten, dass der [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Arbeitsprozess (aspnet_wp.exe oder w3wp.exe) unter einem Benutzerkonto ausgeführt werden kann, führen Sie folgende Schritte aus:

 > [!IMPORTANT]
 > Ab Windows Server 2008 R2 empfiehlt es sich, die [ApplicationPoolIdentity](/iis/manage/configuring-security/application-pool-identities) als Identität für jeden Anwendungspool zu verwenden.

## <a name="procedure"></a>Prozedur

#### <a name="to-run-aspnet_wpexe-under-a-user-account"></a>So führen Sie "aspnet_wp.exe" unter einem Benutzerkonto aus

1. Öffnen Sie die Datei machine.config. Sie befindet sich auf dem Computer im Ordner CONFIG und wurde unter demselben Pfad gespeichert, unter dem die Laufzeit installiert wurde.

2. Suchen Sie den Abschnitt &lt;processModel&gt;, und verwenden Sie für die Attribute „user“ und „password“ den Benutzernamen und das Kennwort des Benutzerkontos, unter dem „aspnet_wp.exe“ ausgeführt werden soll.

3. Speichern Sie die Datei machine.config.

4. Unter [!INCLUDE[winxpsvr](../debugger/includes/winxpsvr_md.md)] wird IIS 6.0 standardmäßig installiert. Der entsprechende Arbeitsprozess ist "w3wp.exe". Führen Sie folgende Schritte aus, um "aspnet_wp.exe" als Arbeitsprozess im IIS 6.0-Modus auszuführen:

   1. Klicken Sie auf **Start** und dann auf **Verwaltung**. Wählen Sie anschließend **Internetinformationsdienste** aus.

   2. Klicken Sie im Dialogfeld **Internetinformationsdienste** mit der rechten Maustaste auf den Ordner **Web Sites** (Websites), und wählen Sie **Eigenschaften** aus.

   3. Wählen Sie im Dialogfeld **Web Sites Properties** (Eigenschaften von Websites) die Option **Service** (Dienst) aus.

   4. Wählen Sie **Run WWW service in IIS6.0 isolation mode** (WWW-Dienst im IIS 6.0-Isolationsmodus ausführen) aus.

   5. Schließen Sie das Dialogfeld **Eigenschaften** und den **Internetdienste-Manager**.

5. Öffnen Sie eine Eingabeaufforderung von Windows, und setzen Sie den Server zurück, indem Sie Folgendes ausführen:

   ```cmd
   iisreset
   ```

   \- oder -

   ```cmd
   net stop iisadmin /y
   net start w3svc
   ```

6. Suchen Sie den Ordner Temporary [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Files. Er sollte sich im selben Pfad befinden wie der Ordner CONFIG. Klicken Sie mit der rechten Maustaste auf den Ordner „Temporäre [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Dateien“, und wählen Sie im Kontextmenü die Option **Eigenschaften** aus.

7. Klicken Sie im Dialogfeld **Temporary ASP.NET Files Properties** (Eigenschaften temporärer ASP.NET-Dateien) auf die Registerkarte **Sicherheit**.

8. Klicken Sie auf **Erweitert**.

9. Klicken Sie im Dialogfeld **Advanced Security Settings for Temporary ASP.Net Files** (Erweiterte Sicherheitseinstellungen für temporäre ASP.NET-Dateien) auf **Hinzufügen**.

    Das Dialogfeld **Select User, Computer, or Group** (Benutzer, Computer oder Gruppen auswählen) wird angezeigt.

10. Geben Sie den Benutzernamen in das Feld **Namen des auszuwählenden Objekts eingeben** ein, und klicken Sie auf **OK**. Der Benutzername muss folgendes Format aufweisen: Domänenname\Benutzername.

11. Gewähren Sie dem Benutzer im Dialogfeld **Permission Entry for Temporary ASP.NET Files** (Berechtigungseintrag für temporäre ASP.NET-Dateien) **Full Control** (Vollzugriff), und klicken Sie dann auf **OK**, um das Dialogfeld **Entry for Temporary ASP.NET Files** (Eintrag für temporäre ASP.NET-Dateien) zu schließen.

12. Das Dialogfeld **Sicherheit** wird angezeigt, und Sie werden gefragt, ob Sie wirklich die Berechtigungen für einen Systemordner ändern möchten. Klicken Sie auf **Ja**.

13. Klicken Sie auf **OK**, um das Dialogfeld **Temporary ASP.NET Files Properties** (Eigenschaften temporärer ASP.NET-Dateien) zu schließen.

## <a name="see-also"></a>Siehe auch
- [Debug ASP.NET Applications (Debuggen von ASP.NET-Anwendungen)](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [ASP.NET-Debugging: Systemanforderungen](../debugger/aspnet-debugging-system-requirements.md)
