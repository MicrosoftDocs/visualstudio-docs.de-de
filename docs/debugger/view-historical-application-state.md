---
title: Anzeigen des vorherigen App-Zustands mithilfe von IntelliTrace
description: Informationen zum Aufnehmen von Momentaufnahmen und Anzeigen von Momentaufnahmen mit der IntelliTrace-Funktion „Schritt zurück“
ms.custom: seodec18
ms.date: 09/19/2018
ms.topic: tutorial
ms.assetid: 7c60d929-d993-49dc-9db3-43b30be9912b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f1ab54ccb3820b3a03724c30d16f08b3e8a45493
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933101"
---
# <a name="inspect-previous-app-states-using-intellitrace-step-back-in-visual-studio-visual-studio-enterprise"></a>Untersuchen von vorherigen App-Zuständen mithilfe des IntelliTrace-Features „Schritt zurück“ in Visual Studio (Visual Studio Enterprise)

Das IntelliTrace-Feature „Schritt zurück“ nimmt automatisch bei jedem Breakpoint und Debuggerschritt eine Momentaufnahme Ihrer Anwendung auf. Durch die erfassten Momentaufnahmen können Sie zu vorherigen Haltepunkten oder Schritten zurückkehren und sich den Zustand der Anwendung so anzeigen lassen, wie er zuvor war. Mit dem IntelliTrace-Feature „Step-back“ können Sie Zeit sparen, wenn Sie den vorherigen Zustand der Anwendung anzeigen oder diesen wiederherstellen, aber das Debuggen nicht erneut starten möchten.

„Schritt zurück“ ist ab Visual Studio Enterprise 2017 Version 15.5 und höher verfügbar und erfordert Windows 10 Anniversary Update oder höher. Das Feature wird derzeit zum Debuggen von ASP.NET, WinForms, WPF, verwalteten Konsolen-Apps und verwalteten Klassenbibliotheken unterstützt. Ab Visual Studio 2017 Enterprise Version 15.7 wird das Feature ebenfalls für ASP.NET Core und .NET Core unterstützt. Ab Visual Studio 2017 Enterprise Version 15.9 Preview 2 wird das Feature ebenfalls für native Apps für Windows unterstützt. Das Debuggen von UWP-Anwendungen wird derzeit nicht unterstützt.

In diesem Tutorial werden Sie Folgendes durchführen:

> [!div class="checklist"]
> * Aktivieren von IntelliTrace-Ereignissen und Momentaufnahmen
> * Navigieren von Ereignissen mithilfe von Step-back- und Step-forward-Befehlen
> * Anzeigen von Ereignismomentaufnahmen

## <a name="enable-intellitrace-events-and-snapshots-mode"></a>Aktivieren von IntelliTrace-Ereignissen und des Momentaufnahmenmodus

1. Öffnen Sie Ihr Projekt in Visual Studio Enterprise.

1. Öffnen Sie **Extras** > **Optionen** > **IntelliTrace-Einstellungen**, und wählen Sie die Option **IntelliTrace-Ereignisse und -Momentaufnahmen** aus.

    Ab Visual Studio 2017 Enterprise Version 15.9 Preview 2 lautet diese Option **IntelliTrace snapshots** (IntelliTrace-Momentaufnahmen) (verwaltet und nativ).

    ![Aktivieren von IntelliTrace-Ereignissen und des Momentaufnahmenmodus](../debugger/media/intellitrace-enable-snapshots.png "Aktivieren von IntelliTrace-Ereignissen und des Momentaufnahmenmodus")

