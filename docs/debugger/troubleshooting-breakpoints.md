---
title: Troubleshooting von Haltepunkten im Debugger | Microsoft-Dokumentation
description: Wenn ein Breakpoint deaktiviert ist oder nicht festgelegt werden konnte, wird er als leerer Kreis angezeigt. Hier finden Sie Informationen zu Problemen, die beim Festlegen von Breakpoints auftreten können.
ms.custom: SEO-VS-2020, seodec18
ms.date: 01/23/2018
ms.topic: troubleshooting
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a07f92eccd7884ea3cc3871d04285a82cb5cb62e
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148051"
---
# <a name="troubleshoot-breakpoints-in-the-visual-studio-debugger"></a>Troubleshooting von Haltepunkten im Visual Studio-Debugger

## <a name="breakpoint-warnings"></a>Warnungen zu Haltepunkten

Beim Debuggen kann ein Haltepunkt zwei verschiedene Symbole aufweisen: einen gefüllten roten Kreis und einen hohlen (weiß gefüllten) Kreis. Wenn der Debugger im Zielprozess einen Haltepunkt erfolgreich festlegen kann, bleibt der Kreis gefüllt und rot. Wenn der Haltepunkt ein leerer Kreis ist, ist entweder der Haltepunkt deaktiviert, oder es wurde beim Festlegen des Haltepunkts eine Warnung zurückgegeben. Zeigen Sie auf den Haltepunkt, und prüfen Sie, ob eine Warnung vorliegt, um herauszufinden, welcher der beiden Fälle vorliegt.

In den folgenden beiden Abschnitten werden wichtige Warnungen und die entsprechende Problembehandlung beschrieben.

### <a name="no-symbols-have-been-loaded-for-this-document"></a>„No Symbols have been loaded for this document“ (Für dieses Dokument wurden keine Symbole geladen)

