---
title: Anpassen des Eigenschaftenfensters
description: Erfahren Sie, wie Sie die Darstellung und das Verhalten des Fensters "Eigenschaften" in ihrer domänenspezifischen Sprache (DSL) in Visual Studio anpassen können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language, Properties window
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b7ee201494ed849062458afdcd41c2aed1b83b42
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935390"
---
# <a name="customize-the-properties-window"></a>Anpassen des Eigenschaftenfenster

Sie können die Darstellung und das Verhalten des Fensters Eigenschaften in ihrer domänenspezifischen Sprache (DSL) in Visual Studio anpassen. In ihrer DSL-Definition definieren Sie Domänen Eigenschaften für jede Domänen Klasse. Wenn Sie eine Instanz der-Klasse entweder in einem Diagramm oder im Modell-Explorer auswählen, wird standardmäßig jede Domänen Eigenschaft im Eigenschaften Fenster aufgelistet. Auf diese Weise können Sie die Werte von Domänen Eigenschaften anzeigen und bearbeiten, auch wenn Sie Sie nicht den Formen Feldern im Diagramm zugeordnet haben.

## <a name="names-descriptions-and-categories"></a>Namen, Beschreibungen und Kategorien

**Name und Anzeige Name**. In der Definition einer Domänen Eigenschaft ist der Anzeige Name der Eigenschaft der Name, der zur Laufzeit im Eigenschaften Fenster angezeigt wird. Im Gegensatz dazu wird der Name verwendet, wenn Sie Programmcode schreiben, um die Eigenschaft zu aktualisieren. Der Name muss ein korrekter CLR-alphanumerischer Name sein, aber der Anzeige Name kann Leerzeichen enthalten.

Wenn Sie den Namen einer Eigenschaft in der DSL-Definition festlegen, wird der Anzeige Name automatisch auf eine Kopie des namensfest gelegt. Wenn Sie einen Namen für die Pascal-Schreibweise schreiben, z. b. "fuelmessgerät", enthält der Anzeige Name automatisch ein Leerzeichen: "Kraftstoff Messgerät". Sie können den anzeigen Amen jedoch explizit auf einen anderen Wert festlegen.

**Beschreibung**. Die Beschreibung einer Domänen Eigenschaft wird an zwei Stellen angezeigt:

- Am unteren Rand des Fensters Eigenschaften, wenn der Benutzer die Eigenschaft auswählt. Sie können es verwenden, um dem Benutzer zu erklären, was die Eigenschaft darstellt.

- Im generierten Programmcode. Wenn Sie die Dokumentations Funktionen zum Extrahieren der API-Dokumentation verwenden, wird Sie als Beschreibung dieser Eigenschaft in der API angezeigt.

**Kategorie** Eine Kategorie ist eine Überschrift in der Eigenschaftenfenster.

## <a name="expose-style-features"></a>Verfügbar machen von Stil Features

Einige dynamische Features von grafischen Elementen *können als* Domänen Eigenschaften dargestellt oder verfügbar gemacht werden. Eine Funktion, die auf diese Weise verfügbar gemacht wurde, kann vom Benutzer aktualisiert werden und kann durch Programmcode leichter aktualisiert werden.

Klicken Sie mit der rechten Maustaste auf eine Shape-Klasse in der DSL-Definition, zeigen **Sie auf verfügbar** machen, und wählen Sie dann eine Funktion

In Shapes können Sie die Eigenschaften **FillColor**, **OutlineColor**, **TextColor**, **outlinedashstyle**, **outlinethickness** und **fillgradientmode** verfügbar machen. Auf Connectors können Sie die **Farben** `,` **TextColor**, **DashStyle** und **Dicke** verfügbar machen. In Diagrammen können Sie die Eigenschaften **FillColor** und **TextColor** verfügbar machen.

## <a name="forwarding-display-properties-of-related-elements"></a>Weiterleitung: Anzeigen von Eigenschaften verwandter Elemente

Wenn der Benutzer Ihrer DSL ein Element in einem Modell auswählt, werden die Eigenschaften des Elements im Eigenschaften Fenster angezeigt. Sie können jedoch auch die Eigenschaften der angegebenen verknüpften Elemente anzeigen. Dies ist hilfreich, wenn Sie eine Gruppe von Elementen definiert haben, die zusammenarbeiten. Sie können z. b. ein Hauptelement und ein optionales Plug-in-Element definieren. Wenn das Hauptelement einer Form zugeordnet ist und die andere nicht, ist es hilfreich, alle Eigenschaften so anzuzeigen, als wären Sie auf einem Element.

