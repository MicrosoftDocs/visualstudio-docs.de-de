---
title: Grundlegendes zum DSL-Code
description: Erfahren Sie, wie die DSL-Lösung (Domain-Specific Language) eine API generiert, die Sie zum Lesen und Aktualisieren von Instanzen der DSL in Visual Studio verwenden können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, generated code
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd739a7780a2a2c858efc14aa72205e9be161900
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361455"
---
# <a name="understanding-the-dsl-code"></a>Grundlegendes zum DSL-Code

Eine Domain-Specific Language (DSL)-Lösung generiert eine API, mit der Sie Instanzen der DSL in Visual Studio lesen und aktualisieren können. Diese API wird im Code definiert, der aus der DSL-Definition generiert wird. In diesem Thema wird die generierte API beschrieben.

## <a name="the-example-solution-component-diagrams"></a>Beispielprojektmappe: Komponentendiagramme

Um die Lösung zu erstellen, die die meisten der Beispiele in diesem Thema ist, erstellen Sie eine DSL aus der Lösungs Vorlage für **Komponentenmodelle** . Dies ist eine der Standardvorlagen, die angezeigt wird, wenn Sie eine neue DSL-Projektmappe erstellen.

> [!NOTE]
> Die DSL-Vorlage für Komponenten Diagramme wird als **Domänen spezifischer sprach Designer** bezeichnet.

Drücken Sie **F5** , und experimentieren Sie, wenn Sie mit dieser Lösungs Vorlage nicht vertraut sind. Achten Sie insbesondere darauf, dass Sie Ports erstellen, indem Sie ein Port-Tool auf eine Komponente ziehen, und dass Sie Verbindungen mit Ports herstellen können.

![Komponenten und verbundene Ports](../modeling/media/componentsample.png)

## <a name="the-structure-of-the-dsl-solution"></a>Struktur der DSL-Projektmappe
 Das **DSL** -Projekt definiert die API für Ihre DSL. Das **dslpackage** -Projekt definiert, wie es in Visual Studio integriert wird. Sie können auch eigene Projekte hinzufügen, die durch das Modell generierten Code enthalten können.

### <a name="the-code-directories"></a>Codeverzeichnisse
 Der größte Teil des Codes in jedem dieser Projekte wird von **Dsl\DslDefinition.DSL** generiert. Der generierte Code befindet sich im **generierten Code** Ordner. Um eine generierte Datei anzuzeigen, klicken Sie auf **[+]** neben der generierten **TT** -Datei.

 Es empfiehlt sich, den generierten Code zu untersuchen, damit Sie die DSL besser verstehen. Erweitern Sie zum Anzeigen der generierten Dateien die TT-Dateien im Projektmappen-Explorer.

 Die \* TT-Dateien enthalten sehr wenig Generierungs Code. Stattdessen verwenden sie `<#include>`-Direktiven, um freigegebene Vorlagendateien einzubinden. Die freigegebenen Dateien finden Sie unter **\Programme\Microsoft Visual Studio 10.0 \ Common7\IDE\Extensions\Microsoft\DSL sdk\dsl designer\11.0\texttemplates** .

 Wenn Sie der DSL-Projektmappe eigenen Programmcode hinzufügen, nutzen Sie dafür eine separate Datei außerhalb des Ordners für generierten Code. Möglicherweise möchten Sie einen **benutzerdefinierten Code** Ordner erstellen. (Wenn Sie eine neue Codedatei einem benutzerdefinierten Ordner hinzufügen, müssen Sie den Namespace im anfänglichen Codeskelett korrigieren.)

 Wir raten dringend davon ab, den generierten Code direkt zu bearbeiten, da Ihre Änderungen verloren gehen, wenn Sie die Projektmappe neu erstellen. Passen Sie stattdessen Ihre DSL an:

- Passen Sie die vielen Parameter in der DSL-Definition an.

