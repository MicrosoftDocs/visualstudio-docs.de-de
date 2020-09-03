---
title: Analysieren des Energieverbrauchs in Store-Apps | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 96d06843-b97e-45a8-8126-07478a40bfc4
caps.latest.revision: 39
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 82f5e6401ba65a0dfaffc268890ece0166432c08
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85532950"
---
# <a name="analyze-energy-use-in-store-apps"></a>Analysieren des Energieverbrauchs in Store-Apps
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der Profiler **Energieverbrauch** von Visual Studio hilft Ihnen, den Strom- und Energieverbrauch von Windows Store-Apps auf Tabletgeräten mit geringer Leistung zu analysieren, die die ganze Zeit oder zeitweilig von eigenen Akkus betrieben werden. Auf einem akkubetriebenen Gerät kann eine App, die zu viel Energie verbraucht, die Kundenzufriedenheit so sehr beeinträchtigen, dass sie von den Kunden möglicherweise sogar deinstalliert wird. Ein optimierter Energieverbrauch kann die Akzeptanz Ihrer App und deren Nutzung durch die Kunden erhöhen.  
  
## <a name="what-the-energy-consumption-profiler-is-how-it-works-and-what-it-measures"></a><a name="BKMK_What_the_Energy_Consumption_tool_is__how_it_works__and_what_it_measures"></a> Was der Energieverbrauch-Profiler ist, wie er funktioniert und was er misst  
 Der Energieverbrauch-Profiler erfasst die Aktivitäten der Anzeige, CPU und Netzwerkverbindungen eines Geräts während einer Profilerstellungssitzung. Daraufhin generiert er Schätzungen der Energie, die für diese Aktivitäten verbraucht wird, sowie der Gesamtmenge an Energie, die für die Profilerstellungssitzung verwendet wird.  
  
> [!NOTE]
> Der Energie-Profiler schätzt den Strom- und Energieverbrauch unter Anwendung eines Softwaremodells einer Standardreferenzgerätehardware, die repräsentativ für Tabletgeräte mit geringer Leistung ist, auf denen Ihre Anwendung möglicherweise ausgeführt wird. Um eine optimale Schätzung zu ermöglichen, wird empfohlen, die Profildaten auf einem Tabletgerät mit geringer Leistung zu sammeln.  
>   
> Auch wenn das Modell gute Schätzungen für eine Vielzahl an Geräten mit geringer Leistung liefert, sind die tatsächlichen Werte des Geräts, für das Sie ein Profil erstellen, wahrscheinlich anders. Anhand der Werte können Sie herausfinden, welche Anzeige-, CPU- und Netzwerkaktivitäten im Vergleich zur Nutzung anderer Ressourcen recht teuer sind und sich so möglicherweise besonders gut für Optimierungszwecke eignen.  
  
 Der Energieverbrauch-Profiler verwendet folgende Definitionen von *Strom* und *Energie*:  
  
- *Strom* misst die Rate, mit der Kraft aufgewendet wird, um in einem bestimmten Zeitraum eine Leistung zu erbringen. In der Elektrik ist die Standardeinheit für Strom *Watt*. Diese wird als die Rate definiert, in der Leistung erbracht wird, wenn ein Ampere Spannung über eine elektrische Potenzialdifferenz von einem Volt fließt. Im Diagramm für den **Stromverbrauch** werden die Einheiten in Milliwatt **mW** (einem Tausendstel Watt) angezeigt.  
  
   Da Strom fließt, hat es auch eine Richtung (die Leistung kann in einem Zeitraum ansteigen oder abnehmen) und eine Geschwindigkeit (die Menge, mit der die Leistung ansteigt oder abnimmt).  
  
- *Energie* misst die Gesamtmenge der Leistung, entweder als Kapazität oder Potenzial, wie bei der Stromkapazität eines Akkus, oder als Gesamtsumme an Leistung über einen bestimmten Zeitraum. Die Einheit für Energie ist eine Wattstunde, d. h. die Menge an Strom eines Watts, die ständig eine Stunde lang angewendet wird. In der **Energiezusammenfassung**werden die Einheiten in Milliwattstunden **mW-h**dargestellt.  
  
  ![Energiekapazität, Energieverbrauch, verbrauchte Energie insgesamt](../profiling/media/energyprof-capcitypowerused.png "ENERGYPROF_CapcityPowerUsed")  
  
  Ein vollständig geladener Akku in einem Tablet verfügt z. B. über eine bestimmte Menge an gespeicherte Energie. Während die Energie verwendet wird, um Aufgaben wie die Kommunikation über ein Netzwerk, die Berechnung von Werten oder die Anzeige von Grafiken auszuführen, verbraucht sich der Strom des Akkus in unterschiedlichen Raten. Während jedes beliebigen Zeitraum wird auch die Summe des verbrauchten Stroms von der Energie gemessen.  
  
