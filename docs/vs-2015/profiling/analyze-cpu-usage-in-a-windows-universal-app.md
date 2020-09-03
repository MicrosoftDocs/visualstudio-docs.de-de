---
title: Analysieren der CPU-Auslastung in einer universellen Windows-App | Windows-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c122b08e-e3bf-43e6-bd6c-e776e178fd9a
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: def581f547db19a8db4cebc4d63739ff09bb5fab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85531663"
---
# <a name="analyze-cpu-usage-in-a-windows-universal-app"></a>Analysieren der CPU-Auslastung in einer universellen Windows-App
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gilt für Windows und Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Wenn Sie Leistungsprobleme in Ihrer App untersuchen müssen, ist ein guter Ausgangspunkt die Untersuchung der CPU-Nutzung. Das Tool **CPU-Auslastung** zeigt Ihnen, wo die CPU Zeit damit verbringt, Code auszuführen. Um sich auf bestimmte Szenarien zu konzentrieren, kann die CPU-Auslastung mit dem Tool [XAML-UI-Reaktionsfähigkeit](https://msdn.microsoft.com/library/4ff84cd1-4e63-4fda-b34f-3ef862a6e480) , dem Tool CPU-Auslastungs [Tool](../profiling/cpu-usage.md) oder beiden Tools in einer einzigen Diagnose Sitzung ausgeführt werden.  
  
> [!NOTE]
> Das Tool **CPU-Auslastung** kann nicht mit Windows Phone Silverlight 8.1-Apps verwendet werden.  
  
 In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie die CPU-Auslastung für eine einfache universelle Windows XAML-App erfassen und analysieren.  
  
## <a name="create-the-cpuusedemo-project"></a><a name="BKMK_Create_the_CpuUseDemo_project"></a> Erstellen des CpuUseDemo-Projekts  
 **CpuUseDemo** ist eine App, die erstellt wurde, um zu zeigen, wie Sie CPU-Auslastungsdaten erfassen und analysieren. Die Schaltflächen generieren eine Zahl, indem sie eine Methode aufrufen, die den maximalen Wert aus mehreren Aufrufen an eine Funktion auswählt. Die aufgerufene Funktion erstellt eine sehr große Anzahl zufälliger Werte und gibt dann den letzten zurück. Die Daten werden in einem Textfeld angezeigt.  
  
1. Erstellen Sie ein neues Projekt für eine universelle C# Windows-App mit dem Namen **CpuUseDemo** über die Vorlage **Leere App**.  
  
     ![CpuUseDemoProject erstellen](../profiling/media/cpu-use-newproject.png "CPU_USE_NewProject")  
  
2. Ersetzen Sie „MainPage.xaml“ durch [folgenden Code](#BKMK_MainPage_xaml).  
  
3. Ersetzen Sie „MainPage.xaml.cs“ durch [folgenden Code](#BKMK_MainPage_xaml_cs).  
  
4. Erstellen Sie die APP, und probieren Sie Sie aus. Die APP ist einfach genug, um Ihnen einige häufige Fälle der Analyse der CPU-Auslastung zu zeigen.  
  
## <a name="collect-cpu-usage-data"></a><a name="BKMK_Collect_CPU_usage_data"></a> Sammeln von CPU-Nutzungsdaten  
 ![Releasebuild der App im Simulator ausführen](../profiling/media/cpu-use-wt-setsimulatorandretail.png "CPU_USE_WT_SetSimulatorAndRetail")  
  
1. Stellen Sie das Bereitstellungsziel in Visual Studio auf **Simulator** und die Projektmappenkonfigurierung auf **Release** ein.  
  
   - Wenn Sie die App im Simulator ausführen, können Sie einfach zwischen der App und der Visual Studio IDE wechseln.  
  
   - Die Ausführung dieser App im **Release**-Modus gibt Ihnen eine bessere Ansicht der tatsächlichen Leistung Ihrer App.  
  
2. Wählen Sie im Menü **Debuggen** die Option **leistungsprofiler...** aus.  
  
3. Wählen Sie im Leistungs- und Diagnosehub **CPU-Auslastung** und dann **Starten** aus.  
  
    ![Diagnosesitzung CpuUsage starten](../profiling/media/cpu-use-wt-perfdiaghub.png "CPU_USE_WT_PerfDiagHub")  
  
4. Klicken Sie nach dem Start der App auf **Maximale Anzahl abrufen**. Warten Sie nach Anzeige der Ausgabe etwa eine Minute, und klicken Sie dann auf **Maximale Anzahl asynchron abrufen**. Das Warten zwischen Schaltflächenklicks vereinfacht das Isolieren der Schaltflächenklickroutinen im Diagnosebericht.  
  
5. Nachdem die zweite Ausgabezeile angezeigt wird, wählen Sie im Leistungs- und Diagnosehub **Auflistung beenden** aus.  
  
   ![CpuUsage-Datensammlung anhalten](../profiling/media/cpu-use-wt-stopcollection.png "CPU_USE_WT_StopCollection")  
  
   Das CPU-Auslastungstool analysiert die Daten und zeigt den Bericht an.  
  
   ![Bericht CpuUsage](../profiling/media/cpu-use-wt-report.png "CPU_USE_WT_Report")  
  
## <a name="analyze-the-cpu-usage-report"></a><a name="BKMK_Analyze_the_CPU_Usage_report"></a> Analysieren des CPU-Auslastungs Berichts  
  
### <a name="cpu-utilization-timeline-graph"></a><a name="BKMK_CPU_utilization_timeline_graph"></a> Diagramm der CPU-Auslastungszeitachse  
 ![Cpunutzungs&#40;% &#41; Zeitachsen Diagramm](../profiling/media/cpu-use-wt-timelinegraph.png "CPU_USE_WT_TimelineGraph")  
  
 Im CPU-Auslastungsdiagramm wird die CPU-Aktivität der App als Prozentsatz der gesamten CPU-Zeit von allen Prozessorkernen auf dem Gerät angezeigt. Die Daten dieses Berichts wurden auf einem Computer mit zwei Kernen erfasst. Die zwei großen Spitzen stellen die CPU-Aktivität der zwei Schaltflächenklicks dar. `GetMaxNumberButton_Click` wird synchron auf einem einzigen Kern ausgeführt, sodass es Sinn macht, dass die Diagrammhöhe der Methode nie über 50 % hinausgeht. `GetMaxNumberAsycButton_Click` wird asynchron über beide Kerne ausgeführt, deshalb sieht es auch hier richtig aus, dass die Spitze näher an die Nutzung aller CPU-Ressourcen auf beiden Kernen herankommt.  
  
#### <a name="select-timeline-segments-to-view-details"></a><a name="BKMK_Select_timeline_segments_to_view_details"></a> Für Detailansicht Zeitachsensegmente auswählen  
 Verwenden Sie die Auswahlleisten auf der Zeitachse **Diagnosesitzung**, um sich auf GetMaxNumberButton_Click-Daten zu konzentrieren:  
  
 ![Getmaxnumschaltfläche&#95;klicken auf "ausgewählt"](../profiling/media/cpu-use-wt-getmaxnumberreport.png "CPU_USE_WT_GetMaxNumberReport")  
  
 In der Zeitachse **Diagnosesitzung** wird jetzt die Zeit angezeigt, die in dem ausgewählten Segment verbracht wurde (etwas mehr als 2 Sekunden in diesem Bericht). Außerdem wird die Aufrufstruktur nach den Methoden gefiltert, die in der Auswahl ausgeführt wurden.  
  
 Wählen Sie jetzt das Segment `GetMaxNumberAsyncButton_Click` aus.  
  
 ![Getmaxnumasyncbutton&#95;auf Berichts Auswahl klicken](../profiling/media/cpu-use-wt-getmaxnumberasync-selected.png "CPU_USE_WT_GetMaxNumberAsync_Selected")  
  
 Diese Methode wird rund eine Sekunde schneller abgeschlossen als `GetMaxNumberButton_Click`, aber die Bedeutung der Aufrufstruktureinträge ist weniger offensichtlich.  
  
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
 Externer Code besteht aus Funktionen in System- und Frameworkkomponenten, die vom Code ausgeführt werden, den Sie schreiben. Externer Code umfasst Funktionen, die die App starten und beenden, die Benutzeroberfläche zeichnen, das Threading steuern und der App andere hardwarenahe Dienste bereitstellen. In den meisten Fällen sind Sie nicht an externem Code interessiert, weshalb die CPU-Verwendungs Aufrufstruktur die externen Funktionen einer Benutzer Methode in einem Knoten **[externer Code]** sammelt.  
  
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
  
## <a name="next-steps"></a><a name="BKMK_Next_steps"></a> Nächste Schritte  
 Die CpuUseDemo-App ist kein Meisterwerk, aber Sie können die Nützlichkeit erweitern, indem Sie sie verwenden, um mit asynchronen Vorgängen und anderen Tools im Leistungs- und Diagnosehub zu experimentieren.  
  
- Beachten Sie, dass `MainPage::<GetNumberAsync>b__b` mehr Zeit in [External Code] als mit der Ausführung der GetNumber-Methode verbringt. Ein großer Teil dieser Zeit ist der Mehraufwand der asynchronen Vorgänge. Versuchen Sie, die Anzahl der Aufgaben (festgelegt in der `NUM_TASKS`-Konstante von MainPage.xaml.cs) zu erhöhen und die Anzahl der Iterationen in `GetNumber` zu verringern (ändern Sie den Wert `MIN_ITERATIONS`). Führen Sie das Erfassungsszenario aus, und vergleichen Sie die CPU-Aktivität von `MainPage::<GetNumberAsync>b__b` mit der in der ursprünglichen CPU-Auslastungsdiagnosesitzung. Versuchen Sie, die Aufgaben zu verringern und die Iterationen zu erhöhen.  
  
- Benutzern ist die tatsächliche Leistung Ihrer App oft egal, ihnen ist die wahrgenommene Leistung und Reaktionsfähigkeit der App wichtig. Mit dem Tool zur XAML-UI-Reaktionsfähigkeit können Sie die Details der Aktivität im UI-Thread anzeigen, die sich auf die wahrgenommene Reaktionsfähigkeit auswirkt.  
  
     Erstellen Sie eine neue Sitzung im Leistungs- und Diagnosehub, und fügen Sie die Tools XAML-UI-Reaktionsfähigkeit und CPU-Auslastung hinzu. Führen Sie das Erfassungsszenario aus. Wenn Sie diesen Artikel gelesen haben, gibt der Bericht Ihnen wahrscheinlich nichts, was Sie nicht bereits herausgefunden haben, aber die Unterschiede im Zeitachsen Diagramm **UI-Thread Auslastung** für die zwei Methoden sind verblüffend. In komplexen realen Apps kann die Kombination der Tools sehr hilfreich sein.  
  
## <a name="mainpagexaml"></a><a name="BKMK_MainPage_xaml"></a> MainPage. XAML  
  
```csharp  
<Page  
    x:Class="CpuUseDemo.MainPage"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:local="using:CpuUseDemo"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    mc:Ignorable="d">  
  
    <Page.Resources>  
        <Style TargetType="TextBox">  
            <Setter Property="FontFamily"  Value="Lucida Console" />  
        </Style>  
    </Page.Resources>  
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">  
        <Grid.RowDefinitions>  
            <RowDefinition Height="Auto" />  
            <RowDefinition Height="*" />  
        </Grid.RowDefinitions>  
        <StackPanel Grid.Row="0" Orientation="Horizontal"  Margin="0,40,0,0">  
            <Button Name="GetMaxNumberButton" Click="GetMaxNumberButton_Click"  Content="Get Max Number" />  
            <Button Name="GetMaxNumberAsyncButton" Click="GetMaxNumberAsyncButton_Click"  Content="Get Max Number Async" />  
        </StackPanel>  
        <StackPanel Grid.Row="1">  
            <TextBox Name="TextBox1" AcceptsReturn="True" />  
        </StackPanel>  
    </Grid>  
  
</Page>  
  
```  
  
## <a name="mainpagexamlcs"></a><a name="BKMK_MainPage_xaml_cs"></a> MainPage.xaml.cs  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.IO;  
using System.Linq;  
using System.Runtime.InteropServices.WindowsRuntime;  
using Windows.Foundation;  
using Windows.Foundation.Collections;  
using Windows.UI.Xaml;  
using Windows.UI.Xaml.Controls;  
using Windows.UI.Xaml.Controls.Primitives;  
using Windows.UI.Xaml.Data;  
using Windows.UI.Xaml.Input;  
using Windows.UI.Xaml.Media;  
using Windows.UI.Xaml.Navigation;  
using Windows.Foundation.Diagnostics;  
using System.Threading;  
using System.Threading.Tasks;  
using System.Collections.Concurrent;  
  
// The Blank Page item template is documented at http://go.microsoft.com/fwlink/?LinkId=234238  
  
namespace CpuUseDemo  
{  
    /// <summary>  
    /// An empty page that can be used on its own or navigated to within a Frame.  
    /// </summary>  
    public sealed partial class MainPage : Page  
    {  
        public MainPage()  
        {  
            this.InitializeComponent();  
        }  
  
        const int NUM_TASKS = 48;  
        const int MIN_ITERATIONS = int.MaxValue / 1000;  
        const int MAX_ITERATIONS = MIN_ITERATIONS + 10000;  
  
        long m_totalIterations = 0;  
        readonly object m_totalItersLock = new object();  
  
        private void GetMaxNumberButton_Click(object sender, RoutedEventArgs e)  
        {  
            GetMaxNumberAsyncButton.IsEnabled = false;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations = 0;  
            }  
            List<int> tasks = new List<int>();  
            for (var i = 0; i < NUM_TASKS; i++)  
            {  
                var result = 0;  
                result = GetNumber();  
                tasks.Add(result);  
            }  
            var max = tasks.Max();  
            var s = GetOutputString("GetMaxNumberButton_Click", NUM_TASKS, max, m_totalIterations);  
            TextBox1.Text += s;  
            GetMaxNumberAsyncButton.IsEnabled = true;  
        }  
  
        private async void GetMaxNumberAsyncButton_Click(object sender, RoutedEventArgs e)  
        {  
            GetMaxNumberButton.IsEnabled = false;  
            GetMaxNumberAsyncButton.IsEnabled = false;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations = 0;  
            }  
            var tasks = new ConcurrentBag<Task<int>>();  
            for (var i = 0; i < NUM_TASKS; i++)  
            {  
                tasks.Add(GetNumberAsync());  
            }  
            await Task.WhenAll(tasks.ToArray());  
            var max = 0;  
            foreach (var task in tasks)  
            {  
                max = Math.Max(max, task.Result);  
            }  
            var func = "GetMaxNumberAsyncButton_Click";  
            var outputText = GetOutputString(func, NUM_TASKS, max, m_totalIterations);  
            TextBox1.Text += outputText;  
            this.GetMaxNumberButton.IsEnabled = true;  
            GetMaxNumberAsyncButton.IsEnabled = true;  
        }  
  
        private int GetNumber()  
        {  
            var rand = new Random();  
            var iters = rand.Next(MIN_ITERATIONS, MAX_ITERATIONS);  
            var result = 0;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations += iters;  
            }  
            // we're just spinning here  
            // and using Random to frustrate compiler optimizations  
            for (var i = 0; i < iters; i++)  
            {  
                result = rand.Next();  
            }  
            return result;  
        }  
  
        private Task<int> GetNumberAsync()  
        {  
            return Task<int>.Run(() =>  
            {  
                return GetNumber();  
            });  
        }  
  
        string GetOutputString(string func, int cycles, int max, long totalIters)  
        {  
            var fmt = "{0,-35}Tasks:{1,3}    Maximum:{2, 12}    Iterations:{3,12}\n";  
            return String.Format(fmt, func, cycles, max, totalIters);  
        }  
  
    }  
}  
  
```
