---
title: Schemareferenz für Codeausschnitte
description: Erfahren Sie mehr über das XML-Schema für IntelliSense-Codeausschnitte und darüber, wie Sie sie verwenden können, um Ihre Produktivität zu steigern.
ms.custom: SEO-VS-2020
ms.date: 03/31/2020
ms.topic: reference
helpviewer_keywords:
- schema reference [Visual Studio]
- snippets [Visual Studio], schema reference
- code snippets [Visual Studio], schema reference
- IntelliSense Code Snippets, XML Schema
ms.assetid: 58a60621-725f-4763-93b7-62ea5424ef88
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 22a5d4543548c8ac927487c9f4e2c9d95ea3487e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99842146"
---
# <a name="code-snippets-schema-reference"></a>Schemareferenz für Codeausschnitte

IntelliSense-Codeausschnitte sind vorab erstellte Codeelemente, die mithilfe von Visual Studio direkt in eine Anwendung eingefügt werden können. Solche Codeausschnitte erhöhen die Produktivität, da sie Zeit bei der Eingabe von wiederholtem Code oder bei der Suche nach Beispielen einsparen. Mithilfe des XML-Schemas für IntelliSense-Codeausschnitte können Sie eigene Codeausschnitte oder XML-Codeausschnitte erstellen und den bereits in Visual Studio enthaltenen Codeausschnitten hinzufügen.

## <a name="assembly-element"></a>Assembly-Element

Gibt den Namen der Assembly an, auf die vom Codeausschnitt verwiesen wird.

Der Textwert des **Assembly**-Elements entspricht entweder dem benutzerfreundlichen Textnamen der Assembly, beispielsweise `System.dll`, oder ihrem starken Namen, beispielsweise `System,Version=1.0.0.1,Culture=neutral,PublicKeyToken=9b35aa323c18d4fb1`.

```xml
<Assembly>
    AssemblyName
</Assembly>
```

