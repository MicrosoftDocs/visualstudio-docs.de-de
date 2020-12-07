---
title: Problembehebungen für Testcontroller und Test-Agents
description: Hier lernen Sie einige der häufigsten Probleme kennen, die Ihnen bei der Arbeit mit Testcontrollern und Test-Agents in Visual Studio in die Quere kommen können.
ms.custom: SEO-VS-2020
ms.date: 10/20/2016
ms.topic: troubleshooting
helpviewer_keywords:
- load tests, test controllers
- load tests, troubleshooting
- load tests, test agents
- troubleshooting, test controllers and agents in load tests
ms.assetid: 77329348-3a5d-43de-b6cb-90f93296a081
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e86811739df2d59e3de7980cfa346da68cc0eb43
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2020
ms.locfileid: "96330146"
---
# <a name="strategies-for-troubleshooting-test-controllers-and-test-agents-in-load-tests"></a>Strategien für die Problembehandlung bei Testcontrollern und Test-Agents in Auslastungstests

Dieser Artikel behandelt einige der häufigsten Probleme, die Ihnen bei der Arbeit mit Testcontrollern und Test-Agents in Visual Studio in die Quere kommen können.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="unable-to-collect-performance-counters-on-test-agent-computer"></a>Leistungsindikatoren auf Test-Agent-Computern können nicht erfasst werden

Beim Ausführen eines Auslastungstests können Fehler auftreten, wenn Sie versuchen, eine Verbindung zu einem Test-Agent-Computer herzustellen und Leistungsindikatoren zu erfassen. Der Remoteregistrierungsdienst ist dafür zuständig, einem Remotecomputer Leistungsindikatordaten zur Verfügung zu stellen. Auf manchen Betriebssystemen wird der Remoteregistrierungsdienst nicht automatisch gestartet. Um dieses Problem zu beheben, starten Sie den Remoteregistrierungsdienst manuell.

> [!NOTE]
> Sie können über die **Systemsteuerung** auf den Remoteregistrierungsdienst zugreifen. Klicken Sie auf **Verwaltung** und dann auf **Dienste**.

Eine weitere Ursache dieses Problems sind unzureichende Berechtigungen zum Lesen von Leistungsindikatoren. Beim Ausführen von lokalen Testläufen muss das Konto des Benutzers, der den Test ausführt, Mitglied der Gruppe Hauptbenutzer (oder höher) oder Mitglied der Gruppe Systemmonitorbenutzer sein. Beim Ausführen von Remotetestläufen muss das Konto, mit dem der Controller ausgeführt wird, Mitglied der Gruppe Hauptbenutzer (oder höher) oder der Gruppe Systemmonitorbenutzer sein.

## <a name="set-the-logging-level-on-a-test-controller-computer"></a>Festlegen der Protokollierungsebene auf einem Testcontrollercomputer

Sie können den Umfang der Protokollierung auf einem Testcontrollercomputer steuern. Dies ist nützlich, wenn Sie versuchen, ein Problem beim Ausführen eines Auslastungstests in einer Umgebung zu diagnostizieren.

### <a name="to-set-the-logging-level-on-a-test-controller-computer"></a>So legen Sie die Protokollierungsebene auf einem Testcontrollercomputer fest

1. Beenden Sie den Testcontrollerdienst. Geben Sie in der Eingabeaufforderung `net stop vsttcontroller` ein.

2. Öffnen Sie die Datei *QTController.exe.config*. Diese Datei befindet sich im Installationsverzeichnis des Controllers.

3. Bearbeiten Sie den Eintrag für den `EqtTraceLevel`-Schalter im Abschnitt Systemdiagnose der Datei. Der Code sollte diesem ähneln:

    ```xml
    <system.diagnostics>
        <trace autoflush="true" indentsize="4">
            <listeners>
                <add name="myListener" type="System.Diagnostics.TextWriterTraceListener" initializeData="d:\VSTestHost.log" />
            </listeners>
        </trace>
        <switches>
            <!-- You must use integral values for "value":
                    0 = off,
                    1 = error,
                    2 = warn,
                    3 = info,
                    4 = verbose. -->
            <add name="EqtTraceLevel" value="4" />
        </switches>
    </system.diagnostics>
    ```

4. Speichern Sie die Datei .

5. Starten Sie den Controllerdienst. Geben Sie in der Eingabeaufforderung `net start vsttcontroller` ein.

Dies gilt für den Testcontroller, den Test-Agent-Dienst und den Test-Agent-Prozess. Beim Diagnostizieren von Problemen ist es hilfreich, die Protokollierung für alle drei Prozesse zu aktivieren. Die Vorgehensweise zum Festlegen der Protokollierungsebene entspricht für alle drei Prozesse der Vorgehensweise, die zuvor für den Testcontroller beschrieben wurde. Verwenden Sie die folgenden Konfigurationsdateien, um die Protokollierungsebenen für den Test-Agent-Dienst und den Agent-Prozess festzulegen.

