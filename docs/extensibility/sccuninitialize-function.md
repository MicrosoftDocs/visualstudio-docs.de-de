---
title: Sccuninitialize-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e7de3572b17bf47859a64451149a269988c91e5c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836682"
---
# <a name="sccuninitialize-function"></a>SccUninitialize-Funktion
Diese Funktion bereinigt alle Zuordnungen oder geöffneten Verbindungen, die durch einen vorherigen [sccinitialize](../extensibility/sccinitialize-function.md) -aufrufungstyp erstellt wurden, um das Quellcodeverwaltungs-Plug-in zu schließen.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccUninitialize (
   LPVOID pvContext
);
```

#### <a name="parameters"></a>Parameter
 pvcontext

in Der Zeiger auf die Kontext Struktur des Quellcodeverwaltungs-Plug-ins, die in [sccinitialize](../extensibility/sccinitialize-function.md)erstellt wurde.

## <a name="return-value"></a>Rückgabewert
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:

|Wert|Beschreibung|
|-----------|-----------------|
|SCC_OK|Die Bereinigung wurde erfolgreich abgeschlossen.|

## <a name="remarks"></a>Bemerkungen
 Das Quellcodeverwaltungs-Plug-in ist dafür verantwortlich, das Herunterfahren vorzubereiten und Arbeitsspeicher freizugeben, den das Plug-in für die Kontext Struktur zugewiesen hat. Die-Funktion wird einmal für jede angegebene Instanz eines Plug-Ins aufgerufen. Ein [sccinitialize](../extensibility/sccinitialize-function.md) -aufruftritt vor diesem-Befehl auf. Zum Zeitpunkt des Aufrufes können noch keine Projekte geöffnet werden `SccUninitialize` .

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
