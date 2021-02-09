---
title: Erstellen eines grundlegenden Projekt Systems, Teil 2 | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie einem Projekt, das in einem vorherigen Artikel erstellt wurde, eine Visual Studio-Vorlage, eine Eigenschaften Seite und andere Funktionen hinzufügen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ceef95f90d2f54ad7b527ccc8c00322c77491fb7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853151"
---
# <a name="create-a-basic-project-system-part-2"></a>Erstellen eines grundlegenden Projekt Systems, Teil 2
In der ersten exemplarischen Vorgehensweise dieser Reihe, der [Erstellung eines grundlegenden Projekt Systems, Teil 1](../extensibility/creating-a-basic-project-system-part-1.md), wird gezeigt, wie ein einfaches Projekt System erstellt wird. In dieser exemplarischen Vorgehensweise wird das grundlegende Projekt System durch Hinzufügen einer Visual Studio-Vorlage, einer Eigenschaften Seite und anderer Features erstellt. Sie müssen die erste Exemplarische Vorgehensweise durchlaufen, bevor Sie diese starten.

In dieser exemplarischen Vorgehensweise wird erläutert, wie Sie einen Projekttyp erstellen, der die Projektdatei Erweiterung *. MyProj* enthält. Um die exemplarische Vorgehensweise abzuschließen, müssen Sie keine eigene Sprache erstellen, da die exemplarische Vorgehensweise aus dem vorhandenen Visual c#-Projekt System aufführt.

In dieser exemplarischen Vorgehensweise wird erläutert, wie Sie diese Aufgaben ausführen:

- Erstellen Sie eine Visual Studio-Vorlage.

- Stellen Sie eine Visual Studio-Vorlage bereit.

- Erstellen Sie im Dialogfeld **Neues Projekt** einen untergeordneten Projekttyp.

- Aktivieren Sie die Parameter Ersetzung in der Visual Studio-Vorlage.

- Erstellen Sie eine Projekteigenschaften Seite.

> [!NOTE]
> Die Schritte in dieser exemplarischen Vorgehensweise basieren auf einem c#-Projekt. Mit Ausnahme von Besonderheiten wie Dateinamen Erweiterungen und Code können Sie jedoch die gleichen Schritte für ein Visual Basic Projekt ausführen.

## <a name="create-a-visual-studio-template"></a>Erstellen einer Visual Studio-Vorlage
- [Erstellen eines grundlegenden Projekt Systems, Teil 1](../extensibility/creating-a-basic-project-system-part-1.md) zeigt, wie eine einfache Projektvorlage erstellt und dem Projekt System hinzugefügt wird. Außerdem wird gezeigt, wie Sie diese Vorlage in Visual Studio registrieren, indem Sie das- <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> Attribut verwenden, das den vollständigen Pfad des Ordners " *\\ \\ templates\projects\simpleproject* " in der Systemregistrierung schreibt.

Mithilfe einer Visual Studio-Vorlage (*VSTEMPLATE* -Datei) anstelle einer grundlegenden Projektvorlage können Sie steuern, wie die Vorlage im Dialogfeld **Neues Projekt** angezeigt wird und wie Vorlagen Parameter ersetzt werden. Eine *VSTEMPLATE* -Datei ist eine XML-Datei, die beschreibt, wie Quelldateien eingeschlossen werden, wenn ein Projekt mithilfe der Projekt System Vorlage erstellt wird. Das Projekt System selbst wird erstellt, indem die *VSTEMPLATE* -Datei und die Quelldateien in einer *ZIP* -Datei gesammelt und bereitgestellt werden, indem die *ZIP* -Datei an einen Speicherort kopiert wird, der Visual Studio bekannt ist. Dieser Prozess wird weiter unten in dieser exemplarischen Vorgehensweise ausführlicher erläutert.

1. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Öffnen Sie in die simpleproject-Projekt Mappe, die Sie erstellt haben, indem Sie das [grundlegende Projekt System, Teil 1, erstellen](../extensibility/creating-a-basic-project-system-part-1.md).

