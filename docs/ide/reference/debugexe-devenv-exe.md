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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5cdf770446b78b1a1bb4b55d61f4c3e9f50c4035
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894607"
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
