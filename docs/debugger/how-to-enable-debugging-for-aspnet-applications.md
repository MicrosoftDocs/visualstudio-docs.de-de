---
title: Aktivieren des Debuggens von ASP.NET-Anwendungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/29/2020
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications
- Web.config configuration file, debug mode
- debugging [Visual Studio], ASP.NET
ms.assetid: 3beed819-cece-4864-8184-bd410000973a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 3755489332bcc174e70e193a836db05e672907e1
ms.sourcegitcommit: f1bb1b66ed141837e992b3352ce68ff24c11f53e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93102570"
---
# <a name="debug-aspnet-or-aspnet-core-apps-in-visual-studio"></a>Debuggen von ASP.NET- oder ASP.NET Core-Apps in Visual Studio

Sie können ASP.NET- und ASP.NET Core-Apps in Visual Studio debuggen. Der Prozess unterscheidet sich zwischen ASP.NET und ASP.NET Core sowie davon, ob Sie ihn auf IIS Express oder einem lokalen IIS-Server ausführen.

>[!NOTE]
>Die folgenden Schritte und Einstellungen gelten nur für das Debuggen von Apps auf einem lokalen Server. Beim Debuggen von Apps auf einem IIS-Remoteserver wird **An Prozess anhängen** verwendet und diese Einstellungen werden ignoriert. Weitere Informationen und Anweisungen zum Remotedebuggen von ASP.NET-Apps auf IIS finden Sie unter [Remotedebuggen von ASP.NET auf einem IIS-Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) oder [Remotedebuggen von ASP.NET Core auf einem IIS-Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md).

Der integrierte IIS Express-Server ist in Visual Studio enthalten. IIS Express ist der Standarddebugserver für ASP.NET- und ASP.NET Core-Projekte und ist vorkonfiguriert. Dies ist die einfachste Möglichkeit zum Debuggen und eignet sich bestens für das anfängliche Debuggen und Testen.

Sie können eine ASP.NET- oder ASP.NET Core-App auch auf einem lokalen IIS-Server (Version 8.0 oder höher) debuggen, der zum Ausführen der App konfiguriert ist. Sie müssen die folgenden Anforderungen erfüllen, um auf einem lokalen IIS-Server debuggen zu können:

<a name="iis"></a>
- Sofern noch nicht vorhanden, installieren Sie die Workload **ASP.NET und Webentwicklung**. (Führen Sie den Visual Studio-Installer erneut aus, klicken Sie auf **Ändern** , und fügen Sie diese Workload hinzu.)

   ::: moniker range="vs-2017"
   Suchen Sie in Visual Studio 2017 nach der Komponente **Entwicklungszeit-IIS-Unterstützung**. Stellen Sie sicher, dass sie beim Hinzufügen der Workload ausgewählt ist.
   ::: moniker-end
- Starten Sie Visual Studio als Administrator.
- Installieren und konfigurieren Sie IIS ordnungsgemäß mit den entsprechenden Versionen von ASP.NET und/oder ASP.NET Core. Weitere Informationen zur Verwendung von IIS mit ASP.NET Core finden Sie unter [Hosten von ASP.NET Core unter Windows mit IIS](/aspnet/core/host-and-deploy/iis/index). Informationen zu ASP.NET finden Sie unter [Installieren von IIS und ASP.NET-Modulen](/iis/application-frameworks/scenario-build-an-aspnet-website-on-iis/configuring-step-1-install-iis-and-asp-net-modules).
- Stellen Sie sicher, dass die App fehlerfrei in IIS ausgeführt wird.

## <a name="debug-aspnet-apps"></a>Debuggen von ASP.NET-Apps

