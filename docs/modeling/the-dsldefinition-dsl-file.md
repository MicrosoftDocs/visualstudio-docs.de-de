---
title: Die Datei DslDefinition.dsl
description: Erfahren Sie mehr über die Struktur der Datei "DslDefinition. DSL" im DSL-Projekt einer DSL-Tool-Projekt Mappe, die eine domänenspezifische Sprache definiert.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5db379447f39ed3d0c2b82aee23c1ac94aad34d
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362781"
---
# <a name="the-dsldefinitiondsl-file"></a>Die Datei DslDefinition.dsl

In diesem Thema wird die Struktur der Datei "DslDefinition. DSL" im DSL-Projekt einer-Projekt Mappe beschrieben [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] , die eine *domänenspezifische Sprache* definiert. Die Datei "DslDefinition. DSL" beschreibt die Klassen und Beziehungen einer domänenspezifischen Sprache, zusammen mit dem Diagramm, den Formen, den Connectors, dem Serialisierungsformat und der **Toolbox** der domänenspezifischen Sprache und der zugehörigen Bearbeitungs Tools. In einer Projektmappe für eine domänenspezifischen Sprache wird der Code, der diese Tools definiert, entsprechend den Informationen in der Datei "DslDefinition.dsl" generiert.

Im Allgemeinen verwenden Sie den *domänenspezifischen sprach Designer* , um die Datei "DslDefinition. DSL" zu bearbeiten. Das Rohformat der Datei ist jedoch XML, und Sie können sie in einem XML-Editor öffnen. Für das Debuggen und für Erweitungen ist es sicherlich sinnvoll zu wissen, welche Informationen die Datei enthält und wie diese organisiert sind.

Die Beispiele in diesem Thema stammen aus der Projektmappenvorlage für Komponentendiagramme. Um ein Beispiel zu sehen, erstellen Sie eine domänenspezifische Sprachprojektmappe, die auf der Projektmappenvorlage für Komponentenmodelle beruht. Nachdem Sie die Projektmappe erstellt haben, wird die Datei "DslDefinition.dsl" im domänenspezifischen Sprachdesigner angezeigt. Schließen Sie die Datei, klicken Sie mit der rechten Maustaste auf **Projektmappen-Explorer**, zeigen Sie auf **Öffnen mit**, klicken Sie auf **XML-Editor**, und klicken Sie dann auf **OK**.

## <a name="sections-of-the-dsldefinitiondsl-file"></a>Abschnitte in der Datei "DslDefinition.dsl"

Das Stamm Element ist \<Dsl> , und seine Attribute geben den Namen der domänenspezifischen Sprache, den Namespace sowie die Haupt-und neben Versionsnummern für die Versionsverwaltung an. Das Schema `DslDefinitionModel` definiert Inhalt und Struktur einer gültigen DslDefinition.dsl-Datei.

Die untergeordneten Elemente des Stamm \<Dsl> Elements lauten wie folgt:

### <a name="classes"></a>Klassen

In diesem Abschnitt wird jede Domänenklasse definiert, die im generierten Code eine Klasse erzeugt.

### <a name="relationships"></a>Beziehungen

In diesem Abschnitt wird jede Beziehung im Modell definiert. Quelle und Ziel stellen die beiden Seiten einer Beziehung dar.

### <a name="types"></a>Typen

In diesem Abschnitt wird jeder Typ und dessen Namespace definiert. Domäneneigenschaften haben zwei Typen. `DomainEnumerations` werden im Modell definiert und generieren Typen in DomainModel.cs. `ExternalTypes` verweisen Sie auf Typen, die an anderer Stelle definiert werden (z. b. `String` oder `Int32` ), und generieren Sie nichts.

### <a name="shapes"></a>Formen

In diesem Abschnitt werden die Formen definiert, die beschreiben, wie das Modell in einem Designer dargestellt wird. Im Abschnitt "Diagramm" werden diese geometrischen Formen den Klassen im Modell zugeordnet.

### <a name="connectors"></a>Connectors

In diesem Abschnitt wird das Erscheinungsbild der Konnektoren definiert, die in einem Designer angezeigt werden. Im Abschnitt "Diagramm" werden diese Beschreibungen geometrischer Stile bestimmten Beziehungen im Modell zugeordnet.

### <a name="xmlserializationbehavior"></a>XmlSerializationBehavior

In diesem Abschnitt wird ein Serialisierungsschema definiert und zusätzliche Informationen darüber bereitgestellt, wie jede Klasse in einer Datei gespeichert wird.

### <a name="explorerbehavior"></a>ExplorerBehavior

In diesem Abschnitt wird definiert, wie das Fenster **DSL-Explorer** angezeigt wird, wenn der Benutzer ein Modell bearbeitet.

### <a name="connectionbuilders"></a>ConnectionBuilders

Dieser Abschnitt definiert einen Verbindungsgenerator für jedes Verbindungstool (das Tool zum Herstellen von Links zwischen zwei beliebigen Klassen, die verbunden werden können). Dieser Abschnitt bestimmt, ob Sie eine Quell- und eine Zielklasse verbinden können.

### <a name="diagram"></a>Diagramm

In diesem Abschnitt wird ein Diagramm definiert, und hier legen Sie Eigenschaften wie Hintergrundfarbe und Stammklasse fest. (Bei der Stamm Klasse handelt es sich um die Domänen Klasse, die durch das Diagramm als Ganzes dargestellt wird.) Der Diagramm Abschnitt enthält auch shapemap-und connectormap-Elemente, die die Form oder den Connector angeben, die die einzelnen Domänen Klassen oder-Beziehungen darstellen.

### <a name="designer"></a>Designer

In diesem Abschnitt wird ein Designer (-Editor) definiert, der eine **Toolbox**, Validierungs Einstellungen, ein Diagramm und ein Serialisierungsschema vereint. Im Abschnitt "Designer" wird auch die Stammklasse des Modells definiert, die in der Regel auch die Stammklasse des Diagramms ist.

