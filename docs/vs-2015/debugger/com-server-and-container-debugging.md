---
title: Debuggen von COM-Servern und -Containern | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.com
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- COM servers, debugging
- ActiveX controls, debugging
- COM [Visual Studio], debugging
ms.assetid: b7ce8696-ebb8-4354-a767-f76b8ada4ac1
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 631b1d35a0878bfc362b03751f35909839c7da19
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161552"
---
# <a name="com-server-and-container-debugging"></a>Debuggen von COM-Servern und -Containern
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

COM-Anwendungen führen eine Reihe von Tasks durch, die nicht direkt vom Programmierer gesteuert werden können. Zu den Bereichen, in denen ein unerwartetes Verhalten auftreten kann, gehören beispielsweise die Kommunikation zwischen DLLs, die Verwendungshäufigkeit von Objekten sowie Zwischenablageoperationen. In einem solchen Fall sollten Sie zunächst die Problemursache ermitteln.  
  
 Der Visual Studio-Debugger unterstützt das Springen über und in Container und Server. Dies schließt die Möglichkeit ein, Remoteprozeduraufrufe zu überspringen.  
  
## <a name="debugging-a-com-server-and-container-in-the-same-solution"></a><a name="BKMK_COMServerandContainerintheSameSolution"></a> Debuggen eines COM-Servers und Containers in der gleichen Projektmappe  
 COM-Server und -Container können mithilfe von zwei Projekten in derselben Projektmappe gedebuggt werden. Sie legen die geeigneten Haltepunkte pro Projekt fest und beginnen dann mit dem Debuggen. Wenn der Container einen Server aufruft und auf einen Haltepunkt trifft, wartet der Container so lange, bis der Servercode wieder verfügbar ist (d. h., bis der Debugvorgang beendet ist).  
  
 Das Debuggen eines COM-Containers ist vergleichbar mit dem Debuggen eines Standardprogramms. Hiervon ausgenommen ist jedoch das Debuggen eines Ereignisses, durch das ein Rückruf generiert wird (z. B. das Ziehen von Daten über die Containeranwendung). In diesem Fall müssen Sie einen Haltepunkt in der Rückruffunktion setzen.  
  
## <a name="debugging-a-server-application-without-container-information"></a><a name="BKMK_ServerApplicationWithoutContainerInformation"></a> Debuggen einer Serveranwendung ohne Containerinformationen  
 Wenn Sie keine Debuginformationen besitzen oder diese für Ihre Containeranwendung nicht verwenden möchten, besteht das Debuggen der Serveranwendung aus drei Schritten:  
  
1. Debuggen Sie den Server wie eine normale Anwendung.  
  
2. Legen Sie die gewünschten Haltepunkte fest.  
  
3. Starten Sie die Containeranwendung.  
  
## <a name="debugging-a-server-and-domain-isolation-sdi-application"></a><a name="BKMK_DebuggingaServerandDomainIsolationSDIApplication"></a> Debuggen einer Server- und Domänenisolationsanwendung (SDI)  
 Beim Debuggen einer SDI-Serveranwendung müssen Sie für Projekte in C/C++, C# oder Visual Basic im Dialogfeld mit den Eigenschaftenseiten zum *Projekt* in der Eigenschaft **Befehlszeilenargumente** die Option `/Embedding` oder `/Automation` festlegen.  
  
 Mithilfe dieser Befehlszeilenargumente kann die Serveranwendung vom Debugger wie von einem Container aus gestartet werden. Das Starten des Containers im Programm-Manager oder Datei-Manager bewirkt dann, dass der Container die im Debugger gestartete Instanz des Servers verwendet.  
  
 Zum Öffnen des Dialogfelds mit den Eigenschaftenseiten zum *Projekt* klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt und klicken anschließend im Kontextmenü auf „Eigenschaften“. Die Eigenschaft Befehlszeilenargumente wird angezeigt, wenn Sie die Kategorie Konfigurationseigenschaften erweitern und dann auf die Seite Debuggen klicken.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Debuggen von COM und ActiveX](../debugger/com-and-activex-debugging.md)
