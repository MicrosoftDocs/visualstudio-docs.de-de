---
title: Befehl "Datei öffnen"
description: Hier erfahren Sie mehr über den Befehl „Datei öffnen“ und darüber, wie dieser eine vorhandene Datei öffnet und es Ihnen ermöglicht, einen Editor anzugeben.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.openfile
helpviewer_keywords:
- Open File command
- File.OpenFile command
- of command
ms.assetid: a51a83fc-e3c6-4fa2-8882-8b7b6c0a6406
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 96376c352d3019ba2efefc1f82e75e89a4ac2370
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935624"
---
# <a name="open-file-command"></a>Befehl „Datei öffnen“

Öffnet eine vorhandene Datei und ermöglicht die Angabe eines Editors.

## <a name="syntax"></a>Syntax

```cmd
File.OpenFile filename [/e:editorname]
```

## <a name="arguments"></a>Argumente

`filename`

Erforderlich. Der vollständige oder partielle Pfad und Dateiname der zu öffnenden Datei. Pfade, die Leerzeichen enthalten, müssen in Anführungszeichen eingeschlossen werden.

## <a name="switches"></a>Switches

/e:`editorname`

Dies ist optional. Der Name des Editors, in dem die Datei geöffnet wird. Wenn zwar das Argument, aber kein Editorname angegeben wurde, wird das Dialogfeld **Öffnen mit** angezeigt.

Die Argumentsyntax /e:`editorname` verwendet die Editornamen wie im Dialogfeld „Öffnen mit“ angezeigt, wobei der Name in Anführungszeichen eingeschlossen ist.

Geben Sie zum Öffnen einer Datei im Quellcode-Editor für das Argument /e:`editorname` beispielsweise Folgendes ein:

```cmd
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Bemerkungen

Bei der automatischen Vervollständigung wird während der Eingabe eines Pfads versucht, den richtigen Pfad und Dateinamen zu finden.

## <a name="example"></a>Beispiel

In diesem Beispiel wird die Stildatei „Test1.css“ im Quellcode-Editor geöffnet.

```cmd
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Direktfenster](../../ide/reference/immediate-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)