### <a name="explorer"></a>Explorer

In diesem Abschnitt wird das Verhalten des **DSL-Explorers** (definiert im Abschnitt xmlserializationbehavior) identifiziert.

## <a name="monikers-in-the-dsldefinitiondsl-file"></a>Moniker in der Datei "DslDefinition.dsl"

In der gesamten Datei "DslDefinition.dsl" können Sie Moniker verwenden, um Querverweise auf bestimmte Elemente zu erstellen. Jede Beziehungsdefinition enthält z. B. einen Unterabschnitt für die Quelle und einen für das Ziel. Jeder Unterabschnitt enthält den Moniker der Klasse des Objekts, das mit dieser Beziehung verknüpft werden kann:

```xml
<DomainRelationship ...        Name="LibraryHasMembers" Namespace="ExampleNamespace" >    <Source>      <DomainRole ...>
       <RolePlayer>
         <DomainClassMoniker Name="Library" />
       </RolePlayer>
     </DomainRole>
   </Source>
```

In der Regel ist der Namespace des Elements, auf das verwiesen wird (in diesem Beispiel die Domänenklasse `Library`), derselbe wie der des verweisenden Elements (in diesem Fall die Domänenbeziehung "LibraryHasMembers"). In diesen Fällen darf der Moniker nur den Namen der Klasse angeben. Andernfalls müssen Sie die vollständige Form "/Namespace/Name" verwenden:

```xml
<DomainClassMoniker Name="/ExampleNameSpace/Library" />
```

Das Monikersystem verlangt unterschiedliche Namen für nebengeordnete Elemente in der XML-Struktur. Aus diesem Grund treten Validierungsfehler auf, wenn Sie versuchen, eine domänenspezifische Sprachdefinition zu speichern, die z. B. zwei Klassen mit demselben Namen enthält. Solche durch Doppelnamenfehler sollten Sie stets korrigieren, bevor Sie die Datei "DslDefinition.dsl" speichern, damit Sie sie später einwandfrei neu laden können.

Jeder Typ hat seinen eigenen Monikertyp: DomainClassMoniker, DomainRelationshipMoniker usw.

## <a name="types"></a>Typen

Im Abschnitt "Typen" werden alle Typen, welche die Datei "DslDefinition.dsl" enthält, als Typen von Eigenschaften angegeben. Von diesen Typen gibt es zwei Arten: externe Typen wie System.String und aufgelistete Typen.

### <a name="external-types"></a>Externe Typen

Im Komponentendiagramm-Beispiel wird eine Reihe von standardmäßigen primitiven Typen aufgelistet, obwohl nur einige davon verwendet werden.

Jede Definition eines externen Typs umfasst einfach einen Namen und einen Namespace, beispielsweise String und System:

```xml
<ExternalType Name="String" Namespace="System" />
```

Die vollständigen Namen der Typen werden verwendet anstelle der gleichbedeutenden Compiler-Schlüsselwörter wie "string".

Externe Typen sind nicht auf Standardbibliothekstypen beschränkt.

### <a name="enumerations"></a>Enumerationen

Eine typische Enumerationsspezifikation ähnelt dem folgenden Beispiel:

```xml
<DomainEnumeration IsFlags="true" Name="PageSort"          Namespace="Fabrikam.Wizard">
  <Literals>
    <EnumerationLiteral Name="Start" Value="1"/>
    <EnumerationLiteral Name="Decision" Value="2"/>
  </Literals>
</DomainEnumeration>
```

Das `IsFlags`-Attribut steuert, ob dem generierten Code das Common Language Runtime (CLR)-Attribut `[Flags]` vorangestellt wird, das bestimmt, ob Werte der Enumeration bitweise kombiniert werden können. Wenn dieses Attribut auf "true" festgelegt ist, müssen Sie für die Literalwerte Zweierpotenzwerte angeben.

## <a name="classes"></a>Klassen

Die meisten Elemente in einer Definition einer domänenspezifischen Sprache sind entweder direkt oder indirekt Instanzen von `DomainClass`. Zu den Unterklassen von `DomainClass` gehören `DomainRelationship`, `Shape`, `Connector` und `Diagram`. Im Abschnitt `Classes` der Datei "DslDefinition.dsl" werden die Domänenklassen aufgelistet.

Jede Klasse hat eine Reihe von Eigenschaften und kann eine Basisklasse besitzen. Im Komponentendiagramm-Beispiel ist `NamedElement` eine abstrakte Klasse, die eine `Name`-Eigenschaft vom Typ Zeichenfolge hat:

```xml
<DomainClass Id="ee3161ca-2818-42c8-b522-88f50fc72de8"  Name="NamedElement" Namespace="Fabrikam.CmptDsl5"      DisplayName="Named Element"  InheritanceModifier="Abstract">
  <Properties>
    <DomainProperty Id="ef553cf0-33b5-4e34-a30b-cfcfd86f2261"   Name="Name" DisplayName="Name"  DefaultValue="" Category="" IsElementName="true">
      <Type>
        <ExternalTypeMoniker Name="/System/String" />
      </Type>
    </DomainProperty>
  </Properties>
</DomainClass>
```

`NamedElement` ist die Basis mehrerer der anderen Klassen, z. b `Component` ., die neben der-Eigenschaft, von der `Name` Sie geerbt hat, über eigene Eigenschaften verfügt `NamedElement` . Der untergeordnete Knoten "BaseClass" enthält einen Monikerverweis. Da sich die referenzierte Klasse im gleichen Namespace befindet, muss im Moniker nur ihr Name angegeben werden:

```xml
<DomainClass Name="Component" Namespace="Fabrikam.CmptDsl5"              DisplayName="Component">
  <BaseClass>
    <DomainClassMoniker Name="NamedElement" />
  </BaseClass>
  <Properties>
    <DomainProperty Name="Kind" DisplayName="Kind" >
      <Type>
        <ExternalTypeMoniker Name="/System/String" />
      </Type>
    </DomainProperty>
  </Properties>
```

