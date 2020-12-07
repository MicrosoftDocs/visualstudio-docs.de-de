---
title: -UseEnv („devenv.exe“)
description: Hier erfahren Sie, wie Sie mit der devenv-Befehlszeilenoption „UseEnv“ Visual Studio starten und bestimmte Umgebungsvariablen für die Kompilierung laden.
ms.custom: SEO-VS-2020
ms.date: 01/10/2019
ms.topic: reference
f1_keywords:
- VC.Project.UseEnvVars.ExcludePath
- VC.Project.UseEnvVars.LibraryPath
- VC.Project.UseEnvVars.SourcePath
- VC.Project.UseEnvVars.Include
- VC.Project.UseEnvVars.Path
- VC.Project.UseEnvVars.ReferencePath
helpviewer_keywords:
- UseEnv switch
- /UseEnv Devenv switch
- Devenv, /UseEnv
ms.assetid: 2dd14603-a61b-42d2-ba31-427a0ee8a799
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 51b47156b73d81f427c08e62006dc6e457e5780b
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040939"
---
# <a name="useenv-devenvexe"></a>/UseEnv (devenv.exe)

Startet Visual Studio und lädt bestimmte Umgebungsvariablen für die Kompilierung.

> [!NOTE]
> Dieser Schalter wird mit der Workload **Desktopentwicklung mit C++** installiert.

## <a name="syntax"></a>Syntax

```shell
devenv /UseEnv {SolutionName|ProjectName}
```

## <a name="arguments"></a>Argumente

- *SolutionName*

  Der vollständige Pfad und Name einer Projektmappendatei

- *Projektname*

  Der vollständige Pfad und Name einer Projektdatei

## <a name="remarks"></a>Bemerkungen

Dieser Schalter wirkt sich auf die Visual Studio-IDE in den Projekteigenschaften für **VC++-Verzeichnisse** aus. Wenn Sie den Schalter `/UseEnv` angeben, zeigt der Knoten **VC++-Verzeichnisse** die Werte für die Umgebungsvariablen PATH, INCLUDE, LIBPATH und LIB. (Er zeigt auch Werte für **Quellverzeichnisse** und **Ausschließbare Verzeichnisse**.) Andernfalls ersetzt der Knoten die Umgebungsvariablen durch fünf Verzeichniswerte: **Ausführbare Verzeichnisse**, **Includeverzeichnisse**, **Verweisverzeichnisse**, **Bibliotheksverzeichnisse** und **WinRT-Bibliotheksverzeichnisse**.

> [!TIP]
> Sie können auf die Projekteigenschaften zugreifen, indem Sie mit der rechten Maustaste auf ein C++-Projekt klicken und **Eigenschaften** auswählen. Wählen Sie im Dialogfeld **Eigenschaftenseiten** die Option **Konfigurationseigenschaften** und dann **VC++-Verzeichnisse** aus.

Wenn ein Projektname mit diesem Schalter angegeben wird, zeigt das Tool die Umgebungsvariablen für alle Projekte in der übergeordneten Projektmappe des Projekts an.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird Visual Studio gestartet, und die Umgebungsvariablen werden in die Eigenschaftenseiten der Projektmappe `MySolution` geladen.

```shell
devenv.exe /useenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Weitere Informationen

- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)
- [Eigenschaftenseite „VC++-Verzeichnisse“ (Windows)](/cpp/build/reference/vcpp-directories-property-page)
