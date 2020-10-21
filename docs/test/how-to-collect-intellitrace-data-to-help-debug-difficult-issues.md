---
title: IntelliTrace-Daten
ms.date: 10/13/2016
ms.topic: how-to
helpviewer_keywords:
- IntelliTrace, configuring test settings
- Diagnostic Data Adapter, InteliTrace
- debugging [Visual Studio ALM], difficult issues using IntelliTrace
- Test Runner, InteliTrace
ms.assetid: 02b6716f-569e-4961-938a-e790a0c74b5c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9da0000397042355387d21501c64c29806ddeaaa
ms.sourcegitcommit: 754133c68ad841f7d7962e0b7a575e133289d8a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91928514"
---
# <a name="how-to-collect-intellitrace-data-to-help-debug-difficult-issues"></a>Vorgehensweise: Erfassen von IntelliTrace-Daten zum Beheben schwieriger Probleme

Sie können den Adapter für diagnostische Daten für IntelliTrace konfigurieren, um bestimmte Informationen der Diagnoseablaufverfolgung in Visual Studio zu erfassen. Dieser Adapter kann für Tests verwendet werden. Während des Tests können signifikante Diagnoseereignisse für die Anwendung gesammelt werden, die ein Entwickler später verwenden kann, um die Ursache eines Fehlers im Code zu finden. Der Adapter für diagnostische Daten für IntelliTrace kann mit manuellen oder automatisierten Tests verwendet werden.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> IntelliTrace kann nur in einer mit verwaltetem Code geschriebenen Anwendung verwendet werden. Beim Testen einer Webanwendung, die einen Browser als Client verwendet, sollten Sie in den Testeinstellungen für den Client nicht IntelliTrace aktivieren, da kein verwalteter Code für die Ablaufverfolgung verfügbar ist. In diesem Fall können Sie eine Umgebung einrichten und IntelliTrace-Daten remote auf dem Webserver sammeln.

Die IntelliTrace-Daten werden in einer Datei mit der Erweiterung *.iTrace* gespeichert. Wenn Sie den Test ausführen und ein Testschritt fehlschlägt, können Sie einen Fehler erstellen. Die IntelliTrace-Datei mit den Diagnoseinformationen wird automatisch an diesen Fehler angefügt.

> [!NOTE]
> Der Adapter für diagnostische Daten für IntelliTrace erstellt bei einer erfolgreichen Testübergabe keine IntelliTrace-Datei. Eine Datei wird nur bei einem Testfall mit Fehler oder beim Senden eines Fehlers gespeichert.

Die in der IntelliTrace-Datei gesammelten Daten können zur Erhöhung der Debugproduktivität beitragen, da die Zeit zum Reproduzieren und Diagnostizieren eines Fehlers im Code verkürzt wird. Da Sie die IntelliTrace-Datei für eine andere Person freigeben können, die die lokale Sitzung auf ihrem Computer replizieren kann, wird darüber hinaus die Wahrscheinlichkeit gemindert, dass ein Fehler nicht reproduziert werden kann.

> [!NOTE]
> Wenn Sie IntelliTrace in den Testeinstellungen aktivieren, ist das Sammeln von Codeabdeckungsdaten nicht möglich.

> [!WARNING]
> Die Funktionsweise des Adapters für diagnostische Daten besteht in der Instrumentierung eines verwalteten Prozesses, der nach dem Laden des ersten Tests für den Testlauf ausgeführt werden muss. Wenn der zu überwachende Prozess bereits gestartet wurde, werden keine IntelliTrace-Dateien gesammelt, da der Prozess bereits ausgeführt wird. Stellen Sie zur Vermeidung dieses Problems sicher, dass der Prozess beendet wird, bevor die Tests geladen werden. Starten Sie dann den Prozess nach dem Laden der Tests oder dem Starten des ersten Tests.

::: moniker range="vs-2017"
In der folgenden Prozedur ist beschrieben, wie Sie die zu sammelnden IntelliTrace-Daten konfigurieren. Diese Schritte gelten für den Konfigurations-Editor in Microsoft Test Manager und das Dialogfeld „Testeinstellungen“ in Visual Studio.
::: moniker-end
::: moniker range=">=vs-2019"
In der folgenden Prozedur ist beschrieben, wie Sie die zu sammelnden IntelliTrace-Daten konfigurieren. Diese Schritte gelten für das Dialogfeld „Testeinstellungen“ in Visual Studio.
::: moniker-end

