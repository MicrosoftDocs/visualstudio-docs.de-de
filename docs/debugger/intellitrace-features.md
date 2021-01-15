---
title: IntelliTrace-Features | Microsoft-Dokumentation
description: In diesem Artikel finden Sie Informationen zu IntelliTrace-Features in Visual Studio. Sie können IntelliTrace zum Aufzeichnen von Ereignissen und Methodenaufrufen in Ihrer Anwendung verwenden.
ms.custom: SEO-VS-2020
ms.date: 09/19/2018
ms.topic: conceptual
helpviewer_keywords:
- IntelliTrace, debugging with events
- IntelliTrace, recording execution history
- debugging [Visual Studio ALM], recording execution history
- IntelliTrace, turn off
- IntelliTrace, navigating event and call history
- IntelliTrace, saving your session
- IntelliTrace, enabling
- IntelliTrace, start debugging
- IntelliTrace, debugging with events and call information
- IntelliTrace, disabling
- IntelliTrace, turn on
- debugging [Visual Studio ALM], IntelliTrace
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2f5d4603e052cd5968055304290559b8a8d5a56a
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148636"
---
# <a name="intellitrace-features-c-visual-basic-c"></a>IntelliTrace-Features (C#, Visual Basic, C++)

Sie können IntelliTrace verwenden, um Ereignisse und Methodenaufrufe Ihrer Anwendung aufzuzeichnen, mit deren Hilfe Sie den Status (Aufruflisten- und lokale Variablenwerte) zu unterschiedlichen Punkten in der Ausführung ermitteln können. Starten Sie das Debugging wie gewohnt – IntelliTrace ist standardmäßig aktiviert, und im neuen Fenster **Diagnosetools** unter der Registerkarte **Ereignisse** werden Ihnen die von IntelliTrace erfassten Informationen angezeigt. Wählen Sie ein Ereignis aus, und klicken Sie auf **Verlaufsbezogenes Debugging aktivieren**, um die Aufrufliste und lokal erfasste Informationen für dieses Ereignis anzuzeigen.

