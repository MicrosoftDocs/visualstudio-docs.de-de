---
title: Befehl "Registrierungen auflisten"
description: Hier erfahren Sie mehr über den Befehl „Registrierungen auflisten“ und darüber, wie dieser die Werte ausgewählter Register anzeigt und wie Sie die Liste der angezeigten Register ändern können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listregisters
helpviewer_keywords:
- list registers command
- Debug.ListRegisters command
- ListRegisters command
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0168f8e4b6c04ea0d6b675ce6c280bd8140971b7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919569"
---
# <a name="list-registers-command"></a>Befehl "Registrierungen auflisten"
Zeigt den Wert des ausgewählten Registers an und ermöglicht es Ihnen, die Liste der anzuzeigenden Register zu ändern

## <a name="syntax"></a>Syntax

```cmd
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]
[/Watch [{register|registerGroup}...]]
[/Unwatch [{register|registerGroup}...]]
```

## <a name="switches"></a>Switches
/Display [{`register`|`registerGroup`}...]

Zeigt die Werte des angegebenen `register` oder `registerGroup` an. Wenn weder `register` noch `registerGroup` angegeben ist, wird die Standardregisterliste angezeigt. Wenn kein Schalter angegeben ist, ist das Verhalten identisch. Zum Beispiel:

`Debug.ListRegisters /Display eax`

für die folgende Syntax:

`Debug.ListRegisters eax`

/List

Zeigt alle Registergruppen in der Liste an

/Watch [{`register`|`registerGroup`}...]

Fügt der Liste einen oder mehrere `register`- oder `registerGroup`-Werte hinzu

/Unwatch [{`register`|`registerGroup`}...]

Entfernt einen oder mehrere `register`- oder `registerGroup`-Werte aus der Liste

## <a name="remarks"></a>Bemerkungen
Der Alias `r` kann anstelle von `Debug.ListRegisters` verwendet werden.

## <a name="example"></a>Beispiel
In diesem Beispiel wird das `Debug.ListRegisters`-Alias `r` verwendet, um die Werte der Registergruppe `Flags` anzuzeigen.

```cmd
r /Display Flags
```

## <a name="see-also"></a>Weitere Informationen

- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Debuggrundlagen: Registerfenster](../../debugger/debugging-basics-registers-window.md)
- [How to: Verwenden des Fensters „Register“](../../debugger/how-to-use-the-registers-window.md)
