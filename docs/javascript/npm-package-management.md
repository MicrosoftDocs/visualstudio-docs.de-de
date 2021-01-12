---
title: Verwalten von npm-Paketen
description: Dank Visual Studio können Sie Pakete mit dem Node.js-Paket-Manager (NPM) verwalten.
ms.custom: seodec18
ms.date: 04/16/2020
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: d2c7ec425767e432105bfcec493599197e2fd5ec
ms.sourcegitcommit: 105e7b5a486262bc92939980383ceee068098a11
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/30/2020
ms.locfileid: "97815684"
---
# <a name="manage-npm-packages-in-visual-studio"></a>Verwalten von NPM-Paketen in Visual Studio

Mit NPM können Sie Pakete zur Verwendung in Ihren Node.js-Anwendungen installieren und verwalten. Visual Studio erleichtert die Interaktion mit NPM sowie die Ausführung von NPM-Befehlen über die Benutzeroberfläche oder direkt. Wenn Sie mit NPM nicht vertraut sind und weitere Informationen benötigen, wechseln Sie zur [NPM-Dokumentation](https://docs.npmjs.com/).

Die Visual Studio-Integration mit npm variiert je nach Projekttyp.
* [Node.js](#nodejs-projects)
* [ASP.NET Core](#aspnet-core-projects)
* [Öffnen von Ordnern (Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md)

> [!Important]
> Von npm wird erwartet, dass der Ordner *node_modules* und *package.json* im Projektstamm vorhanden sind. Wenn sich die Ordnerstruktur Ihrer App unterscheidet, sollten Sie Ihre Ordnerstruktur anpassen, wenn Sie npm-Pakete mit Visual Studio verwalten.

## <a name="nodejs-projects"></a>Node.js-Projekte

Bei Node.js-Projekten können Sie folgende Aufgaben ausführen:
* [Installieren von Paketen über den Projektmappen-Explorer](#npmInstallWindow)
* [Verwalten von installierten Paketen über den Projektmappen-Explorer](#solutionExplorer)
* [Verwenden des Befehls `.npm` im interaktiven Node.js-Fenster](#interactive)

Diese Features arbeiten zusammen und werden mit dem Projektsystem und der Datei *package.json* im Projekt synchronisiert.

### <a name="prerequisites"></a>Voraussetzungen

Sie benötigen die Workload **Node.js-Entwicklung** und die Node.js-Runtime, um npm-Unterstützung für Ihr Projekt hinzuzufügen. Die einzelnen Schritte sind unter [Erstellen eines Node.js-Projekts](../ide/quickstart-nodejs.md?toc=%252fvisualstudio%252fjavascript%252ftoc.json) beschrieben.

> [!NOTE]
> Verwenden Sie für vorhandene Node.js-Projekte die Projektmappenvorlage **Aus vorhandenem Node.js-Code** oder den Projekttyp [Ordner öffnen (Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md), um npm in Ihrem Projekt zu aktivieren.

### <a name="install-packages-from-solution-explorer-nodejs"></a><a name="npmInstallWindow"></a>Installieren von Paketen über den Projektmappen-Explorer (Node.js)

Die npm-Pakete lassen sich bei Node.js-Projekten am einfachsten über das npm-Paketinstallationsfenster installieren. Um dieses Fenster aufzurufen, klicken Sie im Projekt mit der rechten Maustaste auf den Knoten **NPM**. Wählen Sie anschließend die Option **Neue NPM-Pakete installieren** aus.

:::image type="content" source="../javascript/media/solution-explorer-install-package.png" alt-text="Installieren eines neuen npm-Pakets über den Projektmappen-Explorer" border="true":::

In diesem Fenster können Sie nach einem Paket suchen sowie Optionen angeben und installieren.

![Screenshot: Dialogfeld „Neue NPM-Pakete installieren“ mit ausgewähltem Paket „azure 2.2.1-preview“ und angezeigten Details und Optionen zum Paket](../javascript/media/search-package.png)

* **Abhängigkeitstyp**: Wählen Sie zwischen den Paketen **Standard**, **Entwicklung** und **Optional**. „Standard“ gibt an, dass es sich bei dem Pakte um eine Laufzeitabhängigkeit handelt, während „Entwicklung“ angibt, dass das Paket nur während der Entwicklung benötigt wird.
* **Zu "package.json" hinzufügen**: Empfohlen. Diese konfigurierbare Option ist veraltet.
* **Ausgewählte Version**: Wählen Sie die Version des Pakets aus, die Sie installieren möchten.
* **Weitere NPM-Argumente**: Geben Sie weitere NPM-Standardargumente an. Sie können beispielsweise einen Versionswert wie `@~0.8` eingeben, um eine bestimmte Version zu installieren, die in der Versionsliste nicht verfügbar ist.

Der Fortschritt der Installation wird in der **npm**-Ausgabe im Fenster **Ausgabe** angezeigt. Dieser Vorgang kann einige Zeit dauern.

![npm-Ausgabe](../javascript/media/npm-output.png)

> [!TIP]
> Sie können nach bereichsbezogenen Paketen suchen, indem Sie die Suchabfrage mit dem für Sie interessanten Bereich voranstellen. Geben Sie beispielsweise `@types/mocha` ein, um nach TypeScript-Definitionsdateien für Mocha zu suchen. Wenn Sie Typdefinitionen für TypeScript installieren, können Sie die TypeScript-Version angeben, die Sie als Ziel verwenden. Fügen Sie hierzu `@ts2.6` im npm-Argumentfeld hinzu.

### <a name="manage-installed-packages-in-solution-explorer-nodejs"></a><a name="solutionExplorer"></a>Verwalten von installierten Paketen über den Projektmappen-Explorer (Node.js)

NPM-Pakete werden im Projektmappen-Explorer angezeigt. Die Einträge unter dem Knoten **NPM** stellt die Abhängigkeiten in der Datei *package.json* dar.

![Screenshot: NPM-Knoten im Projektmappen-Explorer mit Installationsstatus der NPM-Pakete](../javascript/media/solution-explorer-status.png)

### <a name="package-status"></a>Paketstatus

* ![Installiertes Paket](../javascript/media/installed-npm.png) - In „package.json“ installiert und aufgeführt
* ![Nicht relevantes Paket](../javascript/media/extraneous-npm.png): Installiert, aber in „package.json“ nicht explizit aufgeführt
* ![Fehlendes Paket](../javascript/media/missing-npm.png) - Nicht installiert, aber in „package.json“ aufgeführt

::: moniker range=">=vs-2019"
Klicken Sie mit der rechten Maustaste auf den Konten **npm**, um eine der folgenden Aktionen durchzuführen:

* **Neue NPM-Pakete installieren**: Öffnet die Benutzeroberfläche für die Installation neuer Pakete.
* **NPM-Pakete installieren**: Führt den npm-Installationsbefehl aus, um alle in *package.json* aufgeführten Pakete zu installieren. (Führt `npm install` aus.)
* **NPM-Pakete aktualisieren:** Hiermit werden Pakete in Übereinstimmung mit dem in *package.json* angegebenen Bereich der semantischen Versionierung (SemVer) auf die aktuelle Version aktualisiert. (Führt `npm update --save` aus.). SemVer-Bereiche werden in der Regel mit „~“ oder „^“ angegeben. Weitere Informationen finden Sie unter [package.json-Konfiguration](../javascript/configure-packages-with-package-json.md).

Klicken Sie mit der rechten Maustaste auf einen Paketknoten, um eine der folgenden Aktionen durchzuführen:

* **NPM-Pakete installieren**: Führt den npm-Installationsbefehl aus, um die in *package.json* aufgeführten Paketversionen zu installieren. (Führt `npm install` aus.)
* **NPM-Pakete aktualisieren:** Hiermit wird das Paket in Übereinstimmung mit dem in *package.json* angegebenen SemVer-Bereich auf die aktuelle Version aktualisiert. (Führt `npm update --save` aus.) SemVer-Bereiche werden in der Regel mit „~“ oder „^“ angegeben.
* **NPM-Pakete deinstallieren**: Deinstalliert die Pakete und entfernt sie aus *package.json* (Führt `npm uninstall --save` aus.)
::: moniker-end
::: moniker range="vs-2017"
Klicken Sie mit der rechten Maustaste auf einen Paketknoten oder auf den Konten **NPM**, um eine der folgenden Aktionen durchzuführen:
* **Fehlende Pakete installieren**, die in *package.json* aufgeführt sind
* **NPM-Pakete aktualisieren** (auf die neueste Version)
* **Paket deinstallieren** und in *package.json* entfernen
::: moniker-end

>[!NOTE]
> Hilfe bei Problemen mit npm-Paketen finden Sie unter [Troubleshooting](#troubleshooting-npm-packages).

### <a name="use-the-npm-command-in-the-nodejs-interactive-window-nodejs"></a><a name="interactive"></a>Verwenden des Befehls „.npm“ im interaktiven Node.js-Fenster (Node.js)

Zum Ausführen von NPM-Befehlen können Sie auch den Befehl `.npm` im interaktiven Node.js-Fenster verwenden. Klicken Sie zum Öffnen des Fensters mit der rechten Maustaste im Projektmappen-Explorer auf das Projekt, und wählen Sie **Interaktives Node.js-Fenster** aus.

In diesem Fenster können Sie Befehle wie die folgenden zum Installieren eines Pakets verwenden:

`.npm install azure@4.2.3`

 > [!Tip]
 > NPM wird standardmäßig im Basisverzeichnis Ihres Projekts ausgeführt. Wenn sich in Ihrer Projektmappe mehrere Projekte befinden, geben Sie den Namen oder den Pfad des Projekts in Klammern an.
 > `.npm [MyProjectNameOrPath] install azure@4.2.3`

 > [!Tip]
 > Wenn in Ihrem Projekt die Datei „package.json“ nicht enthalten ist, verwenden Sie `.npm init -y`, um eine neue „package.json“-Datei mit Standardeinträgen zu erstellen.

 ## <a name="aspnet-core-projects"></a>ASP.NET Core-Projekte

Für Projekte wie ASP.NET Core-Projekte können Sie npm-Unterstützung in Ihr Projekt integrieren und npm zum Installieren von Paketen verwenden.
* [Hinzufügen der npm-Unterstützung zu einem Projekt](#npmAdd)
* [Installieren von Paketen mit „package.json“](#npmInstallPackage)

>[!NOTE]
> Für ASP.NET Core-Projekte können Sie auf den [Bibliotheks-Manager](/aspnet/core/client-side/libman/?view=aspnetcore-3.1&preserve-view=true) oder YARN anstelle von npm verwenden, um clientseitige JavaScript- und CSS-Dateien zu installieren.

### <a name="add-npm-support-to-a-project-aspnet-core"></a><a name="npmAdd"></a>Hinzufügen der npm-Unterstützung zu einem Projekt (ASP.NET Core)

Wenn Ihr Projekt noch keine *package.json*-Datei enthält, können Sie diese zu Ihrem Projekt hinzufügen, um die npm-Unterstützung zu aktivieren. Fügen Sie dazu eine *package.json*-Datei zum Projekt hinzu.

1. Sofern Node.js noch nicht installiert ist, sollten Sie die LTS-Version von der [Node.js](https://nodejs.org/en/download/)-Website installieren, um optimale Kompatibilität mit externen Frameworks und Bibliotheken zu gewährleisten.

   Node.js ist für npm erforderlich.

1. Klicken Sie zum Hinzufügen der Datei *package.json* mit der rechten Maustaste im Projektmappen-Explorer auf das Projekt, und wählen Sie dann **Hinzufügen** > **Neues Element** aus. Wählen Sie dann die **npm-Konfigurationsdatei** aus, bestätigen Sie den Standardnamen, und klicken Sie dann auf **Hinzufügen**.

   ![Hinzufügen der Datei „package.json“ zu Ihrem Projekt](../javascript/media/npm-add-package-json.png)

   Wenn die npm-Konfigurationsdatei nicht aufgeführt wird, sind die Node.js-Entwicklungstools nicht installiert. Sie können die Workload **Node.js-Entwicklung** über den Visual Studio-Installer hinzufügen. Wiederholen Sie anschließend den vorherigen Schritt.

1. Fügen Sie mindestens ein npm-Paket in den `dependencies`- oder `devDependencies`-Abschnitt von *package.json* ein. Beispielsweise können Sie Folgendes zur Datei hinzufügen:

   ```json
   "devDependencies": {
      "gulp": "4.0.2",
      "@types/jquery": "3.3.33"
   }
   ```

Wenn Sie die Datei speichern, fügt Visual Studio das Paket unter dem Knoten **Dependencies/npm** (Abhängigkeiten/npm) im Projektmappen-Explorer hinzu. Wenn der Knoten nicht angezeigt wird, klicken Sie mit der rechten Maustaste auf die Datei **package.json**, und wählen Sie dann **Pakete wiederherstellen** aus.

>[!NOTE]
> In einigen Szenarien wird im Projektmappen-Explorer möglicherweise nicht der richtige Status für installierte npm-Pakete angezeigt. Weitere Informationen finden Sie unter [Problembehandlung](#troubleshooting-npm-packages).

### <a name="install-packages-using-packagejson-aspnet-core"></a><a name="npmInstallPackage"></a>Installieren von Paketen mit „package.json“ (ASP.NET Core)

Bei Projekten, in die npm integriert ist, können Sie npm-Pakete mit `package.json` konfigurieren. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den npm-Knoten, und wählen Sie dann **package.json öffnen** aus.

![Screenshot: Projektmappen-Explorer mit ausgewähltem NPM-Knoten mit einem geöffneten Kontextmenü und der Option „Open package.json“ (package.json öffnen) ausgewählt](../javascript/media/npm-add-package.png)

IntelliSense in *package.json* unterstützt Sie bei der Auswahl einer spezifischen Version eines npm-Pakets.

:::image type="content" source="../javascript/media/npm-add-package-intellisense.png" alt-text="Auswahl der npm-Paketversion" border="true":::

Wenn Sie die Datei speichern, fügt Visual Studio das Paket unter dem Knoten **Dependencies/npm** (Abhängigkeiten/npm) im Projektmappen-Explorer hinzu. Wenn der Knoten nicht angezeigt wird, klicken Sie mit der rechten Maustaste auf die Datei **package.json**, und wählen Sie dann **Pakete wiederherstellen** aus.

Die Installation eines Pakets kann mehrere Minuten dauern. Sie können den Fortschritt der Paketinstallation überprüfen, indem Sie zur **npm-Ausgabe** im Fenster **Ausgabe** wechseln.

![npm-Ausgabe](../javascript/media/npm-output.png)

## <a name="troubleshooting-npm-packages"></a>Problembehandlung bei npm-Paketen

* Node.js ist für npm erforderlich. Sofern Node.js noch nicht installiert ist, sollten Sie die LTS-Version von der [Node.js](https://nodejs.org/en/download/)-Website installieren, um optimale Kompatibilität mit externen Frameworks und Bibliotheken zu gewährleisten.

* Für npm-Unterstützung muss bei Node.js-Projekten die Workload **Node.js-Entwicklung** installiert sein.

* In einigen Szenarien wird im Projektmappen-Explorer möglicherweise nicht der richtige Status für installierte npm-Pakete angezeigt. Der Grund dafür ist ein bekanntes Problem, das [hier](https://github.com/aspnet/Tooling/issues/479) beschrieben ist. Beispielsweise wird das Paket möglicherweise als nicht installiert angezeigt, obwohl es installiert ist. In den meisten Fällen können Sie den Projektmappen-Explorer aktualisieren, indem Sie die Datei *package.json* löschen, Visual Studio neu starten und die Datei *package.json* wie zuvor im Artikel beschrieben wieder hinzufügen. Bei der Installation von Paketen können Sie den Installationsstatus alternativ im npm-Ausgabefenster überprüfen.

* Wenn beim Erstellen Ihrer App oder beim Transpilieren von TypeScript-Code Fehler auftreten, könnten Inkompatibilitäten bei npm-Paketen eine mögliche Ursache sein. Um mögliche Fehler zu ermitteln, sollten Sie bei der Installation der Pakete das npm-Ausgabefenster überprüfen (wie zuvor in diesem Artikel beschrieben). Wenn z. B. eine oder mehrere npm-Paketversionen als veraltet markiert wurden und dadurch einen Fehler verursachen, müssen Sie möglicherweise zum Beheben der Fehler eine neuere Version installieren. Informationen zur Verwendung von *package.json* zum Steuern von npm-Paketversionen finden Sie unter [package.json-Konfiguration](../javascript/configure-packages-with-package-json.md).
