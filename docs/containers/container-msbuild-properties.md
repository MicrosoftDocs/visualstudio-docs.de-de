---
title: 'Visual Studio-Containertools: Buildeigenschaften'
author: ghogen
description: Hier erfahren Sie, wie Sie die Buildeigenschaften des Containertools bearbeiten, um anzupassen, wie Visual Studio ein Containerprojekt erstellt und ausführt.
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: reference
ms.openlocfilehash: 4e8675bd0ea12b30ce678ce454bcedee457ddacd
ms.sourcegitcommit: d577818d3d8e365baa55c6108fa8159c46ed8b43
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2021
ms.locfileid: "97846739"
---
# <a name="container-tools-build-properties"></a>Buildeigenschaften für Containertools

Sie können den Buildprozess für Ihre Containerprojekte in Visual Studio anpassen, indem Sie die Eigenschaften festlegen, die MSBuild zum Erstellen Ihres Projekts nutzt. Beispielsweise können Sie den Namen der Dockerfile ändern, Tags und Bezeichnungen für Ihre Images festlegen, zusätzliche an Docker-Befehle übergebene Argumente angeben und steuern, ob Visual Studio bestimmte Leistungsoptimierungen vornimmt, z. B. das Erstellen außerhalb der Containerumgebung. Sie können auch Debuggingeigenschaften wie den Namen der zu startenden ausführbaren Datei und die bereitzustellenden Befehlszeilenargumente festlegen.

Bearbeiten Sie die Projektdatei, um den Wert einer Eigenschaft festzulegen. Angenommen der Name Ihrer Dockerfile lautet *MyDockerfile*. Sie können die `DockerfileFile`-Eigenschaft dann wie folgt in der Projektdatei festlegen:

```xml
<PropertyGroup>
   <DockerfileFile>MyDockerfile</DockerfileFile>
</PropertyGroup>
```

Sie können die Eigenschaftseinstellung einem vorhandenen `PropertyGroup`-Element hinzufügen oder ein neues `PropertyGroup`-Element erstellen, falls noch keines vorhanden ist.

