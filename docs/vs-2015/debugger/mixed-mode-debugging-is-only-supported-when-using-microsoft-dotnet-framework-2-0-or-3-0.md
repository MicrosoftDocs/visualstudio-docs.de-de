---
title: Debuggen im gemischten Modus wird nur bei Verwendung von Microsoft .NET Framework, Version 2.0 oder 3.0, unterstützt | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_to_old
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: f607af6f-57fe-472a-a32e-b6202067aa96
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fc45927ad6cc1189ed1d08328b4dd362821cdcb6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696471"
---
# <a name="mixed-mode-debugging-is-only-supported-when-using-microsoft-net-framework-20-or-30"></a>Debuggen im gemischten Modus wird nur bei Verwendung von Microsoft .NET Framework, Version 2.0 oder 3.0, unterstützt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ältere Versionen von Microsoft .NET Framework 2.0 bieten keine Unterstützung für das Debuggen im gemischten Modus von 64-Bit-Prozessen. Dies bedeutet, dass Sie während des Debuggens nicht von verwaltetem Code zu systemeigenem Code oder von systemeigenem Code zu verwaltetem Code wechseln können.  
  
 Sie können Folgendes tun, um dieses Problem zu umgehen:  
  
- Aktualisieren Sie das Projekt, um Microsoft .NET Framework 2.0 oder 3.0 zu verwenden.  
  
- Debuggen Sie den verwalteten und den systemeigenen Code in separaten Debugsitzungen.  
  
- Debuggen Sie den gemischten Code als 32-Bit-Prozess, wie in den folgenden Prozeduren beschrieben.  
  
### <a name="to-change-the-operating-system-to-32-bit-visual-basic-or-c"></a>So ändern Sie das Betriebssystem in 32-Bit (Visual Basic oder C#)  
  
1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und klicken Sie im Kontextmenü auf **Eigenschaften**.  
  
2. Klicken Sie auf den Eigenschaftenseiten auf die Registerkarte **Kompilieren** oder auf die Registerkarte **Debuggen**.  
  
3. Klicken Sie auf **Plattform**, und wählen Sie **x86** aus der Liste der Plattformen aus.  
  
     Die Visual Basic- und C#-Compiler erzeugen standardmäßig Code, der mit jeder CPU ausgeführt werden kann. Auf einem 64-Bit-Computer werden diese Binärdateien als 64-Bit-Prozesse ausgeführt. Wählen Sie **Win32** anstelle von **AnyCPU** aus, wenn Sie die Ausführung in einem 32-Bit-Prozess wünschen.  
  
### <a name="to-change-the-operating-system-to-32-bit-cc"></a>So ändern Sie das Betriebssystem in 32-Bit (C/C++)  
  
1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und klicken Sie im Kontextmenü auf **Eigenschaften**.  
  
     Klicken Sie auf den Eigenschaftenseiten auf **Plattform**, und wählen Sie **Win32** aus der Liste der Plattformen aus.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Siehe [Einrichten des Transact-SQL-Debuggings](https://msdn.microsoft.com/3db09e68-edcc-42de-9c22-4e97cfd55ab3).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Debuggen von 64-Bit-Anwendungen](../debugger/debug-64-bit-applications.md)
