---
title: -DebugExe („devenv.exe“)
description: Hier erfahren Sie, wie Sie mit der devenv-Befehlszeilenoption „DebugExe“ eine angegebene ausführbare Datei öffnen, die gedebuggt werden soll.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
- debugging executables
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6e60c3fb8a72caa44bcf70ac36850748ce240d42
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "96039470"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)

Öffnet die angegebene ausführbare Datei, die debuggt werden soll.

## <a name="syntax"></a>Syntax

```shell
devenv /DebugExe ExecutableFile
```

## <a name="arguments"></a>Argumente

- *ExecutableFile*

  Erforderlich. Der Pfad und Dateiname einer `.exe`-Datei. Wenn die `.exe`-Datei nicht gefunden wurde oder nicht vorhanden ist, wird keine Warnung oder Fehlermeldung angezeigt und Visual Studio startet normal.

## <a name="remarks"></a>Bemerkungen

Alle Zeichenfolgen, die dem *ExecutableFile*-Parameter folgen, werden dieser Datei als Argumente übergeben.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird die Datei `MyApplication.exe` zum Debuggen geöffnet.

```shell
devenv /debugexe MyApplication.exe
```

## <a name="see-also"></a>Weitere Informationen

- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)
