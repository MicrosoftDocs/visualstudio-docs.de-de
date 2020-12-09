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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad62a487d38500617999a276aa3ae15a75089736
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914126"
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
