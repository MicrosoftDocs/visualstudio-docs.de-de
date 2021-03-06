---
title: -Run („devenv.exe“)
description: Hier erfahren Sie, wie Sie das angegebene Projekt oder die angegebene Projektmappe mit der devenv-Befehlszeilenoption „Run“ kompilieren und ausführen.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /Run Devenv
- Run Devenv switch
- applications [Visual Studio], running
- /R Devenv switch
- Devenv, /Run switch
- R Devenv switch (/R)
ms.assetid: b1f22f9d-39a5-4918-8a2a-4b5c1e872665
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 34e9f50f864f8f2908a3822befda0652df6a3340
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957919"
---
# <a name="run-devenvexe"></a>/Run (devenv.exe)

Kompiliert das angegebene Projekt oder die angegebene Projektmappe und führt sie aus.

## <a name="syntax"></a>Syntax

```shell
devenv {/Run|/R} {SolutionName|ProjectName} [/Out OutputFilename]
```

## <a name="arguments"></a>Argumente

- *SolutionName*

  Der vollständige Pfad und Name einer Projektmappendatei

- *Projektname*

  Der vollständige Pfad und Name einer Projektdatei

- `/Out` *OutputFilename*

  Dies ist optional. Der Name der Datei, an die die Ausgabe des Tools gesendet werden soll. Wenn die Datei bereits vorhanden ist, fügt das Tool die Ausgabe an das Ende der Datei an.

## <a name="remarks"></a>Hinweise

Kompiliert das angegebene Projekt oder die angegebene Projektmappe entsprechend den Einstellungen, die für die aktive Projektmappenkonfiguration angegeben wurde, und führt sie aus. Dieser Schalter startet die IDE und lässt sie aktiviert, nachdem die Ausführung des Projekts oder der Projektmappe beendet wurde.

- Schließen Sie Zeichenfolgen, die Leerzeichen enthalten, in doppelte Anführungszeichen ein.

- Zusammenfassende Informationen inklusive Fehlermeldungen können im Fenster **Befehl** oder durch den `/Out`-Schalter in einer Protokolldatei angezeigt werden.

## <a name="example"></a>Beispiel

In diesem Beispiel wird die Projektmappe `MySolution` mithilfe der aktiven Bereitstellungskonfiguration ausgeführt.

```shell
devenv /run "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Weitere Informationen

- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)
- [/Runexit (devenv.exe)](../../ide/reference/runexit-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
