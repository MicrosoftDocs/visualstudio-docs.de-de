---
title: Stapel Rahmen | Microsoft-Dokumentation
description: In diesem Artikel werden die Definition und die Rolle eines Stapel Rahmens in der Debugger-Architektur in Visual Studio beschrieben.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 97adb5d453e147c45ae1f268a20a2d3091286508
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960727"
---
# <a name="stack-frames"></a>Stapel Rahmen
In der Debugger-Architektur ein *Stapel Rahmen*:

- Eine Abstraktion eines Stapels, der den Ausführungs Kontext eines Threads bereitstellt. Ein Thread wird immer innerhalb einer Funktion ausgeführt. Ein Stapel Rahmen enthält die lokalen Variablen der Funktion und die darin verwendeten Argumente. Zum Debuggen mit Visual Studio muss die zu debuggende Sprache oder Umgebung Stapel Rahmen unterstützen.

- Kann identifizieren und beschreiben und den zugeordneten Thread zurückgeben. Ein Stapel Rahmen kann auch den Code Kontext zurückgeben, der den aktuellen Anweisungs Zeiger und die zugeordneten Kontexte der Dokumentation und Ausdrucks Auswertung darstellt.

- Verfügt über Eigenschaften, die den Namen, den Typ und den Wert lokaler Variablen und Argumente beschreiben und in verschiedenen IDE-Debugfenstern angezeigt werden.

- Wird durch eine [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) -Schnittstelle dargestellt, die in der Regel durch eine Debug-Engine (de) oder eine virtuelle Maschine erstellt wird, wenn ein Thread ausgeführt wird.

## <a name="see-also"></a>Weitere Informationen
- [Debugger-Kontexte](../../extensibility/debugger/debugger-contexts.md)
- [Debugger-Konzepte](../../extensibility/debugger/debugger-concepts.md)
- [Debug-Engine](../../extensibility/debugger/debug-engine.md)
- [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)