2. Suchen Sie in der Datei *SimpleProjectPackage.cs* das Attribut ProvideProjectFactory. Ersetzen Sie den zweiten Parameter (Projektname) durch Null und den vierten Parameter (den Pfad zum Projektvorlagen Ordner) durch ". \\ \Nullpath "wie folgt.

    ```
    [ProvideProjectFactory(typeof(SimpleProjectFactory), null,
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
        ".\\NullPath",
    LanguageVsTemplate = "SimpleProject")]
    ```

3. Fügen Sie eine XML-Datei mit dem Namen *simpleproject. vstemplate* zum Ordner *\\ templates\project\simpleproject \\* hinzu.

4. Ersetzen Sie den Inhalt von *simpleproject. vstemplate* durch den folgenden Code.

    ```xml
    <VSTemplate Version="2.0.0" Type="Project"
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
      <TemplateData>
        <Name>SimpleProject Application</Name>
        <Description>
          A project for creating a SimpleProject application
        </Description>
        <Icon>SimpleProject.ico</Icon>
        <ProjectType>SimpleProject</ProjectType>
      </TemplateData>
      <TemplateContent>
        <Project File="SimpleProject.myproj" ReplaceParameters="true">
          <ProjectItem ReplaceParameters="true" OpenInEditor="true">
            Program.cs
          </ProjectItem>
          <ProjectItem ReplaceParameters="true" OpenInEditor="false">
            AssemblyInfo.cs
          </ProjectItem>
        </Project>
      </TemplateContent>
    </VSTemplate>
    ```

5. Wählen Sie im Fenster **Eigenschaften** alle fünf Dateien im Ordner *\\ templates\project\simpleproject \\* aus, und legen Sie die Buildaktion auf **zipproject** fest. 

    ![Einfacher Projektordner](../extensibility/media/simpproj2.png "SimpProj2")

    Der \<TemplateData> -Abschnitt bestimmt den Speicherort und die Darstellung des simpleproject-Projekt Typs im Dialogfeld **Neues Projekt** wie folgt:

- Das- \<Name> Element benennt die Projektvorlage als simpleproject-Anwendung.

- Das- \<Description> Element enthält die Beschreibung, die im Dialogfeld **Neues Projekt** angezeigt wird, wenn die Projektvorlage ausgewählt wird.

- Das- \<Icon> Element gibt das Symbol an, das in Verbindung mit dem Projekttyp simpleproject angezeigt wird.

- Das- \<ProjectType> Element benennt den Projekttyp im Dialogfeld **Neues Projekt** . Dieser Name ersetzt den Project Name-Parameter des providebug ProjectFactory-Attributs.

  > [!NOTE]
  > Das- \<ProjectType> Element muss mit dem- `LanguageVsTemplate` Argument des- `ProvideProjectFactory` Attributs in der SimpleProjectPackage.cs-Datei identisch sein.

  \<TemplateContent>In diesem Abschnitt werden diese Dateien beschrieben, die beim Erstellen eines neuen Projekts generiert werden:

- *Simpleproject. MyProj*

- *Program.cs*

- *AssemblyInfo.cs*

  Alle drei Dateien sind `ReplaceParameters` auf true festgelegt, was die Parameter Ersetzung ermöglicht. Die Datei *Program.cs* ist `OpenInEditor` auf true festgelegt, wodurch die Datei im Code-Editor geöffnet wird, wenn ein Projekt erstellt wird.

  Weitere Informationen zu den Elementen im Visual Studio-Vorlagen Schema finden Sie in der [Schema Referenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md).

> [!NOTE]
> Wenn ein Projekt mehr als eine Visual Studio-Vorlage enthält, befindet sich jede Vorlage in einem separaten Ordner. Für jede Datei in diesem Ordner muss die **Buildaktion** auf **zipproject** festgelegt sein.

## <a name="adding-a-minimal-vsct-file"></a>Hinzufügen einer minimalen vsct-Datei
 Visual Studio muss im Setup Modus ausgeführt werden, um eine neue oder geänderte Visual Studio-Vorlage zu erkennen. Der Setup Modus erfordert, dass eine *vsct* -Datei vorhanden ist. Daher müssen Sie dem Projekt eine minimale *vsct* -Datei hinzufügen.

1. Fügen Sie dem Projekt simpleproject eine XML-Datei mit dem Namen *simpleproject. vsct* hinzu.

