---
title: Erstellen von benutzerdefinierten Datenschnellansichten | Microsoft-Dokumentation
description: Visual Studio-Debuggerschnellansichten sind Komponenten, die Daten anzeigen. Hier erfahren Sie mehr über die sechs Standardschnellansichten sowie darüber, wie Sie andere Schnellansichten schreiben oder herunterladen können.
ms.custom: SEO-VS-2020
ms.date: 05/27/2020
ms.topic: conceptual
f1_keywords:
- vs.debug.visualizer.troubleshoot
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4c39fae399cd735d09218699f10c1eaead8e40ee
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560680"
---
# <a name="create-custom-data-visualizers"></a>Erstellen von benutzerdefinierten Datenschnellansichten

 Eine *Schnellansicht* ist Teil der Benutzeroberfläche des [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]-Debuggers, in der eine Variable oder ein Objekt auf eine für den jeweiligen Datentyp geeignete Weise angezeigt wird. Eine HTML-Schnellansicht interpretiert beispielsweise eine HTML-Zeichenfolge und zeigt das Ergebnis so an, wie es in einem Browserfenster angezeigt würde. Eine Bitmap-Schnellansicht interpretiert eine Bitmapstruktur und zeigt die zugehörige Grafik an. In einigen Schnellansichten können Sie die Daten nicht nur anzeigen, sondern auch bearbeiten.

 Der [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]-Debugger beinhaltet sechs Standardschnellansichten. Die Text-, HTML-, XML-und JSON-Schnellansichten funktionieren bei Zeichenfolgenobjekten. Die WPF-Strukturschnellansicht zeigt die Eigenschaften der visuellen Struktur eines WPF-Objekts an. Die DataSet-Schnellansicht funktioniert für DataSet-, DataView- und DataTable-Objekte.

Weitere Schnellansichten können von Microsoft, Drittanbietern und aus der Community heruntergeladen werden. Sie können auch eigene Schnellansichten schreiben und sie im [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]-Debugger installieren.

Im Debugger wird eine Schnellansicht durch das Lupensymbol ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Symbol der Schnellansicht") dargestellt. Das Symbol steht in einem **Datentipp**, im **Überwachungsfenster** des Debuggers oder im Dialogfeld **Schnellüberwachung** zur Verfügung. Wählen Sie dieses Symbol und dann die geeignete Schnellansicht für das entsprechende Objekt aus.

## <a name="write-custom-visualizers"></a>Schreiben von benutzerdefinierten Schnellansichten

 > [!NOTE]
 > Im Beispiel [Schnellansicht für eine SQLite-Instanz beim nativen Debuggen](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/SqliteVisualizer) ist beschrieben, wie Sie eine benutzerdefinierte Schnellansicht für nativen Code erstellen. Benutzerdefinierte Schnellansichten werden für UWP- und Windows 8.x-Apps nicht unterstützt.

Sie können für ein Objekt einer beliebigen verwalteten Klasse eine benutzerdefinierte Schnellansicht schreiben. Ausnahmen stellen <xref:System.Object> und <xref:System.Array> dar.

Die Architektur einer Debuggerschnellansicht besteht aus zwei Teilen:

- Die *Debuggerseite*, die im Visual Studio-Debugger ausgeführt wird, erstellt die Benutzeroberfläche der Schnellansicht und zeigt diese an.

- Die *zu debuggende Seite* wird innerhalb des Prozesses ausgeführt, den Visual Studio debuggt (die *zu debuggende Komponente*). Das darzustellende Datenobjekt (z. B. ein Zeichenfolgenobjekt) ist im zu debuggenden Prozess vorhanden. Die zu debuggende Seite sendet das Objekt an die Debuggerseite, die es auf der von Ihnen erstellten Benutzeroberfläche anzeigt.

Die Debuggerseite empfängt das Datenobjekt von einem *Objektanbieter*, der die <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>-Oberfläche implementiert. Die zu debuggende Seite sendet das Objekt über die *Objektquelle*, die von <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> abgeleitet wird.

Der Objektanbieter kann auch Daten an die Objektquelle zurücksenden. Dadurch können Sie eine Schnellansicht schreiben, die Daten bearbeiten kann. Sie überschreiben den Objektanbieter, um mit der Ausdrucksauswertung und der Objektquelle zu kommunizieren.

