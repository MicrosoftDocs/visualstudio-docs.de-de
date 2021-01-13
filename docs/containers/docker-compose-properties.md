---
title: Buildeinstellungen von Docker Compose
author: ghogen
description: Hier erfahren Sie, wie Sie die Docker Compose-Buildeigenschaften bearbeiten, um anzupassen, wie Visual Studio eine Docker Compose-Anwendung erstellt und ausführt.
ms.custom: SEO-VS-2020
ms.author: ghogen
ms.date: 08/12/2019
ms.technology: vs-azure
ms.topic: reference
ms.openlocfilehash: 0a27535e9c07f87391b3cdfd8440578e36feee9e
ms.sourcegitcommit: d577818d3d8e365baa55c6108fa8159c46ed8b43
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2021
ms.locfileid: "97846811"
---
# <a name="docker-compose-build-properties"></a>Buildeigenschaften von Docker Compose

Die Eigenschaften zur Verwaltung einzelner Docker-Projekte sind unter [Buildeigenschaften von Containertools](container-msbuild-properties.md) beschrieben. Diese Eigenschaften können Sie anpassen. Zusätzlich können Sie auch festlegen, wie Visual Studio Docker-Projekte erstellt. Dazu legen Sie die Docker Compose-Eigenschaften fest, die MSBuild zur Erstellung der Projektmappe verwendet. Außerdem können Sie steuern, wie der Visual Studio-Debugger Ihre Docker Compose-Apps ausführt, indem Sie Dateibezeichnungen in Docker Compose-Konfigurationsdateien festlegen.

## <a name="how-to-set-the-msbuild-properties"></a>Festlegen der MSBuild-Eigenschaften

Den Wert einer Eigenschaft legen Sie in der Projektdatei fest. Sofern in der Tabelle im nächsten Abschnitt nicht anders angegeben, handelt es sich bei der Projektdatei für die Docker Compose-Eigenschaften um eine Datei mit der Erweiterung „.dcproj“. Angenommen, Sie möchten festlegen, dass zu Beginn des Debuggens der Browser gestartet wird. Die `DockerLaunchAction`-Eigenschaft in der DCPROJ-Projektdatei können Sie dann wie folgt festlegen:

```xml
<PropertyGroup>
   <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
</PropertyGroup>
```

Sie können die Eigenschaftseinstellung einem vorhandenen `PropertyGroup`-Element hinzufügen oder ein neues `PropertyGroup`-Element erstellen, falls noch keines vorhanden ist.

## <a name="docker-compose-msbuild-properties"></a>MSBuild-Eigenschaften für Docker Compose

In der folgenden Tabelle werden die MSBuild-Eigenschaften aufgeführt, die für Docker Compose-Projekte verfügbar sind.

