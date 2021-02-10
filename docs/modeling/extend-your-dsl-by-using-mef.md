---
title: Erweitern von DSL mittels MEF
description: Erfahren Sie, wie Sie Ihre domänenspezifische Sprache (DSL) mithilfe des Managed Extensibility Framework (MEF) erweitern können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 324037010e642ab4e96f6efea5da0f232c9bd530
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935065"
---
# <a name="extend-your-dsl-by-using-mef"></a>Erweitern von DSL mittels MEF

Sie können Ihre domänenspezifische Sprache (DSL) mithilfe von Managed Extensibility Framework (MEF) erweitern. Sie oder andere Entwickler können Erweiterungen für die DSL schreiben, ohne die DSL-Definition und den Programmcode ändern zu müssen. Diese Erweiterungen umfassen Menübefehle, Drag & Drop-Handler und Validierung. Benutzer können Ihre DSL installieren und dann optional Erweiterungen dafür installieren.

Wenn Sie MEF in ihrer DSL aktivieren, kann es einfacher sein, einige der Funktionen Ihrer DSL zu schreiben, auch wenn Sie alle mit der DSL erstellt wurden.

Weitere Informationen zu MEF finden Sie unter [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-enable-your-dsl-to-be-extended-by-mef"></a>So aktivieren Sie die Erweiterung ihrer DSL durch MEF

1. Erstellen Sie im **dslpackage** -Projekt einen neuen Ordner mit dem Namen **MEF Extension** . Fügen Sie die folgenden Dateien hinzu:

     Dateiname: `CommandExtensionVSCT.tt`

    > [!IMPORTANT]
    > Legen Sie fest, dass die GUID in dieser Datei mit der GUID commandsetid übereinstimmt, die in "dslpackage\generatedcode\constants.tt" definiert ist.

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#
    // CmdSet Guid must be defined before master template is included
    // This Guid must be kept synchronized with the CommandSetId Guid in Constants.tt
    Guid guidCmdSet = new Guid ("00000000-0000-0000-0000-000000000000");
    string menuidCommandsExtensionBaseId="0x4000";
    #>
    <#@ include file="DslPackage\CommandExtensionVSCT.tt" #>
    ```

    Dateiname: `CommandExtensionRegistrar.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\CommandExtensionRegistrar.tt" #>
    ```

    Dateiname: `ValidationExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\ValidationExtensionEnablement.tt" #>
    ```

    Dateiname: `ValidationExtensionRegistrar.tt`

    Wenn Sie diese Datei hinzufügen, müssen Sie die Validierung in ihrer DSL aktivieren, indem Sie mindestens einen der Schalter in **Editor Validation** im DSL-Explorer verwenden.

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\ValidationExtensionRegistrar.tt" #>
    ```

    Dateiname: `PackageExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\PackageExtensionEnablement.tt" #>
    ```

2. Erstellen Sie im **DSL** -Projekt einen neuen Ordner mit dem Namen **MEF Extension** . Fügen Sie die folgenden Dateien hinzu:

     Dateiname: `DesignerExtensionMetaDataAttribute.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\DesignerExtensionMetadataAttribute.tt" #>
    ```

    Dateiname: `GestureExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\GestureExtensionEnablement.tt" #>
    ```

    Dateiname: `GestureExtensionController.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\GestureExtensionController.tt" #>
    ```

3. Fügen Sie der vorhandenen Datei mit dem Namen " **dslpackage\commands.vsct**" die folgende Zeile hinzu:

    ```xml
    <Include href="MefExtension\CommandExtensionVSCT.vsct"/>
    ```

    Fügen Sie die Zeile nach der vorhandenen- `<Include>` Anweisung ein.

4. Öffnen Sie die Datei " *DslDefinition. DSL*".

5. Wählen Sie im DSL-Explorer **Editor \ Validierung** aus.

6. Stellen Sie im Eigenschaftenfenster sicher, dass mindestens eine der Eigenschaften mit dem Namen **verwendet** wird `true` .

7. Klicken Sie in der **Projektmappen-Explorer** Symbolleiste auf **alle Vorlagen transformieren**.

     Neben den Dateien, die Sie hinzugefügt haben, werden untergeordnete Dateien angezeigt.

8. Erstellen Sie die Projekt Mappe, und führen Sie Sie aus.

Ihre DSL ist jetzt MEF-fähig. Sie können Menübefehle, Gesten Handler und Validierungs Einschränkungen als MEF-Erweiterungen schreiben. Sie können diese Erweiterungen in ihrer DSL-Lösung mit anderem benutzerdefiniertem Code schreiben. Außerdem können Sie oder andere Entwickler separate Visual Studio-Erweiterungen schreiben, mit denen die DSL erweitert wird.

## <a name="create-an-extension-for-a-mef-enabled-dsl"></a>Erstellen einer Erweiterung für eine MEF-aktivierte DSL

Wenn Sie Zugriff auf eine MEF-fähige DSL haben, die von Ihnen oder einer anderen Person erstellt wurde, können Sie Erweiterungen dafür schreiben. Mithilfe der Erweiterungen können Menübefehle, Gesten Handler oder Validierungs Einschränkungen hinzugefügt werden. Um diese Erweiterungen zu erstellen, verwenden Sie eine Visual Studio-Erweiterungs Lösung (VSIX). Die Lösung besteht aus zwei Teilen: einem Klassen Bibliotheksprojekt, das die Codeassembly erstellt, und einem VSIX-Projekt, das die Assembly verpackt.

### <a name="to-create-a-dsl-extension-vsix"></a>So erstellen Sie eine DSL-Erweiterung VSIX

1. Erstellen Sie ein neues **Klassenbibliotheksprojekt**.

2. Fügen Sie im neuen Projekt einen Verweis auf die Assembly der DSL hinzu.

   - Diese Assembly weist in der Regel einen Namen auf, der auf ".Dsl.dll" endet.

   - Wenn Sie Zugriff auf das DSL-Projekt haben, können Sie die Assemblydatei unter dem Verzeichnis- **DSL- \\ bin \\ \*** suchen.

   - Wenn Sie Zugriff auf die DSL-vsix-Datei haben, können Sie die Assembly suchen, indem Sie die Dateinamenerweiterung der VSIX-Datei in ". zip" ändern. Dekomprimieren der ZIP-Datei.

3. Verweise auf die folgenden .NET-Assemblys hinzufügen:

   - Microsoft.VisualStudio.Modeling.Sdk.11.0.dll

   - Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0.dll

   - Microsoft.VisualStudio.Modeling.Sdk.Shell.11.0.dll

   - System.ComponentModel.Composition.dll

   - System.Windows.Forms.dll

4. Erstellen Sie ein neues **VSIX-Projekt** Projekt.

5. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf das VSIX-Projekt, und wählen Sie **als Startprojekt festlegen** aus.

6. Öffnen Sie im neuen Projekt die Datei **Source. Extension. vsixmanifest**.

7. Klicken Sie auf **Inhalt hinzufügen**. Legen Sie im Dialogfeld " **Inhaltstyp** " auf " **MEF-Komponente**" und " **Quell Projekt** " auf das Klassen Bibliotheksprojekt fest.

8. Fügen Sie der DSL einen VSIX-Verweis hinzu.

   1. Klicken Sie in **Source. Extension. vsixmanifest** auf **Verweis hinzufügen** .

   2. Klicken Sie im Dialogfeld auf **Nutzlast hinzufügen** , und suchen Sie dann die vsix-Datei der DSL. Die vsix-Datei wird in der DSL-Lösung im **dslpackage \\ - \\ \* bin** erstellt.

       Dadurch können Benutzer die DSL und die Erweiterung gleichzeitig installieren. Wenn der Benutzer die DSL bereits installiert hat, wird nur Ihre Erweiterung installiert.

9. Überprüfen und aktualisieren Sie die anderen Felder von **Source. Extension. vsixmanifest**. Klicken Sie auf **Editionen auswählen** , und überprüfen Sie, ob die richtigen Visual Studio-Editionen festgelegt

10. Fügen Sie dem Klassen Bibliotheksprojekt Code hinzu. Verwenden Sie die Beispiele im nächsten Abschnitt als Leitfaden.

     Sie können eine beliebige Anzahl von Befehls-, Gesten-und Validierungs Klassen hinzufügen.

11. Drücken Sie **F5**, um die Erweiterung zu testen. Erstellen oder öffnen Sie in der experimentellen Instanz von Visual Studio eine Beispieldatei der DSL.

## <a name="writing-mef-extensions-for-dsls"></a>Schreiben von MEF-Erweiterungen für DSLs

Sie können Erweiterungen in das assemblycodeprojekt einer separaten DSL-Erweiterungs Lösung schreiben. Sie können MEF auch in Ihrem dslpackage-Projekt als bequeme Methode zum Schreiben von Befehlen, Gesten und Validierungscode als Teil der DSL verwenden.

### <a name="menu-commands"></a>Menübefehle

Um einen Menübefehl zu schreiben, definieren Sie eine Klasse, die implementiert <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension> und der Klasse das in ihrer DSL definierte Attribut mit dem Namen *yourdsl* vorangestellt `CommandExtension` . Sie können mehr als eine Menübefehls Klasse schreiben.

`QueryStatus()` wird aufgerufen, wenn der Benutzer mit der rechten Maustaste auf das Diagramm klickt. Er sollte die aktuelle Auswahl überprüfen und festlegen `command.Enabled` , um anzugeben, wann der Befehl anwendbar ist.

```csharp
using System.ComponentModel.Composition;
using System.Linq;
using Company.MyDsl; // My DSL
using Company.MyDsl.ExtensionEnablement; // My DSL
using Microsoft.VisualStudio.Modeling; // Transactions
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement; // IVsSelectionContext
using Microsoft.VisualStudio.Modeling.ExtensionEnablement; // ICommandExtension

namespace MyMefExtension
{
  // Defined in Dsl\MefExtension\DesignerExtensionMetaDataAttribute.cs:
  [MyDslCommandExtension]
  public class MyCommandClass : ICommandExtension
  {
    /// <summary>
    /// Provides access to current document and selection.
    /// </summary>
    [Import]
    IVsSelectionContext SelectionContext { get; set; }

    /// <summary>
    /// Called when the user selects this command.
    /// </summary>
    /// <param name="command"></param>
    public void Execute(IMenuCommand command)
    {
      // Transaction is required if you want to update elements.
      using (Transaction t = SelectionContext.CurrentStore
              .TransactionManager.BeginTransaction("fix names"))
      {
        foreach (ExampleShape shape in SelectionContext.CurrentSelection)
        {
          ExampleElement element = shape.ModelElement as ExampleElement;
          element.Name = element.Name + " !";
        }
        t.Commit();
      }
    }

    /// <summary>
    /// Called when the user right-clicks the diagram.
    /// Determines whether the command should appear.
    /// This method should set command.Enabled and command.Visible.
    /// </summary>
    /// <param name="command"></param>
    public void QueryStatus(IMenuCommand command)
    {
      command.Enabled =
        command.Visible = (SelectionContext.CurrentSelection.OfType<ExampleShape>().Count() > 0);
    }

    /// <summary>
    /// Called when the user right-clicks the diagram.
    /// Determines the text of the command in the menu.
    /// </summary>
    public string Text
    {
      get { return "My menu command"; }
    }
  }
}
```

### <a name="gesture-handlers"></a>Gesten Handler

Ein Gesten Handler kann mit Objekten umgehen, die von einem beliebigen Ort innerhalb oder außerhalb von Visual Studio auf das Diagramm gezogen werden. Im folgenden Beispiel kann der Benutzer Dateien aus Windows-Explorer auf das Diagramm ziehen. Es werden Elemente erstellt, die die Dateinamen enthalten.

Sie können Handler für den Umgang mit zieht aus anderen DSL-Modellen und UML-Modellen schreiben. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen eines Drag & Drop-Handlers](../modeling/how-to-add-a-drag-and-drop-handler.md).