- Schreiben Sie partielle Klassen in separaten Codedateien, um Methoden zu überschreiben, die in den generierten Klassen definiert sind oder von ihnen geerbt werden. In einigen Fällen müssen Sie die Option **generiert Double-abgeleitete** einer Klasse in der DSL-Definition festlegen, damit eine generierte Methode überschrieben werden kann.

- Legen Sie Optionen in der DSL-Definition fest, die bewirken, dass der generierte Code "Hooks" für Ihren eigenen Code bereitstellt.

     Wenn Sie z. b. die Option verfügt über einen **benutzerdefinierten Konstruktor** einer Domänen Klasse und dann die Projekt Mappe erstellen, werden Fehlermeldungen angezeigt. Wenn Sie auf eine dieser Fehlermeldungen doppelklicken, sehen Sie Kommentare im generierten Code, die erläutern, was der benutzerdefinierte Code enthalten sollte.

- Schreiben Sie eigene Textvorlagen, um Code speziell für Ihre Anwendung zu erstellen. Sie können Include-Dateien verwenden, um Teile der Vorlagen freizugeben, die für viele Projekte gelten, und Sie können Visual Studio-Projektvorlagen erstellen, um Projekte einzurichten, die mit ihrer eigenen Dateistruktur initialisiert werden.

