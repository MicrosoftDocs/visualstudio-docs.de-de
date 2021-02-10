---
title: -Out („devenv.exe“)
description: Hier erfahren Sie, wie Sie mithilfe der devenv-Befehlszeilenoption „Out“ eine Datei angeben, in der beim Ausführen, Ausführen und Beenden, Aktualisieren, Erstellen, Neuerstellen, Bereinigen oder Bereitstellen einer Projektmappe Fehler gespeichert und angezeigt werden.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- errors [Visual Studio], builds
- Devenv, /Out switch
- builds [Visual Studio], logs
- error logs [Visual Studio], command-line build errors
- error logs [Visual Studio]
- /Out Devenv switch
- Out Devenv switch
- builds [Visual Studio], errors
- output files, build errors
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: db5a67031d48c55a4bd9c668335360897bcca62b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932188"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)

Gibt eine Datei an, die Fehler speichern und anzeigen soll, wenn Sie eine Projektmappe [ausführen](run-devenv-exe.md), [ausführen und beenden](runexit-devenv-exe.md), [aktualisieren](upgrade-devenv-exe.md), [erstellen](build-devenv-exe.md), [erneut erstellen](rebuild-devenv-exe.md), [bereinigen](clean-devenv-exe.md) oder [bereitstellen](deploy-devenv-exe.md).

## <a name="syntax"></a>Syntax

```shell
devenv /Out FileName
```

## <a name="arguments"></a>Argumente

- *FileName*

  Erforderlich. Der Pfad und der Name der Datei, die beim Erstellen einer ausführbaren Datei die Ausgabe empfangen soll.

## <a name="remarks"></a>Bemerkungen

Wenn ein nicht vorhandener Dateiname angegeben wird, wird die Datei automatisch erstellt. Andernfalls ist die Datei bereits vorhanden, und die Ergebnisse werden an die vorhandenen Inhalte der Datei angefügt.

Buildfehler in der Befehlszeile werden im **Befehlsfenster** und der Solution Builder-Ansicht des **Ausgabefensters** angezeigt. Dieser Schalter eignet sich zum Anzeigen der Ergebnisse unbeaufsichtigter Builds.

## <a name="example"></a>Beispiel

In diesem Beispiel wird `MySolution` ausgeführt, und es werden Fehler in die `MyErrorLog.txt`-Datei geschrieben.

```shell
devenv /run "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"
```

## <a name="see-also"></a>Weitere Informationen

- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)
- [/Run („devenv.exe“)](../../ide/reference/run-devenv-exe.md)
- [/RunExit (devenv.exe)](runexit-devenv-exe.md)
- [/Upgrade (devenv.exe)](upgrade-devenv-exe.md)
- [/Clean (devenv.exe)](clean-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
