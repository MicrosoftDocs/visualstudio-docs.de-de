---
title: Veröffentlichen einer Node.js-App in Linux App Service
description: Sie können in Visual Studio erstellte Node.js-Anwendungen in Linux App Service unter Azure veröffentlichen.
ms.date: 11/22/2019
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: c83516891a33a026399a6e5fcfc2458b5e03a0bd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945434"
---
# <a name="publish-a-nodejs-application-to-azure-linux-app-service"></a>Veröffentlichen einer Node.js-Anwendung in Azure (Linux App Service)

Dieses Tutorial unterstützt Sie beim Erstellen einer einfachen Node.js-Anwendung sowie beim Veröffentlichen der Anwendung in Azure.

Beim Veröffentlichen einer Node.js-Anwendung in Azure gibt es verschiedene Möglichkeiten. Hierzu gehören Azure App Service, ein virtueller Computer, auf dem ein Betriebssystem Ihrer Wahl ausgeführt wird, Azure Container Service (AKS) für die Verwaltung mit Kubernetes, eine Containerinstanz mit Docker usw. Weitere Informationen zu den einzelnen Möglichkeiten finden Sie unter [Compute](https://azure.microsoft.com/product-categories/compute/).

In diesem Tutorial wird die App in [Linux App Service](/azure/app-service/containers/app-service-linux-intro) bereitgestellt.
Linux App Service stellt einen Linux Docker-Container zum Ausführen der Node.js-Anwendung bereit (anders als der Windows App Service, der Node.js-Apps hinter IIS unter Windows ausführt).

In diesem Tutorial wird gezeigt, wie eine Node.js-Anwendung mit einer mit den Node.js-Tools für Visual Studio installierten Vorlage erstellt, der Code per Push in ein Repository auf GitHub übertragen und ein Azure App Service über das Azure-Webportal bereitgestellt wird, sodass Sie die Bereitstellung über das GitHub-Repository durchführen können. Informationen zur Verwendung der Befehlszeile für die Bereitstellung des Azure App Services sowie zum Übertragen des Codes aus einem lokalen Git-Repository finden Sie unter [Erstellen einer Node.js-App](/azure/app-service/containers/quickstart-nodejs).

In diesem Tutorial lernen Sie, wie die folgenden Aufgaben ausgeführt werden:
> [!div class="checklist"]
> * Erstellen eines Node.js-Projekts
> * Erstellen eines GitHub-Repositorys für den Code
> * Erstellen eines Linux App Service in Azure
> * Bereitstellen in Linux

## <a name="prerequisites"></a>Voraussetzungen

* Sie müssen Visual Studio und die Workload für die Node.js-Entwicklung installiert haben.

    ::: moniker range=">=vs-2019"
    Wenn Sie Visual Studio 2019 noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/) kostenlos herunterladen.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Wenn Sie Visual Studio 2017 noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/) kostenlos herunterladen.
    ::: moniker-end

    Wenn Sie die Workload installieren müssen, Visual Studio aber bereits besitzen, navigieren Sie zu **Tools** > **Tools und Features abrufen…** . Dadurch wird der Visual Studio-Installer geöffnet. Klicken Sie auf die Workload **Node.js-Entwicklung** und anschließend auf **Ändern**.

    ![Node.js-Workload im VS-Installer](../ide/media/quickstart-nodejs-workload.png)

