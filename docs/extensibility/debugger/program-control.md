---
title: Programmsteuerung | Microsoft-Dokumentation
description: Erfahren Sie mehr über Routinen in Visual Studio-debuggen, die auf der Programmebene auftreten, z. b. ausführen, schrittweise Ausführung, fortsetzen und Anhalten/Fortsetzen von Threads
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f9378dd2aa1ed52408e3aa4d0e9027a34d833dab
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948451"
---
# <a name="program-control"></a>Programmsteuerung
Beim Debuggen in Visual Studio erfolgen alle folgenden Schritt-und fortsetzenden Routinen auf der Programmebene:

- Festlegen der nächsten Anweisung, d. h. Festlegen des Computers auf die nächste Anweisung, die in einer bestimmten Frame Umgebung ausgeführt werden soll

- Ausführen von, d. h. fortsetzen des Fortschritt Modus

- Schritt der nächsten Anweisung

- Fortfahren mit dem aktuellen Schritt Modus

- Anhalten der im Programm enthaltenen Threads

- Fortsetzen der im Programm enthaltenen Threads

> [!NOTE]
> Das Anzeigen der-aufrufsstapel ist auf Thread Ebene implementiert. Um die Frame Informationen beim Anzeigen der-aufrufsstapel für einen Thread aufzulisten, müssen Sie alle Methoden der [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) -Schnittstelle implementieren.

## <a name="methods-of-program-control"></a>Methoden der Programmsteuerung
 In der folgenden Tabelle sind die Methoden von [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) aufgeführt, die für eine minimal funktionale Debug-Engine (de) und die Ausführungs Steuerung implementiert werden müssen.

|Methode|Beschreibung|
|------------|-----------------|
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Setzt die Ausführung aller Threads in einem Programm in einem beendeten Zustand fort. Erforderlich für die Ausführungs Steuerung.|
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Setzt die Ausführung aller Threads in einem Programm in einem beendeten Zustand fort. Erforderlich für die Ausführungs Steuerung.|
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Führt einen Schritt für den angegebenen Thread aus. Setzt die Ausführung aller anderen im Programm enthaltenen Threads fort. Erforderlich für die Ausführungs Steuerung.|

 Für Multithreadprogramme müssen Sie auch die [IDebugProgram2:: enumthreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) -Methode und alle Methoden der [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) -Schnittstelle implementieren.

## <a name="see-also"></a>Weitere Informationen
- [Ausführungs Steuerung und Zustands Auswertung](../../extensibility/debugger/execution-control-and-state-evaluation.md)
