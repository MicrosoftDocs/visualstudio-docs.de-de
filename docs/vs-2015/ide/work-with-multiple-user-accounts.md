---
title: Arbeiten mit mehreren Benutzerkonten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: b73c865c-74e0-420e-89cc-43524f4aafd0
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7dc2ba585c500fe045d143a2b8baa2d193466fdf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75917786"
---
# <a name="work-with-multiple-user-accounts"></a>Arbeiten mit mehreren Benutzerkonten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie mehrere Microsoft-Konten und/oder Geschäfts- oder Schulkonten haben, können Sie all diese Konten zu Visual Studio hinzufügen, sodass Sie über jedes Konto auf die Ressourcen zugreifen können, ohne sich separat anmelden zu müssen. Zum Zeitpunkt der Erstellung von Visual Studio 2015 RTM unterstützen Azure, Application Insights, Team Foundation Server und Office 365-Dienste die optimierte Anmeldung. Zusätzliche Dienste werden im Laufe der Zeit verfügbar sein.

 Wenn Sie auf einem Computer mehrere Benutzerkonten hinzufügen, „wandert“ diese Gruppe von Konten mit Ihnen mit, wenn Sie sich auf einem anderen Computer bei Visual Studio anmelden. Zu beachten ist aber, dass zwar die Namen der Konten übernommen werden, die Anmeldeinformationen jedoch nicht. Aus diesem Grund werden Sie aufgefordert, die Anmeldeinformationen für die anderen Konten einzugeben, wenn Sie zum ersten Mal versuchen, die dazugehörigen Ressourcen auf dem neuen Computer zu verwenden.

 Diese exemplarische Vorgehensweise zeigt, wie Sie mehrere Konten zu Visual Studio hinzufügen und wie Sie feststellen, ob die über diese Konten zugänglichen Ressourcen an Stellen wie dem Dialogfeld **Verbundenen Dienst hinzufügen** , im **Server-Explorer**und im **Team Explorer**dargestellt werden.

#### <a name="sign-in-to-visual-studio"></a>Anmelden bei Visual Studio

1. Melden Sie sich mit einem Microsoft-Konto oder einem Unternehmenskonto bei Visual Studio 2015 an. Ihr Benutzername sollte oben rechts im Fenster angezeigt werden, etwa folgendermaßen:

     ![Aktuell angemeldeter Benutzer](../ide/media/vs2015-username.png "VS2015_UserName")

### <a name="access-your-azure-account-in-server-explorer"></a>Zugreifen auf Ihr Azure-Konto in Server-Explorer
 Drücken Sie **STRG + ALT + S** , um **Server-Explorer**zu öffnen. Klicken Sie auf das Azure-Symbol. Wenn es erweitert wird, sehen Sie die verfügbaren Ressourcen in dem Azure-Konto, das mit der ID verknüpft ist, die Sie zum Anmelden bei Visual Studio 2015 verwendet haben. Die Anzeige sieht etwa folgendermaßen aus, allerdings sehen Sie Ihre eigenen Ressourcen, nicht die von Herrn Guido:

 ![Server-Explorer zeigt den erweiterten "Azure Tools"-Knoten](../ide/media/vs2015-serverexplorer.png "VS2015_ServerExplorer")

 Wenn Sie Visual Studio auf einem bestimmten Gerät zum ersten Mal verwenden, zeigt das Dialogfeld nur die Abonnements an, die unter der ID registriert sind, mit der Sie sich bei der IDE angemeldet haben. Auf die Ressourcen Ihrer anderen Konten können Sie direkt über den **Server-Explorer** zugreifen, indem Sie mit der rechten Maustaste auf den Azure-Knoten klicken, **Abonnements verwalten und filtern** auswählen und Ihre Konten über das Kontoauswahl-Steuerelement hinzufügen. Um ein anderes Konto auszuwählen, klicken Sie auf den Pfeil nach unten, und wählen Sie das gewünschte Konto aus der Liste aus. Nach dem Auswählen des Kontos können Sie auswählen, welche Abonnements dieses Kontos im Server-Explorer angezeigt werden sollen.

 ![Dialogfeld "Azure-Abonnements verwalten"](../ide/media/vs2015-manage-subs.png "vs2015_manage_subs")

 Wenn Sie den Server-Explorer dann zum nächsten Mal öffnen, werden die Ressourcen für diese(s) Abonnement(s) angezeigt.

### <a name="access-your-azure-account-via-add-connected-service-dialog"></a>Zugreifen auf Ihr Azure-Konto über das Dialogfeld "Verbundenen Dienst hinzufügen"

1. Erstellen Sie ein Universal App-Projekt in C#.

2. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Hinzufügen > Verbundener Dienst** aus. Der Assistent zum Hinzufügen eines verbundenen Diensts zeigt die Liste der Dienste in dem Azure-Konto an, das mit Ihrer Visual Studio-Anmelde-ID verknüpft ist. Sie müssen sich nicht separat bei Azure anmelden. Allerdings müssen Sie sich beim ersten Versuch, von einem bestimmten Computer auf die Ressourcen eines anderen Kontos zuzugreifen, bei diesem Konto anmelden.

    > [!WARNING]
    > Wenn Sie zum ersten Mal eine Store-App in Visual Studio 2015 auf einem bestimmten Computer erstellen, werden Sie aufgefordert, Ihr Gerät für den Entwicklungsmodus zu aktivieren, indem Sie zu **Einstellungen &#124; wechseln. Updates und Sicherheits &#124; für Entwickler** auf Ihrem Computer. Weitere Informationen finden Sie unter [Aktivieren Ihres Geräts für die Entwicklung](https://msdn.microsoft.com/library/windows/apps/dn706236.aspx).

### <a name="access-azure-active-directory-in-a-web-project"></a><a name="access_azure"></a> Zugreifen auf Azure Active Directory in einem Webprojekt
 Azure AD unterstützt das einmalige Anmelden für Endbenutzer in ASP.NET MVC-Webanwendungen oder die AD-Authentifizierung in Web-API-Diensten. Die Domänenauthentifizierung unterscheidet sich von der Authentifizierung einzelner Benutzerkonten: Benutzer mit Zugriff auf Ihre Active Directory-Domäne können ihre vorhandenen Azure AD-Konten verwenden, um eine Verbindung zu Ihren Webanwendungen herzustellen. Auch Office 365-Anwendungen können die Domänenauthentifizierung verwenden. Erstellen Sie eine Webanwendung (**Datei > Neues Projekt > C# > Cloud > ASP.NET-Webanwendung**), um diesen Vorgang in der Praxis zu testen. Wählen Sie im Dialogfeld Neues ASP.net Projekt die Option **Authentifizierung ändern**aus. Der Authentifizierungsassistent wird angezeigt und ermöglicht es Ihnen, die Art der Authentifizierung in Ihrer Anwendung auszuwählen.

 ![Dialogfeld "Authentifizierung ändern" für ASP.NET](../ide/media/vs2015-change-authentication.png "VS2015_change_authentication")

 Weitere Informationen zu den verschiedenen Arten der Authentifizierung in ASP.NET finden Sie unter [Erstellen von ASP.NET-Webprojekten in Visual Studio 2013](/aspnet/visual-studio/overview/2013/creating-web-projects-in-visual-studio#orgauth) . Die Informationen zur Authentifizierung gelten auch für Visual Studio 2015.

### <a name="access-your-visual-studio-team-services-account"></a>Zugreifen auf Ihr Visual Studio Team Services-Konto
 Wählen Sie im Hauptmenü **Team > Verbindung mit Team Foundation Server herstellen** aus, um das Fenster **Team Explorer** aufzurufen. Klicken Sie auf **Teamprojekte auswählen**. Im Listenfeld unter **Team Foundation Server-Computer auswählen**sehen Sie die URL für Ihr Visual Studio Team Services-Konto. Nach Auswahl der URL werden Sie angemeldet, ohne Ihre Anmeldeinformationen erneut eingeben zu müssen.

## <a name="add-a-second-user-account-to-visual-studio"></a>Hinzufügen eines zweiten Benutzerkontos zu Visual Studio
 Klicken Sie auf den Abwärtspfeil neben Ihrem Benutzernamen oben rechts in Visual Studio. Klicken Sie anschließend auf das Menüelement **Kontoeinstellungen** . Im Dialogfeld **Konto-Manager** wird das Konto angezeigt, mit dem Sie sich angemeldet haben. Klicken Sie auf den Link **Konto hinzufügen** unten links im Dialogfeld, um ein neues Microsoft-Konto oder ein neues Geschäfts- bzw. Schulkonto hinzuzufügen.

 ![Visual Studio-Kontoauswahl](../ide/media/vs2015-acct-picker.png "VS2015_acct_picker")

 Folgen Sie den Anweisungen, um die neuen Anmeldeinformationen für das Konto einzugeben. Die folgende Abbildung zeigt den Konto-Manager, nachdem ein Benutzer sein Contoso.com-Geschäftskonto hinzugefügt hat.

 ![Konto-Manager](../ide/media/vs2015-accountmanager.gif "VS2015_AccountManager")

## <a name="revisit-the-add-connected-services-wizard-and-server-explorer"></a>Erneutes Aufrufen des Assistenten zum Hinzufügen verbundener Dienste und des Server-Explorers
 Wechseln Sie nun erneut zum **Server-Explorer**, klicken Sie mit der rechten Maustaste auf den Azure-Knoten, und wählen Sie **Abonnements verwalten und filtern** aus. Wählen Sie das neue Konto durch Klicken auf den Pfeil nach unten neben dem aktuellen Konto, und wählen Sie dann aus, welche Abonnements Sie im Server-Explorer anzeigen möchten. Es sollten alle Dienste angezeigt werden, die dem angegebenen Abonnement zugeordnet sind. Auch wenn Sie mit dem zweiten Konto gerade nicht bei der Visual Studio-IDE angemeldet sind, sind Sie bei den Diensten und Ressourcen dieses Kontos angemeldet. Das Gleiche gilt für **Projekt > Verbundenen Dienst hinzufügen** und **Team > Verbindung mit Team Foundation Server herstellen**.
