---
title: SDK der Nebenläufigkeitsschnellansicht | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie mit dem Concurrency Visualizer-SDK Ihren Code für das Anzeigen von Markern instrumentieren. Marker sind Symbole, die in Concurrency Visualizer angezeigt werden, um Ereignisse zu markieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.sdk.about
ms.assetid: 4b22cdf9-59b1-4c88-a6d8-1644a4a11e08
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f07dbfb0ca193f7bacbf2408fc26e622ffb037e1
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720981"
---
# <a name="concurrency-visualizer-sdk"></a>Parallelitätsschnellansichts-SDK
Sie können Ihren Quellcode instrumentieren und mithilfe des SDKs der Nebenläufigkeitsschnellansicht zusätzliche Informationen in der Nebenläufigkeitsschnellansicht anzeigen. Die zusätzlichen Daten lassen sich mit Phasen und Ereignissen in Ihrem Code zuordnen. Diese zusätzlichen Visualisierungen werden als *Marker* bezeichnet.  Eine exemplarische Vorgehensweise finden Sie unter [Introducing the Concurrency Visualizer SDK (Einführung in das Concurrency Visualizer SDK)](/archive/blogs/visualizeparallel/introducing-the-concurrency-visualizer-sdk).

## <a name="properties"></a>Eigenschaften
 Kennzeichen, Spannen und Meldungen verfügen über jeweils zwei Eigenschaften: Kategorie und Wichtigkeit. Im Dialogfeld [Erweiterte Einstellungen](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) können Sie diese Eigenschaften verwenden, um den Satz der angezeigten Marker zu filtern. Diese Eigenschaften beeinflussen außerdem die visuelle Darstellung der Marker. Die Größe der Kennzeichen beispielsweise gibt einen Hinweis auf die Wichtigkeit. Die Farbe weist auf die Kategorie hin.

## <a name="basic-usage"></a>Grundlegende Verwendung
 Die Nebenläufigkeitsschnellansicht macht einen Standardanbieter verfügbar, den Sie zum Generieren von Markern verwenden können. Der Anbieter ist bereits zusammen mit der Nebenläufigkeitsschnellansicht registriert. Sie müssen nichts weiter unternehmen, damit die Marker in der Benutzeroberfläche angezeigt werden.

### <a name="c-and-visual-basic"></a>C# und Visual Basic
 Verwenden Sie in C#, Visual Basic und anderem verwalteten Code den Standardanbieter, indem Sie Methoden in der [Marker](/previous-versions/hh694099(v=vs.140))-Klasse aufrufen. Dadurch werden vier Methoden zum Generieren von Markern verfügbar: [WriteFlag](/previous-versions/hh694185%28v%3dvs.140%29), [EnterSpan](/previous-versions/hh694205(v=vs.140)), [WriteMessage](/previous-versions/hh694161(v=vs.140)) und [WriteAlert](/previous-versions/hh694180(v=vs.140)). Für diese Funktionen gibt es mehrere Überladungen, je nachdem, ob Sie Standardwerte für die Eigenschaften verwenden möchten.  Die einfachste Überladung verwendet nur einen Zeichenfolgenparameter, der die Beschreibung des Ereignisses angibt. Die Beschreibung wird in den Berichten der Nebenläufigkeitsschnellansicht angezeigt.

##### <a name="to-add-sdk-support-to-a-c-or-visual-basic-project"></a>So fügen Sie einem C#- oder Visual Basic-Projekt Unterstützung für SDK hinzu

1. Wählen Sie in der Menüleiste **Analysieren**, **Nebenläufigkeitsschnellansicht** und **SDK zum Projekt hinzufügen** aus.

2. Wählen Sie das Projekt aus, in dem Sie auf das SDK zugreifen möchten, und wählen Sie anschließend die Schaltfläche **SDK zum ausgewählten Projekt hinzufügen** aus.

3. Fügen Sie Ihrem Code eine Import- oder Using-Anweisung hinzu.

    ```csharp
    using Microsoft.ConcurrencyVisualizer.Instrumentation;
    ```

    ```VB
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation
    ```

### <a name="c"></a>C++
 Erstellen Sie in C++ ein [marker_series Class](../profiling/marker-series-class.md)-Objekt, und verwenden Sie sie zum Aufrufen von Funktionen.  Die `marker_series`-Klasse macht drei Funktionen zum Generieren von Markern verfügbar: die [marker_series:: write_flag-Methode](../profiling/marker-series-write-flag-method.md), die [marker_series:: write_message-Methode](../profiling/marker-series-write-message-method.md) und die [marker_series:: write_alert-Methode](../profiling/marker-series-write-alert-method.md).

##### <a name="to-add-sdk-support-to-a-c-or-c-project"></a>So fügen Sie einem C++- oder C-Projekt Unterstützung für SDK hinzu

1. Wählen Sie in der Menüleiste **Analysieren**, **Nebenläufigkeitsschnellansicht** und **SDK zum Projekt hinzufügen** aus.

2. Wählen Sie das Projekt aus, in dem Sie auf das SDK zugreifen möchten, und wählen Sie anschließend die Schaltfläche **SDK zum ausgewählten Projekt hinzufügen** aus.

3. Schließen Sie in C++ `cvmarkersobj.h` ein. Schließen Sie in C `cvmarkers.h` ein.

