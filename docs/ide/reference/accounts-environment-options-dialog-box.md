---
title: Referenz für Kontenoptionen
description: Lernen Sie, einige Optionen im Zusammenhang mit den Konten festzulegen, die Sie zur Anmeldung in Visual Studio verwenden.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: 3cfe09d2-1120-46e8-b882-f7056acb778b
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b0c640b670802e3bb69a26d0b49bee6695955170
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956775"
---
# <a name="accounts-environment-options-dialog-box"></a>Konten, Umgebung, Dialogfeld „Optionen“

Verwenden Sie diese Seite zum Einrichten verschiedener Optionen im Zusammenhang mit den Konten, die Sie zur Anmeldung in Visual Studio verwenden.

## <a name="personalization-account"></a>Personalisierungskonto

### <a name="synchronize-settings-across-devices"></a>Synchronisieren von Einstellungen auf mehreren Geräten

Mit dieser Option können Sie angeben, ob Ihre Einstellungen mit mehreren Computern synchronisiert werden sollen. Weitere Informationen finden Sie unter [Synchronisierte Einstellungen](../../ide/synchronized-settings-in-visual-studio.md).

### <a name="enable-device-code-flow"></a>Gerätecodeflow aktivieren

Wenn diese Option aktiviert ist, ändert sich das Verhalten von Visual Studio, wenn Sie auf der Seite **Datei** > **Kontoeinstellungen** auf **Konto hinzufügen** klicken. Anstelle der Seite **Bei Ihrem Konto anmelden** wird ein Dialogfeld angezeigt, in dem eine URL und ein Code angezeigt wird, die Sie zur Anmeldung in einen Webbrowser einfügen können. Diese Option ist nützlich, wenn Sie sich nicht auf normalem Weg bei Visual Studio anmelden können, z. B wenn Sie eine ältere Version von Internet Explorer verwenden oder der Zugriff durch Ihre Firewall eingeschränkt wird. Weitere Informationen finden Sie unter [Arbeiten mit mehreren Benutzerkonten](../work-with-multiple-user-accounts.md#add-an-account-using-device-code-flow).

## <a name="registered-azure-clouds"></a>Registrierte Azure-Clouds

In diesem Abschnitt werden die Azure-Cloudinstanzen gezeigt, auf die Sie über mindestens ein Konto zugreifen können, mit dem Sie sich bei Visual Studio angemeldet haben. Zum Beispiel verfügen Sie möglicherweise über Zugriff auf eine private Azure-Instanz im Rechenzentrum Ihres Unternehmens. Sie verfügen vielleicht auch über Zugriff auf eine Sovereign Cloud- oder Government Cloud-Instanz von Azure, z. B. Azure China 21 Vianet oder Azure US Government. Die globale Azure-Cloudinstanz wird standardmäßig in der Liste aufgeführt, und Sie können sie nicht entfernen.

Registrieren Sie eine zusätzliche Azure-Cloud, indem Sie auf **Hinzufügen** klicken. Im Dialogfeld **Neue Azure-Cloud hinzufügen** werden mehrere bekannte Azure-Cloudinstanzen aufgeführt, mit denen Sie eine Verbindung herstellen können. Sie können aber auch die URL zu einem privaten Azure-Endpunkt eingeben.

![Neue Azure-Cloudinstanz hinzufügen](media/add-new-azure-cloud.png)

Nachdem Sie eine zusätzliche Azure-Cloud registriert haben, können Sie auswählen, bei welcher Azure-Cloud Sie sich anmelden möchten, wenn Sie sich bei Visual Studio anmelden.

## <a name="see-also"></a>Weitere Informationen

- [Synchronisieren von Einstellungen auf mehreren Computern](../synchronized-settings-in-visual-studio.md)
- [Anmelden bei Visual Studio](../signing-in-to-visual-studio.md)
- [Arbeiten mit mehreren Benutzerkonten](../work-with-multiple-user-accounts.md)
- [Umgebungseinstellungen](../environment-settings.md)
