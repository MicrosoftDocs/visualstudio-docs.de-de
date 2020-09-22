---
title: 'Exemplarische Vorgehensweise: Profilerstellung über die Befehlszeile mit Sampling | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
- performance tools, command-line tools
ms.assetid: 1d53972f-6f35-4842-8c74-1b627f18c70a
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 96dfe49ce4e174680202cd60c3e8bca83cfbf575
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841181"
---
# <a name="walkthrough-command-line-profiling-using-sampling"></a>Exemplarische Vorgehensweise: Profilerstellung über die Befehlszeile mit Sampling
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese exemplarische Vorgehensweise veranschaulicht, wie mithilfe von Befehlszeilentools und Sampling eine Profilerstellung einer Anwendung ausgeführt wird, um Leistungsprobleme zu identifizieren.  
  
 In dieser exemplarischen Vorgehensweise werden Sie Schritt für Schritt durch den Vorgang der Profilerstellung einer verwalteten Anwendung mithilfe von Befehlszeilentools geleitet, wobei mithilfe von Sampling Leistungsprobleme in der Anwendung isoliert und identifiziert werden.  
  
 Im Verlauf dieser exemplarischen Vorgehensweise führen Sie die folgenden Schritte aus:  
  
- Profilerstellung einer Anwendung mithilfe von Befehlszeilentools und Sampling  
  
- Analysieren der Ergebnisse der Profilerstellung, für die ein Sampling durchgeführt wurde, um Leistungsprobleme zu lokalisieren und zu beheben  
  
## <a name="prerequisites"></a>Voraussetzungen  
  
- [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]oder [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
- Grundlegende Kenntnisse über [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)]  
  
- Grundlegende Kenntnisse über die Arbeit mit Befehlszeilentools  
  
- Eine Kopie von [PeopleTrax-Beispiel](../profiling/peopletrax-sample-profiling-tools.md)  
  
- Um mit den durch die Profilerstellung bereitgestellten Informationen arbeiten zu können, sollten Symbolinformationen für das Debuggen verfügbar sein.  
  
## <a name="command-line-profiling-using-the-sampling-method"></a>Profilerstellung über die Befehlszeile mit der Samplingmethode  
 Das Sampling ist eine Methode der Profilerstellung, bei der ein bestimmter Prozess periodisch zum Bestimmen der aktiven Funktion überprüft wird. Die resultierenden Daten enthalten Angaben dazu, wie häufig die Funktion sich während des Samplings des Prozesses in der Aufrufliste ganz oben befunden hat.  
  
> [!NOTE]
> Die Befehlszeilentools der Profilerstellungstools befinden sich im Unterverzeichnis "\Team Tools\Performance Tools" des Visual Studio-Installationsverzeichnisses. Auf 64-Bit-Computern sind 64-Bit- und 32-Bit-Versionen der Tools verfügbar. Damit Sie die Profilerbefehlszeilentools verwenden können, müssen Sie den Pfad der PATH-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen. Weitere Informationen finden Sie unter [Angeben des Pfads zu Tools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). PeopleTrax ist eine 32-Bit-Anwendung.  
  
#### <a name="to-profile-the-peopletrax-application-by-using-the-sampling-method"></a>So erstellen Sie ein Profil für die Anwendung "PeopleTrax" mithilfe der Samplingmethode  
  
1. Installieren Sie die Beispielanwendung "PeopleTrax", und erstellen Sie die Releaseversion der Anwendung.  
  
2. Öffnen Sie ein Eingabeaufforderungsfenster, und fügen Sie der lokalen Path-Umgebungsvariablen das Verzeichnis "Profilerstellungstools" hinzu.  
  
3. Legen Sie das Arbeitsverzeichnis auf das Verzeichnis fest, das die Binärdateien für "PeopleTrax" enthält.  
  
4. Geben Sie den folgenden Befehl ein, um die entsprechenden Umgebungsvariablen festzulegen:  
  
    ```  
    VSPerfCLREnv /sampleon  
    ```  
  
5. Starten Sie die Profilerstellung, indem Sie VSPerfCmd.exe ausführen. Dies ist das Befehlszeilentool, das den Profiler steuert. Mit dem folgenden Befehl werden Anwendung und Profiler im Samplingmodus gestartet:  
  
    ```  
    VsPerfCmd /start:sample /output:PeopleTraxReport.vsp /launch:PeopleTrax.exe  
    ```  
  
     Der Profilerprozess startet und wird an den PeopleTrax.exe-Prozess angefügt. Der Profilerprozess beginnt, die erfassten Profilerstellungsdaten in die Berichtsdatei zu schreiben.  
  
6. Klicken Sie auf **Get People** (Personen abrufen).  
  
7. Klicken Sie auf **Daten exportieren**.  
  
     In Editor wird eine neue Datei angezeigt, die die exportierten Daten aus **PeopleTrax** enthält.  
  
8. Schließen Sie Editor, und schließen Sie dann die Anwendung **PeopleTrax**.  
  
9. Schließen Sie den Profiler. Geben Sie folgenden Befehl ein:  
  
    ```  
    VSPerfCmd /shutdown  
    ```  
  
10. Verwenden Sie den folgenden Befehl, um die Umgebungsvariablen zurückzusetzen:  
  
    ```  
    VSPerfCLREnv /sampleoff  
    ```  
  
11. Die Profilerstellungsdaten werden in der VSP-Datei gespeichert. Analysieren Sie die Ergebnisse mit einer der folgenden Methoden:  
  
    - Öffnen Sie die VSP-Datei in der Visual Studio-IDE.  
  
         \- oder -  
  
    - Generieren Sie mithilfe des Befehlszeilentools "VSPerfReport.exe" eine Datei mit durch Trennzeichen getrennten Werten (CSV-Datei). Verwenden Sie den folgenden Befehl, um Berichte zu generieren, die außerhalb der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-IDE verwendet werden können:  
  
        ```  
        VSPerfReport <dir> PeopleTraxReport.vsp /output:<dir> /summary:all  
        ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über Leistungs Sitzungen](../profiling/performance-session-overview.md)   
 [Profilerstellung über die Befehlszeile](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Grundlegendes zu Stichprobendaten Werten](../profiling/understanding-sampling-data-values.md)   
 [Leistungs Berichts Ansichten](../profiling/performance-report-views.md)