1. Wenn Sie Optionen zum Anzeigen von Momentaufnahmen bei Ausnahmen konfigurieren möchten, wählen Sie **IntelliTrace** > **Erweitert** über das Dialogfeld **Optionen** aus.

    Diese Optionen sind ab Visual Studio 2017 Enterprise Version 15.7 verfügbar.

    ![Konfigurieren des Verhalten für Momentaufnahmen bei Ausnahmen](../debugger/media/intellitrace-enable-snapshots-on-exceptions.png)

    Wenn Sie Ereignisse und Momentaufnahmen aktivieren, wird das Erstellen von Momentaufnahmen bei Ausnahme ebenfalls standardmäßig aktiviert. Sie können Momentaufnahmen bei Ausnahmen deaktivieren, indem Sie das Kontrollkästchen **Collect snapshots on exception events** (Momentaufnahmen bei Ausnahmeereignissen sammeln) deaktivieren. Wenn dieses Feature aktiviert ist, werden Momentaufnahmen bei nicht behandelten Ausnahmen erstellt. Bei behandelten Ausnahmen werden Momentaufnahmen nur erstellt, wenn die Ausnahme ausgelöst wird, und wenn es sich nicht um eine erneut ausgelöste Ausnahme handelt, die zuvor schon einmal ausgelöst wurde. Sie können eine maximale Anzahl von Momentaufnahmen bei Ausnahmen festlegen, indem Sie einen Wert aus der Dropdownliste auswählen. Die maximale Anzahl gilt für jedes Mal, wenn Ihre App in den Unterbrechungsmodus wechselt (z.B. wenn Ihre App einen Breakpoint erreicht).

    > [!NOTE]
    > Momentaufnahmen werden nur bei Ausnahmeereignissen erstellt, die von IntelliTrace aufgezeichnet werden. Für verwalteten Code können Sie angeben, welche Ereignisse von IntelliTrace aufgezeichnet werden, indem Sie **Extras** > **Optionen** > **IntelliTrace-Ereignisse** auswählen.

1. Legen Sie in Ihrem Projekt mindestens einen Breakpoint fest, und beginnen Sie mit dem Debuggen (drücken Sie **F5**). Starten Sie das Debuggen alternativ, indem Sie Ihren Code schrittweise durchlaufen (**F10** oder **F11**).

    IntelliTrace erstellt eine Momentaufnahme des Anwendungsprozesses bei jedem Debuggerschritt, Breakpointereignis und nicht behandelten Ausnahmeereignis. Diese Ereignisse werden auf der Registerkarte **Ereignisse** im Fenster **Diagnosetools** zusammen mit anderen IntelliTrace-Ereignissen aufgezeichnet. Um dieses Fenster zu öffnen, klicken Sie auf **Debuggen** > **Fenster** > **Diagnosetools anzeigen**.

    Ein Kamerasymbol wird neben den Ereignissen angezeigt, für die Momentaufnahmen verfügbar sind.

    ![Registerkarte „Ereignisse“ mit Momentaufnahmen](../debugger/media/intellitrace-events-tab-with-snapshots.png "Registerkarte „Ereignisse“ mit Momentaufnahmen bei Breakpoints und Schritten")

    Aus Leistungsgründen werden Momentaufnahmen nicht erstellt, wenn Sie die Schritte sehr schnell durchlaufen. Wenn kein Kamerasymbol neben dem Schritt angezeigt wird, versuchen Sie, die Schritte langsamer auszuführen.

## <a name="navigate-and-view-snapshots"></a>Navigieren und Anzeigen von Momentaufnahmen

1. Navigieren Sie zwischen Ereignissen, indem Sie die Schaltflächen **Schritt zurück** (ALT+[) und **Schritt vorwärts** (ALT+]) in der „Debuggen“-Symbolleiste verwenden.

    Mit diesen Schaltflächen können Sie durch die Ereignisse navigieren, die in der Registerkarte **Ereignisse** des Fensters **Diagnosetools** angezeigt werden. Wenn Sie mit „Schritt zurück“ oder „Schritt vorwärts“ zu einem Ereignis navigieren, wird das [verlaufsbezogene Debuggen](../debugger/historical-debugging.md) für das ausgewählte Ereignis automatisch aktiviert.

    ![Schaltflächen „Schritt zurück“ und „Schritt vorwärts“](../debugger/media/intellitrace-step-back-icons-description.png "Schaltflächen „Schritt zurück“ und „Schritt vorwärts“")

    Wenn Sie einen Schritt zurück oder vorwärts gehen, wird Visual Studio in den Modus „Verlaufsbezogenes Debugging“ versetzt. In diesem Modus wechselt der Kontext des Debuggers in den Zeitraum, als das ausgewählte Ereignis aufgezeichnet wurde. Visual Studio verschiebt auch den Zeiger auf die entsprechende Codezeile im Quellcodefenster.

    Über diese Ansicht können Sie die Werte in den Fenstern **Call Stack** (Aufrufliste), **Locals** (Lokale), **Autos** und **Watch** (Überwachen) untersuchen. Sie können auch mit dem Mauszeiger auf die Variablen zeigen, um DataTips anzuzeigen und Ausdrucksauswertungen im **Direktfenster** auszuführen. Die Daten, die angezeigt werden, stammen von der Momentaufnahme des Anwendungsprozesses, die zu diesem Zeitpunkt erstellt wurde.

    Wenn Sie beispielsweise einen Breakpoint erreicht haben und einen Schritt durchgeführt haben (**F10**), wird Visual Studio über die Schaltfläche **Schritt vorwärts** entsprechend dem Breakpoint in der Codezeile in den verlaufsbezogenen Modus versetzt.

    ![Aktivieren des verlaufsbezogenen Modus für ein Ereignis mit einer Momentaufnahme](../debugger/media/intellitrace-historical-mode-with-snapshot.png "Aktivieren des verlaufsbezogenen Modus für ein Ereignis mit einer Momentaufnahme")

