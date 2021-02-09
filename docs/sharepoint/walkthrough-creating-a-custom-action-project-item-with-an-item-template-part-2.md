---
title: Erstellen eines benutzerdefinierten Aktionsprojekt Elements mit Element Vorlage, Teil 2
titleSuffix: ''
description: Fügen Sie in dieser exemplarischen Vorgehensweise einen Assistenten zum Sammeln von Informationen von Benutzern hinzu, wenn Sie eine Element Vorlage zum Hinzufügen eines benutzerdefinierten Aktionsprojekt Elements auf einer SharePoint-Website verwenden.
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
ms.openlocfilehash: bc1474d1c7aeabb9b3e9ecbbe6b42931d44c59c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839089"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-2"></a>Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Aktionsprojekt Elements mit einer Element Vorlage, Teil 2
  Nachdem Sie einen benutzerdefinierten Typ von SharePoint-Projekt Element definiert und einer Element Vorlage in Visual Studio zugeordnet haben, möchten Sie möglicherweise auch einen Assistenten für die Vorlage bereitstellen. Sie können den Assistenten verwenden, um Informationen von Benutzern zu sammeln, wenn Sie die Vorlage verwenden, um einem Projekt eine neue Instanz des Projekt Elements hinzuzufügen. Mit den gesammelten Informationen kann das Projektelement initialisiert werden.

 In dieser exemplarischen Vorgehensweise fügen Sie dem Projekt Element für benutzerdefinierte Aktionen einen Assistenten hinzu, der in Exemplarische [Vorgehensweise: Erstellen eines benutzerdefinierten Aktionsprojekt Elements mit einer Element Vorlage, Teil 1,](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)veranschaulicht wird. Wenn ein Benutzer ein benutzerdefiniertes Aktionsprojekt Element einem SharePoint-Projekt hinzufügt, sammelt der Assistent Informationen über die benutzerdefinierte Aktion (z. b. den Speicherort und die URL, zu der navigiert werden soll, wenn ein Endbenutzer diese auswählt) und fügt diese Informationen der *Elements.xml* -Datei im neuen Projekt Element hinzu.

 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:

- Erstellen eines Assistenten für einen benutzerdefinierten SharePoint-Projekt Elementtyp, der mit einer Element Vorlage verknüpft ist.

- Definieren einer benutzerdefinierten Assistenten-Benutzeroberfläche, die den integrierten Assistenten für SharePoint-Projekt Elemente in Visual Studio ähnelt.

- Initialisieren von SharePoint-Projektdateien mit im Assistenten gesammelten Daten mithilfe von ersetzbaren Parametern

- Debuggen und Testen des Assistenten

> [!NOTE]
> Sie können ein Beispiel von [GitHub](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) herunterladen, das zeigt, wie benutzerdefinierte Aktivitäten für einen Workflow erstellt werden.

## <a name="prerequisites"></a>Voraussetzungen
 Um diese exemplarische Vorgehensweise auszuführen, müssen Sie zuerst die Projekt Mappe "CustomAction ProjectItem" erstellen, indem Sie Exemplarische [Vorgehensweise: Erstellen eines benutzerdefinierten Aktionsprojekt Elements mit einer Element Vorlage, Teil 1,](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)abschließen.

 Zum Durchführen dieser exemplarischen Vorgehensweise werden auf dem Entwicklungscomputer außerdem die folgenden Komponenten benötigt:

- Unterstützte Editionen von Windows, SharePoint und Visual Studio.