IIS Express ist die vorkonfigurierte Standardeinstellung. Wenn Sie auf einem lokalen IIS-Server debuggen, müssen Sie sicherstellen, dass Sie die [Anforderungen für Debuggen auf lokalen IIS-Servern](#iis) erfüllen.

1. Klicken Sie in Visual Studio im **Projektmappen-Explorer** auf das ASP.NET-Projekt, dann auf das Symbol für **Eigenschaften** , und drücken Sie **ALT**+**EINGABETASTE**. Alternativ können Sie mit der rechten Maustaste auf das Projekt und anschließend mit der linken Maustaste auf **Eigenschaften** klicken.

1. Wählen Sie die Registerkarte **Web** aus.

1. Gehen Sie im Bereich **Eigenschaften** unter **Server** wie folgt vor:
   - Wählen Sie für IIS Express die Option **IIS Express** im Dropdownmenü aus.
   - Für lokales IIS
     1. wählen Sie im Dropdownmenü die Option **Lokales IIS** aus.
     1. Klicken Sie dann neben dem Feld **Projekt-URL** auf **Virtuelles Verzeichnis erstellen** , wenn Sie die App noch nicht in IIS eingerichtet haben.

1. Wählen Sie unter **Debugger** die Option **ASP.NET** aus.

   ![ASP.NET-Debuggereinstellungen](media/dbg-aspnet-enable-debugging2.png "ASP.NET-Debuggereinstellungen")

1. Verwenden Sie **Datei** > **Ausgewählte Elemente speichern** oder **STRG**+**S** , um jegliche Änderungen zu speichern.

1. Legen Sie Haltepunkte für den Code fest, um die App in Ihrem Projekt zu debuggen. Stellen Sie in der Visual Studio-Symbolleiste sicher, dass die Konfiguration auf **Debuggen** festgelegt ist und dass der gewünschte Browser unter **IIS Express (\<Browser name>)** oder **Lokales IIS (\<Browser name>)** im Emulatorfeld angezeigt wird.

1. Klicken Sie in der Symbolleiste auf **IIS Express (\<Browser name>)** oder **Lokales IIS (\<Browser name>)** , und wählen Sie im Menü **Debuggen** die Option **Debuggen starten** aus, oder drücken Sie **F5**. Der Debugger hält an dem Haltepunkt an. Wenn der Debugger die Haltepunkte nicht erreichen kann, finden Sie weitere Informationen im Abschnitt [Behandeln von Problemen beim Debuggen](#troubleshoot-debugging).

## <a name="debug-aspnet-core-apps"></a>Debuggen von ASP.NET Core-Apps

IIS Express ist die vorkonfigurierte Standardeinstellung. Wenn Sie auf einem lokalen IIS-Server debuggen, müssen Sie sicherstellen, dass Sie die [Anforderungen für Debuggen auf lokalen IIS-Servern](#iis) erfüllen.

1. Klicken Sie in Visual Studio im **Projektmappen-Explorer** auf das ASP.NET Core-Projekt, dann auf das Symbol für **Eigenschaften** , und drücken Sie **ALT**+**EINGABETASTE**. Alternativ können Sie mit der rechten Maustaste auf das Projekt und anschließend mit der linken Maustaste auf **Eigenschaften** klicken.

1. Klicken Sie auf die Registerkarte **Debuggen**.

1. Gehen Sie im Bereich **Eigenschaften** neben **Profil** wie folgt vor:
   - Wählen Sie für IIS Express die Option **IIS Express** im Dropdownmenü aus.
   - Wählen Sie für lokales IIS den App-Namen im Dropdownmenü aus, oder klicken Sie auf **Neu** , erstellen Sie einen neuen Profilnamen, und klicken Sie dann auf **OK**.

1. Wählen Sie im Dropdownmenü neben **Starten** entweder **IIS Express** oder **IIS** aus.

1. Stellen Sie sicher, dass **Browser starten** ausgewählt ist.

1. Stellen Sie unter **Umgebungsvariablen** sicher, dass **ASPNETCORE_ENVIRONMENT** mit dem Wert **Development** vorhanden ist. Wenn das nicht der Fall ist, klicken Sie auf **Hinzufügen** , und fügen Sie die Umgebungsvariable hinzu.

   ![ASP.NET Core-Debuggereinstellungen](../debugger/media/dbg-aspnet-enable-debugging3.png "ASP.NET Core-Debuggereinstellungen")

1. Verwenden Sie **Datei** > **Ausgewählte Elemente speichern** oder **STRG**+**S** , um jegliche Änderungen zu speichern.

1. Legen Sie Haltepunkte für den Code fest, um die App in Ihrem Projekt zu debuggen. Stellen Sie in der Visual Studio-Symbolleiste sicher, dass die Konfiguration auf **Debuggen** festgelegt ist und dass entweder **IIS Express** oder der neue IIS-Profilname im Emulatorfeld angezeigt wird.

1. Klicken Sie in der Symbolleiste auf **IIS Express** oder **\<IIS profile name>** , und wählen Sie im Menü **Debuggen** die Option **Debuggen starten** aus, oder drücken Sie **F5**. Der Debugger hält an dem Haltepunkt an. Wenn der Debugger die Haltepunkte nicht erreichen kann, finden Sie weitere Informationen im Abschnitt [Behandeln von Problemen beim Debuggen](#troubleshoot-debugging).

## <a name="troubleshoot-debugging"></a>Behandeln von Problemen beim Debuggen

Wenn der Haltepunkt beim lokalen IIS-Debuggen nicht erreicht wird, führen Sie die folgenden Schritte zur Problembehandlung aus.

1. Starten Sie die Web-App über IIS, und stellen Sie sicher, dass sie ordnungsgemäß ausgeführt wird. Führen Sie die Web-App weiter aus.

2. Klicken Sie in Visual Studio auf **Debuggen > An Prozess anhängen** , oder drücken Sie **STRG**+**ALT**+**P** , und stellen Sie eine Verbindung mit dem ASP.NET- oder ASP.NET Core-Prozess her (in der Regel **w3wp.exe** oder **dotnet.exe** ). Weitere Informationen finden Sie unter [Anfügen an Prozesse](attach-to-running-processes-with-the-visual-studio-debugger.md) und [Ermitteln des ASP.NET-Prozessnamens](how-to-find-the-name-of-the-aspnet-process.md).

Wenn Sie mit **An Prozess anfügen** eine Verbindung herstellen und den Haltepunkt erreichen können, aber nicht über **Debuggen** > **Debuggen starten** oder **F5** , ist vermutlich eine Einstellung in den Projekteigenschaften falsch konfiguriert. Wenn Sie eine HOSTS-Datei verwenden, überprüfen Sie, ob sie ordnungsgemäß konfiguriert ist.

## <a name="configure-debugging-in-the-webconfig-file"></a>Konfigurieren des Debuggens in der Datei „web.config“

ASP.NET-Projekte enthalten standardmäßig *web.config* -Dateien, die sowohl App-Konfiguration als auch Startinformationen und Debugeinstellungen enthalten. Die *web.config* -Dateien müssen ordnungsgemäß für das Debuggen konfiguriert werden. Die Einstellungen der **Eigenschaften** in den vorherigen Abschnitten nehmen Änderungen an den *web.config* -Dateien vor. Sie können sie aber auch manuell konfigurieren.

> [!NOTE]
> ASP.NET Core-Projekte enthalten zunächst keine *web.config* -Dateien. Stattdessen verwenden sie *appsettings.json* - und *launchSettings.json* -Dateien für die App-Konfiguration und Startinformationen. Beim Bereitstellen der App wird eine *web.config* -Datei oder mehrere Dateien im Projekt erstellt, jedoch enthalten diese in der Regel keine Debuginformationen.

> [!TIP]
> Möglicherweise aktualisiert Ihr Bereitstellungsprozess die *web.config* -Einstellungen, stellen Sie also vor dem Debuggen sicher, dass die Datei *web.config* zum Debuggen konfiguriert ist.

**So konfigurieren Sie eine *web.config* -Datei manuell zum Debuggen:**

1. Öffnen Sie in Visual Studio die Datei *web.config* des ASP.NET-Projekts.

2. Die Datei *web.config* ist eine XML-Datei und enthält daher mit Tags markierte, geschachtelte Abschnitte. Machen Sie den Abschnitt `configuration/system.web/compilation` ausfindig. (Wenn das `compilation`-Element nicht vorhanden ist, erstellen Sie es.)

3. Stellen Sie sicher, dass das `debug`-Attribut im `compilation`-Element auf `true` festgelegt ist. (Wenn das `compilation`-Element kein `debug`-Attribut enthält, fügen Sie es hinzu, und legen Sie es auf `true` fest.)

   Wenn Sie einen lokalen IIS-Server anstelle des IIS Express-Standardservers verwenden, stellen Sie sicher, dass der Wert des `targetFramework`-Attributs im `compilation`-Element mit dem Framework auf dem IIS-Server übereinstimmt.

   Das `compilation`-Element der Datei *web.config* sollte dem folgenden Beispiel ähneln:

   > [!NOTE]
   > Dieses Beispiel ist eine partielle *web.config* -Datei. Normalerweise gibt es in den Elementen `configuration` und `system.web` zusätzliche XML-Abschnitte. Außerdem kann das Element `compilation` auch andere Attribute und Elemente enthalten.

   ```xml
   <configuration>
      ...
      <system.web>
          <compilation  debug="true"  targetFramework="4.6.1" ... >
             ...
          </compilation>
      </system.web>
   </configuration>
   ```

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] erkennt an *web.config* -Dateien vorgenommene Änderungen automatisch und wendet die neuen Konfigurationseinstellungen an. Sie müssen den Computer oder den IIS-Server nicht neu starten, damit die Änderungen wirksam werden.

Eine Website kann mehrere virtuelle Verzeichnisse und Unterverzeichnisse enthalten, die jeweils *web.config* -Dateien enthalten. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Apps erben Konfigurationseinstellungen von *web.config* -Dateien auf höheren Ebenen im URL-Pfad. Die hierarchischen Einstellungen der Datei *web.config* gelten für alle [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Apps, die sich in der Hierarchie unter ihnen befinden. Wenn eine andere Konfiguration in einer *web.config* -Datei festgelegt wird, die sich niedriger in der Hierarchie befindet, werden die Einstellungen der höheren Datei überschrieben.

Wenn Sie beispielsweise `debug="true"` in <em>www.microsoft.com/aaa/web.config</em> festlegen, erben alle Apps im Ordner *aaa* oder den in *aaa* enthaltenen Unterordnern diese Einstellung, es sei denn, eine dieser Apps überschreibt diese Einstellung mit einer eigenen *web.config* -Datei.

## <a name="publish-in-debug-mode-using-the-file-system"></a>Veröffentlichen im Debugmodus mithilfe des Dateisystems

Es gibt verschiedene Möglichkeiten, Apps in IIS zu veröffentlichen. In diesen Schritten wird veranschaulicht, wie Sie mithilfe des Dateisystems ein Debugveröffentlichungsprofil erstellen und bereitstellen. Hierzu müssen Sie Visual Studio als Administrator ausführen.

> [!IMPORTANT]
> Wenn Sie Ihren Code ändern oder neu erstellen, müssen Sie diese Schritte zum erneuten Veröffentlichen wiederholen.

1. Klicken Sie in Visual Studio mit der rechten Maustaste auf das Projekt, und wählen Sie dann **Veröffentlichen** aus.

3. Wählen Sie **IIS, FTP, usw.** aus, und klicken Sie dann auf **Veröffentlichen**.

    ![Veröffentlichen in IIS](media/dbg-aspnet-local-iis.png "Veröffentlichen in IIS")

4. Klicken Sie im Dialogfeld **CustomProfile** für die **Veröffentlichungsmethode** auf **Dateisystem**.

5. Klicken Sie bei **Zielspeicherort** auf **Durchsuchen** ( **...** ).

   - Wählen Sie für ASP.NET **lokales IIS** aus, wählen Sie die Website aus, die Sie für die App erstellt haben, und klicken Sie dann auf **Öffnen**.

     ![Veröffentlichen in ASP.NET in IIS](media/dbg-aspnet-local-iis1.png "Veröffentlichen in ASP.NET in IIS")

   - Klicken Sie für ASP.NET Core auf **Dateisystem** , wählen Sie den Ordner aus, den Sie für die App eingerichtet haben, und klicken Sie dann auf **Öffnen**.

1. Klicken Sie auf **Weiter**.

1. Wählen Sie im Dropdownmenü unter **Konfiguration** die Option **Konfiguration** aus.

1. Klicken Sie auf **Speichern**.

1. Stellen Sie im Dialogfeld **Veröffentlichen** sicher, dass **CustomProfile** (oder der Name des soeben erstellten Profils) angezeigt wird und dass **LastUsedBuildConfiguration** auf **Debuggen** festgelegt ist.

1. Wählen Sie **Veröffentlichen**.

    ![Veröffentlichen in IIS](media/dbg-aspnet-local-iis-select-site.png "Veröffentlichen in IIS")

> [!IMPORTANT]
> Der Debugmodus verringert die Leistung Ihrer App erheblich. Legen Sie `debug="false"` in der Datei *web.config* und ein Releasebuild beim Bereitstellen einer Produktions-App oder beim Durchführen von Leistungsmessungen fest.

## <a name="see-also"></a>Siehe auch
- [Debuggen von ASP.NET: Systemanforderungen](aspnet-debugging-system-requirements.md)
- [How to: Run the worker process under a user account (Vorgehensweise: Ausführen des Workerprozesses unter einem Benutzerkonto)](how-to-run-the-worker-process-under-a-user-account.md)
- [How to: Find the name of the ASP.NET process (Vorgehensweise: Ermitteln des ASP.NET-Prozessnamens)](how-to-find-the-name-of-the-aspnet-process.md)
- [Debug deployed web applications (Debuggen bereitgestellter Webanwendungen)](debugging-deployed-web-applications.md)
- [Exemplarische Vorgehensweise: Debuggen eines Webformulars](walkthrough-debugging-a-web-form.md)
- [How to: Debug ASP.NET exceptions (Vorgehensweise: Debuggen von ASP.NET-Ausnahmen)](how-to-debug-aspnet-exceptions.md)
- [Debuggen von Webanwendungen: Fehler und Problembehandlung](debugging-web-applications-errors-and-troubleshooting.md)