## <a name="generated-files-in-dsl"></a>Generierte Dateien in "Dsl"
 Die folgenden generierten Dateien werden im **DSL** -Projekt angezeigt.

 *Yourdsl*`Schema.xsd`

 Das Schema für Dateien, die Instanzen Ihrer DSL enthalten. Diese Datei wird in das Verzeichnis für die Kompilierung (**bin**) kopiert. Wenn Sie die DSL installieren, können Sie diese Datei in " **\Programme\Microsoft Visual Studio 11.0 \ xml\schemas** " kopieren, damit die Modelldateien überprüft werden können. Weitere Informationen finden Sie unter [Deploying Domain-Specific Language Solutions (Bereitstellen von Projektmappen für eine domänenspezifische Sprache)](msi-and-vsix-deployment-of-a-dsl.md).

 Wenn Sie die Serialisierung durch Festlegen von Optionen im DSL-Explorer anpassen, ändert sich das Schema entsprechend. Wenn Sie jedoch eigenen Serialisierungscode schreiben, bildet diese Datei das eigentliche Schema möglicherweise nicht mehr ab. Weitere Informationen finden Sie unter [Anpassen von File Storage und XML-Serialisierung](../modeling/customizing-file-storage-and-xml-serialization.md).

 `ConnectionBuilders.cs`

 Ein Verbindungs-Generator ist eine Klasse, die Beziehungen erstellt. Es ist der Code für ein Verbindungstool. Diese Datei enthält ein Paar von Klassen für jedes Verbindungstool. Ihre Namen werden von den Namen der Domänen Beziehung und des Verbindungs Tools abgeleitet: *Beziehungs* Generator und *Connector Tool* connectaction.

 (Im Beispiel der Komponentenprojektmappe trägt einer der Verbindungs-Generatoren den Namen "ConnectionBuilder". Dies ist ein Zufall, da die Domänenbeziehung "Connection" genannt wurde.)

 Die Beziehung wird in der *Beziehungs* `Builder.Connect()` Methode erstellt. Die Standardversion überprüft, ob die Quell- und Zielmodellelemente akzeptiert werden können und instanziiert dann die Beziehung. Zum Beispiel:

 `CommentReferencesSubject(sourceAccepted, targetAccepted);`

 Jede Generator Klasse wird von einem Knoten im Abschnitt **Verbindungs** -Generatoren im DSL-Explorer generiert. Eine `Connect`-Methode kann Beziehungen zwischen einem oder mehreren Paaren von Domänenklassen erstellen. Jedes Paar wird durch eine Direktive für Linkverbindungen definiert, die Sie im DSL-Explorer unter dem Generator-Knoten finden.

 Sie könnten beispielsweise einem Verbindungs-Generator Direktiven für Linkverbindungen für jeden der drei Typen von Beziehungen in der Beispiel-DSL hinzufügen. Auf diese Weise erhält der Benutzer ein einziges Verbindungstool. Der Typ der instanziierten Beziehung hängt von den Typen der Quell- und Zielelemente ab, die vom Benutzer ausgewählt werden.  Klicken Sie zum Hinzufügen von Direktiven für Linkverbindungen mit der rechten Maustaste auf einen Generator im DSL-Explorer.

 Wählen Sie zum Schreiben von benutzerdefiniertem Code, der bei der Erstellung eines bestimmten Typs von Domänenbeziehung ausgeführt wird, unter dem Generator-Knoten die entsprechende Direktive für Linkverbindungen aus. Legen Sie in der Eigenschaftenfenster **benutzerdefinierte Verbindung verwendet**. Erstellen Sie die Projektmappe, und stellen Sie dann den Code bereit, um die entstandenen Fehler zu korrigieren.

 Um benutzerdefinierten Code zu schreiben, der immer dann ausgeführt wird, wenn der Benutzer dieses Verbindungs Tool verwendet, legen Sie die Eigenschaft **ist Custom** des Verbindungs-Generators fest. Sie können Code bereitstellen, der bestimmt, ob ein Element zulässig ist, ob eine bestimmte Kombination aus Quelle und Ziel zulässig ist und welche Aktualisierungen am Modell vorgenommen werden sollen, wenn eine Verbindung hergestellt wird. Sie könnten eine Verbindung beispielsweise nur zulassen, wenn damit keine Schleife im Diagramm erstellt wird. Statt eines einzelnen Beziehungslinks könnten Sie eine komplexeres Muster mehrerer miteinander verknüpfter Elemente zwischen Quelle und Ziel instanziieren.

 `Connectors.cs`

 Enthält die Klassen für die Konnektoren, bei denen es sich um die Diagrammelemente handelt, die üblicherweise Verweisbeziehungen darstellen. Jede Klasse wird aus einem Konnektor in der DSL-Definition generiert. Jede Konnektorklasse wird von <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape> abgeleitet.

 Klicken Sie im DSL-Definitions Diagramm mit der rechten Maustaste auf die Klasse, und zeigen Sie auf verfügbar machen **, um die** Farbe und andere Formatvorlagen Variablen zur Laufzeit festzulegen.

 Informationen dazu, wie weitere Stilmerkmale zur Laufzeit variabel gemacht werden, finden Sie in den Beispielen <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField> und <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>.

 `Diagram.cs`

 Enthält die Klasse, die das Diagramm definiert. Sie wird von <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> abgeleitet.

 Klicken Sie im DSL-Definitions Diagramm mit der rechten Maustaste auf die Klasse, und zeigen Sie auf verfügbar machen **, um die** Farbe und andere Formatvorlagen Variablen zur Laufzeit festzulegen.

 Darüber hinaus enthält die Datei die Regel `FixupDiagram`, die angewendet wird, wenn dem Modell ein neues Element hinzugefügt wird. Die Regel fügt eine neue Form hinzu und verknüpft die Form mit dem Modellelement.

 `DirectiveProcessor.cs`

 Mit diesem Direktivenprozessor können Ihre Benutzer Textvorlagen schreiben, die eine Instanz Ihrer DSL lesen. Der Direktivenprozessor lädt die Assemblys (DLLs) für Ihre DSL und fügt effektiv `using`-Anweisungen für Ihren Namespace ein. So kann der Code in den Textvorlagen die Klassen und Beziehungen verwenden, die Sie in Ihrer DSL definiert haben.

 Weitere Informationen finden Sie unter Erstellen [von Code aus einer Domain-Specific Sprache](../modeling/generating-code-from-a-domain-specific-language.md) und [Erstellen von benutzerdefinierten T4-Text Vorlagen-direktivenprozessoren](../modeling/creating-custom-t4-text-template-directive-processors.md).

 `DomainClasses.cs`

 Implementierungen der Domänenklassen, die Sie definiert haben, einschließlich der abstrakten Klassen und der Modellstammklasse. Sie werden von <xref:Microsoft.VisualStudio.Modeling.ModelElement> abgeleitet.

 Jede Domänenklasse enthält Folgendes:

