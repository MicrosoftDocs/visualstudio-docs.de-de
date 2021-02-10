---
title: Popdirlistfunc | Microsoft-Dokumentation
description: Erfahren Sie mehr über die popdirlistfunc-Rückruffunktion, die an Update Verzeichnisse übermittelt wird, um herauszufinden, welche unter Quell Code Verwaltung stehen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: da499ee9bbdcdff95456a4e4d5f5dc63f2acfb2c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967396"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
Dies ist eine Rückruffunktion, die der [sccpopulatedirlist](../extensibility/sccpopulatedirlist-function.md) -Funktion übergeben wird, um eine Auflistung von Verzeichnissen und (optional) Dateinamen zu aktualisieren, die sich unter Quell Code Verwaltung befinden.

 Der `POPDIRLISTFUNC` Rückruf sollte nur für die Verzeichnisse und Dateinamen (in der für die Funktion angegebenen Liste) aufgerufen werden `SccPopulateDirList` , die sich tatsächlich unter Quell Code Verwaltung befinden.

## <a name="signature"></a>Signatur

```cpp
typedef BOOL (*POPDIRLISTFUNC)(
   LPVOID pvCallerData,
   BOOL bFolder,
   LPCSTR lpDirectoryOrFileName
);
```

## <a name="parameters"></a>Parameter
 pvcallerdata

in Benutzer Wert, der [sccpopulatedirlist](../extensibility/sccpopulatedirlist-function.md)zugewiesen ist.

 bfolder

[in] `TRUE` , wenn der Name in `lpDirectoryOrFileName` ein Verzeichnis ist, andernfalls ist der Name ein Dateiname.

 lpdirector yorfilename

in Vollständiger lokaler Pfad zu einem Verzeichnis-oder Dateinamen, der sich unter Quell Code Verwaltung befindet.

## <a name="return-value"></a>Rückgabewert
 Die IDE gibt einen entsprechenden Fehlercode zurück:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Setzen Sie die Verarbeitung fort.|
|SCC_I_OPERATIONCANCELED|Beendet die Verarbeitung.|
|SCC_E_xxx|Jeder geeignete Quell Code Verwaltungsfehler sollte die Verarbeitung verhindern.|

## <a name="remarks"></a>Bemerkungen
 Wenn der- `fOptions` Parameter der `SccPopulateDirList` Funktion das- `SCC_PDL_INCLUDEFILES` Flag enthält, enthält die Liste möglicherweise Dateinamen und Verzeichnisnamen.

## <a name="see-also"></a>Weitere Informationen
- [Von der IDE implementierte Rückruf Funktionen](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)
- [Fehlercodes](../extensibility/error-codes.md)
