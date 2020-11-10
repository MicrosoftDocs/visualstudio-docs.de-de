---
title: 'Tutorial: Erweitern einer einfachen C#-Konsolen-App'
description: Hier erfahren Sie anhand einer exemplarischen Vorgehensweise, wie Sie eine C#-Konsolen-App in Visual Studio erstellen.
ms.custom: get-started
ms.date: 07/09/2020
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: ghogen
ms.author: ghogen
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4f2d5bf573da940c39790d6868a94d588e5efb7b
ms.sourcegitcommit: ae9145b32fc8e1e663e504c315a5df5dd302fee9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92918220"
---
# <a name="tutorial-extend-a-simple-c-console-app"></a>Tutorial: Erweitern einer einfachen C#-Konsolen-App

In diesem Tutorial erfahren Sie, wie Sie Visual Studio verwenden, um die Konsolen-App zu erweitern, die Sie im ersten Teil erstellt haben. Sie lernen einige der Features in Visual Studio kennen, die Sie für die tägliche Entwicklung benötigen, z. B. für die Verwaltung mehrerer Projekte und das Verweisen auf Drittanbieterpakete.

Wenn Sie den [ersten Teil](tutorial-console.md) dieser Reihe abgeschlossen haben, verfügen Sie bereits über die Calculator-Konsolen-App.  Sie können damit beginnen, das Projekt aus einem GitHub-Repository zu öffnen, um Teil 1 zu überspringen. Die C#-App „Calculator“ finden Sie im Repository [vs-tutorial-samples](https://github.com/MicrosoftDocs/vs-tutorial-samples). Sie können also einfach die Schritte im [Tutorial: Öffnen eines Projekts aus einem Repository](../tutorial-open-project-from-repo.md) ausführen, um zu beginnen.

## <a name="add-a-new-project"></a>Neues Projekt hinzufügen

In der Praxis umfasst Code viele Projekte, die in einer Projektmappe zusammenarbeiten. Als Nächstes fügen Sie ein weiteres Projekt zur Calculator-App hinzu. Dabei handelt es sich um eine Klassenbibliothek, die einige der Rechnerfunktionen bereitstellt.

1. In Visual Studio können Sie den allgemeinen Menübefehl **Datei** > **Hinzufügen** > **Neues Projekt** verwenden, um ein neues Projekt hinzuzufügen, jedoch können Sie auch mit der rechten Maustaste auf den Namen des vorhandenen Projekts klicken (der „Projektknoten“), um das Kontextmenü des Projekts zu öffnen. Dieses Kontextmenü enthält mehrere Möglichkeiten, mit denen Sie Funktionen zu Ihren Projekten hinzufügen können. Klicken Sie also mit der rechten Maustaste auf Ihren Projektknoten im **Projektmappen-Explorer** , und wählen Sie dann **Hinzufügen** > **Neues Projekt** aus.

1. Wählen Sie die C#-Projektvorlage **Klassenbibliothek (.NET Standard)** aus.

   ![Screenshot: Auswahl der Projektvorlage „Klassenbibliothek“](media/vs-2019/calculator2-add-project-dark.png)

1. Geben Sie den Projektnamen **CalculatorLibrary** ein, und klicken Sie dann auf **Erstellen**. Visual Studio erstellt das neue Projekt und fügt es zur Projektmappe hinzu.

   ![Screenshot: Projektmappen-Explorer mit hinzugefügtem Klassenbibliotheksprojekt „CalculatorLibrary“](media/vs-2019/calculator2-solution-explorer-with-class-library-dark2.png)

1. Benennen Sie die Datei *Class1.cs* in **CalculatorLibrary.cs** um. Sie können im **Projektmappen-Explorer** auf den Namen klicken, um diesen zu ändern, oder klicken Sie mit der rechten Maustaste auf den Namen, und wählen Sie dann **Umbenennen** aus, oder drücken Sie **F2**.

   Möglicherweise werden Sie gefragt, ob Sie Verweise auf `Class1` in der Datei umbenennen möchten. Es spielt keine Rolle, wie Sie antworten, da Sie den Code in einem zukünftigen Schritt ersetzen.

