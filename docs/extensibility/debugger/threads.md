---
title: Threads | Microsoft-Dokumentation
description: In diesem Artikel werden die Definition und die Rolle eines Threads in der Debugger-Architektur in Visual Studio beschrieben.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b259ffd7814b42145489ee5990cee6da891a9d10
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995953"
---
# <a name="threads"></a>Threads
In der Debugger-Architektur ein *Thread*:

- Ist die grundlegende Einheit der Berechnung. Ein Thread führt seine Anweisungen sequenziell innerhalb des Kontexts einer einzelnen Rückruf Stapel aus und wechselt von einem Code Kontext zum nächsten.

- Kann sich selbst und das Programm identifizieren, in dem es ausgeführt wird. Threads können benannt, angehalten und fortgesetzt werden. Ein Thread kann auch seine zugeordneten Stapel Rahmen auflisten und unter bestimmten Bedingungen in einen anderen Stapel Rahmen verschieben. Bei einem Kontext eines Stapel Rahmens kann ein Thread ggf. den zugeordneten logischen Thread zurückgeben. Ein Thread verfügt über Eigenschaften, z. b. eine Unterbrechungs Anzahl **, die im Thread Fenster der** IDE angezeigt werden kann.

- Wird durch eine [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) -Schnittstelle dargestellt, die in der Regel durch eine Debug-Engine (de) oder eine virtuelle Maschine erstellt wird, wenn ein Programm ausgeführt wird.

## <a name="see-also"></a>Weitere Informationen
- [Programs](../../extensibility/debugger/programs.md)
- [Stapel Rahmen](../../extensibility/debugger/stack-frames.md)
- [Debug-Engine](../../extensibility/debugger/debug-engine.md)
- [Debugger-Konzepte](../../extensibility/debugger/debugger-concepts.md)
- [Sitzungs-Debug-Manager](../../extensibility/debugger/session-debug-manager.md)
