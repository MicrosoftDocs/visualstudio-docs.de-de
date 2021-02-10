---
title: Generieren von Code zur Entwurfszeit mithilfe von T4-Textvorlagen
description: Erfahren Sie, wie Sie mit T4-Textvorlagen zur Entwurfszeit Programmcode und andere Dateien in Ihrem Visual Studio-Projekt generieren können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- text templates, guidelines for code generation
- text templates, data source model
- TextTemplatingFileGenerator custom tool
- Transform All Templates
- text templates, getting started
- Text Template project item
- text templates, generating code for your application
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 11c9384d03971f475abbe680f6731d2757cbb195
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935299"
---
# <a name="design-time-code-generation-by-using-t4-text-templates"></a>Generieren von Code zur Entwurfszeit mithilfe von T4-Textvorlagen

Mit T4-Textvorlagen zur Entwurfszeit können Sie Programmcode und andere Dateien in Ihrem Visual Studio-Projekt generieren. In der Regel schreiben Sie die Vorlagen so, dass Sie den Code, den Sie generieren, gemäß den Daten aus einem *Modell* verändern. Bei einem Modell handelt es sich um eine Datei oder Datenbank, die wichtige Informationen zu den Anforderungen Ihrer Anwendung enthält.

In einem Modell kann z. B. ein Workflow entweder als Tabelle oder Diagramm definiert sein. Anhand des Modells können Sie die Software generieren, die den Workflow ausführt. Wenn sich die Anforderungen der Benutzer ändern, ist es einfach, den neuen Workflow mit den Benutzern zu besprechen. Die erneute Generierung des Codes anhand des Workflows ist zuverlässiger als die manuelle Aktualisierung des Codes.

> [!NOTE]
> Ein *Modell* ist eine Datenquelle, die einen bestimmten Aspekt einer Anwendung beschreibt. Ein Modell kann ein beliebiges Format in einem beliebigen Datei- oder Datenbanktyp aufweisen. Es muss kein bestimmtes Format besitzen, wie z. B. ein UML-Modell oder ein domänenspezifisches Sprachmodell. Typische Modelle werden als Tabellen oder XML-Dateien dargestellt.

Sie sind wahrscheinlich bereits mit der Codegenerierung vertraut. Wenn Sie Ressourcen in einer **RESX** -Datei in der Visual Studio-Projekt Mappe definieren, wird automatisch ein Satz von Klassen und Methoden generiert. Durch die Ressourcendatei können die Ressourcen einfacher und zuverlässiger bearbeitet werden als dies beim Bearbeiten der Klassen und Methoden möglich wäre. Mithilfe von Textvorlagen können Sie Code auf die gleiche Weise aus einer selbst entworfenen Quelle generieren.

Eine Textvorlage enthält eine Mischung des Texts, den Sie generieren möchten, sowie Programmcode, der Variablenteile des Texts generiert. Der Programmcode ermöglicht das wiederholen oder bedingte Weglassen von Teilen des generierten Texts. Der generierte Text selbst kann Programmcode sein, der einen Teil der Anwendung bildet.

## <a name="create-a-design-time-t4-text-template"></a>Erstellen einer Design-Time T4-Text Vorlage

1. Erstellen Sie ein neues Visual Studio-Projekt, oder öffnen Sie ein vorhandenes Projekt.

2. Fügen Sie dem Projekt eine Textvorlagen Datei hinzu, und geben Sie Ihr einen Namen mit der Erweiterung **. tt**.

    Wählen Sie hierzu in **Projektmappen-Explorer** im Kontextmenü des Projekts die Option   >  **Neues Element** hinzufügen aus. Wählen Sie im Dialogfeld **Neues Element hinzufügen** im mittleren Bereich **Text Vorlage** aus.

    Beachten Sie, dass die Eigenschaft **benutzerdefiniertes Tool** der Datei **TextTemplatingFileGenerator** ist.

