---
title: Das Debuggen kann auf dem Webserver nicht gestartet werden | Microsoft-Dokumentation
ms.date: 05/23/2018
ms.topic: error-reference
f1_keywords:
- vs.debug.error.http
- vwd.nonadmin.error.
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- IIS, debugging DLLs
- debugger, Web application errors
- unable to start debugging error
- security [debugger], Web applications
- debugging [Visual Studio], errors
- HTTP servers, debugging error
- security settings, checking for default Web sites
- errors [debugger], unable to start debugging
- debugging ASP.NET Web applications, unable to start debugging error
- remote debugging, errors
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 94dcfdc05f2d852e1a433067b0a574444632195d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870882"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>Fehler: Das Debuggen kann auf dem Webserver nicht gestartet werden

Beim Versuch, eine ASP.NET-Anwendung zu debuggen, die auf einem Webserver ausgeführt wird, kann eventuell die folgende Fehlermeldung angezeigt werden: `Unable to start debugging on the Web server`.

Oft tritt dieser Fehler auf, da ein Fehler zurückgegeben oder eine Konfigurationsänderung durchgeführt wurde, die ein Update für Ihre Anwendungspools, eine IIS-Zurücksetzung oder beides erfordert. Sie können die IIS zurücksetzen, indem Sie eine Eingabeaufforderung mit erhöhten Rechten öffnen und `iisreset` eingeben.

## <a name="what-is-the-detailed-error-message"></a><a name="specificerrors"></a>Was lautet die ausführliche Fehlermeldung?

Die Meldung `Unable to start debugging on the Web server` ist generisch. In der Regel ist in der Fehlerzeichenfolge eine genauere Meldung enthalten, die Ihnen helfen kann, die Ursache des Problems zu identifizieren oder nach einer genaueren Lösung zu suchen. Im folgenden finden Sie einige der häufigsten Fehlermeldungen, die an die Hauptfehlermeldung angefügt werden:

- [Die IIS führen eine Website nicht auf, die der Start-URL entspricht](#IISlist)
- [Der Webserver ist nicht richtig konfiguriert](#web_server_config)
- [Die Verbindung mit dem Webserver konnte nicht hergestellt werden](#unabletoconnect)
- [Der Webserver hat nicht rechtzeitig reagiert](#webservertimeout)
- [Der Microsoft Visual Studio-Remotedebugmonitor (msvsmon.exe) wird auf dem Remotecomputer nicht ausgeführt](#msvsmon)
- [Der Remoteserver hat einen Fehler zurückgegeben](#server_error)
- [Das ASP.NET-Debuggen konnte nicht gestartet werden](#aspnet)
- [Der Debugger kann keine Verbindung zum Remotecomputer herstellen](#cannot_connect)
- [In der Hilfe sind häufige Konfigurationsfehler erläutert. Möglicherweise erhalten Sie weitere Informationen, wenn Sie die Webseite außerhalb des Debuggers ausführen.](#see_help)
- [Vorgang wird nicht unterstützt. Unbekannter Fehler: *Fehlernummer*](#operation_not_supported)

## <a name="iis-does-not-list-a-website-that-matches-the-launch-url"></a><a name="IISlist"></a>Die IIS führen eine Website nicht auf, die der Start-URL entspricht

- Starten Sie Visual Studio neu als Administrator, und versuchen Sie, das Debuggen zu wiederholen. (Für manche ASP.NET-Debugszenarios sind erhöhte Rechte erforderlich.)

    Sie können Visual Studio so konfigurieren, dass der Dienst immer mit der Administratorrolle ausgeführt wird, indem Sie mit der rechten Maustaste auf das Verknüpfungssymbol für Visual Studio klicken, dann auf **Eigenschaften > Erweitert** klicken und dann die Option auswählen, dass der Dienst immer mit der Administratorrolle ausgeführt wird.

## <a name="the-web-server-is-not-configured-correctly"></a><a name="web_server_config"></a> Der Webserver ist nicht richtig konfiguriert

- Unter [Error: Der Webserver ist nicht richtig konfiguriert.](../debugger/error-the-web-server-is-not-configured-correctly.md) finden Sie weitere Informationen.

## <a name="unable-to-connect-to-the-webserver"></a><a name="unabletoconnect"></a> Die Verbindung mit dem Webserver konnte nicht hergestellt werden

- Führen Sie Visual Studio und den Webserver auf demselben Computer aus, und debuggen Sie mithilfe von **F5** (anstelle von **An Prozess anhängen**)? Öffnen Sie die Projekteigenschaften, und vergewissern Sie sich, dass das Projekt so konfiguriert ist, dass es eine Verbindung zum richtigen Webserver und zur Start-URL herstellt. (Öffnen Sie abhängig vom Projekttyp **Eigenschaften > Web > Server** oder **Eigenschaften > Debuggen**. Öffnen Sie bei einem Web Forms-Projekt **Eigenschaftenseiten > Startoptionen > Server**.)

- Starten Sie Ihren Anwendungspool andernfalls neu, und setzen Sie dann die IIS zurück. Weitere Informationen erhalten Sie unter [Überprüfen der IIS-Konfiguration](#vxtbshttpservererrorsthingstocheck).

## <a name="the-web-server-did-not-respond-in-a-timely-manner"></a><a name="webservertimeout"></a> Der Webserver hat nicht rechtzeitig reagiert

- Setzen Sie die IIS zurück, und versuchen Sie, das Debuggen zu wiederholen. Möglicherweise sind an den IIS-Prozess mehrere Debuggerinstanzen angefügt. Wenn Sie ein Zurücksetzungsvorgang durchführen, werden diese beendet. Weitere Informationen erhalten Sie unter [Überprüfen der IIS-Konfiguration](#vxtbshttpservererrorsthingstocheck).

## <a name="the-microsoft-visual-studio-remote-debugging-monitormsvsmonexe-does-not-appear-to-be-running-on-the-remote-computer"></a><a name="msvsmon"></a> Der Microsoft Visual Studio-Remotedebugmonitor (msvsmon.exe) wird auf dem Remotecomputer nicht ausgeführt

- Wenn Sie das Debuggen auf einem Remotecomputer ausführen, vergewissern Sie sich, dass [der Remotedebugger installiert ist und ausgeführt wird](../debugger/remote-debugging.md). Wenn in der Meldung eine Firewall erwähnt wird, überprüfen Sie, ob die [richtigen Ports in der Firewall](../debugger/remote-debugger-port-assignments.md) geöffnet sind, besonders dann, wenn Sie eine Firewall eines Drittanbieters verwenden.
- Wenn Sie eine HOSTS-Datei verwenden, überprüfen Sie, ob sie ordnungsgemäß konfiguriert ist. Wenn Sie beispielsweise mithilfe von **F5** (anstelle von **An Prozess anhängen**) debuggen, muss die HOSTS-Datei dieselbe Projekt-URL enthalten, die auch in den Projekteigenschaften enthalten ist: Je nach Projekttyp finden Sie sie unter **Eigenschaften > Web > Server** oder **Eigenschaften > Debuggen**.

## <a name="the-remote-server-returned-an-error"></a><a name="server_error"></a> Der Remoteserver hat einen Fehler zurückgegeben

Sehen Sie in Ihrer [IIS-Protokolldatei](https://support.microsoft.com/help/943891/the-http-status-code-in-iis-7-0--iis-7-5--and-iis-8-0) nach, ob untergeordneter Fehlercode und weitere Informationen enthalten sind. Sehen Sie sich außerdem diesen IIS 7-[Blogbeitrag](https://blogs.iis.net/tomkmvp/troubleshoot-a-403) an.

Außerdem finden Sie hier einige häufig auftretende Fehlercodes und einige Vorschläge dazu.
- (403) Unzulässig. Für diesen Fehler gibt es viele verschiedene Gründe. Suchen Sie in der Protokolldatei und den IIS-Sicherheitseinstellungen für die Website nach möglichen Ursachen. Sorgen Sie dafür, dass die web.config-Datei des Servers im Kompilierungselement `debug=true` enthält. Vergewissern Sie sich, dass Ihr Webanwendungsordner über die erforderlichen Berechtigungen verfügt und dass die Konfiguration Ihres Anwendungspools korrekt ist. Möglicherweise wurde ein Kennwort geändert. Weitere Informationen finden Sie unter [Überprüfen der IIS-Konfiguration](#vxtbshttpservererrorsthingstocheck). Wenn diese Einstellungen korrekt sind und Sie lokal debuggen, überprüfen Sie außerdem, ob Sie eine Verbindung zum richtigen Servertyp und der korrekten URL herstellen. Je nach Projekttyp finden Sie diese Informationen unter **Eigenschaften > Web > Server** oder **Eigenschaften > Debuggen**.
- (503) Server nicht verfügbar. Möglicherweise wurde der Anwendungspool aufgrund eines Fehlers oder einer Konfigurationsänderung angehalten. Starten Sie den Anwendungspool neu.
- (404) Nicht gefunden. Überprüfen Sie, ob der Anwendungspool mit der richtigen ASP.NET-Version konfiguriert wurde.

## <a name="could-not-start-aspnet-debugging"></a><a name="aspnet"></a> Das ASP.NET-Debuggen konnte nicht gestartet werden

- Starten Sie den Anwendungspool neu, und setzen Sie die IIS zurück. Weitere Informationen erhalten Sie unter [Überprüfen der IIS-Konfiguration](#vxtbshttpservererrorsthingstocheck).
- Wenn Sie URL-Umschreibungen durchführen, testen Sie eine einfache web.config-Datei ohne URL-Umschreibungen. Sehen Sie sich unter [Überprüfen der IIS-Konfiguration](#vxtbshttpservererrorsthingstocheck) den **Hinweis** zum URL-Rewrite-Modul an.

## <a name="the-debugger-cannot-connect-to-the-remote-computer"></a><a name="cannot_connect"></a> Der Debugger kann keine Verbindung zum Remotecomputer herstellen

Wenn Sie lokal debuggen, öffnen Sie die Projekteigenschaften in Visual Studio und vergewissern Sie sich, dass das Projekt so konfiguriert ist, dass eine Verbindung zum richtigen Webserver und zur korrekten URL hergestellt wird. (Öffnen Sie ja nach Projekttyp **Eigenschaften > Web > Server** oder **Eigenschaften > Debuggen**.)

Dieser Fehler kann beim lokalen Debuggen auftreten, da Visual Studio eine 32-Bit-Anwendung ist und daher die 64-Bit-Version des Remotedebuggers zum Debuggen von 64-Bit-Anwendungen verwendet. Überprüfen Sie Ihren Anwendungspool in den IIS, um dafür zu sorgen, dass **32-Bit-Anwendungen aktivieren** auf `true` festgelegt ist. Starten Sie die IIS dann neu, und versuchen Sie es noch mal.

Wenn Sie eine HOSTS-Datei verwenden, überprüfen Sie, ob sie ordnungsgemäß konfiguriert ist. Die HOSTS-Datei muss beispielsweise dieselbe Projekt-URL enthalten, die auch in den Projekteigenschaften enthalten ist: Je nach Projekttyp finden Sie sie unter **Eigenschaften > Web > Server** oder **Eigenschaften > Debuggen**.

## <a name="see-help-for-common-configuration-errors-running-the-webpage-outside-of-the-debugger-may-provide-further-information"></a><a name="see_help"></a> In der Hilfe werden häufige Konfigurationsfehler erläutert. Möglicherweise erhalten Sie weitere Informationen, wenn Sie die Webseite außerhalb des Debuggers ausführen.

- Führen Sie Visual Studio und den Webserver auf demselben Computer aus? Öffnen Sie die Projekteigenschaften, und vergewissern Sie sich, dass das Projekt so konfiguriert ist, dass es eine Verbindung zum richtigen Webserver und zur Start-URL herstellt. (Öffnen Sie ja nach Projekttyp **Eigenschaften > Web > Server** oder **Eigenschaften > Debuggen**.)

- Wenn dies nicht funktioniert oder Sie ein Remotedebugging durchführen, befolgen Sie die Schritte unter [Überprüfen der IIS-Konfiguration](#vxtbshttpservererrorsthingstocheck).

## <a name="operation-not-supported-unknown-error-errornumber"></a><a name="operation_not_supported"></a> Vorgang wird nicht unterstützt. Unbekannter Fehler: *Fehlernummer*

Wenn Sie URL-Umschreibungen durchführen, testen Sie eine einfache web.config-Datei ohne URL-Umschreibungen. Sehen Sie sich unter [Überprüfen der IIS-Konfiguration](#vxtbshttpservererrorsthingstocheck) den **Hinweis** zum URL-Rewrite-Modul an.

## <a name="check-your-iis-configuration"></a><a name="vxtbshttpservererrorsthingstocheck"></a> Überprüfen der IIS-Konfiguration

Unter Umständen müssen Sie auch IIS zurücksetzen, nachdem Sie die hier aufgeführten Problembehandlungsschritte ausgeführt haben und bevor Sie das Debugging noch mal versuchen. Öffnen Sie hierzu eine Administratoreingabeaufforderung mit erhöhten Rechten, und geben Sie `iisreset` ein.

* Stoppen Sie Ihre IIS-Anwendungspools, und starten Sie sie neu, und versuchen Sie es dann noch mal.

    Aufgrund eines Fehlers wurde der Anwendungspool möglicherweise angehalten. Möglicherweise erfordert es auch eine andere Konfigurationsänderung, die Sie vorgenommen haben, dass Sie Ihren Anwendungspool anhalten und neu starten.

    > [!NOTE]
    > Wenn der Anwendungspool weiterhin angehalten wird, müssen Sie möglicherweise das URL-Rewrite-Modul über die Einstellungen deinstallieren. Sie können die Deinstallation mit dem Webplattform-Installer (Web PI) durchführen. Dieses Problem tritt möglicherweise nach einem umfassenden Systemupgrade auf.

* Überprüfen Sie die Konfiguration des Anwendungspools, korrigieren Sie sie gegebenenfalls, und versuchen Sie es dann noch mal.

    Der Anwendungspool wurde möglicherweise für eine ASP.NET-Version konfiguriert, die nicht mit Ihrem Visual Studio-Projekt übereinstimmt. Aktualisieren Sie die ASP.NET-Version im Anwendungspool, und starten Sie ihn dann neu. Detaillierte Informationen finden Sie unter [IIS 8.0 mit ASP.NET 3.5 und ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

    Wenn das Kennwort der Anmeldeinformationen geändert wurde, müssen Sie sie möglicherweise in Ihrem Anwendungspool oder auf der Website ebenfalls aktualisieren.  Aktualisieren Sie Anmeldeinformationen im Anwendungspool über **Erweiterte Einstellungen > Prozessmodell > Identität**. Bei der Website aktualisieren Sie die Anmeldeinformationen unter **Grundeinstellungen > Verbinden als…** . Starten Sie Ihren Anwendungspool neu.

* Überprüfen Sie, ob Ihr Webanwendungsordner die erforderlichen Berechtigungen aufweist.

    Geben Sie IIS_IUSRS, IUSR oder dem spezifischen Benutzer, der dem [Anwendungspool](/iis/manage/configuring-security/application-pool-identities) zugeordnet ist, Lese- und Ausführungsrechte für den Webanwendungsordner. Beheben Sie das Problem, und starten Sie Ihren Anwendungspool neu.

* Stellen Sie sicher, dass in den IIS die richtige ASP.NET-Version installiert ist.

    Das Problem kann durch nicht übereinstimmende Versionen von ASP.NET in IIS und in Ihrem Visual Studio-Projekt verursacht werden. Möglicherweise müssen Sie die Framework-Version in der Datei „web.config“ festlegen. Verwenden Sie zum Installieren von ASP.NET in IIS den [Webplattform-Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). Weitere Informationen finden Sie unter [IIS 8.0: Verwenden von ASP.NET 3.5 und ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45). Lesen Sie bei Verwendung von ASP.NET Core die Informationen unter [Hosten von ASP.NET Core unter Windows mit IIS](https://docs.asp.net/en/latest/publishing/iis.html).

* Beheben Sie Authentifizierungsfehler, wenn Sie nur die IP-Adresse verwenden

     Standardmäßig wird davon ausgegangen, dass IP-Adressen dem Internet zuzuordnen sind, während die NTLM-Authentifizierung nicht über das Internet vorgenommen wird. Wenn Ihre Website in den IIS so konfiguriert wurde, dass eine Authentifizierung erforderlich ist, schlägt die Authentifizierung fehl. Zur Behebung dieses Problems können Sie den Namen des Remotecomputers anstelle der IP-Adresse angeben.

## <a name="other-causes"></a>Weitere Ursachen

Wenn die IIS-Konfiguration das Problem nicht verursacht, können Sie die folgenden Schritte testen:

- Starten Sie Visual Studio mit Administratorberechtigungen neu, und versuchen Sie es noch mal.

    Für manche ASP.NET-Debugszenarios wie der Verwendung von Web Deploy sind erhöhte Rechte für Visual Studio erforderlich.

- Wenn mehrere Visual Studio-Instanzen ausgeführt werden, öffnen Sie Ihr Projekt in einer Visual Studio-Instanz (mit Administratorberechtigungen) neu, und versuchen Sie es noch mal.

- Wenn Sie eine HOSTS-Datei mit lokalen Adressen verwenden, versuchen Sie es mit der Loopbackadresse anstelle der IP-Adresse des Computers.

    Wenn Sie keine lokalen Adressen verwenden, sorgen Sie dafür, dass Ihre HOSTS-Datei dieselbe Projekt-URL einschließt, die auch in Ihren Projekteigenschaften enthalten ist. Je nach Projekttyp finden Sie sie unter **Eigenschaften > Web > Server** oder **Eigenschaften > Debuggen**.

## <a name="more-troubleshooting-steps"></a>Weitere Schritte zur Problembehandlung

* Öffnen Sie die localhost-Seite im Browser auf dem Server.

     Wenn IIS nicht ordnungsgemäß installiert wurde, sollten Fehler angezeigt werden, wenn Sie `http://localhost` in einem Browser eingeben.

     Weitere Informationen zur Bereitstellung in den IIS finden Sie unter [IIS 8.0 mit ASP.NET 3.5 und ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) und für ASP.NET Core unter [Hosten von ASP.NET Core unter Windows mit IIS](https://docs.asp.net/en/latest/publishing/iis.html).

* Erstellen Sie eine grundlegende ASP.NET-Anwendung auf dem Server, oder verwenden Sie eine grundlegende web.config-Datei.

    Wenn Sie es nicht ermöglichen können, dass die App mit dem Debugger verwendet werden kann, versuchen Sie, eine grundlegende ASP.NET-Anwendung lokal auf dem Server zu erstellen, und versuchen Sie, die grundlegende App zu debuggen. (Sie sollten die Standard-ASP.NET-MVC-Vorlage verwenden.) Wenn Sie eine grundlegende App debuggen können, können Sie darüber möglicherweise herausfinden, wo der Unterschied zwischen den beiden Konfigurationen liegt. Suchen Sie in den Einstellungen der web.config-Datei nach Unterschieden, z. B. bei den URL-Umschreibungsregeln.

## <a name="see-also"></a>Siehe auch
- [Debuggen von Webanwendungen: Fehler und Problembehandlung](../debugger/debugging-web-applications-errors-and-troubleshooting.md)