In der folgenden Tabelle werden die MSBuild-Eigenschaften aufgeführt, die für Containerprojekte verfügbar sind. Die NuGet-Paketversion gilt für[Microsoft.VisualStudio.Azure.Containers.Tools.Targets](https://www.nuget.org/packages/Microsoft.VisualStudio.Azure.Containers.Tools.Targets/).

| Name der Eigenschaft | Beschreibung | Standardwert  | NuGet-Paketversion|
|---------------|-------------|----------------|----------------------|
| ContainerDevelopmentMode | Steuert, ob die Optimierung „build-on-host“ (Debugging im schnellen Modus) aktiviert ist.  Zulässige Werte sind: **Fast** (Schnell) und **Regular** (Normal). | Fast |1.0.1872750 oder höher|
| ContainerVsDbgPath | Der Pfad für den VSDBG-Debugger. | `%USERPROFILE%\vsdbg\vs2017u5` |1.0.1985401 oder höher|
| DockerDebuggeeArguments | Beim Debuggen wird der Debugger angewiesen, diese Argumente an die gestartete ausführbare Datei zu übergeben. | Nicht auf .NET Framework-Projekte in ASP.NET anwendbar. |1.7.8 oder höher|
| DockerDebuggeeProgram | Beim Debuggen wird der Debugger aufgefordert, diese ausführbare Datei zu starten. | Bei .NET Core-Projekten: dotnet, bei .NET Framework-Projekten in ASP.NET: Nicht anwendbar (es wird immer IIS verwendet). |1.7.8 oder höher|
| DockerDebuggeeKillProgram | Dieser Befehl wird zum Beenden des in einem Container ausgeführten Prozess verwendet. | Nicht auf .NET Framework-Projekte in ASP.NET anwendbar. |1.7.8 oder höher|
| DockerDebuggeeWorkingDirectory | Beim Debuggen wird der Debugger angewiesen, diesen Pfad als Arbeitsverzeichnis zu verwenden. | C:\app (Windows) oder /app (Linux). |1.7.8 oder höher|
| DockerDefaultTargetOS | Das standardmäßige Zielbetriebssystem, das beim Erstellen des Docker-Images verwendet wird. | Wird von Visual Studio festgelegt. |1.0.1985401 oder höher|
| DockerImageLabels | Die Standardbezeichnungen, die auf das Docker-Image angewendet werden. | com.microsoft.created-by=visual-studio;com.microsoft.visual-studio.project-name=$(MSBuildProjectName) |1.5.4 oder höher|
| DockerFastModeProjectMountDirectory|Im **schnellen Modus** steuert diese Eigenschaft, wo das Volume des Projektausgabeverzeichnisses in den ausgeführten Container eingebunden wird.|C:\app (Windows) oder /app (Linux).|1.9.2 oder höher|
| DockerfileBuildArguments | Zusätzliche Argumente, die an den Befehl [docker build](https://docs.docker.com/engine/reference/commandline/build/) übergeben werden. | Nicht zutreffend. |1.0.1872750 oder höher|
| DockerfileContext | Hierbei handelt es sich um den Standardkontext, der beim Erstellen des Docker-Images als Pfad verwendet wird und relativ zum Dockerfile ist. | Wird von Visual Studio festgelegt. |1.0.1872750 oder höher|
| DockerfileFastModeStage | Die Dockerfile-Phase (d. h. Ziel), die beim Erstellen des Images im Debugmodus verwendet werden soll. | Die erste Phase, die in der Dockerfile (Base) ermittelt wird. |
| DockerfileFile | Beschreibt die standardmäßige Dockerfile, die zum Erstellen oder Ausführen des Containers für das Projekt verwendet wird. Hierfür kann auch ein Pfad angegeben werden. | Docker-Datei |1.0.1872750 oder höher|
| DockerfileRunArguments | Zusätzliche Argumente, die an den Befehl [docker run](https://docs.docker.com/engine/reference/commandline/run/) übergeben werden. | Nicht zutreffend. |1.0.1872750 oder höher|
| DockerfileRunEnvironmentFiles | Durch Semikolons getrennte Liste von Umgebungsdateien, die während der Docker-Ausführung angewendet werden. | Nicht zutreffend. |1.0.1872750 oder höher|
| DockerfileTag | Das Tag, das beim Erstellen des Docker-Images verwendet wird. Beim Debuggen wird „.dev“ an das Tag angehängt. | Der Assemblyname, nachdem nicht alphanumerische Zeichen gemäß der folgenden Regeln entfernt wurden: <br/> Wenn das resultierende Tag nur aus numerischen Zeichen besteht, wird „image“ als Präfix eingefügt (z. B. „image2314“). <br/> Wenn das resultierende Tag eine leere Zeichenfolge ist, wird „image“ als Tag verwendet. |1.0.1872750 oder höher|

## <a name="example"></a>Beispiel

Die folgende Projektdatei enthält Beispiele für einige dieser Einstellungen.

```xml
 <Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
    <UserSecretsId>feae72bf-2368-4487-b6c6-546c19338cb1</UserSecretsId>
    <DockerDefaultTargetOS>Linux</DockerDefaultTargetOS>
    <!-- In CI/CD scenarios, you might need to change the context. By default, Visual Studio uses the
         folder above the Dockerfile. The path is relative to the Dockerfile, so here the context is
         set to the same folder as the Dockerfile. -->
    <DockerfileContext>.</DockerfileContext>
    <!-- Set `docker run` arguments to mount a volume -->
    <DockerfileRunArguments>-v $(pwd)/host-folder:/container-folder:ro</DockerfileRunArguments>
    <!-- Set `docker build` arguments to add a custom tag -->
    <DockerfileBuildArguments>-t contoso/front-end:v2.0</DockerfileBuildArguments>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.VisualStudio.Azure.Containers.Tools.Targets" Version="1.10.6" />
  </ItemGroup>

</Project>
```

## <a name="next-steps"></a>Nächste Schritte

Weitere allgemeine Informationen zu MSBuild-Eigenschaften finden Sie unter [MSBuild-Eigenschaften](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Siehe auch

[Buildeigenschaften von Docker Compose](docker-compose-properties.md)

[Starteinstellungen für Containertools](container-launch-settings.md)

[Reservierte und bekannte Eigenschaften für MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
