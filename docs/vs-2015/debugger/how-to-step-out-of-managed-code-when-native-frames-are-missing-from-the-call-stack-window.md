---
title: 'Gewusst wie: Ausführen von verwaltetem Code bis zum Rücksprung, wenn systemeigene Frames im Fenster "aufrufsstapel" fehlen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
helpviewer_keywords:
- Call Stack window, missing native frames
- code, managed code
- native frames
- stepping, out of managed code
- managed code, stepping out of
ms.assetid: 97cdd2a8-02a9-4a06-a5b1-c92b1e431979
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 63bd55fd254dd263540a9161e8579ea6600e97f1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690089"
---
# <a name="how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window"></a>Gewusst wie: Ausführen von verwaltetem Code bis zum Rücksprung, wenn systemeigene Rahmen im Aufruflistenfenster fehlen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn der Code native Frames enthält, die im Fenster **Aufrufliste** nicht angezeigt werden, kann das Ausführen von verwaltetem Code bis zum Rücksprung zu unerwarteten Ergebnissen führen. Sie können dieses Problem umgehen, indem Sie anstelle von **Ausführung bis Rücksprung** einen Haltepunkt verwenden.  
  
> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-display"></a>So führen Sie verwalteten Code bis zum Rücksprung aus, wenn systemeigene Rahmen in der Aufrufliste fehlen  
  
1. Legen Sie im nativen Code nach dem Aufruf an den verwalteten Code einen Positionshaltepunkt fest.  
  
2. Wählen Sie im Menü **Debuggen** die Option **Weiter** aus.  
  
     Sobald der verwaltete Aufruf fertig gestellt wurde, wird die Ausführung am Haltepunkt im systemeigenen Code beendet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [How to: Use the Call Stack Window (Vorgehensweise: Verwenden des Fensters Aufrufliste)](../debugger/how-to-use-the-call-stack-window.md)
