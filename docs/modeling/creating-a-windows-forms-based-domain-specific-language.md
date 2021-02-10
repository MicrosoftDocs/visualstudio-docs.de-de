---
title: Erstellen einer Windows Forms-basierten domänenspezifischen Sprache
description: Enthält Informationen zum Verwenden von Windows Forms, um den Status eines domänenspezifischen sprach Modells anzuzeigen.
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: 41c3ba299df1e6f9ce0e2848f7ffad59e5b3fbea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945408"
---
# <a name="create-a-windows-forms-based-domain-specific-language"></a>Erstellen einer Windows Forms basierten Domain-Specific Sprache

Sie können Windows Forms verwenden, um den Status eines DSL-Modells (Domain-Specific Language) anzuzeigen, anstatt ein DSL-Diagramm zu verwenden. In diesem Thema wird schrittweise erläutert, wie Sie ein Windows Form mithilfe des Visual Studio-Visualisierungs-und Modellierungs-SDK an eine DSL binden.

Die folgende Abbildung zeigt eine Windows Forms-Benutzeroberfläche und den Modell-Explorer für eine DSL-Instanz:

![DSL-Instanz in Visual Studio](../modeling/media/dsl-wpf-2.png)

## <a name="create-a-windows-forms-dsl"></a>Erstellen eines Windows Forms DSL

Mit der Vorlage für den **minimalen WinForm-Designer** DSL wird eine minimale DSL erstellt, die Sie entsprechend Ihren Anforderungen ändern können.

1. Erstellen Sie eine DSL aus der Vorlage für den **minimalen WinForm-Designer** .

    In dieser exemplarischen Vorgehensweise werden die folgenden Namen angenommen:

    - Lösungs-und DSL-Name: `FarmApp`
    - Namespace: `Company.FarmApp`

2. Experimentieren Sie mit dem ersten Beispiel, das von der Vorlage bereitstellt wird:

   1. Alle Vorlagen transformieren.

   2. Erstellen Sie das Beispiel (**STRG** + **F5**), und führen Sie es aus.

   3. Öffnen Sie in der experimentellen Instanz von Visual Studio die `Sample` Datei im debuggingprojekt.

        Beachten Sie, dass es in einem Windows Forms-Steuerelement angezeigt wird.

        Sie können auch die im Explorer angezeigten Elemente des Modells sehen.

        Fügen Sie einige Elemente entweder im Formular oder im Explorer hinzu, und beachten Sie, dass Sie in der anderen Anzeige angezeigt werden.

   Beachten Sie in der Haupt Instanz von Visual Studio die folgenden Punkte zur DSL-Lösung:

- `DslDefinition.dsl` enthält keine Diagramm Elemente. Dies liegt daran, dass Sie keine DSL-Diagramme verwenden, um instanzmodelle dieser DSL anzuzeigen. Stattdessen binden Sie ein Windows Form an das Modell, und die Elemente im Formular zeigen das Modell an.

- Zusätzlich zu den `Dsl` -und- `DslPackage` Projekten enthält die Projekt Mappe ein drittes Projekt mit dem Namen " `UI.` **UI** Project", das die Definition eines Windows Forms-Steuer Elements enthält. `DslPackage` hängt von ab `UI` und ist von abhängig `UI` `Dsl` .

- Enthält im- `DslPackage` Projekt `UI\DocView.cs` den Code, der das Windows Forms Steuerelement anzeigt, das im Projekt definiert ist `UI` .

- Das `UI` Projekt enthält ein funktionierendes Beispiel für ein Formular Steuerelement, das an die DSL gebunden ist. Dies funktioniert jedoch nicht, wenn Sie die DSL-Definition geändert haben. Das `UI` Projekt enthält Folgendes:

  - Eine Windows Forms Klasse mit dem Namen `ModelViewControl` .

  - Eine Datei mit dem Namen `DataBinding.cs` , die eine zusätzliche partielle Definition von enthält `ModelViewControl` . Um den Inhalt anzuzeigen, öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für die Datei, und wählen Sie **Code anzeigen** aus.

### <a name="about-the-ui-project"></a>Informationen zum UI-Projekt

Wenn Sie die DSL-Definitionsdatei aktualisieren, um Ihre eigene DSL zu definieren, müssen Sie das-Steuerelement im Projekt aktualisieren, `UI` um die DSL anzuzeigen. Im Gegensatz zu den `Dsl` `DslPackage` Projekten und wird das Beispiel `UI` Projekt nicht aus generiert `DslDefinitionl.dsl` . Sie können. tt-Dateien hinzufügen, um den Code zu generieren, wenn Sie möchten, obwohl dies in dieser exemplarischen Vorgehensweise nicht behandelt wird.

