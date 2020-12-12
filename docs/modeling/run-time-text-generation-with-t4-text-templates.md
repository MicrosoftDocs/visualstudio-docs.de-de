---
title: Laufzeittextgenerierung mithilfe von T4-Textvorlagen
description: Erfahren Sie, wie Sie Text Zeichenfolgen in Ihrer Anwendung zur Laufzeit mithilfe von Visual Studio-Lauf Zeit Textvorlagen generieren können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- Preprocessed Text Template project item
- TextTemplatingFilePreprocessor custom tool
- text templates, TransformText() method
- text templates, generating files at run time
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fcb7048b4319d1edb46911a74e96f440540e4299
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363938"
---
# <a name="run-time-text-generation-with-t4-text-templates"></a>Laufzeittextgenerierung mithilfe von T4-Textvorlagen

Sie können Text Zeichenfolgen in Ihrer Anwendung zur Laufzeit mithilfe von Visual Studio-Lauf Zeit Textvorlagen generieren. Auf dem Computer, auf dem die Anwendung ausgeführt wird, ist Visual Studio nicht erforderlich. Lauf Zeit Vorlagen werden manchmal als "vorverarbeitete Textvorlagen" bezeichnet, da die Vorlage zum Zeitpunkt der Kompilierung Code generiert, der zur Laufzeit ausgeführt wird.

Jede Vorlage ist eine Mischung aus dem Text, wie er in der generierten Zeichenfolge angezeigt wird, und Fragmente des Programmcodes. Die Programm Fragmente stellen Werte für die Variablen Teile der Zeichenfolge bereit und Steuern auch bedingte und wiederholte Teile.

Beispielsweise könnte die folgende Vorlage in einer Anwendung verwendet werden, die einen HTML-Bericht erstellt.

```html
<#@ template language="C#" #>
<html><body>
<h1>Sales for Previous Month</h2>
<table>
    <# for (int i = 1; i <= 10; i++)
       { #>
         <tr><td>Test name <#= i #> </td>
             <td>Test value <#= i * i #> </td> </tr>
    <# } #>
 </table>
This report is Company Confidential.
</body></html>
```

Beachten Sie, dass es sich bei der Vorlage um eine HTML-Seite handelt, in der die Variablen Teile durch Programmcode ersetzt wurden. Sie können mit dem Entwurf einer solchen Seite beginnen, indem Sie einen statischen Prototyp der HTML-Seite schreiben. Sie können dann die Tabelle und andere Variablen Teile durch Programmcode ersetzen, der den Inhalt generiert, der von einem Zeitpunkt zum nächsten abweicht.

Wenn Sie eine Vorlage in der Anwendung verwenden, ist es einfacher, die endgültige Form der Ausgabe zu sehen, als Sie z. b. eine lange Reihe von Schreib Anweisungen verwenden können. Das vornehmen von Änderungen an der Form der Ausgabe ist einfacher und zuverlässiger.

## <a name="creating-a-run-time-text-template-in-any-application"></a>Erstellen einer Run-Time Text Vorlage in einer beliebigen Anwendung

### <a name="to-create-a-run-time-text-template"></a>So erstellen Sie eine Lauf Zeit Textvorlage

1. Wählen Sie in Projektmappen-Explorer im Kontextmenü des Projekts die Option   >  **Neues Element** hinzufügen aus.

2. Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option **Lauf Zeit Text Vorlage** aus. (In Visual Basic unter **Allgemeine Elemente**  >  untersuchen **Allgemein**.)

3. Geben Sie einen Namen für die Vorlagen Datei ein.

    > [!NOTE]
    > Der Vorlagen Dateiname wird im generierten Code als Klassenname verwendet. Daher sollten keine Leerzeichen oder Interpunktions Zeichen vorhanden sein.

4. Wählen Sie **Hinzufügen** aus.

    Eine neue Datei mit der Erweiterung **. tt** wird erstellt. Die **benutzerdefinierte Tool** -Eigenschaft ist auf **texttemplatingfilepreprocessor** festgelegt. Sie enthält die folgenden Zeilen:

    ```
    <#@ template language="C#" #>
    <#@ assembly name="System.Core" #>
    <#@ import namespace="System.Linq" #>
    <#@ import namespace="System.Text" #>
    <#@ import namespace="System.Collections.Generic" #>
    ```

