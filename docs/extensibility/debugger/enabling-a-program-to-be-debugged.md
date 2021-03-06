---
title: Aktivieren eines deaktivierte Programms | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die Debug-Engine starten oder die Debug-Engine an ein vorhandenes Programm anfügen, um ein Programm zu Debuggen
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9dd31a9ff81493d0a315efc0ce0b607af0c6e422
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840664"
---
# <a name="enable-a-program-to-be-debugged"></a>Aktivieren eines zu deaktivier enden Programms
Bevor Ihre Debug-Engine (de) ein Programm debuggen kann, müssen Sie zuerst die de starten oder Sie an ein vorhandenes Programm anfügen.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Port erhalten](../../extensibility/debugger/getting-a-port.md) Erläutert, wie Sie einen Port als ersten Schritt zum Aktivieren eines Programms abrufen können.

 [Programm registrieren](../../extensibility/debugger/registering-the-program.md) Erläutert den nächsten Schritt zum Aktivieren eines Programms, das gedeentschlgt werden soll: die Registrierung beim Port. Nach der Registrierung kann das Programm entweder durch das Anfügen oder Just-in-Time-Debuggen (JIT) gedebuggt werden.

 [An das Programm anfügen](../../extensibility/debugger/attaching-to-the-program.md) Erläutert den nächsten Schritt: Anfügen des Debuggers an das Programm.

 [Start basiertes Anhängen](../../extensibility/debugger/launch-based-attachment.md) Beschreibt die Start basierte Anlage zu einem Programm, das beim Starten durch die SDM automatisch erfolgt.

 [Erforderliche Ereignisse senden](../../extensibility/debugger/sending-the-required-events.md) Führt Sie schrittweise durch die erforderlichen Ereignisse beim Erstellen einer Debug-Engine (de) und beim Anfügen an ein Programm.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Erstellen einer benutzerdefinierten Debug-Engine](../../extensibility/debugger/creating-a-custom-debug-engine.md) Definiert eine Debug-Engine (de) und beschreibt Dienste, die über die de-Schnittstellen implementiert werden, und wie Sie bewirken können, dass der Debugger zwischen verschiedenen Betriebsmodi übergeht.
