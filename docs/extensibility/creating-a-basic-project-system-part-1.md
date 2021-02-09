---
title: Erstellen eines grundlegenden Projekt Systems, Teil 1 | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie einen Projekttyp mit dem Namen Extension. MyProj erstellen. In Visual Studio sind Projekte Container, die zum Organisieren von Quell Code Dateien und anderen Ressourcen verwendet werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a1b21ef736e69c962db389a7bb1a3eb284ebdd0a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887366"
---
# <a name="create-a-basic-project-system-part-1"></a>Erstellen eines grundlegenden Projekt Systems, Teil 1
In Visual Studio sind Projekte die Container, mit denen Entwickler Quell Code Dateien und andere Ressourcen organisieren. Projekte werden in der **Projektmappen-Explorer** als untergeordnete Elemente der Projektmappen angezeigt. Mit Projekten können Sie Quellcode organisieren, erstellen, Debuggen und bereitstellen und Verweise auf Webdienste, Datenbanken und andere Ressourcen erstellen.

 Projekte werden in Projektdateien definiert, z. b. eine *csproj* -Datei für ein Visual c#-Projekt. Sie können einen eigenen Projekttyp erstellen, der über eine eigene Projektdatei Namen Erweiterung verfügt. Weitere Informationen zu Projekttypen finden Sie unter [Projekttypen](../extensibility/internals/project-types.md).

