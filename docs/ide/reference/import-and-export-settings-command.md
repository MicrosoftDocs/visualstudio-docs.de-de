---
description: Importiert oder exportiert Visual Studio-Einstellungen oder setzt diese zurück.
title: Befehl Einstellungen importieren und exportieren
ms.date: 11/21/2018
ms.topic: reference
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0f2ea4811af2c44277b9a6dc285972c5267b28d7
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223671"
---
# <a name="import-and-export-settings-command"></a>Befehl Einstellungen importieren und exportieren

Importiert oder exportiert Visual Studio-Einstellungen oder setzt diese zurück.

## <a name="syntax"></a>Syntax

```cmd
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]
```

## <a name="switches"></a>Switches

/export:`filename`

(Optional) Exportiert die aktuellen Einstellungen in eine angegebene Datei

/import:`filename`

(Optional) Importiert die aktuellen Einstellungen in eine angegebene Datei

/reset

(Optional) Setzt die aktuellen Einstellungen zurück

## <a name="remarks"></a>Hinweise

Wenn Sie diesen Befehl ohne Schalter ausführen, wird der Assistent **Einstellungen importieren und exportieren** geöffnet. Weitere Informationen finden Sie unter [Synchronisieren der Einstellungen](../synchronized-settings-in-visual-studio.md) und [Umgebungseinstellungen](../environment-settings.md).

## <a name="example"></a>Beispiel

Der folgende Befehl exportiert die aktuellen Einstellungen in die Datei `MyFile.vssettings`:

```cmd
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```

## <a name="see-also"></a>Weitere Informationen

- [Umgebungseinstellungen](../../ide/environment-settings.md)
- [Synchronisieren der Einstellungen](../../ide/synchronized-settings-in-visual-studio.md)
- [Personalisieren der Visual Studio-IDE](../../ide/personalizing-the-visual-studio-ide.md)
- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
