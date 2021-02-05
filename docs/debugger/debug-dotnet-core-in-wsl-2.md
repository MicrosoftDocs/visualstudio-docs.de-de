---
title: Debuggen von .NET Core-Apps in WSL 2
description: Hier erfahren Sie, wie Sie Ihre .NET Core-Apps in WSL 2 ausführen und Debuggen, ohne Visual Studio zu verlassen.
ms.date: 01/25/2021
ms.topic: conceptual
helpviewer_keywords:
- debugging, linux
- debugging, wsl2
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 736987a02ca7e2f59ce689b8402d9a6fcd7407e9
ms.sourcegitcommit: 586369f5aa61d4a0330802f718f0ceaa55d7e9c7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2021
ms.locfileid: "99227676"
---
# <a name="debug-net-core-apps-in-wsl-2-with-visual-studio"></a>Debuggen von .NET Core-Apps in WSL 2 mit Visual Studio

Sie können Ihre .NET Core-Apps problemlos mithilfe von WSL 2 in Linux ausführen und debuggen, ohne Visual Studio zu verlassen. Wenn Sie plattformübergreifend entwickeln, können Sie diese Methode als einfache Möglichkeit zum Testen Ihrer Zielumgebungen verwenden.

Für Windows .NET-Benutzer, die Linux als Zielplattform verwenden, stellt WSL 2 einen optimalen Punkt zwischen realistischer Produktionsumgebung und Produktivität dar. In Visual Studio können Sie bereits mithilfe des [Remotedebuggers](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md) oder mit Containern unter Verwendung von [Containertools](../containers/overview.md) in einer Linux-Remoteumgebung debuggen. Wenn Sie Ihr Hauptaugenmerk auf eine realistische Produktionsumgebung legen möchten, sollten Sie eine dieser Optionen verwenden. Wenn Ihnen eine einfache und schnelle innere Schleife wichtiger ist, eignet sich WSL 2 gut.

Sie müssen nicht nur eine Methode auswählen. Sie können ein Startprofil für Docker und WSL 2 in demselben Projekt erstellen und auswählen, welcher Dienst für eine bestimmte Ausführung geeignet ist. Nachdem Sie Ihre App bereitgestellt haben, können Sie diese immer an einen Remotedebugger anfügen, wenn ein Problem auftreten sollte.

## <a name="prerequisites"></a>Voraussetzungen

- Visual Studio 2019, Version 16.9, Vorschau 1 oder höhere Versionen mit der optionalen WSL 2-Komponente zum Debuggen mit .NET Core

  Die optionale Komponente ist standardmäßig in plattformübergreifenden .NET Core- oder der ASP.NET- und Webentwicklungsworkloads enthalten. Sie müssen mindestens eine dieser Workloads installieren.

- Installieren Sie [WSL 2](/windows/wsl/about).

