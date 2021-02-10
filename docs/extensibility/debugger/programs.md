---
title: Programme | Microsoft-Dokumentation
description: In diesem Artikel werden die Definition und die Rolle eines Programms in der Debugger-Architektur in Visual Studio beschrieben.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5205dba6cddf104d0cb05f01acbc43f6927acaaf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948425"
---
# <a name="programs"></a>Programs
In der Debugger-Architektur ist ein *Programm*:

- Ist ein Container für einen Satz von Threads und einen Satz von Modulen. Ein Programm hat im Windows-Betriebssystem keine einzige Analogie.

     Ein Programm ist eine Art von unter Prozessen. Wenn Sie z. b. eine Website Debuggen, kann ein Skript als Programm angesehen werden. Während ein Skript im Skript-Engine-Prozess unabhängig von anderen Skripts ausgeführt wird, verfügt es auch über einen eigenen Satz von Threads. Eine Debug-Engine (de) wird an ein Programm angefügt, nicht an einen Prozess oder einen Thread.

- Kann sich selbst und den Prozess identifizieren, in dem er ausgeführt wird. Ein Programm kann angefügt werden, von getrennt werden und den von ihm erstellten Dienst beschreiben, sofern vorhanden. Ein Programm kann auch ausgeführt, beendet, fortgesetzt und beendet werden.

- Kann alle zugehörigen Threads auflisten. Ein Programm kann auch seinen eigenen disassemblystream bereitstellen und alle Code Kontexte einer bestimmten Dokument Position auflisten.

- Wird durch eine [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) -Schnittstelle dargestellt, die erstellt wird, bevor das Programm angefügt wird, oder als Teil des Anfüge Prozesses, abhängig von der Implementierung. Wenn ein Port die Programme eines Prozesses auflistet, wird jedes Programm in Übereinstimmung mit einer entsprechenden [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) -Schnittstelle erstellt, die als Argument an [addprogram Node](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)weitergeleitet wird. Obwohl debugengines auch `IDebugProgram2` Schnittstellen zur Darstellung von Programmen erstellen, werden diese Programme nicht in Übereinstimmung mit einem Programmknoten erstellt. Die `IDebugProgramNode2` von einem de erstellten Schnittstellen werden für das eigentliche Debuggen verwendet, während die von einem Port erstellten Schnittstellen nur für die Ermittlung der Programme verwendet werden, die in einem Prozess ausgeführt werden.

## <a name="see-also"></a>Weitere Informationen
- [Prozesse](../../extensibility/debugger/processes.md)
- [Programmknoten](../../extensibility/debugger/program-nodes.md)
- [Module](../../extensibility/debugger/modules.md)
- [Debugger-Konzepte](../../extensibility/debugger/debugger-concepts.md)
- [Debug-Engine](../../extensibility/debugger/debug-engine.md)
- [Dokument Position](../../extensibility/debugger/document-position.md)
- [Code Kontext](../../extensibility/debugger/code-context.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
