---
title: Debuggen einer JavaScript- oder TypeScript-App
description: Visual Studio unterstützt das Debuggen JavaScript- and TypeScript-Apps in Visual Studio
ms.date: 11/01/2019
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 369fa3c080705f552aed25ecef6bd87a3db43a64
ms.sourcegitcommit: 105e7b5a486262bc92939980383ceee068098a11
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/30/2020
ms.locfileid: "97815619"
---
# <a name="debug-a-javascript-or-typescript-app-in-visual-studio"></a>Debuggen einer JavaScript- oder TypeScript-App in Visual Studio

Sie können mithilfe von Visual Studio JavaScript- und TypeScript-Code debuggen. Sie können Breakpoints festlegen und erreichen, den Debugger anfügen, Variablen untersuchen, die Aufrufliste anzeigen und andere Debugfeatures verwenden.

> [!TIP]
> Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/) kostenlos herunterladen. Je nachdem, welche Art von App-Entwicklung Sie wählen, müssen Sie die **Workload für die Node.js-Entwicklung** zusammen mit Visual Studio installieren.

## <a name="debug-server-side-script"></a>Debuggen von serverseitigen Skripts

1. Öffnen Sie zunächst Ihr Projekt in Visual Studio und anschließend eine serverseitige JavaScript-Datei (z. B. *server.js*). Klicken Sie dann auf den Bundsteg auf der linken Seite, um einen Breakpoint festzulegen:

    ![Screenshot des Visual Studio-Codefensters mit JavaScript-Code. Ein roter Punkt im linken Bundsteg zeigt an, dass ein Haltepunkt festgelegt ist.](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    Haltepunkte sind eine einfache und wichtige Funktion zum zuverlässigen Debuggen. Ein Haltepunkt gibt an, wo Visual Studio im ausgeführten Code angehalten werden soll. So können Sie einen Blick auf die Werte von Variablen oder das Speicherverhalten werfen oder überprüfen, ob eine Verzweigung im Code ausgeführt wird.

1. Drücken Sie **F5** (**Debuggen** > **Debuggen starten**), um die App auszuführen.

    Der Debugger hält an dem von Ihnen festgelegten Haltepunkt an (die aktuelle Anweisung ist gelb gekennzeichnet). Jetzt können Sie den App-Status überprüfen, indem Sie auf die derzeitigen Variablen im Bereich zeigen. Verwenden Sie dafür Debuggerfenster wie **Lokal** und **Überwachen**.

1. Drücken Sie **F5**, um die App fortzusetzen.

1. Wenn Sie die Chrome-Entwicklertools oder die F12-Tools verwenden möchten, drücken Sie **F12**. Mit diesen Tools können Sie das DOM untersuchen und mithilfe der JavaScript-Konsole mit der App interagieren.

## <a name="debug-client-side-script"></a>Debuggen von clientseitigen Skripts

::: moniker range=">=vs-2019"
Visual Studio unterstützt das clientseitige Debuggen nur für Chrome und Microsoft Edge (Chromium). In einigen Szenarios erreicht der Debugger automatisch Breakpoints in JavaScript- und TypeScript-Code sowie in Skripts, die in HTML-Dateien eingebettet sind. Informationen zum Debuggen von clientseitigen Skripts in ASP.NET-Apps finden Sie im Blogbeitrag zum [Debuggen von JavaScript in Microsoft Edge](https://devblogs.microsoft.com/visualstudio/debug-javascript-in-microsoft-edge-from-visual-studio/) und in [diesem Beitrag zu Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome). Weitere Informationen zum Debuggen von TypeScript in ASP.NET Core finden Sie auch unter [Erstellen einer ASP.NET Core-App mit TypeScript](tutorial-aspnet-with-typescript.md).
::: moniker-end
::: moniker range="vs-2017"
Visual Studio unterstützt das clientseitige Debuggen nur für Chrome und Internet Explorer. In einigen Szenarios erreicht der Debugger automatisch Breakpoints in JavaScript- und TypeScript-Code sowie in Skripts, die in HTML-Dateien eingebettet sind. Informationen zum Debuggen von clientseitigen Skripts in ASP.NET-Apps finden Sie im Blogbeitrag [Client-seitiges Debuggen von ASP.NET-Projekten in Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/).
::: moniker-end

Führen Sie für andere Anwendungen als ASP.NET die hier beschriebenen Schritte durch.

### <a name="prepare-your-app-for-debugging"></a>Vorbereiten der App auf das Debuggen

Wenn Ihre Quelle verkleinert oder von einem Transpiler wie TypeScript oder Babel erstellt wird, sollten [Quellzuordnungen](#generate_source_maps) verwendet werden, um beim Debuggen die bestmöglichen Ergebnisse zu erzielen. Wenn keine Quellzuordnungen verwendet werden, können Sie allerdings immer noch den Debugger an ein clientseitiges Skript anfügen, das zu diesem Zeitpunkt ausgeführt wird. Es kann aber vorkommen, dass Sie Breakpoints nicht in der ursprünglichen Quelldatei, sondern nur in der verkleinerten oder transpilierten Datei festlegen oder erreichen können. In einer Vue.js-App werden verkleinerte Skripts beispielsweise als Zeichenfolgen an eine `eval`-Anweisung übergeben, und Sie können den Code nur erfolgreich mithilfe des Visual Studio-Debuggers durchgehen, wenn Sie Quellzuordnungen verwenden. In komplexen Debugszenarios können Sie stattdessen auch auf die Chrome-Entwicklertools oder die F12-Tools in Microsoft Edge zurückgreifen.

Informationen zum Generieren von Quellzuordnungsdateien finden Sie unter [Generieren von Quellzuordnungsdateien zum Debuggen](#generate_source_maps).

### <a name="prepare-the-browser-for-debugging"></a><a name="prepare_the_browser_for_debugging"></a> Vorbereiten des Browsers auf das Debuggen

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

Der Debugger benötigt Hilfe beim Identifizieren des richtigen Prozesses, um den Debugger von Visual Studio anzufügen und Breakpoints im clientseitigen Code zu erreichen. Eine Möglichkeit, dies zu erreichen, ist die folgende:

1. Wechseln Sie zu Visual Studio, und legen Sie dann einen Breakpoint in Ihrem Quellcode fest, bei dem es sich um eine JavaScript-, TypeScript-, oder eine JSX-Datei handeln kann. (Legen Sie den Breakpoint in einer Codezeile fest, die Breakpoints zulässt, z. B. eine return-Anweisung oder eine var-Deklaration.)

    ![Screenshot des Visual Studio-Codefensters. Eine return-Anweisung ist ausgewählt, und ein roter Punkt im linken Bundsteg zeigt an, dass ein Haltepunkt festgelegt ist.](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    Verwenden Sie **STRG**+**F** (oder **Bearbeiten** > **Suchen und Ersetzen** > **Schnellsuche**), um den spezifischen Code in einer transpilierten Datei zu finden.

    Damit clientseitiger Code einen Breakpoint in einer TypeScript-, *VUE*- oder JSX-Datei erreichen kann, ist in der Regel die Verwendung von [Quellzuordnungsdateien](#generate_source_maps) erforderlich. Eine Quellzuordnungsdatei muss für die Unterstützung des Debuggens in Visual Studio ordnungsgemäß konfiguriert sein.

2. Wählen Sie Ihren Zielbrowser in Visual Studio als Debugziel aus, und drücken Sie dann **STRG**+**F5** (oder klicken Sie auf **Debuggen** > **Starten ohne Debuggen**), um die App im Browser auszuführen.

    ::: moniker range=">=vs-2019"
    Wenn Sie eine Browserkonfiguration mit einem Anzeigenamen erstellt haben, wählen Sie diesen als Debugziel aus.
    ::: moniker-end

    Die App wird daraufhin in einer neuen Registerkarte im Browser geöffnet.

3. Wählen Sie **Debuggen** > **An den Prozess anhängen** aus.

    > [!TIP]
    > Sobald Sie mit diesen Schritten erstmalig an den Prozess angehängt haben, können Sie ab Visual Studio 2017 schnell erneut an diesen Prozess anhängen, indem Sie **Debuggen** > **Erneut an Prozess anhängen** auswählen.

4. Im Dialogfeld **An Prozess anhängen** finden Sie eine gefilterte Liste der Browserinstanzen, an die Sie anfügen können.
    ::: moniker range=">=vs-2019"
    Wählen Sie in Visual Studio 2019 im Feld **Anfügen an** den entsprechenden Debugger für Ihren Zielbrowser aus, **JavaScript (Chrome)** oder **JavaScript (Microsoft Edge (Chromium))** , und geben Sie **chrome** oder **edge** in das Filterfeld ein, um die Suchergebnisse zu filtern.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Wählen Sie in Visual Studio 2017 im Feld **Anfügen an** die Option **Webkit-Code** aus, und geben Sie **chrome** in das Filterfeld ein, um die Suchergebnisse zu filtern.
    ::: moniker-end

5. Wählen Sie den Browserprozess mit dem richtigen Hostport aus (in diesem Beispiel „localhost“), und klicken Sie dann auf **Anfügen**.

    Der Port (z. B. 1337) kann auch im Feld **Titel** angezeigt werden, damit Sie die richtige Browserinstanz einfacher identifizieren können.

    ::: moniker range=">=vs-2019"
    Im folgenden Beispiel wird veranschaulicht, wie dies bei Verwendung von Microsoft Edge (Chromium) aussieht.

    ![Anhängen an den Prozess](../javascript/media/tutorial-nodejs-react-attach-to-process-edge.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Anhängen an den Prozess](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    Der Debugger wurde ordnungsgemäß angehängt, wenn DOM Explorer und die JavaScript-Konsole in Visual Studio geöffnet werden. Diese Debugtools ähneln den Chrome-Entwicklertools und den F12-Tools für Microsoft Edge.
    ::: moniker-end

    > [!TIP]
    > Wenn der Debugger nicht angefügt wird, und die Meldung „Fehler beim Starten des Debugadapters.“ oder „Das Anfügen an den Prozess ist nicht möglich. Ein Vorgang ist für den derzeitigen Zustand unzulässig.“ angezeigt wird, verwenden Sie den Windows Task-Manager, um alle Instanzen des Zielbrowsers zu schließen, bevor Sie den Browser im Debugmodus starten. Möglicherweise werden Browsererweiterungen ausgeführt, die den vollständigen Debugmodus verhindern.

6. Da der Code mit dem Breakpoint möglicherweise bereits ausgeführt wurde, aktualisieren Sie die Browserseite. Ergreifen Sie bei Bedarf Maßnahmen, damit der Code mit dem Breakpoint ausgeführt wird.

    Während der Unterbrechung im Debugger können Sie den App-Status überprüfen, indem Sie mit dem Mauszeiger auf Variablen zeigen und Debuggerfenster verwenden. Sie können den Debugger durch Navigieren im Code nach vorne verschieben (**F5**, **F10** und **F11**). Weitere Informationen zu grundlegenden Debugfeatures finden Sie unter [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md).

    Abhängig von Ihrem App-Typ und den zuvor ausgeführten Schritten sowie anderen Faktoren wie Ihrem Browserstatus erreichen Sie möglicherweise den Breakpoint entweder in einer transpilierten *JS*-Datei oder der Quelldatei. In beiden Fällen können Sie durch den Code navigieren und Variablen überprüfen.

   * Wenn Sie Code in einer TypeScript-, JSX- oder *VUE*-Quelldatei unterbrechen müssen und nicht dazu in der Lage sind, sollten Sie gemäß der Beschreibung im Abschnitt [Problembehandlung](#troubleshooting_source_maps) sicherstellen, dass Ihre Umgebung ordnungsgemäß eingerichtet ist.

   * Wenn Sie Code in einer transpilierten JavaScript-Datei (z. B. *app-bundle.js*) unterbrechen müssen, dies jedoch nicht möglich ist, entfernen Sie die Quellzuordnungsdatei *Dateiname.js.map*.

### <a name="troubleshooting-breakpoints-and-source-maps"></a><a name="troubleshooting_source_maps"></a> Problembehandlung für Breakpoints und Quellzuordnungsdateien

Wenn Sie Code in einer TypeScript- oder JSX-Quelldatei unterbrechen müssen und nicht in der Lage dazu sind, verwenden Sie **An Prozess anhängen** wie in den vorherigen Schritten beschrieben, um den Debugger anzuhängen. Stellen Sie sicher, dass Ihre Umgebung ordnungsgemäß eingerichtet ist:

* Haben Sie alle Browserinstanzen, einschließlich der Chrome-Erweiterungen (mithilfe des Task-Managers) geschlossen, damit Sie den Browser im Debugmodus ausführen können?
      
* Stellen Sie sicher, dass Sie [den Browser im Debugmodus starten](#prepare_the_browser_for_debugging).

* Stellen Sie sicher, dass Ihre Quellzuordnungsdatei den relativen Pfad auf Ihre Quelldatei enthält und keine nicht unterstützten Präfixe wie *webpack:///* enthält, was den Visual Studio-Debugger daran hindert, eine Quelldatei zu finden. Ein Verweis wie *webpack:///.app.tsx* sollte beispielsweise in *./app.tsx* korrigiert werden. Diese Änderung können Sie manuell in der Quellzuordnungsdatei (was für Tests nützlich ist) oder über eine benutzerdefinierte Buildkonfiguration durchführen. Weitere Informationen finden Sie unter [Generieren von Quellzuordnungen zum Debuggen](#generate_source_maps).

Wenn Sie den Code in einer Quelldatei (z. B. in *app.tsx*) unterbrechen müssen und nicht in der Lage dazu sind, können Sie alternativ versuchen, die `debugger;`-Anweisung in der Quelldatei zu verwenden oder Breakpoints in den Chrome-Entwicklertools (oder in den F12-Tools für Microsoft Edge) festzulegen.

## <a name="generate-source-maps-for-debugging"></a><a name="generate_source_maps"></a> Generieren von Quellzuordnungen zum Debuggen

In Visual Studio sind Funktionen zum Verwenden und Generieren von Quellzuordnungen für JavaScript-Quelldateien verfügbar. Diese werden häufig benötigt, wenn eine Quelle verkleinert oder von einem Transpiler wie TypeScript oder Babel erstellt wird. Die verfügbaren Optionen sind vom Projekttyp abhängig.

* Ein TypeScript-Projekt in Visual Studio generiert die Quellzuordnungen standardmäßig. Weitere Informationen finden Sie unter [Konfigurieren von Quellzuordnungsdateien mithilfe einer „tsconfig.json“-Datei](#configure_source_maps).

* In einem JavaScript-Projekt können Sie Quellzuordnungen mithilfe eines Bundlers wie Webpack und einem Compiler wie dem TypeScript-Compiler (oder Babel) erstellen, die Sie zu Ihrem Projekt hinzufügen können. Für den TypeScript-Compiler müssen Sie außerdem eine *tsconfig.json*-Datei hinzufügen und die Compileroption `sourceMap` festlegen. Unter [Create a Node.js app with React (Erstellen einer Node.js-App mit React)](../javascript/tutorial-nodejs-with-react-and-jsx.md) wird dieser Vorgang in einem Beispiel mit einer einfachen Webpack-Konfiguration erläutert.

> [!NOTE]
> Wenn Sie sich noch nicht mit Quellzuordnungen auskennen, lesen Sie zunächst den Artikel [Introduction to JavaScript Source Maps (Einführung in JavaScript-Quellzuordnungen)](https://www.html5rocks.com/en/tutorials/developertools/sourcemaps/), bevor Sie fortfahren. 

Verwenden Sie zum Konfigurieren von erweiterten Einstellungen für Quellzuordnungen entweder die *tsconfig.json*-Datei oder die Projekteinstellungen in einem TypeScript-Projekt, aber nicht beides zusammen.

Sie müssen sicherstellen, dass die Verweise auf Ihre Quelldatei in der generierten Quellzuordnungsdatei richtig sind (dies muss gegebenenfalls getestet werden), um das Debuggen mit Visual Studio zu aktivieren. Wenn Sie beispielsweise Webpack verwenden, enthalten Verweise in der Quellzuordnungsdatei das Präfix *webpack:///* , das Visual Studio daran hindert, eine TypeScript- oder JSX-Quelldatei zu finden. Wenn Sie dies spezifisch zu Debugzwecken korrigieren, muss der Verweis auf die Quelldatei (z. B. *app.tsx*) von etwas wie *webpack:///./app.tsx* in etwas wie *./app.tsx* geändert werden, was das Debuggen ermöglicht (der Pfad ist relativ zu Ihrer Quelldatei). Im folgenden Beispiel wird veranschaulicht, wie Sie Quellzuordnungsdateien in Webpack konfigurieren, damit sie in Visual Studio funktionieren. Dies ist einer der am häufigsten verwendeten Bundler.

Wenn Sie den Breakpoint in einer TypeScript- oder JSX-Datei festlegen, (anstelle einer transpilierten JavaScript-Datei), müssen Sie Ihre Webpack-Konfiguration aktualisieren (gilt nur für Webpack). Zum Beispiel müssen Sie in *webpack-config.js* möglicherweise den folgenden Code ersetzen:

```javascript
  output: {
    filename: "./app-bundle.js", // This is an example of the filename in your project
  },
```

durch den folgenden:

```javascript
  output: {
    filename: "./app-bundle.js", // Replace with the filename in your project
    devtoolModuleFilenameTemplate: '[resource-path]'  // Removes the webpack:/// prefix
  },
```

Dies ist eine reine Entwicklungseinstellung, die das Debuggen von clientseitigem Code in Visual Studio aktiviert.

In komplizierten Szenarios eignen sich manchmal die Browsertools (**F12**) am besten zum Debuggen, da sie keine Änderungen an benutzerdefinierten Präfixen erfordern.

### <a name="configure-source-maps-using-a-tsconfigjson-file"></a><a name="configure_source_maps"></a> Konfigurieren von Quellzuordnungsdateien mithilfe einer „tsconfig.json“-Datei

Wenn Sie eine *tsconfig.json*-Datei zu Ihrem Projekt hinzufügen, behandelt Visual Studio den Verzeichnisstamm wie ein TypeScript-Projekt. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf Ihr Projekt, und klicken Sie dann auf **Hinzufügen > Neues Element > TypeScript-JSON-Konfigurationsdatei**, um die Datei hinzuzufügen. Dann wird eine der folgenden Datei ähnlichen *tsconfig.json*-Datei zu Ihrem Projekt hinzugefügt.

```json
{
  "compilerOptions": {
    "noImplicitAny": false,
    "noEmitOnError": true,
    "removeComments": false,
    "sourceMap": true,
    "target": "es5"
  },
  "exclude": [
    "node_modules",
    "wwwroot"
  ]
}
```

#### <a name="compiler-options-for-tsconfigjson"></a>Compileroptionen für „tsconfig.json“-Dateien

* **inlineSourceMap**: Gibt eine einzelne Datei mit Quellzuordnungen aus, anstatt separate Quellzuordnungen für jede Quelldatei zu erstellen.
* **inlineSources**: Gibt die Quelle neben den Quellzuordnungen innerhalb einer einzelnen Datei aus. Dafür müssen die Optionen *inlineSourceMap* oder *sourceMap* festgelegt sein.
* **mapRoot**: Gibt anstelle des Standardspeicherorts den Speicherort an, an dem der Debugger die Quellzuordnungsdateien ( *.map*) finden sollte. Verwenden Sie dieses Flag, wenn die *MAP*-Laufzeitdateien an einem anderen Ort als die *JS*-Dateien gespeichert werden müssen. Der angegebene Speicherort ist in die Quellzuordnung eingebettet, damit der Debugger zum Speicherort der *MAP*-Dateien weitergeleitet wird.
* **sourceMap**: Generiert eine entsprechende *MAP*-Datei.
* **sourceRoot**: Gibt anstelle der Quellspeicherorte den Speicherort an, an dem der Debugger die TypeScript-Dateien finden sollte. Verwenden Sie dieses Flag, wenn die Laufzeitquellen an einem anderen Ort als an dem Speicherort zur Entwurfszeit gespeichert werden müssen. Der angegebene Speicherort wird in die Quellzuordnung eingebettet, um den Debugger an den Ort weiterzuleiten, an dem sich die Quelldateien befinden.

Weitere Informationen zu Compileroptionen finden Sie auf der Seite [Compiler Options (Compileroptionen)](https://www.typescriptlang.org/docs/handbook/compiler-options.html) im TypeScript-Handbuch.

### <a name="configure-source-maps-using-project-settings-typescript-project"></a>Konfigurieren von Quellzuordnungsdateien mithilfe von Projekteinstellungen (TypeScript-Projekt)

Sie können die Einstellungen für die Quellzuordnungen auch mithilfe von Projekteigenschaften konfigurieren, indem Sie erst mit der rechten Maustaste auf das Projekt und anschließend mit der linken auf **Projekt > Eigenschaften > TypeScript-Build > Debuggen** klicken.

Es sind die folgenden Projekteinstellungen verfügbar:

* **Quellzuordnungen generieren** (entspricht der Option **sourceMap** in *tsconfig.json*-Dateien): Generiert die entsprechende *MAP*-Datei.
* **Stammverzeichnis von Quellzuordnungen angeben** (entspricht der Option **mapRoot** in *tsconfig.json*-Dateien): Gibt anstelle der generierten Speicherorte den Speicherort an, an dem der Debugger die MAP-Dateien finden sollte. Verwenden Sie dieses Flag, wenn die *MAP*-Laufzeitdateien an einem anderen Ort als die JS-Dateien gespeichert werden müssen. Der angegebene Speicherort wird in die Quellzuordnung eingebettet, um den Debugger an den Ort weiterzuleiten, an dem sich die MAP-Dateien befinden.
* **Stammverzeichnis von TypeScript-Dateien angeben** (entspricht der Option **sourceRoot** in *tsconfig.json*-Dateien): Gibt anstelle von Quellspeicherorten den Speicherort an, an dem der Debugger die TypeScript-Dateien finden sollte. Verwenden Sie dieses Flag, wenn die Quelldateien zur Laufzeit an einem anderen Ort als zur Entwurfszeit gespeichert werden müssen. Der angegebene Speicherort wird in die Quellzuordnung eingebettet, um den Debugger an den Ort weiterzuleiten, an dem sich die Quelldateien befinden.

## <a name="debug-javascript-in-dynamic-files-using-razor-aspnet"></a>Debuggen von JavaScript in dynamischen Dateien mithilfe von Razor (ASP.NET)

::: moniker range=">=vs-2019"
Ab Visual Studio 2019 wird das Debuggen nur für Chrome und Microsoft Edge (Chromium) unterstützt.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio unterstützt das Debuggen nur für Chrome und Internet Explorer.
::: moniker-end

Jedoch können Breakpoints in Dateien, die mit einer Razor-Syntax erstellt wurden (CSHTML, VBHTML), nicht automatisch erreicht werden. Sie haben zwei Möglichkeiten, diese Art von Datei zu debuggen:

* **Platzieren Sie die `debugger;`-Anweisung an der Stelle, an der Sie den Code unterbrechen möchten:** Dadurch wird die Ausführung des dynamischen Skripts angehalten und der Debugvorgang sofort während der Erstellung gestartet.
* **Laden Sie die Seite, und öffnen Sie das dynamische Dokument in Visual Studio:** Sie müssen die dynamische Datei während des Debuggens öffnen, einen Breakpoint festlegen und anschließend die Seite aktualisieren, damit diese Methode funktioniert. Je nachdem, ob Sie Chrome oder Internet Explorer verwenden, finden Sie die Datei wie folgt:

   Bei Chrome: Navigieren Sie zu **Projektmappen-Explorer > Skriptdokumente > IhrSeitenname**.

    > [!NOTE]
    > Wenn Sie Google Chrome verwenden, wird Ihnen möglicherweise die Meldung **no source is available between \<script> tags** (Keine verfügbare Quelle zwischen <skript>-Tags) angezeigt. Das ist kein Grund zur Sorge, Sie können das Debuggen einfach fortsetzen.

   ::: moniker range=">=vs-2019"
   Verwenden Sie für Microsoft Edge (Chromium) dieselbe Vorgehensweise wie für Chrome.
   ::: moniker-end

   ::: moniker range="vs-2017"
   Bei Internet Explorer: Navigieren Sie zu **Projektmappen-Explorer > Skriptdokumente > Windows Internet Explorer > IhrSeitenname**.
   ::: moniker-end

Weitere Informationen finden Sie unter [Client-side debugging of ASP.NET projects in Google Chrome (Clientseitiges Debuggen von ASP.NET-Projekten in Google Chrome)](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/).