Wechseln Sie in das Fenster **Module** (**Debuggen** > **Fenster** > **Module**), und überprüfen Sie, ob das Modul geladen wurde.
* Wenn das Modul geladen ist, überprüfen Sie in der Spalte **Symbolstatus**, ob Symbole geladen wurden.
  * Wenn keine Symbole geladen wurden, überprüfen Sie den Symbolstatus, um das Problem zu diagnostizieren. Klicken Sie im Kontextmenü eines Moduls im Fenster **Module** auf **Symbolladeinformationen…** , um sich anzeigen zu lassen, wo der Debugger versucht hat, Symbole zu laden. Weitere Informationen zum Laden von Symbolen finden Sie unter [Angeben von Symboldateien (.pdb) und Quelldateien im Visual Studio-Debugger (C#, C++, Visual Basic F#)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).
  * Wenn Symbole geladen wurden, enthält die PDB-Datei keine Informationen zu Ihren Quelldateien. Dies kann z. B. an folgenden Ursachen liegen:
    * Wenn Ihre Quelldateien erst vor Kurzem hinzugefügt wurden, sollten Sie sich vergewissern, dass eine aktuelle Version des Moduls geladen wird.
    * Es ist möglich, mit der Linkeroption **/PDBSTRIPPED** bereinigte PDB-Dateien zu erstellen. Bereinigte PDB-Dateien enthalten keine Quelldateiinformationen. Vergewissern Sie sich, dass Sie mit einer vollständigen, nicht mit einer bereinigten PDB-Datei arbeiten.
    * Die PDB-Datei ist teilweise beschädigt. Löschen Sie die Datei, und führen Sie einen bereinigen Build des Moduls aus, um das Problem zu beheben.

* Wenn das Modul nicht geladen ist, überprüfen Sie Folgendes, um die Ursache zu ermitteln:
  * Vergewissern Sie sich, dass Sie den richtigen Prozess debuggen.
  * Überprüfen Sie, ob Sie die richtige Art von Code debuggen. Im Fenster **Prozesse** (**Debuggen** > **Fenster** > **Prozesse**) können Sie herausfinden, für welche Art von Code der Debugger konfiguriert wurde. Wenn Sie z. B. versuchen, C#-Code zu debuggen, sollten Sie sich vergewissern, dass der Debugger für den entsprechenden Typ und die entsprechende .NET-Version konfiguriert ist (z. B. für verwalteten v4\*-, verwalteten v2\*/v3\*- oder verwalteten CoreCLR-Code).

### <a name="-the-current-source-code-is-different-from-the-version-built-into"></a>"… Der aktuelle Quellcode weicht jedoch von der in (…) erstellten Version ab."

Wenn eine Quelldatei geändert wurde und die Quelle nicht mehr mit dem Code übereinstimmt, den Sie debuggen, legt der Debugger standardmäßig keine Haltepunkte im Code fest. Normalerweise tritt dieses Problem auf, wenn eine Quelldatei geändert wurde, ohne den Quellcode neu zu erstellen. Sie müssen das Projekt neu erstellen, um dieses Problem zu beheben. Wenn das Buildsystem davon ausgeht, dass das Projekt bereits auf dem neuesten Stand ist, auch wenn dies nicht der Fall ist, können Sie erzwingen, dass das Projektsystem neu erstellt wird. Dazu müssen Sie die Quelldatei noch einmal speichern oder die Buildausgabe des Projekts vor dem Erstellen bereinigen.

In seltenen Szenarios müssen Sie unter Umständen bei nicht übereinstimmendem Quellcode debuggen. Dies kann jedoch zu verwirrendem Debuggingverhalten führen. Daher sollten Sie sich sicher sein, dass Sie genau so vorgehen müssen.

Führen Sie einen der folgenden Schritte aus, um diese Sicherheitsüberprüfungen zu deaktivieren:
* Zum Bearbeiten eines einzelnen Haltepunkts müssen Sie im Editor auf das Symbol des Haltepunkts zeigen und auf das Einstellungssymbol (Zahnrad) klicken. Daraufhin wird dem Editor ein Peek-Fenster hinzugefügt. Oben im Peek-Fenster ist ein Link aufgeführt, der die Position des Haltepunkts angibt. Klicken Sie auf den Link, um die Änderung an der Position des Haltepunkts zuzulassen, und aktivieren Sie das Kontrollkästchen **Der Quellcode darf sich vom Original unterscheiden.** .
* Wenn Sie diese Einstellung für alle Haltepunkte bearbeiten möchten, navigieren Sie zu **Debuggen** > **Optionen und Einstellungen**. Deaktivieren Sie auf der Seite **Debugging/Allgemein** das Kontrollkästchen **Quelldateien müssen exakt mit der Originalversion übereinstimmen** . Achten Sie darauf, diese Option zu reaktivieren, wenn das Debugging abgeschlossen ist.

## <a name="the-breakpoint-was-successfully-set-no-warning-but-didnt-hit"></a>Der Haltepunkt wurde erfolgreich festgelegt (keine Warnung), jedoch nicht erreicht

In diesem Abschnitt erfahren Sie, wie Sie das Problem beheben, dass der Debugger keine Warnungen anzeigt: Der Haltepunkt wird als gefüllter roter Kreis angezeigt, wenn der Debugger aktiv ausgeführt wird, und dennoch wird der Haltepunkt nicht erreicht.

Sie können bspw. Folgendes überprüfen:
1. Wenn Ihr Code in mehr als einem Prozess oder auf mehr als einem Computer ausgeführt wird, müssen Sie sicherstellen, dass Sie auch den richtigen Prozess oder Computer debuggen.
2. Überprüfen Sie, ob Ihr Code ausgeführt wird. Fügen Sie dazu in der Codezeile, in die Sie den Haltepunkt platzieren möchten, einen Aufruf von `System.Diagnostics.Debugger.Break` (C#/VB) oder `__debugbreak` (C++) hinzu, und erstellen Sie Ihr Projekt anschließend neu.
3. Wenn Sie optimierten Code debuggen, müssen Sie sicherstellen, dass die Funktion, die Ihren Haltepunkt enthält, keine Inlinefunktion ist. Der Test mit `Debugger.Break`, der zuvor beschrieben wurde, kann auch für diese Überprüfung herangezogen werden.

## <a name="i-deleted-a-breakpoint-but-i-continue-to-hit-it-when-i-start-debugging-again"></a>Ich habe einen Haltepunkt gelöscht, aber erreiche ihn beim erneuten Debuggen weiterhin

Wenn Sie einen Haltepunkt während des Debuggens gelöscht haben, kann der Haltepunkt beim nächsten Debuggen dennoch wieder erreicht werden. Zum Beenden des Erreichens dieses Haltepunkt müssen Sie sicherstellen, dass alle Instanzen des Haltepunkts aus dem Fenster **Haltepunkte** entfernt wurden.
