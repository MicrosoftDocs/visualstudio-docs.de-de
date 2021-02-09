---
title: Debuggen eines Azure-Clouddiensts oder virtuellen Azure-Computers
description: Debuggen eines Clouddiensts oder eines virtuellen Computers in Visual Studio
author: mikejo5000
manager: jmartens
ms.topic: how-to
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: mikejo
ms.technology: vs-ide-debug
ms.openlocfilehash: c7a95c43435cf78f169ce363b3e8fe301e9d0cbe
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844332"
---
# <a name="debugging-an-azure-cloud-service-or-virtual-machine-in-visual-studio"></a>Debuggen eines Azure-Clouddiensts oder virtuellen Computers in Visual Studio

Visual Studio bietet verschiedene Optionen für das Debuggen von Azure-Clouddiensten und virtuellen Computern.

## <a name="debug-your-cloud-service-on-your-local-computer"></a>Debuggen des Clouddiensts auf dem lokalen Computer

Sie können Zeit und Geld sparen, wenn Sie den Azure-Compute-Emulator zum Debuggen Ihres Clouddiensts auf einem lokalen Computer verwenden. Durch lokales Debuggen eines Diensts vor der Bereitstellung können Sie die Zuverlässigkeit und Leistung verbessern, ohne für die Computezeit bezahlen zu müssen. Allerdings können einige Fehler nur auftreten, wenn Sie einen Clouddienst in Azure selbst ausführen. Sie können diese Fehler debuggen, wenn Sie Remotedebuggen beim Veröffentlichen Ihres Diensts aktivieren und dann den Debugger zu einer Rolleninstanz hinzufügen.

Der Emulator simuliert den Azure-Computedienst und wird in Ihrer lokalen Umgebung ausgeführt, sodass Sie den Clouddienst vor der Bereitstellung testen und debuggen können. Der Emulator behandelt den Lebenszyklus der Rolleninstanzen und bietet Zugriff auf simulierte Ressourcen wie lokalen Speicher. Beim Debuggen oder Ausführen des Diensts in Visual Studio wird der Emulator automatisch als Hintergrundanwendung gestartet und dann der Dienst für den Emulator bereitgestellt. Mit dem Emulator können Sie Ihren Dienst anzeigen, wenn er in der lokalen Umgebung ausgeführt wird. Sie können die vollständige Version oder die Express-Version des Emulators ausführen. (Ab Azure 2,3 ist die Express-Version des Emulators der Standard.) Siehe [Verwenden von Emulator Express zum lokalen ausführen und Debuggen eines clouddiensts](vs-azure-tools-emulator-express-debug-run.md).

### <a name="to-debug-your-cloud-service-on-your-local-computer"></a>So debuggen Sie den Clouddienst auf dem lokalen Computer

1. Wählen Sie in der Menüleiste   >  **Debuggen Debuggen starten** aus, um Ihr Azure-clouddienstprojekt auszuführen. Alternativ können Sie F5 drücken. Eine Meldung wird angezeigt, dass der Serveremulator gestartet wurde. Wenn der Emulator gestartet wird, wird dies durch das Taskleistensymbol bestätigt.

    ![Azure-Emulator in der Taskleiste](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC783828.png)

2. Zeigen Sie die Benutzeroberfläche des Serveremulators an, indem Sie im Infobereich das Kontextmenü für das Azure-Symbol öffnen und dann auf **Benutzeroberfläche des Serveremulators anzeigen** klicken.

    Im linken Bereich der Benutzeroberfläche werden die Dienste angezeigt, die zurzeit im Serveremulator bereitgestellt sind, sowie die Rolleninstanzen, die in jedem Dienst ausgeführt werden. Sie können den Dienst oder die Rollen auswählen, um Lebenszyklus-, Protokollierungs- und Diagnoseinformationen im rechten Bereich anzuzeigen. Wenn Sie den Fokus in den oberen Rand eines enthaltenen Fensters setzen, wird es erweitert und füllt den rechten Bereich aus.

