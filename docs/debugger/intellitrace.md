---
title: IntelliTrace | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie IntelliTrace zum Aufzeichnen und Überwachen des Ausführungsverlaufs Ihres Codes in Visual Studio verwenden. Sie können spezifische Ereignisse aufzeichnen, verwandten Code untersuchen und Fehler debuggen.
ms.custom: SEO-VS-2020
ms.date: 09/19/2018
ms.topic: conceptual
f1_keywords:
- vs.historicaldebug.overview
helpviewer_keywords:
- debugger, recording execution history
- debugging, recording execution history
- IntelliTrace [Visual Studio ALM]
- IntelliTrace, debugging applications
- debugger, (See also IntelliTrace [Visual Studio ALM])
- debugging, (See also IntelliTrace [Visual Studio ALM])
- IntelliTrace
- IntelliTrace, debugging after a crash
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 518043a38f3a0f6945840a36a1f7fcade5a313d7
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149000"
---
# <a name="intellitrace-for-visual-studio-enterprise-c-visual-basic-c"></a>IntelliTrace für Visual Studio Enterprise (C#, Visual Basic, C++)

Durch die Verwendung von IntelliTrace zum Erfassen und Nachverfolgen Ihres Codeausführungsverlaufs können Sie beim Debuggen Ihrer Anwendung Zeit sparen. Sie können leicht Fehler finden, da mit IntelliTrace Folgendes möglich ist:

- Aufzeichnen bestimmter Ereignisse

- Sie können ähnlichen Code sowie im Fenster **Lokal** während der Debugger-Ereignisse angezeigte Daten, und Funktionsaufrufinformationen überprüfen.

- Schwer nachstellbare oder während der Bereitstellung auftretende Fehler beim Debuggen

Sie können IntelliTrace in der Visual Studio Enterprise Edition verwenden(jedoch nicht in der Professional oder Community Edition).

## <a name="what-do-you-want-to-do"></a>Wie möchten Sie vorgehen?

|Szenario|Titel|
|-|-|
|**Meine Anwendung mit IntelliTrace debuggen:**<br /><br /> – Vergangene Ereignisse auflisten.<br />– Aufrufinformationen mit vergangenen Ereignissen anzeigen.<br />– Die IntelliTrace-Sitzung speichern.<br />– Die Daten steuern, die IntelliTrace erfasst.|- [Untersuchen von vorherigen App-Zuständen mithilfe des IntelliTrace-Features „Schritt zurück“ in Visual Studio (Visual Studio Enterprise)](../debugger/view-historical-application-state.md)<br />- [Exemplarische Vorgehensweise: Verwenden von IntelliTrace](../debugger/walkthrough-using-intellitrace.md)<br />- [IntelliTrace-Funktionen](../debugger/intellitrace-features.md)<br />- [Verlaufsbezogenes Debuggen](../debugger/historical-debugging.md)|
|**Erfassen IntelliTrace-Daten aus bereitgestellten Anwendungen**|- [Verwenden des eigenständigen IntelliTrace-Collectors](../debugger/using-the-intellitrace-stand-alone-collector.md)|
|**Starten Sie das Debuggen von einer IntelliTrace-Protokolldatei (ITRACE-Datei).**|- [Verwenden gespeicherter IntelliTrace-Daten](../debugger/using-saved-intellitrace-data.md)|

## <a name="what-apps-can-i-debug-with-intellitrace"></a><a name="IntelliTraceSupport"></a>Welche Anwendungen kann ich mit IntelliTrace debuggen?

