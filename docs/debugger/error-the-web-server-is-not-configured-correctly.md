---
title: Der Webserver ist nicht richtig konfiguriert. | Microsoft-Dokumentation
ms.date: 09/20/2017
ms.topic: error-reference
f1_keywords:
- vs.debug.remote.projnotconfigured
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3a5c50822b516b73206791e3d8538bd174cfc8f6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871233"
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>Fehler: Der Webserver ist nicht richtig konfiguriert

Unter Umständen müssen Sie auch IIS zurücksetzen, nachdem Sie die hier aufgeführten Problembehandlungsschritte ausgeführt haben und bevor Sie das Debugging erneut versuchen. Öffnen Sie hierzu eine Administratoreingabeaufforderung, und geben Sie `iisreset` ein.

Gehen Sie wie folgt vor, um das Problem zu beheben:

1. Wenn die auf dem Server gehostete Web-App als Releasebuild konfiguriert ist, veröffentlichen Sie sie erneut als Debugbuild, und überprüfen Sie, ob die Datei „web.config“ im Kompilierungselement `debug=true` enthält. Setzen Sie IIS zurück, und wiederholen Sie den Vorgang.

    Wenn Sie beispielsweise ein Veröffentlichungsprofil für einen Releasebuild verwenden, ändern Sie ihn in einen Debugbuild, und veröffentlichen Sie ihn erneut. Andernfalls wird das debug-Attribut beim Veröffentlichen auf `false` festgelegt.

2. (IIS) Vergewissern Sie sich, dass der physische Pfad korrekt ist. In IIS befindet sich diese Einstellung unter **Grundeinstellungen > Physischer Pfad** (in älteren Versionen von IIS unter **Erweiterten Einstellungen**).

    Der physische Pfad ist unter Umständen falsch, wenn die Webanwendung auf einen anderen Computer kopiert, manuell umbenannt oder verschoben wurde. Setzen Sie IIS zurück, und wiederholen Sie den Vorgang.

3. Vergewissern Sie sich beim lokalen Debuggen in Visual Studio, dass in den Eigenschaften der richtige Server ausgewählt ist. (Öffnen Sie abhängig vom Projekttyp **Eigenschaften > Web > Server** oder **Eigenschaften > Debuggen**. Öffnen Sie bei einem Web Forms-Projekt **Eigenschaftenseiten > Startoptionen > Server**.)

    Wenn Sie einen externen (benutzerdefinierten) Server wie IIS verwenden, muss die URL korrekt sein. Wählen Sie andernfalls IIS Express aus, und versuchen Sie es erneut.

4. (IIS) Stellen Sie sicher, dass auf dem Server die richtige ASP.NET-Version installiert ist.

    Das Problem kann durch nicht übereinstimmende Versionen von ASP.NET in IIS und in Ihrem Visual Studio-Projekt verursacht werden. Möglicherweise müssen Sie die Framework-Version in der Datei „web.config“ festlegen. Verwenden Sie zum Installieren von ASP.NET in IIS den [Webplattform-Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). Weitere Informationen finden Sie unter [IIS 8.0: Verwenden von ASP.NET 3.5 und ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45). Lesen Sie bei Verwendung von ASP.NET Core die Informationen unter [Hosten von ASP.NET Core unter Windows mit IIS](https://docs.asp.net/en/latest/publishing/iis.html).

4. Wenn der `maxConnection`-Grenzwert in IIS zu niedrig ist und Sie über zu viele Verbindungen verfügen, müssen Sie unter Umständen den [Verbindungsgrenzwert erhöhen](/iis/configuration/system.applicationhost/sites/sitedefaults/limits).

## <a name="see-also"></a>Siehe auch
- [Remotedebuggen von ASP.NET auf einem Remotecomputer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [Debuggen von Webanwendungen: Fehler und Problembehandlung](../debugger/debugging-web-applications-errors-and-troubleshooting.md)