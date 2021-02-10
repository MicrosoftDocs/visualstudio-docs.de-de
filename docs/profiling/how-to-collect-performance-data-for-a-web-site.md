---
title: Sammeln von Leistungsdaten für eine Website | Microsoft
description: Hier erfahren Sie, wie Sie den Leistungs-Assistenten zum Sammeln von Leistungsdaten für eine ASP.NET-Web-App verwenden. Diese App wird auf Ihrem lokalen Computer ausgeführt und kann in Visual Studio geöffnet sein.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vsperf.url.url
- vsperf.chooseurl
- vs.performance.wizard.asppage
- vsperf.url.ok
- vsperf.url.cancel
helpviewer_keywords:
- Profiling Tools,profiling ASP.NET
- web sites, performance profiling
- ASP.NET, performance profilng
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: a8e42522967b39c381e834ea93ccb1965aeb97fe
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886222"
---
# <a name="how-to-collect-performance-data-for-a-web-site"></a>Vorgehensweise: Sammeln von Leistungsdaten für eine Website

Sie können den **Leistungs-Assistenten** zum Sammeln von Leistungsdaten einer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Webanwendung verwenden. Sie können ein Profil einer Webanwendung erstellen, die in Visual Studio geöffnet ist, oder Sie können ein Profil einer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Website erstellen, die sich auf dem lokalen Computer befindet und nicht in der Visual Studio-IDE geöffnet ist.

> [!NOTE]
> Der **Leistungs-Assistent** ermöglicht Ihnen das Hinzufügen von Ebeneninteraktionsdaten (TIP) und/oder JScript-Leistungsdaten zu den gesammelten Profilerstellungsdaten. Die Option TIP sammelt Daten von serverseitigen Prozessen. Die JScript-Profilerstellung sammelt Daten aus Skripts, die auf einer lokalen oder Remotewebsite ausgeführt werden. In den meisten Fällen sollten Sie nur eine der Optionen auswählen.

 Je nach Benutzerzugriffsberechtigungs-Einstellungen, die ein Administrator zur Verfügung gestellt hat, kann ein einzelner Benutzer über die Sicherheitsberechtigung zur Erstellung einer Profilersitzung auf dem Computer verfügen, der den ASP.NET-Prozess hostet. Die folgenden Beispiele veranschaulichen mögliche Unterschiede zwischen Benutzern:

- Einige Benutzer könnten auf erweiterte Profilerstellungsfeatures zugreifen, wenn der Administrator Treiber und Dienst gestartet hat.

- Domänenbenutzer könnten nur auf Beispielprofilerstellung zugreifen.

- Einige Benutzer könnten den Zugriff auf Profilerstellung für alle anderen Benutzer verweigern.

  Weitere Informationen finden Sie unter [Profilerstellung und Sicherheit in Windows Vista](../profiling/profiling-and-windows-vista-security.md) und in den ADMIN-Optionen in [VSPerfCmd](../profiling/vsperfcmd.md).

## <a name="to-profile-a-web-site-project"></a>Profilerstellung für ein Websiteprojekt