3. Gehen Sie durch die Anwendung, indem Sie im Menü **Debuggen** die Option Befehle auswählen und Haltepunkte im Code festlegen. Wenn Sie die Anwendung im Debugger schrittweise durchlaufen, werden die Bereiche mit dem aktuellen Status der Anwendung aktualisiert. Wenn Sie das Debuggen beenden, wird die Anwendungsbereitstellung gelöscht. Wenn Ihre Anwendung eine Webrolle umfasst und Sie als Startaktion das Starten des Webbrowsers festgelegt haben, startet Visual Studio Ihre Webanwendung im Browser. Wenn Sie die Anzahl der Instanzen einer Rolle in der Dienstkonfiguration ändern, müssen Sie den Clouddienst beenden und dann das Debuggen neu starten, damit Sie diese neuen Instanzen der Rolle debuggen können.

    > [!NOTE]
    > Wenn Sie das Ausführen oder Debuggen des Diensts beenden, werden der lokale Serveremulator und der Speicheremulator nicht beendet. Sie müssen explizit über den Infobereich beendet werden.

## <a name="debug-a-cloud-service-in-azure"></a>Debuggen eines Clouddiensts in Azure

Um einen Clouddienst über einen Remotecomputer zu debuggen, müssen Sie diese Funktion explizit aktivieren, wenn Sie den Clouddienst bereitstellen, damit erforderliche Dienste (z. B. "msvsmon.exe") auf den virtuellen Computern installiert werden, auf denen die Rolleninstanzen ausgeführt werden. Wenn Sie das Remotedebuggen nicht aktiviert haben, als der Dienst veröffentlicht wurde, müssen Sie den Dienst mit aktiviertem Remotedebuggen erneut veröffentlichen.

Wenn Sie das Remotedebuggen für einen Clouddienst aktivieren, führt dies nicht zu einer Leistungsverschlechterung oder zu zusätzlichen Gebühren. Verwenden Sie das Remotedebuggen nicht für einen Produktionsdienst, da sich dies negativ auf Clients auswirken kann, die den Dienst nutzen.

> [!NOTE]
> Wenn Sie einen Clouddienst über Visual Studio veröffentlichen, können Sie **IntelliTrace** für alle Rollen in diesem Dienst aktivieren, die für .NET Framework 4 oder .NET Framework 4.5 ausgelegt sind. Mit **IntelliTrace** können Sie Ereignisse untersuchen, die in einer Rolleninstanz in der Vergangenheit aufgetreten sind, und den Kontext zum jeweiligen Zeitpunkt reproduzieren. Weitere Informationen finden Sie unter [Debuggen eines veröffentlichten Clouddiensts mit IntelliTrace](vs-azure-tools-IntelliTrace-debug-published-cloud-services.md) und [Visual Studio und Verwenden von IntelliTrace](../debugger/intellitrace.md).

### <a name="to-enable-remote-debugging-for-a-cloud-service"></a>So aktivieren Sie das Remotedebuggen für einen Clouddienst

1. Öffnen Sie das Kontextmenü des Azure-Projekts, und klicken Sie auf **Veröffentlichen**.

2. Wählen Sie die **Stagingumgebung** und die **Debugkonfiguration** aus.

    Dies ist nur eine Empfehlung. Sie können auch Testumgebungen in einer Produktionsumgebung ausführen. Es kann jedoch möglicherweise negative Auswirkungen auf die Benutzer haben, wenn Sie das Remotedebuggen für die Produktionsumgebung aktivieren. Sie können die Releasekonfiguration auswählen, aber die Debugkonfiguration vereinfacht das Debuggen.

    ![Wählen Sie die Debugkonfiguration aus](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746717.gif)

3. Führen Sie die üblichen Schritte aus, aber aktivieren Sie auf der Registerkarte **Erweiterte Einstellungen** das Kontrollkästchen **Remotedebugger für alle Rollen aktivieren**.

    ![Debugkonfiguration](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746718.gif)

### <a name="to-attach-the-debugger-to-a-cloud-service-in-azure"></a>So fügen Sie den Debugger an einen Clouddienst in Azure an

1. Erweitern Sie im Server-Explorer den Knoten für den Clouddienst.

