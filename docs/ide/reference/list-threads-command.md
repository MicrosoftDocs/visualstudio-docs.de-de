---
title: Befehl "Threads auflisten"
description: Hier erfahren Sie mehr über den Befehl „Threads auflisten“ und darüber, wie damit eine Liste der Threads im aktuellen Programm angezeigt wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f3abcd7182c8bb5b94b2f35a9463f845cc6bb5bd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919383"
---
# <a name="list-threads-command"></a>Befehl "Threads auflisten"
Zeigt eine Liste der Threads im aktuellen Programm an.

## <a name="syntax"></a>Syntax

```
Debug.ListThreads [index]
```

## <a name="arguments"></a>Argumente
`index`

Dies ist optional. Wählt einen Thread nach seinem Index als aktuellen Thread aus

## <a name="remarks"></a>Bemerkungen
Wenn angegeben, kennzeichnet das `index`-Argument den angegebenen Thread als aktuellen Thread. Ein Sternchen (*) wird in der Liste neben dem aktuellen Thread angezeigt.

## <a name="example"></a>Beispiel

```
>Debug.ListThreads
```

## <a name="see-also"></a>Siehe auch

- [Befehl "Aufrufliste auflisten"](../../ide/reference/list-call-stack-command.md)
- [Befehl "Disassemblierung auflisten"](../../ide/reference/list-disassembly-command.md)
- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
