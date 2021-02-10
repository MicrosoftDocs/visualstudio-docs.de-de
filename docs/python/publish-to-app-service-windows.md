---
title: Veröffentlichen einer Python-App auf Azure App Service unter Windows
description: Direktes Veröffentlichen einer Python-Web-Anwendung aus Visual Studio in Azure App Service unter Windows, einschließlich der erforderlichen Inhalte für die Datei „web.config“.
ms.date: 01/07/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: af3e7c2d74a9d7b3a95ae24bba37981822247728
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912562"
---
# <a name="publishing-to-azure-app-service-on-windows"></a>Veröffentlichen in Azure App Service unter Windows

> [!Note]
> Dieser Inhalt und die beschriebenen Features sind veraltet, aber weiterhin funktionsfähig. Python-Entwicklern wird empfohlen, nach Möglichkeit die Migration zu [App Service unter Linux](publishing-python-web-applications-to-azure-from-visual-studio.md) auszuführen.

Visual Studio bietet Ihnen die Möglichkeit, Python-Web-Apps direkt in Azure App Service unter Windows zu veröffentlichen. Wenn Sie eine App in Azure App Service unter Windows veröffentlichen möchten, müssen Sie die benötigten Dateien auf den Server kopieren und eine Datei `web.config` einrichten, die Anweisungen für den Webserver zum Starten der App enthält.

Es gibt Unterschiede bei der Veröffentlichung über Visual Studio 2017 und höher und Visual Studio 2015. Insbesondere werden bei Visual Studio 2015 einige der notwendigen Schritte automatisiert, u.a. das Erstellen der `web.config`-Datei. Allerdings schränkt diese Automatisierung auf Dauer die Flexibilität und Kontrolle ein. Für Visual Studio 2017 und höher sind hingegen zwar mehr manuelle Schritte erforderlich, jedoch können Sie dadurch die Python-Umgebung auch genauer kontrollieren. Beide Optionen werden in diesem Artikel beschrieben.