Dieser Effekt wird als *Eigenschaften Weiterleitung* bezeichnet und erfolgt in mehreren Fällen automatisch. In anderen Fällen können Sie die Eigenschaften Weiterleitung erreichen, indem Sie einen Domänentyp Deskriptor definieren.

### <a name="default-property-forwarding-cases"></a>Standardmäßige Eigenschaften Weiterleitungs Fälle

Wenn der Benutzer eine Form oder einen Connector oder ein Element im Explorer auswählt, werden die folgenden Eigenschaften im Eigenschaftenfenster angezeigt:

- Die Domänen Eigenschaften, die für die Domänen Klasse des Modell Elements definiert sind, einschließlich derjenigen, die in Basisklassen definiert sind. Bei einer Ausnahme **handelt es sich** um Domänen Eigenschaften, für die Sie die durchsuchbar festgelegt haben `False` .

- Die Namen von Elementen, die durch Beziehungen verknüpft werden, die eine Multiplizität von 0.. 1 aufweisen. Dies stellt eine bequeme Methode dar, optional verknüpfte Elemente zu sehen, auch wenn Sie keine Connector-Zuordnung für die Beziehung definiert haben.

- Domänen Eigenschaften der Embedding Relationship, die das-Element als Ziel hat. Da Einbett Ende Beziehungen in der Regel nicht explizit angezeigt werden, können Benutzer ihre Eigenschaften anzeigen.

- Domänen Eigenschaften, die für die ausgewählte Form oder den ausgewählten Connector definiert sind.

### <a name="add-property-forwarding"></a>Eigenschaften Weiterleitung hinzufügen

Um eine Eigenschaft weiterzuleiten, definieren Sie einen Domänentyp Deskriptor. Wenn Sie über eine Domänen Beziehung zwischen zwei Domänen Klassen verfügen, können Sie einen Domänentyp Deskriptor verwenden, um eine Domänen Eigenschaft in der ersten Klasse auf den Wert einer Domänen Eigenschaft in der zweiten Domänen Klasse festzulegen. Wenn Sie z. b. über eine Beziehung zwischen einer **Buch** Domänen Klasse und einer Domänen Klasse vom Typ " **Autor** " verfügen, können Sie mithilfe eines Domänentyp Deskriptors festlegen, dass die Eigenschaft " **Name** " des **Autors** eines Buchs im Eigenschaftenfenster angezeigt wird, wenn der Benutzer das Buch auswählt.

> [!NOTE]
> Die Eigenschaften Weiterleitung wirkt sich nur auf die Eigenschaftenfenster aus, wenn der Benutzer ein Modell bearbeitet. Es wird keine Domänen Eigenschaft für die empfangende Klasse definiert. Wenn Sie in anderen Teilen der DSL-Definition oder im Programmcode auf die Eigenschaft der weitergeleiteten Domäne zugreifen möchten, müssen Sie auf das Weiterleitungs Element zugreifen.

Bei der folgenden Prozedur wird davon ausgegangen, dass Sie eine DSL erstellt haben. In den ersten Schritten werden die Voraussetzungen zusammengefasst.

#### <a name="forward-a-property-from-another-element"></a>Weiterleiten einer Eigenschaft von einem anderen Element

1. Erstellen Sie eine Projekt Mappe, die mindestens [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] zwei Klassen enthält, die in diesem Beispiel " **Book** " und " **Author**" genannt werden. Es sollte eine Beziehung zwischen **Buch** und **Autor** vorhanden sein.

    Die Multiplizität der Quell Rolle (die Rolle auf der **Buchseite** ) sollte 0.. 1 oder 1.. 1 lauten, damit jedes **Buch** über einen **Autor** verfügt.

2. Klicken Sie im **DSL-Explorer** mit der rechten Maustaste auf die Klasse **Book** Domain, und klicken Sie dann auf **Add New domaintypedescriptor**.

    Unter dem Knoten **benutzerdefinierter Typdeskriptor** wird ein Knoten mit dem Namen **Pfade von benutzerdefinierten Eigenschaften Deskriptoren** angezeigt.

3. Klicken Sie mit der rechten Maustaste auf den Knoten **benutzerdefinierter Typdeskriptor** , und klicken Sie dann auf **neuen PropertyPath hinzufügen**.

    Ein neuer Eigenschafts Pfad wird unter dem Knoten **Pfade für benutzerdefinierte Eigenschaften Deskriptoren** angezeigt.

