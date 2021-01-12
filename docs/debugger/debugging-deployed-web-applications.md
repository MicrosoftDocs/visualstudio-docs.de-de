---
title: Debuggen bereitgestellter ASP.NET-Anwendungen | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie Visual Studio zum Debuggen einer bereitgestellten ASP.NET-Anwendung verwenden, indem Sie den Debugger an den Workerprozess anhängen und sicherstellen, dass dieser über Zugriff auf Symbole für die Anwendung verfügt.
ms.custom: SEO-VS-2020
ms.date: 06/30/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ASP.NET Web applications
- Web services, debugging
- XML, debugging Web services
- debugging Web services
- ASP.NET, debugging Web applications
- XML Web services, debugging
ms.assetid: b938a91b-be96-416f-83bc-4177e7f3929a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 1e8c99f1988ef1aa2e14c7b0a4d6ed46e10f6f1e
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727046"
---
# <a name="debugging-deployed-aspnet-applications"></a>Debuggen bereitgestellter ASP.NET-Anwendungen
Um eine bereitgestellte und ausgeführte Anwendung über [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zu debuggen, müssen Sie den Debugger an den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Arbeitsprozess anhängen und sicherstellen, dass der Debugger auf Symbole für die Anwendung zugreifen kann. Außerdem müssen Sie die Quelldateien für die Anwendung lokalisieren und öffnen. Weitere Informationen finden Sie unter [Angeben von Symboldateien (PDB-Dateien) und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), [Vorgehensweise: Herausfinden des ASP.NET-Prozessnamens](../debugger/how-to-find-the-name-of-the-aspnet-process.md)und [Systemanforderungen](../debugger/aspnet-debugging-system-requirements.md).

> [!WARNING]
> Wenn der Debugger an den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Workerprozess angefügt wird, wird beim Erreichen eines Breakpoints der gesamte verwaltete Code im Workerprozess angehalten. Das Anhalten des gesamten verwalteten Codes im Arbeitsprozess kann zu einem Arbeitsstopp für alle Benutzer des Servers führen. Wenn Sie auf einem Produktionsserver debuggen, müssen Sie unter allen Umständen die möglichen Auswirkungen auf die Produktion beachten.

Das Anhängen an den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Arbeitsprozess unterscheidet sich nicht vom Anhängen an einen beliebigen anderen Remoteprozess. Wenn das passende Projekt nicht geöffnet ist, wird nach dem Anhängen ein Dialogfeld angezeigt, sobald die Anwendung unterbrochen wird. Dieses Dialogfeld fordert Sie auf, den Speicherort der Quelldateien der Anwendung anzugeben. Der im Dialogfeld eingegebene Dateiname muss mit dem Dateinamen übereinstimmen, der in den Debugsymbolen (auf dem Webserver) angegeben ist. Weitere Informationen finden Sie unter [Anfügen an laufende Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md). Zum Einrichten des Remotedebuggens auf IIS, finden Sie unter [Remotedebuggen von ASP.NET auf einem Remotecomputer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md).

> [!NOTE]
> Viele [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Webanwendungen verweisen auf DLLs, die Geschäftslogik oder sonstigen nützlichen Code enthalten. Durch einen solchen Verweis wird die DLL vom lokalen Computer in den Ordner \bin des virtuellen Verzeichnisses der Webanwendung kopiert, wenn Sie die App bereitstellen. Beim Debuggen sollten Sie beachten, dass die Webanwendung nicht auf die Kopie der DLL auf dem lokalen Computer, sondern auf diese Kopie der DLL verweist.

## <a name="see-also"></a>Siehe auch
- [Debug ASP.NET Applications (Debuggen von ASP.NET-Anwendungen)](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [How to: Debuggen für ASP.NET-Anwendungen aktivieren](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [How to: Herausfinden des ASP.NET-Prozessnamens](../debugger/how-to-find-the-name-of-the-aspnet-process.md)
- [Angeben von Symbol(PDB)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)