- Eine Eigenschaftendefinition und eine geschachtelte Handlerklasse für jede Domäneneigenschaft. Sie können OnValueChanging() und OnValueChanged() überschreiben. Weitere Informationen finden Sie unter [Domänen Eigenschafts Wert-Änderungs Handler](../modeling/domain-property-value-change-handlers.md).

   In der Beispiel-DSL enthält die `Comment`-Klasse eine `Text`-Eigenschaft und eine `TextPropertyHandler`-Handlerklasse.

- Accessoreigenschaften für die Beziehungen mit Beteiligung dieser Domänenklasse. (Es gibt keine geschachtelte Klasse für Rolleneigenschaften.)

   In der Beispiel-DSL weist die `Comment`-Klasse Accessoren auf, die über die Einbettungsbeziehung `ComponentModelHasComments` auf das übergeordnete Modell zugreifen.

- Konstruktoren. Wenn Sie diese überschreiben möchten, legen Sie für die Domänen Klasse **einen benutzerdefinierten Konstruktor** fest.

- EGP-Handlermethoden (Elementgruppenprototyp). Diese sind erforderlich, wenn der Benutzer ein anderes Element auf Instanzen dieser Klasse zusammen *führen* (hinzufügen) kann. Üblicherweise führt der Benutzer dazu einen Ziehvorgang von einem Elementtool oder einer anderen Form oder einen Einfügevorgang aus.

   In der Beispiel-DSL kann ein Eingangsport oder ein Ausgangsport in einer Komponente zusammengeführt werden. Außerdem können Komponenten und Kommentare im Modell zusammengeführt werden. Die

   Die EGP-Handlermethoden in der Komponentenklasse lassen es zu, dass eine Komponente Ports akzeptiert, aber keine Kommentare. Der EGP-Handler in der Stammmodellklasse akzeptiert Kommentare und Komponenten, aber keine Ports.

  `DomainModel.cs`

  Die Klasse, die das Domänenmodell darstellt. Sie wird von <xref:Microsoft.VisualStudio.Modeling.DomainModel> abgeleitet.