## <a name="converting-an-existing-file-to-a-run-time-template"></a>Eine vorhandene Datei in eine Run-Time Vorlage wird umgerechnet

Eine gute Möglichkeit, eine Vorlage zu erstellen, besteht darin, ein vorhandenes Beispiel der Ausgabe zu konvertieren. Wenn Ihre Anwendung z. b. HTML-Dateien generiert, können Sie zunächst eine einfache HTML-Datei erstellen. Stellen Sie sicher, dass er ordnungsgemäß funktioniert und seine Darstellung korrekt ist. Fügen Sie Sie dann in das Visual Studio-Projekt ein, und konvertieren Sie Sie in eine Vorlage.

### <a name="to-convert-an-existing-text-file-to-a-run-time-template"></a>So konvertieren Sie eine vorhandene Textdatei in eine Lauf Zeit Vorlage

1. Fügen Sie die Datei in Ihr Visual Studio-Projekt ein. Wählen Sie in Projektmappen-Explorer im Kontextmenü des Projekts   >  **Vorhandenes Element** hinzufügen aus.

2. Legen Sie die Eigenschaft **benutzerdefinierte Tools** der Datei auf **texttemplatingfilepreprocessor** fest. Klicken Sie in Projektmappen-Explorer im Kontextmenü der Datei auf **Eigenschaften**.

    > [!NOTE]
    > Wenn die Eigenschaft bereits festgelegt ist, stellen Sie sicher, dass Sie **texttemplatingfilepreprocessor** und nicht **TextTemplatingFileGenerator** ist. Dies kann vorkommen, wenn Sie eine Datei mit der Erweiterung **. tt** einschließen.

3. Ändern Sie die Dateinamenerweiterung in **. tt**. Obwohl dieser Schritt optional ist, können Sie die Datei nicht in einem falschen Editor öffnen.

4. Entfernen Sie alle Leerzeichen oder Satzzeichen aus dem Hauptteil des Datei namens. Beispielsweise wäre "My Web Page.tt" falsch, aber "MyWebPage.tt" ist richtig. Der Dateiname wird im generierten Code als Klassenname verwendet.

5. Fügen Sie die folgende Zeile am Anfang der Datei ein. Wenn Sie in einem Visual Basic Projekt arbeiten, ersetzen Sie "c#" durch "vb".

    `<#@ template language="C#" #>`

## <a name="the-content-of-the-run-time-template"></a>Der Inhalt der Run-Time Vorlage

### <a name="template-directive"></a>Template-Direktive

Behalten Sie die erste Zeile der Vorlage beim Erstellen der Datei bei:

`<#@ template language="C#" #>`

Der Language-Parameter hängt von der Sprache des Projekts ab.

### <a name="plain-content"></a>Reiner Inhalt

Bearbeiten Sie die **TT** -Datei so, dass Sie den Text enthält, der von der Anwendung generiert werden soll. Zum Beispiel:

```html
<html><body>
<h1>Sales for January</h2>
<!-- table to be inserted here -->
This report is Company Confidential.
</body></html>
```

### <a name="embedded-program-code"></a>Eingebetteter Programmcode

Sie können Programmcode zwischen `<#` und einfügen `#>` . Zum Beispiel:

```csharp
<table>
    <# for (int i = 1; i <= 10; i++)
       { #>
         <tr><td>Test name <#= i #> </td>
             <td>Test value <#= i * i #> </td> </tr>
    <# } #>
 </table>
```

```vb
<table>
<#
    For i As Integer = 1 To 10
#>
    <tr><td>Test name <#= i #> </td>
      <td>Test value <#= i*i #> </td></tr>
<#
    Next
#>
</table>
```

Beachten Sie, dass-Anweisungen zwischen eingefügt werden `<# ... #>` und Ausdrücke zwischen eingefügt werden `<#= ... #>` . Weitere Informationen finden Sie unter [Schreiben einer T4-Text Vorlage](../modeling/writing-a-t4-text-template.md).

