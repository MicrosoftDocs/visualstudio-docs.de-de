---
title: Module | Microsoft-Dokumentation
description: In diesem Artikel werden die Definition und die Rolle eines Moduls in der Debugger-Architektur in Visual Studio beschrieben.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 57202231c1bbfc7712d322b8cc7a30e3f64c87af
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606644"
---
# <a name="modules"></a>Module
Im Hinblick auf die Debugger-Architektur ist ein *Modul*:

- Ist ein physischer Container von Code, z. b. eine ausführbare Datei oder eine DLL.

- Kann seine Symbole erneut laden und sich selbst beschreiben. Modulbeschreibungen werden im Fenster "Module" der IDE angezeigt.

- Wird durch eine [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) -Schnittstelle dargestellt, die von einem Debug-Modul erstellt wurde, um das Modul zu beschreiben.

## <a name="see-also"></a>Weitere Informationen
- [Debugger-Konzepte](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
