---
title: 'Gewusst wie: Sammeln von Leistungsdaten für eine Website | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
ms.assetid: a62d27fd-a966-4065-bebe-6874195a71fb
caps.latest.revision: 38
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3307b5372852d6f3e269264a02fa2c90cb1acd22
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840890"
---
# <a name="how-to-collect-performance-data-for-a-web-site"></a>Vorgehensweise: Sammeln von Leistungsdaten für eine Website
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können den **Leistungs-Assistenten** zum Sammeln von Leistungsdaten für eine [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Webanwendung verwenden. Sie können ein Profil einer Webanwendung erstellen, die in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]geöffnet ist, oder Sie können ein Profil einer [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] -Website erstellen, die sich auf dem lokalen Computer befindet und nicht in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE geöffnet ist.  
  
> [!NOTE]
> Der **Leistungs-Assistent** ermöglicht Ihnen das Hinzufügen von Ebeneninteraktionsdaten (TIP) und/oder JScript-Leistungsdaten zu den gesammelten Profilerstellungsdaten. Die Option TIP sammelt Daten von serverseitigen Prozessen. Die JScript-Profilerstellung sammelt Daten aus Skripts, die auf einer lokalen oder Remotewebsite ausgeführt werden. In den meisten Fällen sollten Sie nur eine der Optionen auswählen.  
  
 Je nach Benutzerzugriffsberechtigungs-Einstellungen, die ein Administrator zur Verfügung gestellt hat, kann ein einzelner Benutzer über die Sicherheitsberechtigung zur Erstellung einer Profilersitzung auf dem Computer verfügen, der den ASP.NET-Prozess hostet. Die folgenden Beispiele veranschaulichen mögliche Unterschiede zwischen Benutzern:  
  
- Einige Benutzer können auf erweiterte Profilerstellungsfeatures zugreifen, wenn der Administrator Treiber und Dienst gestartet hat.  
  
- Domänenbenutzer können nur auf Beispiel-Profilerstellung zugreifen.  
  
- Einige Benutzer können den Zugriff auf Profilerstellung für alle anderen Benutzer verweigern.  
  
  Weitere Informationen finden Sie unter [Profilerstellung und Windows Vista-Sicherheit](../profiling/profiling-and-windows-vista-security.md) sowie in den Admin-Optionen in [VSPerfCmd](../profiling/vsperfcmd.md).  
  
### <a name="to-profile-a-web-site-project"></a>Profilieren eines Websiteprojekts  
  
1. Öffnen Sie das [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Webprojekt in [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] oder [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)].  
  
2. Klicken Sie im Menü **Analyse** auf **Leistungs-Assistenten starten**.  
  
3. Auf der ersten Seite des Assistenten, wählen Sie eine Profilerstellungsmethode, und klicken Sie dann auf **Weiter**. Weitere Informationen zu Profilerstellungsmethoden finden Sie unter [Grundlagen zu Profilerstellungsmethoden](../profiling/understanding-performance-collection-methods.md). Beachten Sie, dass die Parallelitätsschnellansicht Profilerstellungsmethode nicht für Webanwendungen verfügbar ist.  
  
4. In der Dropdownliste **Welche Anwendung soll für die Profilerstellung als Ziel festgelegt werden?** stellen Sie sicher, dass das aktuelle Projekt ausgewählt ist, und klicken Sie dann auf **Weiter**.  
  
5. Sie können auf der dritten Seite des Assistenten die Profilerstellungsdaten für Ebeneninteraktion (TIP; tier interaction profiling), Daten aus JavaScript auf Webseiten oder beides hinzufügen.  
  
    - Wählen Sie das Kontrollkästchen **Profilerstellung für Ebeneninteraktion aktivieren** aus, um Ebeneninteraktionen zu erfassen.  
  
    - Wählen Sie zum Sammeln von Daten aus JavaScript auf Webseiten das Kontrollkästchen **Profilerstellung für JavaScript** aus.  
  
6. Klicken Sie auf **Weiter**.  
  
7. Klicken Sie auf der vierten Seite des Assistenten auf **Fertig stellen**.  
  
