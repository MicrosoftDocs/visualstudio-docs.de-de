---
title: 'Exemplarische Vorgehensweise: Generieren von Code mithilfe von Textvorlagen'
description: Erfahren Sie, dass Sie mit der Codegenerierung Programmcode erzeugen können, der stark typisiert ist, und sich bei Änderungen des Quell Modells leicht ändern können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- walkthroughs [text templates], generating application code
- walkthroughs [text templates]
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7e6b824d53c37ef922b8c9580c87a478aef93586
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924065"
---
# <a name="walkthrough-generate-code-by-using-text-templates"></a>Exemplarische Vorgehensweise: Generieren von Code mithilfe von Textvorlagen

Durch Codegenerierung können Sie Programmcode erstellen, der stark typisiert ist und problemlos geändert werden, wenn sich das Quellmodell ändert. Vergleichen Sie dies mit der alternativen Technik für ein vollkommen generisches Programm, das eine Konfigurationsdatei akzeptiert, was flexibler ist, aber zu Code führt, der nicht so einfach zu lesen und zu ändern ist und keine so gute Leistung aufweist. In dieser exemplarischen Vorgehensweise wird dieser Vorteil veranschaulicht.

## <a name="typed-code-for-reading-xml"></a>Typisierter Code zum Lesen von XML

Der System.Xml-Namespace stellt umfassende Tools für das Laden eines XML-Dokuments in den Arbeitsspeicher bereit, wo es dann frei navigierbar ist. Leider haben alle Knoten den gleichen Typ, XmlNode. Es ist daher sehr einfach, Programmierfehler zu machen, z.B. den falschen Typ von untergeordneten Knoten oder die falschen Attribute zu erwarten.

In diesem Beispielprojekt liest eine Vorlage eine Beispiel-XML-Datei und generiert Klassen, die jedem Knotentyp entsprechen. Bei handgeschriebenem Code können Sie diese Klassen verwenden, um in der XML-Datei zu navigieren. Sie können Ihre Anwendung auch mit anderen Dateien ausführen, die die gleichen Knotentypen verwenden. Die XML-Beispieldatei dient dazu, Beispiele für alle Knotentypen bereitzustellen, für die Ihre Anwendung gedacht ist.

> [!NOTE]
> Der in Visual Studio enthaltene Anwendungs [xsd.exe](/dotnet/standard/serialization/xml-schema-definition-tool-xsd-exe)kann stark typisierte Klassen aus XML-Dateien generieren. Die hier gezeigte Vorlage wird als Beispiel bereitgestellt.

Hier ist die Beispieldatei:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<catalog>
  <artist id ="Mike%20Nash" name="Mike Nash Quartet">
    <song id ="MikeNashJazzBeforeTeatime">Jazz Before Teatime</song>
    <song id ="MikeNashJazzAfterBreakfast">Jazz After Breakfast</song>
  </artist>
  <artist id ="Euan%20Garden" name="Euan Garden">
    <song id ="GardenScottishCountry">Scottish Country Garden</song>
  </artist>