- *QTController.exe.config* Controllerdienst

- *QTAgentService.exe.config* Agent-Dienst

- *QTDCAgent(32).exe.config* Agent-Datenadapterprozess für 32-Bit-Architektur

- *QTDCAgent(64).exe.config* Agent-Datenadapterprozess für 64-Bit-Architektur

- *QTAgent (32).exe.config* Agent-Testprozess für 32-Bit-Architektur

- *QTAgent (64).exe.config* Agent-Testprozess für 64-Bit-Architektur

## <a name="bind-a-test-controller-to-a-network-adapter"></a>Binden eines Testcontrollers an einen Netzwerkadapter

Beim Versuch, einen Test-Agent einzurichten, kann folgender Fehler auftreten:

**Error 8110. Can not connect to the specified controller computer or access the controller object.** (Fehler 8110: Verbindung zum angegebenen Controllercomputer konnte nicht hergestellt werden, oder es konnte nicht auf das Controllerobjekt zugegriffen werden.)

Dieser Fehler kann bei der Installation des Testcontrollers auf einem Computer mit mehr als einem Netzwerkadapter auftreten.

> [!NOTE]
> Es ist auch möglich, dass Test-Agents erfolgreich installiert werden können und das Problem erst bei einem Testlauf auftritt.

Um diesen Fehler zu beheben, muss der Testcontroller an einen der Netzwerkadapter gebunden werden. Sie müssen die `BindTo`-Eigenschaft auf dem Testcontroller festlegen und anschließend den Test-Agent so ändern, dass er über die IP-Adresse statt über den Namen auf den Testcontroller verweist. Die Schritte werden in den folgenden Verfahren angegeben.

### <a name="to-obtain-the-ip-address-of-the-network-adapter"></a>So erhalten Sie die IP-Adresse des Netzwerkadapters

1. Klicken Sie auf **Start** und dann auf **Ausführen**.

     Das Dialogfeld **Ausführen** wird angezeigt.

2. Geben Sie `cmd` ein, und klicken Sie anschließend auf **OK**.

     Eine Eingabeaufforderung wird geöffnet.

3. Geben Sie `ipconfig /all` ein.

     Die IP-Adressen für Ihre Netzwerkadapter werden angezeigt. Notieren Sie sich die IP-Adresse des Netzwerkadapters, an den Sie den Controller binden möchten.

### <a name="to-bind-a-test-controller-to-a-network-adapter"></a>So binden Sie einen Testcontroller an einen Netzwerkadapter

1. Beenden Sie den Testcontrollerdienst. Geben Sie in der Eingabeaufforderung `net stop vsttcontroller` ein.

2. Öffnen Sie die Datei *QTController.exe.config*. Diese Datei befindet sich im folgenden Verzeichnis: *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

3. Fügen Sie den Anwendungseinstellungen einen Eintrag für die `BindTo`-Eigenschaft hinzu. Geben Sie die IP-Adresse des Netzwerkadapters an, an den Sie den Controller binden möchten. Der Code sollte diesem ähneln:

    ```xml
    <appSettings>
        <add key="LogSizeLimitInMegs" value="20" />
        <add key="AgentSyncTimeoutInSeconds" value="120" />
        <add key="ControllerServicePort" value="6901" />
        <add key="ControllerUsersGroup" value="TeamTestControllerUsers" />
        <add key="ControllerAdminsGroup" value="TeamTestControllerAdmins" />
        <add key="CreateTraceListener" value="no" />
        <add key="BindTo" value="<YOUR IP ADDRESS>" />
    </appSettings>
    ```

4. Speichern Sie die Datei .

5. Starten Sie den Testcontrollerdienst. Geben Sie in der Eingabeaufforderung `net start vsttcontroller` ein.

### <a name="to-connect-a-test-agent-to-a-bound-controller"></a>So verbinden Sie einen Test-Agent mit einem gebundenen Controller

- Installieren Sie den Test-Agent erneut. Geben Sie dieses Mal die IP-Adresse des Testcontrollers anstelle des Namens des Testcontrollers an.

Dies gilt für den Testcontroller, den Test-Agent-Dienst und den Test-Agent-Prozess. Die `BindTo`-Eigenschaft muss für jeden Prozess festgelegt werden, der auf einem Computer mit mehr als einem Netzwerkadapter ausgeführt wird. Die Vorgehensweise zum Festlegen der `BindTo`-Eigenschaft entspricht für alle drei Prozesse der Vorgehensweise, die zuvor für den Testcontroller beschrieben wurde. Zum Festlegen der Protokollierungsebenen für den Test-Agent-Dienst und den Test-Agent-Prozess verwenden Sie die Konfigurationsdateien, die unter [Festlegen der Protokollierungsebene auf einem Testcontrollercomputer](#set-the-logging-level-on-a-test-controller-computer) aufgeführt sind.

## <a name="see-also"></a>Weitere Informationen

- [Testcontroller und Test-Agents](../test/configure-test-agents-and-controllers-for-load-tests.md)