> [!NOTE]
> Sie ist nicht mit der Stammklasse des Modells identisch.

 Mit Kopier- und Löschabschlüssen wird definiert, welche anderen Elemente aufgenommen werden sollen, wenn ein Element kopiert oder gelöscht wird. Sie können dieses Verhalten steuern, indem Sie die Eigenschaften " **Kopie kopieren** " und "Weitergabe **Löschen** " der Rollen auf jeder Seite jeder Beziehung festlegen. Wenn die Werte dynamisch ermittelt werden sollen, können Sie Code schreiben, um die Methoden der Abschlussklassen zu überschreiben.

 `DomainModelResx.resx`

 Enthält Zeichenfolgen wie die Beschreibungen von Domänenklassen und -eigenschaften, Eigenschaftennamen, Toolboxbezeichnungen, Standardfehlermeldungen und andere Zeichenfolgen, die dem Benutzer angezeigt werden können. Die Datei könnte auch Toolsymbole und Bilder für Bildformen enthalten.

 Diese Datei ist an die erstellte Assembly gebunden und enthält die Standardwerte für diese Ressourcen. Sie können Ihre DSL lokalisieren, indem Sie eine Satellitenassembly erstellen, die eine lokalisierte Version der Ressourcen enthält. Diese Version wird verwendet, wenn die DSL in einer Kultur erstellt wird, die mit den lokalisierten Ressourcen übereinstimmt. Weitere Informationen finden Sie unter [Deploying Domain-Specific Language Solutions (Bereitstellen von Projektmappen für eine domänenspezifische Sprache)](msi-and-vsix-deployment-of-a-dsl.md).

 `DomainRelationships.cs`

 Jeder Link zwischen zwei Elementen in einem Modell wird durch eine Instanz einer Domänenbeziehungsklasse dargestellt. Alle Beziehungsklassen werden von <xref:Microsoft.VisualStudio.Modeling.ElementLink> abgeleitet, der wiederum von <xref:Microsoft.VisualStudio.Modeling.ModelElement> abgeleitet wird. Da es sich um ein ModelElement handelt, kann eine Instanz einer Beziehung Eigenschaften aufweisen und die Quelle oder das Ziel einer Beziehung sein.

 `HelpKeywordHelper.cs`

 Stellt Funktionen bereit, die verwendet werden, wenn der Benutzer F1 drückt.

 `MultiplicityValidation.cs`

 In Beziehungsrollen, in denen Sie die Multiplizität 1..1 oder 1..* angegeben haben, sollte der Benutzer informiert werden, dass mindestens eine Instanz der Beziehung erforderlich ist. Diese Datei enthält Validierungseinschränkungen, mit denen diese Warnungen implementiert werden. Der Link 1..1 zu einem übergeordneten Einbettungselement wird nicht überprüft.

 Damit diese Einschränkungen ausgeführt werden, müssen Sie im DSL-Explorer im Knoten **Editor \ Validierung** eine der Optionen **Verwendungs** Optionen festgelegt haben. Weitere Informationen finden Sie unter [Validierung in einer Domain-Specific Sprache](../modeling/validation-in-a-domain-specific-language.md).

 `PropertiesGrid.cs`

 Diese Datei enthält nur Code, wenn Sie einer Domäneneigenschaft einen benutzerdefinierten Typdeskriptor angefügt haben. Weitere Informationen finden Sie unter [Anpassen des Fensters "Eigenschaften](../modeling/customizing-the-properties-window.md)".

 `SerializationHelper.cs`

- Eine Validierungsmethode, mit der sichergestellt wird, dass ein Moniker nicht auf zwei Elemente verweist. Weitere Informationen finden Sie unter [Anpassen von File Storage und XML-Serialisierung](../modeling/customizing-file-storage-and-xml-serialization.md).

- SerializationHelper-Klasse, die Funktionen bereitstellt, die von Serialisierungsklassen gemeinsam verwendet werden.

  `Serializer.cs`

  Eine Serialisierungsklasse für alle Domänenklassen, Beziehungen, Formen, Konnektoren, Diagramme und Modelle.

  Viele der Funktionen dieser Klassen können durch die Einstellungen im DSL-Explorer unter dem XML- **Serialisierungsverhalten** gesteuert werden.

  `Shapes.cs`

  Eine Klasse für jede Formklasse in der DSL-Definition. Formen werden von <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape> abgeleitet. Weitere Informationen finden Sie unter [Anpassen von File Storage und XML-Serialisierung](../modeling/customizing-file-storage-and-xml-serialization.md).

  Wenn Sie die generierten Methoden mit ihren eigenen Methoden in einer partiellen Klasse überschreiben möchten, generiert Set eine **Double-abgeleitete** für den Connector in der DSL-Definition. Um einen Konstruktor durch ihren eigenen Code zu ersetzen, **hat Set einen benutzerdefinierten Konstruktor**.

  Klicken Sie im DSL-Definitions Diagramm mit der rechten Maustaste auf die Klasse, und zeigen Sie auf verfügbar machen **, um die** Farbe und andere Formatvorlagen Variablen zur Laufzeit festzulegen.

  Informationen dazu, wie weitere Stilmerkmale zur Laufzeit variabel gemacht werden, finden Sie in den Beispielen <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField> und <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>.

  `ToolboxHelper.cs`

  Richtet die Toolbox ein, indem Elementgruppenprototypen in den Elementtools installiert werden. Kopien dieser Prototypen werden mit den Zielelementen zusammengeführt, wenn der Benutzer das Tool ausführt.

  Sie könnten `CreateElementPrototype()` überschreiben, um ein Toolboxelement zu definieren, mit dem eine Gruppe aus mehreren Objekten erstellt wird. Sie könnten z. B. ein Element definieren, das Objekte mit Unterkomponenten darstellt. Nachdem Sie den Code geändert haben, setzen Sie die experimentelle Instanz von Visual Studio zurück, um den Toolbox Cache zu löschen.

## <a name="generated-files-in-the-dslpackage-project"></a>Generierte Dateien im DslPackage-Projekt
 Dslpackage verbindet das DSL-Modell mit der Visual Studio-Shell und verwaltet die Fenster-, Toolbox-und Menübefehle. Die meisten der Klassen werden doppelt abgeleitet, sodass Sie deren Methoden überschreiben können.

 `CommandSet.cs`

 Die Kontextmenü Befehle, die im Diagramm sichtbar sind. Sie können diesen Satz anpassen oder erweitern. Diese Datei enthält den Code für die Befehle. Die Position der Befehle in Menüs wird durch die Datei "Commands.vsct" bestimmt. Weitere Informationen finden Sie unter [Schreiben von Benutzerbefehlen und-Aktionen](how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

 `Constants.cs`

 GUIDs.

 `DocData.cs`

 *Yourdsl* `DocData` verwaltet das Laden und Speichern eines Modells in einer Datei und erstellt die Speicher Instanz.

 Wenn Sie Ihre DSL beispielsweise in einer Datenbank statt in einer Datei speichern möchten, können Sie die Methoden `Load` und `Save` überschreiben.

 `DocView.cs`

 *Yourdsl* `DocView` verwaltet das Fenster, in dem das Diagramm angezeigt wird. Sie könnten das Diagramm beispielsweise in eine Windows Form einbetten:

 Fügen Sie dem DslPackage-Projekt eine Datei mit Benutzersteuerelementen hinzu. Fügen Sie ein Panel hinzu, in dem das Diagramm angezeigt werden kann. Fügen Sie Schaltflächen und andere Steuerelemente hinzu. Fügen Sie in der Codeansicht des Formulars den folgenden Code hinzu; passen Sie dabei die Namen an Ihre DSL an:

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Drawing;
using System.Data;
using System.Linq;
using System.Text;
using System.Windows.Forms;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Shell;

namespace Company.EmbedInForm
{
  public partial class UserControl1 : UserControl
  {
    public UserControl1()
    {
      InitializeComponent();
    }

    private DiagramDocView docView;

    public UserControl1(DiagramDocView docView, Control content)
      : this()
    {
      this.docView = docView;
      panel1.Controls.Add(content);
    }

    private void button1_Click(object sender, EventArgs e)
    {
      ExampleModel modelRoot = this.docView.CurrentDiagram.ModelElement as ExampleModel;
      foreach (ExampleElement element in modelRoot.Elements)
      {
       listBox1.Items.Add(element.Name);
      }
    }
  }
  internal partial class EmbedInFormDocView
  {

    private ContainerControl container;

    /// <summary>
    /// Return a User Control instead of the DSL window.
    /// The user control will contain the DSL window.
    /// </summary>

    public override System.Windows.Forms.IWin32Window Window
    {
      get
      {
        if (container == null)
        {
          // Put the normal DSL Window inside our control
          container = new UserControl1(this, (Control)base.Window);
        }
        return container;
      }
    }
  }

}
```

 `EditorFactory.cs`

 Instanziiert `DocData` und `DocView`. Es erfüllt eine Standardschnittstelle, die Visual Studio verwendet, um einen Editor zu öffnen, wenn das DSL-Paket gestartet wird. Auf die Datei wird im `ProvideEditorFactory`-Attribut in "Package.cs" verwiesen.

 `GeneratedVSCT.vsct`

 Gibt die Standardmenü Befehle in Menüs an, z. b. das Diagramm mit der rechten Maustaste (Kontextmenü), das Menü **Bearbeiten** usw. Der Code für die Befehle befindet sich in "CommandSet.cs". Sie können die Standardbefehle verschieben oder ändern, und Sie können eigene Befehle hinzufügen. Weitere Informationen finden Sie unter [Schreiben von Benutzerbefehlen und-Aktionen](how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

 `ModelExplorer.cs`

 Definiert den Modell-Explorer für Ihre DSL. Dies ist eine Strukturansicht des Modells, die dem Benutzer neben dem Diagramm angezeigt wird.

 Sie könnten z. B. `InsertTreeView()` überschreiben, um die Reihenfolge zu ändern, in der Elemente im Modell-Explorer angezeigt werden.

 Mit folgendem Code können Sie festlegen, dass die Auswahl im Modell-Explorer mit der Diagrammauswahl synchron bleibt:

```csharp
protected override void OnSelectionChanged(global::System.EventArgs e)
{
base.OnSelectionChanged(e);
// get the selected element
DslModeling::ModelElement selectedElement =
this.PrimarySelection as DslModeling::ModelElement;
// Select in the model explorer
SelectInModelExplorer<YOURLANGUAGEExplorerToolWindow>(selectedElement);
}
private void SelectInModelExplorer<T>(DslModeling::ModelElement modelElement)
where T : DslShell.ModelExplorerToolWindow
{
DslShell::ModelingPackage package =
this.GetService(typeof(VSShell.Package)) as DslShell::ModelingPackage;

if (package != null)
{
// find the model explorer window
T explorerWindow = package.GetToolWindow(typeof(T), true) as T;
if (explorerWindow != null)
{
// get the tree container
DslShell.ModelExplorerTreeContainer treeContainer =
explorerWindow.TreeContainer;
// find the tree node
DslShell.ExplorerTreeNode treeNode =
treeContainer.FindNodeForElement(modelElement);
// select the node
explorerWindow.TreeContainer.ObjectModelBrowser.SelectedNode = treeNode;
}
}
}
```

 `ModelExplorerToolWindow.cs`

 Definiert das Fenster, in dem der Modell-Explorer angezeigt wird. Verarbeitet die Auswahl der Elemente im Explorer.

 `Package.cs`

 Diese Datei definiert, wie sich die DSL in Visual Studio integriert. Attribute in der Paketklasse registrieren die DSL als Handler für Dateien, die Ihre Dateierweiterung aufweisen, definieren die Toolbox und definieren, wie ein neues Fenster geöffnet wird. Die Initialize ()-Methode wird einmal aufgerufen, wenn die erste DSL in eine Visual Studio-Instanz geladen wird.

 `Source.extension.vsixmanifest`

 Um diese Datei anzupassen, bearbeiten Sie die `.tt`-Datei.

> [!WARNING]
> Wenn Sie die TT-Datei bearbeiten, damit sie Ressourcen wie Symbole oder Bilder enthält, stellen Sie sicher, dass die Ressourcen im VSIX-Build enthalten sind. Wählen Sie in Projektmappen-Explorer die Datei aus, und vergewissern Sie sich, dass die Eigenschaft **in VSIX einschließen** den Wert hat `True` .

 Mit dieser Datei wird gesteuert, wie die DSL in eine Visual Studio-Integrationserweiterung (VSIX) verpackt wird. Weitere Informationen finden Sie unter [Deploying Domain-Specific Language Solutions (Bereitstellen von Projektmappen für eine domänenspezifische Sprache)](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="see-also"></a>Weitere Informationen

- [So definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md)
- [Grundlagen von Modellen, Klassen und Beziehungen](../modeling/understanding-models-classes-and-relationships.md)
- [Anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md)
- [Schreiben von Code zum Anpassen einer Domain-Specific Sprache](../modeling/writing-code-to-customise-a-domain-specific-language.md)
