---
title: Erstellen von SharePoint-Workflow-Projektmappen | Microsoft-Dokumentation
description: Erstellen Sie mithilfe von Tools SharePoint-Wokflowprojektmappen, um benutzerdefinierte Workflows zu erstellen, die den Lebenszyklus von Dokumenten verwalten und Elemente auf SharePoint-Websites auflisten.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
f1_keywords:
- VSTO.NewSharePointWorkflowWizard.Page3
- VS.SharePointTools.Workflow.WorkflowName
- VSTO.NewSharePointWorkflowWizard.Page2
- VSTO.NewSharePointWorkflowWizard.Page1
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 28a5bc44b0f6fa04d32c574e9772369709736ddd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949076"
---
# <a name="create-sharepoint-workflow-solutions"></a>Erstellen von SharePoint-Workflow-Projektmappen

[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] enthält Tools, mit denen Sie benutzerdefinierte Workflows erstellen können, die den Lebenszyklus von Dokumenten und Listenelementen auf einer SharePoint-Website verwalten können. Zu den bereitgestellten Elementen gehören ein Designer, Aktivitätssteuerelemente und die notwendigen Assemblyverweise. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] enthält zudem den **Assistent zum Anpassen von SharePoint**, mit dem Sie Workflows erstellen und konfigurieren können.

Weitere Informationen zu SharePoint finden Sie unter [Microsoft SharePoint-Produkte und -Technologien](/sharepoint/dev/).

## <a name="workflows-in-sharepoint"></a>Workflows in SharePoint
 Wenn Sie einer SharePoint-Bibliothek oder -Liste einen Workflow hinzufügen, erzwingen Sie einen Geschäftsprozess für alle Elemente in der Bibliothek oder Liste. Ein Workflow beschreibt die Aktionen, die das System oder der Benutzer für jedes Element durchführen muss, z. B. das Senden eines Elements zur Bearbeitung und zum anschließenden Review. Diese Aktionen, die als *Aktivitäten* bezeichnet werden, sind die Bestandteile des Workflows.

 Sie können SharePoint-Workflows in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] erstellen und auf einer SharePoint-Website bereitstellen. Nachdem ein Workflow in SharePoint bereitgestellt wurde, müssen Sie ihn einer Bibliothek oder Liste zuordnen. Dieser kann dann automatisch, von einem Prozess oder manuell von einem Benutzer gestartet werden. Weitere Informationen zum Workflowvorgang finden Sie unter [Entwickeln von SharePoint-Workflows mithilfe von Visual Studio](/sharepoint/dev/general-development/develop-sharepoint-workflows-using-visual-studio).

## <a name="create-custom-sharepoint-workflows"></a>Erstellen von benutzerdefinierten SharePoint-Workflows
 In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] stehen zwei SharePoint-Workflowprojekte zur Verfügung: **Sequenzieller Workflow** und **Zustandsautomatworkflow**.

 Ein *sequenzieller Workflow* stellt eine Reihe von Schritten dar. Die Schritte werden nacheinander ausgeführt, bis die letzte Aktivität abgeschlossen ist. Sequenzielle Workflows gehen bei der Ausführung immer strikt sequenziell vor. Da sie externe Ereignisse empfangen können und parallele logische Flows enthalten, kann die Ausführungsreihenfolge variieren. Die folgende Abbildung zeigt ein Beispiel für einen sequenziellen Workflow.

 ![Sequenzieller Workflow](../sharepoint/media/sp-sequential.png "Sequenzieller Workflow")

 Ein *Zustandsautomatworkflow* stellt Zustände, Übergänge und Aktionen dar. Die Schritte in einem Zustandsautomatworkflow werden asynchron ausgeführt. Das bedeutet, dass sie nicht notwendigerweise nacheinander ausgeführt werden, sondern stattdessen durch Aktionen und Zustände ausgelöst werden. Ein Zustand wird als Startzustand festgelegt, und aufgrund eines Ereignisses wird ein Übergang in einen anderen Zustand vorgenommen. Für einen Zustandsautomaten kann ein Endzustand festgelegt werden, der das Ende des Workflows bestimmt. Das folgende Diagramm zeigt ein Beispiel für einen Zustandsautomatworkflow.

 ![Zustandsautomat-Workflow](../sharepoint/media/sp-state.png "Zustandsautomat-Workflow")

 Weitere Informationen zu den verschiedenen Workflows finden Sie unter [Workflowtypen](/previous-versions/office/developer/sharepoint-2010/ms468447(v=office.14)).