3. Öffnen Sie die Datei. Sie enthält bereits die folgenden Anweisungen:

   ```
   <#@ template hostspecific="false" language="C#" #>
   <#@ output extension=".txt" #>
   ```

    Wenn Sie die Vorlage einem [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]-Projekt hinzugefügt haben, ist das Sprachattribut auf `VB` festgelegt.

4. Fügen Sie am Ende der Datei Text hinzu. Beispiel:

   ```
   Hello, world!
   ```

5. Speichern Sie die Datei .

    Möglicherweise wird ein Meldungs Feld mit einer **Sicherheitswarnung** angezeigt, in dem Sie aufgefordert werden, zu bestätigen, dass Sie die Vorlage ausführen möchten. Klicken Sie auf **OK**.

6. Erweitern Sie in **Projektmappen-Explorer** den Vorlagen Datei Knoten, und Sie finden eine Datei mit der Erweiterung **. txt**. Die Datei enthält den Text, der von der Vorlage generiert wird.

   > [!NOTE]
   > Wenn es sich bei dem Projekt um ein Visual Basic Projekt handelt, müssen Sie auf **alle Dateien anzeigen** klicken, um die Ausgabedatei anzuzeigen.

### <a name="regenerate-the-code"></a>Erneutes Generieren des Codes

In den folgenden Fällen wird eine Vorlage ausgeführt, wobei die untergeordnete Datei generiert wird:

- Bearbeiten Sie die Vorlage, und ändern Sie dann den Fokus in ein anderes Visual Studio-Fenster.

- Speichern Sie die Vorlage.

- Klicken Sie im Menü **Erstellen** auf **alle Vorlagen transformieren** . Dadurch werden alle Vorlagen in der Visual Studio-Projekt Mappe transformiert.

- Wählen Sie in **Projektmappen-Explorer** im Kontextmenü einer beliebigen Datei die Option **benutzerdefiniertes Tool ausführen** aus. Verwenden Sie diese Methode, um eine ausgewählte Untergruppe von Vorlagen zu transformieren.

Sie können auch ein Visual Studio-Projekt so einrichten, dass die Vorlagen ausgeführt werden, wenn sich die von Ihnen gelesenen Datendateien geändert haben. Weitere Informationen finden Sie unter Automatisches Erneutes Generieren [des Codes](#Regenerating).

## <a name="generate-variable-text"></a>Variablen Text generieren

Textvorlagen ermöglichen es Ihnen, den Inhalt der generierten Datei mithilfe von Programmcode zu verändern.

1. Ändern des Inhalts der `.tt`-Datei:

   ```csharp
   <#@ template hostspecific="false" language="C#" #>
   <#@ output extension=".txt" #>
   <#int top = 10;

   for (int i = 0; i<=top; i++)
   { #>
      The square of <#= i #> is <#= i*i #>
   <# } #>
   ```

   ```vb
   <#@ template hostspecific="false" language="VB" #>
   <#@ output extension=".txt" #>
   <#Dim top As Integer = 10

   For i As Integer = 0 To top
   #>
       The square of <#= i #> is <#= i*i #>
   <#
   Next
   #>
   ```

2. Speichern Sie die TT-Datei, und überprüfen Sie die generierte TXT-Datei erneut. Sie enthält die Quadratzahlen der Zahlen 0 bis 10.

   Beachten Sie, dass Anweisungen in `<#...#>` eingeschlossen sind und einzelne Ausdrücke in `<#=...#>`. Weitere Informationen finden Sie unter [Schreiben einer T4-Text Vorlage](../modeling/writing-a-t4-text-template.md).

   Wenn Sie den generierenden Code in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] schreiben, sollte die `template`-Direktive `language="VB"` enthalten. `"C#"` ist die Standardeinstellung.

## <a name="debugging-a-design-time-t4-text-template"></a>Debuggen einer T4-Textvorlage für die Entwurfszeit