Jede Domänenklasse (einschließlich Beziehungen, Formen, Konnektoren und Diagrammen) kann die folgenden Attribute und untergeordneten Knoten enthalten:

- **ID.** Dieses Attribut ist eine GUID. Wenn Sie in der Datei keinen Wert angeben, erzeugt der domänenspezifische Sprachdesigner einen Wert. (In den Abbildungen in diesem Dokument wird dieses Attribut aus Platzgründen in der Regel weggelassen.)

- **Name und Namespace.**  Diese Attribute geben den Namen und den Namespace der Klasse im generierten Code an. Gemeinsam müssen sie innerhalb der domänenspezifischen Sprache eindeutig sein.

- **InheritanceModifier.** Dieses Attribut ist "abstrakt", "versiegelt" oder leer.

- **Display Name.** Dieses Attribut ist der Name, der im **Eigenschaften** Fenster angezeigt wird. Das DisplayName-Attribut kann Leerzeichen und Interpunktionszeichen enthalten.

- **GeneratesDoubleDerived.**  Wenn dieses Attribut auf "true" festgelegt ist, werden zwei Klassen generiert, von denen die eine eine Unterklasse der anderen ist. Alle generierten Methoden sind in der Basisklassen enthalten, während die Konstruktoren in der Unterklasse enthalten sind. Durch Festlegen dieses Attributs können Sie jede generierte Methode im benutzerdefinierten Code außer Kraft setzen.

- **Hascustomconstructor**. Wenn dieses Attribut auf "true" festgelegt ist, wird der Konstruktor aus dem generierten Code weggelassen, sodass Sie Ihre eigene Version schreiben können.

- **Attribute**. Dieses Attribut enthält die CLR-Attribute der generierten Klasse.

- **BaseClass**. Wenn Sie eine Basisklasse angeben, muss sie denselben Typ haben. Eine Domänenklasse muss z. B. eine andere Domänenklasse als Basis haben, während eine Depot-Form eine Depot-Form haben muss. Wenn Sie keine Basisklasse angeben, wird die Klasse im generierten Code aus einer Standard-Frameworkklasse abgeleitet. Eine Domänenklasse wird z. B. aus `ModelElement` abgeleitet.

- **Eigenschaften**. Dieses Attribut enthält die Eigenschaften, die unter Transaktionskontrolle verwaltet werden und erhalten bleiben, wenn das Modell gespeichert wird.

- **Elementmergedirektiven**. Jede Elementzusammenführungsdirektive steuert, wie eine andere Instanz einer anderen Klasse einer Instanz der übergeordneten Klasse hinzugefügt wird. Weitere Informationen über Elementzusammenführungsdirektiven finden Sie weiter unten in diesem Thema.

- Eine C#-Klasse wird für jede Domänenklasse generiert, die im Abschnitt `Classes` aufgeführt wird. Die C#-Klassen werden in der Datei "Dsl\GeneratedCode\DomainClasses.cs" generiert.

### <a name="properties"></a>Eigenschaften

Jede Domäneneigenschaft hat einen Namen und einen Typ. Der Name muss innerhalb der Domänenklasse und deren transitiver Basisklassen eindeutig sein.

Der Typ muss einer der im Abschnitt `Types` aufgeführten Typen sein. Der Moniker muss grundsätzlich den Namespace enthalten.

```xml
<DomainProperty Name="Name" DisplayName="Name"  DefaultValue="" Category="" IsElementName="true">
  <Type>
    <ExternalTypeMoniker Name="/System/String" />
  </Type>
</DomainProperty>
```

Jede Domäneneigenschaft kann auch die folgenden Attribute haben:

- **IsBrowsable**. Dieses Attribut bestimmt, ob die Eigenschaft im **Eigenschaften** Fenster angezeigt wird, wenn der Benutzer auf ein Objekt der übergeordneten Klasse klickt.

- **Isuiread only**. Dieses Attribut bestimmt, ob der Benutzer die Eigenschaft im **Eigenschaften** Fenster oder in einem Decorator, in dem die Eigenschaft dargestellt wird, ändern kann.

- **Art**. Sie können dieses Attribut auf "Normal", "Calculated" oder "CustomStorage" festlegen. Wenn Sie dieses Attribut auf "Calculated" festlegen, müssen Sie benutzerdefinierten Code bereitstellen, der den Wert bestimmt, und die Eigenschaft ist schreibgeschützt. Wenn Sie dieses Attribut auf "CustomStorage" festlegen, müssen Sie Code bereitstellen, mit dem Werte sowohl abgerufen als auch festgelegt werden.

- **IsElementName**. Wird dieses Attribut auf "true" festgelegt, wird sein Wert automatisch auf einen eindeutigen Wert eingestellt, wenn eine Instanz der übergeordneten Klasse erstellt wird. Dieses Attribut kann nur für eine Eigenschaft in jeder Klasse, die vom Typ Zeichenfolge sein muss, auf "true" festgelegt werden. Im Komponentendiagramm-Beispiel ist `Name` der `NamedElement`-Eigenschaft in `IsElementName` auf "true" festgelegt. Wenn ein Benutzer ein `Component`-Element (das von `NamedElement` erbt) erstellt, wird der Name automatisch auf einen Wert wie "Component6" initialisiert.

- `DefaultValue`. Wenn Sie dieses Attribut angegeben haben, wird der festgelegte Wert diesem Attribut für neue Instanzen dieser Klasse zugewiesen. Wenn `IsElementName` festgelegt wird, gibt das DefaultValue-Attribut den ersten Teil der neuen Zeichenfolge an.

- **Kategorie** ist die Kopfzeile, unter der die Eigenschaft im **Eigenschaften** Fenster angezeigt wird.

## <a name="relationships"></a>Beziehungen

Im Abschnitt `Relationships` werden alle Beziehungen in der domänenspezifischen Sprache aufgelistet. Jede `Domain Relationship` ist binär und gerichtet und verknüpft Member einer Quellklasse mit Membern einer Zielklasse. Bei den Quell- und Zielklassen handelt es sich in der Regel um Domänenklassen, Beziehungen zu anderen Beziehungen sind jedoch ebenfalls zulässig.

