---
title: 'Fehler: Debuggen ist nicht möglich, da ein Kerneldebugger im System aktiviert ist | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.kernel_dbg_enabled
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- kernel debugger
ms.assetid: 630a7abd-3303-4aaa-888a-6de3de14bc01
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4f2f963ad2fbdad9453f6c6b853bc720034f613c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197076"
---
# <a name="error-debugging-isn39t-possible-because-a-kernel-debugger-is-enabled-on-the-system"></a>Fehler: Debuggen ist nicht möglich, da ein Kerneldebugger im System aktiviert ist
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Beim Debuggen von verwaltetem Code kann die folgende Fehlermeldung ausgegeben werden:  
  
```  
Debugging isn't possible because a kernel debugger is enabled on the system  
```  
  
 Diese Meldung wird angezeigt, wenn Sie versuchen, verwalteten Code zu debuggen:  
  
- auf einem [!INCLUDE[win7](../includes/win7-md.md)]- oder [!INCLUDE[wiprlhext](../includes/wiprlhext-md.md)]-System, das im Debugmodus gestartet wurde.  
  
- Die Anwendung verwendet die CLR-Version 2.0, 3.0 oder 3.5.  
  
## <a name="solution"></a>Lösung  
  
#### <a name="to-fix-this-problem"></a>So beheben Sie dieses Problem  
  
- Aktualisieren Sie die Anwendung auf CLR-Version 4.0 oder 4.5.  
  
     – oder –  
  
- Deaktivieren Sie Kerneldebugging, und debuggen Sie in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
     – oder –  
  
- Debuggen Sie mit dem Kerneldebugger anstatt mit [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
     – oder –  
  
- Deaktivieren Sie im Kerneldebugger die Benutzermodusausnahmen.  
  
#### <a name="to-disable-kernel-debugging-in-the-current-session"></a>So deaktivieren Sie Kerneldebugging in der aktuellen Sitzung  
  
- Geben Sie an der Eingabeaufforderung Folgendes ein:  
  
    ```  
    Kdbgctrl.exe -d  
    ```  
  
#### <a name="to-disable-kernel-debugging-for-all-sessions-windows-vista-and-windows-7"></a>So deaktivieren Sie Kerneldebugging für alle Sitzungen (Windows Vista und Windows 7)  
  
1. Geben Sie an der Eingabeaufforderung Folgendes ein:  
  
    ```  
    bcdedit /debug off   
    ```  
  
2. Starten Sie den Computer neu.  
  
#### <a name="to-disable-kernel-debugging-for-all-sessions-other-windows-operating-systems"></a>So deaktivieren Sie Kerneldebuggen für alle Sitzungen (andere Windows-Betriebssysteme)  
  
1. Suchen Sie die Datei „boot.ini“ auf dem Systemlaufwerk (normalerweise C:\\). Die Datei "boot.ini" ist möglicherweise versteckt installiert und schreibgeschützt. Verwenden Sie zur Anzeige der Datei daher folgenden Befehl:  
  
    ```  
    dir /ASH  
    ```  
  
2. Öffnen Sie "boot.ini" im Editor, und entfernen Sie die folgenden Optionen:  
  
    ```  
    /debug  
    /debugport  
    /baudrate  
    ```  
  
3. Starten Sie den Computer neu.  
  
#### <a name="to-debug-with-the-kernel-debugger"></a>So debuggen Sie mit dem Kerneldebugger  
  
1. Wenn der Kerneldebugger verknüpft ist, werden Sie in einer Meldung gefragt, ob Sie das Debuggen fortsetzen möchten. Klicken Sie auf die Schaltfläche, um den Vorgang fortzusetzen.  
  
2. Sie erhalten möglicherweise einen `User break exception(Int 3).`-Wert. Geben Sie in diesem Fall den folgenden Befehl für den Kerneldebugger ein, um das Debuggen fortzusetzen:  
  
     `gn`  
  
## <a name="see-also"></a>Weitere Informationen  
 [Debugger-Sicherheit](../debugger/debugger-security.md)   
 [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)
