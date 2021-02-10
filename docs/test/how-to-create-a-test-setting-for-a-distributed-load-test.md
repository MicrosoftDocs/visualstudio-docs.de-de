---
title: Erstellen einer Testeinstellung für einen verteilten Auslastungstest
description: Lernen Sie, Testeinstellungen für Ihre Auslastungstests zu konfigurieren, sodass Sie diese Tests mithilfe von Test-Agents und Testcontrollern auf mehrere Computer verteilen können.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- test settings, for distributed load tests
ms.assetid: b63d4b71-3b74-4872-b2d1-f0bd1a9a8544
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 4ca0058d1f06e00941766ed1ecf6f81d73939a8c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877992"
---
# <a name="how-to-create-a-test-settings-file-for-a-distributed-load-test"></a>Vorgehensweise: Erstellen einer Testeinstellungsdatei für einen verteilten Auslastungstest

Konfigurieren Sie *Testeinstellungen* für Ihre Auslastungstests, sodass Sie diese Tests mithilfe von Test-Agents und Testcontrollern auf mehrere Computer verteilen können. Sie können zudem Testeinstellungen für die Verwendung von *Adaptern für diagnostische Daten* konfigurieren, die die Arten der zu sammelnden Daten angeben oder welche Auswirkung auf die Testcomputer erzielt wird, wenn Sie Ihre Auslastungstests in Visual Studio ausführen.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Sie können z. B. den Adapter für diagnostische Daten des ASP.NET-Profilers verwenden, um den Leistungsstrukturplan des Codes zu sammeln. Darüber hinaus können Diagnosedatenadapter verwendet werden, um auf dem Testcomputer potenzielle Engpässe zu simulieren oder den verfügbaren Systemspeicher zu reduzieren.

Die Testeinstellungen für Visual Studio werden in einer Datei gespeichert. Die Testeinstellungen definieren die folgenden Informationen über jede Rolle:

- den Satz von Rollen, der für die zu testende Anwendung erforderlich ist

- die für die Testausführung zu verwendende Rolle

- die für jede Rolle zu verwendenden Diagnosedatenadapter

Beim Ausführen der Tests wählen Sie die aktiven Testeinstellungen anhand der erforderlichen Elemente für diesen bestimmten Testlauf aus. Die Testeinstellungsdatei wird als Teil der Projektmappe gespeichert. Der Dateiname hat die Erweiterung *.testsettings*.

Wenn Sie einer Projektmappe ein Projekt für einen Webleistungs- und Auslastungstest hinzufügen, wird standardmäßig die Datei *Default.testsettings* erstellt. Die Datei wird der Projektmappe automatisch unter dem Ordner **Projektmappenelemente** hinzugefügt. Mit dieser Datei werden die Tests lokal ohne jegliche Adapter für diagnostische Daten ausgeführt. Sie können eine weitere *TESTSETTINGS-Datei* hinzufügen oder eine *TESTSETTINGS-Datei* bearbeiten, um Adapter für diagnostische Daten und Testcontroller anzugeben.

Der Testcontroller verfügt über Agents, die für die einzelnen Rollen in den Testeinstellungen verwendet werden können. Weitere Informationen zu Testcontrollern und Test-Agents finden Sie unter [Verwalten von Testcontrollern und Test-Agents mit Visual Studio](../test/manage-test-controllers-and-test-agents.md).

Befolgen Sie diese Schritte zum Erstellen und Entfernen von Testeinstellungen in Ihrer Lösung für Auslastungstests, die in Visual Studio gemäß dem Plan ausgeführt werden sollen.

## <a name="create-a-test-settings-file"></a>Erstellen einer Testeinstellungsdatei

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **Projektmappenelemente**, verweisen Sie auf **Hinzufügen**, und klicken Sie anschließend auf **Neues Element**.

     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.

2. Wählen Sie im Bereich **Installierte Vorlagen** die Option **Testeinstellungen** aus.

3. (Optional) Ändern Sie Im Feld **Name** den Namen der Testeinstellungsdatei.

4. Wählen Sie **Hinzufügen** aus.

     Die neue Testeinstellungsdatei wird im **Projektmappen-Explorer** unter dem Ordner **Projektmappenelemente** angezeigt.

5. Das Dialogfeld **Testeinstellungen** wird angezeigt. Die Seite **Allgemein** ist ausgewählt.

     Sie können die Testeinstellungswerte jetzt bearbeiten und speichern.

6. Geben Sie unter **Name** den Namen für die Testeinstellungen ein.