2. Ersetzen Sie den Inhalt der *simpleproject. vsct* -Datei durch den folgenden Code.

    ```
    <?xml version="1.0" encoding="utf-8" ?>
    <CommandTable
      xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">
    </CommandTable>
    ```

3. Legen Sie die **Buildaktion** dieser Datei auf **VSCTCompile** fest. Dies ist nur in der *csproj* -Datei möglich, nicht im **Eigenschaften** Fenster. Stellen Sie sicher, dass die **Buildaktion** dieser Datei zu diesem Zeitpunkt auf " **None** " festgelegt ist.

    1. Klicken Sie mit der rechten Maustaste auf den Knoten simpleproject, und klicken Sie dann auf **simpleproject. csproj bearbeiten**.

    2. Suchen Sie in der *csproj* -Datei das Element *simpleproject. vsct* .

        ```
        <None Include="SimpleProject.vsct" />
        ```

    3. Ändern Sie die Buildaktion in **VSCTCompile**.

        ```
        <VSCTCompile Include="SimpleProject.vsct" />
        ```

    4. die Projektdatei, und schließen Sie den Editor.

    5. Speichern Sie den simpleproject-Knoten, und klicken Sie dann in der **Projektmappen-Explorer** auf **Projekt erneut laden**.

## <a name="examine-the-visual-studio-template-build-steps"></a>Überprüfen der Buildschritte für die Visual Studio-Vorlage
 Das VSPackage-Projektbuildsystem führt Visual Studio in der Regel im Setup Modus aus, wenn die *VSTEMPLATE* -Datei geändert wird oder das Projekt, das die *VSTEMPLATE* -Datei enthält, neu erstellt wird. Sie können folgendermaßen vorgehen, indem Sie den ausführlichkeits Grad von MSBuild auf normal oder höher festlegen.

1. Klicken Sie im Menü **Extras** auf **Optionen**.

2. Erweitern Sie den Knoten **Projekte und Projekt** Mappen, und wählen Sie dann **Erstellen und ausführen** aus.

3. Legen Sie **Ausführlichkeit der MSBuild-Projektbuildausgabe** auf **Normal** fest. Klicken Sie auf **OK**.

4. Erstellen Sie das Projekt simpleproject neu.

    Der Buildschritt zum Erstellen der *ZIP* -Projektdatei sollte dem folgenden Beispiel ähneln.

```
ZipProjects:
1>  Zipping ProjectTemplates
1>  Zipping <path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip...
1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "<%LOCALAPPDATA%>\Microsoft\VisualStudio\14.0Exp\ProjectTemplates\\\\SimpleProject.zip".
1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "bin\Debug\\ProjectTemplates\\\\SimpleProject.zip".
1>  SimpleProject -> <path>\SimpleProject\SimpleProject\bin\Debug\ProjectTemplates\SimpleProject.zip
1>ZipItems:
1>  Zipping ItemTemplates
1>  SimpleProject ->
```

## <a name="deploy-a-visual-studio-template"></a>Bereitstellen einer Visual Studio-Vorlage
Visual Studio-Vorlagen enthalten keine Pfadinformationen. Daher muss die *ZIP* -Datei der Vorlage an einem Speicherort bereitgestellt werden, der Visual Studio bekannt ist. Der Speicherort des Ordners ProjectTemplates ist in der Regel *<% LocalAppData% > \microsoft\visualstudio\14.0exp\projecttemplates*.

Zum Bereitstellen der projektfactory muss das Installationsprogramm über Administratorrechte verfügen. Es werden Vorlagen unter dem Visual Studio-Installations Knoten bereitgestellt: *. ..\Microsoft Visual Studio 14,0 \ Common7\IDE\ProjectTemplates*.

## <a name="test-a-visual-studio-template"></a>Testen einer Visual Studio-Vorlage
Testen Sie Ihre projektfactory, um zu sehen, ob Sie mithilfe der Visual Studio-Vorlage eine Projekt Hierarchie erstellt.