Eine detaillierte Beschreibung finden Sie unter [Anzeigen von Ereignissen mit IntelliTrace in Visual Studio Enterprise (C#, Visual Basic)](../debugger/walkthrough-using-intellitrace.md).

IntelliTrace ist verfügbar in Visual Studio Enterprise Edition, jedoch nicht in der Visual Studio Professional oder Community Edition.

Öffnen Sie die Seite **Tools > Optionen > IntelliTrace**, um sich zu vergewissern, dass IntelliTrace aktiviert ist. Das Kontrollkästchen **IntelliTrace aktivieren** sollte standardmäßig aktiviert sein.

> [!NOTE]
> Der Bereich der Einstellungen auf der **IntelliTrace**-Optionsseite umfasst Visual Studio vollständig, nicht nur Projekte oder Projektmappen. Eine Änderung dieser Einstellungen gilt für alle Instanzen von Visual Studio, alle Debugsitzungen und alle Projekte oder Projektmappen.

## <a name="choose-the-events-that-intellitrace-records-c-visual-basic"></a><a name="ChooseEvents"></a> Auswählen der von IntelliTrace aufgezeichneten Ereignisse (C#, Visual Basic)

Sie können die Aufzeichnung bestimmter IntelliTrace-Ereignisse aktivieren oder deaktivieren.

Wenn Sie gerade einen Debugging-Vorgang ausführen, beenden Sie diesen. Wechseln Sie zu **Extras > Optionen > IntelliTrace > IntelliTrace-Ereignisse**. Wählen Sie die Ereignisse, die IntelliTrace aufgezeichnen soll.

## <a name="collect-snapshots-c-visual-basic-c"></a><a name="Snapshots"></a> Erfassen von Momentaufnahmen (C#, Visual Basic, C++ )

Dieses Feature ist nicht automatisch aktiviert. IntelliTrace kann bei jedem Haltepunkt und jedem Ereignis in einem Debuggerschritt Momentaufnahmen Ihrer Anwendung aufzeichnen. Beim verlaufsbezogenen Debuggen können Sie sich diese Momentaufnahmen dann anzeigen lassen. Eine Momentaufnahme bietet Ihnen einen Überblick über den vollständigen Anwendungszustand. Navigieren Sie zu **Extras > Optionen > IntelliTrace > Allgemein**, und klicken Sie auf **IntelliTrace snapshots (managed and native)** (IntelliTrace-Momentaufnahmen [verwaltet und nativ]). Weitere Informationen finden Sie unter [Inspect previous app states using IntelliTrace (Untersuchen vorheriger App-Zustände mithilfe von IntelliTrace)](../debugger/view-historical-application-state.md).

Momentaufnahmen sind ab Visual Studio Enterprise 2017, Version 15.5 und höher verfügbar und erfordern Windows 10 Anniversary Update oder höher.  Für .NET Core- und ASP.NET Core-Apps ist Visual Studio Enterprise 2017, Version 15.7 erforderlich. Für native Apps, die für Windows entwickelt wurden, ist Visual Studio Enterprise 2017, Version 15.9 Preview 2 erforderlich.

## <a name="collect-intellitrace-events-and-call-information-c-visual-basic"></a><a name="GoingFurther"></a> Sammeln von IntelliTrace-Ereignissen und Aufrufen von Informationen (C#, Visual Basic)

Diese Option ist nicht standardmäßig aktiviert, aber IntelliTrace kann Methodenaufrufe zusammen mit Ereignissen aufzeichnen. Wählen Sie unter **Extras > Optionen > IntelliTrace > Allgemein** die Option **IntelliTrace events and call information (managed only)** (IntelliTrace-Ereignisse und Aufrufinformationen) aus, um die Erfassung von Methodenaufrufen zu aktivieren.

Für .NET Core- und ASP.NET Core-Apps sind zurzeit keine Aufrufinformationen verfügbar.

Auf diese Weise können Sie den Verlauf der Aufrufliste anzeigen und Aufrufe in Ihrem Code schrittweise durchlaufen. IntelliTrace zeichnet Daten wie z. B. Methodennamen, Methodeneinstiegs- und -Endpunkte sowie bestimmte Parameter- und Rückgabewerte auf.

> [!TIP]
> Diese Option ist standardmäßig nicht aktiviert, da dadurch ein erheblicher Mehraufwand erforderlich ist. IntelliTrace muss nicht nur jeden Methodenaufruf abfangen, den Ihre Anwendung vornimmt, sondern es muss auch viel größere Datenmenge verarbeiten, wenn es um die Anzeige der Daten auf dem Bildschirm geht.
>
> Sie können den Leistungsaufwand reduzieren, indem Sie die Ereignisliste beschränken, die von IntelliTrace aufgezeichnet werden, und indem Sie die Anzahl der Module auf ein Mindestmaß reduzieren. Weitere Informationen finden Sie unter [Steuern der Anzahl der von IntelliTrace aufgezeichneten Aufrufinformationen](../debugger/intellitrace-features.md#ControlCallData).

### <a name="use-the-navigation-gutter"></a>Verwenden des Navigationsbundstegs

Sie können den Navigationsbundsteg verwenden, der unten links neben dem Code-Fenster angezeigt wird. Wenn den Navigationsbundsteg nicht angezeigt wird, wechseln Sie zu **Extras > Optionen > IntelliTrace > Erweitert**, und wählen Sie **Den Navigationsbundsteg im Debugmodus anzeigen**.

Mithilfe des Navigationsbundstegs können Sie in den Methodenaufrufen und Ereignissen im verlaufsbezogenen Debugmodus vor und zurück navigieren. Weitere Informationen zum verlaufsbezogenen Debuggen finden Sie unter [Verlaufsbezogenes Debugging](../debugger/historical-debugging.md). Dazu gibt es eine Reihe von Befehlen:

|Befehl|Beschreibung|
|-|-|
|**Debuggerkontext hier festlegen**|Legt den Debugkontext auf den Zeitrahmen des Aufrufs fest, in dem er angezeigt wird.<br /><br /> Dieses Symbol wird nur für die aktuelle Aufrufliste angezeigt.|
|**Zur Aufrufwebsite zurückkehren**|Bewegen Sie den Zeiger und den Debugkontext zurück zu dem Punkt, als die aktuelle Funktion aufgerufen wurde.<br /><br /> Wenn Sie im Live-Debugmodus sind, aktiviert dieser Befehl das verlaufsbezogene Debugging. Wenn Sie zur ursprünglichen Ausführungsunterbrechung navigieren, wird das verlaufsbezogene Debugging deaktiviert und das Live-Debuggen aktiviert.|
|**Zum vorherigen Aufruf oder IntelliTrace-Ereignis wechseln**|Bewegt den Zeiger und den Debugkontext zurück zum vorherigen Aufruf oder Ereignis.<br /><br /> Wenn Sie im Live-Debugmodus sind, aktiviert dieser Befehl das verlaufsbezogene Debugging.|
|**Einzelschritt**|Rufen Sie die aktuell ausgewählte Funktion auf.<br /><br /> Dieser Befehl ist nur im verlaufsbezogenen Debugmodus verfügbar.|
|**Zum nächsten Aufruf oder IntelliTrace-Ereignis wechseln**|Setzt den Zeiger- und Debugkontext zeitlich auf den nächsten Aufruf oder das nächste Ereignis vor, für den/das IntelliTrace-Daten vorhanden sind.<br /><br /> Dieser Befehl ist nur im verlaufsbezogenen Debugmodus verfügbar.|
|**Zum Livemodus wechseln**|Zurück zum Live-Debugmodus|

### <a name="search-for-a-line-or-method-in-intellitrace"></a>In IntelliTrace nach einer Zeile oder Methode suchen

Sie können nur bei aktivierten Methodenaufrufinformationen nach Methoden suchen. Sie können den IntelliTrace-Verlauf nach einer bestimmten Zeile oder Methode durchsuchen. Während die Ausführung des Debuggers angehalten ist, können Sie mit der rechten Maustaste in den Text der Funktion klicken, um das Kontextmenü anzuzeigen, und auf die Optionen **In IntelliTrace nach dieser Zeile suchen** oder **In IntelliTrace nach dieser Methode suchen** klicken.

### <a name="control-how-much-call-information-intellitrace-records"></a><a name="ControlCallData"></a> Steuern der Anzahl der von IntelliTrace aufgezeichneten Aufrufinformationen

Standardmäßig erfasst IntelliTrace Informationen für alle Module, die von der Projektmappe verwendet werden. Sie können IntelliTrace so einstellen, dass nur Aufrufinformationen für die Module erfasst werden, die für Sie von Bedeutung sind. Unter **Extras > Optionen > IntelliTrace > Module** können Sie die in IntelliTrace einzuschließenden oder auszuschließenden Module angeben. IntelliTrace erfasst nur die Ereignisse, die aus den Modulen stammen, die Sie angegeben haben, und die Methodenaufrufe, die in den Modulen aufgetreten sind, die für Sie von Bedeutung sind.

Um mehrere Module hinzuzufügen, verwenden Sie das Platzhalterzeichen * am Anfang oder am Ende der Zeichenfolge. Als Modulnamen müssen Dateinamen und keine Assemblynamen verwendet werden. Dateipfade werden nicht akzeptiert.

Versuchen Sie, die Anzahl der Module auf ein Mindestmaß zu beschränken. Sie erhalten eine bessere Leistung, da weniger Daten erfasst werden. Sie erhalten auch weniger Störungen auf der Benutzeroberfläche, da weniger Daten verarbeitet werden müssen.

## <a name="save-intellitrace-data-to-file-c-visual-basic-c"></a><a name="SaveSession"></a> Speichern von IntelliTrace-Daten in Dateien (C#, Visual Basic, C++)

Sie können die von IntelliTrace erfassten Daten speichern, indem Sie während des Debuggens zu **Debuggen > IntelliTrace > IntelliTrace-Sitzung speichern** wechseln, solange die Anwendung unterbrochen ist. Das Menüelement ist deaktiviert, und Sie können die von IntelliTrace erfassten Daten nicht speichern, sofern die Anwendung noch ausgeführt wird oder das Debuggen bereits beendet wurde.

Sie können IntelliTrace so konfigurieren, dass Daten automatisch in einer Datei gespeichert werden, indem Sie auf **Extras > Optionen > IntelliTrace > Erweitert** klicken und **IntelliTrace-Aufzeichnungen in diesem Verzeichnis speichern** auswählen. Sie können auch eine feste Größe für die generierte Datei konfigurieren, sodass IntelliTrace ältere Daten überschreibt, wenn kein Speicherplatz mehr verfügbar ist. Visual Studio erstellt zwei Dateien für jede IntelliTrace-Sitzung, wenn sie automatisch gespeichert und der Visual Studio-Hostprozess (vshost.exe) aktiviert ist.

> [!TIP]
> Um Speicherplatz zu sparen, deaktivieren Sie die Speicherung von Dateien, wenn Sie sie nicht mehr benötigen. Alle vorhandenen Dateien werden nicht gelöscht. Sie können die Datei bei Bedarf immer aus dem Kontextmenü speichern.

Wenn Sie IntelliTrace-Daten in einer Datei speichern, erhalten Sie eine ITRACE-Datei für jeden Prozess, den IntelliTrace erfasst hat. Sie können dann die ITRACE-Datei in Visual Studio öffnen, indem Sie zu **Datei > Öffnen > Datei** wechseln und im Dialogfeld „Datei öffnen“ die ITRACE-Datei auswählen. Weitere Informationen finden Sie unter [Verwenden gespeicherter IntelliTrace-Daten](../debugger/using-saved-intellitrace-data.md).

## <a name="blogs"></a>Blogs

[IntelliTrace in Visual Studio Enterprise 2015](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-ultimate-2015/)

[Exemplarische Vorgehensweise für das Livedebugging mit IntelliTrace in Visual Studio 2015 (Text-Editor)](https://devblogs.microsoft.com/devops/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-text-editor/)

[Exemplarische Vorgehensweise für das Livedebugging mit IntelliTrace in Visual Studio 2015 (SocialClub)](https://devblogs.microsoft.com/devops/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-social-club/)

[IntelliTrace in Visual Studio Enterprise 2015 unterstützt nun das Anfügen](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-enterprise-2015-now-supports-attach/)

[Sammeln von Daten aus einem Windows-Dienst mithilfe des eigenständigen IntelliTrace-Sammlers](https://devblogs.microsoft.com/devops/collect-data-from-a-windows-service-using-the-intellitrace-standalone-collector/)

[Bearbeiten des IntelliTrace-Sammlungsplans](https://devblogs.microsoft.com/devops/editing-the-intellitrace-collection-plan)

[Benutzerdefinierte Quellüberwachung und Debuggen mit IntelliTrace](https://devblogs.microsoft.com/devops/custom-tracesource-and-debugging-using-intellitrace/)

[Eigenständiger IntelliTrace-Sammler und unter Active Directory-Konten ausgeführte Anwendungspools](https://devblogs.microsoft.com/devops/intellitrace-standalone-collector-and-application-pools-running-under-active-directory-accounts/)

## <a name="forums"></a>Foren

[Visual Studio Debugger](https://social.msdn.microsoft.com/Forums/en-US/home)

## <a name="videos"></a>Videos

[Benutzeroberfläche von IntelliTrace](https://channel9.msdn.com/Series/Visual-Studio-2015-Enterprise-Videos/IntelliTrace-Experience)

[Historical Debugging with IntelliTrace in Microsoft Visual Studio Ultimate 2015 (Verlaufsbezogenes Debuggen mit In# in Microsoft Visual Studio Ultimate 2015)](https://channel9.msdn.com/events/Ignite/2015/BRK3716)