| Name der Eigenschaft | Speicherort | Beschreibung | Standardwert  |
|---------------|----------|-------------|----------------|
|AdditionalComposeFilePaths|dcproj|Gibt zusätzliche Compose-Dateien in einer durch Semikolons getrennten Liste an, die an „docker-compose.exe“ für alle Befehle gesendet werden sollen. Relative Pfade aus der docker-compose-Projektdatei (DCPROJ-Datei) sind zulässig.|-|
|DockerComposeBaseFilePath|dcproj|Gibt den ersten Teil der Dateinamen der docker-compose-Dateien ohne die Erweiterung *.yml* an. Zum Beispiel: <br>1.  DockerComposeBaseFilePath = NULL/nicht definiert: Verwenden Sie den Basisdateipfad *docker-compose*. Dateien werden dann als *docker-compose.yml* und *docker-compose.override.yml* benannt.<br>2.   DockerComposeBaseFilePath = *mydockercompose*: Dateien werden als *mydockercompose.yml* und *mydockercompose.override.yml* benannt.<br> 3.  DockerComposeBaseFilePath = *..\mydockercompose*: Dateien werden eine Ebene nach oben verlagert. |docker-compose|
|DockerComposeBuildArguments|dcproj|Legt die zusätzlichen Parameter fest, die dem Befehl `docker-compose build` übergeben werden sollen. Beispiel: `--parallel --pull` |
|DockerComposeDownArguments|dcproj|Legt die zusätzlichen Parameter fest, die dem Befehl `docker-compose down` übergeben werden sollen. Beispiel: `--timeout 500`|-|  
|DockerComposeProjectPath|csproj oder vbproj|Der relative Pfad zur Docker Compose-Projektdatei (mit der DCPROJ-Erweiterung). Legen Sie diese Eigenschaft fest, wenn Sie das Dienstprojekt veröffentlichen, damit die zugeordneten Imagebuildeinstellungen in der Datei „docker-compose.yml“ gefunden werden.|-|
|DockerComposeUpArguments|dcproj|Legt die zusätzlichen Parameter fest, die dem Befehl `docker-compose up` übergeben werden sollen. Beispiel: `--timeout 500`|-|
|DockerDevelopmentMode|dcproj| Steuert, ob die Optimierung „build-on-host“ (Debugging im schnellen Modus) aktiviert ist.  Zulässige Werte sind: **Fast** (Schnell) und **Regular** (Normal). | Fast |
|DockerLaunchAction| dcproj | Legt die Startaktion fest, die beim Drücken von F5 oder STRG+F5 ausgeführt werden soll.  Zulässige Werte sind None, LaunchBrowser und LaunchWCFTestClient.|Keine|
|DockerLaunchBrowser| dcproj | Legt fest, ob der Browser gestartet werden soll. Wird ignoriert, wenn DockerLaunchAction festgelegt wird. | False |
|DockerServiceName| dcproj|Wenn DockerLaunchAction oder DockerLaunchBrowser festgelegt wird, ist DockerServiceName der Name des Diensts, der gestartet werden soll.  Da eine Docker Compose-Datei auf mehrere Projekte verweisen kann, können Sie mit dieser Eigenschaft festlegen, welches Projekt gestartet werden soll.|-|
|DockerServiceUrl| dcproj | Die URL, die beim Start des Browsers verwendet werden soll.  Gültige Ersetzungstoken sind „{ServiceIPAddress}“, „{ServicePort}“ und „{Scheme}“.  Beispiel: {Scheme}://{ServiceIPAddress}:{ServicePort}.|-|
|DockerTargetOS| dcproj | Das Zielbetriebssystem, das beim Erstellen des Docker-Images verwendet wird.|-|

## <a name="example"></a>Beispiel

Wenn Sie den Speicherort der Docker Compose-Dateien ändern, indem Sie `DockerComposeBaseFilePath` auf einen relativen Pfad festlegen. Dann müssen Sie noch sicherstellen, dass der Buildkontext so geändert wird, dass er auf den Projektmappenordner verweist. Wenn Ihre Docker Compose-Datei sich in einem Ordner namens *DockerComposeFiles* befindet, sollte der Buildkontext auf „..“ oder „../..“ festgelegt werden, je nachdem, was dem Projektmappenordner entspricht.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="15.0" Sdk="Microsoft.Docker.Sdk">
  <PropertyGroup Label="Globals">
    <ProjectVersion>2.1</ProjectVersion>
    <DockerTargetOS>Windows</DockerTargetOS>
    <ProjectGuid>154022c1-8014-4e9d-bd78-6ff46670ffa4</ProjectGuid>
    <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
    <DockerServiceUrl>{Scheme}://{ServiceIPAddress}{ServicePort}</DockerServiceUrl>
    <DockerServiceName>webapplication1</DockerServiceName>
    <DockerComposeBaseFilePath>DockerComposeFiles\mydockercompose</DockerComposeBaseFilePath>
    <AdditionalComposeFilePaths>AdditionalComposeFiles\myadditionalcompose.yml</AdditionalComposeFilePaths>
  </PropertyGroup>
  <ItemGroup>
    <None Include="DockerComposeFiles\mydockercompose.override.yml">
      <DependentUpon>DockerComposeFiles\mydockercompose.yml</DependentUpon>
    </None>
    <None Include="DockerComposeFiles\mydockercompose.yml" />
    <None Include=".dockerignore" />
  </ItemGroup>