4. Wählen Sie den neuen Eigenschafts Pfad aus, und legen Sie im **Eigenschaften** Fenster **Pfad auf Eigenschaft** auf den Pfad des entsprechenden Modell Elements fest.

    Sie können den Pfad in einer Strukturansicht bearbeiten, indem Sie auf den Pfeil nach unten rechts neben dieser Eigenschaft klicken. Weitere Informationen zu Domänen Pfaden finden Sie unter [Domänen Pfad Syntax](../modeling/domain-path-syntax.md). Wenn Sie sie bearbeitet haben, sollte der Pfad **bookreferencesauthor. Author/! lauten. Autor**.

5. Legen Sie die **Eigenschaft** auf die **Name** Domain-Eigenschaft von **Author** fest.

6. Legen Sie **Anzeige Name** auf **Autor Name** fest.

7. Transformieren Sie alle Vorlagen, erstellen Sie die DSL und führen Sie Sie aus.

8. Erstellen Sie in einem Modell Diagramm ein Buch, einen Autor, und verknüpfen Sie Sie mithilfe der Verweis Beziehung. Wählen Sie das book-Element aus, und in der Eigenschaftenfenster der Name des Autors zusätzlich zu den Eigenschaften des Buchs angezeigt werden soll. Ändern Sie den Namen des verknüpften Autors, oder verknüpfen Sie das Buch mit einem anderen Autor, und beachten Sie, dass sich der Autor Name des Buchs ändert.

## <a name="custom-property-editors"></a>Editors für benutzerdefinierte Eigenschaften

Das Eigenschaften Fenster bietet eine geeignete Standard Bearbeitungsfunktion für den Typ der einzelnen Domänen Eigenschaften. Für einen enumerierten Typ wird dem Benutzer beispielsweise eine Dropdown Liste angezeigt, und für eine numerische Eigenschaft kann der Benutzer Ziffern eingeben. Dies gilt nur für die integrierten Typen. Wenn Sie einen externen Typ angeben, kann der Benutzer die Eigenschaftswerte anzeigen, aber nicht bearbeiten.

Sie können jedoch die folgenden Editoren und Typen angeben:

1. Ein anderer Editor, der mit einem Standardtyp verwendet wird. Beispielsweise können Sie einen Dateipfad-Editor für eine Zeichen folgen Eigenschaft angeben.

2. Ein externer Typ für die Domänen Eigenschaft und ein Editor dafür.

3. Einen .net-Editor, z. b. den Dateipfad-Editor, oder Sie können einen eigenen benutzerdefinierten Eigenschaften-Editor erstellen.

   Eine Konvertierung zwischen einem externen Typ und einem Typ, wie z. b. String, der über einen Standard Editor verfügt.

   In einer DSL ist ein *externer Typ* ein beliebiger Typ, bei dem es sich nicht um einen der einfachen Typen (z. b. Boolean oder Int32) oder eine Zeichenfolge handelt.

### <a name="define-a-domain-property-that-has-an-external-type"></a>Definieren Sie eine Domänen Eigenschaft mit einem externen Typ.

1. Fügen Sie in **Projektmappen-Explorer** einen Verweis auf die Assembly (dll) hinzu, die den externen Typ im **DSL** -Projekt enthält.

    Die Assembly kann eine .NET-Assembly oder eine von Ihnen bereitgestellte Assembly sein.

2. Fügen Sie den Typ der Liste **Domänen Typen** hinzu, sofern Sie dies nicht bereits getan haben.

   1. Öffnen Sie DslDefinition. DSL, und klicken Sie im **DSL-Explorer** mit der rechten Maustaste auf den Stamm Knoten, und klicken Sie dann auf **neuen externen Typ hinzufügen**.

        Unter dem Knoten **Domänen Typen** wird ein neuer Eintrag angezeigt.

       > [!WARNING]
       > Das Menü Element befindet sich auf dem DSL-Stamm Knoten, nicht auf dem Knoten **Domänen Typen** .

   2. Legen Sie den Namen und den Namespace des neuen Typs in der Eigenschaftenfenster fest.

3. Fügen Sie einer Domänen Klasse auf die übliche Weise eine Domänen Eigenschaft hinzu.

    Wählen Sie im Eigenschaftenfenster den externen Typ aus der Dropdown Liste im Feld **Typ** aus.

   In dieser Phase können Benutzer die Werte der Eigenschaft anzeigen, Sie können Sie jedoch nicht bearbeiten. Die angezeigten Werte werden von der- `ToString()` Funktion abgerufen. Sie könnten Programmcode schreiben, mit dem der Wert der Eigenschaft festgelegt wird, z. b. in einem Befehl oder einer Regel.

