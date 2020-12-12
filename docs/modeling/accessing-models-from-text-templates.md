---
title: Zugreifen auf Modelle aus Textvorlagen
description: Erfahren Sie, wie Sie Textvorlagen zum Erstellen von Berichtsdateien, Quell Code Dateien und anderen Textdateien verwenden können, die auf domänenspezifischen Sprachmodellen basieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- text templates, accessing models
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 64d937f9a63207e16664bbd9254ae60470caeb41
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362287"
---
# <a name="access-models-from-text-templates"></a>Zugreifen auf Modelle aus Textvorlagen

Mithilfe von Textvorlagen können Sie Berichtsdateien, Quell Code Dateien und andere Textdateien erstellen, die auf domänenspezifischen Sprachmodellen basieren. Grundlegende Informationen zu Textvorlagen finden Sie unter [Code Generierung und T4-Textvorlagen](../modeling/code-generation-and-t4-text-templates.md). Die Textvorlagen funktionieren beim Debuggen Ihrer DSL im experimentellen Modus und funktionieren auch auf einem Computer, auf dem Sie die DSL bereitgestellt haben.

> [!NOTE]
> Wenn Sie eine DSL-Projekt Mappe erstellen, werden Sample Text Template **\* . tt** -Dateien im debuggingprojekt generiert. Wenn Sie die Namen der Domänen Klassen ändern, funktionieren diese Vorlagen nicht mehr. Dennoch enthalten Sie die grundlegenden Direktiven, die Sie benötigen, und geben Beispiele an, die Sie entsprechend ihrer DSL aktualisieren können.

 So greifen Sie über eine Textvorlage auf ein Modell zu:

- Legen Sie die Eigenschaft Erben der Template-Direktive auf [Microsoft. VisualStudio. TextTemplating. vshost. modelingtexttransformation](/previous-versions/bb893209(v=vs.140))fest. Dies ermöglicht den Zugriff auf den Store.

- Geben Sie direktivenprozessoren für die DSL an, auf die Sie zugreifen möchten. Dadurch werden die Assemblys für die DSL geladen, sodass Sie Ihre Domänen Klassen, Eigenschaften und Beziehungen im Code der Textvorlage verwenden können. Außerdem wird die von Ihnen angegebene Modelldatei geladen.

  Eine `.tt` Datei, die dem folgenden Beispiel ähnelt, wird im debuggingprojekt erstellt, wenn Sie eine neue Visual Studio-Projekt Mappe aus der DSL-Vorlage mit minimaler Sprache erstellen.

```
<#@ template inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>
<#@ output extension=".txt" #>
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>

This text will be output directly.

This is the name of the model: <#= this.ModelRoot.Name #>

Here is a list of elements in the model:
<#
  // When you change the DSL Definition, some of the code below may not work.
  foreach (ExampleElement element in this.ExampleModel.Elements)
  {#>
<#= element.Name #>
<#
  }
#>
```

 Beachten Sie die folgenden Punkte zu dieser Vorlage:

- Die Vorlage kann die Domänen Klassen,-Eigenschaften und-Beziehungen verwenden, die Sie in der DSL-Definition definiert haben.

- Die Vorlage lädt die Modelldatei, die Sie in der- `requires` Eigenschaft angeben.

- Eine-Eigenschaft in `this` enthält das root-Element. Von dort aus kann der Code zu anderen Elementen des Modells navigieren. Der Name der Eigenschaft ist in der Regel mit der Stamm Domänen Klasse ihrer DSL identisch. In diesem Beispiel lautet er `this.ExampleModel`.

- Obwohl die Sprache, in der die Code Fragmente geschrieben werden, c# ist, können Sie Text beliebiger Art generieren. Sie können den Code auch in schreiben, indem Sie die-Eigenschaft der- [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] `language="VB"` `template` Direktive hinzufügen.

- Um die Vorlage zu debuggen, fügen Sie `debug="true"` der- `template` Anweisung hinzu. Die Vorlage wird in einer anderen Instanz von Visual Studio geöffnet, wenn eine Ausnahme auftritt. Wenn Sie den Debugger an einem bestimmten Punkt im Code unterbrechen möchten, fügen Sie die Anweisung ein. `System.Diagnostics.Debugger.Break();`

   Weitere Informationen finden Sie unter [Debuggen einer T4-Text Vorlage](../modeling/debugging-a-t4-text-template.md).

