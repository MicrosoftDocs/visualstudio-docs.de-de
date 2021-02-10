---
title: Arbeiten mit GitHub-Konten in Visual Studio
ms.date: 11/16/2020
ms.custom: ''
ms.topic: conceptual
description: Hier erfahren Sie, wie Sie Visual Studio mit GitHub-Konten verwenden.
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 9da0f2c2df796f50530f19252c7236c2bb606a10
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960480"
---
# <a name="work-with-github-accounts-in-visual-studio"></a>Arbeiten mit GitHub-Konten in Visual Studio

Wenn Sie über ein öffentliches GitHub- oder GitHub Enterprise-Konto verfügen, können Sie es Ihrer Visual Studio-Keychain hinzufügen. Nachdem Sie Ihr Konto hinzugefügt haben, können Sie die Plattformintegration nutzen, indem Sie direkt in Visual Studio auf GitHub-Repositorys zugreifen und diese erstellen.

## <a name="adding-public-github-accounts"></a>Hinzufügen von öffentlichen GitHub-Konten

Sie können Ihr öffentliches GitHub-Konto hinzufügen, wenn Sie bereits mit einem Microsoft-Konto oder einem Geschäfts-, Schul-oder Unikonto bei Visual Studio angemeldet sind.

1. Wählen Sie das Symbol mit Ihren Initialen rechts oben in der Visual Studio-Umgebung aus. Wählen Sie dann **Kontoeinstellungen...** aus, um Ihre Konten zu verwalten. Sie können das Dialogfeld „Kontoeinstellungen“ auch öffnen, indem Sie zu **Datei** > **Kontoeinstellungen** navigieren.

    :::image type="content" source="../ide/media/account-picker.png" alt-text="Konteneinstellungen":::

2. Wählen Sie im Untermenü **Alle Konten** das Pluszeichen aus, um ein Konto hinzuzufügen, und wählen Sie **GitHub** aus.

    :::image type="content" source="../ide/media/sign-in-add-github.png" alt-text="Auswählen der Option zum Hinzufügen eine GitHub-Kontos":::

3. Sie werden zum Browser umgeleitet, in dem Sie sich mit ihren GitHub-Anmeldeinformationen anmelden können. Nachdem Sie sich angemeldet haben, erhalten Sie eine Nachricht „Erfolgreich!“ im Browserfenster, und Sie können zu Visual Studio zurückkehren.

    :::image type="content" source="../ide/media/github-success-signin.png" alt-text="Nachricht „Erfolgreich!“ im Browser":::

4. Beide Konten sind im Untermenü **Alle Konten** vorhanden.

    :::image type="content" source="../ide/media/show-both-accounts.png" alt-text="Beide Konten werden angezeigt":::

Wenn Sie noch nicht mit einem anderen Konto bei Visual Studio angemeldet sind, wählen Sie den Link **Anmelden** rechts oben in der Visual Studio-Umgebung aus. Sie können das Dialogfeld „Kontoeinstellungen“ auch öffnen, indem Sie zu **Datei** > **Kontoeinstellungen** navigieren. Befolgen Sie anschließend die oben aufgeführten Anweisungen, um Ihr GitHub-Konto hinzuzufügen.

![Nicht angemeldeter Benutzer](../ide/media/vs2019_usernotsignedin.png)

## <a name="adding-github-enterprise-accounts"></a>Hinzufügen von GitHub Enterprise-Konten

In Visual Studio sind standardmäßig nur öffentliche GitHub-Konten aktiviert.

1. Navigieren Sie zu **Tools** > **Optionen**, und suchen Sie nach der Option **Konten**, um GitHub Enterprise-Konten zu aktivieren.

    :::image type="content" source="../ide/media/accounts-options.png" alt-text="Menüoption „Konten“":::

2. Aktivieren Sie dann das Kontrollkästchen **Include GitHub Enterprise Server accounts** (GitHub Enterprise Server-Konten einschließen). Wenn Sie das nächste Mal zu Ihren **Kontoeinstellungen** navigieren und versuchen, ein GitHub-Konto hinzuzufügen, werden Ihnen die Optionen für GitHub und GitHub Enterprise angezeigt.

    :::image type="content" source="../ide/media/github-enterprise-endpoint-signin.png" alt-text="Anmelden mit GitHub Enterprise":::

3. Nachdem Sie die Adresse Ihres GitHub Enterprise-Servers eingegeben haben, wählen Sie **Mit Ihrem Browser anmelden** aus. Dort können Sie sich mit ihren GitHub Enterprise-Anmeldeinformationen anmelden.

## <a name="see-also"></a>Siehe auch

- [Arbeiten mit mehreren Benutzerkonten](work-with-multiple-user-accounts.md)
- [Anmelden bei Visual Studio](signing-in-to-visual-studio.md)
