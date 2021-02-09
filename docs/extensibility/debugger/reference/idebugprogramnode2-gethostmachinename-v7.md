---
title: 'IDebugProgramNode2:: GetHostMachineName_V7 | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetHostMachineName
helpviewer_keywords:
- IDebugProgramNode2::GetHostMachineName_V7
- IDebugProgramNode2::GetHostMachineNameIDebugProgramNode2::GetHostMachineName
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 843e5fdf91fe817681b95422474d3887de5756b0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898611"
---
# <a name="idebugprogramnode2gethostmachinename_v7"></a>IDebugProgramNode2::GetHostMachineName_V7

> [!Note]
> Veraltet. Verwenden Sie nicht.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetHostMachineName_V7 (
   BSTR* pbstrHostMachineName
);
```

```csharp
int GetHostMachineName_V7 (
   out string pbstrHostMachineName
);
```

## <a name="parameters"></a>Parameter

`pbstrHostMachineName`\
vorgenommen Gibt den Namen des Computers zurück, auf dem das Programm ausgeführt wird.

## <a name="return-value"></a>Rückgabewert

Eine-Implementierung sollte immer zurückgeben `E_NOTIMPL` .

## <a name="remarks"></a>Bemerkungen

> [!WARNING]
> Ab Visual Studio 2005 wird diese Methode nicht mehr verwendet und sollte immer zurückgeben `E_NOTIMPL` .

## <a name="see-also"></a>Weitere Informationen

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
