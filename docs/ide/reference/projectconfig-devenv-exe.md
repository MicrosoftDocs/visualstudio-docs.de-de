---
title: -ProjectConfig („devenv.exe“)
description: Hier erfahren Sie, wie Sie mit der devenv-Befehlszeilenoption „ProjectConfig“ eine Projektbuildkonfiguration angeben, die angewendet werden soll, wenn Sie das Projekt erstellen, bereinigen, neu erstellen oder bereitstellen.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /ProjectConfig Devenv switch
- configurations, rebuilding
- deployment projects, creating
- configurations, cleaning
- deployment projects, specifying
- deployment projects, adding
- build configurations, specifying
- Devenv, /ProjectConfig switch
- ProjectConfig Devenv switch (/ProjectConfig)
- projects [Visual Studio], build configuration
- projects [Visual Studio], cleaning
ms.assetid: 6b54ef59-ffed-4f62-a645-1279ede97ebf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 06c6f98e9d022a7b253fdd0ea25a60ff01a4d756
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040068"
---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)

Gibt eine Projektbuildkonfiguration an, die beim Erstellen, Bereinigen, Neuerstellen oder Bereitstellen des im `/Project`-Argument benannten Projekts angewendet werden soll.

## <a name="syntax"></a>Syntax

```shell
devenv SolutionName {/Build|/Clean|/Deploy|/Rebuild} [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Argumente

- *SolutionName*

  Erforderlich. Der vollständige Pfad und Name der Projektmappendatei.

- {`/Build`|`/Clean`|`/Deploy`|`/Rebuild`}

  Erforderlich. Dient zum [Erstellen](build-devenv-exe.md), [Bereinigen](clean-devenv-exe.md), [Bereitstellen](deploy-devenv-exe.md) oder [Neuerstellen](rebuild-devenv-exe.md) des Projekts.

- *SolnConfigName*

  Dies ist optional. Der Name der Projektmappenkonfiguration (z.B. `Debug` oder `Release`), die auf die in *SolutionName* benannte Projektmappe angewendet werden soll. Wenn mehrere Projektmappenplattformen verfügbar sind, müssen Sie auch die Plattform angeben (z.B. `Debug|Win32`). Wenn dieses Argument nicht angegeben wird oder eine leere Zeichenfolge (`""`) enthält, verwendet das Tool die aktive Konfiguration der Projektmappe.

- `/Project` *Projektname*

  Dies ist optional. Der Pfad und der Name einer Projektdatei innerhalb der Projektmappe. Sie können den Anzeigenamen des Projekts oder einen relativen Pfad vom *SolutionName*-Ordner zur Projektdatei eingeben. Sie können auch den vollständigen Pfad und Namen der Projektdatei eingeben.

- `/ProjectConfig` *ProjConfigName*

  Dies ist optional. Der Name der Buildkonfiguration des Projekts (z.B. `Debug` oder `Release`), die auf das benannte `/Project` angewendet werden soll. Wenn mehrere Projektmappenplattformen verfügbar sind, müssen Sie auch die Plattform angeben (z.B. `Debug|Win32`).

- `/Out` *OutputFilename*

  Dies ist optional. Der Name der Datei, an die die Ausgabe des Tools gesendet werden soll. Wenn die Datei bereits vorhanden ist, fügt das Tool die Ausgabe an das Ende der Datei an.

## <a name="remarks"></a>Hinweise

Der `/ProjectConfig`-Schalter muss zusammen mit dem `/Project`-Schalter als Teil eines `/Build`-, /`Clean`-, `/Deploy`- oder`/Rebuild`-Befehls verwendet werden.

Schließen Sie Zeichenfolgen, die Leerzeichen enthalten, in doppelten Anführungszeichen ein.

Zusammenfassende Informationen für Builds, inklusive Fehlermeldungen, können im Befehlsfenster oder in einer Protokolldatei, die durch den Schalter `/Out` angegeben wird, angezeigt werden.

## <a name="example"></a>Beispiel

Mit dem folgenden Befehl wird das Projekt `CSharpWinApp` mithilfe der `Debug`-Projektbuildkonfiguration in `MySolution` erstellt:

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Weitere Informationen

- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)
- [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
