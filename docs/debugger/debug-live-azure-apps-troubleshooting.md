---
title: Problembehandlung beim Debuggen von Momentaufnahmen | Microsoft-Dokumentation
description: Hier finden Sie grundlegende Informationen zur Problembehandlung und zu bekannten Problemen beim Debuggen von Momentaufnahmen in Visual Studio. Laden Sie ICorProfiler, ohne Ausfallzeiten am Produktionsstandort zu verursachen.
ms.custom: SEO-VS-2020
ms.date: 04/24/2019
ms.topic: troubleshooting
helpviewer_keywords:
- debugger
ms.assetid: 511a0697-c68a-4988-9e29-8d0166ca044a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 55d6c5a4b9485051f8c0293ad72f78e5cdddca59
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873263"
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Problembehandlung und bekannte Probleme beim Debuggen von Momentaufnahmen in Visual Studio

Wenn die in diesem Artikel beschriebenen Schritte Ihr Problem nicht lösen, können Sie in der [Entwicklercommunity](https://aka.ms/feedback/suggest?space=8) nach Ihrem Problem suchen oder ein neues Problem melden, indem Sie in Visual Studio auf **Hilfe** > **Feedback senden** > **Problem melden** klicken.

## <a name="issue-attach-snapshot-debugger-encounters-an-http-status-code-error"></a>Problem: „Momentaufnahmedebugger anfügen“ führt zu einem HTTP-Statuscodefehler

Wenn der folgende Fehler im Fenster **Ausgabe** während des Anfügeversuchs angezeigt wird, liegt dies möglicherweise an einem der unten aufgeführten bekannten Probleme. Testen Sie die vorgeschlagenen Lösungen. Wenn das Problem weiterhin besteht, verwenden Sie eine der oben genannten Kontaktmöglichkeiten.

`[TIMESTAMP] Error --- Unable to Start Snapshot Debugger - Attach Snapshot Debugger failed: System.Net.WebException: The remote server returned an error: (###) XXXXXX`

### <a name="401-unauthorized"></a>401 – Nicht autorisiert

Dieser Fehler deutet darauf hin, dass der von Visual Studio für Azure ausgegebene REST-Aufruf ungültige Anmeldeinformationen verwendet. 

Führen Sie diese Schritte aus:

* Überprüfen Sie, ob Ihr Visual Studio-Personalisierungskonto Berechtigungen für das Azure-Abonnement und die Ressourcen hat, an die Sie anfügen möchten. Eine schnelle Möglichkeit, dies bestätigen zu können, ist es, zu überprüfen, ob die Ressource im Dialogfeld über **Debuggen** > **Momentaufnahmedebugger anfügen…**  > **Azure-Ressource** > **Vorhandene auswählen** oder im Cloud-Explorer verfügbar ist.
* Wenn dieser Fehler weiterhin besteht, verwenden Sie einen der Kanäle für Feedback, die zu Beginn dieses Artikels beschrieben wurden.

Wenn Sie Authentifizierung/Autorisierung (EasyAuth) für Ihren App Service aktiviert haben, tritt möglicherweise Fehler 401 mit LaunchAgentAsync in der Fehlermeldung der Aufrufliste auf. Stellen Sie sicher, dass **Die auszuführende Aktion, wenn die Anforderung nicht authentifiziert ist** im Azure-Portal auf **Anonyme Anforderungen erlauben (keine Aktion)** festgelegt ist, und stellen Sie stattdessen die Datei „authorization.json“ in „D:\Home\sites\wwwroot“ mit folgendem Inhalt bereit. 

```
{
  "routes": [
    {
      "path_prefix": "/",
      "policies": {
        "unauthenticated_action": "RedirectToLoginPage"
      }
    },
    {
      "http_methods": [ "POST" ],
      "path_prefix": "/41C07CED-2E08-4609-9D9F-882468261608/api/agent",
      "policies": {
        "unauthenticated_action": "AllowAnonymous"
      }
    }
  ]
}
```

Die erste Route sichert Ihre App-Domäne effektiv, ähnlich wie **Mit [IdentityProvider] anmelden**. Die zweite Route stellt den AgentLaunch-Endpunkt von SnapshotDebugger außerhalb der Authentifizierung bereit, der die vordefinierte Aktion zum Starten des SnapshotDebugger-Diagnose-Agents *nur dann* ausführt, wenn die vorinstallierte SnapshotDebugger-Siteerweiterung für Ihren App Service aktiviert ist. Weitere Informationen zur Konfiguration von „Authorization.json“ finden Sie unter [URL-Autorisierungsregeln](https://azure.github.io/AppService/2016/11/17/URL-Authorization-Rules.html).

### <a name="403-forbidden"></a>(403) Unzulässig

Dieser Fehler weist darauf hin, dass die Berechtigung verweigert wurde. Dies kann viele verschiedene Ursachen haben.

Führen Sie diese Schritte aus:

* Überprüfen Sie, ob Ihr Visual Studio-Konto über ein gültiges Azure-Abonnement mit den erforderlichen Berechtigungen im Rahmen der rollenbasierten Zugriffssteuerung (Role-Based Access Control, RBAC) für die Ressource verfügt. Überprüfen Sie für App Service, ob Sie berechtigt sind, den App Service-Plan [abzufragen](/rest/api/appservice/appserviceplans/get), der Ihre App hostet.
* Vergewissern Sie sich, dass der Zeitstempel Ihres Clientcomputers korrekt und aktuell ist. Server mit Zeitstempeln, die sich um mehr als 15 Minuten vom Zeitstempel der Anforderung unterscheiden, führen in der Regel zu diesem Fehler.
* Wenn dieser Fehler weiterhin besteht, verwenden Sie einen der Kanäle für Feedback, die zu Beginn dieses Artikels beschrieben wurden.

### <a name="404-not-found"></a>404 Nicht gefunden

Dieser Fehler weist darauf hin, dass die Website auf dem Server nicht gefunden werden konnte.

Führen Sie diese Schritte aus:

* Vergewissern Sie sich, dass Sie eine Website bereitgestellt haben und sie auf der App Service-Ressource ausführen, an die Sie anfügen.
* Überprüfen Sie, ob die Website unter https://\<resource\>.azurewebsites.net verfügbar ist.
* Vergewissern Sie sich, dass Ihre benutzerdefinierte Webanwendung bei ordnungsgemäßer Ausführung keinen 404-Statuscode zurückgibt, wenn auf https://\<resource\>.azurewebsites.net zugegriffen wird.
* Wenn dieser Fehler weiterhin besteht, verwenden Sie einen der Kanäle für Feedback, die zu Beginn dieses Artikels beschrieben wurden.

### <a name="406-not-acceptable"></a>406: Nicht annehmbar

Dieser Fehler weist darauf hin, dass der Server nicht auf den Typ reagieren kann, der im Accept-Header der Anforderung festgelegt wurde.

Führen Sie diese Schritte aus:

* Vergewissern Sie sich, dass Ihre Website unter https://\<resource\>.azurewebsites.net verfügbar ist.
* Vergewissern Sie sich, dass Ihre Website nicht auf neue Instanzen migriert wurde. Der Momentaufnahmedebugger verwendet ARRAffinity für das Weiterleiten von Anforderungen an bestimmte Instanzen, die diesen Fehler zeitweilig verursachen können.
* Wenn dieser Fehler weiterhin besteht, verwenden Sie einen der Kanäle für Feedback, die zu Beginn dieses Artikels beschrieben wurden.

### <a name="409-conflict"></a>Konflikt (409)

Dieser Fehler deutet darauf hin, dass die Anforderung mit dem aktuellen Serverzustand in Konflikt steht.

Hierbei handelt es sich um ein bekanntes Problem, das auftritt, wenn ein Benutzer versucht, den Momentaufnahmedebugger für eine App Service-Instanz anzufügen, für die Application Insights aktiviert ist. Application Insights legt die App-Einstellungen mit einer anderen Schreibweise als Visual Studio fest, was dieses Problem verursacht.

::: moniker range=">= vs-2019"
Dieses Problem wurde in Visual Studio 2019 behoben.
::: moniker-end

Führen Sie diese Schritte aus:

::: moniker range="vs-2017"

* Vergewissern Sie sich im Azure-Portal, dass die App-Einstellungen für den Momentaufnahmedebugger (SNAPSHOTDEBUGGER_EXTENSION_VERSION) und die Instrumentierungs-Engine (INSTRUMENTATIONENGINE_EXTENSION_VERSION) in Großbuchstaben geschrieben sind. Aktualisieren Sie andernfalls die Einstellungen manuell. Dafür wird ein Neustart der Website erzwungen.
::: moniker-end
* Wenn dieser Fehler weiterhin besteht, verwenden Sie einen der Kanäle für Feedback, die zu Beginn dieses Artikels beschrieben wurden.

### <a name="500-internal-server-error"></a>500 – Interner Serverfehler

Dieser Fehler deutet darauf hin, dass die Verfügbarkeit der Website vollständig ausgefallen ist oder der Server die Anforderung nicht verarbeiten kann. Der Momentaufnahmedebugger kann nur für Anwendungen verwendet werden, die ausgeführt werden. Der [Momentaufnahmedebugger von Application Insights](/azure/azure-monitor/app/snapshot-debugger) stellt Funktionen für Momentaufnahmen von Ausnahmen zur Verfügung, und er eignet sich möglicherweise für Ihre Anforderungen am besten.

### <a name="502-bad-gateway"></a>502 – Ungültiges Gateway

Dieser Fehler weist auf ein serverseitiges Netzwerkproblem hin, das möglicherweise nur temporär auftritt.

Führen Sie diese Schritte aus:

* Warten Sie einige Minuten, bevor Sie den Momentaufnahmedebugger neu hinzufügen.
* Wenn dieser Fehler weiterhin besteht, verwenden Sie einen der Kanäle für Feedback, die zu Beginn dieses Artikels beschrieben wurden.

## <a name="issue-snappoint-does-not-turn-on"></a>Problem: Andockpunkt wird nicht aktiviert

Wenn Sie ein Warnsymbol ![Andockpunktwarnsymbol](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "Andockpunktwarnsymbol") anstelle des regulären Andockpunktsymbols bei Ihrem Andockpunkt sehen, dann ist der Andockpunkt nicht aktiviert.

![Andockpunkt wird nicht aktiviert](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "Andockpunkt wird nicht aktiviert")

Führen Sie diese Schritte aus:

1. Stellen Sie sicher, dass Sie über die gleiche Version des Quellcodes verfügen, die zum Erstellen und Bereitstellen Ihrer App verwendet wurde. Stellen Sie sicher, dass Sie die richtigen Symbole für die Bereitstellung laden. Zeigen Sie dazu das **Module**-Fenster beim Debuggen von Momentaufnahmen an, und überprüfen Sie, ob die Symboldatei-Spalte eine PDB-Datei enthält, die für das Modul geladen wird, das Sie debuggen. Der Momentaufnahmedebugger versucht, automatisch Symbole für die Bereitstellung herunterzuladen und zu verwenden.

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>Problem: Symbole werden nicht geladen, wenn ich eine Momentaufnahme öffne

Wenn das folgende Fenster angezeigt wird, wurden die Symbole nicht geladen.

![Symbole werden nicht geladen](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "Symbole werden nicht geladen")

Führen Sie diese Schritte aus:

- Klicken Sie auf den **Symboleinstellungen ändern**- Link auf dieser Seite. Fügen Sie in den **Debuggen > Symbol**-Einstellungen ein Symbolcacheverzeichnis hinzu. Starten Sie das Debuggen von Momentaufnahmen neu, nachdem der Symbolpfad festgelegt wurde.

   Die in Ihrem Projekt verfügbaren Symbole oder PDB-Dateien müssen mit Ihrer App Service-Bereitstellung übereinstimmen. Die meisten Bereitstellungen (Bereitstellung über Visual Studio, CI/CD mit Azure-Pipelines oder Kudu usw.) veröffentlichen Ihre Symboldateien für Ihren App Service. Die Einstellung des Symbolcacheverzeichnisses ermöglicht Visual Studio, diese Symbole zu verwenden.

   ![Symboleinstellungen](../debugger/media/snapshot-troubleshooting-symbol-settings.png "Symboleinstellungen")

- Wenn Ihre Organisation einen Symbolserver verwendet oder Symbole in einem anderen Pfad löscht, verwenden Sie alternativ die Symboleinstellungen, um die richtigen Symbole für die Bereitstellung zu laden.

## <a name="issue-i-cannot-see-the-attach-snapshot-debugger-option-in-the-cloud-explorer"></a>Problem: Die Option „Momentaufnahmedebugger anfügen“ wird im Cloud-Explorer nicht angezeigt

Führen Sie diese Schritte aus:

- Stellen Sie sicher, dass die Momentaufnahmedebugger-Komponente installiert ist. Öffnen Sie den Visual Studio-Installer, und aktivieren Sie die **Momentaufnahmedebugger**-Komponente in der Azure-Workload.
::: moniker range="< vs-2019"
- Stellen Sie sicher, dass Ihre App unterstützt wird. Derzeit werden nur ASP.NET- und ASP.NET Core-Apps (4.6.1+ und 2.0+) unterstützt, die für Azure App Services bereitgestellt werden.
::: moniker-end
::: moniker range=">= vs-2019"
- Stellen Sie sicher, dass Ihre App unterstützt wird:
  - Azure App Services – ASP.NET-Apps, die in .NET Framework 4.6.1 oder höher ausgeführt werden.
  - Azure App Services – ASP.NET Core-Apps, die in .NET Core 2.0 oder höher unter Windows ausgeführt werden.
  - Azure-VMs (und VMSSs) – ASP.NET-Apps, die unter .NET Framework 4.6.1 oder höher ausgeführt werden.
  - Azure-VMs (und VMSSs) – ASP.NET Core-Apps, die in .NET Core 2.0 oder höher unter Windows ausgeführt werden.
  - Azure Kubernetes Services – ASP.NET Core-Apps, die in .NET Core 2.2 oder höher unter Debian 9 ausgeführt werden.
  - Azure Kubernetes Services – ASP.NET Core-Apps, die in .NET Core 2.2 oder höher unter Alpine 3.8 ausgeführt werden.
  - Azure Kubernetes Services – ASP.NET Core-Apps, die in .NET Core 2.2 oder höher unter Ubuntu 18.04 ausgeführt werden.
::: moniker-end

## <a name="issue-i-only-see-throttled-snapshots-in-the-diagnostic-tools"></a>Problem: Ich sehe nur gedrosselte Momentaufnahmen in den Diagnosetools

![Gedrosselter Andockpunkt](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "Gedrosselter Andockpunkt")

Führen Sie diese Schritte aus:

- Momentaufnahmen beanspruchen wenig Arbeitsspeicher, nutzen aber festgelegten virtuellen Speicher. Wenn der Momentaufnahmedebugger eine hohe Arbeitsspeicherauslastung Ihres Servers erkennt, erstellt er keine Momentaufnahmen. Sie können bereits erfasste Momentaufnahmen löschen, indem Sie die Momentaufnahmedebugger-Sitzung beenden und es erneut versuchen.

::: moniker range=">= vs-2019"
## <a name="issue-snapshot-debugging-with-multiple-versions-of-the-visual-studio-gives-me-errors"></a>Problem: Beim Debuggen von Momentaufnahmen mit mehreren Versionen von Visual Studio erhalte ich Fehlermeldungen

Visual Studio 2019 erfordert eine neuere Version dieser Momentaufnahmedebugger-Websiteerweiterung in Ihrer Azure App Service-Instanz.  Diese Version ist nicht kompatibel mit der älteren Version der Momentaufnahmedebugger-Websiteerweiterung, die von Visual Studio 2017 verwendet wird.  Sie erhalten die folgende Fehlermeldung, wenn Sie versuchen, den Momentaufnahmedebugger in Visual Studio 2019 einer Azure App Service-Instanz anzufügen, die zuvor vom Momentaufnahmedebugger in Visual Studio 2017 debuggt wurde:

![Nicht kompatible Momentaufnahmedebugger-Websiteerweiterung in Visual Studio 2019](../debugger/media/snapshot-troubleshooting-incompatible-vs2019.png "Nicht kompatible Momentaufnahmedebugger-Websiteerweiterung in Visual Studio 2019")

Wenn Sie im Gegensatz dazu Visual Studio 2017 verwenden, um den Momentaufnahmedebugger einer Azure App Service-Instanz anzufügen, die zuvor vom Momentaufnahmedebugger in Visual Studio 2019 debuggt wurde, erhalten Sie folgende Fehlermeldung:

![Nicht kompatible Momentaufnahmedebugger-Websiteerweiterung in Visual Studio 2017](../debugger/media/snapshot-troubleshooting-incompatible-vs2017.png "Nicht kompatible Momentaufnahmedebugger-Websiteerweiterung in Visual Studio 2017")

Um dieses Problem zu lösen, löschen Sie die folgenden App-Einstellungen im Azure-Portal, und fügen Sie den Momentaufnahmedebugger erneut an:

- INSTRUMENTATIONENGINE_EXTENSION_VERSION
- SNAPSHOTDEBUGGER_EXTENSION_VERSION
::: moniker-end

## <a name="issue-i-am-having-problems-snapshot-debugging-and-i-need-to-enable-more-logging"></a>Problem: Das Debuggen von Momentaufnahmen bereitet mir Probleme, und ich benötige eine umfassendere Protokollierung

### <a name="enable-agent-logs"></a>Aktivieren von Agent-Protokollen

Zum Aktivieren und Deaktivieren der Agent-Protokollierung öffnen Sie Visual Studio, und navigieren Sie zu *Extras > Optionen > Momentaufnahmedebugger > Agent-Protokollierung aktivieren*. Beachten Sie: Wenn *Alte Agent-Protokolle beim Sitzungsstart löschen* auch aktiviert ist, löscht jedes erfolgreiche Anfügen in Visual Studio vorherige Agent-Protokolle.

Agent-Protokolle können sich an folgenden Speicherorten befinden:

- App Services:
  - Navigieren Sie zur Kudu-Website Ihres App Service (d.h. yourappservice.**scm**.azurewebsites.net), und navigieren Sie zur Debugging-Konsole.
  - Agent-Protokolle werden im folgenden Verzeichnis gespeichert:  D:\home\LogFiles\SiteExtensions\DiagnosticsAgentLogs\.
- VM/VMSS:
  - Melden Sie sich bei Ihrer VM an. Agent-Protokolle werden im folgendem Verzeichnis gespeichert:  C:\WindowsAzure\Logs\Plugins\Microsoft.Azure.Diagnostics.IaaSDiagnostics\<Version>\SnapshotDebuggerAgent_*.txt
- AKS
  - Navigieren Sie zum folgenden Verzeichnis: „/tmp/diag/AgentLogs/*“

### <a name="enable-profilerinstrumentation-logs"></a>Aktivieren von Profiler/Instrumentierungsprotokollen

Instrumentierungsprotokolle finden Sie an den folgenden Speicherorten:

- App Services:
  - Die Fehlerprotokollierung wird automatisch an „D:\Home\LogFiles\eventlog.xml“ gesendet. Ereignisse werden mit `<Provider Name="Instrumentation Engine" />` oder „Production Breakpoints“ (Produktionshaltepunkte) gekennzeichnet.
- VM/VMSS:
  - Melden Sie sich bei Ihrem virtuellen Computer an, und öffnen Sie die Ereignisanzeige.
  - Öffnen Sie die folgende Ansicht: *Windows-Protokolle > Anwendung*.
  - *Aktuelles Protokoll filtern* nach *Ereignisquelle* mit entweder *Produktionshaltepunkten* oder *Instrumentation-Engine*.
- AKS
  - Instrumentation-Engine-Protokollierung unter „/tmp/diag/log.txt“ (legen Sie MicrosoftInstrumentationEngine_FileLogPath in DockerFile-Datei fest)
  - Produktionshaltepunkt-Protokollierung unter „/tmp/diag/shLog.txt“

## <a name="known-issues"></a>Bekannte Probleme

- Debuggen von Momentaufnahmen mit mehreren Visual Studio-Clients für den gleichen App Service wird derzeit nicht unterstützt.
- Roslyn IL-Optimierungen werden in ASP.NET Core-Projekten nicht vollständig unterstützt. Für einige ASP.NET Core-Projekte ist es möglicherweise nicht möglich, einige Variablen anzuzeigen oder einige Variablen in bedingten Anweisungen zu verwenden.
- Bestimmte Variablen, wie z.B. *$FUNCTION* oder *$CALLER*, können in bedingten Anweisungen oder Protokollpunkten für ASP.NET Core-Projekte nicht ausgewertet werden.
- Debuggen von Momentaufnahmen funktioniert nicht in App Services, für die [Lokale Zwischenspeicherung](/azure/app-service/app-service-local-cache) aktiviert ist.
- Debuggen von Momentaufnahmen von API-Apps wird derzeit nicht unterstützt.

## <a name="site-extension-upgrade"></a>Websiteerweiterungsupgrade

Debuggen von Momentaufnahmen und Application Insights hängen von einem ICorProfiler ab, der in den Websiteprozess geladen wird und Probleme durch Sperren von Dateien während des Upgrades verursacht. Wir empfehlen diesen Prozess, um sicherzustellen, dass keine Downtime auf Ihrer Produktionswebsite auftritt.

- Erstellen Sie einen [Bereitstellungsslot](/azure/app-service/web-sites-staged-publishing) in Ihrem App Service, und stellen Sie Ihre Website für den Slot bereit.
- Tauschen Sie den Slot vom Cloud-Explorer in Visual Studio aus oder über das Azure-Portal mit der Produktion aus.
- Beenden Sie die Slot-Website. Es dauert ein paar Sekunden, den w3wp.exe-Prozess der Website in allen Instanzen zu beenden.
- Upgraden Sie die Slot-Websiteerweiterung von der Kudu-Website aus oder über das Azure-Portal (*App Service-Blatt > Entwicklungstools > Erweiterungen > Update*).
- Starten Sie die Slot-Website. Sie sollten die Website besuchen, um sie wieder zu aktivieren.
- Tauschen Sie den Slot mit der Produktion aus.

## <a name="see-also"></a>Siehe auch

- [Debuggen in Visual Studio](../debugger/index.yml)
- [Debuggen von aktiven ASP.NET Azure-Apps mit dem Momentaufnahmedebugger](../debugger/debug-live-azure-applications.md)
- [Debuggen von aktiven ASP.NET-Apps auf Azure-VMs und Azure-VMSS mit dem Momentaufnahmedebugger](../debugger/debug-live-azure-virtual-machines.md)
- [Debuggen von aktiven ASP.NET Azure Kubernetes Services mit dem Momentaufnahmedebugger](../debugger/debug-live-azure-kubernetes.md)
- [Häufig gestellte Fragen zum Debuggen von Momentaufnahmen](../debugger/debug-live-azure-apps-faq.md)