## <a name="using-the-template"></a>Verwenden der Vorlage

### <a name="the-code-built-from-the-template"></a>Der aus der Vorlage erstellter Code

Beim Speichern der **TT** -Datei wird eine untergeordnete **CS** -oder **VB** -Datei generiert. Um diese Datei in **Projektmappen-Explorer** anzuzeigen, erweitern Sie den Knoten " **TT** -Datei". Wählen Sie in einem Visual Basic Projekt zuerst in der **Projektmappen-Explorer** Symbolleiste die Option **alle Dateien anzeigen** aus.

Beachten Sie, dass die Tochter Datei eine partielle Klasse enthält, die eine Methode mit dem Namen enthält `TransformText()` . Diese Methode kann von Ihrer Anwendung aufgerufen werden.

### <a name="generating-text-at-run-time"></a>Erstellen von Text zur Laufzeit

In Ihrem Anwendungscode können Sie den Inhalt Ihrer Vorlage mit einem folgenden Befehl generieren:

```csharp
MyWebPage page = new MyWebPage();
String pageContent = page.TransformText();
System.IO.File.WriteAllText("outputPage.html", pageContent);
```

```vb
Dim page = New My.Templates.MyWebPage
Dim pageContent = page.TransformText()
System.IO.File.WriteAllText("outputPage.html", pageContent)
```

Um die generierte Klasse in einem bestimmten Namespace zu platzieren, legen Sie die Eigenschaft **benutzerdefinierter Tool Namespace** der Textvorlagen Datei fest.

### <a name="debugging-runtime-text-templates"></a>Debug-Lauf Zeit Text Vorlagen

Debuggen und Testen von Lauf Zeit Textvorlagen auf die gleiche Weise wie normaler Code.

Sie können in einer Textvorlage einen Haltepunkt festlegen. Wenn Sie die Anwendung in Visual Studio im Debugmodus starten, können Sie den Code schrittweise durchlaufen und die Überwachungs Ausdrücke auf die übliche Weise auswerten.

### <a name="passing-parameters-in-the-constructor"></a>Übergeben von Parametern im Konstruktor

Normalerweise müssen von einer Vorlage einige Daten aus anderen Teilen der Anwendung importiert werden. Um dies zu vereinfachen, ist der von der Vorlage erstellter Code eine partielle Klasse. Sie können einen anderen Teil derselben Klasse in einer anderen Datei im Projekt erstellen. Diese Datei kann einen Konstruktor mit Parametern, Eigenschaften und Funktionen enthalten, auf die sowohl durch den in der Vorlage eingebetteten Code als auch durch den Rest der Anwendung zugegriffen werden kann.

Beispielsweise können Sie eine separate Datei **MyWebPageCode.cs** erstellen:

```csharp
partial class MyWebPage
{
    private MyData m_data;
    public MyWebPage(MyData data) { this.m_data = data; }}
```

In Ihrer Vorlagen Datei **MyWebPage.tt** könnten Sie Folgendes schreiben:

```html
<h2>Sales figures</h2>
<table>
<# foreach (MyDataItem item in m_data.Items)
   // m_data is declared in MyWebPageCode.cs
   { #>
      <tr><td> <#= item.Name #> </td>
          <td> <#= item.Value #> </td></tr>
<# } // end of foreach
#>
</table>
```

So verwenden Sie diese Vorlage in der Anwendung:

```csharp
MyData data = ...;
MyWebPage page = new MyWebPage(data);
String pageContent = page.TransformText();
System.IO.File.WriteAllText("outputPage.html", pageContent);
```

#### <a name="constructor-parameters-in-visual-basic"></a>Konstruktorparameter in Visual Basic

In Visual Basic enthält die separate Datei " **mywebpagecode. vb** " Folgendes:

```vb
Namespace My.Templates
  Partial Public Class MyWebPage
    Private m_data As MyData
    Public Sub New(ByVal data As MyData)
      m_data = data
    End Sub
  End Class
End Namespace
```

Die Vorlagen Datei kann Folgendes enthalten:

```html
<#@ template language="VB" #>
<html><body>
<h1>Sales for January</h2>
<table>
<#
    For Each item In m_data.Items
#>
    <tr><td>Test name <#= item.Name #> </td>
      <td>Test value <#= item.Value #> </td></tr>
<#
    Next
#>
</table>
This report is Company Confidential.
</body></html>
```

Die Vorlage kann aufgerufen werden, indem der-Parameter im-Konstruktor übergeben wird:

```vb
Dim data = New My.Templates.MyData
    ' Add data values here ....
Dim page = New My.Templates.MyWebPage(data)
Dim pageContent = page.TransformText()
System.IO.File.WriteAllText("outputPage.html", pageContent)
```

#### <a name="passing-data-in-template-properties"></a>Übergeben von Daten in Vorlagen Eigenschaften

Eine alternative Möglichkeit, Daten an die Vorlage zu übergeben, besteht darin, der Vorlagen Klasse in einer partiellen Klassendefinition öffentliche Eigenschaften hinzuzufügen. Die Anwendung kann die Eigenschaften vor dem Aufrufen von festlegen `TransformText()` .

Sie können Ihrer Vorlagen Klasse auch in einer partiellen Definition Felder hinzufügen. Dies ermöglicht es Ihnen, Daten zwischen aufeinander folgenden Ausführungen der Vorlage zu übergeben.

### <a name="use-partial-classes-for-code"></a>Verwenden von partiellen Klassen für Code

Viele Entwickler bevorzugen es, große Code Körper in Vorlagen zu schreiben. Stattdessen können Sie Methoden in einer partiellen Klasse definieren, die den gleichen Namen wie die Vorlagen Datei hat. Ruft diese Methoden aus der Vorlage auf. Auf diese Weise zeigt die Vorlage deutlicher an, wie die Ziel Ausgabe Zeichenfolge aussehen soll. Diskussionen über die Darstellung des Ergebnisses können von der Logik der Erstellung der angezeigten Daten getrennt werden.

### <a name="assemblies-and-references"></a>Assemblys und Verweise

Wenn Sie möchten, dass der Vorlagen Code auf eine .net-oder eine andere Assembly verweist, wie z. b. **System.Xml.dll**, fügen Sie Sie auf die übliche Weise den **verweisen** Ihres Projekts hinzu.

Wenn Sie einen Namespace auf die gleiche Weise wie eine-Anweisung importieren möchten `using` , können Sie dies mit der- `import` Direktive erreichen:

```
<#@ import namespace="System.Xml" #>
```

Diese Direktiven müssen am Anfang der Datei unmittelbar nach der- `<#@template` Direktive platziert werden.

### <a name="shared-content"></a>Freigegebener Inhalt

Wenn Sie über Text verfügen, der von mehreren Vorlagen gemeinsam genutzt wird, können Sie ihn in einer separaten Datei platzieren und in jede Datei einschließen, in der er angezeigt werden soll:

```
<#@include file="CommonHeader.txt" #>
```

Der enthaltene Inhalt kann eine beliebige Mischung aus Programmcode und nur-Text enthalten, und er kann andere include-Direktiven und andere Direktiven enthalten.

Die include-Direktive kann an beliebiger Stelle im Text einer Vorlagen Datei oder einer enthaltenen Datei verwendet werden.

### <a name="inheritance-between-run-time-text-templates"></a>Vererbung zwischen Run-Time Text Vorlagen

Sie können Inhalte Zwischenlauf Zeit Vorlagen freigeben, indem Sie eine Basisklassen Vorlage schreiben, die abstrakt sein kann. Verwenden Sie den- `inherits` Parameter der `<@#template#>` Direktive, um auf eine andere Lauf Zeit Vorlagen Klasse zu verweisen

#### <a name="inheritance-pattern-fragments-in-base-methods"></a>Vererbungsmuster: Fragmente in Basis Methoden

Beachten Sie in dem Muster, das im folgenden Beispiel verwendet wird, die folgenden Punkte:

- Die-Basisklasse `SharedFragments` definiert Methoden innerhalb von Klassen Funktionsblöcken `<#+ ... #>` .