## <a name="about-the-dsl-directive-processor"></a>Informationen zum DSL-Direktivenprozessor
 Die Vorlage kann die Domänen Klassen verwenden, die Sie in ihrer DSL-Definition definiert haben. Dies erfolgt über eine-Direktive, die in der Regel am Anfang der Vorlage angezeigt wird. Im vorherigen Beispiel ist dies der folgende.

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>
```

 Der Name der Direktive ( `MyLanguage` in diesem Beispiel) wird vom Namen Ihrer DSL abgeleitet. Es ruft einen *Direktivenprozessor* auf, der als Teil ihrer DSL generiert wird. Sie finden den Quellcode in " **dsl\generatedcode\directiveprocessor.cs**".

 Der DSL-Direktivenprozessor führt zwei Hauptaufgaben aus:

- Sie fügt effektiv Assemblyanweisungen und Import Direktiven in die Vorlage ein, die auf Ihre DSL verweist. Auf diese Weise können Sie Ihre Domänen Klassen im Vorlagen Code verwenden.

- Die Datei, die Sie im-Parameter angeben `requires` , wird geladen, und es wird eine Eigenschaft in festgelegt, die `this` auf das Stamm Element des geladenen Modells verweist.

## <a name="validating-the-model-before-running-the-template"></a>Validieren des Modells vor dem Ausführen der Vorlage
 Sie können bewirken, dass das Modell überprüft wird, bevor die Vorlage ausgeführt wird.

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>
```

 Beachten Sie Folgendes:

1. Der `filename` -Parameter und der- `validation` Parameter werden durch ";" getrennt, und es dürfen keine anderen Trennzeichen oder Leerzeichen vorhanden sein.

2. Die Liste der Validierungs Kategorien bestimmt, welche Validierungs Methoden ausgeführt werden. Mehrere Kategorien sollten durch "&#124;" getrennt werden, und es dürfen keine anderen Trennzeichen oder Leerzeichen vorhanden sein.

   Wenn ein Fehler gefunden wird, wird dieser im Fenster Fehler angezeigt, und die Ergebnisdatei enthält eine Fehlermeldung.

## <a name="accessing-multiple-models-from-a-text-template"></a><a name="Multiple"></a> Zugreifen auf mehrere Modelle aus einer Textvorlage

