---
title: Verwenden von Breakpoints im Debugger | Microsoft-Dokumentation
description: Hier erfahren Sie mehr über Breakpoints, eine der wichtigsten Debuggingtechniken. Der Artikel behandelt Breakpointaktionen, Ablaufverfolgungspunkte, Bedingungen und vieles mehr.
ms.custom: SEO-VS-2020
ms.date: 06/30/2020
ms.topic: how-to
f1_keywords:
- vs.debug.breakpointswin
- vs.debug.disassembly.insert
- vs.debug.sourcewin.edit
- vs.debug.file
- vs.debug.breakpt.new
- vs.debug.whenbreakpointishit
- vs.debug.breakpt.location.address
- vs.debug.breakpt.constraints
- vs.debug.breakpoints.delete
- vs.debug.breakpt.location.data
- vc.breakpoints
- vs.debug.breakpt.condition
- vs.debug.breakpt.location.function
- vs.debug.breakpoints
- vs.debug.menu.insert
- vs.debug.filenames
- vs.debug.breakpt.action
- vs.debug.sourcewin.insert
- vs.debug.address
- vs.debug.data
- vs.debug.func
- vs.debug.breakpt.location.file
helpviewer_keywords:
- breakpoints, about breakpoints
ms.assetid: 020b2e97-3b3e-4b2c-872d-b5c6025e120e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c8487482b1d87ba87dfc3a8b1e07be1360227a2f
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150443"
---
# <a name="use-breakpoints-in-the-visual-studio-debugger"></a>Verwenden von Breakpoints im Visual Studio-Debugger

Breakpoints sind eines der wichtigsten Debugverfahren in der Toolbox eines Entwicklers. Sie können Breakpoints an den Stellen festlegen, an denen der Debugger die Ausführung unterbrechen soll. Sie können sich dann beispielsweise den Status von Codevariablen an einem bestimmten Breakpoint ansehen oder die Aufrufliste anzeigen.  Wenn Sie eine Warnung oder ein Problem bei der Verwendung von Breakpoints auflösen möchten, finden Sie unter [Troubleshooting für Breakpoints im Visual Studio-Debugger](../debugger/troubleshooting-breakpoints.md) weitere Informationen.