### <a name="set-a-property-editor"></a>Festlegen eines Eigenschaften-Editors

Fügen Sie der Domänen Eigenschaft in der folgenden Form ein CLR-Attribut hinzu:

```csharp
[System.ComponentModel.Editor (
   typeof(AnEditor),
   typeof(System.Drawing.Design.UITypeEditor))]
```

Sie können das-Attribut für eine Eigenschaft festlegen, indem Sie in der Eigenschaftenfenster den Eintrag **benutzerdefiniertes Attribut** verwenden.

Der Typ von `AnEditor` muss von dem Typ abgeleitet werden, der im zweiten Parameter angegeben ist. Der zweite Parameter muss entweder <xref:System.Drawing.Design.UITypeEditor> oder sein <xref:System.ComponentModel.ComponentEditor> . Weitere Informationen finden Sie unter <xref:System.ComponentModel.EditorAttribute>.

Sie können einen eigenen Editor oder einen .net-Editor, z <xref:System.Windows.Forms.Design.FileNameEditor> . b. oder, angeben <xref:System.Drawing.Design.ImageEditor> . Verwenden Sie beispielsweise das folgende Verfahren, um eine Eigenschaft zu verwenden, in der der Benutzer einen Dateinamen eingeben kann.

#### <a name="define-a-file-name-domain-property"></a>Definieren einer Dateinamen-Domänen Eigenschaft

1. Fügen Sie eine Domänen Eigenschaft zu einer Domänen Klasse in ihrer DSL-Definition hinzu.

2. Wählen Sie die neue Eigenschaft aus. Geben Sie im Eigenschaftenfenster Feld **benutzerdefiniertes Attribut** das folgende Attribut ein. Um dieses Attribut einzugeben, klicken Sie auf die Auslassungs Punkte **[...]** , und geben Sie dann den Attributnamen und die Parameter separat ein:

    ```csharp
    [System.ComponentModel.Editor (
       typeof(System.Windows.Forms.Design.FileNameEditor)
       , typeof(System.Drawing.Design.UITypeEditor))]

    ```

3. Belassen Sie den Typ der Domänen Eigenschaft bei der Standardeinstellung der **Zeichenfolge**.

4. Um den Editor zu testen, vergewissern Sie sich, dass Benutzer den Dateinamen-Editor öffnen können, um die Domänen Eigenschaft zu bearbeiten.

    1. Drücken Sie STRG + F5 oder F5. Öffnen Sie in der Projekt Mappe Debuggen eine Testdatei. Erstellen Sie ein Element der Domänen Klasse, und wählen Sie es aus.

    2. Wählen Sie im Eigenschaftenfenster die Eigenschaft Domäne aus. Im Feld Wert wird ein Auslassungs Zeichen **[...]** angezeigt.

    3. Klicken Sie auf die Auslassungs Punkte. Ein Datei Dialogfeld wird angezeigt. Wählen Sie eine Datei aus, und schließen Sie das Dialogfeld. Der Dateipfad ist nun der Wert der Domänen Eigenschaft.

### <a name="define-your-own-property-editor"></a>Definieren eines eigenen Eigenschaften-Editors

Sie können einen eigenen Editor definieren. Dies würde dazu führen, dass der Benutzer entweder einen von Ihnen definierten Typ bearbeiten oder einen Standardtyp auf besondere Weise bearbeiten kann. Beispielsweise können Sie es dem Benutzer ermöglichen, eine Zeichenfolge einzugeben, die eine Formel darstellt.

Sie definieren einen Editor, indem Sie eine Klasse schreiben, die von abgeleitet ist <xref:System.Drawing.Design.UITypeEditor> . Die Klasse muss Folgendes überschreiben:

- <xref:System.Drawing.Design.UITypeEditor.EditValue%2A>, um mit dem Benutzer zu interagieren und den Eigenschafts Wert zu aktualisieren.

- <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A>, um anzugeben, ob der Editor ein Dialogfeld öffnet oder ein Dropdown Menü bereitstellt.

Sie können auch eine grafische Darstellung des Eigenschafts Werts bereitstellen, die im Eigenschaften Raster angezeigt wird. Überschreiben Sie hierzu `GetPaintValueSupported` und `PaintValue` .  Weitere Informationen finden Sie unter <xref:System.Drawing.Design.UITypeEditor>.

