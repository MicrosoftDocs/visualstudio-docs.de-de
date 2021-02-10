---
title: Erstellen von Node.js- und Express-Apps
description: Erfahren Sie, wie Sie ein Node.js-Webanwendungsprojekt aus einer Visual Studio-Vorlage erstellen.
ms.custom: ''
ms.date: 4/21/2020
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 852bfad102c4ae34bee9528009e3d4b2dd8c7384
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925732"
---
# <a name="tutorial-create-a-nodejs-and-react-app-in-visual-studio"></a>Tutorial: Erstellen einer Node.js- und React-App in Visual Studio

Mit Visual Studio können Sie problemlos ein Node.js-Projekt erstellen sowie IntelliSense und andere integrierte Features nutzen, die Node.js unterstützen. In diesem Tutorial für Visual Studio erstellen Sie ein Node.js-Webanwendungsprojekt aus einer Visual Studio-Vorlage. Anschließend erstellen Sie mithilfe von React eine einfache App.

In diesem Tutorial lernen Sie, wie die folgenden Aufgaben ausgeführt werden:
> [!div class="checklist"]
> * Erstellen eines Node.js-Projekts
> * Hinzufügen von NPM-Paketen
> * Hinzufügen von React-Code zur App
> * Transpilieren von JSX
> * Fügen Sie den Debugger an.

## <a name="before-you-begin"></a>Vorbereitungen

In den folgenden häufig gestellten Fragen werden einige wichtige Konzepte vorgestellt.

### <a name="what-is-nodejs"></a>Was ist Node.js?

Node.js ist eine serverseitige JavaScript-Runtime-Umgebung, die JavaScript auf dem Server ausführt.

### <a name="what-is-npm"></a>Was ist NPM?

NPM ist der Standardpaket-Manager für Node.js. Der Paket-Manager vereinfacht das Veröffentlichen und Freigeben von Quellcode von Node.js-Bibliotheken und ist zum Vereinfachen der Installation, Aktualisierung und Deinstallation von Bibliotheken konzipiert.

### <a name="what-is-react"></a>Was ist React?

React ist ein Front-End-Framework zum Erstellen einer Benutzeroberfläche.

### <a name="what-is-jsx"></a>Was ist JSX?

JSX ist eine JavaScript-Syntaxerweiterung, die in der Regel mit React dazu verwendet wird, die Elemente der Benutzeroberfläche zu beschreiben. JSX-Code muss in einfaches JavaScript transpiliert werden, bevor er in einem Browser ausgeführt werden kann.

### <a name="what-is-webpack"></a>Was ist webpack?

