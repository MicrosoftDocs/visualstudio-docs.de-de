---
title: 'IDebugProgramHost2:: GetHostName | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f801b6fd4b030866886f86b8cd01916645c2219c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898785"
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
Ruft den Titel, den anzeigen Amen oder den Dateinamen des Hostingprozesses dieses Programms ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetHostName( 
   DWORD dwType,
   BSTR* pbstrHostName
);
```

```csharp
int GetHostName( 
   uint dwType,
   out string pbstrHostName
);
```

## <a name="parameters"></a>Parameter
`dwType`\
in Ein Wert aus der [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) Enumeration.

`pbstrHostName`\
vorgenommen Gibt den angeforderten Namen des Hostingprozesses zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 In einer typischen Implementierung dieser Methode `dwType` wird der-Parameter ignoriert, und es wird ein Anzeige Name des Host Computers zurückgegeben. Eine weitere mögliche Implementierung besteht darin, den- `dwType` Parameter an einen Aufrufen der [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) -Methode zu übergeben, um den Namen zu erhalten.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)
- [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)
