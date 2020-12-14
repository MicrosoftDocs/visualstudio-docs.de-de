---
title: Befehl "Aktuellen Thread festlegen"
description: Hier erfahren Sie mehr über den SetCurrentThread-Befehl sowie darüber, wie damit der angegebene Thread als aktueller Thread festlegt wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setcurrentthread
helpviewer_keywords:
- Set Current Thread command
- Debug.SetCurrentThread command
ms.assetid: 9917ed1d-6c30-4d94-b2f0-69acce74f1b2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3cedd37ece7bcc0eb79ad52cc426b07f8cb2ca57
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616563"
---
# <a name="set-current-thread-command"></a>Befehl "Aktuellen Thread festlegen"
Legt den angegebenen Thread als aktuellen Thread fest.

## <a name="syntax"></a>Syntax

```
Debug.SetCurrentThread index
```

## <a name="arguments"></a>Argumente
`index`

Erforderlich. Wählt einen Thread nach seinem Index aus.

## <a name="example"></a>Beispiel

```
>Debug.SetCurrentThread 1
```

## <a name="see-also"></a>Weitere Informationen

- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)