---
title: Anmelden bei Visual Studio
description: Erfahren Sie, wie Sie sich bei Visual Studio anmelden.
titleSuffix: ''
ms.custom: seodec18, contperf-fy21q1
ms.date: 09/11/2020
ms.topic: how-to
ms.assetid: b9531c25-e4cf-43ae-b331-a9f31a8cd171
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2bc45ae5732db5033a1b123ef18cda27c426fd6f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878525"
---
# <a name="sign-in-to-visual-studio"></a>Anmelden bei Visual Studio

Sie können Ihre Bereitstellungsumgebung in Visual Studio personalisieren und optimieren, wenn Sie sich mit Ihrem Personalisierungskonto anmelden.

> [!NOTE]
> Dieses Thema gilt für Visual Studio unter Windows. Informationen zu Visual Studio für Mac finden Sie unter [Anmelden bei Visual Studio für Mac](/visualstudio/mac/signing-in).

::: moniker range="vs-2017"

> [! ACHTUNG] Wenn Sie Visual Studio 2017 verwenden, um auf Ressourcen zuzugreifen, die für bedingten Zugriff konfiguriert sind, kann dies zu einer verschlechterten Authentifizierung führen, da innerhalb derselben Visual Studio-Sitzung mehrmals eine erneute Authentifizierung angefordert wird. 
> Um mit Ressourcen zu arbeiten, die für bedingten Zugriff konfiguriert sind, aktualisieren Sie mindestens auf Visual Studio 2019 Update 16.6. Weitere Informationen finden Sie unter [Erfahren Sie, wie Visual Studio mit Konten verwendet wird, die mehrstufige Authentifizierung erfordern](work-with-multi-factor-authentication.md).

::: moniker-end

## <a name="why-should-i-sign-in-to-visual-studio"></a>Warum sollte ich mich in Visual Studio anmelden?

Wenn Sie sich anmelden, haben Sie im vollen Umfang Zugang zu den Funktionen von Visual Studio. Beispielsweise können Sie u. a. nach der Anmeldung Ihre [Einstellungen auf mehreren Geräten synchronisieren](synchronized-settings-in-visual-studio.md), die Lizenz für eine Testversion verlängern und automatisch eine Verbindung mit einem Azure-Dienst herstellen.

Im Folgenden werden alle Anmeldevorteile aufgeführt:
- **Verlängerung des Visual Studio-Testzeitraums:** Sie können Visual Studio Professional oder Visual Studio Enterprise für 90 Tage zusätzlich verwenden und sind nicht auf den Testzeitraum von 30 Tagen beschränkt. Weitere Informationen finden Sie unter [Erweitern einer Testversion oder Aktualisieren einer Lizenz](../ide/how-to-unlock-visual-studio.md).

- **Visual Studio Community-Edition weiter verwenden:** Wenn die Installation Ihrer Community-Edition eine Lizenz von Ihnen anfordert, melden Sie sich bei der IDE an, um Visual Studio Community weiterhin **kostenlos** zu verwenden. 

- **Machen Sie Visual Studio verfügbar, wenn Sie ein Konto verwenden, das mit einem Visual Studio-Abonnement oder mit einer Azure DevOps-Organisation verknüpft ist**. Ausführliche Informationen finden Sie unter [Erweitern einer Testversion oder Aktualisieren einer Lizenz](../ide/how-to-unlock-visual-studio.md).

- **Zugang zum Visual Studio Dev Essentials-Programm:** Dieses Programm umfasst u.a. kostenlose Softwareangebote und Support. Weitere Informationen finden Sie unter [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) .

- **Synchronisation der Visual Studio-Einstellungen:** Von Ihnen angepasste Einstellungen, beispielsweise Tastenzuordnung, Fensterlayout und Farbdesign, werden sofort übernommen, wenn Sie sich auf einem beliebigen Gerät bei Visual Studio anmelden. Siehe hierzu [Synchronisieren von Visual Studio-Einstellungen](../ide/synchronized-settings-in-visual-studio.md).

