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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 805d7a5c9250bc511692c497bc9083852dad2301
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863446"
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

## <a name="remarks"></a>Hinweise
 Wenn der- `fOptions` Parameter der `SccPopulateDirList` Funktion das- `SCC_PDL_INCLUDEFILES` Flag enthält, enthält die Liste möglicherweise Dateinamen und Verzeichnisnamen.

## <a name="see-also"></a>Weitere Informationen
- [Von der IDE implementierte Rückruf Funktionen](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)
- [Fehlercodes](../extensibility/error-codes.md)
