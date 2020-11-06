---
title: Profilerstellung für die Leistung von SharePoint-Anwendungen | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Profiling.SilverlightWebPartOnly
- VS.SharePointTools.Profiling.DotNetTrustLevel
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, profiling
- performance testing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, performance testing
- profiling [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 13f2e3f5df236157550aa79af40f0cbc575eb8bf
ms.sourcegitcommit: ba966327498a0f67d2df2291c60b62312f40d1d3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2020
ms.locfileid: "93414411"
---
# <a name="profile-the-performance-of-sharepoint-applications"></a>Profilerstellung für die Leistung von SharePoint-Anwendungen

Wenn die SharePoint-Anwendungen langsam oder ineffizient ausgeführt werden, können Sie die Profilerstellungsfunktionen in Visual Studio verwenden, um problematischen Code und andere Elemente zu identifizieren. Mithilfe der Auslastungstestfunktion können Sie ermitteln, wie eine SharePoint-Anwendung unter Belastung ausgeführt wird, beispielweise wenn viele Benutzer gleichzeitig auf die Anwendung zugreifen. Durch Ausführung von Webleistungstests können Sie messen, wie die Anwendung im Web ausgeführt wird. Anhand von Tests der programmierten UI können Sie überprüfen, ob die ganze SharePoint-Anwendung, einschließlich der Benutzeroberfläche, ordnungsgemäß funktioniert. Mithilfe dieser Tests können Sie Leistungsprobleme identifizieren, bevor Sie die Anwendung bereitstellen.

## <a name="profile-tools-overview"></a>Übersicht über Profil Tools

Profilerstellung bezieht sich auf die Beobachtung und Erfassung des Leistungsverhaltens der Anwendung während sie ausgeführt wird. Durch die Profilerstellung für die Anwendung können Sie Probleme wie Engpässe, ineffizienten Code und Speicherbelegungsprobleme erkennen, die dazu führen, dass Anwendungen langsamer ausgeführt werden oder zu viel Arbeitsspeicher verwenden. Beispielsweise können Sie anhand der Profilerstellung Hotspots in Ihrem Code ermitteln, die Segmente des Codes sind, die häufig aufgerufen werden und die Gesamtleistung der Anwendung verlangsamen können. Nachdem Sie Hotspots identifiziert haben, können Sie sie häufig optimieren oder entfernen.

Sie können mehrere Profilerstellungstools in der integrierten Entwicklungsumgebung (IDE) verwenden, um diese Arten von Leistungsproblemen zu identifizieren und zu suchen. Diese Tools funktionieren für SharePoint-Projekte ebenso wie für andere Arten von Visual Studio-Projekten. Der Leistungs-Assistent der Profilerstellungstools führt Sie durch die Erstellung einer Leistungssitzung, die die angegebenen Tests verwendet. Eine Leistungs Sitzung ist ein Satz von Konfigurationsdaten, die für die Erfassung von Leistungsinformationen aus einer Anwendung verwendet werden, zusammen mit den Ergebnissen von mindestens einer Profilerstellung. Leistungs Sitzungen werden im Projektordner gespeichert, und Sie können Sie in **Leistungs-Explorer** anzeigen. Weitere Informationen finden Sie unter [Grundlagen zu Profilerstellungsmethoden](../profiling/understanding-performance-collection-methods.md).

Nachdem Sie eine Profilanalyse für die Anwendung erstellt und ausgeführt haben, werden die entsprechenden Leistungsdetails in einem Bericht bereitgestellt. Dieser Bericht kann Elemente wie ein Diagramm der CPU-Auslastung im Zeitverlauf, eine hierarchische Funktionsaufrufliste oder eine Aufrufstruktur enthalten. Der genaue Inhalt des Berichts kann, je nach ausgeführtem Testtyp, z. B. Sampling oder Instrumentierung, variieren. Weitere Informationen finden Sie unter [Übersicht über Profilerstellungstools Berichte](../profiling/performance-report-overview.md).

## <a name="performance-session-process"></a>Prozess der Leistungs Sitzung

Um die Profilerstellung einer Anwendung auszuführen, erstellen Sie zunächst eine Leistungssitzung mit dem Leistungs-Assistent der Profilerstellungstools. Wählen Sie in der Menüleiste **analysieren** , **Leistungs-Assistenten starten** aus. Nachdem Sie den Assistenten abgeschlossen haben, geben Sie die erforderlichen Informationen für die Leistungssitzung ein, z. B. die gewünschte Profilmethode und die Anwendung, für die Sie ein Profil erstellen möchten. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen eines Profils für eine Website oder Webanwendung mit dem Leistungs-Assistenten](../profiling/how-to-collect-performance-data-for-a-web-site.md). Alternativ können Sie Befehlszeilenoptionen verwenden, um eine Leistungssitzung zu installieren und auszuführen. Weitere Informationen finden Sie unter [Verwenden der Profilerstellungstools von der Befehlszeile aus](../profiling/using-the-profiling-tools-from-the-command-line.md). Wenn Sie jeden Aspekt einer Leistungs Sitzung manuell konfigurieren möchten, finden Sie weitere Informationen unter Gewusst [wie: Manuelles Erstellen von Leistungs Sitzungen mit dem Profilerstellungstools](../profiling/how-to-manually-create-performance-sessions.md). Sie können auch eine Leistungs Sitzung aus einem Komponenten Test erstellen, indem Sie im **Testergebnisse** Fenster das Kontextmenü für den Komponenten Test öffnen und dann **Leistungs Sitzung erstellen** auswählen.