- Installieren Sie eine [Distribution](https://aka.ms/wslstore) Ihrer Wahl.

## <a name="start-debugging-with-wsl-2"></a>Starten des Debuggens mit WSL 2

1. Nachdem Sie die erforderlichen Komponenten installiert haben, öffnen Sie eine ASP.NET Core Web-App oder eine .NET Core-Konsolen-App in Visual Studio. Dann wird ein neues Startprofil mit dem Namen WSL 2 angezeigt:

   ![WSL 2-Startprofil in der Liste „Startprofil“](media/linux-wsl2-debugging-select-launch-profile.png)

1. Wählen Sie dieses Profil aus, um es der Datei *launchSettings.json* hinzuzufügen.

   Einige der Schlüsselattribute in der Datei werden im folgenden Beispiel gezeigt.

    ```json
    "WSL 2": {
        "commandName": "WSL2",
        "launchBrowser": true,
        "launchUrl": "https://localhost:5001",
        "environmentVariables": {
            "ASPNETCORE_URLS": "https://localhost:5001;http://localhost:5000",
            "ASPNETCORE_ENVIRONMENT": "Development"
        },
        "distributionName": ""
    }
    ```

   Nachdem Sie das neue Profil ausgewählt haben, wird durch die Erweiterung überprüft, ob die WSL 2-Distribution zum Ausführen von .NET Core-Apps konfiguriert ist, und Sie erhalten Hilfe bei der Installation fehlender Abhängigkeiten. Nachdem Sie diese Abhängigkeiten installiert haben, können Sie in WSL 2 debuggen.

1. Starten Sie den Debuggingvorgang wie gewohnt. Dann wird Ihre App in Ihrer WSL 2-Standarddistribution ausgeführt.

   Sie können ganz einfach überprüfen, ob Ihre App in Linux ausgeführt wird, indem Sie den Wert von `Environment.OSVersion` überprüfen.

>[!NOTE]
> Nur Ubuntu und Debian wurden getestet und werden unterstützt. Andere Distributionen, die von .NET Core unterstützt werden, sollten funktionieren. Dafür müssen allerdings die [.NET Core-Runtime](https://aka.ms/wsldotnet) und [cURL](https://curl.haxx.se/) manuell installiert werden.

## <a name="choose-a-specific-distribution"></a>Auswählen einer bestimmten Distribution

Standardmäßig verwendet das WSL 2-Startprofil die Standarddistribution, die in der Datei *wsl.exe* festgelegt ist. Wenn Sie möchten, dass Ihr Startprofil unabhängig von diesem Standard eine bestimmte Distribution als Ziel verwendet, können Sie das Startprofil ändern. Wenn Sie z. B. eine Web-App debuggen und sie unter Ubuntu 20.04 testen möchten, sieht Ihr Startprofil wie folgt aus:

```json
"WSL 2": {
    "commandName": "WSL2",
    "launchBrowser": true,
    "launchUrl": "https://localhost:5001",
    "environmentVariables": {
        "ASPNETCORE_URLS": "https://localhost:5001;http://localhost:5000",
        "ASPNETCORE_ENVIRONMENT": "Development"
    },
    "distributionName": "Ubuntu-20.04"
}
```

## <a name="target-multiple-distributions"></a>Verwenden mehrerer Distributionen als Ziel

Wenn Sie an einer Anwendung arbeiten, die in mehreren Distributionen ausgeführt werden soll, und Sie diese schnell für jede Distributionen testen möchten, können Sie mehrere Startprofile verwenden. Wenn Sie z. B. Ihre Konsolen-App unter Debian, Ubuntu 18.04 und Ubuntu 20.04 testen müssen, können Sie die folgenden Startprofile verwenden:

```json
"WSL 2 : Debian": {
    "commandName": "WSL2",
    "distributionName": "Debian"
},
"WSL 2 : Ubuntu 18.04": {
    "commandName": "WSL2",
    "distributionName": "Ubuntu-18.04"
},
"WSL 2 : Ubuntu 20.04": {
    "commandName": "WSL2",
    "distributionName": "Ubuntu-20.04"
}
```

Mit diesen Startprofilen können Sie problemlos zwischen den Zieldistributionen hin- und herwechseln, ohne auf die Vorteile von Visual Studio verzichten zu müssen.

![Mehrere WSL 2-Startprofile in der Liste „Startprofil“](media/linux-wsl2-debugging-switch-target-distribution.png)

## <a name="wsl-settings-in-the-launch-profile"></a>WSL-Einstellungen im Startprofil

In der folgenden Tabelle werden die Einstellungen aufgeführt, die im Startprofil unterstützt werden.

|Name|Standard|Zweck|Tokenunterstützung?|
|-|-|-|-|
|executablePath|dotnet|Die auszuführende ausführbare Datei|Ja|
|commandLineArgs|Der Wert der MSBuild-Eigenschaft „TargetPath“, die der WSL-Umgebung zugeordnet ist|Befehlszeilenargumente, die an executablePath übergeben werden|Ja|
|workingDirectory|Für Konsolen-Apps: {*OutDir*}</br>Für Web-Apps: {*ProjectDir*}|Das Arbeitsverzeichnis, in dem der Debuggingvorgang gestartet werden soll|Ja|
|EnvironmentVariables||Schlüssel-Wert-Paare von Umgebungsvariablen, die für den Debuggingvorgang festgelegt werden sollen|Ja|
|setupScriptPath||Skript, das vor dem Debuggingvorgang ausgeführt werden soll; nützlich für das Ausführen von Skripts wie „~/.bash_profile“|Ja|
|distributionName||Der Name der zu verwendenden WSL-Distribution|Nein|
|launchBrowser|false|Gibt an, ob ein Browser gestartet werden soll|Nein|
|launchUrl||Zu startende URL, wenn der Wert für „launchbrowser“ „True“ ist|Nein|

Unterstützte Token:

{*ProjectDir*}: der Pfad zum Projektverzeichnis

{*OutDir*}: der Wert der MSBuild-Eigenschaft `OutDir`

>[!NOTE]
> Alle Pfade gelten für WSL, nicht für Windows.
