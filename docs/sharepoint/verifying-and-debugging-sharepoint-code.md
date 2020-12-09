---
title: Überprüfen und Debuggen von SharePoint-Code | Microsoft-Dokumentation
description: Überprüfen und Debuggen Sie SharePoint-Code. Verwenden Sie IntelliTrace, um vergangene Ereignisse und den aktuellen Status in der Projekt Mappe zu untersuchen. Verwenden Sie Komponententests, um sicherzustellen, dass ihre Methoden korrekt funktionieren.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- unit testing [SharePoint development in Visual Studio]
- IntelliTrace [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, IntelliTrace
- SharePoint development in Visual Studio, unit testing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ce891e40552c0f8927bfd4ce006b750b6e5f8a54
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914503"
---
# <a name="verify-and-debug-sharepoint-code"></a>Prüfen und Debuggen von SharePoint-Code
Mit IntelliTrace und Komponententests können Sie die SharePoint-Lösungen leichter debuggen und sicherstellen, dass jede Methode in ihnen ordnungsgemäß funktioniert. Sie können diese Funktionen für SharePoint-Projekte in Visual Studio verwenden, indem Sie die gleichen Prozeduren wie für andere Projekttypen befolgen.

## <a name="intellitrace"></a>IntelliTrace
Mit IntelliTrace können Sie nicht nur den aktuellen Zustand der SharePoint-Lösung bestimmen, sondern auch in der Vergangenheit aufgetretene Ereignisse sowie den Kontext, in dem sie aufgetreten sind. Sie können zwischen verschiedenen Zeitpunkten in Ihrer SharePoint-Lösung, an denen relevante Ereignisse erfasst wurden, hin und her navigieren und die Zustände und Werte von Variablen an jedem Punkt überprüfen. Indem Sie diese dynamische Navigation verwenden, können Sie die SharePoint-Lösungen schneller und einfacher debuggen, ohne zahlreiche Haltepunkte festzulegen. Sie können auch die Debugsitzung in einer IntelliTrace-Protokolldatei (*itrace*-Datei) speichern, Sie später in Visual Studio Enterprise öffnen und nach dem Absturz Debuggen ausführen. Die *itrace* -Datei enthält ausführliche Informationen darüber, wann und wo bestimmte SharePoint-Fehler aufgetreten sind, damit Sie leichter ermitteln können, was die Fehler verursacht. Bei den Informationen in der *itrace* -Datei handelt es sich um eine Teilmenge des gesamten Fehler Protokolls, das vom Unified Logging System (ULS) in SharePoint erstellt wird. Diese Informationen umfassen Ereignisse, die für SharePoint spezifisch sind, wie z. B. wenn ein Benutzerprofil geöffnet oder geschlossen wird und wenn Eigenschaften in einem SharePoint-Projekt geladen, gelesen oder geändert werden. Sie können konfigurieren, welche Ereignisse IntelliTrace aufzeichnet. Weitere Informationen finden Sie unter [Verwenden gespeicherter IntelliTrace-Daten](../debugger/using-saved-intellitrace-data.md).

Wenn ein Fehler in SharePoint auftritt, zeigt das Fehlerdialogfeld einen "Korrelations-ID"-Bezeichner für diesen speziellen Fehler an. Sie können auch Korrelations-IDs von Ereignissen erhalten, die in der *itrace* -Datei aufgelistet sind. Zum Anzeigen einer Liste aller Ereignisse, die mit einer bestimmten Korrelations-ID aufgetreten sind, können Sie die ID im Abschnitt **Analyse** der Seite IntelliTrace-Zusammenfassung eingeben. In diesem Abschnitt können Sie auswählen, ob nur die Namen der aufgetretenen Ereignisse angezeigt werden sollen oder die Namen der Ereignisse zusammen mit ihren Aufrufinformationen, wie z. B. der Funktionsname, die Beendigungs- und Einstiegspunkte, Parameter und Rückgabewerte.

Sie können Visual Studio-Ereignisse in IntelliTrace durch Drücken der **F5** -Taste erhalten. Um für SharePoint spezifische Ereignisse abzurufen, müssen Sie jedoch IntelliTrace-Daten in SharePoint-Lösungen sammeln, indem Sie Microsoft Monitoring Agent verwenden. Dieses Tool sammelt IntelliTrace-Daten und erstellt *itrace* -Dateien für Anwendungen, die außerhalb von Visual Studio bereitgestellt werden. Weitere Informationen finden Sie unter [IntelliTrace-Funktionen](../debugger/intellitrace-features.md) und [Verwenden des eigenständigen IntelliTrace-Sammlers](../debugger/using-the-intellitrace-stand-alone-collector.md).

## <a name="unit-test"></a>Komponententest
Sie können Fehler im Code leichter finden, indem Sie Unittests ausführen, bei denen Sie Testcode in Testmethoden schreiben und ausführen. Diese Methoden enthalten leere Variablen und eine Assert-Anweisung, die Sie verwenden können, um die Logik und die Funktionalität des Projekts auf Grundlage des SharePoint-Objektmodells zu überprüfen. Weitere Informationen finden Sie unter [Komponententests des Codes](../test/unit-test-your-code.md).

### <a name="support-for-microsoft-fakes-framework"></a>Unterstützung für Microsoft Fakes-Framework
SharePoint-Projekte unterstützen Microsoft Fakes, ein Isolationsframework, in dem Sie delegatbasierte Test-Stubs und -Shims in Anwendungen erstellen können, die auf .NET Framework basieren. Mithilfe des Fakes Framework können Sie Platzhalterimplementierungen in Ihren Komponententests erstellen, verwalten und einfügen. Diese Stubs und Shims isolieren die Komponententests von der Umgebung. Sie können Stubs erstellen, um Code zu testen, der Schnittstellen oder nicht versiegelte Klassen mit überschreibbaren Methoden verwendet. Sie können Shims erstellen, um hartcodierte Aufrufe von versiegelten Klassen mit statischen oder nicht überschreibbaren Methoden zu einer alternativen Shim-Implementierung umzuleiten. Sie können auch Delegate mit Stub-Typen und Shim-Typen verwenden, um das Verhalten einzelner Stub-Member dynamisch anzupassen. Weitere Informationen finden Sie [unter Isolieren von zu testenden Code mit Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md).

## <a name="related-articles"></a>Verwandte Artikel

|Titel|Beschreibung|
|-----------|-----------------|
|[IntelliTrace](../debugger/intellitrace.md)|Beschreibt, wie Visual Studio-Projektmappen mithilfe von IntelliTrace leichter zu debuggen sind.|
|[Exemplarische Vorgehensweise: Debuggen einer SharePoint-Anwendung mithilfe von IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)|Veranschaulicht, wie IntelliTrace verwendet wird, um Codefehler in einem SharePoint-Projekt zu suchen.|
|[Komponententests für Ihren Code](../test/unit-test-your-code.md)|Beschreibt, wie logische Fehler in Ihrem Code anhand von Komponententests gesucht werden.|

## <a name="see-also"></a>Weitere Informationen

- [Verbessern der Codequalität](../test/improve-code-quality.md)