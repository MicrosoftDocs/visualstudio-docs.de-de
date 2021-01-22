---
title: Analysieren des Energieverbrauchs in UWP-Apps | Microsoft-Dokumentation
description: Verwenden Sie den Visual Studio-Profiler „Energieverbrauch“, um den Energie- und Strombedarf von UWP-Apps zu analysieren, die auf batteriebetriebenen Geräten ausgeführt werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 96d06843-b97e-45a8-8126-07478a40bfc4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
monikerRange: vs-2017
ms.openlocfilehash: cf55035ba5a05917334b2192067a3273f4930775
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205787"
---
# <a name="analyze-energy-use-in-uwp-apps"></a>Analysieren des Energieverbrauchs in UWP-Apps

Der Profiler **Energieverbrauch** von Visual Studio hilft Ihnen, den Strom- und Energieverbrauch von UWP-Apps auf Tablets mit geringer Leistung zu analysieren, die die ganze Zeit oder zeitweilig von eigenen Akkus betrieben werden. Auf einem akkubetriebenen Gerät kann eine App, die zu viel Energie verbraucht, die Kundenzufriedenheit so sehr beeinträchtigen, dass sie von den Kunden möglicherweise sogar deinstalliert wird. Ein optimierter Energieverbrauch kann die Akzeptanz Ihrer App und deren Nutzung durch die Kunden erhöhen.

## <a name="what-the-energy-consumption-profiler-is-how-it-works-and-what-it-measures"></a>Beschreibung, Funktionsweise und Messwerte des Energieverbrauchsprofilers

Der Energieverbrauch-Profiler erfasst die Aktivitäten der Anzeige, CPU und Netzwerkverbindungen eines Geräts während einer Profilerstellungssitzung. Daraufhin generiert er Schätzungen der Energie, die für diese Aktivitäten verbraucht wird, sowie der Gesamtmenge an Energie, die für die Profilerstellungssitzung verwendet wird.

> [!NOTE]
> Der Energie-Profiler schätzt den Strom- und Energieverbrauch unter Anwendung eines Softwaremodells einer Standardreferenzgerätehardware, die repräsentativ für Tabletgeräte mit geringer Leistung ist, auf denen Ihre Anwendung möglicherweise ausgeführt wird. Um eine optimale Schätzung zu ermöglichen, wird empfohlen, die Profildaten auf einem Tabletgerät mit geringer Leistung zu sammeln.
>
> Auch wenn das Modell gute Schätzungen für eine Vielzahl an Geräten mit geringer Leistung liefert, sind die tatsächlichen Werte des Geräts, für das Sie ein Profil erstellen, wahrscheinlich anders. Anhand der Werte können Sie herausfinden, welche Anzeige-, CPU- und Netzwerkaktivitäten im Vergleich zur Nutzung anderer Ressourcen recht teuer sind und sich so möglicherweise besonders gut für Optimierungszwecke eignen.

Der Energieverbrauch-Profiler verwendet folgende Definitionen von *Strom* und *Energie*:

- *Strom* misst die Rate, mit der Kraft aufgewendet wird, um in einem bestimmten Zeitraum eine Leistung zu erbringen. In der Elektrik ist die Standardeinheit für Strom *Watt*. Diese wird als die Rate definiert, in der Leistung erbracht wird, wenn ein Ampere Spannung über eine elektrische Potenzialdifferenz von einem Volt fließt. Im Diagramm für den **Stromverbrauch** werden die Einheiten in Milliwatt **mW** (einem Tausendstel Watt) angezeigt.

   Da Strom fließt, hat es auch eine Richtung (die Leistung kann in einem Zeitraum ansteigen oder abnehmen) und eine Geschwindigkeit (die Menge, mit der die Leistung ansteigt oder abnimmt).

- *Energie* misst die Gesamtmenge der Leistung, entweder als Kapazität oder Potenzial, wie bei der Stromkapazität eines Akkus, oder als Gesamtsumme an Leistung über einen bestimmten Zeitraum. Die Einheit für Energie ist eine Wattstunde, d. h. die Menge an Strom eines Watts, die ständig eine Stunde lang angewendet wird. In der **Energiezusammenfassung** werden die Einheiten in Milliwattstunden **mW-h** dargestellt.

![Energiekapazität, Energieverbrauch, verbrauchte Energie insgesamt](../profiling/media/energyprof_capcitypowerused.png)

