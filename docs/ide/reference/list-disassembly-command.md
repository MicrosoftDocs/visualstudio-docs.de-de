---
title: Befehl "Disassemblierung auflisten"
description: Hier erfahren Sie mehr über den Befehl „Disassembly auflisten“ und darüber, wie damit der Debugvorgang gestartet und das Vorgehen bei der Fehlerbehandlung angegeben wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 15e9016551b178b0a29656e615d029ddaf0ca279
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305341"
---
# <a name="list-disassembly-command"></a>Befehl "Disassemblierung auflisten"
Startet den Debugprozess und ermöglicht es, die Behebung von Fehlern festzulegen.

## <a name="syntax"></a>Syntax

```cmd
Debug.ListDisassembly [/count:number] [/endaddress:expression]
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]
[/linenumbers:yes|no]
```

## <a name="switches"></a>Switches
Jeder Schalter kann sowohl mit der vollständigen als auch mit der Kurzform aufgerufen werden.

/count: `number` [oder] /c: `number` [oder] /length: `number` [oder] /l: `number`

Optional. Anzahl der anzuzeigenden Anweisungen. Der Standardwert ist 8.

/endaddress: `expression` [oder] /e: `expression`

Optional. Adresse, an der die Disassemblierung beendet wird.

/codebytes:`yes`|`no` [oder] /bytes:`yes`|`no` [oder] /b:`yes`|`no`

Optional. Gibt an, ob Codebytes angezeigt werden sollen. Der Standardwert ist `no`.

/source:`yes`|`no` [oder] /s:`yes`|`no`

Optional. Gibt an, ob Quellcode angezeigt werden soll. Der Standardwert ist `no`.

/symbolnames:`yes`|`no` [oder] /names:`yes`|`no` [oder] /n:`yes`|`no`

Optional. Gibt an, ob Symbolnamen angezeigt werden sollen. Der Standardwert ist `yes`.

 [/linenumbers:`yes`|`no`]

Optional. Ermöglicht das Anzeigen von dem Quellcode zugeordneten Zeilennummern. Der Schalter „/source“ muss den Wert `yes` haben, um den Schalter „/linenumbers“ zu verwenden.

## <a name="example"></a>Beispiel

```cmd
>Debug.ListDisassembly
```

## <a name="see-also"></a>Siehe auch

- [Befehl "Aufrufliste auflisten"](../../ide/reference/list-call-stack-command.md)
- [Befehl "Threads auflisten"](../../ide/reference/list-threads-command.md)
- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)