---
title: Idebugcontainerfield | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2e7ed9e573236f0bdeff9c9a8433af322a5a5f79
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928496"
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
Diese Schnittstelle stellt ein Symbol oder einen Typ dar, der ein Container für andere Symbole oder Typen ist.

## <a name="syntax"></a>Syntax

```
IDebugContainerField : IDebugField
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein Symbol Anbieter implementiert diese Schnittstelle für das gleiche Objekt, das die [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Schnittstelle implementiert. Diese Schnittstelle ist auch die Basisklasse für alle Schnittstellen, die Container darstellen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Viele Methoden für viele Schnittstellen geben diese Schnittstelle zurück. Da es sich um eine Basisklasse für alle Container handelt, können durch die Verwendung von [QueryInterface](/cpp/atl/queryinterface)weitere spezialisierte Schnittstellen von dieser Schnittstelle abgerufen werden. Zu diesen Schnittstellen gehören [idebugarrayfield](../../../extensibility/debugger/reference/idebugarrayfield.md), [idebugclassfield](../../../extensibility/debugger/reference/idebugclassfield.md), [idebugmethodfield](../../../extensibility/debugger/reference/idebugmethodfield.md)und [idebugpropertyfield](../../../extensibility/debugger/reference/idebugpropertyfield.md).

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den Methoden für die [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Schnittstelle implementiert diese Schnittstelle die folgende Methode:

|Methode|Beschreibung|
|------------|-----------------|
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|Erstellt einen Enumerator für die Felder des Containers.|

## <a name="remarks"></a>Bemerkungen
 Arrays (Container für Variablen), Klassen (Container für Methoden und Variablen) und Methoden (Container für Parameter und lokale Variablen) sind Beispiele für Container.

## <a name="requirements"></a>Anforderungen
 Header: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