</catalog>
```

Im Projekt, das in dieser exemplarischen Vorgehensweise erstellt wird, können Sie Code wie den folgenden schreiben und IntelliSense stellt Ihnen während der Eingabe die korrekten Attribute und untergeordneten Namen bereit:

```csharp
Catalog catalog = new Catalog(xmlDocument);
foreach (Artist artist in catalog.Artist)
{
  Console.WriteLine(artist.name);
  foreach (Song song in artist.Song)
  {
    Console.WriteLine("   " + song.Text);
  }
}
```

Vergleichen Sie dies mit dem nicht typisierten Code, den Sie ohne die Vorlage schreiben würden:

```csharp
XmlNode catalog = xmlDocument.SelectSingleNode("catalog");
foreach (XmlNode artist in catalog.SelectNodes("artist"))
{
    Console.WriteLine(artist.Attributes["name"].Value);
    foreach (XmlNode song in artist.SelectNodes("song"))
    {
         Console.WriteLine("   " + song.InnerText);
     }
}
```

In der stark typisierten Version führt eine Änderung des XML-Schemas zu Änderungen an den Klassen. Der Compiler hebt die Teile des Anwendungs Codes hervor, die geändert werden müssen. In der nicht typisierten Version, die allgemeinen XML-Code verwendet, gibt es keine solche Unterstützung.

In diesem Projekt wird eine einzelne Vorlagendatei verwendet, um die Klassen zu generieren, die die typisierte Version ermöglichen.

## <a name="set-up-the-project"></a>Einrichten des Projekts

### <a name="create-or-open-a-c-project"></a>Erstellen oder öffnen Sie ein C#-Projekt

Sie können diese Technik für jedes Codeprojekt anwenden. Diese exemplarische Vorgehensweise verwendet ein C#-Projekt, und zu Testzwecken verwenden wir eine Konsolenanwendung.

1. Klicken Sie im Menü **Datei** auf **neu** , und klicken Sie dann auf **Projekt**.

2. Klicken Sie auf den **Visual C#** -Knoten und anschließend im Bereich **Vorlagen** auf **Konsolenanwendung**.

### <a name="add-a-prototype-xml-file-to-the-project"></a>Fügen Sie eine XML-Prototypdatei zum Projekt hinzu

Diese Datei dient dazu, Beispiele der XML-Knotentypen bereitzustellen, die Ihre Anwendung lesen können soll. Es kann eine Datei sein, die zum Testen der Anwendung verwendet wird. Die Vorlage erzeugt eine C#-Klasse für jeden Knotentyp in dieser Datei.

Die Datei sollte Teil des Projekts sein, damit die Vorlage sie lesen kann, aber sie wird nicht in die kompilierte Anwendung integriert werden.

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, klicken Sie auf **Hinzufügen** und dann auf **Neues Element**.

2. Wählen Sie im Dialogfeld **Neues Element hinzufügen****XML-Datei** aus den **Vorlagen** aus.

3. Fügen Sie der Datei Ihren Beispielinhalt hinzu.

4. In dieser exemplarischen Vorgehensweise benennen Sie die Datei `exampleXml.xml`. Legen Sie als Inhalt der Datei die im vorherigen Abschnitt gezeigten XML-Daten fest.

### <a name="add-a-test-code-file"></a>Fügen Sie eine Testcodedatei hinzu

Fügen Sie eine C#-Datei dem Projekt hinzu und schreiben Sie darin ein Beispiel für Code, den Sie schreiben können möchten. Beispiel:

```csharp
using System;
namespace MyProject
{
  class CodeGeneratorTest
  {
    public void TestMethod()
    {
      Catalog catalog = new Catalog(@"..\..\exampleXml.xml");
      foreach (Artist artist in catalog.Artist)
      {
        Console.WriteLine(artist.name);
        foreach (Song song in artist.Song)
        {
          Console.WriteLine("   " + song.Text);
} } } } }
```

In dieser Phase wird dieser Code nicht kompiliert. Beim Schreiben der Vorlage generieren Sie Klassen, die eine erfolgreiche Kompilierung ermöglichen.

Ein umfassender Test könnte die Ausgabe dieser Testfunktion im Vergleich zu dem bekannten Inhalt der Beispiel-XML-Datei überprüfen. In dieser exemplarischen Vorgehensweise sind wir jedoch zufrieden, wenn die Testmethode kompiliert.

### <a name="add-a-text-template-file"></a>Fügen Sie eine Textvorlagendatei hinzu

Fügen Sie eine Textvorlagen Datei hinzu, und legen Sie die Ausgabe Erweiterung auf " *. cs*" fest.

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, klicken Sie auf **Hinzufügen** und anschließend auf **Neues Element**.

2. Wählen Sie im Dialogfeld **Neues Element hinzufügen****Textvorlage** aus den **Vorlagen** aus.

    > [!NOTE]
    > Stellen Sie sicher, dass Sie eine Textvorlage und keine vorverarbeitete Textvorlage hinzufügen.

3. Ändern Sie in der Datei, in der Vorlagendirektive das `hostspecific` -Attribut in `true`.

     Durch diese Änderung kann der Vorlagen Code auf die Visual Studio-Dienste zugreifen.

4. Ändern Sie in der Output-Direktive das Erweiterungsattribut in ".cs", sodass die Vorlage eine C#-Datei generiert. In einem Visual Basic-Projekt würden Sie es in ".vb" ändern.

5. Speichern Sie die Datei . In dieser Phase sollte die Textvorlagendatei diese Zeilen enthalten:

    ```
    <#@ template debug="false" hostspecific="true" language="C#" #>
    <#@ output extension=".cs" #>
    ```

Beachten Sie, dass eine CS-Datei im Projektmappen-Explorer als untergeordnete Datei der Vorlagendatei angezeigt wird. Sie können Sie sehen, wenn Sie auf das [+] neben dem Namen der Vorlagendatei klicken. Diese Datei wird aus der Vorlagendatei generiert wenn Sie speichern oder den Fokus von der Vorlagendatei wegnehmen. Die generierte Datei wird als Teil des Projekts kompiliert.

Während Sie die Vorlagendatei entwickeln, ordnen Sie der Einfachheit halber die Fenster der Vorlagendatei und der generierten Datei so an, dass Sie nebeneinander angezeigt werden. Dadurch können Sie sofort die Ausgabe der Vorlage sehen. Wenn die Vorlage ungültigen C#-Code generiert, erscheinen Fehler im Fenster mit den Fehlermeldungen.

Änderungen, die Sie direkt in der generierten Datei ausführen, gehen verloren, sobald Sie die Vorlagendatei speichern. Sie sollten daher entweder vermeiden, die generierte Datei zu bearbeiten, oder sie nur für kurze Experimente bearbeiten. Manchmal ist es sinnvoll, ein kurzes Codefragment in der generierten Datei zu testen, wo IntelliSense in Betrieb ist, und dann in die Vorlagendatei zu kopieren.

## <a name="develop-the-text-template"></a>Entwickeln der Text Vorlage

Nach der Empfehlung zu agiler Entwicklung werden wir die Vorlage in kleinen Schritten entwickeln und in jedem Schritt einige Fehler bereinigen, bis der Testcode korrekt kompiliert und ausgeführt wird.

### <a name="prototype-the-code-to-be-generated"></a>Erstellen Sie einen Prototyp des Codes, der generiert werden soll

Der Testcode erfordert eine Klasse für jeden Knoten in der Datei. Daher werden einige der Kompilierungsfehler behoben, wenn Sie diese Zeilen an die Vorlage anfügen und speichern:

```csharp
class Catalog {}
class Artist {}
class Song {}
```

Dadurch können Sie sehen, was erforderlich ist, aber die Deklarationen sollten aus den Knotentypen in der Beispiel-XML-Datei erstellt werden. Löschen Sie diese experimentellen Zeilen aus der Vorlage.

### <a name="generate-application-code-from-the-model-xml-file"></a>Generieren Sie Anwendungscode aus der XML-Modelldatei

Um die XML-Datei lesen und Klassendeklarationen generieren zu können, ersetzen Sie den Vorlageninhalt durch den folgenden Vorlagencode:

```
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml"#>
<#@ import namespace="System.Xml" #>
<#
 XmlDocument doc = new XmlDocument();
 // Replace this file path with yours:
 doc.Load(@"C:\MySolution\MyProject\exampleXml.xml");
 foreach (XmlNode node in doc.SelectNodes("//*"))
 {
#>
  public partial class <#= node.Name #> {}
<#
 }
