---
description: Diese Funktion Listet eine angegebene Liste von Dateien auf, die Informationen über Namensänderungen für jede Datei über eine Rückruffunktion bereitstellt.
title: Sccquerychanges-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e34c37ca999b05e7148d910032fe90c33470ce50
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102220520"
---
# <a name="sccquerychanges-function"></a>SccQueryChanges-Funktion
Diese Funktion Listet eine angegebene Liste von Dateien auf, die Informationen über Namensänderungen für jede Datei über eine Rückruffunktion bereitstellt.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccQueryChanges(
   LPVOID           pContext,
   LONG             nFiles,
   LPCSTR*          lpFileNames,
   QUERYCHANGESFUNC pfnCallback,
   LPVOID           pvCallerData
);
```

#### <a name="parameters"></a>Parameter
 pContext

in Der Kontext Zeiger für das Quellcodeverwaltungs-Plug-in.

 nnoch

in Anzahl der Dateien im `lpFileNames` Array.

 lpfile-Namen

in Array von Dateinamen, über die Informationen erhalten werden.

 pfncallback

in Rückruffunktion, die für jeden Dateinamen in der Liste aufgerufen werden soll (Weitere Informationen finden Sie unter [querychangesfunc](../extensibility/querychangesfunc.md) ).

 pvcallerdata

in Der Wert, der unverändert an die Rückruffunktion übermittelt wird.

## <a name="return-value"></a>Rückgabewert
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Der Abfrageprozess wurde erfolgreich abgeschlossen.|
|SCC_E_PROJNOTOPEN|Das Projekt wurde nicht in der Quell Code Verwaltung geöffnet.|
|SCC_E_ACCESSFAILURE|Beim Zugriff auf das Quell Code Verwaltungssystem ist ein Problem aufgetreten, wahrscheinlich aufgrund von Netzwerk-oder Konflikt Problemen.|
|SCC_E_NONSPECIFICERROR|Ein nicht spezifizierter oder allgemeiner Fehler ist aufgetreten.|

## <a name="remarks"></a>Bemerkungen
 Änderungen, die abgefragt werden, sind der Namespace: das Umbenennen, hinzufügen und Entfernen einer Datei.

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)
- [Fehlercodes](../extensibility/error-codes.md)
