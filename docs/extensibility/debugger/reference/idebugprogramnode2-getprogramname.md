---
description: 'IDebugProgramNode2:: getprogramname Ruft den Namen des Programms ab.'
title: 'IDebugProgramNode2:: getprogramname | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetProgramName
helpviewer_keywords:
- IDebugProgramNode2::GetProgramName
ms.assetid: 510c7f5d-48ff-4d9f-ad79-fbad9f15239d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 88a4bc58f5d91cdb52482f4dc862446cfc9e7eb1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161384"
---
# <a name="idebugprogramnode2getprogramname"></a>IDebugProgramNode2::GetProgramName
Ruft den Namen des Programms ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetProgramName (
    BSTR* pbstrProgramName
);
```

```csharp
int GetProgramName (
    out string pbstrProgramName
);
```

## <a name="parameters"></a>Parameter
`pbstrProgramName`\
vorgenommen Gibt den Namen des Programms zurück.

## <a name="return-value"></a>Rückgabewert
Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
Der Name eines Programms ist nicht das gleiche wie der Pfad zum Programm, obwohl der Name des Programms möglicherweise Teil eines solchen Pfades ist.

## <a name="example"></a>Beispiel
Im folgenden Beispiel wird gezeigt, wie diese Methode für ein einfaches `CProgram` Objekt implementiert wird, das die [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) -Schnittstelle implementiert. Die- `MakeBstr` Funktion weist eine Kopie der angegebenen Zeichenfolge als BSTR zu.

```cpp
HRESULT CProgram::GetProgramName(BSTR* pbstrProgramName) {
    if (!pbstrProgramName)
        return E_INVALIDARG;

    // Assign the member program name to the passed program name.
    *pbstrProgramName = MakeBstr(m_pszProgramName);
    return NOERROR;
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
