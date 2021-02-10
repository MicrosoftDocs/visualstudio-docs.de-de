---
title: Befehl "Aufrufliste auflisten"
description: Hier erfahren Sie mehr über den Befehl „Aufrufliste auflisten“ und wie damit die aktuelle Aufrufliste angezeigt wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listcallstack
helpviewer_keywords:
- list call stack command
- Debug.ListCallStack command
ms.assetid: a8b20bf2-81d2-4069-aea8-23e6b15b4347
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ccb55b1c00621f6e97c8f1297e2cedf2abebe73b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852101"
---
# <a name="list-call-stack-command"></a>Befehl "Aufrufliste auflisten"
Zeigt die aktuelle Aufrufliste an.

## <a name="syntax"></a>Syntax

```cmd
Debug.ListCallStack [/Count:number] [/ShowTypes:yes|no]
[/ShowNames:yes|no] [/ShowValues:yes|no] [/ShowModule:yes|no]
[/ShowLineOffset:yes|no] [/ShowByteOffset:yes|no]
[/ShowLanguage:yes|no] [/IncludeCallsAcrossThreads:yes|no]
[/ShowExternalCode:yes|no] [Thread:n] [index]
```

## <a name="arguments"></a>Argumente

`index`\
Dies ist optional. Legt den aktuellen Stapelrahmen fest, und zeigt keine Ausgabe an.

## <a name="switches"></a>Switches
Jeder Schalter kann sowohl mit der vollständigen als auch mit der Kurzform aufgerufen werden.

/Count:`number` [oder] /C:`number`

Optional. Maximale Anzahl der anzuzeigenden Aufruflisten. Der Standardwert ist unbegrenzt.

/ShowTypes:`yes`|`no` [oder] /T:`yes`|`no`

Optional. Gibt an, ob Parametertypen angezeigt werden sollen. Der Standardwert ist `yes`.

/ShowNames:`yes`|`no` [oder] /N:`yes`|`no`

Optional. Gibt an, ob Parameternamen angezeigt werden sollen. Der Standardwert ist `yes`.

/ShowValues:`yes`|`no` [oder] /V:`yes`|`no`

Optional. Gibt an, ob Parameterwerte angezeigt werden sollen. Der Standardwert ist `yes`.

/ShowModule:`yes`|`no` [oder] /M:`yes`|`no`

Optional. Gibt an, ob der Modulname angezeigt werden soll. Der Standardwert ist `yes`.

/ShowLineOffset:`yes`|`no` [oder] /#:`yes`|`no`

Optional. Gibt an, ob der Zeilenoffset angezeigt werden soll. Der Standardwert ist `no`.

/ShowByteOffset:`yes`|`no` [oder] /B:`yes`|`no`

Optional. Gibt an, ob der Byte-Offset angezeigt werden soll. Der Standardwert ist `no`.

/ShowLanguage:`yes`|`no` [oder] /L:`yes`|`no`

Optional. Gibt an, ob die Sprache angezeigt werden soll. Der Standardwert ist `no`.

/IncludeCallsAcrossThreads:`yes`|`no` [oder] /I:`yes`|`no`

Optional. Gibt an, ob angegeben werden soll, ob andere Threads aufgerufen werden oder selbst aufrufen. Der Standardwert ist `no`.

/ShowExternalCode:`yes`|`no`

Optional. Gibt an, ob für die Aufrufliste nur Benutzercode angezeigt werden soll. Wenn die Funktion „Nur eigenen Code“ deaktiviert ist, wird der gesamte nicht benutzerseitige Code angezeigt. Wenn diese Funktion aktiviert ist, wird nicht benutzerseitiger Code als `[external]` in der Ausgabe der Aufrufliste angezeigt.

Thread:`n`

Optional. Zeigt die Aufrufliste für den Thread `n` an. Wenn kein Thread angegeben ist, wird die Aufrufliste für den aktuellen Thread angezeigt.

## <a name="remarks"></a>Bemerkungen
Änderungen an den Argumenten oder Schaltern gelten bei zukünftigen Aufrufen dieses Befehls. Wenn Sie Debug.ListCallStackby selbst ausgeben, wird die gesamte Aufrufliste angezeigt. Wenn Sie beispielsweise einen Index angeben

```cmd
Debug.ListCallStack 2
```

wird der aktuelle Stapelrahmen auf diesen Frame festgelegt (in diesem Fall auf den zweiten Frame).

Sie können diesen Befehl auch mit dem vordefinierten Alias „kb“ schreiben. Sie können beispielsweise Folgendes eingeben:

```cmd
kb 2
```

um den aktuellen Stapelrahmen auf den zweiten Frame festzulegen.

## <a name="example"></a>Beispiel

```cmd
>Debug.CallStack /Count:4 /ShowTypes:yes
```

## <a name="see-also"></a>Siehe auch

- [Befehl "Disassemblierung auflisten"](../../ide/reference/list-disassembly-command.md)
- [Befehl "Threads auflisten"](../../ide/reference/list-threads-command.md)
- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)