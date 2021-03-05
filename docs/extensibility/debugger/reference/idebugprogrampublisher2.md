---
description: Diese Schnittstelle ermöglicht einem Debugmodul (de) oder benutzerdefinierten Port Zulieferern das Registrieren von Programmen für das Debuggen.
title: IDebugProgramPublisher2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2
helpviewer_keywords:
- IDebugProgramPublisher2 interface
ms.assetid: b1d17f63-7146-4076-a588-034cfc6858b9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: deac68ba693bd9e4f827fef5610e3c9d2c3c26f6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166969"
---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
Diese Schnittstelle ermöglicht einem Debugmodul (de) oder benutzerdefinierten Port Zulieferern das Registrieren von Programmen für das Debuggen.

## <a name="syntax"></a>Syntax

```
IDebugProgramPublisher2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
Visual Studio implementiert diese Schnittstelle, um Programme zu registrieren, die gedebuggt werden, damit Sie für das Debuggen über mehrere Prozesse sichtbar sind.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
Rufen Sie die com- `CoCreateInstance` Funktion mit `CLSID_ProgramPublisher` auf, um diese Schnittstelle zu erhalten (siehe Beispiel). Ein oder ein benutzerdefinierter Port Lieferant verwendet diese Schnittstelle, um Programmknoten zu registrieren, die Programme darstellen, die gedebuggt werden.

## <a name="methods-in-vtable-order"></a>Methoden in der Vtable-Reihenfolge
Diese Schnittstelle implementiert die folgenden Methoden:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|Macht einen Programmknoten für den und den Sitzungs-Debug-Manager (SDM) verfügbar.|
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|Entfernt einen Programmknoten, sodass er nicht mehr verfügbar ist.|
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|Stellt ein Programm für den und den SDM zur Verfügung.|
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|Entfernt ein Programm, sodass es nicht mehr verfügbar ist.|
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|Legt ein Flag fest, das angibt, dass ein Debugger vorhanden ist.|

## <a name="remarks"></a>Bemerkungen
Diese Schnittstelle macht Programme und Programmknoten verfügbar (d. h., veröffentlicht sie) für die Verwendung durch des und den Sitzungs-Debug-Manager (SDM). Um auf veröffentlichte Programme und Programmknoten zuzugreifen, verwenden Sie die [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) -Schnittstelle. Dies ist die einzige Möglichkeit, wie Visual Studio erkennen kann, dass ein Programm gedeppt wird.

## <a name="requirements"></a>Requirements (Anforderungen)
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Beispiel
In diesem Beispiel wird gezeigt, wie der Programm Verleger instanziiert und ein Programmknoten registriert wird. Dies wird aus dem Tutorial zum [Veröffentlichen des Programm Knotens](/previous-versions/bb161795(v=vs.90))entnommen.

```cpp
// This is how m_srpProgramPublisher is defined in the class definition:
// CComPtr<IDebugProgramPublisher2> m_srpProgramPublisher.

void CProgram::Start(IDebugEngine2 * pEngine)
{
    m_spEngine = pEngine;

    HRESULT hr = m_srpProgramPublisher.CoCreateInstance(CLSID_ProgramPublisher);
    if ( FAILED(hr) )
    {
        ATLTRACE("Failed to create the program publisher: 0x%x.", hr);
        return;
    }

    // Register ourselves with the program publisher. Note that
    // CProgram implements the IDebgProgramNode2 interface, hence
    // the static cast on "this".
    hr = m_srpProgramPublisher->PublishProgramNode(
        static_cast<IDebugProgramNode2*>(this));
    if ( FAILED(hr) )
    {
        ATLTRACE("Failed to publish the program node: 0x%x.", hr);
        m_srpProgramPublisher.Release();
        return;
    }

    ATLTRACE("Added program node.\n");
}
```

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