> [!NOTE]
> Fügen Sie den Code in einer separaten Codedatei im **DSL** -Projekt hinzu.

Beispiel:

```csharp
internal class TextFileNameEditor : System.Windows.Forms.Design.FileNameEditor
{
  protected override void InitializeDialog(System.Windows.Forms.OpenFileDialog openFileDialog)
  {
    base.InitializeDialog(openFileDialog);
    openFileDialog.Filter = "Text files(*.txt)|*.txt|All files (*.*)|*.*";
    openFileDialog.Title = "Select a text file";
  }
}
```

Wenn Sie diesen Editor verwenden möchten, legen Sie das **benutzerdefinierte Attribut** einer Domänen Eigenschaft auf fest:

```csharp
[System.ComponentModel.Editor (
   typeof(MyNamespace.TextFileNameEditor)
   , typeof(System.Drawing.Design.UITypeEditor))]
```

Weitere Informationen finden Sie unter <xref:System.Drawing.Design.UITypeEditor>.

## <a name="provide-a-drop-down-list-of-values"></a>Dropdown Liste mit Werten angeben

Sie können eine Liste von Werten bereitstellen, aus denen ein Benutzer auswählen kann.

> [!NOTE]
> Diese Technik stellt eine Liste von Werten bereit, die zur Laufzeit geändert werden können. Wenn Sie eine Liste angeben möchten, die sich nicht ändert, sollten Sie stattdessen einen enumerierten Typ als Typ der Domänen Eigenschaft verwenden.

Zum Definieren einer Liste von Standardwerten fügen Sie der Domänen Eigenschaft ein CLR-Attribut hinzu, das die folgende Form aufweist:

```csharp
[System.ComponentModel.TypeConverter
(typeof(MyTypeConverter))]
```

Definieren Sie eine Klasse, die sich von <xref:System.ComponentModel.TypeConverter> ableitet. Fügen Sie den Code in einer separaten Datei im **DSL** -Projekt hinzu. Beispiel:

```csharp
/// <summary>
/// Type converter that provides a list of values
/// to be displayed in the property grid.
/// </summary>
/// <remarks>This type converter returns a list
/// of the names of all "ExampleElements" in the
/// current store.</remarks>
public class MyTypeConverter : System.ComponentModel.TypeConverter
{
  /// <summary>
  /// Return true to indicate that we return a list of values to choose from
  /// </summary>
  /// <param name="context"></param>
  public override bool GetStandardValuesSupported
    (System.ComponentModel.ITypeDescriptorContext context)
  {
    return true;
  }

  /// <summary>
  /// Returns true to indicate that the user has
  /// to select a value from the list
  /// </summary>
  /// <param name="context"></param>
  /// <returns>If we returned false, the user would
  /// be able to either select a value from
  /// the list or type in a value that is not in the list.</returns>
  public override bool GetStandardValuesExclusive
      (System.ComponentModel.ITypeDescriptorContext context)
  {
    return true;
  }

  /// <summary>
  /// Return a list of the values to display in the grid
  /// </summary>
  /// <param name="context"></param>
  /// <returns>A list of values the user can choose from</returns>
  public override StandardValuesCollection GetStandardValues
      (System.ComponentModel.ITypeDescriptorContext context)
  {
    // Try to get a store from the current context
    // "context.Instance"  returns the element(s) that
    // are currently selected i.e. whose values are being
    // shown in the property grid.
    // Note that the user could have selected multiple objects,
    // in which case context.Instance will be an array.
    Store store = GetStore(context.Instance);

    List<string> values = new List<string>();

    if (store != null)
    {
      values.AddRange(store.ElementDirectory
        .FindElements<ExampleElement>()
        .Select<ExampleElement, string>(e =>
      {
        return e.Name;
      }));
    }
    return new StandardValuesCollection(values);
  }

  /// <summary>
  /// Attempts to get to a store from the currently selected object(s)
  /// in the property grid.
  /// </summary>
  private Store GetStore(object gridSelection)
  {
    // We assume that "instance" will either be a single model element, or
    // an array of model elements (if multiple items are selected).

    ModelElement currentElement = null;

    object[] objects = gridSelection as object[];
    if (objects != null && objects.Length > 0)
    {
      currentElement = objects[0] as ModelElement;
    }
    else
    {
        currentElement = gridSelection as ModelElement;
    }

    return (currentElement == null) ? null : currentElement.Store;
  }

}
```

## <a name="see-also"></a>Weitere Informationen

- [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md)