### <a name="use-the-wizard"></a>Verwenden des Assistenten
 Wenn Sie in ein SharePoint-Workflowprojekt in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] erstellen, geben Sie die Einstellungen zunächst im **Assistent zum Anpassen von SharePoint** an. Der Assistent verwendet diese Einstellungen, um ein Projekt im **Projektmappen-Explorer** zu erstellen. Dieses Projekt enthält eine Codedatei, mehrere Dateien zum Bereitstellen des Workflows sowie Verweise auf Assemblys, die zum Erstellen eines benutzerdefinierten SharePoint-Workflows erforderlich sind.

 Nachdem Sie einen Workflow erstellt haben, können Sie dessen Eigenschaften im Eigenschaftenfenster bearbeiten. Obwohl die meisten Workfloweigenschaften direkt im Eigenschaftenfenster geändert werden können, müssen Sie für manche auf die Schaltfläche mit den Auslassungspunkten (![Auslassungspunkte im ASP.NET Mobile-Designer](../sharepoint/media/mwellipsis.gif "Auslassungszeichen im ASP.NET Mobile-Designer")) klicken, um die Werte zu ändern. Mit dieser Schaltfläche wird der **Assistent zum Anpassen von SharePoint** neu gestartet. Nachdem Sie die Änderungen an den Eigenschaftswerten vorgenommen haben, klicken Sie auf **Fertigstellen**, um den Vorgang abzuschließen.

> [!NOTE]
> Die Eigenschaft **Workflowtyp** ist schreibgeschützt und kann nicht geändert werden. Wenn Sie den Workflowtyp ändern möchten, müssen Sie einen weiteren Workflow erstellen.

## <a name="design-a-sharepoint-workflow"></a>Entwerfen eines SharePoint-Workflows
 Nachdem Sie alle Schritte im Geschäftsprozess definiert haben, verwenden Sie den [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]-Workflow-Designer, um den SharePoint-Workflow zu entwerfen. Doppelklicken Sie auf „Workflow1.cs“ oder „Workflow1.vb“ im **Projektmappen-Explorer**, oder öffnen Sie das Kontextmenü für eine dieser Dateien, und klicken Sie dort auf **Öffnen**, um den Designer zu öffnen.

### <a name="activities"></a>Aktivitäten
 Fügen Sie Aktivitäten aus der **Toolbox** zu einem *Workflowzeitplan* im Designer hinzu, um einen Workflow zu entwerfen. Ein Workflowzeitplan enthält die Abfolge der Aktivitäten in der Reihenfolge, in der sie ausgeführt werden sollen.

 Es gibt zwei Arten von Aktivitäten:

- *Einfache Aktivitäten* führen eine einzelne Arbeitseinheit durch, z. B. „Um 1 Tag verschieben“ oder „Webdienst starten“.

- *Zusammengesetzte Aktivitäten* enthalten andere Aktivitäten. Beispielsweise kann eine bedingte Aktivität zwei Verzweigungen enthalten.

  Beide Arten von Aktivitäten sind in der **Toolbox** verfügbar.

  Aktivitäten können über Eigenschaften, Methoden und Ereignisse verfügen. Verwenden Sie das Fenster **Eigenschaften**, um die Eigenschaften einer Aktivität festzulegen.

  Sie können auch eine benutzerdefinierte Aktivität erstellen. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Website-Workflowaktivität](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md).

  Aktivitäten werden auf den folgenden Registerkarten der **Toolbox** organisiert:

- **SharePoint Workflow**

- **Windows Workflow Version 3.0**

- **Windows Workflow Version 3.5**

  SharePoint unterstützt nicht alle Kernaktivitäten für Workflows. Weitere Informationen finden Sie unter [Workflowaktivitäten für SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14)).

