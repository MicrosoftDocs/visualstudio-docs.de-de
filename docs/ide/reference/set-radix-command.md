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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 50d0097debbd7e91906202b85e8e9e6dab36a27d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957685"
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