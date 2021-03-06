---
title: OPTNAMECHANGEPFN | Microsoft-Dokumentation
description: Erfahren Sie mehr über die OPTNAMECHANGEPFN-Rückruffunktion, die Namensänderungen aus dem Quellcodeverwaltungs-Plug-in an die Visual Studio-IDE übermittelt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e583c7e19fb6123da06d0ee525abe9c573d8d788
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922887"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
Dies ist eine Rückruffunktion, die in einem aufzurufenden [sccsetoption](../extensibility/sccsetoption-function.md) -Operator (using-Option) angegeben wird `SCC_OPT_NAMECHANGEPFN` und zur Übermittlung von Namensänderungen verwendet wird, die vom Quellcodeverwaltungs-Plug-in an der IDE vorgenommen wurden.

## <a name="signature"></a>Signatur

```cpp
typedef void (*OPTNAMECHANGEPFN)(
   LPVOID pvCallerData,
   LPCSTR pszOldName,
   LPCSTR pszNewName
);
```

## <a name="parameters"></a>Parameter
 pvcallerdata

in Benutzer Wert, der in einem vorherigen [csetoption-aufrufswert](../extensibility/sccsetoption-function.md) (using-Option) angegeben wurde `SCC_OPT_USERDATA` .

 pszoldname

in Der ursprüngliche Name der Datei.

 psznewname

in Der Name, in den die Datei umbenannt wurde.

## <a name="return-value"></a>Rückgabewert
 Keine.

## <a name="remarks"></a>Bemerkungen
 Wenn eine Datei während eines Quell Code Verwaltungs Vorgangs umbenannt wird, kann das Quellcodeverwaltungs-Plug-in die IDE über diesen Rückruf über die Namensänderung benachrichtigen.

 Wenn die IDE diesen Rückruf nicht unterstützt, ruft Sie " [sccsetoption](../extensibility/sccsetoption-function.md) " nicht auf, um Sie anzugeben. Wenn das Plug-in diesen Rückruf nicht unterstützt, wird von der-Funktion zurückgegeben, `SCC_E_OPNOTSUPPORTED` `SccSetOption` Wenn die IDE versucht, den Rückruf festzulegen.

## <a name="see-also"></a>Weitere Informationen
- [Von der IDE implementierte Rückruf Funktionen](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
