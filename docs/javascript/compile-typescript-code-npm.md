---
title: Erstellen und Kompilieren von TypeScript-Code mithilfe von npm
description: Hier erfahren Sie, wie Sie Ihren Visual Studio-Projekten mithilfe von Node Package Manager (npm) Typescript-Unterstützung hinzufügen.
ms.date: 7/23/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 966b08a912a7bab59998daf39590a6fd46920eb7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969528"
---
# <a name="compile-typescript-code-nodejs"></a>Kompilieren von TypeScript-Code (Node.js)

Sie können TypeScript-Unterstützung mit dem TypeScript SDK, das standardmäßig im Visual Studio-Installationsprogramm enthalten ist, oder mit npm zu Ihren Projekten hinzufügen. Bei Projekten, die in Visual Studio 2019 entwickelt wurden, empfehlen wir, das TypeScript-npm-Paket zu verwenden, um eine bessere Portabilität über verschiedene Plattformen und Umgebungen hinweg zu erzielen.

Bei ASP.NET Core-Projekten wird stattdessen die Verwendung des [NuGet-Pakets](../javascript/compile-typescript-code-nuget.md) empfohlen.

## <a name="add-typescript-support-using-npm"></a>Hinzufügen von TypeScript-Unterstützung mit npm

Das [TypeScript-npm-Paket](https://www.npmjs.com/package/typescript) fügt TypeScript-Unterstützung hinzu. Wenn das npm-Paket für TypeScript 2.1 oder höher in Ihrem Projekt installiert ist, wird die entsprechende Version des TypeScript-Sprachdienstes in den Editor geladen.

1. [Befolgen Sie diese Anweisungen](../ide/quickstart-nodejs.md?toc=%252fvisualstudio%252fjavascript%252ftoc.json), um die Node.js-Entwicklungsworkload und die Node.js-Runtime zu installieren.

   Um eine möglichst einfache Integration in Visual Studio zu erzielen, erstellen Sie Ihr Projekt mit einer der Node.js-TypeScript-Vorlagen, z. B. mit der Vorlage „Blank Node.js Web Application“. Andernfalls können Sie auch jede in Visual Studio enthaltene Node.js-JavaScript-Vorlage verwenden und die Anweisungen hier befolgen, oder ein [Open Folder](../javascript/develop-javascript-code-without-solutions-projects.md)-Projekt verwenden.

1. Wenn Ihr Projekt das [TypeScript-npm-Paket](https://www.npmjs.com/package/typescript) nicht bereits enthält, installieren Sie es.

   Öffnen Sie im Projektmappen-Explorer im Bereich auf der rechten Seite die Datei *package.json* im Stammverzeichnis. Die aufgeführten Pakete entsprechen Paketen unter dem npm-Knoten im Projektmappen-Explorer. Weitere Informationen finden Sie unter [Verwalten von npm-Paketen](../javascript/npm-package-management.md).

   Bei einem Node.js-Projekt können Sie das TypeScript-npm-Paket über die Befehlszeile oder die IDE installieren. Klicken Sie zur Installation über die IDE im Projektmappen-Explorer mit der rechten Maustaste auf den npm-Knoten, wählen Sie **Neues npm-Paket installieren** aus, suchen Sie nach **TypeScript**, und installieren Sie das Paket.

   Überprüfen Sie die Option **npm** im Fenster **Ausgabe**, um den Fortschritt bei der Paketinstallation anzuzeigen. Das installierte Paket wird im Projektmappen-Explorer unter dem Knoten **npm** angezeigt.

1. Wenn Ihr Projekt noch keine *.tsconfig*-Datei enthält, fügen Sie Ihrem Projektstamm eine solche Datei hinzu. Um die Datei hinzuzufügen, klicken Sie mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Hinzufügen > Neues Element** aus. Wählen Sie die **TypeScript JSON-Konfigurationsdatei** aus und klicken Sie dann auf **Hinzufügen**.

   Visual Studio fügt die Datei *tsconfig.json* zum Projektstamm hinzu. Sie können mit dieser Datei für den TypeScript-Compiler [Optionen konfigurieren](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).

1. Öffnen Sie die Datei *tsconfig.json*, und legen Sie die von Ihnen gewünschten Compileroptionen fest.

   Im folgenden Beispiel wird eine einfache *tsconfig.json*-Datei dargestellt.

   ```json
   {
     "compilerOptions": {
       "noImplicitAny": false,
       "noEmitOnError": true,
       "removeComments": false,
       "sourceMap": true,
       "target": "es5",
       "outDir": "dist"
     },
     "include": [
       "scripts/**/*"
     ]
   }
   ```

   In diesem Beispiel:
   - *include* informiert den Compiler darüber, wo sich die TypeScript-Dateien (*.ts) befinden.
   - Die Option *outDir* gibt den Ausgabeordner für die einfachen JavaScript-Dateien an, die vom TypeScript-Compiler transpiliert werden.
   - *sourceMap* gibt an, ob der Compiler *sourceMap*-Dateien generiert.

   Die oben genannte Konfiguration bietet nur eine grundlegende Einführung in die Konfiguration von TypeScript. Informationen zu weiteren Optionen finden Sie unter [tsconfig.json](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).

## <a name="build-the-application"></a>Erstellen der Anwendung

1. Fügen Sie TypeScript-Dateien ( *.ts*) oder TypeScript JSX-Dateien ( *.tsx*) zu Ihrem Projekt hinzu, und fügen Sie dann TypeScript-Code hinzu. Hier sehen Sie ein einfaches Beispiel für TypeScript:

   ```typescript
   let message: string = 'Hello World';
   console.log(message);
   ```

1. Fügen Sie in der *package.json* mithilfe der folgenden Skripts Unterstützung für die Visual Studio-Befehle zum Kompilieren und Bereinigen hinzu.

   ```json
   "scripts": {
     "build": "tsc --build",
     "clean": "tsc --build --clean"
   },
   ```

   Wenn Sie ein Drittanbietertool wie webpack zum Kompilieren verwenden müssen, können Sie Ihrer *package.json*-Datei ein befehlszeilenbasiertes Buildskript hinzufügen:

   ```json
   "scripts": {
      "build": "webpack-cli app.tsx --config webpack-config.js"
   }
   ```

   Ein Beispiel für die Verwendung von webpack mit React und eine webpack-Konfigurationsdatei finden Sie unter [Erstellen einer Web-App mit Node.js und React](../javascript/tutorial-nodejs-with-react-and-jsx.md).

   Ein Beispiel für die Verwendung von Vue.js mit TypeScript finden Sie unter [Erstellen einer Vue.js-Anwendung](/javascript/create-application-with-vuejs).

1. Wenn Sie Optionen wie die Startseite, den Pfad zur Node.js-Runtime, den Anwendungsport oder Laufzeitargumente konfigurieren müssen, klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Eigenschaften** aus.

   >[!NOTE]
   > Beim Konfigurieren von Drittanbietertools verwenden Node.js-Projekte nicht die unter **Tools** > **Optionen** > **Projekte und Projektmappen** > **Webpaketverwaltung** > **Externe Webtools** konfigurierten Pfade. Diese Einstellungen werden für andere Projekttypen verwendet.

1. Wählen Sie **Erstellen > Projektmappe erstellen** aus.

   Obwohl die App bei der Ausführung automatisch kompiliert wird, sollten Sie sich etwas ansehen, das während des Buildvorgangs geschieht:

   Wenn Sie Quellzuordnungsdateien generiert haben, öffnen Sie den in der *outDir*-Option angegebenen Ordner. Dort finden Sie die generierten \*.js-Dateien sowie die generierten \*js.map-Dateien.

   Quellzuordnungsdateien werden zum [Debuggen](../javascript/debug-nodejs.md) benötigt.

### <a name="run-the-application"></a>Ausführen der Anwendung

Eine Anleitung zum Ausführen der App nach ihrer Kompilierung finden Sie unter [Schnellstart: Erstellen einer ersten Node.js-App mit Visual Studio](../ide/quickstart-nodejs.md?toc=%252fvisualstudio%252fjavascript%252ftoc.json#run-the-application).

## <a name="automate-build-tasks"></a>Automatisieren von Buildaufgaben

Sie können den Taskausführungs-Explorer in Visual Studio verwenden, um Aufgaben für Drittanbietertools wie npm und webpack zu automatisieren.

- [NPM Task Runner](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.NPMTaskRunner) – fügt Unterstützung für in *package.json* definierte npm-Skripts hinzu. Unterstützt Yarn.
- [Webpack Task Runner](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.WebPackTaskRunner) – fügt Unterstützung für webpack hinzu.