> [!NOTE]
> Das Benutzerkonto für den Test-Agent, mit dem IntelliTrace-Daten gesammelt werden, muss Mitglied der Administratorgruppe sein. Weitere Informationen finden Sie unter [Installieren und Konfigurieren von Test-Agents](../test/lab-management/install-configure-test-agents.md).

## <a name="configure-the-data-to-collect-with-the-intellitrace-diagnostic-data-adapter"></a>Konfigurieren der zu sammelnden Daten mit dem IntelliTrace-Adapter für diagnostische Daten

::: moniker range="vs-2017"
Bevor Sie die Schritte in diesem Verfahren ausführen, müssen Sie die Testeinstellungen in Microsoft Test Manager oder Visual Studio öffnen und die Seite **Daten und Diagnose** auswählen.
::: moniker-end
::: moniker range=">=vs-2019"
Bevor Sie die Schritte in diesem Verfahren ausführen, müssen Sie die Testeinstellungen in Visual Studio und dann die Seite **Daten und Diagnose** öffnen.
::: moniker-end

### <a name="to-configure-the-data-to-collect-with-the-intellitrace-diagnostic-data-adapter"></a>So konfigurieren Sie die zu sammelnden Daten mit dem IntelliTrace-Adapter für diagnostische Daten

1. Wählen Sie die Rolle aus, die zum Sammeln von IntelliTrace-Daten verwendet werden soll.

2. Wählen Sie **IntelliTrace** aus.

3. Wenn Sie IntelliTrace für eine Webclientrolle oder für eine ASP.NET-Webanwendung hinzufügen, müssen Sie auch **ASP.NET-Clientproxy für IntelliTrace und Testauswirkung** auswählen.

     Dieser Proxy ermöglicht das Erfassen von Informationen zu HTTP-Aufrufen von einem Client an einen Webserver für die IntelliTrace- und Testauswirkungsadapter für diagnostische Daten.

    > [!WARNING]
    > Wenn Sie ein benutzerdefiniertes Konto für die Identität verwenden möchten, die für den Anwendungspool auf dem Internet Information Server (IIS) verwendet wird, mit dem Sie IntelliTrace-Daten sammeln möchten, müssen Sie das lokale Benutzerprofil auf dem IIS-Computer mit dem verwendeten benutzerdefinierten Konto erstellen. Sie können das lokale Profil für das benutzerdefinierte Konto entweder durch die einmalige lokale Anmeldung am IIS-Computer oder durch Ausführung der folgenden Befehlszeile unter Verwendung der Anmeldeinformationen des benutzerdefinierten Kontos erstellen:
    >
    > **runas /user:domain\name /profile cmd.exe**

4. Wählen Sie **Konfigurieren** für **IntelliTrace** aus, um die standardmäßigen IntelliTrace-Einstellungen zu ändern.

     Das Dialogfeld zum Konfigurieren der zu sammelnden Daten wird angezeigt.

    > [!WARNING]
    > Wenn Sie das Sammeln von IntelliTrace-Daten aktivieren, können keine Codeabdeckungsdaten gesammelt werden.

5. Wählen Sie die Registerkarte **Allgemein** aus. Wählen Sie **Nur IntelliTrace-Ereignisse** aus, um beim Testen signifikante Diagnoseereignisse mit minimalen Auswirkungen auf die Leistung aufzuzeichnen.

     - oder -

     Wählen Sie **IntelliTrace events and call information** (IntelliTrace-Ereignisse und Aufrufinformationen) aus, um Diagnoseereignisse und die Ablaufverfolgung auf Methodenebene unter Anzeige von Aufrufinformationen aufzuzeichnen. Diese Ebene der Ablaufverfolgung kann sich beim Ausführen der Tests auf die Leistung auswirken.

6. Wenn Sie Daten aus der ASP.NET-Anwendung sammeln möchten, die für Internetinformationsdienste ausgeführt wird, aktivieren Sie die Option **Collect data from ASP.NET applications that are running on Internet Information Services** (Daten von ASP.NET-Anwendungen sammeln, die auf Internetinformationsdiensten ausgeführt werden). Installieren und konfigurieren Sie den Test-Agent auf der Webserverrolle. Informationen finden Sie unter [Installieren und Konfigurieren von Test-Agents](../test/lab-management/install-configure-test-agents.md).