So debuggen Sie eine Textvorlage

- Fügen Sie `debug="true"` in die `template`-Anweisung ein. Beispiel:

   `<#@ template debug="true" hostspecific="false" language="C#" #>`

- Legen Sie in der Vorlage Haltepunkte auf dieselbe Weise fest wie für normalen Code.

- Wählen Sie im Kontextmenü der Textvorlagen Datei in Projektmappen-Explorer die Option **T4-Vorlage Debuggen** aus.

   Die Vorlage wird an den Breakpoints ausgeführt und angehalten. Sie können Variablen prüfen und den Code ganz normal durchlaufen.

> [!TIP]
> `debug="true"` bewirkt, dass der generierte Code Map präziser in die Textvorlage eingefügt wird, indem weitere Zeilen nummerierungsdirektiven in den generierten Code eingefügt werden. Wenn Sie diese auslassen, wird die Ausführung möglicherweise durch die Haltepunkte im falschen Zustand angehalten.
>
> Sie können jedoch die Klausel in der template-Anweisung lassen, auch wenn Sie nicht debuggen. Dies verursacht nur einen sehr geringen Leistungsverlust.

## <a name="generating-code-or-resources-for-your-solution"></a>Generieren von Code oder Ressourcen für die Projektmappe

Abhängig vom Modell können verschiedene Programmdateien generiert werden. Ein Modell ist eine Eingabequelle wie eine Datenbank, eine Konfigurationsdatei, ein UML- oder DSL-Modell oder eine andere Quelle. Normalerweise generieren Sie mehrere Programmdateien aus demselben Modell. Sie erstellen zu diesem Zweck eine Vorlagendatei für jede generierte Programmdatei und lassen das gleiche Modell von allen Vorlagen lesen.

### <a name="to-generate-program-code-or-resources"></a>So generieren Sie Programmcode oder Ressourcen

1. Ändern Sie die output-Direktive, um eine Datei des entsprechenden Typs zu generieren, z. B. .cs, .vb, .resx oder .xml.

2. Fügen Sie Code ein, durch den der benötigte Projektmappencode generiert wird. Fügen Sie z. B. folgenden Code ein, wenn Sie drei Deklarationen für Felder für ganze Zahlen in einer Klasse generieren möchten:

    ```csharp

    <#@ template debug="false" hostspecific="false" language="C#" #>
    <#@ output extension=".cs" #>
    <# var properties = new string [] {"P1", "P2", "P3"}; #>
    // This is generated code:
    class MyGeneratedClass {
    <# // This code runs in the text template:
      foreach (string propertyName in properties)  { #>
      // Generated code:
      private int <#= propertyName #> = 0;
    <# } #>
    }
    ```

    ```vb
    <#@ template debug="false" hostspecific="false" language="VB" #>
    <#@ output extension=".cs" #>
    <# Dim properties = {"P1", "P2", "P3"} #>
    class MyGeneratedClass {
    <#
       For Each propertyName As String In properties
    #>
      private int <#= propertyName #> = 0;
    <#
       Next
    #>
    }

    ```

3. Speichern Sie die Datei, und überprüfen Sie die generierte Datei, die nun den folgenden Code enthält:

    ```csharp
    class MyGeneratedClass {
      private int P1 = 0;
      private int P2 = 0;
      private int P3 = 0;
    }
    ```

### <a name="generating-code-and-generated-text"></a>Generieren von Code und generierter Text

Wenn Sie Programmcode generieren, ist es wichtig, den Generierungscode, der in der Vorlage ausgeführt wird, nicht mit dem resultierenden generierten Code zu verwechseln, der Teil der Projektmappe wird. Die beiden Sprachen müssen nicht identisch sein.

Das vorherige Beispiel enthält zwei Versionen. In einer Version liegt der generierende Code in C# vor. In der anderen Version liegt der generierende Code in Visual Basic vor. Der in beiden Versionen generierte Text ist jedoch identisch, und er befindet sich in einer C#-Klasse.