> [!NOTE]
> Mit dieser Methode können Sie mehrere Modelle in derselben Vorlage lesen, aber ModelBus-Verweise werden nicht unterstützt. Informationen zum Lesen von Modellen, die durch ModelBus-Verweise miteinander verknüpft sind, finden Sie unter [Verwenden von Visual Studio ModelBus in einer Text Vorlage](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

 Wenn Sie auf mehr als ein Modell aus derselben Textvorlage zugreifen möchten, müssen Sie den generierten Direktivenprozessor einmal für jedes Modell aufrufen. Sie müssen den Dateinamen der einzelnen Modelle im- `requires` Parameter angeben. Sie müssen die Namen angeben, die Sie für die Stamm Domänen Klasse im-Parameter verwenden möchten `provides` . Sie müssen unterschiedliche Werte für die `provides` Parameter in den einzelnen direktivenaufrufen angeben. Nehmen Sie beispielsweise an, dass Sie über drei Modelldateien mit den Namen Library. XYZ, School. XYZ und work. XYZ verfügen. Um über dieselbe Textvorlage auf Sie zuzugreifen, müssen Sie drei direktivenaufrufe schreiben, die den folgenden ähneln.

```
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>
```

> [!NOTE]
> Dieser Beispielcode ist für eine Sprache vorgesehen, die auf der Vorlage für minimale Sprachlösungen basiert.

 Um auf die Modelle in der Textvorlage zuzugreifen, können Sie nun Code schreiben, der dem Code im folgenden Beispiel ähnelt.

```csharp
<#
foreach (ExampleElement element in this.LibraryModel.Elements)
...
foreach (ExampleElement element in this.SchoolModel.Elements)
...
foreach (ExampleElement element in this.WorkModel.Elements)
...
#>
```

```vb
<#
For Each element As ExampleElement In Me.LibraryModel.Elements
...
For Each element As ExampleElement In Me.SchoolModel.Elements
...
For Each element As ExampleElement In Me.WorkModel.Elements
...
#>
```

## <a name="loading-models-dynamically"></a>Dynamisches Laden von Modellen
 Wenn Sie zur Laufzeit bestimmen möchten, welche Modelle geladen werden sollen, können Sie eine Modelldatei dynamisch in den Programmcode laden, anstatt die DSL-spezifische Direktive zu verwenden.

 Eine der Funktionen der DSL-spezifischen Direktive besteht jedoch darin, den DSL-Namespace zu importieren, damit der Vorlagen Code die in dieser DSL definierten Domänen Klassen verwenden kann. Da Sie nicht die-Direktive verwenden, müssen Sie **\<assembly>** -und- **\<import>** Direktiven für alle Modelle hinzufügen, die Sie möglicherweise laden. Dies ist einfach, wenn die verschiedenen Modelle, die Sie möglicherweise laden, alle Instanzen derselben DSL sind.

 Die effektivste Methode zum Laden der Datei ist die Verwendung Visual Studio ModelBus. In einem typischen Szenario verwendet Ihre Textvorlage eine DSL-spezifische Direktive, um das erste Modell auf die übliche Weise zu laden. Dieses Modell enthält ModelBus-Verweise auf ein anderes Modell. Mit ModelBus können Sie das Modell öffnen, auf das verwiesen wird, und auf ein bestimmtes Element zugreifen. Weitere Informationen finden Sie unter [Verwenden von Visual Studio ModelBus in einer Text Vorlage](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

 In einem weniger üblichen Szenario möchten Sie möglicherweise eine Modelldatei öffnen, für die Sie nur einen Dateinamen haben und der möglicherweise nicht im aktuellen Visual Studio-Projekt enthalten ist. In diesem Fall können Sie die Datei mit dem Verfahren öffnen, das unter Gewusst [wie: Öffnen eines Modells aus einer Datei im Programm Code](../modeling/how-to-open-a-model-from-file-in-program-code.md)beschrieben wird.

## <a name="generating-multiple-files-from-a-template"></a>Erstellen mehrerer Dateien aus einer Vorlage
 Wenn Sie mehrere Dateien generieren möchten, um z. b. eine separate Datei für jedes Element in einem Modell zu generieren, gibt es mehrere mögliche Ansätze. Standardmäßig wird nur eine Datei aus jeder Vorlagen Datei erstellt.

### <a name="splitting-a-long-file"></a>Aufteilen einer langen Datei
 In dieser Methode verwenden Sie eine Vorlage, um eine einzelne Datei zu generieren, die durch ein Trennzeichen getrennt ist. Dann teilen Sie die Datei in ihre Teile. Es gibt zwei Vorlagen, eine zum Generieren der einzelnen Datei und die andere, um Sie zu teilen.

 **Looptemplate. T4** generiert die lange einzelne Datei. Beachten Sie, dass die Dateierweiterung ". T4" lautet, da Sie nicht direkt verarbeitet werden sollte, wenn Sie auf **alle Vorlagen transformieren** klicken. Diese Vorlage verwendet einen-Parameter, der die Trenn Zeichenfolge angibt, die die Segmente trennt:

```
<#@ template ninherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>
<#@ parameter name="delimiter" type="System.String" #>
<#@ output extension=".txt" #>
<#@ MyDSL processor="MyDSLDirectiveProcessor" requires="fileName='SampleModel.mydsl1';validation='open|load|save|menu'" #>
<#
  // Create a file segment for each element:
  foreach (ExampleElement element in this.ExampleModel.Elements)
  {
    // First item is the delimiter:
#>
<#= string.Format(delimiter, element.Id) #>

   Element: <#= element.Name #>
<#
   // Here you generate more content derived from the element.
  }
#>
```

 `LoopSplitter.tt` Ruft `LoopTemplate.t4` auf und teilt dann die resultierende Datei in ihre Segmente auf. Beachten Sie, dass diese Vorlage keine Modellierungs Vorlage sein muss, da Sie das Modell nicht liest.

```
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="Microsoft.VisualStudio.TextTemplating" #>
<#@ import namespace="System.Runtime.Remoting.Messaging" #>
<#@ import namespace="System.IO" #>

<#
  // Get the local path:
  string itemTemplatePath = this.Host.ResolvePath("LoopTemplate.t4");
  string dir = Path.GetDirectoryName(itemTemplatePath);

  // Get the template for generating each file:
  string loopTemplate = File.ReadAllText(itemTemplatePath);

  Engine engine = new Engine();

  // Pass parameter to new template:
  string delimiterGuid = Guid.NewGuid().ToString();
  string delimiter = "::::" + delimiterGuid + ":::";
  CallContext.LogicalSetData("delimiter", delimiter + "{0}:::");
  string joinedFiles = engine.ProcessTemplate(loopTemplate, this.Host);

  string [] separateFiles = joinedFiles.Split(new string [] {delimiter}, StringSplitOptions.None);

  foreach (string nameAndFile in separateFiles)
  {
     if (string.IsNullOrWhiteSpace(nameAndFile)) continue;
     string[] parts = nameAndFile.Split(new string[]{":::"}, 2, StringSplitOptions.None);
     if (parts.Length < 2) continue;
#>
 Generate: [<#= dir #>] [<#= parts[0] #>]
<#
     // Generate a file from this item:
     File.WriteAllText(Path.Combine(dir, parts[0] + ".txt"), parts[1]);
  }
#>
```