> [!Note]
> Hintergrundinformationen zu den Unterschieden zwischen Visual Studio 2015 und Visual Studio 2017 und höher finden Sie im Blogeintrag [Publish to Azure in Visual Studio 2017 (Veröffentlichen auf Azure in Visual Studio 2017)](https://devblogs.microsoft.com/python/publish-to-azure-in-vs-2017/).

## <a name="prerequisites"></a>Voraussetzungen

Für diese exemplarische Vorgehensweise benötigen Sie ein auf den Bottle-, Flask- oder Django-Frameworks basierendes Web-App-Projekt. Wenn Sie kein Projekt erstellt haben, aber gerne den Veröffentlichungsprozess ausprobieren möchten, können Sie wie folgt ein einfaches Testprojekt erstellen:

1. Wählen Sie in Visual Studio **Datei > Neu > Projekt** aus, suchen Sie nach „Bottle“, wählen Sie **Bottle-Webprojekt** aus, geben Sie einen Pfad und einen Namen für das Projekt an, und wählen Sie **OK** aus. (Die Bottle-Vorlage ist Bestandteil der Python-Entwicklungsworkload. Informationen dazu finden Sie unter [Installation](installing-python-support-in-visual-studio.md).)

1. Befolgen Sie die Eingabeaufforderungen für die Installation von externen Paketen, indem Sie auf **In einer virtuellen Umgebung installieren** klicken und den von Ihnen bevorzugten Basisinterpreter für die virtuelle Umgebung auswählen. Diese Auswahl entspricht in der Regel der in App Service installierten Python-Version.

1. Testen Sie das Projekt lokal, indem Sie F5 drücken, oder auf **Debuggen > Debuggen starten** klicken.

## <a name="create-an-azure-app-service"></a>Erstellen von Azure App Service

Sie benötigen App Service als Ziel, wenn Sie eine Anwendung auf Azure veröffentlichen möchten. Dafür können Sie App Service über ein Azure-Abonnement erstellen, oder Sie verwenden eine temporäre Website.

Wenn Sie noch kein Abonnement abgeschlossen haben, beginnen Sie mit einem [kostenlosen vollwertigen Azure-Konto](https://azure.microsoft.com/free/), das mit einer großzügigen Gutschrift für Azure-Dienste verbunden ist. Erwägen Sie auch die Anmeldung für die Mitgliedschaft bei [Visual Studio Developer Essentials](https://azure.microsoft.com/pricing/member-offers/vs-dev-essentials/), wo Sie ein ganzes Jahr lang jeden Monat ein Guthaben von 25 $ erhalten.

> [!Tip]
> Obwohl Azure Sie auffordert, Kreditkarteninformationen einzugeben, um Ihr Konto zu prüfen, wird Ihre Kreditkarte nicht belastet. Sie können aber gerne auch ein [Ausgabenlimit](/azure/billing/billing-spending-limit) festlegen, dass dem Wert Ihrer Gutschrift entspricht, um sicherzustellen, das keine zusätzlichen Kosten anfallen. Außerdem stellt Azure einen kostenlosen Tarif für App Service-Plan zur Verfügung, der sich ideal für einfache Test-Apps eignet. Dies wird im folgenden Abschnitt beschrieben.

### <a name="using-a-subscription"></a>Verwenden eines Abonnements

Erstellen Sie, wie im Folgenden beschrieben, über ein aktives Azure-Abonnement App Service mit einer leeren Web-App:

1. Melden Sie sich unter [portal.azure.com](https://portal.azure.com) an.
1. Klicken Sie auf **+Neu** > **Web + Mobil** > **Web-App**.
1. Geben Sie einen Namen für die Web-App an, behalten Sie für **Ressourcengruppe** die Einstellung „Neu Erstellen“ bei, und wählen Sie **Windows** als Betriebssystem aus.
1. Klicken Sie auf **App Service-Plan/Standort** > **Neu erstellen**, und geben Sie einen Namen und einen Speicherort an. Klicken Sie dann auf **Tarif**, scrollen Sie nach unten, klicken Sie auf den Plan **F1 Free** (F1 gratis), und klicken Sie auf **Select** (Auswählen) > **OK** > **Erstellen**.
1. (Optional) Sobald App Service erstellt wurde, navigieren Sie zu dem entsprechenden Speicherort, klicken Sie auf **Veröffentlichungsprofil abrufen**, und speichern Sie die Datei lokal.

### <a name="using-a-temporary-app-service"></a>Verwenden eines temporären App Service

Führen Sie die folgenden Schritte aus, um einen temporären App Service zu erstellen, ohne dass ein Azure-Abonnement erforderlich ist:

1. Öffnen Sie Ihren Browser mit [https://azure.microsoft.com/try/app-service/web/](https://azure.microsoft.com/try/app-service/web/).
1. Wählen Sie **Web-App** als App-Typ und dann **Weiter**.
1. Klicken Sie auf **Empty Site** (Leere Website) > **Erstellen**.
1. Melden Sie sich mit den Anmeldedaten eines sozialen Netzwerks Ihrer Wahl an, und nach kurzer Zeit ist Ihre Website unter der angezeigten URL bereit.
1. Wählen Sie **Veröffentlichungsprofil herunterladen**, und speichern Sie die `.publishsettings`-Datei, die Sie später verwenden.

## <a name="configure-python-on-azure-app-service"></a>Konfigurieren von Python auf Azure App Service

Sobald Sie App Service erstellt haben und eine leere Web-App ausgeführt wird (entweder in Ihrem Abonnement oder auf einer kostenlosen Website), installieren Sie eine ausgewählte Python-Version wie unter [Verwalten von Python auf Azure App Service](managing-python-on-azure-app-service.md) beschrieben. Zeichnen Sie, wie in diesem Artikel beschrieben, den genauen Pfad zum installierten Python-Interpreter mit der Websiteerweiterung auf, um eine App über Visual Studio 2017 und höher zu veröffentlichen.

Fall gewünscht, können Sie auch das `bottle`-Paket installieren, indem Sie die hier beschriebenen Anweisungen befolgen, da das Paket als Teil anderer Schritte in dieser exemplarischen Vorgehensweise installiert wird.

## <a name="publish-to-app-service---visual-studio-2017-and-later"></a>Veröffentlichen in App Service: Visual Studio 2017 und höher

Wenn Sie eine App in Azure App Service über Visual Studio 2017 und höher veröffentlichen, werden nur die Dateien in Ihrem Projekt auf den Server kopiert. Aus diesem Grund ist es notwendig, die benötigten Dateien zu erstellen, um die Serverumgebung zu konfigurieren.

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt und auf **Hinzufügen > Neues Element…** . Klicken Sie in dem angezeigten Dialogfeld auf die Vorlage „Azure web.config (Fast CGI)“ und dann auf „OK“. Dadurch erstellen Sie eine `web.config`-Datei in Ihrem Projektstamm.

1. Bearbeiten Sie den `PythonHandler`-Eintrag in `web.config` so, dass der Pfad mit der Python-Installation auf dem Server übereinstimmt (genaue Details finden Sie in der [Referenz zur IIS-Konfiguration](https://www.iis.net/configreference) (iis.net)). Für Python 3.6.1 x64 sollte der Eintrag wie folgt aussehen:

    ```xml
    <system.webServer>
      <handlers>
        <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
            scriptProcessor="D:\home\Python361x64\python.exe|D:\home\Python361x64\wfastcgi.py"
            resourceType="Unspecified" requireAccess="Script"/>
      </handlers>
    </system.webServer>
    ```

1. Legen Sie den `WSGI_HANDLER`-Eintrag auf die `web.config`-Datei fest, die für das von Ihnen verwendete Framework angemessen ist:

    - **Bottle:** Fügen Sie, wie im untenstehenden Beispiel dargestellt, nach `app.wsgi_app` Klammern ein. Dies ist notwendig, da das Objekt eine Funktion (siehe `app.py`) und keine Variable ist:

        ```xml
        <!-- Bottle apps only -->
        <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
        ```

    - **Flask:** Ändern Sie den Wert `WSGI_HANDLER` in `<project_name>.app`, wobei das `<project_name>`-Element dem Namen Ihres Projekts entspricht. Den genauen Identifizierer können Sie ermitteln, indem Sie sich die Anweisung `from <project_name> import app` im `runserver.py`-Objekt ansehen. Wenn das Projekt z.B. den Namen „FlaskAzurePublishExample“ hat, sieht der Eintrag wie folgt aus:

        ```xml
        <!-- Flask apps only: change the project name to match your app -->
        <add key="WSGI_HANDLER" value="FlaskAzurePublishExample.app"/>
        ```

    - **Django:** Für Django-Projekte müssen Sie zwei Änderungen an der `web.config`-Datei vornehmen. Ändern Sie zunächst den `WSGI_HANDLER`-Wert auf `django.core.wsgi.get_wsgi_application()` (das Objekt befindet sich in der `wsgi.py`-Datei):

        ```xml
        <!-- Django apps only -->
        <add key="WSGI_HANDLER" value="django.core.wsgi.get_wsgi_application()"/>
        ```

        Fügen Sie dann den folgenden Eintrag unter dem für `WSGI_HANDLER` hinzu, wobei Sie `DjangoAzurePublishExample` durch den Namen Ihres Projekts ersetzen:

        ```xml
        <add key="DJANGO_SETTINGS_MODULE" value="DjangoAzurePublishExample.settings" />
        ```

1. **Nur für Django-Apps:** Fügen Sie in der `settings.py`-Datei des Django-Projekts wie unten dargestellt die Domäne Ihrer Website-URL zu `ALLOWED_HOSTS` hinzu. Dabei ersetzen Sie „vspython-test-02.azurewebsites.net“ durch Ihre URL:

    ```python
    # Change the URL to your specific site
    ALLOWED_HOSTS = ['vspython-test-02.azurewebsites.net']
    ```

    Fehler beim Hinzufügen Ihrer URL zu den Arrayergebnissen im „Fehler DisallowedHost at/Invalid HTTP_HOST header: \<site URL\>. Sie müssen ALLOWED_HOSTS möglicherweise \<site URL\> hinzufügen.“

    Beachten Sie, dass wenn das Array leer ist, Django automatisch 'localhost' zulässt. Wenn Sie jedoch Ihre Produktions-URL hinzufügen, werden diese Funktionen entfernt. Aus diesem Grund sollten Sie separate Entwicklungs- und Produktionskopien von `settings.py` beibehalten, oder alternativ die Umgebungsvariablen verwenden, um die Laufzeitwerte zu kontrollieren.

1. Erweitern Sie im **Projektmappen-Explorer** den Ordner, der denselben Namen wie Ihr Projekt hat, klicken Sie mit der rechten Maustaste auf den `static`-Ordner und dann auf **Hinzufügen > Neues Element...** , wählen Sie die Vorlage „web.config“ für statische Azure-Dateien“ aus, und klicken Sie auf **OK**. So erstellen Sie eine weitere `web.config`-Datei im `static`-Ordner, die die Python-Verarbeitung für diesen Ordner deaktiviert. Diese Konfiguration sendet Anforderungen für statische Dateien an den Standardwebserver und verwendet nicht die Python-Anwendung.

1. Speichern Sie Ihr Projekt, klicken Sie dann im **Projektmappen-Explorer** mit der rechten Maustaste darauf, und klicken Sie auf **Veröffentlichen**.

    ![Befehl „Veröffentlichen“ im Kontextmenü eines Projekts](media/template-web-publish-command.png)

1. Wählen Sie in der angezeigten Registerkarte **Veröffentlichen** das Ziel für die Veröffentlichung aus:

    a. Ihr eigenes Azure-Abonnement: Klicken Sie auf **Microsoft Azure App Service** und dann auf **Vorhandenen auswählen** > **Veröffentlichen**. Ein Dialogfeld wird angezeigt, in dem Sie das passende Abonnement und den passenden App-Dienst auswählen. Wenn App Service nicht angezeigt wird, verwenden Sie, wie unten beschrieben, das heruntergeladene Veröffentlichungsprofil für einen temporären App-Dienst.

    ![Veröffentlichen in Azure, Schritt 1, Visual Studio 2017 und höher: vorhandene Abonnements](media/tutorials-common-publish-1a-2017.png)

    b. Wenn Sie auf „try.azurewebsites.net“ ein temporäres App Service verwenden oder stattdessen ein anderes Veröffentlichungsprofil verwenden müssen, klicken Sie auf das Steuerelement **>** , um nach **Profil importieren** zu suchen. Wählen Sie diese Option aus, und klicken Sie dann auf **Veröffentlichen**. Dann wird die Eingabe des Speicherorts der zuvor heruntergeladenen `.publishsettings`-Datei verlangt.

    ![Veröffentlichen in Azure, Schritt 1, Visual Studio 2017 und höher: vorübergehender App-Dienst](media/tutorials-common-publish-1b-2017.png)

1. Visual Studio zeigt einen Veröffentlichungsstatus im Fenster „Webveröffentlichungsaktivität“ und das Veröffentlichungsfenster an. Sobald der Veröffentlichungsprozess abgeschlossen ist, wird die Website-URL im Standardbrowser geöffnet. Die URL wird außerdem auch im Veröffentlichungsfenster angezeigt.

1. Wenn der Browser geöffnet wird, sollte die Meldung „Die Seite kann aufgrund eines internen Serverfehlers nicht angezeigt werden.“ angezeigt werden. Diese Meldung deutet darauf hin, dass die Python-Umgebung auf dem Server nicht vollständig konfiguriert wurde. Führen Sie in diesem Fall folgende Schritte aus:

    a. Lesen Sie erneut den Artikel [Verwalten von Python auf Azure App Service](managing-python-on-azure-app-service.md), um sicherzustellen, dass eine passende Websiteerweiterung für Python installiert ist.

    b. Prüfen Sie den Pfad zum Python-Interpreter in Ihrer `web.config`-Datei erneut. Der Pfad muss genau mit dem Installationsspeicherort der ausgewählten Websiteerweiterung übereinstimmen.

    c. Verwenden Sie die Kudu-Konsole, um alle aufgeführten Pakete in der `requirements.txt`-Datei Ihrer App zu aktualisieren: Navigieren Sie zu demselben Python-Ordner, der auch für die `web.config`-Datei verwendet wird (z.B. `/home/python361x64`), und führen Sie den Befehl aus, der im Abschnitt [Kudu-Konsole](managing-python-on-azure-app-service.md#azure-app-service-kudu-console) beschrieben wird:

    ```command
    python -m pip install --upgrade -r /home/site/wwwroot/requirements.txt
    ```

    Wenn beim Ausführen dieses Befehls Fehler im Zusammenhang mit Berechtigungen auftreten, überprüfen Sie, ob Sie den Befehl auch wirklich im Websiteerweiterungsordner und *nicht* im Ordner einer der App Service-Standardinstallation von Python ausführen. Da Sie diese Standardumgebungen nicht verändern können, tritt bei dem Versuch, Pakete zu installieren, in jedem Fall ein Fehler auf.

    d. Fügen Sie dem `<system.webServer>`-Knoten der `web.config`-Datei die folgende Zeile hinzu, um eine detailliertere Fehlerausgabe zu erhalten:

    ```xml
    <httpErrors errorMode="Detailed"></httpErrors>
    ```

    e. Versuchen Sie, App Service nach der Installation neuer Pakete neu zu starten. Wenn Sie die `web.config`-Datei ändern, ist kein Neustart erforderlich, da App Service bei jeder Änderung von `web.config` einen automatischen Neustart durchführt.

    > [!Tip]
    > Wenn Sie Änderungen an der `requirements.txt`-Datei der App vornehmen, verwenden Sie die Kudu-Konsole erneut, um sämtliche Pakete zu installieren, die zu diesem Zeitpunkt in der Datei aufgeführt sind.

1. Sobald Sie die Serverumgebung vollständig konfiguriert haben, aktualisieren Sie die Seite im Browser und die Web-App sollte angezeigt werden.

    ![Ergebnisse der Veröffentlichung von Bottle-, Flask- und Django-Apps in App Service](media/azure-publish-results.png)

## <a name="publishing-to-app-service---visual-studio-2015"></a>Veröffentlichen in App Service: Visual Studio 2015

> [!Note]
> Ein kurzes Video zu diesem Prozess finden Sie unter [Visual Studio Python Tutorial: Building a Website (Visual Studio-Python-Tutorial: Erstellen einer Website)](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6) (youtube.com, 3 Min. 10 Sek.).

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie **Veröffentlichen** aus.

1. Wählen Sie im Dialogfeld **Veröffentlichen** **Microsoft Azure App Service**:

  ![Veröffentlichen in Azure – Schritt 1](media/tutorials-common-publish-1.png)

1. Wählen Sie ein Ziel aus:

    - Wenn Sie ein Azure-Abonnement haben, wählen Sie **Microsoft Azure App Service** als Veröffentlichungsziel, wählen Sie dann im folgenden Dialogfeld einen vorhandenen App Service aus, oder wählen Sie **Neu**, um einen neuen zu erstellen.
    - Wenn Sie eine temporäre Website von „try.azurewebsites.net“ verwenden, wählen Sie **Importieren** als Veröffentlichungsziel, suchen Sie dann nach der `.publishsettings`-Datei, die von der Website heruntergeladen wurde, und wählen Sie **OK**.

1. Die App Service-Details werden im Dialogfeld **Veröffentlichen** auf der Registerkarte **Verbindung** unten angezeigt.

  ![Veröffentlichen in Azure – Schritt 2](media/tutorials-common-publish-2.png)

1. Wählen Sie **Weiter >** nach Bedarf, um zusätzliche Einstellungen zu überprüfen.

1. Wählen Sie **Veröffentlichen**. Sobald Ihre Anwendung in Azure bereitgestellt ist, öffnet Ihr Standardbrowser diese Website.

Visual Studio führt ebenfalls die folgenden Schritte aus, die Bestandteil dieses Prozesses sind:

- Erstellen Sie eine `web.config`-Datei auf dem Server, der angemessene Zeiger auf die `wsgi_app`-Funktionen der App und den Standardinterpreter von App Service für Python 3.4 enthält.
- Deaktivieren Sie die Verarbeitung von Dateien im `static`-Ordner des Projekts (die Regeln dazu finden Sie in der `web.config`-Datei).
- Veröffentlichen Sie die virtuelle Umgebung auf dem Server.
- Fügen Sie eine `web.debug.config`-Datei und die Tools zum Debuggen hinzu, um das Remotedebuggen zu aktivieren. Für Visual Studio 2019 bis Version 16.4 bietet ptvsd die Tools zum Debuggen. Für Visual Studio 2019 ab Version 16.5 bietet debugpy die Tools zum Debuggen.

Wie zuvor bereits erwähnt, vereinfachen diese automatischen Schritte zwar den Veröffentlichungsprozess, jedoch gestaltet sich dadurch auch die Kontrolle über die Python-Umgebung schwieriger. Beispielsweise wird die `web.config`-Datei nur auf dem Server erstellt und nicht dem Projekt hinzugefügt. Der Veröffentlichungsprozess nimmt außerdem zusätzliche Zeit in Anspruch, da die gesamte virtuelle Umgebung von Ihrem Entwicklungscomputer kopiert wird und keine Abhängigkeit von der Serverkonfiguration entsteht.

Irgendwann möchten Sie möglicherweise Ihre eigene `web.config`-Datei verwalten und `requirements.txt` verwenden, um Pakete direkt auf dem Server zu verwalten. Wenn Sie `requirements.txt` verwenden, wird insbesondere sichergestellt, dass Ihre Entwicklung immer an die Serverumgebungen angepasst wird.
