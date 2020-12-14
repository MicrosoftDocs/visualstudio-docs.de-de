---
title: Befehl "Aktuellen Stapelrahmen festlegen"
description: Hier erfahren Sie mehr über den SetCurrentStackFrame-Befehl sowie darüber, wie Sie damit einen bestimmten Stapelrahmen festlegen können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setcurrentstackframe
helpviewer_keywords:
- Set Current Stack Frame command
- Debug.SetCurrentStackFrame command
ms.assetid: 3dcf52c0-6781-4598-bac2-0094dce67c20
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 032602744247ded5cb38d8a3ae3e1157ccbc5cee
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616602"
---
# <a name="set-current-stack-frame-command"></a>Befehl "Aktuellen Stapelrahmen festlegen"
Ermöglicht das Festlegen eines bestimmten Stapelrahmens.

## <a name="syntax"></a>Syntax

```cmd
Debug.SetCurrentStackFrame index
```

## <a name="arguments"></a>Argumente
`index`

Erforderlich. Wählt einen Stapelrahmen über dessen Index aus.

## <a name="example"></a>Beispiel

```cmd
>Debug.SetCurrentStackFrame 1
```

## <a name="see-also"></a>Weitere Informationen

- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)