7. (Optional) Geben Sie unter **Beschreibung** eine Beschreibung für die Testeinstellung ein, damit andere Teammitglieder ihren Zweck erkennen können.

8. (Optional) Um das Standardnamensschema für die Testläufe auszuwählen, wählen Sie **Standardbenennungsschema** aus. Um ein eigenes Namensschema zu definieren, wählen Sie **Benutzerdefiniertes Schema** aus, und geben Sie dann den Text ein, der in **Präfixtext** angezeigt werden soll. Wenn Sie das Datum und den Zeitstempel an den Testlaufnamen anfügen möchten, wählen Sie **Datums-/Zeitstempel anfügen** aus.

9. Klicken Sie auf **Rollen**.

     Die Seite **Rollen** wird angezeigt.

     ![Testeinstellungsrolle](../test/media/load_testtestrole.png)

10. Um die Tests remote auszuführen oder um die Tests remote auszuführen und Daten remote zu sammeln, wählen Sie im Dropdownelement **Testausführungsmethode** die Option **Remoteausführung** aus.

11. Wählen Sie mit dem Dropdownelement **Controller** unter **Controller** einen Testcontroller für die Test-Agents aus, die verwendet werden, um die Tests auszuführen oder Daten zu sammeln.

    > [!NOTE]
    > Wenn Sie zum ersten Mal einen Controller hinzufügen, enthält die Dropdownliste keine Controller. Die Liste wird mit vorherigen Controllern aufgefüllt, die Sie in anderen Testeinstellungen angegeben haben. Sie müssen den Namen des Controllers im Feld eingeben (z.B. **TestControllerMachine1**).

12. Zum Hinzufügen der Rollen, mit denen Sie Tests ausführen und Daten sammeln möchten, klicken Sie unter **Rollen** auf **Hinzufügen**.

13. Geben Sie in der Spalte **Name** einen Namen für die Rolle ein. Die Rolle kann z. B. "Webserver" sein.

14. Wiederholen Sie die Schritte 12 und 13, um alle erforderlichen Rollen hinzuzufügen.

     Jede Rolle verwendet einen Test-Agent, der vom Testcontroller verwaltet wird.

15. Wählen Sie die Rolle aus, mit der Sie die Tests ausführen möchten, und klicken Sie auf **Als Rolle zum Ausführen von Tests festlegen**.

    > [!IMPORTANT]
    > Die anderen erstellten und definierten Rollen führen keine Tests aus, sondern werden nur für die Datenerfassung gemäß den für die Rollen auf der Seite **Daten und Diagnosen** angegebenen Datenadaptern und Adaptern für diagnostische Daten verwendet.

16. Wenn Sie die Agents einschränken möchten, die für eine Rolle verwendet werden können, wählen Sie die Rolle aus, und klicken Sie anschließend in der Symbolleiste unter **Agent-Attribute für ausgewählte Rolle** auf **Hinzufügen**.

     Das Dialogfeld **Agent-Auswahlregel** wird angezeigt.

     Geben Sie den Namen unter **Attributname** und den Wert unter **Attributwert ein**, und klicken Sie dann auf **OK**. Fügen Sie so viele Attribute hinzu, wie Sie benötigen.

     Sie können z. B. ein Attribut mit dem Namen "RAM > 16GB" hinzufügen, das über den Wert "True" oder "False" verfügt, um nach Test-Agent-Computern mit mehr als 16 GB Arbeitsspeicher zu filtern. Wenden Sie mithilfe des Dialogfelds **Testcontroller verwalten** dasselbe Attribut auf mehrere Test-Agents an. Weitere Informationen finden Sie unter [Verwalten von Testcontrollern und Test-Agents mit Visual Studio](../test/manage-test-controllers-and-test-agents.md).

17. Klicken Sie auf **Daten und Diagnose**.

     Die Seite **Daten und Diagnose** wird angezeigt.

     ![Testeinstellungsdaten und -diagnose](../test/media/load_testtest.png)

