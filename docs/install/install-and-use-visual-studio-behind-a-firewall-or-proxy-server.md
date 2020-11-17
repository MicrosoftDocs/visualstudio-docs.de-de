---
title: Installation und Verwendung hinter einer Firewall oder einem Proxy
description: Überprüfen Sie die Domänen-URLs, Ports und Protokolle, die Sie möglicherweise auf die Zulassungsliste setzen oder öffnen möchten, wenn Ihre Organisation eine Firewall oder einen Proxyserver verwendet.
ms.date: 06/17/2020
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs
ms.assetid: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 52eee3535590842db53cd80ac761286fb4a23fa9
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2020
ms.locfileid: "93398994"
---
# <a name="install-and-use-visual-studio-and-azure-services-behind-a-firewall-or-proxy-server"></a>Installieren und Verwenden von Visual Studio und Azure-Diensten hinter einer Firewall oder einem Proxyserver

Wenn Ihre Organisation Sicherheitsmechanismen wie eine Firewall oder einen Proxyserver verwendet, dann sollten Sie einige Domänen-URLs in die Zulassungsliste aufnehmen und verschiedene Ports und Protokolle öffnen bzw. deren Verwendung zulassen, um eine optimale Installation und Verwendung von Visual Studio und Azure-Diensten zu gewährleisten.