## <a name="update-the-dsl-definition"></a>Aktualisieren der DSL-Definition

Die folgende Abbildung ist die DSL-Definition, die in dieser exemplarischen Vorgehensweise verwendet wird.

![DSL-Definition](../modeling/media/dsl-wpf-1.png)

1. Öffnen Sie die Datei "DslDefinition. DSL" im DSL-Designer.

2. Löschen von **ExampleElement**

3. Benennen Sie die **examplemodel** -Domänen Klasse in um `Farm` .

     Geben Sie zusätzliche Domänen Eigenschaften mit dem Namen " `Size` **Int32**" und dem `IsOrganic` Typ " **Boolean**" an.

    > [!NOTE]
    > Wenn Sie die Stamm Domänen Klasse löschen und dann einen neuen Stamm erstellen, müssen Sie die Eigenschaft Editor-Stamm Klasse zurücksetzen. Wählen Sie im **DSL-Explorer** **Editor** aus. Legen Sie dann im Eigenschaftenfenster die Stamm **Klasse** auf fest `Farm` .

4. Verwenden Sie das **benannte Domänen Klassen** Tool, um die folgenden Domänen Klassen zu erstellen:

    - `Field` -Übergeben Sie eine zusätzliche Domänen Eigenschaft mit dem Namen `Size` .

    - `Animal` -Legen Sie in der Eigenschaftenfenster **Vererbungs Modifizierer** auf **abstract** fest.

5. Verwenden Sie das **Domänen Klassen** Tool, um die folgenden Klassen zu erstellen:

    - `Sheep`

    - `Goat`

6. Verwenden Sie das **Vererbungs** Tool, um zu erstellen `Goat` und zu `Sheep` erben `Animal` .

7. Verwenden Sie das **Einbettungs** Tool zum Einbetten von `Field` und `Animal` unter `Farm` .

8. Möglicherweise möchten Sie das Diagramm bereinigen. Um die Anzahl doppelter Elemente zu reduzieren, verwenden Sie den Befehl " **Unterstruktur hier** einfügen" im Kontextmenü der Blatt Elemente.

9. **Transformieren Sie alle Vorlagen** in der Symbolleiste von Projektmappen-Explorer.

10. Erstellen Sie das **DSL** -Projekt.

    > [!NOTE]
    > In dieser Phase werden die anderen Projekte nicht fehlerfrei erstellt. Wir möchten jedoch das DSL-Projekt so erstellen, dass die Assembly für den Datenquellen-Assistenten verfügbar ist.

## <a name="update-the-ui-project"></a>Aktualisieren des Benutzeroberflächen Projekts

Nun können Sie ein neues Benutzer Steuerelement erstellen, in dem die im DSL-Modell gespeicherten Informationen angezeigt werden. Die einfachste Möglichkeit, das Benutzer Steuerelement mit dem Modell zu verbinden, ist die Datenbindung. Der Adaptertyp für die Datenbindung mit dem Namen **modelingbindingsource** wurde speziell zum Verbinden von DSLs mit nicht-vmsdk-Schnittstellen entwickelt.

### <a name="define-your-dsl-model-as-a-data-source"></a>Definieren des DSL-Modells als Datenquelle

1. Wählen Sie im Menü **Daten** die Option **Datenquellen anzeigen** aus.

     Das Fenster **Datenquellen** wird geöffnet.

     Wählen Sie **neue Datenquelle hinzufügen** aus. Der **Assistent zum Konfigurieren von Datenquellen** wird geöffnet.

2. Wählen Sie **Objekt**, **weiter** aus.

     Erweitern Sie **DSL**, **Company. farmapp**, und wählen Sie **Farm** aus, bei der es sich um die Stamm Klasse des Modells handelt. Klicken Sie auf **Fertig stellen**.

     In Projektmappen-Explorer enthält das **UI** -Projekt jetzt " **properties\datasources\farm.DataSource** ".

     Die Eigenschaften und Beziehungen der Modell Klasse werden im Fenster Datenquellen angezeigt.

     ![Datenquellen Fenster](../modeling/media/dslwpf-3.png)

### <a name="connect-your-model-to-a-form"></a>Verbinden des Modells mit einem Formular

1. Löschen Sie im **Benutzer** Oberflächen Projekt alle vorhandenen CS-Dateien.

2. Fügen Sie dem UI-Projekt eine neue **Benutzer Steuer** Element Datei `FarmControl` mit dem Namen hinzu. 

3. Wählen Sie im Fenster **Datenquellen** im Dropdown Menü der **Farm** die Option **Details** aus.

    Überlassen Sie die Standardeinstellungen für die anderen Eigenschaften.

