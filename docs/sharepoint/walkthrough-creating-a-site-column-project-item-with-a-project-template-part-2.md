---
title: Erstellen eines Projekt Elements für eine Website Spalte mit einer Projektvorlage, Teil 2
titleSuffix: ''
description: Fügen Sie einer Website Spalten-Projektvorlage einen Assistenten hinzu, um Daten von Benutzern zu sammeln, wenn Sie die Vorlage zum Erstellen eines SharePoint-Projekts verwenden, das das Projekt Element enthält.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], creating template wizards
- SharePoint project items, creating template wizards
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: bc664a50fc307c59d5c168b26c8af1bc6181ebad
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918719"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-2"></a>Exemplarische Vorgehensweise: Erstellen eines Projekt Elements für eine Website Spalte mit einer Projektvorlage, Teil 2
  Nachdem Sie einen benutzerdefinierten Typ des SharePoint-Projektelements definiert und diesen einer Projektvorlage in Visual Studio zugeordnet haben, empfiehlt es sich, außerdem einen Assistenten für die Vorlage bereitzustellen. Mithilfe des Assistenten können Sie Informationen von Benutzern sammeln, während diese Ihre Vorlage verwenden, um ein neues Projekt zu erstellen, das das Projektelement enthält. Mit den gesammelten Informationen kann das Projektelement initialisiert werden.

 In dieser exemplarischen Vorgehensweise fügen Sie der Projektvorlage für Website Spalten einen Assistenten hinzu, der in Exemplarische Vorgehensweise [: Erstellen eines Projekt Elements für eine Website Spalte mit einer Projektvorlage, Teil 1,](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)veranschaulicht wird. Wenn ein Benutzer ein Website Spalten Projekt erstellt, sammelt der Assistent Informationen über die Website Spalte (z. b. den Basistyp und die zugehörige Gruppe) und fügt diese Informationen der *Elements.xml* -Datei im neuen Projekt hinzu.

 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:

- Erstellen eines Assistenten für einen benutzerdefinierten SharePoint-Projektelementtyp, dem eine Projektvorlage zugeordnet ist.

- Definieren Sie eine benutzerdefinierte Assistenten-Benutzeroberfläche, die den integrierten Visual Studio-Assistenten für SharePoint-Projekte ähnelt.

- Erstellen von zwei *SharePoint-Befehlen* , die verwendet werden, um die lokale SharePoint-Website aufzurufen, während der Assistent ausgeführt wird. SharePoint-Befehle sind Methoden, mit denen Visual Studio-Erweiterungsassemblys APIs im SharePoint-Serverobjektmodell aufrufen können. Weitere Informationen finden Sie unter [Aufrufen der SharePoint-Objekt Modelle](../sharepoint/calling-into-the-sharepoint-object-models.md).

- Initialisieren von SharePoint-Projektdateien mit im Assistenten gesammelten Daten mithilfe von ersetzbaren Parametern

- Erstellen einer neuen SNK-Datei in jeder neuen Projektinstanz für Websitespalten. Mit dieser Datei wird die Projektausgabe signiert, sodass die SharePoint-Projektmappenassembly im globalen Assemblycache bereitgestellt werden kann.

- Debuggen und Testen des Assistenten

> [!NOTE]
> Eine Reihe von Beispiel Workflows finden Sie unter [Beispiele für SharePoint-Workflows](/sharepoint/dev/general-development/sharepoint-workflow-samples).

## <a name="prerequisites"></a>Voraussetzungen
 Um diese exemplarische Vorgehensweise auszuführen, müssen Sie zunächst die Projekt Mappe sitecolumnprojectitem erstellen, indem Sie Exemplarische Vorgehensweise [: Erstellen eines Projekt Elements für eine Website Spalte mit einer Projektvorlage, Teil 1,](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)abschließen.

 Zum Durchführen dieser exemplarischen Vorgehensweise werden auf dem Entwicklungscomputer außerdem die folgenden Komponenten benötigt:

- Unterstützte Editionen von Windows, SharePoint und Visual Studio.

- Das Visual Studio SDK. In dieser exemplarischen Vorgehensweise wird die **VSIX-Projekt** Vorlage im SDK verwendet, um ein VSIX-Paket zum Bereitstellen des Projekt Elements zu erstellen. Weitere Informationen finden Sie unter [Erweitern der SharePoint-Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Kenntnisse der folgenden Konzepte sind hilfreich, wenn auch für die Durchführung der exemplarischen Vorgehensweise nicht erforderlich:

- Assistenten für Projekt- und Elementvorlagen in Visual Studio. Weitere Informationen finden Sie unter Gewusst [wie: Verwenden von Assistenten mit Projektvorlagen](../extensibility/how-to-use-wizards-with-project-templates.md) und der- <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> Schnittstelle.

- Websitespalten in SharePoint Weitere Informationen finden Sie unter [Spalten](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14)).

## <a name="understand-the-wizard-components"></a>Grundlegendes zu den Assistenten Komponenten
 Der Assistent, der in dieser exemplarischen Vorgehensweise veranschaulicht wird, enthält mehrere Komponenten. In der folgenden Tabelle werden diese Komponenten beschrieben.

