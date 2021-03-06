---
description: Diese Schnittstelle zählt eine Liste von Modulen auf.
title: IEnumDebugModules2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2
helpviewer_keywords:
- IEnumDebugModules2
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 33853804078d5f32aba6fda6dac409cf2a24de0a
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224758"
---
# <a name="ienumdebugmodules2"></a>IEnumDebugModules2
Diese Schnittstelle zählt eine Liste von Modulen auf.

## <a name="syntax"></a>Syntax

```
IEnumDebugModules2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine (de) implementiert diese Schnittstelle, um eine Liste von Modulen darzustellen, die für ein Programm geladen werden.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Visual Studio ruft [enummodule](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) auf, um diese Schnittstelle zu erhalten.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IEnumDebugModules2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Nächste](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|Ruft eine angegebene Anzahl von Modulen in einer enumerationssequenz ab.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|Überspringt eine angegebene Anzahl von Modulen in einer enumerationssequenz.|
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugmodules2-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|
|[Klonen](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|Ruft die Anzahl der Module ab.|

## <a name="remarks"></a>Bemerkungen
 Visual Studio verwendet diese Schnittstelle hauptsächlich, um das Fenster **Module** zu aktualisieren.

 Zum Zwecke des Debuggens in Visual Studio ist ein Programm eine logische Sequenz von Code Anweisungen, die Modul Grenzen überschreiten können. Daher ist eine Liste von Modulen für eine einzelne [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) -Schnittstelle erforderlich. Das erste Modul in der Liste enthält normalerweise den ersten Einstiegspunkt für das zugehörige Programm.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)