#>
```

Ersetzen Sie den Dateipfad durch den korrekten Pfad für das Projekt.

Beachten Sie die Codeblocktrennzeichen `<#...#>`. Diese Trennzeichen umklammern ein Fragment des Programmcodes, das den Text generiert. Sie Ausdrucksblocktrennzeichen `<#=...#>` umklammern einen Ausdruck, der zu einer Zeichenfolge ausgewertet werden kann.

Wenn Sie eine Vorlage schreiben, die Quellcode für die Anwendung generiert, arbeiten Sie mit zwei separaten Programmtexten. Das Programm innerhalb der Codeblocktrennzeichen wird jedes Mal ausgeführt, wenn Sie die Vorlage speichern oder den Fokus in ein anderes Fenster verschieben. Der generierte Text, der außerhalb der Trennzeichen angezeigt wird, wird in die generierte Datei kopiert und wird Teil des Anwendungscodes.

Die `<#@assembly#>` -Direktive verhält sich wie ein Verweis und macht die Assembly für den Vorlagencode verfügbar. Die Liste der Assemblys, die die Vorlage sieht, ist unabhängig von der Liste der Verweise im Anwendungsprojekt.

Die `<#@import#>` -Direktive verhält sich wie eine `using` -Anweisung und ermöglicht Ihnen die Verwendung von Kurznamen von Klassen im importierten Namespace.

