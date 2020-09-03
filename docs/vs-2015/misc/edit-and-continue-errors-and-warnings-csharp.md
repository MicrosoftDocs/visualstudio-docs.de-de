---
title: Bearbeiten und Fortfahren mit Fehlern und Warnungen (c#) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.csharp.enc.error_4001
- vs.csharp.enc.error_4034
- vs.csharp.enc.error_4003
- vs.csharp.enc.error_4026
- vs.csharp.enc.error_4032
- vs.csharp.enc.error_4017
- vs.csharp.enc.error_4053
- vs.csharp.enc.error_4024
- vs.csharp.enc.error_4012
- vs.csharp.enc.error_4066
- vs.csharp.enc.error_4020
- vs.csharp.enc.error_4008
- vs.csharp.enc.error_4033
- vs.csharp.enc.error_4014
- vs.csharp.enc.error_4023
- vs.csharp.enc.error_4011
- vs.csharp.enc.error_4006
- vs.csharp.enc.error_4059
- vs.csharp.enc.error_4015
- vs.csharp.enc.error_4018
- vs.csharp.enc.error_4028
- vs.csharp.enc.error_4013
- vs.csharp.enc.error_4009
- vs.csharp.enc.error_4021
- vs.csharp.enc.error_4065
- vs.csharp.enc.error_4029
- vs.csharp.enc.error_4058
- vs.csharp.enc.error_4019
- vs.csharp.enc.error_4007
- vs.csharp.enc.error_4052
- vs.csharp.enc.error_4025
- vs.csharp.enc.error_4055
- vs.csharp.enc.error_4022
- vs.csharp.enc.error_4002
- vs.csharp.enc.error_4016
- vs.csharp.enc.error_4043
- vs.csharp.enc.error_4027
- vs.csharp.enc.error_4054
- vs.csharp.enc.error_4004
- vs.csharp.enc.error_4010
- vs.csharp.enc.error_4030
- vs.csharp.enc.error_4005
- vs.csharp.enc.error_4035
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], errors and warnings
- errors [C#], debugging
- errors [debugger], Edit and Continue
ms.assetid: c0e12b0a-8009-4a4a-979f-c804a91a5d9b
caps.latest.revision: 11
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eec40bc584e831f8b43b79c9bc7cee5a48a291aa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850974"
---
# <a name="edit-and-continue-errors-and-warnings-c"></a>Bearbeiten und Fortfahren: Fehlermeldungen und Warnungen (C#)
Sie haben einen Codeabschnitt auf eine Weise bearbeitet, die in der Visual C#-Funktion "Bearbeiten und Fortsetzen" nicht zulässig ist.  
  
 [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)] "Bearbeiten und Fortfahren" bietet im Unterbrechungsmodus die Möglichkeit, die Programmausführung anzuhalten, Änderungen im Ausführungscode vorzunehmen und die Programmausführung dann mit den neu eingefügten Änderungen wieder aufzunehmen.  
  
 Bearbeitungen von deklarativem Code, die die öffentliche Struktur einer Klasse beeinflussen, sind generell unzulässig. Einige der Bearbeitungen, die Sie ggf. an einer Methode, an Eigenschaftentext oder an privaten Deklarationen in einer Klasse vornehmen, sind ebenfalls unzulässig. Wenn möglich wird Code, der nicht bearbeitet werden kann von "Bearbeiten und Fortsetzen" hellgrau markiert, und eine Fehlermeldung wird angezeigt.  
  
 Weitere Informationen zu unterstützten Bearbeitungen bei „Bearbeiten und Fortfahren“ für [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)]finden Sie unter [Supported Code Changes (C#)](../debugger/supported-code-changes-csharp.md). Wenn Sie weitere Informationen zu einem bestimmten Fehler oder einer Warnung benötigen, können Sie im MSDN [Visual C#-IDE-Forum](https://social.msdn.microsoft.com/Forums/en-US/csharpide/threads)suchen oder posten.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
1. Wählen Sie im Menü **Debuggen** den Befehl **Rückgängig** aus, um die Änderung rückgängig zu machen.  
  
     - oder -  
  
2. Halten Sie die Debugsitzung an, nehmen Sie die Änderungen vor, und starten Sie eine neue Debugsitzung.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bearbeiten und Fortfahren (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)