Die Connection-Beziehung z. B. verknüpft Member der OutPort-Klasse mit Membern der InPort-Klasse. Jede Verknüpfungsinstanz der Beziehung verbindet eine Instanz eines OutPort mit einer Instanz eines InPort. Da es sich um eine n:n-Beziehung handelt, kann jede OutPort-Klasse viele Connection-Verknüpfungen mit Quellen enthalten, und jede InPort-Instanz kann viele Connection-Verknüpfungen haben, die sie als Ziel haben.

### <a name="source-and-target-roles"></a>Quell- und Zielrollen

Jede Beziehung enthält Quell- und Zielrollen, die die folgenden Attribute haben:

- Das `RolePlayer`-Attribut verweist auf die Domänenklasse der verknüpften Instanzen: OutPort für die Quelle, InPort für das Ziel.

- Das `Multiplicity`-Attribut hat vier mögliche Werte (ZeroMany, ZeroOne, One und OneMany). Dieses Attribut verweist auf die Anzahl von Links dieser Beziehung, die mit einem Rolleninhaber verknüpft werden können.

- Das `PropertyName`-Attribut gibt den Namen an, der in der Rolleninhaberklasse verwendet wird, um auf die Objekte am anderen Ende zuzugreifen. Dieser Name wird im Vorlagen- oder benutzerdefinierten Code zum Durchlaufen der Beziehung verwendet. Das `PropertyName`-Attribut der Quellrolle wird z. B. auf `Targets` festgelegt. Daher funktioniert der folgende Code:

    ```
    OutPort op = ...; foreach (InPort ip in op.Targets) ...
    ```

     Üblicherweise haben Eigenschaftennamen eine Pluralform, wenn die Multiplizität ZeroMany oder OneMany lautet.

     Die Multiplizität einer Rolle bezieht sich darauf, wie viele Gegenrollen mit jeder Instanz dieser Rolle verknüpft werden können. In der Beziehung ComponentHasPorts ist das `RolePlayer`-Attribut der Zielrolle auf "Port", das `PropertyName`-Attribut auf "Component" und das `Multiplicity`-Attribut auf "ZeroOne" festgelegt. Der entsprechende Code zur Verwendung dieser Rolle lautet daher:

    ```
    ComponentPort p = ...; Component c = p.Component; if (c != null) ...
    ```

- Der `Name` der Rolle ist der Name, mit dem innerhalb der Beziehungsklasse auf das betreffende Ende eines Links verwiesen wird. Rollennamen stehen üblicherweise im Singular, da jeder Link an jedem Ende nur eine Instanz hat. Der folgende Code funktioniert:

    ```
    Connection connectionLink = ...; OutPort op = connectionLink.Source;
    ```

- Standardmäßig ist das `IsPropertyGenerator`-Attribut auf "true" festgelegt. Wenn es auf "false" festgelegt ist, wird in der Rolleninhaber-Klasse keine Eigenschaft erstellt. (In diesem Fall würde z. B. `op.Targets` nicht funktionieren.) Es ist jedoch weiterhin möglich, benutzerdefinierten Code zu verwenden, um die Beziehung zu durchlaufen oder um Zugriff auf die Links selbst zu erhalten, wenn der benutzerdefinierte Code die Beziehung explizit verwendet:

    ```
    OutPort op = ...; foreach (InPort ip in Connection.GetTargets(op)) ...
    foreach (Connection link in Connection.GetLinksToTargets(op)) ...
    ```

### <a name="relationship-attributes"></a>Beziehungsattribute

Neben den Attributen und untergeordneten Knoten, die allen Klassen zur Verfügung stehen, hat jede Beziehung die folgenden Attribute:

- **Isembedding**. Dieses Boolesche Attribut gibt an, ob die Beziehung Teil der einbettenden Struktur ist. Jedes Modell muss mit seinen einbettenden Beziehungen eine Struktur bilden. Jede Domänenklasse muss daher das Ziel mindestens einer einbettenden Beziehung sein, es sei denn, es handelt sich um den Stamm eines Modells.

- **AllowsDuplicates**. Dieses Boolesche Attribut, dessen Standardwert "false" lautet, gilt nur für Beziehungen mit einer n-Multiplizität sowohl bei Quelle als auch bei Ziel. Es bestimmt, ob Benutzer der Sprache ein einzelnes Paar von Quell- und Zielelementen über mehr als einen Link derselben Beziehung verbinden können.

## <a name="designer-and-toolbox-tabs"></a>Designer und Toolbox-Registerkarten

Der Hauptteil des **Designers** -Abschnitts der Datei "DslDefinition. DSL" sind die **ToolBoxTab** -Elemente. Ein Designer kann über mehrere dieser Elemente verfügen, von denen jeder einen Kopf Abschnitt in der **Toolbox** des generierten Designers darstellt. Jedes **ToolBoxTab** -Element kann ein oder mehrere Element **Tool** -Elemente, **connectiontool** -Elemente oder beides enthalten.

Elementtools können Instanzen einer bestimmten Domänenklasse erstellen. Wenn der Benutzer ein Elementtool auf das Diagramm zieht, wird das Ergebnis durch die Elementzusammenführungsdirektiven bestimmt, wie weiter unten in diesem Thema im entsprechenden Abschnitt erläutert wird.

Jedes Verbindungstool kann einen bestimmten Verbindungsgenerator aufrufen. Wie im Abschnitt über Verbindungsgeneratoren erläutert wird, kann ein Verbindungsgenerator mehr als einen Beziehungstyp erstellen, je nachdem, worauf der Benutzer mit der Maus klickt.

Mit keinem der beiden Tooltypen werden Formen oder Konnektoren direkt konstruiert. Jedes Tool instanziiert eine Domänenklasse oder eine Domänenbeziehung. Die Form- und Konnektorzuordnungen bestimmen dann, wie diese Domänenklasse oder Domänenbeziehung dargestellt wird.