Leider, obwohl diese Vorlage Code generiert, erzeugt sie eine Klassendeklaration für jeden Knoten in der Beispiel-XML-Datei. Wenn mehrere Instanzen des `<song>` -Knotens vorhanden sind, werden mehrere Deklarationen der Klasse „song“ angezeigt.

### <a name="read-the-model-file-then-generate-the-code"></a>Lesen der Modelldatei, anschließend Generieren des Codes

Viele Textvorlagen folgen einem Muster, in dem der erste Teil der Vorlage die Quelldatei liest und der zweite Teil die Vorlage generiert. Wir müssen die gesamte Beispieldatei lesen, um die Knotentypen zusammenzufassen, die sie enthält, und dann die Klassendeklarationen generieren. Ein anderes `<#@import#>` ist erforderlich, damit wir `Dictionary<>:` verwenden können

```
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml"#>
<#@ import namespace="System.Xml" #>
<#@ import namespace="System.Collections.Generic" #>
<#
 // Read the model file
 XmlDocument doc = new XmlDocument();
 doc.Load(@"C:\MySolution\MyProject\exampleXml.xml");
 Dictionary <string, string> nodeTypes =
        new Dictionary<string, string>();
 foreach (XmlNode node in doc.SelectNodes("//*"))
 {
   nodeTypes[node.Name] = "";
 }
 // Generate the code
 foreach (string nodeName in nodeTypes.Keys)
 {
#>
  public partial class <#= nodeName #> {}
<#
 }
#>
```

### <a name="add-an-auxiliary-method"></a>Hinzufügen einer zusätzlichen Methode

Ein Klassenfunktionskontrollblock ist ein Block in dem Sie zusätzliche Methoden definieren können. Der Block wird getrennt durch `<#+...#>` und muss als letzter Block in der Datei erscheinen.

Wenn Sie Klassennamen bevorzugen, die mit einem Großbuchstaben beginnen, können Sie den letzten Teil der Vorlage mit dem folgenden Vorlagencode ersetzen:

```
// Generate the code
 foreach (string nodeName in nodeTypes.Keys)
 {
#>
  public partial class <#= UpperInitial(nodeName) #> {}
<#
 }
#>
<#+
 private string UpperInitial(string name)
 { return name[0].ToString().ToUpperInvariant() + name.Substring(1); }
#>
```

In dieser Phase enthält die generierte *CS* -Datei die folgenden Deklarationen:

```csharp
public partial class Catalog {}
public partial class Artist {}
public partial class Song {}
```

