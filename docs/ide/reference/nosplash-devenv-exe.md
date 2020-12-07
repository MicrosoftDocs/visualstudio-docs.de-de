---
title: -NoSplash („devenv.exe“)
description: Hier erfahren Sie, wie Sie mit der devenv-Befehlszeilenoption „NoSplash“ verhindern, dass der Begrüßungsbildschirm angezeigt wird.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /NoSplash switch
- /NoSplash Devenv switch
- NoSplash Devenv switch
author: DennisLee-DennisLee
ms.author: v-dele
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e86398663ea7b6c8209d4123ab3cb12651d4491e
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "96043997"
---
# <a name="nosplash-devenvexe"></a>/NoSplash (devenv.exe)

Verhindert, dass der Begrüßungsbildschirm angezeigt wird.

## <a name="syntax"></a>Syntax

```shell
devenv /NoSplash [File1[ FileN]...]
```

## <a name="arguments"></a>Argumente

- *File1*

  Optional. Die Datei, die in einer vorhandenen Instanz von Visual Studio geöffnet werden soll. Wenn keine Instanz von Visual Studio vorhanden ist, wird eine neue Instanz mit einem vereinfachten Fensterlayout erstellt, und das Tool öffnet *File1* in der neuen Instanz.

- *FileN*

  Optional. Eine oder mehrere zusätzliche Dateien, die in der vorhandenen Instanz von Visual Studio geöffnet werden sollen.

## <a name="remarks"></a>Bemerkungen

Dieser Schalter blendet den Begrüßungsbildschirm aus. Durch Auslassen dieses Schalters wird der Begrüßungsbildschirm angezeigt. Wenn Sie den Begrüßungsbildschirm genauer untersuchen möchten (um beispielsweise das VSPackage-Produktsymbol zu überprüfen), verwenden Sie den Schalter [/Splash](../../extensibility/devenv-command-line-switches-for-vspackage-development.md).

Der Schalter `/NoSplash` kann mit anderen Schaltern kombiniert werden, z.B. [/Run](run-devenv-exe.md) oder [/DebugExe](debugexe-devenv-exe.md).

## <a name="example"></a>Beispiel

In allen drei Beispielen wird die IDE ohne Anzeige des Begrüßungsbildschirms geöffnet. Im zweiten Beispiel wird außerdem die angegebene Projektmappe kompiliert und die erstellte ausführbare Datei ausgeführt. Im dritten Beispiel wird die angegebene ausführbare Datei zum Debuggen in der IDE geöffnet.

```shell
devenv /nosplash

devenv /nosplash /run MySolution.sln

devenv /nosplash /debugexe MySolution.exe
```

## <a name="see-also"></a>Weitere Informationen

- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)
- [Devenv-Befehlszeilenschalter für die VSPackage-Entwicklung](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)