1. Setzen Sie die experimentelle Instanz von Visual Studio SDK zurück.

    An [!INCLUDE[win7](../debugger/includes/win7_md.md)] : Suchen Sie im **Startmenü** den Ordner **Microsoft Visual Studio/Microsoft Visual Studio SDK/Tools** , und wählen Sie dann **Microsoft Visual Studio experimentelle Instanz zurücksetzen** aus.

    Bei späteren Versionen von Windows: Geben Sie auf dem **Start** Bildschirm **die Microsoft Visual Studio \<version> experimentelle Instanz zurücksetzen** ein.

2. Ein Eingabe Aufforderungs Fenster wird angezeigt. Wenn Sie die Wörter **zum Fortfahren auf eine beliebige Taste drücken**, klicken Sie auf die **Eingabe** Taste. Öffnen Sie Visual Studio, nachdem das Fenster geschlossen wurde.

3. Erstellen Sie das Projekt simpleproject neu, und starten Sie das Debugging. Die experimentelle Instanz wird geöffnet.

4. Erstellen Sie in der experimentellen Instanz ein simpleproject-Projekt. Wählen Sie im Dialogfeld **Neues Projekt** die Option **simpleproject** aus.

5. Eine neue Instanz von simpleproject sollte angezeigt werden.

    ![Einfache neue Projekt Instanz](../extensibility/media/simpproj2_newproj.png "SimpProj2_NewProj")

    ![Meine Projekt neue Instanz](../extensibility/media/simpproj2_myproj.png "SimpProj2_MyProj")

## <a name="create-a-project-type-child-node"></a>Erstellen eines untergeordneten Projekt Typs
Sie können einem Projekttyp Knoten im Dialogfeld **Neues Projekt** einen untergeordneten Knoten hinzufügen. Für den Projekttyp simpleproject können Sie z. b. untergeordnete Knoten für Konsolen Anwendungen, Fenster Anwendungen, Webanwendungen usw. haben.

Untergeordnete Knoten werden erstellt, indem die Projektdatei geändert und den Elementen untergeordnete Knoten hinzugefügt werden \<OutputSubPath> \<ZipProject> . Wenn eine Vorlage während des Builds oder der Bereitstellung kopiert wird, wird jeder untergeordnete Knoten zu einem Unterordner des Ordners für Projektvorlagen.

In diesem Abschnitt wird gezeigt, wie ein untergeordneter Konsolen Knoten für den Projekttyp simpleproject erstellt wird.

1. Benennen Sie den Ordner *\\ templates\project\simpleproject \\* in *\\ templates\project\consoleapp \\* um.

2. Wählen Sie im Fenster **Eigenschaften** alle fünf Dateien im Ordner *\\ templates\project\consoleapp \\* aus, und stellen Sie sicher, dass die Buildaktion auf **zipproject** festgelegt ist. 

3. Fügen Sie in der simpleproject. VSTEMPLATE-Datei am Ende des \<TemplateData> Abschnitts direkt vor dem schließenden-Tag die folgende Zeile hinzu.

    ```
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
    ```

    Dadurch wird die Konsolen Anwendungs Vorlage sowohl im untergeordneten Knoten der Konsole als auch im übergeordneten Knoten simpleproject angezeigt, der eine Ebene oberhalb des untergeordneten Knotens ist.

4. Speichern Sie die *simpleproject. vstemplate* -Datei.

5. Fügen Sie in der *csproj* -Datei \<OutputSubPath> jedem der zipproject-Elemente hinzu. Entladen Sie das Projekt wie zuvor, und bearbeiten Sie die Projektdatei.

6. Suchen Sie die- \<ZipProject> Elemente. Fügen Sie für jedes \<ZipProject> Element ein \<OutputSubPath> Element hinzu, und geben Sie ihm die Wert Konsole. Das zipproject-

    ```
    <ZipProject Include="Templates\Projects\ConsoleApp\AssemblyInfo.cs">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    <ZipProject Include="Templates\Projects\ConsoleApp\Program.cs">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.myproj">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.vstemplate">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.ico">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    ```

7. Fügen Sie \<PropertyGroup> der Projektdatei Folgendes hinzu:

    ```
    <PropertyGroup>
      <VsTemplateLanguage>SimpleProject</VsTemplateLanguage>
    </PropertyGroup>
    ```

8. Speichern Sie die Projektdatei, und laden Sie das Projekt erneut.