* **[Installieren von Visual Studio](#install-visual-studio)** : Diese Tabellen enthalten die Domänen-URLs, die Sie in die Zulassungsliste aufnehmen müssen, um Zugriff auf alle gewünschten Komponenten und Workloads zu erhalten.

* **[Verwenden von Visual Studio und Azure-Diensten](#use-visual-studio-and-azure-services)** : Diese Tabellen enthalten die Domänen-URLs, die Sie in die Zulassungsliste aufnehmen sollten, sowie die Ports und Protokolle, die Sie öffnen bzw. zulassen müssen, um Zugriff auf alle gewünschten Features und Dienste zu erhalten.

> [!NOTE]
> Dieser Artikel wurde für Visual Studio unter Windows geschrieben. Bestimmte Informationen gelten jedoch auch für die [Installation von Visual Studio für Mac](/visualstudio/mac/install-behind-a-firewall-or-proxy-server) hinter einer Firewall oder einem Proxy-Server.

## <a name="install-visual-studio"></a>Installieren von Visual Studio

### <a name="urls-to-add-to-an-allow-list"></a>URLs, die Sie in die Zulassungsliste aufnehmen sollten

Der Visual Studio-Installer lädt Dateien aus verschiedenen Domänen und den zugehörigen Downloadservern herunter, deshalb müssen Sie die folgenden URLs unter Verwendung der Benutzeroberfläche oder in Ihren Bereitstellungsskripts als vertrauenswürdige URLs in die Zulassungsliste aufnehmen.

#### <a name="microsoft-domains"></a>Microsoft-Domänen

| Domäne | Zweck |
| - | - |
| go.microsoft.com | Einrichten der URL-Lösung |
| aka.ms | Einrichten der URL-Lösung |
| download.visualstudio.microsoft.com | Einrichten des Speicherorts für den Paketdownload |
| 0download.microsoft.com | Einrichten des Speicherorts für den Paketdownload |
| download.visualstudio.com | Einrichten des Speicherorts für den Paketdownload |
| dl.xamarin.com | Einrichten des Speicherorts für den Paketdownload |
| xamarin-downloads.azureedge.net | Liste herunterladbarer Android SDK-Pakete |
| marketplace.visualstudio.com | Speicherort des Downloads der Visual Studio-Erweiterungen |
| \*.gallerycdn.vsassets.io  | Speicherort des Downloads der Visual Studio-Erweiterungen |
| visualstudio.microsoft.com | Speicherort der Dokumentation |
| docs.microsoft.com | Speicherort der Dokumentation |
| msdn.microsoft.com | Speicherort der Dokumentation |
| www\.microsoft.com | Speicherort der Dokumentation |
| \*.windows.net | Anmeldeort |
| \*.microsoftonline.com | Anmeldeort |
| \*.live.com | Anmeldeort |
| | |

#### <a name="non-microsoft-domains"></a>Nicht-Microsoft-Domänen

| Domäne | Installieren dieser Workloads |
| - | - |
| archive.apache.org | Mobile Entwicklung mit JavaScript (Cordova) |
| cocos2d-x.org | Spieleentwicklung mit C++ (Cocos) |
| download.epicgames.com | Spieleentwicklung mit C++ (Unreal Engine) |
| download.oracle.com | Mobile Entwicklung mit JavaScript (Java SDK) <br /><br />Mobile Entwicklung mit .NET (Java SDK) |
| download.unity3d.com | Spieleentwicklung mit Unity (Unity) |
| netstorage.unity3d.com | Spieleentwicklung mit Unity (Unity) |
| dl.google.com | Mobile Entwicklung mit JavaScript (Android SDK und NDK, Emulator) <br /><br />Mobile Entwicklung mit .NET (Android SDK und NDK, Emulator) |
| www\.incredibuild.com | Spieleentwicklung mit C++ (IncrediBuild) |
| incredibuildvs2017i.azureedge.net | Spieleentwicklung mit C++ (IncrediBuild) |
| www\.python.org | Python-Entwicklung (Python) <br /><br />Data Science und analytische Anwendungen (Python) |
| developerservices2.apple.com | Xamarin.iOS-Bereitstellung |
| developer.apple.com | Xamarin.iOS-Bereitstellung |
| appstoreconnect.apple.com | Xamarin.iOS-Bereitstellung |
| idmsa.apple.com | Xamarin.iOS-Bereitstellung |
| akamized.net | Content Delivery Network (Akamai Technologies) |
| | |

## <a name="use-visual-studio-and-azure-services"></a>Verwenden von Visual Studio und Azure-Diensten

### <a name="urls-to-add-to-an-allow-list-and-ports-and-protocols-to-open"></a>URLs für Zulassungsliste und zu öffnende Ports und Protokolle

Um sicherzustellen, dass Sie bei der Verwendung von Visual Studio oder Azure-Diensten hinter einer Firewall oder einem Proxyserver Zugriff auf alle gewünschten Komponenten haben, sollten Sie die folgenden URLs in die Zulassungsliste aufnehmen und die genannten Ports und Protokolle öffnen bzw. zulassen.

| Dienst oder Szenario | DNS-Endpunkt | Protokoll<br/>/Port | Beschreibung |
| - | - | -: | - | - |
| URL<br>Auflösung | go.microsoft.com<br><br>aka.ms | | Dient dem Verkürzen von URLs, die anschließend in längere URLs aufgelöst werden. |
| Startseite | vsstartpage.blob.core.windows.net | 443 | Dient der Anzeige Neuigkeiten für Entwickler auf der Startseite (nur in Visual Studio 2017). |
| Ziel-<br> benachrichtigungs- <br>Dienst | targetednotifications-tm.trafficmanager.net <br><br>www.research.net | 443<br><br>443 | Dient zum Filtern einer globalen Liste mit Benachrichtigungen in eine Liste, die nur für bestimmte Computertypen/Verwendungsszenarien gilt. |
| Erweiterung <br>auf Update überprüfen | marketplace.visualstudio.com<br><br>&#42;.windows.net <br>&#42;.microsoftonline.com <br>&#42;.live.com | 443 | Dient zum Bereitstellen von Benachrichtigungen wenn für eine installierte Erweiterung ein Update verfügbar ist. <br><br> Wird als Anmeldestandort verwendet. |
| AI-Projekt <br>Integration | az861674.vo.msecnd.net | 443<br> | Wird zum Konfigurieren neuer Projekte und zum Senden von Nutzungsdaten an Ihr registriertes Application Insights-Konto verwendet. |
| Code Lens | codelensprodscus1su0.app.<br>codelens.visualstudio.com | 443 | Wird verwendet, um im Editor Informationen anzuzeigen: letzte Aktualisierung einer Datei, Zeitachse der Änderungen, von den Änderungen betroffene Arbeitselemente, Autoren usw. |
| Experimentell <br>Featureaktivierung | visualstudio-devdiv-c2s.msedge.net | 80 | Wird zum Aktivieren experimenteller neuer Features oder Featureänderungen verwendet. |
| Identitätsbadge <br>(Benutzername und Avatar)<br>und <br>Roamingeinstellungen | app.vssps.visualstudio.com <br><br>app.vsspsext.visualstudio.com<br><br>app.vssps.visualstudio.com<br><br> ns-sb2-prod-ch1-002.cloudapp.net <br><br>az700632.vo.msecnd.net<br><br>api.vstsusers.visualstudio.com/profiles/* | 443 | Wird verwendet, um den Benutzernamen und Avatar in der IDE anzuzeigen. <br><br> Stellt sicher, dass Einstellungsänderungen von Computer zu Computer übernommen werden. |
| Remoteeinstellungen | az700632.vo.msecnd.net | 443 | Dient dem Deaktivieren von Erweiterungen, die bekanntermaßen Probleme in Visual Studio verursachen. |
| Windows-Tools | developer.microsoft.com <br><br>dev.windows.com  <br><br>appdev.microsoft.com | https/443 | Wird für Windows-App Store-Szenarien verwendet. |
| JSON-Schema <br>Suche <br><br>JSON-Schema <br>Definition<br><br>JSON-Schema <br>Unterstützung für <br>Azure-Ressourcen | json.schemastore.org <br>schemastoreorg.azurewebsites.net<br><br>json-schema.org<br><br>schema.management.azure.com | http/80<br>https/443<br><br>http/80<br><br>https/443 | Wird zum Ermitteln und Herunterladen von JSON-Schemas verwendet, die der Benutzer beim Bearbeiten von JSON-Dokumenten möglicherweise verwendet. <br><br>Dient dem Abruf des Schemas zur Metavalidierung für JSON.<br><br>Wird zum Abrufen des aktuellen Schemas für Azure Resource Manager-Bereitstellungsvorlagen verwendet. |
| NPM-Paket <br>Erkennung | Skimdb.npmjs.com <br><br>Registry.npmjs.org <br><br>Api.npms.io | https/443<br><br>http/80 &<br> https/443<br>https/443 | Wird zur Suche nach NPM-Paketen benötigt und zur clientseitigen Skriptpaketinstallation in Webprojekten verwendet. |
| Bower-Paket<br> Symbole<br><br>Bower-Paket <br>search | Bower.io <br><br>bowercache.azurewebsites.net <br>go.microsoft.com <br>Registry.bower.io | http/80<br><br>https/443<br>http/80<br>https/443 | Stellt das standardmäßige Bower-Paketsymbol bereit.  <br><br>Ermöglicht die Suche nach Bower-Paketen. |
| NuGet<br><br>NuGet-Paket<br> Erkennung | api.nuget.org <br>www.nuget.org <br>nuget.org <br>azuresearch-usnc.nuget.org <br>azuresearch-ussc.nuget.org <br>licenses.nuget.org <br>nuget.cdn.azure.cn <br>azuresearch-ea.nuget.org <br>azuresearch-sea.nuget.org <br><br>crl3.digicert.com <br>crl4.digicert.com <br>ocsp.digicert.com <br>cacerts.digicert.com | https/443<br><br>http/80 &<br>https/443<br> | Dient der Überprüfung von signierten NuGet-Paketen.<br><br>Erforderlich für die Suche nach NuGet-Paketen und -Versionen. |
| GitHub-Repositoryinformationen | api.github.com | https/443 | Erforderlich zum Abrufen zusätzlicher Informationen zu Bower-Paketen. |
| Weblinter | Eslint.org<br><br>www.Bing.com <br><br>www.coffeelint.org | http/80 | |
| Cookiecutter<br>Explorer-Vorlage<br>Erkennung <br><br>Cookiecutter <br>Explorer-Projekt<br> Erstellung | api.github.com <br>raw.githubusercontent.com <br>go.microsoft.com<br><br>pypi.org <br> pypi.python.org | https/443<br> | Wird zum Ermitteln von Onlinevorlagen im empfohlenen Feed sowie in GitHub-Repositorys verwendet. <br><br>Dient zum Erstellen eines Projekts aus einer Cookiecutter-Vorlage, die eine einmalige Installation eines Cookiecutter-Python-Pakets aus dem Python-Paketindex (PyPI) erfordert. |
| Python-Paket <br>Erkennung<br><br>Python-Paket <br>Verwaltung<br><br>Neu <br>Python <br> Projekt <br>Vorlagen | pypi.org<br> <br>pypi.python.org <br>bootstrap.pypa.io<br><br>go.microsoft.com | https/443 | Ermöglicht die Suche nach PIP-Paketen.<br><br>Installiert PIP automatisch, sofern nicht vorhanden. <br><br>Wird zum Auflösen der folgenden neuen Python-Projektvorlagen für Cookiecutter-Vorlagen-URLs verwendet:<br> – Klassifiziererprojekt<br>– Clusteringprojekt <br> – Regressionsprojekt <br> – PyGame unter Verwendung von PyKinect <br> – Pyvot-Projekt |
| Office Web <br>Add-In <br> Manifest <br>Überprüfung <br>Dienst | verificationservice.osi.office.net | https/443 | Wird zum Validieren von Manifesten für Office Web-Add-Ins verwendet. |
| SharePoint- und <br>Office-Add-ins | sharepoint.com<br> microsoft.com/microsoft-365<br> microsoftonline.com <br> outlook.com | https/443 | Wird zum Veröffentlichen und Testen von SharePoint- und Office-Add-Ins in SharePoint Online und Microsoft 365 verwendet |
| Workflow-Manager- <br>Testdienst-<br> Host | | http/12292 | Eine Firewall, die zum Testen von SharePoint-Add-Ins mit Workflows automatisch erstellt wird. |
| Automatisch gesammelte <br>Zuverlässigkeitsstatistiken <br>und weitere Daten des <br>Programms zur Verbesserung <br>der Benutzerfreundlichkeit<br> für Azure SDK und <br>SQL-Tools <br><br> | vortex.data.microsoft.com<br> <br>dc.services.visualstudio.com | https/443 | Wird zum Senden von Zuverlässigkeitsstatistiken (Daten zu Abstürzen/Nichtreaktionen) vom Benutzer an Microsoft verwendet. Die eigentlichen Speicherabbilder zu Abstürzen/Nichtreaktionen werden weiterhin hochgeladen, wenn die Windows-Fehlerberichterstattung aktiviert ist. Es werden lediglich statistische Informationen unterdrückt. <br>Wird verwendet, um anonyme Nutzungsmuster der Azure-Tools SDK-Erweiterung sowie Nutzungsmuster der SQL-Tools für Visual Studio offenzulegen. |
| Visual Studio <br> Programm zur Verbesserung <br>der Benutzerfreundlichkeit (CEIP) <br><br>PerfWatson.exe | vortex.data.microsoft.com<br>dc.services.visualstudio.com<br>visualstudio-devdiv-c2s.msedge.net<br>az667904.vo.msecnd.net <br>scus-breeziest-in.cloudapp.net<br> | https/443 | Dient zum Sammeln von anonymen Nutzungsmustern und Fehlerprotokollen. <br><br>Hiermit werden Probleme mit einer nicht reagierenden Benutzeroberfläche nachverfolgt. |
| Erstellung und<br>Verwaltung von <br>Azure-Ressourcen | management.azure.com <br>management.core.windows.net | https/443 | Wird verwendet, um Azure-Websites oder andere Ressourcen zur Unterstützung der Veröffentlichung von Webanwendungen, Azure-Funktionen oder WebJobs zu unterstützen. |
| Überprüfung auf aktualisierte Tools <br>und Erweiterungsempfehlungen <br>für die Webveröffentlichung | marketplace.visualstudio.com | https/443 | Wird verwendet, um nach aktualisierten Veröffentlichungstools zu suchen. Sofern deaktiviert, wird eine potenziell empfohlene Erweiterung für die Webveröffentlichung möglicherweise nicht angezeigt. |
| Aktualisierte Informationen zu Endpunkten <br>für die Erstellung von Azure-Ressourcen | \*.blob.core.windows.net | https/443 | Hiermit werden die Endpunkte für die Erstellung von Azure-Ressourcen für bestimmte Azure-Dienste aktualisiert. Sofern deaktiviert, werden stattdessen die zuletzt heruntergeladenen oder integrierten Endpunktstandorte verwendet. |
| Remotedebuggen und <br>Remoteprofilerstellung für <br>Azure Websites | &#42;.cloudapp.net <br> &#42;.azurewebsites.net | 4022 | Hiermit wird der Remotedebugger an Azure Websites angefügt. Sofern deaktiviert, funktioniert das Anfügen des Remotedebuggers an Azure Websites nicht. |
| Active Directory <br>Graph | graph.windows.net | https/443 | Wird verwendet, um neue Azure Active Directory-Anwendungen bereitzustellen. Wird auch vom verbundenen Microsoft 365 MSGraph-Dienstanbieter verwendet. |
| Überprüfung auf <br>CLI-Update für <br>Azure Functions | functionscdn.azureedge.net | https/443 | Wird verwendet, um nach aktualisierten Versionen der Azure Functions-CLI zu suchen. Sofern deaktiviert, wird stattdessen eine zwischengespeicherte Kopie (oder die Kopie der Azure Functions-Komponente) der CLI verwendet. |
| Cordova | npmjs.org<br>gradle.org | http/80 &<br/>https/443 | HTTP wird für Gradle-Downloads während der Builderstellung verwendet; HTTP wird zum Einschließen von Cordova-Plug-Ins in Projekten genutzt. |
| Cloud-Explorer | 1. &#60;Clusterendpunkt&#62; <br>Service Fabric <br>2. &#60;Verwaltungsendpunkt&#62;<br>Allgemeine Cloudoberfläche <br>3. &#60;Graph-Endpunkt&#62;<br>Allgemeine Cloudoberfläche<br>4. &#60;Speicherkontoendpunkt&#62;<br>Speicherknoten <br>5. &#60;Azure-Portal-URLs&#62;<br>Allgemeine Cloudoberfläche <br>6. &#60;Key Vault-Endpunkte&#62; <br>Azure Resource Manager-VM-Knoten<br>7. &#60;PublicIPAddressOfCluster&#62;<br>Service Fabric-Remotedebuggen und ETW-Ablaufverfolgungen | <br>1.https/19080<br>2. https/443<br>3. https/443<br>4. https/443<br>5. https/443<br>6. https/443<br>7.tcp/dynamic | 1. Beispiel: test12.eastus.cloudapp.com<br>2. Ruft Abonnements ab und ruft Azure-Ressourcen ab bzw. verwaltet sie.<br>3. Ruft Azure Stack-Abonnements ab.<br>4. Verwaltet Speicherressourcen (Beispiel: mystorageaccount.blob.core.windows.net).<br>5. Kontextmenüoption „In Portal öffnen“ (öffnet eine Ressource im Azure-Portal).<br>6. Erstellt und verwaltet Schlüsselspeicher für das VM-Debugging (Beispiel: myvault.vault.azure.net). <br><br>7. Hiermit wird ein Portblock basierend auf der Anzahl von Knoten im Cluster sowie den verfügbaren Ports dynamisch zugewiesen. <br><br>Ein Portblock versucht, die dreifache Anzahl von Knoten mit mindestens zehn Ports abzurufen.<br><br>Für Streamingablaufverfolgungen wird versucht, den Portblock ab 810 zu erhalten. Wenn einer dieser Ports bereits verwendet wird, wird versucht, den nächsten Block abzurufen usw. (Wenn der Load Balancer leer ist, werden die Ports ab 810 sehr wahrscheinlich verwendet.) <br><br>Ähnlich werden für das Debugging vier Sätze an Portblocks reserviert: <br>– connectorPort: 30398, <br>– forwarderPort: 31398, <br>– forwarderPortx86: 31399,<br>– fileUploadPort: 32398<br> |
| Cloud Services | 1. RDP<br><br>2. core.windows.net <br><br>3.  management.azure.com<br> management.core.windows.net <br><br>4. &#42;.blob.core.windows.net <br>&#42;.queue.core.windows.net<br>&#42;.table.core.windows.net <br><br>5. portal.azure.com <br><br>6. &#60;Benutzerclouddienst&#62;.cloudapp.net <br> &#60;Benutzer-VM&#62;.&#60;Region&#62;.azure.com | 1. rdp/3389 <br><br> 2. https/443 <br><br> 3. https/443 <br><br> 4. https/443 <br><br> 5. https/443 <br><br>6. TCP <br>a) 30398 <br>b) 30400 <br>c) 31398 <br>d) 31400 <br>e) 32398 <br>f) 32400 | 1.  Remotedesktop zu Cloud Services-VM <br><br> 2.  Speicherkontokomponente der privaten Diagnosekonfiguration <br><br> 3.  Azure-Portal <br><br> 4. Server-Explorer – Azure Storage &#42; entspricht dem vom Kunden benannten Speicherkonto  <br><br> 5.  Links zum Öffnen des Portals &#47; Download des Abonnementzertifikats &#47; Veröffentlichen der Einstellungsdatei <br><br>6. a) Lokaler Connectorport für das Remotedebuggen von Clouddienst und VM<br> 6. b) Öffentlicher Connectorport für das Remotedebuggen von Clouddienst und VM <br> 6. c) Lokaler Weiterleitungsport für das Remotedebuggen von Clouddienst und VM <br> 6. d) Öffentlicher Weiterleitungsport für das Remotedebuggen von Clouddienst und VM  <br> 6. e) Lokaler Port des Programms zum Hochladen von Dateien für das Remotedebuggen von Clouddienst und VM <br> 6. f) Öffentlicher Port des Programms zum Hochladen von Dateien für das Remotedebuggen von Clouddienst und VM |
| Service Fabric | 1. <br>docs.Microsoft.com<br>aka.ms <br>go.microsoft.com <br><br>2. <br>vssftools.blob.core.windows.net <br>Vault.azure.com <br>Portal.azure.com <br><br> 3. &#42; vault.azure.net<br><br> 4. <br>app.vsaex.visualstudio.com<br>&#42; .vsspsext.visualstudio.com<br>clouds.vsrm.visualstudio.com <br>clouds.visualstudio.com<br>app.vssps.visualstudio.com <br>&#42; .visualstudio.com | https/443 | 1. Dokumentation <br><br> 2. Feature zur Clustererstellung <br><br>3. &#42; ist der Azure Key Vault-Name (Beispiel: test11220180112110108.vault.azure.net)  <br><br>  4. &#42; ist dynamisch (Beispiel: vsspsextprodch1su1.vsspsext.visualstudio.com) |
| Snapshot <br>Debugger | 1. go.microsoft.com <br>2. management.azure.com <br> 3. &#42;.azurewebsites.net <br> 4. &#42;.scm.azurewebsites.net<br>5. api.nuget.org/v3/index.json <br>6. Remotedienst/Server-IP-Adresse/FQDN | 1. https/443 <br>2. https/443  <br>3. http/80 <br>4. https/443 <br>5. https/443 <br>6. Concord/<br> 4022 (abhängig von der Visual Studio-Version) | 1. Abfrage-JSON-Datei für App Service-SKU-Größe <br>2. Verschiedene Azure-RM-Aufrufe <br>3. Aufruf zur Standortaufwärmung über  <br>4. Vom Kunden festgelegter App Service-Kudu-Endpunkt <br>5. Auf nuget.org veröffentlichte Erweiterungsversion für die Abfragewebsite <br>6. [Remotedebuggen](../debugger/remote-debugging.md) |
| Azure Stream Analytics <br><br>HDInsight | Management.azure.com | https/443 | Dient zum Anzeigen, Übermitteln, Ausführen und Verwalten von ASA-Aufträgen. <br><br> Wird verwendet, um HDI-Cluster zu durchsuchen und HDI-Aufträge zu übermitteln, zu diagnostizieren und zu debuggen. |
| Azure Data Lake | &#42;.azuredatalakestore.net <br>&#42;.azuredatalakeanalytics.net | https/443 | Wird verwendet, um Auftrage zu kompilieren, zu übermitteln, anzuzeigen, zu diagnostizieren und zu debuggen. Dient zum Durchsuchen von ADLS-Dateien und zum Hoch- und Herunterladen von Dateien. |
| Paketerstellungsdienst | [account].visualstudio.com <br/> [Konto].\*.visualstudio.com <br/> \*.blob.core.windows.net <br/> registry.npmjs.org </br> nodejs.org <br/> dist.nuget.org <br/> nuget.org | https/443 | Die Domänen \*.npmjs.org, \*.nuget.org und \*.nodejs.org sind nur für bestimmte Buildtaskszenarios erforderlich (z. B.: NuGet-Toolinstaller, Node Tool-Installationsprogramm) oder wenn Sie öffentliche Upstreams mit Ihren Feeds verwenden müssen. Die anderen drei Domänen werden für wichtige Funktionen des Paketerstellungsdiensts benötigt. |
| Azure DevOps Services | \*.vsassets.io <br/> static2.sharepointonline.com <br/> dev.azure.com | | Wird zum Herstellen einer Verbindung mit Azure DevOps Services verwendet. |
| Azure-Servicebus | \*.servicebus.windows.net | ampq/5671 und 5672, </br> sbmp/9350-9354, </br> http/80, </br> https/443 | Dient zum Erstellen von Warteschlangen, Themen und Abonnements. </br> Dient auch zum Senden/Empfangen von Nachrichten an/von Service Bus-Warteschlangen und -Themen. |
| Azure Cosmos DB | \*.documents.azure.com | https/443 | Dient zum Aufruf der APIs der zentralen Dokumentdatenbank. |
| Entwicklercommunity | sendvsfeedback2.azurewebsites.net/api | https/443 | Wird zum Aufrufen von Developer Community Feedback Tool-APIs verwendet (Meine Probleme, Suchen, Abstimmungen, Kommentare, gegebenes Feedback, Uploads, Lebenslauf) |
| Intellicode | \*.intellicode.vsengsaas.visualstudio.com | https/443 | Wird zum Aufrufen von Intellicode-APIs verwendet |
| Live Share | \*.liveshare.vsengsaas.visualstudio.com| https/443 | Wird zum Aufrufen von Live Share-APIs verwendet |
| GitHub Codespaces | \*.online.visualstudio.com | https/443 | Wird zum Aufrufen von GitHub-Codespaces-APIs verwendet |
| Automatische Typerfassung für JavaScript | registry.npmjs.org | https/443 | Wird zum Installieren von TypeScript-Typdefinitionen verwendet, um IntelliSense für häufig verwendete JavaScript-Bibliotheken zur Verfügung zu stellen |
| Lizenzierungsdienst für Visual Studio-Abonnements | app.vssps.visualstudio.com/apis/<br/>Licensing/ClientRights | https/443 | Lizenzierung für Online-Aktivierung |
| Debugger | 1. <br>vsdebugger.blob.core.windows.net <br>vsdebugger.azureedge.net <br><br>2. <br>download.visualstudio.com/\*/<br/>onecore.msvsmon.\*.zip<br><br> 3. referencesource.microsoft.com/symbols <br><br> 4. <br>symbols.nuget.org/download/symbols<br><br> 5. visualstudio.com<br><br>6. msdl.microsoft.com/download/symbols | https/443 | 1. <br>Wird zum Herunterladen von Debuggerbits für das .NET Core-Debuggen unter Unix oder macOS über SSH verwendet <br><br>2. <br>Wird zum Herunterladen von Debuggerbits für das Debuggen von Docker für Windows-Remotecontainer verwendet<br><br> 3. Wird für das Durchlaufen des .NET Framework-Quellcodes verwendet <br><br> 4. <br>(Bei Benutzeranmeldung) Wird für das Herunterladen von Symbolen verwendet, die für NuGet.org-Symbolserver veröffentlicht wurden<br><br> 5. (Bei Benutzeranmeldung) Wird für das Herunterladen von Microsoft-Symbolen und Binärdateien verwendet, und möglicherweise für das Debuggen von verwaltetem Code in Speicherabbildern |
| GitHub Codespaces| \*.online.visualstudio.com | https/443 | Wird zum Aufrufen von GitHub-Codespaces-APIs verwendet |
| Veröffentlichen von Xamarin Android-Apps | \*.googleapis.com <br/> play.google.com <br/>accounts.google.com | https/443 | Wird für die Interaktion mit dem Google Play Store-Dienst zum Veröffentlichen/Hochladen von Xamarin Android-Anwendungen direkt in Visual Studio verwendet |
| Azure Container Registry | *.azurecr.io | https/443 | Zugriff für auf Azure gehostete Containerregistrierungen für die Konfiguration von CI/CD-Pipelines |
| | | | |

## <a name="troubleshoot-network-related-errors"></a>Behandlung netzwerkbezogener Fehler

Gelegentlich kann es zu netzwerk- oder proxybezogenen Fehlern kommen, wenn Sie Visual Studio hinter einer Firewall oder einem Proxyserver installieren oder verwenden. Weitere Informationen zu Lösungen für diese Fehlermeldungen finden Sie unter [Beheben von Netzwerkfehlern beim Installieren oder Verwenden von Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md).

## <a name="get-support"></a>Support aufrufen

Für installationsbezogene Probleme wird eine [**Livechat**](https://visualstudio.microsoft.com/vs/support/#talktous)-Supportoption angeboten (nur auf Englisch).

Hier sind einige weitere Supportoptionen:

* Sie können uns über Produktprobleme mit dem Tool [Problem melden](../ide/how-to-report-a-problem-with-visual-studio.md) informieren, das sowohl im Visual Studio-Installer als auch in der Visual Studio-IDE angezeigt wird.
* Schlagen Sie ein Feature vor, verfolgen Sie Produktprobleme nach, und finden Sie Antworten in der [Visual Studio-Entwicklercommunity](https://developercommunity.visualstudio.com/).
* Sie können Ihr [GitHub](https://github.com/)-Konto verwenden, um über die [Visual Studio-Unterhaltung in der Gitter-Community](https://gitter.im/Microsoft/VisualStudio) Kontakt zu uns oder zu anderen Visual Studio-Entwicklern aufzunehmen.

## <a name="see-also"></a>Siehe auch

* [Anforderungen an die Konnektivität für Live Share](/visualstudio/liveshare/reference/connectivity/)
* [Erstellen einer Netzwerkinstallation von Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Beheben von Netzwerkfehlern in Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md)
* [Administratorhandbuch für Visual Studio 2017 RC](visual-studio-administrator-guide.md)
* [Installieren hinter einer Firewall oder einem Proxy-Server (Visual Studio für Mac)](/visualstudio/mac/install-behind-a-firewall-or-proxy-server)
