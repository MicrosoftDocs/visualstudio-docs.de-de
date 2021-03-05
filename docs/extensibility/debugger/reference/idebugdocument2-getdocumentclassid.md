---
description: Ruft den Klassen Bezeichner des Dokuments ab.
title: 'IDebugDocument2:: getdocumentclassid | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2::GetDocumentClassID
helpviewer_keywords:
- IDebugDocument2::GetDocumentClassID
ms.assetid: 111c2b85-ebfa-487f-b896-2ec4a3eac4d1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 36a95914f470d0ce095db0c0db8d1397b02be3cf
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166553"
---
# <a name="idebugdocument2getdocumentclassid"></a>IDebugDocument2::GetDocumentClassID
Ruft den Klassen Bezeichner des Dokuments ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetDocumentClassID( 
   CLSID* pclsid
);
```

```csharp
int GetDocumentClassID( 
   out Guid pclsid
);
```

## <a name="parameters"></a>Parameter
`pclsid` vorgenommen Gibt eine GUID zurück, die die Klassen-ID des Dokuments ist.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Der Klassen-GUID kann verwendet werden, um einzelne Klassen zu instanziieren, die jeweils ein Dokument darstellen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
