---
title: Benutzerdefinierte Aufgabenbereiche
description: Erfahren Sie, wie Sie mit benutzerdefinierten Aufgabenbereichen einen eigenen Aufgabenbereich erstellen und Benutzern eine vertraute Schnittstelle für den Zugriff auf die Features Ihrer Lösung bereitstellen können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, task panes
- user interface panels [Office development in Visual Studio]
- task panes [Office development in Visual Studio]
- user interfaces [Office development in Visual Studio], custom task panes
- custom task panes [Office development in Visual Studio], creating
- task panes [Office development in Visual Studio]. multiple application windows
- custom task panes [Office development in Visual Studio], multiple application windows
- task panes [Office development in Visual Studio], creating
- application-level add-ins [Office development in Visual Studio], custom task panes
- multiple applications windows with custom task panes [Office development in Visual Studio]
- add-ins [Office development in Visual Studio], custom task panes
- custom task panes [Office development in Visual Studio]
- task panes [Office development in Visual Studio], about custom task panes
- custom task panes [Office development in Visual Studio], about custom task panes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b08e0e3bbc9f45b33ecd0248179011113db7a779
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844179"
---
# <a name="custom-task-panes"></a>Benutzerdefinierte Aufgabenbereiche
  Aufgabenbereiche sind Bereiche der Benutzeroberfläche, die in einer Microsoft Office-Anwendung normalerweise auf einer Seite eines Fensters angedockt sind. Mit benutzerdefinierten Aufgabenbereichen können Sie einen eigenen Aufgabenbereich erstellen und Benutzern eine vertraute Oberfläche für den Zugriff auf die Funktionen Ihrer Projektmappe zur Verfügung stellen. Die Oberfläche kann beispielsweise Steuerelemente enthalten, die Code zum Ändern von Dokumenten oder zum Anzeigen von Daten aus einer Datenquelle ausführen.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

> [!NOTE]
> Ein benutzerdefinierter Aufgabenbereich ist nicht das gleiche wie der Aktionsbereich. Der Aktionsbereich ist Bestandteil von Anpassungen auf Dokumentebene für Microsoft Office Word und Microsoft Office Excel. Weitere Informationen finden Sie unter [Übersicht über den Aktions](../vsto/actions-pane-overview.md)Bereich.

## <a name="benefits-of-custom-task-panes"></a>Vorteile von benutzerdefinierten Aufgabenbereichen
 Mit benutzerdefinierten Aufgabenbereichen können Sie Funktionen in eine vertraute Benutzeroberfläche integrieren. Sie können mit Visual Studio-Tools schnell einen benutzerdefinierten Aufgabenbereich erstellen.

### <a name="familiar-user-interface"></a>Vertraute Benutzeroberfläche
 Benutzer von Anwendungen im Microsoft Office System sind bereits mit der Verwendung von Aufgabenbereichen wie dem Aufgabenbereich **Formatvorlagen und Formatierung** in Word vertraut. Das Verhalten von benutzerdefinierten Aufgabenbereichen entspricht dem Verhalten anderer Aufgabenbereiche in Microsoft Office System. Benutzer können benutzerdefinierte Aufgabenbereiche an verschiedene Seiten des Anwendungsfensters andocken, oder sie können benutzerdefinierte Aufgabenbereiche an eine beliebige Position im Fenster ziehen. Sie können ein VSTO-Add-In erstellen, das mehrere benutzerdefinierte Aufgabenbereiche gleichzeitig anzeigt, wobei die Benutzer jeden Aufgabenbereich einzeln steuern können.

### <a name="windows-forms-support"></a>Windows Forms-Unterstützung
 Die Benutzeroberfläche eines benutzerdefinierten Aufgabenbereichs, den Sie mit den Office-Entwicklungstools in Visual Studio erstellen, basiert auf Windows Forms-Steuerelementen. Sie können zum Entwerfen der Benutzeroberfläche für einen benutzerdefinierten Aufgabenbereich den vertrauten Windows Forms-Designer verwenden. Sie können auch die Datenbindungsunterstützung in Windows Forms nutzen, um eine Datenquelle an Steuerelemente im Aufgabenbereich zu binden.

## <a name="create-a-custom-task-pane"></a>Erstellen eines benutzerdefinierten Aufgabenbereichs
 Ein einfacher benutzerdefinierter Aufgabenbereich kann in zwei Schritten erstellt werden:

1. Erstellen Sie eine Benutzeroberfläche für den benutzerdefinierten Aufgabenbereich, indem Sie einem <xref:System.Windows.Forms.UserControl>-Objekt Windows Forms-Steuerelemente hinzufügen.

2. Instanziieren Sie den benutzerdefinierten Aufgabenbereich, indem Sie das Benutzersteuerelement an das <xref:Microsoft.Office.Tools.CustomTaskPaneCollection>-Objekt im VSTO-Add-In übergeben. Diese Auflistung gibt ein neues <xref:Microsoft.Office.Tools.CustomTaskPane>-Objekt zurück, mit dem Sie die Darstellung des Aufgabenbereichs ändern und auf Benutzerereignisse reagieren können.

   Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen eines benutzerdefinierten Aufgabenbereichs zu einer Anwendung](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).

### <a name="create-the-user-interface"></a>Erstellen der Benutzeroberfläche
 Alle benutzerdefinierten Aufgabenbereiche, die mit den Office-Entwicklungstools in Visual Studio erstellt werden, enthalten ein <xref:System.Windows.Forms.UserControl>-Objekt. Dieses Benutzersteuerelement stellt die Benutzeroberfläche des benutzerdefinierten Aufgabenbereichs bereit. Sie können das Benutzersteuerelement zur Entwurfszeit oder zur Laufzeit erstellen. Wenn Sie das Benutzersteuerelement zur Entwurfszeit erstellen, können Sie die Benutzeroberfläche des Aufgabenbereichs mit dem Windows Forms-Designer entwerfen.