1. Jetzt müssen Sie einen Projektverweis hinzufügen, damit das erste Projekt die APIs nutzen kann, die von der neuen Klassenbibliothek zur Verfügung gestellt werden.  Klicken Sie mit der rechten Maustaste auf den Knoten **Verweise** im ersten Projekt, und wählen Sie dann **Projektverweis hinzufügen** aus.

   ![Screenshot: Menüelement „Projektverweis hinzufügen“](media/vs-2019/calculator2-add-project-reference-dark.png)

   Das Dialogfeld **Verweis-Manager** wird angezeigt. Mithilfe dieses Dialogfelds können Sie Verweise auf andere Projekte sowie Assemblys und COM DLLs hinzufügen, die Ihre Projekte benötigen.

   ![Screenshot: Dialogfeld „Verweis-Manager“](media/vs-2019/calculator2-ref-manager-dark.png)

1. Aktivieren Sie im Dialogfeld **Verweis-Manager** das Kontrollkästchen für das Projekt **CalculatorLibrary** , und klicken Sie dann auf **OK**.  Der Projektverweis wird unter dem Knoten **Projekte** im **Projektmappen-Explorer** angezeigt.

   ![Screenshot: Projektmappen-Explorer mit Projektverweis](media/vs-2019/calculator2-solution-explorer-with-project-reference-dark2.png)

1. Wählen Sie in der Datei *Program.cs* die Klasse `Calculator` und ihren gesamten Code aus, und drücken Sie **STRG+X** , um diesen aus der Datei auszuschneiden. Fügen Sie den Code dann in **CalculatorLibrary** in der Datei *CalculatorLibrary.cs* in den Namespace `CalculatorLibrary` ein. Erstellen Sie dann die Calculator-Klasse `public`, um ihn außerhalb der Bibliothek zur Verfügung zu stellen. Der Code in der Datei *CalculatorLibrary.cs* sollte nun dem folgenden Code ähneln:

   ```csharp
   using System;

    namespace CalculatorLibrary
    {
        public class Calculator
        {
            public static double DoOperation(double num1, double num2, string op)
            {
                double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

                // Use a switch statement to do the math.
                switch (op)
                {
                    case "a":
                        result = num1 + num2;
                        break;
                    case "s":
                        result = num1 - num2;
                        break;
                    case "m":
                        result = num1 * num2;
                        break;
                    case "d":
                        // Ask the user to enter a non-zero divisor.
                        if (num2 != 0)
                        {
                            result = num1 / num2;
                        }
                        break;
                    // Return text for an incorrect option entry.
                    default:
                        break;
                }
                return result;
            }
        }
    }
   ```

