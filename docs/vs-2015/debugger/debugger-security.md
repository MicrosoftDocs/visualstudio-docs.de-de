---
title: Debuggersicherheit | Microsoft-Dokumentation
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
- debugging [Visual Studio], security
- debugger, security
- security [Visual Studio], debugging best practices
ms.assetid: d4fc3c43-e844-419c-8dbb-551cc2a9b09e
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c1c56b3081f9e74ff9ab864639772c18bd758df6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686779"
---
# <a name="debugger-security"></a>Debuggersicherheit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Fähigkeit zum Debuggen eines anderen Prozesses verleiht Ihnen weitreichende Möglichkeiten, die sonst nicht zur Verfügung stehen. Dies gilt insbesondere für das Remotedebuggen. Ein bösartiger Debugger könnte sich diese Möglichkeiten zunutze machen und auf dem zu debuggenden Computer schwere Schäden verursachen.  
  
 Viele Entwickler sind sich jedoch der Tatsache nicht bewusst, dass die Sicherheit auch in entgegengesetzter Richtung bedroht werden kann. Bösartiger Code im zu debuggenden Prozess kann die Sicherheit des debuggenden Computers gefährden: Es gibt eine Reihe von Angriffsmöglichkeiten, gegen die Vorsichtsmaßnahmen zu treffen sind.  
  
## <a name="security-best-practices"></a>Empfohlene Vorgehensweisen bezüglich der Sicherheit  
 Zwischen dem Debugger und dem zu debuggenden Code besteht ein implizites Vertrauensverhältnis. Sie sollten ein Codefragment nur debuggen, wenn Sie auch bereit wären, es auszuführen. Die Grundfrage besteht darin, ob Sie dem zu debuggenden Code vertrauen können. Wenn Sie dem Code nicht vertrauen können, sollten Sie ihn nicht debuggen, oder Sie sollten ihn von einem Computer aus debuggen, bei dem die mögliche Gefährdung der Sicherheit kein Problem darstellt, da er sich in einer isolierten Umgebung befindet.  
  
 Um möglichst wenig Angriffsfläche zu bieten, sollte das Debuggen auf Produktionscomputern deaktiviert werden. Aus demselben Grund sollte das Debuggen niemals für unbegrenzte Zeit aktiviert werden.  
  
### <a name="managed-debugging-security"></a>Sicherheit bei verwaltetem Debuggen  
 Im Folgenden finden Sie allgemeine Empfehlungen für das verwaltete Debuggen.  
  
- Seien Sie vorsichtig, wenn Sie den Debugger an einen Prozess anhängen, der einem nicht vertrauenswürdigen Benutzer gehört: Das Anhängen ist mit der impliziten Annahme verbunden, dass der Prozess vertrauenswürdig ist. Wenn Sie versuchen, den Debugger an einen Prozess eines nicht vertrauenswürdigen Benutzers anzuhängen, wird ein Dialogfeld mit einer Sicherheitswarnung angezeigt, das Sie dazu auffordert, das Anhängen an den Prozess zu bestätigen. „Vertrauenswürdige Benutzer“ schließt Sie selbst und eine Reihe von Standardbenutzern ein, die üblicherweise auf Computern mit installiertem .NET Framework definiert sind, z.B. **aspnet**, **localsystem**, **networkservice**und **localservice**. Weitere Informationen finden Sie unter [Sicherheitswarnung: Das Anfügen an einen Prozess, der einem nicht vertrauenswürdigen Benutzer gehört, kann gefährlich sein. Wenn die folgenden Informationen verdächtig wirken oder Sie sich hinsichtlich der Vorgehensweise nicht sicher sind, fügen Sie an den Prozess nichts an](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015)  
  
- Seien Sie vorsichtig, wenn Sie ein Projekt aus dem Internet herunterladen und in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]laden. Dies ist auch ohne Debuggen sehr riskant. Indem Sie dies tun, gehen Sie davon aus, dass das Projekt und der darin enthaltene Code vertrauenswürdig sind.  
  
  Weitere Informationen finden Sie unter [Debugging Managed Code](../debugger/debugging-managed-code.md).  
  
