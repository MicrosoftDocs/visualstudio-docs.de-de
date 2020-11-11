---
title: Debuggen von Workflows mit dem Workflow-Designer
description: Erfahren Sie, wie die Workflow-Designer die Möglichkeit bietet, Workflows und benutzerdefinierte Aktivitäten mit einem Prozess zu debuggen, der dem standardmäßigen Visual Studio-Debugger ähnelt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Workflow Designer [WFD], debugging workflows
- Workflow Designer [WFD], debugging workflows
ms.assetid: d71308cf-d464-4536-8711-0d0a8eadb255
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 45219da52cdd1ff87b7243c3cc742bb4c97a74e7
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435859"
---
# <a name="debug-workflows-with-the-workflow-designer"></a>Debuggen von Workflows mit dem Workflow-Designer

Der **Workflow-Designer** bietet die Möglichkeit, Workflows und benutzerdefinierte Aktivitäten zu debuggen. Prozess und Verhalten ähneln dem standardmäßigen Visual Studio-Debugger.

## <a name="invoke-the-workflow-debugger"></a>Workflow Debugger aufrufen

Grundsätzlich debuggen Sie Workflows genau wie in anderen Visual Studio-Programmiersprachen geschriebene Programme. Sie können den Workflowdebugger auf folgende Weise starten:

- Wählen Sie im Menü **Debuggen** die Option **an den Prozess anhängen** aus, um den ausgesuchten Host Prozess für die Workflow Instanz auszuwählen. Dieses Verfahren entspricht dem Anhängen an einen Hostprozess in verwaltetem Code.

- Drücken Sie **F5** , um die Ausführung einer Instanz des Workflows zu starten, oder, um die Ausführung nach dem Erreichen eines Breakpoints fortzusetzen.

- Verwenden Sie Remotedebuggen. Weitere Informationen zur Verwendung des Remote Debuggens finden Sie unter Gewusst [wie: Aktivieren des Remote Debuggens](/previous-versions/visualstudio/visual-studio-2010/febz73k0(v=vs.100)).

   > [!NOTE]
   > Wenn die Workflow Anwendung die x86-Architektur als Ziel verwendet und auf einem Computer gehostet wird, auf dem ein 64-Bit-Betriebssystem ausgeführt wird, funktioniert das Remote Debuggen nur dann, wenn Visual Studio auf dem Remote Computer installiert ist oder das Ziel für die Workflow Anwendung in eine **beliebige CPU** geändert wird.

## <a name="step-through-code"></a>Schritt-für-Schritt-Ausführung des Codes

- Einzel **Schritt** : schrittweises Ausführen einer Aktivität durch Drücken von **F11**. Der Debugger führt alle definierten Handler in Einzelschritten aus. Ist kein Handler definiert, wird die Aktivität übersprungen. Bei zusammengesetzten Aktivitäten, die andere Aktivitäten enthalten, führen Sie die erste ausgeführte Aktivität in einem Einzelschritt aus.

- Rück **Sprung:** Durch Drücken von **UMSCHALT** F11 wird eine Aktivität schrittweise durchlaufen + **F11**. Mit dem Verlassen einer Aktivität werden die aktuelle Aktivität und alle dazugehörigen gleichgeordneten Aktivitäten bis zum Abschluss ausgeführt. Der Debugger wird dann auf dem übergeordneten Element der aktuellen Aktivität unterbrochen. Bei der Ausführung bis zum Rücksprung von einem Codehandler unterbricht der Debugger an der Aktivität, der der Handler zugewiesen ist.

- Prozedur **Schritt** : Überspringen einer Aktivität durch Drücken von **F10** Wird ein Prozedurschritt für eine zusammengesetzte Aktivität ausgeführt, unterbricht der Debugger an der ersten ausführbaren untergeordneten Komponente der zusammengesetzten Aktivität. Wird ein Prozedurschritt für eine nicht zusammengesetzte Aktivität ausgeführt, zum Beispiel eine <xref:System.Activities.Statements.Assign>-Aktivität, führt der Debugger die Aktivität und die dazugehörigen Handler aus und unterbricht an der nächsten Aktivität. Handelt es sich bei der ausgeführten Aktivität um die letzte untergeordnete Aktivität einer zusammengesetzten Aktivität, hält der Debugger nach der Ausführung an der übergeordneten Aktivität an.

## <a name="debug-with-f5"></a>Debuggen mit F5

Wenn Sie eine Workflow Konsolen-App entwickeln, drücken Sie einfach **F5** , um das Debuggen in Ihre Anwendung und den Workflow zu starten. Wenn Sie eine Aktivitäts Bibliothek eigenständig aufbauen, müssen Sie eine ausführbare Host Anwendung als Startprojekt angeben. Wenn Sie ein Startprojekt in **Projektmappen-Explorer** festlegen möchten, klicken Sie mit der rechten Maustaste auf den Projektnamen des Hosts, und wählen Sie **als Startprojekt festlegen** aus.