4. Öffnen Sie FarmControl.cs in der Entwurfs Ansicht.

    Ziehen Sie **Farm** aus dem Datenquellen Fenster auf farmcontrol.

    Eine Reihe von Steuerelementen wird angezeigt, eine für jede Eigenschaft. Die Beziehungs Eigenschaften generieren keine Steuerelemente.

5. Löschen Sie **farmbindingnavigator**. Dies wird auch automatisch im Designer generiert `FarmControl` , ist aber für diese Anwendung nicht nützlich.

6. Erstellen Sie mithilfe der Toolbox zwei Instanzen von **DataGridView**, und benennen Sie Sie `AnimalGridView` und `FieldGridView` .

   > [!NOTE]
   > Ein alternativer Schritt besteht darin, die Elemente "Animals" und "Fields" aus dem Datenquellen Fenster auf das-Steuerelement zu ziehen. Mit dieser Aktion werden automatisch Datenraster und Bindungen zwischen der Rasteransicht und der Datenquelle erstellt. Diese Bindung funktioniert für DSLs jedoch nicht ordnungsgemäß. Daher ist es besser, die Datenraster und Bindungen manuell zu erstellen.

7. Wenn das Tool **modelingbindingsource** nicht in der Toolbox enthalten ist, fügen Sie es hinzu. Wählen Sie im Kontextmenü der Registerkarte **Daten** die Option **Elemente auswählen** aus. Wählen Sie im Dialogfeld **Toolbox Elemente auswählen** auf der Registerkarte **.NET Framework** die Option **modelingbindingsource** aus.

8. Erstellen Sie mithilfe der Toolbox zwei Instanzen von **modelingbindingsource**, und benennen Sie Sie `AnimalBinding` und `FieldBinding` .

9. Legen Sie die **DataSource** -Eigenschaft der einzelnen **modelingbindingsource** auf **farmbindingsource** fest.

     Legen Sie die **DataMember** -Eigenschaft auf **animals** oder **Fields** fest.

10. Legen Sie die **DataSource** -Eigenschaften von `AnimalGridView` auf `AnimalBinding` und von  `FieldGridView` auf fest `FieldBinding` .

11. Passen Sie das Layout des Steuer Elements Farm an Ihren Geschmack an.

    **Modelingbindingsource** ist ein Adapter, der verschiedene Funktionen ausführt, die für DSLs spezifisch sind:

- Es umschließt Updates in einer vmsdk-Speicher Transaktion.

   Wenn der Benutzer z. b. eine Zeile aus dem Daten Sicht Raster löscht, würde eine reguläre Bindung zu einer Transaktions Ausnahme führen.

- Dadurch wird sichergestellt, dass die Eigenschaftenfenster die Eigenschaften des entsprechenden Modell Elements anstelle der Datenraster Zeile anzeigt, wenn der Benutzer eine Zeile auswählt.

  ![Schema der DSL-Bindung](../modeling/media/dslwpf4.png)
  
  Schema der Links zwischen Datenquellen und Sichten.

### <a name="complete-the-bindings-to-the-dsl"></a>Vervollständigen der Bindungen an die DSL

1. Fügen Sie den folgenden Code in eine separate Codedatei im **UI** -Projekt ein:

    ```csharp
    using System.ComponentModel;
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Design;

    namespace Company.FarmApp
    {
      partial class FarmControl
      {
        public IContainer Components { get { return components; } }

        /// <summary>Binds the WinForms data source to the DSL model.
        /// </summary>
        /// <param name="nodelRoot">The root element of the model.</param>
        public void DataBind(ModelElement modelRoot)
        {
          WinFormsDataBindingHelper.PreInitializeDataSources(this);
          this.farmBindingSource.DataSource = modelRoot;
          WinFormsDataBindingHelper.InitializeDataSources(this);
        }
      }
    }
    ```

2. Bearbeiten Sie im **dslpackage** -Projekt die Datei " **dslpackage\docview.tt** ", um die folgende Variablen Definition zu aktualisieren:

    ```csharp
    string viewControlTypeName = "FarmControl";
    ```

## <a name="test-the-dsl"></a>Testen der DSL

Die DSL-Lösung kann nun erstellt und ausgeführt werden, obwohl Sie möglicherweise später weitere Verbesserungen hinzufügen möchten.

1. Erstellen Sie das Projekt, und führen Sie es aus.

2. Öffnen Sie in der experimentellen Instanz von Visual Studio die **Beispiel** Datei.

3. Öffnen Sie im **farmapp-Explorer** das Kontextmenü für den Stamm Knoten **Farm** , und wählen Sie **neue Ziege hinzufügen** aus.

     `Goat1` wird in der Ansicht " **Tiere** " angezeigt.

    > [!WARNING]
    > Sie müssen das Kontextmenü auf dem **Farm** Knoten und nicht auf dem Knoten " **animals** " verwenden.

