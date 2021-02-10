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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fb43d3a12e50d3f4a7af43721a5e93b769da28ea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907591"
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