```csharp
using System.ComponentModel.Composition;
using System.Linq;
using Company.MyDsl;
using Company.MyDsl.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling; // Transactions
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;

namespace MefExtension
{
  [MyDslGestureExtension]
  class MyGestureExtension : IGestureExtension
  {
    public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)
    {
      System.Windows.Forms.MessageBox.Show("double click!");
    }

    /// <summary>
    /// Called when the user drags anything over the diagram.
    /// Return true if the dragged object can be dropped on the current target.
    /// </summary>
    /// <param name="targetMergeElement">The shape or diagram that the mouse is currently over</param>
    /// <param name="diagramDragEventArgs">Data about the dragged element.</param>
    /// <returns></returns>
    public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)
    {
      // This handler only allows items to be dropped onto the diagram:
      return targetMergeElement is MefDsl2Diagram &&
      // And only accepts files dragged from Windows Explorer:
        diagramDragEventArgs.Data.GetFormats().Contains("FileNameW");
    }

    /// <summary>
    /// Called when the user drops an item onto the diagram.
    /// </summary>
    /// <param name="targetDropElement"></param>
    /// <param name="diagramDragEventArgs"></param>
    public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
    {
      MefDsl2Diagram diagram = targetDropElement as MefDsl2Diagram;
      if (diagram == null) return;

      // This handler only accepts files dragged from Windows Explorer:
      string[] draggedFileNames = diagramDragEventArgs.Data.GetData("FileNameW") as string[];
      if (draggedFileNames == null || draggedFileNames.Length == 0) return;

      using (Transaction t = diagram.Store.TransactionManager.BeginTransaction("file names"))
      {
        // Create an element to represent each file:
        foreach (string fileName in draggedFileNames)
        {
          ExampleElement element = new ExampleElement(diagram.ModelElement.Partition);
          element.Name = fileName;

          // This method of adding the new element allows the position
          // of the shape to be specified:
          ElementGroup group = new ElementGroup(element);
          diagram.ElementOperations.MergeElementGroupPrototype(
            diagram, group.CreatePrototype(), PointD.ToPointF(diagramDragEventArgs.MousePosition));
        }
        t.Commit();
      }
    }
  }
}
```

