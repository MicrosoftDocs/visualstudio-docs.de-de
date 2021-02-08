---
title: Sccgetversion-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 91daeca1df76f6b624d0eddf9d28222369b2cc4a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844540"
---
# <a name="sccgetversion-function"></a>SccGetVersion-Funktion
Diese Funktion Ruft die Versionsnummer der Quellcodeverwaltungs-Plug-in-API ab, die vom Quellcodeverwaltungs-Plug-in unterstützt wird.

## <a name="syntax"></a>Syntax

```cpp
LONG SccGetVersion(void);
```

#### <a name="parameters"></a>Parameter
 Keine.

## <a name="return-value"></a>Rückgabewert
 Ein `LONG` Datentyp, der die Versionsnummer der unterstützten Quellcodeverwaltungs-Plug-in-API enthält:

|WORD|Beschreibung|
|----------|-----------------|
|HIWORD|Hauptversion|
|LOWORD|Nebenversion|

## <a name="remarks"></a>Bemerkungen
 Wenn ein Quellcodeverwaltungs-Plug-in z. b. Version 1,3 der Quellcodeverwaltungs-Plug-in-API unterstützt, würde diese Funktion 0x0103 zurückgeben.

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
