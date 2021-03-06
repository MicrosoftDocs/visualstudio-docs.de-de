---
description: Diese Funktion gibt zusätzliche Funktionen zurück, die vom Quellcodeverwaltungs-Plug-in unterstützt werden.
title: Sccgetextendedfunctions-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e1409753559088c0f8129ebacd17387bfb7d111e
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102220780"
---
# <a name="sccgetextendedcapabilities-function"></a>Sccgetextendedfunctions-Funktion
Diese Funktion gibt zusätzliche Funktionen zurück, die vom Quellcodeverwaltungs-Plug-in unterstützt werden.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccGetExtendedCapabilities(
   LPVOID pContext,
   LONG lSccExCaps,
   LPBOOL pbSupported
);
```

### <a name="parameters"></a>Parameter
 pContext

in Der Kontext Zeiger für das Quellcodeverwaltungs-Plug-in.

 lsccexcaps

in Ein Flag, das eine erweiterte Funktion angibt, die getestet werden soll (Weitere Informationen finden Sie in der Code Tabelle für erweiterte Funktionen in [funktionsflags](../extensibility/capability-flags.md) für die möglichen Flags).

 pbsupported

vorgenommen Gibt einen Wert ungleich 0 (NULL `TRUE` ) zurück, wenn die angegebene Funktion unterstützt wird; andernfalls wird NULL () zurückgegeben `FALSE` .

## <a name="return-value"></a>Rückgabewert
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Der Vorgang "Get Capability" wurde erfolgreich abgeschlossen.|
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Unbekannter oder nicht angegebener Fehler.|

## <a name="remarks"></a>Bemerkungen
 Diese Methode wird bei Bedarf aufgerufen. Das heißt, wenn eine Funktion getestet werden muss, wird diese Methode aufgerufen, um zu bestimmen, ob diese Funktion unterstützt wird. Es wird nur jeweils ein Flag angegeben.

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen der Quellcodeverwaltungs-Plug-in](../extensibility/source-control-plug-in-api-functions.md)
- [Fehlercodes](../extensibility/error-codes.md)
- [Funktionsflags](../extensibility/capability-flags.md)
