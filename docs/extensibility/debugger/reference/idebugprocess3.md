---
description: Diese Schnittstelle stellt einen laufenden Prozess und seine Programme dar.
title: IDebugProcess3 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3
helpviewer_keywords:
- IDebugProcess3 interface
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a2303dfef18a1abccc728d80def0de25b4e7eadd
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169183"
---
# <a name="idebugprocess3"></a>IDebugProcess3
Diese Schnittstelle stellt einen laufenden Prozess und seine Programme dar. Diese Schnittstelle ist als Ersatz für mehrere Methoden in der [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) -Schnittstelle vorhanden. Er bietet Kontrolle über alle Programme im Prozess.

> [!NOTE]
> Die Methoden " [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)", " [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)" und " [Step](../../../extensibility/debugger/reference/idebugprogram2-step.md) " sind veraltet und sollten nicht mehr verwendet werden. Verwenden Sie stattdessen die entsprechenden Methoden für die `IDebugProcess3` Schnittstelle.

## <a name="syntax"></a>Syntax

```
IDebugProcess3 : IDebugProcess2
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird von einem benutzerdefinierten Port Lieferanten implementiert, um Programme als Gruppe zu verwalten. Wenn Programme als Gruppe verwaltet werden, können Sie deren Ausführung steuern und eine Sprache für eine Ausdrucks Auswertung einrichten. Diese Schnittstelle muss vom Port Lieferanten implementiert werden.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Diese Schnittstelle wird hauptsächlich vom Sitzungs-Debug-Manager (SDM) aufgerufen, um mit einer Gruppe von Programmen zu interagieren, die in diesem Prozess identifiziert werden.

 Rufen Sie [QueryInterface](/cpp/atl/queryinterface) für eine [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) -Schnittstelle auf, um diese Schnittstelle abzurufen.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den von [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)geerbten Methoden `IDebugProcess3` implementiert die folgenden Methoden.

|Methode|Beschreibung|
|------------|-----------------|
|[Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|Setzt die Ausführung von oder schrittweise durch.|
|[Ausführen](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|Startet die Ausführung eines Prozesses.|
|[Schritt](../../../extensibility/debugger/reference/idebugprocess3-step.md)|Schritte leiten eine Anweisung oder Anweisung im Prozess weiter.|
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|Ruft den Grund ab, warum der Prozess zum Debuggen gestartet wurde.|
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|Legt die hostingsprache so fest, dass die Debug-Engine die entsprechende Ausdrucks Auswertung laden kann.|
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|Ruft die Sprache ab, die zurzeit für diesen Prozess festgelegt ist.|
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|Deaktiviert "Bearbeiten und Fortfahren" (ENC) für diesen Prozess.<br /><br /> Ein benutzerdefinierter Port Lieferant implementiert diese Methode nicht (er sollte immer zurückgeben `E_NOTIMPL` ).|
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|Hiermit wird der Status der Status für diesen Prozess erhalten.<br /><br /> Ein benutzerdefinierter Port Lieferant implementiert diese Methode nicht (er sollte immer zurückgeben `E_NOTIMPL` ).|
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|Ruft ein Array eindeutiger Bezeichner für verfügbare Debug-engines ab.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
