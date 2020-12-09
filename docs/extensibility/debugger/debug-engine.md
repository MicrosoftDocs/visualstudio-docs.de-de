---
title: Debug-Engine | Microsoft-Dokumentation
description: Erfahren Sie, wie ein Debug-Modul mit dem Interpreter oder Betriebssystem zusammenarbeitet, um Dienste wie z. b. die Ausführungs Steuerung, Breakpoints und Ausdrucks Auswertung bereitzustellen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c31d095a3e340bf7e8f7a61a8db5bcbed53f0d5f
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914217"
---
# <a name="debug-engine"></a>Debug-Engine
Eine Debug-Engine (de) verwendet den Interpreter oder das Betriebssystem, um debuggingdienste wie Ausführungs Steuerung, Breakpoints und Ausdrucks Auswertung bereitzustellen. Die de ist für die Überwachung des Status eines Programms zuständig, das gedeppt wird. Um dies zu erreichen, verwendet die de alle verfügbaren Methoden in der unterstützten Laufzeit, unabhängig davon, ob die CPU oder die von der Laufzeit bereitgestellten APIs verwendet werden.

 Der Common Language Runtime (CLR) stellt z. b. Mechanismen zum Überwachen eines laufenden Programms über die ICorDebugXxx-Schnittstellen bereit. Ein de-Element, das die CLR unterstützt, verwendet die entsprechenden ICorDebugXxx-Schnittstellen, um das debuggt eines verwalteten Code Programms nachzuverfolgen. Anschließend werden alle Zustandsänderungen an den Sitzungs-Debug-Manager (SDM) übermittelt, der diese Informationen an die IDE weiterleitet [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

> [!NOTE]
> Eine Debug-Engine hat eine bestimmte Laufzeit als Ziel, d. h. das System, in dem das Debuggingprogramm ausgeführt wird. Die CLR ist die Laufzeit für verwalteten Code, und die Win32-Laufzeit ist für Native Windows-Anwendungen vorgesehen. Wenn die von Ihnen erstellte Sprache auf eine dieser beiden Laufzeiten abzielen kann, stellt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bereits die erforderlichen Debug-engines bereit. Sie müssen lediglich eine Ausdrucks Auswertung implementieren.

## <a name="debug-engine-operation"></a>Debug-Engine-Vorgang
 Die Überwachungsdienste werden über die de-Schnittstellen implementiert und können dazu führen, dass das Debugpaket zwischen verschiedenen Betriebsmodi übergeht. Weitere Informationen finden Sie unter [Betriebsmodi](../../extensibility/debugger/operational-modes.md). Es gibt in der Regel nur eine de-Implementierung pro Laufzeitumgebung.

> [!NOTE]
> Es gibt zwar separate de-Implementierungen für Transact-SQL und [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] VBScript und verwenden [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] nur ein einzelnes de-Objekt.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] das Debuggen ermöglicht debugengines, eine von zwei Methoden auszuführen: entweder in demselben Prozess wie die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Shell oder im gleichen Prozess wie das zu debuggende Zielprogramm. Das letztere Formular tritt normalerweise auf, wenn der Prozess, der gedebuggt wird, tatsächlich ein Skript ist, das unter einem Interpreter Die Debug-Engine muss über eine intime Kenntnis des interpreters verfügen, um das Skript zu überwachen. In diesem Fall ist der Interpreter tatsächlich eine Laufzeit. Debug-engines gelten für bestimmte Lauf Zeit Implementierungen. Außerdem kann die Implementierung eines einzelnen de-Prozesses über Prozess-und Computer Grenzen hinweg aufgeteilt werden (z. b. Remote Debugging).

 Der de macht die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugschnittstellen verfügbar. Die gesamte Kommunikation erfolgt über com. Ob die de in-Process, out-of-Process oder auf einem anderen Computer geladen wird, wirkt sich nicht auf die Komponenten Kommunikation aus.

 Die Funktion "de" funktioniert mit einer Ausdrucks auswerterkomponente, um die Verwendung der Syntax von Ausdrücken durch den de für diese bestimmte Laufzeit zu ermöglichen. Der Dienst kann auch mit einer symbolhandlerkomponente auf die symbolischen Debuginformationen zugreifen, die vom sprach Compiler generiert werden. Weitere Informationen finden Sie unter [Ausdrucks Auswertung](../../extensibility/debugger/expression-evaluator.md) und [Symbol Anbieter](../../extensibility/debugger/symbol-provider.md).

## <a name="see-also"></a>Weitere Informationen
- [Debugger-Komponenten](../../extensibility/debugger/debugger-components.md)
- [Ausdrucks Auswertung](../../extensibility/debugger/expression-evaluator.md)
- [Symbol Anbieter](../../extensibility/debugger/symbol-provider.md)