## <a name="paths"></a>Paths

Domänenpfade treten in der Datei "DslDefinition.dsl" an verschiedenen Stellen auf. Diese Pfade geben eine Reihe von Links von einem Element in einem Modell (d. h. einer Instanz der domänenspezifischen Sprache) zu einem anderen an. Die Pfadsyntax ist einfach, aber ausführlich.

Pfade erscheinen in der Datei "DslDefinition.dsl" in `<DomainPath>...</DomainPath>`-Tags. Obwohl Pfade mehrere Links durchlaufen können, durchlaufen die meisten Beispiele in der Praxis nur einen Link.

Ein Pfad besteht aus einer Abfolge von Segmenten. Jedes Segment ist ein Sprung entweder von einem Objekt zu einem Link oder von einem Link zu einem Objekt. In einem langen Pfad wechseln die Sprünge daher in der Regel. Der erste Sprung erfolgt von einem Objekt zu einem Link, der zweite zum Objekt am anderen Ende des Links, der dritte Sprung zum nächsten Link usw. Ausnahmen von dieser Abfolge finden gelegentlich ausnahmsweise statt, wenn eine Beziehung selbst die Quelle oder das Ziel einer anderen Beziehung ist.

Jedes Segment beginnt mit einem Beziehungsnamen. In einem Objekt-Link-Sprung geht die Beziehung einem Punkt und dem Eigenschaftennamen voran: "`Relationship . Property`". In einem Link-Objekt-Sprung geht die Beziehung einem Ausrufezeichen und dem Rollennamen voran: "`Relationship ! Role`".

Das Komponentendiagramm-Beispiel enthält einen Pfad im ParentElementPath der ShapeMap für InPort. Dieser Pfad beginnt folgendermaßen:

```
    ComponentHasPorts.Component
```

In diesem Beispiel ist InPort eine Unterklasse von ComponentPort und hat eine Beziehung namens ComponentHasPorts. Die Eigenschaft wird "Component" genannt.

Wenn Sie C#-Code für dieses Modell schreiben, können Sie einen Link in einem Schritt überspringen. Verwenden Sie dazu die Eigenschaft, die die Beziehung in jeder der Klassen generiert, die sie verknüpft:

```
     InPort port; ...  Component c = port.Component;
```

Beide Sprünge müssen in der Pfadsyntax jedoch explizit ausgeführt werden. Aufgrund dieser Anforderung können Sie bequemer auf den Zwischenlink zugreifen. Mit dem folgenden Code wird der Sprung vom Link zur Komponente vervollständigt:

```
    ComponentHasPorts.Component / ! Component
```

(Sie können den Namen der Beziehung weglassen, wenn dieser mit dem Namen im vorherigen Segment übereinstimmt.)

## <a name="element-merge-directives"></a>Elementzusammenführungsdirektiven

Wenn der Benutzer der Sprache ein Element aus der **Toolbox** auf das Diagramm zieht, wird eine Instanz der Klasse des Tools erstellt. Außerdem werden Links zwischen dieser Instanz und den vorhandenen Modellelementen hergestellt. Einige Elemente, wie z. b. Komponenten oder Kommentare, werden erstellt, wenn der Benutzer der Sprache Sie aus der **Toolbox** auf einen leeren Bereich des Diagramms zieht. Andere Elemente werden erstellt, wenn der Benutzer der Sprache sie auf andere Hostelemente zieht. Beispielsweise wird ein OutPort oder InPort erstellt, wenn der Benutzer der Sprache ein solches Element auf eine Komponente zieht.

Eine potenzielle Hostklasse wie "Component" akzeptiert ein neues Element nur dann, wenn sie eine Elementzusammenführungsdirektive für die Klasse des neuen Elements enthält. Der Knoten "DomainClass" mit Name="Component" enthält z. B.:

```xml
<DomainClass Name="Component" ...> ...
    <ElementMergeDirective>
      <Index>
        <DomainClassMoniker Name="ComponentPort" />
      </Index>
      <LinkCreationPaths>
        <DomainPath>ComponentHasPorts.Ports</DomainPath>
      </LinkCreationPaths>
    </ElementMergeDirective> ...
```

Der Klassenmoniker, der sich unter dem Knoten "Index" befindet, referenziert die Klasse von Elementen, die akzeptiert werden können. In diesem Fall ist ComponentPort die abstrakte Basisklasse von InPort und OutPort. Daher kann jedes dieser Elemente akzeptiert werden.

ComponentModel, die Stammklasse der Sprache, enthält Elementzusammenführungsdirektiven für Komponenten und Kommentare. Der Benutzer der Sprache kann Elemente für diese Klassen direkt auf das Diagramm ziehen, da die leeren Abschnitte des Diagramms die Stammklasse darstellen. ComponentModel enthält jedoch keine Elementzusammenführungsdirektive für ComponentPort. Der Benutzer der Sprache kann InPorts oder OutPorts daher nicht direkt auf das Diagramm ziehen.

Die Elementzusammenführungsdirektive bestimmt, welcher Link oder welche Links erstellt werden, sodass das neue Element in das vorhandene Modell integriert oder mit diesem zusammengeführt werden kann. Für einen ComponentPort wird eine Instanz von ComponentHasPorts erstellt. Der DomainPath gibt sowohl die Beziehung als auch die Eigenschaft der übergeordneten Klasse "Ports" an, der das neue Element hinzugefügt wird.

Sie können in einer Elementzusammenführungsdirektive mehrere Links erstellen, indem Sie mehrere Link-Erstellungspfade angeben. Einer der Pfade muss eingebettet sein.

In einem Link-Erstellungspfad können Sie mehrere Segmente verwenden. In diesem Fall bestimmt das letzte Segment, welcher Link erstellt werden muss. Die früheren Segmente navigieren von der übergeordneten Klasse zu dem Objekt, von dem der neue Link erstellt werden soll.

