---
title: Befehl "Überwachung"
description: Hier erfahren Sie mehr über den Befehl „Watch“ und darüber, wie dieser eine angegebene Instanz des Überwachungsfensters erstellt und öffnet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 631c9cf61e6da70b3c7554a1aac0cacc8eef0294
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480147"
---
# <a name="watch-command"></a>Befehl "Überwachung"
Erstellt und öffnet eine angegebene Instanz des Fensters **Überwachen** . Sie können das Fenster **Überwachen** verwenden, um die Werte von Variablen, Ausdrücken und Registern zu berechnen, um diese Werte zu berechnen und die Ergebnisse zu speichern.

## <a name="syntax"></a>Syntax

```cmd
Debug.Watch[index]
```

## <a name="arguments"></a>Argumente

`index`\
Erforderlich. Die Instanznummer des Fensters „Überwachen“.

## <a name="remarks"></a>Bemerkungen

Der `index` muss eine ganze Zahl sein. Gültige Werte sind 1, 2, 3 oder 4.

## <a name="example"></a>Beispiel

```cmd
>Debug.Watch1
```

## <a name="see-also"></a>Siehe auch

- [Fenster „Auto“ und „Lokal“](../../debugger/autos-and-locals-windows.md)
- [Set a Watch on Variables using the Watch and QuickWatch Windows in Visual Studio (Festlegen einer Überwachung von Variablen in den Fenstern „Überwachung“ und „Schnellüberwachung“ in Visual Studio)](../../debugger/watch-and-quickwatch-windows.md)
- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
