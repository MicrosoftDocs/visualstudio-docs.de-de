---
title: Erstellen einer ASP.NET Core-App mit TypeScript
description: In diesem Tutorial erstellen Sie eine ASP.NET Core-App mit ASP.NET Core und TypeScript.
ms.date: 03/16/2020
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: c28355e4097dc014f4757788f175ea80850a3f63
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960428"
---
# <a name="tutorial-create-an-aspnet-core-app-with-typescript-in-visual-studio"></a>Tutorial: Erstellen einer ASP.NET Core-App mit TypeScript in Visual Studio

In diesem Tutorial für die Visual Studio-Entwicklung mit ASP.NET Core und TypeScript erstellen Sie eine einfache Webanwendung, fügen etwas TypeScript-Code hinzu und führen dann die App aus.

::: moniker range="vs-2017"

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) kostenlos herunterladen.

::: moniker-end

::: moniker range="vs-2019"

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads) kostenlos herunterladen.

::: moniker-end

In diesem Tutorial lernen Sie, wie die folgenden Aufgaben ausgeführt werden:
> [!div class="checklist"]
> * Erstellen eines ASP.NET Core-Projekts
> * Hinzufügen des NuGet-Pakets für die TypeScript-Unterstützung
> * Hinzufügen von TypeScript-Code
> * Ausführen der App
> * Hinzufügen einer Drittanbieterbibliothek mit npm

## <a name="prerequisites"></a>Voraussetzungen

* Sie müssen Visual Studio und die Workload „ASP.NET-Webentwicklung“ installiert haben.

    ::: moniker range=">=vs-2019"
    Wenn Sie Visual Studio 2019 noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/) kostenlos herunterladen.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Wenn Sie Visual Studio 2017 noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/) kostenlos herunterladen.
    ::: moniker-end

    Wenn Sie die Workload installieren müssen, Visual Studio aber bereits besitzen, navigieren Sie zu **Tools** > **Tools und Features abrufen…** . Dadurch wird der Visual Studio-Installer geöffnet. Klicken Sie auf die Workload **ASP.NET und Webentwicklung**, und klicken Sie anschließend auf **Ändern**.

## <a name="create-a-new-aspnet-core-mvc-project"></a>Erstellen eines neuen ASP.NET Core MVC-Projekts

Visual Studio verwaltet Dateien für eine einzelne Anwendung in einem *Projekt*. Das Projekt umfasst Quellcode, Ressourcen und Konfigurationsdateien.

>[!NOTE]
> Eine Anleitung zum Beginnen mit einem leeren ASP.NET Core-Projekt und zum Hinzufügen eines TypeScript-Front-Ends finden Sie unter [ASP.NET Core mit TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html).

In diesem Tutorial beginnen Sie mit einem einfachen Projekt, das Code für eine ASP.NET Core MVC-App enthält.

1. Öffnen Sie Visual Studio.

