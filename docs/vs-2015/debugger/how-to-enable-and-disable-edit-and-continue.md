---
title: 'Vorgehensweise: Aktivieren und Deaktivieren von "Bearbeiten und Fortfahren" | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- /INCREMENTAL linker option
- Apply Code Changes command
- Edit and Continue, disabling
- code changes, applying in break mode
- INCREMENTAL linker option
- Edit and Continue, enabling
- break mode, applying code changes
- Edit and Continue, applying code changes
- Step command
- Go command
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 70914da9be4046589a0ca3b8e5fd4ae13210ca51
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65689261"
---
# <a name="how-to-enable-and-disable-edit-and-continue"></a>Gewusst wie: Aktivieren und Deaktivieren von "Bearbeiten und Fortfahren"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können "Bearbeiten und Fortfahren" im Dialogfeld " **Optionen** " zur Entwurfszeit deaktivieren oder aktivieren. Sie können diese Einstellung nicht ändern, während Sie debuggen.  
  
 Die Funktion "Bearbeiten und Fortfahren" funktioniert nur in Debugversionen. Bei systemeigenem C++ muss die /INCREMENTAL-Option verwendet werden, damit "Bearbeiten und Fortfahren" funktioniert.  
  
## <a name="procedures"></a>Prozeduren  
  
#### <a name="to-enabledisable-edit-and-continue"></a>So aktivieren bzw. deaktivieren Sie "Bearbeiten und Fortfahren"  
  
1. Öffnen Sie die Seite "Debugoptionen" (Extras **/Optionen/Debugging**).  
  
2. Scrollen Sie nach unten zur Kategorie **Bearbeiten und Fortfahren** .  
  
3. Aktivieren Sie zum aktivieren das Kontrollkästchen **Bearbeiten und Fortfahren aktivieren** . Deaktivieren Sie das Kontrollkästchen, wenn Sie die Funktion deaktivieren möchten.  
  
   > [!NOTE]
   > Wenn IntelliTrace aktiviert ist und Sie IntelliTrace-Ereignisse und Aufrufinformationen erfassen, wird "Bearbeiten und Fortfahren" deaktiviert. Weitere Informationen finden Sie unter [Konfigurieren von IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
4. Klicken Sie auf **OK**.  
  
   Weitere Informationen zu diesen Optionen finden Sie unter [Allgemein, Debuggen, Dialog Feld "Optionen](../debugger/general-debugging-options-dialog-box.md)".  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bearbeiten und Fortfahren](../debugger/edit-and-continue.md)