### <a name="validation-constraints"></a>Validierungs Einschränkungen

Validierungs Methoden werden durch das `ValidationExtension` -Attribut gekennzeichnet, das von der DSL generiert wird, und auch durch <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute> . Die-Methode kann in jeder Klasse vorkommen, die nicht durch ein-Attribut gekennzeichnet ist.

Weitere Informationen finden Sie unter [Validierung in einer Domain-Specific Sprache](../modeling/validation-in-a-domain-specific-language.md).

```csharp
using Company.MyDsl;
using Company.MyDsl.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.Validation;

namespace MefExtension
{
  class MyValidationExtension // Can be any class.
  {
    // SAMPLE VALIDATION METHOD.
    // All validation methods have the following attributes.

    // Specific to the extended DSL:
    [MyDslValidationExtension]

    // Determines when validation is applied:
    [ValidationMethod(
       ValidationCategories.Save
     | ValidationCategories.Open
     | ValidationCategories.Menu)]

    /// <summary>
    /// When validation is executed, this method is invoked
    /// for every element in the model that is an instance
    /// of the second parameter type.
    /// </summary>
    /// <param name="context">For reporting errors</param>
    /// <param name="elementToValidate"></param>
    private void ValidateClassNames
      (ValidationContext context,
       // Type determines to what elements this will be applied:
       ExampleElement elementToValidate)
    {
      // Write code here to test values and links.
      if (elementToValidate.Name.IndexOf(' ') >= 0)
      {
        // Log any unacceptable values:
        context.LogError(
          // Description:
          "Name must not contain spaces"
          // Error code unique to this type of error:
          , "MyDsl001"
          // Element to highlight when user double-clicks error:
          , elementToValidate);
} } } }
```

## <a name="see-also"></a>Weitere Informationen

- [Bereitstellen von Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md)
- [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)
- [Gewusst wie: Hinzufügen eines Drag & Drop-Handlers](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Validierung in einer domänenspezifischen Sprache](../modeling/validation-in-a-domain-specific-language.md)
