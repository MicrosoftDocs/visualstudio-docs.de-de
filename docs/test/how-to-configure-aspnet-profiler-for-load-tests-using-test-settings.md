---
title: Konfigurieren eines ASP.NET-Profilers für Auslastungstests
description: Lernen Sie, den Adapter für diagnostische Daten des ASP.NET-Profilers zu verwenden, um ASP.NET-Profilerinformationen zu sammeln.
ms.custom: SEO-VS-2020
ms.date: 10/13/2016
ms.topic: how-to
helpviewer_keywords:
- test settings, ASP.NET
ms.assetid: 6832fe39-04d5-4d94-8a18-3e2730bad423
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 6222d4ff9107a44c52846d2904668dab225e35a6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966772"
---
# <a name="how-to-configure-aspnet-profiler-for-load-tests-using-test-settings-in-visual-studio"></a>Vorgehensweise: Konfigurieren des ASP.NET-Profilers für Auslastungstests mit Testeinstellungen in Visual Studio

Sie können den Adapter für diagnostische Daten des ASP.NET-Profilers verwenden, um ASP.NET-Profilerinformationen zu sammeln. Dieser Adapter für diagnostische Daten erfasst Leistungsdaten für ASP.NET-Anwendungen.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Dieser Adapter für diagnostische Daten kann nicht für Tests verwendet werden, die mit Microsoft Test Manager ausgeführt werden (ab Visual Studio 2017 veraltet). Der Diagnoseadapter des ASP.NET-Profilers kann nur für Auslastungstests mit Websites verwendet werden, für die Visual Studio Enterprise erforderlich ist.

Mit dem Adapter für diagnostische Daten des ASP.NET-Profilers können ASP.NET-Profilerdaten auf der Logikschicht gesammelt werden, wenn Sie einen Auslastungstest ausführen. Der Profiler sollte nicht für lange Auslastungstests verwendet werden (z. B. für Auslastungstests von mehr als einer Stunde). Die Profilerdatei kann bei einem solchen Test Hunderte von Megabyte groß werden. Führen Sie stattdessen kürzere Auslastungstests mit dem ASP.NET-Profiler aus. Diese bieten ebenfalls den Vorteil einer umfassenden Diagnose von Leistungsproblemen.

> [!NOTE]
> Der Adapter für diagnostische Daten des ASP.NET-Profilers erstellt ein Profil des IIS-Prozesses (Internetinformationsdienste). Er funktioniert daher nicht für einen Entwicklungswebserver. Um ein Profil der Website im Auslastungstest zu erstellen, müssen Sie einen Test-Agent auf dem Computer installieren, auf dem IIS ausgeführt wird. Der Test-Agent generiert keine Auslastung, sondert dient nur zur Datensammlung. Weitere Informationen finden Sie unter [Installieren und Konfigurieren von Test-Agents](../test/lab-management/install-configure-test-agents.md).

Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen einer Testeinstellung für einen verteilten Auslastungstest](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md).

## <a name="configure-the-aspnet-profiler-for-your-test-settings"></a>Konfigurieren des ASP.NET-Profilers für die Testeinstellungen

Bevor Sie die Schritte in diesem Verfahren ausführen, müssen Sie die Testeinstellungen in Visual Studio und dann die Seite **Daten und Diagnose** öffnen.

1. Wählen Sie die Rolle aus, die zum Erfassen der ASP.NET-Profilerdaten verwendet werden soll.

    > [!WARNING]
    > Diese Rolle muss ein Webserver sein.

2. Wählen Sie **ASP.NET-Profiler** aus, um die Erfassung von ASP.NET-Profilerstellungsdaten zu aktivieren, und klicken Sie dann auf **Konfigurieren**.

     Das Dialogfeld zum Konfigurieren der Erfassung von ASP.NET-Profilerstellungsdaten wird angezeigt.

3. Geben Sie im Feld **Profilersamplingintervall** die Anzahl nicht angehaltener CPU-Uhrzyklen an, nach der das nächste ASP.NET-Profilerstellungssample erfasst werden soll.

4. Klicken Sie zum Aktivieren der Profilerstellung für Ebeneninteraktion auf **Profilerstellung für Ebeneninteraktion aktivieren**.

     Bei der Profilerstellung für die Ebeneninteraktion wird die Anzahl von Anforderungen, die für jedes Artefakt (z.B. *MyPage.aspx* oder *CompanyLogo.gif*) an den Webserver gesendet werden, und die zum Verarbeiten jeder Anforderung benötigte Zeit erfasst. Zudem werden bei der Profilerstellung für die Interaktion die im Rahmen der Seitenanforderung verwendeten ADO.NET-Verbindungen und die Anzahl von Abfragen und Aufrufen gespeicherter Prozeduren erfasst, die bei der Verarbeitung dieser Anforderung ausgeführt wurden.

     Es werden zwei unterschiedliche Sätze von Zeitsteuerungsinformationen erfasst:

    - Die Zeitsteuerungsinformationen ("Min.", "Max.", "Mittelwert" und "Gesamt") für die Verarbeitung jeder Webanforderung

    - Die Zeitsteuerungsinformationen ("Min.", "Max.", "Mittelwert" und "Gesamt") für die Ausführung jeder Abfrage

Mit dem in der Testeinstellung konfigurierten Adapter für diagnostische Daten des ASP.NET-Profilers können Sie jetzt ASP.NET-Profilerstellungsdaten für die ASP.NET-Webanwendung erfassen.

## <a name="see-also"></a>Siehe auch

- [Sammeln von Diagnoseinformationen mithilfe von Testeinstellungen](../test/collect-diagnostic-information-using-test-settings.md)
- [How to: Erstellen einer Testeinstellung für einen verteilten Auslastungstest](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md)
- [Testcontroller und Test-Agents](configure-test-agents-and-controllers-for-load-tests.md)