## <a name="test-the-project-type-child-node"></a>Testen des untergeordneten Knotens "Project Type"
Testen Sie die geänderte Projektdatei, um festzustellen, ob der untergeordnete **Konsolen** Knoten im Dialogfeld **Neues Projekt** angezeigt wird.

1. Führen Sie das Tool **Microsoft Visual Studio experimentelle Instanz zurücksetzen** aus.

2. Erstellen Sie das Projekt simpleproject neu, und starten Sie das Debugging. Die experimentelle Instanz sollte angezeigt werden.

3. Klicken Sie im Dialogfeld **Neues Projekt** auf den Knoten **simpleproject** . Die Vorlage " **Konsolenanwendung** " sollte im Bereich " **Vorlagen** " angezeigt werden.

4. Erweitern Sie den Knoten **simpleproject** . Der untergeordnete **Konsolen** Knoten sollte angezeigt werden. Die **Anwendungs Vorlage simpleproject** wird weiterhin im **Vorlagen** Bereich angezeigt.

5. Klicken Sie auf **Abbrechen** und Debuggen beenden.

    ![Einfaches projekttrollup](../extensibility/media/simpproj2_rollup.png "SimpProj2_Rollup")

    ![Konsolen Knoten "Simple Project"](../extensibility/media/simpproj2_subfolder.png "SimpProj2_Subfolder")

## <a name="substitute-project-template-parameters"></a>Projektvorlagen Parameter ersetzen
- Beim [Erstellen eines grundlegenden Projekt Systems, Teil 1, wurde gezeigt,](../extensibility/creating-a-basic-project-system-part-1.md) wie die-Methode überschrieben wird, `ProjectNode.AddFileFromTemplate` um eine grundlegende Art von Vorlagen Parameter Ersetzung durchzuführen In diesem Abschnitt erfahren Sie, wie Sie anspruchsvollere Visual Studio-Vorlagen Parameter verwenden.

Wenn Sie ein Projekt erstellen, indem Sie eine Visual Studio-Vorlage im Dialogfeld **Neues Projekt** verwenden, werden Vorlagen Parameter durch Zeichen folgen ersetzt, um das Projekt anzupassen. Ein Vorlagen Parameter ist ein spezielles Token, das mit einem Dollarzeichen beginnt und endet, z. b. $time $. Die folgenden beiden Parameter sind besonders nützlich, um Anpassungen in Projekten zu ermöglichen, die auf der Vorlage basieren:

- $Guid [1-10] $ wird durch eine neue GUID ersetzt. Sie können bis zu 10 eindeutige GUIDs angeben, z. b. $GUID $1.

- $safeprojectname $ ist der Name, der von einem Benutzer im Dialogfeld **Neues Projekt** bereitgestellt wird, um alle unsicheren Zeichen und Leerzeichen zu entfernen.

  Eine vollständige Liste der Vorlagenparameter finden Sie unter [Vorlagenparameter](../ide/template-parameters.md).

### <a name="to-substitute-project-template-parameters"></a>So ersetzen Sie Projektvorlagen Parameter

1. Entfernen Sie die-Methode in der Datei *SimpleProjectNode.cs* `AddFileFromTemplate` .

2. Suchen Sie in der Datei " *\\ templates\project\consoleapp\simpleproject.MyProj* " die \<RootNamespace> Eigenschaft, und ändern Sie den Wert in $safeprojectname $.

    ```
    <RootNamespace>$safeprojectname$</RootNamespace>
    ```

3. Ersetzen Sie in der Datei " *\\ templates\projects\simpleproject\program.cs* " den Inhalt der Datei durch den folgenden Code:

    ```
    using System;
    using System.Collections.Generic;
    using System.Text;
    using System.Runtime.InteropServices;    // Guid

    namespace $safeprojectname$
    {
        [Guid("$guid1$")]
        public class $safeprojectname$
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Hello VSX!!!");
                Console.ReadKey();
            }
        }
    }
    ```

4. Erstellen Sie das Projekt simpleproject neu, und starten Sie das Debugging. Die experimentelle Instanz sollte angezeigt werden.

