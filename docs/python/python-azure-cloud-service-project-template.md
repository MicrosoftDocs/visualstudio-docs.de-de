---
title: Projektvorlage für Azure-Clouddienste für Python
description: Visual Studio stellt in Python geschriebene Vorlagen einschließlich Rollenbereitstellung, Abhängigkeiten und Problembehandlung für Azure-Clouddienste bereit.
ms.date: 11/12/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: a40745b19bde57f7f0ca52e04a11a89ad1ca69ea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912425"
---
# <a name="azure-cloud-service-projects-for-python"></a>Projekte für Azure-Clouddienste für Python

Visual Studio enthält Vorlagen, die Ihnen bei der Verwendung von Azure Cloud Services mithilfe von Python helfen.

Ein [Clouddienst](/azure/cloud-services/) besteht aus einer beliebigen Anzahl von *Workerrollen* und *Webrollen*, von denen jede eine konzeptionell gesonderte Aufgabe ausführt und je nach Skalierungsbedarf separat über virtuelle Computer repliziert werden kann. Webrollen bieten das Hosting für Front-End-Webanwendungen. Für Python kann jedes Webframework, das WSGI unterstützt, zum Schreiben einer solchen Anwendung verwendet werden (wie von der [Webprojektvorlage](python-web-application-project-templates.md) unterstützt). Workerrollen sind für lang andauernde Prozesse vorgesehen, die nicht direkt mit den Benutzern interagieren. In der Regel verwenden sie die Pakete im Paket „azure“, das mit [`pip install azure`](https://pypi.org/project/azure) installiert wird.

Dieser Artikel enthält Details über die Projektvorlage und sonstige Unterstützung in Visual Studio 2017 und höher (frühere Versionen sind ähnlich, es gibt jedoch einige Unterschiede). Weitere Informationen zum Verwenden von Azure über Python finden Sie im [Azure Python Developer Center](/azure/python/).

## <a name="create-a-project"></a>Erstellen eines Projekts

1. Installieren Sie das [Azure .NET SDK für Visual Studio](https://visualstudio.microsoft.com/vs/azure-tools/), das für die Clouddienstvorlage erforderlich ist.
1. Wählen Sie in Visual Studio **Datei** > **Neu** > **Projekt** aus, suchen Sie nach „Azure Python“, und wählen Sie **Azure-Clouddienst** aus der Liste aus:

    ![Azure-Cloudprojektvorlage für Python](media/template-azure-cloud-project.png)

1. Wählen Sie eine oder mehrere aufzunehmende Rollen aus. In Cloudprojekten können Rollen, die in verschiedenen Sprachen geschrieben wurden, kombiniert werden, sodass Sie problemlos jeden Teil der Anwendung in der am besten geeigneten Sprache schreiben können. Um dem Projekt nach Abschluss dieses Dialogfelds neue Rollen hinzuzufügen, klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **Rollen**, und wählen Sie eines der Elemente unter **Hinzufügen** aus.

    ![Hinzufügen von Rollen in der Azure-Cloudprojektvorlage](media/template-azure-cloud-service-project-wizard.png)

1. Beim Erstellen der einzelnen Rollenprojekte werden Sie möglicherweise aufgefordert, zusätzliche Python-Pakete, z.B. die Django-, Bottle- oder Flask-Frameworks, zu installieren, wenn Sie eine Rolle ausgewählt haben, die eines davon verwendet.

1. Nachdem Sie dem Projekt eine neue Rolle hinzugefügt haben, werden Konfigurationsanweisungen angezeigt. Konfigurationsanweisungen sind in der Regel nicht erforderlich, können aber für die zukünftige Anpassung Ihrer Projekte hilfreich sein. Beachten Sie, dass nur die Anweisungen für die letzte Rolle geöffnet bleiben, wenn Sie mehrere Rollen gleichzeitig hinzufügen. Sie finden jedoch Anweisungen und Tipps zur Problembehandlung für die anderen Rollen in den jeweiligen *readme.mht*-Dateien, die sich im Stammverzeichnis der Rolle oder im Ordner *bin* befinden.

1. Der Ordner *bin* eines Projekts enthält auch ein oder zwei PowerShell-Skripts, die verwendet werden, um die virtuellen Remotecomputer zu konfigurieren. Dies umfasst die Installation von Python, [*requirements.txt*](#dependencies)-Dateien in Ihrem Projekt und bei Bedarf die Einrichtung von IIS. Sie können diese Dateien nach Bedarf für Ihre Bereitstellung bearbeiten. Allerdings können die am häufigsten verwendeten Optionen auf andere Weise verwaltet werden (siehe [Konfigurieren der Rollenbereitstellung](#configure-role-deployment) weiter unten). Es empfiehlt sich nicht, diese Dateien zu entfernen, da ein älteres Konfigurationsskript verwendet wird, wenn die Dateien nicht verfügbar sind.

    ![Unterstützungsdateien für Workerrollen](media/template-azure-cloud-service-worker-role-support-files.png)

    Um diese Konfigurationsskripts einem neuen Projekt hinzuzufügen, klicken Sie mit der rechten Maustaste auf das Projekt, wählen Sie **Hinzufügen** > **Neues Element** und dann entweder **Webrollen-Unterstützungsdateien** oder **Workerrollen-Unterstützungsdateien** aus.

## <a name="configure-role-deployment"></a>Konfigurieren der Rollenbereitstellung

Die PowerShell-Skripts im Ordner *bin* eines Rollenprojekts steuern die Bereitstellung der Rolle und können zum Anpassen der Konfiguration bearbeitet werden:

- *ConfigureCloudService.ps1* wird für Web- und Workerrollen verwendet und dient normalerweise zum Installieren und Konfigurieren von Abhängigkeiten und zum Festlegen der Python-Version.
- *LaunchWorker.ps1* wird nur für Workerrollen verwendet und dient dazu, das Startverhalten zu ändern und Befehlszeilenargumente oder Umgebungsvariablen hinzuzufügen.

Beide Dateien enthalten Anweisungen für die Anpassung. Sie können auch Ihre eigene Version von Python installieren, indem Sie eine weitere Aufgabe zur Datei *ServiceDefinition.csdef* des Clouddienst-Hauptprojekts hinzufügen und die `PYTHON`-Variable auf den Pfad der installierten Datei *python.exe* (oder einer entsprechenden Datei) festlegen. Wenn `PYTHON` festgelegt ist, wird Python nicht von NuGet installiert.

Die zusätzliche Konfiguration kann wie folgt durchgeführt werden:

1. Installieren Sie Pakete mit `pip`, indem Sie die Datei *requirements.txt* im Stammverzeichnis des Projekts aktualisieren. Das Skript *ConfigureCloudService.ps1* installiert diese Datei bei der Bereitstellung.
1. Legen Sie Umgebungsvariablen fest, indem Sie Ihre Datei Set environment variables by modifying your *web.config* (Webrollen) oder den Abschnitt `Runtime` Ihrer Datei *ServiceDefinition.csdef* (Workerrollen) ändern.
1. Geben Sie das Skript und die Argumente für eine Workerrolle an, indem Sie die Befehlszeile im Abschnitt `Runtime/EntryPoint` Ihrer Datei *ServiceDefinitions.csdef* ändern.
1. Legen Sie das Hauptskript des Handlers für eine Webrolle über die Datei *web.config* fest.

## <a name="test-role-deployment"></a>Testen der Rollenbereitstellung

Beim Schreiben der Rollen können Sie Ihr Cloudprojekt lokal mit dem Clouddienstemulator testen. Der Emulator ist in den Azure SDK-Tools enthalten. Er stellt eine eingeschränkte Version der Umgebung dar, die verwendet wird, wenn Ihr Clouddienst in Azure veröffentlicht wird.

Um den Emulator zu starten, stellen Sie zunächst sicher, dass Ihr Cloudprojekt das Startprojekt in der Projektmappe ist, indem Sie mit der rechten Maustaste klicken und **Als Startprojekt festlegen** auswählen. Wählen Sie anschließend **Debuggen** > **Debuggen starten** (**F5**) oder **Debuggen** > **Starten ohne Debuggen** (**STRG**+**F5**) aus.

Beachten Sie, dass es aufgrund von Beschränkungen im Emulator nicht möglich ist, den Python-Code zu debuggen. Wir empfehlen Ihnen daher, Ihre Rollen zu debuggen, indem Sie sie unabhängig voneinander ausführen, und dann den Emulator für Integrationstests vor der Veröffentlichung zu verwenden.

## <a name="deploy-a-role"></a>Bereitstellen einer Rolle

Wählen Sie zum Öffnen des **Veröffentlichungs-Assistenten** das Rollenprojekt im **Projektmappen-Explorer** aus, und wählen Sie im Hauptmenü **Erstellen** > **Veröffentlichen** aus, oder klicken Sie mit der rechten Maustaste, und wählen Sie **Veröffentlichen** aus.

Der Veröffentlichungsvorgang umfasst zwei Phasen. Zunächst erstellt Visual Studio ein einzelnes Paket, das alle Rollen für den Clouddenst enthält. Dieses Paket wird in Azure bereitgestellt. Dadurch werden ein oder mehrere virtuelle Computer für jede Rolle initialisiert und die Quelle bereitgestellt.

Wenn die einzelnen virtuellen Computer aktiviert werden, führen das Skript *ConfigureCloudService.ps1* aus und installieren alle Abhängigkeiten. Mit diesem Skript werden standardmäßig eine aktuelle Python-Version von [NuGet](https://www.nuget.org/packages?q=Tags%3A%22python%22+Authors%3A%22Python+Software+Foundation%22) und alle Pakete gemäß einer *requirements.txt*-Datei installiert.

Schließlich führen Workerrollen *LaunchWorker.ps1* aus. Damit wird die Ausführung des Python-Skripts gestartet. Webrollen initialisieren IIS und beginnen mit der Verarbeitung von Webanforderungen.

## <a name="dependencies"></a>Abhängigkeiten

Das Skript *ConfigureCloudService.ps1* verwendet für Cloud Services `pip`, um Python-Abhängigkeiten zu installieren. Abhängigkeiten sollten in einer Datei mit dem Namen *requirements.txt* angegeben werden (diese kann durch Anpassen von *ConfigureCloudService.ps1* erstellt werden). Die Datei wird mit `pip install -r requirements.txt` als Teil der Initialisierung ausgeführt.

Clouddienstinstanzen beinhalten keine C-Compiler. Daher müssen alle Bibliotheken mit C-Erweiterungen vorkompilierte Binärdateien bereitstellen.

pip und entsprechende Abhängigkeiten sowie die Pakete in *requirements.txt* werden automatisch heruntergeladen. Dies kann als fakturierbare Bandbreitennutzung gewertet werden. Unter [Verwalten von erforderlichen Paketen](managing-required-packages-with-requirements-txt.md) finden Sie ausführliche Informationen zum Verwalten von *requirements.txt*-Dateien.

## <a name="troubleshooting"></a>Problembehandlung

Wenn sich Ihre Web- oder Workerrolle nach der Bereitstellung nicht ordnungsgemäß verhält, überprüfen Sie Folgendes:

- Ihr Python-Projekt enthält einen Ordner *bin\\* mit (mindestens):

  - *ConfigureCloudService.ps1*
  - *LaunchWorker.ps1* (für Workerrollen)
  - *ps.cmd*

- Ihr Python-Projekt enthält eine Datei *requirements.txt* mit allen Abhängigkeiten (oder alternativ eine Sammlung von wheel-Dateien).
- Aktivieren Sie Remotedesktop für den Clouddienst, und untersuchen Sie die Protokolldateien.
- Protokolle für *ConfigureCloudService.ps1* und *LaunchWorker.ps1* befinden sich im *C:\Resources\Directory\%RoleId %. DiagnosticStore\LogFiles*-Ordner auf dem Remotecomputer.
- Webrollen können weitere Protokolle in einen Pfad schreiben, der in *web.config* konfiguriert ist, und zwar in den Pfad in der `WSGI_LOG`-appSetting. Die meisten normalen IIS- oder FastCGI-Protokolle können auch verwendet werden.
- Derzeit ist die Datei *LaunchWorker.ps1.log* die einzige Möglichkeit zum Anzeigen von Ausgaben oder Fehlern, die von der Python-Workerrolle angezeigt werden.
