---
title: Debuggen von ASP.NET-Ausnahmen | Microsoft-Dokumentation
Description: Lernen Sie, wie Sie den Debugger so konfigurieren, dass er bei unbehandelten Ausnahmen in Ihrer ASP.NET-Anwendung angehalten wird. Sie können sicherstellen, dass die Unterbrechung in Nicht-Systemcode auftritt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], ASP.NET exceptions
- ASP.NET, exceptions
- exceptions, ASP.NET
ms.assetid: 1810096e-de8c-435e-be3d-f365d0cd0a6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 945e289f3da55c8884f4ec2cd115c65dbe3be237
ms.sourcegitcommit: 40d758f779d42c66cb02ae7face8a62763a8662b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97398648"
---
# <a name="how-to-debug-aspnet-exceptions"></a>Vorgehensweise: Debuggen von ASP.NET-Ausnahmen
Das Debuggen von Ausnahmen ist ein wichtiger Teil bei der Entwicklung einer robusten [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Anwendung. Allgemeine Informationen zum Debuggen von Ausnahmen finden Sie unter [Verwalten von Ausnahmen mit dem Debugger](../debugger/managing-exceptions-with-the-debugger.md).

 Zum Debuggen von nicht behandelten [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Ausnahmen muss sichergestellt sein, dass der Debugger dort anhält. Die [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Laufzeit verfügt über einen Ausnahmehandler der obersten Ebene. Daher wird der Debugger bei Ausnahmefehlern standardmäßig nie unterbrochen. Um den Debugger beim Auslösen einer Ausnahme zu unterbrechen, müssen Sie die Einstellung **Unterbrechen bei folgendem Ausnahmezustand: Ausgelöst** für diese bestimmte Ausnahme im Dialogfeld **Ausnahmen** auswählen.

 Wenn Sie „Nur eigenen Code“ aktiviert haben, bewirkt **Unterbrechen bei folgendem Ausnahmezustand: Ausgelöst** nicht, dass der Debugger sofort unterbrochen wird, wenn eine Ausnahme in einer .NET-Methode oder anderem Systemcode ausgelöst wird. Stattdessen wird die Ausführung fortgesetzt, bis der Debugger auf Nicht-Systemcode trifft, und dann unterbrochen. Folglich müssen Sie den Systemcode nicht schrittweise durchlaufen, wenn eine Ausnahme auftritt.

 Die Einstellung „Nur eigenen Code“ stellt Ihnen eine weitere Option zur Verfügung, die sogar noch nützlicher sein kann: **Unterbrechen bei folgendem Ausnahmezustand: Vom Benutzercode unbehandelt**. Bei dieser Einstellung für eine Ausnahme unterbricht der Debugger die Ausführung im Benutzercode nur, wenn die Ausnahme nicht durch den Benutzercode abgefangen und behandelt wird. Diese Einstellung neutralisiert die Wirkung des [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Ausnahmehandlers der obersten Ebene, da dieser kein benutzerdefinierter Code ist.

### <a name="to-enable-debugging-of-aspnet-exceptions-with-just-my-code"></a>So aktivieren Sie Debuggen der ASP.NET-Ausnahmen mit Nur mein Code

1. Klicken Sie im Menü **Debuggen** auf **Ausnahmen**.

     Das Dialogfeld **Ausnahmen** wird angezeigt.

2. Wählen Sie in der Zeile **Common Language Runtime-Ausnahmen** die Einstellung **Ausgelöst** oder **Vom Benutzercode unbehandelt** aus.

     Wenn Sie die Einstellung **Vom Benutzercode unbehandelt** verwenden möchten, muss **Nur eigenen Code** aktiviert werden.

### <a name="to-use-best-practices-for-aspnet-exception-handling"></a>Empfohlene Vorgehensweise für die ASP.NET-Ausnahmebehandlung

- Platzieren Sie `try ... catch`-Blöcke für Code, der Ausnahmen auslösen kann, die Sie vorhersehen und behandeln können. Wenn die Anwendung beispielsweise Aufrufe an einen XML-Webdienst sendet oder direkt an eine SQL Server-Instanz, sollte dieser Code in **try … catch**-Blöcken enthalten sein, weil eine Reihe von Ausnahmen auftreten können.

## <a name="see-also"></a>Siehe auch
- [Debug ASP.NET Applications (Debuggen von ASP.NET-Anwendungen)](../debugger/how-to-enable-debugging-for-aspnet-applications.md)