- Das Visual Studio SDK. In dieser exemplarischen Vorgehensweise wird die **VSIX-Projekt** Vorlage im SDK verwendet, um ein VSIX-Paket zum Bereitstellen des Projekt Elements zu erstellen. Weitere Informationen finden Sie unter [Erweitern der SharePoint-Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Kenntnisse der folgenden Konzepte sind hilfreich, wenn auch für die Durchführung der exemplarischen Vorgehensweise nicht erforderlich:

- Assistenten für Projekt- und Elementvorlagen in Visual Studio. Weitere Informationen finden Sie unter Gewusst [wie: Verwenden von Assistenten mit Projektvorlagen](../extensibility/how-to-use-wizards-with-project-templates.md) und der- <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> Schnittstelle.

- Benutzerdefinierte Aktionen in SharePoint. Weitere Informationen finden Sie unter [Custom Action](/previous-versions/office/developer/sharepoint-2010/ms458635(v=office.14)).

## <a name="create-the-wizard-project"></a>Erstellen des Assistenten Projekts
 Um diese exemplarische Vorgehensweise durchzuführen, müssen Sie der Projekt Mappe CustomAction ProjectItem ein Projekt hinzufügen, das Sie in Exemplarische [Vorgehensweise: Erstellen eines benutzerdefinierten Aktionsprojekt Elements mit einer Element Vorlage, Teil 1, erstellt haben](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md). In diesem Projekt implementieren Sie die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>-Schnittstelle, und Sie definieren die Assistenten-Benutzeroberfläche.

#### <a name="to-create-the-wizard-project"></a>So erstellen Sie das Assistenten Projekt

1. Öffnen Sie in Visual Studio die Projekt Mappe "customaktionprojectitem".

2. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für den Projektmappenknoten, wählen Sie **Hinzufügen** aus, und wählen Sie dann **Neues Projekt** aus.

3. Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Visual c#** oder **Visual Basic** , und wählen Sie dann den Knoten **Windows** aus.

4. Stellen Sie oben im Dialogfeld **Neues Projekt** sicher, dass **.NET Framework 4,5** in der Liste der .NET Framework Versionen ausgewählt ist.

5. Wählen Sie die Projektvorlage **WPF-Benutzer Steuerelement Bibliothek** aus, benennen Sie das Projekt **itemtemplatewizard**, und wählen Sie dann die Schaltfläche **OK** aus.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt der Projekt **Mappe das itemtemplatewizard** -Projekt hinzu.

6. Löschen Sie das UserControl1-Element aus dem Projekt.

## <a name="configure-the-wizard-project"></a>Konfigurieren des Assistenten Projekts
 Bevor Sie den Assistenten erstellen, müssen Sie dem Projekt ein Windows Presentation Foundation Fenster (WPF), eine Codedatei und Assemblyverweise hinzufügen.

#### <a name="to-configure-the-wizard-project"></a>So konfigurieren Sie ein Assistentenprojekt

1. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü im Projekt Knoten **itemtemplatewizard** , und wählen Sie dann **Eigenschaften** aus.

2. Vergewissern Sie sich, dass das Ziel Framework im **Projekt-Designer** auf .NET Framework 4,5 festgelegt ist.

     Für Visual c#-Projekte können Sie diesen Wert auf der Registerkarte **Anwendung** festlegen. Für Visual Basic Projekte können Sie diesen Wert auf der Registerkarte **Kompilieren** festlegen. Weitere Informationen finden Sie unter Gewusst [wie: Ausrichten auf eine Version der .NET Framework](../ide/visual-studio-multi-targeting-overview.md).

3. Fügen Sie im Projekt **itemtemplatewizard** dem Projekt ein **Fenster (WPF)** -Element hinzu, und benennen Sie das Element **wizardwindow**.

4. Fügen Sie zwei Code Dateien mit dem Namen "customaktionwizard" und "Strings" hinzu.

5. Öffnen Sie das Kontextmenü für das Projekt **itemtemplatewizard** , und wählen Sie dann **Verweis hinzufügen** aus.

6. Wählen Sie im Dialogfeld **Verweis-Manager-itemtemplatewizard** unter **dem Knoten** Assemblys den Knoten **Erweiterungen** aus.

7. Aktivieren Sie die Kontrollkästchen neben den folgenden Assemblys, und wählen Sie dann die Schaltfläche **OK** aus:

    - EnvDTE

    - Microsoft.VisualStudio.Shell.11.0

    - Microsoft.VisualStudio.TemplateWizardInterface

8. Wählen Sie in **Projektmappen-Explorer** im Ordner **Verweise** für das Projekt itemtemplatewizard den Verweis **svdte** aus.

9. Ändern Sie im **Eigenschaften** Fenster den Wert der Eigenschaft **Interop-Typen einbetten** in **false**.

## <a name="define-the-default-location-and-id-strings-for-custom-actions"></a>Definieren des Standard Speicher Orts und der ID-Zeichen folgen für benutzerdefinierte Aktionen
 Jede benutzerdefinierte Aktion verfügt über einen Speicherort und eine ID, der im `GroupID` -Attribut und im- `Location` Attribut des- `CustomAction` Elements in der *Elements.xml* -Datei angegeben ist. In diesem Schritt definieren Sie einige der gültigen Zeichen folgen für diese Attribute im itemtemplatewizard-Projekt. Wenn Sie diese exemplarische Vorgehensweise durcharbeiten, werden diese Zeichen folgen in die *Elements.xml* -Datei im Projekt Element für benutzerdefinierte Aktionen geschrieben, wenn Benutzer einen Speicherort und eine ID im Assistenten angeben.

 Der Einfachheit halber wird in diesem Beispiel nur eine Teilmenge der verfügbaren Standard Speicherorte und IDs unterstützt. Eine vollständige Liste finden Sie unter [standardmäßige benutzerdefinierte Aktions Orte und IDs](/previous-versions/office/developer/sharepoint-2010/bb802730(v=office.14)).

#### <a name="to-define-the-default-location-and-id-strings"></a>So definieren Sie den Standard Speicherort und ID-Zeichen folgen

1. eren.

2. Ersetzen Sie im Projekt **itemtemplatewizard** den Code in der Zeichen folgen-Codedatei durch den folgenden Code.

     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/strings.cs#6)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/strings.vb#6)]

## <a name="create-the-wizard-ui"></a>Erstellen der Benutzeroberfläche des Assistenten
 Fügen Sie XAML hinzu, um die Benutzeroberfläche des Assistenten zu definieren, und fügen Sie Code hinzu, um einige der Steuerelemente im Assistenten an die ID-Zeichen folgen zu binden. Der erstellte Assistent ähnelt dem integrierten Assistenten für SharePoint-Projekte in Visual Studio.

#### <a name="to-create-the-wizard-ui"></a>So erstellen Sie die Benutzeroberfläche des Assistenten

1. Öffnen Sie im Projekt **itemtemplatewizard** das Kontextmenü für die Datei **wizardwindow. XAML** , und wählen Sie dann **Öffnen** aus, um das Fenster im Designer zu öffnen.

2. Ersetzen Sie in der XAML-Ansicht das aktuelle durch folgendes XAML. Der XAML-Code definiert eine Benutzeroberfläche, die eine Überschrift, Steuerelemente zum Angeben des Verhaltens der benutzerdefinierten Aktion und Navigations Schaltflächen am unteren Rand des Fensters enthält.

    > [!NOTE]
    > Das Projekt enthält einige Kompilierungsfehler, nachdem Sie diesen Code hinzugefügt haben. Diese Fehler werden durch Code behoben, den Sie in späteren Schritten hinzufügen.

     [!code-xml[SPExtensibility.ProjectItem.CustomAction#9](../sharepoint/codesnippet/Xaml/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml#9)]

    > [!NOTE]
    > Das Fenster, das in diesem XAML-Code erstellt wird, wird von der- <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> Basisklasse abgeleitet. Wenn Sie Visual Studio ein benutzerdefiniertes WPF-Dialogfeld hinzufügen, wird empfohlen, dass Sie das Dialogfeld von dieser Klasse ableiten, um das konsistente formatieren mit anderen Dialogfeldern in Visual Studio zu erhalten und Probleme zu vermeiden, die andernfalls bei modalen Dialogfeldern auftreten können. Weitere Informationen finden Sie unter [Erstellen und Verwalten von modalen Dialog Feldern](../extensibility/creating-and-managing-modal-dialog-boxes.md).

3. Wenn Sie ein Visual Basic Projekt entwickeln, entfernen Sie den `ItemTemplateWizard` Namespace aus dem `WizardWindow` Klassennamen im- `x:Class` Attribut des- `Window` Elements. Dieses Element befindet sich in der ersten XAML-Zeile. Wenn Sie fertig sind, sollte die erste Zeile dem folgenden Code ähneln:

    ```xml
    <Window x:Class="WizardWindow"
    ```

4. Ersetzen Sie den aktuellen Code in der Code Behind-Datei für die Datei wizardwindow. XAML durch den folgenden Code.

     [!code-vb[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.cs#7)]

## <a name="implement-the-wizard"></a>Implementieren des Assistenten
 Definieren Sie die Funktionalität des Assistenten, indem Sie die- <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> Schnittstelle implementieren.

#### <a name="to-implement-the-wizard"></a>So implementieren Sie den Assistenten

1. Öffnen Sie im Projekt " **itemtemplatewizard** " die Codedatei " **customaktionwizard** ", und ersetzen Sie dann den aktuellen Code in dieser Datei durch den folgenden Code:

     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/customactionwizard.cs#8)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/customactionwizard.vb#8)]

## <a name="checkpoint"></a>Prüfpunkt
 Ab diesem Punkt in der exemplarischen Vorgehensweise wurde der gesamte für den Assistenten benötigte Code in das Projekt eingefügt. Erstellen Sie das Projekt, um sicherzustellen, dass es ohne Fehler kompiliert wird.

#### <a name="to-build-your-project"></a>So erstellen Sie das Projekt

1. Wählen Sie auf der Menüleiste **Erstellen** > **Projektmappe erstellen** aus.

## <a name="associate-the-wizard-with-the-item-template"></a>Ordnen Sie den Assistenten der Element Vorlage zu.
 Nachdem Sie den Assistenten implementiert haben, müssen Sie ihn der **benutzerdefinierten Aktions** Element Vorlage zuordnen, indem Sie drei Hauptschritte ausführen:

1. Signieren der Assistenten-Assembly mit einem starkem Namen

2. Abrufen des öffentlichen Schlüsseltokens der Assistenten-Assembly

3. Fügen Sie einen Verweis auf die Assistenten-Assembly in der VSTEMPLATE-Datei für die **benutzerdefinierte Aktions** Element Vorlage hinzu.

#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>So signieren Sie die Assistenten-Assembly mit einem starkem Namen

1. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü im Projekt Knoten **itemtemplatewizard** , und wählen Sie dann **Eigenschaften** aus.

2. Aktivieren Sie auf der Registerkarte **Signierung** das Kontrollkästchen **Assembly signieren**.

3. Wählen Sie in der Liste **Schlüsseldatei mit starkem Namen auswählen** die Option aus **\<New...>** .

4. Geben Sie im Dialogfeld Schlüssel für einen **starken Namen erstellen** einen Namen ein, deaktivieren Sie das Kontrollkästchen **Schlüsseldatei mit Kennwort schützen** , und klicken Sie dann auf die Schaltfläche **OK** .

5. Wählen Sie auf der Menüleiste **Erstellen** > **Projektmappe erstellen** aus.

#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>So rufen Sie das öffentliche Schlüsseltoken der Assistenten-Assembly ab

1. Führen Sie in einem Visual Studio-Eingabe Aufforderungs Fenster den folgenden Befehl aus, und ersetzen Sie *pathtowizardassembly* durch den vollständigen Pfad zur erstellten ItemTemplateWizard.dll-Assembly für das itemtemplatewizard-Projekt auf Ihrem Entwicklungs Computer.

    ```xml
    sn.exe -T PathToWizardAssembly
    ```

     Das öffentliche Schlüssel Token für die *ItemTemplateWizard.dll* -Assembly wird in das Visual Studio-Eingabe Aufforderungs Fenster geschrieben.

2. Lassen Sie das Fenster der Visual Studio-Eingabeaufforderung geöffnet. Sie benötigen das öffentliche Schlüssel Token, um das nächste Verfahren abzuschließen.

#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>So fügen Sie einen Verweis auf die Assistenten-Assembly in der VSTEMPLATE-Datei hinzu

1. Erweitern Sie in **Projektmappen-Explorer** den Projekt Knoten **ItemTemplate** , und öffnen Sie dann die Datei *ItemTemplate. vstemplate* .

2. Fügen Sie das folgende `WizardExtension`-Element zwischen dem `</TemplateContent>`-Tag und dem `</VSTemplate>`-Tag am Ende der Datei hinzu. Ersetzen Sie den *yourtoken* -Wert des- `PublicKeyToken` Attributs durch das öffentliche Schlüssel Token, das Sie im vorherigen Verfahren abgerufen haben.

    ```xml
    <WizardExtension>
      <Assembly>ItemTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=YourToken</Assembly>
      <FullClassName>ItemTemplateWizard.CustomActionWizard</FullClassName>
    </WizardExtension>
    ```

     Weitere Informationen zum- `WizardExtension` Element finden Sie unter [WizardExtension-Element &#40;Visual Studio-Vorlagen&#41;](../extensibility/wizardextension-element-visual-studio-templates.md).

3. Speichern und schließen Sie die Datei.

## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-item-template"></a>Hinzufügen von austauschbaren Parametern zur *Elements.xml* Datei in der Element Vorlage
 Fügen Sie der *Elements.xml* -Datei im Projekt "ItemTemplate" mehrere austauschbare Parameter hinzu. Diese Parameter werden in der `PopulateReplacementDictionary`-Methode in der zuvor definierten `CustomActionWizard`-Klasse initialisiert. Wenn ein Benutzer ein benutzerdefiniertes Aktionsprojekt Element einem Projekt hinzufügt, ersetzt Visual Studio diese Parameter automatisch in der *Elements.xml* -Datei im neuen Projekt Element durch die Werte, die Sie im Assistenten angegeben haben.

 Ein ersetzbarer Parameter ist ein Token, das mit einem Dollarzeichen ($) beginnt und endet. Zusätzlich zum Definieren der eigenen ersetzbaren Parameter können Sie integrierte Parameter verwenden, die vom SharePoint-Projekt System definiert und initialisiert werden. Weitere Informationen finden Sie unter [Ersetzbare Parameter](../sharepoint/replaceable-parameters.md).

#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>So fügen Sie dem *Elements.xml* Dateiaustausch Bare Parameter hinzu

1. Ersetzen Sie im Projekt ItemTemplate den Inhalt der *Elements.xml* -Datei durch den folgenden XML-Code.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">
      <CustomAction Id="$IdValue$"
                    GroupId="$GroupIdValue$"
                    Location="$LocationValue$"
                    Sequence="1000"
                    Title="$TitleValue$"
                    Description="$DescriptionValue$" >
        <UrlAction Url="$UrlValue$"/>
      </CustomAction>
    </Elements>
    ```

     Der neue XML-Code ändert die Werte `Id` der `GroupId` Attribute,,, `Location` `Description` und `Url` in ersetzbare Parameter.

2. Speichern und schließen Sie die Datei.

## <a name="add-the-wizard-to-the-vsix-package"></a>Hinzufügen des Assistenten zum VSIX-Paket
 Fügen Sie in der Datei "Source. Extension. vsixmanifest" im VSIX-Projekt einen Verweis auf das Assistenten Projekt hinzu, sodass er mit dem VSIX-Paket bereitgestellt wird, das das Projekt Element enthält.

#### <a name="to-add-the-wizard-to-the-vsix-package"></a>So fügen Sie den Assistenten dem VSIX-Paket hinzu

1. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü aus der Datei " **Source. Extension. vsixmanifest** " im Projekt "customaktionprojectitem", und wählen Sie dann **Öffnen** aus, um die Datei im Manifest-Editor zu öffnen.

2. Wählen Sie im Manifest-Editor die Registerkarte **Assets** aus, und klicken Sie dann auf die Schaltfläche **neu** .

     Das Dialogfeld **Neues Objekt hinzufügen** wird angezeigt.

3. Wählen Sie in der Liste **Typ** den Eintrag **Microsoft. VisualStudio. Assembly** aus.

4. Wählen Sie  in der Liste Quelle **ein Projekt in der aktuellen Projekt** Mappe aus.

5. Wählen Sie in der Liste **Projekt** die Option **itemtemplatewizard** aus, und klicken Sie dann auf die Schaltfläche **OK** .

6. Wählen Sie in der Menüleiste Buildprojektmappe **Erstellen** aus, und vergewissern Sie sich,  >  dass die Projekt Mappe ohne Fehler kompiliert wird.

## <a name="test-the-wizard"></a>Testen des Assistenten
 Sie können den Assistenten jetzt testen. Beginnen Sie zunächst mit dem Debuggen der Projekt Mappe "customaktionprojectitem" in der experimentellen Instanz von Visual Studio. Testen Sie dann den Assistenten für das Projekt Element benutzerdefinierte Aktion in einem SharePoint-Projekt in der experimentellen Instanz von Visual Studio. Erstellen und führen Sie zum Schluss das SharePoint-Projekt aus, um sicherzustellen, dass die benutzerdefinierte Aktion ordnungsgemäß funktioniert.

#### <a name="to-start-to-debug-the-solution"></a>So starten Sie das Debuggen der Projekt Mappe

1. Starten Sie Visual Studio erneut mit Administratoranmeldeinformationen, und öffnen Sie dann die Projektmappe "CustomActionProjectItem".

2. Öffnen Sie im Projekt "itemtemplatewizard" die Codedatei "customaktionwizard", und fügen Sie der ersten Codezeile in der-Methode einen Haltepunkt hinzu `RunStarted` .

3. Wählen Sie in der Menüleiste **debugausnahmen** aus  >  .

4. Stellen Sie im Dialogfeld **Ausnahmen** sicher, dass die Kontrollkästchen ausgelöste **und** **Benutzer unbehandelt** für **Common Language Runtime-Ausnahmen** deaktiviert sind, und klicken Sie dann auf die Schaltfläche **OK** .

5. Starten Sie das Debugging, indem Sie die Taste **F5** drücken, oder wählen Sie in der Menüleiste **Debuggen**  >  **Debuggen starten** aus.

     Visual Studio installiert die Erweiterung in%USERPROFILE%\appdata\local\microsoft\visualstudio\11.0exp\extensions\condeso\custom Action Project Item\1.0 und startet eine experimentelle Instanz von Visual Studio. Sie testen das Projektelement in dieser Instanz von Visual Studio.

#### <a name="to-test-the-wizard-in-visual-studio"></a>So testen Sie den Assistenten in Visual Studio

1. Wählen Sie in der experimentellen Instanz von Visual Studio in der Menüleiste **Datei**  >  **neu**  >  **Projekt** aus.

2. Erweitern Sie den Knoten **Visual c#** oder **Visual Basic** (abhängig von der von der Element Vorlage unterstützten Sprache), erweitern Sie den Knoten **SharePoint** , und wählen Sie dann den Knoten **2010** aus.

3. Wählen Sie in der Liste der Projektvorlagen **SharePoint 2010-Projekt** aus, nennen Sie das Projekt **customaktionwizardtest**, und klicken Sie dann auf die Schaltfläche **OK** .

4. Geben Sie im Assistenten zum Anpassen von **SharePoint** die URL der Website ein, die Sie zum Debuggen verwenden möchten, und wählen Sie dann die Schaltfläche **Fertig** stellen aus.

5. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für den Projekt Knoten, wählen Sie **Hinzufügen** aus, und wählen Sie dann **Neues Element** aus.

6. Erweitern Sie im Dialogfeld **Neues Element hinzufügen-customitemwizardtest** den Knoten **SharePoint** , und erweitern Sie dann den Knoten **2010** .

7. Wählen Sie in der Liste der Projekt Elemente das Element **benutzerdefinierte Aktion** aus, und klicken Sie dann auf die Schaltfläche **Hinzufügen** .

8. Überprüfen Sie, ob die Codeausführung in der anderen Instanz von Visual Studio an dem Haltepunkt unterbrochen wird, den Sie zuvor in der `RunStarted`-Methode festgelegt haben.

9. Fahren Sie mit dem Debuggen des Projekts fort, indem Sie die **F5** -Taste drücken oder in der Menüleiste **Debuggen**  >  **fortfahren** auswählen

     Der Assistent zum Anpassen von SharePoint wird angezeigt.

10. Klicken Sie unter **Speicherort** auf das Optionsfeld **Liste bearbeiten** .

11. Wählen Sie in der Liste **Gruppen-ID** die Option **Kommunikation** aus.

12. Geben Sie im Feld **Titel** den Namen **SharePoint Developer Center** ein.

13. Geben Sie im Feld  **Beschreibung** **die SharePoint Developer Center-Website** ein.

14. Geben Sie im Feld **URL** ein **https://docs.microsoft.com/sharepoint/dev/** , und wählen Sie dann die Schaltfläche **Fertig** stellen aus.

     Visual Studio fügt dem Projekt ein Element mit dem Namen **CustomAction1** hinzu und öffnet die Datei *Elements.xml* im Editor. Vergewissern Sie sich, dass *Elements.xml* die Werte enthält, die Sie im Assistenten angegeben haben.

#### <a name="to-test-the-custom-action-in-sharepoint"></a>So testen Sie die benutzerdefinierte Aktion in SharePoint

1. Wählen Sie in der experimentellen Instanz von Visual Studio die **F5** -Taste, oder wählen Sie in der Menüleiste **Debuggen**  >  **Debuggen starten** aus.

     Die benutzerdefinierte Aktion wird verpackt und auf der SharePoint-Website bereitgestellt, die von der **Website-URL** -Eigenschaft des Projekts angegeben wird, und der Webbrowser wird mit der Standardseite dieser Website geöffnet.

    > [!NOTE]
    > Wenn das Dialogfeld **Skript Debuggen deaktiviert** angezeigt wird, klicken Sie auf die Schaltfläche **Ja** .

2. Wählen Sie im Listen Bereich der SharePoint-Website den Link **Aufgaben** aus.

     Die Seite **Tasks-alle Aufgaben** wird angezeigt.

3. Wählen Sie auf der Registerkarte **Listen Tools** des Menübands die Registerkarte **Liste** aus, und wählen Sie dann in der Gruppe **Einstellungen** die Option **Listen Einstellungen** aus.

     Die Seite " **Listen Einstellungen** " wird angezeigt.

4. Wählen Sie unter der Überschrift Übertragung im oberen Bereich der **Seite den Link** **SharePoint Developer Center** aus, vergewissern Sie sich, dass der Browser die Website öffnet https://docs.microsoft.com/sharepoint/dev/ , und schließen Sie dann den Browser.

## <a name="cleaning-up-the-development-computer"></a>Bereinigen des Entwicklungs Computers
 Nachdem Sie die Tests des Projektelements abgeschlossen haben, entfernen Sie die Projektelementvorlage aus der experimentellen Instanz von Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>So bereinigen Sie den Entwicklungscomputer

1. Wählen Sie in der experimentellen Instanz von Visual Studio auf der Menüleiste Extras   >  **Erweiterungen und Updates** aus.

     Das Dialogfeld **Erweiterungen und Updates** wird geöffnet.

2. Wählen Sie in der Liste der Erweiterungen die **Projekt Element Erweiterung benutzerdefinierte Aktion** aus, und wählen Sie dann die Schaltfläche **deinstallieren** aus.

3. Wählen Sie im angezeigten Dialogfeld die Schaltfläche **Ja** , um zu bestätigen, dass Sie die Erweiterung deinstallieren möchten, und wählen Sie dann die Schaltfläche **jetzt neu starten** aus, um die Deinstallation abzuschließen.

4. Schließen Sie beide Instanzen von Visual Studio (die experimentelle Instanz und die Instanz von Visual Studio, in der die Projekt Mappe "customaktionprojectitem" geöffnet ist).

## <a name="see-also"></a>Weitere Informationen
- [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Aktionsprojekt Elements mit einer Element Vorlage, Teil 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Definieren von benutzerdefinierten SharePoint-Projekt Elementtypen](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Erstellen von Element Vorlagen und Projektvorlagen für SharePoint-Projekt Elemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Schema Referenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
- [Gewusst wie: Verwenden von Assistenten mit Projektvorlagen](../extensibility/how-to-use-wizards-with-project-templates.md)
- [Standardmäßige benutzerdefinierte Aktions Orte und IDs](/previous-versions/office/developer/sharepoint-2010/bb802730(v=office.14))
