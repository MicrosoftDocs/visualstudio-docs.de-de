---
title: Sitzungs-Debug-Manager | Microsoft-Dokumentation
description: Erfahren Sie mehr über den Session Debug Manager, der mehrere Debug-engines zum Debuggen von Programmen in mehreren Prozessen auf einer beliebigen Anzahl von Computern verwaltet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d2c51b1fd345789cabbb9735621626ab7c2db993
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845283"
---
# <a name="session-debug-manager"></a>Sitzungs-Debug-Manager
Der sitzungsdebug-Manager (SDM) verwaltet eine beliebige Anzahl von Debugmodulen (de), die eine beliebige Anzahl von Programmen in mehreren Prozessen auf einer beliebigen Anzahl von Computern Debuggen. Die SDM ist nicht nur ein Debug Engine Multiplexer, sondern bietet eine einheitliche Ansicht der Debugsitzung für die IDE.

## <a name="session-debug-manager-operation"></a>Sitzungs-Debug-Manager-Vorgang
 Der Sitzungs-Debug-Manager (SDM) verwaltet den de. Auf einem Computer können mehrere Debug-Engine gleichzeitig ausgeführt werden. Der SDM umschließt eine Reihe von Schnittstellen aus dem des und macht Sie als eine einzige Schnittstelle für die IDE verfügbar, um den des zu multiplizieren.

 Um die Leistung zu verbessern, werden einige Schnittstellen nicht multiplext. Stattdessen werden Sie direkt von der de verwendet, und Aufrufe an diese Schnittstellen durchlaufen nicht die SDM. Beispielsweise werden Schnittstellen, die mit Speicher-, Code-und Dokument Kontexten verwendet werden, nicht multiplext, da Sie auf eine bestimmte Anweisung, einen Speicher oder ein Dokument in einem bestimmten Programm verweisen, das von einer bestimmten de debuggten wird. An dieser Kommunikationsebene muss keine andere de beteiligt sein.

 Dies gilt nicht für alle Kontexte. Aufrufe der Kontext Schnittstelle der Ausdrucks Auswertung durchlaufen die SDM. Während der Ausdrucks Auswertung umschließt SDM die [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) -Schnittstelle, die es der IDE zuweist, denn wenn dieser Ausdruck ausgewertet wird, kann er mehrere des umfassen, die Programme in demselben Prozess Debuggen, der möglicherweise im gleichen Thread ausgeführt wird.

 Der SDM fungiert in der Regel als Delegierungs Mechanismus, kann aber auch als Übertragungsmechanismus fungieren. Während der Ausdrucks Auswertung fungiert die SDM z. b. als Übertragungsmechanismus, mit dem alle des benachrichtigt werden, dass Sie Code in einem bestimmten Thread ausführen können. Wenn das SDM ein anhalteereignis empfängt, sendet es auf ähnliche Weise an die Programme, die nicht mehr ausgeführt werden sollen. Wenn ein Schritt aufgerufen wird, überträgt SDM an die Programme, die Sie weiter ausführen können. Breakpoints werden ebenfalls an alle de gesendet.

 Der SDM verfolgt das aktuelle Programm, den Thread oder den Stapel Rahmen nicht. Prozess-, Programm-und Thread Informationen werden in Verbindung mit bestimmten debuggingereignissen an die SDM gesendet.

## <a name="see-also"></a>Siehe auch
- [Debug-Engine](../../extensibility/debugger/debug-engine.md)
- [Debugger-Komponenten](../../extensibility/debugger/debugger-components.md)
- [Debugger-Kontexte](../../extensibility/debugger/debugger-contexts.md)
