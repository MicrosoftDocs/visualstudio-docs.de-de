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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d60c214fce57f5958d8b30ca231c3e8a2bc05194
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960805"
---
# <a name="servers-visual-studio-sdk"></a>Server (Visual Studio SDK)
In der Debugger-Architektur ist ein *Server*:

- Ist ein Container von Ports und Port Lieferanten und kommuniziert Ports und Port Lieferanten mit dem sitzungsdebug-Manager (SDM) und Debug-engines.

- Kann sich selbst anhand des Namens identifizieren und seine Ports und Port Lieferanten auflisten.

- Wird durch eine [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) -Schnittstelle dargestellt, die nur von Visual Studio implementiert wird (eine Instanz eines Servers für jede Instanz von Visual Studio, die ausgeführt wird).

## <a name="see-also"></a>Weitere Informationen
- [Ports](../../extensibility/debugger/ports.md)
- [Port Lieferanten](../../extensibility/debugger/port-suppliers.md)
- [Debugger-Konzepte](../../extensibility/debugger/debugger-concepts.md)
- [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)