Weitere Informationen, wie Eigenschaften für die untergeordneten Knoten, Attribute und innerer Text können auf gleiche Weise hinzugefügt werden.

### <a name="access-the-visual-studio-api"></a>Zugreifen auf die Visual Studio-API

Durch Festlegen des- `hostspecific` Attributs der- `<#@template#>` Direktive kann die Vorlage Zugriff auf die Visual Studio-API erhalten. Die Vorlage kann dies verwenden, um den Speicherort der Projektdateien zu erhalten, um zu vermeiden, dass ein absoluter Dateipfad im Vorlagencode enthalten ist.

```
<#@ template debug="false" hostspecific="true" language="C#" #>
...
<#@ assembly name="EnvDTE" #>
...
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
// Open the prototype document.
XmlDocument doc = new XmlDocument();
doc.Load(System.IO.Path.Combine(dte.ActiveDocument.Path, "exampleXml.xml"));
```

## <a name="complete-the-text-template"></a>Text Vorlage vervollständigen

Der folgende Vorlageninhalt generiert Code, mit dem der Testcode kompiliert und ausgeführt werden kann.

```
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="System.Xml" #>
<#@ import namespace="System.Collections.Generic" #>
using System;using System.Collections.Generic;using System.Linq;using System.Xml;namespace MyProject{
<#
 // Map node name --> child name --> child node type
 Dictionary<string, Dictionary<string, XmlNodeType>> nodeTypes = new Dictionary<string, Dictionary<string, XmlNodeType>>();

 // The Visual Studio host, to get the local file path.
 EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
 // Open the prototype document.
 XmlDocument doc = new XmlDocument();
 doc.Load(System.IO.Path.Combine(dte.ActiveDocument.Path, "exampleXml.xml"));
 // Inspect all the nodes in the document.
 // The example might contain many nodes of the same type,
 // so make a dictionary of node types and their children.
 foreach (XmlNode node in doc.SelectNodes("//*"))
 {
   Dictionary<string, XmlNodeType> subs = null;
   if (!nodeTypes.TryGetValue(node.Name, out subs))
   {
     subs = new Dictionary<string, XmlNodeType>();
     nodeTypes.Add(node.Name, subs);
   }
   foreach (XmlNode child in node.ChildNodes)
   {
     subs[child.Name] = child.NodeType;
   }
   foreach (XmlNode child in node.Attributes)
   {
     subs[child.Name] = child.NodeType;
   }
 }
 // Generate a class for each node type.
 foreach (string className in nodeTypes.Keys)
 {
    // Capitalize the first character of the name.
#>
    partial class <#= UpperInitial(className) #>
    {      private XmlNode thisNode;      public <#= UpperInitial(className) #>(XmlNode node)       { thisNode = node; }

<#
    // Generate a property for each child.
    foreach (string childName in nodeTypes[className].Keys)
    {
      // Allow for different types of child.
      switch (nodeTypes[className][childName])
      {
         // Child nodes:
         case XmlNodeType.Element:
#>
      public IEnumerable<<#=UpperInitial(childName)#>><#=UpperInitial(childName) #>      {         get         {            foreach (XmlNode node in                thisNode.SelectNodes("<#=childName#>"))              yield return new <#=UpperInitial(childName)#>(node);       } }
<#
         break;
         // Child attributes:
         case XmlNodeType.Attribute:
#>
      public string <#=childName #>      { get { return thisNode.Attributes["<#=childName#>"].Value; } }
<#
         break;
         // Plain text:
         case XmlNodeType.Text:
#>
      public string Text  { get { return thisNode.InnerText; } }
<#
         break;
       } // switch
     } // foreach class child
  // End of the generated class:
#>
   }
<#
 } // foreach class

   // Add a constructor for the root class
   // that accepts an XML filename.
   string rootClassName = doc.SelectSingleNode("*").Name;
#>
   partial class <#= UpperInitial(rootClassName) #>   {      public <#= UpperInitial(rootClassName) #>(string fileName){        XmlDocument doc = new XmlDocument();        doc.Load(fileName);        thisNode = doc.SelectSingleNode("<#=rootClassName#>");}   }}
<#+
   private string UpperInitial(string name)
   {
      return name[0].ToString().ToUpperInvariant() + name.Substring(1);
   }
#>
```