Ebenso können Sie eine [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]-Vorlage verwenden, um Code in einer beliebigen Sprache zu generieren. Der generierte Text muss nicht in einer bestimmten Sprache vorliegen, und es muss sich nicht um Programmcode handeln.

### <a name="structuring-text-templates"></a>Strukturieren von Textvorlagen

Es wird empfohlen, den Vorlagencode in zwei Teile aufzuteilen:

- Ein Konfigurations- oder Datensammlungsteil, der Werte in Variablen festlegt, jedoch keine Textblöcke enthält. Im vorherigen Beispiel ist dieser Teil die Initialisierung von `properties`.

   Dies wird manchmal als Modellabschnitt bezeichnet, da ein speicherinternes Modell erstellt und normalerweise eine Modelldatei gelesen wird.

- Der Textgenerierungsteil (im vorliegenden Beispiel `foreach(...){...}`), in dem die Werte der Variablen verwendet werden.

   Dies ist keine notwendige Trennung, doch auf diese Weise wird das Lesen der Vorlage wegen der geringeren Komplexität des Teils, der Text enthält, vereinfacht.

## <a name="reading-files-or-other-sources"></a>Lesen von Dateien oder anderen Quellen

Im Vorlagencode können Assemblys wie System.XML verwendet werden, um auf eine Modelldatei oder eine Datenbank zuzugreifen. Um Zugriff auf diese Assemblys zu erhalten, müssen Sie wie hier dargestellt Anweisungen einfügen:

```
<#@ assembly name="System.Xml.dll" #>
<#@ import namespace="System.Xml" #>
<#@ import namespace="System.IO" #>
```

Die- `assembly` Direktive macht die angegebene Assembly auf die gleiche Weise wie der Referenz Abschnitt eines Visual Studio-Projekts für den Vorlagen Code verfügbar. Sie müssen keinen Verweis auf "System.dll" einschließen, da automatisch darauf verwiesen wird. Die `import`-Anweisung ermöglicht wie die `using`-Anweisung in einer normalen Programmdatei die Verwendung von Typen ohne ihre vollqualifizierten Namen.

Beispielsweise können Sie nach dem Importieren von **System.IO** Folgendes schreiben:

```csharp

<# var properties = File.ReadLines("C:\\propertyList.txt");#>
...
<# foreach (string propertyName in properties) { #>
...
```

```vb
<# For Each propertyName As String In
             File.ReadLines("C:\\propertyList.txt")
#>
```

### <a name="opening-a-file-with-a-relative-pathname"></a>Öffnen einer Datei mit einem relativen Pfadnamen

Verwenden Sie `this.Host.ResolvePath()`, um eine Datei aus einem Ort zu laden, der relativ zur Textvorlage ist. Zur Verwendung von this.Host muss `hostspecific="true"` in `template` festgelegt werden:

```
<#@ template debug="false" hostspecific="true" language="C#" #>
```

Anschließend können Sie z. B. Folgendes schreiben:

```csharp
<# string filename = this.Host.ResolvePath("filename.txt");
  string [] properties = File.ReadLines(filename);
#>
...
<#  foreach (string propertyName in properties { #>
...
```

```vb
<# Dim filename = Me.Host.ResolvePath("propertyList.txt")
   Dim properties = File.ReadLines(filename)
#>
...
<#   For Each propertyName As String In properties
...
#>
```

Sie können auch `this.Host.TemplateFile` verwenden, was den Namen der aktuellen Vorlagendatei darstellt.

Der Typ von `this.Host` (in VB `Me.Host`) ist `Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost`.

### <a name="getting-data-from-visual-studio"></a>Erhalten von Daten aus Visual Studio