18. Auf der Seite **Daten und Diagnosen** definieren Sie, was die Rolle bewirkt, indem Sie die von der Rolle für die Datensammlung verwendeten *Adapter für diagnostische Daten* auswählen. Wenn mindestens ein Adapter für diagnostische Daten oder Datenadapter für die Rolle aktiviert ist, wird vom Testcontroller daher ein verfügbarer Test-Agent-Computer zur Datenerfassung für die angegebenen Datenadapter und Adapter für diagnostische Daten basierend auf den für die Rolle festgelegten Attributen ausgewählt. Zur Auswahl der Datenadapter und Adapter für diagnostische Daten, die Sie für jede Rolle sammeln möchten, wählen Sie die Rolle aus. Wählen Sie für jede Rolle die Adapter für diagnostische Daten gemäß den Anforderungen der Tests aus. Klicken Sie Konfiguration der einzelnen Diagnosedatenadapter, die Sie für jede Rolle ausgewählt haben, auf **Konfigurieren**.

     **Beispiel für Rollen und Adapter für diagnostische Daten:**

     Sie können z. B. eine Clientrolle mit dem Namen "Desktopclient" erstellen, deren Attribut "Verwendet SQL" auf "True" festgelegt ist, sowie eine Serverrolle mit dem Namen "SQL Server", die über ein auf "RAM > 16GB" festgelegtes Attribut verfügt. Wenn Sie durch Auswahl von **Als Rolle zum Ausführen von Tests festlegen** auf der Seite **Rollen** angeben, dass die Tests von „Desktopclient“ ausgeführt werden, werden vom Testcontroller Computer mit Test-Agents ausgewählt, die das auf TRUE festgelegte Attribut „Verwendet SQL“ enthalten, um auf diesen die Tests auszuführen. Der Testcontroller wählt auch SQL Server-Computer mit Test-Agents aus, die nur das Attribut "RAM > 16GB" enthalten, um Daten anhand der in der Rolle enthaltenen Datenadapter und Adapter für diagnostische Daten zu erfassen. Der Test-Agent "Desktopclient" kann außerdem Daten für die Computer sammeln, auf denen er ausgeführt wird, wenn Sie auch für diese Rolle Datenadapter und Adapter für diagnostische Daten auswählen.

     Ausführliche Informationen zu den einzelnen Diagnosedatenadaptern und deren Konfiguration finden Sie im entsprechenden Thema in der folgenden Tabelle.

     Weitere Informationen zu Adaptern für diagnostische Daten finden Sie unter [Erfassen von Diagnoseinformationen mithilfe von Testeinstellungen](../test/collect-diagnostic-information-using-test-settings.md).

     **Adapter für diagnostische Daten für Auslastungstests**

    |Diagnosedatenadapter|Verwendung in Auslastungstests|Entsprechendes Thema|
    |-|-------------------------|-|
    |**ASP.NET-Clientproxy für IntelliTrace und Testauswirkung:** Mit diesem Proxy können Sie Informationen zu HTTP-Aufrufen von einem Client an einen Webserver für die IntelliTrace- und Testauswirkungsadapter für diagnostische Daten erfassen.|![Informationssymbol](../test/media/vc364f4.gif)<br /><br /> Schließen Sie diesen Adapter nur ein, wenn Sie Systeminformationen für die Test-Agent-Computer sammeln müssen. **Vorsicht:** Es wird davon abgeraten, den IntelliTrace-Adapter in Auslastungstests zu verwenden, da aufgrund der großen gesammelten Datenmenge Probleme auftreten. <br /><br /> Bei Verwendung von Auslastungstests werden keine Testauswirkungsdaten erfasst.||
    |**IntelliTrace:** Sie können konfigurieren, welche speziellen Informationen zur Diagnoseablaufverfolgung in einer Protokolldatei gespeichert werden. Eine Protokolldatei hat die Erweiterung *TDLOG*. Wenn Sie den Test ausführen und ein Testschritt fehlschlägt, können Sie einen Fehler erstellen. Die Protokolldatei, die die Diagnoseablaufverfolgung enthält, wird automatisch an diesen Fehler angefügt. Die in der Protokolldatei gesammelten Daten steigern die Debuggingproduktivität, da sie die Zeit für das Reproduzieren und Diagnostizieren eines Fehlers im Code verkürzen. Aus dieser Protokolldatei kann die lokale Sitzung auf einem anderen Computer erneut erstellt werden. So wird die Wahrscheinlichkeit verringert, dass ein Fehler nicht reproduziert werden kann.<br /><br /> Weitere Informationen finden Sie unter [Erfassen von IntelliTrace-Daten](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md).|![Symbol "Wichtig"](../test/media/vc364f3.gif)<br /><br /> Es wird davon abgeraten, den IntelliTrace-Adapter in Auslastungstests zu verwenden, da aufgrund der großen gesammelten und protokollierten Datenmenge Probleme auftreten. Sie sollten versuchen, den IntelliTrace-Adapter nur in kurzen Auslastungstests zu verwenden, in denen wenige Test-Agents verwendet werden.|[Vorgehensweise: Erfassen von IntelliTrace-Daten zum Beheben schwieriger Probleme](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)|
    |**ASP.NET-Profiler:** Sie können eine Testeinstellung erstellen, die die ASP.NET-Profilerstellung umfasst, und so Leistungsdaten zu ASP.NET-Webanwendungen sammeln.|Der Adapter für diagnostische Daten des ASP.NET-Profilers erstellt ein Profil des IIS-Prozesses (Internet Information Services). Daher kann er nicht für Entwicklungswebserver verwendet werden. Um ein Profil der Website im Auslastungstest zu erstellen, müssen Sie einen Test-Agent auf dem Computer installieren, auf dem IIS ausgeführt wird. Der Test-Agent generiert keine Auslastung, sondert dient nur als Datensammlungs-Agent. Weitere Informationen finden Sie unter [Installieren und Konfigurieren von Test-Agents](../test/lab-management/install-configure-test-agents.md).|[Vorgehensweise: Konfigurieren des ASP.NET-Profilers für Auslastungstests mit Testeinstellungen](../test/how-to-configure-aspnet-profiler-for-load-tests-using-test-settings.md)|
    |**Ereignisprotokoll**: Sie können eine Testeinstellung konfigurieren, um das Ereignisprotokoll zu erfassen und in die Testergebnisse aufzunehmen.||[Vorgehensweise: How to: Configure Event Log Collection Using Test Settings (Vorgehensweise: Konfigurieren der Ereignisprotokollerfassung mithilfe von Testeinstellungen)](/previous-versions/dd504816(v=vs.110))|
    |**Netzwerkemulation:** Sie können mit einer Testeinstellung angeben, dass Sie eine künstliche Netzwerklast auf den Test anwenden möchten. Die Netzwerkemulation wirkt sich auf die Kommunikation vom und zum Computer aus, indem eine bestimmte Netzwerkverbindungsgeschwindigkeit, z. B. DFÜ, emuliert wird. **Hinweis**:  Die Netzwerkemulation kann nicht verwendet werden, um die Netzwerkverbindungsgeschwindigkeit zu erhöhen.|Der Netzwerkemulationsadapter wird von Auslastungstests ignoriert. Stattdessen verwenden Auslastungstests die Einstellungen, die in der Netzwerkmischung des Auslastungstestszenarios angegeben sind.<br /><br /> Weitere Informationen finden Sie unter [Angeben von virtuellen Netzwerktypen](../test/specify-virtual-network-types-in-a-load-test-scenario.md).||
    |**Systeminformationen:** Eine Testeinstellung kann so eingerichtet werden, dass sie die Systeminformationen zu den Computern einschließt, auf denen die Systeminformationsdiagnose und der Datensammler ausgeführt werden. Die Systeminformationen werden in den Testergebnissen mit einer Testeinstellung angegeben.|![Informationssymbol](../test/media/vc364f4.gif)<br /><br /> Sie können Systeminformationen sowohl für die Auslastungs-Agents als auch für das getestete System sammeln.|Zur Erfassung dieser Informationen ist keine Konfiguration erforderlich.|
    |**Testauswirkungen:** Sie können Informationen zu den Methoden des Anwendungscodes erfassen, die beim Ausführen eines Testfalls verwendet wurden. Diese können zusammen mit von Entwicklern am Anwendungscode vorgenommenen Änderungen verwendet werden, um zu ermitteln, auf welche Tests sich diese Entwicklungsänderungen ausgewirkt haben.|Bei Auslastungstests werden keine Testauswirkungsdaten erfasst.||
    |**Videorekorder:** Sie können beim Ausführen eines automatisierten Tests eine Videoaufzeichnung der Desktopsitzung erstellen. Dies kann nützlich sein, um die Benutzeraktionen für einen Test der codierten UI zu sehen. Das Video kann anderen Teammitgliedern helfen, Anwendungsprobleme zu isolieren, die schwer reproduzierbar sind. **Hinweis:** Bei der Remoteausführung von Tests funktioniert die Videoaufzeichnung nicht, wenn der Agent nicht im interaktiven Prozessmodus ausgeführt wird.|![Symbol „Wichtig“](../test/media/vc364f3.gif) **Warnung:** Es wird davon abgeraten, den Videoaufzeichnungsadapter für Auslastungstests zu verwenden.|[Vorgehensweise: Einschließen von Bildschirm- und Stimmenaufzeichnungen während der Tests mit Testeinstellungen](../test/how-to-include-recordings-of-the-screen-and-voice-during-tests.md)|