2. Klicken Sie auf **Weiter (F5)** oder auf den Link **Zurück zum Livedebugging** in der Infoleiste, um zur Liveausführung zurückzukehren.

3. Sie können ebenso eine Momentaufnahme über die Registerkarte **Ereignisse** anzeigen. Wählen Sie dazu ein Ereignis mit einer Momentaufnahme aus, und klicken Sie auf **Verlaufsbezogenes Debugging aktivieren**.

    ![Aktivieren des verlaufsbezogenen Debuggens für ein Ereignis](../debugger/media/intellitrace-activate-historical-debugging.png "Aktivieren des verlaufsbezogenen Debuggens für ein Ereignis")

    Anders als beim Befehl **Nächste Anweisung festlegen** wird Ihr Code durch das Anzeigen einer Momentaufnahme nicht erneut ausgeführt. Stattdessen erhalten Sie eine statische Ansicht des Anwendungszustands zu einem Zeitpunkt, der in der Vergangenheit liegt.

    ![Übersicht über die Funktion „Schritt zurück“ von IntelliTrace](../debugger/media/intellitrace-step-back-overview.png "Übersicht über die Funktion „Schritt zurück“ von IntelliTrace")

    Weitere Informationen zum Untersuchen von Variablen in Visual Studio finden Sie unter [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md).

## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen (FAQs)

#### <a name="how-is-intellitrace-step-back-different-from-intellitrace-events-only-mode"></a>Wie unterscheidet sich „Schritt zurück“ in IntelliTrace von der ausschließlichen Verwendung des IntelliTrace-Ereignismodus?

Im IntelliTrace-Modus zum ausschließlichen Verwenden von Ereignissen ist das Aktivieren des verlaufsbezogenen Debuggens von Einzelschritten und Breakpoints nicht gestattet. IntelliTrace erfasst jedoch nur Daten in den Fenstern **Locals** (Lokale) und **Autos**, falls diese geöffnet sind. Es werden zudem ausschließlich Daten erfasst, die erweitert sind und sich in der Ansicht befinden. Im Modus zum ausschließlichen Verwenden von Ereignissen haben Sie selten eine vollständige Ansicht der Variablen und komplexen Objekte. Zusätzlich werden die Ausdrucksauswertung und das Anzeigen von Daten im **Überwachungsfenster** nicht unterstützt.

Wenn sich IntelliTrace im Ereignis- und Momentaufnahmemodus befindet, wird die gesamte Momentaufnahme des Anwendungsprozesses erfasst, einschließlich der komplexen Objekte. In einer Codezeile werden die gleichen Informationen wie beim Anhalten an einem Breakpoint (dabei ist es egal, ob Sie die Informationen zuvor erweitert hatten). Die Ausdrucksauswertung wird auch beim Anzeigen einer Momentaufnahme unterstützt.  

#### <a name="what-is-the-performance-impact-of-this-feature"></a>Wie wirkt sich dieses Feature auf die Leistung aus? 

Die Auswirkung auf die gesamte Steppingleistung hängt von Ihrer Anwendung ab. Der Mehraufwand, der für das Erstellen einer Momentaufnahme aufgewendet werden muss, beträgt etwa 30 ms. Wenn eine Momentaufnahme erstellt wird, wird der App-Prozess aufgespalten, und die verzweigte Kopie wird angehalten. Wenn Sie eine Momentaufnahme anzeigen, fügt Visual Studio diese zur verzweigten Kopie des Prozesses hinzu. Visual Studio kopiert für jede Momentaufnahme nur die Seitentabelle und legt Copy-on-Write für Seiten fest (beim Schreibvorgang kopieren). Wenn sich Objekte auf dem Heap zwischen den Debuggerschritten mit zugeordneten Momentaufnahmen ändern, wird die jeweilige Seitentabelle daraufhin kopiert, wodurch nur minimale Arbeitsspeicherkosten entstehen. Sollte Visual Studio erkennen, dass nicht genügend Arbeitsspeicher zum Erstellen einer Momentaufnahme verfügbar ist, wird keine erstellt.

