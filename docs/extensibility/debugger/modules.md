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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9aa0aaf7e82287c1dc2e35c524798a3480d2573e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926320"
---
# <a name="modules"></a>Module
Im Hinblick auf die Debugger-Architektur ist ein *Modul*:

- Ist ein physischer Container von Code, z. b. eine ausführbare Datei oder eine DLL.

- Kann seine Symbole erneut laden und sich selbst beschreiben. Modulbeschreibungen werden im Fenster "Module" der IDE angezeigt.

- Wird durch eine [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) -Schnittstelle dargestellt, die von einem Debug-Modul erstellt wurde, um das Modul zu beschreiben.

## <a name="see-also"></a>Weitere Informationen
- [Debugger-Konzepte](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
