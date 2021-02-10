---
title: Sccbackgroundget-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6d081389124b8703958f82cb97fc877f9f812290
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952121"
---
# <a name="sccbackgroundget-function"></a>Sccbackgroundget-Funktion
Diese Funktion ruft jede der angegebenen Dateien ohne Benutzerinteraktion aus der Quell Code Verwaltung ab.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccBackgroundGet(
   LPVOID  pContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LONG    dwFlags,
   LONG    dwBackgroundOperationID
);
```

### <a name="parameters"></a>Parameter
 pContext

in Der Kontext Zeiger für das Quellcodeverwaltungs-Plug-in.

 nnoch

in Anzahl der im Array angegebenen Dateien `lpFileNames` .

 lpfile-Namen

[in, out] Ein Array von Namen von Dateien, die abgerufen werden sollen.

> [!NOTE]
> Die Namen müssen voll qualifizierte lokale Dateinamen sein.

 dwFlags

in Befehlsflags ( `SCC_GET_ALL` , `SCC_GET_RECURSIVE` ).

 dwbackgroundoperationid

in Ein eindeutiger Wert, der diesem Vorgang zugeordnet ist.

## <a name="return-value"></a>Rückgabewert
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Operation erfolgreich abgeschlossen.|
|SCC_E_BACKGROUNDGETINPROGRESS|Ein Hintergrund Abruf wird bereits ausgeführt (das Quellcodeverwaltungs-Plug-in sollte dieses Element nur zurückgeben, wenn es keine gleichzeitigen Batch Vorgänge unterstützt).|
|SCC_I_OPERATIONCANCELED|Der Vorgang wurde abgebrochen, bevor er abgeschlossen wurde.|

## <a name="remarks"></a>Bemerkungen
 Diese Funktion wird immer in einem Thread aufgerufen, der sich von dem unterscheidet, der das Quellcodeverwaltungs-Plug-in geladen hat. Diese Funktion wird nicht erwartungsgemäß zurückgegeben, bis Sie abgeschlossen ist. Sie kann jedoch mehrmals mit mehreren Listen von Dateien aufgerufen werden, die alle gleichzeitig sind.

 Die Verwendung des- `dwFlags` Arguments ist mit dem [sccget](../extensibility/sccget-function.md)identisch.

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen der Quellcodeverwaltungs-Plug-in](../extensibility/source-control-plug-in-api-functions.md)
- [SccGet](../extensibility/sccget-function.md)
