---
description: Diese Funktion beendet einen Batch von Quell Code Verwaltungs Vorgängen.
title: Sccendbatch-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f4ea8ec19fcfe55da0666383408c2addbd42f2e6
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221573"
---
# <a name="sccendbatch-function"></a>Sccendbatch-Funktion
Diese Funktion beendet einen Batch von Quell Code Verwaltungs Vorgängen. Diese Batches dürfen nicht eingebettet werden.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccEndBatch(void);
```

## <a name="parameters"></a>Parameter
 Keine.

## <a name="return-value"></a>Rückgabewert
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Der Batch der Vorgänge wurde erfolgreich abgeschlossen.|
|SCC_E_UNKNOWNERROR|Nicht spezifischer Fehler.|

## <a name="remarks"></a>Bemerkungen
 Quell Code Verwaltungs Batches werden verwendet, um dieselben Quell Code Verwaltungsvorgänge für mehrere Projekte oder mehrere Kontexte auszuführen. Batches können verwendet werden, um redundante Dialogfelder aus der Benutzer Darstellung während eines Batch Vorgangs auszuschließen. [Sccbeginbatch](../extensibility/sccbeginbatch-function.md) und die- `SccEndBatch` Funktion werden als Paar verwendet, um den Anfang und das Ende eines Vorgangs anzugeben. Sie können nicht eingefügt werden.

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen der Quellcodeverwaltungs-Plug-in](../extensibility/source-control-plug-in-api-functions.md)
- [SccBeginBatch](../extensibility/sccbeginbatch-function.md)
