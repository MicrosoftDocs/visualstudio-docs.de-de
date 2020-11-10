---
title: Möglichkeiten zum Debuggen von XSLT-Code
description: Erfahren Sie, wie Sie in Visual Studio mit dem XSLT-Debugger XSLT-Code debuggen können, indem Sie Code durchlaufen, Haltepunkte festlegen und XSLT-Ausführungszustände anzeigen.
ms.custom: SEO-VS-2020
ms.date: 03/05/2019
ms.topic: overview
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 5ad9ec70e5cd0f215dbb138db521dee09d722242
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047750"
---
# <a name="debugging-xslt"></a>Debugging von XSLT

Sie können XSLT-Code in Visual Studio debuggen. Der XSLT-Debugger unterstützt das Festlegen von Haltepunkten, das Anzeigen des XSLT-Ausführungszustands und weitere Vorgänge. Mit dem XSLT-Debugger können XSLT-Stylesheets oder XSLT-Anwendungen debuggt werden.

Sie können den Code zeilenweise ausführen, wobei Sie in einen Codeausdruck springen, einen Codeausdruck überspringen oder einen Codeausdruck wieder verlassen können, d. h., Sie haben die Möglichkeit, diesen Ausdruck bis zum Rücksprung auszuführen. Die bei der schrittweisen Codeausführung verwendeten Befehle des XSLT-Debuggers sind mit denen in den anderen Debuggern von Visual Studio identisch.

Wenn Sie das Debuggen starten, öffnet der XSLT-Debugger Fenster, in denen das Eingabedokument und die XSLT-Ausgabe angezeigt werden.

> [!NOTE]
> Der XSLT-Debugger ist nur in den Visual Studio-Editionen „Professional“ und „Enterprise“ verfügbar.

## <a name="debug-from-the-xml-editor"></a>Debuggen im XML-Editor

Sie können den Debugger starten, wenn Sie entweder ein Stylesheet oder eine XML-Eingabedatei im Editor geöffnet haben. Auf diese Weise können Sie bereits während des Entwerfens des Stylesheets debuggen.

1. Öffnen Sie das Stylesheet oder die XML-Datei in Visual Studio.

1. Wählen Sie **XSLT-Debuggen starten** im Menü **XML** , oder drücken Sie **ALT**+**F5**.

## <a name="debug-from-an-app-that-uses-xslt"></a>Debuggen aus einer App, die XSLT verwendet

Sie können beim Debuggen einer Anwendung XSLT schrittweise ausführen. Wenn Sie die bei einem <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=fullName>-Aufruf **F11** drücken, führt der Debugger den XSLT-Code schrittweise aus.

> [!NOTE]
> Die schrittweise Ausführung von XSLT aus der <xref:System.Xml.Xsl.XslTransform>-Klasse wird nicht unterstützt. Die <xref:System.Xml.Xsl.XslCompiledTransform>-Klasse ist der einzige XSLT-Prozessor, der beim Debuggen die schrittweise Ausführung von XSLT unterstützt.

### <a name="to-start-debugging-an-xslt-application"></a>So starten Sie das Debuggen einer XSLT-Anwendung

1. Legen Sie beim Instanziieren des <xref:System.Xml.Xsl.XslCompiledTransform>-Objekts im Code den `enableDebug`-Parameter auf `true` fest. Damit wird der XSLT-Prozessor angewiesen, dass beim Kompilieren des Codes Debuginformationen erstellt werden sollen.

1. Um den XSLT-Code schrittweise auszuführen, drücken Sie die Taste **F11**.

   Das XSLT-Stylesheet wird in einem neuen Dokumentfenster geladen, und der XSLT-Debugger wird gestartet.

   Alternativ können Sie dem Stylesheet einen Haltepunkt hinzufügen und die Anwendung ausführen.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird ein C#-XSLT-Programm dargestellt. Darin wird veranschaulicht, wie das XSLT-Debuggen aktiviert wird.

```csharp
using System;
using System.IO;
using System.Xml;
using System.Xml.Xsl;

namespace ConsoleApplication
{
  class Program
  {
    private const string sourceFile = @"c:\data\xsl_files\books.xml";
    private const string stylesheet = @"c:\data\xsl_files\below-average.xsl";
    private const string outputFile = @"c:\data\xsl_files\output.xml";

    static void Main(string[] args)
    {
      // Enable XSLT debugging.
      XslCompiledTransform xslt = new XslCompiledTransform(true);

      // Compile the style sheet.
      xslt.Load(stylesheet);

      // Execute the XSLT transform.
      FileStream outputStream = new FileStream(outputFile, FileMode.Append);
      xslt.Transform(sourceFile, null, outputStream);
    }
  }
}
```

## <a name="xslt-profiler"></a>XSLT-Profiler

Der [XSLT-Profiler](../xml-tools/xslt-profiler.md) ist ein Tool, mit dem Entwickler durch das Erstellen von ausführlichen XSLT-Leistungsberichten XSLT-Codeprobleme im Zusammenhang mit der Leistung messen, auswerten und beheben können. Weitere Informationen finden Sie unter [XSLT-Profiler](../xml-tools/xslt-profiler.md).

## <a name="see-also"></a>Siehe auch

- [Exemplarische Vorgehensweise: Debuggen eines XSLT-Stylesheets](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)
- [Ein erster Blick auf den Visual Studio-Debugger](../debugger/debugger-feature-tour.md)
- [Debuggrundlagen: Breakpoints (Haltepunkte)](../debugger/using-breakpoints.md)
