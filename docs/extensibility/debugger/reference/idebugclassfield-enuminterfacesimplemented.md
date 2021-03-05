---
description: Erstellt einen Enumerator für die von dieser Klasse implementierten Schnittstellen.
title: 'Idebugclassfield:: enuminterfacesimplementiert | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumInterfacesImplemented
helpviewer_keywords:
- IDebugClassField::EnumInterfacesImplemented method
ms.assetid: e5523e45-d350-491e-a92c-fe0ca97d2052
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5f90bf6efc3a34e4f6b9f60ef5bdadb0640f495b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164317"
---
# <a name="idebugclassfieldenuminterfacesimplemented"></a>IDebugClassField::EnumInterfacesImplemented
Erstellt einen Enumerator für die von dieser Klasse implementierten Schnittstellen.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumInterfacesImplemented( 
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumInterfacesImplemented(
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parameter
`ppEnum`\
vorgenommen Gibt ein [ienumdebugfields](../../../extensibility/debugger/reference/ienumdebugfields.md) -Objekt zurück, das die Liste der implementierten Schnittstellen darstellt. Gibt einen NULL-Wert zurück, wenn keine Schnittstellen vorhanden sind.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben, oder es wird S_FALSE zurückgegeben, wenn für diese Klasse keine Schnittstellen implementiert sind. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Jedes Element der-Enumeration ist ein [idebugclassfield](../../../extensibility/debugger/reference/idebugclassfield.md) -Objekt, das eine-Schnittstelle beschreibt. Beachten Sie, dass nicht verwalteter [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] Code keine Schnittstellen als diskrete Entität verwendet, sodass diese Methode immer einen NULL-Wert für nicht verwalteten Code zurückgibt [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] .

## <a name="see-also"></a>Weitere Informationen
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
