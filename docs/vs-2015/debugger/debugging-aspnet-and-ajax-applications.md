---
title: Debuggen von ASP.net und AJAX-Anwendungen | Microsoft-Dokumentation
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
- debugging, WCF
- debugging ASP.NET Web applications
- debugging [ASP.NET], about ASP.NET debugging
- WCF, debugging
ms.assetid: 9d531913-541b-47b8-864d-138021fca0c6
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e0645cd28e6124e31e19b03489661c6828799cf4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686741"
---
# <a name="debugging-aspnet-and-ajax-applications"></a>Debuggen von ASP.NET- und AJAX-Anwendungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das Debuggen von [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Webanwendungen ähnelt dem Debuggen von Windows Forms oder anderen Windows-Anwendungen, da beide Arten von Anwendungen Steuerelemente und Ereignisse enthalten. Aber es gibt auch grundlegende Unterschiede zwischen den beiden Anwendungsarten:  
  
- Die Zustandsüberwachung ist in einer Webanwendung komplexer.  
  
- In einer Windows-Anwendung befindet sich der zu debuggende Code meistens an einem Ort. Bei einer Webanwendung kann der Code auf dem Client und auf dem Server vorhanden sein. Obwohl sich der gesamte [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Code auf dem Server befindet, kann auf dem Client auch JavaScript- oder [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]-Code vorhanden sein.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Vorbereitungen zum Debuggen von ASP.NET](../debugger/preparing-to-debug-aspnet.md)  
 Beschreibt die erforderlichen Schritte, um das Debuggen von [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Anwendungen zu ermöglichen.  
  
 [Debuggen von Webanwendungen](../debugger/debugging-web-applications.md)  
 Erläutert das Debuggen einer [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Anwendung, einschließlich AJAX-fähiger Skriptanwendungen.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Verwalten von Ausnahmen mit dem Debugger](../debugger/managing-exceptions-with-the-debugger.md)  
 Erläutert, warum Nur mein Code zum Debuggen von [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Ausnahmen aktiviert werden muss.  
  
 [Übersicht über Debugging und Ablauf Verfolgung von AJAX-Anwendungen](https://msdn.microsoft.com/library/92684ea0-7bb4-4a34-9203-3aa6394ce375)  
 Es werden einige Techniken und Tools erläutert, die Ihnen beim Debuggen Ihres AJAX-Codes helfen können.  
  
 [IntelliTrace](../debugger/intellitrace.md)  
 Debuggen Sie den Code schneller, indem Sie mit IntelliTrace einen Verlauf vom Zustand der Anwendung aufzuzeichnen und überprüfen, ohne die Anwendung so oft neu zu starten. Sie können Informationen zu Ereignissen und Aufrufen, die während der Ausführung der Anwendung auftreten, anzeigen und das Debuggen ab diesen Zeitpunkten starten. Erfordert Visual Studio Ultimate.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Debugger-Sicherheit](../debugger/debugger-security.md)   
 [Webanwendungen und Skript Debuggen](../debugger/debugging-web-applications-and-script.md)   
 [Debugger-Einstellungen und-Vorbereitung](../debugger/debugger-settings-and-preparation.md)   
 [Debugger – Grundlagen](../debugger/debugger-basics.md)
