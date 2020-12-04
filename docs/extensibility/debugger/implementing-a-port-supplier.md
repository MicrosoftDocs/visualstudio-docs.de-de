---
title: Implementieren eines Port Anbieters | Microsoft-Dokumentation
description: Erfahren Sie mehr über das Implementieren eines Port Anbieters, der beim Debuggen auf einen nicht-DCOM-Computer oder bei Unterstützung für ein neues Gerät erforderlich ist.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 72963660e4f50a72cdbc04bab4833b397d15fc27
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560667"
---
# <a name="implement-a-port-supplier"></a>Implementieren eines Port Anbieters
Ein Port Lieferant liefert Ports für die Anforderung an den Sitzungs-Debug-Manager (SDM). Ein Port Lieferant muss implementiert werden, wenn ein Debuggen auf einen nicht-DCOM-Computer oder ein neues Gerät unterstützt wird. Wenn Sie z. b. das Debuggen auf einem Mobiltelefon bereitstellen möchten, können Sie einen Port Lieferanten einrichten, der Ports bereitstellt, die eine Verbindung mit dem Mobiltelefon herstellen (z. b. über IR oder eine Zell Verbindung) und die Prozesse und Programme auflisten, die auf dem Telefon ausgeführt werden.

 Für das Debuggen von Programmen auf Windows-basierten Computern (einschließlich Remote Debuggen) stellt Visual Studio Port Lieferanten für systemeigene und CLR-Prozesse (Common Language Runtime) bereit, sodass Sie in diesen Fällen keinen eigenen Port Lieferanten einrichten müssen.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Implementieren und Registrieren eines Port Anbieters](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md) Erläutert, wie die SDM mit dem Port Lieferanten und seinen Ports interagiert.

 [Erforderliche Port Lieferanten Schnittstellen](../../extensibility/debugger/required-port-supplier-interfaces.md) Dokumentiert die Schnittstellen, die Sie implementieren müssen, um einen Port Lieferanten zu erhalten.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md) beschreibt die wichtigsten Architekturkonzepte für das Debuggen.

## <a name="see-also"></a>Siehe auch
 [Erweiterbarkeit von Visual Studio-Debugger](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
