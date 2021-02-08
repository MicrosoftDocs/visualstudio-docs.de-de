---
title: Erstellen eines benutzerdefinierten Aktionsprojekt Elements mit Element Vorlage, Teil 1
titleSuffix: ''
description: Erstellen Sie mithilfe einer Element Vorlage ein Projekt Element, das einem SharePoint-Projekt hinzugefügt werden kann, um eine benutzerdefinierte Aktion auf einer SharePoint-Website zu erstellen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, creating custom templates
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e7427c0866806c705ed28a049b33024771631c0a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839122"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-1"></a>Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Aktionsprojekt Elements mit einer Element Vorlage, Teil 1
  Sie können das SharePoint-Projektsystem in Visual Studio erweitern, indem Sie eigene Projektelementtypen erstellen. In dieser exemplarischen Vorgehensweise erstellen Sie ein Projektelement, das einem SharePoint-Projekt hinzugefügt werden kann, um eine benutzerdefinierte Aktion auf einer SharePoint-Website zu erstellen. Durch die benutzerdefinierte Aktion wird dem Menü **Website Aktionen** der SharePoint-Website ein Menü Element hinzugefügt.

 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:

- Erstellen einer Visual Studio-Erweiterung, die einen neuen Typ von SharePoint-Projektelement für eine benutzerdefinierte Aktion definiert. Mit dem neuen Projektelementtyp werden mehrere benutzerdefinierte Funktionen implementiert:

  - Ein Kontextmenü, über das weitere auf das Projektelement bezogene Aufgaben ausgewählt werden können, z. B. für das Anzeigen eines Designers für die benutzerdefinierte Aktion in Visual Studio.

  - Code, der ausgeführt wird, wenn ein Entwickler bestimmte Eigenschaften des Projektelements oder des Projekts ändert, in dem es enthalten ist.

  - Ein benutzerdefiniertes Symbol, das neben dem Projekt Element in **Projektmappen-Explorer** angezeigt wird.

- Erstellen einer Visual Studio-Elementvorlage für das Projektelement.

- Erstellen eines Visual Studio-Erweiterungspakets (VSIX) zum Bereitstellen der Projektelementvorlage und der Erweiterungsassembly.

