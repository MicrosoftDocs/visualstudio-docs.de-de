---
title: Verwenden von Microsoft Monitoring Agent | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie Microsoft Monitoring Agent verwenden, um ASP.NET-Web-Apps und SharePoint 2010- oder SharePoint 2013-Anwendungen auf Fehler, Leistungsprobleme und andere Probleme zu überwachen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fd0a86b9-015d-408e-aa58-59a0a97826ac
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 16c0655cdd55a1825f0a872ef013392bc9e5db79
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150105"
---
# <a name="using-the-microsoft-monitoring-agent-c-visual-basic"></a>Verwenden von Microsoft Monitoring Agent (C#, Visual Basic)

Sie können von IIS gehostete ASP.NET-Webanwendungen sowie SharePoint 2010- oder 2013-Anwendungen lokal auf Fehler, Leistungsprobleme und andere Probleme überwachen, indem Sie **Microsoft Monitoring Agent** verwenden. Sie können Diagnoseereignisse vom Agent in einer IntelliTrace-Protokoll-(.iTrace)-Datei speichern. Sie können dann das Protokoll in Visual Studio Enterprise (jedoch nicht in den Versionen Professional oder Community) öffnen, um Probleme mit allen Visual Studio-Diagnosetools zu debuggen. Sie können auch IntelliTrace-Diagnosedaten und Methodendaten erfassen, indem Sie den Agenten im **Ablaufverfolgungs** modus ausführen. Microsoft Monitoring Agent kann mit [Application Insights](/azure/application-insights/) und [System Center Operation Manager](/previous-versions/system-center/system-center-2012-R2/hh205987(v=sc.12))integriert werden. Durch die Installation von Microsoft Monitoring Agent ändert sich nicht die Zielsystemumgebung.

> [!NOTE]
> Sie können mithilfe des **eigenständigen IntelliTrace Collector** auch IntelliTrace-Diagnose- und Methodendaten für Web-, SharePoint-, WPF- und Windows-Formularanwendungen auf Remotecomputern sammeln, ohne die Zielumgebung zu ändern. Der eigenständige Collector hat größere Auswirkungen auf die Leistung als die Ausführung von Microsoft Monitoring Agent im **Überwachungs** modus. Weitere Informationen finden Sie unter [Verwenden des eigenständigen IntelliTrace-Collectors](../debugger/using-the-intellitrace-stand-alone-collector.md).

 Wenn Sie System Center 2012 verwenden, verwenden Sie Microsoft Monitoring Agent mit Operations Manager, um Warnungen zu Problemen abzurufen und Team Foundation Server-Arbeitselemente mit Links zu gespeicherten IntelliTrace-Protokollen zu erstellen. Sie können dann diese Arbeitselemente anderen zum weiteren Debuggen zuweisen. Weitere Informationen finden Sie unter [Integration von Operations Manager in Entwicklungsprozesse](/previous-versions/system-center/system-center-2012-R2/jj614609(v=sc.12)) und [Überwachen mit Microsoft Monitoring Agent](/previous-versions/system-center/system-center-2012-R2/dn465153(v=sc.12)).

 Bevor Sie beginnen, überprüfen Sie, ob Sie die entsprechende Quelle und die Symbole für den erstellten und bereitgestellten Code haben. Dies hilft Ihnen dabei, direkt auf den Anwendungscode zuzugreifen, wenn Sie das Debuggen starten und das IntelliTrace-Protokoll nach Diagnoseereignissen durchsuchen. [Installieren Sie die Builds](../debugger/diagnose-problems-after-deployment.md) , sodass Visual Studio die entsprechende Quelle für den bereitgestellten Code automatisch suchen und öffnen kann.