Sie können der Klasse "Component" zum Beispiel die folgende Elementzusammenführungsdirektive hinzufügen:

```xml
<DomainClass Name="Component" ...> ...
  <ElementMergeDirective>
    <Index>
       <DomainClassMoniker Name="Comment"/>
    </Index>
    <LinkCreationPaths>
       <DomainPath>          ComponentModelHasComponents . ComponentModel / !ComponentModel         / ComponentModelHasComments.Comments       </DomainPath>
       <DomainPath>CommentsReferenceComponents.Comments</DomainPath>
    </LinkCreationPaths>
  </ElementMergeDirective>
```

Benutzer der Sprache können dann einen Kommentar auf eine Komponente ziehen und den neuen Kommentar automatisch mit einem Link zur Komponente erstellen lassen.

Der erste Link-Erstellungspfad navigiert von der `Component` zum `ComponentModel` und erstellt dann eine Instanz der einbettenden Beziehung `ComponentModelHasComments`. Der zweite Link-Erstellungspfad erstellt einen Link der Referenzbeziehung "CommentsReferenceComponents" von der Hostkomponente zum neuen Kommentar. Alle Link-Erstellungspfade müssen mit der Hostklasse beginnen und an einem Link enden, der zur neu instanziierten Klasse führt.

## <a name="xmlclassdata"></a>XmlClassData

Jede Domänenklasse (einschließlich Beziehungen und anderen Untertypen) kann zusätzliche Informationen enthalten, die in einem `XmlClassData`-Knoten bereitgestellt werden, der im Abschnitt `XmlSerializationBehavior` der Datei "DslDefinition.dsl" enthalten ist. Diese Informationen betreffen insbesondere die Art und Weise, wie Instanzen der Klasse in serialisierter Form gespeichert werden, wenn ein Modell in einer Datei gespeichert wird.

Ein großer Teil des generierten Codes, den `XmlSerializationBehavior` beeinflusst, befindet sich in `Dsl\GeneratedCode\Serializer.cs`.

Jeder `XmlClassData`-Knoten enthält die folgenden untergeordneten Knoten und Attribute:

- Einen Monikerknoten, der auf die Klasse verweist, auf welche die Daten angewendet werden.

- **Xmlpropertydata** für jede Eigenschaft, die für die Klasse definiert ist.

- **Xmlrelationshipdata** für jede Beziehung, die von der-Klasse stammt. (Beziehungen haben auch ihre eigenen XmlClassData-Knoten.)

- **Typname** Zeichen folgen Attribut, das den Namen der serialisierungshilfsklasse im generierten Code bestimmt.

- **ElementName** -Zeichenfolge, die das XML-Tag der serialisierten Instanzen dieser Klasse bestimmt. ElementName ist üblicherweise bis auf den ersten Buchstaben, der klein geschrieben ist, identisch mit dem Klassennamen. Eine Beispielmodelldatei beginnt z. B. folgendermaßen:

    ```xml
    <componentModel ...
    ```

- **Monikerelementname** in den serialisierten Modelldateien des Benutzers. Mit diesem Attribut wird ein Moniker eingeführt, der auf diese Klasse verweist.

- **Monikerattributename**: gibt den Namen des XML-Attributs in einem Moniker an. In diesem Fragment der serialisierten Datei eines Benutzers hat der Autor der domänenspezifischen Sprache **monikerelementname** als "inportmoniker" und **monikerattributename** als "Path" definiert:

    ```xml
    <inPortMoniker path="//Component2/InPort1" />
    ```

### <a name="connectionbuilders"></a>ConnectionBuilders

Ein Verbindungsgenerator wird für jedes Verbindungstool definiert. Jeder Verbindungsgenerator besteht aus mindestens einem LinkConnectDirective-Element, das mindestens ein SourceDirective-Element und mindestens ein TargetDirective-Element enthält. Nach dem Klicken auf ein Verbindungstool kann der Benutzer eine Verbindung von jeder Form aus starten, die einem Modellelement zugeordnet ist, das in der Liste von SourceDirective-Elementen aufgeführt wird. Die Verbindung kann dann auf einer Form abgeschlossen werden, die einem Element zugeordnet ist, das in der Liste von TargetDirective-Elementen aufgeführt wird. Die instanziierte Beziehungsklasse hängt von dem LinkConnectDirective-Element ab, das durch den Startpunkt der Verbindung ausgewiesen wird.

### <a name="xmlpropertydata"></a>XmlPropertyData

Ein **domainpropertymoniker** -Attribut identifiziert die Eigenschaft, auf die sich die Daten beziehen. Dieses Attribut muss eine Eigenschaft der einschließenden Klasse von ClassData sein.

Das **XMLName** -Attribut gibt den entsprechenden Attributnamen an, wie er in der XML-Datei angezeigt werden soll. Diese Zeichenfolge ist üblicherweise bis auf den ersten Buchstaben, der klein geschrieben ist, identisch mit dem Namen der Eigenschaft.

Standardmäßig ist das **Darstellungs** Attribut auf "Attribute" festgelegt. Wenn die **Darstellung** auf Element festgelegt ist, wird ein untergeordneter Knoten in der XML-Datei erstellt. Wenn die- **Darstellung** auf Ignore festgelegt ist, wird die-Eigenschaft nicht serialisiert.

Die Attribute **IsMonikerKey** und **ismonikerqualifier** legen einer Eigenschaft eine Rolle beim Identifizieren von Instanzen der übergeordneten Klasse. Sie können **IsMonikerKey** für eine Eigenschaft, die in einer Klasse definiert ist oder von einer Klasse geerbt wird, auf "true" festlegen. Dieses Attribut identifiziert eine einzelne Instanz der übergeordneten Klasse. Bei der Eigenschaft, die Sie auf `IsMonikerKey` festlegen, handelt es sich in der Regel um einen Namen oder eine andere Schlüsselkennung. Die Zeichenfolgeneigenschaft `Name` ist z. B. der Monikerschlüssel für NamedElement und dessen abgeleitete Klassen. Wenn der Benutzer ein Modell in einer Datei speichert, muss dieses Attribut eindeutige Werte für jede Instanz unter den nebengeordneten Elementen in der Struktur einbettender Beziehungen enthalten.

