---
title: 'Vorgehensweise: Starten und Beenden der Sammlung von Leistungsdaten | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.wizard.summarypage
helpviewer_keywords:
- profiling tools, launching sessions
- performance sessions, launching
- performance sessions, ending
- profiling tools, ending sessions
ms.assetid: 9f6eb0d5-d9e9-4bec-b627-445065610bce
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 15c6d6c904bbab27bac541894ed6cd4f9e1f80f1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202678"
---
# <a name="how-to-start-and-end-performance-data-collection"></a>Vorgehensweise: Starten und Beenden der Sammlung von Leistungsdaten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie müssen die Zielbinärdatei, für die Sie ein Profil erstellen möchten, vor Beginn der Profilerstellung zur Leistungssitzung hinzufügen. Klicken Sie mit der rechten Maustaste auf **Ziele** im **Leistungs-Explorer** und anschließend auf **Zielbinärdatei hinzufügen**, um ein Ziel hinzuzufügen. Wählen Sie im Dialogfeld **Zielbinärdatei hinzufügen** den Dateinamen aus und klicken Sie anschließend auf **Öffnen**. Es wird eine neue Binärdatei hinzugefügt.  
  
### <a name="to-start-profiling"></a>So starten Sie die Profilerstellung  
  
1. Klicken Sie mit der rechten Maustaste auf den Namen der Leistungssitzung im Fenster **Leistungs-Explorer** und wählen Sie eine der folgenden Optionen:  
  
    - **Mit Profilerstellung starten** – die Anwendung wird gestartet und beginnt sofort mit der Profilerstellung.  
  
    - **Mit angehaltener Profilerstellung starten** – die Anwendung wird gestartet, aber beginnt nicht mit der Profilerstellung. Sie können die Profilerstellung starten, indem Sie **Auflistung wiederaufnehmen** im Fenster **Steuerung der Datensammlung** auswählen. Weitere Informationen finden Sie unter Vorgehensweise: anhalten und Fortsetzen der [Erfassung von Leistungsdaten](../profiling/how-to-pause-and-resume-performance-data-collection.md).  
  
### <a name="to-end-profiling"></a>So beenden Sie die Profilerstellung  
  
- Die bevorzugte Methode zum Beenden einer Profilerstellungssitzung ist das Beenden der Anwendung. Klicken Sie auf der Symbolleiste **Leistungs-Explorer** auf **Stop**, um die Profilerstellung sofort zu beenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Steuern der Datensammlung](../profiling/controlling-data-collection.md)   
 [Vorgehensweise: anhalten und Fortsetzen der Erfassung von Leistungsdaten](../profiling/how-to-pause-and-resume-performance-data-collection.md)