1. Erstellen Sie ein neues Projekt.

    ::: moniker range=">=vs-2019"
    Wenn das Startfenster nicht geöffnet ist, klicken Sie auf **Datei** > **Startfenster**. Wählen Sie im Startfenster **Neues Projekt erstellen** aus. Wählen Sie **C#** in der Dropdownliste für die Programmiersprache aus. Geben Sie **ASP.NET** in das Suchfeld ein, und wählen Sie dann die Option **ASP.NET Core-Webanwendung** aus. Wählen Sie **Weiter** aus.

    Geben Sie einen Namen für das Projekt aus, und klicken Sie dann auf **Erstellen**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Klicken Sie oben in der Menüleiste auf **Datei** > **Neu** > **Projekt**. Erweitern Sie im linken Bereich des Dialogfelds **Neues Projekt** den Eintrag **Visual C#** , und wählen Sie **.NET Core** aus. Wählen Sie im mittleren Bereich **ASP.NET Core-Webanwendung – C#** und anschließend **OK** aus.
    ::: moniker-end
    Wenn Ihnen die Projektvorlage **ASP.NET Core-Webanwendung** fehlt, müssen Sie die Workload **ASP.NET und Webentwicklung** hinzufügen. Ausführliche Anweisungen dazu finden Sie in den [Voraussetzungen](#prerequisites).

1. Wählen Sie im angezeigten Dialogfeld die Option **Webanwendung (Model View Controller, MVC)** aus, und klicken Sie dann auf **Erstellen** (oder **OK**).

   ![Auswählen der MVC-Vorlage](../javascript/media/aspnet-core-ts-mvc-template.png)

    Visual Studio erstellt die neue Projektmappe und öffnet das Projekt im rechten Bereich.

## <a name="add-some-code"></a>Hinzufügen von Code

1. Im Projektmappen-Explorer (rechter Bereich) klicken Sie mit der rechten Maustaste auf den Projektknoten, und wählen Sie **NuGet-Pakete verwalten** aus. Suchen Sie auf der Registerkarte **Durchsuchen** nach **Microsoft.TypeScript.MSBuild**, und klicken Sie dann rechts auf **Installieren**, um das Paket zu installieren.

   ![Hinzufügen des NuGet-Pakets](../javascript/media/aspnet-core-ts-nuget.png)

   Visual Studio fügt das NuGet-Paket unter dem Knoten **Abhängigkeiten** im Projektmappen-Explorer hinzu.

1. Klicken Sie mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Hinzufügen > Neues Element** aus. Wählen Sie die **TypeScript JSON-Konfigurationsdatei** aus und klicken Sie dann auf **Hinzufügen**.

   Visual Studio fügt die Datei *tsconfig.json* zum Projektstamm hinzu. Sie können mit dieser Datei für den TypeScript-Compiler [Optionen konfigurieren](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).

1. Öffnen Sie *tsconfig.json* und ersetzen Sie den Standardcode durch den folgenden Code:

   ```json
   {
     "compileOnSave": true,
     "compilerOptions": {
       "noImplicitAny": false,
       "noEmitOnError": true,
       "removeComments": false,
       "sourceMap": true,
       "target": "es5",
       "outDir": "wwwroot/js"
     },
     "include": [
       "scripts/**/*"
     ]
   }
   ```

   Die Option *outDir* gibt den Ausgabeordner für die einfachen JavaScript-Dateien an, die vom TypeScript-Compiler transpiliert werden.

   Diese Konfiguration bietet eine grundlegende Einführung in die Verwendung von TypeScript. In anderen Szenarien, z. B. bei der Verwendung von [gulp oder webpack](https://www.typescriptlang.org/docs/handbook/asp-net-core.html), möchten Sie vielleicht je nach Tools und Konfigurationseinstellungen einen anderen Zwischenspeicherort für die transpilierten JavaScript-Dateien verwenden als *wwwwroot/js*.

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Projektknoten und wählen Sie **Hinzufügen > Neuer Ordner** aus. Verwenden Sie den Namen *scripts* für den neuen Ordner.

1. Klicken Sie mit der rechten Maustaste auf den Ordner *scripts* und wählen Sie **Hinzufügen > Neues Element** aus. Wählen Sie die **TypeScript-Datei** aus, geben Sie den Namen *app.ts* als Dateinamen ein und klicken Sie dann auf **Hinzufügen**.

   Visual Studio fügt *app.ts* zum Ordner *scripts* hinzu.

1. Öffnen Sie *app.ts* und fügen Sie den folgenden TypeScript-Code hinzu.

    ```ts
    function TSButton() {
       let name: string = "Fred";
       document.getElementById("ts-example").innerHTML = greeter(user);
    }

    class Student {
       fullName: string;
       constructor(public firstName: string, public middleInitial: string, public lastName: string) {
           this.fullName = firstName + " " + middleInitial + " " + lastName;
       }
    }

    interface Person {
       firstName: string;
       lastName: string;
    }

    function greeter(person: Person) {
       return "Hello, " + person.firstName + " " + person.lastName;
    }

    let user = new Student("Fred", "M.", "Smith");
    ```

    Visual Studio bietet die IntelliSense-Unterstützung für Ihren TypeScript-Code.

    Um dies zu testen, entfernen Sie `.lastName` aus der `greeter`-Funktion, geben dann den „.“ neu ein, und anschließend wird IntelliSense angezeigt.

    ![Anzeigen von IntelliSense](../javascript/media/aspnet-core-ts-intellisense.png)

    Wählen Sie `lastName` aus, um den Nachnamen wieder dem Code hinzuzufügen.

1. Öffnen Sie den Ordner *Views/Home* und dann die Datei *Index.cshtml*.

1. Fügen Sie den folgenden HTML-Code am Ende der Datei hinzu.

    ```html
    <div id="ts-example">
        <br />
        <button type="button" class="btn btn-primary btn-md" onclick="TSButton()">
            Click Me
        </button>
    </div>
    ```

1. Öffnen Sie den Ordner *Views/Shared*, und öffnen Sie dann die Datei *_Layout.cshtml*.

1. Fügen Sie die folgende Skriptreferenz vor dem Aufruf von `@RenderSection("Scripts", required: false)` hinzu:

    ```js
    <script src="~/js/app.js"></script>
    ````

## <a name="build-the-application"></a>Erstellen der Anwendung

1. Wählen Sie **Erstellen > Projektmappe erstellen** aus.

   Obwohl die App automatisch erstellt wird, wenn Sie sie ausführen, wollen wir einen Blick auf etwas werfen, das während des Buildvorgangs geschieht.

1. Öffnen Sie den Ordner *wwwwroot/js*. Sie finden zwei neue Dateien: *app.js* und die Quellzuordnungsdatei *app.js.map*. Diese Dateien werden vom TypeScript-Compiler generiert.

   Für die Fehlersuche werden Quellzuordnungsdateien benötigt.

## <a name="run-the-application"></a>Ausführen der Anwendung

1. Drücken Sie **F5** (**Debuggen** > **Debuggen starten**), um die Anwendung auszuführen.

    Die App wird daraufhin in einem Browser geöffnet.

    Im Browserfenster wird die Überschrift **Willkommen** und die Schaltfläche **Hier klicken** angezeigt.

    ![ASP.NET Core mit TypeScript](../javascript/media/aspnet-core-ts-running-app.png)

1. Klicken Sie auf die Schaltfläche, um die von uns in der TypeScript-Datei angegebene Meldung anzuzeigen.

## <a name="debug-the-application"></a>Debuggen der Anwendung

1. Setzen Sie einen Haltepunkt in der Funktion `greeter` in `app.ts`, indem Sie im Code-Editor auf den linken Rand klicken.

    ![Haltepunkt festlegen](../javascript/media/aspnet-core-ts-set-breakpoint.png)

1. Drücken Sie **F5**, um die Anwendung auszuführen.

   Möglicherweise müssen Sie auf eine Meldung reagieren, um das Skriptdebuggen zu aktivieren.

   Die Anwendung hält am Haltepunkt an. Jetzt können Sie Variablen untersuchen und Debugger-Features verwenden.

## <a name="add-typescript-support-for-a-third-party-library"></a>Hinzufügen der TypeScript-Unterstützung für eine Drittanbieterbibliothek

1. Führen Sie die Anweisungen in der [npm-Paketverwaltung](../javascript/npm-package-management.md#aspnet-core-projects) aus, um eine `package.json`-Datei zu Ihrem Projekt hinzuzufügen. Dadurch wird die npm-Unterstützung zu Ihrem Projekt hinzugefügt.

   >[!NOTE]
   > Für ASP.NET Core-Projekte können Sie auf den [Bibliotheks-Manager](https://docs.microsoft.com/aspnet/core/client-side/libman/?view=aspnetcore-3.1&preserve-view=true) oder YARN anstelle von npm verwenden, um clientseitige JavaScript- und CSS-Dateien zu installieren.

1. In diesem Beispiel fügen Sie eine TypeScript-Definitionsdatei für jQuery zu Ihrem Projekt hinzu. Fügen Sie Folgendes in Ihre Datei *package.json* ein.

   ```json
   "devDependencies": {
      "@types/jquery": "3.3.33"
   }
   ```

   Dadurch wird die TypeScript-Unterstützung für jQuery hinzugefügt. Die jQuery-Bibliothek selbst ist bereit in der MVC-Projektvorlage enthalten (diese finden Sie im Projektmappen-Explorer unter „wwwroot/lib“). Wenn Sie eine andere Vorlage verwenden, müssen Sie möglicherweise auch das npm-Paket für jQuery einfügen.

1. Wenn das Paket nicht im Projektmappen-Explorer installiert ist, klicken Sie mit der rechten Maustaste auf den npm-Knoten, und wählen Sie dann **Pakete wiederherstellen** aus.

   >[!NOTE]
   > In einigen Szenarios gibt der Projektmappen-Explorer möglicherweise an, dass ein npm-Paket nicht mit der Datei *package.json* synchron ist. Dies liegt an einem bekannten Fehler, der [hier](https://github.com/aspnet/Tooling/issues/479) beschrieben wird. Beispielsweise wird das Paket möglicherweise als nicht installiert angezeigt, obwohl es installiert ist. In den meisten Fällen können Sie den Projektmappen-Explorer aktualisieren, indem Sie die Datei *package.json* löschen, Visual Studio neu starten und die Datei *package.json* wie zuvor im Artikel beschrieben wieder hinzufügen.

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Skriptordner, und wählen Sie dann **Hinzufügen** > **Neues Element** aus.

1. Wählen Sie **TypeScript-Datei** aus, geben Sie *library.ts* ein, und klicken Sie dann auf **Hinzufügen**.

1. Fügen Sie den folgenden Code in die Datei *library.ts* ein:

   ```ts
   var jqtest = {
      showMsg: function (): void {
         let v: any = jQuery.fn.jquery.toString();
         let content: any = $("#ts-example-2")[0].innerHTML;
         alert(content.toString());
         $("#ts-example-2")[0].innerHTML = content + " " + v + "!!";
      }
   };

   jqtest.showMsg();
   ```

   Der Einfachheit halber zeigt dieser Code eine Nachricht mithilfe von jQuery sowie eine Warnung an.

   Da Sie nun TypeScript-Typdefinitionen für jQuery hinzugefügt haben, erhalten Sie IntelliSense-Unterstützung für jQuery-Objekte, wenn Sie wie im folgenden Bild gezeigt nach einem jQuery-Objekt „.“ eingeben.

   ![IntelliSense für jQuery](../javascript/media/aspnet-core-ts-jquery-intellisense.png)

1. Fügen Sie `library.js` zu den Skriptverweisen in der Datei „_Layout.cshtml“ hinzu.

   ```html
   <script src="~/js/app.js"></script>
   <script src="~/js/library.js"></script>
   ```

1. Fügen Sie den folgenden HTML-Code am Ende der Datei „Index.cshtml“ hinzu.

   ```html
   <div>
      <p id="ts-example-2">jQuery version is:</p>
   </div>
   ```

1. Drücken Sie **F5** (**Debuggen** > **Debuggen starten**), um die Anwendung auszuführen.

    Daraufhin wird die App im Browser geöffnet.

    Klicken Sie in der Warnung auf **OK**, damit die Seite aktualisiert wird und **jQuery version is 3.3.1!!** anzeigt.

    ![jQuery-Beispiel](../javascript/media/aspnet-core-ts-jquery-example.png)

## <a name="next-steps"></a>Nächste Schritte

Möglicherweise möchten Sie weitere Details über die Verwendung von TypeScript mit ASP.NET Core erhalten.

> [!div class="nextstepaction"]
> [ASP.NET Core und TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)
