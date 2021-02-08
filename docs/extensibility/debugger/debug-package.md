---
title: Paket Debuggen | Microsoft-Dokumentation
description: Erfahren Sie, wie das Debugpaket in Visual Studio Shell ausgeführt wird und die Benutzeroberfläche verarbeitet, indem Sie die Debugschnittstellen nutzen und mit dem sitzungsdebug-Manager
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0e5296a77e835ab291bce7a77e3f0cb09eb6bcf5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840846"
---
# <a name="debug-package"></a>Paket Debuggen
Das Debugpaket wird in der Visual Studio-Shell ausgeführt und verarbeitet die gesamte Benutzeroberfläche. Dabei werden die Visual Studio-debuggingschnittstellen verarbeitet und mit dem sitzungsdebug-Manager (SDM) kommuniziert.

 Break-Ereignisse, die über den SDM gesendet werden, wechseln den Debugger vom Lauf Modus in den Break-Modus und ändern den Fokus auf das Programm, in dem die Unterbrechung aufgetreten ist Das Debugpaket verfolgt den Stapel Rahmen und den Thread aus den Informationen, die von den Ereignissen an ihn gesendet werden.

 Das Debugpaket hat keine sprach-oder Lauf Zeit Umgebungs Abhängigkeiten. Das Debugpaket muss nicht implementiert oder geändert werden.

 Das Debugpaket wird von *vsdebug.dll* implementiert.

## <a name="see-also"></a>Weitere Informationen
- [Sitzungs-Debug-Manager](../../extensibility/debugger/session-debug-manager.md)
- [Stapel Rahmen](../../extensibility/debugger/stack-frames.md)
- [Threads](../../extensibility/debugger/threads.md)
- [Debugger-Komponenten](../../extensibility/debugger/debugger-components.md)