4. Wählen Sie den Stamm Knoten **Farm** aus, und zeigen Sie seine Eigenschaften an.

     Ändern Sie in der Formularansicht den **Namen** oder die **Größe** der Farm.

     Wenn Sie von jedem Feld im Formular aus navigieren, ändert sich die entsprechende-Eigenschaft in der Eigenschaftenfenster.

## <a name="enhance-the-dsl"></a>Verbessern der DSL

### <a name="make-the-properties-update-immediately"></a>Aktualisieren der Eigenschaften sofort

1. Wählen Sie in der Entwurfs Ansicht von FarmControl.cs ein einfaches Feld aus, z. b. Name, Größe oder isbio.

2. Erweitern Sie im Eigenschaftenfenster den Eintrag **DataBindings** , und öffnen Sie **(erweitert)**.

     Wählen Sie im Dialogfeld **Formatierung und erweiterte Bindung** unter **Datenquellen-Aktualisierungs Modus** die Option **OnPropertyChanged** aus.

3. Erstellen Sie das Projekt, und führen Sie es aus.

     Vergewissern Sie sich, dass die entsprechende Eigenschaft des Farm Modells sofort geändert wird, wenn Sie den Inhalt des Felds ändern.

### <a name="provide-add-buttons"></a>Add-Schaltflächen angeben

1. Verwenden Sie in der Entwurfs Ansicht von FarmControl.cs die Toolbox zum Erstellen einer Schaltfläche auf dem Formular.

    Bearbeiten Sie den Namen und den Text der Schaltfläche, z `New Sheep` . b. in.

2. Öffnen Sie den Code hinter der Schaltfläche (z. b. durch Doppelklicken).

    Bearbeiten Sie die Datei wie folgt:

   ```csharp
   private void NewSheepButton_Click(object sender, EventArgs e)
   {
     using (Transaction t = farm.Store.TransactionManager.BeginTransaction("Add sheep"))
     {
       elementOperations.MergeElementGroup(farm,
         new ElementGroup(new Sheep(farm.Partition)));
       t.Commit();
     }
   }

   // The following code is shared with other add buttons:
   private ElementOperations operationsCache = null;
   private ElementOperations elementOperations
   {
     get
     {
       if (operationsCache == null)
       {
         operationsCache = new ElementOperations(farm.Store, farm.Partition);
       }
       return operationsCache;
     }
   }
   private Farm farm
   {
     get { return this.farmBindingSource.DataSource as Farm; }
   }
   ```

    Außerdem müssen Sie die folgende Direktive einfügen:

   ```csharp

   using Microsoft.VisualStudio.Modeling;
   ```

3. Fügen Sie ähnliche Schaltflächen für Ziegen und Felder hinzu.

4. Erstellen Sie das Projekt, und führen Sie es aus.

5. Überprüfen Sie, ob die Schaltfläche neu ein Element hinzufügt. Das neue Element sollte sowohl im farmapp-Explorer als auch in der entsprechenden Datenraster Ansicht angezeigt werden.

    Sie sollten in der Lage sein, den Namen des Elements in der Datenraster Ansicht zu bearbeiten. Sie können Sie auch von dort aus löschen.

   ![Beispiel Datenraster Ansicht](../modeling/media/dsl-wpf-2.png)

### <a name="about-the-code-to-add-an-element"></a>Informationen zum Code zum Hinzufügen eines Elements

Der folgende Alternative Code ist für die Schaltflächen "Neues Element" etwas einfacher.

```csharp
private void NewSheepButton_Click(object sender, EventArgs e)
{
  using (Transaction t = farm.Store.TransactionManager.BeginTransaction("Add sheep"))
  {
    farm.Animals.Add(new Sheep(farm.Partition)); ;
    t.Commit();
  }
}
```

In diesem Code wird jedoch kein Standardname für das neue Element festgelegt. Es führt keine angepasste Zusammenführung aus, die Sie möglicherweise in den **elementmerge-Direktiven** der DSL definiert haben, und führt keinen benutzerdefinierten mergecode aus, der möglicherweise definiert wurde.

Daher wird empfohlen, <xref:Microsoft.VisualStudio.Modeling.ElementOperations> zum Erstellen neuer Elemente zu verwenden. Weitere Informationen finden Sie unter [Anpassen der Element Erstellung und-](../modeling/customizing-element-creation-and-movement.md)Verschiebung.

## <a name="see-also"></a>Weitere Informationen

- [Definieren einer Domain-Specific Sprache](../modeling/how-to-define-a-domain-specific-language.md)
- [Schreiben von Code zum Anpassen einer Domain-Specific Sprache](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Modellierungs-SDK für Visual Studio - Domänenspezifische Sprachen](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)
