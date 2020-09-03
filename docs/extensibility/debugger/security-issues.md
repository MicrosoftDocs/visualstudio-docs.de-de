---
title: Sicherheitsprobleme | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40898f5633eac374206ed40bfcac96d9c1c5b753
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713054"
---
# <a name="security-issues"></a>Sicherheitsprobleme
Wenn Sie ein Programm mit Visual Studio debuggen möchten, sind nur die Berechtigungen erforderlich, die ein Entwickler zum Ausführen des Programms benötigt. Dies umfasst in den meisten Situationen das Remote Debuggen. Einige Situationen, die andere Dienste betreffen, wie z. b. der Internet Informationsdienst, benötigen möglicherweise eine höhere Berechtigungsebene.

 Während Visual Studio ausgeführt wird, verfolgt der Process Debug Manager (PDM) Debugprozesse auf dem lokalen Computer. Ein Programm mit dem Namen *msvsmon.exe* wird vom Entwickler gestartet, um das Remote Debuggen zu verarbeiten und das PDM verfügbar zu machen. (*msvsmon.exe* ist kein Dienst und muss manuell gestartet werden, um das Remote Debuggen auf diesem Computer zu aktivieren.) Wenn Visual Studio (oder *msvsmon.exe*) nicht ausgeführt wird, werden keine Prozesse zum Debuggen nachverfolgt.

 Ein Entwickler kann Programme debuggen, die Sie ohne spezielle Berechtigungen gestartet haben. Der Entwickler kann sogar Prozesse Debuggen, die von einem anderen Benutzer gestartet wurden, wenn die andere Person Mitglied derselben Sicherheitsgruppe ist. Zum Aktivieren des Remote Debuggens müssen lediglich die erforderlichen Dateien auf den Remote Computer kopiert und *msvsmon.exe*gestartet werden. Weitere Informationen finden Sie unter [Remotedebuggen](../../debugger/remote-debugging.md).

## <a name="see-also"></a>Weitere Informationen
- [Debugtasks](../../extensibility/debugger/debugging-tasks.md)
- [Process Debug Manager](../../extensibility/debugger/process-debug-manager.md)
- [Remotedebuggen](../../debugger/remote-debugging.md)
