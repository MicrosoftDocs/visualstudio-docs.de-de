---
title: Befehl "Wurzel setzen"
description: Hier erfahren Sie mehr über den SetRadix-Befehl sowie darüber, wie dieser die zum Anzeigen von ganzzahligen Werten verwendete numerische Basis festlegt oder zurückgibt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b47c30ed938a83a2b4c47f73f55b5f7ca1db6a62
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616407"
---
# <a name="set-radix-command"></a>Befehl "Wurzel setzen"
Legt die zum Anzeigen von ganzzahligen Werten verwendete numerische Basis fest bzw. gibt sie zurück.

## <a name="syntax"></a>Syntax

```cmd
Debug.SetRadix [10 | 16 | hex | dec]
```

## <a name="arguments"></a>Argumente
`10` oder `16` oder `hex` oder `dec`

Optional. Legt „dezimal“ (10 bzw. dec) oder „hexadezimal“ (16 bzw. hex) als Format fest. Wird ein Argument weggelassen, wird der aktuelle Wert der Wurzel zurückgegeben.

## <a name="example"></a>Beispiel
In diesem Beispiel wird die Umgebung zum Anzeigen ganzzahliger Werte im Hexadezimalformat konfiguriert.

```cmd
>Debug.SetRadix hex
```

## <a name="see-also"></a>Weitere Informationen

- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)