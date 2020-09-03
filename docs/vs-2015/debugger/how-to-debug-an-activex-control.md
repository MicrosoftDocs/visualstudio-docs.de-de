---
title: 'Vorgehensweise: Debuggen von ActiveX-Steuerelementen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vc.controls.debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- testing [Visual Studio], test containers
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- data-bound controls, ActiveX
- test container
- containers, specifying for debug sessions
- ActiveX controls, debugging
- testing [Visual Studio], ActiveX controls
ms.assetid: bbc02cf7-a7e6-44fe-99af-87a43e1d7251
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9524ab08ab955609f29f437e8a1576af02738aa1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704465"
---
# <a name="how-to-debug-an-activex-control"></a>Vorgehensweise: Debuggen von ActiveX-Steuerelementen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

HINWEIS]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü Extras auf Einstellungen importieren und exportieren, um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Um das ActiveX-Steuerelement zu debuggen, müssen Sie einen Container (ausführbare Datei) angeben, in dem das Steuerelement ausgeführt werden kann.  
  
### <a name="to-specify-a-container-for-the-debug-session"></a>So legen Sie einen Container für die Debugsitzung fest  
  
1. Wählen Sie im Projektmappen-Explorer das Projekt aus.  
  
2. Klicken Sie im Menü **Ansicht** auf **Eigenschaftenseiten**.  
  
3. Öffnen Sie im Dialogfeld **Projekteigenschaftenseiten** den Ordner **Konfigurationseigenschaften**, und wählen Sie **Debuggen** aus.  
  
4. Suchen Sie in der Kategorie **Debuggen** die Eigenschaft **Befehl**.  
  
5. Geben Sie den Pfadnamen für den Container an. Beispielsweise C:\Programme\Internet Explorer\IEXPLORE.EXE.  
  
6. Wenn Sie Internet Explorer als Container festlegen und Active Desktop verwenden, geben Sie `/new` in das Feld **Befehlsargumente** ein.  
  
7. Klicken Sie auf **OK**.  
  
     Wenn Sie keinen Container im Dialogfeld **Projekteigenschaftenseiten** festlegen, können Sie dies zu Beginn des Debuggens nachholen. Falls Sie zum Starten des Debugvorgangs einen Ausführungsbefehl wählen, wird das Dialogfeld [Executable for Debugging Session](../debugger/executable-for-debugging-session-dialog-box.md) (Ausführbare Datei für die Debugsitzung) angezeigt. Geben Sie den Pfadnamen des Containers im Dialogfeld an.  
  
## <a name="see-also"></a>Weitere Informationen  
 [ActiveX-Steuerelemente](https://msdn.microsoft.com/library/52aaec4d-3889-402e-b57d-758078f8ac57)   
 [Testen von Eigenschaften und Ereignissen mit dem Test Container](https://msdn.microsoft.com/library/626867cf-fe53-4c30-8973-55bb93ef3917)   
 [COM-und ActiveX-Debugging](../debugger/com-and-activex-debugging.md)   
 [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md)
