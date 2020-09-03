---
title: Befehl "Disassemblierung auflisten"
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
ms.openlocfilehash: 91319a8d25aaec6bdd676ed6d709dffc47100195
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85770644"
---
# <a name="list-disassembly-command"></a>Befehl "Disassemblierung auflisten"
Startet den Debugprozess und ermöglicht es, die Behebung von Fehlern festzulegen.

## <a name="syntax"></a>Syntax

```cmd
Debug.ListDisassembly [/count:number] [/endaddress:expression]
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]
[/linenumbers:yes|no]
```

## <a name="switches"></a>Schalter
Jeder Schalter kann sowohl mit der vollständigen als auch mit der Kurzform aufgerufen werden.

/count: `number` [oder] /c: `number` [oder] /length: `number` [oder] /l: `number`

Dies ist optional. Anzahl der anzuzeigenden Anweisungen. Der Standardwert ist 8.

/endaddress: `expression` [oder] /e: `expression`

Dies ist optional. Adresse, an der die Disassemblierung beendet wird.

/codebytes:`yes`|`no` [oder] /bytes:`yes`|`no` [oder] /b:`yes`|`no`

Dies ist optional. Gibt an, ob Codebytes angezeigt werden sollen. Der Standardwert lautet `no`.

/source:`yes`|`no` [oder] /s:`yes`|`no`

Dies ist optional. Gibt an, ob Quellcode angezeigt werden soll. Der Standardwert lautet `no`.

/symbolnames:`yes`|`no` [oder] /names:`yes`|`no` [oder] /n:`yes`|`no`

Dies ist optional. Gibt an, ob Symbolnamen angezeigt werden sollen. Der Standardwert lautet `yes`.

 [/linenumbers:`yes`|`no`]

Dies ist optional. Ermöglicht das Anzeigen von dem Quellcode zugeordneten Zeilennummern. Der Schalter „/source“ muss den Wert `yes` haben, um den Schalter „/linenumbers“ zu verwenden.

## <a name="example"></a>Beispiel

```cmd
>Debug.ListDisassembly
```

## <a name="see-also"></a>Weitere Informationen

- [Befehl "Aufrufliste auflisten"](../../ide/reference/list-call-stack-command.md)
- [Threads auflisten (Befehl)](../../ide/reference/list-threads-command.md)
- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)