Ein vollständig geladener Akku in einem Tablet verfügt z. B. über eine bestimmte Menge an gespeicherte Energie. Während die Energie verwendet wird, um Aufgaben wie die Kommunikation über ein Netzwerk, die Berechnung von Werten oder die Anzeige von Grafiken auszuführen, verbraucht sich der Strom des Akkus in unterschiedlichen Raten. Während jedes beliebigen Zeitraum wird auch die Summe des verbrauchten Stroms von der Energie gemessen.

## <a name="identify-scenarios-with-user-marks"></a>Identifizieren von Szenarien mit Benutzermarkierungen
 Sie können den Profilerstellungsdaten *Benutzermarkierungen* hinzufügen, die bei der Identifizierung von Bereichen im Zeitachsenlineal hilfreich sind.

 ![Benutzermarkierungen auf der Zeitachse](../profiling/media/profilers_usermarktimeline.png "PROFILERS_UserMarkTimeline")

 Die Markierung wird bei Ausführung der Methode in der Zeitachse als orangefarbenes Dreieck angezeigt. Die Meldung und Uhrzeit werden als QuickInfo angezeigt, wenn Sie mit der Maus über die Markierung fahren. Wenn mindestens zwei Benutzermarkierungen nahe beieinander liegen, werden die Markierungen zusammengeführt und die QuickInfo-Daten werden kombiniert. Sie können auf der Zeitachse eine Vergrößerung durchführen, um die Markierungen zu trennen.

 **Hinzufügen von Markierungen zu C#-, Visual Basic- und C++-Code**

 Um eine Benutzermarkierung zu Code von C#, Visual Basic oder C++ hinzuzufügen, erstellen Sie zunächst ein <xref:Windows.Foundation.Diagnostics.LoggingChannel?displayProperty=fullName>-Objekt. Fügen Sie anschließend an den Positionen im Code, die Sie markieren möchten, Aufrufe von <xref:Windows.Foundation.Diagnostics.LoggingChannel.LogMessage%2A?displayProperty=nameWithType>-Methoden ein. Verwenden Sie in den Aufrufen [LoggingLevel.Information](xref:Windows.Foundation.Diagnostics.LoggingLevel) .

 Wenn die Methode ausgeführt wird, wird eine Benutzermarkierung zu den Profilerstellungsdaten zusammen mit einer Meldung hinzugefügt.

