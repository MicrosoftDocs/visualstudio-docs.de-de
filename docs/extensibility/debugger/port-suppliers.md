---
title: Port Lieferanten | Microsoft-Dokumentation
description: In diesem Artikel werden die Definition und die Rolle eines Port Anbieters in der Debugger-Architektur in Visual Studio beschrieben.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b3226053a23a45c42a45de038e44829d4a150af6
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606579"
---
# <a name="port-suppliers"></a>Port Lieferanten
In der Debugger-Architektur ist ein *Port Lieferant*:

- Ist in einem Server enthalten und stellt Ports auf Anforderung an diesen Server bereit.

- Kann Ports hinzufügen und aus dem enthaltenden Server entfernen.

- Kann alle Ports auflisten, die Sie auf dem Server bereitgestellt haben.

- Wird durch eine [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) -Schnittstelle dargestellt, die in Visual Studio über die Registrierung registriert ist. Diese Schnittstelle kann durch Aufrufen von [getportsupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)abgerufen werden.

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] stellt einen standardportlieferant und einen Standardport bereit. Wenn ein benutzerdefinierter Port implementiert werden muss, muss auch ein benutzerdefinierter Port Lieferant implementiert werden, um diese benutzerdefinierten Ports bereitzustellen.

## <a name="see-also"></a>Weitere Informationen
- [Server](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Ports](../../extensibility/debugger/ports.md)
- [Debugger-Konzepte](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)
- [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
