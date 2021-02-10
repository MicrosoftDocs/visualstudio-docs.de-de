---
title: Konfigurieren von Python-Web-Apps für IIS
description: Konfigurieren von Python-Web-Apps für die Ausführung mit Internetinformationsdienste (Internet Information Services, IIS) von einem virtuellen Windows-Computer aus.
ms.date: 12/06/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 40411f47e7deda48b04ac4efb9bb9bc18688989a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839109"
---
# <a name="configure-python-web-apps-for-iis"></a>Konfigurieren von Python-Web-Apps für IIS

Wenn Sie Internetinformationsdienste (Internet Information Services, IIS) als Webserver auf einem Windows-Computer verwenden (einschließlich [Windows Virtual Machines in Azure](/azure/architecture/reference-architectures/n-tier/windows-vm)), müssen Python-Anwendungen bestimmte Einstellungen in ihren *web.config*-Dateien enthalten, damit IIS Python-Code ordnungsgemäß verarbeiten kann. Auf dem Computer selbst muss Python ebenfalls installiert sein, zusammen mit allen Paketen, die die Web-App benötigt.

> [!Note]
> Dieser Artikel enthielt zuvor Anleitungen zum Konfigurieren von Python unter Azure App Service unter Windows. Die in diesem Szenario verwendeten Python-Erweiterungen und Windows-Hosts wurden zugunsten von Azure App Service unter Linux als veraltet erklärt. Weitere Informationen finden Sie unter [Veröffentlichen von Python-Apps für Azure App Service (Linux)](publishing-python-web-applications-to-azure-from-visual-studio.md). Der frühere Artikel ist jedoch unter [Verwalten von App Service unter Windows mit den Python-Erweiterungen](managing-python-on-azure-app-service.md) noch verfügbar.

## <a name="install-python-on-windows"></a>Installieren von Python unter Windows

Um eine Web-App auszuführen, installieren Sie zunächst Ihre gewünschte Version von Python direkt auf dem Windows-Hostcomputer, wie unter [Installieren von Python-Interpretern](installing-python-interpreters.md) beschrieben.

Notieren Sie sich den Speicherort des `python.exe`-Interpreters für spätere Schritte. Zur Vereinfachung können Sie diesen Speicherort Ihrer PATH-Umgebungsvariablen hinzufügen.

## <a name="install-packages"></a>Installieren von Paketen

Wenn Sie einen dedizierten Host verwenden, können Sie die globale Python-Umgebung verwenden, um Ihre App anstelle einer virtuellen Umgebung auszuführen. Dementsprechend können Sie alle Anforderungen Ihrer Apps in der globalen Umgebung installieren, indem Sie einfach `pip install -r requirements.txt` an einer Eingabeaufforderung ausführen.

## <a name="set-webconfig-to-point-to-the-python-interpreter"></a>Festlegen, dass die „web.config“-Datei auf den Python-Interpreter verweist

Die Datei *web.config* Ihrer App weist den IIS-Webserver (Version 7 oder höher) unter Windows an, wie er Python-Anforderungen über HttpPlatform (empfohlen) oder FastCGI verarbeiten soll. Visual Studio 2015 und frühere Versionen nehmen diese Anpassungen automatisch vor. Wenn Sie Visual Studio 2017 oder höher verwenden, müssen Sie *web.config* manuell ändern.

### <a name="configure-the-httpplatform-handler"></a>Konfigurieren des HttpPlatform-Handlers

Das HTTP-Plattformmodul übergibt die Socketverbindungen direkt an einen eigenständigen Python-Prozess. Diese Weitergabe ermöglicht es Ihnen, einen beliebigen Webserver auszuführen, benötigt aber ein Startskript, das auf einem lokalen Webserver ausgeführt wird. Geben Sie das Skript in dem `<httpPlatform>`-Element von *web.config* an, in dem das `processPath`-Attribut auf den Python-Interpreter der Websiteerweiterung, und das `arguments`-Attribut auf Ihr Skript und alle Argumente verweist, die Sie bereitstellen möchten:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="httpPlatformHandler" resourceType="Unspecified"/>
    </handlers>
    <httpPlatform processPath="c:\python36-32\python.exe"
                  arguments="c:\home\site\wwwroot\runserver.py --port %HTTP_PLATFORM_PORT%"
                  stdoutLogEnabled="true"
                  stdoutLogFile="c:\home\LogFiles\python.log"
                  startupTimeLimit="60"
                  processesPerApplication="16">
      <environmentVariables>
        <environmentVariable name="SERVER_PORT" value="%HTTP_PLATFORM_PORT%" />
      </environmentVariables>
    </httpPlatform>
  </system.webServer>