Um in Visual Studio bereitgestellte Dienste zu verwenden, legen Sie das `hostSpecific` -Attribut fest, und laden Sie die `EnvDTE` Assembly. Import `Microsoft.VisualStudio.TextTemplating` , das die `GetCOMService()` Erweiterungsmethode enthält.  Sie können dann IServiceProvider.GetCOMService() verwenden, um auf DTE und andere Dienste zuzugreifen. Beispiel:

```src
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="Microsoft.VisualStudio.TextTemplating" #>
<#
  IServiceProvider serviceProvider = (IServiceProvider)this.Host;
  EnvDTE.DTE dte = (EnvDTE.DTE) serviceProvider.GetCOMService(typeof(EnvDTE.DTE));
#>

Number of projects in this VS solution:  <#= dte.Solution.Projects.Count #>
```

> [!TIP]
> Eine Textvorlage wird in ihrer eigene App-Domäne ausgeführt, und der Zugriff auf Dienste erfolgt durch Marshalling. Unter diesen Umständen ist GetCOMService() zuverlässiger als GetService().

## <a name="regenerating-the-code-automatically"></a><a name="Regenerating"></a> Automatisches Erneutes Generieren des Codes

In der Regel werden mehrere Dateien in einer Visual Studio-Projekt Mappe mit einem Eingabe Modell generiert. Jede Datei wird aus einer eigenen Vorlage generiert, die Vorlagen verweisen jedoch alle auf das gleiche Modell.

Wenn sich das Quellmodell ändert, müssen Sie alle Vorlagen in der Projektmappe erneut ausführen. Um dies manuell durchzuführen, wählen Sie im Menü **Erstellen** die Option **alle Vorlagen transformieren** aus.

Wenn Sie das Visual Studio-Modellierungs-SDK installiert haben, können alle Vorlagen automatisch transformiert werden, wenn Sie einen Build ausführen. Bearbeiten Sie dazu die Projektdatei (.csproj oder .vbproj) in einem Text-Editor, und fügen Sie in der Nähe des Endes der Datei nach allen anderen `<import>`-Anweisungen die folgenden Zeilen hinzu:

> [!NOTE]
> Das Text Template Transformation SDK und das Visual Studio-Modellierungs-SDK werden automatisch installiert, wenn Sie bestimmte Features von Visual Studio installieren. Weitere Informationen finden Sie in [diesem Blogbeitrag](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/).

::: moniker range="vs-2017"

```xml
<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v15.0\TextTemplating\Microsoft.TextTemplating.targets" />
<PropertyGroup>
   <TransformOnBuild>true</TransformOnBuild>
   <!-- Other properties can be inserted here -->
</PropertyGroup>
```

::: moniker-end

::: moniker range=">=vs-2019"

```xml
<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v16.0\TextTemplating\Microsoft.TextTemplating.targets" />
<PropertyGroup>
   <TransformOnBuild>true</TransformOnBuild>
   <!-- Other properties can be inserted here -->
</PropertyGroup>
```

::: moniker-end

Weitere Informationen finden Sie unter [Code Generierung in einem Buildprozess](../modeling/code-generation-in-a-build-process.md).

## <a name="error-reporting"></a>Fehlerberichterstellung

Zum Platzieren von Fehler-und Warnmeldungen im Visual Studio-Fehler Fenster können Sie folgende Methoden verwenden:

```
Error("An error message");
Warning("A warning message");
```

## <a name="converting-an-existing-file-to-a-template"></a><a name="Converting"></a> Eine vorhandene Datei in eine Vorlage wird umgerechnet

