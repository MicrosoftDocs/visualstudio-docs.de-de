---
title: Befehl „Einstellungen importieren und exportieren“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6e3ee8549fd8cf1a4551818c013551ba24128f95
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671053"
---
# <a name="import-and-export-settings-command"></a>Befehl Einstellungen importieren und exportieren
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Importiert, exportiert oder setzt [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]-Einstellungen zurück

## <a name="syntax"></a>Syntax

```
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]
```

## <a name="switches"></a>Schalter
 /export:`filename` ist optional. Exportiert die aktuellen Einstellungen in eine angegebene Datei

 /Import: `filename` optional. Importiert die aktuellen Einstellungen in eine angegebene Datei

 /reset ist optional. Setzt die aktuellen Einstellungen zurück

## <a name="remarks"></a>Bemerkungen
 Wenn Sie diesen Befehl ohne Schalter ausführen, wird der Assistent **Einstellungen importieren und exportieren** geöffnet. Weitere Informationen finden Sie unter [Vorgehensweise: Freigeben von Einstellungen zwischen Computern oder Visual Studio-Versionen](https://msdn.microsoft.com/1131fb10-35c1-42da-9cd8-91aa3235b882).

## <a name="example"></a>Beispiel
 Der folgende Befehl exportiert die aktuellen Einstellungen in die Datei `MyFile.vssettings`.

```
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```

## <a name="see-also"></a>Weitere Informationen
 [Anpassen von Entwicklungseinstellungen in Visual](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) Studio [Visual Studio-Befehlen](../../ide/reference/visual-studio-commands.md)
