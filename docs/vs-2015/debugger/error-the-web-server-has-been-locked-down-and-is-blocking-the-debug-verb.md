---
title: 'Fehler: Der Webserver wurde gesperrt und blockiert das DEBUG-Verb | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.webdbg_debug_verb_blocked
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: 9c8c4812-17db-484d-9c1b-ffd9e3bfef5a
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b85efc44b39485476154d0f41f3261b2aeb1ea7c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203211"
---
# <a name="error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb"></a>Fehler: Der Webserver wurde gesperrt und blockiert das DEBUG-Verb
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Fehler beim schrittweisen Ausführen einer Webanwendung oder eines XML-Webdiensts, da das Tool zum Sperren der IIS-Sicherheit ausgeführt und URLScan installiert und aktiviert wurde. Durch diesen Zustand wird IIS daran gehindert, das DEBUG-Verb zu empfangen.  
  
 URLScan ist ein Sicherheitstool, das Websiteadministratoren in Kombination mit dem Tool zum Sperren der IIS-Sicherheit die Möglichkeit gibt, nicht benötigte Features zu deaktivieren und die Typen der vom Server zu verarbeitenden HTTP-Anforderungen einzugrenzen. Durch das Abweisen spezifischer HTTP-Anforderungen verhindert das URLScan-Sicherheitstool, dass potenziell schädliche Anforderungen auf den Server gelangen und dort Schaden anrichten können.  
  
 Wenn Ihre Anwendung auf Windows Server 2003 unter IIS 6.0 ausgeführt wird, müssen Sie das Tool zum Sperren der IIS-Sicherheit nicht ausführen, da IIS 6.0 diese Funktionalität bereits enthält.  
  
### <a name="to-enable-debugging-on-a-web-server-with-urlscan-installed"></a>So aktivieren Sie das Debuggen auf einem Webserver mit installiertem URLScan-Tool  
  
1. Suchen Sie die Datei Urlscan.ini. Normalerweise befindet sie sich in einem Verzeichnis wie dem Folgenden:  
  
     C:\WINNT\System32\Inetsrv\urlscan  
  
2. Erstellen Sie eine Kopie der Datei, und nennen Sie sie **Urlscan.old**.  
  
3. Öffnen Sie die ursprüngliche Version der Datei Urlscan.ini mit dem Editor oder einem Text-Editor Ihrer Wahl.  
  
4. Suchen Sie in Urlscan.ini den Abschnitt [AllowVerbs]. Fügen Sie dem Abschnitt [AllowVerbs] den Eintrag DEBUG hinzu. Wenn im Abschnitt [AllowVerbs] ;DEBUG enthalten ist, können Sie das Semikolon entfernen (durch das das Verb auskommentiert wird).  
  
5. Suchen Sie den Abschnitt [DenyVerbs]. Wenn DEBUG im Abschnitt [DenyVerbs] angezeigt wird, entfernen Sie es.  
  
6. Speichern Sie die Datei.  
  
7. Starten Sie den Server oder IIS neu.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Debuggen von Webanwendungen: Fehler und Problembehandlung](../debugger/debugging-web-applications-errors-and-troubleshooting.md)   
 [Fehler: Der Webserver konnte die angeforderte Ressource nicht finden](../debugger/error-the-web-server-could-not-find-the-requested-resource.md)
