---
title: -Upgrade („devenv.exe“)
description: Hier erfahren Sie, wie Sie mithilfe der devenv-Befehlszeilenoption „Upgrade“ die Projektmappendatei und alle zugehörigen Projektdateien oder die angegebene Projektdatei auf die aktuellen Visual Studio-Formate dieser Dateien aktualisieren.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /upgrade Devenv switch
- Devenv, /upgrade switch
- upgrade Devenv switch
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e7dc759cefae4ae262362265daf67ee5b1cb50f2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960558"
---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)

Aktualisiert die Projektmappendatei und alle zugehörigen Projektdateien bzw. die angegebene Projektdatei mit den aktuellen, für diese Dateien gültigen Visual Studio-Formaten.

## <a name="syntax"></a>Syntax

```shell
devenv {SolutionFile|ProjectFile} /Upgrade [/Out OutputFilename]
```

## <a name="arguments"></a>Argumente

- *SolutionFile*

  Dies ist erforderlich, sofern Sie eine vollständige Projektmappe und deren Projekte aktualisieren. Der Pfad und Name einer Projektmappendatei. Es reicht aus, nur den Namen der Projektmappendatei oder einen vollständigen Pfad und den Namen der Projektmappendatei einzugeben. Wenn der angegebene Ordner bzw. die Datei noch nicht vorhanden ist, wird der Ordner oder die Datei erstellt.

- *ProjectFile*

  Dies ist erforderlich, sofern Sie ein einzelnes Projekt aktualisieren. Der Pfad und der Name einer Projektdatei innerhalb der Projektmappe. Es reicht aus, nur den Namen der Projektdatei oder einen vollständigen Pfad und den Namen der Projektdatei einzugeben. Wenn der angegebene Ordner bzw. die Datei noch nicht vorhanden ist, wird der Ordner oder die Datei erstellt.

- `/Out` *OutputFilename*

  Dies ist optional. Der Name der Datei, an die die Ausgabe des Tools gesendet werden soll. Wenn die Datei bereits vorhanden ist, fügt das Tool die Ausgabe an das Ende der Datei an.

## <a name="remarks"></a>Hinweise

Es werden automatisch Sicherungen erstellt und in ein Verzeichnis mit der Bezeichnung „Backup“ kopiert, das im aktuellen Verzeichnis erstellt wird.

Der Quellcodeverwaltung unterliegende Projektmappen oder Projekte müssen ausgecheckt werden, bevor sie aktualisiert werden können.

Bei Verwendung des Schalters `/Upgrade` wird Visual Studio nicht geöffnet. Die Ergebnisse des Upgrades sind im Upgradebericht für die Entwicklungssprache der Projektmappe oder des Projekts aufgeführt. Informationen zu Fehlern oder zur Verwendung werden nicht zurückgegeben. Weitere Informationen zum Upgraden von Projekten in Visual Studio finden Sie unter [Übertragung, Migration und Upgrade der Visual Studio-Projekte](../../porting/port-migrate-and-upgrade-visual-studio-projects.md).

## <a name="example"></a>Beispiel

In diesem Beispiel wird eine Projektmappendatei mit dem Namen „MyProject.sln“ aktualisiert.

```shell
devenv "%USERPROFILE%\source\repos\MyProject\MyProject.sln" /upgrade
```

## <a name="see-also"></a>Weitere Informationen

- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)
