---
description: Stellt eine Position in einer Quelldatei als Zeichen Offset dar.
title: IDebugDocumentPositionOffset2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1dee28d7f19f6398863476afbab8eb9b3cdbbb60
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167320"
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
Stellt eine Position in einer Quelldatei als Zeichen Offset dar.

## <a name="syntax"></a>Syntax

```
IDebugDocumentPositionOffset2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Wird von der IDE implementiert und von Debug-engines genutzt.

## <a name="methods"></a>Methoden
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugDocumentPositionOffset2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|Ruft den Bereich für die aktuelle Dokument Position ab.|

## <a name="remarks"></a>Bemerkungen
 Dadurch werden dieselben Informationen wie [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) zurückgegeben, jedoch in `char` Offsets vom Anfang des Dokuments. Dadurch wird das Dokument so dargestellt, wie es auf einem Datenträger vorhanden ist, d. h. ein eindimensionales Array von Zeichen, anstelle der Zeilen-und Spalten Informationen, die normalerweise zurückgegeben werden.

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
