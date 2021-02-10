---
title: Erstellen und Kompilieren von TypeScript-Code mithilfe von NuGet
description: Hier erfahren Sie, wie Sie Ihren Visual Studio-Projekten mithilfe des NuGet-Pakets Typescript-Unterstützung hinzufügen.
ms.date: 7/23/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 375f56d8a367c6d5cb090e10069b714b5a3843f2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969541"
---
# <a name="compile-typescript-code-aspnet-core"></a>Kompilieren von TypeScript-Code (ASP.NET Core)

Sie können TypeScript-Unterstützung mit dem TypeScript SDK, das standardmäßig im Visual Studio-Installationsprogramm enthalten ist, oder mit dem NuGet-Paket zu Ihren Projekten hinzufügen. Bei Projekten, die in Visual Studio 2019 entwickelt wurden, empfehlen wir, das TypeScript-NuGet-Paket zu verwenden, um eine bessere Portabilität über verschiedene Plattformen und Umgebungen hinweg zu erzielen.

Bei ASP.NET Core-Projekten ist ein gängiger Anwendungsfall für das NuGet-Paket die Kompilierung von TypeScript über die .NET Core-CLI. Das NuGet-Paket ist die einzige Möglichkeit zum Aktivieren der TypeScript-Kompilierung mit .NET Core-CLI-Befehlen wie `dotnet build` und `dotnet publish`, es sei denn, Sie bearbeiten Ihre Projektdatei manuell, um Buildziele von einer Installation der TypeScript SDK zu importieren. Auch bei der [MSBuild-Integration](https://www.staging-typescript.org/docs/handbook/compiler-options-in-msbuild.html) in ASP.NET Core und TypeScript sollten Sie das NuGet-Paket dem npm-Paket vorziehen.

## <a name="add-typescript-support-with-nuget"></a>Hinzufügen der TypeScript-Unterstützung mit NuGet

[Das TypeScript-NuGet-Paket](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild) fügt TypeScript-Unterstützung hinzu. Wenn das NuGet-Paket für TypeScript 3.2 oder höher in Ihrem Projekt installiert ist, wird die entsprechende Version des TypeScript-Sprachdienstes in den Editor geladen.

Wenn Visual Studio installiert ist, wird die enthaltene node.exe-Datei von Visual Studio automatisch ausgewählt. Wenn Node.js nicht bereits installiert ist, empfiehlt sich die Installation der LTS-Version über die [Node.js](https://nodejs.org/en/download/)-Website.

1. Öffnen Sie Ihr ASP.NET Core-Projekt in Visual Studio.

1. Im Projektmappen-Explorer (rechter Bereich) klicken Sie mit der rechten Maustaste auf den Projektknoten, und wählen Sie **NuGet-Pakete verwalten** aus. Suchen Sie auf der Registerkarte **Durchsuchen** nach **Microsoft.TypeScript.MSBuild**, und klicken Sie dann rechts auf **Installieren**, um das Paket zu installieren.

   ![Hinzufügen des NuGet-Pakets](../javascript/media/aspnet-core-ts-nuget.png)

   Visual Studio fügt das NuGet-Paket unter dem Knoten **Abhängigkeiten** im Projektmappen-Explorer hinzu. Der folgende Paketverweis wird zu Ihrer *.csproj-Datei hinzugefügt.

   ```xml
   <PackageReference Include="Microsoft.TypeScript.MSBuild" Version="3.9.7">
      <PrivateAssets>all</PrivateAssets>
      <IncludeAssets>runtime; build; native; contentfiles; analyzers; buildtransitive</IncludeAssets>
   </PackageReference>
   ```

1. Klicken Sie mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Hinzufügen > Neues Element** aus. Wählen Sie die **TypeScript JSON-Konfigurationsdatei** aus und klicken Sie dann auf **Hinzufügen**.

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
       "outDir": "wwwroot/js"
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

### <a name="build-the-application"></a>Erstellen der Anwendung

1. Fügen Sie TypeScript-Dateien ( *.ts*) oder TypeScript JSX-Dateien ( *.tsx*) zu Ihrem Projekt hinzu, und fügen Sie dann TypeScript-Code hinzu. Hier sehen Sie ein einfaches Beispiel für TypeScript:

   ```typescript
   let message: string = 'Hello World';
   console.log(message);
   ```

1. Wenn Sie ein älteres Projekt verwenden, das nicht im SDK-Format vorliegt, befolgen Sie vor dem Kompilieren die Anweisungen unter [Entfernen von Standardimporten](#remove-default-imports).

1. Wählen Sie **Erstellen > Projektmappe erstellen** aus.

   Obwohl die App bei der Ausführung automatisch kompiliert wird, sollten Sie sich etwas ansehen, das während des Buildvorgangs geschieht:

   Wenn Sie Quellzuordnungsdateien generiert haben, öffnen Sie den in der *outDir*-Option angegebenen Ordner. Dort finden Sie die generierten *.js-Dateien sowie die generierten *js.map-Dateien.

   Für die Fehlersuche werden Quellzuordnungsdateien benötigt.

1. Wenn Sie das Projekt bei jedem Speichervorgang kompilieren möchten, verwenden Sie die Option *compileOnSave* in der *.tsconfig-Datei.

   ```json
   ```{
      "compileOnSave":  true,
      "compilerOptions": {
      }
   }
   ```

Ein Beispiel für die Verwendung von gulp mit der Aufgabenausführung zum Kompilieren Ihrer App finden Sie unter [ASP.NET Core und TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html).

Wenn Visual Studio eine Node.js-Version oder Drittanbieteranwendung verwendet, die sich von der erwarteten Version unterscheidet, und dadurch Probleme auftreten, müssen Sie möglicherweise den Pfad festlegen, den Visual Studio verwenden soll. Wählen Sie **Tools** > **Optionen** aus. Wählen Sie unter **Projekte und Projektmappen** die Option **Webpaketverwaltung** > **Externe Webtools** aus.

### <a name="run-the-application"></a>Ausführen der Anwendung

Eine Anleitung zum Ausführen der App nach ihrer Kompilierung finden Sie unter [Schnellstart: Erstellen einer ersten Node.js-App mit Visual Studio](/visualstudio/ide/quickstart-nodejs?toc=%2Fvisualstudio%2Fjavascript%2Ftoc.json#run-the-application).

### <a name="nuget-package-structure-details"></a>Details zur Struktur des NuGet-Pakets

`Microsoft.TypeScript.MSBuild.nupkg` enthält zwei Hauptordner:

- Ordner *build*

    In diesem Ordner befinden sich zwei Dateien.
    Beide sind Einstiegspunkte für die TypeScript-Hauptzieldatei bzw. die Eigenschaftendatei.

    1. *Microsoft.TypeScript.MSBuild.targets*

        Diese Datei legt Variablen zur Angabe der Laufzeitplattform fest, z. B. einen Pfad zu *TypeScript.Tasks.dll*, bevor *Microsoft.TypeScript.targets* aus dem Ordner *tools* importiert wird.

    2. *Microsoft.TypeScript.MSBuild.props*

        Diese Datei importiert *Microsoft.TypeScript.Default.props* aus dem Ordner *tools* und legt Eigenschaften fest, die darauf hinweisen, dass der Build über NuGet initiiert wurde.

- Ordner *tools*

    Paketversionen vor 2.3 enthalten den Ordner „tsc“. *Microsoft.TypeScript.targets* und *TypeScript.Tasks.dll* befinden sich auf Stammebene.

    In Paketversionen 2.3 und höher enthält die Stammebene `Microsoft.TypeScript.targets` und `Microsoft.TypeScript.Default.props`. Weitere Informationen zu diesen Dateien finden Sie in der [MSBuild-Konfiguration](https://www.typescriptlang.org/docs/handbook/compiler-options-in-msbuild.html).

    Darüber hinaus enthält der Ordner drei Unterordner:

    1. *net45*

        Dieser Ordner enthält `TypeScript.Tasks.dll` und andere DLLs, von denen diese DLL abhängt.
        Beim Kompilieren eines Projekts auf einer Windows-Plattform verwendet MSBuild die DLLs aus diesem Ordner.

    2. *netstandard1.3*

        Dieser Ordner enthält eine andere Version von `TypeScript.Tasks.dll`, die zum Kompilieren von Projekten auf einem Nicht-Windows-Computer verwendet wird.

    3. *tsc*

        Dieser Ordner enthält `tsc.js`, `tsserver.js` und alle Abhängigkeitsdateien, die zum Ausführen als node-Skripts erforderlich sind.

        > [!NOTE]
        > Wenn Visual Studio installiert ist, wird die enthaltene *node.exe*-Datei automatisch ausgewählt. Andernfalls muss Node.js auf dem Computer installiert werden.

        Versionen vor 3.1 enthielten eine ausführbare `tsc.exe`-Datei, um die Kompilierung auszuführen. In Version 3.1 wurde diese zugunsten von `node.exe` entfernt.

### <a name="remove-default-imports"></a>Entfernen von Standardimporten

Bei älteren ASP.NET Core-Projekten, die ein [Nicht-SDK-Format](https://docs.microsoft.com/nuget/resources/check-project-format) verwenden, müssen Sie möglicherweise einige Projektdateielemente entfernen.

Wenn Sie das NuGet-Paket für MSBuild-Unterstützung in einem Projekt verwenden, darf die Projektdatei weder `Microsoft.TypeScript.Default.props` noch `Microsoft.TypeScript.targets` importieren. Die Dateien werden vom NuGet-Paket importiert, d. h., wenn Sie sie separat einfügen, kann ein unerwartetes Verhalten auftreten.

1. Klicken Sie mit der rechten Maustaste auf das Projekt, und wählen Sie **Projekt entladen** aus.

1. Klicken Sie mit der rechten Maustaste auf das Projekt, und wählen Sie **Bearbeiten\<*project file name*\>** aus.

   Daraufhin wird die Projektdatei geöffnet.

1. Entfernen Sie die Verweise auf `Microsoft.TypeScript.Default.props` und `Microsoft.TypeScript.targets`.

   Die zu entfernenden Importe sehen etwa wie folgt aus:

   ```xml
   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props')" />

   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets')" />
   ```