19. Klicken Sie auf **Bereitstellung**.

     Die Seite **Bereitstellung** wird angezeigt.

20. Wenn bei jeder Testausführung ein separates Verzeichnis für die Bereitstellung erstellt werden soll, klicken Sie auf **Bereitstellung aktivieren**.

    > [!NOTE]
    > In diesem Fall können Sie weiterhin an der Erstellung der Anwendung arbeiten, während die Tests ausgeführt werden.

21. Um dem Verzeichnis zum Ausführen der Tests eine Datei hinzuzufügen, klicken Sie auf **Datei hinzufügen**, und wählen Sie dann die Datei aus, die Sie hinzufügen möchten.

    > [!NOTE]
    > Wenn Sie Auslastungstests ausführen, werden Plug-In-Assemblys, Datendateien und hochgeladene Dateien automatisch bereitgestellt.

22. Um dem Verzeichnis zum Ausführen der Tests ein Verzeichnis hinzuzufügen, klicken Sie auf **Verzeichnis hinzufügen**, und wählen Sie dann das Verzeichnis aus, das Sie hinzufügen möchten.

23. Um vor und nach dem Ausführen von Tests Skripts auszuführen, klicken Sie auf **Setup- und Bereinigungsskripts**.

     Die Seite **Setup- und Bereinigungsskripts** wird angezeigt.

    1. Geben Sie den Speicherort der Skriptdatei unter **Setupskript** ein, oder klicken Sie auf die Auslassungspunkte (**…**), um das Setupskript zu suchen.

    2. Geben Sie den Speicherort der Skriptdatei unter **Bereinigungsskript** ein, oder klicken Sie auf die Auslassungspunkte (**…**), um das Bereinigungsskript zu suchen.

