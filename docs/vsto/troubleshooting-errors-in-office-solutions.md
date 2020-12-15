---
title: Beheben von Fehlern in Office-Projektmappen
description: Erfahren Sie, wie Sie Fehler beheben können, die auftreten können, während Sie Microsoft Office Lösungen in Visual Studio entwickeln.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: troubleshooting
f1_keywords:
- VST.Project.DesignerDisabled
- VST.Designer.CannotActivate
- VST.Project.ExcelBusy
- VST.SelectDocWizard.AlreadyCustomized
- VST.SelectDocWizard.DocPath
- VST.Project.CannotOpen
- VST.Designer.ErrorsOccurred
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- troubleshooting [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fd12c3dd9cd3c90564351dd1c64cebfe5df6e99d
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97523034"
---
# <a name="troubleshoot-errors-in-office-solutions"></a>Beheben von Fehlern in Office-Projektmappen
  Wenn Sie beim Entwickeln von Office-Projektmappen in Visual Studio die folgenden Aufgaben ausführen, können Probleme auftreten:

- [Erstellen, aktualisieren und Öffnen von Projekten](#creating)

- [Verwenden der Designer](#designers)

- [Schreiben von Code](#code)

- [Erstellen von Projekten](#building)

- [Projekte Debuggen](#debugging)

## <a name="create-upgrade-and-open-projects"></a><a name="creating"></a> Erstellen, aktualisieren und Öffnen von Projekten
 Die folgenden Fehler können auftreten, wenn Sie Office-Projekte erstellen oder öffnen.

### <a name="the-project-cannot-be-created"></a>Das Projekt kann nicht erstellt werden.
 Bei dem Versuch, ein Office-Projekt zu erstellen oder zu öffnen, ist ein Fehler aufgetreten. Visual Studio verfügte jedoch nicht über ausreichende Informationen, um die Ursache zu bestimmen. Versuchen Sie, das Projekt zu schließen, beenden Sie Visual Studio, und führen Sie den Vorgang erneut aus.

 Wenn Sie versuchen, ein Projekt auf Dokumentebene zu erstellen, kann es vorkommen, dass ein anderes Dokument mit demselben Namen wie das Dokument im neuen Projekt bereits in Word oder Excel geöffnet ist. Stellen Sie sicher, dass alle anderen Instanzen von Excel oder Word geschlossen sind.

### <a name="control-properties-are-lost-when-you-create-a-new-project-based-on-a-document-from-an-existing-project"></a>Steuerelement Eigenschaften gehen verloren, wenn Sie ein neues Projekt erstellen, das auf einem Dokument aus einem vorhandenen Projekt basiert.
 Wenn Sie ein neues Office-Projekt anhand eines Dokuments aus einem vorhandenen Projekt erstellen, werden die Eigenschaften für Steuerelemente im Dokument nicht in das neue Projekt kopiert. Sie müssen die Eigenschaften für alle bereits bestehenden Steuerelemente manuell zurücksetzen. Alternativ können Sie die Steuerelementeigenschaften beibehalten, indem Sie statt eines neuen Projekts eine Kopie des vorhandenen Projekts erstellen oder indem Sie das vorhandene Projekt in die neue Projektmappe (im Designer) laden und die Steuerelemente aus dem vorhandenen Dokument kopieren und in das neue Dokument einfügen.

### <a name="errors-when-you-create-an-excel-workbook-project-based-on-an-existing-workbook"></a>Fehler beim Erstellen eines Excel-Arbeitsmappenprojekts basierend auf einer vorhandenen Arbeitsmappe
 Wenn Sie ein neues Excel-Arbeitsmappenprojekt erstellen, das auf einer vorhandenen Arbeitsmappe basiert, wird möglicherweise eine Kombination der folgenden Fehler angezeigt.

 Excel: "Datenschutzwarnung: Dieses Dokument enthält Makros, ActiveX-Steuerelemente, XML-Erweiterungspaketinformationen oder Webkomponenten. Diese enthalten möglicherweise persönliche Informationen, die durch die Dokumentprüfung nicht entfernt werden können."

 Visual Studio: "Der Designer wurde nicht ordnungsgemäß geladen."

 Diese Fehler können auftreten, wenn Sie versuchen, ein Projekt zu erstellen, das auf einer Arbeitsmappe basiert, deren persönliche Informationen mithilfe der Dokumentprüfung entfernt wurden. Führen Sie vor dem Erstellen des Projekts die folgenden Schritte aus, um diesen Fehler zu vermeiden.

1. Öffnen Sie die Arbeitsmappe in Excel.

2. Öffnen Sie in Excel das Trust Center.

3. Deaktivieren Sie auf der Registerkarte **Datenschutzoptionen** das Kontrollkästchen **persönliche Informationen aus Dateieigenschaften beim Speichern entfernen** .

4. Speichern Sie die Arbeitsmappe, und schließen Sie Excel.

### <a name="cannot-open-a-project-after-migration"></a>Ein Projekt kann nach der Migration nicht geöffnet werden.
 Nachdem eine Office-Projektmappe zu Microsoft Office 2010 migriert wurde, kann das Projekt nicht auf einem Entwicklungscomputer geöffnet werden, wenn nur 2007 Microsoft Office System installiert ist. Die folgenden Fehler können angezeigt werden.

 "Ein oder mehrere Projekte in der Projektmappe wurden nicht ordnungsgemäß geladen. Details finden Sie im Ausgabefenster."

 "Das Projekt kann nicht erstellt werden, da die diesem Projekttyp zugeordnete Anwendung nicht auf diesem Computer installiert ist. Sie müssen die diesem Projekttyp zugeordnete Microsoft Office-Anwendung installieren."

 Um dieses Problem zu beheben, bearbeiten Sie die *vbproj* -oder *csproj* -Datei. Ersetzen Sie für ein Word-Projekt HostPackage="{763FDC83-64E5-4651-AC9B-28C4FEB985A1}" durch HostPackage="{6CE98B71-D55A-4305-87A8-0D6E368D9600}". Ersetzen Sie für ein Excel-Projekt HostPackage="{B284B16A-C42C-4438-BDCD-B72F4AC43CFB}" durch HostPackage="{825100CF-0BA7-47EA-A084-DCF3308DAF74}". Ersetzen Sie für ein Outlook-Projekt HostPackage="{D2B20FF5-A6E5-47E1-90E8-463C6860CB05}" durch HostPackage="{20A848B8-E01F-4801-962E-25DB0FF57389}".

 Stellen Sie alternativ sicher, dass migrierte Projekte nur auf Entwicklungscomputern geöffnet werden, auf denen Microsoft Office 2010 bereits installiert ist.

### <a name="errors-in-upgraded-office-2003-document-level-projects-that-contain-windows-forms-controls"></a>Fehler in aktualisierten Office 2003-Projekten auf Dokument Ebene, die Windows Forms Steuerelemente enthalten
 Wenn Sie ein Microsoft Office 2003-Projekt auf Dokument Ebene aktualisieren und das Dokument Windows Forms Steuerelemente enthält, kann das aktualisierte Projekt Kompilierungs-oder Laufzeitfehler aufweisen. Um dieses Problem zu vermeiden, installieren Sie vor dem Aktualisieren des Projekts die Visual Studio 2005-Tools für Office Second Edition-Laufzeit auf dem Entwicklungscomputer. Diese Version der Laufzeit steht im Microsoft Download Center unter [Microsoft Visual Studio 2005-Tools für Office Second Edition-Laufzeit (VSTO 2005 SE) (x86)](https://www.microsoft.com/download/details.aspx?id=2392)als verteilbares Paket zur Verfügung.

 Nachdem Sie das Projekt aktualisiert haben, können Sie die Visual Studio 2005-Tools für Office Second Edition-Laufzeit vom Entwicklungscomputer deinstallieren, wenn sie nicht von anderen Office-Projektmappen verwendet wird.

## <a name="use-the-designers"></a><a name="designers"></a> Verwenden der Designer
 Die folgenden Fehler können auftreten, wenn Sie in Projekten auf Dokumentebene mit dem Dokument-, Arbeitsmappen- oder Arbeitsblatt-Designer arbeiten.

### <a name="designer-failed-to-load-correctly"></a>Der Designer konnte nicht ordnungsgemäß geladen werden
 In den folgenden Fällen kann Visual Studio den Designer nicht öffnen:

- Excel oder Word ist bereits geöffnet und zeigt ein modales Dialogfeld an. Um den Designer zu öffnen, prüfen Sie, ob in Excel oder Word ein modales Dialogfeld geöffnet ist, und schließen Sie alle geöffneten modalen Dialogfelder. Wenn keine modalen Dialogfelder geöffnet sind, sind möglicherweise andere Maßnahmen erforderlich, damit Excel bzw. Word reagiert.

- Das Projekt wird gerade debuggt. Beenden Sie den Debugvorgang, oder schließen Sie ihn ab, um den Designer zu öffnen.

- Ein auf dem Entwicklungscomputer installiertes Excel-VSTO-Add-In zeigt ein Dialogfeld an, wenn Excel gestartet wird. Um ein Excel-Projekt auf Dokumentebene zu erstellen, müssen Sie zuerst das VSTO-Add-In deaktivieren.

### <a name="controls-appear-as-black-rectangles-on-the-document-or-worksheet"></a>Steuerelemente werden im Dokument oder Arbeitsblatt als schwarze Rechtecke angezeigt.
 Wenn Sie Steuerelemente in einem Dokument oder Arbeitsblatt gruppieren, erkennt Visual Studio die Steuerelemente nicht mehr. Auf gruppierte Steuerelemente kann im **Eigenschaften** Fenster nicht zugegriffen werden, und Sie werden im Dokument oder Arbeitsblatt als schwarze Rechtecke angezeigt. Sie müssen die Gruppierung der Steuerelemente aufheben, um ihre Funktionalität wiederherzustellen.

### <a name="controls-on-a-word-template-are-not-visible-in-visual-studio"></a>Steuerelemente in einer Word-Vorlage sind in Visual Studio nicht sichtbar.
 Wenn Sie eine Word-Vorlage im Visual Studio-Designer öffnen, sind Steuerelemente in der Vorlage, die nicht in den Textfluss eingefügt wurden, eventuell nicht sichtbar. Dies liegt daran, dass Visual Studio Word-Vorlagen in **normaler** Ansicht öffnet. Um die Steuerelemente anzuzeigen, klicken Sie auf das Menü **Ansicht** , zeigen Sie auf **Microsoft Office Word-Ansicht** , und klicken Sie dann auf **Layout drucken**.

### <a name="insert-clip-art-command-does-nothing-in-the-visual-studio-designer"></a>Befehl "Clip-Art einfügen" führt keine Aktion im Visual Studio-Designer aus
 Wenn Excel oder Word im Visual Studio-Designer geöffnet ist, wird durch Klicken auf die Schaltfläche **Clip-Art** auf der Registerkarte **Abbildungen** im Menüband nicht der Aufgabenbereich **Clip-Art** geöffnet. Um Clip Art hinzuzufügen, müssen Sie die Kopie der Arbeitsmappe oder des Dokuments, das sich im Hauptprojekt Ordner befindet (nicht die Kopie im Ordner " *\bin* ") außerhalb von Visual Studio öffnen, das ClipArt hinzufügen und dann die Arbeitsmappe oder das Dokument speichern.

## <a name="write-code"></a><a name="code"></a> Schreiben von Code
 Die folgenden Fehler können auftreten, wenn Sie Code in Office-Projekten schreiben.

### <a name="some-events-of-office-objects-are-not-accessible-when-using-c"></a>Einige Ereignisse von Office-Objekten sind bei Verwendung von C nicht verfügbar.\#
 In einigen Fällen kann ein Compilerfehler wie der folgende angezeigt werden, wenn Sie versuchen, auf ein bestimmtes Ereignis einer Instanz eines primären Interopassemblytyps (PIA) für Office in einem Visual C#-Projekt zuzugreifen.

 "Mehrdeutigkeit zwischen 'Microsoft.Office.Interop.Excel._Application.NewWorkbook' und 'Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook'"

 Dieser Fehler bedeutet, dass Sie auf ein Ereignis zuzugreifen versuchen, das den gleichen Namen wie eine andere Eigenschaft oder Methode des Objekts besitzt. Um auf das-Ereignis zuzugreifen, müssen Sie das-Objekt in seine *Ereignis Schnittstelle* umwandeln.

 Office-PIA-Typen mit Ereignissen implementieren zwei Schnittstellen: eine Kernschnittstelle mit allen Eigenschaften und Methoden und eine Ereignisschnittstelle, die die vom Objekt verfügbar gemachten Ereignisse enthält. Diese Ereignis Schnittstellen verwenden die Benennungs Konvention *objectName* Events *n* _Event, z <xref:Microsoft.Office.Interop.Excel.AppEvents_Event> <xref:Microsoft.Office.Interop.Word.ApplicationEvents2_Event> . b. und. Wenn Sie nicht auf ein Ereignis zugreifen können, das in einem Objekt vorhanden sein sollte, wandeln Sie das Objekt in die zugehörige Ereignisschnittstelle um.

 <xref:Microsoft.Office.Interop.Excel.Application>-Objekte verfügen beispielsweise über ein <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook>-Ereignis und eine <xref:Microsoft.Office.Interop.Excel._Application.NewWorkbook%2A>-Eigenschaft. Um das <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook>-Ereignis zu behandeln, wandeln Sie <xref:Microsoft.Office.Interop.Excel.Application> in die <xref:Microsoft.Office.Interop.Excel.AppEvents_Event>-Schnittstelle um. Im folgenden Codebeispiel wird dies für ein Projekt auf Dokumentebene für Excel veranschaulicht.

 [!code-csharp[Trin_VstcoreTroubleshootingExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingExcelCS/ThisWorkbook.cs#1)]

 Weitere Informationen zu Ereignis Schnittstellen in den Office-PIAs finden Sie unter [Übersicht über Klassen und Schnittstellen in den primären Interop-](/previous-versions/office/office-12//ms247299(v=office.12))Assemblys von Office.

### <a name="cannot-reference-office-pia-classes-in-projects-that-target-the-net_v40_short-or-the-net_v45"></a>Auf Office Pia-Klassen in Projekten, die auf oder abzielen, kann nicht verwiesen werden. [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)][!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]
 In Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] ausgerichtet sind, wird Code, der auf eine in einer Office-PIA definierte Klasse verweist, standardmäßig nicht kompiliert. Klassen in den PIAs verwenden die *objectName*-Klasse der Benennungs Konvention, z <xref:Microsoft.Office.Interop.Word.DocumentClass> <xref:Microsoft.Office.Interop.Excel.WorkbookClass> . b. und. Der folgende Code aus einem Word-VSTO-Add-In-Projekt wird z. B. nicht kompiliert.

```vb
Dim document As Word.DocumentClass = Globals.ThisAddIn.Application.ActiveDocument
```

```csharp
Word.DocumentClass document = (Word.DocumentClass) Globals.ThisAddIn.Application.ActiveDocument;
```

 Dieser Code führt zu folgenden Kompilierungsfehlern:

- Visual Basic: "der Verweis auf die Klasse ' DocumentClass ' ist nicht zulässig, wenn die zugehörige Assembly im No-PIA-Modus verknüpft ist."

- Visual c#: der Interoptyp "Microsoft.Office.Interop.Word.Docenumerclass" kann nicht eingebettet werden. Verwenden Sie stattdessen die entsprechende Schnittstelle."

  Um diesen Fehler zu beheben, ändern Sie den Code, sodass er stattdessen auf die entsprechende Schnittstelle verweist. Verwenden Sie z. B. anstelle eines Verweises auf ein <xref:Microsoft.Office.Interop.Word.DocumentClass>-Objekt einen Verweis auf eine Instanz der <xref:Microsoft.Office.Interop.Word.Document>-Schnittstelle.

```vb
Dim document As Word.Document = Globals.ThisAddIn.Application.ActiveDocument
```

```csharp
Word.Document document = Globals.ThisAddIn.Application.ActiveDocument;
```

 Projekte, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] ausgerichtet sind, betten alle Interop-Typen aus Office-PIAs standardmäßig automatisch ein. Dieser Kompilierungsfehler tritt auf, weil das Feature für eingebettete Interoptypen nur für Schnittstellen funktioniert, aber nicht für Klassen. Weitere Informationen zu Schnittstellen und Klassen in den Office-PIAs finden Sie unter [Übersicht über Klassen und Schnittstellen in den primären Interop](/previous-versions/office/office-12/ms247299(v=office.12))-Assemblys von Office. Weitere Informationen zur Funktion für eingebettete Interoptypen in Office-Projekten finden Sie unter [Entwerfen und Erstellen von Office-](../vsto/designing-and-creating-office-solutions.md)Projektmappen.

### <a name="references-to-office-classes-are-not-recognized"></a>Verweise auf Office-Klassen werden nicht erkannt.
 Einige Klassennamen, z. b. eine Anwendung, befinden sich in mehreren Namespaces, z <xref:Microsoft.Office.Interop.Word> <xref:System.Windows.Forms> . b. und. Aus diesem Grund enthält die **Imports** / **using** -Anweisung am Anfang der Projektvorlagen eine kurzanqualifizier Ende Konstante, z. b.:

 [!code-csharp[Trin_VstcoreTroubleshootingWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs#2)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb#2)]

 Diese Verwendung der **Imports** / **using** -Anweisung erfordert, dass Sie Verweise auf Office-Klassen mit dem Word-oder Excel-Qualifizierer unterscheiden, z. b.:

 [!code-csharp[Trin_VstcoreTroubleshootingWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs#3)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb#3)]

 Bei Verwendung einer Deklaration ohne Qualifizierer werden Fehlermeldungen ausgegeben, z. B.:

 [!code-csharp[Trin_VstcoreTroubleshootingWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs#4)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb#4)]

 Obwohl Sie den Word-oder Excel-Namespace importiert haben und Zugriff auf alle darin enthaltenen Klassen haben, müssen Sie alle Typen mit Word oder Excel vollständig qualifizieren, um die Mehrdeutigkeit von Namespaces zu entfernen.

## <a name="build-projects"></a><a name="building"></a> Erstellen von Projekten
 Beim Erstellen von Office-Projekten können die folgenden Fehler auftreten.

### <a name="cannot-build-a-document-level-project-that-is-based-on-a-document-with-restricted-permissions"></a>Ein Projekt auf Dokument Ebene kann nicht erstellt werden, das auf einem Dokument mit eingeschränkten Berechtigungen basiert.
 Visual Studio kann keine Projekte auf Dokumentebene erstellen, wenn das Dokument eingeschränkte Berechtigungen aufweist. Wenn das Projekt ein Dokument mit eingeschränkten Berechtigungen enthält, wird das Projekt nicht kompiliert, und im **Fehlerliste** Fenster wird die folgende Meldung angezeigt.

 "Fehler beim Hinzufügen der Anpassung."

 Wenn Sie ein Dokument mit eingeschränkten Berechtigungen einschließen möchten, müssen Sie beim Entwickeln und Erstellen der Projektmappe ein nicht eingeschränktes Dokument verwenden. Wenden Sie dann die eingeschränkten Berechtigungen auf das Dokument am Veröffentlichungsort an, nachdem Sie die Projektmappe veröffentlicht haben.

### <a name="compiler-errors-occur-after-a-namedrange-control-is-deleted"></a>Compilerfehler treten auf, nachdem ein Name Drange-Steuerelement gelöscht wurde.
 Wenn Sie ein <xref:Microsoft.Office.Tools.Excel.NamedRange>-Steuerelement aus einem Arbeitsblatt löschen, das nicht das aktive Arbeitsblatt im Designer ist, wird der automatisch generierte Code möglicherweise nicht aus dem Projekt entfernt, und es können Compilerfehler auftreten. Um sicherzustellen, dass der Code entfernt wird, müssen Sie vor dem Löschen des Steuerelements immer das Arbeitsblatt auswählen, das das <xref:Microsoft.Office.Tools.Excel.NamedRange>-Steuerelement enthält, um dieses als aktives Arbeitsblatt festzulegen. Wenn automatisch generierter Code beim Löschen des Steuerelements nicht gelöscht wird, können Sie den Designer anweisen, den Code zu löschen. Aktivieren Sie dazu das Arbeitsblatt, und nehmen Sie eine Änderung vor, sodass das Arbeitsblatt als geändert markiert wird. Beim Neuerstellen des Projekts wird der Code entfernt.

## <a name="debug-projects"></a><a name="debugging"></a> Projekte Debuggen
 Beim Debuggen von Office-Projekten können die folgenden Fehler auftreten.

### <a name="prompt-to-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>Die Aufforderung zur Deinstallation wird angezeigt, wenn Sie eine Lösung auf dem Entwicklungs Computer veröffentlichen und installieren.
 Wenn Sie eine Office-Projektmappe debuggen, kann der folgende Fehler angezeigt werden.

 "Die Anpassung kann nicht installiert werden, weil derzeit eine andere Version installiert ist und von diesem Speicherort nicht aktualisiert werden kann."

 Dieser Fehler weist darauf hin, dass Sie die Office-Projektmappe zuvor auf dem Entwicklungscomputer veröffentlicht und installiert haben. Um zu verhindern, dass die Meldung angezeigt wird, deinstallieren Sie die Projektmappe über die Liste der auf dem Computer installierten Programme, bevor Sie die Projektmappe debuggen. Alternativ können Sie ein anderes Benutzerkonto auf dem Entwicklungscomputer erstellen, um die Installation der veröffentlichten Projektmappe zu testen.

### <a name="document-level-projects-created-at-unc-network-locations-do-not-run-from-visual-studio"></a>Projekte auf Dokument Ebene, die an UNC-Netzwerk Standorten erstellt wurden, können nicht in Visual Studio ausgeführt werden.
 Wenn Sie ein Projekt auf Dokumentebene für Excel oder Word an einem UNC-Netzwerkspeicherort erstellen, müssen Sie den Speicherort des Dokuments der Liste vertrauenswürdiger Speicherorte in Word oder Excel hinzufügen. Andernfalls wird die Anpassung nicht geladen, wenn Sie versuchen, das Projekt in Visual Studio auszuführen oder zu debuggen. Weitere Informationen zu vertrauenswürdigen Speicherorten finden [Sie unter Gewähren von Vertrauenswürdigkeit für Dokumente](../vsto/granting-trust-to-documents.md).

### <a name="threads-are-not-stopped-correctly-after-debugging"></a>Threads werden nach dem Debuggen nicht ordnungsgemäß beendet.
 Office-Projekte in Visual Studio folgen einer Threadnamenskonvention, die den Debugger in die Lage versetzt, das Programm ordnungsgemäß zu schließen. Wenn Sie in der Projektmappe Threads erstellen, versehen Sie den Namen jedes einzelnen Threads mit dem Präfix "VSTA_", um sicherzustellen, dass diese Threads ordnungsgemäß behandelt werden, wenn Sie das Debuggen beenden. Beispielsweise können Sie die-Eigenschaft eines Threads festlegen, der auf das `Name` **VSTA_NetworkListener** eines Netzwerk Ereignisses wartet.

### <a name="cannot-run-or-debug-any-office-solution-on-the-development-computer"></a>Kann keine Office-Projekt Mappe auf dem Entwicklungs Computer ausführen oder Debuggen
 Wenn Sie ein Office-Projekt auf dem Entwicklungscomputer nicht ausführen oder entwickeln können, wird möglicherweise die folgende Fehlermeldung angezeigt.

 "Die Anpassung konnte nicht geladen werden, weil die Anwendungsdomäne nicht erstellt werden konnte."

 Visual Studio speichert die Assemblys vor dem Laden von Office-Projektmappen mithilfe von Fusion, dem Assemblyladeprogramm von .NET Framework, zwischen. Stellen Sie sicher, dass Visual Studio in den Fusion-Cache schreiben kann, und versuchen Sie es erneut. Weitere Informationen finden Sie unter [schattenkopienassemblys](/dotnet/framework/app-domains/shadow-copy-assemblies).

### <a name="error-when-stopping-the-debugger-in-a-document-level-project-after-using-edit-and-continue"></a>Fehler beim Beenden des Debuggers in einem Projekt auf Dokument Ebene nach der Verwendung von "Bearbeiten und Fortfahren".
 Wenn Sie " **Bearbeiten** und **fortfahren** " verwenden, um Änderungen am Code in einem Projekt auf Dokument Ebene für Excel oder Word vorzunehmen, während sich das Projekt im unterbrechen Modus befindet, wird möglicherweise ein Dialogfeld mit der folgenden Fehlermeldung angezeigt, wenn Sie den Debugger anschließend anhalten.

 "Das Beenden des Prozesses im aktuellen Zustand kann unerwünschte Ergebnisse wie Datenverlust oder Systeminstabilität zur Folge haben."

 Unabhängig davon, ob Sie im Dialogfeld auf " **Ja** " oder " **Nein** " klicken, beendet Visual Studio den Excel-oder Word-Prozess und beendet den Debugger. Um das Debuggen des Projekts ohne Anzeige dieses Dialogfelds zu beenden, beenden Sie Excel oder Word direkt, anstatt den Debugger in Visual Studio zu beenden.

## <a name="see-also"></a>Weitere Informationen
- [Problembehandlung für Office-Lösungen](../vsto/troubleshooting-office-solutions.md)
- [Behandeln von Problemen mit der Sicherheit von Office](../vsto/troubleshooting-office-solution-security.md)
- [Problembehandlung bei der Bereitstellung von Office](../vsto/troubleshooting-office-solution-deployment.md)
- [Problembehandlung für Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)
