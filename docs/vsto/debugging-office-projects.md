---
title: Debugging von Office-Projekten
description: Erfahren Sie, wie Sie Office-Projekte mit den gleichen Microsoft Visual Studio Tools debuggen können, die Sie auch für andere Visual Studio-Projekte verwenden.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel projects [Office development in Visual Studio], debugging
- Word projects [Office development in Visual Studio], debugging
- Outlook [Office development in Visual Studio], debugging
- debugging [Office development in Visual Studio], Outlook projects
- Office projects [Office development in Visual Studio], debugging
- Outlook [Office development in Visual Studio], projects
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ea4874effcba4ee948f921ae9bf91f145b661f4f
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845634"
---
# <a name="debug-office-projects"></a>Debugging von Office-Projekten
  Sie können Office-Projekte mit den gleichen Microsoft [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Tools debuggen, die Sie auch für andere [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Projekte verwenden. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Debuggerfunktionen, beispielsweise die Fähigkeit, Haltepunkte einzufügen und Variablen im Fenster **Lokal** anzuzeigen, stehen auch zur Verfügung, wenn Sie Office-Projekte debuggen. Weitere Informationen zu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Debuggingtools finden Sie unter [Debuggen in Visual Studio](../debugger/debugger-feature-tour.md).

> [!TIP]
> Um das Debuggen zu vereinfachen, schließen Sie alle geöffneten Instanzen der Office-Anwendung, bevor Sie sie erstellen und debuggen.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="start-and-stop-the-debugger"></a>Starten und Abbrechen des Debuggers
 Sie können mit dem Debuggen eines Office-Projekts beginnen, ebenso wie beim Debuggen anderer [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Projekte. Sie können z. b. die Taste **F5** drücken. Wenn Sie mit dem Debuggen eines VSTO-Add-in-Projekts beginnen, wird ein neuer Prozess für die entsprechende Office-Anwendung gestartet, und das VSTO-Add-in wird geladen.

 Wenn Sie mit dem Debuggen eines Projekts auf Dokumentebene beginnen, wird das Dokument oder die Arbeitsmappe in einem neuen Word- oder Excel-Prozess geöffnet.

 Wenn Sie den Debugger beenden, bricht der Debugger den Anwendungsprozess abrupt ab oder trennt sich vom Prozess, sofern Sie dies festgelegt haben. Alle anderen Dokumente, die in einem beendeten Office-Anwendungsprozess geöffnet sind, werden ohne Warnung ebenfalls geschlossen, wobei alle nicht gespeicherten Änderungen verloren gehen. Dazu können alle Dokumente oder Arbeitsmappen gehören, die geöffnet werden, während der Debugger ausgeführt wird.

 Normalerweise empfiehlt es sich, den Prozess vor dem Beenden des Debuggers zu trennen. So können Sie die Office-Anwendung normal beenden. Wenn Sie nach dem Beenden des Debuggers weiter in einem geöffneten Dokument oder Arbeitsblatt arbeiten möchten, können Sie den Prozess auch zuerst trennen.

 Wenn Sie eine Anpassung auf Dokumentebene für Word debuggen, kann das wiederholte Beenden des Debuggers ein abruptes Schließen von Word zur Folge haben, wodurch die Normal-Vorlage beschädigt werden kann. In diesem Fall können Sie die beschädigte Normal-Vorlage löschen. Sie wird beim nächsten Öffnen von Word automatisch neu erstellt. In der Normal-Vorlage gespeicherte Makros werden allerdings nicht neu erstellt.

### <a name="debug-office-2013-vsto-add-ins-by-using-either-office-2013-or-office-2016"></a>Debuggen von Office 2013-VSTO-Add-Ins mithilfe von Office 2013 oder Office 2016
 Wenn Sie Visual Studio 2015 verwenden und beide Versionen von Office nebeneinander installiert sind, startet Visual Studio Office 2016. Wenn Sie Visual Studio 2013 verwenden, startet Visual Studio Office 2013.

 Wenn Sie Ihr VSTO-Add-In mithilfe einer anderen Office-Version (2013 oder 2016) debuggen möchten, öffnen Sie den **Projekt-Designer** und wählen auf der Registerkarte **Debuggen** die Optionsschaltfläche **Externes Programm starten** aus. Navigieren Sie dann zum Speicherort der ausführbaren Datei der entsprechenden Office-Anwendung.

## <a name="f10-and-f11-behavior"></a>F10-und F11-Verhalten
 Wenn Sie mit dem Debuggen eines Office-Projekts beginnen, haben **F10** und **F11** nicht das gleiche Verhalten wie beim Starten des Debuggens anderer Visual Basic-oder c#-Projekte. In Visual Basic- oder C#-Projekten wird der Debugger bei der main-Funktion angehalten. In Office-Projekten besitzt Visual Studio dagegen keine Kontrolle über die main-Funktion der Office-Anwendung. Während des Debuggens verfügen **F10** und **F11** jedoch über dieselben Funktionen wie in Visual Basic-und c#-Projekten.

## <a name="display-exceptions"></a>Ausnahmen anzeigen
 Durch die Art und Weise der Interaktion zwischen verwaltetem und nicht verwaltetem Code werden in Visual Studio keine Fehler angezeigt, die von Microsoft Office-Anwendungen ausgelöst werden. Wenn beispielsweise ein VSTO-Add-in, das mithilfe von Office-Entwicklungs Tools in Visual Studio erstellt wurde, eine Ausnahme auslöst, wird die Microsoft Office-Anwendung fortgesetzt, ohne dass ein Fehler angezeigt wird. Um diese Fehler anzuzeigen, konfigurieren Sie den Debugger so, dass er bei Ausnahmen der Common Language Runtime anhält. Weitere Informationen finden Sie unter [Verwalten von Ausnahmen mit dem Debugger](../debugger/managing-exceptions-with-the-debugger.md).

 Wenn Sie den Debugger so konfigurieren, dass er bei Ausnahmen der Common Language Runtime anhält, wird der Debugger bei jeder Ausnahme aufgerufen. Dazu gehören auch Ausnahmen, die Sie behandelt haben, sowie Ausnahmen (erste Chance), die von der Common Language Runtime selbst ausgelöst werden und für das Projekt nicht relevant sind. Fehler, in denen darauf Bezug genommen wird, dass msosec nicht gefunden werden kann, treten in jedem Projekt auf, können aber ignoriert werden. Diese msoec-Ausnahmen haben keine Auswirkungen auf die Projektmappe.

 Sie können für Methoden auch **Try...Catch** -Anweisungen verwenden, um Ausnahmen abzufangen.

 In der Standardeinstellung zeigt Visual Studio auch keine Just-In-Time-Debugfehler für Office-Projekte an. Sie können dieses Feature jedoch aktivieren, um die ausgelösten Fehler anzuzeigen. Weitere Informationen finden Sie unter [Just-in-Time-Debuggen in Visual Studio](../debugger/just-in-time-debugging-in-visual-studio.md).

## <a name="command-line-arguments"></a>Befehlszeilenargumente
 Wenn auf der Debugeigenschaftenseite die **Start Aktion** auf **Projekt starten** festgelegt ist, werden beim **Debuggen** des Projekts von Visual Studio keine Befehlszeilenargumente verwendet. Dies gilt auch, wenn Sie Befehlszeilenargumente als Start Optionen angegeben haben. Wenn Sie beim Starten des Debuggens Befehlszeilenargumente verwenden möchten, müssen Sie eine andere **Start Aktion** als **Projekt starten** auswählen.

## <a name="source-control"></a>Quellcodeverwaltung
 In der Quellcodeverwaltung werden Debugeigenschaften nicht für mehrere Benutzer gemeinsam verwendet. In Visual Basic- und C#-Projekten werden die Debugeigenschaften in einer benutzerspezifischen Datei („*ProjectName*.vbproj.user“ oder „ *ProjectName*.csproj.user“) gespeichert, und diese Datei wird nicht in die Quellcodeverwaltung einbezogen. Wenn mehrere Personen debuggen, muss jede Person die Debugeigenschaften manuell eingeben.

## <a name="debug-cached-datasets-in-a-document-level-project"></a>Debuggen zwischen gespeicherter Datasets in einem Projekt auf Dokument Ebene
 Bei jeder Erstellung eines Projekts wird das Dataset geleert und neu erstellt. Wenn Sie ein zwischengespeichertes Dataset debuggen möchten, müssen Sie das Dokument außerhalb von Visual Studio öffnen und dann den Debugger anfügen.

## <a name="debug-word-document-projects-based-on-the-word-97-2003-document-doc-format"></a>Debuggen von Word-Dokument Projekten auf Grundlage des Word 97-2003-Dokument Formats (*. doc)
 Zum Debuggen eines Word-Dokument Projekts basierend auf dem Word 97-2003-Dokument */* Format (doc *) müssen Sie den Projektordner der Liste vertrauenswürdiger Ordner hinzufügen. Weitere Informationen hierzu finden Sie unter Gewähren von Vertrauenswürdigkeit [für Dokumente](../vsto/granting-trust-to-documents.md).

## <a name="debug-disabled-add-ins"></a>Debugdeaktivierte Add-ins
 VSTO-Add-Ins, die ein unerwartetes Verhalten aufweisen, können von Microsoft Office-Anwendungen deaktiviert werden. Solche VSTO-Add-Ins werden von der Microsoft Office-Anwendung deaktiviert, um zu verhindern, dass bei jedem Start der Anwendung problematischer Code geladen wird. Aber auch beim typischen Debuggen kann es zu unerwartetem Verhalten kommen. Weitere Informationen zum erneuten Aktivieren von VSTO-Add-Ins finden Sie unter Gewusst [wie: Erneutes Aktivieren eines VSTO-Add-Ins, das deaktiviert](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)wurde.

 Es gibt zwei Arten der Deaktivierung von VSTO-Add-Ins in Microsoft Office-Anwendungen: harte Deaktivierung und weiche Deaktivierung.

### <a name="hard-disabling"></a>Harte Deaktivierung
 Die harte Deaktivierung kann auftreten, wenn ein VSTO-Add-in bewirkt, dass die Anwendung unerwartet geschlossen wird. Sie kann auch auf dem Entwicklungscomputer auftreten, wenn Sie den Debugger beenden, während der <xref:Microsoft.Office.Tools.AddIn.Startup> -Ereignishandler im VSTO-Add-In ausgeführt wird. Wenn ein VSTO-Add-in hart deaktiviert ist, wird es in der Liste **Deaktivierte Elemente** in der Anwendung angezeigt.

 Wenn eine Office-Anwendung ein VSTO-Add-in hart deaktiviert, das mithilfe von Office-Entwicklungs Tools in Visual Studio erstellt wurde, deaktiviert die Anwendung nur das VSTO-Add-in, das den Fehler verursacht hat. Andere VSTO-Add-Ins, die mit den Office-Entwicklungstools in Visual Studio für diese Office-Anwendung erstellt wurden, werden weiterhin geladen.

### <a name="soft-disabling"></a>Weiche Deaktivierung
 Die weiche Deaktivierung kann auftreten, wenn ein VSTO-Add-In einen Fehler erzeugt, der nicht zur unerwarteten Beendigung der Anwendung führt. Ein VSTO-Add-In kann von einer Anwendung z. B. weich deaktiviert werden, wenn es einen Ausnahmefehler auslöst, während der <xref:Microsoft.Office.Tools.AddIn.Startup> -Ereignishandler ausgeführt wird. Wenn ein VSTO-Add-in weich deaktiviert ist, wird es in der Liste **inaktive Anwendungs-Add-ins** in der Anwendung angezeigt, und die Anwendung ändert den Wert des Registrierungs Eintrags **LoadBehavior** für das VSTO-Add-in, um anzugeben, dass es entladen wurde. Weitere Informationen zum Registrierungs Eintrag **LoadBehavior** finden [Sie unter Registrierungseinträge für VSTO-Add-ins](../vsto/registry-entries-for-vsto-add-ins.md).

## <a name="troubleshoot-installation-errors-by-using-the-event-viewer"></a>Beheben von Installationsfehlern mithilfe der Ereignisanzeige
 Die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] schreibt Meldungen für alle Ausnahmen, die beim Installieren oder Deinstallieren von Office-Projektmappen ausgelöst werden, in die Ereignisanzeige in Windows. Anhand dieser Meldungen können Sie Installations- und Bereitstellungsprobleme beheben.

## <a name="troubleshoot-startup-errors-by-using-a-log-file-and-error-messages"></a>Beheben von Start Fehlern mithilfe einer Protokolldatei und Fehlermeldungen
 Alle beim Start auftretenden Fehler können von der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] in eine Protokolldatei geschrieben oder in einem Meldungsfeld angezeigt werden. Standardmäßig werden diese Optionen deaktiviert. Sie können die Optionen aktivieren, indem Sie Umgebungsvariablen erstellen.

 Um jeden Fehler in einem Meldungsfeld anzuzeigen, erstellen Sie eine Umgebungsvariable mit dem Namen `VSTO_SUPPRESSDISPLAYALERTS` , die Sie auf 0 (null) festlegen. Sie können die Meldungen unterdrücken, indem Sie die Umgebungsvariable löschen oder auf 1 (eins) festlegen.

 Um die Fehler in eine Protokolldatei zu schreiben, erstellen Sie eine Umgebungsvariable mit dem Namen `VSTO_LOGALERTS` , die Sie auf 1 (eins) festlegen. Die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] erstellt die Protokolldatei in dem Ordner, der das Bereitstellungsmanifest für das VSTO-Add-In enthält, bzw. dem Ordner, der das Dokument oder die Arbeitsmappe enthält, das bzw. die der Anpassung zugeordnet ist. Wenn dies fehlschlägt, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] erstellt die Protokolldatei im lokalen Ordner " *% Temp%* ". Für VSTO-Add-Ins auf Anwendungsebene lautet der Standardname „ *Add-In-Name*.vsto.log“. Für Projekte auf Dokumentebene lautet der Name der Protokolldatei „ *Dokumentname*.*Erweiterung*.log“; Beispiel: „ExcelWorkbook1.xlsx.log“. Um die Fehlerprotokollierung zu beenden, löschen Sie die Umgebungsvariable, oder legen Sie sie auf 0 (null) fest.

## <a name="see-also"></a>Siehe auch

- [Erstellen von Office-Lösungen](../vsto/building-office-solutions.md)
- [Gewusst wie: Erneutes Aktivieren eines VSTO-Add-Ins, das deaktiviert wurde](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)
- [Program mieren von VSTO-Add-ins](../vsto/programming-vsto-add-ins.md)