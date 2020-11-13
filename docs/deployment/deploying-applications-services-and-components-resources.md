---
title: Stellen Sie Ihre Visual Studio-App in einem Ordner, in IIS, in Azure oder in einem anderen Ziel bereit.
titleSuffix: ''
description: Hier erhalten Sie weitere Informationen zu Veröffentlichungsoptionen für Ihre App mit dem Veröffentlichungstool.
ms.custom:
- SEO-VS-2020
- contperfq1
ms.date: 08/21/2020
ms.topic: troubleshooting
dev_langs:
- FSharp
- VB
- CSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 45fc0a58262a533416f630ede795d0060f9fc909
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94434492"
---
# <a name="deploy-your-app-to-a-folder-iis-azure-or-another-destination"></a>Stellen Sie Ihre App in einem Ordner, in IIS, in Azure oder einem anderen Ziel bereit.

Wenn Sie eine Anwendung, einen Dienst oder eine Komponente bereitstellen, verteilen Sie diese für die Installation auf anderen Computern, Geräten, Servern oder in der Cloud. Wählen Sie die entsprechende Methode für den Typ der Bereitstellung in Visual Studio aus, den Sie benötigen.

Hilfe zu Ihrer Bereitstellungsaufgabe:

- Sind Sie nicht sicher, welche Bereitstellungsoption Sie wählen sollen? Siehe [Welche Optionen für die Veröffentlichung sind für mich geeignet?](#what-publishing-options-are-right-for-me).
- Hilfe zu Bereitstellungsproblemen für Azure App Service oder IIS finden Sie unter [Problembehandlung bei ASP.NET Core in Azure App Service und IIS](/aspnet/core/test/troubleshoot-azure-iis).
- Hilfe zum Konfigurieren der .NET-Bereitstellungseinstellungen finden Sie unter [Konfigurieren von .NET-Bereitstellungseinstellungen](#configure-net-deployment-settings).
- Wenn Sie zuvor ein Veröffentlichungsprofil erstellt haben, wählen Sie für die Bereitstellung auf einem neuen Ziel im Fenster **Veröffentlichen** für ein konfiguriertes Profil **Neu** aus.

   ![Erstellen eines neuen Veröffentlichungsprofils](../deployment/media/create-a-new-publish-profile.png)

   Wählen Sie dann im Fenster „Veröffentlichen“ eine Bereitstellungsoption aus. Informationen zu den Veröffentlichungsoptionen finden Sie in den folgenden Abschnitten.

## <a name="what-publishing-options-are-right-for-me"></a>Welche Optionen für die Veröffentlichung sind für mich geeignet?

Apps können aus Visual Studio direkt auf die folgenden Ziele veröffentlicht werden:

::: moniker range=">=vs-2019"
- [Azure](#azure)
- [Docker-Containerregistrierung](#docker-container-registry)
- [Ordner](#folder)
- [FTP/FTPS-Server](#ftpftps-server)
- [Webserver (IIS)](#web-server-iis)
- [Profil importieren](#import-profile)
::: moniker-end
::: moniker range="vs-2017"
- [App Service](#azure-app-service)
- [App Service (Linux)](#azure-app-service)
- [IIS (Auswählen von IIS, FTP usw.)](#web-server-iis)
- [FTP/FTPS (Auswählen von IIS, FTP usw.)](#ftpftps-server)
- [Ordner](#folder)
- [Profil importieren](#import-profile)
::: moniker-end

Die vorangehenden Optionen werden wie in der folgenden Abbildung dargestellt angezeigt, wenn Sie ein neues Veröffentlichungsprofil erstellen.

::: moniker range=">=vs-2019"
![Auswählen einer Veröffentlichungsoption](../deployment/media/quickstart-publish-dialog.png)
::: moniker-end
::: moniker range="vs-2017"
![Auswählen einer Veröffentlichungsoption](../deployment/media/quickstart-publish-dialog-vs-2017.png)
::: moniker-end

Einen kurzen Überblick über allgemeinere Optionen für die Anwendungsbereitstellung finden Sie unter [Erster Einblick in die Bereitstellung](../deployment/deploying-applications-services-and-components.md).

## <a name="azure"></a>Azure 

Wenn Sie Azure auswählen, können Sie zwischen den folgenden Optionen wählen:

- [Azure App Service](#azure-app-service) unter Windows, Linux oder als Docker-Image ausgeführt
- Ein Docker-Image, das der [Azure Container Registry](#azure-container-registry) bereitgestellt wird
- [Ein virtueller Azure-Computer](#azure-virtual-machine)

![Auswahl eines Azure-Diensts](../deployment/media/quickstart-choose-azure-service.png)

### <a name="azure-app-service"></a>Azure App Service

[Azure App Service](/azure/app-service/app-service-web-overview) ermöglicht Entwicklern, schnell und ohne die Verwaltung von Infrastruktur skalierbare Webanwendungen und -dienste zu erstellen. Ein App Service wird auf in der Cloud gehosteten virtuellen Computern in Azure ausgeführt, aber diese virtuellen Maschinen werden für Sie verwaltet. Jeder App in einem App Service wird eine eindeutige „\*. azurewebsites.net“-URL zugeordnet. Alle Tarife (außer „kostenlos“) ermöglichen, dass Sie der Website benutzerdefinierte Domänennamen zuweisen.

Sie bestimmen, wie viel Computingleistung dem App Service zur Verfügung stehen, indem Sie einen [Tarif oder Plan](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview) für den enthaltenden App Service auswählen. Sie können mehrere Web-Apps (und andere App-Typen) ohne Tarifänderung den gleichen App Service nutzen lassen. Sie können z.B. Entwicklungs-, Staging- und Produktions-Web-Apps gemeinsam im selben App Service hosten.

#### <a name="when-to-choose-azure-app-service"></a>Wann sollten Sie Azure App Service wählen?

- Sie möchten eine Webanwendung bereitstellen, auf die über das Internet zugegriffen werden kann.
- Sie möchten Ihre Webanwendung automatisch entsprechend Ihrem Bedarf skalieren, ohne sie erneut bereitstellen zu müssen.
- Sie möchten keine Serverinfrastruktur (einschließlich Softwareupdates) verwalten.
- Auf den Servern, auf denen Ihre Anwendung gehostet wird, sind keine Anpassungen auf Computerebene erforderlich.

> Wenn Sie Azure App Service in Ihrem eigenen Datencenter oder anderen lokalen Computern verwenden möchten, können Sie dazu [Azure Stack](https://azure.microsoft.com/overview/azure-stack/) verwenden.

Weitere Informationen zum Veröffentlichen in App Service finden Sie unter:
- [Schnellstart: Veröffentlichen in Azure App Service](quickstart-deploy-to-azure.md)
- [Schnellstart: Veröffentlichen einer ASP.NET Core-App in Azure App Service mit Visual Studio unter Linux](quickstart-deploy-to-linux.md)
- [Veröffentlichen einer ASP.NET Core-App in Azure mit Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)
- [Problembehandlung bei ASP.NET Core in Azure App Service und IIS](/aspnet/core/test/troubleshoot-azure-iis).

### <a name="azure-container-registry"></a>Azure Container Registry

Mit [Azure Container Registry](/azure/container-registry/) können Sie Docker-Containerimages und -artefakte in einer privaten Registrierung für alle Arten von Containerbereitstellungen erstellen, speichern und verwalten.

#### <a name="when-to-choose-azure-container-registry"></a>Unter welchen Umständen Azure Container Registry ausgewählt werden sollte

- Wenn Sie über eine Entwicklungs- und Bereitstellungspipeline für Docker-Container verfügen.
- Wenn Sie Docker-Containerimages in Azure erstellen möchten.

Weitere Informationen finden Sie unter:

- [Bereitstellen eines ASP.NET-Containers an eine Containerregistrierung mithilfe von Visual Studio](../containers/hosting-web-apps-in-docker.md)

### <a name="azure-virtual-machine"></a>Virtueller Azure-Computer

Mit [Azure Virtual Machines (VMs)](https://azure.microsoft.com/documentation/services/virtual-machines/) können Sie eine beliebige Anzahl von Computingressourcen in der Cloud erstellen und verwalten. Indem Sie die Verantwortung für die gesamte Software und alle Updates auf den VMs übernehmen, können Sie diese wie gewünscht dem Bedarf Ihrer App anpassen. Sie können direkt über den Remotedesktop auf die VMs zugreifen, und jeder behält, sofern gewünscht, die ihm zugewiesene IP-Adresse bei.

Beim Skalieren einer App, die auf virtuellen Computern gehostet wird, werden zusätzliche VMs entsprechend dem Bedarf sowie die erforderliche Software bereitgestellt. Diese zusätzliche Kontrollebene ermöglicht Ihnen, in verschiedenen Regionen weltweit unterschiedliche Skalierungen vorzunehmen. Wenn Ihre Anwendung beispielsweise von Mitarbeitern in einer Vielzahl von Zweigstellen eingesetzt wird, können Sie Ihre virtuellen Computer entsprechend der Anzahl der Mitarbeiter in diesen Regionen skalieren und damit potenziell Kosten senken.

Weitere Informationen finden Sie in dem [detaillierten Vergleich](/azure/architecture/guide/technology-choices/compute-decision-tree) zwischen Azure App Service, Azure Virtual Machines und anderen Azure-Diensten, die Sie als Bereitstellungsziel mithilfe der Option „Benutzerdefiniert“ in Visual Studio verwenden können.

#### <a name="when-to-choose-azure-virtual-machines"></a>Unter welchen Umständen Sie Azure Virtual Machines wählen sollten

- Sie möchten eine über das Internet zugängliche Webanwendung mit vollständiger Kontrolle über die Lebensdauer der zugewiesenen IP-Adressen bereitstellen.
- Sie benötigen auf den Servern Anpassungen auf Computerebene, einschließlich Software, wie z. B. ein spezielles Datenbanksystem, bestimmte Netzwerkkonfigurationen, Datenträgerpartitionen usw.
- Sie benötigen hochgradige Kontrolle über die Skalierung Ihrer Webanwendung.
- Sie benötigen aus anderen Gründen direkten Zugriff auf die Server, auf denen Ihre Anwendung gehostet wird.

> Wenn Sie Azure Virtual Machines in Ihrem eigenen Datencenter oder anderen lokalen Computern verwenden möchten, können Sie dazu [Azure Stack](https://azure.microsoft.com/overview/azure-stack/) verwenden.

## <a name="docker-container-registry"></a>Docker-Containerregistrierung

Wenn Ihre Anwendung Docker verwendet, können Sie Ihre containerisierte Anwendung in einer Docker-Containerregistrierung veröffentlichen.

### <a name="when-to-choose-docker-container-registry"></a>Unter welchen Umständen eine Docker-Containerregistrierung ausgewählt werden sollte

- Sie möchten eine containerisierte Anwendung bereitstellen.

Weitere Informationen finden Sie unter

- [Bereitstellen eines ASP.NET-Containers an eine Containerregistrierung mithilfe von Visual Studio](../containers/hosting-web-apps-in-docker.md)
- [Bereitstellen in Docker Hub](../containers/deploy-docker-hub.md)

## <a name="folder"></a>Ordner

Bereitstellung im Dateisystem bedeutet, dass Sie die Dateien Ihrer App in einen bestimmten Ordner auf Ihrem eigenen Computer kopieren. Die Bereitstellung in einem Ordner erfolgt meistens zu Testzwecken oder zum Bereitstellen der Anwendung für die Verwendung durch eine begrenzte Anzahl von Personen, wenn auf dem Computer auch ein Server ausgeführt wird. Wird der Zielordner in einem Netzwerk freigegeben, können die Webanwendungsdateien durch das Bereitstellen im Dateisystem für andere Personen verfügbar gemacht werden, die diese dann auf bestimmten Servern bereitstellen können.
::: moniker range=">=vs-2019"
Ab Visual Studio 2019 16.8 beinhaltet das Ordnerziel die Möglichkeit, eine .NET-Windows-Anwendung mithilfe von ClickOnce zu veröffentlichen.

Wenn Sie eine .NET Core 3.1-Windows-Anwendung (oder höher) mit ClickOnce veröffentlichen möchten, finden Sie weitere Informationen unter [Bereitstellen einer .NET-Windows-Anwendung mit ClickOnce](quickstart-deploy-using-clickonce-folder.md).
::: moniker-end
Alle lokalen Computer, auf denen ein Server ausgeführt wird, können die App, abhängig von Konfiguration und Netzwerkverbindungen, über das Internet oder ein Intranet zur Verfügung stellen. (Wenn Sie einen Computer direkt mit dem Internet verbinden, müssen Sie ihn besonders vor externen Sicherheitsrisiken schützen.) Da Sie diese Computer verwalten, haben Sie vollständige Kontrolle über die Software- und Hardwarekonfigurationen.

Wenn die Verwendung von Clouddiensten wie Azure App Service oder Azure Virtual Machines aus irgendeinem Grund (z. B. Computerzugriff) nicht möglich ist, können Sie [Azure Stack](https://azure.microsoft.com/overview/azure-stack/) in Ihrem eigenen Rechenzentrum verwenden. Azure Stack ermöglicht die lokale Verwaltung und Verwendung von Computerressourcen über Azure App Service und Azure Virtual Machines.

### <a name="when-to-choose-file-system-deployment"></a>Wann sollten Sie die Bereitstellung im Dateisystem wählen?

- Sie müssen die Anwendung nur auf einer Dateifreigabe bereitstellen. Von dort werden sie von anderen Benutzern auf verschiedenen Servern bereitgestellt.
::: moniker range=">=vs-2019"
- Sie möchten eine .NET-Windows-Anwendung mithilfe von ClickOnce bereitstellen
::: moniker-end
- Sie benötigen nur eine lokale Testbereitstellung.
- Sie möchten Anwendungsdateien einzeln untersuchen und möglicherweise ändern, bevor sie auf ein anderes Bereitstellungsziel gesendet werden.

Weitere Informationen finden Sie unter [Bereitstellen einer App in einem lokalen Ordner mithilfe von Visual Studio](quickstart-deploy-to-local-folder.md).
::: moniker range=">=vs-2019"
Weitere Informationen zum Bereitstellen einer .NET-Windows-Anwendung mit ClickOnce finden Sie unter [Bereitstellen einer .NET-Windows-Anwendung mit ClickOnce](quickstart-deploy-using-clickonce-folder.md).
::: moniker-end

Weitere Hilfe zum Auswählen der Einstellungen finden Sie in den folgenden Themen:

- [Übersicht über die .NET Core-Anwendungsveröffentlichung](/dotnet/core/deploying/)
- [.NET Core-RID-Katalog](/dotnet/core/rid-catalog)
- [Grundlagen der Buildkonfiguration](../ide/understanding-build-configurations.md)

## <a name="ftpftps-server"></a>FTP/FTPS-Server

Mit einem FTP/FTPS-Server können Sie die Anwendung auf einem anderen Server als Azure bereitstellen. Sie können die Webanwendung in einem Dateisystem oder auf einem anderen Server (Internet oder Intranet) bereitstellen, auf das bzw. den Sie Zugriff haben, einschließlich Ziele in anderen Clouddiensten. Es funktioniert mit Web Deploy (Dateien oder ZIP) und FTP.

Wenn Sie einen FTP/FTPS-Server auswählen, fordert Visual Studio Sie auf, einen Profilnamen anzugeben, und erfasst anschließend zusätzliche Informationen zur **Verbindung** , einschließlich Zielserver oder Speicherort, Standortnamen und Anmeldeinformationen. Sie können folgendes Verhalten auf der Registerkarte **Einstellungen** steuern:

- Die Konfiguration, die Sie bereitstellen möchten.
- Ob vorhandene Dateien aus dem Ziel entfernt werden.
- Ob während der Veröffentlichung vorkompiliert wird.
- Ob Dateien im Ordner „App_Data“ von der Bereitstellung ausgeschlossen sind.

Sie können in Visual Studio beliebig viele FTP/FTPS-Bereitstellungsprofile erstellen, wodurch Sie Profile mit unterschiedlichen Einstellungen verwalten können.

### <a name="when-to-choose-ftpftps-server-deployment"></a>Unter welchen Umständen Sie die FTP/FTPS-Serverbereitstellung auswählen sollten

- Sie verwenden Clouddienste auf einem anderen Anbieter als Azure, auf den über URLs zugegriffen werden kann.
- Sie möchten eine Bereitstellung mit anderen als den in Visual Studio verwendeten oder den direkt mit Ihren Azure-Konten verknüpften Anmeldeinformationen durchführen.
- Sie möchten bei jeder Bereitstellung Dateien vom Ziel löschen.

## <a name="web-server-iis"></a>Webserver (IIS)

Mit einem IIS-Webserver können Sie die Anwendung auf einem anderen Webserver als Azure bereitstellen. Sie können die Webanwendung auf einem IIS-Server (Internet oder Intranet) bereitstellen, auf den Sie Zugriff haben, einschließlich solchen in anderen Clouddiensten. Der Einsatz in Verbindung mit Web Deploy oder einem Web Deploy-Paket ist möglich.

Wenn Sie einen IIS-Webserver auswählen, fordert Visual Studio Sie auf, einen Profilnamen anzugeben, und erfasst anschließend zusätzliche Informationen zur **Verbindung** , einschließlich Zielserver oder Speicherort, Standortnamen und Anmeldeinformationen. Sie können folgendes Verhalten auf der Registerkarte **Einstellungen** steuern:

- Die Konfiguration, die Sie bereitstellen möchten.
- Ob vorhandene Dateien aus dem Ziel entfernt werden.
- Ob während der Veröffentlichung vorkompiliert wird.
- Ob Dateien im Ordner „App_Data“ von der Bereitstellung ausgeschlossen sind.

Sie können in Visual Studio beliebig viele IIS-Webserver-Bereitstellungsprofile erstellen, wodurch Sie Profile mit unterschiedlichen Einstellungen verwalten können.

### <a name="when-to-choose-web-server-iis-deployment"></a>Unter welchen Umständen Sie die IIS-Webserverbereitstellung wählen sollten

- Sie verwenden IIS, um eine Website oder einen Dienst zu veröffentlichen, auf die über URLs zugegriffen werden kann.
- Sie möchten eine Bereitstellung mit anderen als den in Visual Studio verwendeten oder den direkt mit Ihren Azure-Konten verknüpften Anmeldeinformationen durchführen.
- Sie möchten bei jeder Bereitstellung Dateien vom Ziel löschen.

Weitere Informationen finden Sie unter [Veröffentlichen einer Web-App auf einer Website mithilfe von Visual Studio](quickstart-deploy-to-a-web-site.md).

Weitere Informationen zur Problembehandlung von ASP.NET Core in IIS finden Sie unter [Problembehandlung bei ASP.NET Core in Azure App Service und IIS](/aspnet/core/test/troubleshoot-azure-iis).

## <a name="import-profile"></a>Profil importieren

Sie können ein Profil beim Veröffentlichen in IIS oder Azure App Service importieren. Sie können die Bereitstellung mithilfe einer *Datei mit Veröffentlichungseinstellungen* ( *\*.publishsettings* ) konfigurieren. Eine Veröffentlichungseinstellungsdatei wird von IIS oder Azure App Service erstellt. Sie können sie aber auch manuell erstellen und dann in Visual Studio importieren.

Die Verwendung einer Datei mit Veröffentlichungseinstellungen kann die Bereitstellungskonfiguration vereinfachen und hat in einer Teamumgebung Vorteile gegenüber der manuellen Konfiguration eines einzelnen Bereitstellungsprofils.

### <a name="when-to-choose-import-profile"></a>Unter welchen Umständen Sie ein Importprofil auswählen sollten

- Sie veröffentlichen in IIS und möchten die Bereitstellungskonfiguration vereinfachen.
- Sie veröffentlichen in IIS oder Azure App Service und möchten die Bereitstellungskonfiguration für die erneute Verwendung oder für Teammitglieder beschleunigen, die im selben Dienst veröffentlichen.

Weitere Informationen finden Sie unter

- [Importieren von Veröffentlichungseinstellungen und deren Bereitstellung in IIS](tutorial-import-publish-settings-iis.md)
- [Importieren von Veröffentlichungseinstellungen und deren Bereitstellung in Azure](tutorial-import-publish-settings-azure.md)

## <a name="configure-net-deployment-settings"></a>Konfigurieren von .NET-Bereitstellungseinstellungen

Weitere Hilfe zum Auswählen der Einstellungen finden Sie in den folgenden Themen:

- [Übersicht über die .NET Core-Anwendungsveröffentlichung](/dotnet/core/deploying/)
- [.NET Core-RID-Katalog](/dotnet/core/rid-catalog)
- [Grundlagen der Buildkonfiguration](../ide/understanding-build-configurations.md)

## <a name="next-steps"></a>Nächste Schritte

Tutorials:

- [Bereitstellen von .NET Core-Apps mit Visual Studio](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Veröffentlichen einer ASP.NET Core-App in Azure mit Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Bereitstellung in Visual C++](/cpp/windows/deployment-in-visual-cpp)
- [Deploy UWP apps (Bereitstellen von UWP-Apps)](/windows/uwp/packaging/packaging-uwp-apps?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publish a Node.js app to Azure using Web Deploy (Bereitstellen einer Node.js-App in Azure mithilfe von Web Deploy)](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Veröffentlichen einer Python-App in Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