Nachdem Sie eine Leistungssitzung eingerichtet haben, wird die Sitzungskonfiguration gespeichert, wird der Server so konfiguriert, dass Profilerstellungsdaten bereitgestellt werden, und wird die Anwendung ausgeführt. Während Sie die Anwendung verwenden, werden Leistungsdaten in eine Protokolldatei geschrieben. Leistungs Sitzungen werden in **Leistungs-Explorer** unter dem Ordner " **Ziele** " aufgeführt. Nachdem eine Leistungs Sitzung abgeschlossen wurde, wird der Bericht im Ordner **Berichte** in **Leistungs-Explorer** angezeigt. Um den Bericht anzuzeigen, öffnen Sie ihn in **Leistungs-Explorer**. Öffnen Sie das Kontextmenü in **Leistungs-Explorer** , und wählen Sie dann **Eigenschaften** aus, um die Eigenschaften einer Leistungs Sitzung anzuzeigen oder zu konfigurieren. Weitere Informationen zu bestimmten Eigenschaften einer Leistungs Sitzung finden Sie unter [Konfigurieren von Leistungs Sitzungen für Profilerstellungstools](../profiling/configuring-performance-sessions.md). Weitere Informationen zum Interpretieren der Ergebnisse einer Leistungs Sitzung finden Sie unter Analysieren von [Profilerstellungstools Daten](../profiling/analyzing-performance-tools-data.md).

## <a name="stress-test"></a>Belastungstest

Sie können die belastungsleistung Ihrer Anwendungen analysieren, indem Sie Auslastungs Tests und webleistungs Tests in Visual Studio erstellen. Wenn Sie einen Auslastungstest in Visual Studio erstellen, geben Sie eine Kombination von Faktoren, ein so genanntes Szenario, an, gegen das die Anwendung getestet werden soll. Diese Faktoren enthalten Auslastungsmuster, Testmischungsmodell, Testmischung, Netzwerkmischung und Browsermischung. Auslastungstestszenarien können sowohl Komponententests als auch Webleistungstests enthalten.

Abbildung 1: Beispiel für Auslastungstestergebnisse

![Diagramm für die Ausführung von Auslastungstests](../sharepoint/media/load-webgraphs.png "Diagramm für die Ausführung von Auslastungstests")

Webleistungstests simulieren die mögliche Interaktion eines Endbenutzers mit einer SharePoint-Anwendung. Sie können webleistungs Tests erstellen, indem Sie HTTP-Anforderungen in einer Browsersitzung oder mithilfe der **webleistungs Test** -Aufzeichnung aufzeichnen. Die Webanforderungen werden in der **Webleistungstest-Editor** angezeigt, nachdem die Browsersitzung abgeschlossen wurde. Anschließend können Sie die Ergebnisse im **webleistungs Testergebnisse Viewer** Debuggen. Sie können webleistungs Tests auch manuell erstellen, indem Sie die **Webleistungstest-Editor** verwenden.

## <a name="test-user-interfaces"></a>Testen von Benutzeroberflächen

Tests der programmierten UI steuern automatisch die SharePoint-Anwendung über die Benutzeroberfläche (UI). Diese Tests decken UI-Steuerelemente, wie Schaltflächen und Menüs, ab, um zu überprüfen, ob sie ordnungsgemäß funktionieren. Diese Art von Tests sind besonders bei der Validierung oder einer anderen Logik der Benutzeroberfläche hilfreich, beispielsweise einer Webseite. Sie können auch Tests der codierten UI verwenden, um manuelle Tests zu automatisieren. Sie erstellen Tests der programmierten UI für die SharePoint-Anwendungen auf die gleiche Weise wie Sie Tests für andere Anwendungstypen erstellen. Weitere Informationen finden Sie unter [Testen von SharePoint 2010-Anwendungen mit Tests](/previous-versions/visualstudio/visual-studio-2015/test/testing-sharepoint-2010-applications-with-coded-ui-tests?preserve-view=true&view=vs-2015)der programmierten UI.

## <a name="related-topics"></a>Verwandte Themen

|Titel|Beschreibung|
|-----------|-----------------|
|[Exemplarische Vorgehensweise: Profilerstellung einer SharePoint-Anwendung](../sharepoint/walkthrough-profiling-a-sharepoint-application.md)|Veranschaulicht, wie eine Samplingsprofilanalyse für eine SharePoint-Anwendung ausgeführt wird.|
|[Testen der Leistung Ihrer App vor der Freigabe](/azure/devops/test/load-test/run-performance-tests-app-before-release?view=vsts&preserve-view=true)|Beschreibt, wie Auslastungstests erstellt werden, mit deren Hilfe Sie Belastungstests für SharePoint-Anwendungen durchführen.|
|[Komponententests für Ihren Code](../test/unit-test-your-code.md)|Beschreibt, wie logische Fehler in Ihrem Code anhand von Komponententests gesucht werden.|
|[Testen von SharePoint 2010-Anwendungen mit Tests der programmierten UI](/previous-versions/visualstudio/visual-studio-2015/test/testing-sharepoint-2010-applications-with-coded-ui-tests?preserve-view=true&view=vs-2015)|Beschreibt, wie die Benutzeroberfläche Ihrer SharePoint-Anwendungen getestet wird.|

## <a name="see-also"></a>Weitere Informationen

- [Erstellen und Debuggen von SharePoint-Lösungen](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Verbessern der Codequalität](../test/improve-code-quality.md)