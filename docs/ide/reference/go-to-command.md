---
title: Befehl "Gehe zu"
description: Hier erfahren Sie mehr über den Befehl „Gehe zu“ und darüber, wie der Cursor damit in die angegebene Zeile verschoben wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 29f81e5a17a573fdca25482479111a9f83e95a16
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946448"
---
# <a name="go-to-command"></a>Gehe zu (Befehl)
Bewegt den Cursor in die angegebene Zeile.

## <a name="syntax"></a>Syntax

```cmd
Edit.GoTo [linenumber]
```

## <a name="arguments"></a>Argumente
`linenumber`\
Dies ist optional. Eine ganze Zahl, die die Zeilennummer, zu der Sie springen wollen, angibt.

## <a name="remarks"></a>Bemerkungen
Die Zeilennummerierung beginnt bei eins. Wenn der Wert von `linenumber` kleiner als eins ist, wird die erste Zeile angezeigt. Wenn der Wert von `linenumber` größer als die Nummer der letzten Zeile ist, wird die letzte Zeile angezeigt.

Wenn für `linenumber` kein Wert angegeben wird, wird das **Gehe zu Zeile**-Dialogfeld angezeigt.

Der Alias dieses Befehls lautet „GoToLn“.

## <a name="example"></a>Beispiel

```cmd
>Edit.GoTo 125
```

## <a name="see-also"></a>Weitere Informationen

- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