### <a name="run-the-test-program"></a>Ausführen des Testprogramms

Im Hauptfenster der Konsolenanwendung führen die folgenden Zeilen die Testmethode aus. Drücken Sie F5, um das Programm im Debugmodus auszuführen:

```csharp
using System;
namespace MyProject
{
  class Program
  {
    static void Main(string[] args)
    {
      new CodeGeneratorTest().TestMethod();
      // Allow user to see the output:
      Console.ReadLine();
    }
  }
}
```

### <a name="write-and-update-the-application"></a>Schreiben und Aktualisieren der Anwendung

Die Anwendung kann jetzt im stark typisierten Stil geschrieben werden, mit den generierten Klassen anstelle von generischem XML-Code.

Wenn sich das XML-Schema ändert, können neue Klassen leicht generiert werden. Der Compiler teilt dem Entwickler mit, wo der Anwendungscode aktualisiert werden muss.

Um die Klassen neu zu generieren, wenn die XML-Beispieldatei geändert wird, klicken Sie auf der Symbolleiste **Projektmappen-Explorer** auf **alle Vorlagen transformieren** .

## <a name="conclusion"></a>Zusammenfassung

In dieser exemplarischen Vorgehensweise werden verschiedene Techniken und Vorteile der Codegenerierung veranschaulicht:

- *Codegenerierung* ist die Erstellung eines Teils des Quellcodes der Anwendung aus einem *Modell*. Das Modell enthält Informationen in einer zur Anwendungsdomäne passenden Form und kann sich im Laufe der Lebensdauer der Anwendung ändern.

- Starke Typisierung ist ein Vorteil bei der Codegenerierung. Während das Modell Informationen in einer für den Benutzer geeigneten Form darstellt, ermöglicht der generierte Code anderen Teilen der Anwendung den Umgang mit den Informationen über einen Satz von Typen.

- IntelliSense und der Compiler hilft beim Erstellen von Code, der zum Schema des Modells passt – wenn Sie neuen Code schreiben und bei der Aktualisierung des Schemas.

- Das Hinzufügen einer einzigen unkomplizierten Vorlagendatei zu einem Projekt kann diese Vorteile bieten.

- Eine Textvorlage kann entwickelt und schnell und schrittweise getestet werden.

In dieser exemplarischen Vorgehensweise wird der Programmcode eigentlich aus einer Instanz des Modells generiert, einem repräsentativen Beispiel der XML-Dateien, die die Anwendung verarbeitet. In einem formaleren Ansatz würde das XML-Schema in der Form einer XSD-Datei oder einer domänenspezifischen Sprachdefinition als Vorgabe für die Vorlage dienen. Dieser Ansatz würde es für die Vorlage einfacher machen, Merkmale wie die Multiplizität einer Beziehung zu ermitteln.

## <a name="troubleshoot-the-text-template"></a>Problembehandlung bei der Text Vorlage

Wenn Sie Vorlagentransformations- oder Kompilierungsfehler in der **Fehlerliste** sehen oder die Ausgabedatei nicht korrekt generiert wurde, können Sie die Textvorlage mit den unter [Generieren von Dateien mit dem Hilfsprogramm „TextTransform“](../modeling/generating-files-with-the-texttransform-utility.md) beschriebenen Techniken entsprechend korrigieren.

## <a name="see-also"></a>Weitere Informationen

- [Generieren von Code zur Entwurfszeit mithilfe von T4-Textvorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
- [Schreiben einer T4-Textvorlage](../modeling/writing-a-t4-text-template.md)
