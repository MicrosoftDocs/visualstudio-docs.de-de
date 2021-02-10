---
title: Erstellen einer Node.js- und Express-App
description: In diesem Tutorial erfahren Sie, wie Sie eine einfache Node.js-Anwendung mithilfe des Express-Webanwendungsframeworks in Visual Studio erstellen.
ms.date: 04/20/2020
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: d3b8413673318f2e0cd2a5f00cfb9d1d7f0b4097
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957529"
---
# <a name="tutorial-create-a-nodejs-and-express-app-in-visual-studio"></a>Tutorial: Erstellen einer Node.js- und Express-App in Visual Studio

In diesem Tutorial für die Visual Studio-Entwicklung erfahren Sie, wie Sie mithilfe von Node.js und Express eine einfache Node.js-Webanwendung erstellen, Code hinzufügen, einige Features der IDE kennenlernen und die App ausführen. 

::: moniker range="vs-2017"

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) kostenlos herunterladen.

::: moniker-end

::: moniker range="vs-2019"

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads) kostenlos herunterladen.

::: moniker-end

In diesem Tutorial lernen Sie, wie die folgenden Aufgaben ausgeführt werden:
> [!div class="checklist"]
> * Erstellen eines Node.js-Projekts
> * Hinzufügen von Code
> * Verwenden von IntelliSense zum Bearbeiten von Code
> * Ausführen der App
> * Erreichen eines Haltepunkts im Debugger

## <a name="before-you-begin"></a>Vorbereitungen

In den folgenden häufig gestellten Fragen werden einige wichtige Konzepte vorgestellt.

### <a name="what-is-nodejs"></a>Was ist Node.js?

Node.js ist eine serverseitige JavaScript-Runtime-Umgebung, die JavaScript auf dem Server ausführt.

### <a name="what-is-npm"></a>Was ist NPM?

NPM ist der Standardpaket-Manager für Node.js. Der Paket-Manager vereinfacht das Veröffentlichen und Freigeben von Quellcode von Node.js-Bibliotheken und ist zum Vereinfachen der Installation, Aktualisierung und Deinstallation von Bibliotheken konzipiert.

### <a name="what-is-express"></a>Was ist Express?

