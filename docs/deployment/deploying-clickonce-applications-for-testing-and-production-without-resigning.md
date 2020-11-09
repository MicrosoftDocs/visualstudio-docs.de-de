---
title: ClickOnce-apps ohne erneute Signatur bereitstellen
description: Erfahren Sie mehr über das Bereitstellen von ClickOnce-Anwendungen aus mehreren Netzwerk Standorten, ohne die ClickOnce-Manifeste neu zu signieren
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, deploying without resigning
- ClickOnce deployment, without resigning
- application updates, ClickOnce
- update location [ClickOnce]
- deploymentProvider tag
- manifests [ClickOnce]
ms.assetid: 1218a98d-1ad5-4eef-95dd-0e0b3c44168c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5644a890a8705c68852cb5f67e4d998e12338dc
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382935"
---
# <a name="deploy-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Bereitstellen von ClickOnce-Anwendungen für Test-und Produktionsserver ohne erneutes Signieren
In diesem Artikel wird eine Funktion von ClickOnce beschrieben, die in der .NET Framework Version 3,5 eingeführt wurde, die die Bereitstellung von ClickOnce-Anwendungen von mehreren Netzwerk Standorten aus ermöglicht, ohne dass die ClickOnce-Manifeste neu signiert oder geändert werden

> [!NOTE]
> Das erneute Signieren ist nach wie vor die bevorzugte Methode für die Bereitstellung neuer Versionen von Anwendungen. Verwenden Sie nach Möglichkeit die Methode zum erneuten Signieren. Weitere Informationen finden Sie unter [ *Mage.exe* (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

 Entwickler und ISVs von Drittanbietern können diese Funktion abonnieren, was ihren Kunden die Aktualisierung Ihrer Anwendungen erleichtert. Diese Funktion kann in den folgenden Situationen verwendet werden:

- Beim Aktualisieren einer Anwendung, nicht bei der ersten Installation einer Anwendung.

- Wenn es nur eine Konfiguration der Anwendung auf einem Computer gibt. Wenn beispielsweise eine Anwendung so konfiguriert ist, dass Sie auf zwei unterschiedliche Datenbanken verweist, können Sie diese Funktion nicht verwenden.

## <a name="exclude-deploymentprovider-from-deployment-manifests"></a>DeploymentProvider von Bereitstellungs Manifesten ausschließen
 In den .NET Framework 2,0 und .NET Framework 3,0 muss jede ClickOnce-Anwendung, die auf dem System zur Offline Verfügbarkeit installiert wird, eine `deploymentProvider` in Ihrem Bereitstellungs Manifest auflisten. `deploymentProvider`Wird häufig als Update Speicherort bezeichnet. Hierbei handelt es sich um den Speicherort, an dem ClickOnce auf Anwendungs Updates überprüft. Diese Anforderung, zusammen mit der Anforderung, dass Anwendungs Herausgeber ihre bereit Stellungen signieren müssen, erschwert es einem Unternehmen, eine ClickOnce-Anwendung von einem Hersteller oder einem anderen Drittanbieter zu aktualisieren. Außerdem ist es schwieriger, dieselbe Anwendung von mehreren Speicherorten im gleichen Netzwerk aus bereitzustellen.

 Mit Änderungen, die in der .NET Framework 3,5 an ClickOnce vorgenommen wurden, ist es möglich, dass ein Drittanbieter eine ClickOnce-Anwendung für eine andere Organisation bereitstellt, die dann die Anwendung in einem eigenen Netzwerk bereitstellen kann.

 Um dieses Feature nutzen zu können, müssen Entwickler von ClickOnce-Anwendungen `deploymentProvider` von ihren Bereitstellungs Manifesten ausschließen. Diese Anforderung bedeutet, dass Sie das-Argument ausschließen müssen, `-providerUrl` Wenn Sie Bereitstellungs Manifeste mit Mage.exe erstellen. Wenn Sie Bereitstellungs Manifeste mit MageUI.exe erstellen, müssen Sie sicherstellen, dass das Textfeld **Startort** auf der Registerkarte **Anwendungs Manifest** leer bleibt.

## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider und Anwendungs Updates
 Ab dem .NET Framework 3,5 müssen Sie `deploymentProvider` in Ihrem Bereitstellungs Manifest keinen mehr angeben, um eine ClickOnce-Anwendung für die Online-und Offline Verwendung bereitzustellen. Diese Änderung unterstützt das Szenario, in dem Sie die Bereitstellung selbst verpacken und signieren müssen, aber anderen Unternehmen die Bereitstellung der Anwendung über ihre Netzwerke erlauben.

 Wichtig zu beachten ist, dass Anwendungen, die eine ausschließen `deploymentProvider` , den Installationsort während der Updates nicht ändern können, bis Sie ein Update mit dem `deploymentProvider` Tag erneut senden.

 Es folgen zwei Beispiele, um diesen Punkt zu verdeutlichen. Im ersten Beispiel veröffentlichen Sie eine ClickOnce-Anwendung, die kein `deploymentProvider` Tag hat, und Sie bitten Benutzer, Sie aus zu installieren `http://www.adatum.com/MyApplication/` . Wenn Sie das nächste Update der Anwendung aus veröffentlichen möchten `http://subdomain.adatum.com/MyApplication/` , haben Sie keine Möglichkeit, dies im Bereitstellungs Manifest zu signalisieren, das sich in befindet `http://www.adatum.com/MyApplication/` . Sie haben zwei Möglichkeiten:

- Teilen Sie den Benutzern mit, dass Sie die vorherige Version deinstallieren, und installieren Sie die neue Version am neuen Speicherort.

- Fügen Sie ein Update für `http://www.adatum.com/MyApplication/` ein, das eine enthält `deploymentProvider` , auf die verweist `http://www.adatum.com/MyApplication/` . Anschließend können Sie später ein weiteres Update freigeben, das `deploymentProvider` auf verweist `http://subdomain.adatum.com/MyApplication/` .

  Im zweiten Beispiel veröffentlichen Sie eine ClickOnce-Anwendung, die angibt `deploymentProvider` und Sie dann entfernen. Sobald die neue Version ohne `deploymentProvider` auf Clients heruntergeladen wird, können Sie den für Updates verwendeten Pfad erst umleiten, wenn Sie eine Version der `deploymentProvider` wiederhergestellten Anwendung freigeben. Wie im ersten Beispiel, `deploymentProvider` muss zunächst auf den aktuellen Update Speicherort und nicht auf den neuen Speicherort zeigen. Wenn Sie in diesem Fall versuchen, eine einzufügen, `deploymentProvider` die auf verweist `http://subdomain.adatum.com/MyApplication/` , schlägt das nächste Update fehl.

## <a name="create-a-deployment"></a>Erstellen einer Bereitstellung
 Eine Schritt-für-Schritt-Anleitung zum Erstellen von bereit Stellungen, die von verschiedenen Netzwerk Standorten aus bereitgestellt werden können, finden Sie unter Exemplarische Vorgehensweise [: Manuelles Bereitstellen einer ClickOnce-Anwendung, für die keine erneute Signierung erforderlich](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)ist

## <a name="see-also"></a>Siehe auch
- [*Mage.exe* (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [*MageUI.exe* (Manifest Generation and Editing Tool, grafischer Client)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