## <a name="known-issues"></a>Bekannte Probleme
* Wenn Sie den IntelliTrace-Ereignis- und Momentaufnahmemodus auf Windows-Versionen verwenden, die älter sind als Windows 10 Fall Creators Update (RS3) und wenn das Debugplattformziel der Anwendung auf x86 festgelegt ist, erstellt IntelliTrace keine Momentaufnahme.

    Problemumgehungen:
  * Wenn Sie die Windows 10 Anniversary Update-Version (RS1) oder die niedrigere Version 10.0.14393.2273 nutzen, [installieren Sie KB4103720](https://support.microsoft.com/help/4103720/windows-10-update-kb4103720).
  * Wenn Sie die Windows 10 Creators Update-Version (RS2) oder die niedrigere Version 10.0.15063.1112 nutzen, [installieren Sie KB4103722](https://support.microsoft.com/help/4103722/windows-10-update-4103722).
  * Installieren Sie Windows 10 Fall Creators Update (RS3), oder führen Sie ein Upgrade darauf aus.
  * Alternative Vorgehensweise:
    1. Installieren Sie das Toolset VC++ 2015.3 v140 für Desktop (x86, x64) aus dem Visual Studio-Installer.
    2. Erstellen Sie die Zielanwendung.
    3. Verwenden Sie das EDITBIN-Tool aus der Befehlszeile, um das Tag `Largeaddressaware` für das Ziel als ausführbar festzulegen. Sie können beispielsweise den folgenden Befehl (nach dem Update des Pfads) verwenden: "C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise\VC\Tools\MSVC\14.12.25718\bin\Hostx86\x86\editbin.exe" /Largeaddressaware "C:\Path\To\Application\app.exe".
    4. Drücken Sie **F5**, um mit dem Debuggen zu beginnen. Jetzt werden Momentaufnahmen von Einzelschritten des Debuggers und Breakpoints gemacht.

       > [!Note]
       > Das Flag `Largeaddressaware` muss jedes Mal festgelegt werden, wenn die ausführbare Datei mit Änderungen erneut erstellt wird.

* Wenn eine Momentaufnahme des Anwendungsprozesses für eine Anwendung erstellt wird, die eine permanente im Speicher abgebildete Datei verwendet, hält der Prozess mit der Momentaufnahme eine exklusive Sperre auf diese Datei aufrecht. Andere Prozess können die im Speicher abgebildete Datei noch immer lesen, jedoch keine Schreibvorgänge darin ausführen.

  Problemumgehung:
  * Löschen Sie alle Momentaufnahmen, indem Sie die Debugsitzung beenden.

* Die Steppingleistung mit aktivierten Momentaufnahmen kann beim Debuggen einer Anwendung betroffen sein, deren Prozess über eine hohe Anzahl von eindeutigen Arbeitsspeicherregionen verfügt, in etwa eine Anwendung, die eine hohe Anzahl von DLLs lädt. Dieses Problem wird in einer zukünftigen Version von Windows behoben. Wenn dieser Fehler bei Ihnen auftritt, wenden Sie sich an uns: stepback@microsoft.com

* Wenn Sie eine Datei im Ereignis- und Momentaufnahmemodus speichern (über **Debuggen > IntelliTrace > IntelliTrace-Sitzung speichern**), sind die zusätzlichen aus Momentaufnahmen erfassten Daten nicht in der ITRACE-Datei verfügbar. Bei Breakpoint- und Schrittereignissen werden die gleichen Informationen angezeigt wie die, die Sie in der Datei im ausschließlichen IntelliTrace-Ereignismodus gespeichert hatten.

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie gelernt, wie das Feature „Schritt zurück“ von IntelliTrace verwendet wird. Wenn Sie noch mehr zu IntelliTrace-Features erfahren möchten, besuchen Sie folgende Seite:

> [!div class="nextstepaction"]
> [IntelliTrace-Funktionen](../debugger/intellitrace-features.md)
