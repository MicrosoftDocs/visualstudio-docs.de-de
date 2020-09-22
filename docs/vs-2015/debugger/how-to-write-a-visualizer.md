---
title: 'Gewusst wie: Schreiben einer Schnellansicht | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers, writing
ms.assetid: 625a0d4f-abcc-43f2-9f8c-31c131a4378e
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ce50276e4e83a1a055294c8e2b6e09cd0f93d54d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841289"
---
# <a name="how-to-write-a-visualizer"></a>Gewusst wie: Schreiben einer Schnellansicht
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können für ein Objekt einer beliebigen verwalteten Klasse eine benutzerdefinierte Schnellansicht schreiben. Ausnahmen stellen <xref:System.Object> und <xref:System.Array> dar.  
  
> [!NOTE]
> In **Store** -apps werden nur die standardmäßigen Text-, HTML-, XML-und JSON-Visualisierungen unterstützt. Benutzerdefinierte (von Benutzern erstellte) Schnellansichten werden nicht unterstützt.  
  
 Die Architektur einer Debuggerschnellansicht besteht aus zwei Teilen:  
  
- Die *Debuggerseite* wird innerhalb des Visual Studio-Debuggers ausgeführt. Im debuggerseitigen Code wird die Benutzeroberfläche für die Schnellansicht erstellt und angezeigt.  
  
- Die *zu debuggende Seite* wird innerhalb des Prozesses ausgeführt, den Visual Studio debuggt (die *zu debuggende Komponente*).  
  
  Das Datenobjekt, das Sie visuell darstellen möchten (z. B. ein Zeichenfolgenobjekt), ist im zu debuggenden Prozess vorhanden. Die zu debuggende Seite muss dieses Datenobjekt zur Debuggerseite senden, die dieses Objekt dann über die erstellte Benutzeroberfläche anzeigen kann.  
  
  Die Debugger-Seite empfängt dieses Datenobjekt, das von einem *Objekt Anbieter* visualisiert werden soll, der die- <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> Schnittstelle implementiert. Die zu debuggende Seite sendet das Datenobjekt über die *Objekt Quelle*, die von abgeleitet ist <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> . Der Objektanbieter kann auch Daten an die Objektquelle zurücksenden. Dadurch können Sie eine Schnellansicht schreiben, die Daten bearbeitet und anzeigt. Der Objektanbieter kann überschrieben werden, um mit der Ausdrucksauswertung und somit der Objektquelle zu kommunizieren.  
  
  Die zu debuggende Seite und die Debuggerseite kommunizieren durch <xref:System.IO.Stream> miteinander. Es werden Methoden bereitgestellt für die Serialisierung eines Datenobjekts in einen <xref:System.IO.Stream> und für die Deserialisierung eines <xref:System.IO.Stream> zurück in ein Datenobjekt.  
  
  Der Code der zu debuggenden Seite wird mit dem DebuggerVisualizer-Attribut (<xref:System.Diagnostics.DebuggerVisualizerAttribute>) angegeben.  
  
  Um die Benutzeroberfläche der Schnellansicht auf Debuggerseite zu erstellen, müssen Sie eine Klasse erstellen, die von <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> erbt und die <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName>-Methode zum Anzeigen der Oberfläche überschreibt.  
  
  Sie können mit <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> Windows Forms, Dialogfelder und Steuerelemente über die Schnellansicht anzeigen lassen.  
  
  Die Unterstützung für generische Typen ist eingeschränkt. Sie können für ein Zielobjekt eines generischen Typs nur dann eine Schnellansicht schreiben, wenn es sich bei dem generischen Typ um einen offenen Typ handelt. Diese Einschränkung entspricht der Einschränkung bei Verwendung des `DebuggerTypeProxy`-Attributs. Weitere Informationen finden [Sie unter Verwenden des Attributs "tbuggertypeproxy](../debugger/using-debuggertypeproxy-attribute.md)".  
  
  In benutzerdefinierten Schnellansichten treten möglicherweise Sicherheitsprobleme auf. Weitere Informationen finden Sie unter [Sicherheitsüberlegungen für Visualisierungen](../debugger/visualizer-security-considerations.md).  
  
  Die folgenden Verfahren vermitteln Ihnen einen allgemeinen Überblick darüber, welche Schritte zum Erstellen einer Schnellansicht erforderlich sind. Eine ausführlichere Erläuterung finden Sie unter Exemplarische Vorgehensweise [: Schreiben einer Schnellansicht in c#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).  
  
### <a name="to-create-the-debugger-side"></a>So erstellen Sie die Debuggerseite  
  
1. Verwenden Sie <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>-Methoden, damit das visuell dargestellte Objekt auf der Debuggerseite ist.  
  
2. Erstellen Sie eine Klasse, die von <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> erbt.  
  
3. Überschreiben Sie die <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName>-Methode, um die Oberfläche anzuzeigen. Mit <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService>-Methoden können Sie Windows Forms, Dialogfelder und Steuerelemente als Teil der Oberfläche anzeigen.  
  
4. Übernehmen Sie <xref:System.Diagnostics.DebuggerVisualizerAttribute>, indem Sie diesem Attribut eine Schnellansicht (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>) zuweisen.  
  
### <a name="to-create-the-debuggee-side"></a>So erstellen Sie die zu debuggende Seite  
  
1. Übernehmen Sie <xref:System.Diagnostics.DebuggerVisualizerAttribute>, indem Sie diesem Attribut eine Schnellansicht (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>) und eine Objektquelle (<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>) zuweisen. Wenn Sie die Objektquelle weglassen, wird eine Standardobjektquelle verwendet.  
  
2. Wenn Sie möchten, dass die Schnellansicht Datenobjekte sowohl bearbeiten als auch anzeigen kann, müssen Sie die `TransferData`-Methode oder die `CreateReplacementObject`-Methode aus <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> überschreiben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen von benutzerdefinierten Visualisierungen](../debugger/create-custom-visualizers-of-data.md)   
 [Gewusst wie: Installieren einer Schnellansicht](../debugger/how-to-install-a-visualizer.md)   
 [Gewusst wie: Testen und Debuggen einer Schnellansicht](../debugger/how-to-test-and-debug-a-visualizer.md)   
 [Sicherheitsüberlegungen zu Schnellansichten](../debugger/visualizer-security-considerations.md)
