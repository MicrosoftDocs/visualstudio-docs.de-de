---
title: Befehl "Arbeitsspeicher auflisten"
description: Hier erfahren Sie mehr über den Befehl „Arbeitsspeicher auflisten“ und darüber, wie der Inhalt des angegebenen Arbeitsspeicherbereichs angezeigt wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listmemory
helpviewer_keywords:
- Debug.ListMemory command
- ListMemory command
- list memory command
ms.assetid: a84de361-a6a6-4f6d-96aa-a0d4a424371e
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4fb0d62f6f4ade51fe0224917a1e3ec3a199de14
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852049"
---
# <a name="list-memory-command"></a>Befehl "Arbeitsspeicher auflisten"
Zeigt den Inhalt des angegebenen Speicherbereichs an.

## <a name="syntax"></a>Syntax

```cmd
Debug.ListMemory [/ANSI|Unicode] [/Count:number] [/Format:formattype]
[/Hex|Signed|Unsigned] [expression]
```

## <a name="arguments"></a>Argumente
`expression`

Dies ist optional. Die Speicheradresse, ab der die Anzeige des Arbeitsspeicher begonnen werden soll

## <a name="switches"></a>Switches
/ANSI|Unicode

Optional. Zeigen Sie den Arbeitsspeicher als Zeichen an, die den Bytes im Arbeitsspeicher entsprechen, entweder als ANSI- oder Unicode-Zeichen.

/Count:`number`

Optional. Bestimmt, wie viele Byte Arbeitsspeicher angezeigt werden, beginnend bei `expression`.

/Format:`formattype`

Optional. Formattypen für das Anzeigen von Speicherinformationen im Fenster **Arbeitsspeicher**; entweder OneByte, TwoBytes, FourBytes, EightBytes, Float (32-Bit), oder Double (64-Bit). Wenn OneByte verwendet wird, ist `/Unicode` nicht verfügbar.

/Hex|Signed|Unsigned

Optional. Gibt das Format zum Anzeigen von Zahlen an: mit Vorzeichen, ohne Vorzeichen oder hexadezimal.

## <a name="remarks"></a>Bemerkungen
Anstatt einen kompletten **Debug.ListMemory**-Befehl mit allen Schaltern zu schreiben, können Sie den Befehl mithilfe vordefinierter Aliase aufrufen, bei denen bestimmte Schalter auf angegebene Werte voreingestellt werden. Anstatt z.B. Folgendes einzugeben:

```cmd
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

Können Sie Folgendes schreiben:

```cmd
>df /Count:30 /Unicode
```

Hier finden Sie eine Liste vorhandener Aliase für den **Debug.ListMemory**-Befehl:

|Alias|Befehl und Schalter|
|-----------| - |
|**d**|Debug.ListMemory|
|**da**|Debug.ListMemory /Ansi|
|**db**|Debug.ListMemory /Format:OneByte|
|**dc**|Debug.ListMemory /Format:FourBytes /Ansi|
|**dd**|Debug.ListMemory /Format:FourBytes|
|**df**|Debug.ListMemory /Format:Float|
|**dq**|Debug.ListMemory /Format:EightBytes|
|**du**|Debug.ListMemory /Unicode|

## <a name="example"></a>Beispiel

```cmd
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

## <a name="see-also"></a>Siehe auch

- [Befehl "Aufrufliste auflisten"](../../ide/reference/list-call-stack-command.md)
- [Befehl "Threads auflisten"](../../ide/reference/list-threads-command.md)
- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
