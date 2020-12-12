---
title: 'Gewusst wie: Hinzufügen eines Befehls zum Kontextmenü'
description: Erfahren Sie, wie Sie Ihrer domänenspezifischen Sprache (DSL) Menübefehle hinzufügen können, damit Ihre Benutzer Aufgaben ausführen können, die für Ihre DSL spezifisch sind.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7dc51de28162471262d8c4bd35ddd09bc156896e
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363340"
---
# <a name="how-to-add-a-command-to-the-shortcut-menu"></a>Gewusst wie: Hinzufügen eines Befehls zum Kontextmenü

Sie können Ihrer domänenspezifischen Sprache (DSL) Menübefehle hinzufügen, damit Benutzer für die DSL typische Aufgaben ausführen können. Die Befehle werden im Kontextmenü angezeigt, wenn Benutzer mit der rechten Maustaste auf das Diagramm klicken. Sie können einen Befehl so definieren, dass er nur unter bestimmten Bedingungen im Menü angezeigt wird. Sie können beispielsweise angeben, dass der Befehl nur sichtbar ist, wenn der Benutzer auf bestimmte Typen von Elementen oder auf Elemente in bestimmten Zuständen klickt.

Zusammenfassend werden die Schritte im dslpackage-Projekt wie folgt ausgeführt:

1. [Deklarieren Sie den Befehl in "Commands. vsct".](#VSCT)

2. [Aktualisieren Sie die Paket Versionsnummer in Package.tt](#version). Dies müssen Sie nach jeder Änderung von Commands.vsct tun.

3. [Schreiben Sie Methoden in der CommandSet-Klasse](#CommandSet) , um den Befehl sichtbar zu machen und zu definieren, was der Befehl tun soll.

> [!NOTE]
> Sie können auch das Verhalten einiger vorhandener Befehle wie Ausschneiden, Einfügen, Alle auswählen und Drucken ändern, indem Sie die entsprechenden Methoden in "CommandSet.cs" überschreiben. Weitere Informationen finden Sie unter Gewusst [wie: Ändern eines Standard Menübefehls](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

## <a name="define-a-command-using-mef"></a>Definieren eines Befehls mithilfe von MEF

Managed Extension Framework (MEF) bietet eine alternative Möglichkeit, Menübefehle im Diagrammmenü zu definieren. Sein Hauptzweck besteht darin, Ihnen oder anderen Personen die Erweiterung einer DSL zu ermöglichen. Benutzer können entweder nur die DSL oder die DSL und Erweiterungen installieren. Nach dem anfänglichen Aufwand der Aktivierung von MEF für die DSL vereinfacht MEF jedoch das Definieren von Kontextmenübefehlen.

Verwenden Sie das Verfahren in diesem Thema in folgenden Fällen:

1. Sie möchten Menübefehle in anderen Menüs als dem Rechtsklick-Kontextmenü definieren.

2. Sie möchten bestimmte Gruppierungen von Befehlen im Menü definieren.

3. Sie möchten nicht, dass andere Personen die DSL mit ihren eigenen Befehlen erweitern können.

4. Sie möchten nur einen einzelnen Befehl definieren.

   In anderen Fällen können Sie die MEF-Methode zum Definieren von Befehlen in Betracht ziehen. Weitere Informationen finden Sie unter [Erweitern Ihrer DSL mithilfe von MEF](../modeling/extend-your-dsl-by-using-mef.md).

## <a name="declare-the-command-in-commandsvsct"></a><a name="VSCT"></a> Deklarieren Sie den Befehl in "Commands. vsct".
 Menübefehle werden in "DslPackage\Commands.vsct" deklariert. Diese Definitionen definieren die Bezeichnungen der Menüelemente und ihre Position in den Menüs.

 Die Datei, die Sie bearbeiten, Commands. vsct, importiert Definitionen aus mehreren h-Dateien, die sich im Verzeichnis " *Visual Studio SDK-Installationspfad*\visualstudiointegration\common\inc" befinden. Sie enthält auch "generatedvsct. vsct", das aus ihrer DSL-Definition generiert wird.

 Weitere Informationen zu vsct-Dateien finden Sie unter [Visual Studio Command Table (. Vsct-Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

### <a name="to-add-the-command"></a>So fügen Sie den Befehl hinzu

1. Öffnen Sie in **Projektmappen-Explorer** unter dem **dslpackage** -Projekt die Datei Commands. vsct.

2. Definieren Sie im `Commands`-Element mindestens eine Schaltfläche und eine Gruppe. Eine *Schaltfläche* ist ein Element im Menü. Eine *Gruppe* ist ein Abschnitt im Menü. Fügen Sie folgende Elemente hinzu, um diese Objekte zu definieren:

    ```xml
    <!-- Define a group - a section in the menu -->
    <Groups>
      <Group guid="guidCustomMenuCmdSet" id="grpidMyMenuGroup" priority="0x0100">
        <!-- These symbols are defined in GeneratedVSCT.vsct -->
        <Parent guid="guidCmdSet" id="menuidContext" />
      </Group>
    </Groups>
    <!-- Define a button - a menu item - inside the Group -->
    <Buttons>
      <Button guid="guidCustomMenuCmdSet" id="cmdidMyContextMenuCommand"
        priority="0x0100" type="Button">
        <Parent guid="guidCustomMenuCmdSet" id="grpidMyMenuGroup"/>
        <!-- If you do not want to place the command in your own Group,
             use Parent guid="guidCmdSet" id="grpidContextMain".
             These symbols are defined in GeneratedVSCT.vsct -->
        <CommandFlag>DynamicVisibility</CommandFlag>
        <Strings>
          <ButtonText>My Context Menu Command</ButtonText>
        </Strings>
      </Button>
    </Buttons>
    ```

    > [!NOTE]
    > Jede Schaltfläche oder Gruppe wird durch eine GUID und eine ganzzahlige ID identifiziert. Sie können mehrere Gruppen und Schaltflächen mit derselben GUID erstellen. Alle Gruppen und Schaltflächen müssen jedoch unterschiedliche IDs aufweisen. Die GUID-Namen und ID-Namen werden in tatsächliche GUIDs und numerische IDs im `<Symbols>` Knoten übersetzt.

3. Fügen Sie eine Sichtbarkeitseinschränkung für den Befehl hinzu, sodass er nur im Kontext der domänenspezifischen Sprache geladen wird. Weitere Informationen finden Sie unter [visibilityrestriselement](../extensibility/visibilityconstraints-element.md).

     Fügen Sie hierzu im `CommandTable`-Element nach dem `Commands`-Element die folgenden Elemente hinzu.

    ```xml
    <VisibilityConstraints>
      <!-- Ensures the command is only loaded for this DSL -->
      <VisibilityItem guid="guidCustomMenuCmdSet" id="cmdidMyContextMenuCommand"
        context="guidEditor"/>
    </VisibilityConstraints>
    ```

4. Definieren Sie die Namen, die Sie für die GUIDs und IDs verwendet haben. Fügen Sie hierzu im `Symbols`-Element nach dem `CommandTable`-Element ein `Commands`-Element hinzu.

    ```xml
    <Symbols>
      <!-- Substitute a unique GUID for the placeholder: -->
      <GuidSymbol name="guidCustomMenuCmdSet"
        value="{00000000-0000-0000-0000-000000000000}" >
        <IDSymbol name="grpidMyMenuGroup" value="0x01001"/>
        <IDSymbol name="cmdidMyContextMenuCommand" value="0x00001"/>
      </GuidSymbol>
    </Symbols>
    ```

5. Ersetzen Sie `{000...000}` durch eine GUID, die Ihre Gruppen und Menüelemente identifiziert. Verwenden Sie zum Abrufen einer neuen GUID das Tool zum **Erstellen von GUID** **im Menü Extras** .

    > [!NOTE]
    > Wenn Sie mehrere Gruppen oder Menüelemente hinzufügen, können Sie dieselbe GUID verwenden. Sie müssen aber neue Werte für `IDSymbols` verwenden.

6. Ersetzen Sie in dem Code, den Sie aus diesem Verfahren kopiert haben, jedes Vorkommen der folgenden Zeichenfolgen durch Ihre eigenen Zeichenfolgen:

    - `grpidMyMenuGroup`

    - `cmdidMyContextMenuCommand`

    - `guidCustomMenuCmdSet`

    - `My Context Menu Command`

## <a name="update-the-package-version-in-packagett"></a><a name="version"></a> Aktualisieren der Paket Version in Package.tt
 Immer wenn Sie einen Befehl hinzufügen oder ändern, müssen Sie den `version`-Parameter des Attributs <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> aktualisieren, das auf die Paketklasse angewendet wird, bevor Sie die neue Version der domänenspezifischen Sprache veröffentlichen.

 Da die Paketklasse in einer generierten Datei definiert wird, müssen Sie das Attribut in der Textvorlagendatei aktualisieren, aus der die Datei Package.cs generiert wird.

### <a name="to-update-the-packagett-file"></a>So aktualisieren Sie die Datei Package.tt

1. Öffnen Sie in **Projektmappen-Explorer** im **dslpackage** -Projekt im Ordner **generatedcode** die Datei Package.tt.

2. Suchen Sie das `ProvideMenuResource`-Attribut.

3. Erhöhen Sie den `version`-Parameter des Attributs. Es ist der zweite Parameter. Auf Wunsch können Sie den Parameternamen explizit angeben, um sich an den Zweck zu erinnern. Zum Beispiel:

     `[VSShell::ProvideMenuResource("1000.ctmenu", version: 2 )]`

## <a name="define-the-behavior-of-the-command"></a><a name="CommandSet"></a> Definieren des Verhaltens des Befehls

Die DSL umfasst bereits einige Befehle. Diese sind in einer partiellen Klasse implementiert, die in "DslPackage\GeneratedCode\CommandSet.cs" deklariert ist. Um neue Befehle hinzuzufügen, müssen Sie diese Klasse erweitern. Dazu erstellen Sie eine neue Datei mit einer partiellen Deklaration derselben Klasse. Der Name der Klasse ist in der Regel *\<YourDslName>* `CommandSet` . Es ist hilfreich zu beginnen, indem Sie den Namen der Klasse überprüfen und ihren Inhalt überprüfen.

Die Befehlssatzklasse wird von <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> abgeleitet.

### <a name="extend-the-commandset-class"></a>Erweitern der CommandSet-Klasse

1. Öffnen Sie im Projektmappen-Explorer im Projekt "DslPackage" den Ordner "GeneratedCode". Suchen Sie unter "CommandSet.tt" die generierte Datei "CommandSet.cs", und öffnen Sie sie. Notieren Sie sich den Namespace und den Namen der ersten dort definierten Klasse. Es wird beispielsweise Folgendes angezeigt:

     `namespace Company.Language1`

     `{ ...  internal partial class Language1CommandSet : ...`

2. Erstellen Sie in **dslpackage** einen Ordner mit dem Namen **benutzerdefinierter Code**. Erstellen Sie in diesem Ordner eine neue Klassendatei mit dem Namen `CommandSet.cs` .

3. Schreiben Sie in die neue Datei eine partielle Deklaration mit demselben Namespace und Namen wie die generierte partielle Klasse. Zum Beispiel:

     `namespace Company.Language1 /* Make sure this is correct */`

     `{ internal partial class Language1CommandSet { ...`

     > [!NOTE]
     > Wenn Sie die Klassen Vorlage verwendet haben, um die neue Datei zu erstellen, müssen Sie sowohl den Namespace als auch den Klassennamen korrigieren.

Ihr Befehlssatzcode muss in der Regel folgende Namespaces importieren:

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel.Design;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Shell;
```

Passen Sie den Namespace und den Klassennamen an, sodass sie mit denen in der generierten Datei CommandSet.cs übereinstimmen:

```csharp
namespace Company.Language1 /* Make sure this is correct */
{
  // Same class as the generated class.
  internal partial class Language1CommandSet
  {
```

Sie müssen zwei Methoden definieren, eine, um zu bestimmen, wann der Befehl im Kontextmenü (Kontextmenü) angezeigt wird, und der andere, um den Befehl auszuführen. Diese Methoden sind keine Überschreibungen, sondern Sie registrieren sie in einer Liste von Befehlen.

### <a name="define-when-the-command-will-be-visible"></a>Definieren, wann der Befehl sichtbar ist
 Definieren Sie für jeden Befehl eine `OnStatus...` Methode, die bestimmt, ob der Befehl im Menü angezeigt wird und ob er aktiviert oder abgeblendet wird. Legen Sie die `Visible` -Eigenschaft und die-Eigenschaft des fest `Enabled` `MenuCommand` , wie im folgenden Beispiel gezeigt. Diese Methode wird jedes Mal, wenn der Benutzer mit der rechten Maustaste auf das Diagramm klickt, aufgerufen, um das Kontextmenü zu erstellen. Daher muss sie schnell ausführbar sein.

 Im Beispiel ist der Befehl nur sichtbar, wenn der Benutzer einen bestimmten Formtyp ausgewählt hat. Und er wird nur aktiviert, wenn sich mindestens eines der ausgewählten Elemente in einem bestimmten Zustand befindet. Das Beispiel basiert auf der Vorlage "Klassendiagramm-DSL", und ClassShape und ModelClass sind in der DSL definierte Typen:

```csharp
private void OnStatusMyContextMenuCommand(object sender, EventArgs e)
{
  MenuCommand command = sender as MenuCommand;
  command.Visible = command.Enabled = false;
  foreach (object selectedObject in this.CurrentSelection)
  {
    ClassShape shape = selectedObject as ClassShape;
    if (shape != null)
    {
      // Visibility depends on what is selected.
      command.Visible = true;
      ModelClass element = shape.ModelElement as ModelClass;
      // Enabled depends on state of selection.
      if (element != null && element.Comments.Count == 0)
      {
        command.Enabled = true;
        return; // seen enough
} } } }
```

Die folgenden Fragmente sind häufig in OnStatus-Methoden nützlich:

- `this.CurrentSelection`. Die Form, auf die der Benutzer mit der rechten Maustaste geklickt hat, wird immer in diese Liste aufgenommen. Wenn der Benutzer auf einen leeren Bereich des Diagramms klickt, ist das Diagramm das einzige Mitglied der Liste.

- `this.IsDiagramSelected()` - `true` , wenn der Benutzer auf einen leeren Teil des Diagramms geklickt hat.

- `this.IsCurrentDiagramEmpty()`

- `this.IsSingleSelection()` -der Benutzer hat nicht mehrere Objekte ausgewählt.

- `this.SingleSelection` die Form oder das Diagramm, auf die der Benutzer mit der rechten Maustaste geklickt hat

- `shape.ModelElement as MyLanguageElement` -das Modellelement, das durch eine Form dargestellt wird.

Generell sollten Sie die `Visible`-Eigenschaft davon abhängig machen, was ausgewählt ist, und die `Enabled`-Eigenschaft vom Zustand der ausgewählten Elemente abhängig machen.

Eine OnStatus-Methode sollte nicht den Zustand des Speichers ändern.

### <a name="define-what-the-command-does"></a>Definieren der Aktionen des Befehls
 Definieren Sie für jeden Befehl eine `OnMenu...`-Methode, die die erforderliche Aktion ausführt, wenn der Benutzer auf den Menübefehl klickt.

 Falls Sie Modellelemente ändern, müssen Sie dies in einer Transaktion tun. Weitere Informationen finden Sie unter Gewusst [wie: Ändern eines Standard Menübefehls](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

 Im Beispiel sind `ClassShape`, `ModelClass` und `Comment` Typen, die in der DSL definiert sind, die von der Klassendiagramm-DSL-Vorlage abgeleitet ist.

```csharp
private void OnMenuMyContextMenuCommand(object sender, EventArgs e)
{
  MenuCommand command = sender as MenuCommand;
  Store store = this.CurrentDocData.Store;
  // Changes to elements and shapes must be performed in a Transaction.
  using (Transaction transaction =
       store.TransactionManager.BeginTransaction("My command"))
  {
    foreach (object selectedObject in this.CurrentSelection)
    {
      // ClassShape is defined in my DSL.
      ClassShape shape = selectedObject as ClassShape;
      if (shape != null)
      {
        // ModelClass is defined in my DSL.
        ModelClass element = shape.ModelElement as ModelClass;
        if (element != null)
        {
          // Do required action here - for example:

          // Create a new element. Comment is defined in my DSL.
          Comment newComment = new Comment(element.Partition);
          // Every element must be the target of an embedding link.
          element.ModelRoot.Comments.Add(newComment);
          // Set properties of new element.
          newComment.Text = "This is a comment";
          // Create a reference link to existing object.
          element.Comments.Add(newComment);
        }
      }
    }
    transaction.Commit(); // Don't forget this!
  }
}
```

 Weitere Informationen zum Navigieren von einem Objekt zu einem Objekt im Modell und zum Erstellen von Objekten und Verknüpfungen finden Sie unter Gewusst [wie: Ändern eines Standard Menübefehls](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

### <a name="register-the-command"></a>Registrieren des Befehls
 Wiederholen Sie in C# die Deklarationen der GUID- und ID-Werte, die Sie im Abschnitt "Symbols" von CommandSet.vsct ausgeführt haben:

```csharp
private Guid guidCustomMenuCmdSet =
    new Guid("00000000-0000-0000-0000-000000000000");
private const int grpidMyMenuGroup = 0x01001;
private const int cmdidMyContextMenuCommand = 1;
```

 Verwenden Sie denselben GUID-Wert, den Sie in " **Commands. vsct**" eingefügt haben.

> [!NOTE]
> Wenn Sie den Abschnitt "Symbols" in der VSCT-Datei ändern, müssen Sie auch diese Deklarationen entsprechend ändern. Außerdem sollten Sie die Versionsnummer in Package.tt erhöhen.

 Registrieren Sie Ihre Menübefehle im Rahmen dieses Befehlssatzes. `GetMenuCommands()` wird einmal aufgerufen, wenn das Diagramm initialisiert wird:

```csharp
protected override IList<MenuCommand> GetMenuCommands()
{
  // Get the list of generated commands.
  IList<MenuCommand> commands = base.GetMenuCommands();
  // Add a custom command:
  DynamicStatusMenuCommand myContextMenuCommand =
    new DynamicStatusMenuCommand(
      new EventHandler(OnStatusMyContextMenuCommand),
      new EventHandler(OnMenuMyContextMenuCommand),
      new CommandID(guidCustomMenuCmdSet, cmdidMyContextMenuCommand));
  commands.Add(myContextMenuCommand);
  // Add more commands here.
  return commands;
}
```

## <a name="test-the-command"></a>Testen des Befehls
 Erstellen Sie die DSL, und führen Sie sie in einer experimentellen Instanz von Visual Studio aus. Der Befehl sollte in den von Ihnen angegebenen Situationen im Kontextmenü erscheinen.

### <a name="to-exercise-the-command"></a>So führen Sie den Befehl aus

1. Klicken Sie auf der Symbolleiste **Projektmappen-Explorer** auf **alle Vorlagen transformieren**.

2. Drücken Sie **F5** , um die Projekt Mappe neu zu erstellen, und starten Sie das Debuggen der domänenspezifischen Sprache im experimentellen Build.

3. Öffnen Sie im experimentellen Build ein Beispieldiagramm.

4. Klicken Sie mit der rechten Maustaste auf verschiedene Elemente im Diagramm, um zu überprüfen, ob der Befehl richtig aktiviert bzw. deaktiviert und je nach ausgewähltem Element angezeigt oder ausgeblendet wird.

## <a name="troubleshoot"></a>Problembehandlung

**Der Befehl wird nicht im Menü angezeigt:**

- Der Befehl wird nur in Debuginstanzen von Visual Studio angezeigt, bis Sie das DSL-Paket installiert haben. Weitere Informationen finden Sie unter [Deploying Domain-Specific Language Solutions (Bereitstellen von Projektmappen für eine domänenspezifische Sprache)](msi-and-vsix-deployment-of-a-dsl.md).

- Stellen Sie sicher, dass Ihr experimentelles Beispiel die richtige Dateinamenerweiterung für diese DSL hat. Öffnen Sie "DslDefinition.dsl" in der Hauptinstanz von Visual Studio, um die Dateinamenerweiterung zu überprüfen. Klicken Sie dann in DSL Explorer mit der rechten Maustaste auf den Editor-Knoten, und klicken Sie auf "Eigenschaften". Untersuchen Sie im Eigenschaftenfenster die Eigenschaft "FileExtension".

- Haben Sie [die Paket Versionsnummer erhöht](#version)?

- Setzen Sie am Anfang der OnStatus-Methode einen Haltepunkt. Er sollte die Verarbeitung anhalten, wenn Sie mit der rechten Maustaste auf einen Bereich des Diagramms klicken.

Die **OnStatus-Methode wird nicht aufgerufen**:

- Vergewissern Sie sich, dass die GUIDs und IDs in Ihrem CommandSet-Code mit denen im Abschnitt "Symbols" von Commands.vsct übereinstimmen.

- Überprüfen Sie in Commands.vsct, ob die GUID und ID in jedem Parent-Knoten die richtige übergeordnete Gruppe identifizieren.

- Geben Sie an einer Visual Studio-Eingabeaufforderung Folgendes ein: devenv /rootsuffix exp /setup. Starten Sie dann die Debuginstanz von Visual Studio neu.

- Durchlaufen Sie die OnStatus-Methode schrittweise, um zu überprüfen, ob "command.Visible" und "command.Enabled" auf True festgelegt sind.

**Der falsche Menütext wird angezeigt, oder der Befehl wird an der falschen Stelle angezeigt**:

- Stellen Sie sicher, dass die Kombination von GUID und ID für diesen Befehl eindeutig ist.

- Stellen Sie sicher, dass frühere Versionen des Pakets deinstalliert wurden.

## <a name="see-also"></a>Siehe auch

- [Schreiben von Code zum Anpassen einer domänenspezifischen Sprache](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Gewusst wie: Ändern eines Standardmenü Befehls](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)
- [Bereitstellen von domänenspezifischen Sprachlösungen](msi-and-vsix-deployment-of-a-dsl.md)
- [Beispielcode: Leitungs Diagramme](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
