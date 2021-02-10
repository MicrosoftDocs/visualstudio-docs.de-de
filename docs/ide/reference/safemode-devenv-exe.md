---
title: -SafeMode („devenv.exe“)
description: Hier erfahren Sie, wie Sie Visual Studio mit der devenv-Befehlszeilenoption „SafeMode“ im abgesicherten Modus starten und nur die Standardumgebung und -dienste laden.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1626776ec41bdbdfe5ad2b611516e62ada4f15a3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957867"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)

Startet Visual Studio im abgesicherten Modus und lädt nur die Standardumgebung und -dienste.

## <a name="syntax"></a>Syntax

```shell
devenv /SafeMode
```

## <a name="remarks"></a>Bemerkungen

Dieser Schalter verhindert, dass beim Start von Visual Studio VSPackages von Drittanbietern geladen werden und ermöglicht so eine stabile Ausführung.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird Visual Studio im abgesicherten Modus gestartet.

```shell
devenv /safemode
```

## <a name="see-also"></a>Weitere Informationen

- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)