4. Fügen Sie Ihrem Code eine Using-Anweisung hinzu.

    ```cpp
    using namespace Concurrency::diagnostic;
    ```

5. Erstellen Sie ein `marker_series`-Objekt, und übergeben Sie es dem `span`-Konstruktor.

    ```C++

    marker_series mySeries;
    span s(mySeries, _T("Span description"));

    ```

## <a name="custom-usage"></a>Benutzerdefinierte Verwendung
 Bei erweiterten Szenarios macht das SDK der Nebenläufigkeitsschnellansicht weitere Steuerelemente verfügbar.  Mit erweiterten Szenarios sind zwei wesentliche Konzepte verbunden: Markeranbieter und Markerserien. Markeranbieter sind verschiedene ETW-Anbieter (jeder verfügt über eine andere GUID). Markerserien sind serielle Kanäle von Ereignissen, die von einem Anbieter generiert werden. Sie können sie verwenden, um die Ereignisse zu organisieren, die von einem Markeranbieter generiert werden.

#### <a name="to-use-a-new-marker-provider-in-a-c-or-visual-basic-project"></a>So verwenden Sie einen neuen Markeranbieter in einem C#- oder Visual Basic-Projekt

1. Erstellen Sie ein [MarkerWriter](/previous-versions/hh694138(v=vs.140)) -Objekt.  Der Konstruktor nimmt eine GUID an.

2. Öffnen Sie zum Registrieren des Anbieters das Dialogfeld [Erweiterte Einstellungen](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) der Nebenläufigkeitsschnellansicht.  Wählen Sie die Registerkarte **Marker**, und wählen Sie anschließend die Schaltfläche **Neuen Anbieter hinzufügen** aus. Geben Sie im Dialogfeld [Erweiterte Einstellungen](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) die GUID ein, die verwendet wurde, um den Anbieter und eine Beschreibung des Anbieters zu erstellen.

#### <a name="to-use-a-new-marker-provider-in-a-c-or-c-project"></a>So verwenden Sie einen neuen Markeranbieter in einem C++- oder Visual Basic-Projekt

1. Verwenden Sie die `CvInitProvider`-Funktion, um PCV_PROVIDER zu initialisieren.  Der Konstruktor nimmt eine GUID* und einen PCV_PROVIDER\* an.

2. Öffnen Sie zum Registrieren des Anbieters das Dialogfeld [Erweiterte Einstellungen](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md).  Wählen Sie die Registerkarte **Marker**, und wählen Sie anschließend die Schaltfläche **Neuen Anbieter hinzufügen** aus. Geben Sie in diesem Dialogfeld die GUID ein, die verwendet wurde, um den Anbieter und eine Beschreibung des Anbieters zu erstellen.

#### <a name="to-use-a-marker-series-in-a-c-or-visual-basic-project"></a>So verwenden Sie eine neue Markerserie in einem C#- oder Visual Basic-Projekt

1. Um eine neue [MarkerSeries](/previous-versions/hh694127(v=vs.140)) zu verwenden, erstellen Sie sie zuerst mithilfe eines [MarkerWriter](/previous-versions/hh694138(v=vs.140))-Objekts. Generieren Sie anschließend Markerereignisse direkt aus der neuen Serie.

    ```csharp
    MarkerSeries series1 = myMarkerWriter.CreateMarkerSeries("Series 1");
    series1.WriteFlag("My flag");
    ```

    ```VB
    Dim series1 As New myMarkerWriter.CreateMarkerSeries("Series 1")
    series1.WriteFlag("My flag")
    ```

#### <a name="to-use-a-marker-series-in-a-c-project"></a>So verwenden Sie eine neue Markerserie in einem C++-Projekt

1. Erstellen eines `marker_series`-Objekts  Sie können Ereignisse aus dieser neuen Serie generieren.

    ```scr
    marker_series series;
    series.write_flag(_T("Hello world!"));
    ```

#### <a name="to-use-a-marker-series-in-a-c-project"></a>So verwenden Sie eine Markerserie in einem C-Projekt

1. Verwenden Sie die `CvCreateMarkerSeries`-Funktion, um eine PCV_MARKERSERIES zu erstellen.

    ```C++
    PCV_MARKERSERIES series;
    CvCreatemarkerSeries(myProvider, _T("My Series"), &series);
    CvWriteFlag(series, _T("Writing a flag"));
    ```

## <a name="see-also"></a>Siehe auch

|Titel|Beschreibung|
|-----------|-----------------|
|[C++-Bibliotheksreferenz](../profiling/cpp-library-reference.md)|Beschreibt die Nebenläufigkeitsschnellansicht-API für C++|
|[C Bibliotheksreferenz](../profiling/c-library-reference.md)|Beschreibt die Nebenläufigkeitsschnellansicht-API für C|
|[Instrumentation](/previous-versions/hh694104(v=vs.140))|Beschreibt die Nebenläufigkeitsschnellansicht-API für verwalteten Code|
|[Parallelitätsschnellansicht](../profiling/concurrency-visualizer.md)|Referenzinformationen zu den Ansichten und Berichten der Profilerstellungs-Datendateien, die mithilfe der Parallelitätsmethode generiert werden und Threadausführungsdaten enthalten.|