24. Um die Tests mithilfe eines anderen Hosts auszuführen, klicken Sie auf **Hosts**.

    1. Stellen Sie sicher, dass unter **Hosttyp** die Option **Standard** ausgewählt ist.

        > [!NOTE]
        > Die Option **ASP.NET** für **Hosttyp** wird in Auslastungstests nicht unterstützt.

    2. Wählen Sie mithilfe der Option **Tests als 32-Bit- oder 64-Bit-Prozess ausführen** aus, ob Sie die Webleistungs- und Komponententests in den Auslastungstests als 32-Bit- oder 64-Bit-Prozesse ausführen möchten.

        > [!NOTE]
        > Maximale Flexibilität erhalten Sie, wenn Sie die Projekte für einen Webleistungs- und Auslastungstest mit der Konfiguration **Beliebige CPU** kompilieren. Die Ausführung ist dann sowohl auf 32- als auch auf 64-Bit-Agents möglich. Das Kompilieren von Projekten für einen Webleistungs- und Auslastungstest mit der **64-Bit-Konfiguration** bietet keinen Vorteil.

25. (Optional) Zur Begrenzung der Dauer jedes Testlaufs und der einzelnen Tests wählen Sie **Test-Timeouts** aus.

    1. Um einen Testlauf bei Überschreitung eines Zeitlimits abzubrechen, wählen Sie **Testlauf abbrechen, wenn die gesamte Zeitdauer folgenden Wert überschreitet** aus und geben einen Wert für die Zeitdauer ein.

    2. Wenn ein einzelner Test bei Überschreitung eines Zeitlimits fehlschlagen soll, wählen Sie **Einzelnen Test als gescheitert markieren, wenn die Ausführungszeit folgenden Wert überschreitet** aus und geben einen Wert für diese Zeitdauer ein.

26. Überspringen Sie **Komponententest**. Diese Einstellungen werden von Auslastungstests nicht verwendet.

27. Überspringen Sie **Webtest**. Diese Einstellungen werden von Auslastungstests nicht verwendet.

28. Klicken Sie zum Speichern der Testeinstellungen auf **Speichern unter**. Geben Sie unter **Objektname** den gewünschten Namen für die Datei ein.

## <a name="remove-a-test-settings-file-from-your-solution"></a>Entfernen einer Testeinstellungsdatei aus der Projektmappe

Klicken Sie im Ordner **Projektmappenelemente** im **Projektmappen-Explorer** mit der rechten Maustaste auf die zu entfernenden Testeinstellungen, und wählen Sie anschließend **Entfernen** aus.

Die Testeinstellungsdatei wird aus der Projektmappe entfernt.

## <a name="see-also"></a>Weitere Informationen

- [Testcontroller und Test-Agents](configure-test-agents-and-controllers-for-load-tests.md)
- [Sammeln von Diagnoseinformationen mithilfe von Testeinstellungen](../test/collect-diagnostic-information-using-test-settings.md)