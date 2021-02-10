---
title: Projekt öffnen (Befehl)
description: Hier erfahren Sie mehr über den Befehl „Projekt öffnen“ und darüber, wie dieser ein vorhandenes Projekt oder eine vorhandene Projektmappe öffnet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.openproject
- file.opensolution
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4298c840094f7f1f75e58be1b25213cdf66a6674
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881969"
---
# <a name="open-project-command"></a>Projekt öffnen (Befehl)

Öffnet ein vorhandenes Projekt oder eine vorhandene Projektmappe.

## <a name="syntax"></a>Syntax

```cmd
File.OpenProject filename
```

## <a name="arguments"></a>Argumente

`filename`

Erforderlich. Der vollständige Pfad und Dateiname des zu öffnenden Projekts oder der zu öffnenden Projektmappe.

> [!NOTE]
> Die Syntax für das Argument `filename` erfordert, dass Pfade, die Leerzeichen enthalten, in Anführungszeichen gesetzt werden.

## <a name="remarks"></a>Bemerkungen

Bei der automatischen Vervollständigung wird während der Eingabe versucht, den richtigen Pfad und Dateinamen zu finden.

Dieser Befehl ist während des Debuggens nicht verfügbar.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird das Visual Basic-Projekt **Test1** geöffnet:

```cmd
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"
```

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)