### <a name="remote-debugging-security"></a>Sicherheit beim Remotedebuggen  
 Lokales Debuggen ist im Allgemeinen sicherer als Remotedebuggen. Beim Remotedebuggen wird eine wesentlich größere Angriffsfläche geboten, die ausgenutzt werden könnte.  
  
 Beim Remotedebuggen wird der Visual Studio-Remotedebugmonitor (msvsmon.exe) verwendet, bei dessen Konfiguration verschiedene Sicherheitsempfehlungen beachtet werden sollten. Der bevorzugte Authentifizierungsmodus ist die Windows-Authentifizierung, da der Modus Keine Authentifizierung ein Sicherheitsrisiko darstellt.  
  
 ![Fehlerdialogfeld](../debugger/media/dbg-err-remotepermissionschanged.png "DBG_ERR_RemotePermissionsChanged")  
  
 Bedenken Sie bei Verwendung des Windows-Authentifizierungsmodus, dass ein gewisses Sicherheitsrisiko vorliegt, wenn Sie einem nicht vertrauenswürdigen Benutzer die Berechtigung zur Verbindungsherstellung mit "msvsmon" gewähren, da der Benutzer sämtliche Zugriffsrechte auf den Computer erhält.  
  
 Debuggen Sie niemals einen unbekannten Prozess auf einem Remotecomputer: Es existieren verschiedene Angriffe, die den Computer beeinträchtigen können, auf dem der Debugger ausgeführt wird, oder die den Visual Studio-Remotedebugmonitor msvsmon.exe gefährden können. Wenn sich das Debuggen eines unbekannten Prozesses nicht vermeiden lässt, versuchen Sie, den Prozess lokal zu debuggen, und verwenden Sie eine Firewall, damit die Bedrohung auf den lokalen Computer beschränkt bleibt.  
  
 Weitere Informationen finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md).  
  
### <a name="web-services-debugging-security"></a>Sicherheit beim Debuggen von Webdiensten  
 Lokales Debuggen ist sicherer, aber häufig nicht durchführbar, da [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wahrscheinlich nicht auf dem Webserver installiert ist. Das Debuggen von Webdiensten erfolgt außer während der Entwicklung im Allgemeinen remote. Daher gelten die Empfehlungen für die Sicherheit beim Remotedebuggen auch für das Debuggen von Webdiensten. Im Folgenden finden Sie einige zusätzlich empfohlene Vorgehensweisen. Weitere Informationen finden Sie unter [Debugging XML Web Services](https://msdn.microsoft.com/c900b137-9fbd-4f59-91b5-9c2c6ce06f00).  
  
- Aktivieren Sie das Debuggen nicht auf einem Webserver, dessen Sicherheit gefährdet ist.  
  
- Überprüfen Sie vor dem Debuggen die Sicherheit des Webservers. Debuggen Sie ihn nicht, wenn Sie nicht von seiner Sicherheit überzeugt sind.  
  
- Seien Sie besonders vorsichtig, wenn Sie einen Webdienst debuggen, der vom Internet aus verfügbar ist.  
  
### <a name="external-components"></a>Externe Komponenten  
 Beachten Sie den Vertrauenswürdigkeitsstatus externer Komponenten, mit denen das Programm interagiert. Dies ist besonders wichtig, wenn Sie den Code nicht selbst geschrieben haben. Beachten Sie dabei auch die Komponenten, die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oder der Debugger möglicherweise verwenden.  
  
### <a name="symbols-and-source-code"></a>Symbole und Quellcode  
 Die folgenden beiden [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Tools erfordern ebenfalls einige Überlegungen zur Sicherheit:  
  
- Der Quellserver, der verschiedene Versionen des Quellcodes in einem Quellcoderepository bereitstellt. Dieses Tool ist nützlich, wenn Sie nicht über die aktuelle Version des Quellcodes eines Programms verfügen. [Sicherheitswarnung: Der Debugger muss diesen nicht vertrauenswürdigen Befehl ausführen](../debugger/security-warning-debugger-must-execute-untrusted-command.md).  
  
- Der Symbolserver, der die Symbole zur Verfügung stellt, die zum Debuggen eines Absturzes während eines Systemaufrufs erforderlich sind.  
  
  Weitere Informationen finden Sie unter [Angeben von Symbol- (.pdb) und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Debugger-Einstellungen und-Vorbereitung](../debugger/debugger-settings-and-preparation.md)   
 [Debugger-Grundlagen](../debugger/debugger-basics.md)   
 [Sicherheitswarnung: das Anfügen an einen Prozess, der einem nicht vertrauenswürdigen Benutzer gehört, kann gefährlich sein. Wenn die folgenden Informationen verdächtig sind oder Sie sich nicht sicher sind, fügen Sie diesen Vorgang nicht an.](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015)   
 [Sicherheitswarnung: Der Debugger muss diesen nicht vertrauenswürdigen Befehl ausführen](../debugger/security-warning-debugger-must-execute-untrusted-command.md)
