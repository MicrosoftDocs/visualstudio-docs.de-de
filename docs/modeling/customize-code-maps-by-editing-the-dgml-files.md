---
title: Anpassen von Code Maps durch Bearbeiten der DGML-Dateien
description: Erfahren Sie, wie Sie eine Code Map anpassen, indem Sie die entsprechende dgml-Datei (Graph Markup Language) bearbeiten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- dependency graphs, creating path aliases
- dependency graphs, linking items to nodes
- graph documents, creating path aliases
- dependency graphs, grouping nodes
- graph documents, editing
- graph documents, linking items to nodes
- graph documents, customizing
- graph documentings, assigning categories and properties
- dependency graphs, editing
- dependency graphs, customizing
- graph documents, grouping nodes
- dependency graphs, assigning categories and properties
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 47613a2f74ce1c89a6b032e46fa18b978c1c5f0f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945291"
---
# <a name="customize-code-maps-by-editing-the-dgml-files"></a>Anpassen von Code Maps durch Bearbeiten der DGML-Dateien

Zum Anpassen einer Code Map können Sie die gesteuerte dgml-Datei (Graph Markup Language) bearbeiten. Sie können beispielsweise Elemente bearbeiten, um benutzerdefinierte Stile anzugeben, Codeelementen und Links Eigenschaften und Kategorien zuzuweisen oder Dokumente bzw. URLs mit Codeelementen oder Links zu verknüpfen. Weitere Informationen zu dgml-Elementen finden Sie in der [Referenz zur Referenz für geleitete Graph Markup Language (dgml)](../modeling/directed-graph-markup-language-dgml-reference.md).

Bearbeiten Sie die DGML-Datei der Code Map in einem Text- oder XML-Editor. Wenn die Karte Teil Ihrer Visual Studio-Projekt Mappe ist, wählen Sie Sie in **Projektmappen-Explorer** aus, öffnen Sie das Kontextmenü, und wählen Sie dann **Öffnen mit**, **XML (Text)-Editor** aus.

> [!NOTE]
> Zum Erstellen von Code Maps muss Visual Studio Enterprise Edition vorhanden sein. Wenn Sie eine Code Map in Visual Studio bearbeiten, werden alle nicht verwendeten DGML-Elemente und -Attribute beim Speichern der DGML-Datei gelöscht. Zudem werden automatisch Codeelemente erstellt, wenn Sie neue Links manuell hinzufügen. Wenn Sie die DGML-Datei speichern, werden möglicherweise alle Attribute, die Sie einem Element hinzugefügt haben, in alphabetischer Reihenfolge angeordnet.

## <a name="group-code-elements"></a><a name="OrganizeNodes"></a> Gruppieren von Code Elementen
 Sie können neue Gruppen hinzufügen oder vorhandene Knoten in eine Gruppe konvertieren.

1. Öffnen Sie die DGML-Datei in einem Text- oder XML-Editor.

2. Um ein Codeelement in eine Gruppe zu konvertieren, suchen Sie das `<Node/>`-Element für diese Codeelement.

    \- oder -

    Suchen Sie den `<Nodes>`-Abschnitt, um eine neue Gruppe hinzuzufügen. Fügen Sie ein neues `<Node/>`-Element hinzu.

3. Fügen Sie im `<Node/>`-Element ein `Group`-Attribut hinzu, um anzugeben, ob die Gruppe erweitert oder reduziert angezeigt werden soll. Beispiel:

   ```xml
   <Nodes>
      <Node Id="MyFirstGroup" Group="Expanded" />
      <Node Id="MySecondGroup" Group="Collapsed" />
   </Nodes>
   ```