- **Automatische Verbindung mit Diensten wie Azure und Azure DevOps Services** über die IDE, ohne dass Sie erneut aufgefordert werden, für dasselbe Konto Ihre Anmeldeinformationen einzugeben.

## <a name="how-to-sign-in-to-visual-studio"></a>So melden Sie sich bei Visual Studio an

Wenn Sie Visual Studio erstmals öffnen, werden Sie aufgefordert, sich anzumelden und einige grundlegenden Registrierungsinformationen bereitzustellen.

![Aufforderung zum Anmelden](../ide/media/vs2019_signinpopup.png)

Sie sollten ein Microsoft-Konto oder ein Arbeits- oder Schulkonto auswählen, das Sie bestmöglich repräsentiert. Wenn Sie keines dieser Konten besitzen, können Sie kostenlos ein Microsoft-Konto erstellen, indem Sie auf den Link unter der Anmeldeschaltfläche klicken. Falls Problemen auftreten, lesen Sie [Erstellen eines neuen Microsoft-Kontos](https://support.microsoft.com/help/4026324/microsoft-account-how-to-create).

Wählen Sie anschließend die gewünschten Einstellungen für die Benutzeroberfläche und das Farbschema in Visual Studio aus. Visual Studio speichert diese Einstellungen und synchronisiert sie über alle Visual Studio-Umgebungen hinweg, an denen Sie sich angemeldet haben. Eine Liste der synchronisierten Einstellungen finden Sie unter [Synchronisierte Einstellungen](../ide/synchronized-settings-in-visual-studio.md). Sie können die Einstellungen später im Visual Studio-Menü unter **Extras** > **Optionen** ändern.

Nach Angabe der Einstellungen wird Visual Studio gestartet. Sie sind nun registriert und können beginnen. Um sicherzustellen, dass Sie angemeldet sind, suchen Sie in der rechten oberen Ecke der Visual Studio-Umgebung nach Ihrem Namen.

![Aktuell angemeldeter Benutzer in VS2019](../ide/media/vs2019_username.png)

Wenn Sie sich beim ersten Öffnen von Visual Studio nicht anmelden möchten, können Sie dies später jederzeit nachholen. Suchen Sie nach dem Link **Anmelden** oben rechts in der Visual Studio-Umgebung.

![Nicht angemeldeter Benutzer](../ide/media/vs2019_usernotsignedin.png)

Sofern Sie sich nicht abmelden, sind Sie automatisch angemeldet, wenn Sie Visual Studio starten. Alle Änderungen an synchronisierten Einstellungen werden automatisch übernommen. Klicken Sie zur Abmeldung oben rechts in der Visual Studio-Umgebung auf das Symbol mit Ihrem Profilnamen, wählen Sie den Befehl **Kontoeinstellungen** aus, und klicken Sie dann auf den Link **Abmelden**. Für eine erneute Anmeldung wählen Sie den Befehl **Anmelden** in der rechten oberen Ecke der Visual Studio-Umgebung.

## <a name="to-change-your-profile-information"></a>So ändern Sie Profilinformationen

1. Wechseln Sie zu **Datei** > **Kontoeinstellungen**, und klicken Sie auf den Link **Visual Studio-Profil verwalten**.

1. Wählen Sie im Browserfenster **Profil bearbeiten** aus, und ändern Sie die gewünschten Einstellungen.

1. Wählen Sie anschließend **Änderungen speichern** aus.

## <a name="troubleshooting"></a>Problembehandlung

Wenn es bei der Anmeldung zu Problemen kommt, erhalten Sie auf der Seite [Support für Abonnements](https://visualstudio.microsoft.com/subscriptions/support/) Hilfe.

## <a name="see-also"></a>Siehe auch

* [Erweitern einer Testversion oder Aktualisieren einer Lizenz](../ide/how-to-unlock-visual-studio.md)
* [Arbeiten mit GitHub-Konten in Visual Studio](../ide/work-with-github-accounts.md)
* [Übersicht über die Visual Studio-IDE](../get-started/visual-studio-ide.md)
* [Anmelden (Visual Studio für Mac)](/visualstudio/mac/signing-in)
* [Aktivierung (Visual Studio für Mac)](/visualstudio/mac/activation)
