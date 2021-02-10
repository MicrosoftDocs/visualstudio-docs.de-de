---
title: Konfigurieren von Python in Azure App Service (Windows)
description: Installieren von Python-Interpretern und -Bibliotheken in Azure App Service und Konfigurieren von Webanwendungen in der Weise, dass sie korrekt auf den Interpreter verweisen.
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
ms.openlocfilehash: b76bc008c30efdee0185e6f122abaff8457acef6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882790"
---
# <a name="how-to-set-up-a-python-environment-on-azure-app-service-windows"></a>Einrichten einer Python-Umgebung in Azure App Service (Windows)

> [!Important]
> Microsoft hat die Python-Erweiterungen für App Service unter Windows wie in diesem Artikel beschrieben als veraltet erklärt, um eine direkte Bereitstellung für [App Service unter Linux](publishing-python-web-applications-to-azure-from-visual-studio.md) zu unterstützen.

[Azure App Service](https://azure.microsoft.com/services/app-service/) ist ein Platform-as-a-Service-Angebot für Webanwendungen, egal, ob es sich um über einen Webbrowser zugreifbare Websites, um von Ihren eigenen Clients verwendete REST-APIs, oder um ereignisgesteuerte Verarbeitung handelt. App Service unterstützt die Verwendung von Python zur Implementierung von Anwendungen vollständig.

Die benutzerdefinierte Python-Unterstützung auf Azure App Service besteht aus mehreren *Websiteerweiterungen* für App Service, von denen jede eine bestimmte Version der Python-Laufzeit enthält. Sie können sämtliche gewünschten Pakete direkt, wie in diesem Artikel beschrieben, in dieser Umgebung installieren. Wenn Sie die Umgebung in App Service anpassen, müssen Sie keine Pakete in Ihren Web-App-Projekten verwalten, und Sie müssen sie auch nicht zusammen mit dem App-Code hochladen.

> [!Tip]
> Obwohl in App Service standardmäßig Python 2.7 und Python 3.4 in Stammordnern auf dem Server installiert sind, können Sie die Pakete in diesen Umgebungen nicht anpassen oder installieren. Außerdem sollten Sie sich nicht darauf verlassen, dass tatsächlich Pakete vorhanden sind. Stattdessen sollten Sie sich, wie in diesem Artikel beschrieben, auf eine von Ihnen kontrollierte Websiteerweiterung verlassen.

## <a name="choose-a-python-version-through-the-azure-portal"></a>Auswählen einer Python-Version über das Azure-Portal

1. Erstellen Sie auf dem Azure-Portal App Service führ Ihre Web-App.
1. Scrollen Sie auf der Seite „App Service“ zum Abschnitt **Entwicklungstools**, und klicken Sie auf **Erweiterungen** > **+ Hinzufügen**.
1. Scrollen Sie in der Liste nach unten, bis Sie die Erweiterung finden, die die von Ihnen gewünschte Python-Version enthält:

    ![Azure-Portal mit Python-Erweiterungen](media/python-on-azure-extensions.png)

    > [!Tip]
    > Wenn Sie eine ältere Python-Version benötigen, die nicht unter den Websiteerweiterungen aufgeführt ist, können Sie diese, wie im nächsten Abschnitt beschrieben, über Azure Resource Manager installieren.

1. Klicken Sie auf die Erweiterung, akzeptieren Sie die rechtlichen Bedingungen, und klicken Sie anschließend auf **OK**.
1. Im Portal wird eine Benachrichtigung angezeigt, nachdem die Installation abgeschlossen wurde.

## <a name="choose-a-python-version-through-the-azure-resource-manager"></a>Auswählen einer Python-Version über den Azure Resource Manager

Wenn Sie App Service mit einer Azure Resource Manager-Vorlage bereitstellen, fügen Sie die Websiteerweiterung als Ressource hinzu. Insbesondere wird die Erweiterung als geschachtelte Ressource (ein `resources`-Objekt unter `resources`) mit dem Typ `siteextensions` und dem Namen aus [siteextensions.net](https://www.siteextensions.net/packages?q=Tags%3A%22python%22) angezeigt.

Nach dem Hinzufügen eines Verweises auf `python361x64` (Python 3.6.1 x64), sieht Ihre Vorlage in etwa wie folgt aus (einige Eigenschaften werden ausgelassen):

```json
"resources": [
  {
    "apiVersion": "2015-08-01",
    "name": "[parameters('siteName')]",
    "type": "Microsoft.Web/sites",

    // ...

    "resources": [
      {
        "apiVersion": "2015-08-01",
        "name": "python361x64",
        "type": "siteextensions",
        "properties": { },
        "dependsOn": [
          "[resourceId('Microsoft.Web/sites', parameters('siteName'))]"
        ]
      },
      // ...
    ]
  }
```

## <a name="set-webconfig-to-point-to-the-python-interpreter"></a>Festlegen, dass die „web.config“-Datei auf den Python-Interpreter verweist

Nach der Installation der Websiteerweiterung (entweder über das Portal oder eine Azure Resource Manager-Vorlage), verweisen Sie als Nächstes mit der *web.config*-Datei Ihrer App auf den Python-Interpreter. Die *web.config*-Datei weist den in App Service ausgeführten IIS-Webserver (7 und höher) entweder über HttpPlatform (empfohlen) oder FastCGI an, wie er mit Python-Anforderungen umgehen soll.

Suchen Sie zunächst den vollständigen Pfad zur *python.exe* der Websiteerweiterungen, und erstellen und ändern Sie dann die entsprechende *web.config*-Datei.

### <a name="find-the-path-to-pythonexe"></a>Finden des Pfads zu „python.exe“

Auf dem Server wird unter *d:\home* eine Python-Websiteerweiterung in einem Ordner installiert, der für die Python-Version und -Architektur geeignet ist (außer bei einigen älteren Versionen). Beispielsweise ist Python 3.6.1 x64 unter *d:\home\python361x64* installiert. Dann lautete der vollständige Pfad zum Python-Interpreter *d:\home\python361x64\python.exe*.

Klicken Sie auf **Erweiterungen** auf der Seite „App Service“, und wählen Sie die Erweiterung aus der Liste aus, um den genauen Pfad in App Service abzurufen.

![Liste der Erweiterung in Azure App Service](media/python-on-azure-extension-list.png)

Über diese Aktion wird die Beschreibungsseite der Erweiterung mit dem Pfad geöffnet:

![Details der Erweiterungen in Azure App Service](media/python-on-azure-extension-detail.png)

Wenn beim Anzeigen des Pfads zu einer Erweiterung Probleme auftreten, können Sie diesen manuell über die Konsole finden:

1. Wählen Sie auf der Seite „App Service“ **Entwicklungstools** > **Konsole** aus.
1. Geben Sie entweder den Befehl `ls ../home` oder den Befehl `dir ..\home` ein, um die Erweiterungsordner auf der obersten Ebene zu sehen, z.B. *Python361x64*.
1. Geben Sie einen Befehl wie `ls ../home/python361x64` oder `dir ..\home\python361x64` ein, um zu bestätigen, dass er *Python361x64* und andere Interpreterdateien enthält.

### <a name="configure-the-httpplatform-handler"></a>Konfigurieren des HttpPlatform-Handlers

Das HTTP-Plattformmodul übergibt die Socketverbindungen direkt an einen eigenständigen Python-Prozess. Diese Weitergabe ermöglicht es Ihnen, einen beliebigen Webserver auszuführen, benötigt aber ein Startskript, das auf einem lokalen Webserver ausgeführt wird. Geben Sie das Skript in dem `<httpPlatform>`-Element von *web.config* an, in dem das `processPath`-Attribut auf den Python-Interpreter der Websiteerweiterung, und das `arguments`-Attribut auf Ihr Skript und alle Argumente verweist, die Sie bereitstellen möchten:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="httpPlatformHandler" resourceType="Unspecified"/>
    </handlers>
    <httpPlatform processPath="D:\home\Python361x64\python.exe"
                  arguments="D:\home\site\wwwroot\runserver.py --port %HTTP_PLATFORM_PORT%"
                  stdoutLogEnabled="true"
                  stdoutLogFile="D:\home\LogFiles\python.log"
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

FastCGI ist eine Schnittstelle, die auf der Anforderungsebene funktioniert. IIS empfängt eingehende Verbindungen und leitet jede Anforderung an eine WSGI-Anwendung an einen oder mehrere persistente Python-Prozesse weiter. Das [wfastcgi-Paket](https://pypi.io/project/wfastcgi) ist bereits installiert und mit jeder Python-Websiteerweiterung konfiguriert, sodass Sie es leicht aktivieren können, indem Sie den Code in *web.config* einschließen. Dies wird im untenstehenden Beispiel für eine auf dem Bottle-Framework basierende Web-App dargestellt. Beachten Sie, dass sich die vollständigen Pfade zu *python.exe* und *wfastcgi.py* im `PythonHandler`-Schlüssel befinden:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <appSettings>
    <add key="PYTHONPATH" value="D:\home\site\wwwroot"/>
    <!-- The handler here is specific to Bottle; other frameworks vary. -->
    <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
    <add key="WSGI_LOG" value="D:\home\LogFiles\wfastcgi.log"/>
  </appSettings>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
           scriptProcessor="D:\home\Python361x64\python.exe|D:\home\Python361x64\wfastcgi.py"
           resourceType="Unspecified" requireAccess="Script"/>
    </handlers>
  </system.webServer>
</configuration>
```

Die an dieser Stelle definierten `<appSettings>` sind für Ihre Anwendung als Umgebungsvariablen verfügbar:

- Der Wert für `PYTHONPATH` kann frei erweitert werden, muss jedoch den Stamm Ihrer App enthalten.
- `WSGI_HANDLER` muss auf eine durch Ihre App importierbare WSGI-Anwendung verweisen.
- `WSGI_LOG` ist optional, wird jedoch zum Debuggen Ihrer App empfohlen.

Zusätzliche Informationen zu *web.config*-Inhalten für Bottle-, Flask- und Django-Web-Apps finden Sie unter [Veröffentlichen in Azure](publishing-python-web-applications-to-azure-from-visual-studio.md).

## <a name="install-packages"></a>Installieren von Paketen

Der über eine Websiteerweiterung installierte Python-Interpreter ist nur ein Bestandteil Ihrer Python-Erweiterung. Es ist sehr wahrscheinlich, dass Sie in dieser Umgebung verschiedene Pakete installieren müssen.

Verwenden Sie eine der folgenden Methoden, um Pakete direkt in der Serverumgebung zu installieren:

| Methoden | Verwendung |
| --- | --- |
| [Kudu-Konsole für Azure App Service](#azure-app-service-kudu-console) | Installiert Pakete interaktiv. Pakete müssen entweder nur aus Python bestehen oder Wheels veröffentlichen. |
| [Kudu-REST-API](#kudu-rest-api) | Können zur Automatisierung von Paketinstallationen verwendet werden.  Pakete müssen entweder nur aus Python bestehen oder Wheels veröffentlichen. |
| Bündeln mit einer App | Installieren Sie Pakete direkt in Ihrem Projekt, und stellen Sie sie für App Service als Teil Ihrer App bereit. Je nachdem, wie viele Abhängigkeiten Sie haben und wie oft Sie diese aktualisieren, kann diese Methode möglicherweise die einfachste Möglichkeit darstellen, eine funktionierende Bereitstellung zum Laufen zu bringen. Achten Sie darauf, dass Bibliotheken mit der Version von Python auf dem Server übereinstimmen müssen, andernfalls werden nach der Bereitstellung ungewöhnliche Fehler angezeigt. Da die Versionen von Python in den App Service-Websiteerweiterungen jedoch identisch mit denen sind, die auf „Python.org“ freigegeben wurden, können Sie problemlos eine kompatible Version für die lokale Entwicklung erhalten. |
| Virtuelle Umgebungen | Wird nicht unterstützt. Verwenden Sie stattdessen die Bündelung, und legen Sie die `PYTHONPATH`-Umgebungsvariable fest, sodass sie auf den Speicherort der Pakete verweist. |

### <a name="azure-app-service-kudu-console"></a>Kudu-Konsole für Azure App Service

Die [Kudu-Konsole](https://github.com/projectkudu/kudu/wiki/Kudu-console) ermöglicht Ihnen den direkten Befehlszeilenzugriff mit erhöhten Rechten auf den App Services-Server und dessen Dateisystem. Dies ist ein wichtiges Tool zum Debuggen und ermöglicht CLI-Vorgänge wie das Installieren von Paketen.

1. Öffnen Sie Kudu über die Seite „App Service“ im Azure-Portal, indem Sie auf **Entwicklunsgtools** > **Erweiterte Tools** klicken und dann **Go** (Los) auswählen. Über diese Aktion navigieren Sie zu einer URL, die der Basis-URL für App Service entspricht, allerdings wird `.scm` angefügt. Wenn Ihre Basis-URL `https://vspython-test.azurewebsites.net/` ist, dann ist Kudu auf `https://vspython-test.scm.azurewebsites.net/` (dort können Sie ein Lesezeichen hinzufügen):

    ![Die Kudu-Konsole für Azure App Service](media/python-on-azure-console01.png)

1. Wählen Sie **Debug-Konsole** > **CMD** aus, um die Konsole zu öffnen, in der Sie zu Ihrer Python-Installation navigieren können und sehen, welche Bibliotheken bereits vorhanden sind.

1. Um ein einzelnes Paket zu installieren:

    a. Navigieren Sie zum Ordner der Python-Installation, in dem Sie das Paket installieren möchten, z.B. *d:\home\python361x64*.

    b. Verwenden Sie `python.exe -m pip install <package_name>`, um ein Paket zu installieren.

    ![Beispiel für die Installation von Bottle über die Kudu-Konsole für Azure App Service](media/python-on-azure-console02.png)

1. Wenn Sie für Ihre App eine *requirements.txt*-Datei auf dem Server bereitgestellt haben, installieren Sie diese Anforderungen wie folgt:

    a. Navigieren Sie zum Ordner der Python-Installation, in dem Sie das Paket installieren möchten, z.B. *d:\home\python361x64*.

    b. Führen Sie den `python.exe -m pip install --upgrade -r d:\home\site\wwwroot\requirements.txt`-Befehl aus.

    Die Verwendung *requirements.txt* wird empfohlen, da es damit einfach ist, ihren genauen Paketsatz sowohl lokal als auch auf dem Server zu reproduzieren. Denken Sie daran, die Konsole erneut aufzurufen, nachdem Sie Änderungen an der *requirements.txt*-Datei bereitgestellt haben, und führen Sie den Befehl erneut aus.

> [!Note]
> Es gibt keinen C-Compiler auf Ihrem App Service, daher müssen Sie das Rad für alle Pakete mit nativen Erweiterungsmodulen installieren. Viele gängige Pakete stellen ihre eigenen Räder zur Verfügung. Sollte dies nicht der Fall sein, verwenden Sie `pip wheel <package_name>` auf dem lokalen Entwicklungscomputer und laden Sie das Rad auf Ihre Website hoch. Ein Beispiel finden Sie unter [Verwalten von erforderlichen Paketen mit „requirements.txt“](managing-required-packages-with-requirements-txt.md).

### <a name="kudu-rest-api"></a>Kudu-REST-API

Anstatt die Kudu-Konsole über das Azure-Portal zu verwenden, können Sie Befehle auch Remote über die Kudu-REST-API ausführen, indem Sie den Befehl auf `https://yoursite.scm.azurewebsites.net/api/command` posten. Posten Sie beispielsweise zum Installieren des `bottle`-Pakets den folgenden JSON auf `/api/command`:

```json
{
    "command": 'python.exe -m pip install bottle',
    "dir": '\home\python361x64'
}
```

Informationen zu Befehlen und Authentifizierung finden Sie in der [Kudu-Dokumentation](https://github.com/projectkudu/kudu/wiki/REST-API).

Über den Befehl `az webapp deployment list-publishing-profiles`, den Sie über die Azure CLI ausführen, werden außerdem Anmeldeinformationen angezeigt (vgl. [az webapp deployment (Bereitstellung der Azure Web-App](/cli/azure/webapp/deployment?view=azure-cli-latest&preserve-view=true#az-webapp-deployment-list-publishing-profiles))). Eine Hilfsbibliothek zum Bereitstellen von Kudu-Befehlen ist auch auf [GitHub](https://github.com/lmazuel/azure-webapp-publish/blob/master/azure_webapp_publish/kudu.py#L42) verfügbar.