4. Vergewissern Sie sich im `<Links>`-Abschnitt, dass für jede Beziehung zwischen einem Gruppencodeelement und den jeweiligen untergeordneten Codeelementen ein `<Link/>`-Element mit den folgenden Attributen vorhanden ist:

   - Ein `Source`-Attribut, das das Gruppencodeelement angibt

   - Ein `Target`-Attribut, das das untergeordnete Codeelement angibt

   - Ein `Category`-Attribut, das eine `Contains`-Beziehung zwischen dem Gruppencodeelement und seinem untergeordneten Codeelement angibt

     Beispiel:

   ```xml
   <Links>
      <Link Category="Contains" Source="MyFirstNewGroup" Target="FirstGroupChildOne" />
      <Link Category ="Contains" Source="MyFirstNewGroup" Target="FirstGroupChildTwo" />
      <Link Category ="Contains" Source="MySecondNewGroup" Target="SecondGroupChildOne" />
      <Link Category="Contains" Source="MySecondNewGroup" Target="SecondGroupChildTwo" />
   </Links>
   ```

    Weitere Informationen zum `Category` -Attribut finden Sie unter [Zuweisen von Kategorien zu Code Elementen und Links](#AssignCategories).

## <a name="change-the-style-of-the-map"></a><a name="ChangeGraphStyle"></a> Ändern des Stils der Karte
 Sie können die Hintergrundfarbe und die Rahmenfarbe der Map ändern, indem Sie die DGML-Datei der Map bearbeiten. Informationen zum Ändern des Stils von Code Elementen und Links finden Sie unter [Ändern des Stils von Code Elementen und Links](#Highlight).

1. Öffnen Sie die DGML-Datei in einem Text- oder XML-Editor.

2. Fügen Sie im `<DirectedGraph>`-Element beliebige der folgenden Attribute hinzu, um den Stil zu ändern:

     Hintergrundfarbe

    ```xml
    Background="ColorNameOrHexadecimalValue"
    ```

     Rahmenfarbe

    ```xml
    Stroke="StrokeValue"
    ```

     Beispiel:

    ```xml
    <DirectedGraph Background="Green" xmlns="http://schemas.microsoft.com/vs/2009/dgml" >
       ...
       ...
    </DirectedGraph>
    ```

## <a name="change-the-style-of-code-elements-and-links"></a><a name="Highlight"></a> Ändern des Stils von Code Elementen und Links

### <a name="CreateCustomStyles"></a>
 Benutzerdefinierte Stile können auf die folgenden Codeelemente angewendet werden:

- Einzelne Codeelemente und Links

- Gruppen von Codeelementen und Links

- Gruppen von Codeelementen und Links auf der Grundlage bestimmter Bedingungen

> [!TIP]
> Wenn Sie sich wiederholende Stile für viele Codeelemente oder Links verwenden, sollten Sie in Betracht ziehen, eine Kategorie auf die Codeelemente oder Links anzuwenden und dann einen Stil auf diese Kategorie anzuwenden. Weitere Informationen finden Sie unter [Zuweisen von Kategorien zu Code Elementen und Links](#AssignCategories) und [Zuweisen von Eigenschaften zu Code Elementen und Links](#AssignProperties).

##### <a name="to-apply-a-custom-style-to-a-single-code-element"></a>So wenden Sie einen benutzerdefinierten Stil auf einen einzelnes Codeelement an

1. Öffnen Sie die DGML-Datei in einem Text- oder XML-Editor.

2. Suchen Sie das `<Node/>`-Element des Codeelements. Fügen Sie beliebige der folgenden Attribute hinzu, um den Stil anzupassen:

     Hintergrundfarbe

    ```xml
    Background="ColorNameOrHexadecimalValue"
    ```

     Outline

    ```xml
    Stroke="ColorNameOrHexadecimalValue"
    ```

     Umrissstärke

    ```xml
    StrokeThickness="StrokeValue"
    ```

     Textfarbe

    ```xml
    Foreground="ColorNameOrHexadecimalValue"
    ```

     Symbol

    ```xml
    Icon="IconFilePathLocation"
    ```

     Textgröße

    ```xml
    FontSize="FontSizeValue"
    ```

     Texttyp

    ```xml
    FontFamily="FontFamilyName"
    ```

     Textbreite

    ```xml
    FontWeight="FontWeightValue"
    ```

     Textstil

    ```xml
    FontStyle="FontStyleName"
    ```

     Sie können als Textformat beispielsweise `Italic` angeben.

     Struktur

    ```xml
    Style="Glass"
    ```

     - ODER

    ```xml
    Style="Plain"
    ```

     Form

     Legen Sie für die `Shape`-Eigenschaft den Wert `None` und für die `Icon`-Eigenschaft den Pfad der Symboldatei fest, um die Form durch ein Symbol zu ersetzen.

    ```xml
    Shape="ShapeFilePathLocation"
    ```

     Beispiel:

    ```xml
    <Nodes>
       <Node Id="MyNode" Background="#FF008000" Stroke="#FF000000"
       Foreground="#FFFFFFFF" Icon="...\Icons\Globe.png"/>
    </Nodes>
    ```

##### <a name="to-apply-a-custom-style-to-a-single-link"></a>So wenden Sie einen benutzerdefinierten Stil auf einen einzelnen Link an

1. Öffnen Sie die DGML-Datei in einem Text- oder XML-Editor.

2. Suchen Sie das `<Link/>`-Element, das sowohl den Namen des Quellcodeelements als auch den Namen des Zielcodeelements enthält.

3. Fügen Sie im `<Link/>`-Element beliebige der folgenden Attribute hinzu, um den Stil anzupassen:

     Umriss- und Pfeilspitzenfarbe

    ```xml
    Stroke="ColorNameOrHexadecimalValue"
    ```

     Umrissstärke

    ```xml
    StrokeThickness="StrokeValue"
    ```

     Umrissstil

    ```xml
    StrokeDashArray="StrokeArrayValues"
    ```

     Beispiel:

    ```xml
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" Background="Green" Stroke="#FF000000" StrokeDashArray="2,2"/>
    </Links>
    ```

##### <a name="to-apply-custom-styles-to-a-group-of-code-elements-or-links"></a>So wenden Sie benutzerdefinierte Stile auf eine Gruppe von Codeelementen oder Links an

1. Öffnen Sie die DGML-Datei in einem Text- oder XML-Editor.

2. Sollte kein `<Styles></Styles>`-Element vorhanden sein, fügen Sie unter dem `<DirectedGraph></DirectedGraph>`-Element nach dem `<Links></Links>`-Element eines hinzu.

3. Geben Sie im `<Styles></Styles>`-Element unter dem `<Style/>`-Element die folgenden Attribute an:

   - `TargetType="Node` &#124; `Link | Graph"`

   - `GroupLabel="`*Nameilegendbox*`"`

   - `ValueLabel="`*Nameinstylepickerbox*`"`

     Verwenden Sie keine Bedingung, wenn Sie einen benutzerdefinierten Stil auf alle Zieltypen anwenden möchten.

##### <a name="to-apply-a-conditional-style-to-groups-of-code-elements-or-links"></a>So wenden Sie einen bedingten Stil auf Gruppen von Codeelementen oder Links an

1. Öffnen Sie die DGML-Datei in einem Text- oder XML-Editor.

2. Fügen Sie im `<Style/>`-Element ein `<Condition/>`-Element mit einem `Expression`-Attribut hinzu, um einen Ausdruck anzugeben, von dem ein boolescher Wert zurückgegeben wird.

    Beispiel:

   ```xml
   <Condition Expression="MyCategory"/>
   ```

    - ODER

   ```xml
   <Condition Expression="MyCategory > 100"/>
   ```

    - ODER

   ```xml
   <Condition Expression="HasCategory('MyCategory')"/>
   ```

    In diesem Ausdruck wird die folgende BNF-Syntax (Backus-Naur-Form) verwendet:

    \<Expression> :: = \<BinaryExpression> &#124; \<UnaryExpression> &#124; "(" \<Expression> ")" &#124; \<MemberBindings> &#124; \<Literal> &#124; \<Number>

    \<BinaryExpression>::= \<Expression> \<Operator>\<Expression>

    \<UnaryExpression> ::= "!" \<Expression> &#124; "+" \<Expression> &#124; "-" \<Expression>

    \<Operator> :: = "<" &#124; " \<=" &#124; "=" &#124; "> =" &#124; ">" &#124; "! =" &#124; "," &#124; "und" &#124; "+" &#124; "*" &#124; "/" &#124; "-"

    \<MemberBindings> :: = \<MemberBindings> &#124; \<MemberBinding> "." \<MemberBinding>

    \<MemberBinding> :: = \<MethodCall> &#124; \<PropertyGet>

    \<MethodCall> ::= \<Identifier> "(" \<MethodArgs> ")"

    \<PropertyGet> :: = Bezeichner

    \<MethodArgs> :: = \<Expression> &#124; \<Expression> "," \<MethodArgs> &#124; \<empty>

    \<Identifier> ::= [^. ]*

    \<Literal> :: = Single-oder Double-Anführungszeichen für Zeichen folgen Literale

    \<Number> :: = Zeichenfolge von Ziffern mit optionalem Dezimaltrennzeichen

    Sie können mehrere- `<Condition/>` Elemente angeben, die alle "true" sein müssen, um den Stil anzuwenden.

3. Fügen Sie in der nächsten Zeile nach dem `<Condition/>`-Element mindestens ein `<Setter/>`-Element hinzu, um ein `Property`-Attribut anzugeben, sowie ein festes `Value`-Attribut oder ein berechnetes `Expression`-Attribut, das auf die Map, auf die Codeelemente oder auf die Links angewendet werden soll, von der bzw. von denen die Bedingung erfüllt wird.

    Beispiel:

   ```xml
   <Setter Property="BackGround" Value="Green"/>
   ```

   Im folgenden einfachen und umfassenden Beispiel wird durch die Bedingung angegeben, dass ein Codeelement abhängig davon, ob die `Passed`-Kategorie auf `True` oder `False` festgelegt ist, grün bzw. rot dargestellt werden soll:

```xml
<?xml version="1.0" encoding="utf-8"?>
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">
   <Nodes>
      <Node Id="MyFirstNode" Passed="True" />
      <Node Id="MySecondNode" Passed="False" />
   </Nodes>
   <Links>
   </Links>
   <Styles>
      <Style TargetType="Node" GroupLabel="Passed" ValueLabel="True">
         <Condition Expression="Passed='True'"/>
         <Setter Property="Background" Value="Green"/>
      </Style>
      <Style TargetType="Node" GroupLabel="Passed" ValueLabel="False">
         <Condition Expression="Passed='False'"/>
         <Setter Property="Background" Value="Red"/>
      </Style>
   </Styles>
</DirectedGraph>
```

 Die folgende Tabelle enthält einige Beispielbedingungen, die Sie verwenden können:

 Festlegen des Schriftgrads als Funktion der Anzahl von Codezeilen, durch die auch die Größe des Codeelements geändert wird. In diesem Beispiel werden mehrere Eigenschaften (`FontSize` und `FontFamily`) mithilfe eines einzelnen bedingten Ausdrucks festgelegt.

```xml
<?xml version="1.0" encoding="utf-8"?>
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">
<Nodes>
   <Node Id="Class1" LinesOfCode ="200" />
   <Node Id="Class2" LinesOfCode ="1000" />
   <Node Id="Class3" LinesOfCode ="20" />
</Nodes>
<Properties>
   <Property Id="LinesOfCode" Label="LinesOfCode" Description="LinesOfCode" DataType="System.Int32" />
</Properties>
<Styles>
   <Style TargetType="Node" GroupLabel="LinesOfCode" ValueLabel="Function">
      <Condition Expression="LinesOfCode > 0" />
      <Setter Property="FontSize" Expression="Math.Max(9,Math.Sqrt(LinesOfCode))" />
      <Setter Property="FontFamily" Value="Papyrus" />
   </Style>
</Styles>
</DirectedGraph>
```

 Festlegen der Hintergrundfarbe eines Codeelements auf Basis der `Coverage`-Eigenschaft. Die Stile werden – ähnlich wie `if-else`-Anweisungen – in der Anzeigereihenfolge ausgewertet.

 In diesem Beispiel:

1. Wenn `Coverage` > 80 ist, legen Sie die- `Background` Eigenschaft auf grün fest.

2. Wenn `Coverage` > 50 ist, legen Sie die- `Background` Eigenschaft basierend auf dem Wert der-Eigenschaft auf einen Farbton Orange fest `Coverage` .

3. Legen Sie die `Background`-Eigenschaft abhängig vom Wert der `Coverage`-Eigenschaft auf Rot fest.

```xml
<?xml version="1.0" encoding="utf-8"?>
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">
<Nodes>
   <Node Id="Class1" Coverage="58" />
   <Node Id="Class2" Coverage="95" />
   <Node Id="Class3" Coverage="32" />
</Nodes>
<Properties>
   <Property Id="Coverage" Label="Coverage" Description="Code coverage as a percentage of blocks" DataType="Double" />
</Properties>
<Styles>
   <Style TargetType="Node" GroupLabel="Coverage" ValueLabel="Good">
      <Condition Expression="Coverage > 80" />
      <Setter Property="Background" Value="Green" />
   </Style>
   <Style TargetType="Node" GroupLabel="Coverage" ValueLabel="OK">
      <Condition Expression="Coverage > 50" />
      <Setter Property="Background" Expression="Color.FromRgb(180 * Math.Max(1, (80 - Coverage) / 30), 180, 0)" />
   </Style>
   <Style TargetType="Node" GroupLabel="Coverage" ValueLabel="Bad">
      <Setter Property="Background" Expression="Color.FromRgb(180, 180 * Coverage / 50, 0)" />
   </Style>
</Styles>
</DirectedGraph>
```

 Legen Sie die `Shape`-Eigenschaft auf `None` fest, sodass die Form durch das Symbol ersetzt wird. Geben Sie mithilfe der `Icon`-Eigenschaft den Ort des Symbols an.

```xml
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">
<Nodes>
   <Node Id="Automation" Category="Test" Label="Automation" />
   <Node Id="C# Provider" Category="Provider" Label="C# Provider" />
</Nodes>
<Categories>
   <Category Id="Provider" Icon="...\Icons\Module.png" Shape="None" />
   <Category Id="Test" Icon="...\Icons\Page.png" Shape="None" />
</Categories>
<Properties>
   <Property Id="Icon" DataType="System.String" />
   <Property Id="Label" Label="Label" Description="Displayable label of an Annotatable object" DataType="System.String" />
   <Property Id="Shape" DataType="System.String" />
</Properties>
<Styles>
   <Style TargetType="Node" GroupLabel="Group" ValueLabel="Has category">
      <Condition Expression="HasCategory('Group')" />
      <Setter Property="Background" Value="#80008080" />
   </Style>
   <Style TargetType="Node">
      <Setter Property="HorizontalAlignment" Value="Center" />
   </Style>
</Styles>
</DirectedGraph>
```

## <a name="assign-properties-to-code-elements-and-links"></a><a name="AssignProperties"></a> Zuweisen von Eigenschaften zu Code Elementen und Links
 Sie können Codeelemente und Links organisieren, indem Sie ihnen Eigenschaften zuweisen. So können Sie beispielsweise Codeelemente auswählen, die über bestimmte Eigenschaften verfügen, um diese Codeelemente zu gruppieren, ihren Stil zu ändern oder sie auszublenden.

#### <a name="to-assign-a-property-to-a-code-element"></a>So weisen Sie einem Codeelement eine Eigenschaft zu

1. Öffnen Sie die DGML-Datei in einem Text- oder XML-Editor.

2. Suchen Sie das `<Node/>`-Element für dieses Codeelement. Geben Sie den Namen der Eigenschaft und ihren Wert an. Beispiel:

    ```xml
    <Nodes>
       <Node Id="MyNode" MyPropertyName="PropertyValue" />
    </Nodes>
    ```

3. Fügen Sie dem `<Property/>`-Abschnitt ein `<Properties>`-Element hinzu, um Attribute wie den angezeigten Namen und den Datentyp anzugeben:

    ```xml
    <Properties>
       <Property Id="MyPropertyName" Label="My Property" DataType="System.DataType"/>
    </Properties>
    ```

#### <a name="to-assign-a-property-to-a-link"></a>So weisen Sie einem Link eine Eigenschaft zu

1. Öffnen Sie die DGML-Datei in einem Text- oder XML-Editor.

2. Suchen Sie das `<Link/>`-Element, das sowohl den Namen des Quellcodeelements als auch den Namen des Zielcodeelements enthält.

3. Geben Sie im `<Node/>`-Element den Namen der Eigenschaft und deren Wert an. Beispiel:

    ```xml
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" MyPropertyName="PropertyValue" />
    </Links>
    ```

4. Fügen Sie dem `<Property/>`-Abschnitt ein `<Properties>`-Element hinzu, um Attribute wie den angezeigten Namen und den Datentyp anzugeben:

    ```xml
    <Properties>
       <Property Id="MyPropertyName" Label="My Property Name" DataType="System.DataType"/>
    </Properties>
    ```

## <a name="assign-categories-to-code-elements-and-links"></a><a name="AssignCategories"></a> Zuweisen von Kategorien zu Code Elementen und Links
 In den folgenden Abschnitten wird gezeigt, wie Sie Codeelemente durch Zuweisen von Kategorien organisieren können und wie Sie hierarchische Kategorien erstellen können, die Ihnen helfen, Codeelemente zu organisieren und untergeordneten Kategorien mithilfe der Vererbung Attribute hinzuzufügen.

#### <a name="to-assign-a-category-to-a-code-element"></a>So weisen Sie einem Codeelement eine Kategorie zu

- Öffnen Sie die DGML-Datei in einem Text- oder XML-Editor.

- Suchen Sie das `<Node/>`-Element für das gewünschte Codeelement.

- Fügen Sie im `<Node/>`-Element ein `Category`-Attribut hinzu, um den Namen der Kategorie anzugeben. Beispiel:

    ```xml
    <Nodes>
       <Node Id="MyNode" Category="MyCategory" />
    </Nodes>
    ```

     Fügen Sie ein `<Category/>`-Element zum `<Categories>`-Abschnitt hinzu, um mithilfe des `Label`-Attributs den Anzeigetext für diese Kategorie angeben zu können:

    ```xml
    <Categories>
       <Category Id="MyCategory" Label="My Category" />
    </Categories>
    ```

#### <a name="to-assign-a-category-to-a-link"></a>So weisen Sie einem Link eine Kategorie zu

1. Öffnen Sie die DGML-Datei in einem Text- oder XML-Editor.

2. Suchen Sie das `<Link/>`-Element, das sowohl den Namen des Quellcodeelements als auch den Namen des Zielcodeelements enthält.

3. Fügen Sie im `<Link/>`-Element ein `Category`-Attribut hinzu, um den Namen der Kategorie anzugeben. Beispiel:

    ```xml
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" Category="MyCategory"
    </Links>
    ```

4. Fügen Sie ein `<Category/>`-Element zum `<Categories>`-Abschnitt hinzu, um mithilfe des `Label`-Attributs den Anzeigetext für diese Kategorie angeben zu können:

    ```xml
    <Categories>
       <Category Id="MyCategory" Label="My Category" />
    </Categories>
    ```

#### <a name="to-create-hierarchical-categories"></a>So erstellen Sie hierarchische Kategorien

1. Öffnen Sie die DGML-Datei in einem Text- oder XML-Editor.

2. Fügen Sie ein `<Category/>`-Element für die übergeordnete Kategorie hinzu, und fügen Sie anschließend dem `BasedOn`-Element der untergeordneten Kategorie das `<Category/>`-Attribut hinzu.

     Beispiel:

    ```xml
    <Nodes>
       <Node Id="MyFirstNode" Label="My First Node" Category= "MyCategory" />
       <Node Id="MySecondNode" Label="My Second Node" />
    </Nodes>
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" />
    </Links>
    <Categories>
       <Category Id="MyCategory" Label="My Category" BasedOn="MyParentCategory"/>
       <Category Id="MyParentCategory" Label="My Parent Category" Background="Green"/>
    </Categories>
    ```

     In diesem Beispiel ist der Hintergrund von `MyFirstNode` grün, da das `Category`-Attribut das `Background`-Attribut von `MyParentCategory` erbt.

## <a name="link-documents-or-urls-to-code-elements-and-links"></a><a name="AddReferences"></a> Verknüpfen von Dokumenten oder URLs mit Code Elementen und Links
 Sie können Dokumente oder URLs mit Codeelementen oder Links verknüpfen, indem Sie die DGML-Datei der Map bearbeiten und ein `Reference`-Attribut für ein Codeelement zum `<Node/>`-Element und für einen Link zum `<Link/>`-Element hinzufügen. Anschließend können Sie den Inhalt über das Codeelement bzw. den Link öffnen und anzeigen. Das `Reference`-Attribut gibt den Pfad dieses Inhalts an. Dabei kann es sich um einen relativ zum Ort der DGML-Datei angegebenen Pfad oder um einen absoluten Pfad handeln.

> [!CAUTION]
> Wenn Sie relative Pfade verwenden und die DGML-Datei an einen anderen Speicherort verschoben wird, können diese Pfade nicht mehr aufgelöst werden. Wenn Sie versuchen, den verknüpften Inhalt zu öffnen und anzuzeigen, gibt eine Fehlermeldung an, dass der Inhalt nicht angezeigt werden kann.

 Möglicherweise möchten Sie die folgenden Codeelemente verknüpfen:

- Möglicherweise verknüpfen Sie zur Beschreibung der Änderungen an einer Klasse die URL eines Arbeitscodeelements, eines Dokuments oder einer anderen DGML-Datei mit dem Codeelement einer Klasse.

- Sie können ein Abhängigkeits Diagramm mit einem Gruppen Code Element verknüpfen, das eine Ebene in der logischen Architektur der Software darstellt.

- Möglicherweise verknüpfen Sie ein Komponentendiagramm mit dem Codeelement für eine Schnittstelle, um weitere Informationen über eine Komponente anzuzeigen, die diese Schnittstelle verfügbar macht.

- Verknüpfen Sie ein Codeelement mit einer Team Foundation Server-Arbeitsaufgabe, einem Team Foundation Server-Fehler oder anderen Informationen, die sich auf das Codeelement beziehen.

#### <a name="to-link-a-document-or-url-to-a-code-element"></a>So verknüpfen Sie ein Dokument oder eine URL mit einem Codeelement

1. Öffnen Sie die DGML-Datei in einem Text- oder XML-Editor.

2. Suchen Sie das `<Node/>`-Element für das gewünschte Codeelement.

3. Führen Sie eine der Aufgaben aus der folgenden Tabelle aus:

    Ein einziges Codeelement

   - Fügen Sie im `<Node/>`- oder `<Link/>`-Element ein `Reference`-Attribut hinzu, um den Ort des Codeelements anzugeben.

     > [!NOTE]
     > Pro Element kann nur ein `Reference`-Attribut verwendet werden.

     Beispiel:

   ```xml
   <Nodes>
      <Node Id="MyNode" Reference="MyDocument.txt" />
   </Nodes>
   <Properties>
      <Property Id="Reference" Label="My Document" DataType="System.String" IsReference="True" />
   </Properties>
   ```

    Mehrere Codeelemente

   1. Fügen Sie im `<Node/>`- oder `<Link/>`-Element ein neues Attribut hinzu, um den Ort der einzelnen Verweise anzugeben.

   2. Gehen Sie im `<Properties>`-Abschnitt folgendermaßen vor:

      1. Fügen Sie für jeden neuen Verweistyp ein `<Property/>`-Element hinzu.

      2. Legen Sie das `Id`-Attribut auf den Namen des neuen Verweisattributs fest.

      3. Fügen `IsReference` Sie das-Attribut hinzu, und legen Sie es auf fest `True` , damit der Verweis im Kontextmenü **Gehe zu Verweis** des Code Elements angezeigt wird.

      4. Verwenden Sie das- `Label` Attribut, um den Anzeige Text im Kontextmenü **Gehe zu Verweis** des Code Elements anzugeben.

      Beispiel:

   ```xml
   <Nodes>
      <Node Id="MyNode" SequenceDiagram="MySequenceDiagram.sequencediagram" ActiveBugs="MyActiveBugs.wiq"/>
   </Nodes>
   <Properties>
      <Property Id="SequenceDiagram" Label="My Sequence Diagram" DataType="System.String" IsReference="True" />
      <Property Id="ActiveBugs" Label="Active Bugs" DataType="System.String" IsReference="True" />
   </Properties>
   ```

    Auf der Map wird der Name des Codeelements unterstrichen angezeigt. Wenn Sie das Kontextmenü für das Code Element oder den Link öffnen, wird das Kontextmenü **Gehe zu Verweis** angezeigt, das die verknüpften Code Elemente enthält, die Sie auswählen können.

4. Geben Sie mithilfe des `ReferenceTemplate`-Attributs eine allgemeine, von mehreren Verweisen verwendete Zeichenfolge (beispielsweise eine URL) an, anstatt die Zeichenfolge im Verweis zu wiederholen.

    Mit dem `ReferenceTemplate`-Attribut wird ein Platzhalter für den Wert des Verweises angegeben. Im folgenden Beispiel wird der `{0}`-Platzhalter im `ReferenceTemplate`-Attribut durch die Werte des `MyFirstReference`- und `MySecondReference`-Attributs im `<Node/>`-Element ersetzt, um einen vollständigen Pfad zu bilden:

   ```xml
   <Nodes>
      <Node Id="MyNode" MyFirstReference="MyFirstDocument" MySecondReference="MySecondDocument"/>
      <Node Id="MySecondNode" MyFirstReference="AnotherFirstDocument" MySecondReference="AnotherSecondDocument"/>
   </Nodes>
   <Properties>
      <Property Id="MyFirstReference" Label="My First Document" DataType="System.String" IsReference="True" ReferenceTemplate="http://www.Fabrikam.com/FirstDocuments/{0}.asp"/>
      <Property Id="MySecondReference" Label="My Second Document" DataType="System.String" IsReference="True" ReferenceTemplate=" http://www.Fabrikam.com/SecondDocuments/{0}.asp"/>
   </Properties>
   ```

5. Öffnen Sie das Kontextmenü für das Codeelement oder den Link, um das Codeelement, auf das verwiesen wird, bzw. die Codeelemente aus der Map anzuzeigen. Wählen Sie **Gehe zu Verweis** und dann das Code Element aus.

## <a name="see-also"></a>Siehe auch

- [Projektmappenübergreifendes Zuordnen von Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md)
- [Verwenden von Code Maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md)
- [Ermitteln potenzieller Probleme mithilfe von Code Map-Analyzern](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Durchsuchen und Neuanordnen von Code Maps](../modeling/browse-and-rearrange-code-maps.md)
- [Referenz zur Directed Graph Markup Language (DGML)](../modeling/directed-graph-markup-language-dgml-reference.md)
