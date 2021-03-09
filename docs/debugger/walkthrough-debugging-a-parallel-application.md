---
title: Debuggen einer parallelen Anwendung | Microsoft-Dokumentation
description: Debuggen mit den Fenstern „Parallele Aufgaben“ und „Parallele Stapel“ in Visual Studio
ms.date: 02/14/2020
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks walkthrough
- parallel stacks toolwindow
- parallel tasks toolwindow
- parallel applications, debugging [C++]
- debugging, parallel applications
- parallel applications, debugging [Visual Basic]
- parallel applications, debugging [C#]
ms.assetid: 2820ac4c-c893-4d87-8c62-83981d561493
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d8f739ab99f060005f7bbfebc400c424c50ba7d5
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/03/2021
ms.locfileid: "101684125"
---
# <a name="walkthrough-debugging-a-parallel-application-in-visual-studio-c-visual-basic-c"></a>Exemplarische Vorgehensweise: Debuggen einer parallelen Anwendung in Visual Studio (C#, Visual Basic, C++)

In dieser exemplarischen Vorgehensweise wird das Debuggen einer parallelen Anwendung mithilfe der Fenster **Parallele Aufgaben** und **Parallele Stapel** erläutert. Mit diesen Fenstern können Sie das Laufzeitverhalten von Code, für den die [Task Parallel Library (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) oder die [Concurrency Runtime](/cpp/parallel/concrt/concurrency-runtime) genutzt werden, besser verstehen und überprüfen. Diese exemplarische Vorgehensweise bietet Beispielcode mit integrierten Haltepunkte. Es wird erläutert, wie der Code nach Unterbrechung der Ausführung mithilfe der Fenster **Parallele Aufgaben** und **Parallele Stapel** untersucht wird.

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben erklärt:

- Anzeigen der Aufruflisten aller Threads in einer Ansicht.

- Anzeigen der Liste der `System.Threading.Tasks.Task`-Instanzen, die in der Anwendung erstellt werden.

- Anzeigen der tatsächlichen Aufruflisten mit Aufgaben anstelle von Threads.

- Navigieren von den Fenstern **Parallele Aufgaben** und **Parallele Stapel** zu Code.

- Skalieren der Fenster durch Gruppieren, Vergrößern/Verkleinern und sonstigen entsprechenden Funktionen.

## <a name="prerequisites"></a>Voraussetzungen
 Bei dieser exemplarischen Vorgehensweise wird vorausgesetzt, dass die Option **Nur eigenen Code** aktiviert ist (in neueren Versionen von Visual Studio standardmäßig aktiviert). Klicken Sie im Menü **Extras** auf **Optionen**, und erweitern Sie den Knoten **Debuggen**. Wählen Sie **Allgemein** aus, und wählen Sie dann **Nur eigenen Code aktivieren (nur verwaltet)** aus. Wenn Sie diese Funktion nicht festlegen, können Sie die vorliegende exemplarische Vorgehensweise zwar verwenden, Ihre Ergebnisse weichen jedoch möglicherweise von den Abbildungen ab.

## <a name="c-sample"></a>C#-Beispiel
 Wenn Sie das C#-Beispiel verwenden, wird in dieser exemplarischen Vorgehensweise auch davon ausgegangen, dass externer Code ausgeblendet ist. Klicken Sie mit der rechten Maustaste im Fenster **Aufrufliste** auf den Tabellenheader **Name**, und aktivieren bzw. deaktivieren Sie **Externen Code anzeigen**, um die Anzeige von externem Code umzuschalten. Wenn Sie diese Funktion nicht festlegen, können Sie die vorliegende exemplarische Vorgehensweise zwar verwenden, Ihre Ergebnisse weichen jedoch möglicherweise von den Abbildungen ab.

## <a name="c-sample"></a>C++-Beispiel
 Wenn Sie das C++-Beispiel verwenden, können Sie Verweise auf externen Code in diesem Thema ignorieren. Externer Code bezieht sich ausschließlich auf das C#-Beispiel.

## <a name="illustrations"></a>Abbildungen
 Die Abbildungen in diesem Thema wurden auf einem Quad-Core-Computer aufgezeichnet, auf dem das C#-Beispiel ausgeführt wird. Sie können diese exemplarische Vorgehensweise auch mit anderen Konfigurationen durcharbeiten. Die Abbildungen unterscheiden sich jedoch möglicherweise von der Anzeige auf Ihrem Computer.

## <a name="creating-the-sample-project"></a>Erstellen des Beispielprojekts
 Der Beispielcode in dieser exemplarischen Vorgehensweise ist für eine Anwendung ohne konkrete Aufgaben. Das Ziel besteht lediglich darin zu erläutern, wie mit den Toolfenstern parallele Anwendungen gedebuggt werden.

#### <a name="to-create-the-sample-project"></a>So erstellen Sie das Beispielprojekt

1. Öffnen Sie Visual Studio, und erstellen Sie ein neues Projekt.

   ::: moniker range=">=vs-2019"

   Wenn das Startfenster nicht geöffnet ist, klicken Sie auf **Datei** > **Startfenster**.

   Wählen Sie im Startfenster **Neues Projekt erstellen** aus.

   Geben Sie im Fenster **Neues Projekt erstellen** im Suchfeld *Konsole* ein. Wählen Sie anschließend in der Liste mit den Sprachen die Option **C#** , **C++** oder **Visual Basic** und dann in der Liste mit den Plattformen **Windows** aus.

   Nachdem Sie die Sprach- und Plattformfilter angewendet haben, wählen Sie **Konsolen-App** für .NET Core oder C++ und dann **Weiter** aus.

   > [!NOTE]
   > Wenn die richtige Vorlage nicht angezeigt wird, öffnen Sie unter **Tools** > **Tools und Features abrufen...** den Visual Studio-Installer. Wählen Sie die Workload **Plattformübergreifende .NET Core-Entwicklung** oder **Desktopentwicklung mit C++** aus, und klicken Sie dann auf **Anpassen**.

   Geben Sie im Fenster **Neues Projekt konfigurieren** einen Namen ein, oder verwenden Sie im Feld **Projektname** den Standardnamen. Klicken Sie anschließend je nach verfügbarer Option entweder auf **Weiter** oder auf **Erstellen**.

   Wählen Sie für .NET Core entweder das empfohlene Zielframework (.NET Core 3.1) oder .NET 5 aus, und klicken Sie dann auf **Erstellen**.

   ::: moniker-end
   ::: moniker range="vs-2017"
   Klicken Sie oben in der Menüleiste auf **Datei** > **Neu** > **Projekt**. Wählen Sie im linken Bereich des Dialogfelds **Neues Projekt** eine der folgenden Optionen aus:

   - Wählen Sie für eine C#-App unter **Visual C#** die Option **Windows-Desktop** und dann im mittleren Bereich **Konsolen-App (.NET Framework)** aus.
   - Wählen Sie für eine Visual Basic-App unter **Visual Basic** die Option **Windows-Desktop** und dann im mittleren Bereich **Konsolen-App (.NET Framework)** aus.
   - Klicken Sie für eine C++-App unter **Visual C++** auf **Windows-Desktop**, und wählen Sie dann im mittleren Bereich **Windows-Konsolenanwendung** aus.

   Wenn die Projektvorlage **Konsolen-App (.NET Core)** oder für C++ **Konsolen-App (.NET Framework)** nicht angezeigt wird, navigieren Sie zu **Tools** > **Tools und Features abrufen...** , um den Visual Studio-Installer zu öffnen. Wählen Sie die Workload **.NET-Desktopentwicklung** oder **Desktopentwicklung mit C++** und anschließend **Ändern** aus.

   Geben Sie anschließend einen Namen ein, oder verwenden Sie den Standardnamen, und klicken Sie auf **OK**.

   Klicken Sie auf **OK**.
   ::: moniker-end

   Ein neues Konsolenprojekt wird angezeigt. Nachdem das Projekt erstellt wurde, wird eine Quelldatei angezeigt.

1. Öffnen Sie die CPP-, CS- oder VB-Codedatei im Projekt. Löschen Sie den Dateiinhalt, um eine leere Codedatei zu erstellen.

1. Fügen Sie den folgenden Code für die ausgewählte Sprache in die leere Codedatei ein.

   [!code-csharp[Debugger#1](../debugger/codesnippet/CSharp/walkthrough-debugging-a-parallel-application_1.cs)]
   [!code-cpp[Debugger#1](../debugger/codesnippet/CPP/walkthrough-debugging-a-parallel-application_1.cpp)]
   [!code-vb[Debugger#1](../debugger/codesnippet/VisualBasic/walkthrough-debugging-a-parallel-application_1.vb)]

1. Klicken Sie im Menü **Datei** auf **Alle speichern**.

1. Klicken Sie im Menü **Build** auf **Projektmappe neu erstellen**.

    Beachten Sie, dass es vier Aufrufe zu `Debugger.Break` (`DebugBreak` im C++-Beispiel) gibt. Daher müssen keine Haltepunkte eingefügt werden; wenn nur die Anwendung ausgeführt wird, hat dies bis zu vier Unterbrechungen im Debugger zur Folge.

## <a name="using-the-parallel-stacks-window-threads-view"></a>Verwenden des Fensters „Parallele Stapel“: Threadansicht
 Klicken Sie im Menü **Debuggen** auf **Debuggen starten**. Warten Sie, bis der erste Haltepunkt erreicht wird.

#### <a name="to-view-the-call-stack-of-a-single-thread"></a>So zeigen Sie die Aufrufliste eines einzelnen Threads an

1. Zeigen Sie im Menü **Debuggen** auf **Fenster**, und klicken Sie dann auf **Threads**. Docken Sie das Fenster **Threads** am unteren Rand von Visual Studio an.

2. Zeigen Sie im Menü **Debuggen** auf **Fenster**, und klicken Sie dann auf **Aufrufliste**. Docken Sie das Fenster **Aufrufliste** am unteren Rand von Visual Studio an.

3. Doppelklicken Sie im Fenster **Threads** auf einen Thread, um diesen als aktuellen Thread festzulegen. Aktuelle Threads sind durch einen gelben Pfeil gekennzeichnet. Wenn Sie den aktuellen Thread ändern, wird seine Aufrufliste im Fenster **Aufrufliste** angezeigt.

#### <a name="to-examine-the-parallel-stacks-window"></a>So untersuchen Sie das Fenster Parallele Stapel

1. Zeigen Sie im Menü **Debuggen** auf **Fenster**, und klicken Sie dann auf **Parallele Stapel**. Vergewissern Sie sich, dass im Feld in der oberen linken Ecke **Threads** ausgewählt ist.

     Im Fenster **Parallele Stapel** können Sie mehrere Aufruflisten gleichzeitig in einer Ansicht anzeigen. In der folgenden Abbildung wird das Fenster **Parallele Stapel** über dem Fenster **Aufrufliste** angezeigt.

     ![Ansicht „Threads“ im Fenster „Parallele Stapel“](../debugger/media/pdb_walkthrough_1.png "PDB_Walkthrough_1")

     Die Aufrufliste des Hauptthreads wird in einem Feld angezeigt, während die Aufruflisten für die anderen vier Threads als Gruppe in einem anderen Feld angezeigt werden. Vier Threads werden als Gruppe angezeigt, da für ihre Stapelrahmen dieselben Methodenkontexte verwendet werden; d. h., sie befinden sich in denselben Methoden: `A`, `B` und `C`. Um die IDs und Namen der Threads anzuzeigen, die in demselben Feld enthalten sind, zeigen Sie mit dem Mauszeiger auf das Feld mit dem Header (**4 Threads**). Der aktuelle Thread wird fett hervorgehoben angezeigt.

     ![QuickInfo mit Thread-IDs und -Namen](../debugger/media/pdb_walkthrough_1a.png "PDB_Walkthrough_1A")

     Der gelbe Pfeil gibt den aktiven Stapelrahmen des aktuellen Threads an.

     Sie können festlegen, wie viele Details für die Stapelrahmen angezeigt werden sollen (**Modulnamen**, **Parametertypen**, **Parameternamen**, **Parameterwerte**, **Zeilennummern** und **Byte-Offsets**), indem Sie mit der rechten Maustaste in das Fenster **Aufrufliste** klicken.

     Durch eine blaue Hervorhebung um ein Feld wird angegeben, dass der aktuelle Thread zu diesem Feld gehört. Der aktuelle Thread wird auch durch den fett formatierten Stapelrahmen in der QuickInfo angegeben. Wenn Sie im Fenster Threads auf den Hauptthread doppelklicken, können Sie beobachten, wie die blaue Hervorhebung im Fenster **Parallele Stapel** entsprechend verschoben wird.

     ![Hervorgehobener Hauptthread im Fenster „Parallele Stapel“](../debugger/media/pdb_walkthrough_1c.png "PDB_Walkthrough_1C")

#### <a name="to-resume-execution-until-the-second-breakpoint"></a>So setzen Sie die Ausführung bis zum zweiten Haltepunkt fort

1. Klicken Sie im Menü **Debuggen** auf **Weiter**, um die Ausführung bis zum zweiten Breakpoint fortzusetzen. In der folgenden Abbildung wird die Threadstruktur beim zweiten Haltepunkt dargestellt.

     ![Fenster „Parallele Stapel“ mit vielen Branches](../debugger/media/pdb_walkthrough_2.png "PDB_Walkthrough_2")

     Beim ersten Haltepunkt gingen alle vier Threads von den Methoden S.A zu S.B zu S.C über. Diese Informationen werden im Fenster **Parallele Stapel** immer noch angezeigt, die vier Threads wurden jedoch weiter ausgeführt. Ein Thread ist zu S.D und dann zu S.E übergegangen. Ein anderer hat mit S.F, S.G und S.H fortgefahren. Zwei andere wechselten zu S.I und S.J. Von dort ging einer zu S.K über, während der andere zu nicht vom Benutzer stammendem externen Code wechselte.

     Sie können mit dem Mauszeiger auf den Header des Felds zeigen (beispielsweise **1 Thread** oder **2 Threads**), um die Thread-IDs der Threads anzuzeigen. Sie können mit dem Mauszeiger auf Stapelrahmen zeigen, um die Thread-IDs sowie andere Details zum Rahmen zu überprüfen. Die blaue Hervorhebung gibt den aktuellen Thread an, während mit dem gelben Pfeil der aktive Stapelrahmen des aktuellen Threads angegeben wird.

     Mit dem Faden-Symbol (miteinander verwobene Linien) werden die aktiven Stapelrahmen der nicht aktuellen Threads angegeben. Doppelklicken Sie im Fenster **Aufrufliste** auf S.B, um zwischen Frames zu wechseln. Im Fenster **Parallele Stapel** wird der aktuelle Stapelrahmen des aktuellen Threads mit einem grünen gebogenen Pfeilsymbol angegeben.

     Schalten Sie im Fenster **Threads** zwischen Threads um. Sie werden feststellen, dass die Ansicht des Fensters **Parallele Stapel** aktualisiert wird.

     Sie können über das Kontextmenü im Fenster **Parallele Stapel** zu einem anderen Thread oder zu einem anderen Frame eines anderen Threads wechseln. Klicken Sie z. B. mit der rechten Maustaste auf S.J, zeigen Sie auf **Zu Rahmen wechseln**, und klicken Sie dann auf einen Befehl.

     ![Parallele Stapel: Ausführungspfad](../debugger/media/pdb_walkthrough_2b.png "PDB_Walkthrough_2B")

     Klicken Sie mit der rechten Maustaste auf S.C, und zeigen Sie auf **Zu Rahmen wechseln**. Ein Befehl ist mit einem Häkchen versehen, das den Stapelrahmen des aktuellen Threads angibt. Sie können zu diesem Frame desselben Threads (nur der grüne Pfeil wird verschoben) wechseln, oder Sie können zum anderen Thread (die blaue Hervorhebung wird ebenfalls verschoben) wechseln. Die folgende Abbildung zeigt das Untermenü.

     ![Menü „Stapel“ mit zwei Optionen auf C, während J aktuell ist](../debugger/media/pdb_walkthrough_3.png "PDB_Walkthrough_3")

     Wenn ein Methodenkontext nur einem Stapelrahmen zugeordnet ist, wird im Feldheader **1 Thread** angezeigt, und Sie können durch Doppelklicken zu diesem wechseln. Wenn Sie auf einen Methodenkontext doppelklicken, dem mehrere Frames zugeordnet sind, wird das Menü automatisch aufgerufen. Wie Sie mit dem Mauszeiger auf die Methodenkontexte zeigen, wird rechts ein schwarzes Dreieck angezeigt. Wenn Sie auf dieses Dreieck klicken, wird ebenfalls das Kontextmenü geöffnet.

     Bei großen Anwendungen mit einer Vielzahl von Threads kann es sich empfehlen, sich nur auf eine Teilmenge von Threads zu konzentrieren. Im Fenster **Parallele Stapel** können Aufruflisten nur für gekennzeichnete Threads angezeigt werden. Verwenden Sie zum Kennzeichnen von Threads das Kontextmenü oder die erste Zelle eines Threads.

     Klicken Sie auf der Symbolleiste neben dem Listenfeld auf die Schaltfläche **Nur gekennzeichnete anzeigen**.

     ![Fenster „Parallele Stapel“ und QuickInfo](../debugger/media/pdb_walkthrough_3a.png "PDB_Walkthrough_3A")

     Jetzt wird nur der gekennzeichnete Thread im Fenster **Parallele Stapel** angezeigt.

#### <a name="to-resume-execution-until-the-third-breakpoint"></a>So setzen Sie die Ausführung bis zum dritten Haltepunkt fort

1. Klicken Sie im Menü **Debuggen** auf **Weiter**, um die Ausführung bis zum dritten Breakpoint fortzusetzen.

     Wenn mehrere Threads in derselben Methode enthalten sind, diese sich jedoch nicht am Anfang der Aufrufliste befand, wird die Methode in verschiedenen Feldern angezeigt. Ein Beispiel am aktuellen Haltepunkt ist S.L. Hierin sind drei Threads enthalten, und die Methode wird in drei Feldern angezeigt. Doppelklicken Sie auf S.L.

     ![Ausführungspfad im Fenster „Parallele Stapel“](../debugger/media/pdb_walkthrough_3b.png "PDB_Walkthrough_3B")

     Beachten Sie, dass S.L in den anderen beiden Feldern fett formatiert ist, damit dort ersichtlich ist, an welcher Stelle die Methode außerdem angezeigt wird. Wenn Sie bestimmen möchten, welche Frames S.L aufrufen und welche Frames von der Methode aufgerufen werden, klicken Sie auf der Symbolleiste auf die Schaltfläche **Methodenansicht umschalten**. In der folgenden Abbildung wird die Methodenansicht des Fensters **Parallele Stapel** angezeigt.

     ![Methodenansicht im Fenster „Parallele Stapel“](../debugger/media/pdb_walkthrough_4.png "PDW_Walkthrough_4")

     Das Diagramm wurde für die ausgewählte Methode pivotiert, und diese wurde in einem eigenen Feld in der Mitte der Ansicht positioniert. Die Aufgerufenen und die Aufrufer werden am oberen und unteren Rand angezeigt. Klicken Sie auf die Schaltfläche **Methodenansicht umschalten**, um diesen Modus wieder zu verlassen.

     Das Kontextmenü des Fensters **Parallele Stapel** weist zudem die folgenden weiteren Elemente auf.

    - Mit **Hexadezimale Anzeige** wird die Anzeige der Zahlen in den QuickInfos zwischen Dezimal- und Hexadezimaldarstellung umgeschaltet.

    - Mit **Symboleinstellungen** werden die entsprechenden Dialogfelder geöffnet.

    - Mit **Threads in Quelle anzeigen** wird die Anzeige von Threadmarkern in Ihrem Quellcode umgeschaltet, mit denen die Positionen der Threads im Quellcode angegeben wird.

    - Mit **Externen Code anzeigen** werden alle Frames angezeigt, auch wenn sie sich nicht im Benutzercode befinden. Das Diagramm wird erweitert, um die zusätzlichen Frames aufzunehmen (die möglicherweise abgeblendet dargestellt werden, da keine Symbole dafür vorhanden sind).

2. Vergewissern Sie sich, dass im Fenster **Parallele Stapel** die Symbolleistenschaltfläche **Autom. Bildlauf zu aktuellem Stapelrahmen** aktiviert ist.

     Wenn Sie bei großen Diagrammen zum nächsten Haltepunkt wechseln, können Sie einen automatischen Bildlauf der Anzeige zum aktiven Stapelrahmen des aktuellen Threads ausführen lassen (d. h. des Threads, der den Haltepunkt zuerst erreicht hat).

3. Scrollen Sie vor dem Fortfahren im Fenster **Parallele Stapel** zunächst ganz nach links und ganz nach unten.

#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>So setzen Sie die Ausführung bis zum vierten Haltepunkt fort

1. Klicken Sie im Menü **Debuggen** auf **Weiter**, um die Ausführung bis zum vierten Breakpoint fortzusetzen.

     Beachten Sie, wie ein automatischer Bildlauf der Ansicht an die korrekte Position stattfindet. Schalten Sie zwischen Threads im Fenster **Threads** um, oder schalten Sie zwischen Stapelrahmen im Fenster **Aufrufliste** um. Sie werden feststellen, dass immer ein automatischer Bildlauf der Ansicht zum richtigen Frame erfolgt. Deaktivieren Sie die Option **Autom. Bildlauf zu aktuellem Stapelrahmen**, und beobachten Sie den Unterschied.

     Die **Vogelperspektive** ist auch hilfreich bei großen Diagrammen im Fenster **Parallele Stapel**. Standardmäßig ist die **Vogelperspektive** aktiviert. Sie können dies aber umschalten, indem Sie auf die Schaltfläche zwischen den Bildlaufleisten in der rechten unteren Ecke des Fensters klicken. Dies ist in der folgenden Abbildung dargestellt.

     ![Vogelperspektive im Fenster „Parallele Stapel“](../debugger/media/pdb_walkthrough_5.png "PDB_Walkthrough_5")

     In der Vogelperspektive können Sie das Rechteck verschieben, um einen schnellen Schwenk für das Diagramm auszuführen.

     Eine weitere Möglichkeit, das Diagramm in beliebiger Richtung zu verschieben, besteht darin, auf einen leeren Bereich des Diagramms zu klicken und das Diagramm an die gewünschte Stelle zu ziehen.

     Zum Vergrößern und Verkleinern der Ansicht des Diagramms halten Sie STRG gedrückt, während Sie das Mausrad drehen. Sie können auch auf der Symbolleiste auf die Schaltfläche Zoom klicken und das Tool Zoom verwenden.

     Sie können die Stapel auch von oben nach unten angeordnet anstatt von unten nach oben anzeigen. Klicken Sie dazu im Menü **Extras** auf **Optionen**, und aktivieren bzw. deaktivieren Sie anschließend die Option unter dem Knoten **Debuggen**.

2. Klicken Sie vor dem Fortfahren im Menü **Debuggen** auf **Debuggen beenden**, um die Ausführung zu beenden.

## <a name="using-the-parallel-tasks-window-and-the-tasks-view-of-the-parallel-stacks-window"></a>Verwenden des Fensters Parallele Aufgaben und der Aufgabenansicht des Fensters Parallele Stapel
 Es empfiehlt sich, vor dem Fortfahren die früheren Prozeduren abzuschließen.

#### <a name="to-restart-the-application-until-the-first-breakpoint-is-hit"></a>So starten Sie die Anwendung neu, bis der erste Haltepunkt erreicht wird

1. Klicken Sie im Menü **Debuggen** auf **Debuggen starten**, und warten Sie, bis der erste Breakpoint erreicht wird.

2. Zeigen Sie im Menü **Debuggen** auf **Fenster**, und klicken Sie dann auf **Threads**. Docken Sie das Fenster **Threads** am unteren Rand von Visual Studio an.

3. Zeigen Sie im Menü **Debuggen** auf **Fenster**, und klicken Sie auf **Aufrufliste**. Docken Sie das Fenster **Aufrufliste** am unteren Rand von Visual Studio an.

4. Doppelklicken Sie im Fenster **Threads** auf einen Thread, um diesen als aktuellen Thread festzulegen. Aktuelle Threads sind durch einen gelben Pfeil gekennzeichnet. Wenn Sie den aktuellen Thread ändern, werden die anderen Fenster aktualisiert. Nun werden Aufgaben untersucht.

5. Zeigen Sie im Menü **Debuggen** auf **Fenster**, und klicken Sie dann auf **Aufgaben**. In der folgenden Abbildung ist das Fenster **Aufgaben** dargestellt.

     ![Vier ausgeführte Aufgaben im Fenster „Aufgaben“](../debugger/media/pdb_walkthrough_6.png "PDW_Walkthrough_6")

     Für jede ausgeführte Aufgabe können Sie die zugehörige ID lesen. Diese wird zusammen mit der gleichnamigen Eigenschaft, der ID und dem Namen des ausführenden Threads und ihrer Position zurückgegeben (wenn Sie mit dem Mauszeiger darauf zeigen, wird eine QuickInfo mit der gesamten Aufrufliste angezeigt). Unter der Spalte **Aufgabe** wird auch die Methode angezeigt, die in die Aufgabe übergeben wurde (mit anderen Worten, den Ausgangspunkt).

     Alle Spalten können sortiert werden. Beachten Sie das Sortiersymbol, das Sortierspalte und -richtung angibt. Sie können auch die Anordnung der Spalten ändern, indem Sie sie nach links oder rechts ziehen.

     Der gelbe Pfeil gibt die aktuelle Aufgabe an. Sie können zwischen Aufgaben wechseln, indem Sie auf eine Aufgabe doppelklicken oder indem Sie das Kontextmenü aufrufen. Beim Wechseln zwischen Aufgaben wird der zugrunde liegende Thread zum aktuellen Thread, und die übrigen Fenster werden aktualisiert.

     Wenn Sie manuell von einer Aufgabe zu einer anderen wechseln, wird der gelbe Pfeil verschoben. Ein weißer Pfeil zeigt jedoch weiterhin die Aufgabe an, die die Unterbrechung des Debuggers verursacht hat.

#### <a name="to-resume-execution-until-the-second-breakpoint"></a>So setzen Sie die Ausführung bis zum zweiten Haltepunkt fort

1. Klicken Sie im Menü **Debuggen** auf **Weiter**, um die Ausführung bis zum zweiten Breakpoint fortzusetzen.

     Zuvor wurden in der Spalte **Status** alle Aufgaben als „Aktiv“ angezeigt, aber jetzt weisen zwei Aufgaben den Status „Blockiert“ auf. Aufgaben können aus vielen anderen Gründen blockiert werden. Zeigen Sie in der Spalte **Status** auf eine wartende Aufgabe, um den Grund für ihre Blockierung anzuzeigen. In der folgenden Abbildung wartet beispielsweise Aufgabe 3 auf Aufgabe 4.

     ![Zwei wartende Aufgaben im Fenster „Aufgaben“](../debugger/media/pdb_walkthrough_7.png "PDB_Walkthrough_7")

     Aufgabe 4 wiederum wartet auf einen Monitor, der zu dem Thread gehört, der Aufgabe 2 zugewiesen ist. (Klicken Sie mit der rechten Maustaste auf die Headerzeile, und wählen Sie **Spalten** > **Threadzuweisung** aus, um den Wert für die Threadzuweisung für Aufgabe 2 anzuzeigen.)

     ![Wartende Aufgabe und QuickInfo im Fenster „Aufgaben“](../debugger/media/pdb_walkthrough_7a.png "PDB_Walkthrough_7A")

     Sie können eine Aufgabe kennzeichnen, indem Sie in der ersten Spalte des Fensters **Aufgaben** auf das Flag klicken.

     Durch das Kennzeichnen können Sie Aufgaben zwischen den verschiedenen Breakpoints einer Debugsitzung verfolgen oder Aufgaben filtern, deren Aufruflisten im Fenster **Parallele Stapel** angezeigt werden.

     Als Sie das Fenster **Parallele Stapel** weiter oben verwendet haben, haben Sie die Anwendungsthreads angezeigt. Rufen Sie das Fenster **Parallele Stapel** erneut auf, zeigen Sie dieses Mal jedoch die Anwendungsaufgaben an. Wählen Sie dazu im Feld in der oberen linken Ecke **Aufgaben** aus. In der folgenden Abbildung wird die Aufgabenansicht dargestellt.

     ![Ansicht „Aufgaben“ im Fenster „Parallele Stapel“](../debugger/media/pdb_walkthrough_8.png "PDB_Walkthrough_8")

     Threads, die derzeit keine Aufgaben ausführen, werden in der Aufgabenansicht des Fensters **Parallele Stapel** nicht angezeigt. Auch für Threads, die Aufgaben ausführen, werden einige der für Aufgaben irrelevanten Stapelrahmen im Stapel von oben und unten gefiltert.

     Sehen Sie sich das Fenster **Aufgaben** erneut an. Klicken Sie mit der rechten Maustaste auf einen Spaltenheader, um das Kontextmenü für die betreffende Spalte aufzurufen.

     Über das Kontextmenü können Spalten hinzugefügt und entfernt werden. Die Spalte AppDomain ist z. B. nicht ausgewählt. Daher wird sie in der Liste nicht aufgeführt. Klicken Sie auf **Übergeordnetes Element**. Die Spalte **Übergeordnetes Element** wird ohne Werte für die vier Aufgaben angezeigt.

#### <a name="to-resume-execution-until-the-third-breakpoint"></a>So setzen Sie die Ausführung bis zum dritten Haltepunkt fort

1. Klicken Sie im Menü **Debuggen** auf **Weiter**, um die Ausführung bis zum dritten Breakpoint fortzusetzen.

     Eine neue Aufgabe, Aufgabe 5, wird nun ausgeführt, und Aufgabe 4 ist nun wartend. Sie können dies überprüfen, indem Sie im Fenster **Status** mit dem Mauszeiger auf die wartende Aufgabe zeigen. Beachten Sie in der Spalte **Übergeordnetes Element**, dass Aufgabe 4 das übergeordnete Element von Aufgabe 5 ist.

     Um die Beziehung zwischen übergeordneten und untergeordneten Daten besser zu veranschaulichen, klicken Sie mit der rechten Maustaste auf die Spaltenkopfzeile und klicken anschließend auf **Ansicht über- und untergeordneter Elemente**. Die Anzeige entspricht der folgenden Abbildung:

     ![Ansicht über- und untergeordneter Elemente im Fenster „Aufgaben“](../debugger/media/pdb_walkthrough_9.png "PDB_Walkthrough_9")

     Beachten Sie, dass Aufgabe 4 und Aufgabe 5 unter demselben Thread ausgeführt werden. (Zeigen Sie die Spalte **Threadzuweisung** an, falls sie ausgeblendet ist.) Diese Informationen werden im Fenster **Threads** nicht angezeigt. Ihre Anzeige an dieser Stelle ist ein weiterer Vorteil des Fensters **Aufgaben**. Überprüfen Sie dies, indem Sie das Fenster **Parallele Stapel** öffnen. Stellen Sie sicher, dass Sie sich **Aufgaben** ansehen. Suchen Sie nach den Aufgaben 4 und 5, indem Sie im Fenster **Aufgaben** darauf doppelklicken. In diesem Fall wird die blaue Hervorhebung im Fenster **Parallele Stapel** aktualisiert. Sie können die Aufgaben 4 und 5 auch suchen, indem Sie die QuickInfos im Fenster **Parallele Stapel** überprüfen.

     ![Aufgabenansicht im Fenster „Parallele Stapel“](../debugger/media/pdb_walkthrough_9a.png "PDB_Walkthrough_9A")

     Klicken Sie im Fenster **Parallele Stapel** mit der rechten Maustaste auf S.P, und klicken Sie anschließend auf **Zu Thread wechseln**. Das Fenster wechselt zur Threadansicht, und der entsprechende Frame wird angezeigt. Sie können beide Aufgaben im selben Thread sehen.

     ![Hervorgehobener Thread in der Ansicht „Threads“](../debugger/media/pdb_walkthrough_9b.png "PDB_Walkthrough_9B")

     Dies ist ein weiterer Vorteil der Aufgabenansicht im Fenster **Parallele Stapel** gegenüber dem Fenster **Threads**.

#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>So setzen Sie die Ausführung bis zum vierten Haltepunkt fort

1. Klicken Sie im Menü **Debuggen** auf **Weiter**, um die Ausführung bis zum dritten Breakpoint fortzusetzen. Klicken Sie auf den Spaltenheader **ID**, um die Einträge nach ID zu sortieren. Die Anzeige entspricht der folgenden Abbildung:

     ![Aufgaben mit vier Zuständen im Fenster „Parallele Stapel“](../debugger/media/pdb_walkthrough_10.png "PDB_Walkthrough_10")

     Da Aufgabe 5 abgeschlossen wurde, wird sie nicht mehr angezeigt. Wenn dies auf Ihrem Computer nicht der Fall ist und der Deadlock nicht angezeigt wird, führen Sie den Code einen weiteren Schritt aus, indem Sie **F11** drücken.

     Aufgabe 3 und Aufgabe 4 warten nun auf einander und sind blockiert. Es sind auch fünf neue Aufgaben vorhanden, die untergeordnete Elemente von Aufgabe 2 darstellen und nun geplant sind. Geplante Aufgaben sind Aufgaben, die im Code gestartet, jedoch noch nicht ausgeführt wurden. Daher sind ihre Spalten **Speicherort** und **Threadzuweisung** leer.

     Rufen Sie das Fenster **Parallele Stapel** erneut auf. Der Header der einzelnen Felder weist jeweils eine QuickInfo auf, in der die Thread-IDs und -Namen angegeben werden. Wechseln Sie im Fenster **Parallele Stapel** zur Aufgabenansicht. Zeigen Sie auf einen Header, um die Aufgaben-ID sowie den Namen und den Status der Aufgabe anzuzeigen, wie in der folgenden Abbildung veranschaulicht.

     ![Header-QuickInfo im Fenster „Parallele Stapel“](../debugger/media/pdb_walkthrough_11.png "PDB_Walkthrough_11")

     Sie können die Aufgaben nach Spalten gruppieren. Klicken Sie im Fenster **Aufgaben** mit der rechten Maustaste auf den Spaltenheader **Status**, und klicken Sie dann auf **Nach Status gruppieren**. In der folgenden Abbildung ist das nach Status gruppierte Fenster **Aufgaben** dargestellt.

     ![Gruppierte Aufgaben im Fenster „Aufgaben“](../debugger/media/pdb_walkthrough_12.png "PDB_Walkthrough_12")

     Sie können auch nach einer beliebigen anderen Spalte gruppieren. Durch das Gruppieren von Aufgaben können sich auf eine Teilmenge von Aufgaben konzentrieren. Jede reduzierbare Gruppe weist eine Anzahl von Elementen auf, die zu einer Gruppe gehören.

     Die letzte zu untersuchende Funktion des Fensters **Aufgaben** ist das Kontextmenü, das aufgerufen wird, wenn Sie mit der rechten Maustaste auf eine Aufgabe klicken.

     Im Kontextmenü sind weitere Befehle enthalten, die vom Status der Aufgabe abhängen. Zu diesen können folgende Befehle zählen: **Kopieren**, **Alle auswählen**, **Hexadezimale Anzeige**, **Zu Aufgabe wechseln**, **Zugewiesenen Thread fixieren**, **Alle Threads bis auf diesen einfrieren** und **Zugewiesenen Thread reaktivieren** sowie **Flag**.

     Sie können den zugrunde liegenden Thread einer Aufgabe oder mehrerer Aufgaben einfrieren, oder Sie können alle Threads außer dem zugewiesenen Thread einfrieren. Ein eingefrorener Thread wird im Fenster **Aufgaben** wie im Fenster **Threads** durch ein blaues Symbol vom Typ *Pause* dargestellt.

## <a name="summary"></a>Zusammenfassung
 In dieser exemplarischen Vorgehensweise wurden die Debuggerfenster **Parallele Aufgaben** und **Parallele Stapel** veranschaulicht. Verwenden Sie diese Fenster für tatsächliche Projekte, in denen Code mit mehreren Threads enthalten ist. Sie können parallelen Code in C++, C# oder Visual Basic untersuchen.

## <a name="see-also"></a>Siehe auch
- [Debuggen von Multithreadanwendungen](../debugger/walkthrough-debugging-a-parallel-application.md)
- [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)
- [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)
- [Parallele Programmierung](/dotnet/standard/parallel-programming/index)
- [Concurrency Runtime](/cpp/parallel/concrt/concurrency-runtime)
- [Verwenden des Fensters "Parallele Stapel"](../debugger/using-the-parallel-stacks-window.md)
- [Verwenden des Fensters „Aufgaben“](../debugger/using-the-tasks-window.md)