> [!NOTE]
> Wenn die Aufgabe oder das Problem, das Sie lösen möchten, bekannt ist, Sie aber nicht sicher sind, welche Art von Breakpoint Sie dazu verwenden müssen, finden Sie unter [Häufig gestellte Fragen: Suchen Ihrer Debugfunktion](../debugger/find-your-debugging-task.md#pause-running-code) weitere Informationen.

## <a name="set-breakpoints-in-source-code"></a><a name="BKMK_Overview"></a> Festlegen von Breakpoints im Quellcode

Sie können einen Haltepunkt für jede beliebige Zeile mit ausführbarem Code festlegen. Im folgenden C#-Code könnte Sie beispielsweise einen Breakpoint in der Codezeile mit der Variablenzuweisung (`int testInt = 1`), der `for`-Schleife oder im Code innerhalb der `for`-Schleife festlegen. Sie können einen Breakpoint bei Methodensignaturen, Namespace-, Klassen- oder Variablendeklarationen festlegen, wenn keine Zuweisung und keine Getter oder Setter vorhanden sind.

Wenn Sie einen Breakpoint im Quellcode festlegen möchten, klicken Sie links neben einer Codezeile auf den Rand. Sie können auch die entsprechende Zeile auswählen und **F9** drücken, auf **Debuggen**  >  **Haltepunkt ein/aus** klicken oder mit der rechten Maustaste klicken und **Haltepunkt**  >  **Haltepunkt einfügen** auswählen. Der Breakpoint wird als roter Punkt am linken Rand angezeigt.

Bei den meisten Programmiersprachen, einschließlich C#, werden Breakpoints und die aktuelle Ausführungszeile automatisch hervorgehoben. Bei C++-Code können Sie die Hervorhebung für Breakpoints und die aktuelle Zeile aktivieren, indem Sie auf **Extras** (oder **Debuggen**) > **Optionen**  >  **Debuggen**  >   **Bei Haltepunkten und aktueller Anweisung gesamte Quellcodezeile markieren (nur C++)** klicken.

![Festlegen eines Breakpoints](../debugger/media/basicbreakpoint.png "Einfacher Breakpoint")

Beim Debuggen wird die Ausführung am Breakpoint angehalten, bevor der Code in der entsprechenden Zeile ausgeführt wird. Das Breakpointsymbol wird als gelber Pfeil angezeigt.

Beim Breakpoint im folgenden Beispiel bleibt der Wert von `testInt` 1. Der Wert hat sich also nicht geändert, seit die Variable initialisiert wurde (sie wurde auf einen Wert von 1 festgelegt), da die Anweisung in gelb nicht ausgeführt wurde.

![Am Breakpoint angehaltene Ausführung](../debugger/media/breakpointexecution.png "Breakpointausführung")

Wenn der Debugger am Breakpoint anhält, können Sie den aktuellen Status der App anzeigen, einschließlich [Variablenwerten](../debugger/debugger-feature-tour.md#inspect-variables-with-data-tips) und der [Aufrufliste](../debugger/how-to-use-the-call-stack-window.md).

Im Folgenden finden Sie einige allgemeine Hinweise für das Arbeiten mit Breakpoints.

- Bei einem Breakpoint handelt es sich um eine Umschaltfläche. Sie können auf sie klicken, **F9** drücken oder **Debuggen**  >  **Haltepunkt ein/aus** verwenden, um den Breakpoint zu löschen oder ihn neu einzufügen.

- Wenn Sie einen Breakpoint deaktivieren möchten, ohne ihn zu löschen, bewegen Sie den Mauszeiger darauf, oder klicken Sie mit der rechten Maustaste auf ihn, und klicken Sie dann auf **Haltepunkt deaktivieren**. Deaktivierte Breakpoints werden am linken Rand oder im Fenster **Haltepunkte** ausgegraut angezeigt. Wenn Sie einen Breakpoint wieder aktiveren möchten, bewegen Sie den Mauszeiger darauf, oder klicken Sie mit der rechten Maustaste darauf, und klicken Sie auf **Haltepunkt aktivieren**.

- Wenn Sie Bedingungen und Aktionen festlegen, Bezeichnungen hinzufügen und bearbeiten oder einen Breakpoint exportieren möchten, klicken Sie mit der rechten Maustaste darauf, und wählen Sie den entsprechenden Befehl aus, oder bewegen Sie den Mauszeiger darauf, und klicken Sie auf das Symbol **Einstellungen**.

## <a name="breakpoint-actions-and-tracepoints"></a><a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a> Haltepunktaktionen und Ablaufverfolgungspunkte

Beim *Ablaufverfolgungspunkt* handelt es sich um einen Haltepunkt, der eine Meldung im Fenster **Ausgabe** ausgibt. Ein Ablaufverfolgungspunkt kann wie eine temporäre Überwachungsanweisung in der Programmiersprache fungieren und unterbricht die Codeausführung nicht. Sie erstellen einen Ablaufverfolgungspunkt, indem Sie eine spezielle Aktion im Fenster **Haltepunkteinstellungen** festlegen. Eine detaillierte Anleitung finden Sie unter [Protokollinformationen im Ausgabefenster mithilfe von Ablaufverfolgungspunkten in Visual Studio](../debugger/using-tracepoints.md).

## <a name="breakpoint-conditions"></a>Haltepunktbedingungen

Sie können steuern, wann und wo ein Haltepunkt ausgeführt wird, indem Sie Bedingungen festlegen. Die Bedingung kann ein beliebiger gültiger Ausdruck sein, der vom Debugger erkannt wird. Weitere Informationen zu gültigen Ausdrücken finden Sie unter [Expressions in the Debugger (Ausdrücke im Debugger)](../debugger/expressions-in-the-debugger.md).

**So legen Sie eine Breakpointbedingung fest:**

1. Klicken Sie mit der rechten Maustaste auf das Breakpointsymbol und dann auf **Bedingungen**. Alternativ können Sie den Mauszeiger auf das Breakpointsymbol bewegen, auf das Symbol **Einstellungen** klicken, und dann im Fenster **Haltepunkteinstellungen** auf **Bedingungen** klicken.

   Sie können Bedingungen auch im Fenster **Haltepunkte** festlegen, indem Sie mit der rechten Maustaste auf einen Breakpoint klicken, auf **Einstellungen** und dann auf **Bedingungen** klicken.

   ![Haltepunkteinstellungen](../debugger/media/breakpointsettings.png "Breakpointeinstellungen")

2. Klicken Sie im Dropdown auf **Bedingter Ausdruck**, **Trefferanzahl** oder **Filter**, und legen Sie den Wert entsprechend fest.

3. Klicken Sie auf **Schließen**, oder drücken Sie **STRG**+**EINGABETASTE**, um das Fenster **Haltepunkteinstellungen** zu schließen. Alternativ können Sie im Fenster **Haltepunkte** auf **OK** klicken, um das Dialogfeld zu schließen.

Breakpoints, für die Bedingungen festgelegt wurden, werden im Quellcode und im Fenster **Haltepunkte** mit einem **+** -Symbol angezeigt.

<a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>
### <a name="create-a-conditional-expression"></a>Erstellen eines bedingten Ausdrucks

Wenn Sie **Bedingter Ausdruck** auswählen, können Sie zwischen zwei Bedingungen auswählen: **ist „True“** oder **Bei Änderung**. Wählen Sie **ist „True“** aus, um die Ausführung zu unterbrechen, wenn der Ausdruck erfüllt ist. Wenn Sie **Bei Änderung** auswählen, wird die Ausführung unterbrochen, wenn sich der Wert des Ausdrucks geändert hat.

Im folgenden Beispiel wird der Breakpoint nur beachtet, wenn der Wert von `testInt` **4** ist:

![Breakpointbedingung „ist ‚True‘“](../debugger/media/breakpointconditionistrue.png "Breakpoint „ist ‚True‘“")

Im folgenden Beispiel wird der Breakpoint nur beachtet, wenn sich der Wert von `testInt` ändert:

![Breakpoint „Bei Änderung“](../debugger/media/breakpointwhenchanged.png "Breakpoint „Bei Änderung“")

Wenn Sie eine Haltepunktbedingung mit ungültiger Syntax festlegen, wird sofort eine Warnmeldung angezeigt. Wenn Sie eine Haltepunktbedingung mit gültiger Syntax aber ungültiger Semantik angeben, wird beim ersten Erreichen des Haltepunkts eine Warnmeldung angezeigt. In beiden Fällen unterbricht der Debugger die Ausführung beim Erreichen des ungültigen Breakpoints. Der Haltepunkt wird nur übersprungen, wenn die Bedingung gültig ist mit `false`bewertet wird.

>[!NOTE]
> Für das Feld **Bei Änderung** betrachtet der Debugger die erste Auswertung nicht als Änderung. Der Breakpoint wird also bei der ersten Auswertung nicht beachtet.

<a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>
### <a name="use-object-ids-in-conditional-expressions-c-and-f-only"></a>Verwenden von Objekt-IDs in bedingten Ausdrücken (nur C# und F#)

 Manchmal möchten Sie sich nur das Verhalten eines bestimmten Objekts ansehen. Zum Beispiel wollen Sie herausfinden, warum ein Objekt mehrfach in eine Sammlung eingefügt wurde. In C# und F# können Sie Objekt-IDs für bestimmte Instanzen von [Verweistypen](/dotnet/csharp/language-reference/keywords/reference-types) erstellen und in Haltepunktbedingungen verwenden. Die Objekt-ID wird von den Debugdiensten der CLR (Common Language Runtime) generiert und dem Objekt zugeordnet.

**So erstellen Sie eine Objekt-ID:**

1. Legen Sie im Code an einer beliebigen Stelle nach der Erstellung des Objekts einen Breakpoint fest.

2. Starten Sie das Debuggen, und klicken Sie auf **Debuggen**  >  **Fenster**  >  **Lokale Variablen** oder **ALT**+**4**, um das Fenster **Lokale Variablen** zu öffnen, wenn die Ausführung am Breakpoint angehalten wird.

   Suchen Sie im Fenster **Lokale Variablen** nach der spezifischen Objektinstanz, klicken Sie mit der rechten Maustaste darauf, und klicken Sie dann auf **Objekt-ID erstellen**.

   Sie sollten ein **$** und eine Zahl im **Lokalfenster** einen Haltepunkt festlegen. Dies ist die Objekt-ID.

3. Fügen Sie einen neuen Breakpoint an der Stelle hinzu, die untersucht werden soll, z. B. an der Stelle, an der das Objekt der Sammlung hinzugefügt werden soll. Klicken Sie mit der rechten Maustaste auf den Haltepunkt, und wählen Sie **Bedingungen** aus.

4. Verwenden Sie die Objekt-ID im Feld **Bedingter Ausdruck**. Wenn beispielsweise die Variable `item` das Objekt ist, das der Sammlung hinzugefügt werden soll, wählen Sie **ist „True“** aus und geben **item == $\<n>** ein, wobei \<n> der Nummer der Objekt-ID entspricht.

   Die Ausführung wird an dem Punkt unterbrochen, an dem dieses Objekt der Auflistung hinzugefügt werden soll.

   Wenn Sie die Objekt-ID löschen möchten, können Sie mit der rechten Maustaste im Fenster **Lokale Variablen** auf die Variable und dann auf **Objekt-ID löschen** klicken.

> [!NOTE]
> Objekt-IDs erstellen Weak-Verweise und verhindern nicht, dass das Objekt in die Garbage Collection aufgenommen wird. Sie gelten nur für die aktuelle Debugsitzung.

### <a name="set-a-hit-count-condition"></a>Festlegen einer Trefferanzahlbedingung

Wenn Sie vermuten, dass eine Schleife im Code nach einer bestimmten Anzahl von Iterationen ein fehlerhaftes Verhalten aufweist, können Sie einen Breakpoint festlegen, um die Ausführung nach einer bestimmten Trefferanzahl anzuhalten, anstatt mehrmals **F5** zu drücken, um die Iteration zu erreichen.

Klicken Sie im Fenster **Haltepunkteinstellungen** unter **Bedingungen** auf die Option **Trefferanzahl**, und geben Sie dann die Anzahl an Iterationen an. Im folgenden Beispiel wird der Breakpoint so festgelegt, dass er bei jeder weiteren Iteration beachtet wird:

![Breakpoint „Trefferanzahl“](../debugger/media/breakpointhitcount.png "Breakpoint „Trefferanzahl“")

### <a name="set-a-filter-condition"></a>Festlegen einer Filterbedingung

Sie können einen Haltepunkt so einschränken, dass dieser nur auf bestimmten Geräten oder in angegebenen Prozesse und Threads aktiviert wird.

Klicken Sie im Fenster **Haltepunkteinstellungen** unter **Bedingungen** auf **Filter**, und geben Sie dann mindestens einen der folgenden Ausdrücke ein:

- MachineName = "name"
- ProcessId = value
- ProcessName = "name"
- ThreadId = value
- ThreadName = "name"

Schließen Sie Zeichenfolgewerte in doppelte Anführungszeichen ein. Sie können Klauseln mit `&` (AND), `||` (OR), `!` (NOT), und Klammern kombinieren.

## <a name="set-function-breakpoints"></a><a name="BKMK_Set_a_breakpoint_in_a_source_file"></a> Festlegen von Funktionsbreakpoints

Sie können eine Ausführung anhalten, wenn eine Funktion aufgerufen wird. Dies ist z. B. dann hilfreich, wenn Sie den Name einer Funktion kennen, jedoch nicht die Stelle im Code, an der sie auftritt. Es ist auch dann hilfreich, wenn Funktionen denselben Namen haben und Sie wollen, dass die Ausführung bei Erreichen aller dieser Funktionen angehalten wird (z. B. überladene Funktionen oder Funktionen in anderen Projekten).

**So legen Sie einen Funktionsbreakpoint fest:**

1. Klicken Sie auf **Debuggen**  >  **Neuer Haltepunkt**  >  **Funktionshaltepunkt**, oder drücken Sie **ALT**+**F9** > **STRG**+**B**.

   Alternativ können Sie im Fenster **Haltepunkte** auch auf **Neu**  >  **Funktionshaltepunkt** klicken.

1. Geben Sie im Dialogfeld **Neuer Funktionshaltepunkt** den Funktionsname in das Feld **Funktionsname** ein.

   So schränken Sie die Funktionsspezifikation ein:

   - Verwenden Sie den vollqualifizierten Funktionsname.

     Beispiel: `Namespace1.ClassX.MethodA()`

   - Fügen Sie Parametertypen einer überladenen Funktion hinzu.

     Beispiel: `MethodA(int, string)`

   - Verwenden Sie das „!“-Symbol, um das Modul anzugeben.

     Ein Beispiel: `App1.dll!MethodA`

   - Verwenden Sie den Kontextoperator in nativem C++-Code.

     `{function, , [module]} [+<line offset from start of method>]`

     Ein Beispiel: `{MethodA, , App1.dll}+2`

1. Wählen Sie im Dropdown **Sprache** die Sprache der Funktion aus.

1. Klicken Sie auf **OK**.

### <a name="set-a-function-breakpoint-using-a-memory-address-native-c-only"></a>Festlegen eines Funktionsbreakpoints mit einer Speicheradresse (nur nativer C++-Code)
 Sie können die Adresse eines Objekts verwenden, um einen Funktionsbreakpoint für eine Methode festzulegen, die von einer bestimmten Instanz einer Klasse aufgerufen wird.  Bei einem adressierbaren Objekt vom Typ `my_class` können Sie beispielsweise einen Funktionsbreakpoint für eine `my_method`-Methode festlegen, die von dieser Instanz aufgerufen wird.

1. Legen Sie einen Breakpoint an einer Stelle nach der Instanziierung der Instanz der Klasse fest.

2. Suchen Sie nach der Adresse der Instanz (z. B. `0xcccccccc`).

3. Klicken Sie auf **Debuggen**  >  **Neuer Haltepunkt**  >  **Funktionshaltepunkt**, oder drücken Sie **ALT**+**F9** > **STRG**+**B**.

4. Fügen Sie im Feld **Funktionsname** Folgendes hinzu, und wählen Sie die Sprache **C++** aus.

   ```cpp
   ((my_class *) 0xcccccccc)->my_method
   ```

::: moniker range=">= vs-2019"

## <a name="set-data-breakpoints-net-core-30-or-higher"></a><a name="BKMK_set_a_data_breakpoint_managed"></a>Festlegen von Datenbreakpoints (.NET Core 3.0 oder höher)

Datenbreakpoints unterbrechen die Ausführung, wenn sich die Eigenschaft eines bestimmten Objekts ändert.

**So legen Sie einen Datenbreakpoint fest:**

1. Starten Sie das Debuggen in einem .NET Core-Projekt, und warten Sie, bis ein Breakpoint erreicht wird.

2. Klicken Sie in einem der Fenster **Auto**, **Überwachung** oder **Lokale Variablen** mit der rechten Maustaste auf eine Eigenschaft, und klicken Sie dann im Kontextmenü auf die Option **Bei Wertänderungen unterbrechen**.

    ![Verwaltete Datenbreakpoints](../debugger/media/managed-data-breakpoint.png "Verwalteter Datenbreakpoint")

Datenbreakpoints in .NET Core funktionieren für Folgendes nicht:

- Eigenschaften, die im QuickInfo-, Lokale Variablen-, Auto- oder Überwachungsfenster nicht aufgeklappt werden können
- Statische Variablen
- Klassen mit dem DebuggerTypeProxy-Attribut
- Felder innerhalb von Strukturen

::: moniker-end

## <a name="set-data-breakpoints-native-c-only"></a><a name="BKMK_set_a_data_breakpoint_native_cplusplus"></a>Festlegen von Datenbreakpoints (nur nativer C++-Code)

 Datenbreakpoints unterbrechen die Ausführung, wenn sich ein Wert ändert, der unter einer bestimmten Speicheradresse gespeichert ist. Wenn der Wert ausgelesen jedoch nicht geändert wird, wird die Ausführung nicht unterbrochen.

**So legen Sie einen Datenbreakpoint fest:**

1. Starten Sie das Debuggen in einem C++-Projekt, und warten Sie, bis ein Breakpoint erreicht wird. Klicken Sie im Menü **Debuggen** auf die Option **Neuer Haltepunkt**  >  **Datenhaltepunkt**.

    Alternativ können Sie im Fenster **Haltepunkte** auf **Neu**  >  **Datenhaltepunkt** klicken, oder mit der rechten Maustaste auf ein Element in einem der Fenster **Auto**, **Überwachung** oder **Lokale Variablen** klicken und dann im Kontextmenü auf die Option **Bei Wertänderungen unterbrechen** klicken.

2. Geben Sie im Feld **Adresse** eine Speicheradresse oder einen Ausdruck ein, der als Speicheradresse ausgewertet wird. Geben Sie beispielsweise `&avar` ein, um die Ausführung bei einer Änderung des Inhalts der Variable `avar` zu unterbrechen.

3. Geben Sie im Feld **Byteanzahl** die Anzahl der Bytes an, die der Debugger überwachen soll. Wenn Sie beispielsweise **4** auswählen, überwacht der Debugger vier Bytes ab `&avar` und unterbricht, wenn eines dieser Bytes seinen Wert ändert.

Unter folgenden Bedingungen funktionieren Datenbreakpoints nicht:
- Ein Prozess, der nicht gedebuggt wird, wird in einen Speicherbereich geschrieben.
- Der Speicherbereich wird von mindestens zwei Prozessen gemeinsam verwendet.
- Der Speicherort wird innerhalb des Kernels aktualisiert. Dies ist beispielsweise der Fall, wenn Speicher an eine 32-Bit Windows-`ReadFile`-Funktion übergeben wird, der Speicher aus dem Kernelmodus aktualisiert wird, und der Debugger die Aktualisierung so nicht unterbricht.
- In Szenarios, in denen der Überwachungsausdruck eine Größe von 4 Bytes auf einer 32-Bit-Hardware bzw. von 8 Bytes auf einer 64-Bit-Hardware überschreitet. Dies ist eine Einschränkung der x86-Architektur.

> [!NOTE]
> - Datenbreakpoints hängen von spezifischen Speicheradressen ab. Die Adresse einer Variable ändert sich von einer Debugsitzung zur nächsten. Datenbreakpoints werden also am Ende jeder Debugsitzung automatisch deaktiviert.
>
> - Wenn Sie einen Datenhaltepunkt bei einer lokalen Variable festlegen, bleibt der Haltepunkt aktiviert, wenn die Funktion beendet wird, die Speicheradresse ist jedoch nicht mehr gültig, und das Verhalten des Haltepunkts ist unvorhersehbar. Wenn Sie einen Datenbreakpoint für eine lokale Variable festlegen, sollten Sie diesen vor dem Ende der Funktion entfernen oder deaktivieren.

## <a name="manage-breakpoints-in-the-breakpoints-window"></a><a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a> Verwalten von Haltepunkten im Haltepunktefenster

 Im Fenster **Haltepunkte** können Sie sich alle Breakpoints in Ihrer Projektmappe ansehen und sie verwalten. Dieser zentrale Ort ist besonders für große Projektmappen oder für komplexe Debugszenarios sehr hilfreich, in denen Breakpoints von entscheidender Bedeutung sind.

Im Fenster **Haltepunkte** können Sie nach Breakpoints suchen, sie sortieren, filtern, aktivieren/deaktivieren oder entfernen. Sie können auch Bedingungen und Aktionen festlegen oder neue Funktions- oder Datenbreakpoints hinzufügen.

Klicken Sie auf **Debuggen**  >  **Fenster**  >  **Haltepunkte**, oder drücken Sie **ALT**+**F9** oder **STRG**+**ALT**+**B**, um das Fenster **Haltepunkte** zu öffnen.

![Fenster „Haltepunkte“](../debugger/media/breakpointswindow.png "Haltepunkte(Fenster)")

Klicken Sie auf die Option **Spalten anzeigen**, um die Spalten auszuwählen, die im Fenster **Haltepunkte** angezeigt werden sollen. Wählen Sie eine Spaltenüberschrift aus, um die Breakpointliste nach der entsprechenden Spalte zu sortieren.

### <a name="breakpoint-labels"></a><a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a> Haltepunktbezeichnungen
Sie können Bezeichnungen verwenden, um die Breakpointliste im Fenster **Haltepunkte** zu sortieren und zu filtern.

1. Wenn Sie einem Breakpoint eine Bezeichnung hinzufügen möchten, klicken Sie im Quellcode oder im Fenster **Haltepunkte** mit der rechten Maustaste auf den Breakpoint, und klicken Sie dann auf **Bezeichnung bearbeiten**. Fügen Sie eine neue Bezeichnung hinzu, oder wählen Sie eine vorhandene aus, und klicken Sie dann auf **OK**.
2. Sortieren Sie die Breakpointliste im Fenster **Haltepunkte**, indem Sie **Bezeichnungen**, **Bedingungen** oder andere Spaltenüberschriften auswählen. Sie können auswählen, welche Spalten angezeigt werden sollen, indem Sie in der Symbolleiste auf **Spalten anzeigen** klicken.

### <a name="export-and-import-breakpoints"></a>Exportieren und Importieren von Haltepunkten
 Wenn Sie den Status und die Position Ihrer Breakpoints speichern oder freigeben möchten, können Sie diese Informationen exportieren oder importieren.

- Wenn Sie einen einzelnen Breakpoint in eine XML-Datei exportieren möchten, klicken Sie im Quellcode oder im Fenster **Haltepunkte** mit der rechten Maustaste auf den Breakpoint, und klicken Sie auf **Exportieren** oder auf **Auswahl exportieren**. Wählen Sie einen Speicherort für den Export aus, und klicken Sie anschließend auf **Speichern**. Der Standardspeicherort ist der Projektmappenordner.
- Wenn Sie mehrere Breakpoints exportieren möchten, klicken Sie im Fenster **Haltepunkte** auf die Kontrollkästchen neben den jeweiligen Breakpoints, oder geben Sie im Feld **Suche** ein Suchkriterium ein. Klicken Sie auf das Symbol **Alle Haltepunkte exportieren, die mit den aktuellen Suchkriterien übereinstimmen**, und speichern Sie die Datei.
- Wenn Sie alle Breakpoints exportieren möchten, heben Sie die Auswahl für alle Kontrollkästchen auf, und lassen Sie das Feld **Suche** leer. Klicken Sie auf das Symbol **Alle Haltepunkte exportieren, die mit den aktuellen Suchkriterien übereinstimmen**, und speichern Sie die Datei.
- Wenn Sie Breakpoints importieren möchten, klicken Sie im Fenster **Haltepunkte** auf das Symbol **Haltepunkte aus einer Datei importieren**, navigieren Sie zum Speicherort der XML-Datei, und klicken Sie auf **Öffnen**.

## <a name="set-breakpoints-from-debugger-windows"></a><a name="BKMK_Set_a_breakpoint_from_debugger_windows"></a> Festlegen von Breakpoints in Debuggerfenstern

Sie können auch Breakpoints in den Debuggerfenstern **Aufrufliste** und **Disassemblierung** festlegen.

### <a name="set-a-breakpoint-in-the-call-stack-window"></a>Festlegen eines Breakpoints im Aufruflistenfenster

 Sie können einen Breakpoint im Fenster **Aufrufliste** festlegen, um die Ausführung bei der Anweisung oder in der Zeile zu unterbrechen, zu der eine aufrufende Funktion zurückkehrt.

**So legen Sie einen Breakpoint im Aufruflistenfenster fest:**

1. Das Debuggen muss pausiert sein, wenn Sie das Fenster **Aufrufliste** öffnen möchten. Klicken Sie auf **Debuggen**  >  **Fenster**  >  **Aufrufliste**, oder drücken Sie **STRG**+**ALT**+**C**.

2. Klicken Sie im Fenster **Aufrufliste** mit der rechten Maustaste auf die aufrufende Funktion, und klicken Sie dann auf **Haltepunkt**  >  **Haltepunkt einfügen**, oder drücken Sie **F9**.

   Am linken Rand der Aufrufliste wird neben dem Funktionsaufrufnamen ein Symbol für den Breakpoint angezeigt.

Im Fenster **Haltepunkte** wird der Aufruflistenhaltepunkt als Adresse mit Speicherort angezeigt, der der nächsten ausführbaren Anweisung der Funktion entspricht.

Der Debugger unterbricht die Ausführung an der Anweisung.

Weitere Informationen zur Aufrufliste finden Sie unter [Anzeigen der Aufrufliste und Verwenden des Aufruflistenfensters im Debugger](../debugger/how-to-use-the-call-stack-window.md).

Weitere Informationen zur visuellen Nachverfolgung während der Codeausführung finden Sie unter [Erstellen einer visuellen Code Map für die Aufrufliste während des Debuggens (C#, Visual Basic, C++, JavaScript)](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="set-a-breakpoint-in-the-disassembly-window"></a>Festlegen eines Breakpoints im Disassemblierungsfenster

1. Das Debuggen muss pausiert sein, wenn Sie das Fenster **Disassemblierung** öffnen möchten. Klicken Sie auf **Debuggen**  >  **Fenster**  >  **Disassemblierung**, oder drücken Sie **ALT**+**8**.

2. Klicken Sie im Fenster **Disassemblierung** in Höhe der Anweisung, an der die Ausführung unterbrochen werden soll, auf den linken Rand. Sie können auch die entsprechende Zeile auswählen und **F9** drücken, oder mit der rechten Maustaste klicken und auf **Haltepunkt**  >  **Haltepunkt einfügen** klicken.

## <a name="see-also"></a>Siehe auch

- [Was bedeutet „Debuggen“?](../debugger/what-is-debugging.md)
- [Debugtechniken und -tools, mit denen Sie besseren Code schreiben](../debugger/write-better-code-with-visual-studio.md)
- [Ein erster Blick auf den Visual Studio-Debugger](../debugger/debugger-feature-tour.md)
- [Troubleshooting für Breakpoints im Visual Studio-Debugger](../debugger/troubleshooting-breakpoints.md)