## <a name="identify-scenarios-with-user-marks"></a><a name="BKMK_Identify_scenarios_with_user_marks"></a> Identifizieren von Szenarien mit Benutzer Markierungen  
 Sie können den Profilerstellungsdaten *Benutzermarkierungen* hinzufügen, die bei der Identifizierung von Bereichen im Zeitachsenlineal hilfreich sind.  
  
 ![Benutzermarkierungen auf der Zeitachse](../profiling/media/profilers-usermarktimeline.png "PROFILERS_UserMarkTimeline")  
  
 Die Markierung wird bei Ausführung der Methode in der Zeitachse als orangefarbenes Dreieck angezeigt. Die Meldung und Uhrzeit werden als QuickInfo angezeigt, wenn Sie mit der Maus über die Markierung fahren. Wenn mindestens zwei Benutzermarkierungen nahe beieinander liegen, werden die Markierungen zusammengeführt und die QuickInfo-Daten werden kombiniert. Sie können auf der Zeitachse eine Vergrößerung durchführen, um die Markierungen zu trennen.  
  
 **Hinzufügen von Markierungen zu C#-, Visual Basic- und C++-Code**  
  
 Erstellen Sie zuerst ein [Windows.Foundation.Diagnostics LoggingChannel](https://msdn.microsoft.com/library/windows/apps/windows.foundation.diagnostics.loggingchannel.aspx) -Objekt, um C#-, Visual Basic- und C++-Code eine Benutzermarkierung hinzuzufügen. Fügen Sie anschließend an den Positionen im Code, die Sie markieren möchten, Aufrufe von [LoggingChannel.LogMessage](https://msdn.microsoft.com/library/windows/apps/dn264210.aspx) -Methoden ein. Verwenden Sie in den Aufrufen [LoggingLevel.Information](https://msdn.microsoft.com/library/windows/apps/windows.foundation.diagnostics.logginglevel.aspx) .  
  
 Wenn die Methode ausgeführt wird, wird eine Benutzermarkierung zu den Profilerstellungsdaten zusammen mit einer Meldung hinzugefügt.  
  
> [!NOTE]
> - Die Windows.Foundation.Diagnostics LoggingChannel-Klasse implementiert die [Windows.Foundation.IClosable](https://msdn.microsoft.com/library/windows/apps/windows.foundation.iclosable.aspx)-Schnittstelle (in C# und VB als [System.IDisposable](https://msdn.microsoft.com/library/System.IDisposable.aspx) projiziert). Rufen Sie [LoggingChannel.Close()](https://msdn.microsoft.com/library/windows/apps/windows.foundation.diagnostics.loggingchannel.close.aspx) (Windows.Foundation.Diagnostics.LoggingChannel.Dispose() in C# und VB) auf, wenn Sie mit einem Protokollierungskanal fertig sind, um Verluste von Betriebssystemressourcen zu vermeiden.  
>   - Jeder offene Protokollierungschannel muss einen eindeutigen Namen haben. Wenn Sie versuchen, einen neuen Protokollierungschannel mit demselben Namen wie ein nicht gelöschter Channel zu erstellen, wird eine Ausnahme verursacht.  
  
 **Hinzufügen von Markierungen zu JavaScript-Code**  
  
 Um Benutzermarkierungen hinzuzufügen, fügen Sie Ihrem Code an den gewünschten Positionen den folgenden Code hinzu:  
  
```  
if (performance && performance.mark) {  
    performance.mark(markDescription);  
}  
```  
  
 *markDescription* ist eine Zeichenfolge, die die Meldung enthält, die in der QuickInfo der Benutzermarkierung angezeigt werden soll.  
  
## <a name="configure-your-environment-for-profiling"></a><a name="BKMK_Configure_your_environment_for_profiling"></a> Konfigurieren Ihrer Umgebung für die Profilerstellung  
 Um gute Schätzungen zu erhalten, sollten Sie für den Energieverbrauch der App auf einem Gerät mit geringer Leistung, das durch Akkus betrieben wird, ein Profil erstellen. Da Visual Studio auf den meisten dieser Geräte nicht ausgeführt wird, müssen Sie den Visual Studio-Computer mithilfe der Visual Studio-Remotetools mit dem Gerät verbinden. Um eine Verbindung mit einem Remotegerät herzustellen, müssen Sie sowohl das Visual Studio-Projekt und als auch das Remotegerät konfigurieren. Weitere Informationen finden Sie unter [Ausführen von Windows Store-Apps auf einem Remotecomputer](../debugger/run-windows-store-apps-on-a-remote-machine.md).  
  
> [!TIP]
> - Energieprofilerstellung auf dem Windows Store-Simulator oder auf dem Visual Studio-Computer wird nicht empfohlen. Die Profilerstellung auf dem tatsächlichen Gerät bietet weitaus realistischere Daten.  
>   - Erstellen Sie das Profil auf dem Zielgerät, während es über seine Akkus betrieben wird.  
>   - Schließen Sie alle anderen Anwendungen, die möglicherweise die gleichen Ressourcen verwenden (Netzwerk, CPU oder Anzeige).  
  
## <a name="collect-energy-profile-data-for-your-app"></a><a name="BKMK_Collect_energy_profile_data_for_your_app"></a> Sammeln von Energieprofil Daten für Ihre APP  
  
1. Wählen Sie im Menü **Debuggen** die Option **Diagnose ohne Debugging starten**.  
  
     ![„Energieverbrauch“ im Diagnosehub auswählen](../profiling/media/energyprof-diagnosticshub.png "ENERGYPROF_DiagnosticsHub")  
  
2. Wählen Sie **Energieverbrauch** und dann **Starten**aus.  
  
    > [!NOTE]
    > Wenn Sie den Profiler **Energieverbrauch** starten, wird möglicherweise ein Fenster " **Benutzerkontensteuerung** " angezeigt, das Ihre Berechtigung zum Ausführen von VsEtwCollector.exe anfordert. Klicken Sie auf **Ja**.  
  
3. Führen Sie Ihre App aus, um Daten zu sammeln.  
  
4. Um die Profilerstellung zu beenden, wechseln Sie zu Visual Studio zurück (ALT+TAB), und wählen Sie **Auflistung beenden** auf der Diagnosehubseite aus.  
  
     ![Datensammlung beenden](../profiling/media/xamlprof-stopcollection.png "XAMLProf_StopCollection")  
  
     Visual Studio analysiert die gesammelten Daten und zeigt die Ergebnisse an.  
  
## <a name="collect-energy-profile-data-for-an-installed-app"></a><a name="BKMK_Collect_energy_profile_data_for_an_installed_app"></a> Sammeln von Energieprofil Daten für eine installierte App  
 Das Energieverbrauchstool kann nur für Windows Store 8.1-Apps ausgeführt werden, die von einer Visual Studio-Projektmappe gestartet oder vom Windows Store installiert werden. Wenn eine Projektmappe in Visual Studio geöffnet ist, lautet das Standardziel **Startprojekt**. So verwenden Sie eine installierte App als Ziel  
  
1. Wählen Sie **Ziel ändern** und dann **Installierte App**aus.  
  
2. Wählen Sie in der Liste **Installiertes App-Paket auswählen** das Ziel aus.  
  
3. Wählen Sie auf der Seite "Diagnosehub" **Energieverbrauch** aus.  
  
4. Wählen **Starten** , um die Profilerstellung zu starten.  
  
   Um die Profilerstellung zu beenden, wechseln Sie zu Visual Studio zurück (ALT+TAB), und wählen Sie **Auflistung beenden** auf der Diagnosehubseite aus.  
  
## <a name="analyze-energy-profile-data"></a><a name="BKMK_Analyze_energy_profile_data"></a> Analysieren von Energieprofil Daten  
 Die Energieprofildaten werden im Dokumentfenster von Visual Studio angezeigt:  
  
 ![Berichtsseite des Energie-Profilers](../profiling/media/energyprof-all.png "ENERGYPROF_All")  
  
|Bild|Beschreibung|  
|-|-|  
|![Schritt 1](../profiling/media/procguid-1.png "ProcGuid_1")|Die Berichtsdatei heißt Report*JJJJMMTT-HHMM*.diagsession. Sie können den Namen ändern, wenn Sie den Bericht speichern.|  
|![Schritt 2](../profiling/media/procguid-2.png "ProcGuid_2")|Die Zeitachse zeigt die Länge der Profilerstellungssitzung, der App-Lebenszyklusaktivierungsereignisse und der Benutzermarkierungen an.|  
|![Schritt 3](../profiling/media/procguid-3.png "ProcGuid_3")|Sie können den Bericht auf einen Teil der Zeitachse einschränken, indem Sie die blauen Striche ziehen, um einen Bereich der Zeitachse auszuwählen.|  
|![Schritt 4](../profiling/media/procguid-4.png "ProcGuid_4")|Das Diagramm **Stromverbrauch** ist ein Liniendiagramm (mit mehreren Linien), in dem die Änderung in der Stromabgabe anzeigt wird, die durch eine Geräteressource während einer Profilerstellungssitzung verursacht wird. Der Energieverbrauchsprofiler verfolgt die von der CPU, von der Netzwerkaktivität und von der Bildschirmanzeige verwendete Energie.|  
|![Schritt 5](../profiling/media/procguid-6.png "ProcGuid_6")|Das Diagramm **Ressourcen (Ein/Aus)**  stellt Details der Netzwerkenergiekosten dar. Die Leiste **Netzwerk** stellt die Zeit dar, während der die Netzwerkverbindung geöffnet war. Die untergeordnete Leiste **Datenübertragung** stellt die Zeit dar, in der die App Daten über das Netzwerk empfangen oder gesendet hat.|  
|![Schritt 6](../profiling/media/procguid-6a.png "ProcGuid_6a")|In der **Zusammenfassung der Energieverwendung** wird der proportionale Betrag der gesamten Energie dargestellt, die in einem ausgewählten Zeitraum von der CPU, von der Netzwerkaktivität und von der Bildschirmanzeige verbraucht wurde.|  
  
 **Analyse der Energieprofildaten**  
  
 Suchen Sie einen Bereich, in dem die Ressourcenenergie sehr hoch war. Verknüpfen Sie den Höchstbereich mit der Funktionalität der App. Verwenden Sie dann die Steuerleisten auf der Zeitachse, um den Bereich zu vergrößern. Wenn Sie sich auf die Netzwerkauslastung konzentrieren möchten, erweitern Sie den Knoten **Netzwerk** im Diagramm **Ressourcen (Ein/Aus)**  . Sie können nun die Zeit, in der die Netzwerkverbindung aktiv war, mit der Zeit vergleichen, in der die App Daten über die Verbindung empfangen oder übertragen hat. Eine sehr wirksame Optimierungsmaßnahme ist, die Zeitspanne zu reduzieren, die das Netzwerk unnötigerweise geöffnet ist.  
  
## <a name="optimize-energy-use"></a><a name="BKMK_Optimize_energy_use"></a> Optimieren des Energieverbrauchs  
 Zusätzlich zur Datenübertragung verursachen Netzwerkverbindungen auch Energiekosten für das Initialisieren, Verwalten und Schließen der Verbindung. Einige Netzwerke halten die Verbindung für einen bestimmten Zeitraum aufrecht, nachdem Daten gesendet bzw. empfangen wurden, damit über eine einzige Verbindung mehr Daten übertragen werden können. Im Bereich **Ressourcen (Ein/Aus)** können Sie die Methode überprüfen, mit der die App auf die Verbindung interagiert.  
  
 ![Bereich „Ressourcen &#40;Ein&#47;Aus&#41;“](../profiling/media/energyprof-resources.png "ENERGYPROF_Resources")  
  
 Wenn in den Leisten **Netzwerk** und **Datenübertragung** angezeigt wird, dass die Verbindung langfristig aktiv ist, damit eine Reihe kleiner Datenpakete nacheinander übertragen werden kann, können Sie die Daten im Batch im Rahmen einer Übertragung senden. Damit verringern Sie die Zeit, in der das Netzwerk aktiv ist, und und sparen somit Energiekosten.  
  
 ![Zusammenfassungsbereich für Energieverbrauch](../profiling/media/energyprof-summary.png "ENERGYPROF_Summary")  
  
 Über die Energiekosten der Anzeige haben Sie weniger Kontrolle. Die meisten Bildschirme benötigen mehr Energie, um helle Farben darzustellen als dunklere Farben. Deshalb ist eine Möglichkeit, Kosten zu reduzieren, einen dunklen Hintergrund zu verwenden.  
  
## <a name="other-resources"></a><a name="BKMK_Other_resources"></a> Weitere Ressourcen  
  
- In den Abschnitten **Verbindungsstatus- und Kostenverwaltung** für [C#/VB/C++ und XAML](https://msdn.microsoft.com/0ee0b706-8432-4d49-9801-306ed90764e1) und [JavaScript und HTML](https://msdn.microsoft.com/372afa6a-1c7c-4657-967d-03a77cd8e933) im Windows Dev Center werden die Windows-APIs beschrieben, die Informationen zur Netzwerkkonnektivität bereitstellen, die Ihre App nutzen kann, damit Sie die Kosten für den Netzwerkdatenverkehr reduzieren können.  
  
     Mit dem Visual Studio-Simulator für Windows Store-Apps können Sie Datenverbindungseigenschaften der APIs für Netzwerkinformationen simulieren. Weitere Informationen finden Sie unter [Ausführen von Windows Store-Apps im Simulator](../debugger/run-windows-store-apps-in-the-simulator.md).  
  
- Mit den Tools **JavaScript-Funktionstiming** und **CPU-Auslastung** können Sie die CPU-Last reduzieren, wenn diese von ineffizienten Funktionen verursacht wird. Siehe [Analysieren der CPU-Auslastung](../profiling/analyze-cpu-usage-in-a-windows-universal-app.md).
