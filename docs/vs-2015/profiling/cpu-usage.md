---
title: CPU-Auslastung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7501a20d-04a1-480f-a69c-201524aa709d
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7732a5757281e83c501a8258dd1d44b4f329a87a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548056"
---
# <a name="cpu-usage"></a>CPU-Auslastung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie Leistungsprobleme in Ihrer App untersuchen müssen, ist ein guter Ausgangspunkt die Untersuchung der CPU-Nutzung. Das Tool **CPU-Auslastung** zeigt Ihnen, wo die CPU Zeit für die Ausführung von Visual C++-, Visual C#/Visual Basic und JavaScript-Code verbringt.  
  
 Ab Visual Studio 2015 Update 1 können Sie eine Aufteilung nach Funktion der CPU-Auslastung anzeigen, ohne den Debugger zu verlassen. Sie können die CPU-Profilerstellung während des Debuggens ein- und ausschalten und die Ergebnisse anzeigen, wenn die Ausführung angehalten wird, z. B. an einem Haltepunkt. Weitere Informationen finden Sie unter [CPU-Profilerstellung im Debugger in Visual Studio 2015](https://devblogs.microsoft.com/devops/profile-your-cpu-in-the-debugger-in-visual-studio-2015/).  
  
 Eine exemplarische Vorgehensweise, die die Leistung von Windows Store-Apps analysiert, finden Sie unter [Analysieren der CPU-Auslastung in Store-Apps](https://msdn.microsoft.com/library/windows/apps/dn641982.aspx).  
  
 Der Hub "Leistung und Diagnose" bietet Ihnen viele weitere Optionen zum Ausführen und Verwalten Ihrer Diagnosesitzung. Sie können z. B. das Tool **CPU-Auslastung** auf lokalen oder Remotecomputern oder in einem Simulator oder Emulator ausführen. Sie können die Leistung eines geöffneten Projekts in Visual Studio analysieren, eine Verbindung mit einer ausgeführten App herstellen oder eine App starten, die aus dem Windows Store installiert wurde. Weitere Informationen finden Sie unter [Ausführen von Profil Erstellungs Tools ohne Debugging](https://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01) .  
  
## <a name="collect-cpu-usage-data"></a><a name="BKMK_Collect_CPU_usage_data"></a> Sammeln von CPU-Nutzungsdaten  
  
1. Legen Sie in Visual Studio die Konfiguration der Projektmappe auf **Release** fest, und wählen Sie das Bereitstellungsziel.  
  
    ![Auswählen von Release und lokalem Computer](../profiling/media/cpuuse-selectreleaselocalmachine.png "CPUUSE_SelectReleaseLocalMachine")  
  
   - Durch das Ausführen der App im **Release** -Modus erhalten Sie eine bessere Übersicht über die tatsächliche Leistung Ihrer App.  
  
   - Durch Ausführen der App auf dem lokalen Computer wird die Ausführung der installierten App am besten repliziert.  
  
   - Wenn Sie Daten von einem Remotegerät sammeln, führen Sie die App direkt auf dem Gerät und nicht über eine Remotedesktopverbindung aus.  
  
   - Bei Windows Phone-Apps bietet das Sammeln von Daten direkt auf dem **Gerät** die genauesten Daten.  
  
2. Wählen Sie im Menü **Debuggen** die Option **leistungsprofiler...** aus.  
  
3. Wählen Sie **CPU-Auslastung** , und klicken Sie dann auf **Starten**.  
  
    ![Auswählen der CPU-Auslastung](../profiling/media/cpuuse-lib-choosecpuusage.png "CPUUSE_LIB_ChooseCpuUsage")  
  
4. Klicken Sie nach dem Start der App auf **Maximale Anzahl abrufen**. Warten Sie nach Anzeige der Ausgabe etwa eine Minute, und klicken Sie dann auf **Maximale Anzahl asynchron abrufen**. Das Warten zwischen Schaltflächenklicks vereinfacht das Isolieren der Schaltflächenklickroutinen im Diagnosebericht.  
  
5. Nachdem die zweite Ausgabezeile angezeigt wird, wählen Sie im Leistungs- und Diagnosehub **Auflistung beenden** aus.  
  
   ![CpuUsage-Datensammlung anhalten](../profiling/media/cpu-use-wt-stopcollection.png "CPU_USE_WT_StopCollection")  
  
   Das CPU-Auslastungstool analysiert die Daten und zeigt den Bericht an.  
  
   ![Bericht CpuUsage](../profiling/media/cpu-use-wt-report.png "CPU_USE_WT_Report")  
  
## <a name="analyze-the-cpu-usage-report"></a>Analysieren des CPU-Auslastungsberichts  
  
### <a name="the-cpu-usage-call-tree"></a><a name="BKMK_The_CPU_Usage_call_tree"></a> Die Aufrufstruktur der CPU-Auslastung  
 Um sich mit den Informationen in der Aufrufstruktur vertraut zu machen, wählen Sie zunächst `GetMaxNumberButton_Click` erneut aus, und sehen Sie sich dann die Aufrufstrukturdetails an.  
  
#### <a name="call-tree-structure"></a><a name="BKMK_Call_tree_structure"></a> Struktur der Aufrufstruktur  
 ![Getmaxnumschaltfläche&#95;auf Aufrufstruktur klicken](../profiling/media/cpu-use-wt-getmaxnumbercalltree-annotated.png "CPU_USE_WT_GetMaxNumberCallTree_annotated")  
  
|Bild|Beschreibung|  
|-|-|  
|![Schritt 1](../profiling/media/procguid-1.png "ProcGuid_1")|Der oberste Knoten in CPU-Auslastungsaufrufstrukturen ist ein Pseudoknoten.|  
|![Schritt 2](../profiling/media/procguid-2.png "ProcGuid_2")|Wenn die Option **Externen Code anzeigen** deaktiviert ist, ist in den meisten Apps der Knoten der zweiten Ebene ein **[External Code]** -Knoten, der den System- und Frameworkcode enthält, der die App startet und beendet, die Benutzeroberfläche zeichnet, die Threadplanung steuert und andere Dienste der unteren Ebene für die App bereitstellt.|  
|![Schritt 3](../profiling/media/procguid-3.png "ProcGuid_3")|Die untergeordneten Elemente des Knotens der zweiten Ebene sind die Benutzercodemethoden und asynchronen Routinen, die vom System- und Frameworkcode der zweiten Ebene aufgerufen oder erstellt werden.|  
|![Schritt 4](../profiling/media/procguid-4.png "ProcGuid_4")|Untergeordnete Knoten einer Methode enthalten Daten nur für die Aufrufe der übergeordneten Methode. Wenn **Externen Code anzeigen** deaktiviert ist, können App-Methoden auch den Knoten **[Externer Code]** enthalten.|  
  
#### <a name="external-code"></a><a name="BKMK_External_Code"></a> Externer Code  
 Externer Code umfasst Funktionen in System- und Frameworkkomponenten, die vom Code ausgeführt werden, den Sie schreiben. Externer Code umfasst Funktionen, die die App starten und beenden, die Benutzeroberfläche zeichnen, das Threading steuern und der App andere hardwarenahe Dienste bereitstellen. In den meisten Fällen sind Sie nicht an externem Code interessiert, weshalb die CPU-Verwendungs Aufrufstruktur die externen Funktionen einer Benutzer Methode in einem Knoten **[externer Code]** sammelt.  
  
 Wenn Sie die Aufrufpfade von externem Code anzeigen möchten, wählen Sie aus der Liste **Ansicht filtern** die Option **Externen Code anzeigen** und dann **Übernehmen**aus.  
  
 ![Anzeigen der Filteransicht und anschließendes Anzeigen von externem Code](../profiling/media/cpu-use-wt-filterview.png "CPU_USE_WT_FilterView")  
  
 Achten Sie darauf, dass viele externe Codeaufrufketten tief verschachtelt sind, sodass die Breite der Spalte mit dem Funktionsnamen die Anzeigebreite aller außer sehr großer Computerbildschirme überschreiten kann. Wenn dies geschieht, werden Funktionsnamen als **[...]** angezeigt:  
  
 ![Geschachtelter externer Code in der Aufrufstruktur](../profiling/media/cpu-use-wt-showexternalcodetoowide.png "CPU_USE_WT_ShowExternalCodeTooWide")  
  
 Verwenden Sie das Suchfeld, um nach einem gewünschten Knoten zu suchen, und verwenden Sie dann die horizontale Bildlaufleiste, um die Daten sichtbar zu machen:  
  
 ![Suche nach geschachteltem externen Code](../profiling/media/cpu-use-wt-showexternalcodetoowide-found.png "CPU_USE_WT_ShowExternalCodeTooWide_Found")  
  
### <a name="call-tree-data-columns"></a><a name="BKMK_Call_tree_data_columns"></a> Datenspalten der Aufrufstruktur  
  
|Eigenschaft|BESCHREIBUNG|
|-|-|  
|**Gesamt-CPU (%)**|![Gesamt % Datengleichung](../profiling/media/cpu-use-wt-totalpercentequation.png "CPU_USE_WT_TotalPercentEquation")<br /><br /> Der Prozentsatz der CPU-Aktivität der App im ausgewählten Zeitraum durch Aufrufe der Funktion und die von der Funktion aufgerufenen Funktionen. Beachten Sie, dass sich dieser Wert vom Zeitachsendiagramm **CPU-Auslastung** unterscheidet, das die Gesamtaktivität der App in einem Zeitraum mit der insgesamt verfügbaren CPU-Kapazität vergleicht.|  
|**Eigen-CPU (%)**|![Selbst % Gleichung](../profiling/media/cpu-use-wt-selflpercentequation.png "CPU_USE_WT_SelflPercentEquation")<br /><br /> Der Prozentsatz der CPU-Aktivität der App im ausgewählten Zeitraum durch Aufrufe der Funktion ohne die Aktivität der von der Funktion aufgerufenen Funktionen.|  
|**Gesamt-CPU (ms)**|Die Anzahl der Millisekunden für Aufrufe an die Funktion im ausgewählten Zeitraum und die von der Funktion aufgerufenen Funktionen.|  
|**Eigen-CPU (ms)**|Die Anzahl der Millisekunden für Aufrufe an die Funktion im ausgewählten Zeitraum und die von der Funktion aufgerufenen Funktionen.|  
|**Modul**|Der Name des Moduls mit der Funktion oder die Anzahl der Module, die die Funktionen in einem Knoten vom Typ [Externer Code] enthalten.|  
  
### <a name="asynchronous-functions-in-the-cpu-usage-call-tree"></a><a name="BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree"></a> Asynchrone Funktionen in der CPU-Verwendungs Aufrufstruktur  
 Wenn der Compiler auf eine asynchrone Methode trifft, erstellt er eine versteckte Klasse zum Steuern der Ausführung der Methode. Grundsätzlich ist die Klasse ein Zustandsautomat mit einer Liste von vom Compiler generierten Funktionen, die Vorgänge der ursprünglichen Methode asynchron aufrufen, und den Rückrufen, dem Scheduler und den Iteratoren, die für diese ordnungsgemäß erforderlich sind. Wenn die ursprüngliche Methode von einer übergeordneten Methode aufgerufen wird, entfernt die Runtime die Methode aus dem Ausführungskontext der übergeordneten Methode und führt die Methode der ausgeblendeten Klasse im Kontext des System- und Frameworkcodes durch, der die Ausführung der App steuert. Die asynchronen Methoden werden oft, jedoch nicht immer, in einem oder mehreren verschiedenen Threads ausgeführt. Dieser Code wird in der Aufrufstruktur der CPU-Auslastung als untergeordnete Elemente des Knotens **[Externer Code]** direkt unter dem obersten Knoten der Struktur gezeigt.  
  
 Um dies in unserem Beispiel zu sehen, wählen Sie erneut das Segment `GetMaxNumberAsyncButton_Click` in der Zeitachse aus.  
  
 ![Getmaxnumasyncbutton&#95;auf Berichts Auswahl klicken](../profiling/media/cpu-use-wt-getmaxnumberasync-selected.png "CPU_USE_WT_GetMaxNumberAsync_Selected")  
  
 Die ersten zwei Knoten unter **[External Code]** sind die vom Compiler generierten Methoden der Zustandsautomatklasse. Der dritte ist der Aufruf der ursprünglichen Methode. Wenn Sie die generierte Methoden erweitern, sehen Sie, was passiert.  
  
 ![Erweiterte getmaxnumasyncbutton-&#95;klicken auf die Aufrufstruktur](../profiling/media/cpu-use-wt-getmaxnumberasync-expandedcalltree.png "CPU_USE_WT_GetMaxNumberAsync_ExpandedCallTree")  
  
- `MainPage::GetMaxNumberAsyncButton_Click` macht sehr wenig, nämlich Verwalten einer Liste von Aufgabenwerten, Berechnen des Maximums der Ergebnisse und Anzeigen der Ausgabe.  
  
- `MainPage+<GetMaxNumberAsyncButton_Click>d__3::MoveNext` zeigt die erforderliche Aktivität zum Planen und Starten der 48 Aufgaben, die den Aufruf von `GetNumberAsync`umschließen.  
  
- `MainPage::<GetNumberAsync>b__b` zeigt die Aktivität der Aufgaben, die `GetNumber` aufrufen.
