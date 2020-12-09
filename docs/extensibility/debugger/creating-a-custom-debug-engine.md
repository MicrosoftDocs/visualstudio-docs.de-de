---
title: Erstellen einer benutzerdefinierten Debug-Engine | Microsoft-Dokumentation
description: In diesen Artikeln erfahren Sie mehr über das Erstellen einer Debug-Engine, die das Debuggen bestimmter Lauf Zeit Architekturen ermöglicht.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 673b08bf5680e04c90376c9eb3d63f6f03df9723
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914191"
---
# <a name="create-a-custom-debug-engine"></a>Erstellen einer benutzerdefinierten Debug-Engine
Eine Debug-Engine (de) ist eine Komponente, die das Debuggen bestimmter Lauf Zeit Architekturen ermöglicht. Es gibt in der Regel nur eine de-Implementierung pro Laufzeitumgebung.

> [!NOTE]
> Obwohl es separate de-Implementierungen für Transact-SQL und JScript gibt, verwenden VBScript und JScript eine einzelne de.

 Ein de funktioniert mit dem Interpreter oder dem Betriebssystem, um solche debuggingdienste als Ausführungs Steuerung, Breakpoints und Ausdrucks Auswertung bereitzustellen. Diese Dienste werden über die de-Schnittstellen implementiert und können dazu führen, dass der Debugger zwischen verschiedenen Betriebsmodi übergeht. Weitere Informationen finden Sie unter [Betriebsmodi](../../extensibility/debugger/operational-modes.md).

 Das Erstellen eines de besteht aus den folgenden Schritten:

1. Registrieren einer de mit Visual Studio

2. Aktivieren eines zu deaktivier enden Programms

3. Implementieren der Ausführungs Steuerung und der Zustands Auswertung

4. Senden von Ereignisse

5. Einrichten von Beendigung und trennen

## <a name="in-this-section"></a>In diesem Abschnitt
 [Registrieren einer benutzerdefinierten Debug-Engine](../../extensibility/debugger/registering-a-custom-debug-engine.md) Erläutert die erforderlichen Schritte zum Registrieren einer Debug-Engine in Visual Studio, damit Sie verwendet werden kann.

 [Aktivieren eines zu deaktivier enden Programms](../../extensibility/debugger/enabling-a-program-to-be-debugged.md) Erläutert, dass Sie vor dem Debuggen eines Programms das Programm zuerst starten oder an ein vorhandenes Programm Anfügen müssen.

 [Implementieren der Ausführungs Steuerung und der Zustands Auswertung](../../extensibility/debugger/execution-control-and-state-evaluation.md) Erläutert, warum beim Debuggen einer Anwendung Ausführungs Steuerungsfunktionen implementiert werden müssen.

 [Ereignisse senden](../../extensibility/debugger/sending-events.md) Beschreibt die Kommunikation zwischen dem Debugger und der de als Ereignis Modell, das auf DCOM basiert.

 [Einrichten von Beendigung und trennen](../../extensibility/debugger/termination-and-detaching.md) Erläutert das Erreichen der normalen Beendigung, d. h., es gibt keine Haltepunkte, Ausnahmen, Laufzeitfehler oder unendliche Schleifen in der zu debuggenden Anwendung.

 [Debugger-Ereignisse aufzurufen](../../extensibility/debugger/calling-debugger-events.md) Dokumentiert die Aufruf Reihenfolge der Ereignisse, die in einer Debugsitzung auftreten.

 Gewusst [wie: Debuggen einer benutzerdefinierten Debug-Engine](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md) Erläutert, wie eine benutzerdefinierte de debuggt wird.

## <a name="see-also"></a>Weitere Informationen
- [Erweiterbarkeit von Visual Studio-Debugger](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