In der serialisierten Modelldatei ist der vollständige Moniker eines Elements ein Pfad, der vom Modellstamm ausgehend die Struktur einbettender Beziehungen hinunterläuft; dabei wird der Monikerschlüssel an jedem Punkt angegeben. InPorts sind beispielsweise in Components eingebettet, die wiederum im Modellstamm eingebettet sind. Ein gültiger Moniker lautet daher folgendermaßen:

```xml
<inPortMoniker name="//Component2/InPort1" />
```

Sie können das **ismonikerqualifier** -Attribut für eine Zeichen folgen Eigenschaft festlegen und eine zusätzliche Möglichkeit zum Erstellen des vollständigen Namens eines Elements bereitstellen. In der Datei "DslDefinition. DSL" ist " **Namespace** " z. b. ein monikerqualifizierer.

### <a name="xmlrelationshipdata"></a>XmlRelationshipData

Innerhalb einer serialisierten Modelldatei werden Links (sowohl für einbettende als auch für Referenzbeziehungen) durch untergeordnete Knoten des Quellendes der Beziehung dargestellt. Bei einbettenden Beziehungen enthält der untergeordnete Knoten eine Teilstruktur. Bei Referenzbeziehungen enthält der untergeordnete Knoten einen Moniker, der auf einen anderen Teil der Struktur verweist.

Das **xmlrelationshipdata** -Attribut in einem **xmlclassdata** -Attribut definiert genau, wie die untergeordneten Knoten innerhalb des Quell Elements geschachtelt sind. Jede Beziehung, die eine Quelle in der Domänen Klasse ist, verfügt über ein **xmlrelationshipdata** -Attribut.

Das **domainrelationshipmoniker** -Attribut identifiziert eine der Beziehungen, die von der-Klasse stammt.

Das **roleelementname** -Attribut gibt den XML-Tagnamen an, der den untergeordneten Knoten in den serialisierten Daten einschließt.

Die Datei "DslDefinition.dsl" enthält z. B. Folgendes:

```xml
<XmlClassData ElementName="component" ...>
  <DomainClassMoniker Name="Component" />
  <ElementData>
    <XmlRelationshipData RoleElementName="ports">
      <DomainRelationshipMoniker Name="ComponentHasPorts" />
    </XmlRelationshipData>
```

Die serialisierte Datei enthält daher:

```xml
<component name="Component1"> <!-- parent -->
   <ports> <!-- role -->
     <outPort name="OutPort1"> <!-- child element -->
       ...
     </outPort>
   </ports> ...
```

Wenn das **usefullform** -Attribut auf "true" festgelegt ist, wird eine zusätzliche Schachtelungs Ebene eingeführt. Diese Ebene stellt die Beziehung selbst dar. Das Attribut muss auf "true" festgelegt werden, wenn die Beziehung Eigenschaften hat.

```xml
<XmlClassData ElementName="outPort">
   <DomainClassMoniker Name="OutPort" />
   <ElementData>
     <XmlRelationshipData UseFullForm="true" RoleElementName="targets">
       <DomainRelationshipMoniker Name="Connection" />
     </XmlRelationshipData>
   </ElementData>
 </XmlClassData>
```

Die serialisierte Datei enthält:

```xml
<outPort name="OutPort1">  <!-- Parent -->
   <targets>  <!-- role -->
     <connection sourceRoleName="X">  <!-- relationship link -->
         <inPortMoniker name="//Component2/InPort1" /> <!-- child -->
     </connection>
    </targets>
  </outPort>
```

(Die Verbindungsbeziehung hat ihre eigenen XML-Klassendaten, die ihre Element- und Attributnamen bereitstellen.)

Wenn das **omitelement** -Attribut auf "true" festgelegt ist, wird der Beziehungs Rollenname weggelassen, der die serialisierte Datei abkürzt und eindeutig ist, wenn die beiden Klassen nicht mehr als eine Beziehung aufweisen. Zum Beispiel:

```xml
<component name="Component3">
  <!-- only one relationship could get here: -->
  <outPort name="OutPort1">
     <targets> ...
```

### <a name="serialization-of-a-domain-specific-language-definition"></a>Serialisierung einer domänenspezifischen Sprachdefinition

Die Datei "DslDefinition.dsl" selbst ist eine serialisierte Datei und entspricht einer domänenspezifischen Sprachdefinition. Es folgen einige Beispiele für XML-Serialisierungsdefinitionen:

- **DSL** ist der rootclass-Knoten und die-Klasse des Diagramms. DomainClass, DomainRelationship und andere Elemente sind unter `Dsl` eingebettet.

- **Classes** ist der **roleelementname** der Beziehung zwischen Domain-Specific Sprache und domainClass.

```xml
<Dsl Name="CmptDsl5" ...>
  <Classes>
    <DomainClass Name="NamedElement" InheritanceModifier="Abstract" ...
```

- Das **xmlserializationbehavior** -Attribut ist unter dem- `Dsl` Attribut eingebettet, aber das **omitelement** -Attribut wurde für den Embedding Relationship festgelegt. Daher tritt kein `RoleElementName`-Attribut dazwischen. Im Gegensatz dazu ist ein **classdata** -Attribut das `RoleElementName` Attribut des Embedding Relationship zwischen einem **xmlserializationbehavior** -Attribut und einem **xmlclassdata** -Attribut.

```xml
<Dsl Name="CmptDsl5" ...> ...
  <XmlSerializationBehavior Name="ComponentsSerializationBehavior" >
    <ClassData>
      <XmlClassData ...>...</XmlClassData>
      <XmlClassData ...>...</XmlClassData>
```

