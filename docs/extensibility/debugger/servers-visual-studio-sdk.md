---
title: Server (Visual Studio SDK) | Microsoft-Dokumentation
description: In diesem Artikel werden die Definition und Rolle eines Servers in der Debugger-Architektur in Visual Studio beschrieben.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9eaccebf874fa5fc0e7aaf63823547742215a568
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845296"
---
# <a name="servers-visual-studio-sdk"></a>Server (Visual Studio SDK)
In der Debugger-Architektur ist ein *Server*:

- Ist ein Container von Ports und Port Lieferanten und kommuniziert Ports und Port Lieferanten mit dem sitzungsdebug-Manager (SDM) und Debug-engines.

- Kann sich selbst anhand des Namens identifizieren und seine Ports und Port Lieferanten auflisten.

- Wird durch eine [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) -Schnittstelle dargestellt, die nur von Visual Studio implementiert wird (eine Instanz eines Servers für jede Instanz von Visual Studio, die ausgeführt wird).

## <a name="see-also"></a>Siehe auch
- [Ports](../../extensibility/debugger/ports.md)
- [Port Lieferanten](../../extensibility/debugger/port-suppliers.md)
- [Debugger-Konzepte](../../extensibility/debugger/debugger-concepts.md)
- [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)
