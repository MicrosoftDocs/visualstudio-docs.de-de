---
title: IEnumCodePaths2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2
helpviewer_keywords:
- IEnumCodePaths2 interface
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 69a65488d38fe2562392be152e448369ff081915
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962157"
---
# <a name="ienumcodepaths2"></a>IEnumCodePaths2
Diese Schnittstelle stellt eine Liste von Codepfade dar.

## <a name="syntax"></a>Syntax

```
IEnumCodePaths2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine (de) implementiert diese Schnittstelle, um eine Liste von Codepfade darzustellen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Rufen Sie [enumcodepath](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) auf, um diese Schnittstelle zu erhalten.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IEnumCodePaths2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Nächste](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|Ruft eine angegebene Anzahl von Codepfade in einer enumerationssequenz ab.|
|[Skip](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|Überspringt eine angegebene Anzahl von Codepfade in einer enumerationssequenz.|
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|
|[Klonen](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|
|[GetCount](../../../extensibility/debugger/reference/ienumcodepaths2-getcount.md)|Ruft die Anzahl der Codepfade in einem Enumerator ab.|

## <a name="remarks"></a>Bemerkungen
 Ein Codepfad stellt einen Verzweigungs Punkt oder Funktions aufrufin einem Programm dar. Eine Liste von Codepfade steht für den Pfad, über den die Codeausführung erfolgt ist.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