#### <a name="sharepoint-workflow-activities"></a>SharePoint-Workflowaktivitäten
 Die **SharePoint Workflow**-Registerkarten enthalten Aktivitäten für die spezielle Verwendung in [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]. Diese Aktivitäten vereinfachen und optimieren die Entwicklung von Lebenszyklusworkflows für Dokumente. Weitere Informationen zu den auf der Registerkarte **SharePoint Workflow** aufgeführten Aktivitäten finden Sie unter [Workflowaktivitäten für SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14)).

#### <a name="windows-workflow-activities"></a>Windows Workflow-Aktivitäten
 Die **Windows Workflow**-Registerkarten enthalten Aktivitäten, die von [!INCLUDE[TLA#tla_workflow](../sharepoint/includes/tlasharptla-workflow-md.md)] bereitgestellt werden. Sie können diese Aktivitäten verwenden, um Workflowzeitpläne für jede Art von Windows Workflow-Anwendung zu erstellen.

 Weitere Informationen zu den Aktivitäten auf der Registerkarte **Windows Workflows** finden Sie unter [Windows Workflow Foundation-Aktivitäten](/previous-versions/dotnet/netframework-3.5/ms733615(v=vs.90)). Weitere Informationen zu Windows Workflow Foundation finden Sie unter [Übersicht über Windows Workflow Foundation](/previous-versions/dotnet/netframework-3.5/ms734631(v=vs.90)).

### <a name="work-with-activities-in-the-designer"></a>Arbeiten mit Aktivitäten im Designer
 Ihr Workflowzeitplan kann eine Kombination aus Windows Workflow-Aktivitäten und SharePoint Workflow-Aktivitäten enthalten.

 Der Designer zeigt Hinweise an, damit Sie Aktivitäten ordnungsgemäß positionieren und konfigurieren können. Wenn Sie eine Aktivität in den Workflowzeitplan ziehen oder kopieren, erkennen Sie an einem grünen Pluszeichen (+) im Designer, welche Positionen für diese Aktivität im Workflow gültig sind. Sie können eine Aktivität nicht an einer ungültigen Position einfügen. Beispielsweise können Sie keine Sendeaktivät als erste Aktivität in der Verzweigung für eine Lauschaktivität positionieren. Weitere Informationen finden Sie im [SharePoint Designer Developer Center](https://developer.microsoft.com/office/docs).

## <a name="collect-information-during-the-workflow"></a>Sammeln von Informationen während des Workflows
 Sie sollten zu vordefinierten Zeitpunkten im Workflow Informationen von Benutzern einholen. Informationen können mithilfe von Formularen oder Elementeigenschaften gesammelt werden.

### <a name="forms"></a>Formulare
 Formulare sind wie Dialogfelder, die Fragen enthalten und es Benutzern ermöglichen, Antworten einzugeben.

 Es gibt vier Arten von Formularen, die in einem Workflow verwendet werden können:

- Zuordnung

- Initiierung

- Modifikation (Modification)

- Aufgabe

  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] enthält Elementvorlagen für Zuordnungs- und Initiierungsformulare. Ein *Zuordnungsformular* ermöglicht es beispielsweise einem Administrator, bei der Installation des Workflows passende Parameter einzugeben (z. B. ein Ausgabenlimit für einen Ausgabenworkflow). Ein *Initiierungsformular* ermöglicht es beispielsweise dem Benutzer eines Ausgabenworkflows, den ausgegebenen Betrag in den Workflow einzugeben. Weitere Informationen zu diesen Formularen finden Sie unter [SharePoint-Projekt- und -Projektelementvorlagen](../sharepoint/sharepoint-project-and-project-item-templates.md).

### <a name="item-properties"></a>Elementeigenschaften
 Sie können auch Informationen von Benutzern erfassen, indem Sie die Eigenschaften eines Elements in der SharePoint-Bibliothek oder -Liste verwenden. Die Hauptcodedatei („Workflow1.cs“ oder „Workflow1.vb“) deklariert eine Instanz der Klasse Microsoft.SharePoint.Workflow.SPWorkflowActivationProperties.WorkflowProperties namens `workflowProperties`. Verwenden Sie das `workflowProperties`-Objekt, um im Code auf die Eigenschaften der Bibliothek oder Liste zuzugreifen. Ein Beispiel finden Sie unter [Exemplarische Vorgehensweise: Erstellen und Debuggen einer Projektmappe für einen SharePoint-Workflow](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md).

## <a name="debug-a-sharepoint-workflow-template"></a>Debuggen einer SharePoint-Workflowvorlage
 Sie können ein SharePoint-Workflowprojekt auf die gleiche Weise wie andere webbasierte [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]-Projekte debuggen. Wenn Sie den [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]-Debugger starten, verwendet [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] die Einstellungen, die Sie im **Assistent zum Anpassen von SharePoint** angeben, um die entsprechende SharePoint-Website zu öffnen und die Workflowvorlage der entsprechenden Bibliothek oder Liste automatisch zuzuordnen. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fügt zudem den [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]-Debugger an den [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]-Prozess namens *w3wp.exe* an.

 Sie müssen den Workflow manuell starten, um ihn zu testen. Weitere Informationen finden Sie im Abschnitt „Debuggen von Workflows“ unter [Debuggen von SharePoint-Projektmappen](../sharepoint/debugging-sharepoint-solutions.md). Weitere Informationen zum Debuggen von Webanwendungen in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] finden Sie unter [Debuggen von ASP.NET- oder ASP.NET Core-Apps in Visual Studio](../debugger/how-to-enable-debugging-for-aspnet-applications.md).

## <a name="deploy-a-sharepoint-workflow-template"></a>Bereitstellen einer SharePoint-Workflowvorlage
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]-Projekte für SharePoint-Workflows werden genau wie andere [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]-Projekte für SharePoint bereitgestellt. Weitere Informationen finden Sie unter [Packen und Bereitstellen von SharePoint-Projektmappen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md).

