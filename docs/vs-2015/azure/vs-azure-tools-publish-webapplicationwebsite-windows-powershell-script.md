---
title: Publish-WebApplicationWebSite (Windows PowerShell-Skript) | Microsoft Docs
description: Informationen zum Veröffentlichen eines Webprojekts auf einer Azure-Website. Dieses Skript erstellt die erforderlichen Ressourcen in Ihrem Azure-Abonnement, wenn sie noch nicht vorhanden sind.
author: ghogen
manager: jillfra
assetId: 63cfaa2d-f04d-40dc-8677-345385c278d5
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: 3d56cfce70b0723b636b9b8ef7c6f3917015bf66
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75915545"
---
# <a name="publish-webapplicationwebsite-windows-powershell-script"></a>Publish-WebApplicationWebSite (Windows PowerShell-Skript)
## <a name="syntax"></a>Syntax
Veröffentlicht ein Webprojekt auf einer Azure-Website. Das Skript erstellt die erforderlichen Ressourcen in Ihrem Azure-Abonnement, wenn sie noch nicht vorhanden sind.

```
Publish-WebApplicationWebSite
–Configuration <configuration>
-SubscriptionName <subscriptionName>
-WebDeployPackage <packageName>
-DatabaseServerPassword @{Name = "name"; Password = "password"}
-SendHostMessagesToOutput
-Verbose
```

## <a name="configuration"></a>Konfiguration
Der Pfad zur JSON-Konfigurationsdatei, in der die Details der Bereitstellung beschrieben sind.

| Parameter | Standardwert |
| --- | --- |
| Aliase |Keine |
| Erforderlich? |true |
| Position |benannt |
| Standardwert |Keine |
| Pipelineeingabe akzeptieren? |false |
| Platzhalterzeichen akzeptieren? |false |

## <a name="subscriptionname"></a>SubscriptionName
Der Name des Azure-Abonnements, in dem Sie die Website erstellen möchten.

| Parameter | Standardwert |
| --- | --- |
| Aliase |Keine |
| Erforderlich? |false |
| Position |benannt |
| Standardwert |Keine |
| Pipelineeingabe akzeptieren? |false |
| Platzhalterzeichen akzeptieren? |false |

## <a name="webdeploypackage"></a>WebDeployPackage
Der Pfad zum Webbereitstellungspaket für die Veröffentlichung auf der Website. Sie können dieses Paket in Visual Studio mithilfe des Assistenten "Web veröffentlichen" erstellen. Weitere Informationen finden Sie unter [Erste Schritte mit Azure-Clouddiensten und ASP.NET](vs-azure-tools-publish-webapplicationwebsite-windows-powershell-script.md).

| Parameter | Standardwert |
| --- | --- |
| Aliase |Keine |
| Erforderlich? |false |
| Position |benannt |
| Standardwert |Keine |
| Pipelineeingabe akzeptieren? |false |
| Platzhalterzeichen akzeptieren? |false |

## <a name="databaseserverpassword"></a>DatabaseServerPassword
Der Benutzername und das Kennwort für die SQL-Datenbank in Azure.

| Parameter | Standardwert |
| --- | --- |
| Aliase |Keine |
| Erforderlich? |false |
| Position |benannt |
| Standardwert |Keine |
| Pipelineeingabe akzeptieren? |false |
| Platzhalterzeichen akzeptieren? |false |

## <a name="sendhostmessagestooutput"></a>SendHostMessagesToOutput
Falls "true", werden Nachrichten vom Skript in den Ausgabedatenstrom ausgegeben.

| Parameter | Standardwert |
| --- | --- |
| Aliase |Keine |
| Erforderlich? |false |
| Position |benannt |
| Standardwert |false |
| Pipelineeingabe akzeptieren? |false |
| Platzhalterzeichen akzeptieren? |false |

## <a name="remarks"></a>Bemerkungen
Eine ausführliche Erläuterung der Verwendung des Skripts zum Erstellen von Entwicklungs- und Testumgebungen finden Sie unter [Verwenden von Windows PowerShell-Skripts zum Veröffentlichen in Entwicklungs- und Testumgebungen](vs-azure-tools-publishing-using-powershell-scripts.md).

In der JSON-Konfigurationsdatei sind die Details angegeben, was bereitgestellt werden muss. Dazu zählen die Informationen, die Sie beim Erstellen des Projekts angegeben haben, z. B. den Namen und Benutzernamen für die Website. Sie umfassen auch die bereitzustellende Datenbank, sofern vorhanden. Der folgende Code zeigt ein Beispiel einer JSON-Konfigurationsdatei:

```json
{
    "environmentSettings": {
        "webSite": {
            "name": "WebApplication10554",
            "location": "West US"
        },
        "databases": [
            {
                "connectionStringName": "DefaultConnection",
                "databaseName": "WebApplication10554_db",
                "serverName": "iss00brc88",
                "user": "sqluser2",
                "password": "",
                "edition": "",
                "size": "",
                "collation": "",
                "location": "West US"
            }
        ]
    }
}
```

Sie können die JSON-Konfigurationsdatei bearbeiten, um den Umfang der Bereitstellung zu ändern. Der Abschnitt "Website" ist erforderlich, der Abschnitt "Datenbank" optional.

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen finden Sie unter [Publish-WebApplicationWebSite (Windows PowerShell-Skript)](vs-azure-tools-publish-webapplicationvm.md)
