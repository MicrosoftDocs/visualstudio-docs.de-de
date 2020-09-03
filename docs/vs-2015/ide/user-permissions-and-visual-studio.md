---
title: Benutzerberechtigungen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
ms.assetid: 70485ed7-6342-41bf-8250-7a6826e21b98
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aa01cb77e8a003438721984da13f46de350104ea
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75918997"
---
# <a name="user-permissions-and-visual-studio"></a>Benutzerberechtigungen und Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aus Sicherheitsgründen sollten Sie Visual Studio möglichst als normaler Benutzer ausführen.

> [!WARNING]
> Sie sollten auch sicherstellen, dass Sie keine Visual Studio-Projektmappe kompilieren, starten oder debuggen, die nicht von einer vertrauenswürdigen Person oder einem vertrauenswürdigen Speicherort stammt.

 Sie können nahezu alles in der Visual Studio-IDE als normaler Benutzer ausführen. Für die folgenden Aufgaben benötigen Sie allerdings Administratorberechtigungen:

|Bereich|Aufgabe|Weitere Informationen finden Sie unter|
|----------|----------|--------------------------|
|Installation|Installieren von Visual Studio.|[Installieren von Visual Studio 2015](../install/install-visual-studio-2015.md)|
||Aktualisieren von einer Testversion von Visual Studio.|[Gewusst wie: Aktualisieren von einer Visual Studio-Testversion](../install/how-to-upgrade-from-a-trial-edition-of-visual-studio.md)|
||Installieren, Aktualisieren oder Entfernen der lokalen Hilfeinhalte.|[Installieren und Verwalten von lokalen Inhalten](../ide/install-and-manage-local-content.md)|
|Anwendungstypen|Entwickeln von Lösungen für SharePoint 2010.|[Anforderungen für die Entwicklung von SharePoint-Projektmappen](https://msdn.microsoft.com/library/ae8ff69d-4540-4380-ab0b-845f7108e89c)|
||Erwerben einer Entwicklerlizenz für [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)].|[Anfordern einer Entwicklerlizenz (Windows Store-Apps)](https://msdn.microsoft.com/library/windows/apps/hh974578.aspx)|
|Werkzeugkasten|Hinzufügen von klassischen COM-Steuerelementen zur **Toolbox**.|[Verwenden der Toolbox](../ide/using-the-toolbox.md)|
|Add-Ins|Installieren und Verwenden von Add-Ins, die mit klassischem COM in der IDE geschrieben wurden.|[Erstellen von Add-Ins und Assistenten](https://msdn.microsoft.com/library/c5a47c21-6668-4de3-898d-afa969317e73)|
|Erstellen|Verwenden von Postbuildereignissen, die eine Komponente registrieren.|[Grundlagen benutzerdefinierter Buildschritte und Buildereignisse](https://msdn.microsoft.com/library/beb2f017-3e9f-4b2c-9b57-2572fd2628e4)|
||Einschließen eines Registrierungsschritts beim Erstellen von C++-Projekten.|[Grundlagen benutzerdefinierter Buildschritte und Buildereignisse](https://msdn.microsoft.com/library/beb2f017-3e9f-4b2c-9b57-2572fd2628e4)|
|Debuggen|Debuggen von Anwendungen, die mit höheren Berechtigungen ausgeführt werden.|[Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)|
||Debuggen von Anwendungen, die unter einem anderen Benutzerkonto, wie ASP.NET-Websites, ausgeführt werden.|[Debuggen von ASP.NET- und AJAX-Anwendungen](../debugger/debugging-aspnet-and-ajax-applications.md)|
||Debuggen in der Zone für XAML-Browseranwendungen (XBAP).|[WPF-Host (PresentationHost.exe)](https://msdn.microsoft.com/library/3215bfa1-722c-4ac8-a7c5-bdd02d30afbd)|
||Verwenden des Emulators zum Debuggen von Cloud-Dienstprojekten für Microsoft Azure.|[Debuggen eines Clouddiensts in Visual Studio](../azure/vs-azure-tools-debug-cloud-services-virtual-machines.md)|
||Konfigurieren einer Firewall für das Remotedebuggen.|[Einrichten der Remotetools auf dem Gerät](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)|
|Leistungstools|Profilerstellung für eine Anwendung|[Einführung in die Leistungsprofil Erstellung](../profiling/beginners-guide-to-performance-profiling.md)|
|Bereitstellung|Bereitstellen einer Webanwendung auf Internetinformationsdienste (IIS) auf einem lokalen Computer.|[Deploying an ASP.NET Web Application to a Hosting Provider using Visual Studio or Visual Web Developer: Deploying to IIS as a Test Environment (Bereitstellen einer ASP.NET-Webanwendung für einen Hostinganbieter, der Visual Studio oder Visual Web Developer verwendet: Bereitstellen in IIS als Testumgebung)](https://www.asp.net/web-forms/tutorials/deployment/deployment-to-a-hosting-provider/Deployment-to-a-Hosting-Provider-Deploying-to-IIS-as-a-Test-Environment-5-of-12)|
|Bereitstellen von Feedback für Microsoft|Ändern der Teilnahme am Visual Studio-Programm zur Verbesserung der Benutzerfreundlichkeit.|[Gewusst wie: Senden von Feedback](../misc/how-to-send-feedback-about-visual-studio.md)|

## <a name="running-visual-studio-as-an-administrator"></a>Ausführen von Visual Studio als Administrator
 Sie können Visual Studio bei jedem Starten der IDE mit Administratorberechtigungen starten, oder Sie können die Anwendungsverknüpfung so ändern, dass sie immer mit Administratorberechtigungen ausgeführt werden muss. Weitere Informationen finden Sie in der Windows-Hilfe.

#### <a name="to-run-visual-studio-with-administrative-permissions-on-win8-win81-winserver8-or-winblue_server_2"></a>So führen Sie Visual Studio mit Administratorberechtigungen in [!INCLUDE[win8](../includes/win8-md.md)], [!INCLUDE[win81](../includes/win81-md.md)], [!INCLUDE[winserver8](../includes/winserver8-md.md)] oder [!INCLUDE[winblue_server_2](../includes/winblue-server-2-md.md)] aus

1. Geben Sie auf dem **Start**-Bildschirm **Visual Studio** ein. Sie sollten die Version oder die Versionen von Visual Studio sehen, die Sie installiert haben.

2. Wählen Sie die Version von Visual Studio, die Sie starten möchten, und öffnen Sie dann das Kontextmenü (es wird am unteren Bildschirmrand angezeigt). Wählen Sie **Als Administrator ausführen**.

     Beim Starten von Visual Studio wird **(Administrator)** nach dem Produktnamen in der Titelleiste angezeigt.

#### <a name="to-run-visual-studio-with-administrative-permissions-on-win7-or-winsvr08_r2"></a>So führen Sie Visual Studio mit Administratorberechtigungen in [!INCLUDE[win7](../includes/win7-md.md)] oder [!INCLUDE[winsvr08_r2](../includes/winsvr08-r2-md.md)] aus

1. Wählen Sie im **Start**-Menü die Option **Alle Programme** aus.

2. Klicken Sie im Ordner **Microsoft Visual Studio** * Version * auf **Visual Studio** *Version*, öffnen Sie das Kontextmenü, und wählen Sie **Als Administrator ausführen** aus.

     Beim Starten von Visual Studio wird **(Administrator)** nach dem Produktnamen in der Titelleiste angezeigt.

## <a name="see-also"></a>Weitere Informationen
 [Portieren, Migrieren und Upgraden von Visual Studio-Projekten](../porting/porting-migrating-and-upgrading-visual-studio-projects.md) [Installieren von Visual Studio 2015](../install/install-visual-studio-2015.md)
