---
title: 'IDebugCoreServer2:: GetMachineUtilities_V7 | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3572390f6e047d0e06b645b6a364971fe4557ea8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904056"
---
# <a name="idebugcoreserver2getmachineutilities_v7"></a>IDebugCoreServer2::GetMachineUtilities_V7
Diese Methode ruft die Computer Dienstprogramme für einen Server ab.

> [!NOTE]
> Diese Methode ist veraltet: Verwenden Sie nicht ( [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] gibt immer zurück, `E_NOTIMPL` Wenn diese Methode aufgerufen wird). Sie wird aus historischen Gründen beibehalten.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetMachineUtilities_V7(
   IDebugMDMUtil2_V7** ppUtil
);
```

```csharp
int GetMachineUtilities_V7(
   out IDebugMDMUtil2_V7 ppUtil
);
```

## <a name="parameters"></a>Parameter
`ppUtil`\
vorgenommen Gibt eine `IDebugMDMUtil2_V7` Schnittstelle zurück, die die Informationen zu den Computer Dienstprogrammen darstellt

## <a name="return-value"></a>Rückgabewert
 Gibt immer zurück `E_NOTIMPL` , was darauf hinweist, dass die Methode nicht implementiert ist.

## <a name="remarks"></a>Bemerkungen
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] gibt immer zurück, `E_NOTIMPL` Wenn diese Methode aufgerufen wird.

## <a name="see-also"></a>Weitere Informationen
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
