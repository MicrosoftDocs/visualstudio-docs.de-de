---
title: Anpassen der nativen Laufzeitüberprüfung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.crt
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- runtime_checks pragma
- debugger, native run-time checks
- /RTC compiler option [C++], native run-time checks
- customizing CRT error checking
- native run-time checks, customizing
ms.assetid: 76a365fe-6439-49db-8603-34058b78e5a8
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 434f2425b1eeefd82b954e47a8ced55491a7ec11
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697822"
---
# <a name="native-run-time-checks-customization"></a>Anpassen der systemeigenen Laufzeitüberprüfung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bei der Kompilierung mit **/RTC** (Run-Time Checks, Laufzeitüberprüfungen) oder mit dem `runtime_checks`-Pragma stellt die C-Laufzeitbibliothek native Laufzeitüberprüfungen zur Verfügung. In einigen Fällen können Sie die Laufzeitüberprüfung anpassen:  
  
- Zum Weiterleiten von Meldungen der Laufzeitüberprüfung an eine Datei oder an ein vom Standardziel abweichendes Ziel.  
  
- Zum Festlegen eines Ausgabeziels für Meldungen der Laufzeitüberprüfung im Debugger eines Drittanbieters.  
  
- Zum Erfassen von Meldungen der Laufzeitüberprüfung aus einem Programm, das mit einer Releaseversion der C-Laufzeitbibliothek kompiliert wurde. Releaseversionen der Bibliothek verwenden zum Erfassen von Laufzeitfehlern nicht `_CrtDbgReportW`. Stattdessen wird für jeden Laufzeitfehler ein Dialogfeld **Assert** angezeigt.  
  
  Sie haben folgende Möglichkeiten, um Laufzeitfehlerüberprüfungen anzupassen:  
  
- Schreiben einer Funktion zur Erstellung von Laufzeitfehlerberichten. Weitere Informationen finden Sie unter [Vorgehensweise: Schreiben einer Berichtsfunktion für Laufzeitfehler](../debugger/how-to-write-a-run-time-error-reporting-function.md).  
  
- Anpassen des Ziels für Fehlermeldungen.  
  
- Abfrage von Informationen zu Laufzeitfehlerüberprüfungen.  
  
## <a name="customize-the-error-message-destination"></a>Anpassen des Ziels für Fehlermeldungen  
 Wenn Sie `_CrtDbgReportW` zum Erfassen von Fehlern verwenden, können Sie das Ziel der Fehlermeldungen mit `_CrtSetReportMode` angeben.  
  
 Wenn Sie mit einer benutzerdefinierten Berichtsfunktion arbeiten, verwenden Sie `_RTC_SetErrorType`, um Fehlern Berichtstypen zuzuordnen.  
  
## <a name="query-for-information-about-run-time-checks"></a>Abfragen von Informationen zu Laufzeitüberprüfungen  
 `_RTC_NumErrors` gibt die Anzahl der Fehlertypen zurück, die bei Laufzeitfehlerüberprüfungen entdeckt wurden. Um eine kurze Beschreibung der einzelnen Fehler zu erhalten, können Sie eine Schleife von 0 bis zum Rückgabewert von `_RTC_NumErrors` durchlaufen, wobei der Iterationswert in jedem Schleifendurchlauf an `_RTC_GetErrDesc` übergeben wird. Weitere Informationen finden Sie unter [_RTC_NumErrors](https://msdn.microsoft.com/library/7e82adae-38e2-4f8b-bc0b-37bda8109fd1) und [_RTC_GetErrDesc](https://msdn.microsoft.com/library/7994ec2b-5488-4fd4-806d-a166c9a9f927).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gewusst wie: Verwenden von nativen Laufzeitüberprüfungen](../debugger/how-to-use-native-run-time-checks.md)   
 [runtime_checks](https://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b)   
 [_CrtDbgReport, _CrtDbgReportW](https://msdn.microsoft.com/library/6e581fb6-f7fb-4716-9432-f0145d639ecc)
