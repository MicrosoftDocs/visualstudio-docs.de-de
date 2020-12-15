---
title: Verbessern der Leistung eines VSTO-Add-ins
description: Erfahren Sie, wie Sie VSTO-Add-ins optimieren, die Sie für Office-Anwendungen erstellen, sodass diese schnell gestartet und heruntergefahren, Elemente geöffnet und andere Aufgaben ausgeführt werden können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 83ba2e9cc2cd55b3e3f6362250ffc1e9489b1626
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524435"
---
# <a name="improve-the-performance-of-a-vsto-add-in"></a>Verbessern der Leistung eines VSTO-Add-ins
  Sie können die Benutzererfahrung verbessern, indem Sie VSTO-Add-Ins optimieren, die Sie für Office-Anwendungen erstellen, sodass diese schnell gestartet und heruntergefahren, Elemente schnell geöffnet und andere Aufgaben rasch ausgeführt werden können. Wenn das VSTO-Add-In für Outlook bestimmt ist, können Sie das Risiko senken, dass das VSTO-Add-In aufgrund schwacher Leistung deaktiviert wird. Sie können die Leistung des VSTO-Add-Ins mithilfe der folgenden Strategien steigern:

- [Bedarfsgesteuertes Laden von VSTO-Add-Ins](#Load).

- [Office-Projektmappen mit Windows Installer veröffentlichen](#Publish).

- Menü [Band Reflektion umgehen](#Bypass).

- [Kostenintensive Vorgänge in einem separaten Ausführungsthread ausführen](#Perform).

  Weitere Informationen zur Optimierung eines Outlook-VSTO-Add-Ins finden Sie unter [Leistungskriterien, um VSTO-Add-Ins zu aktivieren](/previous-versions/office/jj228679(v=office.15)#performance-criteria-for-keeping-add-ins-enabled).

## <a name="load-vsto-add-ins-on-demand"></a><a name="Load"></a> Bedarfs gesteuertes Laden von VSTO-Add-ins
 Sie können ein VSTO-Add-In so konfigurieren, dass es nur unter folgenden Umständen geladen wird:

- Beim ersten Start der Anwendung nach Installation des VSTO-Add-Ins.

- Bei der ersten Interaktion des Benutzers mit dem VSTO-Add-In nach weiteren Starts der Anwendung.

  Beispielsweise füllt das VSTO-Add-in möglicherweise ein Arbeitsblatt mit Daten auf, wenn der Benutzer eine benutzerdefinierte Schaltfläche mit der Bezeichnung **meine Daten erhalten** auswählt. Die Anwendung muss das VSTO-Add-in mindestens einmal laden, damit die Schaltfläche " **meine Daten** " im Menüband angezeigt werden kann. Das VSTO-Add-in wird jedoch nicht erneut geladen, wenn der Benutzer die Anwendung das nächste Mal startet. Das VSTO-Add-In wird nur geladen, wenn der Benutzer die Schaltfläche **Meine Daten abrufen** auswählt.

### <a name="to-configure-a-clickonce-solution-to-load-vsto-add-ins-on-demand"></a>So konfigurieren Sie eine ClickOnce-Projektmappe, um VSTO-Add-Ins bedarfsgesteuert zu laden

1. Wählen Sie im **Projektmappen-Explorer** den Projektknoten aus.

2. Wählen Sie in der Menüleiste **Ansicht** >  **Eigenschaftenseiten** aus.

3. Wählen Sie auf der Registerkarte **Veröffentlichen** die Schaltfläche **Optionen** aus.

4. Wählen Sie im Dialogfeld **Veröffentlichungsoptionen** das Listenelement **Office-Einstellungen** . Wählen Sie die Option **Bedarfsgesteuert laden** und anschließend die Schaltfläche **OK** aus.

### <a name="to-configure-a-windows-installer-solution-to-load-vsto-add-ins-on-demand"></a>So konfigurieren Sie eine Windows Installer-Projektmappe, um VSTO-Add-Ins bedarfsgesteuert zu laden

1. Legen Sie in der Registrierung den `LoadBehavior` Eintrag für den Schlüssel " **_root_\software\microsoft\office \\ _ApplicationName_\Addins \\ _Add-in ID_** " auf " **0x10**" fest.

     Weitere Informationen finden Sie unter [Registrierungseinträge für VSTO-Add-ins](../vsto/registry-entries-for-vsto-add-ins.md).

### <a name="to-configure-a-solution-to-load-vsto-add-ins-on-demand-while-you-debug-the-solution"></a>So konfigurieren Sie eine Projektmappe so, dass VSTO-Add-Ins beim Debuggen der Projektmappe bedarfsgesteuert geladen werden

1. Erstellen Sie ein Skript, mit dem der `LoadBehavior` Eintrag für den Stamm Ordner **\software\microsoft\office \\ _ApplicationName_\Addins \\ _Add-in ID_** auf **0x10** festgelegt wird.

     Der folgende Code ist ein Beispiel für ein solches Skript.

    ```cmd/sh
    [HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\MyAddIn]
    "Description"="MyAddIn"
    "FriendlyName"="MyAddIn"
    "LoadBehavior"=dword:00000010
    "Manifest"="c:\\Temp\\MyAddIn\\bin\\Debug\\MyAddIn.vsto|vstolocal"

    ```

2. Erstellen Sie ein Postbuildereignis, das die Registrierung mithilfe des Skripts aktualisiert.

     Der folgende Code veranschaulicht eine Befehlszeichenfolge, die Sie einem Postbuildereignis hinzufügen können.

    ```cmd/sh
    regedit /s "$(SolutionDir)$(SolutionName).reg"

    ```

     Weitere Informationen zum Erstellen eines Postbuildereignisses in einem c#-Projekt finden Sie unter Gewusst [wie: Angeben von Buildereignissen &#40;C&#35;&#41;](../ide/how-to-specify-build-events-csharp.md).

     Weitere Informationen zum Erstellen eines Postbuildereignisses in einem Visual Basic Projekt finden Sie unter Gewusst [wie: Angeben von Buildereignissen &#40;Visual Basic&#41;](../ide/how-to-specify-build-events-visual-basic.md).

## <a name="publish-office-solutions-by-using-windows-installer"></a><a name="Publish"></a> Office-Projektmappen mithilfe von Windows Installer veröffentlichen
 Wenn Sie die Projekt Mappe mithilfe von Windows Installer veröffentlichen, umgeht Visual Studio 2010 Tools for Office Runtime die folgenden Schritte, wenn das VSTO-Add-in geladen wird.

- Überprüfen des Manifestschemas.

- Automatische Überprüfung auf Updates.

- Überprüfen der digitalen Signaturen der Bereitstellungsmanifeste.

  > [!NOTE]
  > Diese Vorgehensweise ist nicht erforderlich, wenn Sie Ihr VSTO-Add-in an einem sicheren Ort auf den Computern der Benutzer bereitstellen.

  Weitere Informationen finden Sie unter Bereitstellen [einer Office](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md)-Projekt Mappe mit Windows Installer.

## <a name="bypass-ribbon-reflection"></a><a name="Bypass"></a> Menü Band Reflektion umgehen
 Wenn Sie eine Projekt Mappe mithilfe von erstellen [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] , stellen Sie sicher, dass die Benutzer die neueste Version der Visual Studio 2010-Tools für Office-Laufzeit installiert haben, wenn Sie die Lösung bereitstellen. Ältere Versionen der VSTO-Laufzeit wurden in Projektmappenassemblys reflektiert, um Menü Band Anpassungen zu suchen. Dieser Prozess kann zur Folge haben, dass das VSTO-Add-In langsamer geladen wird.

 Als Alternative können Sie verhindern, dass eine beliebige Version der Visual Studio 2010-Tools für Office-Laufzeit Reflektion zum Identifizieren von Menü Band Anpassungen verwendet. Um dieser Strategie zu folgen, überschreiben Sie die `CreateRibbonExtensibility` -Methode, und geben Sie explizit Ribbon-Objekte zurück. Wenn das VSTO-Add-in keine Menü Band Anpassungen enthält, geben Sie innerhalb der- `null` Methode zurück.

 Im folgenden Beispiel wird ein Menüband-Objekt basierend auf dem Wert eines Felds zurückgegeben.

 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs#1)]

## <a name="perform-expensive-operations-in-a-separate-execution-thread"></a><a name="Perform"></a> Ausführen von teuren Vorgängen in einem separaten Ausführungs Thread
 Erwägen Sie, zeitintensive Aufgaben (z. B. Aufgaben mit langer Ausführungsdauer, Datenbankverbindungen oder andere Arten von Netzwerkaufrufen) in einem separaten Thread auszuführen. Weitere Informationen finden Sie [unter Threading-Unterstützung in Office](../vsto/threading-support-in-office.md).

> [!NOTE]
> Der gesamte Code, der das Office-Objektmodell aufruft, muss im Hauptthread ausgeführt werden.

## <a name="see-also"></a>Weitere Informationen

- [Bedarfs gesteuertes Laden von VSTO-Add-ins](/archive/blogs/andreww/demand-loading-vsto-add-ins)
- [Verzögertes Laden der CLR in Office-Add-Ins](/archive/blogs/andreww/delay-loading-the-clr-in-office-add-ins)
- [Erstellen von VSTO-Add-ins für Office mithilfe von Visual Studio](create-vsto-add-ins-for-office-by-using-visual-studio.md)