| Supportebene| Anwendungstypen |
|---------------------| - |
| **Vollständige Unterstützung** | – Visual Basic- und Visual C#-Anwendungen, die .NET Framework 2.0 oder höher verwenden.<br/>Sie können die meisten Anwendungen debuggen, einschließlich ASP.NET, Microsoft Azure, Windows Forms, WCF, WPF, Windows Workflow, SharePoint 2010, SharePoint 2013 und 64-Bit-Anwendungen.<br/>Weitere Informationen zum Debuggen von SharePoint-Anwendungen mit IntelliTrace finden Sie unter [Exemplarische Vorgehensweise: Debuggen einer SharePoint-Anwendung mithilfe von IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md).<br/> Weitere Informationen zum Debuggen von Microsoft Azure-Apps mit IntelliTrace finden Sie unter [Debuggen eines veröffentlichten Azure-Clouddiensts mit Visual Studio und IntelliTrace](../azure/vs-azure-tools-intellitrace-debug-published-cloud-services.md). |
| **Eingeschränkte Unterstützung** | - Von C++-Apps für Windows wird das Anzeigen von Momentaufnahmen mithilfe des IntelliTrace-Features „Schritt zurück“ unterstützt. Nur Debugger- und Ausnahmeereignisse werden unterstützt.<br />- .NET Core- und ASP.NET Core-Apps werden nur für bestimmte Ereignisse (MVC-Controller-, ADO.NET- und HttpClient-Ereignisse) beim lokalen Debuggen unterstützt. Der eigenständige Collector wird für .NET Core- und ASP.NET Core-Apps nicht unterstützt.<br />– F#-Apps versuchsweise<br />- UWP-Apps werden nur für Ereignisse unterstützt. |
| **Nicht unterstützt** | - Andere Sprachen und Skripts<br />- Windows-Dienste, Silverlight, Xbox oder Windows Mobile-Apps |

> [!NOTE]
> Wenn Sie einen bereits aktiven Prozess debuggen möchten, können Sie nur IntelliTrace-Ereignisse, aber keine Aufrufinformationen erfassen. Es ist nur eine Anfügung an einen 32-Bit- oder 64-Bit-Prozess auf dem lokalen Computer möglich. Ereignisse, die vor dem Anfügen an den Prozess auftreten, werden nicht erfasst.

## <a name="why-debug-with-intellitrace"></a><a name="IntelliTraceVSTraditional"></a> Warum sollte ich mit IntelliTrace debuggen?

Herkömmliche oder *Live*-Debugvorgänge zeigen nur den aktuellen Status der Anwendung mit eingeschränkten Informationen zu vergangenen Ereignissen. Sie müssen diese Ereignisse entweder auf Grundlage des aktuellen Anwendungsstatus ableiten, oder Sie müssen diese Ereignisse neu erstellen, indem Sie die Anwendung erneut ausführen.