- Debuggen und Testen des Projektelements

  Dies ist eine eigenständige exemplarische Vorgehensweise. Nachdem Sie diese exemplarische Vorgehensweise abgeschlossen haben, können Sie das Projektelement erweitern, indem Sie der Elementvorlage einen Assistenten hinzufügen. Weitere Informationen finden Sie unter Exemplarische [Vorgehensweise: Erstellen eines benutzerdefinierten Aktionsprojekt Elements mit einer Element Vorlage, Teil 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

> [!NOTE]
> Sie können ein Beispiel von [GitHub](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) herunterladen, das zeigt, wie benutzerdefinierte Aktivitäten für einen Workflow erstellt werden.

## <a name="prerequisites"></a>Voraussetzungen
 Zum Durchführen dieser exemplarischen Vorgehensweise werden auf dem Entwicklungscomputer die folgenden Komponenten benötigt:

- Unterstützte Editionen von Microsoft Windows, SharePoint und Visual Studio.

- Die [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. In dieser exemplarischen Vorgehensweise wird die **VSIX-Projekt** Vorlage im SDK verwendet, um ein VSIX-Paket zum Bereitstellen des Projekt Elements zu erstellen. Weitere Informationen finden Sie unter [Erweitern der SharePoint-Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Kenntnisse der folgenden Konzepte sind hilfreich, wenn auch für die Durchführung der exemplarischen Vorgehensweise nicht erforderlich:

- Benutzerdefinierte Aktionen in SharePoint. Weitere Informationen finden Sie unter [Custom Action](/previous-versions/office/developer/sharepoint-2010/ms458635(v=office.14)).

- Elementvorlagen in Visual Studio. Weitere Informationen finden Sie unter [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md).

## <a name="create-the-projects"></a>Erstellen der Projekte
 Zum Abschließen dieser exemplarischen Vorgehensweise müssen Sie drei Projekte erstellen:

- Ein VSIX-Projekt. Von diesem Projekt wird das VSIX-Paket zum Bereitstellen des SharePoint-Projektelements erstellt.

- Ein Elementvorlagenprojekt. Von diesem Projekt wird eine Elementvorlage erstellt, mit der das SharePoint-Projektelement einem SharePoint-Projekt hinzugefügt werden kann.

- Ein Klassenbibliotheksprojekt. Dieses Projekt implementiert eine Visual Studio-Erweiterung, die das Verhalten des SharePoint-Projektelements definiert.

  Beginnen Sie mit der exemplarischen Vorgehensweise, indem Sie beide Projekte erstellen.

#### <a name="to-create-the-vsix-project"></a>So erstellen Sie das VSIX-Projekt

1. Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**.

3. Stellen Sie sicher, dass in der Liste am oberen Rand des Dialog Felds **Neues Projekt** die Option **.NET Framework 4,5** ausgewählt ist.

4. Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Visual c#** oder **Visual Basic** , und wählen Sie dann den Knoten **Erweiterbarkeit** aus.

    > [!NOTE]
    > Der **Erweiterbarkeits** Knoten ist nur verfügbar, wenn Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie weiter oben in diesem Thema im Abschnitt zu den erforderlichen Komponenten.

5. Wählen Sie die **VSIX-Projekt** Vorlage aus.

6. Geben Sie im Feld **Name den Namen** **customaktionprojectitem** ein, und klicken Sie dann auf die Schaltfläche **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]fügt **Projektmappen-Explorer** das **customaktionprojectitem** -Projekt hinzu.

#### <a name="to-create-the-item-template-project"></a>So erstellen Sie das Elementvorlagenprojekt

1. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für den Projektmappenknoten, wählen Sie **Hinzufügen** aus, und wählen Sie dann **Neues Projekt** aus.

2. Stellen Sie sicher, dass in der Liste am oberen Rand des Dialog Felds **Neues Projekt** die Option **.NET Framework 4,5** ausgewählt ist.

3. Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Visual c#** oder **Visual Basic** , und wählen Sie dann den Knoten **Erweiterbarkeit** aus.

4. Wählen Sie in der Liste der Projektvorlagen die **c#-Element Vorlage** oder die Vorlage für **Visual Basic Element Vorlage** aus.

5. Geben Sie im Feld **Name den Namen** **ItemTemplate** ein, und klicken Sie dann auf die Schaltfläche **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt der Projekt Mappe das Projekt **ItemTemplate** hinzu.

#### <a name="to-create-the-extension-project"></a>So erstellen Sie das Erweiterungsprojekt

1. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für den Projektmappenknoten, wählen Sie **Hinzufügen** aus, und wählen Sie dann **Neues Projekt** aus.

2. Stellen Sie sicher, dass in der Liste am oberen Rand des Dialog Felds **Neues Projekt** die Option **.NET Framework 4,5** ausgewählt ist.

3. Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Visual c#** oder **Visual Basic** , wählen Sie den Knoten **Windows** aus, und wählen Sie dann die Projektvorlage **Klassenbibliothek** aus.

4. Geben Sie im Feld **Name** **ProjectItemDefinition** ein, und klicken Sie dann auf die Schaltfläche **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt der Projekt Mappe das Projekt **ProjectItemDefinition** hinzu und öffnet die standardmäßige Class1-Codedatei.

5. Löschen Sie die Class1-Codedatei aus dem Projekt.

## <a name="configure-the-extension-project"></a>Konfigurieren des Erweiterungsprojekts
 Bevor Sie Code zum Erstellen des SharePoint-Projektelementtyps schreiben, müssen Sie dem Erweiterungsprojekt Codedateien und Assemblyverweise hinzufügen.

#### <a name="to-configure-the-project"></a>So konfigurieren Sie das Projekt

1. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für das Projekt **ProjectItemDefinition** , und wählen Sie **Hinzufügen** und dann **Neues Element** aus.

2. Wählen Sie in der Liste der Projekt Elemente **Codedatei** aus.

3. Geben Sie im Feld **Name** den Namen **CustomAction** mit der entsprechenden Dateinamenerweiterung ein, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.

4. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für das Projekt **ProjectItemDefinition** , und wählen Sie dann **Verweis hinzufügen** aus.

5. Wählen Sie im Dialogfeld **Verweis-Manager-ProjectItemDefinition** den **Knoten** Assemblys aus, und wählen Sie dann den Knoten **Framework** aus.

6. Aktivieren Sie das Kontrollkästchen neben jeder der folgenden Assemblys:

    - System.ComponentModel.Composition

    - System.Windows.Forms

7. Wählen Sie den Knoten **Erweiterungen** aus, aktivieren Sie das Kontrollkästchen neben der Microsoft. VisualStudio. SharePoint-Assembly, und wählen Sie dann die Schaltfläche **OK** aus.

## <a name="define-the-new-sharepoint-project-item-type"></a>Definieren des neuen SharePoint-Projekt Elementtyps
 Erstellen Sie eine Klasse, die die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>-Schnittstelle implementiert, um das Verhalten des neuen Projektelementtyps zu definieren. Implementieren Sie diese Schnittstelle immer dann, wenn Sie einen neuen Projektelementtyp definieren möchten.

#### <a name="to-define-the-new-sharepoint-project-item-type"></a>So definieren Sie den neuen SharePoint-Projektelementtyp

1. Öffnen Sie im Projekt ProjectItemDefinition die CustomAction-Codedatei.

2. Ersetzen Sie den Code in dieser Datei durch den folgenden Code:

     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/CSharp/customactionprojectitem/projectitemtypedefinition/customaction.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/projectitemdefinition/customaction.vb#1)]

## <a name="create-an-icon-for-the-project-item-in-solution-explorer"></a>Erstellen Sie ein Symbol für das Projekt Element in Projektmappen-Explorer
 Wenn Sie ein benutzerdefiniertes SharePoint-Projektelement erstellen, können Sie dem Projektelement ein Bild (ein Symbol oder eine Bitmap) zuordnen. Dieses Bild wird neben dem Projekt Element in **Projektmappen-Explorer** angezeigt.

 In der folgenden Vorgehensweise erstellen Sie ein Symbol für das Projektelement und betten das Symbol in die Erweiterungsassembly ein. Auf dieses Symbol wird durch das <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute> der zuvor erstellten `CustomActionProjectItemTypeProvider`-Klasse verwiesen.

#### <a name="to-create-a-custom-icon-for-the-project-item"></a>So erstellen Sie ein benutzerdefiniertes Symbol für das Projektelement

1. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für das Projekt **ProjectItemDefinition** , wählen Sie **Hinzufügen** aus, und wählen Sie dann **Neues Element...** aus.

2. Wählen Sie in der Liste der Projekt Elemente das **Symbol Datei** Element aus.

    > [!NOTE]
    > In Visual Basic-Projekten müssen Sie den Knoten **Allgemein** auswählen, um das **Symbol Datei** Element anzuzeigen.

3. Geben Sie im Feld **Name** **CustomAction_SolutionExplorer. ico** ein, und klicken Sie dann auf die Schaltfläche **Hinzufügen** .

     Das neue Symbol wird im **Bild-Editor** geöffnet.

4. Bearbeiten Sie die 16x16-Version der Symboldatei so, dass sich das Symbol leicht von anderen unterscheiden lässt, und speichern Sie dann die Symboldatei.

5. Wählen Sie in Projektmappen-Explorer **CustomAction_SolutionExplorer. ico** aus.

6. Wählen Sie im Fenster **Eigenschaften** den Pfeil neben der Eigenschaft **Buildaktion** aus.

7. Wählen Sie in der angezeigten Liste **eingebettete Ressource** aus.

## <a name="checkpoint"></a>Prüfpunkt
 Ab diesem Punkt in der exemplarischen Vorgehensweise wurde der gesamte für das Projektelement benötigte Code in das Projekt eingefügt. Erstellen Sie das Projekt, um zu überprüfen, ob es fehlerfrei kompiliert wird.

#### <a name="to-build-your-project"></a>So erstellen Sie das Projekt

1. Öffnen Sie das Kontextmenü für das Projekt **ProjectItemDefinition** , und wählen Sie dann **Erstellen** aus.

## <a name="create-a-visual-studio-item-template"></a>Erstellen einer Visual Studio-Element Vorlage
 Um Ihr Projektelement anderen Entwicklern zur Verfügung stellen zu können, müssen Sie eine Projektvorlage oder eine Elementvorlage erstellen. Mithilfe dieser Vorlagen können Entwickler in Visual Studio eine Instanz des Projekts erstellen, indem sie ein neues Projekt erstellen oder ein Element zu einem vorhandenen Projekt hinzufügen. Konfigurieren Sie für diese exemplarische Vorgehensweise das Projektelement mithilfe des Projekts ItemTemplate.

#### <a name="to-create-the-item-template"></a>So erstellen Sie die Elementvorlage

1. Löschen Sie die Class1-Codedatei aus dem ItemTemplate-Projekt.

2. Öffnen Sie im Projekt "ItemTemplate" die Datei " *ItemTemplate. vstemplate* ".

3. Ersetzen Sie den Inhalt der Datei durch das folgende XML, speichern Sie anschließend die Datei, und schließen Sie sie.

    > [!NOTE]
    > Das folgende XML ist für eine Visual C#-Elementvorlage bestimmt. Wenn Sie eine Visual Basic-Elementvorlage erstellen, ersetzen Sie den Wert des `ProjectType`-Elements durch `VisualBasic`.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">
      <TemplateData>
        <DefaultName>CustomAction</DefaultName>
        <Name>Custom Action</Name>
        <Description>SharePoint Custom Action by Contoso</Description>
        <ProjectType>CSharp</ProjectType>
        <SortOrder>1000</SortOrder>
        <Icon>ItemTemplate.ico</Icon>
        <ProvideDefaultName>true</ProvideDefaultName>
      </TemplateData>
      <TemplateContent>
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\Elements.xml">Elements.xml</ProjectItem>
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\SharePointProjectItem.spdata">CustomAction.spdata</ProjectItem>
      </TemplateContent>
    </VSTemplate>
    ```

     Diese Datei definiert den Inhalt und das Verhalten der Elementvorlage. Weitere Informationen zum Inhalt dieser Datei finden Sie unter [Schema Referenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md).

4. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für das Projekt **ItemTemplate** , wählen Sie **Hinzufügen** aus, und wählen Sie dann **Neues Element** aus.

5. Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Vorlage **Text Datei** aus.

6. Geben Sie im Feld **Name den Namen** **CustomAction. spdata** ein, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.

7. Fügen Sie der Datei *CustomAction. spdata* den folgenden XML-Code hinzu, und speichern und schließen Sie dann die Datei.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <ProjectItem Type="Contoso.CustomAction" DefaultFile="Elements.xml"
     xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">
      <Files>
        <ProjectItemFile Source="Elements.xml" Target="$fileinputname$\" Type="ElementManifest" />
      </Files>
    </ProjectItem>
    ```

     Diese Datei enthält Informationen zu den Dateien, die im Projektelement enthalten sind. Das `Type`-Attribut des `ProjectItem`-Elements muss auf die gleiche Zeichenfolge festgelegt werden, die in der Projektelementdefinition (die <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>-Klasse, die Sie zuvor in dieser exemplarischen Vorgehensweise erstellt haben) an `CustomActionProjectItemTypeProvider` übergeben wird. Weitere Informationen zum Inhalt von *spdata* -Dateien finden Sie unter [Schema Referenz für SharePoint-Projekt Elemente](../sharepoint/sharepoint-project-item-schema-reference.md).

8. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für das Projekt **ItemTemplate** , wählen Sie **Hinzufügen** aus, und wählen Sie dann **Neues Element** aus.

9. Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Vorlage **XML-Datei** aus.

10. Geben Sie im Feld **Name** **Elements.xml** ein, und klicken Sie dann auf die Schaltfläche **Hinzufügen** .

11. Ersetzen Sie den Inhalt der Datei *Elements.xml* durch den folgenden XML-Code, und speichern und schließen Sie dann die Datei.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">
      <CustomAction Id="Replace this with a GUID or some other unique string"
                    GroupId="SiteActions"
                    Location="Microsoft.SharePoint.StandardMenu"
                    Sequence="1000"
                    Title="Replace this with your title"
                    Description="Replace this with your description" >
        <UrlAction Url="~site/Lists/Tasks/AllItems.aspx"/>
      </CustomAction>
    </Elements>
    ```

     Diese Datei definiert eine standardmäßige benutzerdefinierte Aktion, mit der im Menü **Website Aktionen** der SharePoint-Website ein Menü Element erstellt wird. Wenn ein Benutzer das Menüelement auswählt, wird die im `UrlAction`-Element angegebene URL im Webbrowser geöffnet. Weitere Informationen zu den XML-Elementen, die Sie verwenden können, um eine benutzerdefinierte Aktion zu definieren, finden Sie unter [benutzerdefinierte Aktions Definitionen](/sharepoint/dev/schema/custom-action-definition-schema).

12. Öffnen Sie optional die Datei " *ItemTemplate. ico* ", und ändern Sie Sie so, dass Sie einen Entwurf aufweist, den Sie erkennen können. Dieses Symbol wird neben dem Projekt Element im Dialogfeld **Neues Element hinzufügen** angezeigt.

13. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für das Projekt **ItemTemplate** , und wählen Sie dann **Projekt entladen** aus.

14. Öffnen Sie erneut das Kontextmenü für das Projekt **ItemTemplate** , und wählen Sie dann **ItemTemplate. csproj bearbeiten** oder **ItemTemplate. vbproj bearbeiten** aus.

15. Suchen Sie das folgende `VSTemplate`-Element in der Projektdatei.

    ```xml
    <VSTemplate Include="ItemTemplate.vstemplate">
    ```

16. Ersetzen Sie dieses `VSTemplate`-Element durch das folgende XML, und speichern und schließen Sie dann die Datei.

    ```xml
    <VSTemplate Include="ItemTemplate.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     Das `OutputSubPath`-Element gibt weitere Ordner in dem Pfad an, unter dem die Elementvorlage beim Erstellen des Projekts erstellt wird. Mit den hier angegebenen Ordnern wird sichergestellt, dass die Element Vorlage nur verfügbar ist, wenn Kunden das Dialogfeld **Neues Element hinzufügen** öffnen, den **SharePoint** -Knoten erweitern und dann den Knoten **2010** auswählen.

17. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für das Projekt **ItemTemplate** , und wählen Sie dann **Projekt erneut laden** aus.

## <a name="create-a-vsix-package-to-deploy-the-project-item"></a>Erstellen eines VSIX-Pakets zum Bereitstellen des Projekt Elements
 Zum Bereitstellen der Erweiterung erstellen Sie anhand des VSIX-Projekts in der Lösung ein VSIX-Paket. Konfigurieren Sie zuerst das VSIX-Paket, indem Sie die im VSIX-Projekt enthaltene Datei "source.extension.vsixmanifest" ändern. Erstellen Sie anschließend das VSIX-Paket, indem Sie die Lösung erstellen.

#### <a name="to-configure-and-create-the-vsix-package"></a>So erstellen und konfigurieren Sie das VSIX-Paket

1. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für die Datei " **Source. Extension. vsixmanifest** " im Projekt "customaktionprojectitem", und wählen Sie dann **Öffnen** aus.

     Die Datei wird von Visual Studio im Manifest-Editor geöffnet. Die Datei "source.extension.vsixmanifest" bildet die Grundlage für die Datei "extension.vsixmanifest", die für alle VSIX-Pakete erforderlich ist. Weitere Informationen zu dieser Datei finden Sie in der [Referenz zu VSIX-Erweiterungs Schema 1,0](/previous-versions/dd393700(v=vs.110)).

2. Geben Sie im Feld **Produkt Name** die Option **benutzerdefiniertes Aktionsprojekt Element** ein.

3. **Geben Sie** im Feld **Autor** den Text "" ein.

4. Geben Sie im Feld **Beschreibung** **ein SharePoint-Projekt Element ein, das eine benutzerdefinierte Aktion darstellt**.

5. Wählen Sie auf der Registerkarte **Objekte** die Schaltfläche **neu** aus.

     Das Dialogfeld **Neues Objekt hinzufügen** wird angezeigt.

6. Wählen Sie in der Liste **Typ** den Eintrag **Microsoft. VisualStudio. ItemTemplate** aus.

    > [!NOTE]
    > Dieser Wert entspricht dem `ItemTemplate`-Element in der Datei "extension.vsixmanifest". Dieses Element identifiziert den Unterordner im VSIX-Paket, der die Projektelementvorlage enthält. Weitere Informationen finden Sie unter [ItemTemplate-Element (VSX-Schema)](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\)).

7. Wählen Sie  in der Liste Quelle **ein Projekt in der aktuellen Projekt** Mappe aus.

8. Wählen Sie in der Liste **Projekt** die Option **ItemTemplate** aus, und klicken Sie dann auf die Schaltfläche **OK** .

9. Wählen Sie auf der Registerkarte **Objekte** erneut die Schaltfläche **neu** aus.

     Das Dialogfeld **Neues Objekt hinzufügen** wird angezeigt.

10. Wählen Sie in der Liste **Typ** den Eintrag **Microsoft. VisualStudio. MEFComponent** aus.

    > [!NOTE]
    > Dieser Wert entspricht dem `MefComponent`-Element in der Datei "extension.vsixmanifest". Von diesem Element wird der Name einer Erweiterungsassembly im VSIX-Paket angegeben. Weitere Informationen finden Sie unter [MEFComponent-Element (VSX-Schema)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

11. Wählen Sie  in der Liste Quelle **ein Projekt in der aktuellen Projekt** Mappe aus.

12. Wählen Sie in der Liste **Projekt** die Option **ProjectItemDefinition** aus.

13. Klicken Sie auf die Schaltfläche **OK** .

14. Wählen Sie in der Menüleiste Buildprojektmappe **Erstellen** aus, und vergewissern Sie sich,  >  dass das Projekt ohne Fehler kompiliert wird.

15. Überprüfen Sie, ob der Buildausgabeordner für das Projekt "CustomActionProjectItem" die Datei "CustomActionProjectItem.vsix" enthält.

     Standardmäßig ist der Buildausgabeordner der Ordner "\bin\Debug" in dem Ordner, der das Projekt "CustomActionProjectItem" enthält.

## <a name="test-the-project-item"></a>Testen des Projekt Elements
 Jetzt können Sie das Projektelement testen. Debuggen Sie die Projektmappe CustomActionProjectItem zunächst in der experimentellen Instanz von Visual Studio. Testen Sie dann das Projekt Element für **benutzerdefinierte Aktionen** in einem SharePoint-Projekt in der experimentellen Instanz von Visual Studio. Erstellen und führen Sie zum Schluss das SharePoint-Projekt aus, um sicherzustellen, dass die benutzerdefinierte Aktion ordnungsgemäß funktioniert.

#### <a name="to-start-debugging-the-solution"></a>So debuggen Sie die Projektmappe

1. Starten Sie Visual Studio erneut mit Administratoranmeldeinformationen, und öffnen Sie dann die Projektmappe "CustomActionProjectItem".

2. Öffnen Sie die CustomAction-Codedatei, und fügen Sie dann in der ersten Codezeile in der `InitializeType`-Methode einen Haltepunkt ein.

3. Drücken Sie **F5** , um das Debuggen zu starten.

     Die Erweiterung wird unter "%UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Custom Action Project Item\1.0" installiert, und eine experimentelle Instanz von Visual Studio wird gestartet. Sie testen das Projektelement in dieser Instanz von Visual Studio.

#### <a name="to-test-the-project-item-in-visual-studio"></a>So testen Sie das Projektelement in Visual Studio

1. Wählen Sie in der experimentellen Instanz von Visual Studio in der Menüleiste **Datei**  >  **neu**  >  **Projekt** aus.

2. Erweitern Sie **Visual c#** oder **Visual Basic** (abhängig von der von der Element Vorlage unterstützten Sprache), erweitern Sie **SharePoint**, und wählen Sie dann den Knoten **2010** aus.

3. Wählen Sie in der Liste der Projektvorlagen **SharePoint 2010-Projekt** aus.

4. Geben Sie im Feld **Name den Namen** **customaktiontest** ein, und klicken Sie dann auf die Schaltfläche **OK** .

5. Geben Sie im Assistenten zum Anpassen von **SharePoint** die URL der Website ein, die Sie zum Debuggen verwenden möchten, und wählen Sie dann die Schaltfläche **Fertig** stellen aus.

6. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für den Projekt Knoten, wählen Sie **Hinzufügen** aus, und wählen Sie dann **Neues Element** aus.

7. Wählen Sie im Dialogfeld **Neues Element hinzufügen** unter dem Knoten **SharePoint** den Knoten **2010** aus.

     Überprüfen Sie, ob das **benutzerdefinierte Aktions** Element in der Liste der Projekt Elemente angezeigt wird.

8. Wählen Sie das **benutzerdefinierte Aktions** Element aus, und wählen Sie dann die Schaltfläche **Hinzufügen** .

     Visual Studio fügt dem Projekt ein Element mit dem Namen **CustomAction1** hinzu und öffnet die Datei *Elements.xml* im Editor.

9. Überprüfen Sie, ob die Codeausführung in der anderen Instanz von Visual Studio an dem Haltepunkt unterbrochen wird, den Sie zuvor in der `InitializeType`-Methode festgelegt haben.

10. Drücken Sie die Taste **F5** , um das Debuggen des Projekts fortzusetzen.

11. Öffnen Sie in der experimentellen Instanz von Visual Studio in **Projektmappen-Explorer** das Kontextmenü für den Knoten **CustomAction1** , und wählen Sie dann **benutzerdefinierter Aktions-Designer anzeigen** aus.

12. Überprüfen Sie, ob ein Meldungs Feld angezeigt wird, und wählen Sie dann die Schaltfläche **OK**

     Sie können dieses Kontextmenü verwenden, um zusätzliche Optionen oder Befehle für Entwickler bereitzustellen, z. B. zum Anzeigen eines Designers für die benutzerdefinierte Aktion.

13. Wählen Sie in der Menüleiste   >  **Ausgabe** anzeigen aus.

     Das Fenster **Ausgabe** wird geöffnet.

14. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für das Element **CustomAction1** , und ändern Sie dann den Namen in **MyCustomAction**.

     Im Fenster **Ausgabe** wird eine Bestätigungsmeldung angezeigt. Diese Meldung wird von dem <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemNameChanged>-Ereignishandler ausgegeben, den Sie in der `CustomActionProjectItemTypeProvider`-Klasse definiert haben. Sie können dieses Ereignis und andere Projektelementereignisse behandeln, um ein benutzerdefiniertes Verhalten bei Änderungen des Projektelements durch den Entwickler zu implementieren.

#### <a name="to-test-the-custom-action-in-sharepoint"></a>So testen Sie die benutzerdefinierte Aktion in SharePoint

1. Öffnen Sie in der experimentellen Instanz von Visual Studio die Datei *Elements.xml* , die dem Projekt Element **MyCustomAction** untergeordnet ist.

2. Nehmen Sie in der Datei *Elements.xml* die folgenden Änderungen vor, und speichern Sie dann die Datei:

    - Legen Sie im `CustomAction`-Element das `Id`-Attribut auf eine GUID oder eine andere eindeutige Zeichenfolge fest, wie im folgenden Beispiel gezeigt:

        ```xml
        Id="cd85f6a7-af2e-44ab-885a-0c795b52121a"
        ```

    - Legen Sie im `CustomAction`-Element das `Title`-Attribut fest, wie im folgenden Beispiel gezeigt:

        ```xml
        Title="SharePoint Developer Center"
        ```

    - Legen Sie im `CustomAction`-Element das `Description`-Attribut fest, wie im folgenden Beispiel gezeigt:

        ```xml
        Description="Opens the SharePoint Developer Center Web site."
        ```

    - Legen Sie im `UrlAction`-Element das `Url`-Attribut fest, wie im folgenden Beispiel gezeigt:

        ```xml
        Url="https://docs.microsoft.com/sharepoint/dev/"
        ```

3. Drücken Sie die Taste **F5**.

     Die benutzerdefinierte Aktion wird verpackt und auf der SharePoint-Website bereitgestellt, die in der **Website-URL** -Eigenschaft des Projekts angegeben ist. Im Webbrowser wird die Standardseite dieser Website geöffnet.

    > [!NOTE]
    > Wenn das Dialogfeld **Skript Debugging deaktiviert** angezeigt wird, klicken Sie auf die Schaltfläche **Ja** , um das Debuggen des Projekts fortzusetzen.

4. Wählen Sie im Menü **Website Aktionen** die Option **SharePoint Developer Center** aus, vergewissern Sie sich, dass der Browser die Website öffnet https://docs.microsoft.com/sharepoint/dev/ , und schließen Sie dann den Webbrowser.

## <a name="clean-up-the-development-computer"></a>Bereinigen des Entwicklungs Computers
 Nachdem Sie die Tests des Projektelements abgeschlossen haben, entfernen Sie die Projektelementvorlage aus der experimentellen Instanz von Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>So bereinigen Sie den Entwicklungscomputer

1. Wählen Sie in der experimentellen Instanz von Visual Studio auf der Menüleiste Extras   >  **Erweiterungen und Updates** aus.

     Das Dialogfeld **Erweiterungen und Updates** wird geöffnet.

2. Wählen Sie in der Liste der Erweiterungen **benutzerdefinierte Aktion Projekt Element** aus, und wählen Sie dann die Schaltfläche **deinstallieren** aus.

3. Wählen Sie im angezeigten Dialogfeld die Schaltfläche **Ja** aus, um zu bestätigen, dass Sie die Erweiterung deinstallieren möchten.

4. Wählen Sie die Schaltfläche **jetzt neu starten** aus, um die Installation abzuschließen.

5. Schließen Sie die experimentelle Instanz von Visual Studio und die Instanz, in der die Projektmappe "CustomActionProjectItem" geöffnet ist.

## <a name="next-steps"></a>Nächste Schritte
 Nachdem Sie diese exemplarische Vorgehensweise abgeschlossen haben, können Sie der Elementvorlage einen Assistenten hinzufügen. Wenn ein Benutzer ein benutzerdefiniertes Aktionsprojekt Element einem SharePoint-Projekt hinzufügt, sammelt der Assistent Informationen über die Aktion (z. b. den Speicherort und die URL, zu der navigiert werden soll, wenn die Aktion ausgewählt wird) und fügt diese Informationen der *Elements.xml* -Datei im neuen Projekt Element hinzu. Weitere Informationen finden Sie unter Exemplarische [Vorgehensweise: Erstellen eines benutzerdefinierten Aktionsprojekt Elements mit einer Element Vorlage, Teil 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

## <a name="see-also"></a>Weitere Informationen

- [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Aktionsprojekt Elements mit einer Element Vorlage, Teil 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [Definieren von benutzerdefinierten SharePoint-Projekt Elementtypen](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Erstellen von Element Vorlagen und Projektvorlagen für SharePoint-Projekt Elemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Verwenden des SharePoint-Projekt Dienstanbieter](../sharepoint/using-the-sharepoint-project-service.md)
- [Schema Referenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
- [Bildbearbeitung für Symbole](/cpp/windows/image-editor-for-icons)
- [Erstellen eines Symbols oder anderen Bilds &#40;Bildbearbeitung für Symbole&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)