</configuration>
```

Die Umgebungsvariable `HTTP_PLATFORM_PORT`, die an dieser Stelle angezeigt wird, enthält den Port, auf den Ihr lokaler Server nach Verbindungen von „localhost“ lauschen soll. In diesem Beispiel wird auch gezeigt, wie Sie gegebenenfalls eine andere Umgebungsvariable erstellen, in diesem Fall `SERVER_PORT`.

### <a name="configure-the-fastcgi-handler"></a>Konfigurieren des FastCGI-Handlers

FastCGI ist eine Schnittstelle, die auf der Anforderungsebene funktioniert. IIS empfängt eingehende Verbindungen und leitet jede Anforderung an eine WSGI-Anwendung an einen oder mehrere persistente Python-Prozesse weiter.

Um die Schnittstelle zu verwenden, installieren und konfigurieren Sie zunächst das wfastcgi-Paket wie unter [pypi.org/project/wfastcgi/](https://pypi.io/project/wfastcgi) beschrieben.

Ändern Sie anschließend die Datei *web.config* Ihrer App, um die vollständigen Pfade zu *python.exe* und *wfastcgi.py* in den Schlüssel `PythonHandler` aufzunehmen. Die folgenden Schritte gehen davon aus, dass Python in *c:\python36-32* installiert ist und dass sich Ihr App-Code in *c:\home\site\wwwwroot* befindet. Passen Sie Ihre Pfade entsprechend an:

1. Ändern Sie den Eintrag `PythonHandler` in *web.config* so, dass der Pfad mit dem Python-Installationsverzeichnis übereinstimmt (genaue Details finden Sie in der [IIS-Konfigurationsreferenz](https://www.iis.net/configreference) (iis.net)).

    ```xml
    <system.webServer>
      <handlers>
        <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
            scriptProcessor="c:\python36-32\python.exe|c:\python36-32\wfastcgi.py"
            resourceType="Unspecified" requireAccess="Script"/>
      </handlers>
    </system.webServer>
    ```

1. Fügen Sie im Abschnitt `<appSettings>` der Datei *web.config* Schlüssel für `WSGI_HANDLER`, `WSGI_LOG` (optional) und `PYTHONPATH` hinzu:

    ```xml
    <appSettings>
      <add key="PYTHONPATH" value="c:\home\site\wwwroot"/>
      <!-- The handler here is specific to Bottle; see the next section. -->
      <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
      <add key="WSGI_LOG" value="c:\home\LogFiles\wfastcgi.log"/>
    </appSettings>
    ```

    Diese `<appSettings>`-Werte stehen Ihrer App als Umgebungsvariablen zur Verfügung:

    - Der Wert für `PYTHONPATH` kann frei erweitert werden, muss jedoch den Stamm Ihrer App enthalten.
    - `WSGI_HANDLER` muss auf eine durch Ihre App importierbare WSGI-Anwendung verweisen.
    - `WSGI_LOG` ist optional, wird jedoch zum Debuggen Ihrer App empfohlen.

1. Legen Sie den `WSGI_HANDLER`-Eintrag auf die *web.config*-Datei fest, die für das von Ihnen verwendete Framework angemessen ist:

    - **Bottle**: Stellen Sie sicher, dass Klammern nach `app.wsgi_app` wie unten gezeigt vorhanden sind. Dies ist notwendig, da das Objekt eine Funktion (siehe *app.py*) und keine Variable ist:

        ```xml
        <!-- Bottle apps only -->
        <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
        ```

    - **Flask:** Ändern Sie den Wert `WSGI_HANDLER` in `<project_name>.app`, wobei das `<project_name>`-Element dem Namen Ihres Projekts entspricht. Den genauen Identifizierer können Sie ermitteln, indem Sie sich die Anweisung `from <project_name> import app` im *runserver.py*-Objekt ansehen. Wenn das Projekt z.B. den Namen „FlaskAzurePublishExample“ hat, sieht der Eintrag wie folgt aus:

        ```xml
        <!-- Flask apps only: change the project name to match your app -->
        <add key="WSGI_HANDLER" value="flask_iis_example.app"/>
        ```

    - **Django:** Für Django-Projekte müssen Sie zwei Änderungen an der *web.config*-Datei vornehmen. Ändern Sie zunächst den `WSGI_HANDLER`-Wert auf `django.core.wsgi.get_wsgi_application()` (das Objekt befindet sich in der *wsgi.py*-Datei):

        ```xml
        <!-- Django apps only -->
        <add key="WSGI_HANDLER" value="django.core.wsgi.get_wsgi_application()"/>
        ```

        Fügen Sie dann den folgenden Eintrag unter dem für `WSGI_HANDLER` hinzu, wobei Sie `DjangoAzurePublishExample` durch den Namen Ihres Projekts ersetzen:

        ```xml
        <add key="DJANGO_SETTINGS_MODULE" value="django_iis_example.settings" />
        ```

1. **Nur für Django-Anwendungen:** Fügen Sie in der Datei *settings.py* des Django-Projekts die Domäne Ihrer Website-URL oder Ihre IP-Adresse wie unten gezeigt zu `ALLOWED_HOSTS` hinzu, und ersetzen Sie „1.2.3.4“ durch Ihre URL oder IP-Adresse:

    ```python
    # Change the URL or IP address to your specific site
    ALLOWED_HOSTS = ['1.2.3.4']
    ```

    Fehler beim Hinzufügen Ihrer URL zu den Arrayergebnissen im Fehler **DisallowedHost at / Invalid HTTP_HOST header: '\<site URL\>'. Möglicherweise müssen Sie '\<site URL\>' zu ALLOWED_HOSTS hinzufügen.**

    Beachten Sie, dass Django automatisch „localhost“ und „127.0.0.1“ zulässt, wenn das Array leer ist. Wenn Sie jedoch Ihre Produktions-URL hinzufügen, werden diese Funktionen entfernt. Aus diesem Grund sollten Sie separate Entwicklungs- und Produktionskopien von *settings.py* beibehalten oder alternativ die Umgebungsvariablen verwenden, um die Laufzeitwerte zu kontrollieren.

## <a name="deploy-to-iis-or-a-windows-vm"></a>Bereitstellen für IIS oder einen virtuellen Windows-Computer

Mit der richtigen Datei *web.config* in Ihrem Projekt können Sie die Veröffentlichung auf dem Computer vornehmen, auf dem IIS ausgeführt wird, indem Sie den Befehl **Veröffentlichen** im Kontextmenü des Projekts im **Projektmappen-Explorer** verwenden und die Option **IIS, FTP usw.** auswählen. In diesem Fall kopiert Visual Studio einfach die Projektdateien auf den Server. Sie sind für die gesamte serverseitige Konfiguration verantwortlich.
