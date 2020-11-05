---
title: Einrichten benannter Authentifizierungsanmeldeinformationen | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die Anmeldeinformationen angeben, mit denen Visual Studio Anforderungen für Azure authentifizieren kann, um eine Anwendung von Visual Studio aus in Azure zu veröffentlichen oder einen vorhandenen Clouddienst zu überwachen.
author: ghogen
manager: jillfra
assetId: 61570907-42a1-40e8-bcd6-952b21a55786
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: 5f45517eb12c5443667e7a308f03943ee394190e
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2020
ms.locfileid: "93399331"
---
# <a name="set-up-named-authentication-credentials"></a>Einrichten von benannten Anmeldeinformationen zur Authentifizierung

Wenn Sie eine Anwendung in Azure veröffentlichen oder einen vorhandenen Clouddienst überwachen möchten, benötigt Visual Studio folgende Anmeldeinformationen, um an Azure gerichtete Anforderungen zu authentifizieren: die Azure-Abonnement-ID und ein gültiges X.509-Zertifikat (v3) mit einem Schlüssel, der mindestens 2.048 Bit umfasst. Diese Anmeldeinformationen können auf folgende Arten angegeben werden:

- Navigieren Sie in Visual Studio zu **Ansicht > Server-Explorer** , klicken Sie mit der rechten Maustaste auf den Knoten **Azure** , klicken Sie auf **Verbindung mit Microsoft Azure-Abonnement herstellen** , und melden Sie sich an.
- Erstellen Sie eine Abonnementdatei (`.publishsettings`). Diese enthält einen öffentlichen Schlüssel für das Zertifikat. Die Abonnementdatei kann Anmeldeinformationen für mehrere Abonnements enthalten, wie in diesem Artikel beschrieben.

Hinweis: Diese Anmeldeinformationen unterscheiden sich von Anmeldeinformationen zur Authentifizierung von Anforderungen an Azure-Speicherdienste.

## <a name="create-a-subscription-file"></a>Erstellen einer Abonnementdatei

Klicken Sie im Server-Explorer mit der rechten Maustaste auf den Knoten **Azure** , und klicken Sie anschließend auf **Abonnements verwalten und filtern**. Klicken Sie auf die Registerkarte **Zertifikate** , und führen Sie eine der folgenden Aktionen aus:

- Wählen Sie **Importieren** , um das Dialogfeld **Microsoft Azure-Abonnements importieren** zu öffnen. Klicken Sie auf den Link **Abonnementdatei herunterladen** , und speichern Sie die heruntergeladene Datei im Browser an einem temporären Speicherort. Wechseln Sie zurück zum Dialogfeld, navigieren Sie zum Downloadspeicherort, und importieren Sie die Datei für die Authentifizierung.
- Wählen Sie ein aktives Abonnement aus, und klicken Sie auf **Bearbeiten**. Dadurch wird ein Dialogfeld geöffnet, in dem Sie ein vorhandenes Abonnement für die Verwendung bei der Authentifizierung bearbeiten können.
- Klicken Sie auf **Neu** , um das Dialogfeld **Neues Abonnement** zu öffnen, und geben Sie die erforderlichen Details an. Um das Zertifikat für den im Dialogfeld angegebenen Clouddienst hochzuladen, melden Sie sich beim Azure-Portal an, navigieren Sie zu Ihrem Clouddienst, klicken Sie auf **Einstellungen > Verwaltungszertifikate** , klicken Sie auf **Hochladen** , und geben Sie dann den Pfad zu der Datei vom Typ `.cer` an.

Wenn Sie selbst ein Zertifikat erstellen möchten, lesen Sie die Anleitung unter [Erstellen und Hochladen eines Verwaltungszertifikats für Azure](/azure/cloud-services/cloud-services-certs-create), und laden Sie das Zertifikat anschließend manuell in das [Azure-Portal](https://portal.azure.com/) hoch.

## <a name="next-steps"></a>Nächste Schritte

- [Allgemeine Übersicht über die Web-Apps](/azure/app-service/)
- [Bereitstellen der App in Azure App Service](/azure/app-service/app-service-deploy-local-git)
- [Bereitstellen von Webaufträgen mit Visual Studio](/azure/app-service/websites-dotnet-deploy-webjobs)
- [Erstellen und Bereitstellen eines Clouddiensts](/azure/cloud-services/cloud-services-how-to-create-deploy-portal)