1. [Schritt 1: Microsoft Monitoring Agent installieren](#SetUpMonitoring)

2. [Schritt 2: Die Überwachung Ihrer App starten](#MonitorEvents)

3. [Schritt 3: Speichern von aufgezeichneten Ereignissen](#SaveEvents)

## <a name="step-1-set-up-microsoft-monitoring-agent"></a><a name="SetUpMonitoring"></a> Schritt 1: Microsoft Monitoring Agent installieren

 Installieren Sie den eigenständigen Agent auf dem Webserver, um eine lokale Überwachung auszuführen, ohne Ihre Anwendung zu ändern. Wenn Sie System Center 2012 verwenden, erhalten Sie weitere Informationen unter [Microsoft Monitoring Agent installieren](/previous-versions/system-center/system-center-2012-R2/dn465156(v=sc.12)).

### <a name="set-up-the-standalone-agent"></a><a name="SetUpStandaloneMMA"></a> Installieren Sie den eigenständigen Agent.

1. Stellen Sie Folgendes sicher:

    - Auf Ihrem Webserver werden [unterstützte Versionen von Internet Information Services (IIS)](/previous-versions/system-center/system-center-2012-R2/dn465154(v=sc.12))ausgeführt.

    - Ihr Webserver verfügt über .NET Framework 3.5, 4 oder 4.5.

    - Auf Ihrem Webserver wird Windows PowerShell 3.0 oder höher ausgeführt. [Frage: Was geschieht, wenn ich Windows PowerShell 2.0 verwende?](#PowerShell2)

    - Sie verfügen über Administratorberechtigungen auf dem Webserver, um PowerShell-Befehle auszuführen und den Anwendungspool wiederzuverwenden, wenn Sie die Überwachung starten.

    - Sie haben alle vorherigen Versionen von Microsoft Monitoring Agent deinstalliert.

2. [Laden Sie den kostenlosen Microsoft Monitoring Agent](https://www.microsoft.com/download/details.aspx?id=40316)(entweder die 32-Bit-Version **MMASetup-i386.exe** oder die 64-Bit-Version **MMASetup-AMD64.exe**) vom Microsoft Download Center auf Ihren Webserver herunter.

3. Führen Sie die heruntergeladene ausführbare Datei aus, um den Installations-Assistenten zu starten.

4. Erstellen Sie ein sicheres Verzeichnis auf Ihrem Webserver, um die IntelliTrace-Protokolle zu speichern, beispielsweise **C:\IntelliTraceLogs**.

     Achten Sie darauf, dass Sie dieses Verzeichnis erstellen, bevor Sie die Überwachung starten. Um eine Verlangsamung der App zu vermeiden, wählen Sie einen Speicherort auf einem lokalen Hochgeschwindigkeitsdatenträger, der nicht sehr aktiv ist.

    > [!IMPORTANT]
    > IntelliTrace-Protokolle enthalten möglicherweise persönliche und vertrauliche Daten. Beschränken Sie den Zugriff auf dieses Verzeichnis auf die Identitäten, die die Dateien für die Arbeit benötigen. Überprüfen Sie Datenschutzrichtlinien des Unternehmens.

5. Um eine ausführliche Funktionsebenenüberwachung auszuführen oder um SharePoint-Anwendungen zu überwachen, erteilen Sie dem Anwendungspool, der Ihre Web App oder SharePoint-Anwendung hostet, Lese- und Schreibberechtigungen für das IntelliTrace-Protokollverzeichnis. [Frage: Wie richte ich Berechtigungen für den Anwendungspool ein?](#FullPermissionsITLog)

### <a name="q--a"></a>Fragen und Antworten

#### <a name="q-what-if-i-have-windows-powershell-20"></a><a name="PowerShell2"></a> Frage: Was geschieht, wenn ich Windows PowerShell 2.0 verwende?
 **Antwort:** Wir empfehlen dringend, PowerShell 3.0 zu verwenden. Andernfalls müssen Sie jedes Mal, wenn Sie PowerShell ausführen, die Microsoft Monitoring Agent-PowerShell-Cmdlets importieren. Sie haben auch keinen Zugriff auf den Hilfeinhalt zum Herunterladen.

1. Öffnen Sie ein **Windows PowerShell** - oder **Windows PowerShell ISE** -Eingabeaufforderungsfenster als Administrator.

2. Importieren Sie das PowerShell-Modul für Microsoft Monitoring Agent über den Standardinstallationspfad:

     **PS C:>Import-Module "C:\Programme\Microsoft Monitoring Agent\Agent\PowerShell\Microsoft.MonitoringAgent.PowerShell\Microsoft.MonitoringAgent.PowerShell.dll"**

3. Um die neuesten Hilfeinhalte abzurufen,[besuchen Sie TechNet](/previous-versions/system-center/developer/cc817313(v=msdn.10)) .

#### <a name="q-how-do-i-set-up-permissions-for-the-application-pool"></a><a name="FullPermissionsITLog"></a> Frage: Wie richte ich Berechtigungen für den Anwendungspool ein?
 **Antwort:** Verwenden Sie den Windows-Befehl **icacls** oder den Windows-Explorer (bzw. den Datei-Explorer). Zum Beispiel:

- So legen Sie Berechtigungen mit dem Windows-Befehl **icacls** fest:

  - Für eine Web App im **DefaultAppPool** -Anwendungspool:

     `icacls "C:\IntelliTraceLogs" /grant "IIS APPPOOL\DefaultAppPool":RX`

  - Für eine SharePoint-Anwendung im **SharePoint - 80** -Anwendungspool:

     `icacls "C:\IntelliTraceLogs" /grant "IIS APPPOOL\SharePoint - 80":RX`

    - oder -

- So legen Sie die Berechtigungen mit dem Windows-Explorer (bzw. dem Datei-Explorer) fest:

  1. Öffnen Sie die **Eigenschaften** für das IntelliTrace-Protokollverzeichnis.

  2. Wählen Sie auf der Registerkarte **Sicherheit** die Option **Bearbeiten**, **Hinzufügen** aus.

  3. Stellen Sie sicher, dass im Feld **Diesen Objekttyp auswählen** die Option **Integrierte Sicherheitsprinzipale** angezeigt wird. Wenn sie nicht vorhanden ist, wählen Sie **Objekttypen**, um sie hinzuzufügen.

  4. Versichern Sie sich, dass der lokale Computer im Feld **Aus diesem Speicherort** angezeigt wird. Wenn er nicht vorhanden ist, wählen Sie **Speicherorte** aus, um es zu ändern.

  5. Fügen Sie im Feld **Geben Sie die Namen der auszuwählenden Objekte ein** den Anwendungspool für die Web App oder die SharePoint-Anwendung hinzu.

  6. Wählen Sie **Namen überprüfen** aus, um den Namen aufzulösen. Klicken Sie auf **OK**.

  7. Stellen Sie sicher, dass der Anwendungspool über Berechtigungen zum **Lesen und Ausführen** verfügt.

## <a name="step-2-start-monitoring-your-app"></a><a name="MonitorEvents"></a> Schritt 2: Die Überwachung Ihrer App starten
 Verwenden Sie den Windows PowerShell-Befehl [Start-WebApplicationMonitoring](/previous-versions/system-center/powershell/system-center-2012-r2/dn472749(v=sc.20)) , um die Überwachung der App zu starten. Wenn Sie System Center 2012 verwenden, erhalten Sie weitere Informationen unter [Überwachung von Webanwendungen mit Microsoft Monitoring Agent](/previous-versions/system-center/system-center-2012-R2/dn465157(v=sc.12)).

1. Öffnen Sie auf dem Webserver ein **Windows PowerShell** - oder **Windows PowerShell ISE** -Eingabeaufforderungsfenster als Administrator.

     ![Öffnen Sie Windows PowerShell als Administrator](../debugger/media/ffr_powershellrunadmin.png "FFR_PowerShellRunAdmin").

2. Führen Sie den Befehl [Start-WebApplicationMonitoring](/previous-versions/system-center/powershell/system-center-2012-r2/dn472749(v=sc.20)) aus, um die Überwachung Ihrer App zu starten. Dies startet alle Web Apps auf Ihrem Webserver neu.

     Hier ist die kurze Syntax:

     **Start-WebApplicationMonitoring** *"\<appName>"* *\<monitoringMode>* *"\<outputPath>"* *\<UInt32>* *"\<collectionPlanPathAndFileName>"*

     Im Folgenden ein Beispiel, bei dem nur der Web App-Name und der Lightweight- **Monitor** -Modus verwendet wird:

     **PS C:>Start-WebApplicationMonitoring "FabrikamFabrikamFiber.Web" Monitor "C:IntelliTraceLogs"**

     Im Folgenden ein Beispiel, bei dem der IIS-Pfad- und der Lightweight- **Monitor** -Modus verwendet wird:

     **PS C:>Start-WebApplicationMonitoring "IIS:sitesFabrikamFabrikamFiber.Web" Monitor "C:IntelliTraceLogs"**

     Nachdem Sie die Überwachung gestartet haben, wird Microsoft Monitoring Agent während des Neustarts der Apps möglicherweise angehalten.

     ![Starten der Überwachung mit MMA-Bestätigung](../debugger/media/ffr_powershellstartmonitoringconfirmation.png "FFR_PowerShellStartMonitoringConfirmation")

    |name|Beschreibung|
    |-|-|
    |*"\<appName>"*|Geben Sie den Pfad zur Website und dem Namen der Web App in IIS an. Sie können auch den IIS-Pfad einschließen, falls gewünscht.<br /><br /> *"\<IISWebsiteName>\\<IISWebAppName\>"*<br /><br /> - oder -<br /><br /> **"IIS:\sites** *\\<IISWebsiteName\>\\<IISWebAppName\>"*<br /><br /> Sie können diesen Pfad im IIS-Manager finden. Zum Beispiel:<br /><br /> ![Pfad zur IIS-Website und -Webanwendung](../debugger/media/ffr_iismanager.png "FFR_IISManager")<br /><br /> Sie können auch die Befehle [Get-WebSite](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee807832(v=technet.10)) und [Get WebApplication](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee790554(v=technet.10)) verwenden.|
    |*\<monitoringMode>*|Legen Sie den Überwachungsmodus fest:<br /><br /> <ul><li>**Überwachen**: Zeichnen Sie minimale Details über Ausnahmeereignisse und Leistungsereignisse auf. Dieser Modus verwendet den Standardauflistungsplan.</li><li>**Ablaufverfolgung**: Zeichnen Sie Funktionsebenendetails auf, oder überwachen Sie SharePoint 2010- und SharePoint 2013-Anwendungen mithilfe des angegebenen Auflistungsplans. Durch diesen Modus wird Ihre App möglicherweise langsamer ausgeführt.<br /><br /> <ul><li>[Frage: Wie richte ich Berechtigungen für den Anwendungspool ein?](#FullPermissionsITLog)</li><li>[Frage: Wie rufe ich die möglichst viele Daten ab, ohne die App zu verlangsamen?](#Minimizing)</li></ul><br />     Dieses Beispiel zeichnet Ereignisse für eine SharePoint-App auf, die auf einer SharePoint-Website gehostet wird:<br /><br />     **Start-WebApplicationMonitoring "FabrikamSharePointSite\FabrikamSharePointApp" Trace "C:\Programme\Microsoft Monitoring Agent\Agent\IntelliTraceCollector\collection_plan.ASP.NET.default.xml" "C:\IntelliTraceLogs"**</li><li>**Benutzerdefiniert**: Zeichnen Sie benutzerdefinierte Details mithilfe des angegebenen benutzerdefinierten Auflistungsplans auf. Sie müssen die Überwachung neu starten, wenn Sie den Auflistungsplan bearbeiten, nachdem die Überwachung bereits gestartet wurde.</li></ul>|
    |*"\<outputPath>"*|Geben Sie den vollständigen Verzeichnispfad zum Speichern der IntelliTrace-Protokolle an. Achten Sie darauf, dass Sie dieses Verzeichnis erstellen, bevor Sie die Überwachung starten.|
    |*\<UInt32>*|Geben Sie die maximale Größe für das IntelliTrace-Protokoll an. Die standardmäßige maximale Größe der IntelliTrace-Datei beträgt 250 MB.<br /><br /> Wenn das Protokoll diese Grenze erreicht, überschreibt der Agent die frühesten Einträge, um Platz für mehr Einträge zu schaffen. Um diese Beschränkung zu ändern, verwenden Sie die Option **-MaximumFileSizeInMegabytes** oder bearbeiten Sie das `MaximumLogFileSize` -Attribut im Auflistungsplan.|
    |*"\<collectionPlanPathAndFileName>"*|Geben Sie den vollständigen Pfad oder den relativen Pfad und den Dateiname des Auflistungsplans an. Dieser Plan ist eine XML-Datei, die Einstellungen für den Agent konfiguriert.<br /><br /> Diese Pläne werden mit dem Agent eingeschlossen und funktionieren mit Web Apps und SharePoint-Anwendungen:<br /><br /> -   **collection_plan.ASP.NET.default.xml**<br />     Sammelt nur Ereignisse, wie z. B. Ausnahmen, Leistungsereignisse, Datenbankaufrufe und Webserveranforderungen.<br />-   **collection_plan.ASP.NET.trace.xml**<br />     Sammelt Funktionsebenenaufrufe sowie alle Daten im Standardauflistungsplan. Dieser Plan ist gut für eine ausführliche Analyse. Er verlangsamt jedoch möglicherweise die App.<br /><br /> Sie können lokalisierte Versionen dieser Pläne in Unterordnern des Agents finden. Um eine Verlangsamung der App zu vermeiden, können Sie auch [diese Pläne anpassen oder Ihre eigenen Pläne erstellen](https://devblogs.microsoft.com/devops/modifying-an-intellitrace-collection-plan-for-the-stand-alone-collector/) . Legen Sie alle benutzerdefinierten Pläne am gleichen sicheren Speicherort ab wie den Agenten.<br /><br /> [Frage: Wie rufe ich die möglichst viele Daten ab, ohne die App zu verlangsamen?](#Minimizing)|

     Für weitere Informationen über die vollständige Syntax und andere Beispiele, führen Sie den Befehl **get-help Start-WebApplicationMonitoring -detailed** oder den Befehl **get-help Start-WebApplicationMonitoring -examples** aus.

3. Um den Status aller überwachten Web Apps zu überprüfen, führen Sie den Befehl [GET-WebApplicationMonitoringStatus](/previous-versions/system-center/powershell/system-center-2012-r2/dn472751(v=sc.20)) aus.

### <a name="q--a"></a>Fragen und Antworten

#### <a name="q-how-do-i-get-the-most-data-without-slowing-down-my-app"></a><a name="Minimizing"></a> Frage: Wie rufe ich die möglichst viele Daten ab, ohne die App zu verlangsamen?
 **Antwort:** Microsoft Monitoring Agent kann viele Daten sammeln und wirkt sich auf die Leistung der App aus, abhängig von den Daten, die Sie sammeln möchten und wie sie diese sammeln. Es gibt folgende Möglichkeiten, möglichst viele Daten abzurufen, ohne die App zu verlangsamen:

- Für Web Apps und für SharePoint-Anwendungen zeichnet der Agent Daten für alle Anwendungen auf, die den angegebenen Anwendungspool gemeinsam verwenden. Dies verlangsamt möglicherweise die Leistung jeder App, die den gleichen Anwendungspool verwendet, obwohl Sie die Sammlung auf die Module für eine einzelne App beschränken können. Um zu verhindern, dass andere Apps verlangsamt werden, hosten Sie jede App in ihrem eigenen Anwendungspool.

- Überprüfen Sie die Ereignisse, für die der Agent Daten im Sammlungsplan sammelt. Bearbeiten Sie den Sammlungsplan, um nicht relevante Ereignisse zu deaktivieren. Dies kann die Startleistung und Laufzeitleistung verbessern.

   Um ein Ereignis zu deaktivieren, legen Sie das `enabled` -Attribut für das `<DiagnosticEventSpecification>` -Element auf `false`fest:

   `<DiagnosticEventSpecification enabled="false">`

   Wenn das `enabled` -Attribut nicht vorhanden ist, wird das Ereignis aktiviert.

   Zum Beispiel:

  - Deaktivieren Sie Windows Workflow-Ereignisse für Apps, die Windows Workflow nicht verwenden.

  - Deaktivieren Sie Registrierungsereignisse für Apps, die auf die Registrierung zugreifen, jedoch keine Probleme mit den Registrierungseinstellungen haben.

- Überprüfen Sie die Module, für die der Agent Daten im Sammlungsplan sammelt. Bearbeiten Sie den Sammlungsplan, um nur für Sie interessante Module einzuschließen.

   Dadurch wird die Menge der Methodenaufrufinformationen und anderer Instrumentationsdaten reduziert, die der Agent sammelt, wenn die Anwendung gestartet und ausgeführt wird. Diese Daten ermöglichen es Ihnen, den Code schrittweise durchzugehen, wenn Sie debuggen und Werte überprüfen, die an Funktionsaufrufe übergeben werden und von ihnen zurückgegeben werden.

  1. Öffnen Sie den Sammlungsplan. Suchen Sie das `<ModuleList>` -Element.

  2. Legen Sie in `<ModuleList>`das `isExclusionList` -Attribut auf `false`fest.

  3. Verwenden Sie das `<Name>` -Element, um jedes Modul mit einer der folgenden Informationen anzugeben: Dateiname, Zeichenfolgenwert, um jedes Modul einzuschließen, das diese Zeichenfolge enthält, oder öffentlicher Schlüssel.

     Dieses Beispiel erstellt eine Liste, die Daten nur vom Hauptmodul der "Fabrikam Fiber"-Web App sammelt:

  ```xml
  <ModuleList isExclusionList="false">
     <Name>FabrikamFiber.Web.dll</Name>
  </ModuleList>

  ```

   Um Daten aus jedem Modul zu sammeln, dessen Name "Fabrikam" enthält, erstellen Sie eine Liste wie diese:

  ```xml
  <ModuleList isExclusionList="false">
     <Name>Fabrikam</Name>
  </ModuleList>

  ```

   Um Daten aus Modulen zu sammeln, indem Sie deren öffentliche Schlüsseltoken angeben, erstellen Sie eine Liste wie diese:

  ```xml
  <ModuleList isExclusionList="false">
     <Name>PublicKeyToken:B77A5C561934E089</Name>
     <Name>PublicKeyToken:B03F5F7F11D50A3A</Name>
     <Name>PublicKeyToken:31BF3856AD364E35</Name>
     <Name>PublicKeyToken:89845DCD8080CC91</Name>
     <Name>PublicKeyToken:71E9BCE111E9429C</Name>
  </ModuleList>

  ```

   **Frage: Warum sollten Module stattdessen nicht einfach ausgeschlossen werden?**

   **Antwort:** Standardmäßig schließen Sammlungspläne Module aus, indem das `isExclusionList` -Attribut auf `true`festgelegt wird. Dieses kann jedoch möglicherweise immer noch Daten aus Modulen sammeln, die die Kriterien in der Liste nicht erfüllen oder für Sie nicht relevant sind, wie etwa Module von Drittanbietern oder Open Source-Module.

#### <a name="q-what-values-does-the-agent-collect"></a>Frage: Welche Werte sammelt der Agent?

**Antwort:** Um die Auswirkungen auf die Leistung zu reduzieren, sammelt der Agent nur diese Werte:

- Primitive Datentypen, die an Methoden übergeben und von ihnen zurückgegeben werden

- Primitive Datentypen in Feldern für Objekte auf oberster Ebene, die an Methoden übergeben und von ihnen zurückgegeben werden

Angenommen, Sie verfügen über eine `AlterEmployee` -Methodensignatur, die eine Ganzzahl- `id` und ein `Employee` -Objekt `oldemployee`akzeptiert:

`public Employee AlterEmployee(int id, Employee oldemployee)`

Der `Employee` -Typ verfügt über die folgenden Attribute: `Id`, `Name`und `HomeAddress`. Eine Zuordnungsbeziehung besteht zwischen dem `Employee` - und dem `Address` -Typ.

![Beziehung zwischen Mitarbeiter und Adresse](../debugger/media/employeeaddressrelationship.png "EmployeeAddressRelationship")

Der Agent zeichnet Werte für `id`, `Employee.Id`, `Employee.Name` und das `Employee` -Objekt auf, das von der `AlterEmployee` -Methode zurückgegeben wird. Der Agent zeichnet jedoch keine Informationen zum `Address` -Objekt (außer NULL oder keine) auf. Der Agent zeichnet auch keine Daten zu lokalen Variablen in der `AlterEmployee` -Methode auf, es sei denn, andere Methoden verwenden diese lokalen Variablen als Parameter. An diesem Punkt werden sie als Methodenparameter aufgezeichnet.

## <a name="step-3-save-recorded-events"></a><a name="SaveEvents"></a>Schritt 3: Speichern von aufgezeichneten Ereignissen
 Wenn Sie einen Fehler oder ein Leistungsproblem finden, speichern Sie die aufgezeichneten Ereignisse in einem IntelliTrace-Protokoll. Der Agent erstellt das Protokoll nur, wenn Ereignisse aufgezeichnet wurden. Wenn Sie System Center 2012 verwenden, erhalten Sie weitere Informationen unter [Überwachung von Webanwendungen mit Microsoft Monitoring Agent](/previous-versions/system-center/system-center-2012-R2/dn465157(v=sc.12)).

### <a name="save-recorded-events-but-continue-monitoring"></a>Speichern Sie aufgezeichnete Ereignisse, aber setzen Sie die Überwachung fort.
 Befolgen Sie diese Schritte, wenn Sie das IntelliTrace-Protokoll erstellen möchten, aber nicht möchten, dass die App neu startet oder die Überwachung beendet wird. Der Agent setzt die Überwachung auch dann fort, wenn der Server oder die Anwendung neu gestartet wird.

1. Öffnen Sie auf dem Webserver ein Windows PowerShell-Eingabeaufforderungsfenster als Administrator.

2. Führen Sie den Befehl [Checkpoint-WebApplicationMonitoring](/previous-versions/system-center/powershell/system-center-2012-r2/dn472750(v=sc.20)) aus, um eine Momentaufnahme des IntelliTrace-Protokolls zu speichern:

    **Checkpoint-WebApplicationMonitoring** *"\<IISWebsiteName>\\<IISWebAppName\>"*

    \- oder -

    **Checkpoint-WebApplicationMonitoring "IIS:\sites** *\\<IISWebsiteName\>\\<IISWebAppName\>"*

    Zum Beispiel:

    **PS C:\\>Checkpoint-WebApplicationMonitoring "Fabrikam\FabrikamFiber.Web"**

    - oder -

    **PS C:>Checkpoint-WebApplicationMonitoring "IIS:sitesFabrikamFabrikamFiber.Web"**

    Für weitere Informationen führen Sie den Befehl **get-help Checkpoint-WebApplicationMonitoring -detailed** oder den Befehl **get-help Checkpoint-WebApplicationMonitoring -examples** aus.

3. Kopieren Sie das Protokoll in einen sicheren Ordner, und öffnen Sie das Protokoll auf einem Computer, auf dem Visual Studio Enterprise (nicht Professional oder Community) installiert ist.

   > [!IMPORTANT]
   > Seien Sie vorsichtig, wenn Sie IntelliTrace-Protokolle freigeben, da diese eventuell persönliche und vertrauliche Daten enthalten. Stellen Sie sicher, dass Personen mit Zugriff auf diese Protokolle auch die Berechtigungen zu deren Anzeige haben. Überprüfen Sie Datenschutzrichtlinien des Unternehmens.

   **Weiter:** [Diagnose von aufgezeichneten Ereignissen in Visual Studio Enterprise](../debugger/diagnose-problems-after-deployment.md#InvestigateEvents)

### <a name="save-recorded-events-and-stop-monitoring"></a>Speichern von aufgezeichneten Ereignissen und Beenden der Überwachung
 Führen Sie folgende Schritte aus, wenn das Abrufen von Diagnoseinformationen nur beim Reproduzieren eines bestimmten Problems erwünscht ist. Dies startet alle Web Apps auf Ihrem Webserver neu.

1. Öffnen Sie auf dem Webserver ein Windows PowerShell-Eingabeaufforderungsfenster als Administrator.

2. Führen Sie den Befehl [Stop-WebApplicationMonitoring](/previous-versions/system-center/powershell/system-center-2012-r2/dn472753(v=sc.20)) aus, um das IntelliTrace-Protokoll zu erstellen und die Überwachung einer bestimmten Webanwendung zu beenden:

    **Stop-WebApplicationMonitoring** *"\<IISWebsiteName>\\<IISWebAppName\>"*

    \- oder -

    **Stop-WebApplicationMonitoring "IIS:\sites** *\\<IISWebsiteName\>\\<IISWebAppName\>"*

    Oder, um die Überwachung aller Web-Apps zu beenden:

    **Stop-WebApplicationMonitoring -All**

    Zum Beispiel:

    **PS C:\\>Stop-WebApplicationMonitoring "Fabrikam\iFabrikamFiber.Web"**

    \- oder -

    **PS C:\\>Stop-WebApplicationMonitoring "IIS:\sites\Fabrikam\FabrikamFiber.Web"**

    Für weitere Informationen führen Sie den Befehl **get-help Stop-WebApplicationMonitoring -detailed** oder den Befehl **get-help Stop-WebApplicationMonitoring -examples** aus.

3. Kopieren Sie das Protokoll in einen sicheren Ordner, und öffnen Sie das Protokoll auf einem Computer, auf dem Visual Studio Enterprise installiert ist.

   **Weiter:** [Diagnose von aufgezeichneten Ereignissen in Visual Studio Enterprise](../debugger/diagnose-problems-after-deployment.md#InvestigateEvents)

## <a name="q--a"></a>Fragen und Antworten

### <a name="q-where-can-i-get-more-information"></a>Frage: Wo kann ich weitere Informationen abrufen?

#### <a name="blogs"></a>Blogs
 [Einführung in Microsoft Monitoring Agent](https://devblogs.microsoft.com/devops/introducing-microsoft-monitoring-agent/)

 [Optimieren der IntelliTrace-Auflistung auf Produktionsservern](https://devblogs.microsoft.com/devops/optimizing-intellitrace-collection-on-production-server/)

#### <a name="forums"></a>Foren
 [Visual Studio-Diagnose](https://social.msdn.microsoft.com/Forums/en-US/home)