7. Wählen Sie die Registerkarte **Module** aus. Wählen Sie entweder **Collect data from all modules except for the following** (Daten aus allen Modulen mit Ausnahme der folgenden auflisten) aus, und fügen Sie der Liste der Module ein Modul mit der Option **Hinzufügen** hinzu, oder entfernen Sie ein Modul mit der Option **Entfernen**. Mit dieser Option können Sie alle im System ausgeführten Module einschließen, mit Ausnahme der von Ihnen angegebenen Module.

     - oder -

     Wählen Sie **Collect data from only the following modules** (Daten nur aus den folgenden Modulen auflisten) aus, und fügen Sie der Liste der Module ein Modul mit **Hinzufügen** hinzu, oder entfernen Sie ein Modul mit **Entfernen**. Mit dieser Option können Sie die gewünschten Module genau angeben.

    > [!NOTE]
    > Wählen Sie nach Möglichkeit die bestimmten Prozesse aus, die Sie überwachen möchten. Dies wird für eine optimale Leistung empfohlen.

8. Wählen Sie die Registerkarte **Prozesse** aus. Wählen Sie **Collect data from all processes except for the following** (Daten von allen Prozessen mit Ausnahme der folgenden sammeln) aus, und fügen Sie der Liste der Prozesse einen Prozess mit **Hinzufügen** hinzu, oder entfernen Sie einen Prozess mit **Entfernen**. Mit dieser Option können Sie alle im System ausgeführten Prozesse einschließen, mit Ausnahme der von Ihnen angegebenen Prozesse.

     - oder -

     Wählen Sie **Nur Daten von den angegebenen Prozessen sammeln** aus, und fügen Sie der Liste der Prozesse mit **Hinzufügen** einen Prozess hinzu, oder entfernen Sie einen Prozess mit **Entfernen**. Mit dieser Option können Sie die gewünschten Prozesse genau angeben.

9. Wählen Sie die Registerkarte **IntelliTrace-Ereignisse** aus (optional). Wählen Sie die einzelnen IntelliTrace-Ereigniskategorien aus, die Sie beim Sammeln von Diagnoseereignissen ein- oder ausschließen möchten, bzw. heben Sie die Auswahl auf.

10. (Optional) Erweitern Sie die einzelnen IntelliTrace-Ereigniskategorien, und wählen Sie jedes Ereignis aus, das Sie in die IntelliTrace-Ereignisse einschließen bzw. davon ausschließen möchten, bzw. heben Sie die Auswahl auf.

11. Wählen Sie die Registerkarte **Erweitert** aus (optional). Klicken Sie dann auf den Pfeil neben **Maximum amount of disk space for recording** (Maximaler Speicherplatz pro Aufzeichnung), und wählen Sie die maximale Größe für die IntelliTrace-Datei aus.

    > [!NOTE]
    > Wenn Sie die Größe der Aufzeichnung erhöhen, könnte ein Timeoutproblem auftreten, wenn Sie diese Aufzeichnung zusammen mit den Testergebnissen speichern.

12. Klicken Sie auf **Speichern**, wenn Sie Microsoft Test Manager verwenden (ab Visual Studio 2017 veraltet). Wenn Sie Visual Studio verwenden, klicken Sie auf **OK**. Die IntelliTrace-Einstellungen werden jetzt konfiguriert und für die Testeinstellungen gespeichert.

    ::: moniker range="vs-2017"
    > [!NOTE]
    > Zum Zurücksetzen der Konfiguration dieses Adapters für diagnostische Daten, wählen Sie **Auf Standardkonfiguration zurücksetzen** für Visual Studio oder **Standard wiederherstellen** für Microsoft Test Manager aus.
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    > [!NOTE]
    > Klicken Sie in Visual Studio auf **Auf Standardkonfiguration zurücksetzen**, um die Konfiguration für diesen Adapter für diagnostische Daten zurückzusetzen.
    ::: moniker-end

## <a name="see-also"></a>Siehe auch

- [Collect diagnostic data while testing (Azure Test Plans) (Sammeln von Diagnosedaten beim Testen (Azure Test Plans))](/azure/devops/test/collect-diagnostic-data?view=vsts&preserve-view=true)
- [Collect diagnostic data in manual tests (Azure Test Plans) (Sammeln von Diagnosedaten in manuellen Tests (Azure Test Plans))](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts&preserve-view=true)
- [Sammeln von Diagnoseinformationen mithilfe von Testeinstellungen](../test/collect-diagnostic-information-using-test-settings.md)
- [Erfassen von IntelliTrace-Daten](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)