- ConnectorHasDecorators ist die einbettende Beziehung zwischen `Connector` und `Decorator`. `UseFullForm` wurde so festgelegt, dass der Name der Beziehung mit der Liste der Eigenschaften für die einzelnen Links des Connector-Objekts angezeigt wird. `OmitElement` wurde jedoch ebenfalls festgelegt, sodass kein `RoleElementName` die Links einschließt, die in `Connector` eingebettet sind:

```xml
<Connector Name="AssociationLink" ...>
  <ConnectorHasDecorators Position="TargetTop" ...>
    <TextDecorator Name="TargetRoleName"   />
  </ConnectorHasDecorators>
  <ConnectorHasDecorators Position="SourceTop" ...>
    <TextDecorator Name="SourceRoleName"   />
  </ConnectorHasDecorators>
</Connector>
```

## <a name="shapes-and-connectors"></a>Formen und Konnektoren

Definitionen von Formen und Konnektoren erben neben Folgendem auch Attribute und untergeordnete Knoten von Domänenklassen:

- `Color`-Attribute und `Line``Style`-Attribute

- **Exposesfillcolorasproperty** und mehrere ähnliche Attribute. Dank dieser Booleschen Attribute kann die entsprechende Eigenschaft vom Benutzer variiert werden. Wenn ein Benutzer einer Sprache auf eine Form im Diagramm klickt, werden im Allgemeinen die Eigenschaften, die im **Eigenschaften** Fenster angezeigt werden, die Eigenschaften der Domänen Klasseninstanz, der die Form zugeordnet ist, angezeigt. Wenn `ExposesFillColorAsProperty` auf "true" festgelegt ist, wird auch eine Eigenschaft der Form selbst angezeigt.

- **Shapehasdecorators**. Eine Instanz dieses Attribut tritt für jeden Text-, Symbol- oder Erweitern/Reduzieren-Decorator auf. (In der Datei "DslDefinition.dsl" ist `ShapeHasDecorators` eine Beziehung, wobei `UseFullForm` auf "true" festgelegt ist.)

## <a name="shape-maps"></a>Formzuordnungen

Formzuordnungen bestimmen, wie Instanzen einer bestimmten Domänenklasse durch eine Form auf dem Bildschirm dargestellt werden. Form- und Konnektorzuordnungen werden im Abschnitt `Diagram` der Datei "DslDefinition.dsl" aufgeführt.

Wie im folgenden Beispiel haben die `ShapeMap`-Elemente mindestens den Moniker einer Domänenklasse, den Moniker einer Form und ein `ParentElementPath`-Element:

```xml
<ShapeMap>
  <DomainClassMoniker Name="InPort" />
  <ParentElementPath>
    <DomainPath>ComponentHasPorts.Component/!Component</DomainPath>
  </ParentElementPath>
  <PortMoniker Name="InPortShape" />
</ShapeMap>
```

Die Hauptfunktion des `ParentElementPath`-Elements besteht darin, dass dieselbe Klasse von Objekten in unterschiedlichen Kontexten als unterschiedliche Form dargestellt werden kann. Wenn ein `InPort` beispielsweise auch in einen Kommentar eingebettet werden kann, kann der `InPort` für diesen Zweck auch als andere Form dargestellt werden.

Darüber hinaus bestimmt zweitens der Pfad, wie sich die Form auf ihr übergeordnetes Element bezieht. Zwischen den Formen in einer DslDefinition.dsl-Datei ist keine einbettende Struktur definiert. Sie müssen Sie Struktur aus den Formzuordnungen ableiten. Das übergeordnete Element einer Form ist die Form, die dem Domänenelement zugeordnet ist, das vom Pfad des übergeordneten Elements bezeichnet wird. In diesem Fall bezeichnet der Pfad die Komponente, zu der `InPort` gehört. In einer anderen Formzuordnung wird die Component-Klasse ComponentShape zugeordnet. Daher wird die neue `InPort`-Form zu einer untergeordneten Form von `ComponentShape` ihrer Komponente.

Wenn Sie die InPort-Form stattdessen an das Diagramm anfügen würden, müsste der Pfad des übergeordneten Elements einen weiteren Schritt zum Komponentenmodell umfassen, das dem Diagramm zugeordnet ist:

```
ComponentHasPorts . Component / ! Component /    ComponentModelHasComponents . ComponentModel / ! ComponentModel
```

Das Stammelement des Modells enthält keine Formzuordnung. Das Stammelement wird stattdessen direkt über das Diagramm referenziert, das ein `Class`-Element enthält:

```xml
<Diagram Name="ComponentDiagram" >
    <Class>
      <DomainClassMoniker Name="ComponentModel" />
    </Class>...
```

### <a name="decorator-maps"></a>Decorator-Zuordnungen

Eine Decorator-Zuordnung verknüpft eine Eigenschaft in der zugeordneten Klasse mit einem Decorator auf der Form. Wenn es sich bei der Eigenschaft um einen enumerierten oder Booleschen Typ handelt, hängt es von ihrem Wert ab, ob der Decorator sichtbar ist. Wenn es sich um einen Text-Decorator handelt, kann der Wert der Eigenschaft angezeigt werden, und der Benutzer kann ihn bearbeiten.

### <a name="compartment-shape-maps"></a>Depot-Formzuordnungen

Depot-Formzuordnungen sind Untertypen von Formzuordnungen.

## <a name="connector-maps"></a>Konnektorzuordnungen

Eine minimale Konnektorzuordnung verweist auf einen Konnektor und eine Beziehung:

```xml
<ConnectorMap>
  <ConnectorMoniker Name="CommentLink" />
  <DomainRelationshipMoniker Name="CommentsReferenceComponents" />
</ConnectorMap>
```

Konnektorzuordnungen können auch Decorator-Zuordnungen enthalten.

## <a name="see-also"></a>Siehe auch

- [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](/previous-versions/bb126564(v=vs.100))
- [So definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md)
- [Grundlagen von Modellen, Klassen und Beziehungen](../modeling/understanding-models-classes-and-relationships.md)