5. Erstellen Sie eine neue simpleproject-Konsolenanwendung. (Wählen Sie im Bereich **Projekttypen** die Option **simpleproject** aus. Wählen Sie unter von **Visual Studio installierte Vorlagen** die Option **Konsolenanwendung** aus.)

6. Öffnen Sie *Program.cs* im neu erstellten Projekt. Sie sollte in etwa wie folgt aussehen (die GUID-Werte in der Datei unterscheiden sich.):

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Text;
    using System.Runtime.InteropServices;    // Guid

    namespace Console_Application1
    {
        [Guid("00000000-0000-0000-00000000-00000000)"]
        public class Console_Application1
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Hello VSX!!!");
                Console.ReadKey();
            }
        }
    }
    ```

## <a name="create-a-project-property-page"></a>Erstellen einer Projekteigenschaften Seite
Sie können eine Eigenschaften Seite für den Projekttyp erstellen, damit Benutzereigenschaften in Projekten anzeigen und ändern können, die auf der Vorlage basieren. In diesem Abschnitt wird gezeigt, wie Sie eine Konfigurations unabhängige Eigenschaften Seite erstellen. Diese grundlegende Eigenschaften Seite verwendet ein Eigenschaften Raster, um die öffentlichen Eigenschaften anzuzeigen, die Sie in der Eigenschaften Seiten Klasse verfügbar machen.

Leiten Sie die Eigenschaften Seiten Klasse von der- `SettingsPage` Basisklasse ab. Das von der-Klasse bereitgestellte Eigenschaften Raster `SettingsPage` kennt die meisten primitiven Datentypen und weiß, wie Sie angezeigt werden. Außerdem weiß die- `SettingsPage` Klasse, wie Eigenschaftswerte in der Projektdatei beibehalten werden.

Auf der Eigenschaften Seite, die Sie in diesem Abschnitt erstellen, können Sie diese Projekteigenschaften ändern und speichern:

- AssemblyName

- OutputType

- RootNamespace.

1. Fügen Sie der-Klasse in der Datei *SimpleProjectPackage.cs* dieses `ProvideObject` Attribut hinzu `SimpleProjectPackage` :

    ```
    [ProvideObject(typeof(GeneralPropertyPage))]
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

    Dadurch wird die Eigenschaften Seiten Klasse `GeneralPropertyPage` bei com registriert.

2. Fügen Sie in der Datei *SimpleProjectNode.cs* die folgenden beiden überschriebenen Methoden zur- `SimpleProjectNode` Klasse hinzu:

    ```csharp
    protected override Guid[] GetConfigurationIndependentPropertyPages()
    {
        Guid[] result = new Guid[1];
        result[0] = typeof(GeneralPropertyPage).GUID;
        return result;
    }
    protected override Guid[] GetPriorityProjectDesignerPages()
    {
        Guid[] result = new Guid[1];
        result[0] = typeof(GeneralPropertyPage).GUID;
        return result;
    }
    ```

    Beide Methoden geben ein Array von Eigenschaften Seiten-GUIDs zurück. Der GUID generalpropertypage ist das einzige Element im Array, sodass im Dialogfeld **Eigenschaften Seiten** nur eine Seite angezeigt wird.

3. Fügen Sie dem Projekt simpleproject eine Klassendatei mit dem Namen *GeneralPropertyPage.cs* hinzu.