|Übergeordnetes Element|Beschreibung|
| - |-----------------|
|[Reference-Element](../ide/code-snippets-schema-reference.md#reference-element)|Enthält Informationen über die für den Codeausschnitt erforderlichen Assemblyverweise.|

Ein Textwert ist erforderlich. Dieser Text gibt die Assembly an, auf die der Codeausschnitt verweist.

## <a name="author-element"></a>Author-Element

Gibt den Namen des Autors des Codeausschnitts an. Der **Codeausschnitt-Manager** zeigt den im `Author`-Element des Codeausschnitts gespeicherten Namen an.

```xml
<Author>
   Code Snippet Author
</Author>
```

|Übergeordnetes Element|Beschreibung|
| - |-----------------|
|[Header-Element](../ide/code-snippets-schema-reference.md#header-element)|Enthält allgemeine Informationen über den Codeausschnitt.|

Ein Textwert ist erforderlich. Dieser Text gibt den Autor des Codeausschnitts an.

## <a name="code-element"></a>Codeelement

Stellt einen Container für kurze Codeblöcke bereit.

### <a name="keywords"></a>Stichwörter

Zwei reservierte Wörter sind zur Verwendung im Text des `Code`-Elements verfügbar: `$end$` und `$selected$`. `$end$` markiert die Position, an die der Cursor zu setzen ist, nachdem der Codeausschnitt eingefügt wurde. `$selected$` stellt Text dar, der im Dokument ausgewählt wurde, das in den Ausschnitt eingefügt werden soll, wenn dieser aufgerufen wird. Betrachten wir beispielsweise einen Ausschnitt, der Folgendes enthält:

```
$selected$ is a great color.
```

Wenn das Wort "Blue" aktiviert ist, wenn der Benutzer die Vorlage aufruft, ist das Ergebnis:

```
Blue is a great color.
```

Sie können entweder `$end$` oder `$selected$` nicht mehr als einmal in einem Codeausschnitt verwenden. Andernfalls wird nur die zweite Instanz erkannt. Betrachten wir einen Ausschnitt, der Folgendes enthält:

```
$selected$ is a great color. I love $selected$.
```

Wenn das Wort "Blue" aktiviert ist, ist das Ergebnis:

```
 is a great color. I love Blue.
```

Der ursprüngliche Speicherplatz wird angezeigt, weil ein zwischen Leerzeichen `$selected$` und `is`vorhanden ist.

Alle anderen `$`-Schlüsselwörter werden dynamisch im `<Literal>`-Tag und im `<Object>`-Tag definiert.

Es folgt die Struktur des Codeelements:

```xml
<Code Language="Language"
    Kind="method body/method decl/type decl/page/file/any"
    Delimiter="Delimiter">
    Code to insert
</Code>
```

Ein Textwert ist erforderlich. Dieser Text gibt den Code, der verwendet werden kann, wenn dieser Codeausschnitt in eine Codedatei eingefügt wird, zusammen mit den Literalen und Objekten an.

### <a name="attributes"></a>Attribute

Für dieses Codeelement sind drei Attribute verfügbar:

- **Sprache** - _erforderlich:_ ein Attribut, das die Sprache des Codeausschnitts angibt. Der Wert kann in folgenden Formen vorliegen:

   |Wert|Beschreibung|
   |-----|-----------|
   |`VB`|Bezeichnet einen Visual Basic-Codeausschnitt.|
   |`CSharp`|Bezeichnet einen C#-Codeausschnitt.|
   |`CPP`|Bezeichnet einen C++-Codeausschnitt.|
   |`XAML`|Bezeichnet einen XAML-Codeausschnitt.|
   |`XML`|Bezeichnet einen XML-Codeausschnitt.|
   |`JavaScript`|Bezeichnet einen JavaScript-Codeausschnitt.|
   |`TypeScript`|Bezeichnet einen TypeScript-Codeausschnitt.|
   |`SQL`|Bezeichnet einen SQL-Codeausschnitt.|
   |`HTML`|Bezeichnet einen HTML-Codeausschnitt.|

- **Kind**: _optionales_ Attribut, das angibt, welche Art von Code der Codeausschnitt enthält. Der Wert kann in folgenden Formen vorliegen:

   |Wert|Beschreibung|
   |-----|-----------|
   |`method body`|Gibt an, dass der Codeausschnitt einen Methodenrumpf darstellt und daher innerhalb einer Methodendeklaration eingefügt werden muss.|
   |`method decl`|Gibt an, dass der Codeausschnitt eine Methode ist und daher innerhalb eine Klasse oder eines Moduls eingefügt werden muss.|
   |`type decl`|Gibt an, dass der Codeausschnitt ein Typ ist und daher innerhalb eine Klasse, eines Modul oder eines Namespace eingefügt werden muss.|
   |`file`|Gibt an, dass der Ausschnitt eine vollständige Codedatei ist. Diese Codeausschnitte können eigenständig in eine Codedatei oder einen Namespace eingefügt werden.|
   |`any`|Gibt an, dass der Ausschnitt überall eingefügt werden kann. Dieses Tag wird für kontextunabhängige Codeausschnitte verwendet, beispielsweise Kommentare.|

- **Trennzeichen** - _optional:_ Gibt das Trennzeichen an, mit dem Literale und Objekte im Code beschreiben werden. Standardmäßig ist `$` das Trennzeichen.

### <a name="parent-element"></a>Übergeordnetes Element

|Übergeordnetes Element|Beschreibung|
| - |-----------------|
|[Snippet-Element](../ide/code-snippets-schema-reference.md#snippet-element)|Enthält die Verweise, Importe, Deklarationen und den Code für den Codeausschnitt.|

## <a name="codesnippet-element"></a>CodeSnippet-Element

Ermöglicht die Angabe einer Überschrift und mehrerer IntelliSense-Codeausschnitte, die Sie in Visual Studio Codedateien einfügen können.

```xml
<CodeSnippet Format="x.x.x">
    <Header>... </Header>
    <Snippet>... </Snippet>
</CodeSnippet>
```

|Attribut|Beschreibung|
|---------------|-----------------|
|`Format`|Erforderliches Attribut. Gibt die Schemaversion des Codeausschnitts an. Das Formatattribut muss eine Zeichenfolge mit der Syntax "x.x.x" sein, wobei jedes "x" einen numerischen Wert der Versionsnummer darstellt. Visual Studio ignoriert Codeausschnitte mit `Format`-Attributen, die nicht verstanden werden.|

|Untergeordnetes Element|Beschreibung|
|-------------------|-----------------|
|[Header-Element](../ide/code-snippets-schema-reference.md#header-element)|Erforderliches Element. Enthält allgemeine Informationen über den Codeausschnitt. Es muss genau ein `Header`-Element in einem Codeausschnitt vorhanden sein.|
|[Snippet-Element](../ide/code-snippets-schema-reference.md#snippet-element)|Erforderliches Element. Enthält den Code, der von Visual Studio eingefügt wird. Es muss genau ein `Snippet`-Element in einem Codeausschnitt vorhanden sein.|

|Übergeordnetes Element|Beschreibung|
| - |-----------------|
|[CodeSnippets-Element](../ide/code-snippets-schema-reference.md#codesnippets-element)|Stammelement des XML-Schemas für den Codeausschnitt.|

## <a name="codesnippets-element"></a>CodeSnippets-Element

Gruppiert [CodeSnippet-Elemente](../ide/code-snippets-schema-reference.md#codesnippet-element). Das `CodeSnippets`-Element ist das Stammelement des XML-Schemas des Codeausschnitts.

```xml
<CodeSnippets>
    <CodeSnippet>... </CodeSnippet>
</CodeSnippets>
```

|Untergeordnetes Element|Beschreibung|
|-------------------|-----------------|
|[CodeSnippet-Element](../ide/code-snippets-schema-reference.md#codesnippet-element)|Optionales Element. Übergeordnetes Element für alle Codeausschnittdaten. Es kann keine oder mehrere `CodeSnippet`-Elemente in einem `CodeSnippets`-Element geben.|

## <a name="declarations-element"></a>Declarations-Element

Gibt die Literale und Objekte an, die die bearbeitbaren Teile eines Codeausschnitts darstellen.

```xml
<Declarations>
    <Literal>... </Literal>
    <Object>... </Object>
</Declarations>
```

|Untergeordnetes Element|Beschreibung|
|-------------------|-----------------|
|[Literal-Element](../ide/code-snippets-schema-reference.md#literal-element)|Optionales Element. Definiert die bearbeitbaren Literale des Codeausschnitts an. Es kann keine oder mehrere `Literal`-Elemente in einem `Declarations`-Element geben.|
|[Object-Element](../ide/code-snippets-schema-reference.md#object-element)|Optionales Element. Definiert die Objekte des Codeausschnitts an, die bearbeitet werden können. Es kann keine oder mehrere `Object`-Elemente in einem `Declarations`-Element geben.|

|Übergeordnetes Element|Beschreibung|
| - |-----------------|
|[Snippet-Element](../ide/code-snippets-schema-reference.md#snippet-element)|Enthält die Verweise, Importe, Deklarationen und den Code für den Codeausschnitt.|

## <a name="default-element"></a>Default-Element

Gibt den Standardwert des Literals oder Objekts für einen IntelliSense-Codeausschnitt an.

```xml
<Default>
    Default value
</Default>
```

|Übergeordnetes Element|Beschreibung|
| - |-----------------|
|[Literal-Element](../ide/code-snippets-schema-reference.md#literal-element)|Definiert die Literalfelder des Codeausschnitts, die Sie bearbeiten können.|
|[Object-Element](../ide/code-snippets-schema-reference.md#object-element)|Definiert die Objektfelder des Codeausschnitts, die Sie bearbeiten können.|

Ein Textwert ist erforderlich. Dieser Text gibt den Standardwert des Literals oder Objekts an, das die Felder des bearbeitbaren Codeausschnitts füllt.

## <a name="description-element"></a>Description-Element

Bezeichnet beschreibende Informationen über den Inhalt eines IntelliSense-Codeausschnitts.

```xml
<Description>
    Code Snippet Description
</Description>
```

|Übergeordnetes Element|Beschreibung|
| - |-----------------|
|[Header-Element](../ide/code-snippets-schema-reference.md#header-element)|Enthält allgemeine Informationen über den Codeausschnitt.|

Ein Textwert ist erforderlich. Dieser Text beschreibt den Codeausschnitt.

## <a name="function-element"></a>Function-Element

Gibt eine Funktion an, die ausgeführt wird, wenn das Literal oder Objekt in Visual Studio den Fokus erhält.

> [!NOTE]
> Nicht alle Sprachen unterstützen `function`-Elemente. Informationen zu den verfügbaren Funktionen finden Sie in den jeweiligen sprachspezifischen Dokumentationen.

```xml
<Function>
    FunctionName
</Function>
```

|Übergeordnetes Element|Beschreibung|
| - |-----------------|
|[Literal-Element](../ide/code-snippets-schema-reference.md#literal-element)|Definiert die Literalfelder des Codeausschnitts, die Sie bearbeiten können.|
|[Object-Element](../ide/code-snippets-schema-reference.md#object-element)|Definiert die Objektfelder des Codeausschnitts, die Sie bearbeiten können.|

Ein Textwert ist erforderlich. Dieser Text bezeichnet eine Funktion, die ausgeführt wird, wenn das Literal- oder Objektfeld in Visual Studio den Fokus erhält.

## <a name="header-element"></a>Header-Element

Gibt allgemeine Informationen über den IntelliSense-Codeausschnitt an.

```xml
<Header>
    <Title>... </Title>
    <Author>... </Author>
    <Description>... </Description>
    <HelpUrl>... </HelpUrl>
    <SnippetTypes>... </SnippetTypes>
    <Keywords>... </Keywords>
    <Shortcut>... </Shortcut>
</Header>
```

|Untergeordnetes Element|Beschreibung|
|-------------------|-----------------|
|[Author-Element](../ide/code-snippets-schema-reference.md#author-element)|Optionales Element. Der Name der Person oder der Firma, die den Codeausschnitt erstellt hat. Ein `Author`-Element kann kein oder ein `Header`-Element enthalten.|
|[Description-Element](../ide/code-snippets-schema-reference.md#description-element)|Optionales Element. Eine Beschreibung des Codeausschnitts. Ein `Description`-Element kann kein oder ein `Header`-Element enthalten.|
|[HelpUrl-Element](../ide/code-snippets-schema-reference.md#helpurl-element)|Optionales Element. Eine URL, die weitere Informationen über den Codeausschnitt enthält. Ein Header-Element kann kein oder ein `HelpURL`-Element enthalten. **Hinweis**:  Visual Studio verwendet das `HelpUrl`-Element nicht. Das Element ist Bestandteil des XML-Schemas für IntelliSense-Codeausschnitte. Alle Codeausschnitte mit dem Element werden überprüft, der Wert des Elements wird jedoch nie verwendet.|
|[Keywords-Element](../ide/code-snippets-schema-reference.md#keywords-element)|Optionales Element. Gruppiert `Keyword`-Elemente. Ein `Keywords`-Element kann kein oder ein `Header`-Element enthalten.|
|[Shortcut-Element](../ide/code-snippets-schema-reference.md#shortcut-element)|Optionales Element. Gibt den Verknüpfungstext an, der zum Einfügen des Ausschnitts verwendet werden kann. Ein `Shortcut`-Element kann kein oder ein `Header`-Element enthalten.|
|[SnippetTypes-Element](../ide/code-snippets-schema-reference.md#snippettypes-element)|Optionales Element. Gruppiert `SnippetType`-Elemente. Ein `SnippetTypes`-Element kann kein oder ein `Header`-Element enthalten. Wenn keine `SnippetTypes`-Elemente verfügbar sind, ist der Codeausschnitt immer gültig.|
|[Title-Element](../ide/code-snippets-schema-reference.md#title-element)|Erforderliches Element. Der benutzerfreundliche Name des Codeausschnitts. Es muss genau ein `Title`-Element in einem `Header`-Element vorhanden sein.|

|Übergeordnetes Element|Beschreibung|
| - |-----------------|
|[CodeSnippet-Element](../ide/code-snippets-schema-reference.md#codesnippet-element)|Übergeordnetes Element für alle Codeausschnittdaten.|

## <a name="helpurl-element"></a>HelpUrl-Element

Gibt eine URL zu weiteren Informationen über einen Codeausschnitt an.

> [!NOTE]
> Visual Studio verwendet das `HelpUrl`-Element nicht. Das Element ist Bestandteil des XML-Schemas für IntelliSense-Codeausschnitte. Alle Codeausschnitte mit dem Element werden überprüft, der Wert des Elements wird jedoch nie verwendet.

```xml
<HelpUrl>
    www.microsoft.com
</HelpUrl>
```

|Übergeordnetes Element|Beschreibung|
| - |-----------------|
|[Header-Element](../ide/code-snippets-schema-reference.md#header-element)|Enthält allgemeine Informationen über den Codeausschnitt.|

Ein Textwert ist optional. Dieser Text bezeichnet die aufzurufende URL, die weitere Informationen über einen Codeausschnitt enthält.

## <a name="id-element"></a>ID-Element

Gibt einen eindeutigen Bezeichner für ein `Literal`-Element oder ein `Object`-Element an. Zwei Literale oder Objekte im selben Codeausschnitt können nicht über den gleichen Textwert im `ID`-Element verfügen. Literale und Objekte können kein `ID`-Element mit dem Wert „end“ enthalten. Der Wert `$end$` ist reserviert. Mit diesem Wert wird die Stelle gekennzeichnet, an der der Cursor nach dem Einfügen des Codeausschnitts positioniert wird.

```xml
<ID>
    Unique Identifier
</ID>
```

|Übergeordnetes Element|Beschreibung|
| - |-----------------|
|[Literal-Element](../ide/code-snippets-schema-reference.md#literal-element)|Definiert die Literalfelder des Codeausschnitts, die Sie bearbeiten können.|
|[Object-Element](../ide/code-snippets-schema-reference.md#object-element)|Definiert die Objektfelder des Codeausschnitts, die Sie bearbeiten können.|

Ein Textwert ist erforderlich. Dieser Text bezeichnet den eindeutigen Bezeichner für das Objekt oder Literal.

## <a name="import-element"></a>Import-Element

Gibt die importierten Namespaces an, die von einem IntelliSense-Codeausschnitt verwendet werden.

```xml
<Import>
    <Namespace>... </Namespace>
</Import>
```

|Untergeordnetes Element|Beschreibung|
|-------------------|-----------------|
|[Namespace-Element](../ide/code-snippets-schema-reference.md#namespace-element)|Erforderliches Element. Gibt den vom Codeausschnitt verwendeten Namespace an. Es muss genau ein `Namespace`-Element in einem `Import`-Element vorhanden sein.|

|Übergeordnetes Element|Beschreibung|
| - |-----------------|
|[Imports-Element](../ide/code-snippets-schema-reference.md#imports-element)|Gruppierungselement für **Import**-Elemente.|

## <a name="imports-element"></a>Imports-Element

Gruppiert einzelne `Import`-Elemente.

```xml
<Imports>
    <Import>... </Import>
</Imports>
```

|Untergeordnetes Element|Beschreibung|
|-------------------|-----------------|
|[Import-Element](../ide/code-snippets-schema-reference.md#import-element)|Optionales Element. Enthält die importierten Namespaces für den Codeausschnitt. Ein `Imports`-Element kann keine oder mehrere **Import**-Elemente enthalten.|

|Übergeordnetes Element|Beschreibung|
| - |-----------------|
|[Snippet-Element](../ide/code-snippets-schema-reference.md#snippet-element)|Enthält die Verweise, Importe, Deklarationen und den Code für den Codeausschnitt.|

## <a name="keyword-element"></a>Keyword-Element

Gibt ein benutzerdefiniertes Schlüsselwort für den Codeausschnitt an. Die Schlüsselwörter des Codeausschnitts werden von Visual Studio verwendet und bieten Onlineinhaltsanbietern eine Standardmöglichkeit zum Hinzufügen von benutzerdefinierten Schlüsselwörtern für Suche und Kategorisierung.

```xml
<Keyword>
    Code Snippet Keyword
</Keyword>
```

|Übergeordnetes Element|Beschreibung|
| - |-----------------|
|[Keywords-Element](../ide/code-snippets-schema-reference.md#keywords-element)|Gruppiert einzelne `Keyword`-Elemente.|

Ein Textwert ist erforderlich. Das Schlüsselwort für den Codeausschnitt.

## <a name="keywords-element"></a>Keywords-Element

Gruppiert einzelne `Keyword`-Elemente. Die Schlüsselwörter des Codeausschnitts werden von Visual Studio verwendet und bieten Onlineinhaltsanbietern eine Standardmöglichkeit zum Hinzufügen von benutzerdefinierten Schlüsselwörtern für Suche und Kategorisierung.

```xml
<Keywords>
    <Keyword>... </Keyword>
    <Keyword>... </Keyword>
</Keywords>
```

|Untergeordnetes Element|Beschreibung|
|-------------------|-----------------|
|[Keyword-Element](../ide/code-snippets-schema-reference.md#keyword-element)|Optionales Element. Enthält einzelne Schlüsselwörter für den Codeausschnitt. Es kann keine oder mehrere `Keyword`-Elemente in einem `Keywords`-Element geben.|

|Übergeordnetes Element|Beschreibung|
| - |-----------------|
|[Header-Element](../ide/code-snippets-schema-reference.md#header-element)|Enthält allgemeine Informationen über den Codeausschnitt.|

## <a name="literal-element"></a>Literalelement

Definiert die bearbeitbaren Literale des Codeausschnitts an. Das `Literal`-Element wird verwendet, um eine Ersetzung für ein Codeelement zu kennzeichnen, das zwar vollständig im Ausschnitt enthalten ist, nach dem Einfügen in den Code jedoch wahrscheinlich geändert wird. So sollten beispielsweise Literalzeichenfolgen, numerische Werte und einige Variablennamen als Literale deklariert werden.

Literale und Objekte können kein **ID**-Element mit dem Wert „selected“ oder „end“ enthalten. Der Wert `$selected$` stellt den im Dokument ausgewählten Text dar, der beim Aufruf in den Ausschnitt eingefügt werden soll. `$end$` markiert die Position, an die der Cursor zu setzen ist, nachdem der Codeausschnitt eingefügt wurde.

```xml
<Literal Editable="true/false">
   <ID>... </ID>
   <ToolTip>... </ToolTip>
   <Default>... </Default>
   <Function>... </Function>
</Literal>
```

|Attribut|Beschreibung|
|---------------|-----------------|
|`Editable`|Optionales `Boolean`-Attribut. Gibt an, ob das Literal bearbeitet werden kann, nachdem der Codeausschnitt eingefügt wurde. Der Standardwert dieses Attributs ist `true`.|

|Untergeordnetes Element|Beschreibung|
|-------------------|-----------------|
|[Default-Element](../ide/code-snippets-schema-reference.md#default-element)|Erforderliches Element. Gibt den Standardwert des Literals an, wenn Sie den Codeausschnitt einfügen. Es muss genau ein `Default`-Element in einem `Literal`-Element vorhanden sein.|
|[Function-Element](../ide/code-snippets-schema-reference.md#function-element)|Optionales Element. Gibt eine Funktion an, die ausgeführt werden soll, wenn das Literal in Visual Studio den Fokus erhält. Ein `Function`-Element kann kein oder ein `Literal`-Element enthalten.|
|[ID-Element](../ide/code-snippets-schema-reference.md#id-element)|Erforderliches Element. Gibt einen eindeutigen Bezeichner für das Literal an. Es muss genau ein `ID`-Element in einem `Literal`-Element vorhanden sein.|
|[ToolTip-Element](../ide/code-snippets-schema-reference.md#tooltip-element)|Optionales Element. Beschreibt den erwarteten Wert sowie die Verwendungsweise des Literals. Es kann kein oder ein **Tooltip**-Element in einem `Literal` enthalten sein.|

|Übergeordnetes Element|Beschreibung|
| - |-----------------|
|[Declarations-Element](../ide/code-snippets-schema-reference.md#declarations-element)|Enthält die Literale und Objekte eines Codeausschnitts, die Sie bearbeiten können.|

## <a name="namespace-element"></a>Namespace-Element

Gibt den Namespace an, der für die Kompilierung und Ausführung des Codeausschnitts importiert werden muss. Der im `Namespace`-Element angegebene Namespace wird automatisch einer `using`- oder `Imports`-Anweisung am Anfang des Codes hinzugefügt, sofern er nicht bereits vorhanden ist.

```xml
<Namespace>
    Namespace
</Namespace>
```

|Übergeordnetes Element|Beschreibung|
| - |-----------------|
|[Import-Element](../ide/code-snippets-schema-reference.md#import-element)|Importiert den angegebenen Namespace.|

Ein Textwert ist erforderlich. Dieser Text gibt einen importierten Namespace an, der Voraussetzung für den Codeausschnitt ist.

## <a name="object-element"></a>Object-Element

Definiert die Objekte des Codeausschnitts an, die bearbeitet werden können. Das `Object`-Element wird zur Kennzeichnung eines vom Codeausschnitt benötigten Elements verwendet, das möglicherweise jedoch außerhalb des Codeausschnitts selbst definiert wird. Beispielsweise sollten Windows Forms-Steuerelemente, ASP.NET-Steuerelemente, Objektinstanzen und Typinstanzen als Objekte deklariert werden. Für Objektdeklarationen muss ein Typ angegeben werden. Zu diesem Zweck wird das `Type`-Element verwendet.

```xml
<Object Editable="true/false">
    <ID>... </ID>
    <Type>... </Type>
    <ToolTip>... </ToolTip>
    <Default>... </Default>
    <Function>... </Function>
</Object>
```

|Attribut|Beschreibung|
|---------------|-----------------|
|`Editable`|Optionales `Boolean`-Attribut. Gibt an, ob das Literal bearbeitet werden kann, nachdem der Codeausschnitt eingefügt wurde. Der Standardwert dieses Attributs ist `true`.|

|Untergeordnetes Element|Beschreibung|
|-------------------|-----------------|
|[Default-Element](../ide/code-snippets-schema-reference.md#default-element)|Erforderliches Element. Gibt den Standardwert des Literals an, wenn Sie den Codeausschnitt einfügen. Es muss genau ein `Default`-Element in einem `Literal`-Element vorhanden sein.|
|[Function-Element](../ide/code-snippets-schema-reference.md#function-element)|Optionales Element. Gibt eine Funktion an, die ausgeführt werden soll, wenn das Literal in Visual Studio den Fokus erhält. Ein `Function`-Element kann kein oder ein `Literal`-Element enthalten.|
|[ID-Element](../ide/code-snippets-schema-reference.md#id-element)|Erforderliches Element. Gibt einen eindeutigen Bezeichner für das Literal an. Es muss genau ein `ID`-Element in einem `Literal`-Element vorhanden sein.|
|[ToolTip-Element](../ide/code-snippets-schema-reference.md#tooltip-element)|Optionales Element. Beschreibt den erwarteten Wert sowie die Verwendungsweise des Literals. Es kann kein oder ein **Tooltip**-Element in einem `Literal` enthalten sein.|
|[Type-Element](../ide/code-snippets-schema-reference.md#type-element)|Erforderliches Element. Gibt den Typ des Objekts an. Es muss genau ein `Type`-Element in einem `Object`-Element vorhanden sein.|

|Übergeordnetes Element|Beschreibung|
| - |-----------------|
|[Declarations-Element](../ide/code-snippets-schema-reference.md#declarations-element)|Enthält die Literale und Objekte eines Codeausschnitts, die Sie bearbeiten können.|

## <a name="reference-element"></a>Reference-Element

Bezeichnet Informationen über die für den Codeausschnitt erforderlichen Assemblyverweise.

```xml
<Reference>
    <Assembly>... </Assembly>
    <Url>... </Url>
</Reference>
```

|Untergeordnetes Element|Beschreibung|
|-------------------|-----------------|
|[Assembly-Element](../ide/code-snippets-schema-reference.md#assembly-element)|Erforderliches Element. Enthält den Namen der Assembly, auf die vom Codeausschnitt verwiesen wird. Es muss genau ein `Assembly`-Element in einem `Reference`-Element vorhanden sein.|
|[URL-Element](../ide/code-snippets-schema-reference.md#url-element)|Optionales Element. Enthält eine URL, die weitere Informationen über die Assembly bereitstellt, auf die verwiesen wird. Ein `Url`-Element kann kein oder ein `Reference`-Element enthalten.|

|Übergeordnetes Element|Beschreibung|
| - |-----------------|
|[References-Element](../ide/code-snippets-schema-reference.md#references-element)|Gruppierungselement für `Reference`-Elemente.|

## <a name="references-element"></a>References-Element

Gruppiert einzelne `Reference`-Elemente.

```xml
<References>
    <Reference>... </Reference>
</References>
```

|Untergeordnetes Element|Beschreibung|
|-------------------|-----------------|
|[Reference-Element](../ide/code-snippets-schema-reference.md#reference-element)|Optionales Element. Enthält Informationen zu Assemblyverweisen für den Codeausschnitt. Es kann keine oder mehrere `Reference`-Elemente in einem `References`-Element geben.|

|Übergeordnetes Element|Beschreibung|
| - |-----------------|
|[Snippet-Element](../ide/code-snippets-schema-reference.md#snippet-element)|Enthält die Verweise, Importe, Deklarationen und den Code für den Codeausschnitt.|

## <a name="shortcut-element"></a>Shortcut-Element

Gibt den Verknüpfungstext an, der zum Einfügen des Codeausschnitts verwendet wird. Der Textwert eines `Shortcut`-Elements kann nur alphanumerische Zeichen und Unterstriche ( _ ) enthalten.

> [!CAUTION]
> Der Unterstrich (_) ist kein unterstütztes Zeichen in C++-Ausschnittsverknüpfungen.

```xml
<Shortcut>
    Shortcut Text
</Shortcut>
```

|Übergeordnetes Element|Beschreibung|
| - |-----------------|
|[Header-Element](../ide/code-snippets-schema-reference.md#header-element)|Enthält allgemeine Informationen über den Codeausschnitt.|

Ein Textwert ist optional. Dieser Text wird als Verknüpfung zum Einfügen des Codeausschnitts verwendet.

## <a name="snippet-element"></a>Snippet-Element

Gibt die Verweise, Importe, Deklarationen und den Code für den Codeausschnitt an.

```xml
<Snippet>
    <References>... </References>
    <Imports>... </Imports>
    <Declarations>... </Declarations>
    <Code>... </Code>
</Snippet>
```

|Untergeordnetes Element|Beschreibung|
|-------------------|-----------------|
|[Code-Element](../ide/code-snippets-schema-reference.md#code-element)|Erforderliches Element. Gibt den Code an, den Sie in eine Dokumentationsdatei einfügen möchten. Es muss genau ein `Code`-Element in einem `Snippet`-Element vorhanden sein.|
|[Declarations-Element](../ide/code-snippets-schema-reference.md#declarations-element)|Optionales Element. Gibt die Literale und Objekte an, die die bearbeitbaren Teile eines Codeausschnitts darstellen. Ein `Declarations`-Element kann kein oder ein `Snippet`-Element enthalten.|
|[Imports-Element](../ide/code-snippets-schema-reference.md#imports-element)|Optionales Element. Gruppiert einzelne `Import`-Elemente. Ein `Imports`-Element kann kein oder ein `Snippet`-Element enthalten.|
|[References-Element](../ide/code-snippets-schema-reference.md#references-element)|Optionales Element. Gruppiert einzelne `Reference`-Elemente. Ein `References`-Element kann kein oder ein `Snippet`-Element enthalten.|

|Übergeordnetes Element|Beschreibung|
| - |-----------------|
|[CodeSnippet-Element](../ide/code-snippets-schema-reference.md#codesnippet-element)|Ermöglicht die Angabe einer Überschrift und mehrerer IntelliSense-Codeausschnitte, die Sie in Visual Studio Codedateien einfügen können.|

## <a name="snippettype-element"></a>SnippetType-Element

Gibt an, wie Visual Studio den Codeausschnitt einfügt.

```xml
<SnippetType>
    SurroundsWith/Expansion
</SnippetType>
```

|Übergeordnetes Element|Beschreibung|
| - |-----------------|
|[SnippetTypes-Element](../ide/code-snippets-schema-reference.md#snippettypes-element)|Gruppiert `SnippetType`-Elemente.|

Der Textwert muss einer der folgenden Werte sein:

- `SurroundsWith`: Der Codeausschnitt kann ein ausgewähltes Codeelement umschließen.

- `Expansion`: Der Codeausschnitt kann an der Cursorposition eingefügt werden.

- `Refactoring`: Der Codeausschnitt wird während des C#-Refactorings verwendet. `Refactoring` kann in benutzerdefinierten Codeausschnitten nicht verwendet werden.

## <a name="snippettypes-element"></a>SnippetTypes-Element

Gruppiert einzelne `SnippetType`-Elemente. Wenn das `SnippetTypes`-Element nicht vorhanden ist, kann der Codeausschnitt an beliebiger Stelle im Code eingefügt werden.

```xml
<SnippetTypes>
    <SnippetType>... </SnippetType>
    <SnippetType>... </SnippetType>
</SnippetTypes>
```

|Untergeordnetes Element|Beschreibung|
|-------------------|-----------------|
|[SnippetType-Element](../ide/code-snippets-schema-reference.md#snippettype-element)|Optionales Element. Gibt an, wie Visual Studio den Codeausschnitt im Code einfügt. Es kann keine oder mehrere `SnippetType`-Elemente in einem `SnippetTypes`-Element geben.|

|Übergeordnetes Element|Beschreibung|
| - |-----------------|
|[Header-Element](../ide/code-snippets-schema-reference.md#header-element)|Bezeichnet allgemeine Informationen über den Codeausschnitt.|

## <a name="title-element"></a>Title-Element

Gibt den Titel für den Codeausschnitt an. Der im `Title`-Element des Codeausschnitts gespeicherte Titel wird im **Code Snippet Picker** sowie in der Beschreibung des Codeausschnitts im **Codeausschnitt-Manager** angezeigt.

```xml
<Title>
    Code Snippet Title
</Title>
```

|Übergeordnetes Element|Beschreibung|
| - |-----------------|
|[Header-Element](../ide/code-snippets-schema-reference.md#header-element)|Bezeichnet allgemeine Informationen über den Codeausschnitt.|

Ein Textwert ist erforderlich. Dieser Text gibt den Titel des Codeausschnitts an.

## <a name="tooltip-element"></a>ToolTip-Element

Beschreibt den erwarteten Wert und die erwartete Verwendung eines Literals oder Objekts in einem Codeausschnitt, das Visual Studio beim Einfügen des Codeausschnitts in ein Projekt in einer QuickInfo anzeigt. Der QuickInfo-Text (ToolTip) wird angezeigt, wenn mit der Maus nach dem Einfügen des Codeausschnitts auf das Literal oder Objekt gezeigt wird.

```xml
<ToolTip>
    ToolTip description
</ToolTip>
```

|Übergeordnetes Element|Beschreibung|
| - |-----------------|
|[Literal-Element](../ide/code-snippets-schema-reference.md#literal-element)|Definiert die Literalfelder des Codeausschnitts, die Sie bearbeiten können.|
|[Object-Element](../ide/code-snippets-schema-reference.md#object-element)|Definiert die Objektfelder des Codeausschnitts, die Sie bearbeiten können.|

Ein Textwert ist erforderlich. Dieser Text gibt die QuickInfo-Beschreibung an, die dem Objekt oder Literal im Codeausschnitt zugeordnet werden soll.

## <a name="type-element"></a>Type-Element

Gibt den Typ des Objekts an. Das `Object`-Element wird zur Kennzeichnung eines vom Codeausschnitt benötigten Elements verwendet, das möglicherweise jedoch außerhalb des Codeausschnitts selbst definiert wird. Beispielsweise sollten Windows Forms-Steuerelemente, ASP.NET-Steuerelemente, Objektinstanzen und Typinstanzen als Objekte deklariert werden. Für Objektdeklarationen muss ein Typ angegeben werden. Zu diesem Zweck wird das `Type`-Element verwendet.

```xml
<Type>
    Type
</Type>
```

|Übergeordnetes Element|Beschreibung|
| - |-----------------|
|[Object-Element](../ide/code-snippets-schema-reference.md#object-element)|Definiert die Objektfelder des Codeausschnitts, die Sie bearbeiten können.|

Ein Textwert ist erforderlich. Dieser Text gibt den Typ des Objekts an. Zum Beispiel:

```xml
<Type>System.Data.SqlClient.SqlConnection</Type>
```

## <a name="url-element"></a>URL-Element

Gibt eine URL an, die weitere Informationen über die referenzierte Assembly bietet.

> [!NOTE]
> Das `Url`-Element wird nur für Visual Basic-Projekte unterstützt.

```xml
<Url>
    www.microsoft.com
</Url>
```

|Übergeordnetes Element|Beschreibung|
| - |-----------------|
|[Reference-Element](../ide/code-snippets-schema-reference.md#reference-element)|Gibt die vom Codeausschnitt benötigten Assemblyverweise an.|

Ein Textwert ist erforderlich. Dieser Text bezeichnet eine URL mit weiteren Informationen über die Assembly, auf die verwiesen wird. Diese URL wird angezeigt, wenn dem Projekt der Verweis nicht hinzugefügt werden kann.

## <a name="see-also"></a>Siehe auch

- [Codeausschnitte](../ide/code-snippets.md)
- [Exemplarische Vorgehensweise: Create a code snippet (Exemplarische Vorgehensweise: Erstellen eines Codeausschnitts)](../ide/walkthrough-creating-a-code-snippet.md)
