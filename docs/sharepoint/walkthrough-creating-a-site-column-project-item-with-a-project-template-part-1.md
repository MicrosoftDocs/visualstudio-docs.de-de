---
title: Erstellen eines Projekt Elements für eine Website Spalte mit einer Projektvorlage, Teil 1
titleSuffix: ''
description: Definieren Sie einen Projekt Elementtyp zum Erstellen einer Websites palte, und erstellen Sie dann eine Projektvorlage, die zum Erstellen eines SharePoint-Projekts verwendet wird, das das Projekt Element enthält.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b9ccf478a084b8dedabc6f470a333e3fe4b54eb7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918728"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-1"></a>Exemplarische Vorgehensweise: Erstellen eines Projekt Elements für eine Website Spalte mit einer Projektvorlage, Teil 1
  SharePoint-Projekte sind Container für SharePoint-Projektelemente. Sie können das SharePoint-Projektsystem in Visual Studio erweitern, indem Sie eigene SharePoint-Projektelementtypen erstellen und diese dann einer Projektvorlage zuordnen. In dieser exemplarischen Vorgehensweise definieren Sie einen Projektelementtyp zum Erstellen einer Websitespalte. Anschließend erstellen Sie eine Projektvorlage, mit der ein neues Projekt erstellt werden kann, das ein Projektelement einer Websitespalte enthält.

 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:

- Erstellen einer Visual Studio-Erweiterung, die einen neuen Typ von SharePoint-Projektelement für eine Websitespalte definiert. Der Projekt Elementtyp enthält eine einfache benutzerdefinierte Eigenschaft, die im **Eigenschaften** Fenster angezeigt wird.

- Erstellen einer [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]-Projektvorlage für das Projektelement.

- Erstellen eines [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]-Erweiterungspakets (VSIX) zum Bereitstellen der Projektvorlage und der Erweiterungsassembly.

- Debuggen und Testen des Projektelements

  Dies ist eine eigenständige exemplarische Vorgehensweise. Nachdem Sie diese exemplarische Vorgehensweise abgeschlossen haben, können Sie das Projektelement erweitern, indem Sie der Projektvorlage einen Assistenten hinzufügen. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Erstellen eines Projekt Elements für eine Website Spalte mit einer Projektvorlage, Teil 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

> [!NOTE]
> Eine Reihe von Beispiel Workflows finden Sie unter [Beispiele für SharePoint-Workflows](/sharepoint/dev/general-development/sharepoint-workflow-samples).

## <a name="prerequisites"></a>Voraussetzungen
 Zum Durchführen dieser exemplarischen Vorgehensweise werden auf dem Entwicklungscomputer die folgenden Komponenten benötigt:

- Unterstützte Editionen von Microsoft Windows, SharePoint und [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

- Die [!include[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. In dieser exemplarischen Vorgehensweise wird die **VSIX-Projekt** Vorlage im SDK verwendet, um ein VSIX-Paket zum Bereitstellen des Projekt Elements zu erstellen. Weitere Informationen finden Sie unter [Erweitern der SharePoint-Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Kenntnisse des folgenden Konzepts sind hilfreich, wenn auch für die Durchführung der exemplarischen Vorgehensweise nicht erforderlich:

- Websitespalten in SharePoint Weitere Informationen finden Sie unter [Spalten](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14)).

- Projektvorlagen in Visual Studio. Weitere Informationen finden Sie unter [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md).

## <a name="create-the-projects"></a>Erstellen der Projekte
 Zum Abschließen dieser exemplarischen Vorgehensweise müssen Sie drei Projekte erstellen:

- Ein VSIX-Projekt. In diesem Projekt wird das VSIX-Paket zum Bereitstellen des Projektelements für die Websitespalte sowie die Projektvorlage erstellt.

- Ein Projektvorlagenprojekt. In diesem Projekt wird eine Projektvorlage zum Erstellen eines neuen SharePoint-Projekts mit dem Projektelement für die Websitespalte erstellt.

- Ein Klassenbibliotheksprojekt. In diesem Projekt wird eine Visual Studio-Erweiterung implementiert, die das Verhalten des SharePoint-Projektelements definiert.

  Beginnen Sie mit der exemplarischen Vorgehensweise, indem Sie beide Projekte erstellen.

#### <a name="to-create-the-vsix-project"></a>So erstellen Sie das VSIX-Projekt

1. Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**.

3. Stellen Sie oben im Dialogfeld **Neues Projekt** sicher, dass **.NET Framework 4,5** in der Liste der .NET Framework Versionen ausgewählt ist.

4. Erweitern Sie den Knoten **Visual Basic** oder **Visual c#** , und wählen Sie dann den Knoten **Erweiterbarkeit** aus.

    > [!NOTE]
    > Der **Erweiterbarkeits** Knoten ist nur verfügbar, wenn Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie weiter oben in diesem Thema im Abschnitt zu den erforderlichen Komponenten.

5. Wählen Sie in der Liste der Projektvorlagen die Option **VSIX-Projekt** aus.

6. Geben Sie im Feld **Name den Namen** **sitecolumnprojectitem** ein, und klicken Sie dann auf die Schaltfläche **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt das Projekt **sitecolumnprojectitem** **Projektmappen-Explorer** hinzu.

#### <a name="to-create-the-project-template-project"></a>So erstellen Sie das Projektvorlagenprojekt

1. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für den Projektmappenknoten, wählen Sie **Hinzufügen** aus, und wählen Sie dann **Neues Projekt** aus.

2. Stellen Sie oben im Dialogfeld **Neues Projekt** sicher, dass **.NET Framework 4,5** in der Liste der .NET Framework Versionen ausgewählt ist.

3. Erweitern Sie den Knoten **Visual c#** oder **Visual Basic** , und wählen Sie dann den Knoten **Erweiterbarkeit** aus.

4. Wählen Sie in der Liste der Projektvorlagen die **c#-Projektvorlage** oder die Vorlage **Visual Basic Projektvorlage** aus.

5. Geben Sie im Feld **Name den Namen** **sitecolumnprojecttemplate** ein, und klicken Sie dann auf die Schaltfläche **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt der Projekt Mappe das **sitecolumnprojecttemplate** -Projekt hinzu.

6. Löschen Sie die Class1-Codedatei aus dem Projekt.

7. Wenn Sie ein Visual Basic-Projekt erstellt haben, löschen Sie auch die folgenden Dateien aus dem Projekt:

    - *MyApplication.Designer.vb*

    - MyApplication.myapp

    - *Resources.Designer.vb*

    - *Resources. resx*

    - *Settings.Designer.vb*

    - Settings.settings

#### <a name="to-create-the-extension-project"></a>So erstellen Sie das Erweiterungsprojekt

1. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für den Projektmappenknoten, wählen Sie **Hinzufügen** aus, und wählen Sie dann **Neues Projekt** aus.

2. Stellen Sie oben im Dialogfeld **Neues Projekt** sicher, dass **.NET Framework 4,5** in der Liste der .NET Framework Versionen ausgewählt ist.

3. Erweitern Sie den Knoten **Visual c#** oder **Visual Basic** , wählen Sie den Knoten **Windows** aus, und wählen Sie dann die Vorlage **Klassenbibliothek** aus.

4. Geben Sie im Feld **Name** **projectItemTypeDefinition** ein, und klicken Sie dann auf die Schaltfläche **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt der Projekt Mappe das Projekt **projectItemTypeDefinition** hinzu und öffnet die standardmäßige Class1-Codedatei.

5. Löschen Sie die Class1-Codedatei aus dem Projekt.

## <a name="configure-the-extension-project"></a>Konfigurieren des Erweiterungsprojekts
 Fügen Sie Codedateien und Assemblyverweise hinzu, um das Erweiterungsprojekt zu konfigurieren.

#### <a name="to-configure-the-project"></a>So konfigurieren Sie das Projekt

1. Fügen Sie im Projekt projectItemTypeDefinition eine Codedatei mit dem Namen **sitecolumnprojectitemtypeprovider** hinzu.

2. Wählen Sie in der Menüleiste die Optionen **Projekt** > **Verweis hinzufügen** aus.

3. Erweitern Sie im Dialogfeld **Verweis-Manager-projectItemTypeDefinition** den **Knoten** Assemblys, wählen Sie den Knoten **Framework** aus, und aktivieren Sie dann das Kontrollkästchen System. ComponentModel. Composition.

4. Wählen Sie den Knoten **Erweiterungen** aus, aktivieren Sie das Kontrollkästchen neben der Microsoft. VisualStudio. SharePoint-Assembly, und wählen Sie dann die Schaltfläche **OK** aus.

## <a name="define-the-new-sharepoint-project-item-type"></a>Definieren des neuen SharePoint-Projekt Elementtyps
 Erstellen Sie eine Klasse, die die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>-Schnittstelle implementiert, um das Verhalten des neuen Projektelementtyps zu definieren. Implementieren Sie diese Schnittstelle immer dann, wenn Sie einen neuen Projektelementtyp definieren möchten.

#### <a name="to-define-the-new-sharepoint-project-item-type"></a>So definieren Sie den neuen SharePoint-Projektelementtyp

1. Ersetzen Sie in der **sitecolumnprojectitemtypeprovider** -Codedatei den Standard Code durch den folgenden Code, und speichern Sie die Datei.

     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.vb#1)]

## <a name="create-a-visual-studio-project-template"></a>Erstellen einer Visual Studio-Projektvorlage
 Durch das Erstellen einer Projektvorlage ermöglichen Sie anderen Entwicklern das Erstellen von SharePoint-Projekten, die Websitespalten-Projektelemente enthalten. Eine SharePoint-Projektvorlage enthält Dateien, die für alle Projekte in Visual Studio erforderlich sind, z *. b. csproj* -oder *vbproj* -und *VSTEMPLATE* -Dateien sowie für SharePoint-Projekte spezifische Dateien. Weitere Informationen finden Sie unter [Erstellen von Element Vorlagen und Projektvorlagen für SharePoint-Projekt Elemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Bei diesem Verfahren erstellen Sie ein leeres SharePoint-Projekt, um Dateien zu generieren, die spezifisch für SharePoint-Projekte sind. Sie fügen diese Dateien dem SiteColumnProjectTemplate-Projekt hinzu, damit sie in der Vorlage enthalten sind, die von diesem Projekt generiert wird. Außerdem konfigurieren Sie die Projektdatei sitecolumnprojecttemplate, um anzugeben, wo die Projektvorlage im Dialogfeld **Neues Projekt** angezeigt wird.

#### <a name="to-create-the-files-for-the-project-template"></a>So erstellen Sie die Dateien für die Projektvorlage

1. Starten Sie eine zweite Instanz von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] mit Administratorrechten.

2. Erstellen Sie ein SharePoint 2010-Projekt mit dem Namen **basesharepointproject**.

   > [!IMPORTANT]
   > Wählen Sie im Assistenten zum Anpassen von **SharePoint** nicht das Optionsfeld **als Farm Lösung** bereitstellen aus.

3. Fügen Sie dem Projekt ein leeres Element Element hinzu, und benennen Sie dann das Element **field1**.

4. Speichern Sie das Projekt, und schließen Sie die zweite Instanz von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

5. Öffnen Sie in der Instanz von, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] in der die Projekt Mappe sitecolumnprojectitem geöffnet ist, in **Projektmappen-Explorer** das Kontextmenü für den Projekt Knoten **sitecolumnprojecttemplate** , wählen Sie **Hinzufügen** aus, und wählen Sie dann **Vorhandenes Element** aus.

6. Öffnen Sie im Dialogfeld **Vorhandenes Element hinzufügen** die Liste der Dateierweiterungen, und wählen Sie dann **alle Dateien ( \* . \* )** aus.

7. Wählen Sie in dem Verzeichnis, das das basesharepointproject-Projekt enthält, die Datei Key. snk aus, und klicken Sie dann auf die Schaltfläche **Hinzufügen** .

   > [!NOTE]
   > In dieser exemplarischen Vorgehensweise wird diese KEY.SNK-Datei von der Projektvorlage verwendet, die Sie erstellen, um die einzelnen Projekte zu signieren, die mit der Vorlage erstellt werden. Weitere Informationen zum Erweitern dieses Beispiels, um eine andere Key. SNK-Datei für jede Projekt Instanz zu erstellen, finden Sie unter Exemplarische Vorgehensweise [: Erstellen eines Website Spalten-Projekt Elements mit einer Projektvorlage, Teil 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

8. Wiederholen Sie die Schritte 5-8, um die folgenden Dateien aus den angegebenen Unterordnern im Verzeichnis BaseSharePointProject hinzuzufügen:

   - *\Field1\Elements.xml*

   - *\Field1\SharePointProjectItem.spdata*

   - *\Features\Feature1\Feature1.feature*

   - *\Features\Feature1\Feature1.Template.xml*

   - *\Package\Package.package*

   - *\Package\Package.Template.xml*

     Fügen Sie die Dateien unmittelbar zum SiteColumnProjectTemplate-Projekt hinzu. Erstellen Sie die Unterordner Field1, Feature oder Package nicht erneut im Projekt. Weitere Informationen zu diesen Dateien finden Sie unter [Erstellen von Element Vorlagen und Projektvorlagen für SharePoint-Projekt Elemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

#### <a name="to-configure-how-developers-discover-the-project-template-in-the-new-project-dialog-box"></a>So konfigurieren Sie die Verwendung der Projektvorlage durch Entwickler im Dialogfeld "Neues Projekt"

1. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für den **sitecolumnprojecttemplate** -Projekt Knoten, und wählen Sie dann **Projekt entladen** aus. Wenn Sie aufgefordert werden, Änderungen an Dateien zu speichern, klicken Sie auf die Schaltfläche **Ja** .

2. Öffnen Sie erneut das Kontextmenü für den **sitecolumnprojecttemplate** -Knoten, und wählen Sie dann **sitecolumnprojecttemplate. csproj bearbeiten** oder **sitecolumnprojecttemplate. vbproj bearbeiten** aus.

3. Suchen Sie das folgende `VSTemplate`-Element in der Projektdatei.

    ```xml
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">
    ```

4. Ersetze dieses Element durch folgenden XML-Code.

    ```xml
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     Das `OutputSubPath`-Element gibt weitere Ordner in dem Pfad an, unter dem die Projektvorlage beim Erstellen des Projekts erstellt wird. Mit den hier angegebenen Ordnern wird sichergestellt, dass die Projektvorlage nur verfügbar ist, wenn Kunden das Dialogfeld **Neues Projekt** öffnen, den **SharePoint** -Knoten erweitern und dann den Knoten **2010** auswählen.

5. Speichern und schließen Sie die Datei.

6. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für das Projekt **sitecolumnprojecttemplate** , und wählen Sie dann **Projekt erneut laden** aus.

## <a name="edit-the-project-template-files"></a>Bearbeiten der Projektvorlagen Dateien
 Bearbeiten Sie die folgenden Dateien im SiteColumnProjectTemplate-Projekt, um das Verhalten der Projektvorlage zu definieren:

- *AssemblyInfo.cs* oder *AssemblyInfo. vb*

- *Elements.xml*

- *SharePointProjectItem.spdata*

- *Feature1.feature*

- *Package.package*

- *SiteColumnProjectTemplate.vstemplate*

- *ProjectTemplate. csproj* oder *ProjectTemplate. vbproj*

  In den folgenden Verfahren fügen Sie einigen Dateien ersetzbare Parameter hinzu. Ein ersetzbarer Parameter ist ein Token, das mit einem Dollarzeichen ($) beginnt und endet. Wenn ein Benutzer mit dieser Projektvorlage ein Projekt erstellt, werden diese Parameter im neuen Projekt von Visual Studio automatisch durch bestimmte Werte ersetzt. Weitere Informationen finden Sie unter [Ersetzbare Parameter](../sharepoint/replaceable-parameters.md).

#### <a name="to-edit-the-assemblyinfocs-or-assemblyinfovb-file"></a>So bearbeiten Sie die Datei AssemblyInfo.cs oder die Datei AssemblyInfo.vb

1. Öffnen Sie im sitecolumnprojecttemplate-Projekt die Datei " *AssemblyInfo.cs* " oder " *AssemblyInfo. vb* ", und fügen Sie dann die folgende Anweisung am Anfang der Datei hinzu:

    ```vb
    Imports System.Security
    ```

    ```csharp
    using System.Security;
    ```

     Wenn die **Sandbox** -Projektmappeneigenschaft eines SharePoint-Projekts auf **true** festgelegt ist, fügt Visual Studio die der <xref:System.Security.AllowPartiallyTrustedCallersAttribute> AssemblyInfo-Codedatei hinzu. Der Namespace <xref:System.Security> wird von der Codedatei AssemblyInfo in Projektvorlage allerdings nicht standardmäßig importiert. Sie müssen diese **using** -oder **Imports** -Anweisung hinzufügen, um Kompilierungsfehler zu verhindern.

2. Speichern und schließen Sie die Datei.

#### <a name="to-edit-the-elementsxml-file"></a>So bearbeiten Sie die Datei Elements.xml

1. Ersetzen Sie im sitecolumnprojecttemplate-Projekt den Inhalt der *Elements.xml* -Datei durch den folgenden XML-Code.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">
      <Field ID="{$guid5$}"
          Name="$safeprojectname$"
          DisplayName="$projectname$"
          Type="Text"
          Group="Custom Columns">
      </Field>
    </Elements>
    ```

     Mit dem neuen XML wird ein `Field`-Element hinzugefügt, das den Namen der Websitespalte, den Basistyp sowie die Gruppe definiert, in der die Websitespalte im Katalog aufgelistet wird. Weitere Informationen zum Inhalt dieser Datei finden Sie unter [Field Definition Schema](/previous-versions/office/developer/sharepoint-2010/ms196289(v=office.14)).

2. Speichern und schließen Sie die Datei.

#### <a name="to-edit-the-sharepointprojectitemspdata-file"></a>So bearbeiten Sie die Datei SharePointProjectItem.spdata

1. Ersetzen Sie im sitecolumnprojecttemplate-Projekt den Inhalt der Datei *SharePointProjectItem. spdata* durch den folgenden XML-Code.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <ProjectItem Type="Contoso.SiteColumn" DefaultFile="Elements.xml"
                xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">
     <Files>
       <ProjectItemFile Source="Elements.xml" Target="$safeprojectname$\" Type="ElementManifest" />
     </Files>
   </ProjectItem>
   ```

    Durch das neue XML werden folgende Änderungen an der Datei vorgenommen:

   - Ändert das `Type`-Attribut des `ProjectItem`-Elements in dieselbe Zeichenfolge, die an <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> in der Projektdefinition übergeben wird (die `SiteColumnProjectItemTypeProvider`-Klasse, die Sie zuvor in dieser exemplarischen Vorgehensweise erstellt haben).

   - Entfernt die Attribute `SupportedTrustLevels` und `SupportedDeploymentScopes` aus dem `ProjectItem`-Element. Diese Attributwerte werden nicht benötigt, da die Vertrauensebenen und Bereitstellungsbereiche in der `SiteColumnProjectItemTypeProvider`-Klasse im Projekt ProjectItemTypeDefinition angegeben werden.

     Weitere Informationen zum Inhalt von *spdata* -Dateien finden Sie unter [Schema Referenz für SharePoint-Projekt Elemente](../sharepoint/sharepoint-project-item-schema-reference.md).

2. Speichern und schließen Sie die Datei.

#### <a name="to-edit-the-feature1feature-file"></a>So bearbeiten Sie die Datei Feature1.feature

1. Ersetzen Sie im sitecolumnprojecttemplate-Projekt den Inhalt der Datei *Feature1. Feature* durch den folgenden XML-Code.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <feature xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="$guid4$" featureId="$guid4$"
            imageUrl="" solutionId="00000000-0000-0000-0000-000000000000" title="Site Column Feature1" version=""
            deploymentPath="$SharePoint.Project.FileNameWithoutExtension$_$SharePoint.Feature.FileNameWithoutExtension$"
            xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/FeatureModel">
     <projectItems>
       <projectItemReference itemId="$guid2$" />
     </projectItems>
   </feature>
   ```

    Durch das neue XML werden folgende Änderungen an der Datei vorgenommen:

   - Ändert die Werte der Attribute `Id` und `featureId` des `feature`-Elements in `$guid4$`.

   - Ändert die Werte des `itemId`-Attributs für das `projectItemReference`-Element in `$guid2$`.

     Weitere Informationen zu *Funktions* Dateien finden Sie unter [Erstellen von Element Vorlagen und Projektvorlagen für SharePoint-Projekt Elemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

2. Speichern und schließen Sie die Datei.

#### <a name="to-edit-the-packagepackage-file"></a>So bearbeiten Sie die Datei Package.package

1. Ersetzen Sie im sitecolumnprojecttemplate-Projekt den Inhalt der Datei *Package. Package* durch den folgenden XML-Code.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <package xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0"
            Id="$guid3$" solutionId="$guid3$" resetWebServer="false" name="$safeprojectname$"
            xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/PackageModel">
     <features>
       <featureReference itemId="$guid4$" />
     </features>
   </package>
   ```

    Durch das neue XML werden folgende Änderungen an der Datei vorgenommen:

   - Ändert die Werte der Attribute `Id` und `solutionId` des `package`-Elements in `$guid3$`.

   - Ändert die Werte des `itemId`-Attributs für das `featureReference`-Element in `$guid4$`.

     Weitere Informationen zu *Paket* Dateien finden Sie unter [Erstellen von Element Vorlagen und Projektvorlagen für SharePoint-Projekt Elemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

2. Speichern und schließen Sie die Datei.

#### <a name="to-edit-the-sitecolumnprojecttemplatevstemplate-file"></a>So bearbeiten Sie die Datei sitecolumnprojecttemplate. vstemplate

1. Ersetzen Sie im SiteColumnProjectTemplate-Projekt die Inhalte der SiteColumnProjectTemplate.vstemplate-Datei durch einen der folgenden XML-Abschnitte.

   - Wenn Sie eine Visual C#-Projektvorlage erstellen, verwenden Sie das folgende XML:

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Project">
     <TemplateData>
       <Name>Site Column</Name>
       <Description>Creates a new site column in SharePoint</Description>
       <FrameworkVersion>3.5</FrameworkVersion>
       <ProjectType>CSharp</ProjectType>
       <CreateNewFolder>true</CreateNewFolder>
       <CreateInPlace>true</CreateInPlace>
       <ProvideDefaultName>true</ProvideDefaultName>
       <DefaultName>SiteColumn</DefaultName>
       <LocationField>Enabled</LocationField>
       <EnableLocationBrowseButton>true</EnableLocationBrowseButton>
       <PromptForSaveOnCreation>true</PromptForSaveOnCreation>
       <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
       <Icon>SiteColumnProjectTemplate.ico</Icon>
       <SortOrder>1000</SortOrder>
     </TemplateData>
     <TemplateContent>
       <Project TargetFileName="SharePointProject1.csproj" File="ProjectTemplate.csproj" ReplaceParameters="true">
         <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.feature">Feature1.feature</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.Template.xml">Feature1.template.xml</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.package">Package.package</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.Template.xml">Package.Template.xml</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\SharePointProjectItem.spdata">SharePointProjectItem.spdata</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\Elements.xml" OpenInEditor="true">Elements.xml</ProjectItem>
         <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>
       </Project>
     </TemplateContent>
   </VSTemplate>
   ```

   - Wenn Sie eine Visual Basic-Projektvorlage erstellen, verwenden Sie das folgende XML:

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Project">
     <TemplateData>
       <Name>Site Column</Name>
       <Description>Creates a new site column in SharePoint</Description>
       <FrameworkVersion>3.5</FrameworkVersion>
       <ProjectType>VisualBasic</ProjectType>
       <CreateNewFolder>true</CreateNewFolder>
       <CreateInPlace>true</CreateInPlace>
       <ProvideDefaultName>true</ProvideDefaultName>
       <DefaultName>SiteColumn</DefaultName>
       <LocationField>Enabled</LocationField>
       <EnableLocationBrowseButton>true</EnableLocationBrowseButton>
       <PromptForSaveOnCreation>true</PromptForSaveOnCreation>
       <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
       <Icon>SiteColumnProjectTemplate.ico</Icon>
       <SortOrder>1000</SortOrder>
     </TemplateData>
     <TemplateContent>
       <Project TargetFileName="SharePointProject1.vbproj" File="ProjectTemplate.vbproj" ReplaceParameters="true">
         <ProjectItem ReplaceParameters="true" TargetFileName="My Project\AssemblyInfo.vb">AssemblyInfo.vb</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.feature">Feature1.feature</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.Template.xml">Feature1.template.xml</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.package">Package.package</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.Template.xml">Package.Template.xml</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\SharePointProjectItem.spdata">SharePointProjectItem.spdata</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\Elements.xml" OpenInEditor="true">Elements.xml</ProjectItem>
         <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>
       </Project>
     </TemplateContent>
   </VSTemplate>
   ```

    Durch das neue XML werden folgende Änderungen an der Datei vorgenommen:

   - Legt das `Name` Element auf die **Spalte Wert Site** fest. (Dieser Name wird im Dialogfeld **Neues Projekt** angezeigt.)

   - Fügt die `ProjectItem`-Elemente für alle Dateien hinzu, die in den einzelnen Projektinstanzen enthalten sind.

   - Verwendet den-Namespace `http://schemas.microsoft.com/developer/vstemplate/2005` . Andere Projektdateien in dieser Projekt Mappe verwenden den- `http://schemas.microsoft.com/developer/msbuild/2003` Namespace. Daher werden XML-Schema-Warnmeldungen generiert, die Sie aber bei dieser exemplarischen Vorgehensweise ignorieren können.

     Weitere Informationen zum Inhalt von *VSTEMPLATE* -Dateien finden Sie unter [Schema Referenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md).

2. Speichern und schließen Sie die Datei.

#### <a name="to-edit-the-projecttemplatecsproj-or-projecttemplatevbproj-file"></a>So bearbeiten Sie die Datei "ProjectTemplate. csproj" oder "ProjectTemplate. vbproj"

1. Ersetzen Sie im sitecolumnprojecttemplate-Projekt den Inhalt der *ProjectTemplate. csproj* -Datei oder der *ProjectTemplate. vbproj* -Datei durch einen der folgenden XML-Abschnitte.

    - Wenn Sie eine Visual C#-Projektvorlage erstellen, verwenden Sie das folgende XML:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
      <PropertyGroup>
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
        <SchemaVersion>2.0</SchemaVersion>
        <ProjectGuid>{$guid1$}</ProjectGuid>
        <OutputType>Library</OutputType>
        <AppDesignerFolder>Properties</AppDesignerFolder>
        <RootNamespace>$safeprojectname$</RootNamespace>
        <AssemblyName>$safeprojectname$</AssemblyName>
        <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>
        <FileAlignment>512</FileAlignment>
        <ProjectTypeGuids>{BB1F664B-9266-4fd6-B973-E1E44974B511};{14822709-B5A1-4724-98CA-57A101D1B079};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
        <DebugSymbols>true</DebugSymbols>
        <DebugType>full</DebugType>
        <Optimize>false</Optimize>
        <OutputPath>bin\Debug\</OutputPath>
        <DefineConstants>DEBUG;TRACE</DefineConstants>
        <ErrorReport>prompt</ErrorReport>
        <WarningLevel>4</WarningLevel>
        <UseVSHostingProcess>false</UseVSHostingProcess>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">
        <DebugType>pdbonly</DebugType>
        <Optimize>true</Optimize>
        <OutputPath>bin\Release\</OutputPath>
        <DefineConstants>TRACE</DefineConstants>
        <ErrorReport>prompt</ErrorReport>
        <WarningLevel>4</WarningLevel>
      </PropertyGroup>
      <PropertyGroup>
        <SignAssembly>true</SignAssembly>
        <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>
      </PropertyGroup>
      <ItemGroup>
        <Reference Include="System" />
        <Reference Include="System.Core" />
        <Reference Include="System.Data" />
        <Reference Include="System.Data.DataSetExtensions" />
        <Reference Include="System.Web" />
        <Reference Include="System.Xml" />
        <Reference Include="System.Xml.Linq" />
        <Reference Include="Microsoft.SharePoint" />
        <Reference Include="Microsoft.SharePoint.Security" />
      </ItemGroup>
      <ItemGroup>
        <Compile Include="Properties\AssemblyInfo.cs" />
      </ItemGroup>
      <ItemGroup>
        <None Include="Field1\SharePointProjectItem.spdata">
          <SharePointProjectItemId>{$guid2$}</SharePointProjectItemId>
        </None>
        <None Include="Field1\Elements.xml" />
      </ItemGroup>
      <ItemGroup>
        <None Include="key.snk" />
        <None Include="Package\Package.package">
          <PackageId>{$guid3$}</PackageId>
        </None>
        <None Include="Package\Package.Template.xml">
          <DependentUpon>Package.package</DependentUpon>
        </None>
        <None Include="Features\Feature1\Feature1.feature">
          <FeatureId>{$guid4$}</FeatureId>
        </None>
        <None Include="Features\Feature1\Feature1.Template.xml">
          <DependentUpon>Feature1.feature</DependentUpon>
        </None>
      </ItemGroup>
      <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
      <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SharePointTools\Microsoft.VisualStudio.SharePoint.targets" />
    </Project>
    ```

    1. Wenn Sie eine Visual Basic-Projektvorlage erstellen, verwenden Sie das folgende XML:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
      <PropertyGroup>
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
        <ProductVersion>
        </ProductVersion>
        <SchemaVersion>
        </SchemaVersion>
        <ProjectGuid>{$guid1$}</ProjectGuid>
        <OutputType>Library</OutputType>
        <RootNamespace>$safeprojectname$</RootNamespace>
        <AssemblyName>$safeprojectname$</AssemblyName>
        <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>
        <FileAlignment>512</FileAlignment>
        <ProjectTypeGuids>{BB1F664B-9266-4fd6-B973-E1E44974B511};{D59BE175-2ED0-4C54-BE3D-CDAA9F3214C8};{F184B08F-C81C-45F6-A57F-5ABD9991F28F}</ProjectTypeGuids>
        <OptionExplicit>On</OptionExplicit>
        <OptionCompare>Binary</OptionCompare>
        <OptionStrict>Off</OptionStrict>
        <OptionInfer>On</OptionInfer>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
        <DebugSymbols>true</DebugSymbols>
        <DebugType>full</DebugType>
        <DefineDebug>true</DefineDebug>
        <DefineTrace>true</DefineTrace>
        <OutputPath>bin\Debug\</OutputPath>
        <WarningLevel>4</WarningLevel>
        <UseVSHostingProcess>false</UseVSHostingProcess>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">
        <DebugType>pdbonly</DebugType>
        <DefineDebug>false</DefineDebug>
        <DefineTrace>true</DefineTrace>
        <Optimize>true</Optimize>
        <OutputPath>bin\Release\</OutputPath>
        <UseVSHostingProcess>false</UseVSHostingProcess>
      </PropertyGroup>
      <PropertyGroup>
        <SignAssembly>true</SignAssembly>
        <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>
      </PropertyGroup>
      <ItemGroup>
        <Reference Include="System" />
        <Reference Include="System.Core" />
        <Reference Include="System.Data" />
        <Reference Include="System.Data.DataSetExtensions" />
        <Reference Include="System.Xml" />
        <Reference Include="System.Xml.Linq" />
        <Reference Include="Microsoft.SharePoint" />
        <Reference Include="Microsoft.SharePoint.Security" />
      </ItemGroup>
      <ItemGroup>
        <Import Include="Microsoft.VisualBasic" />
        <Import Include="System" />
        <Import Include="System.Collections" />
        <Import Include="System.Collections.Generic" />
        <Import Include="System.Data" />
        <Import Include="System.Diagnostics" />
        <Import Include="System.Linq" />
        <Import Include="System.Xml.Linq" />
        <Import Include="Microsoft.SharePoint" />
        <Import Include="Microsoft.SharePoint.Security" />
      </ItemGroup>
      <ItemGroup>
        <Compile Include="My Project\AssemblyInfo.vb" />
      </ItemGroup>
      <ItemGroup>
        <AppDesigner Include="My Project\" />
      </ItemGroup>
      <ItemGroup>
        <None Include="Features\Feature1\Feature1.feature">
          <FeatureId>{$guid4$}</FeatureId>
        </None>
        <None Include="Field1\SharePointProjectItem.spdata">
          <SharePointProjectItemId>{$guid2$}</SharePointProjectItemId>
        </None>
        <None Include="key.snk" />
        <None Include="Package\Package.package">
          <PackageId>{$guid3$}</PackageId>
        </None>
        <None Include="Package\Package.Template.xml">
          <DependentUpon>Package.package</DependentUpon>
        </None>
      </ItemGroup>
      <ItemGroup>
        <None Include="Features\Feature1\Feature1.Template.xml">
          <DependentUpon>Feature1.feature</DependentUpon>
        </None>
        <None Include="Field1\Elements.xml" />
      </ItemGroup>
      <Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />
      <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SharePointTools\Microsoft.VisualStudio.SharePoint.targets" />
    </Project>
    ```

     Durch das neue XML werden folgende Änderungen an der Datei vorgenommen:

    - Verwendet das `TargetFrameworkVersion`-Element, um .NET Framework 3.5 und nicht .NET Framework 4.5 festzulegen.

    - Fügt die Elemente `SignAssembly` und `AssemblyOriginatorKeyFile` hinzu, um die Projektausgabe zu signieren.

    - Fügt die `Reference`-Elemente für Assemblyverweise hinzu, die von SharePoint-Projekten verwendet werden.

    - Fügt der Standarddatei im Projekt Elemente hinzu, z. b. *Elements.xml* und *SharePointProjectItem. spdata*.

2. Speichern und schließen Sie die Datei.

## <a name="create-a-vsix-package-to-deploy-the-project-template"></a>Erstellen eines VSIX-Pakets zum Bereitstellen der Projektvorlage
 Verwenden Sie zum Bereitstellen der Erweiterung das VSIX-Projekt in der Projekt Mappe " **sitecolumnprojectitem** ", um ein VSIX-Paket zu erstellen. Konfigurieren Sie zuerst das VSIX-Paket, indem Sie die im VSIX-Projekt enthaltene Datei "source.extension.vsixmanifest" ändern. Erstellen Sie anschließend das VSIX-Paket, indem Sie die Lösung erstellen.

#### <a name="to-configure-and-create-the-vsix-package"></a>So erstellen und konfigurieren Sie das VSIX-Paket

1. Öffnen Sie in **Projektmappen-Explorer** im Projekt **sitecolumnprojectitem** die Datei "Source. Extension. vsixmanifest" im Manifest-Editor.

     Die Datei "source.extension.vsixmanifest" bildet die Grundlage für die Datei "extension.vsixmanifest", die für alle VSIX-Pakete erforderlich ist. Weitere Informationen zu dieser Datei finden Sie in der [Referenz zu VSIX-Erweiterungs Schema 1,0](/previous-versions/dd393700(v=vs.110)).

2. Geben Sie im Feld **Produkt Name den Namen** **Site Column** ein.

3. **Geben Sie** im Feld **Autor** den Text "" ein.

4. Geben Sie im Feld **Beschreibung** **ein SharePoint-Projekt zum Erstellen von Website Spalten ein**.

5. Wählen Sie die Registerkarte **Assets** aus, und klicken Sie dann auf die Schaltfläche **neu** .

     Das Dialogfeld **Neues Objekt hinzufügen** wird geöffnet.

6. Wählen Sie in der Liste **Typ** den Eintrag **Microsoft. VisualStudio. ProjectTemplate** aus.

    > [!NOTE]
    > Dieser Wert entspricht dem `ProjectTemplate`-Element in der Datei "extension.vsixmanifest". Durch dieses Element wird der Unterordner im VSIX-Paket identifiziert, der die Projektvorlage enthält. Weitere Informationen finden Sie unter [ProjectTemplate-Element (VSX-Schema)](/previous-versions/visualstudio/visual-studio-2010/dd393735\(v\=vs.100\)).

7. Wählen Sie  in der Liste Quelle **ein Projekt in der aktuellen Projekt** Mappe aus.

8. Wählen Sie in der Liste **Projekt** die Option **sitecolumnprojecttemplate** aus, und klicken Sie dann auf die Schaltfläche **OK** .

9. Klicken Sie erneut auf die Schaltfläche **neu** .

     Das Dialogfeld **Neues Objekt hinzufügen** wird geöffnet.

10. Wählen Sie in der Liste **Typ** den Eintrag **Microsoft. VisualStudio. MEFComponent** aus.

    > [!NOTE]
    > Dieser Wert entspricht dem `MefComponent`-Element in der Datei "extension.vsixmanifest". Von diesem Element wird der Name einer Erweiterungsassembly im VSIX-Paket angegeben. Weitere Informationen finden Sie unter [MEFComponent-Element (VSX-Schema)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

11. Wählen Sie  in der Liste Quelle **ein Projekt in der aktuellen Projekt** Mappe aus.

12. Wählen Sie in der Liste **Projekt** die Option **projectItemTypeDefinition** aus, und klicken Sie dann auf die Schaltfläche **OK** .

13. Wählen Sie in der Menüleiste Buildprojektmappe **Erstellen** aus, und vergewissern Sie sich,  >  dass das Projekt ohne Fehler kompiliert wird.

## <a name="test-the-project-template"></a>Testen der Projektvorlage
 Jetzt können Sie die Projektvorlage testen. Debuggen Sie die Projektmappe SiteColumnProjectItem zunächst in der experimentellen Instanz von Visual Studio. Testen Sie anschließend das **Website Spalten** Projekt in der experimentellen Instanz von Visual Studio. Erstellen und führen Sie zum Schluss das SharePoint-Projekt aus, um sicherzustellen, dass die Websitespalte ordnungsgemäß funktioniert.

#### <a name="to-start-debugging-the-solution"></a>So debuggen Sie die Projektmappe

1. Starten Sie Visual Studio erneut mit Administratoranmeldeinformationen, und öffnen Sie dann die Projektmappe "SiteColumnProjectItem".

2. Fügen Sie in der Codedatei sitecolumnprojectitemtypeprovider der ersten Codezeile in der-Methode einen Haltepunkt hinzu `InitializeType` , und drücken Sie dann die Taste **F5** , um das Debuggen zu starten.

     Die Erweiterung wird unter %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Websitespalte\1.0 installiert, und eine experimentelle Instanz von Visual Studio wird gestartet. Sie testen das Projektelement in dieser Instanz von Visual Studio.

#### <a name="to-test-the-project-in-visual-studio"></a>So testen Sie das Projekt in Visual Studio

1. Wählen Sie in der experimentellen Instanz von Visual Studio in der Menüleiste **Datei**  >  **neu**  >  **Projekt** aus.

2. Erweitern Sie den Knoten **Visual c#** oder **Visual Basic** (abhängig von der von der Projektvorlage unterstützten Sprache), erweitern Sie den Knoten **SharePoint** , und wählen Sie dann den Knoten **2010** aus.

3. Wählen Sie in der Liste der Projektvorlagen die Vorlage **Website Spalte** aus.

4. Geben Sie im Feld **Name den Namen** **sitecolumntest** ein, und klicken Sie dann auf die Schaltfläche **OK** .

     In **Projektmappen-Explorer** wird ein neues Projekt mit einem Projekt Element mit dem Namen " **field1**" angezeigt.

5. Vergewissern Sie sich, dass der Code in der anderen Instanz von Visual Studio an dem Haltepunkt anhält, den Sie zuvor in der Methode festgelegt `InitializeType` haben, und drücken Sie dann die Taste **F5** , um das Debuggen des Projekts fortzusetzen.

6. Wählen Sie in **Projektmappen-Explorer** den Knoten **field1** aus, und wählen Sie dann die **F4** -Taste.

     Das Fenster **Eigenschaften** wird geöffnet.

7. Vergewissern Sie sich, dass in der Liste Eigenschaften die Eigenschaft **Beispiel** Eigenschaft angezeigt wird.

#### <a name="to-test-the-site-column-in-sharepoint"></a>So testen Sie die Websitespalte in SharePoint

1. Wählen Sie in **Projektmappen-Explorer** den Knoten **sitecolumntest** aus.

2. Geben Sie im Fenster **Eigenschaften** im Textfeld neben der Eigenschaft **Website-URL** ein **http://localhost** .

     Dadurch wird auf dem Entwicklungscomputer die lokale SharePoint-Website angegeben, die zum Debuggen verwendet werden soll.

    > [!NOTE]
    > Die **Website-URL** -Eigenschaft ist standardmäßig leer, da die Projektvorlage für die Website Spalte keinen Assistenten zum Erfassen dieses Werts bereitstellt, wenn das Projekt erstellt wird. Weitere Informationen zum Hinzufügen eines Assistenten, der den Entwickler zu diesem Wert auffordert und dann diese Eigenschaft im neuen Projekt konfiguriert, finden Sie unter Exemplarische Vorgehensweise [: Erstellen eines Website Spalten-Projekt Elements mit einer Projektvorlage, Teil 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

3. Drücken Sie die Taste **F5**.

     Die Spalte Site wird verpackt und auf der SharePoint-Website bereitgestellt, die in der **Website-URL** -Eigenschaft des Projekts angegeben ist. Im Webbrowser wird die Standardseite dieser Website geöffnet.

    > [!NOTE]
    > Wenn das Dialogfeld **Skript Debugging deaktiviert** angezeigt wird, klicken Sie auf die Schaltfläche **Ja** , um das Debuggen des Projekts fortzusetzen.

4. Wählen Sie im Menü **Website Aktionen** die Option **Website Einstellungen** aus.

5. Wählen Sie auf der Seite **Site Einstellungen** unter der Liste **Galerien** den Link **Site Columns** aus.

6. Überprüfen Sie in der Liste der Website Spalten, ob eine **benutzerdefinierte Spalten** Gruppe eine Spalte mit dem Namen **sitecolumntest** enthält.

7. Schließen Sie den Webbrowser.

## <a name="clean-up-the-development-computer"></a>Bereinigen des Entwicklungs Computers
 Nachdem Sie die Tests des Projekts abgeschlossen haben, entfernen Sie die Projektvorlage aus der experimentellen Instanz von Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>So bereinigen Sie den Entwicklungscomputer

1. Wählen Sie in der experimentellen Instanz von Visual Studio auf der Menüleiste Extras   >  **Erweiterungen und Updates** aus.

     Das Dialogfeld **Erweiterungen und Updates** wird geöffnet.

2. Wählen Sie in der Liste der Erweiterungen die **Website-Spalten** Erweiterung aus, und klicken Sie dann auf die Schaltfläche **deinstallieren** .

3. Wählen Sie im angezeigten Dialogfeld die Schaltfläche **Ja** aus, um zu bestätigen, dass Sie die Erweiterung deinstallieren möchten.

4. Wählen Sie die Schaltfläche **Schließen** aus, um die Installation abzuschließen.

5. Schließen Sie beide Instanzen von Visual Studio (die experimentelle Instanz und die Instanz von Visual Studio, in der die SiteColumnProjectItem-Projektmappe geöffnet ist).

## <a name="next-steps"></a>Nächste Schritte
 Nachdem Sie diese exemplarische Vorgehensweise abgeschlossen haben, können Sie der Projektvorlage einen Assistenten hinzufügen. Beim Erstellen eines Websitespaltenprojekts wird der Benutzer vom Assistenten aufgefordert, die URL der Website anzugeben, die zum Debuggen verwendet werden soll. Darüber hinaus muss vom Benutzer angegeben werden, ob die neue Projektmappe als Sandkastenlösung bereitgestellt wird. Anschließend wird das Projekt vom Assistenten mit diesen Informationen konfiguriert. Der Assistent sammelt außerdem Informationen über die Spalte (z. b. den Basistyp und die Gruppe, in der die Spalte in der Website Spalten Galerie aufgeführt werden soll) und fügt diese Informationen der *Elements.xml* -Datei im neuen Projekt hinzu. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Erstellen eines Projekt Elements für eine Website Spalte mit einer Projektvorlage, Teil 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

## <a name="see-also"></a>Weitere Informationen

- [Exemplarische Vorgehensweise: Erstellen eines Projekt Elements für eine Website Spalte mit einer Projektvorlage, Teil 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Definieren von benutzerdefinierten SharePoint-Projekt Elementtypen](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Erstellen von Element Vorlagen und Projektvorlagen für SharePoint-Projekt Elemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Speichern von Daten in Erweiterungen des SharePoint-Projekt Systems](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [Zuordnen von benutzerdefinierten Daten zu SharePoint-Tools-Erweiterungen](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)