2. Öffnen Sie das Kontextmenü für die Rolle oder Rolleninstanz, an die das Anfügen erfolgen soll, und klicken Sie dann auf **Debugger anfügen**.

    Wenn Sie eine Rolle debuggen, wird der Visual Studio-Debugger an jede Instanz dieser Rolle angefügt. Der Debugger wird an einem Haltepunkt für die erste Rolleninstanz unterbrochen, die diese Codezeile ausführt und alle Bedingungen dieses Haltepunkts erfüllt. Wenn Sie eine Instanz debuggen, wird der Debugger nur an diese Instanz angefügt und wird an einem Haltepunkt nur unterbrochen, wenn diese spezielle Instanz diese Codezeile ausführt und die Bedingungen des Haltepunkts erfüllt.

    ![Debugger anfügen](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746719.gif)

3. Nachdem der Debugger an eine Instanz angefügt wurde, debuggen Sie wie üblich. Der Debugger wird automatisch an den entsprechenden Hostprozess für Ihre Rolle angefügt. Abhängig von der Rolle wird der Debugger an "w3wp.exe", "WaWorkerHost.exe" oder "WaIISHost.exe" angefügt. Erweitern Sie im Server-Explorer den Instanzknoten, um den Prozess zu überprüfen, an den der Debugger angefügt ist. Weitere Informationen zu Azure-Prozessen finden Sie unter [Azure-Rollenarchitektur](/archive/blogs/kwill/windows-azure-role-architecture).

    ![Dialogfeld "Codetyp auswählen"](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

4. Zum Identifizieren der Prozesse, an die der Debugger angefügt ist, wählen Sie in der Menüleiste die Option Windows-Prozesse **Debuggen** aus  >    >  , und öffnen Sie das Dialogfeld **Prozesse** . (Tastatur: Strg+Alt+Z) Um einen bestimmten Prozess zu trennen, öffnen Sie dessen Kontextmenü, und klicken Sie dann auf **Prozess abtrennen**. Sie können auch den Instanzknoten im Server-Explorer suchen, dann den Prozess suchen, das Kontextmenü öffnen und auf **Prozess abtrennen** klicken.

    ![Prozesse debuggen](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC690787.gif)

> [!WARNING]
> Vermeiden Sie es beim Remotedebuggen, lange an Breakpoints anzuhalten. Azure behandelt Prozesse, die länger als einige Minuten angehalten wurden, als nicht reagierend und sendet keinen Datenverkehr mehr an diese Instanz. Wenn Sie zu lange unterbrechen, wird "msvsmon.exe" vom Prozess getrennt.

Um den Debugger von allen Prozessen in Ihrer Instanz oder Rolle zu trennen, öffnen Sie das Kontextmenü für die Rolle oder Instanz, die Sie debuggen, und klicken Sie dann auf **Debugger lösen**.

## <a name="limitations-of-remote-debugging-in-azure"></a>Einschränkungen beim Remotedebuggen in Azure

Analog zu Azure SDK 2.3 gelten beim Remotedebuggen folgende Einschränkungen:

* Wenn das Remotedebuggen aktiviert ist, können Sie keinen Clouddienst veröffentlichen, in dem eine Rolle mehr als 25 Instanzen aufweist.
* Der Debugger verwendet die Ports 30400 bis 30424, 31400 bis 31424 und 32400 bis 32424. Wenn Sie versuchen, diese Ports zu verwenden, können Sie Ihren Dienst nicht veröffentlichen, und eine der folgenden Fehlermeldungen wird im Aktivitätsprotokoll für Azure angezeigt:

  * Fehler beim Überprüfen der CSCFG-Datei anhand der CSDEF-Datei.
    Der reservierte Portbereich "Bereich" für den Endpunkt "Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector" der Rolle "Rolle" überschneidet sich mit einem bereits definierten Port oder Bereich.
  * Fehler bei der Zuordnung. Wiederholen Sie den Vorgang später. Reduzieren Sie die VM-Größe oder die Anzahl der Rolleninstanzen, oder stellen Sie die VM in einer anderen Region bereit.

## <a name="debugging-azure-virtual-machines"></a>Debuggen virtueller Azure-Computer

Sie können Programme debuggen, die auf virtuellen Computern in Azure ausgeführt werden, indem Sie den Server-Explorer in Visual Studio verwenden. Wenn Sie das Remotedebuggen auf einem virtuellen Computer in Azure aktivieren, installiert Azure die Erweiterung für das Remotedebuggen auf dem virtuellen Computer. Sie können dann den Debugger an Prozesse auf dem virtuellen Computer anfügen und wie gewohnt debuggen.

> [!NOTE]
> Für durch den Azure-Ressourcen-Manager-Stapel erstellte virtuelle Computer ist Remotedebuggen mit dem Cloud-Explorer in Visual Studio 2015 möglich. Weitere Informationen finden Sie unter [Verwalten von Azure-Ressourcen mit dem Cloud-Explorer](vs-azure-tools-resources-managing-with-cloud-explorer.md).

### <a name="to-debug-an-azure-virtual-machine"></a>So debuggen Sie einen virtuellen Computer in Azure

1. Erweitern Sie im Server-Explorer den Knoten "Virtuelle Computer", und wählen Sie den Knoten des virtuellen Computers aus, den Sie debuggen möchten.

2. Öffnen Sie das Kontextmenü, und klicken Sie auf **Debuggen aktivieren**. Wenn Sie gefragt werden, ob Sie sicher sind, dass Sie das Debuggen auf dem virtuellen Computer aktivieren möchten, klicken Sie auf **Ja**.

    Azure installiert die Erweiterung für das Remotedebuggen auf dem virtuellen Computer, um das Debuggen zu aktivieren.

    ![Befehl zum Aktivieren des Debuggens virtueller Computer](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Azure-Aktivitätsprotokoll](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

3. Nachdem die Installation der Remotedebugerweiterung abgeschlossen ist, öffnen Sie das Kontextmenü des virtuellen Computers und klicken dann auf **Debugger anfügen**

    Azure ruft eine Liste der Prozesse auf dem virtuellen Computer ab und zeigt diese im Dialogfeld **An den Prozess anhängen** an.

    ![Befehl "Debugger anfügen"](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

4. Klicken Sie im Dialogfeld **An den Prozess anhängen** auf **Auswählen**, um die Ergebnisliste einzuschränken, sodass nur die Codetypen angezeigt werden, die Sie debuggen möchten. Sie können verwalteten 32- oder 64-Bit-Code und/oder systemeigenen Code debuggen.

    ![Dialogfeld "Codetyp auswählen"](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

5. Wählen Sie die Prozesse aus, die Sie auf dem virtuellen Computer debuggen möchten, und wählen Sie dann **Anfügen** Beispielsweise können Sie den Prozess "w3wp.exe" auswählen, wenn Sie eine Web-App auf dem virtuellen Computer debuggen möchten. Weitere Informationen finden Sie unter [Debuggen von mindestens einem Prozess in Visual Studio](../debugger/debug-multiple-processes.md) und im Blogbeitrag zur [Azure-Rollenarchitektur](/archive/blogs/kwill/windows-azure-role-architecture).

## <a name="create-a-web-project-and-a-virtual-machine-for-debugging"></a>Erstellen eines Webprojekts und eines virtuellen Computers zum Debuggen

Vor dem Veröffentlichen des Azure-Projekts finden Sie es möglicherweise nützlich, es in einer eigenständigen Umgebung zu testen, die Debug- und Testszenarien unterstützt und in der Sie Test- und Überwachungsprogramme installieren können. Eine Möglichkeit zum Ausführen solcher Tests ist das Remotedebuggen Ihrer App auf einem virtuellen Computer.

Visual Studio ASP.NET-Projekte bieten eine Option, einen praktischen virtuellen Computer zu erstellen, den Sie für App-Tests verwenden können. Der virtuelle Computer umfasst häufig genutzte Endpunkte wie z.B. PowerShell, Remotedesktop und WebDeploy.

### <a name="to-create-a-web-project-and-a-virtual-machine-for-debugging"></a>So erstellen Sie ein Webprojekt und einen virtuellen Computer zum Debuggen

1. Erstellen Sie eine neue ASP.NET-Webanwendung in Visual Studio.

2. Wählen Sie im Dialogfeld Neues ASP.net-Projekt im Abschnitt Azure im Dropdown-Listenfeld **virtueller Computer** aus. Lassen Sie das Kontrollkästchen **Remoteressourcen erstellen** aktiviert. Klicken Sie zum Fortfahren auf **OK** .

    Das Dialogfeld **Virtuellen Computer in Azure erstellen** wird angezeigt.

    ![Dialogfeld "Neues ASP.NET-Webprojekt erstellen"](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746723.png)

    > [!NOTE]
    > Sie werden aufgefordert, sich bei Ihrem Azure-Konto anzumelden, wenn Sie noch nicht angemeldet sind.

3. Wählen Sie die verschiedenen Einstellungen für den virtuellen Computer aus, und klicken Sie dann auf **OK**. Weitere Informationen finden Sie unter [Virtuelle Computer](/azure/virtual-machines/) .

    Der Name, den Sie als DNS-Namen eingeben, ist der Name des virtuellen Computers.

    ![Dialogfeld zum Erstellen eines virtuellen Computers in Azure](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746724.png)

    Azure erstellt den virtuellen Computer und stellt dann die Endpunkte (z. b. Remotedesktop und Web deploy bereit und konfiguriert sie.

4. Nachdem der virtuelle Computer vollständig konfiguriert wurde, wählen Sie im Server-Explorer den Knoten des virtuellen Computers aus.

5. Öffnen Sie das Kontextmenü, und klicken Sie auf **Debuggen aktivieren**. Wenn Sie gefragt werden, ob Sie sicher sind, dass Sie das Debuggen auf dem virtuellen Computer aktivieren möchten, klicken Sie auf **Ja**.

    Azure installiert die Erweiterung für das Remotedebuggen auf dem virtuellen Computer, um das Debuggen zu aktivieren.

    ![Befehl zum Aktivieren des Debuggens virtueller Computer](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Azure-Aktivitätsprotokoll](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

6. Veröffentlichen Sie Ihr Projekt, wie unter [Gewusst wie: Bereitstellen eines Webanwendungsprojekts mit der One-Click-Veröffentlichung in Visual Studio](/previous-versions/aspnet/dd465337(v=vs.110))beschrieben. Da Sie auf dem virtuellen Computer debuggen möchten, wählen Sie auf der Seite **Einstellungen** des Assistenten **Web veröffentlichen** als Konfiguration **Debuggen** aus. Dadurch wird sichergestellt, dass Codesymbole beim Debuggen verfügbar sind.

    ![Veröffentlichungseinstellungen](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718349.png)

7. Wählen Sie unter **Dateiveröffentlichungsoptionen** die Option **Zusätzliche Dateien am Ziel entfernen** aus, wenn das Projekt zu einem früheren Zeitpunkt bereits bereitgestellt wurde.

8. Nachdem das Projekt veröffentlicht wurde, klicken Sie im Kontextmenü des virtuellen Computers in Server-Explorer auf **Debugger anfügen**

    Azure ruft eine Liste der Prozesse auf dem virtuellen Computer ab und zeigt diese im Dialogfeld **An den Prozess anhängen** an.

    ![Befehl "Debugger anfügen"](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

9. Klicken Sie im Dialogfeld **An den Prozess anhängen** auf **Auswählen**, um die Ergebnisliste einzuschränken, sodass nur die Codetypen angezeigt werden, die Sie debuggen möchten. Sie können verwalteten 32- oder 64-Bit-Code und/oder systemeigenen Code debuggen.

    ![Dialogfeld "Codetyp auswählen"](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

10. Wählen Sie die Prozesse aus, die Sie auf dem virtuellen Computer debuggen möchten, und wählen Sie dann **Anfügen** Beispielsweise können Sie den Prozess "w3wp.exe" auswählen, wenn Sie eine Web-App auf dem virtuellen Computer debuggen möchten. Weitere Informationen finden Sie unter [Debugging von mindestens einem Prozess in Visual Studio](../debugger/debug-multiple-processes.md) .

## <a name="next-steps"></a>Nächste Schritte

* Verwenden Sie **IntelliTrace** , um ein Protokoll der Aufrufe und Ereignisse von einem Releaseserver zu erfassen. Weitere Informationen finden Sie unter [Debuggen eines veröffentlichten Clouddiensts mit IntelliTrace und Visual Studio](vs-azure-tools-IntelliTrace-debug-published-cloud-services.md).

* Verwenden Sie die **Azure-Diagnose** , um ausführliche Informationen zu Code, der in Rollen ausgeführt wird, zu protokollieren, unabhängig davon, ob die Rollen in der Entwicklungsumgebung oder in Azure ausgeführt werden. Weitere Informationen finden Sie unter [Sammeln von Protokollierungsdaten mit der Azure-Diagnose](/azure/cloud-services/cloud-services-dotnet-diagnostics).
