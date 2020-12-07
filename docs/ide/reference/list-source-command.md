---
title: Befehl "Quelle auflisten"
description: Hier erfahren Sie mehr über den Befehl „Quelle auflisten“ und darüber, wie dieser bestimmte Quellcodezeilen anzeigt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae2463a3d8dd295fcba9bf264e1ad3fa250169d4
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305280"
---
# <a name="list-source-command"></a>Befehl "Quelle auflisten"
Zeigt die angegebenen Quellcodezeilen an.

## <a name="syntax"></a>Syntax

```
Debug.ListSource [/Count:number] [/Current] [/File:filename]
[/Line:number] [/ShowLineNumbers:yes|no]
```

## <a name="switches"></a>Switches
/Count:`number`

Optional. Gibt die Anzahl der anzuzeigenden Zeilen an.

/Current

Optional. Zeigt die aktuelle Zeile an.

/File:`filename`

Optional. Pfad der anzuzeigenden Datei. Ist kein Dateiname angegeben, zeigt der Befehl den Quellcode für die Zeile der aktuellen Anweisung an.

/Line:`number`

Optional. Zeigt eine bestimmte Zeilennummer an.

/ShowLineNumbers:`yes|no`

Optional. Gibt an, ob Zeilennummern angezeigt werden sollen.

## <a name="example"></a>Beispiel
Dieses Beispiel listet den Quellcode aus Zeile 4 der Datei „Form1.vb“ mit eingeblendeten Zeilennummern an.

```
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes
```

## <a name="see-also"></a>Weitere Informationen

- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)