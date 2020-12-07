---
title: -DoNotLoadProjects („devenv.exe“)
description: Hier erfahren Sie, wie Sie mithilfe der Befehlszeilenoption „DoNotLoadProjects“ die angegebene Projektmappe öffnen, ohne Projekte zu laden.
ms.custom: SEO-VS-2020
ms.date: 04/30/2019
ms.topic: reference
helpviewer_keywords:
- Devenv, /DoNotLoadProjects switch
- /DoNotLoadProjects Devenv switch
- DoNotLoadProjects Devenv switch
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef3502a2180f7ae7ed5963deb14844b46f3dbff9
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040627"
---
# <a name="donotloadprojects-devenvexe"></a>/DoNotLoadProjects (devenv.exe)

**Neu für Visual Studio 2019, Version 16.1**

Öffnet die angegebene Lösung, ohne Projekte zu laden. Weitere Informationen finden Sie unter [Gefilterte Projektmappen in Visual Studio](../filtered-solutions.md).

## <a name="syntax"></a>Syntax

```shell
devenv /DoNotLoadProjects SolutionName
```

## <a name="arguments"></a>Argumente

*SolutionName*

Erforderlich. Der vollständige Pfad und Name der Projektmappe, die geöffnet werden soll.

## <a name="example"></a>Beispiel

Im Beispiel wird die Projektmappe „MySln.sln“ geöffnet, ohne dass Projekte geladen werden.

```shell
devenv /donotloadprojects MySln.sln
```

## <a name="see-also"></a>Siehe auch

- [Gefilterte Projektmappen in Visual Studio](../filtered-solutions.md)
- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)