- Die Basisklasse enthält keinen freien Text. Stattdessen treten alle Textblöcke innerhalb der Klassen Funktions Methoden auf.

- Die abgeleitete Klasse ruft die Methoden auf, die in definiert sind `SharedFragments` .

- Die Anwendung ruft die- `TextTransform()` Methode der abgeleiteten Klasse auf, transformiert jedoch nicht die Basisklasse `SharedFragments` .

- Sowohl die Basisklasse als auch die abgeleiteten Klassen sind Lauf Zeit Textvorlagen. Das heißt, die Eigenschaft **benutzerdefinierter Tool** ist auf **texttemplatingfilepreprocessor** festgelegt.

**SharedFragments.tt:**

```
<#@ template language="C#" #>
<#+
protected void SharedText(int n)
{
#>
   Shared Text <#= n #>
<#+
}
// Insert more methods here if required.
#>
```

**MyTextTemplate1.tt:**

```
<#@ template language="C#" inherits="SharedFragments" #>
begin 1
   <# SharedText(2); #>
end 1
```

**MyProgram.cs:**

```csharp
...
MyTextTemplate1 t1  = new MyTextTemplate1();
string result = t1.TransformText();
Console.WriteLine(result);
```

**Die resultierende Ausgabe:**

```
begin 1
    Shared Text 2
end 1
```

#### <a name="inheritance-pattern-text-in-base-body"></a>Vererbungsmuster: Text im Basis Körper

In dieser alternativen Vorgehensweise zum Verwenden der Vorlagen Vererbung wird der Großteil des Texts in der Basisvorlage definiert. Die abgeleiteten Vorlagen stellen Daten und Textfragmente bereit, die in den Basis Inhalt passen.

**AbstractBaseTemplate1.tt:**

```
<#@ template language="C#" #>

Here is the description for this derived template:
  <#= this.Description #>

Here is the fragment specific to this derived template:
<#
  this.PushIndent("  ");
  SpecificFragment(42);
  this.PopIndent();
#>
End of common template.
<#+
  // State set by derived class before calling TextTransform:
  protected string Description = "";
  // 'abstract' method to be defined in derived classes:
  protected virtual void SpecificFragment(int n) { }
#>
```

**DerivedTemplate1.tt:**

```
<#@ template language="C#" inherits="AbstractBaseTemplate1" #>
<#
  // Set the base template properties:
  base.Description = "Description for this derived class";

  // Run the base template:
  base.TransformText();

#>
End material for DerivedTemplate1.

<#+
// Provide a fragment specific to this derived template:

protected override void SpecificFragment(int n)
{
#>
   Specific to DerivedTemplate1 : <#= n #>
<#+
}
#>
```

**Anwendungscode:**

```csharp
...
DerivedTemplate1 t1 = new DerivedTemplate1();
string result = t1.TransformText();
Console.WriteLine(result);
```

**Ergebnis:**

```
Here is the description for this derived template:
  Description for this derived class

Here is the fragment specific to this derived template:
     Specific to DerivedTemplate1 : 42
End of common template.
End material for DerivedTemplate1.
```

## <a name="related-topics"></a>Verwandte Themen

Entwurfszeit Vorlagen: Wenn Sie eine Vorlage verwenden möchten, um Code zu generieren, der Teil der Anwendung wird, finden Sie weitere Informationen unter [Entwurfszeit Codegenerierung mithilfe von T4-Text Vorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

Lauf Zeit Vorlagen können in jeder Anwendung verwendet werden, in der die Vorlagen und deren Inhalt zur Kompilierzeit bestimmt werden. Wenn Sie jedoch eine Visual Studio-Erweiterung schreiben möchten, die Text aus Vorlagen generiert, die zur Laufzeit geändert werden, finden Sie weitere Informationen unter [Aufrufen von Text Transformation in einer vs-Erweiterung](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="see-also"></a>Siehe auch

- [Code Generierung und T4-Text Vorlagen](../modeling/code-generation-and-t4-text-templates.md)
- [Schreiben einer T4-Textvorlage](../modeling/writing-a-t4-text-template.md)
- [T4-Toolbox](http://olegsych.com/T4Toolbox/)
