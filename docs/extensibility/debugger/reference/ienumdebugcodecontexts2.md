---
description: Diese Schnittstelle listet die der Debugsitzung zugeordneten Code Kontexte oder ein bestimmtes Programm oder Dokument auf.
title: IEnumDebugCodeContexts2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2
helpviewer_keywords:
- IEnumDebugCodeContexts2
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 82e3583333c784fffa55abf2e86f5a7335aeb7c1
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102226929"
---
# <a name="ienumdebugcodecontexts2"></a>IEnumDebugCodeContexts2
Diese Schnittstelle listet die der Debugsitzung zugeordneten Code Kontexte oder ein bestimmtes Programm oder Dokument auf.

## <a name="syntax"></a>Syntax

```
IEnumDebugCodeContexts2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine (de) implementiert diese Schnittstelle, um eine Liste von Code Kontexten für eine bestimmte Textposition in einem Programm oder eine Liste von Code Kontexten für einen bestimmten Dokument Kontext darzustellen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Rufen Sie [enumcodekontexte](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) auf, um diese Schnittstelle zu erhalten, die eine Liste von Code Kontexten für eine bestimmte Textposition im Quelldokument eines Programms darstellt.

 Rufen Sie [enumcodekontexte](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) auf, um diese Schnittstelle zu erhalten, die eine Liste aller Code Kontexte in einem bestimmten Quelldokument darstellt.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IEnumDebugCodeContexts2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Nächste](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|Ruft eine angegebene Anzahl von Code Kontexten in einer enumerationssequenz ab.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|Überspringt eine angegebene Anzahl von Code Kontexten in einer enumerationssequenz.|
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|
|[Klonen](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|Ruft die Anzahl von Code Kontexten in einem Enumerator ab.|

## <a name="remarks"></a>Bemerkungen
 Visual Studio ruft [enumcodekontexte](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) auf, um eine Liste von Code Kontexten aufzufüllen, aus denen der Benutzer auswählen kann, wenn die nächste Anweisung festgelegt oder die Disassembly für eine Quelldatei angezeigt wird. Es können mehrere Code Kontexte auftreten, z. b. Wenn mehrere Instanzen einer C++-Vorlage vorhanden sind.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)
