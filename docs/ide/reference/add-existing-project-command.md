---
title: Befehl "Vorhandenes Projekt hinzufügen"
description: Informieren Sie sich über den Befehl „Vorhandenes Projekt hinzufügen“ und darüber, wie er ein vorhandenes Projekt einer aktuellen Projektmappe hinzufügt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 30e2daae72dfd3b5d5a08847ddf87b93d1810a37
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956671"
---
# <a name="add-existing-project-command"></a>Befehl "Vorhandenes Projekt hinzufügen"
Fügt der aktuellen Projektmappe ein vorhandenes Projekt hinzu.

## <a name="syntax"></a>Syntax

```cmd
File.AddExistingProject filename
```

## <a name="arguments"></a>Argumente
`filename`\
Dies ist optional. Der vollständige Pfad und der Projektname des Projekts mit Erweiterung, die der Projektmappe hinzugefügt werden sollen.

Wenn das `filename`-Argument Leerzeichen enthält, muss es in Anführungszeichen stehen.

Wenn kein Dateiname angegeben ist, öffnet der Befehl das Dialogfeld „Datei“, damit der Benutzer ein Projekt auswählen kann.

## <a name="remarks"></a>Hinweise
Bei der automatischen Vervollständigung wird während der Eingabe versucht, den richtigen Pfad und Dateinamen zu finden.

## <a name="example"></a>Beispiel
In diesem Beispiel wird das [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]-Projekt, TestProject1, der aktuellen Projektmappe hinzugefügt.

```cmd
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"
```

## <a name="see-also"></a>Weitere Informationen

- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
