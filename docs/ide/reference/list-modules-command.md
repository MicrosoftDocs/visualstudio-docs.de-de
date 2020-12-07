---
title: Befehl "Module auflisten"
description: Hier erfahren Sie mehr über den Befehl „Module auflisten“ und darüber, wie dieser die Module für den aktuellen Prozess auflistet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listmodules
helpviewer_keywords:
- Debug.ListModules command
- ListModules command
- list modules command
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fa0c3f6445a22ee80457e8a7f9f24fb7008f77ed
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305312"
---
# <a name="list-modules-command"></a>Befehl "Module auflisten"
Listet die Module für den aktuellen Prozess auf.

## <a name="syntax"></a>Syntax

```
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]
```

#### <a name="parameters"></a>Parameter
/Address:`yes|no`

Optional. Gibt an, ob die Speicheradressen der Module angezeigt werden sollen. Der Standardwert ist `yes`.

/Name:`yes|no`

Optional. Gibt an, ob die Namen der Module angezeigt werden sollen. Der Standardwert ist `yes`.

/Order:`yes|no`

Optional. Gibt an, ob die Reihenfolge der Module angezeigt werden soll. Der Standardwert ist `no`.

/Path:`yes|no`

Optional. Gibt an, ob die Pfade zu den Modulen angezeigt werden sollen. Der Standardwert ist `yes`.

/Process:`yes|no`

Optional. Gibt an, ob die Prozesse der Module angezeigt werden sollen. Der Standardwert ist `no`.

/SymbolFile:`yes|no`

Optional. Gibt an, ob die Symboldateien der Module angezeigt werden sollen. Der Standardwert ist `no`.

/SymbolStatus:`yes|no`

Optional. Gibt an, ob die Symbolstatus der Module angezeigt werden sollen. Der Standardwert ist `yes`.

/Timestamp:`yes|no`

Optional. Gibt an, ob der Zeitstempel der Module angezeigt werden soll. Der Standardwert ist `no`.

/Version:`yes|no`

Optional. Gibt an, ob die Versionen der Module angezeigt werden sollen. Der Standardwert ist `no`.

## <a name="example"></a>Beispiel
In diesem Beispiel werden die Modulnamen, -adressen und -zeitstempel für den aktuellen Prozess aufgeführt.

```
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no
```

## <a name="see-also"></a>Weitere Informationen

- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [How to: Verwenden des Modulfensters](../../debugger/how-to-use-the-modules-window.md)
