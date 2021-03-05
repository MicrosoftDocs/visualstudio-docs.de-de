---
description: Ruft den Namen dieses generischen Parameters ab.
title: 'Idebuggenericparamfield:: getnameof formalparam | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericParamField::GetNameOfFormalParam
- GetNameOfFormalParam
ms.assetid: 05032a83-49ce-4007-b5d6-7b56945b956c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5bf8997d8b7e8887f800e61499bd67ab7d18750c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102172609"
---
# <a name="idebuggenericparamfieldgetnameofformalparam"></a>IDebugGenericParamField::GetNameOfFormalParam
Ruft den Namen dieses generischen Parameters ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetNameOfFormalParam (
    BSTR* pbstrName
);
```

```csharp
int GetNameOfFormalParam (
    string pbstrName
);
```

## <a name="parameters"></a>Parameter
`pbstrName`\
vorgenommen Der Name dieses generischen Parameters.

## <a name="return-value"></a>Rückgabewert
Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="example"></a>Beispiel
Im folgenden Beispiel wird gezeigt, wie diese Methode für ein **cdebuggenericparamfieldtype** -Objekt implementiert wird, das die [idebuggenericparamfield](../../../extensibility/debugger/reference/idebuggenericparamfield.md) -Schnittstelle verfügbar macht.

```cpp
HRESULT CDebugGenericParamFieldType::GetNameOfFormalParam(BSTR *pbstrName)
{
    HRESULT hr = S_OK;
    CComBSTR bstrName;

    METHOD_ENTRY( CDebugGenericParamFieldType::GetNameOfFormalParam );

    IfFalseGo( pbstrName, E_INVALIDARG );
    IfFailGo( this->LoadProps() );
    IfNullGo( *pbstrName = SysAllocString(m_bstrName), E_OUTOFMEMORY );

Error:

    METHOD_EXIT( CDebugGenericParamFieldType::GetNameOfFormalParam, hr );
    return hr;
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)