> [!NOTE]
> Wenn Sie Visual Studio mit einem benutzerdefinierten Projekttyp erweitern müssen, empfehlen wir dringend, das [Visual Studio-Projekt System](https://github.com/Microsoft/VSProjectSystem) (VSPS) zu nutzen, das eine Reihe von Vorteilen gegenüber der Erstellung eines Projekt Systems von Grund auf bietet:
>
> - Einfacheres Onboarding.  Selbst bei einem einfachen Projekt System sind Zehntausende von Codezeilen erforderlich.  Durch die Nutzung von VSPs werden die onboardingkosten auf einige Klicks reduziert, bevor Sie diese an Ihre Anforderungen anpassen können.
> - Einfachere Wartung.  Durch die Nutzung von VSPs müssen Sie nur Ihre eigenen Szenarien einhalten.  Wir behandeln die Wartung der gesamten Projekt Systeminfrastruktur.
>
>   Wenn Sie Versionen von Visual Studio, die älter als Visual Studio 2013 sind, als Zielversion verwenden müssen, können Sie VSPS nicht in einer Visual Studio-Erweiterung nutzen.  Wenn dies der Fall ist, ist diese exemplarische Vorgehensweise ein guter Ausgangspunkt für den Einstieg.

 In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie einen Projekttyp erstellen, der die Projektdatei Namen Erweiterung *. MyProj* enthält. Diese exemplarische Vorgehensweise wird aus dem vorhandenen Visual c#-Projekt System entfernt.

> [!NOTE]
> Weitere Beispiele für Erweiterungsprojekte finden Sie unter [VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples)-Beispiele.

 In dieser exemplarischen Vorgehensweise wird erläutert, wie Sie diese Aufgaben ausführen:

- Erstellen Sie einen grundlegenden Projekttyp.

- Erstellen Sie eine einfache Projektvorlage.

- Registrieren Sie die Projektvorlage bei Visual Studio.

- Erstellen Sie eine Projekt Instanz, indem Sie das Dialogfeld **Neues Projekt** öffnen und dann die Vorlage verwenden.

- Erstellen Sie eine projektfactory für das Projekt System.

- Erstellen Sie einen Projekt Knoten für das Projekt System.

- Fügen Sie benutzerdefinierte Symbole für das Projekt System hinzu.

- Implementieren Sie die grundlegende Vorlagen Parameter Ersetzung.

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Sie ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

 Außerdem müssen Sie den Quellcode für das [verwaltete Paket Framework für Projekte](https://github.com/tunnelvisionlabs/MPFProj10)herunterladen. Extrahieren Sie die Datei an einen Speicherort, der für die Lösung zugänglich ist, die Sie erstellen möchten.

## <a name="create-a-basic-project-type"></a>Erstellen eines grundlegenden Projekt Typs
 Erstellen Sie ein c#-VSIX-Projekt mit dem Namen **simpleproject**. (**Datei**  >  **Neu**  >  **Project** und dann **Visual c#**  >  **Extensibility**  >  **VSIX Project**). Fügen Sie eine Visual Studio-Paket-Projekt Element Vorlage hinzu (Klicken Sie auf dem **Projektmappen-Explorer** mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie neues Element **Hinzufügen** aus. wechseln Sie  >  dann zu **Erweiterbarkeit**  >  **Visual Studio-Paket** Nennen Sie die Datei *simpleprojectpackage*.

## <a name="creating-a-basic-project-template"></a>Erstellen einer grundlegenden Projektvorlage
 Nun können Sie dieses grundlegende VSPackage ändern, um den neuen Projekttyp " *. MyProj* " zu implementieren. Um ein Projekt zu erstellen, das auf dem Projekttyp *. MyProj* basiert, muss Visual Studio wissen, welche Dateien, Ressourcen und Verweise dem neuen Projekt hinzugefügt werden sollen. Um diese Informationen bereitzustellen, fügen Sie Projektdateien in einem Projektvorlagen Ordner ein. Wenn ein Benutzer das *MyProj* -Projekt verwendet, um ein Projekt zu erstellen, werden die Dateien in das neue Projekt kopiert.

### <a name="to-create-a-basic-project-template"></a>So erstellen Sie eine einfache Projektvorlage

1. Fügen Sie dem Projekt drei Ordner hinzu, eine unter der anderen: *templates\project\simpleproject*. (Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf den Projekt Knoten **simpleproject** , zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **neuer Ordner**. Benennen Sie die Ordner *Vorlagen*. Fügen Sie im Ordner *Vorlagen* einen Ordner mit dem Namen *projects* hinzu. Fügen Sie im *Projektordner einen* Ordner mit dem Namen *simpleproject* hinzu.)

2. Fügen Sie im Ordner *templates\project\simpleproject* eine Bitmap-Bilddatei hinzu, die als Symbol mit dem Namen *simpleproject. ico* verwendet werden soll. Wenn Sie auf **Hinzufügen** klicken, wird der Symbol-Editor geöffnet.

3. Machen Sie das Symbol unverwechselbar. Dieses Symbol wird später in der exemplarischen Vorgehensweise im Dialogfeld **Neues Projekt** angezeigt.

    ![Symbol Einfaches Projekt](../extensibility/media/simpleprojicon.png "SimpleProjIcon")

4. Speichern Sie das Symbol, und schließen Sie den Symbol-Editor.

5. Fügen Sie im Ordner *templates\project\simpleproject* ein **Klassen** Element mit dem Namen *Program.cs* hinzu.

6. Ersetzen Sie den vorhandenen Code durch die folgenden Zeilen.

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Text;

   namespace $nameSpace$
   {
       public class $className$
       {
           static void Main(string[] args)
           {
               Console.WriteLine("Hello VSX!!!");
               Console.ReadKey();
           }
       }
   }
   ```

   > [!IMPORTANT]
   > Dies ist nicht die endgültige Form des *Program.cs* -Codes. die Ersetzungs Parameter werden in einem späteren Schritt behandelt. Möglicherweise werden Kompilierungsfehler angezeigt, aber solange die **BuildAction** -Datei der Datei **Inhalt** ist, sollten Sie in der Lage sein, das Projekt wie gewohnt zu erstellen und auszuführen.

7. Speichern Sie die Datei .

8. Kopieren Sie die Datei *AssemblyInfo.cs* aus dem Ordner *Properties* in den Ordner *project\simpleproject* .

9. Fügen Sie im Ordner *project\simpleproject* eine XML-Datei mit dem Namen *simpleproject. MyProj* hinzu.

   > [!NOTE]
   > Die Dateinamenerweiterung für alle Projekte dieses Typs ist *. MyProj*. Wenn Sie Sie ändern möchten, müssen Sie Sie überall dort ändern, wo Sie in der exemplarischen Vorgehensweise erwähnt werden.

10. Ersetzen Sie den vorhandenen Inhalt durch die folgenden Zeilen.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
      <PropertyGroup>
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
        <SchemaVersion>2.0</SchemaVersion>
        <ProjectGuid></ProjectGuid>
        <OutputType>Exe</OutputType>
        <RootNamespace>MyRootNamespace</RootNamespace>
        <AssemblyName>MyAssemblyName</AssemblyName>
        <EnableUnmanagedDebugging>false</EnableUnmanagedDebugging>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
        <DebugSymbols>true</DebugSymbols>
        <OutputPath>bin\Debug\</OutputPath>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">
        <DebugSymbols>false</DebugSymbols>
        <OutputPath>bin\Release\</OutputPath>
      </PropertyGroup>
      <ItemGroup>
        <Reference Include="mscorlib" />
        <Reference Include="System" />
        <Reference Include="System.Data" />
        <Reference Include="System.Xml" />
      </ItemGroup>
      <ItemGroup>
        <Compile Include="AssemblyInfo.cs">
          <SubType>Code</SubType>
        </Compile>
        <Compile Include="Program.cs">
          <SubType>Code</SubType>
        </Compile>
      </ItemGroup>
      <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
    </Project>
    ```

11. Speichern Sie die Datei .

12. Legen Sie im Fenster **Eigenschaften** die **Buildaktion** von *AssemblyInfo.cs*, *Program.cs*, *simpleproject. ico* und *simpleproject. MyProj* auf **Content** fest, und legen Sie Ihre include-Eigenschaft **in VSIX** -Eigenschaften auf **true** fest.

    In dieser Projektvorlage wird ein einfaches Visual c#-Projekt beschrieben, das sowohl eine Debugkonfiguration als auch eine Releasekonfiguration aufweist. Das Projekt enthält zwei Quelldateien: *AssemblyInfo.cs* und *Program.cs* sowie mehrere Assemblyverweise. Wenn ein Projekt aus der Vorlage erstellt wird, wird der ProjectGuid-Wert automatisch durch eine neue GUID ersetzt.

    In **Projektmappen-Explorer** sollte der Ordner erweiterte **Vorlagen** folgendermaßen aussehen:

```
Templates
   Projects
      SimpleProject
         AssemblyInfo.cs
         Program.cs
         SimpleProject.ico
         SimpleProject.myproj
```

## <a name="create-a-basic-project-factory"></a>Erstellen einer grundlegenden projektfactory
 Sie müssen Visual Studio den Speicherort Ihres Projektvorlagen Ordners mitteilen. Fügen Sie zu diesem Zweck der VSPackage-Klasse ein Attribut hinzu, das die projektfactory implementiert, sodass der Speicherort der Vorlage in die Systemregistrierung geschrieben wird, wenn das VSPackage erstellt wird. Beginnen Sie, indem Sie eine grundlegende projektfactory erstellen, die durch eine projektfactory-GUID identifiziert wird. Verwenden Sie das- <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> Attribut, um die projektfactory mit der-Klasse zu verbinden `SimpleProjectPackage` .

### <a name="to-create-a-basic-project-factory"></a>So erstellen Sie eine grundlegende projektfactory

1. Erstellen Sie GUIDs für Ihre projektfactory (Klicken Sie **im Menü Extras** auf **GUID erstellen**), oder verwenden Sie das im folgenden Beispiel. Fügen Sie die GUIDs der- `SimpleProjectPackage` Klasse in der Nähe des-Abschnitts hinzu, wobei bereits definiert ist `PackageGuidString` . Die GUIDs müssen sowohl das GUID-Formular als auch das Zeichen folgen Format aufweisen. Der resultierende Code sollte dem folgenden Beispiel ähneln.

   ```csharp
       public sealed class SimpleProjectPackage : Package
       {
           ...
           public const string SimpleProjectPkgString = "96bf4c26-d94e-43bf-a56a-f8500b52bfad";
           public const string SimpleProjectFactoryString = "471EC4BB-E47E-4229-A789-D1F5F83B52D4";

           public static readonly Guid guidSimpleProjectFactory = new Guid(SimpleProjectFactoryString);
       }
   ```

2. Fügen Sie dem Hauptordner *simpleproject* eine Klasse mit dem Namen *SimpleProjectFactory.cs* hinzu.

3. Fügen Sie die folgenden using-Direktiven hinzu:

   ```csharp
   using System.Runtime.InteropServices;
   using Microsoft.VisualStudio.Shell;
   ```

4. Fügen Sie der-Klasse ein GUID-Attribut hinzu `SimpleProjectFactory` . Der Wert des-Attributs ist die neue projektfactory-GUID.

   ```csharp
   [Guid(SimpleProjectPackage.SimpleProjectFactoryString)]
   class SimpleProjectFactory
   {
   }
   ```

   Nun können Sie Ihre Projektvorlage registrieren.

### <a name="to-register-the-project-template"></a>So registrieren Sie die Projektvorlage

1. Fügen Sie in *SimpleProjectPackage.cs* <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> der- `SimpleProjectPackage` Klasse wie folgt ein-Attribut hinzu.

   ```csharp
   [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
       @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]
   [Guid(SimpleProjectPackage.PackageGuidString)]
   public sealed class SimpleProjectPackage : Package
   ```

2. Erstellen Sie die Lösung neu, und überprüfen Sie, ob Sie fehlerfrei erstellt

    Beim erneuten Erstellen wird die Projektvorlage registriert.

   Die Parameter `defaultProjectExtension` und `possibleProjectExtensions` werden auf die Projektdatei Erweiterung (*. MyProj*) festgelegt. Der- `projectTemplatesDirectory` Parameter wird auf den relativen Pfad des *Vorlagen* Ordners festgelegt. Während des Builds wird dieser Pfad in einen vollständigen Build konvertiert und zur Registrierung hinzugefügt, um das Projekt System zu registrieren.

## <a name="test-the-template-registration"></a>Testen der Vorlagen Registrierung
 Die Vorlagen Registrierung weist Visual Studio den Speicherort des Projektvorlagen Ordners an, damit Visual Studio den Vorlagen Namen und das Symbol im Dialogfeld **Neues Projekt** anzeigen kann.

### <a name="to-test-the-template-registration"></a>So testen Sie die Vorlagen Registrierung

1. Drücken Sie **F5** , um das Debuggen einer experimentellen Instanz von Visual Studio zu starten.

2. Erstellen Sie in der experimentellen Instanz ein neues Projekt für den neu erstellten Projekttyp. Im Dialogfeld **Neues Projekt** sollte **simpleproject** unter **installierte Vorlagen** angezeigt werden.

   Nun verfügen Sie über eine projektfactory, die registriert ist. Es kann jedoch noch kein Projekt erstellt werden. Das Projektpaket und die projektfactory arbeiten zusammen, um ein Projekt zu erstellen und zu initialisieren.

## <a name="add-the-managed-package-framework-code"></a>Hinzufügen des verwalteten Paket-Framework-Codes
 Implementieren Sie die Verbindung zwischen dem Projektpaket und der projektfactory.

- Importieren Sie die Quell Code Dateien für das verwaltete Paket Framework.

    1. Entladen Sie das Projekt simpleproject (Klicken Sie in **Projektmappen-Explorer** auf den Projekt Knoten, und klicken Sie im Kontextmenü auf **Projekt entladen**.), und öffnen Sie die Projektdatei im XML-Editor.

    2. Fügen Sie der Projektdatei die folgenden Blöcke hinzu (direkt oberhalb der- \<Import> Blöcke). Legen `ProjectBasePath` Sie den Speicherort der Datei *projectbase. Files* im verwalteten Paket Framework-Code fest, den Sie soeben heruntergeladen haben. Möglicherweise müssen Sie dem Pfadnamen einen umgekehrten Schrägstrich hinzufügen. Wenn dies nicht der Fall ist, kann das Projekt möglicherweise den Quellcode des verwalteten Paket-Frameworks nicht finden.

        ```
        <PropertyGroup>
             <ProjectBasePath>your path here\</ProjectBasePath>
             <RegisterWithCodebase>true</RegisterWithCodebase>
          </PropertyGroup>
          <Import Project="$(ProjectBasePath)\ProjectBase.Files" />
        ```

        > [!IMPORTANT]
        > Vergessen Sie nicht den umgekehrten Schrägstrich am Ende des Pfads.

    3. Laden Sie das Projekt neu.

    4. Fügen Sie Verweise auf die folgenden Assemblys hinzu:

        - `Microsoft.VisualStudio.Designer.Interfaces`(in *\<VSSDK install> \visualstudiointegration\common\assemblies\v2.0*)

        - `WindowsBase`

        - `Microsoft.Build.Tasks.v4.0`

### <a name="to-initialize-the-project-factory"></a>So initialisieren Sie die projektfactory

1. Fügen Sie in der *SimpleProjectPackage.cs* -Datei die folgende `using` Direktive hinzu.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

2. Leiten Sie die `SimpleProjectPackage` Klasse von ab `Microsoft.VisualStudio.Package.ProjectPackage` .

    ```csharp
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

3. Registrieren Sie die projektfactory. Fügen Sie der-Methode die folgende Zeile `SimpleProjectPackage.Initialize` direkt nach hinzu `base.Initialize` .

    ```csharp
    base.Initialize();
    this.RegisterProjectFactory(new SimpleProjectFactory(this));
    ```

4. Implementieren Sie die abstrakte-Eigenschaft `ProductUserContext` :

    ```csharp
    public override string ProductUserContext
        {
            get { return ""; }
    }
    ```

5. Fügen Sie in *SimpleProjectFactory.cs* `using` nach den vorhandenen-Anweisungen die folgende-Direktive hinzu `using` .

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

6. Leiten Sie die `SimpleProjectFactory` Klasse von ab `ProjectFactory` .

    ```csharp
    class SimpleProjectFactory : ProjectFactory
    ```

7. Fügen Sie der-Klasse die folgende Dummy-Methode hinzu `SimpleProjectFactory` . Diese Methode wird in einem späteren Abschnitt implementiert.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        return null;
    }
    ```

8. Fügen Sie der-Klasse das folgende Feld und den folgenden Konstruktor hinzu `SimpleProjectFactory` . Dieser `SimpleProjectPackage` Verweis wird in einem privaten Feld zwischengespeichert, sodass er beim Festlegen einer Dienstanbieter Website verwendet werden kann.

    ```csharp
    private SimpleProjectPackage package;

    public SimpleProjectFactory(SimpleProjectPackage package)
        : base(package)
    {
        this.package = package;
    }
    ```

9. Erstellen Sie die Lösung neu, und überprüfen Sie, ob Sie fehlerfrei erstellt

## <a name="test-the-project-factory-implementation"></a>Testen der projektfactory-Implementierung
 Testen Sie, ob der Konstruktor für die projektfactory-Implementierung aufgerufen wird.

### <a name="to-test-the-project-factory-implementation"></a>So testen Sie die projektfactory-Implementierung

1. Legen Sie in der Datei *SimpleProjectFactory.cs* einen Haltepunkt in der folgenden Zeile im `SimpleProjectFactory` Konstruktor fest.

    ```csharp
    this.package = package;
    ```

2. Drücken Sie **F5** , um eine experimentelle Instanz von Visual Studio zu starten.

3. Beginnen Sie in der experimentellen Instanz mit dem Erstellen eines neuen Projekts. Wählen Sie im Dialogfeld **Neues Projekt** den Projekttyp **simpleproject** aus, und klicken Sie dann auf **OK**. Die Ausführung hält am Haltepunkt an.

4. Löschen Sie den Haltepunkt, und beenden Sie das Debugging. Da wir noch keinen Projekt Knoten erstellt haben, löst der Projekt Erstellungs Code weiterhin Ausnahmen aus.

## <a name="extend-the-projectnode-class"></a>Erweitern der projectnode-Klasse
 Jetzt können Sie die- `SimpleProjectNode` Klasse implementieren, die von der-Klasse abgeleitet wird `ProjectNode` . Die- `ProjectNode` Basisklasse verarbeitet die folgenden Aufgaben der Projekt Erstellung:

- Kopiert die Projektvorlagen Datei *simpleproject. MyProj* in den neuen Projektordner. Die Kopie wird entsprechend dem Namen umbenannt, der im Dialogfeld **Neues Projekt** eingegeben wurde. Der `ProjectGuid` Eigenschafts Wert wird durch eine neue GUID ersetzt.

- Durchläuft die MSBuild-Elemente der Projektvorlagen Datei *simpleproject. MyProj* und sucht nach `Compile` Elementen. Für jede `Compile` Zieldatei wird die Datei in den neuen Projektordner kopiert.

  Die abgeleitete `SimpleProjectNode` Klasse verarbeitet diese Aufgaben:

- Ermöglicht das Erstellen oder auswählen von Symbolen für Projekt-und Datei Knoten in **Projektmappen-Explorer** .

- Ermöglicht das Angeben zusätzlicher Projektvorlagen-Parameter Ersetzungen.

### <a name="to-extend-the-projectnode-class"></a>So erweitern Sie die projectnode-Klasse

1. Fügen Sie eine Klasse namens `SimpleProjectNode.cs`hinzu.

2. Ersetzen Sie den vorhandenen Code durch folgenden Code:

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Project;

   namespace SimpleProject
   {
       public class SimpleProjectNode : ProjectNode
       {
           private SimpleProjectPackage package;

           public SimpleProjectNode(SimpleProjectPackage package)
           {
               this.package = package;
           }
           public override Guid ProjectGuid
           {
               get { return SimpleProjectPackage.guidSimpleProjectFactory; }
           }
           public override string ProjectType
           {
               get { return "SimpleProjectType"; }
           }

           public override void AddFileFromTemplate(
               string source, string target)
           {
               this.FileTemplateProcessor.UntokenFile(source, target);
               this.FileTemplateProcessor.Reset();
           }
       }
   }
   ```

   Diese `SimpleProjectNode` Klassen Implementierung weist diese überschriebenen Methoden auf:

- `ProjectGuid`, die die projektfactory-GUID zurückgibt.

- `ProjectType`, die den lokalisierten Namen des Projekt Typs zurückgibt.

- `AddFileFromTemplate`, die ausgewählte Dateien aus dem Vorlagen Ordner in das Ziel Projekt kopiert. Diese Methode wird in einem späteren Abschnitt weiter implementiert.

  Der `SimpleProjectNode` Konstruktor speichert, wie der- `SimpleProjectFactory` Konstruktor, einen `SimpleProjectPackage` Verweis in einem privaten Feld zur späteren Verwendung zwischen.

  Um die- `SimpleProjectFactory` Klasse mit der-Klasse zu verbinden `SimpleProjectNode` , müssen Sie eine neue `SimpleProjectNode` in der `SimpleProjectFactory.CreateProject` -Methode instanziieren und in einem privaten Feld zur späteren Verwendung Zwischenspeichern.

### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>So verbinden Sie die projektfactoryklasse und die Node-Klasse

1. Fügen Sie in der *SimpleProjectFactory.cs* -Datei die folgende `using` Direktive hinzu:

    ```csharp
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;
    ```

2. Ersetzen Sie die- `SimpleProjectFactory.CreateProject` Methode, indem Sie den folgenden Code verwenden.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        SimpleProjectNode project = new SimpleProjectNode(this.package);

        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));
        return project;
    }
    ```

3. Erstellen Sie die Lösung neu, und überprüfen Sie, ob Sie fehlerfrei erstellt

## <a name="test-the-projectnode-class"></a>Testen der projectnode-Klasse
 Testen Sie Ihre projektfactory, um festzustellen, ob eine Projekt Hierarchie erstellt wird.

### <a name="to-test-the-projectnode-class"></a>So testen Sie die projectnode-Klasse

1. Drücken Sie die Taste **F5** , um mit dem Debuggen zu beginnen. Erstellen Sie in der experimentellen Instanz ein neues simpleproject.

2. Visual Studio sollte Ihre projektfactory aufzurufen, um ein Projekt zu erstellen.

3. Schließen Sie die experimentelle Instanz von Visual Studio.

## <a name="add-a-custom-project-node-icon"></a>Symbol "benutzerdefiniertes Projekt Knoten hinzufügen"
 Das Symbol für den Projekt Knoten im vorherigen Abschnitt ist ein Standard Symbol. Sie können Sie in ein benutzerdefiniertes Symbol ändern.

### <a name="to-add-a-custom-project-node-icon"></a>So fügen Sie ein Symbol für einen benutzerdefinierten Projekt Knoten hinzu

1. Fügen Sie im Ordner **Ressourcen** eine Bitmapdatei mit dem Namen *SimpleProjectNode.bmp* hinzu.

2. Reduzieren Sie im Fenster **Eigenschaften** die Bitmap auf 16 x 16 Pixel. Legen Sie die Bitmap als unverwechselbar dar.

    ![Einfaches Projekt - Comm](../extensibility/media/simpleprojprojectcomm.png "Simpleprojprojectcomm")

3. Ändern Sie im **Eigenschaften** Fenster die **Buildaktion** der Bitmap in **Embedded Resource**.

4. Fügen Sie in *SimpleProjectNode.cs* die folgenden- `using` Anweisungen hinzu:

   ```csharp
   using System.Drawing;
   using System.Windows.Forms;
   ```

5. Fügen Sie der-Klasse das folgende statische Feld und den folgenden Konstruktor hinzu `SimpleProjectNode` .

   ```csharp
   private static ImageList imageList;

   static SimpleProjectNode()
   {
       imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));
   }
   ```

6. Fügen Sie am Anfang der-Klasse die folgende Eigenschaft hinzu `SimpleProjectNode` .

   ```csharp
   internal static int imageIndex;
      public override int ImageIndex
      {
          get { return imageIndex; }
      }
   ```

7. Ersetzen Sie den Instanzkonstruktor durch den folgenden Code.

   ```csharp
   public SimpleProjectNode(SimpleProjectPackage package)
   {
       this.package = package;

       imageIndex = this.ImageHandler.ImageList.Images.Count;

       foreach (Image img in imageList.Images)
       {
           this.ImageHandler.AddImage(img);
       }
   }
   ```

   Bei der statischen Konstruktion wird `SimpleProjectNode` die Bitmap des Projekt Knotens aus den Assemblymanifestressourcen abgerufen und zur späteren Verwendung in einem privaten Feld zwischengespeichert. Beachten Sie die Syntax des <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> Image Pfads. Verwenden Sie die-Methode, um die Namen der Manifestressourcen anzuzeigen, die in eine Assembly eingebettet sind <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> . Wenn diese Methode auf die Assembly angewendet wird `SimpleProject` , sollten die Ergebnisse wie folgt lauten:

- *Simpleproject. resources. Resources*

- *VisualStudio. Project. Resources*

- *Simpleproject. VSPackage. Resources*

- *Resources.imagelis.bmp*

- *Microsoft. VisualStudio. Project. dontshowagaindialog. Resources*

- *Microsoft. VisualStudio. Project. securitywarningdialog. Resources*

- *SimpleProject.Resources.SimpleProjectNode.bmp*

  Während der instanzerbau `ProjectNode` lädt die-Basisklasse *Resources.imagelis.bmp*, in dem häufig eingebettete 16 x 16-Bitmaps von *Resources\imagelis.bmp* verwendet werden. Diese Bitmap-Liste wird als zur Verfügung gestellt `SimpleProjectNode` `ImageHandler.ImageList` . `SimpleProjectNode` Fügt die Bitmap des Projekt Knotens an die Liste an. Der Offset der Bitmap für das Projekt Knoten in der Bildliste wird für die spätere Verwendung als Wert der Public- `ImageIndex` Eigenschaft zwischengespeichert. Visual Studio verwendet diese Eigenschaft, um zu bestimmen, welche Bitmap als Projekt Knoten Symbol angezeigt werden soll.

## <a name="test-the-custom-project-node-icon"></a>Testen des Symbol für den benutzerdefinierten Projekt Knoten
 Testen Sie Ihre projektfactory, um zu sehen, ob Sie eine Projekt Hierarchie mit dem Symbol des benutzerdefinierten Projekt Knotens erstellt.

### <a name="to-test-the-custom-project-node-icon"></a>So testen Sie das Symbol für den benutzerdefinierten Projekt Knoten

1. Starten Sie das Debugging, und erstellen Sie in der experimentellen Instanz ein neues simpleproject.

2. Beachten Sie, dass im neu erstellten Projekt *SimpleProjectNode.bmp* als Symbol für den Projekt Knoten verwendet wird.

     ![Einfaches Projekt - Knoten Neues Projekt](../extensibility/media/simpleprojnewprojectnode.png "Simpleprojnewprojectnode")

3. Öffnen Sie *Program.cs* im Code-Editor. Es sollte Quellcode angezeigt werden, der dem folgenden Code ähnelt.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Text;

    namespace $nameSpace$
    {
        public class $className$
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Hello VSX!!!");
                Console.ReadKey();
            }
        }
    }
    ```

     Beachten Sie, dass die Vorlagen Parameter $Namespace $ und $ClassName $ keine neuen Werte aufweisen. Im nächsten Abschnitt erfahren Sie, wie die Vorlagen Parameter Ersetzung implementiert wird.

## <a name="substitute-template-parameters"></a>Ersetzen von Vorlagen Parametern
 In einem früheren Abschnitt haben Sie die Projektvorlage mithilfe des-Attributs bei Visual Studio registriert `ProvideProjectFactory` . Wenn Sie den Pfad eines Vorlagen Ordners auf diese Weise registrieren, können Sie die grundlegende Vorlagen Parameter Ersetzung durch Überschreiben und Erweitern der- `ProjectNode.AddFileFromTemplate` Klasse aktivieren. Weitere Informationen finden Sie [unter New Project Generation: at the Hood, Part Two](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 Fügen Sie nun der-Klasse Ersatz Code hinzu `AddFileFromTemplate` .

### <a name="to-substitute-template-parameters"></a>So ersetzen Sie Vorlagen Parameter

1. Fügen Sie in der *SimpleProjectNode.cs* -Datei die folgende `using` Direktive hinzu.

   ```csharp
   using System.IO;
   ```

2. Ersetzen Sie die- `AddFileFromTemplate` Methode, indem Sie den folgenden Code verwenden.

   ```csharp
   public override void AddFileFromTemplate(
       string source, string target)
   {
       string nameSpace =
           this.FileTemplateProcessor.GetFileNamespace(target, this);
       string className = Path.GetFileNameWithoutExtension(target);

       this.FileTemplateProcessor.AddReplace("$nameSpace$", nameSpace);
       this.FileTemplateProcessor.AddReplace("$className$", className);

       this.FileTemplateProcessor.UntokenFile(source, target);
       this.FileTemplateProcessor.Reset();
   }
   ```

3. Legen Sie einen Haltepunkt in der-Methode direkt nach der `className` Zuweisungsanweisung fest.

   Die Zuweisungs Anweisungen bestimmen angemessene Werte für einen Namespace und einen neuen Klassennamen. Die zwei `ProjectNode.FileTemplateProcessor.AddReplace` Methodenaufrufe ersetzen die entsprechenden Vorlagen Parameterwerte mithilfe dieser neuen Werte.

## <a name="test-the-template-parameter-substitution"></a>Testen der Vorlagen Parameter Ersetzung
 Nun können Sie die Vorlagen Parameter Ersetzung testen.

### <a name="to-test-the-template-parameter-substitution"></a>So testen Sie die Vorlagen Parameter Ersetzung

1. Starten Sie das Debugging, und erstellen Sie in der experimentellen Instanz ein neues simpleproject.

2. Die Ausführung wird am Haltepunkt in der-Methode angehalten `AddFileFromTemplate` .

3. Überprüfen Sie die Werte für die `nameSpace` `className` Parameter und.

   - `nameSpace` erhält den Wert des- \<RootNamespace> Elements in der Projektvorlagen Datei " *\templates\project\simpleproject\simpleproject.MyProj* ". In diesem Fall handelt es sich um den Wert `MyRootNamespace`.

   - `className` erhält den Wert des Klassen Quell Dateinamens ohne die Dateinamenerweiterung. In diesem Fall ist die erste Datei, die in den Zielordner kopiert werden soll, *AssemblyInfo.cs*; Daher ist der Wert von ClassName `AssemblyInfo` .

4. Entfernen Sie den Breakpoint und drücken Sie **F5** , um die Ausführung fortzusetzen.

    Visual Studio sollte die Erstellung eines Projekts abschließen.

5. Öffnen Sie *Program.cs* im Code-Editor. Es sollte Quellcode angezeigt werden, der dem folgenden Code ähnelt.

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using System.Text;

   namespace MyRootNamespace
   {
       public class Program
       {
           static void Main(string[] args)
           {
               Console.WriteLine("Hello VSX!!!");
               Console.ReadKey();
           }
       }
   }
   ```

    Beachten Sie, dass der Namespace jetzt `MyRootNamespace` und der Klassenname jetzt ist `Program` .

6. Beginnen Sie mit dem Debuggen des Projekts. Das neue Projekt sollte "Hello VSX!!!" kompilieren, ausführen und anzeigen. im Konsolenfenster anzuzeigen.

    ![Befehl Einfaches Projekt](../extensibility/media/simpleprojcommand.png "Simpleprojcommand")

   Glückwunsch! Sie haben ein grundlegendes verwaltetes Projekt System implementiert.