8. Eine Leistungssitzung wird für die [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] -Anwendung erstellt und die Website wird im Browser gestartet. Verwenden Sie die Funktionen, für die eine Profilerstellung erfolgen soll, und schließen Sie dann den Browser.  
  
     Der Profiler generiert die Datendatei und zeigt die Zusammenfassungsansicht der Daten im [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Hauptfenster.  
  
### <a name="to-profile-a-web-site-without-opening-a-project-in-visual-studio"></a>Profilieren einer Website ohne ein Projekt in Visual Studio zu öffnen  
  
1. Öffnen Sie [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] oder [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)].  
  
2. Klicken Sie im Menü **Analyse** auf **Leistungs-Assistenten starten**.  
  
3. Auf der ersten Seite des Assistenten, wählen Sie eine Profilerstellungsmethode, und klicken Sie dann auf **Weiter**. Weitere Informationen finden Sie unter [Grundlagen zu Profilerstellungsmethoden](../profiling/understanding-performance-collection-methods.md).  
  
4. Wählen Sie auf der zweiten Seite des Assistenten die Option **Profil einer ASP.NET- oder JavaScript-Anwendung erstellen** und klicken Sie dann auf **Weiter**.  
  
5. Geben Sie im Feld **Auf welcher URL oder welchem Pfad wird die Webanwendung ausgeführt?** auf der dritten Seite des Assistenten die URL der Startseite der Anwendung ein und klicken Sie dann auf **Weiter**.  
  
   - Geben Sie für eine serverbasierte (oder IIS-basierte) Website z. B. die URL **http://localhost/MySite/default.aspx** ein. Dies bewirkt, dass für die [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] -Anwendung auf dem lokalen Computer beim Anwendungsstamm von MySite ein Profil erstellt wird und die Seite default.aspx dieser Site im Internet Explorer geöffnet wird, um die Sitzung zu starten.  
  
   - Für eine dateibasierte Website geben Sie einen Pfad ein, zum Beispiel file///**c:\WebSites\MySite\default.aspx**. Dies bewirkt, dass von der [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Anwendung in „C:\webSites\MySite“ ein Profil erstellt wird und die Seite http://localhost:nnnn/MySite/default.aspx im Internet Explorer zu Beginn der Sitzung gestartet wird.  
  
   - Geben Sie für externe Websites, auf denen Sie JavaScript-Daten sammeln möchten, die URL ein, z \/ . b. http:/www.contoso.com.  
  
     Weitere Informationen finden Sie auf den Eigenschaftenseiten für eine [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] -Zielbinärdatei.  
  
6. Sie können auf der dritten Seite des Assistenten die Profilerstellungsdaten für Ebeneninteraktion (TIP; tier interaction profiling), Daten aus JavaScript auf Webseiten oder beides hinzufügen.  
  
   - Wählen Sie das Kontrollkästchen **Profilerstellung für Ebeneninteraktion aktivieren** aus, um Ebeneninteraktionen zu erfassen.  
  
   - Wählen Sie zum Sammeln von Daten aus JavaScript auf Webseiten das Kontrollkästchen **Profilerstellung für JavaScript** aus.  
  
7. Klicken Sie auf **Weiter**.  
  
8. Klicken Sie auf der vierten Seite des Assistenten auf **Fertig stellen**.  
  
9. Eine Leistungssitzung wird für die ASP.NET-Anwendung erstellt und die Website wird im Browser gestartet. Verwenden Sie die Funktionen, für die eine Profilerstellung erfolgen soll, und schließen Sie dann den Browser.  
  
     Der Profiler generiert die Datendatei und zeigt die Zusammenfassungsansicht der Daten im [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Hauptfenster.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersichten](../profiling/overviews-performance-tools.md)   
 [Konfigurieren von Leistungs Sitzungen](../profiling/configuring-performance-sessions.md)   
 [Grundlegendes zu Instrumentations Datenwerten](../profiling/understanding-instrumentation-data-values.md)   
 [Grundlegendes zu Stichprobendaten Werten](../profiling/understanding-sampling-data-values.md)