* Die Node.js-Laufzeit muss installiert sein.

    Wenn sie nicht bereits installiert ist, installieren Sie die LTS-Version über die [Node.js](https://nodejs.org/en/download/)-Website. Im Allgemeinen erkennt Visual Studio die installierte Node.js-Runtime automatisch. Wird die installierte Laufzeit nicht erkannt, können Sie das Projekt so konfigurieren, dass es auf die installierte Laufzeit auf der Eigenschaftenseite verweist (klicken Sie hierfür nach dem Erstellen des Projekts mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Eigenschaften** aus).

## <a name="create-a-nodejs-project-to-run-in-azure"></a>Erstellen eines Node.js-Projekts zum Ausführen in Azure

1. Öffnen Sie Visual Studio.

1. Erstellen Sie eine neue TypeScript Express-App.

    ::: moniker range=">=vs-2019"
    Drücken Sie **ESC**, um das Startfenster zu schließen. Geben Sie **STRG + Q** ein, um das Suchfeld zu öffnen, geben Sie **Node.js** ein, und wählen Sie dann **Neue einfache Azure Node.js Express 4-Anwendung erstellen** (TypeScript) aus. Wählen Sie im angezeigten Dialogfeld **Erstellen** aus.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Klicken Sie oben in der Menüleiste auf **Datei** > **Neu** > **Projekt**. Erweitern Sie im linken Bereich des Dialogfelds **Neues Projekt** den Eintrag **TypeScript**, und wählen Sie dann **Node.js** aus. Wählen Sie im mittleren Bereich die Option **Azure Node.js Express 4-Basisanwendung** und anschließend **OK** aus.

    ![Erstellen einer neuen TypeScript Express-App](../javascript/media/azure-ts-express-app.png)
    ::: moniker-end
    Wenn die Projektvorlage **Azure Node.js Express 4-Basisanwendung** nicht angezeigt wird, müssen Sie die Workload **Node.js-Entwicklung** hinzufügen. Ausführliche Anweisungen dazu finden Sie in den [Voraussetzungen](#prerequisites).

    Visual Studio erstellt das Projekt und öffnet es im Projektmappen-Explorer (rechter Bereich).

1. Drücken Sie die Taste **F5**, um die App zu kompilieren und auszuführen. Stellen Sie sicher, dass alles wie erwartet ausgeführt wird.

1. Wählen Sie **Datei** > **Zur Quellcodeverwaltung hinzufügen** aus, um ein lokales Git-Repository für das Projekt zu erstellen.

    An dieser Stelle wird eine Node.js-App, für die das Express-Framework verwendet wird und die in TypeScript geschrieben ist, ausgeführt und bei der lokalen Quellcodeverwaltung angemeldet.

1. Bearbeiten Sie das Projekt wie gewünscht, bevor Sie mit den nächsten Schritten fortfahren.

## <a name="push-code-from-visual-studio-to-github"></a>Übertragen des Codes per Push von Visual Studio zu GitHub

So richten Sie GitHub für Visual Studio ein:

1. Stellen Sie über das Menüelement **Extras** > **Erweiterungen und Updates** sicher, dass die [GitHub-Erweiterung für Visual Studio](https://visualstudio.github.com/) installiert ist und aktiviert wurde.

2. Wählen Sie im Menü **Ansicht** > **Weitere Fenster** > **GitHub** aus.

    Das GitHub-Fenster wird geöffnet.

3. Wenn im GitHub-Fenster die Schaltfläche **Get Started** (Erste Schritte) nicht angezeigt wird, klicken Sie auf **Datei** > **Zur Quellcodeverwaltung hinzufügen**, und warten Sie, bis die Benutzeroberfläche aktualisiert wurde.

    ![Öffnen des GitHub-Fensters](../javascript/media/azure-github-get-started.png)

4. Klicken Sie auf **Get started** (Erste Schritte).

    Wenn Sie bereits mit GitHub verbunden sind, wird die Toolbox ähnlich wie in der folgenden Abbildung angezeigt.

    ![Einstellungen für das GitHub-Repository](../javascript/media/azure-github-publish.png)

5. Füllen Sie die Felder für das neue Repository aus, das veröffentlicht werden soll, und klicken Sie anschließend auf **Veröffentlichen**.

    Nach wenigen Augenblicken wird ein Banner mit der Meldung „Repository erfolgreich erstellt“ angezeigt.

    Im nächsten Abschnitt erfahren Sie, wie Sie dieses Repository in einem Azure App Service unter Linux veröffentlichen.

## <a name="create-a-linux-app-service-in-azure"></a>Erstellen eines Linux App Service in Azure

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

2. Wählen Sie in der Liste mit Services auf der linken Seite **App Services** aus, und klicken Sie dann auf **Hinzufügen**.

3. Erstellen Sie bei Bedarf eine neue Ressourcengruppe und einen App Service-Plan zum Hosten der neuen App.

4. Legen Sie für das **Betriebssystem** die Option **Linux** und für den **Laufzeitstapel** die erforderliche Node.js-Version wie in der Abbildung fest.

    ![Erstellen eines Linux App Service](../javascript/media/azure-create-appservice-annotated.png)

5. Klicken Sie auf **Erstellen**, um den App Service zu erstellen.

    Dieser Bereitstellungsvorgang kann einige Minuten dauern.

6. Wechseln Sie nach der Bereitstellung zum Abschnitt **Anwendungseinstellungen**, und fügen Sie eine Einstellung mit dem Namen `SCM_SCRIPT_GENERATOR_ARGS` und dem Wert `--node` hinzu.

    ![Anwendungseinstellungen](../javascript/media/azure-script-generator-args.png)

    > [!WARNING]
    > Bei der Bereitstellung des App Service wird mit Heuristiken ermittelt, welche Art von Anwendung ausprobiert und ausgeführt wird. Wenn im bereitgestellten Inhalt eine *SLN*-Datei erkannt wird, wird davon ausgegangen, dass ein auf MSBuild basierendes Projekt bereitgestellt wird. Mit der weiter oben hinzugefügten Einstellung wird diese Logik überschrieben und explizit angegeben, dass es sich hierbei um eine Node.js-Anwendung handelt. Ohne diese Einstellung kann die Node.js-Anwendung nicht bereitgestellt werden, wenn die *SLN*-Datei Teil des Repositorys ist, das im App Service bereitgestellt wird.

7. Fügen Sie unter **Anwendungseinstellungen** eine weitere Einstellung mit dem Namen `WEBSITE_NODE_DEFAULT_VERSION` und dem Wert `8.9.0` hinzu.

8. Öffnen Sie den App Service nach der Bereitstellung, und wählen Sie **Bereitstellungsoptionen** aus.

    ![Bereitstellungsoptionen](../javascript/media/azure-deployment-options.png)

9. Klicken Sie auf **Quelle auswählen**, wählen Sie **GitHub** aus, und konfigurieren Sie anschließend alle erforderlichen Berechtigungen.

    ![GitHub-Berechtigungen](../javascript/media/azure-choose-source.png)

10. Wählen Sie das Repository aus, branchen Sie zum Veröffentlichen, und wählen Sie **OK** aus.

    ![Veröffentlichen in Linux App Service](../javascript/media/azure-repo-and-branch.png)

    Beim Synchronisieren wird die Seite **Bereitstellungsoptionen** angezeigt.

    ![Bereitstellen und Synchronisieren mit GitHub](../javascript/media/azure-deployment-options-sync.png)

    Nach Abschluss der Synchronisierung wird ein Häkchen angezeigt.

    Die Node.js-Anwendung wird nun über das GitHub-Repository ausgeführt und kann über die URL aufgerufen werden, die für den Azure App Service erstellt wurde (standardmäßig der Name, der dem Azure App Service zugewiesen wird, gefolgt von „.azurewebsites.net“).

## <a name="modify-your-app-and-push-changes"></a>Anpassen der App und Übertragen der Änderungen per Push

1. Fügen Sie den hier angezeigten Code in *app.ts* nach der Zeile `app.use('/users', users);` hinzu. Dadurch wird in der URL */api* eine REST-API hinzugefügt.

    ```typescript
    app.use('/api', (req, res, next) => {
        res.json({"result": "success"});
    });
    ```

2. Kompilieren Sie den Code, und testen Sie ihn lokal. Überprüfen Sie ihn, und übertragen Sie ihn per Push an GitHub.

    Es dauert einen Moment, bis im Azure-Portal Änderungen am GitHub-Repository erkannt werden und dann eine neue Synchronisierung der Bereitstellung angestoßen wird. Das Portal entspricht in etwa der folgenden Abbildung.

    ![Ändern und Synchronisieren](../javascript/media/azure-changes-detected.png)

3. Navigieren Sie nach Abschluss der Bereitstellung zur öffentlichen Site, und fügen Sie an die URL */api* an. Daraufhin wird die JSON-Antwort zurückgegeben.

## <a name="troubleshooting"></a>Problembehandlung

* Wenn der node.exe-Prozess stockt (d.h., wenn ein Ausnahmefehler auftritt), wird der Container neu gestartet.
* Der Container durchläuft beim Starten verschiedene Heuristiken, um zu ermitteln, wie der Node.js-Prozess gestartet werden soll. Details zur Implementierung finden Sie unter [generateStartupCommand.js](https://github.com/Azure/app-service-builtin-images/blob/master/node/8.9.4/startup/generateStartupCommand.js).
* Für Untersuchungen können Sie über SSH eine Verbindung mit dem aktiven Container herstellen. Hierzu können Sie einfach das Azure-Portal verwenden. Wählen Sie den App Service aus. Blättern Sie in der Liste der Tools nach unten bis zu **SSH** im Abschnitt **Entwicklungstools**.
* Wechseln Sie zur Unterstützung bei der Problembehandlung zu den Einstellungen für **Diagnoseprotokolle** für den App Service. Ändern Sie die Einstellung **Protokollierung von Docker-Containern** von **Off** (Aus) in **Dateisystem**. Protokolle werden im Container unter */home/LogFiles/* _docker.log* erstellt. Sie können auf Ihrem Computer über SSH oder FTP(S) darauf zugreifen.
* Anstelle der standardmäßig zugewiesenen *.azurewebsites.net-URL wird der Site möglicherweise ein benutzerdefinierter Domänenname zugewiesen. Weitere Informationen finden Sie im Thema [Map Custom Domain (Zuordnen von benutzerdefinierten Domänen)](/azure/app-service/app-service-web-tutorial-custom-domain).
* Die Bereitstellung auf einer Stagingsite vor dem Wechsel in die Produktion zum Durchführen weiterer Tests hat sich bewährt. Informationen zur entsprechenden Konfiguration finden Sie im Thema [Create staging environments (Erstellen von Stagingumgebungen)](/azure/app-service/web-sites-staged-publishing).
* Häufig gestellte Fragen finden Sie unter [Häufig gestellte Fragen (FAQ) zu Azure App Service unter Linux](/azure/app-service/containers/app-service-linux-faq).

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie erfahren, wie ein Linux App Service erstellt und eine Node.js-Anwendung im Service bereitgestellt wird. Informieren Sie sich weiter über Linux App Service.

> [!div class="nextstepaction"]
> [Linux App Service](/azure/app-service/containers/app-service-linux-intro)