> [!NOTE]
> - <xref:Windows.Foundation.Diagnostics.LoggingChannel?displayProperty=nameWithType> implementiert die Schnittstelle <xref:Windows.Foundation.IClosable?displayProperty=nameWithType> (projiziert als <xref:System.IDisposable?displayProperty=nameWithType> in C# und VB). Rufen Sie <xref:Windows.Foundation.Diagnostics.LoggingChannel.Close%2A?displayProperty=nameWithType> (<xref:Windows.Foundation.Diagnostics.LoggingChannel.Dispose%2A?displayProperty=nameWithType> in C# und VB) auf, wenn Sie mit einem Protokollierungskanal fertig sind, um Verluste von Betriebssystemressourcen zu vermeiden.
> - Jeder offene Protokollierungschannel muss einen eindeutigen Namen haben. Wenn Sie versuchen, einen neuen Protokollierungschannel mit demselben Namen wie ein nicht gelöschter Channel zu erstellen, wird eine Ausnahme ausgelöst.

Beispielcode finden Sie im Windows SDK-Beispiel [LoggingSession](https://code.msdn.microsoft.com/windowsapps/LoggingSession-Sample-ccd52336).

::: moniker range="vs-2017"
**Hinzufügen von Markierungen zu JavaScript-Code**

Um Benutzermarkierungen hinzuzufügen, fügen Sie Ihrem Code an den gewünschten Positionen den folgenden Code hinzu:

```JavaScript
if (performance && performance.mark) {
    performance.mark(markDescription);
}
```

*markDescription* ist eine Zeichenfolge, die die Meldung enthält, die in der QuickInfo der Benutzermarkierung angezeigt werden soll.
::: moniker-end

## <a name="configure-your-environment-for-profiling"></a>Konfigurieren der Umgebung für die Profilerstellung
 Um gute Schätzungen zu erhalten, sollten Sie für den Energieverbrauch der App auf einem Gerät mit geringer Leistung, das durch Akkus betrieben wird, ein Profil erstellen. Da Visual Studio auf den meisten dieser Geräte nicht ausgeführt wird, müssen Sie den Visual Studio-Computer mithilfe der Visual Studio-Remotetools mit dem Gerät verbinden. Um eine Verbindung mit einem Remotegerät herzustellen, müssen Sie sowohl das Visual Studio-Projekt und als auch das Remotegerät konfigurieren. Weitere Informationen finden Sie unter [Ausführen von UWP-Apps auf einem Remotecomputer](../debugger/run-windows-store-apps-on-a-remote-machine.md).

> [!TIP]
> - Energieprofilerstellung auf dem UWP-Simulator oder auf dem Visual Studio-Computer wird nicht empfohlen. Die Profilerstellung auf dem tatsächlichen Gerät bietet weitaus realistischere Daten.
> - Erstellen Sie das Profil auf dem Zielgerät, während es über seine Akkus betrieben wird.
> - Schließen Sie alle anderen Anwendungen, die möglicherweise die gleichen Ressourcen verwenden (Netzwerk, CPU oder Anzeige).

## <a name="collect-energy-profile-data-for-your-app"></a>Sammeln von Energieprofildaten für die App

1. Wählen Sie im Menü **Debuggen** die Option **Diagnose ohne Debugging starten**.

     ![„Energieverbrauch“ im Leistungs-Profiler auswählen](../profiling/media/energyprof_diagnosticshub.png "ENERGYPROF_DiagnosticsHub")

2. Wählen Sie **Energieverbrauch** und dann **Starten** aus.

    > [!NOTE]
    > Wenn Sie den Profiler **Energieverbrauch** starten, wird möglicherweise das Fenster **Benutzerkontensteuerung** angezeigt, im dem Sie zur Eingabe Ihrer Berechtigung zur Ausführung von *VsEtwCollector.exe* aufgefordert werden. Klicken Sie auf **Ja**.

3. Führen Sie Ihre App aus, um Daten zu sammeln.

4. Um die Profilerstellung zu beenden, wechseln Sie zu Visual Studio zurück (ALT+TAB), und wählen Sie **Auflistung beenden** auf der Diagnosehubseite aus.

     ![Datensammlung beenden](../profiling/media/xamlprof_stopcollection.png "XAMLProf_StopCollection")

     Visual Studio analysiert die gesammelten Daten und zeigt die Ergebnisse an.

## <a name="collect-energy-profile-data-for-an-installed-app"></a>Sammeln von Energieprofildaten für eine installierte App
 Das Energieverbrauchstool kann nur für UWP-Apps ausgeführt werden, die von einer Visual Studio-Projektmappe gestartet oder vom Microsoft Store installiert werden. Wenn eine Projektmappe in Visual Studio geöffnet ist, lautet das Standardziel **Startprojekt**. So verwenden Sie eine installierte App als Ziel

1. Wählen Sie **Ziel ändern** und dann **Installierte App** aus.

2. Wählen Sie in der Liste **Installiertes App-Paket auswählen** das Ziel aus.

3. Wählen Sie auf der Seite „Leistungs-Profiler“ **Energieverbrauch** aus.

4. Wählen **Starten** , um die Profilerstellung zu starten.

   Um die Profilerstellung zu beenden, wechseln Sie zu Visual Studio zurück (ALT+TAB), und wählen Sie **Auflistung beenden** auf der Diagnosehubseite aus.

## <a name="analyze-energy-profile-data"></a>Analysieren der Energieprofildaten
 Die Energieprofildaten werden im Dokumentfenster von Visual Studio angezeigt:

 ![Berichtsseite des Energie-Profilers](../profiling/media/energyprof_all.png "ENERGYPROF_All")

|Bild|Beschreibung|
|-|-|
|![Schritt 1](../profiling/media/procguid_1.png "ProcGuid_1")|Die Berichtsdatei heißt Report *JJJJMMTT-HHMM*.diagsession. Sie können den Namen ändern, wenn Sie den Bericht speichern.|
|![Schritt 2](../profiling/media/procguid_2.png "ProcGuid_2")|Die Zeitachse zeigt die Länge der Profilerstellungssitzung, der App-Lebenszyklusaktivierungsereignisse und der Benutzermarkierungen an.|
|![Schritt 3](../profiling/media/procguid_3.png "ProcGuid_3")|Sie können den Bericht auf einen Teil der Zeitachse einschränken, indem Sie die blauen Striche ziehen, um einen Bereich der Zeitachse auszuwählen.|
|![Schritt 4](../profiling/media/procguid_4.png "ProcGuid_4")|Das Diagramm **Stromverbrauch** ist ein Liniendiagramm (mit mehreren Linien), in dem die Änderung in der Stromabgabe anzeigt wird, die durch eine Geräteressource während einer Profilerstellungssitzung verursacht wird. Der Energieverbrauchsprofiler verfolgt die von der CPU, von der Netzwerkaktivität und von der Bildschirmanzeige verwendete Energie.|
|![Schritt 5](../profiling/media/procguid_6.png "ProcGuid_6")|Das Diagramm **Ressourcen (Ein/Aus)**  stellt Details der Netzwerkenergiekosten dar. Die Leiste **Netzwerk** stellt die Zeit dar, während der die Netzwerkverbindung geöffnet war. Die untergeordnete Leiste **Datenübertragung** stellt die Zeit dar, in der die App Daten über das Netzwerk empfangen oder gesendet hat.|
|![Schritt 6](../profiling/media/procguid_6a.png "ProcGuid_6a")|In der **Zusammenfassung der Energieverwendung** wird der proportionale Betrag der gesamten Energie dargestellt, die in einem ausgewählten Zeitraum von der CPU, von der Netzwerkaktivität und von der Bildschirmanzeige verbraucht wurde.|

 **Analyse der Energieprofildaten**

 Suchen Sie einen Bereich, in dem die Ressourcenenergie sehr hoch war. Verknüpfen Sie den Höchstbereich mit der Funktionalität der App. Verwenden Sie dann die Steuerleisten auf der Zeitachse, um den Bereich zu vergrößern. Wenn Sie sich auf die Netzwerkauslastung konzentrieren möchten, erweitern Sie den Knoten **Netzwerk** im Diagramm **Ressourcen (Ein/Aus)**  . Sie können nun die Zeit, in der die Netzwerkverbindung aktiv war, mit der Zeit vergleichen, in der die App Daten über die Verbindung empfangen oder übertragen hat. Eine sehr wirksame Optimierungsmaßnahme ist, die Zeitspanne zu reduzieren, die das Netzwerk unnötigerweise geöffnet ist.

## <a name="optimize-energy-use"></a>Optimieren des Energieverbrauchs
 Zusätzlich zur Datenübertragung verursachen Netzwerkverbindungen auch Energiekosten für das Initialisieren, Verwalten und Schließen der Verbindung. Einige Netzwerke halten die Verbindung für einen bestimmten Zeitraum aufrecht, nachdem Daten gesendet bzw. empfangen wurden, damit über eine einzige Verbindung mehr Daten übertragen werden können. Im Bereich **Ressourcen (Ein/Aus)** können Sie die Methode überprüfen, mit der die App auf die Verbindung interagiert.

 ![Bereich „Ressourcen &#40;Ein&#47;Aus&#41;“](../profiling/media/energyprof_resources.png "ENERGYPROF_Resources")

 Wenn in den Leisten **Netzwerk** und **Datenübertragung** angezeigt wird, dass die Verbindung langfristig aktiv ist, damit eine Reihe kleiner Datenpakete nacheinander übertragen werden kann, können Sie die Daten im Batch im Rahmen einer Übertragung senden. Damit verringern Sie die Zeit, in der das Netzwerk aktiv ist, und und sparen somit Energiekosten.

 ![Zusammenfassungsbereich für Energieverbrauch](../profiling/media/energyprof_summary.png "ENERGYPROF_Summary")

 Über die Energiekosten der Anzeige haben Sie weniger Kontrolle. Die meisten Bildschirme benötigen mehr Energie, um helle Farben darzustellen als dunklere Farben. Deshalb ist eine Möglichkeit, Kosten zu reduzieren, einen dunklen Hintergrund zu verwenden.

## <a name="other-resources"></a>Weitere Ressourcen

- In den Abschnitten **Verbindungsstatus und Kostenverwaltung** für [C#, VB, C++ und XAML](/previous-versions/windows/apps/hh452985\(v\=win.10\)) werden die Windows-APIs beschrieben, die Informationen zur Netzwerkkonnektivität bereitstellen, die Ihre App nutzen kann, damit Sie die Kosten für den Netzwerkdatenverkehr reduzieren können.

   Mit dem Visual Studio-Simulator für UWP-Apps können Sie Datenverbindungseigenschaften der APIs für Netzwerkinformationen simulieren. Weitere Informationen finden Sie unter [Ausführen von UWP-Apps im Simulator](../debugger/run-windows-store-apps-in-the-simulator.md).

- Mit den Tools für die **CPU-Auslastung** können Sie die CPU-Last reduzieren, wenn diese von ineffizienten Funktionen verursacht wird. Weitere Informationen finden Sie unter [Profilerstellung für die Anwendungsleistung in Visual Studio](../profiling/beginners-guide-to-performance-profiling.md).

## <a name="see-also"></a>Siehe auch

- [Profilerstellung in Visual Studio](../profiling/index.yml)
- [Einführung in Profilerstellungstools](../profiling/profiling-feature-tour.md)