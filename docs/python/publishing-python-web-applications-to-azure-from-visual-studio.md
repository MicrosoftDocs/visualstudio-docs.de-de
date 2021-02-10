---
title: Veröffentlichen einer Python-App in Azure App Service
description: Optionen für das Veröffentlichen einer Python-App in Azure App Service, z. B. über die Git-Bereitstellung, Container für Linux und die Bereitstellung in IIS.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: b2848a54ddbce41b538bf58f82db42ede76026d1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912414"
---
# <a name="publish-to-azure-app-service"></a>Veröffentlichen in Azure App Service

Zurzeit wird Python unter Azure App Service für Linux unterstützt, und Sie können Apps mit [Git deploy](#publish-to-app-service-on-linux-using-git-deploy) und [Containern](#publish-to-app-service-on-linux-using-containers) veröffentlichen, wie in diesem Artikel beschrieben.

> [!Note]
> Python-Unterstützung in Azure App Service für Windows wird offiziell als veraltet eingestuft. Infolgedessen wird der Befehl **Veröffentlichen** in Visual Studio offiziell nur für ein [IIS-Ziel](#publish-to-iis) unterstützt, und Remotedebuggen für Azure App Service wird offiziell nicht mehr unterstützt.
>
> Das Feature [Veröffentlichen in App Service unter Windows](publish-to-app-service-windows.md) funktioniert jedoch vorerst noch, da die Python-Erweiterungen für App Service unter Windows verfügbar bleiben, aber nicht mehr gewartet oder aktualisiert werden.

## <a name="publish-to-app-service-on-linux-using-git-deploy"></a>Veröffentlichen in App Service unter Linux mit „Git deploy“

„Git deploy“ verbindet eine App Service-Instanz unter Linux mit einem bestimmten Branch eines Git-Repositorys. Durch das Committen von Code an diesen Branch erfolgt automatisch die Bereitstellung in App Service, und App Service installiert automatisch alle in *requirements.txt* aufgeführten Abhängigkeiten. In diesem Fall führt App Service unter Linux Ihren Code in einem vorkonfigurierten Containerimage aus, das den Gunicorn-Webserver verwendet. Zurzeit ist dieser Dienst als Vorschauversion verfügbar und wird für die Produktion nicht unterstützt.

Weitere Informationen finden Sie in den folgenden Artikeln in der Azure-Dokumentation:

- [Schnellstart: Erstellen einer Python-Web-App in App Service](/azure/app-service/containers/quickstart-python?toc=%2Fpython%2Fazure%2FTOC.json) bietet eine kurze exemplarische Vorgehensweise für den Git-Bereitstellungsvorgang mit einer einfachen Flask-App und der Bereitstellung aus einem lokalen Git-Repository.
- [Vorgehensweise: Konfigurieren von Python](/azure/app-service/containers/how-to-configure-python) beschreibt die Merkmale des App Service unter Linux-Containers und das Anpassen des Gunicorn-Startbefehls für Ihre App.

## <a name="publish-to-app-service-on-linux-using-containers"></a>Veröffentlichen in App Service unter Linux mit Containern

Anstatt den vordefinierten Container mit App Service unter Linux zu verwenden, können Sie Ihren eigenen Container bereitstellen. Mit dieser Option können Sie auswählen, welche Webserver Sie verwenden, und das Verhalten des Containers anpassen.

Es gibt zwei Optionen zum Erstellen, Verwalten und Pushen von Containern:

- Verwenden Sie Visual Studio Code und die Docker-Erweiterung, wie unter [Bereitstellen von Python mit Docker-Containern](https://code.visualstudio.com/docs/python/tutorial-deploy-containers) beschrieben. Auch wenn Sie Visual Studio Code nicht verwenden, enthält der Artikel hilfreiche Details zum Erstellen von Containerimages für Flask- und Django-Anwendungen mit den produktionsbereiten uwsgi- und nginx-Webservern. Anschließend können Sie die gleichen Container mit der Azure CLI bereitstellen.

- Verwenden Sie die Befehlszeile und die Azure CLI, wie unter [Verwenden eines benutzerdefinierten Docker-Images](/azure/app-service/containers/tutorial-custom-docker-image) in der Azure-Dokumentation beschrieben. Dieser Leitfaden ist jedoch generisch und nicht für Python spezifisch.

## <a name="publish-to-iis"></a>Veröffentlichen in IIS

Aus Visual Studio können Sie die Veröffentlichung mit dem Befehl **Veröffentlichen** für einen virtuellen Windows-Computer oder einen anderen IIS-fähigen Computer ausführen. Wenn Sie IIS verwenden, stellen Sie sicher, dass Sie eine Datei *web.config* in der App erstellen oder ändern, die IIS informiert, wo der Python-Interpreter zu finden ist. Weitere Informationen finden Sie unter [Konfigurieren von Web-Apps für IIS](configure-web-apps-for-iis-windows.md).