## <a name="import-globally-reusable-workflows"></a>Importieren global wiederverwendbarer Workflows
 Mit SharePoint Designer können Sie nicht nur websitespezifisch wiederverwendbare Workflows erstellen, sondern auch *global wiederverwendbare Workflows*, die auf jeder SharePoint-Website verwendet werden können. Die Option „Wiederverwendbaren Workflow importieren“ in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kann derzeit keine global wiederverwendbaren Workflows importieren. Sie können jedoch entweder SharePoint Designer verwenden, um einen global wiederverwendbaren Workflow in einen wiederverwendbaren Workflow zu konvertieren, oder den Workflow als nicht konvertierten deklarativen Workflow importieren. Weitere Informationen finden Sie unter [Importieren von Elementen von einer vorhandenen SharePoint-Website](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

## <a name="related-topics"></a>Verwandte Themen

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[Exemplarische Vorgehensweise: Erstellen und Debuggen einer Projektmappe für einen SharePoint-Workflow](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)|Diese Anleitung führt Sie Schritt für Schritt durch die Erstellung und das Debuggen eines einfachen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]-Workflows.|
|[Exemplarische Vorgehensweise: Erstellen eines Workflows mit Zuordnungs- und Initiierungsformularen](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)|Diese Anleitung führt Sie Schritt für Schritt durch das Erstellen eines vollumfänglichen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]-Workflows mit Zuordnungs- und Initiierungsformularen.|
|[Exemplarische Vorgehensweise: Hinzufügen einer Anwendungsseite zu einem Workflow](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)|Diese Anleitung baut auf [Exemplarische Vorgehensweise: Erstellen eines Workflows mit Zuordnungs- und Initiierungsformularen](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) auf und ergänzt diese durch eine zusätzliche *ASPX*-Anwendungsseite, die Berichte zu in den Workflow eingegebenen Daten erstellt.|
|[Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Website-Workflowaktivität](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)|In dieser Anleitung werden zwei Hauptaufgaben veranschaulicht: das Erstellen eines Workflows auf Websiteebene und das Erstellen einer benutzerdefinierten Workflowaktivität.|
|[Exemplarische Vorgehensweise: Importieren eines wiederverwendbaren Workflows aus SharePoint Designer in Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)|In dieser Anleitung wird veranschaulicht, wie ein in SharePoint-Designer 2010 erstellter, wiederverwendbarer deklarativer Workflow in ein SharePoint-Projekt in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] importiert wird.|

## <a name="see-also"></a>Weitere Informationen

- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)
- [Erstellen und Debuggen von SharePoint-Lösungen](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Erstellen von Anwendungsseiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)