1. Öffnen Sie das [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Webprojekt in Visual Studio.

2. Wählen Sie im Menü **Analysieren** **Leistungsprofiler**, wählen Sie **Leistungs-Explorer** und dann **Starten**.

3. Auf der ersten Seite des Assistenten, wählen Sie eine Profilerstellungsmethode, und klicken Sie dann auf **Weiter**. Weitere Informationen zu Profilerstellungsmethoden finden Sie unter [Grundlagen zu Profilerstellungsmethoden](../profiling/understanding-performance-collection-methods.md). Beachten Sie, dass die Parallelitätsschnellansicht Profilerstellungsmethode nicht für Webanwendungen verfügbar ist.

4. In der Dropdownliste **Welche Anwendung soll für die Profilerstellung als Ziel festgelegt werden?** stellen Sie sicher, dass das aktuelle Projekt ausgewählt ist, und klicken Sie dann auf **Weiter**.

5. Sie können auf der dritten Seite des Assistenten die Profilerstellungsdaten für Ebeneninteraktion (TIP; tier interaction profiling), Daten aus JavaScript auf Webseiten oder beides hinzufügen.

    - Wählen Sie das Kontrollkästchen **Profilerstellung für Ebeneninteraktion aktivieren** aus, um Ebeneninteraktionen zu erfassen.

    - Wählen Sie zum Sammeln von Daten aus JavaScript auf Webseiten das Kontrollkästchen **Profilerstellung für JavaScript** aus.

6. Klicken Sie auf **Weiter**.

7. Klicken Sie auf der vierten Seite des Assistenten auf **Fertig stellen**.

8. Eine Leistungssitzung wird für die [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] -Anwendung erstellt, und die Website wird im Browser gestartet. Verwenden Sie die Funktionen, für die eine Profilerstellung erfolgen soll, und schließen Sie dann den Browser.

     Der Profiler generiert die Datendatei und zeigt die Zusammenfassungsansicht der Daten im [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Hauptfenster.

## <a name="to-profile-a-web-site-without-opening-a-project-in-visual-studio"></a>Profilerstellung für eine Website ohne das Öffnen eines Projekts in Visual Studio

1. Öffnen Sie Visual Studio.

2. Wählen Sie im Menü **Analysieren** **Leistungsprofiler**, wählen Sie **Leistungs-Explorer** und dann **Starten**.

3. Auf der ersten Seite des Assistenten, wählen Sie eine Profilerstellungsmethode, und klicken Sie dann auf **Weiter**. Weitere Informationen finden Sie unter [Grundlagen zu Profilerstellungsmethoden](../profiling/understanding-performance-collection-methods.md).

4. Wählen Sie auf der zweiten Seite des Assistenten die Option **Profil einer ASP.NET- oder JavaScript-Anwendung erstellen** und klicken Sie dann auf **Weiter**.

5. Geben Sie im Feld **Auf welcher URL oder welchem Pfad wird die Webanwendung ausgeführt?** auf der dritten Seite des Assistenten die URL der Startseite der Anwendung ein und klicken Sie dann auf **Weiter**.

   - Geben Sie für eine serverbasierte (oder IIS-basierte) Website z. B. die URL **<`http://localhost/MySite/default.aspx`>** ein. Dies bewirkt, dass für die [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] -Anwendung auf dem lokalen Computer beim Anwendungsstamm von MySite ein Profil erstellt wird und die Seite default.aspx dieser Site im Internet Explorer geöffnet wird, um die Sitzung zu starten.

   - Für eine dateibasierte Website geben Sie einen Pfad ein, zum Beispiel file///**c:\WebSites\MySite\default.aspx**. Dies bewirkt, dass von der [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Anwendung in „C:\webSites\MySite“ ein Profil erstellt wird und die Seite `http://localhost:nnnn/MySite/default.aspx` im Internet Explorer zu Beginn der Sitzung gestartet wird.

   - Geben Sie die URL für externe Websites an, deren JavaScript-Daten gesammelt werden sollen (z.B. `http://www.contoso.com`).

     Weitere Informationen finden Sie auf den Eigenschaftenseiten für eine [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] -Zielbinärdatei.

6. Sie können auf der dritten Seite des Assistenten die Profilerstellungsdaten für Ebeneninteraktion (TIP; tier interaction profiling), Daten aus JavaScript auf Webseiten oder beides hinzufügen.

    - Wählen Sie das Kontrollkästchen **Profilerstellung für Ebeneninteraktion aktivieren** aus, um Ebeneninteraktionen zu erfassen.

    - Aktivieren Sie zum Sammeln von Daten aus JavaScript auf Webseiten das Kontrollkästchen **Profilerstellung für JavaScript**.

7. Klicken Sie auf **Weiter**.

8. Klicken Sie auf der vierten Seite des Assistenten auf **Fertig stellen**.

9. Eine Leistungssitzung wird für die ASP.NET-Anwendung erstellt, und die Website wird im Browser gestartet. Verwenden Sie die Funktionen, für die eine Profilerstellung erfolgen soll, und schließen Sie dann den Browser.

     Der Profiler generiert die Datendatei und zeigt die Zusammenfassungsansicht der Daten im [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Hauptfenster.

## <a name="see-also"></a>Siehe auch

[Übersichten (Leistungstools)](../profiling/overviews-performance-tools.md)
[Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)
[Grundlagen zu Instrumentierungsdatenwerten](../profiling/understanding-instrumentation-data-values.md)
[Grundlagen zu Samplingdatenwerten](../profiling/understanding-sampling-data-values.md)