|Komponente|BESCHREIBUNG|
|---------------|-----------------|
|Implementieren des Assistenten|Mit der `SiteColumnProjectWizard`-Klasse wird die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>-Schnittstelle implementiert. Diese Schnittstelle definiert die Methoden, die von Visual Studio aufgerufen werden, wenn der Assistent gestartet wird, wenn der Assistent beendet wird und gelegentlich, während der Assistent ausgeführt wird.|
|Benutzeroberfläche des Assistenten|Dies ist ein WPF-basiertes Fenster mit dem Namen `WizardWindow`. Dieses Fenster enthält zwei Benutzersteuerelemente: `Page1` und `Page2`. Diese Benutzersteuerelemente stellen die beiden Seiten des Assistenten dar.<br /><br /> In dieser exemplarischen Vorgehensweise wird die Benutzeroberfläche des Assistenten von der <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A>-Methode der diesbezüglichen Implementierung dargestellt.|
|Datenmodell des Assistenten|Hierbei handelt es sich um die Vermittlerklasse `SiteColumnWizardModel`, die eine Ebene zwischen der Benutzeroberfläche und der Implementierung des Assistenten bereitstellt. In diesem Beispiel wird mithilfe der Klasse eine Abstrahierung zwischen der Implementierung und der Benutzeroberfläche des Assistenten vorgenommen. Diese Klasse ist keine erforderliche Komponenten von Assistenten.<br /><br /> In dieser exemplarischen Vorgehensweise wird von der Implementierung des Assistenten beim Anzeigen der entsprechenden Benutzeroberfläche `SiteColumnWizardModel`-Objekt an das Fenster des Assistenten übergeben. Die Methoden dieses Objekts dienen der Benutzeroberfläche des Assistenten zum Speichern der Werte von Steuerelementen in der Benutzeroberfläche sowie zum Durchführen von Aufgaben wie die Validierung der eingegebenen Website-URL. Nachdem der Assistent vom Benutzer beendet wurde, wird der abschließende Zustand der Benutzeroberfläche von der Implementierung des Assistenten mit dem `SiteColumnWizardModel`-Objekt bestimmt.|
|Projektsignierungs-Manager|Mit der Hilfsklasse `ProjectSigningManager` wird von der Implementierung des Assistenten eine neue key.snk-Datei in jeder neuen Projektinstanz erstellt.|
|SharePoint-Befehle|Mit diesen Methoden werden vom Datenmodell des Assistenten während der Ausführung des Assistenten Aufrufe in die lokale SharePoint-Website durchgeführt. Da SharePoint-Befehle .NET Framework 3.5 zum Ziel haben müssen, werden diese Befehle in einer anderen Assembly als der übrige Code des Assistenten implementiert.|

## <a name="create-the-projects"></a>Erstellen der Projekte
 Um diese exemplarische Vorgehensweise durchzuführen, müssen Sie der sitecolumnprojectitem-Projekt Mappe mehrere Projekte hinzufügen, die Sie in Exemplarische Vorgehensweise [: Erstellen eines Website Spalten-Projekt Elements mit einer Projektvorlage, Teil 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md):

- Ein WPF-Projekt. In diesem Projekt implementieren Sie die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>-Schnittstelle, und Sie definieren die Assistenten-Benutzeroberfläche.

- Ein Klassenbibliotheksprojekt, mit dem die benutzerdefinierten SharePoint-Befehle definiert werden. Für dieses Projekt muss .NET Framework 3.5 als Zielversion verwendet werden.

  Beginnen Sie mit der exemplarischen Vorgehensweise, indem Sie beide Projekte erstellen.

#### <a name="to-create-the-wpf-project"></a>So erstellen Sie das WPF-Projekt

1. Öffnen Sie in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] die Projektmappe "SiteColumnProjectItem".

2. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für den **Projektmappenknoten sitecolumnprojectitem** , klicken Sie auf **Hinzufügen**, und wählen Sie dann **Neues Projekt** aus.

3. Stellen Sie oben im Dialogfeld **Neues Projekt hinzufügen** sicher, dass **.NET Framework 4,5** in der Liste der .NET Framework Versionen ausgewählt ist.

4. Erweitern Sie den Knoten **Visual c#** oder den Knoten **Visual Basic** , und wählen Sie den Knoten **Windows** aus.

5. Wählen Sie in der Liste der Projektvorlagen **WPF-Benutzer Steuerelement Bibliothek** aus, benennen Sie das Projekt **projecttemplatewizard**, und wählen Sie dann die Schaltfläche **OK** aus.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt der Projekt Mappe das Projekt **projecttemplatewizard** hinzu und öffnet die Standarddatei UserControl1. XAML.

6. Löschen Sie die Datei UserControl1.xaml aus dem Projekt.

#### <a name="to-create-the-sharepoint-commands-project"></a>So erstellen Sie das SharePoint-Befehlsprojekt

1. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für den Projektmappenknoten sitecolumnprojectitem, klicken Sie auf **Hinzufügen**, und wählen Sie dann **Neues Projekt** aus.

2. Wählen Sie oben im Dialogfeld **Neues Projekt hinzufügen** **.NET Framework 3,5** in der Liste der .NET Framework Versionen aus.

3. Erweitern Sie den Knoten **Visual c#** oder den Knoten  **Visual Basic** , und wählen Sie dann den Knoten **Windows** aus.

4. Wählen Sie die Projektvorlage **Klassenbibliothek** aus, benennen Sie das Projekt **SharePointCommands**, und klicken Sie dann auf die Schaltfläche **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt der Projekt Mappe das Projekt **SharePointCommands** hinzu und öffnet die standardmäßige Class1-Codedatei.