Webpack bündelt JavaScript-Dateien für die Ausführung in einem Browser, kann aber auch andere Ressourcen und Objekte transformieren oder packen. Mit webpack werden häufig Compiler angegeben, z.B. Babel oder TypeScript, um JSX oder TypeScript-Code in einfaches JavaScript zu transpilieren.

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

    Dieses Tutorial wurde mit der Version 12.6.2 getestet.

    Sofern nicht bereits geschehen, empfehlen wir Ihnen, die LTS-Version von der [Node.js](https://nodejs.org/en/download/)-Website zu installieren, um optimale Kompatibilität mit externen Frameworks und Bibliotheken zu gewährleisten. Node.js wurde für 32-Bit- und 64-Bit-Architekturen entwickelt. Die Node.js-Tools in Visual Studio, die in der Node.js-Workload enthalten sind, unterstützen beide Versionen. Es wird nur eine Version benötigt, und das Node.js-Installationsprogramm unterstützt zu jedem Zeitpunkt nur jeweils eine Installation.
    
    Im Allgemeinen erkennt Visual Studio die installierte Node.js-Runtime automatisch. Wird die installierte Runtime nicht erkannt, können Sie das Projekt so konfigurieren, dass auf der Eigenschaftenseite auf die installierte Runtime verwiesen wird (klicken Sie hierzu nach dem Erstellen des Projekts mit der rechten Maustaste auf den Projektknoten, wählen Sie **Eigenschaften** aus, und legen Sie den **Node.exe-Pfad** fest). Sie können eine globale Installation von Node.js verwenden oder in jedem Ihrer Node.js-Projekte den Pfad zu einem lokalen Interpreter angeben. 

## <a name="create-a-project"></a>Erstellen eines Projekts

Erstellen Sie zunächst ein Projekt für die Node.js-Webanwendung.

1. Öffnen Sie Visual Studio.

1. Erstellen Sie ein neues Projekt.

    ::: moniker range=">=vs-2019"
    Drücken Sie **ESC**, um das Startfenster zu schließen. Geben Sie **STRG+Q** ein, um das Suchfeld zu öffnen, geben Sie **Node.js** ein, und wählen Sie dann **Leere Node.js-Webanwendung – JavaScript** aus. (Obwohl dieses Tutorial den TypeScript-Compiler verwendet, erfordern die Schritte, dass Sie mit der **JavaScript**-Vorlage beginnen.)
    
    Wählen Sie im angezeigten Dialogfeld **Erstellen** aus.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Klicken Sie oben in der Menüleiste auf **Datei** > **Neu** > **Projekt**. Erweitern Sie im linken Bereich des Dialogfelds **Neues Projekt** den Eintrag **JavaScript**, und wählen Sie dann **Node.js** aus. Klicken Sie im mittleren Bereich auf **Leere Node.js-Webanwendung**, geben Sie den Namen **NodejsWebAppBlank** ein, und wählen Sie **OK** aus.
    ::: moniker-end
    Wenn die Projektvorlage **Leere Node.js-Webanwendung** nicht angezeigt wird, müssen Sie die Workload für die **Node.js-Entwicklung** hinzufügen. Ausführliche Anweisungen dazu finden Sie in den [Voraussetzungen](#prerequisites).

    Visual Studio erstellt die neue Projektmappe und öffnet das Projekt.

    ![Node.js-Projekt im Projektmappen-Explorer](../javascript/media/tutorial-nodejs-react-project-structure.png)

    (1) Der **fett** hervorgehobene Name ist Ihr Projekt, dem Sie den Namen im Dialogfeld **Neues Projekt** gegeben haben. Im Dateisystem wird dieses Projekt durch eine *NJSPROJ*-Datei im Projektordner dargestellt. Klicken Sie mit der rechten Maustaste auf das Projekt, und wählen Sie **Eigenschaften** aus, um Eigenschaften und Umgebungsvariablen festzulegen, die dem Projekt zugeordnet sind. Roundtrips mit anderen Entwicklungstools sind möglich, da die Projektdatei keine benutzerdefinierte Änderungen an der Node.js-Projektquelle vornimmt.

    (2) Auf der oberen Ebene finden Sie eine Projektmappe, die standardmäßig denselben Namen hat wie Ihr Projekt. Eine Projektmappe, die auf dem Datenträger durch eine *SLN*-Datei dargestellt wird, ist ein Container für mindestens ein zugehöriges Projekt.

    (3) Der NPM-Knoten zeigt alle installierten NPM-Pakete an. Sie können mit der rechten Maustaste auf den NPM-Knoten klicken, um mithilfe eines Dialogfelds nach NPM-Paketen zu suchen und diese zu installieren.Sie können Pakete auch installieren oder aktualisieren, indem Sie die Einstellungen in *package.json* und die Optionen verwenden, die Sie über einen Rechtsklick auf den NPM-Knoten erreichen.

    (4) *package.json* ist eine Datei, die von NPM zum Verwalten von Paketabhängigkeiten und Paketversionen von lokal installierten Paketen verwendet wird. Weitere Informationen finden Sie unter [Verwalten von npm-Paketen](../javascript/npm-package-management.md).

    (5) Projektdateien wie z.B. *server.js* werden unter dem Projektknoten angezeigt. *server.js* ist die Projektstartdatei. Deshalb wird Sie **fett** angezeigt. Sie können die Startdatei festlegen, indem Sie mit der rechten Maustaste auf eine Datei im Projekt klicken und **Als Node.js-Startdatei festlegen** auswählen.

## <a name="add-npm-packages"></a>Hinzufügen von NPM-Paketen

Diese App erfordert mehrere NPM-Module, damit sie ordnungsgemäß ausgeführt wird.

* react
* react-dom
* express
* path
* ts-loader
* typescript
* webpack
* webpack-cli

1. Klicken Sie im Projektmappen-Explorer (rechter Bereich) mit der rechten Maustaste auf den **NPM**-Knoten im Projekt, und wählen Sie **Neue NPM-Pakete installieren** aus.

    Wählen Sie im Dialogfeld **Neue NPM-Pakete installieren** die aktuellste Paketversion aus, oder geben Sie eine Version an, die Sie installieren möchten. Wenn Sie die aktuelle Version dieser Pakete installieren, jedoch zu einem späteren Zeitpunkt unerwartete Fehler auftreten, sollten Sie die weiter unten beschriebenen Paketversionen installieren.

1. Suchen Sie im Dialogfeld **Neue npm-Pakete installieren** das React-Paket, und klicken Sie auf **Paket installieren**, um es zu installieren.

    ![NPM-Pakete installieren](../javascript/media/tutorial-nodejs-react-install-package.png)

    Klicken Sie auf das **Ausgabefenster**, um den Fortschritt der Paketinstallation anzuzeigen (Wählen Sie **npm** im Feld **Ausgabe anzeigen von** aus). Nach dem Installieren wird das Paket unter dem **NPM**-Knoten angezeigt.

    Die *package.json*-Datei des Projekts wird mit den neuen Paketinformationen einschließlich der Paketversion aktualisiert.

1. Verwenden Sie anstelle der Benutzeroberfläche den folgenden Code, und fügen Sie ihn in *package.json* ein, um nach den restlichen Paketen zu suchen und sie hinzuzufügen. Fügen Sie dazu einen `dependencies`-Abschnitt mit dem folgenden Code hinzu:

    ```json
    "dependencies": {
      "express": "~4.17.1",
      "path": "~0.12.7",
      "react": "~16.13.1",
      "react-dom": "~16.13.1",
      "ts-loader": "~7.0.1",
      "typescript": "~3.8.3",
      "webpack": "~4.42.1",
      "webpack-cli": "~3.3.11"
    }
    ```

    Wenn bereits ein `dependencies`-Abschnitt in Ihrer Version der leeren Vorlage vorhanden ist, ersetzen Sie ihn einfach durch den obigen JSON-Code. Weitere Informationen zur Verwendung dieser Datei finden Sie unter [package.json-Konfiguration](../javascript/configure-packages-with-package-json.md).

1. Speichern Sie die Änderungen.

1. Klicken Sie mit der rechten Maustaste auf den **NPM**-Knoten in Ihrem Projekt, und wählen Sie **NPM-Pakete installieren** aus.

    Dieser Befehl führt den npm-Installationsbefehl direkt aus.

    Klicken Sie im unteren Bereich auf das **Ausgabefenster**, um den Fortschritt der Installation der Pakete anzuzeigen. Die Installation kann einige Minuten dauern, und die Ergebnisse werden Ihnen möglicherweise nicht sofort angezeigt. Achten Sie zum Anzeigen der Ausgabe darauf, dass Sie im Fenster **Ausgabe** im Feld **Ausgabe anzeigen von** die Option **npm** ausgewählt haben.

    Die folgenden NPM-Module werden im Projektmappen-Explorer angezeigt, nachdem sie installiert wurden.

    ![NPM-Pakete](../javascript/media/tutorial-nodejs-react-npm-modules-installed.png)

    > [!NOTE]
    > Wenn Sie NPM-Pakete über die Befehlszeile installieren möchten, klicken Sie mit der rechten Maustaste auf den Projektknoten, und klicken Sie dann auf **Eingabeaufforderung hier öffnen**. Verwenden Sie die Node.js-Standardbefehle, um die Pakete zu installieren.

## <a name="add-project-files"></a>Hinzufügen von Projektdateien

Mit den folgenden Schritten fügen Sie dem Projekt vier neue Dateien hinzu.

* *app.tsx*
* *webpack-config.js*
* *index.html*
* *tsconfig.json*

Fügen Sie für diese einfache App die neuen Projektdateien dem Projektstammverzeichnis hinzu. (In den meisten Apps werden die Dateien in der Regel Unterordnern hinzugefügt und die relativen Pfadverweise entsprechend angepasst.)

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt **NodejsWebAppBlank**, und klicken Sie auf **Hinzufügen** > **Neues Element**.

1. Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option **TypeScript-JSX-Datei** aus, geben Sie den Namen *app.tsx* ein, und klicken Sie dann auf **Hinzufügen** bzw. **OK**.

1. Wiederholen Sie diese Schritte, um die Datei *webpack-config.js* hinzuzufügen. Wählen Sie anstelle einer TypeScript-JSX-Datei eine **JavaScript-Datei** aus.

1. Wiederholen Sie dieselben Schritte, um dem Projekt die Datei *index.html* hinzuzufügen. Wählen Sie anstelle einer JavaScript-Datei die Option **HTML-Datei** aus.

1. Wiederholen Sie dieselben Schritte, um dem Projekt die Datei *tsconfig.json* hinzuzufügen. Wählen Sie anstelle einer JavaScript-Datei die Option **TypeScript-JSON-Konfigurationsdatei** aus.

## <a name="add-app-code"></a>Hinzufügen von App-Code

1. Öffnen Sie *server.js*, und ersetzen Sie den vorhandenen Code durch den folgenden:

    ```javascript
    'use strict';
    var path = require('path');
    var express = require('express');

    var app = express();

    var staticPath = path.join(__dirname, '/');
    app.use(express.static(staticPath));

    // Allows you to set port in the project properties.
    app.set('port', process.env.PORT || 3000);

    var server = app.listen(app.get('port'), function() {
        console.log('listening');
    });
    ```

   Der vorherige Code verwendet Express, um Node.js als Webanwendungsserver zu starten. Dieser Code legt den Port auf die Portnummer fest, die in den Projekteigenschaften konfiguriert wird (die Standard-Portnummer in den Eigenschaften lautet 1337). Klicken Sie zum Öffnen der Projekteigenschaften im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie **Eigenschaften** aus.

1. Öffnen Sie *app.tsx*, und fügen Sie den folgenden Code hinzu:

    ```javascript
    declare var require: any

    var React = require('react');
    var ReactDOM = require('react-dom');

    export class Hello extends React.Component {
        render() {
            return (
                <h1>Welcome to React!!</h1>
            );
        }
    }

    ReactDOM.render(<Hello />, document.getElementById('root'));
    ```

    Der vorherige Code verwendet zum Anzeigen einer einfachen Nachricht JSX-Syntax und React.

1. Öffnen Sie *index.html*, und ersetzen Sie den **body**-Abschnitt durch den folgenden Code:

    ```html
    <body>
        <div id="root"></div>
        <!-- scripts -->
        <script src="./dist/app-bundle.js"></script>
    </body>
    ```

    Diese HTML-Seite lädt die Datei *app-bundle.js*, die den in einfaches JavaScript transpilierten JSX- und React-Code enthält. *app-bundle.js* ist momentan eine leere Datei. Im nächsten Abschnitt konfigurieren Sie Optionen, um den Code zu transpilieren.

## <a name="configure-webpack-and-typescript-compiler-options"></a>Konfigurieren von Webpack- und TypeScript-Compileroptionen

In den vorherigen Schritten haben Sie dem Projekt die Datei *webpack-config.js* hinzugefügt. Als Nächstes fügen Sie Webpack-Konfigurationscode hinzu. Sie fügen eine einfache Webpack-Konfiguration zur Angabe einer Eingabedatei (*app.tsx*) und einer Ausgabedatei (*app-bundle.js*) hinzu, um JSX in einfaches JavaScript zu bündeln und zu transpilieren. Für die Transpilierung konfigurieren Sie auch mehrere TypeScript-Compileroptionen. Dieser Code stellt eine Basiskonfiguration als Einführung in Webpack und den TypeScript-Compiler dar.

1. Öffnen Sie im Projektmappen-Explorer die Datei *webpack-config.js*, und fügen Sie den folgenden Code hinzu:

    ```json
    module.exports = {
        devtool: 'source-map',
        entry: "./app.tsx",
        mode: "development",
        output: {
            filename: "./app-bundle.js"
        },
        resolve: {
            extensions: ['.Webpack.js', '.web.js', '.ts', '.js', '.jsx', '.tsx']
        },
        module: {
            rules: [
                {
                    test: /\.tsx$/,
                    exclude: /(node_modules|bower_components)/,
                    use: {
                        loader: 'ts-loader'
                    }
                }
            ]
        }
    }
    ```

    Durch den Webpack-Konfigurationscode verwendet Webpack das TypeScript-Ladeprogramm, um JSX zu transpilieren.

1. Öffnen Sie *tsconfig.json*, und ersetzen Sie den Standardcode durch den folgenden Code, der die TypeScript-Compileroptionen angibt:

    ```json
    {
      "compilerOptions": {
        "noImplicitAny": false,
        "module": "commonjs",
        "noEmitOnError": true,
        "removeComments": false,
        "sourceMap": true,
        "target": "es5",
        "jsx": "react"
      },
      "exclude": [
        "node_modules"
      ],
      "files": [
        "app.tsx"
      ]
    }
    ```

    *app.tsx* wird als Quelldatei angegeben.

## <a name="transpile-the-jsx"></a>Transpilieren von JSX

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Eingabeaufforderung hier öffnen** aus.

1. Geben Sie in der Eingabeaufforderung folgenden Befehl ein:

    `node_modules\.bin\webpack app.tsx --config webpack-config.js`

    Das Ergebnis wird im Fenster „Eingabeaufforderung“ angezeigt.

    ![Ausführen von Webpack](../javascript/media/tutorial-nodejs-react-run-webpack-cmd.png)

    Werden anstatt der vorherigen Ausgabe Fehler angezeigt, müssen Sie diese beheben, damit Ihre App funktioniert. Wenn sich Ihre NPM-Paketversionen von den in diesem Tutorial verwendeten Versionen unterscheiden, kann dies eine der Fehlerursachen darstellen. Sie können die Fehler beheben, indem Sie exakt die in den vorherigen Schritten beschriebenen Versionen verwenden. Zudem müssen Sie möglicherweise zum Beheben der Fehler eine neuere Version installieren, wenn eine oder mehrere der Paketversionen als veraltet markiert wurden und zu einem Fehler führen. Informationen zur Verwendung von *package.json* zum Steuern von npm-Paketversionen finden Sie unter [package.json-Konfiguration](../javascript/configure-packages-with-package-json.md).

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Hinzufügen** > **Vorhandener Ordner** aus. Klicken Sie anschließend auf den *dist*-Ordner und auf **Ordner auswählen**.

    Visual Studio fügt dem Projekt den *dist*-Ordner hinzu, der die Dateien *app-bundle.js* und *app-bundle.js.map* enthält.

1. Öffnen Sie zum Anzeigen des transpilierten JavaScript-Codes die Datei *app-bundle.js*.

1. Wenn Sie aufgefordert werden, die extern geänderten Dateien erneut zu laden, klicken Sie auf **Ja, alle**.

    ![Laden geänderter Dateien](../javascript/media/tutorial-nodejs-react-reload-files.png)

Bei jeder Änderung, die Sie an *app.tsx* vornehmen, müssen Sie den Webpack-Befehl erneut ausführen. Fügen Sie zum Automatisieren dieses Schritts eine Buildskript hinzu, um JSX zu transpilieren.

## <a name="add-a-build-script-to-transpile-the-jsx"></a>Hinzufügen eines Buildskripts zum Transpilieren von JSX

Ab Visual Studio 2019 ist ein Buildskript erforderlich. Sie können JSX beim Erstellen von Visual Studio transpilieren, anstatt JSX über die Befehlszeile (wie im vorherigen Abschnitt gezeigt) zu transpilieren.

* Öffnen Sie *package.json*, und fügen Sie nach Abschnitt `dependencies` den folgenden Abschnitt ein:

   ```json
   "scripts": {
    "build": "webpack-cli app.tsx --config webpack-config.js"
   }
   ```

## <a name="run-the-app"></a>Ausführen der App

1. Wählen Sie **Webserver (Google Chrome)** oder **Webserver (Microsoft Edge)** als aktuelles Debugziel aus.

    ::: moniker range=">=vs-2019"
    ![Auswählen von Chrome als Debugziel](../javascript/media/vs-2019/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Auswählen von Chrome als Debugziel](../javascript/media/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end

    Wenn Chrome auf Ihrem Computer verfügbar ist, jedoch nicht als Option angezeigt wird, wählen Sie aus der Dropdownliste für das Debugziel **Browserauswahl** aus, und klicken Sie dann auf Chrome, um diesen Browser als Standardbrowser festzulegen (wählen Sie dazu **Als Standard festlegen** aus).

1. Drücken Sie zum Ausführen der App **F5** (**Debuggen** > **Debuggen starten**), oder klicken Sie auf die Schaltfläche mit dem grünen Pfeil.

    Ein Node.js-Konsolenfenster wird geöffnet, in dem der Port angezeigt wird, den der Debugger abhört.

    Visual Studio startet die Anwendung durch Öffnen der Startdatei *server.js*.

    ![Ausführen von React im Browser](../javascript/media/tutorial-nodejs-react-running-react.png)

1. Schließen Sie das Browserfenster.

1. Schließen Sie das Konsolenfenster.

## <a name="set-a-breakpoint-and-run-the-app"></a>Festlegen eines Haltepunkts und Ausführen der App

1. Klicken Sie in *server.js* auf den Bundsteg links neben der `staticPath`-Deklaration, um einen Haltepunkt festzulegen:

    ![Screenshot des Visual Studio-Codefensters für server.js. Ein roter Punkt im linken Bundsteg zeigt an, dass für die staticPath-Deklaration ein Haltepunkt festgelegt ist.](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    Haltepunkte sind eine einfache und wichtige Funktion zum zuverlässigen Debuggen. Ein Haltepunkt gibt an, wo Visual Studio im ausgeführten Code angehalten werden soll. So können Sie einen Blick auf die Werte von Variablen oder das Speicherverhalten werfen oder überprüfen, ob eine Verzweigung im Code ausgeführt wird.

1. Drücken Sie **F5** (**Debuggen** > **Debuggen starten**), um die App auszuführen.

    Der Debugger hält an dem von Ihnen festgelegten Haltepunkt an (die aktuelle Anweisung ist gelb gekennzeichnet). Jetzt können Sie den App-Status überprüfen, indem Sie auf die derzeitigen Variablen im Bereich zeigen. Verwenden Sie dafür Debuggerfenster wie **Lokal** und **Überwachen**.

1. Drücken Sie **F5**, um die App fortzusetzen.

1. Wenn Sie die Chrome-Entwicklertools oder F12-Tools für Microsoft Edge verwenden möchten, drücken Sie **F12**. Mit diesen Tools können Sie das DOM untersuchen und mithilfe der JavaScript-Konsole mit der App interagieren.

1. Schließen Sie den Webbrowser und die Konsole.

## <a name="set-and-hit-a-breakpoint-in-the-client-side-react-code"></a>Festlegen und Erreichen eines Haltepunkts im clientseitigen React-Code

Im vorherigen Abschnitt haben Sie den Debugger an den serverseitigen Node.js-Code angehängt. Wenn der Debugger von Visual Studio angehängt werden und Haltepunkte im clientseitigen React-Code erreichen soll, benötigt er Hilfe beim Identifizieren des richtigen Prozesses. Eine Möglichkeit, dies zu erreichen, ist die folgende:

### <a name="prepare-the-browser-for-debugging"></a>Vorbereiten des Browsers auf das Debuggen

::: moniker range=">=vs-2019"
Für dieses Szenario können Sie entweder Microsoft Edge (Chromium), was derzeit in der IDE **Microsoft Edge Beta** genannt wird, oder Chrome verwenden.
::: moniker-end
::: moniker range="vs-2017"
Verwenden Sie Chrome für dieses Szenario.
::: moniker-end

1. Schließen Sie alle Fenster des Zielbrowsers.

   Andere Browserinstanzen können das Öffnen des Browsers bei aktiviertem Debuggen verhindern. (Möglicherweise werden Browsererweiterungen ausgeführt, die den vollständigen Debugmodus verhindern. Wenn dies der Fall ist, müssen Sie den Task-Manager öffnen, um unerwartete Chrome-Instanzen zu finden.)

   ::: moniker range=">=vs-2019"
   Beenden Sie auch alle Instanzen von Chrome, wenn Sie Microsoft Edge (Chromium) verwenden. Da beide Browser die Chromium-Codebase nutzen, führt dies zu den besten Ergebnissen.
   ::: moniker-end

2. Starten Sie Ihren Browser mit aktiviertem Debuggen.

    ::: moniker range=">=vs-2019"
    Ab Visual Studio 2019 können Sie das `--remote-debugging-port=9222`-Flag beim Start des Browsers festlegen, indem Sie in der Symbolleiste **Debuggen** auf **Browserauswahl...** und dann auf **Hinzufügen** klicken, anschließend legen Sie das Flag im Feld **Argumente** fest. Verwenden Sie einen anderen Anzeigenamen für den Browser, z. B. **Microsoft Edge mit Debuggen** oder **Chrome mit Debuggen**. Weitere Informationen finden Sie in den [Versionshinweisen](/visualstudio/releases/2019/release-notes-v16.2).

    ![Ihren Browser zum Starten mit aktiviertem Debuggen festlegen](../javascript/media/tutorial-nodejs-react-edge-with-debugging.png)

    Öffnen Sie alternativ über das Windows-**Startmenü** den Befehl **Ausführen** (klicken Sie mit der rechten Maustaste auf die Schaltfläche, und wählen Sie **Ausführen** aus), und geben Sie den folgenden Befehl ein:

    `msedge --remote-debugging-port=9222`

    -oder-

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    ::: moniker range="vs-2017"
    Öffnen Sie über das Windows-**Startmenü** den Befehl **Ausführen** (klicken Sie mit der rechten Maustaste auf die Schaltfläche, und wählen Sie **Ausführen** aus), und geben Sie den folgenden Befehl ein:

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    Dadurch wird Ihr Browser mit aktiviertem Debuggen gestartet.

    Die App wird noch nicht ausgeführt, weshalb Ihnen eine leere Browserseite angezeigt wird.

### <a name="attach-the-debugger-to-client-side-script"></a>Anfügen des Debuggers an clientseitiges Skript

1. Wechseln Sie zu Visual Studio, und legen Sie dann einen Breakpoint in Ihrem Quellcode fest, entweder in *app-bundle.js* oder *app.tsx*.

    Legen Sie den Breakpoint für *app-bundle.js* wie in der folgenden Abbildung veranschaulicht in der `render()`-Funktion fest:

    ![Screenshot des Visual Studio-Codefensters für app-bundle.js. Ein roter Punkt im linken Bundsteg zeigt an, dass in der render-Funktion ein Haltepunkt festgelegt ist.](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    Drücken Sie **STRG**+**F**, um die `render()`-Funktion in der transpilierten Datei *app-bundle.js* zu suchen (oder klicken Sie auf **Bearbeiten** > **Suchen und Ersetzen** > **Schnellsuche**).

    Legen Sie den Breakpoint für *app.tsx* in der `render()`-Funktion in der `return`-Anweisung fest.

    ![Screenshot des Visual Studio-Codefensters für app.tsx. Ein roter Punkt im linken Bundsteg zeigt an, dass für die return-Anweisung der render-Funktion ein Haltepunkt festgelegt ist.](../javascript/media/tutorial-nodejs-react-set-breakpoint-in-tsx-file.png)

2. Wenn Sie den Breakpoint in der *TSX*-Datei festlegen (statt in *app-bundle.js*), müssen Sie die Datei *webpack-config.js* aktualisieren. Ersetzen Sie den folgenden Code:

    ```javascript
    output: {
        filename: "./app-bundle.js",
    },
    ```

    durch den folgenden:

    ```javascript
    output: {
        filename: "./app-bundle.js",
        devtoolModuleFilenameTemplate: '[resource-path]'  // removes the webpack:/// prefix
    },
    ```

    Dies ist eine reine Entwicklungseinstellung, die das Debuggen in Visual Studio aktiviert. Mit dieser Einstellung können Sie die generierten Verweise in der Quellzuordnungsdatei (*app-bundle.js.map*) beim Erstellen der App überschreiben. Webpack-Verweise in der Quellzuordnungsdatei enthalten standardmäßig das Präfix *webpack:///* , das Visual Studio daran hindert, die Quelldatei *app.tsx* zu finden. Wenn Sie diese spezifische Änderung vornehmen, wird der Verweis auf die Quelldatei *app.tsx* von *webpack:///./app.tsx* in *./app.tsx* geändert, wodurch das Debuggen ermöglicht wird.

3. Wählen Sie Ihren Zielbrowser in Visual Studio als Debugziel aus, und drücken Sie dann **STRG**+**F5** (oder klicken Sie auf **Debuggen** > **Starten ohne Debuggen**), um die App im Browser auszuführen.

    ::: moniker range=">=vs-2019"
    Wenn Sie eine Browserkonfiguration mit einem Anzeigenamen erstellt haben, wählen Sie diesen als Debugziel aus.
    ::: moniker-end

    Die App wird daraufhin in einer neuen Registerkarte im Browser geöffnet.

4. Wählen Sie **Debuggen** > **An den Prozess anhängen** aus.

    > [!TIP]
    > Sobald Sie mit diesen Schritten erstmalig an den Prozess angehängt haben, können Sie ab Visual Studio 2017 schnell erneut an diesen Prozess anhängen, indem Sie **Debuggen** > **Erneut an Prozess anhängen** auswählen.

5. Im Dialogfeld **An Prozess anhängen** finden Sie eine gefilterte Liste der Browserinstanzen, an die Sie anfügen können.

    ::: moniker range=">=vs-2019"
    Wählen Sie in Visual Studio 2019 im Feld **Anfügen an** den entsprechenden Debugger für Ihren Zielbrowser aus, **JavaScript (Chrome)** oder **JavaScript (Microsoft Edge (Chromium))** , und geben Sie **chrome** oder **edge** in das Filterfeld ein, um die Suchergebnisse zu filtern.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Wählen Sie in Visual Studio 2017 im Feld **Anfügen an** die Option **Webkit-Code** aus, und geben Sie **chrome** in das Filterfeld ein, um die Suchergebnisse zu filtern.
    ::: moniker-end

6. Wählen Sie den Browserprozess mit dem richtigen Hostport aus (in diesem Beispiel „localhost“), und klicken Sie dann auf **Anfügen**.

    Der Port (1337) kann auch im Feld **Titel** angezeigt werden, damit Sie die richtige Browserinstanz einfacher identifizieren können.

    ::: moniker range=">=vs-2019"
    Im folgenden Beispiel wird veranschaulicht, wie dies bei Verwendung von Microsoft Edge (Chromium) aussieht.

    ![Anhängen an den Prozess](../javascript/media/tutorial-nodejs-react-attach-to-process-edge.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Anhängen an den Prozess](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    Der Debugger wurde ordnungsgemäß angehängt, wenn DOM Explorer und die JavaScript-Konsole in Visual Studio geöffnet werden. Diese Debugtools ähneln den Chrome-Entwicklertools und den F12-Tools für Microsoft Edge.
    ::: moniker-end

    > [!TIP]
    > Wenn der Debugger nicht angefügt wird, und die Meldung „Das Anfügen an den Prozess ist nicht möglich. Ein Vorgang ist für den derzeitigen Zustand unzulässig.“ angezeigt wird, verwenden Sie den Task-Manager, um alle Instanzen des Zielbrowsers zu schließen, bevor Sie den Browser im Debugmodus starten. Möglicherweise werden Browsererweiterungen ausgeführt, die den vollständigen Debugmodus verhindern.

7. Da der Code mit dem Haltepunkt bereits ausgeführt wurde, aktualisieren Sie zum Erreichen des Haltepunkts die Browserseite.

    Während der Unterbrechung im Debugger können Sie den App-Status überprüfen, indem Sie mit dem Mauszeiger auf Variablen zeigen und Debuggerfenster verwenden. Sie können den Debugger durch Navigieren im Code nach vorne verschieben (**F5**, **F10** und **F11**). Weitere Informationen zu grundlegenden Debugfeatures finden Sie unter [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md).

    Abhängig von den zuvor ausgeführten Schritten sowie von Ihrer Umgebung und dem Browserstatus erreichen Sie möglicherweise den Breakpoint entweder in *app-bundle.js* oder am zugeordneten Speicherort in *app.tsx*. In beiden Fällen können Sie durch den Code navigieren und Variablen überprüfen.

   * Wenn Sie in *app.tsx* Code unterbrechen müssen und dies nicht können, verwenden Sie **An den Prozess anhängen**, wie in den vorherigen Schritten beschrieben, um den Debugger anzuhängen. Stellen Sie sicher, dass Ihre Umgebung ordnungsgemäß eingerichtet ist:

      * Haben Sie alle Browserinstanzen, einschließlich der Chrome-Erweiterungen (mithilfe des Task-Managers) geschlossen, damit Sie den Browser im Debugmodus ausführen können? Stellen Sie sicher, dass Sie den Browser im Debugmodus starten.

      * Stellen Sie sicher, dass Ihre Quellzuordnungsdatei einen Verweis auf *./app.tsx* und nicht auf *webpack:///./app.tsx* enthält, da dies den Visual Studio-Debugger daran hindern würde, *app.tsx* zu finden.
       Wenn Sie den Code in *app.tsx* unterbrechen müssen und nicht in der Lage dazu sind, können Sie alternativ versuchen, die `debugger;`-Anweisung in *app.tsx* zu verwenden oder Breakpoints in den Chrome-Entwicklertools (oder in den F12-Tools für Microsoft Edge) festzulegen.

   * Wenn Sie Code in *app bundle.js* unterbrechen müssen, dies jedoch nicht möglich ist, entfernen Sie die Quellzuordnungsdatei *app bundle.js.map*.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Deploy the app to Linux App Service (Bereitstellen der App für Linux App Service)](../javascript/publish-nodejs-app-azure.md)