IntelliTrace erweitert diese herkömmlichen Debuggenvorgänge, indem bestimmte Ereignisse und Daten an diesen Zeitpunkten erfasst werden. Somit können Sie auch ohne Neustart der Anwendung die Ereignisse verfolgen und finden auch bereits aufgetretene Fehler. IntelliTrace ist standardmäßig während des herkömmlichen Debuggen aktiviert, sodass Daten automatisch und unsichtbar erfasst werden. Sie können also zwischen dem herkömmlichen Debuggen und dem IntelliTrace-Debuggen problemlos wechseln, um die aufgezeichneten Informationen abzurufen. Weitere Informationen finden Sie unter [IntelliTrace-Features (C#, Visual Basic, C++)](../debugger/intellitrace-features.md) sowie unter [Welche Daten erfasst IntelliTrace?](#WhatData).

IntelliTrace hilft Ihnen außerdem beim Debuggen von Fehlern, die schwer reproduzierbar sind oder die bei der Bereitstellung auftreten. Sie können IntelliTrace-Daten sammeln und in einer IntelliTrace-Protokolldatei (ITRACE-Datei) speichern. Eine ITRACE-Datei enthält Details über Ausnahmen, Leistungsereignisse, Webanforderungen, Testdaten, Threads, Module und andere Systeminformationen. Sie können diese Datei in Visual Studio Enterprise öffnen, ein Element auswählen und das Debuggen mit IntelliTrace starten. Sie können also zu jedem beliebigen Ereignis in der Datei gehen und bestimmte Einzelheiten über die Anwendung an diesem Punkt anzeigen lassen.

IntelliTrace-Daten können aus den folgenden Quellen gespeichert werden:

- Eine IntelliTrace-Sitzung in Visual Studio 2015 Enterprise oder einer höheren Version oder in Vorgängerversionen von Visual Studio Ultimate.

- Auf IIS gehostete ASP.NET-Anwendungen oder SharePoint 2010- und SharePoint 2013-Anwendungen, die bei der Bereitstellung ausgeführt werden, wenn Sie Microsoft Monitoring Agent verwenden, entweder allein oder mit System Center 2012. Weitere Informationen finden Sie unter [Verwenden des eigenständigen IntelliTrace-Collectors (C#, Visual Basic)](../debugger/using-the-intellitrace-stand-alone-collector.md) sowie unter [Überwachen mit Microsoft Monitoring Agent](/previous-versions/system-center/system-center-2012-R2/dn465153(v=sc.12)).

Im Folgenden werden einige Beispiele aufgeführt, die den Nutzen von IntelliTrace beim Debuggen veranschaulichen:

- Ihre Anwendung hat eine Datendatei beschädigt, doch Sie wissen nicht, wann das passiert ist.

  Ohne IntelliTrace müssten Sie den Code auf alle möglichen Dateizugriffe durchsuchen, Haltepunkte für diese Zugriffe festlegen und die Anwendung dann erneut ausführen, um die Stelle ausfindig zu machen, an der das Problem aufgetreten ist. Mit IntelliTrace können Sie alle erfassten Dateizugriffsereignisse und bestimmte Details über die Anwendung finden, wenn Ereignisse auftreten.

- Eine Ausnahme tritt auf.

  Ohne IntelliTrace erhalten Sie zwar eine Meldung über eine Ausnahme, aber Sie bekommen kaum Informationen über die Ereignisse, die zu der Ausnahme geführt haben. Sie können in der Aufrufliste die Kette der Aufrufe untersuchen, die zur Ausnahme geführt haben, aber Sie können nicht die Ereignisabfolge während dieser Aufrufe einsehen. Mit IntelliTrace können Sie die Ereignisse untersuchen, die vor der Ausnahme auftraten.

- Ein Fehler oder ein Absturz geschieht in einer bereitgestellten Anwendung.

  Für Microsoft Azure-basierte Apps können Sie die IntelliTrace-Datenerfassung vor der Veröffentlichung Ihrer App konfigurieren. Während die App ausgeführt wird, werden von IntelliTrace Daten in einer iTrace-Datei gespeichert. Weitere Informationen finden Sie unter [Debuggen eines veröffentlichten Azure-Clouddiensts mit Visual Studio und IntelliTrace](../azure/vs-azure-tools-intellitrace-debug-published-cloud-services.md).

  Für ASP.NET-Webanwendungen, die auf IIS 7.0, 7,5 und 8,0 gehostet werden, sowie für SharePoint 2010- oder SharePoint 2013-Anwendungen verwenden Sie Microsoft Monitoring Agent, entweder alleine oder mit System Center 2012, um IntelliTrace-Daten in einer ITRACE-Datei zu speichern.

  Dies ist hilfreich, wenn Sie Probleme mit Apps in der Bereitstellung diagnostizieren möchten. Weitere Informationen finden Sie unter [Verwenden des eigenständigen IntelliTrace-Collectors (C#, Visual Basic)](../debugger/using-the-intellitrace-stand-alone-collector.md).

## <a name="what-data-does-intellitrace-collect"></a><a name="WhatData"></a> Welche Daten erfasst IntelliTrace?

**Erfassen von Ereignisinformationen**

Standardmäßig erfasst IntelliTrace nur IntelliTrace-Ereignisse: Debuggerereignisse, Ausnahmen, .NET Framework-Ereignisse und andere Systemereignisse, die beim Debuggen hilfreich sein können. Sie können die IntelliTrace-Ereignisse auswählen, die Sie sammeln möchten. Debuggerereignisse und -ausnahmen werden allerdings immer gesammelt. Weitere Informationen finden Sie unter [IntelliTrace-Features (C#, Visual Basic, C++)](../debugger/intellitrace-features.md).

- **Debuggerereignisse**

  IntelliTrace zeichnet alle Ereignisse auf, die im Visual Studio-Debugger stattfinden. Der Anwendungsstart ist beispielsweise ein Debuggerereignis. Weitere Debuggerereignisse sind Beenden-Ereignissen, die zur Unterbrechung der Anwendungsausführung führen. Zum Beispiel wenn das Programm einen Haltepunkt oder einen Ablaufverfolgungspunkt erreicht oder einen **Schritt** befehl ausführt.

  Zur Verbesserung der Leistung wird von IntelliTrace standardmäßig nicht jeder mögliche Wert für ein Debuggerereignis aufgezeichnet. Stattdessen werden folgende Werte aufgezeichnet:

  - Werte im Fenster **Lokal**. Lassen Sie das Fenster **Lokal** geöffnet, um diese Werte anzuzeigen.

  - Werte im Fenster **Auto**, wenn das Fenster **Auto** geöffnet ist

  - Werte in DataTips, die angezeigt werden, wenn Sie den Mauszeiger über eine Variable im Quellcodefenster bewegen, um den Wert anzuzeigen. IntelliTrace erfasst keine Werte in angehefteten DataTips.

    Wenn der Modus für IntelliTrace-Ereignisse und Momentaufnahmen aktiviert ist, wird von IntelliTrace bei jedem **Breakpoint** und **Debuggerschritt** eine Momentaufnahme des Anwendungsprozesses erstellt. Dadurch werden Werte im **Lokalfenster**, **Auto-Fenster** und **Überwachungsfenster** aufgezeichnet, und zwar unabhängig davon, ob die Fenster geöffnet sind. Werte in angehefteten Datentipps werden ebenfalls erfasst.

- **Ausnahmen**

  IntelliTrace zeichnet den Ausnahmetyp und die Meldung für diese Ausnahmen auf:

  - Bearbeitete Ausnahmen, in denen die Ausnahme ausgelöst und abgefangen wird

  - Ausnahmefehler

- **.NET Framework-Ereignisse**

  IntelliTrace zeichnet standardmäßig die häufigsten .NET Framework-Ereignisse auf. Für ein Ereignis vom Typ <xref:System.Windows.Forms.CheckBox.CheckedChanged?displayProperty=nameWithType> werden von IntelliTrace beispielsweise der Kontrollkästchenzustand und der Text erfasst.

- **SharePoint 2010- und SharePoint 2013-Anwendungsereignisse**

  Sie können Benutzerprofilereignisse und eine Teilmenge von einheitlichen Ereignissen des Protokollierungs-Systems (ULS) für SharePoint 2010- und 2013-Anwendungen erfassen, die außerhalb von Visual Studio ausgeführt werden. Sie können diese Ereignisse in einer ITRACE-Datei speichern. Erfordert mindestens Visual Studio Enterprise 2015, eine Vorgängerversion von Visual Studio Ultimate oder [Microsoft Monitoring Agent](https://www.microsoft.com/download/details.aspx?id=40316) im Modus **Ablaufverfolgung**.

  Wenn Sie die ITRACE-Datei öffnen, geben Sie eine SharePoint-Korrelations-ID ein, um die entsprechenden Webanforderung zu suchen, die aufgezeichneten Ereignisse anzuzeigen und das Debuggen von einem bestimmten Ereignis aus zu starten. Wenn die Datei Ausnahmefehler enthält, können Sie eine Korrelations-ID auswählen, um das Debuggen einer Ausnahme zu starten.

  Thema

  - [Verwenden des eigenständigen IntelliTrace-Collectors](../debugger/using-the-intellitrace-stand-alone-collector.md)

  - [Verwenden gespeicherter IntelliTrace-Daten](../debugger/using-saved-intellitrace-data.md)

  - [Exemplarische Vorgehensweise: Debuggen einer SharePoint-Anwendung mithilfe von IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)

**Erfassen von Momentaufnahmen**

Sie können IntelliTrace so konfigurieren, dass bei jedem Breakpoint und Debuggerschritt Momentaufnahmen erfasst werden. Von IntelliTrace wird bei jeder Momentaufnahme der vollständigen Anwendungszustand aufgezeichnet, sodass Sie komplexe Variablen anzeigen und Ausdrücke auswerten können.

> [!NOTE]
> Das Erfassen von Momentaufnahmen wird vom [eigenständigen IntelliTrace-Collector](../debugger/using-the-intellitrace-stand-alone-collector.md) nicht unterstützt.

Weitere Informationen finden Sie unter [Untersuchen von vorherigen App-Zuständen mithilfe des IntelliTrace-Features „Schritt zurück“ in Visual Studio (Visual Studio Enterprise)](../debugger/view-historical-application-state.md).

**Erfassen von Funktionsaufrufinformationen**

Sie können IntelliTrace so konfigurieren, dass Aufrufinformationen für Funktionen gesammelt werden. Anhand dieser Informationen können Sie den Aufruflistenverlauf anzeigen und die Aufrufe im Code vorwärts und rückwärts durchlaufen. Für jeden Funktionsaufruf werden die folgenden Daten von IntelliTrace aufgezeichnet:

- Funktionsname
- Werte primitiver Datentypen, die als Parameter an Funktionseinstiegspunkten übergeben und an Funktionsendpunkten zurückgegeben werden
- Werte von automatischen Eigenschaften, wenn sie gelesen oder geändert werden
- Zeiger auf untergeordnete Objekte auf der obersten Ebene ohne Werte (außer NULL oder keine)

> [!NOTE]
> IntelliTrace erfasst nur die ersten 256 Objekte in Arrays und die ersten 256 Zeichen von Zeichenfolgen.

Weitere Informationen finden Sie unter [Untersuchen Ihrer App mit verlaufsbezogenem Debuggen von IntelliTrace in Visual Studio (C#, Visual Basic, C++)](../debugger/historical-debugging-inspect-app.md).

**Erfassen von Modulinformationen**

Um zu steuern, wie viel Aufrufsinformationen IntelliTrace erfasst, legen Sie nur die Module fest, die für Sie von Bedeutung sind. Das kann dabei helfen, die Anwendungsleistung während der Erfassung zu verbessern. Weitere Informationen finden Sie im Artikel zu IntelliTrace-Features im Abschnitt [Steuern der Anzahl der von IntelliTrace aufgezeichneten Aufrufinformationen](../debugger/intellitrace-features.md#ControlCallData).

## <a name="will-intellitrace-slow-down-my-application"></a><a name="AffectPerformance"></a> Verlangsamt IntelliTrace meine Anwendung?

Standardmäßig werden von IntelliTrace nur Daten für ausgewählte IntelliTrace-Ereignisse gesammelt. Das kann, abhängig von der Struktur und der Organisation Ihres Codes, eventuell die Anwendung verlangsamen. Wenn IntelliTrace beispielsweise oft ein Ereignis protokolliert, kann dies die Anwendung verlangsamen. Erwägen Sie, eine Umgestaltung Ihrer Anwendung vorzunehmen.

Das Sammeln der Aufrufsinformationen verlangsamt die App möglicherweise erheblich. Außerdem erhöht sich dadurch möglicherweise die Größe aller auf dem Datenträger gespeicherter IntelliTrace-Protokolldateien (ITRACE-Dateien). Um diese Auswirkungen zu minimieren, sammeln Sie Aufrufinformationen nur für die Module, die Sie interessieren.  Um die maximale Größe der ITRACE-Dateien zu ändern, wechseln Sie zu **Tools**, **Optionen**, **IntelliTrace**, **Erweitert**.

### <a name="blogs"></a>Blogs

[Microsoft DevOps](https://devblogs.microsoft.com/devops/)

### <a name="forums"></a>Foren

[Visual Studio-Diagnose](https://social.msdn.microsoft.com/Forums/en-US/home)