5. Löschen Sie die Class1-Codedatei aus dem Projekt.

## <a name="configure-the-projects"></a>Konfigurieren der Projekte
 Bevor Sie den Assistenten erstellen, müssen Sie den Projekten einige Codedateien und Assemblyverweise hinzufügen.

#### <a name="to-configure-the-wizard-project"></a>So konfigurieren Sie ein Assistentenprojekt

1. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für den Projekt Knoten **projecttemplatewizard** , und wählen Sie dann **Eigenschaften** aus.

2. Wählen Sie im **Projekt-Designer** die Registerkarte **Anwendung** für ein Visual c#-Projekt oder die Registerkarte **Kompilieren** für ein Visual Basic Projekt aus.

3. Stellen Sie sicher, dass für das Zielframework .NET Framework 4.5 und nicht .NET Framework 4.5 Client Profile festgelegt ist.

     Weitere Informationen finden Sie unter Gewusst [wie: Ausrichten auf eine Version der .NET Framework](../ide/visual-studio-multi-targeting-overview.md).

4. Öffnen Sie das Kontextmenü für das Projekt **projecttemplatewizard** , wählen Sie **Hinzufügen** aus, und wählen Sie dann **Neues Element** aus.

5. Wählen Sie das Element **Fenster (WPF)** aus, benennen Sie das Element **wizardwindow**, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.

6. Fügen Sie dem Projekt zwei **Benutzer Steuerelement (WPF)** -Elemente hinzu, und benennen Sie Sie **"Page1** und **Page2**.

7. Fügen Sie dem Projekt vier Codedateien mit den folgenden Namen hinzu:

    - SiteColumnProjectWizard

    - SiteColumnWizardModel

    - ProjectSigningManager

    - CommandIds

8. Öffnen Sie das Kontextmenü für den Projekt Knoten **projecttemplatewizard** , und wählen Sie dann **Verweis hinzufügen** aus.

9. Erweitern Sie **den Knoten** Assemblys, wählen Sie den Knoten **Erweiterungen** aus, und aktivieren Sie dann die Kontrollkästchen neben den folgenden Assemblys:

    - EnvDTE

    - Microsoft.VisualStudio.OLE.Interop

    - Microsoft.VisualStudio.SharePoint

    - Microsoft.VisualStudio.Shell.11.0

    - Microsoft.VisualStudio.Shell.Interop.10.0

    - Microsoft.VisualStudio.Shell.Interop.11.0

    - Microsoft.VisualStudio.TemplateWizardInterface

10. Wählen Sie die Schaltfläche **OK** aus, um die Assemblys dem Projekt hinzuzufügen.

11. Wählen Sie in **Projektmappen-Explorer** unter dem Ordner **Verweise** für das Projekt **projecttemplatewizard** die Option **umvdte** aus.

12. Ändern Sie im **Eigenschaften** Fenster den Wert der Eigenschaft **Interop-Typen einbetten** in **false**.

13. Wenn Sie ein Visual Basic Projekt entwickeln, importieren Sie den projecttemplatewizard-Namespace mit dem **Projekt-Designer** in Ihr Projekt.

     Weitere Informationen finden Sie unter Vorgehens [Weise: Hinzufügen oder Entfernen von importierten Namespaces &#40;Visual Basic&#41;](../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md).

#### <a name="to-configure-the-sharepointcommands-project"></a>So konfigurieren Sie das Projekt SharePointCommands

1. Wählen Sie in **Projektmappen-Explorer** den Projekt Knoten **SharePointCommands** aus.

2. Wählen Sie in der Menüleiste **Projekt** und dann  **Vorhandenes Element hinzufügen** aus.

3. Navigieren Sie im Dialogfeld **Vorhandenes Element hinzufügen** zu dem Ordner, der die Code Dateien für das Projekt projecttemplatewizard enthält, und wählen Sie dann die Codedatei **CommandIds** aus.

4. Wählen Sie den Pfeil neben der Schaltfläche **Hinzufügen** aus, und wählen Sie dann im angezeigten Menü die Option **als Link hinzufügen** aus.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] die Codedatei wird dem Projekt **SharePointCommands** als Link hinzugefügt. Die Codedatei befindet sich im Projekt " **projecttemplatewizard** ", aber der Code in der Datei wird ebenfalls im Projekt " **SharePointCommands** " kompiliert.

5. Fügen Sie im Projekt **SharePointCommands** eine weitere Codedatei mit dem Namen Befehle hinzu.

6. Wählen Sie das Projekt SharePointCommands aus, und wählen Sie dann auf der Menüleiste die Option **Projekt**  >  **Verweis hinzufügen** aus.

7. Erweitern Sie **den Knoten** Assemblys, wählen Sie den Knoten **Erweiterungen** aus, und aktivieren Sie dann die Kontrollkästchen neben den folgenden Assemblys:

    - Microsoft.SharePoint

    - Microsoft.VisualStudio.SharePoint.Commands

8. Wählen Sie die Schaltfläche **OK** aus, um die Assemblys dem Projekt hinzuzufügen.

## <a name="create-the-wizard-model-signing-manager-and-sharepoint-command-ids"></a>Erstellen der Assistenten Modell-, Signatur-Manager-und SharePoint-Befehls-IDs
 Fügen Sie dem Projekt ProjectTemplateWizard Code hinzu, um die folgenden Komponenten im Beispiel zu implementieren:

- Die SharePoint-Befehls-IDs. Durch diese Zeichenfolgen werden die vom Assistenten verwendeten SharePoint-Befehle identifiziert. Später in dieser exemplarischen Vorgehensweise fügen Sie dem Projekt SharePointCommands Code zum Implementieren der Befehle hinzu.

- Das Datenmodell des Assistenten.

- Der Signatur-Manager für Projekte.

  Weitere Informationen zu diesen Komponenten finden Sie Untergrund Legendes zu [den Komponenten des Assistenten](#understand-the-wizard-components).

#### <a name="to-define-the-sharepoint-command-ids"></a>So definieren Sie die SharePoint-Befehls-IDs

1. Öffnen Sie im Projekt "ProjectTemplateWizard" die Codedatei "CommandIds", und ersetzen Sie den gesamten Inhalt dieser Datei durch den folgenden Code.

     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/commandids.cs#5)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/commandids.vb#5)]

#### <a name="to-create-the-wizard-model"></a>So erstellen Sie das Assistentenmodell

1. Öffnen Sie die Codedatei "SiteColumnWizardModel", und ersetzen Sie den gesamten Inhalt dieser Datei durch den folgenden Code.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.vb#6)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.cs#6)]

#### <a name="to-create-the-project-signing-manager"></a>So erstellen Sie den Signatur-Manager für Projekte

1. Öffnen Sie die Codedatei "ProjectSigningManager", und ersetzen Sie dann den gesamten Inhalt dieser Datei durch den folgenden Code.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.vb#8)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.cs#8)]

## <a name="create-the-wizard-ui"></a>Erstellen der Benutzeroberfläche des Assistenten
 Fügen Sie XAML hinzu, um die Benutzeroberfläche des Fensters für den Assistenten zu definieren, sowie die beiden Benutzersteuerelemente, die die Benutzeroberfläche für die Seiten des Assistenten bereitstellen, und fügen Sie Code hinzu, um das Verhalten des Fensters und der Benutzersteuerelemente zu definieren. Der erstellte Assistent ähnelt dem integrierten Assistenten für SharePoint-Projekte in Visual Studio.

> [!NOTE]
> In den folgenden Schritten treten mehrere Compilerfehler im Projekt auf, nachdem Sie diesem XAML oder Code hinzugefügt haben. Diese Fehler werden durch Code behoben, den Sie in späteren Schritten hinzufügen.

#### <a name="to-create-the-wizard-window-ui"></a>So erstellen Sie die Benutzeroberfläche für das Fenster des Assistenten

1. Öffnen Sie im Projekt projecttemplatewizard das Kontextmenü für die Datei wizardwindow. XAML, und wählen Sie dann **Öffnen** aus, um das Fenster im Designer zu öffnen.

2. Ersetzen Sie in der XAML-Ansicht des Designers das aktuelle XAML durch das folgende XAML. Mit dem XAML wird eine Benutzeroberfläche einschließlich einer Überschrift, einem <xref:System.Windows.Controls.Grid> mit den Seiten des Assistenten sowie Navigationsschaltflächen unten im Fenster definiert.

     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#10](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml#10)]

    > [!NOTE]
    > Das Fenster, das in diesem XAML-Code erstellt wird, wird von der- <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> Basisklasse abgeleitet. Wenn Sie Visual Studio ein benutzerdefiniertes WPF-Dialogfeld hinzufügen, wird empfohlen, das Dialogfeld von dieser Klasse abzuleiten, um ein einheitliches Aussehen mit anderen Dialogfeldern von Visual Studio sicherzustellen und Probleme mit modalen Dialogfeldern zu vermeiden, die andernfalls auftreten können. Weitere Informationen finden Sie unter [Erstellen und Verwalten von modalen Dialog Feldern](../extensibility/creating-and-managing-modal-dialog-boxes.md).

3. Wenn Sie ein Visual Basic Projekt entwickeln, entfernen Sie den `ProjectTemplateWizard` Namespace aus dem `WizardWindow` Klassennamen im- `x:Class` Attribut des- `Window` Elements. Dieses Element befindet sich in der ersten XAML-Zeile. Wenn Sie fertig sind, sollte die erste Zeile wie im folgenden Beispiel aussehen.

    ```xml
    <Window x:Class="WizardWindow"
    ```

4. Öffnen Sie die CodeBehind-Datei für die Datei WizardWindow.xaml.

5. Ersetzen Sie den Inhalt dieser Datei mit Ausnahme der `using`-Deklarationen am Dateianfang durch den folgenden Code.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.vb#4)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.cs#4)]

#### <a name="to-create-the-first-wizard-page-ui"></a>So erstellen Sie die Benutzeroberfläche für die erste Seite des Assistenten

1. Öffnen Sie im Projekt projecttemplatewizard das Kontextmenü für die Datei "Page1. XAML, und wählen Sie dann **Öffnen** aus, um das Benutzer Steuerelement im Designer zu öffnen.

2. Ersetzen Sie in der XAML-Ansicht des Designers das aktuelle XAML durch das folgende XAML. Vom XAML wird eine Benutzeroberfläche mit einem Textfeld definiert, in dem Benutzer die URL der lokalen Websites eingeben können, die sie zum Debuggen verwenden möchten. Die Benutzeroberfläche weist zudem Optionsfelder auf, mit denen Benutzer angeben können, ob es sich um ein Sandkastenprojekt handelt.

     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#11](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page1.xaml#11)]

3. Wenn Sie ein Visual Basic-Projekt entwickeln, entfernen Sie den `ProjectTemplateWizard`-Namespace aus dem `Page1`-Klassennamen im `x:Class`-Attribut des `UserControl`-Elements. Dies erfolgt in der ersten Zeile des XAML. Anschließend sollte die erste Zeile wie folgt aussehen.

    ```xml
    <UserControl x:Class="Page1"
    ```

4. Ersetzen Sie den Inhalt der Datei "Page1.xaml" mit Ausnahme der `using`-Deklarationen am Dateianfang durch den folgenden Code.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.cs#2)]

#### <a name="to-create-the-second-wizard-page-ui"></a>So erstellen Sie die Benutzeroberfläche für die zweite Seite des Assistenten

1. Öffnen Sie im Projekt projecttemplatewizard das Kontextmenü für die Datei Page2. XAML, und wählen Sie dann **Öffnen** aus.

     Das Benutzersteuerelement wird im Designer geöffnet.

2. Ersetzen Sie in der XAML-Ansicht das aktuelle durch folgendes XAML. Mit dem XAML wird eine Benutzeroberfläche einschließlich einer Dropdownliste zum Auswählen des Basistyps der Websitespalte, eines Kombinationsfelds zum Angeben der integrierten oder benutzerdefinierten Gruppe, unter der die Websitespalte im Katalog angezeigt werden soll, sowie eines Textfelds zum Angeben des Namens der Websitespalte definiert.

     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#12](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page2.xaml#12)]

3. Wenn Sie ein Visual Basic-Projekt entwickeln, entfernen Sie den `ProjectTemplateWizard`-Namespace aus dem `Page2`-Klassennamen im `x:Class`-Attribut des `UserControl`-Elements. Dies erfolgt in der ersten Zeile des XAML. Anschließend sollte die erste Zeile wie folgt aussehen.

    ```xml
    <UserControl x:Class="Page2"
    ```

4. Ersetzen Sie den Inhalt der CodeBehind-Datei für die Datei "Page2.xaml" mit Ausnahme der `using`-Deklarationen am Dateianfang durch den folgenden Code.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.vb#3)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.cs#3)]

## <a name="implement-the-wizard"></a>Implementieren des Assistenten
 Definieren Sie die wichtigsten Funktionen des Assistenten, indem Sie die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>-Schnittstelle implementieren. Diese Schnittstelle definiert die Methoden, die von Visual Studio aufgerufen werden, wenn der Assistent gestartet wird, wenn der Assistent beendet wird und gelegentlich, während der Assistent ausgeführt wird.

#### <a name="to-implement-the-wizard"></a>So implementieren Sie den Assistenten

1. Öffnen Sie die Codedatei SiteColumnProjectWizard im Projekt ProjectTemplateWizard.

2. Ersetzen Sie den gesamten Inhalt der Datei durch folgenden Code:

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.cs#7)]

## <a name="create-the-sharepoint-commands"></a>Erstellen der SharePoint-Befehle
 Erstellen Sie zwei benutzerdefinierte Befehle, die einen Aufruf in das SharePoint-Serverobjektmodell durchführen. Mit einem Befehl wird angegeben, ob die Website-URL, die vom Benutzer im Assistenten eingegeben wird, gültig ist. Mit dem anderen Befehl werden alle Feldtypen von der angegebenen SharePoint-Website abgerufen, sodass Benutzer auswählen können, welcher Typ als Basis für die neue Websitespalte verwendet werden soll.

#### <a name="to-define-the-sharepoint-commands"></a>So definieren Sie die SharePoint-Befehle

1. Öffnen Sie im Projekt **SharePointCommands** die Codedatei für Befehle.

2. Ersetzen Sie den gesamten Inhalt der Datei durch folgenden Code:

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/sharepointcommands/commands.vb#9)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/sharepointcommands/commands.cs#9)]

## <a name="checkpoint"></a>Prüfpunkt
 Ab diesem Punkt in der exemplarischen Vorgehensweise wurde der gesamte für den Assistenten benötigte Code in das Projekt eingefügt. Erstellen Sie das Projekt, um sicherzustellen, dass es ohne Fehler kompiliert wird.

#### <a name="to-build-your-project"></a>So erstellen Sie das Projekt

1. Wählen Sie auf der Menüleiste **Erstellen** > **Projektmappe erstellen** aus.

## <a name="removing-the-keysnk-file-from-the-project-template"></a>Entfernen der Datei "Key. snk" aus der Projektvorlage
 In Exemplarische Vorgehensweise [: Erstellen eines Projekt Elements für eine Website Spalte mit einer Projektvorlage, Teil 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md), enthält die Projektvorlage, die Sie erstellt haben, eine Key. SNK-Datei, die zum Signieren jeder Site Column-Projekt Instanz verwendet wird. Diese key.snk-Datei wird nicht mehr benötigt, da vom Assistenten nun eine neue key.snk-Datei für jedes Projekt generiert wird. Entfernen Sie die key.snk-Datei aus der Projektvorlage, und entfernen Sie die Verweise auf die Datei.

#### <a name="to-remove-the-keysnk-file-from-the-project-template"></a>So entfernen Sie die key.snk-Datei aus der Projektvorlage

1. Öffnen Sie in **Projektmappen-Explorer** unter dem Knoten **sitecolumnprojecttemplate** das Kontextmenü für die Datei **Key. snk** , und wählen Sie dann **Löschen** aus.

2. Klicken Sie im angezeigten Bestätigungsdialogfeld auf die Schaltfläche **OK**.

3. Öffnen Sie unter dem **sitecolumnprojecttemplate** -Knoten die Datei sitecolumnprojecttemplate. vstemplate, und entfernen Sie dann das folgende-Element aus der Datei.

    ```xml
    <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>
    ```

4. Speichern und schließen Sie die Datei.

5. Öffnen Sie unter dem **sitecolumnprojecttemplate** -Knoten die Datei "ProjectTemplate. csproj" oder "ProjectTemplate. vbproj", und entfernen Sie dann das folgende- `PropertyGroup` Element aus der Datei.

    ```xml
    <PropertyGroup>
      <SignAssembly>true</SignAssembly>
      <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>
    </PropertyGroup>
    ```

6. Entfernen Sie das folgende `None`-Element:

    ```xml
    <None Include="key.snk" />
    ```

7. Speichern und schließen Sie die Datei.

## <a name="associating-the-wizard-with-the-project-template"></a>Verknüpfen des Assistenten mit der Projektvorlage
 Nachdem Sie den Assistenten implementiert haben, müssen Sie den Assistenten der Projektvorlage für **Websites Palten** zuordnen. Hierzu müssen drei Verfahren ausgeführt werden:

1. Signieren der Assistenten-Assembly mit einem starkem Namen

2. Abrufen des öffentlichen Schlüsseltokens der Assistenten-Assembly

3. Fügen Sie einen Verweis auf die Assistenten-Assembly in der VSTEMPLATE-Datei für die **Website Spalten** -Projektvorlage hinzu.

#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>So signieren Sie die Assistenten-Assembly mit einem starkem Namen

1. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für das Projekt **projecttemplatewizard** , und wählen Sie dann **Eigenschaften** aus.

2. Aktivieren Sie auf der Registerkarte **Signierung** das Kontrollkästchen **Assembly signieren**.

3. Wählen Sie in der Liste **Schlüsseldatei mit starkem Namen auswählen** die Option aus **\<New...>** .

4. Geben Sie im Dialogfeld Schlüssel für einen **starken Namen erstellen** einen Namen für die neue Schlüsseldatei ein, deaktivieren Sie das Kontrollkästchen **Schlüsseldatei mit Kennwort schützen** , und klicken Sie dann auf die Schaltfläche **OK** .

5. Öffnen Sie das Kontextmenü für das Projekt **projecttemplatewizard** , und wählen Sie dann **Erstellen** aus, um die ProjectTemplateWizard.dll-Datei zu erstellen.

#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>So rufen Sie das öffentliche Schlüsseltoken der Assistenten-Assembly ab

1. Klicken Sie im **Startmenü** auf **Alle Programme**, wählen Sie **Microsoft Visual Studio** aus, wählen Sie **Visual Studio-Tools** aus, und wählen Sie dann **Developer-Eingabeaufforderung** aus.

     Ein Visual Studio-Eingabeaufforderungsfenster wird geöffnet.

2. Führen Sie den folgenden Befehl aus, und ersetzen Sie *pathtowizardassembly* durch den vollständigen Pfad zur erstellten ProjectTemplateWizard.dll-Assembly für das Projekt projecttemplatewizard auf dem Entwicklungs Computer:

    ```cmd
    sn.exe -T PathToWizardAssembly
    ```

     Das öffentliche Schlüsseltoken für die Assembly ProjectTemplateWizard.dll wird in das Fenster der Visual Studio-Eingabeaufforderung geschrieben.

3. Lassen Sie das Fenster der Visual Studio-Eingabeaufforderung geöffnet. Sie benötigen das öffentliche Schlüsseltoken während der nächsten Prozedur.

#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>So fügen Sie einen Verweis auf die Assistenten-Assembly in der VSTEMPLATE-Datei hinzu

1. Erweitern Sie in **Projektmappen-Explorer** den Projekt Knoten **sitecolumnprojecttemplate** , und öffnen Sie die Datei sitecolumnprojecttemplate. vstemplate.

2. Fügen Sie das folgende `WizardExtension`-Element zwischen dem `</TemplateContent>`-Tag und dem `</VSTemplate>`-Tag am Ende der Datei hinzu. Ersetzen Sie den *Tokenwert* des- `PublicKeyToken` Attributs durch das öffentliche Schlüssel Token, das Sie im vorherigen Verfahren abgerufen haben.

    ```xml
    <WizardExtension>
      <Assembly>ProjectTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=your token</Assembly>
      <FullClassName>ProjectTemplateWizard.SiteColumnProjectWizard</FullClassName>
    </WizardExtension>
    ```

     Weitere Informationen zum- `WizardExtension` Element finden Sie unter [WizardExtension-Element &#40;Visual Studio-Vorlagen&#41;](../extensibility/wizardextension-element-visual-studio-templates.md).

3. Speichern und schließen Sie die Datei.

## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-project-template"></a>Hinzufügen von austauschbaren Parametern zur Elements.xml Datei in der Projektvorlage
 Fügen Sie der *Elements.xml* Datei im sitecolumnprojecttemplate-Projekt mehrere ersetzbare Parameter hinzu. Diese Parameter werden in der `RunStarted`-Methode in der zuvor definierten `SiteColumnProjectWizard`-Klasse initialisiert. Wenn ein Benutzer ein Website Spalten Projekt erstellt, ersetzt Visual Studio diese Parameter automatisch in der *Elements.xml* -Datei im neuen Projekt durch die Werte, die Sie im Assistenten angegeben haben.

 Ein ersetzbarer Parameter ist ein Token, das mit einem Dollarzeichen ($) beginnt und endet. Zusätzlich zu den selbst definierten ersetzbaren Parametern können Sie auch integrierte Parameter verwenden, die vom SharePoint-Projektsystem definiert und initialisiert werden. Weitere Informationen finden Sie unter [Ersetzbare Parameter](../sharepoint/replaceable-parameters.md).

#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>So fügen Sie der Datei Elements.xml ersetzbare Parameter hinzu

1. Ersetzen Sie im sitecolumnprojecttemplate-Projekt den Inhalt der *Elements.xml* -Datei durch den folgenden XML-Code.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">
      <Field ID="{$guid5$}"
             Name="$fieldname$"
             DisplayName="$fieldname$"
             Type="$selectedfieldtype$"
             Group="$selectedgrouptype$">
      </Field>
    </Elements>
    ```

     Durch das neue XML werden die Werte der Attribute `Name`, `DisplayName`, `Type` und `Group` in benutzerdefinierte ersetzbare Parameter geändert.

2. Speichern und schließen Sie die Datei.

## <a name="add-the-wizard-to-the-vsix-package"></a>Hinzufügen des Assistenten zum VSIX-Paket
 Um den Assistenten mit dem VSIX-Paket und der Projektvorlage für Websitespalten bereitzustellen, fügen Sie der Datei source.extension.vsixmanifest im VSIX-Projekt Verweise auf das Assistentenprojekt und das SharePoint-Befehlsprojekt hinzu.

#### <a name="to-add-the-wizard-to-the-vsix-package"></a>So fügen Sie den Assistenten dem VSIX-Paket hinzu

1. Öffnen Sie in **Projektmappen-Explorer** im Projekt **sitecolumnprojectitem** das Kontextmenü für die Datei " **Source. Extension. vsixmanifest** ", und wählen Sie dann **Öffnen** aus.

     Die Datei wird von Visual Studio im Manifest-Editor geöffnet.

2. Wählen Sie im Editor auf der Registerkarte **Objekte** die Schaltfläche **neu** aus.

     Das Dialogfeld **Neues Objekt hinzufügen** wird geöffnet.

3. Wählen Sie in der Liste **Typ** den Eintrag **Microsoft. VisualStudio. Assembly** aus.

4. Wählen Sie  in der Liste Quelle **ein Projekt in der aktuellen Projekt** Mappe aus.

5. Wählen Sie in der Liste **Projekt** die Option **projecttemplatewizard** aus, und klicken Sie dann auf die Schaltfläche **OK** .

6. Wählen Sie auf der Registerkarte **Objekte** des Editors erneut die Schaltfläche **neu** aus.

     Das Dialogfeld **Neues Objekt hinzufügen** wird geöffnet.

7. Geben Sie in der Liste **Typ** den Namen **SharePoint. Commands. v4** ein.

8. Wählen Sie  in der Liste Quelle **ein Projekt in der aktuellen Projekt** Mappe aus.

9. Wählen Sie in der Liste **Projekt** das Projekt **SharePointCommands** aus, und klicken Sie dann auf die Schaltfläche **OK** .

10. Wählen Sie in der Menüleiste Buildprojektmappe **Erstellen** aus, und vergewissern Sie sich,  >  dass die Projekt Mappe ohne Fehler erstellt wird.

## <a name="test-the-wizard"></a>Testen des Assistenten
 Sie können den Assistenten jetzt testen. Debuggen Sie die Projektmappe SiteColumnProjectItem zunächst in der experimentellen Instanz von Visual Studio. Anschließend testen Sie den Assistenten für das Websitespaltenprojekt in der experimentellen Instanz von Visual Studio. Erstellen und führen Sie zum Schluss das Projekt aus, um sicherzustellen, dass die Websitespalte ordnungsgemäß funktioniert.

#### <a name="to-start-debugging-the-solution"></a>So debuggen Sie die Projektmappe

1. Starten Sie Visual Studio erneut mit Administratoranmeldeinformationen, und öffnen Sie dann die Projektmappe "SiteColumnProjectItem".

2. Öffnen Sie im Projekt "ProjectTemplateWizard" die Codedatei "SiteColumnProjectWizard", und fügen Sie dann der ersten Codezeile in der `RunStarted`-Methode einen Haltepunkt hinzu.

3. Wählen Sie in der Menüleiste **debugausnahmen** aus  >  .

4. Stellen Sie im Dialogfeld **Ausnahmen** sicher, dass die Kontrollkästchen ausgelöste **und** **Benutzer unbehandelt** für **Common Language Runtime-Ausnahmen** deaktiviert sind, und klicken Sie dann auf die Schaltfläche **OK** .

5. Starten Sie das Debugging, indem Sie die **F5** -Taste drücken oder in der Menüleiste **Debuggen**  >  **Debuggen starten** auswählen.

     Die Erweiterung wird unter "%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Websitespalte\1.0 installiert", und eine experimentelle Instanz von Visual Studio wird gestartet. Sie testen das Projektelement in dieser Instanz von Visual Studio.

#### <a name="to-test-the-wizard-in-visual-studio"></a>So testen Sie den Assistenten in Visual Studio

1. Wählen Sie in der experimentellen Instanz von Visual Studio in der Menüleiste **Datei**  >  **neu**  >  **Projekt** aus.

2. Erweitern Sie den **Visual c#** -Knoten oder den **Visual Basic** -Knoten (je nach der von der Projektvorlage unterstützten Sprache), erweitern Sie den **SharePoint** -Knoten, und wählen Sie dann den Knoten **2010** aus.

3. Wählen Sie in der Liste der Projektvorlagen die Option **Website Spalte** aus, benennen Sie das Projekt **sitecolumnwizardtest**, und klicken Sie dann auf die Schaltfläche **OK** .

4. Überprüfen Sie, ob die Codeausführung in der anderen Instanz von Visual Studio an dem Haltepunkt unterbrochen wird, den Sie zuvor in der `RunStarted`-Methode festgelegt haben.

5. Fahren Sie mit dem Debuggen des Projekts fort, indem Sie die **F5** -Taste drücken oder in der Menüleiste **Debuggen**  >  **fortfahren** auswählen

6. Geben Sie im Assistenten zum Anpassen von **SharePoint** die URL der Website ein, die Sie zum Debuggen verwenden möchten, und klicken Sie dann auf die Schaltfläche **weiter** .

7. Treffen Sie auf der zweiten Seite des Assistenten zum Anpassen von **SharePoint** die folgenden Optionen:

   - Wählen Sie in der Liste **Typ** die Option **Boolesch** aus.

   - Wählen Sie in der Liste **Gruppe** die Option **benutzerdefinierte Ja/Nein-Spalten** aus.

   - Geben Sie im Feld **Name** die **Spalte meine Yes/No-Spalte** ein, und wählen Sie dann die Schaltfläche **Fertig** stellen aus.

     In **Projektmappen-Explorer** wird ein neues Projekt angezeigt, das ein Projekt Element mit dem Namen **field1** enthält, und Visual Studio öffnet die *Elements.xml* -Datei des Projekts im Editor.

8. Vergewissern Sie sich, dass *Elements.xml* die Werte enthält, die Sie im Assistenten angegeben haben.

#### <a name="to-test-the-site-column-in-sharepoint"></a>So testen Sie die Websitespalte in SharePoint

1. Wählen Sie in der experimentellen Instanz von Visual Studio die Taste **F5** .

     Die Spalte Site wird verpackt und auf der SharePoint-Website bereitgestellt, die von der **Website-URL** -Eigenschaft des Projekts angegeben wird. Im Webbrowser wird die Standardseite dieser Website geöffnet.

    > [!NOTE]
    > Wenn das Dialogfeld **Skript Debugging deaktiviert** angezeigt wird, klicken Sie auf die Schaltfläche **Ja** , um das Debuggen des Projekts fortzusetzen.

2. Wählen Sie im Menü **Website Aktionen** die Option **Website Einstellungen** aus.

3. Wählen Sie auf der Seite Site Einstellungen **unter Kataloge** den Link **Site Spalten** aus.

4. Überprüfen Sie in der Liste der Website Spalten, ob eine **benutzerdefinierte Gruppe Ja/Nein-Spalten** eine Spalte mit dem Namen **meine Ja/Nein-Spalte** enthält, und schließen Sie dann den Webbrowser.

## <a name="clean-up-the-development-computer"></a>Bereinigen des Entwicklungs Computers
 Nachdem Sie die Tests des Projektelements abgeschlossen haben, entfernen Sie die Projektvorlage aus der experimentellen Instanz von Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>So bereinigen Sie den Entwicklungscomputer

1. Wählen Sie in der experimentellen Instanz von Visual Studio auf der Menüleiste Extras   >  **Erweiterungen und Updates** aus.

     Das Dialogfeld **Erweiterungen und Updates** wird geöffnet.

2. Wählen Sie in der Liste der Erweiterungen **Website Spalte** aus, und klicken Sie dann auf die Schaltfläche **deinstallieren** .

3. Wählen Sie im angezeigten Dialogfeld die Schaltfläche **Ja** , um zu bestätigen, dass Sie die Erweiterung deinstallieren möchten, und wählen Sie dann die Schaltfläche **jetzt neu starten** aus, um die Deinstallation abzuschließen.

4. Schließen Sie die experimentelle Instanz von Visual Studio und die Instanz, in der die Projektmappe "CustomActionProjectItem" geöffnet ist.

     Weitere Informationen zum Bereitstellen von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Erweiterungen finden Sie unter [Versand von Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md).

## <a name="see-also"></a>Weitere Informationen
- [Exemplarische Vorgehensweise: Erstellen eines Projekt Elements für eine Website Spalte mit einer Projektvorlage, Teil 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Definieren von benutzerdefinierten SharePoint-Projekt Elementtypen](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Erstellen von Elementvorlagen und Projektvorlagen für SharePoint-Projektelemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Schema Referenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
- [Gewusst wie: Verwenden von Assistenten mit Projektvorlagen](../extensibility/how-to-use-wizards-with-project-templates.md)