</Project>
```

Die Datei *mydockercompose.yml* sollte folgendermaßen aussehen, dabei muss der Buildkontext auf den relativen Pfad des Projektmappenordners (in diesem Fall `..`) festgelegt sein.

```yml
version: '3.4'

services:
  webapplication1:
    image: ${DOCKER_REGISTRY-}webapplication1
    build:
      context: ..
      dockerfile: WebApplication1\Dockerfile
```

> [!NOTE]
> DockerComposeBuildArguments, DockerComposeDownArguments und DockerComposeUpArguments sind neu in Visual Studio 2019 Version 16.3.

## <a name="docker-compose-file-labels"></a>Docker Compose-Dateibezeichnungen

Sie können bestimmte Einstellungen auch überschreiben, indem Sie eine Datei mit dem Namen *docker-compose.vs.debug.yml* (für die **Debugkonfiguration**) oder *docker-compose.vs.release.yml* (für die **Releasekonfiguration**) im selben Verzeichnis wie die Datei *docker-compose.yml* platzieren.  In dieser Datei können Sie Einstellungen wie folgt festlegen:

```yml
services:
  webapplication1:
    labels:
      com.microsoft.visualstudio.debuggee.workingdirectory: "C:\\my_app_folder"
```

Setzen Sie wie im vorherigen Beispiel die Werte in doppelte Anführungszeichen, und verwenden Sie den umgekehrten Schrägstrich als Escapezeichen für umgekehrte Schrägstriche in Pfaden.

|Bezeichnungsname|Beschreibung|
|----------|-----------|
|com.microsoft.visualstudio.debuggee.arguments|Die Argumente, die zu Beginn des Debuggens dem Programm übergeben werden. Bei .NET Core-Apps sind diese Argumente in der Regel zusätzliche Suchpfade für NuGet-Pakete, auf die der Pfad zur Ausgabeassembly des Projekts folgt.|
|com.microsoft.visualstudio.debuggee.killprogram|Mit diesem Befehl wird ggf. das Programm der zu debuggenden Komponente beendet, das im Container ausgeführt wird.|
|com.microsoft.visualstudio.debuggee.program|Das Programm, das zu Beginn des Debuggens gestartet wird. Bei .NET Core-Apps ist für diese Einstellung in der Regel **dotnet** festgelegt.|
|com.microsoft.visualstudio.debuggee.workingdirectory|Das Verzeichnis, das zu Beginn des Debuggens als Startverzeichnis verwendet wird. Bei Linux-Containern ist für diese Einstellung üblicherweise */app* festgelegt, bei Windows-Containern *C:\app*.|

## <a name="customize-the-app-startup-process"></a>Anpassen des App-Startvorgangs

Sie können einen Befehl oder ein benutzerdefiniertes Skript vor dem App-Start ausführen, indem Sie es mithilfe der `entrypoint`-Einstellung von der Konfiguration abhängig machen. Wenn Sie ein Zertifikat durch Ausführen von `update-ca-certificates` z. B. nur für den **Debugmodus**, aber nicht für den **Releasemodus** einrichten müssen, fügen Sie den folgenden Code nur in der Datei *docker-compose.vs.debug.yml* hinzu:

```yml
services:
  webapplication1:
    entrypoint: "sh -c 'update-ca-certificates && tail -f /dev/null'"
    labels:
      ...
```

Wenn Sie die Datei *docker-compose.vs.release.yml* oder *docker-compose.vs.debug.yml* weglassen, dann generiert Visual Studio anhand der Standardeinstellungen selbst eine.

## <a name="next-steps"></a>Nächste Schritte

Weitere allgemeine Informationen zu MSBuild-Eigenschaften finden Sie unter [MSBuild-Eigenschaften](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Siehe auch

[Buildeigenschaften für Containertools](container-msbuild-properties.md)

[Starteinstellungen für Containertools](container-launch-settings.md)

[Reservierte und bekannte Eigenschaften für MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
