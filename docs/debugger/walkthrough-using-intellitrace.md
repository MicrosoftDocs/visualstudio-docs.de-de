---
title: Anzeigen von Ereignissen mit IntelliTrace | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie IntelliTrace in Visual Studio Enterprise zum Sammeln von Daten über bestimmte Ereignisse, Ereigniskategorien und einzelne Funktionsaufrufe sammeln.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e1c9c91a-0009-4c4e-9b4f-c9ab3a6022a7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6fef839b5473881450581db77a885da158e67bbc
ms.sourcegitcommit: 105e7b5a486262bc92939980383ceee068098a11
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/30/2020
ms.locfileid: "97815749"
---
# <a name="view-events-with-intellitrace-in-visual-studio-enterprise-c-visual-basic"></a>Anzeigen von Ereignissen mit IntelliTrace in Visual Studio Enterprise (C#, Visual Basic)

Sie können IntelliTrace zum Sammeln von Informationen über bestimmte Ereignisse oder Ereigniskategorien oder zum Erfassen von einzelnen Funktionsaufrufen zusätzlich zu den Ereignissen verwenden. In der folgenden Vorgehensweisen wird gezeigt, wie dies umzusetzen ist.

Sie können IntelliTrace in der Visual Studio Enterprise Edition verwenden, jedoch nicht in der Professional oder Community Edition.

## <a name="configure-intellitrace"></a><a name="GettingStarted"></a> Konfigurieren von IntelliTrace

Sie können ein Debugging nur mit IntelliTrace-Ereignissen durchführen. IntelliTrace-Ereignisse sind Debuggerereignisse, Ausnahmen, .NET Framework-Ereignisse und andere Systemereignisse. Bevor Sie mit dem Debuggen beginnen, sollten Sie bestimmte Ereignisse aktivieren oder deaktivieren, um die von IntelliTrace aufgezeichneten Ereignisse zu steuern. Weitere Informationen finden Sie unter [IntelliTrace-Funktionen](../debugger/intellitrace-features.md).

- Aktivieren Sie das IntelliTrace-Ereignis für den Dateizugriff. Wechseln Sie zur Seite **Extras > Optionen > IntelliTrace > IntelliTrace-Ereignisse**, und erweitern Sie die Kategorie **Datei**. Aktivieren Sie die Ereigniskategorie **Datei** . Dadurch werden alle Dateiereignisse (Zugriff, Schließen, Löschen) überprüft.

## <a name="create-your-app"></a>Erstellen der App

1. Erstellen Sie eine C#- Konsolenanwendung. Fügen Sie in der Datei "Program.cs" die folgende `using` -Anweisung hinzu:

    ```csharp
    using System.IO;
    ```

2. Erstellen Sie ein <xref:System.IO.FileStream> -Element in der Main-Methode, lesen Sie es aus, schließen Sie es, und löschen Sie die Datei. Fügen Sie eine weitere Zeile hinzu, um einen Haltepunkt festlegen zu können:

    ```csharp
    static void Main(string[] args)
    {
        FileStream fs = File.Create("WordSearchInputs.txt");
        fs.ReadByte();
        fs.Close();
        File.Delete("WordSearchInputs.txt");

        Console.WriteLine("done");
    }
    ```

3. Legen Sie einen Haltepunkt auf `Console.WriteLine("done");`fest.

## <a name="start-debugging-and-view-intellitrace-events"></a>Starten des Debuggens und Anzeigen von IntelliTrace-Ereignissen

1. Starten Sie das Debuggen wie gewohnt. (Drücken Sie **F5**, oder klicken Sie auf **Debuggen > Debuggen starten**.)

    > [!TIP]
    > Halten Sie während des Debuggens die Fenster **Lokal** und **Auto** geöffnet, um die Werte darin anzuzeigen und aufzuzeichnen.

2. Die Ausführung hält am Haltepunkt an. Wenn das Fenster **Diagnosetools** nicht angezeigt wird, klicken Sie auf **Debuggen > Fenster > IntelliTrace-Ereignisse**.

    Wechseln Sie im Fenster **Diagnosetools** zur Registerkarte **Ereignisse** (es sollten drei Registerkarten vorhanden sein: **Ereignisse**, **Speicherauslastung** und **CPU-Auslastung**). Die Registerkarte **Ereignisse** zeigt eine chronologische Liste aller Ereignisse, die mit dem letzten Ereignis endet, bevor die Ausführung vom Debugger unterbrochen wurde. Es sollte ein Ereignis namens **Access WordSearchInputs.txt** angezeigt werden.

    Der folgende Screenshot stammt aus Visual Studio 2015 Update 1.

    ![Screenshot des Visual Studio-Codefensters. Die Ausführung wird an einem Haltepunkt angehalten, und auf der Registerkarte „Ereignisse“ im Fenster „Diagnosetools“ werden Ereignisse aufgelistet.](../debugger/media/intellitrace-update1.png)

3. Wählen Sie das Ereignis aus, um die Details zu erweitern.

    Der folgende Screenshot stammt aus Visual Studio 2015 Update 1.

    ![Screenshot der Registerkarte „Ereignisse“ im Fenster der Diagnosetools von Visual Studio. Ein Ereignis ist ausgewählt und erweitert, um seine Details anzuzeigen.](../debugger/media/intellitraceupdate1-singleevent.png)

    Sie können den Link des Pfadnamens auswählen, um die Datei zu öffnen. Wenn der vollständige Pfadname nicht verfügbar ist, wird das Dialogfeld **Datei öffnen** angezeigt.

    Klicken Sie auf **Verlaufsbezogenes Debugging aktivieren**, um den Kontext des Debuggers auf den Zeitpunkt festzulegen, zu dem das ausgewählte Ereignis gesammelt wurde. So werden Verlaufsdaten in den Fenstern **Aufrufliste**, **Lokal** sowie in den anderen zugehörigen Debuggerfenstern angezeigt. Wenn Quellcode verfügbar ist, bewegt Visual Studio den Zeiger auf den entsprechenden Code im Quellcodefenster, damit Sie ihn überprüfen können.

    Der folgende Screenshot stammt aus Visual Studio 2015 Update 1.

    ![Screenshot des Visual Studio-Codefensters. Die Ausführung ist an einem Haltepunkt angehalten, ein Ereignis ist ausgewählt, und die entsprechende Codezeile ist hervorgehoben.](../debugger/media/historicaldebugging-update1.png)

4. Wenn Sie den Fehler nicht finden, überprüfen Sie andere Ereignisse, die zu dem Fehler geführt haben. Sie können auch veranlassen, dass IntelliTrace Aufrufinformationen aufzeichnet, damit Sie die Funktionsaufrufe schrittweise durchlaufen können.

## <a name="next-steps"></a>Nächste Schritte

Sie können einige der erweiterten Features von IntelliTrace mit verlaufsbezogenem Debuggen verwenden:

- Wenn Sie Momentaufnahmen anzeigen möchten, finden Sie weitere Informationen unter [Untersuchen von vorherigen App-Zuständen mithilfe von IntelliTrace](../debugger/view-historical-application-state.md).
- Informationen zum Untersuchen von Variablen und Navigieren in Code finden Sie unter [Untersuchen der App mit verlaufsbezogenem Debuggen](../debugger/historical-debugging-inspect-app.md).