1. Das erste Projekt enthält einen Verweis, jedoch wird ein Fehler angezeigt, der angibt, dass der Calculator.DoOperation-Aufruf nicht aufgelöst werden kann. Das liegt daran, dass sich CalculatorLibrary in einem anderen Namespace befindet. Fügen Sie also den Namespace `CalculatorLibrary` hinzu, damit Sie über einen vollqualifizierten Verweis verfügen.

   ```csharp
   result = CalculatorLibrary.Calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   Versuchen Sie stattdessen, eine using-Anweisung am Anfang der Datei hinzuzufügen:

   ```csharp
   using CalculatorLibrary;
   ```

   Durch diese Änderung sollten Sie dazu in der Lage sein, den CalculatorLibrary-Namespace aus der Aufrufsite zu entfernen, jedoch liegt nun eine Mehrdeutigkeit vor. Ist `Calculator` die Klasse in CalculatorLibrary oder ist „Calculator“ der Namespace?  Benennen Sie den Namespace `CalculatorProgram` um, um diese Mehrdeutigkeit aufzulösen.

   ```csharp
   namespace CalculatorProgram
   ```

## <a name="reference-net-libraries-write-to-a-log"></a>Referenzieren von .NET-Bibliotheken: Schreiben in ein Protokoll

1. Angenommen, Sie möchten nun ein Protokoll aller Vorgänge hinzufügen und dieses in eine Textdatei schreiben. Die .NET-Klasse `Trace` stellt diese Funktionalität bereit. (Dies eignet auch für grundlegende Debugverfahren mit Ablaufverfolgung.)  Die „Trace“-Klasse befindet sich in „System.Diagnostics“, und Sie benötigen „System.IO“-Klassen wie `StreamWriter`, weshalb Sie zunächst die using-Anweisungen hinzufügen:

   ```csharp
   using System.IO;
   using System.Diagnostics;
   ```

1. Dementsprechend, wie die Trace-Klasse verwendet wird, müssen Sie einen Verweis auf die Klasse verwenden, der einem Filestream zugeordnet ist. Das bedeutet, der Rechner würde als Objekt besser funktionieren, also fügen Sie einen Konstruktor hinzu.

   ```csharp
   public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculator.log");
            Trace.Listeners.Add(new TextWriterTraceListener(logFile));
            Trace.AutoFlush = true;
            Trace.WriteLine("Starting Calculator Log");
            Trace.WriteLine(String.Format("Started {0}", System.DateTime.Now.ToString()));
        }

    public double DoOperation(double num1, double num2, string op)
        {
   ```

1. Außerdem müssen Sie die statische Methode `DoOperation` in eine Membermethode ändern.  Fügen Sie also Ausgaben zu jeder Berechnung für das Protokoll hinzu, sodass DoOperation dem folgenden Code ähnelt:

   ```csharp
   public double DoOperation(double num1, double num2, string op)
   {
        double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

        // Use a switch statement to do the math.
        switch (op)
        {
            case "a":
                result = num1 + num2;
                Trace.WriteLine(String.Format("{0} + {1} = {2}", num1, num2, result));
                break;
            case "s":
                result = num1 - num2;
                Trace.WriteLine(String.Format("{0} - {1} = {2}", num1, num2, result));
                break;
            case "m":
                result = num1 * num2;
                Trace.WriteLine(String.Format("{0} * {1} = {2}", num1, num2, result));
                break;
            case "d":
                // Ask the user to enter a non-zero divisor.
                if (num2 != 0)
                {
                    result = num1 / num2;
                    Trace.WriteLine(String.Format("{0} / {1} = {2}", num1, num2, result));
                }
                    break;
            // Return text for an incorrect option entry.
            default:
                break;
        }
        return result;
    }
   ```

1. Wenn Sie nun wieder die Datei „Program.cs“ öffnen, wird der statische Aufruf mit einer roten Wellenlinie gekennzeichnet. Erstellen Sie eine `calculator`-Variable, indem Sie die folgende Zeile unmittelbar vor der while-Schleife hinzufügen, um dies zu beheben:

   ```csharp
   Calculator calculator = new Calculator();
   ```

   Ändern Sie außerdem die Aufrufsite für `DoOperation` wie folgt:

   ```csharp
   result = calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

1. Führen Sie das Programm noch mal aus. Klicken Sie anschließend mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Ordner im Datei-Explorer öffnen** aus. Navigieren Sie dann im Datei-Explorer nach unten zum Ausgabeordner. Dabei handelt es sich möglicherweise um *bin/Debug/netcoreapp3.1*. Öffnen Sie die Datei *calculator.log*.

    ```output
    Starting Calculator Log
    Started 7/9/2020 1:58:19 PM
    1 + 2 = 3
    3 * 3 = 9
    ```

## <a name="add-a-nuget-package-write-to-a-json-file"></a>Hinzufügen eines NuGet-Pakets: Schreiben in eine JSON-Datei

1. Angenommen Sie möchten die Vorgänge nun in einem JSON-Format ausgeben. Dabei handelt es sich um ein beliebtes und portierbares Format zum Speichern von Objektdaten. Zum Implementieren dieser Funktionalität müssen Sie das NuGet-Paket „Newtonsoft.Json“ referenzieren. NuGet-Pakete sind die primäre Methode zur Verteilung von .NET-Klassenbibliotheken. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten **Verweise** für das CalculatorLibrary-Projekt, und wählen Sie dann **NuGet-Pakete verwalten** aus.

   ![Screenshot: „NuGet-Pakete verwalten“ im Kontextmenü](media/vs-2019/calculator2-manage-nuget-packages-dark2.png)

   Daraufhin wird der NuGet-Paket-Manager geöffnet.

   ![Screenshot: NuGet-Paket-Manager](media/vs-2019/calculator2-nuget-package-manager-dark.png)

1. Suchen Sie nach dem Paket „Newtonsoft.Json“, und klicken Sie auf **Installieren**.

   ![Screenshot: Informationen zum NuGet-Paket „Newtonsoft“](media/vs-2019/calculator2-nuget-newtonsoft-json-dark2.png)

   Das Paket wird heruntergeladen und zu Ihrem Projekt hinzugefügt, außerdem wird im **Projektmappen-Explorer** im Knoten „Verweise“ ein neuer Eintrag angezeigt.

1. Fügen Sie eine using-Anweisung für die Pakete „System.IO“ und „Newtonsoft.Json“ am Anfang der Datei *CalculatorLibrary.cs* hinzu.

   ```csharp
   using Newtonsoft.Json;
   ```

1. Ersetzen Sie nun den Konstruktor für Calculator durch den folgenden Code, und erstellen Sie das Memberobjekt „JsonWriter“:

   ```csharp
        JsonWriter writer;

        public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculatorlog.json");
            logFile.AutoFlush = true;
            writer = new JsonTextWriter(logFile);
            writer.Formatting = Formatting.Indented;
            writer.WriteStartObject();
            writer.WritePropertyName("Operations");
            writer.WriteStartArray();
        }
   ```

1. Ändern Sie die `DoOperation`-Methode, um den JSON-Writer-Code hinzuzufügen:

   ```csharp
        public double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.
            writer.WriteStartObject();
            writer.WritePropertyName("Operand1");
            writer.WriteValue(num1);
            writer.WritePropertyName("Operand2");
            writer.WriteValue(num2);
            writer.WritePropertyName("Operation");
            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    writer.WriteValue("Add");
                    break;
                case "s":
                    result = num1 - num2;
                    writer.WriteValue("Subtract");
                    break;
                case "m":
                    result = num1 * num2;
                    writer.WriteValue("Multiply");
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                        writer.WriteValue("Divide");
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            writer.WritePropertyName("Result");
            writer.WriteValue(result);
            writer.WriteEndObject();

            return result;
        }
   ```

1. Sie müssen eine Methode hinzufügen, um die JSON-Syntax zu beenden, sobald der Benutzer damit fertig ist, Vorgangsdaten einzugeben.

   ```csharp
    public void Finish()
    {
        writer.WriteEndArray();
        writer.WriteEndObject();
        writer.Close();
    }
   ```

1. Fügen Sie außerdem am Ende der Datei *Program.cs* einen Aufruf zum Beenden hinzu.

   ```csharp
            // And call to close the JSON writer before return
            calculator.Finish();
            return;
        }
   ```

1. Erstellen Sie die App, und führen Sie sie aus. Nachdem Sie einige Vorgänge eingegeben haben, schließen Sie die App ordnungsgemäß mithilfe des Befehls „n“.  Öffnen Sie nun die Datei „calculatorlog.json“. Es sollte in etwa Folgendes angezeigt werden:

   ```json
   {
    "Operations": [
        {
        "Operand1": 2.0,
        "Operand2": 3.0,
        "Operation": "Add",
        "Result": 5.0
        },
        {
        "Operand1": 3.0,
        "Operand2": 4.0,
        "Operation": "Multiply",
        "Result": 12.0
        }
    ]
   }
   ```

## <a name="debug-set-and-hit-a-breakpoint"></a>Debuggen: Festlegen und Erreichen eines Haltepunkts

Der Visual Studio-Debugger ist ein leistungsstarkes Tool, mit dem Sie Ihren Code Schritt für Schritt durchlaufen und die exakte Position von Programmierfehlern ermitteln können. Anschließend erhalten Sie Informationen darüber, welche Korrekturen im Code erforderlich sind. Visual Studio ermöglicht das Durchführen temporärer Änderungen, damit Sie die Ausführung des Programms fortsetzen können.

1. Klicken Sie in *Program.cs* auf den Rand links neben der folgenden Codezeile (alternativ können Sie das Kontextmenü öffnen und **Haltepunkt** > **Haltepunkt einfügen** auswählen oder **F9** drücken):

   ```csharp
   result = calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   Der anschließend angezeigte rote Punkt weist darauf hin, dass ein Haltepunkt eingefügt wurde. Mithilfe von Haltepunkten können Sie Ihre App anhalten und den Code untersuchen. Sie können einen Haltepunkt für jede beliebige Zeile mit ausführbarem Code festlegen.

   ![Screenshot: Festlegen eines Haltepunkts](media/vs-2019/calculator-2-debug-set-breakpoint.png)

1. Erstellen Sie die App, und führen Sie sie aus.

1. Geben Sie in der ausgeführten App einige Werte zur Berechnung ein:

   - Geben Sie als erste Zahl **8** ein, und drücken Sie die EINGABETASTE.
   - Geben Sie als zweite Zahl **0** ein, und drücken Sie die EINGABETASTE.
   - Geben Sie als Operator den Wert **d** ein.

   Die App pausiert an der Position des Haltepunkts, dies ist am links angezeigten gelben Pfeil und am hervorgehobenen Code erkennbar. Der hervorgehobene Code wurde noch nicht ausgeführt.

   ![Screenshot: Erreichen eines Haltepunkts](media/vs-2019/calculator-2-debug-hit-breakpoint.png)

   Nun, da die App angehalten wurde, können Sie den Status Ihrer Anwendung untersuchen.

## <a name="debug-view-variables"></a>Debuggen: Anzeigen von Variablen

1. Bewegen Sie im hervorgehobenen Code den Mauszeiger über Variablen wie z. B. `cleanNum1` und `op`. Es werden die aktuellen Werte für diese Variablen eingeblendet (`8` und `d`), die in DataTips angezeigt werden.

   ![Screenshot: Anzeige von DataTips](media/vs-2019/calculator-2-debug-view-datatip.png)

   Beim Debuggen ist es zur Problembehandlung oft entscheidend, zu prüfen, ob Variablen die erwarteten Werte enthalten.

2. Sehen Sie sich im unteren Bereich das Fenster **Lokal** an. (Klicken Sie auf **Debuggen** > **Fenster** > **Lokal** , falls es nicht geöffnet ist.)

   Im Fenster „Lokal“ werden alle Variablen angezeigt, die sich derzeit im Bereich befinden, gemeinsam mit dem zugehörigen Wert und Typ.

   ![Screenshot: Fenster „Lokal“](media/vs-2019/calculator-2-debug-locals-window.png)

3. Sehen Sie sich das Fenster **Auto** an.

   Das Fenster „Auto“ ähnelt dem Fenster **Lokal** , zeigt jedoch die Variablen direkt vor und nach der aktuellen Codezeile, an der Ihre App angehalten wurde.

   Als Nächstes führen Sie den Code im Debugger Anweisung für Anweisung aus. Dieses Vorgehen wird als *Einzelschrittausführung* bezeichnet.

## <a name="debug-step-through-code"></a>Debuggen: Schritt-für-Schritt-Ausführung des Codes

1. Drücken Sie **F11** (oder klicken Sie auf **Debuggen** > **Einzelschritt** ).

   Bei Verwendung des Befehls „Einzelschritt“ führt die App die aktuelle Anweisung aus und wechselt zur nächsten ausführbaren Anweisung (dies ist üblicherweise die nächste Codezeile). Der gelbe Pfeil auf der linken Seiten verweist jeweils auf die aktuelle Anweisung.

   ![Screenshot: Befehl „Einzelschritt“](media/vs-2019/calculator-2-debug-step-into.png)

   Sie haben soeben einen Einzelschritt in die Methode `DoOperation` der Klasse `Calculator` ausgeführt.

1. Betrachten Sie das Fenster **Aufrufliste** , um eine hierarchische Ansicht des Programmflows zu erhalten. (Klicken Sie auf **Debuggen** > **Fenster** > **Aufrufliste** , falls es nicht geöffnet ist.)

   ![Screenshot: Aufrufliste](media/vs-2019/calculator-2-debug-call-stack.png)

   Diese Ansicht zeigt die aktuelle Methode `Calculator.DoOperation`, markiert durch den gelben Pfeil. Die zweite Zeile zeigt die Funktion, die die Methode aus der Methode `Main` in *Program.cs* aufgerufen hat. Im Fenster **Aufrufliste** wird die Reihenfolge angezeigt, in der Methoden und Funktionen aufgerufen werden. Zusätzlich bietet es über das Kontextmenü Zugriff auf viele Debuggerfeatures, darunter beispielsweise **Zum Quellcode wechseln**.

1. Drücken Sie wiederholt **F10** (oder **Debuggen** > **Prozedurschritt** ), bis die App an der Anweisung `switch` angehalten wird.

   ```csharp
   switch (op)
   {
   ```

   Der Befehl „Prozedurschritt“ ähnelt dem Befehl „Einzelschritt“, weist aber folgenden Unterschied auf: Wenn die aktuelle Anweisung eine Funktion aufruft, führt der Debugger den Code in der aufgerufenen Funktion auf und hält die Ausführung erst an, wenn die Funktion zurückgegeben wird. Mit dem Befehl „Prozedurschritt“ kann der Code schneller durchlaufen werden, wenn Sie an einer bestimmten Funktion nicht interessiert sind.

1. Drücken Sie noch einmal **F10** , damit die App an der folgenden Codezeile angehalten wird.

   ```csharp
   if (num2 != 0)
   {
   ```

   Dieser Code überprüft, ob eine Division durch 0 durchgeführt wird. Beim Fortsetzen der App wird eine allgemeine Ausnahme (ein Fehler) ausgelöst. Nehmen wir aber an, Sie betrachten dies als Fehler und möchten etwas anderes tun, z. B. den tatsächlichen Rückgabewert in der Konsole anzeigen. Eine Option besteht darin, das Debuggerfeature namens „Bearbeiten und Fortfahren“ zu verwenden, um Änderungen am Code vorzunehmen und das Debuggen fortzusetzen. Es gibt aber noch einen anderen Trick, den Ausführungsflow temporär zu ändern.

## <a name="debug-test-a-temporary-change"></a>Debuggen: Testen einer temporären Änderung

1. Wählen Sie den gelben Pfeil aus, der im angehaltenen Zustand aktuell auf die Anweisung `if (num2 != 0)` zeigt, und ziehen Sie ihn auf die folgende Anweisung.

   ```csharp
   result = num1 / num2;
   ```

   Hierdurch überspringt die App die Anweisung `if` vollständig, sodass Sie sehen können, was bei einer Division durch 0 geschieht.

1. Drücken Sie **F10** , um die Codezeile auszuführen.

1. Bewegen Sie den Mauszeiger über die Variable `result`. Sie sehen, dass sie den Wert `Infinity` speichert.

   In C# ist `Infinity` das Ergebnis einer Division durch 0.

1. Drücken Sie **F5** (oder klicken Sie auf **Debuggen** > **Debuggen fortsetzen** ).

   Das Unendlichkeitssymbol wird in der Konsole als Ergebnis der mathematischen Operation angezeigt.

1. Schließen Sie die App ordnungsgemäß, indem Sie den Befehl „n“ verwenden.

## <a name="next-steps"></a>Nächste Schritte

Damit haben Sie das Tutorial erfolgreich abgeschlossen. Wenn Sie weitere Informationen erhalten möchten, fahren Sie mit den folgenden Tutorials fort.

> [!div class="nextstepaction"]
> [C#-Tutorials](/dotnet/csharp/tutorials/)

> [!div class="nextstepaction"]
> [Übersicht über die Visual Studio-IDE](/../visual-studio-ide.md)

## <a name="see-also"></a>Siehe auch

* [C#-IntelliSense](../../ide/visual-csharp-intellisense.md)
* [Tutorial: Debuggen von C#-Code mit Visual Studio](tutorial-debugger.md)