4. Ersetzen Sie den Inhalt dieser Datei durch den folgenden Code:

    ```csharp
    using System;
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Project;
    using System.ComponentModel;

    namespace SimpleProject
    {
        [ComVisible(true)]
        [Guid("6BC7046B-B110-40d8-9F23-34263D8D2936")]
        public class GeneralPropertyPage : SettingsPage
        {
            private string assemblyName;
            private OutputType outputType;
            private string defaultNamespace;

            public GeneralPropertyPage()
            {
                this.Name = "General";
            }

            [Category("AssemblyName")]
            [DisplayName("AssemblyName")]
            [Description("The output file holding assembly metadata.")]
            public string AssemblyName
            {
                get { return this.assemblyName; }
            }
            [Category("Application")]
            [DisplayName("OutputType")]
            [Description("The type of application to build.")]
            public OutputType OutputType
            {
                get { return this.outputType; }
                set { this.outputType = value; this.IsDirty = true; }
            }
            [Category("Application")]
            [DisplayName("DefaultNamespace")]
            [Description("Specifies the default namespace for added items.")]
            public string DefaultNamespace
            {
                get { return this.defaultNamespace; }
                set { this.defaultNamespace = value; this.IsDirty = true; }
            }

            protected override void BindProperties()
            {
                this.assemblyName = this.ProjectMgr.GetProjectProperty("AssemblyName", true);
                this.defaultNamespace = this.ProjectMgr.GetProjectProperty("RootNamespace", false);

                string outputType = this.ProjectMgr.GetProjectProperty("OutputType", false);
                this.outputType = (OutputType)Enum.Parse(typeof(OutputType), outputType);
            }

            protected override int ApplyChanges()
            {
                this.ProjectMgr.SetProjectProperty("AssemblyName", this.assemblyName);
                this.ProjectMgr.SetProjectProperty("OutputType", this.outputType.ToString());
                this.ProjectMgr.SetProjectProperty("RootNamespace", this.defaultNamespace);
                this.IsDirty = false;

                return VSConstants.S_OK;
            }
        }
    }
    ```

    Die- `GeneralPropertyPage` Klasse macht die drei öffentlichen Eigenschaften AssemblyName, OutputType und RootNamespace verfügbar. Da AssemblyName über keine Set-Methode verfügt, wird Sie als schreibgeschützte Eigenschaft angezeigt. OutputType ist eine Enumerationskonstante, die als Dropdown Liste angezeigt wird.

    Die- `SettingsPage` Basisklasse stellt bereit `ProjectMgr` , um die Eigenschaften beizubehalten. Die `BindProperties` -Methode verwendet `ProjectMgr` , um die beibehaltenen Eigenschaftswerte abzurufen und die entsprechenden Eigenschaften festzulegen. Die `ApplyChanges` -Methode verwendet `ProjectMgr` , um die Werte der Eigenschaften zu erhalten, und speichert Sie in der Projektdatei. Mit der Eigenschaft Set-Methode `IsDirty` wird auf true festgelegt, um anzugeben, dass die Eigenschaften persistent sein müssen. Persistenz tritt auf, wenn Sie das Projekt oder die Projekt Mappe speichern.

5. Erstellen Sie die Projekt Mappe simpleproject neu, und starten Sie das Debugging Die experimentelle Instanz sollte angezeigt werden.

6. Erstellen Sie in der experimentellen Instanz eine neue simpleproject-Anwendung.

7. Visual Studio ruft Ihre projektfactory auf, um ein Projekt mithilfe der Visual Studio-Vorlage zu erstellen. Die neue *Program.cs* -Datei wird im Code-Editor geöffnet.

8. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf den Projekt Knoten, und klicken Sie dann auf **Eigenschaften**. Das Dialogfeld **Eigenschaftenseiten** wird angezeigt.

    ![Einfache Projekteigenschaften Seite](../extensibility/media/simpproj2_proppage.png "SimpProj2_PropPage")

## <a name="test-the-project-property-page"></a>Testen der Eigenschaften Seite des Projekts
Nun können Sie testen, ob Sie Eigenschaftswerte ändern und ändern können.

1. Ändern Sie im Dialogfeld **Eigenschaften Seiten von myconsoleapplication** den **DefaultNamespace** in **MyApplication**.

2. Wählen Sie die **OutputType** -Eigenschaft aus, und wählen Sie dann **Klassenbibliothek** aus.

3. Klicken Sie auf **Übernehmen**, und klicken Sie anschließend auf **OK**.

4. Öffnen Sie das Dialogfeld **Eigenschaften Seiten** erneut, und überprüfen Sie, ob die Änderungen persistent gespeichert wurden.

5. Schließen Sie die experimentelle Instanz von Visual Studio.

6. Öffnen Sie die experimentelle Instanz erneut.

7. Öffnen Sie das Dialogfeld **Eigenschaften Seiten** erneut, und überprüfen Sie, ob die Änderungen persistent gespeichert wurden.

8. Schließen Sie die experimentelle Instanz von Visual Studio.
    ![Die experimentelle Instanz schließen](../extensibility/media/simpproj2_proppage2.png "SimpProj2_PropPage2")