Express ist ein Webanwendungsframework, das für Node.js als Serverframework zum Erstellen von Webanwendungen verwendet wird. Mit Express können Sie aus verschiedenen Front-End-Frameworks auswählen, um eine Benutzeroberfläche zu erstellen, z. B. Pug (ehemals Jade). In diesem Tutorial wird Pug verwendet.

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

    Sofern nicht bereits geschehen, empfehlen wir Ihnen, die LTS-Version von der [Node.js](https://nodejs.org/en/download/)-Website zu installieren, um optimale Kompatibilität mit externen Frameworks und Bibliotheken zu gewährleisten. Node.js wurde für 32-Bit- und 64-Bit-Architekturen entwickelt. Die Node.js-Tools in Visual Studio, die in der Node.js-Workload enthalten sind, unterstützen beide Versionen. Es wird nur eine Version benötigt, und das Node.js-Installationsprogramm unterstützt zu jedem Zeitpunkt nur jeweils eine Installation.
    
    Im Allgemeinen erkennt Visual Studio die installierte Node.js-Runtime automatisch. Wird die installierte Runtime nicht erkannt, können Sie das Projekt so konfigurieren, dass auf der Eigenschaftenseite auf die installierte Runtime verwiesen wird (klicken Sie hierzu nach dem Erstellen des Projekts mit der rechten Maustaste auf den Projektknoten, wählen Sie **Eigenschaften** aus, und legen Sie den **Node.exe-Pfad** fest). Sie können eine globale Installation von Node.js verwenden oder in jedem Ihrer Node.js-Projekte den Pfad zu einem lokalen Interpreter angeben. 

    Dieses Tutorial wurde mit Node.js 8.10.0 getestet.

## <a name="create-a-new-nodejs-project"></a>Erstellen eines neuen Node.js-Projekts

Visual Studio verwaltet Dateien für eine einzelne Anwendung in einem *Projekt*. Das Projekt umfasst Quellcode, Ressourcen und Konfigurationsdateien.

In diesem Tutorial beginnen Sie mit einem einfachen Projekt, das Code für eine Node.js- und eine Express-App enthält.

1. Öffnen Sie Visual Studio.

1. Erstellen Sie ein neues Projekt.

    ::: moniker range=">=vs-2019"
    Drücken Sie **ESC**, um das Startfenster zu schließen. Geben Sie **STRG + Q** ein, um das Suchfeld zu öffnen, geben Sie **Node.js** ein, und wählen Sie dann **Neue einfache Azure Node.js Express 4-Anwendung erstellen** (JavaScript) aus. Wählen Sie im angezeigten Dialogfeld **Erstellen** aus.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Klicken Sie oben in der Menüleiste auf **Datei** > **Neu** > **Projekt**. Erweitern Sie im linken Bereich des Dialogfelds **Neues Projekt** den Eintrag **JavaScript**, und wählen Sie dann **Node.js** aus. Wählen Sie im mittleren Bereich die Option **Azure Node.js Express 4-Basisanwendung** und anschließend **OK** aus.
    ::: moniker-end
    Wenn die Projektvorlage **Azure Node.js Express 4-Basisanwendung** nicht angezeigt wird, müssen Sie die Workload **Node.js-Entwicklung** hinzufügen. Ausführliche Anweisungen dazu finden Sie in den [Voraussetzungen](#prerequisites).

    Visual Studio erstellt die neue Projektmappe und öffnet das Projekt im rechten Bereich. Die Projektdatei *app.js* wird im Editor (linker Bereich) geöffnet.

    ![Projektstruktur](../javascript/media/tutorial-project-structure.png)

    (1) Der **fett** hervorgehobene Name ist Ihr Projekt, dem Sie den Namen im Dialogfeld **Neues Projekt** gegeben haben. Im Dateisystem wird dieses Projekt durch eine *NJSPROJ*-Datei im Projektordner dargestellt. Klicken Sie mit der rechten Maustaste auf das Projekt, und wählen Sie **Eigenschaften** aus, um Eigenschaften und Umgebungsvariablen festzulegen, die dem Projekt zugeordnet sind. Roundtrips mit anderen Entwicklungstools sind möglich, da die Projektdatei keine benutzerdefinierte Änderungen an der Node.js-Projektquelle vornimmt.

    (2) Auf der oberen Ebene finden Sie eine Projektmappe, die standardmäßig denselben Namen hat wie Ihr Projekt. Eine Projektmappe, die auf dem Datenträger durch eine *SLN*-Datei dargestellt wird, ist ein Container für mindestens ein zugehöriges Projekt.

    (3) Der NPM-Knoten zeigt alle installierten NPM-Pakete an. Sie können mit der rechten Maustaste auf den NPM-Knoten klicken, um mithilfe eines Dialogfelds nach NPM-Paketen zu suchen und diese zu installieren.Sie können Pakete auch installieren oder aktualisieren, indem Sie die Einstellungen in *package.json* und die Optionen verwenden, die Sie über einen Rechtsklick auf den NPM-Knoten erreichen.

    (4) *package.json* ist eine Datei, die von NPM zum Verwalten von Paketabhängigkeiten und Paketversionen von lokal installierten Paketen verwendet wird. Weitere Informationen finden Sie unter [Verwalten von npm-Paketen](../javascript/npm-package-management.md).

    (5) Projektdateien wie *app.js* werden unter dem Projektknoten angezeigt. *app.js* ist die Projektstartdatei. Deshalb wird Sie **fett** angezeigt. Sie können die Startdatei festlegen, indem Sie mit der rechten Maustaste auf eine Datei im Projekt klicken und **Als Node.js-Startdatei festlegen** auswählen.

1. Öffnen Sie den **NPM**-Knoten, und stellen Sie sicher, dass alle erforderlichen NPM-Pakete vorhanden sind.

    Wenn Pakete fehlen (Ausrufezeichensymbol), klicken Sie mit der rechten Maustaste auf den **NPM**-Knoten, und wählen Sie **NPM-Pakete installieren** aus.

## <a name="add-some-code"></a>Hinzufügen von Code

Die Anwendung verwendet Pug für das Front-End-JavaScript-Framework. Pug verwendet einfachen Markupcode, der in HTML kompiliert wird. (Pug ist in *app.js* als Ansichts-Engine festgelegt. Der Code, der die Ansichts-Engine in *app.js* festlegt, ist `app.set('view engine', 'pug');`.)

1. Öffnen Sie im Projektmappen-Explorer (rechter Bereich) den Ordner „Views“ (Ansichten) und anschließend *index.pug*.

1. Ersetzen Sie den Inhalt durch folgenden Code.

    ```js
    extends layout

    block content
      h1= title
      p Welcome to #{title}
      script.
        var f1 = function() { document.getElementById('myImage').src='#{data.item1}' }
      script.
        var f2 = function() { document.getElementById('myImage').src='#{data.item2}' }
      script.
        var f3 = function() { document.getElementById('myImage').src='#{data.item3}' }

      button(onclick='f1()') One!
      button(onclick='f2()') Two!
      button(onclick='f3()') Three!
      p
      a: img(id='myImage' height='200' width='200' src='')
    ```

    Der vorhergehende Code wird verwendet, um eine HTML-Seite mit einem Titel und einer Begrüßungsnachricht dynamisch zu generieren. Die Seite enthält auch Code zum Anzeigen eines Images, das sich mit jedem Drücken einer Schaltfläche verändert.

1. Öffnen Sie im Ordner „routes“ die Datei *index.js*.

1. Fügen Sie direkt vor dem Aufruf von `router.get` den folgenden Code hinzu:

    ```js
    var getData = function () {
        var data = {
            'item1': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg',
            'item2': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg',
            'item3': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg'
        }
        return data;
    }
    ````

    Dieser Code erstellt ein Datenobjekt, das Sie an die dynamisch generierte HTML-Seite weitergeben.

1. Ersetzen Sie den Funktionsaufruf `router.get` durch den folgenden Code:

    ```js
    router.get('/', function (req, res) {
        res.render('index', { title: 'Express', "data" });
    });
    ```

    Der vorangehende Code legt die aktuelle Seite mithilfe des Routerobjekts „Express“ fest und rendert die Seite. Dabei werden Titel- und Datenobjekte an die Seite weitergegeben. Die Datei *index.pug* wird hier als Seite angegeben, die geladen wird, wenn *index.js* ausgeführt wird. *index.js* ist im *app.js*-Code als Standardroute konfiguriert (nicht angezeigt).

    Zur Veranschaulichung zahlreicher Features von Visual Studio wurde absichtlich ein Fehler in die Codezeile eingefügt, die `res.render` enthält. Sie müssen diesen Fehler beheben, bevor die App ausgeführt werden kann. Dies führen Sie im nächsten Abschnitt durch.

## <a name="use-intellisense"></a>Verwendung von IntelliSense

IntelliSense ist ein Visual Studio-Tool, das Ihnen beim Schreiben von Code hilft.

1. Gehen Sie in der Datei *index.js* zur Codezeile mit `res.render`.

1. Platzieren Sie Ihren Cursor hinter der `data`-Zeichenfolge, und geben Sie `: get` ein. IntelliSense zeigt Ihnen daraufhin die `getData`-Funktion an, die zuvor im Code definiert wurde. Klicken Sie auf `getData`.

    ![Verwendung von IntelliSense](../javascript/media/tutorial-nodejs-intellisense.png)

1. Fügen Sie die Klammern hinzu, um daraus einen Funktionsaufruf zu machen: `getData()`.

1. Wenn Sie das Komma (`,`) vor `"data"` entfernen, wird die Syntax im Ausdruck grün unterkringelt. Zeigen Sie auf die Syntaxhervorhebung.

    ![Syntaxfehler anzeigen](../javascript/media/tutorial-nodejs-syntax-checking.png)

    Die letzte Zeile dieser Meldung besagt, dass der JavaScript-Interpreter ein Komma erwartet (`,`).

1. Klicken Sie im unteren Bereich auf die Registerkarte **Fehlerliste**, und wählen Sie **Build und IntelliSense** für die Art der gemeldeten Fehler aus.

    Hier finden Sie die Warnung und die Beschreibung sowie den Dateinamen und die Zeilennummer.

    ![Fehlerliste anzeigen](../javascript/media/tutorial-nodejs-error-list.png)

1. Korrigieren Sie den Code, indem Sie das Komma (`,`) vor `"data"` hinzufügen.

    Die korrigierte Codezeile sollte wie folgt aussehen: `res.render('index', { title: 'Express', "data": getData() });`

## <a name="set-a-breakpoint"></a>Haltepunkt festlegen

Als Nächstes führen Sie die App mit dem angefügten Visual Studio-Debugger aus. Zuvor müssen Sie einen Breakpoint festlegen.

1. Klicken Sie in *index.js* im linken Bundsteg vor die folgende Codezeile, um einen Haltepunkt festzulegen:

    `res.render('index', { title: 'Express', "data": getData() });`

    Haltepunkte sind eine einfache und wichtige Funktion zum zuverlässigen Debuggen. Ein Haltepunkt gibt an, wo Visual Studio im ausgeführten Code angehalten werden soll. So können Sie einen Blick auf die Werte von Variablen oder das Speicherverhalten werfen oder überprüfen, ob eine Verzweigung im Code ausgeführt wird.

    ![Haltepunkt festlegen](../javascript/media/tutorial-nodejs-set-breakpoint.png)

## <a name="run-the-application"></a>Ausführen der Anwendung

1. Wählen Sie in der Debug-Symbolleiste das Debugziel aus, z. B. **Webserver (Google Chrome)** oder **Webserver (Microsoft Edge)** .

    ::: moniker range=">=vs-2019"
    ![Debugziel auswählen](../javascript/media/vs-2019/tutorial-nodejs-deploy-target.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Debugziel auswählen](../javascript/media/tutorial-nodejs-deploy-target.png)
    ::: moniker-end

    Wenn Chrome auf Ihrem Computer verfügbar ist, jedoch nicht als Option angezeigt wird, wählen Sie aus der Dropdownliste für das Debugziel **Browserauswahl** aus, und klicken Sie dann auf Chrome, um diesen Browser als Standardbrowser festzulegen (wählen Sie dazu **Als Standard festlegen** aus).

1. Drücken Sie **F5** (**Debuggen** > **Debuggen starten**), um die Anwendung auszuführen.

    Der Debugger hält an dem Haltepunkt an, den Sie festlegen. Jetzt können Sie den Status Ihrer App überprüfen.

1. Zeigen Sie auf `getData`, um die Eigenschaften in einem DataTip anzuzeigen.

    ![Variablen überprüfen](../javascript/media/tutorial-nodejs-inspect-variables.png)

1. Drücken Sie **F5** (**Debuggen** > **Fortsetzen**), um den Vorgang fortzusetzen.

    Die App wird daraufhin in einem Browser geöffnet.

    Im Browserfenster wird im Titel „Express“ und im ersten Absatz „Welcome to Express“ (Willkommen bei Express) angezeigt.

1. Klicken Sie auf die Schaltflächen, um verschiedene Bilder anzuzeigen.

    ![Im Browser ausgeführte App](../javascript/media/tutorial-nodejs-running-in-browser.png)

1. Schließen Sie den Webbrowser.

## <a name="optional-publish-to-azure-app-service"></a>(Optional) Veröffentlichen in Azure App Service

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und klicken Sie auf **Veröffentlichen**.

   ![Veröffentlichen in Azure App Service](../javascript/media/tutorial-nodejs-publish-to-azure.png)

1. Klicken Sie auf **Microsoft Azure App Service**.

    Im Dialogfeld **App-Dienst** können Sie sich in Ihrem Azure-Konto anmelden und eine Verbindung mit vorhandenen Azure-Abonnements herstellen.

1. Führen Sie die verbleibenden Schritte aus, um ein Abonnement auszuwählen. Wählen Sie dann eine Ressourcengruppe aus, oder erstellen Sie eine. Wiederholen Sie dieselben Aktionen für einen App Service-Plan, und führen Sie die Schritte aus, wenn Sie zur Veröffentlichung in Azure aufgefordert werden. Ausführlichere Anweisungen finden Sie unter [Publish to Azure website using web deploy (Veröffentlichen auf einer Azure-Website mit Web Deploy)](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy).

1. Im Fenster **Ausgabe** wird der Fortschritt bei der Bereitstellung in Azure angezeigt.

    Bei erfolgreicher Bereitstellung wird Ihre App in einem Browser geöffnet, der in Azure App Service ausgeführt wird. Klicken Sie auf eine Schaltfläche, um ein Bild anzuzeigen.

   ![Die in Azure App Service ausgeführte App](../javascript/media/tutorial-nodejs-running-in-azure.png)

Damit haben Sie das Tutorial erfolgreich abgeschlossen.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Deploy the app to Linux App Service (Bereitstellen der App für Linux App Service)](../javascript/publish-nodejs-app-azure.md)