Die zu debuggende Seite und die Debuggerseite kommunizieren miteinander über <xref:System.IO.Stream>-Methoden, die ein Datenobjekt in einem <xref:System.IO.Stream> serialisieren und anschließend den <xref:System.IO.Stream> wieder in ein Datenobjekt konvertieren (deserialisieren).

Sie können für einen generischen Typ nur dann eine Schnellansicht schreiben, wenn es sich um einen offenen Typ handelt. Diese Einschränkung entspricht der Einschränkung bei Verwendung des `DebuggerTypeProxy`-Attributs. Einzelheiten finden Sie unter [Verwenden des DebuggerTypeProxy-Attributs](../debugger/using-debuggertypeproxy-attribute.md).

In benutzerdefinierten Schnellansichten treten möglicherweise Sicherheitsprobleme auf. Siehe [Sicherheitsüberlegungen zu Schnellansichten](../debugger/visualizer-security-considerations.md).

Die folgenden Schritte bieten einen allgemeinen Überblick über das Erstellen einer Schnellansicht. Ausführliche Anweisungen dazu finden Sie unter [Exemplarische Vorgehensweise: Schreiben einer Schnellansicht in C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md) oder [Exemplarische Vorgehensweise: Schreiben einer Schnellansicht in Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md).

### <a name="to-create-the-debugger-side"></a>So erstellen Sie die Debuggerseite

Zum Erstellen der Benutzeroberfläche der Schnellansicht auf Debuggerseite erstellen Sie eine Klasse, die von <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> erbt, und überschreiben die <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName>-Methode zum Anzeigen der Oberfläche. Mit <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> können Sie Windows Forms, Dialogfelder und Steuerelemente in der Schnellansicht anzeigen.

1. Verwenden Sie <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>-Methoden, damit das visuell dargestellte Objekt auf der Debuggerseite ist.

1. Erstellen Sie eine Klasse, die von <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> erbt.

1. Überschreiben Sie die <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName>-Methode, um die Oberfläche anzuzeigen. Mit den <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService>-Methoden können Sie Windows Forms, Dialogfelder und Steuerelemente auf der Oberfläche anzeigen.

4. Wenden Sie <xref:System.Diagnostics.DebuggerVisualizerAttribute> an, und lassen Sie es in der Schnellansicht anzeigen (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>).

### <a name="to-create-the-visualizer-object-source-for-the-debuggee-side"></a>So erstellen Sie die Schnellansichtobjektquelle für die zu debuggende Seite

Bearbeiten Sie im debuggerseitigen Code das Element <xref:System.Diagnostics.DebuggerVisualizerAttribute>, indem Sie ihm den zu visualisierenden Typ angeben (die zu debuggende Objektquelle) (<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>). Die `Target`-Eigenschaft legt die Objektquelle fest. Wenn Sie die Objektquelle weglassen, wird eine Standardobjektquelle für die Schnellansicht verwendet.

::: moniker range=">=vs-2019"
Der zu debuggende Code enthält die Objektquelle, die visualisiert wird. Das Datenobjekt kann Methoden von <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> überschreiben. Eine zu debuggende DLL ist erforderlich, wenn Sie eine eigenständige Schnellansicht erstellen möchten.
::: moniker-end

Im zu debuggenden Code:

- Damit Sie in der Schnellansicht Datenobjekte bearbeiten können, muss die Objektquelle von <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> erben und die Methoden `TransferData` oder `CreateReplacementObject` überschreiben.

- Wenn Sie in Ihrer Schnellansicht mehrere Ziele unterstützen müssen, können Sie die folgenden Zielframeworkmoniker (Target Framework Monikers, TFMs) in die zu debuggende Projektdatei einfügen.

   ```xml
   <TargetFrameworks>net20;netstandard2.0;netcoreapp2.0</TargetFrameworks>
   ```

   Dies sind die einzigen unterstützten TFMs.

## <a name="see-also"></a>Siehe auch

- [Exemplarische Vorgehensweise: Schreiben einer Schnellansicht in C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [Exemplarische Vorgehensweise: Schreiben einer Schnellansicht in Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)
- [How to: Installieren einer Schnellansicht](../debugger/how-to-install-a-visualizer.md)
- [How to: Testen und Debuggen einer Schnellansicht](../debugger/how-to-test-and-debug-a-visualizer.md)
- [Referenz zur Schnellansicht-API](../debugger/visualizer-api-reference.md)
- [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)