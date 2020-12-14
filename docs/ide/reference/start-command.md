---
title: Befehl "Start"
description: Hier erfahren Sie mehr über den Start-Befehl sowie darüber, wie damit das Debuggen des Startprojekts gestartet wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d6d9e1e36a2790fb63f9d39c0c83d67d889cc0a8
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616420"
---
# <a name="start-command"></a>Befehl "Start"
Startet das Debuggen des Startup-Projekts.

## <a name="syntax"></a>Syntax

```cmd
Debug.Start [address]
```

## <a name="arguments"></a>Argumente
`address`

Dies ist optional. Die Adresse, an der das Programm die Ausführung anhält, ähnlich wie ein Breakpoint im Quellcode. Dieses Argument ist nur im Debugmodus gültig.

## <a name="remarks"></a>Bemerkungen
Der Befehl **Start** führt bei der Ausführung einen RunToCursor-Vorgang auf die angegebene Adresse aus.

## <a name="example"></a>Beispiel
In diesem Beispiel wird der Debugger gestartet und ignoriert alle auftretenden Ausnahmen.

```cmd
>Debug.Start
```

## <a name="see-also"></a>Weitere Informationen

- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