Eine hilfreiche Funktion von Vorlagen ist, dass sie den generierten Dateien sehr ähneln und zudem einigen eingefügten Programmcode enthalten. Dadurch ergibt sich eine einfache Methode zum Erstellen einer Vorlage. Erstellen Sie zunächst eine gewöhnliche Datei als Prototyp, z. b. eine [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Datei, und führen Sie dann schrittweise den Generierungs Code ein, der die resultierende Datei variiert.

### <a name="to-convert-an-existing-file-to-a-design-time-template"></a>So konvertieren Sie eine vorhandene Datei in eine Entwurfszeitvorlage

1. Fügen Sie Ihrem Visual Studio-Projekt eine Datei des Typs hinzu, den Sie generieren möchten, z. b `.cs` . eine-,-oder- `.vb` `.resx` Datei.

2. Testen Sie die neue Datei, um sicherzustellen, dass sie ordnungsgemäß funktioniert.

3. Ändern Sie in Projektmappen-Explorer die Dateinamenerweiterung in **. tt**.

4. Überprüfen Sie die folgenden Eigenschaften der **TT** -Datei:

   | | |
   |-|-|
   | **Benutzerdefiniertes Tool =** | **TextTemplatingFileGenerator** |
   | **Buildvorgang =** | **None** |

5. Fügen Sie am Anfang der Datei die folgenden Zeilen ein:

   ```
   <#@ template debug="false" hostspecific="false" language="C#" #>
   <#@ output extension=".cs" #>
   ```

    Wenn Sie den Generierungscode der Vorlage in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] schreiben möchten, legen Sie das `language`-Attribut anstelle von `"VB"` auf `"C#"` fest.

    Legen Sie das `extension`-Attribut auf die Dateinamenerweiterung für den zu generierenden Dateityp fest, z. B. `.cs`, `.resx` oder `.xml`.

6. Speichern Sie die Datei .

    Eine untergeordnete Datei mit der angegebenen Erweiterung wird erstellt. Die Eigenschaften entsprechen dem Dateityp. Beispielsweise **wäre die Eigenschaft** Buildvorgang einer CS-Datei " **Compile**".

    Vergewissern Sie sich, dass die generierte Datei den gleichen Inhalt enthält wie die ursprüngliche Datei.

7. Identifizieren Sie einen Teil der Datei, den Sie ändern möchten. Beispielsweise einen Teil, der nur unter bestimmten Bedingungen angezeigt oder wiederholt wird oder in dem sich bestimmte Werte ändern. Fügen Sie Generierungscode ein. Speichern Sie die Datei, und überprüfen Sie, ob die untergeordnete Datei ordnungsgemäß generiert wurde. Wiederholen Sie diesen Schritt.

## <a name="guidelines-for-code-generation"></a>Richtlinien für die Codegenerierung

Informationen finden Sie unter [Richtlinien zum Schreiben von T4-Text Vorlagen](../modeling/guidelines-for-writing-t4-text-templates.md).

## <a name="next-steps"></a>Nächste Schritte

|Nächster Schritt|Thema|
|-|-|
|Schreiben und debuggen Sie eine erweiterte Textvorlage mit Code, in dem zusätzliche Funktionen, eingeschlossene Dateien und externe Daten verwendet werden.|[Schreiben einer T4-Textvorlage](../modeling/writing-a-t4-text-template.md)|
|Generieren Sie zur Laufzeit Dokumente aus Vorlagen.|[Laufzeittextgenerierung mithilfe von T4-Textvorlagen](../modeling/run-time-text-generation-with-t4-text-templates.md)|
|Ausführen von Textgenerierung außerhalb von Visual Studio.|[Generieren von Dateien mit dem Hilfsprogramm "TextTransform"](../modeling/generating-files-with-the-texttransform-utility.md)|
|Transformieren Sie die Daten in das Format einer domänenspezifischen Sprache.|[Generieren von Code für eine domänenspezifische Sprache](../modeling/generating-code-from-a-domain-specific-language.md)|
|Schreiben Sie Direktivenprozessoren, um eigene Datenquellen zu transformieren.|[Anpassen der T4-Texttransformation](../modeling/customizing-t4-text-transformation.md)|

## <a name="see-also"></a>Weitere Informationen

- [Richtlinien für das Verfassen von T4-Textvorlagen](../modeling/guidelines-for-writing-t4-text-templates.md)
