---
title: Senden von Ereignissen | Microsoft-Dokumentation
description: Erfahren Sie, wie der Debugger und die Debug-Engine ein Ereignis Modell verwenden, das auf DCOM basiert. Ereignisse werden als COM-Objekte gesendet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: eb86be560f45941b1ca5eb04f38087c23c431fda
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960857"
---
# <a name="send-events"></a>Senden von Ereignisse
Der Mechanismus für die Kommunikation zwischen dem Debugger und der Debug-Engine (de) ist ein Ereignis Modell, das auf DCOM basiert. Ereignisse werden als COM-Objekte gesendet, und jedes Ereignis verfügt über Parameter, die Folgendes angeben:

- Der de-Wert, der das Ereignis aufgerufen hat.

- Eine Beschreibung, was passiert ist.

- Der Prozess, das Programm und die Thread Informationen, die den Kontext identifizieren, in dem das Ereignis aufgetreten ist. Der Prozess wird nicht für Ereignisse gesendet, die von einem de gesendet werden.

- Der Ereignistyp, der angibt, ob das Ereignis synchron oder asynchron ist.

  Alle Debugereignisse werden mithilfe der [IDebugEventCallback2:: Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md)-Methode gesendet.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Ereignis Quellen](../../extensibility/debugger/event-sources-visual-studio-sdk.md) Erläutert die beiden Quellen für Ereignisse: Debug Engine (de) und Session Debug Manager (SDM).

 [Unterstützte Ereignis Typen](../../extensibility/debugger/supported-event-types.md) Erläutert die derzeit unterstützten Ereignis Typen: asynchron und synchron.

 [Ereignis Beschreibungen](../../extensibility/debugger/event-descriptions.md) Definiert Ereignisse und die Gründe für deren Verwendung.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Erstellen einer benutzerdefinierten Debug-Engine](../../extensibility/debugger/creating-a-custom-debug-engine.md) Beschreibt, wie ein de mit dem Interpreter oder dem Betriebssystem verwendet wird, um Debugdienste bereitzustellen.