### <a name="instantiate-the-custom-task-pane"></a>Instanziieren des benutzerdefinierten Aufgabenbereichs
 Nachdem Sie ein Benutzersteuerelement erstellt haben, das die Benutzeroberfläche des benutzerdefinierten Aufgabenbereichs enthält, müssen Sie <xref:Microsoft.Office.Tools.CustomTaskPane> instanziieren. Übergeben Sie hierfür das Benutzersteuerelement an <xref:Microsoft.Office.Tools.CustomTaskPaneCollection> im VSTO-Add-In, indem Sie eine der <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A>-Methoden aufrufen. Diese Auflistung wird als `CustomTaskPanes`-Feld der `ThisAddIn`-Klasse verfügbar gemacht. Das folgende Codebeispiel sollte von der `ThisAddIn`-Klasse ausgeführt werden.

 [!code-vb[Trin_TaskPaneBasic#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#2)]
 [!code-csharp[Trin_TaskPaneBasic#2](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#2)]

 Die <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A>-Methoden geben ein neues <xref:Microsoft.Office.Tools.CustomTaskPane>-Objekt zurück. Sie können dieses Objekt verwenden, um die Darstellung des Aufgabenbereichs zu ändern und auf Benutzerereignisse zu reagieren.

### <a name="control-the-task-pane-in-multiple-windows"></a>Steuern des Aufgabenbereichs in mehreren Fenstern
 Benutzerdefinierte Aufgabenbereiche sind einem Dokumentrahmenfenster zugeordnet, das eine Ansicht eines Dokuments oder Elements für den Benutzer darstellt. Der Aufgabenbereich ist nur sichtbar, wenn das zugeordnete Fenster sichtbar ist.

 Um zu bestimmen, in welchem Fenster der benutzerdefinierte Aufgabenbereich angezeigt wird, verwenden Sie die entsprechende <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A>-Methodenüberladung beim Erstellen des Aufgabenbereichs:

- Um dem aktiven Fenster den Aufgabenbereich zuzuordnen, verwenden Sie die <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A>-Methode.

- Um den Aufgabenbereich einem Dokument zuzuordnen, das von einem angegebenen Fenster gehostet wird, verwenden Sie die <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A>-Methode.

  Wenn mehrere Fenster geöffnet sind, erfordern einige Office-Anwendungen explizite Anweisungen dazu, wann der Aufgabenbereich erstellt oder angezeigt werden soll. Daher ist es wichtig, zu entscheiden, wo der benutzerdefinierte Aufgabenbereich im Code instanziiert werden soll, um sicherzustellen, dass der Aufgabenbereich mit den entsprechenden Dokumenten oder Elementen in der Anwendung angezeigt wird. Weitere Informationen finden Sie unter [Verwalten von benutzerdefinierten Aufgabenbereichen in Anwendungs Fenstern](#Managing).

## <a name="access-the-application-from-the-task-pane"></a>Zugreifen auf die Anwendung über den Aufgabenbereich
 Wenn Sie die Anwendung über das Benutzersteuerelement automatisieren möchten, können Sie mithilfe von `Globals.ThisAddIn.Application` im Code direkt auf das Objektmodell zugreifen. Die statische `Globals`-Klasse ermöglicht den Zugriff auf das `ThisAddIn`-Objekt. Das `Application`-Feld dieses Objekts ist der Einstiegspunkt in das Objektmodell der Anwendung.

 Weitere Informationen zum- `Application` Feld des- `ThisAddIn` Objekts finden Sie unter [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md). Eine exemplarische Vorgehensweise, die veranschaulicht, wie eine Anwendung über einen benutzerdefinierten Aufgabenbereich automatisiert wird, finden Sie unter Exemplarische Vorgehensweise [: Automatisches eine Anwendung aus einem benutzerdefinierten Aufgaben](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)Bereich. Weitere Informationen zur- `Globals` Klasse finden Sie unter [globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md).

## <a name="manage-the-user-interface-of-the-task-pane"></a>Verwalten der Benutzeroberfläche des Aufgabenbereichs
 Nachdem Sie den Aufgabenbereich erstellt haben, können Sie Eigenschaften und Ereignisse des <xref:Microsoft.Office.Tools.CustomTaskPane>-Objekts verwenden, um die Benutzeroberfläche des Aufgabenbereichs zu steuern und auf Änderungen des Aufgabenbereichs durch Benutzer zu reagieren.

### <a name="make-the-custom-task-pane-visible"></a>Anzeigen des benutzerdefinierten Aufgabenbereichs
 Der Aufgabenbereich ist standardmäßig nicht sichtbar. Um den Aufgabenbereich sichtbar zu machen, müssen Sie die- <xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A> Eigenschaft auf " **true**" festlegen.

 Benutzer können einen Aufgabenbereich jederzeit schließen, indem Sie in der Ecke des Aufgabenbereichs auf die Schaltfläche **Schließen** (X) klicken. Es gibt jedoch kein Standardverfahren für das erneute Öffnen des benutzerdefinierten Aufgabenbereichs durch die Benutzer. Wenn ein Benutzer einen benutzerdefinierten Aufgabenbereich schließt, kann dieser Benutzer den benutzerdefinierten Aufgabenbereich nur erneut anzeigen, wenn Sie ein Verfahren zum Anzeigen des Aufgabenbereichs bereitstellen.

 Wenn Sie im VSTO-Add-In einen benutzerdefinierten Aufgabenbereich erstellen, sollten Sie auch ein Benutzeroberflächenelement, z. B. eine Schaltfläche, erstellen, auf das Benutzer klicken können, um den benutzerdefinierten Aufgabenbereich anzuzeigen oder auszublenden. Wenn Sie einen benutzerdefinierten Aufgabenbereich in einer Microsoft Office-Anwendung erstellen, die das Anpassen des Menübands unterstützt, können Sie dem Menüband eine Steuerelementgruppe mit einer Schaltfläche hinzufügen, über die der benutzerdefinierte Aufgabenbereich angezeigt und ausgeblendet wird. Eine exemplarische Vorgehensweise, die die Vorgehensweise veranschaulicht, finden Sie unter Exemplarische Vorgehensweise [: Synchronisieren eines benutzerdefinierten Aufgabenbereichs mit einer Menü Band Schaltfläche](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).

 Wenn Sie einen benutzerdefinierten Aufgabenbereich in einer Microsoft Office-Anwendung erstellen, die das Anpassen des Menübands nicht unterstützt, können Sie eine <xref:Microsoft.Office.Core.CommandBarButton> hinzufügen, mit der der benutzerdefinierte Aufgabenbereich angezeigt oder ausgeblendet wird.

### <a name="modify-the-appearance-of-the-task-pane"></a>Ändern der Darstellung des Aufgabenbereichs
 Die Größe und Position eines benutzerdefinierten Aufgabenbereichs können mithilfe der Eigenschaften des <xref:Microsoft.Office.Tools.CustomTaskPane>-Objekts gesteuert werden. Mit den Eigenschaften des <xref:System.Windows.Forms.UserControl>-Objekts, das im benutzerdefinierten Aufgabenbereich enthalten ist, können Sie viele weitere Änderungen an der Darstellung eines benutzerdefinierten Aufgabenbereichs vornehmen. Beispielsweise können Sie mit der <xref:System.Windows.Forms.Control.BackgroundImage%2A>-Eigenschaft des Benutzersteuerelements ein Hintergrundbild für einen benutzerdefinierten Aufgabenbereich angeben.

 In der folgenden Tabelle werden die Änderungen aufgelistet, die Sie mithilfe von <xref:Microsoft.Office.Tools.CustomTaskPane>-Eigenschaften an einem benutzerdefinierten Aufgabenbereich vornehmen können.

|Aufgabe|Eigenschaft|
|----------|--------------|
|So ändern Sie die Größe des Aufgabenbereichs|<xref:Microsoft.Office.Tools.CustomTaskPane.Height%2A><br /><br /> <xref:Microsoft.Office.Tools.CustomTaskPane.Width%2A>|
|So ändern Sie die Position des Aufgabenbereichs|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPosition%2A>|
|So blenden Sie den Aufgabenbereich aus oder machen ihn sichtbar|<xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A>|
|So verhindern Sie das Ändern der Position des Aufgabenbereichs durch Benutzer|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPositionRestrict%2A>|

### <a name="program-custom-task-pane-events"></a>Program mieren von benutzerdefinierten Aufgabenbereichs Ereignissen
 Sie können festlegen, dass das VSTO-Add-In auf Änderungen des benutzerdefinierten Aufgabenbereichs durch den Benutzer reagiert. Wenn der Benutzer beispielsweise die Ausrichtung des Bereichs von vertikal in horizontal ändert, sollen möglicherweise die Steuerelemente neu positioniert werden.

 In der folgenden Tabelle sind die Ereignisse aufgeführt, die Sie behandeln können, um auf Änderungen von Benutzern am benutzerdefinierten Aufgabenbereich zu reagieren.

|Aufgabe|Ereignis|
|----------|-----------|
|So reagieren Sie, wenn der Benutzer die Position des Aufgabenbereichs ändert|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPositionChanged>|
|So reagieren Sie, wenn der Benutzer den Aufgabenbereich ausblendet oder sichtbar macht|<xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged>|

## <a name="clean-up-resources-used-by-the-task-pane"></a>Bereinigen von Ressourcen, die vom Aufgabenbereich verwendet werden
 Nachdem Sie einen benutzerdefinierten Aufgabenbereich erstellt haben, bleibt das <xref:Microsoft.Office.Tools.CustomTaskPane>-Objekt so lange im Arbeitsspeicher, wie das VSTO-Add-In ausgeführt wird. Das Objekt verbleibt im Arbeitsspeicher, auch wenn der Benutzer auf die Schaltfläche **Schließen** (X) in der Ecke des Aufgabenbereichs klickt.

 Um vom Aufgabenbereich verwendete Ressourcen zu bereinigen, während das VSTO-Add-In noch ausgeführt wird, verwenden Sie die <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A>-Methode oder <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.RemoveAt%2A>-Methode. Durch diese Methoden werden das angegebene <xref:Microsoft.Office.Tools.CustomTaskPane>-Objekt aus der `CustomTaskPanes`-Auflistung entfernt und die `Dispose`-Methode des Objekts aufgerufen.

 Vom benutzerdefinierten Aufgabenbereich verwendete Ressourcen werden von der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] automatisch bereinigt, wenn das VSTO-Add-In entladen wird. Die-Methode oder die-Methode kann nicht <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.RemoveAt%2A> im- `ThisAddIn_Shutdown` Ereignishandler Ihres Projekts aufgerufen werden. Durch diese Methoden wird <xref:System.ObjectDisposedException> ausgelöst, da die vom <xref:Microsoft.Office.Tools.CustomTaskPane>-Objekt verwendeten Ressourcen von [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] bereinigt werden, bevor `ThisAddIn_Shutdown` aufgerufen wird. Weitere Informationen zu `ThisAddIn_Shutdown` finden Sie unter [Ereignisse in Office-Projekten](../vsto/events-in-office-projects.md).

## <a name="manage-custom-task-panes-in-multiple-application-windows"></a><a name="Managing"></a> Verwalten von benutzerdefinierten Aufgabenbereichen in mehreren Anwendungs Fenstern
 Wenn Sie einen benutzerdefinierten Aufgabenbereich in einer Anwendung erstellen, die mehrere Fenster zum Anzeigen von Dokumenten und anderen Elementen verwendet, müssen Sie in zusätzlichen Schritten sicherstellen, dass der Aufgabenbereich sichtbar ist, wenn der Benutzer es erwartet.

 Benutzerdefinierte Aufgabenbereiche sind in allen Anwendungen einem Dokumentrahmenfenster zugeordnet, das eine Ansicht eines Dokuments oder Elements für den Benutzer enthält. Der Aufgabenbereich ist nur sichtbar, wenn das zugeordnete Fenster sichtbar ist. Allerdings verwenden nicht alle Anwendungen Dokumentrahmenfenster auf dieselbe Weise.

 Für die folgenden Anwendungsgruppen gelten unterschiedliche Entwicklungsanforderungen:

- [Outlook](#Outlook)

- [Word, InfoPath und PowerPoint](#WordAndInfoPath)

## <a name="outlook"></a><a name="Outlook"></a> Positiv
 Wenn Sie einen benutzerdefinierten Aufgabenbereich für Outlook erstellen, wird dieser einem bestimmten Explorer- oder Inspektor-Fenster zugeordnet. Explorers sind Fenster, in denen der Inhalt eines Ordners angezeigt wird, und Inspektoren sind Fenster, die ein Element anzeigen, z. b. eine e-Mail-Nachricht oder eine Aufgabe.

 Wenn Sie einen benutzerdefinierten Aufgabenbereich mit mehreren Explorer- oder Inspektor-Fenstern anzeigen möchten, müssen Sie eine neue Instanz des benutzerdefinierten Aufgabenbereichs erstellen, wenn ein Explorer- oder Inspektor-Fenster geöffnet wird. Behandeln Sie dazu ein Ereignis, das ausgelöst wird, wenn ein Explorer- oder Inspektor-Fenster erstellt wird, und erstellen Sie dann den Aufgabenbereich im Ereignishandler. Sie können auch Explorer- und Inspektor-Ereignisse behandeln, um Aufgabenbereiche abhängig davon auszublenden oder anzuzeigen, welches Fenster sichtbar ist.

 Um den Aufgabenbereich einem bestimmten Explorer oder Inspektor zuzuordnen, verwenden Sie die <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> -Methode, um den Aufgabenbereich zu erstellen, und übergeben Sie das- <xref:Microsoft.Office.Interop.Outlook.Explorer> Objekt oder das- <xref:Microsoft.Office.Interop.Outlook.Inspector> Objekt an den *Window* -Parameter. Weitere Informationen zum Erstellen von benutzerdefinierten Aufgabenbereichen finden Sie unter [Übersicht über benutzerdefinierte Aufgaben](../vsto/custom-task-panes.md)Bereiche.

- <xref:Microsoft.Office.Interop.Outlook.ExplorersEvents_Event.NewExplorer>

- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Activate>

- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close>

- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Deactivate>

  Um den Zustand von Inspektor-Fenstern zu überwachen, können Sie die folgenden Inspektor-bezogenen Ereignisse behandeln:

- <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector>

- <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Activate>

- <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Close>

- <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Deactivate>

### <a name="prevent-multiple-instances-of-a-custom-task-pane-in-outlook"></a>Verhindern mehrerer Instanzen eines benutzerdefinierten Aufgabenbereichs in Outlook
 Um zu verhindern, dass in Outlook-Fenstern mehrere Instanzen eines benutzerdefinierten Aufgabenbereichs angezeigt werden, müssen Sie den benutzerdefinierten Aufgabenbereich explizit aus der `CustomTaskPanes`-Auflistung der `ThisAddIn`-Klasse entfernen, wenn die einzelnen Fenster geschlossen werden. Rufen Sie die <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A>-Methode in einem Ereignis auf, das beim Schließen eines Fensters ausgelöst wird, z. B. <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close> oder <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Close>.

 Wenn Sie den benutzerdefinierten Aufgabenbereich nicht explizit entfernen, werden in Outlook-Fenstern möglicherweise mehrere Instanzen des benutzerdefinierten Aufgabenbereichs angezeigt. Fenster werden in Outlook gelegentlich wiederverwendet, und in wiederverwendeten Fenstern werden Verweise auf benutzerdefinierte Aufgabenbereiche beibehalten, die an die Fenster angefügt waren.

## <a name="word-infopath-and-powerpoint"></a><a name="WordAndInfoPath"></a> Word, InfoPath und PowerPoint
 In Word, InfoPath und PowerPoint wird jedes Dokument in einem anderen Dokumentrahmenfenster angezeigt. Wenn Sie einen benutzerdefinierten Aufgabenbereich für diese Anwendungen erstellen, ist dieser nur einem bestimmten Dokument zugeordnet. Wenn der Benutzer ein anderes Dokument öffnet, wird der benutzerdefinierte Aufgabenbereich ausgeblendet, bis das vorherige Dokument wieder sichtbar ist.

 Wenn Sie einen benutzerdefinierten Aufgabenbereich mit mehreren Dokumenten anzeigen möchten, erstellen Sie eine neue Instanz des benutzerdefinierten Aufgabenbereichs, wenn der Benutzer ein neues Dokument erstellt oder ein vorhandenes Dokument öffnet. Behandeln Sie dazu Ereignisse, die ausgelöst werden, wenn ein Dokument erstellt oder geöffnet wird, und erstellen Sie dann den Aufgabenbereich in den Ereignishandlern. Sie können auch Dokumentereignisse behandeln, um Aufgabenbereiche abhängig davon auszublenden oder anzuzeigen, welches Dokument sichtbar ist.

 Um den Aufgabenbereich einem bestimmten Dokument Fenster zuzuordnen, verwenden Sie die <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> -Methode, um den Aufgabenbereich zu erstellen, und übergeben Sie einen <xref:Microsoft.Office.Interop.Word.Window> (für Word),  <xref:Microsoft.Office.Interop.InfoPath.WindowObject> (für InfoPath) oder [DocumentWindow](/previous-versions/office/developer/office-2010/ff762047(v=office.14)) (für PowerPoint) an den *Window* -Parameter.

### <a name="word-events"></a>Word-Ereignisse
 Um den Zustand von Dokumentfenstern in Word zu überwachen, können Sie die folgenden Ereignisse behandeln:

- <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeClose>

- <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>

- <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.NewDocument>

- <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.WindowActivate>

- <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.WindowDeactivate>

### <a name="infopath-events"></a>InfoPath-Ereignisse
 Um den Zustand von Dokumentfenstern in InfoPath zu überwachen, können Sie die folgenden Ereignisse behandeln:

- <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.NewXDocument>

- <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.WindowActivate>

- <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.WindowDeactivate>

- <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentBeforeClose>

- <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentOpen>

### <a name="powerpoint-events"></a>PowerPoint-Ereignisse
 Um den Zustand von Dokumentfenstern in PowerPoint zu überwachen, können Sie die folgenden Ereignisse behandeln:

- [Microsoft.Office.Interop.PowerPoint.EApplication_Event. afternewpresentation](/previous-versions/office/developer/office-2010/ff761105(v%3doffice.14))

- [Microsoft.Office.Interop.PowerPoint.EApplication_Event. AfterPresentationOpen](/previous-versions/office/developer/office-2010/ff762843(v%3doffice.14))

- [Microsoft.Office.Interop.PowerPoint.EApplication_Event. NewPresentation](/previous-versions/office/developer/office-2010/ff761498(v%3doffice.14))

- [Microsoft.Office.Interop.PowerPoint.EApplication_Event. PresentationOpen](/previous-versions/office/developer/office-2010/ff760423(v=office.14))

- [Microsoft.Office.Interop.PowerPoint.EApplication_Event. windowaktivierungs](/previous-versions/office/developer/office-2010/ff761153(v=office.14))

- [Microsoft.Office.Interop.PowerPoint.EApplication_Event. windowdeaktivieren](/previous-versions/office/developer/office-2010/ff763093(v=office.14))

## <a name="see-also"></a>Siehe auch
- [Gewusst wie: Hinzufügen eines benutzerdefinierten Aufgabenbereichs zu einer Anwendung](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Exemplarische Vorgehensweise: Automatisieren einer Anwendung über einen benutzerdefinierten Aufgabenbereich](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
- [Exemplarische Vorgehensweise: Synchronisieren eines benutzerdefinierten Aufgabenbereichs mit einer Menü Band Schaltfläche](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)
- [Exemplarische Vorgehensweise: Anzeigen von benutzerdefinierten Aufgabenbereichen mit e-Mails in Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)
