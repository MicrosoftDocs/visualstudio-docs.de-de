---
title: Kontrollblöcke für Textvorlagen
description: Erfahren Sie mehr über Textvorlagen-Kontroll Blöcke und wie Kontroll Blöcke Ihnen das Schreiben von Code in der Textvorlage ermöglichen, um die Ausgabe zu variieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, template code
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 11cc289f668a674707c584396998ea7abb9e7ea9
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363587"
---
# <a name="text-template-control-blocks"></a>Kontrollblöcke für Textvorlagen
Kontrollblöcke ermöglichen Ihnen das Schreiben von Code in die Textvorlage, um die Ausgabe zu variieren. Es gibt drei Arten von Kontrollblöcken, die anhand ihrer öffnenden Klammern unterschieden werden:

- `<# Standard control blocks #>` kann Anweisungen enthalten.

- `<#= Expression control blocks #>` kann Ausdrücke enthalten.

- `<#+ Class feature control blocks #>` kann Methoden, Felder und Eigenschaften enthalten.

## <a name="standard-control-block"></a>Standardkontrollblock
 Standardkontrollblöcke enthalten Anweisungen. Beispielsweise werden mit dem folgenden Standardblock die Namen aller Attribute im XML-Dokument abgerufen:

```
<#@ assembly name="System.Xml.dll" #>
<#@ import namespace="System.Xml" #>

<#
    List<string> allAttributes = new List<string>();
    XmlDocument xDoc = new XmlDocument();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes.Count > 0)
    {
       foreach (XmlAttribute attr in attributes)
       {
           allAtributes.Add(attr.Name);
       }
     }
#>
```

 Sie können Nur-Text in einer Verbundanweisung einbetten, wie `if` oder `for`. Dieses Fragment beispielsweise generiert eine Ausgabezeile in jeder Schleifeniteration:

```
<#
       foreach (XmlAttribute attr in attributes)
       {
#>
Found another one!
<#
           allAtributes.Add(attr.Name);
       }
#>
```

> [!WARNING]
> Immer {...} verwenden zum Begrenzen von schsted-Anweisungen, die eingebetteten nur-Text enthalten. Das folgende Beispiel funktioniert möglicherweise nicht ordnungsgemäß:
>
> `<# if (ShouldPrint) #> Some text. -- WRONG`
>
> Stattdessen sollten Sie {geschweifte Klammern} wie folgt einfügen:

```

<#
 if (ShouldPrint)
 {   //  "{" REQUIRED
#>
Some text.
<#
 }
#>
```

## <a name="expression-control-block"></a>Ausdruckskontrollblock
 Ausdruckskontrollblöcke werden für Code verwendet, der in die Ausgabedatei zu schreibende Zeichenfolgen bietet. Mit dem obigen Beispiel beispielsweise können Sie die Namen der Attribute in die Ausgabedatei drucken, indem Sie den Codeblock wie folgt ändern:

```
<#
    XmlDocument xDoc = new XmlDocument();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes != null)
    {
       foreach (XmlAttribute attr in attributes)
       {
#><#= attr.Name #><#
       }
    }
#>
```

## <a name="class-feature-control-block"></a>Klassenfunktionskontrollblock
 Sie können Klassenfunktionskontrollblöcke verwenden, um der Textvorlage Methoden, Eigenschaften, Felder oder sogar geschachtelte Klassen hinzuzufügen. Die häufigste Verwendung von Klassenfunktionsblöcken besteht in der Bereitstellung von Hilfsfunktonen für Code in anderen Teilen der Textvorlage. Beispielsweise wird mit dem folgenden Klassenfunktionsblock der erste Buchstabe des Attributnamens großgeschrieben (oder, wenn der Name Leerzeichen enthält, wird der erste Buchstabe jedes Wortes großgeschrieben):

```
<#@ import namespace="System.Globalization" #>
```

```
<#+
    private string FixAttributeName(string name)
    {
        return CultureInfo.CurrentCulture.TextInfo.ToTitleCase(name);
    }
#>
```

> [!NOTE]
> Einem Klassenfunktionskontrollblock darf nicht von Standardkontrollblöcken in derselben Vorlagendatei gefolgt werden. Allerdings gilt diese Einschränkung nicht für das Ergebnis der Verwendung von `<#@include#>`-Direktiven. Jede enthaltene Datei kann Standardblöcke besitzen, denen von Klassenfunktionsblöcken gefolgt wird.

 Sie können eine Funktion erstellen, die Ausgaben durch das Einbetten von Text und Ausdrucksblöcken in einem Klassenfunktionskontrollblock generiert. Zum Beispiel:

```
<#+
    private void OutputFixedAttributeName(string name)
    {
#>
 Attribute:  <#= CultureInfo.CurrentCulture.TextInfo.ToTitleCase(name) #>
<#+  // <<< Notice that this is also a class feature block.
    }
#>
```

 Sie können diese Funktion über einen Standardblock oder einen anderen Klassenfunktionsblock aufrufen:

```
<# foreach (Attribute attribute in item.Attributes)
{
  OutputFixedAttributeName(attribute.Name);
}
#>
```

## <a name="how-to-use-control-blocks"></a>So verwenden Sie Kontrollblöcke
 Der gesamte Code in all den Standard- und Ausdruckskontrollblöcken in einer einzelnen Vorlage (einschließlich des gesamten Codes in eingeschlossenen Vorlagen) wird zur `TransformText()`-Methode des generierten Codes kombiniert. (Weitere Informationen zum einschließen anderer Textvorlagen mit der- `include` Direktive finden Sie unter [T4-Textvorlagen Direktiven](../modeling/t4-text-template-directives.md).)

 Sie sollten beim Verwenden von Kontrollblöcken Folgendes bedenken:

- **Sprache.** Sie können in einer Textvorlage entweder C#- oder Visual Basic-Code verwenden. Die Standardsprache ist C#, Sie können jedoch Visual Basic mit dem `language`-Parameter der `template`-Direktive angeben. (Weitere Informationen zur- `template` Direktive finden Sie unter [T4-Text Vorlagen Direktiven](../modeling/t4-text-template-directives.md).)

     Die in Kontrollblöcken verwendete Sprache hat nichts mit der Sprache oder dem Format des Texts zu tun, den Sie in einer Textvorlage generieren. Sie können C# mithilfe von Visual Basic-Code generieren oder umgekehrt.

     Sie können nur eine Sprache in einer Textvorlage verwenden, einschließlich aller Textvorlagen, die Sie in die `include`-Direktive einschließen.

- **Lokale Variablen.** Da der gesamte Code in den Standard- und-Ausdruckskontrollblöcken in einer Textvorlage als eine einzelne Methode generiert wird, sollten Sie sicherstellen, dass keine Konflikte mit den Namen der lokalen Variable bestehen. Wenn Sie andere Textvorlagen einschließen, müssen Sie sicherstellen, dass Variablennamen in allen eingeschlossenen Vorlagen eindeutig sind. Eine Möglichkeit, dies sicherzustellen, besteht darin, jedem lokalen Variablennamen eine Zeichenfolge hinzuzufügen, die die Textvorlage identifiziert, in der sie deklariert wurde.

     Es ist auch eine gute Idee, die lokalen Variablen mit sinnvollen Werten zu initialisieren, wenn Sie sie deklarieren, insbesondere dann, wenn Sie mehrere Textvorlagen einschließen.

- **Schachteln von Kontrollblöcken.** Kontrollblöcke können nicht ineinander geschachtelt werden. Sie müssen einen Kontrollblock immer beenden, bevor Sie einen anderen öffnen. Beispielsweise zeigt folgende Vorgehensweise das Drucken von Text in einem Ausdrucksblock als Teil eines Standardkontrollblocks.

    ```
    <#
    int x = 10;
    while (x-- > 0)
    {
    #>
    <#= x #>
    <# } #>
    ```

- **Refactoring.** Um die Textvorlagen kurz und leicht verständlich zu halten, wird dringend empfohlen, dass Sie sich wiederholenden Code vermeiden, entweder durch die Einteilung von wiederverwendbarem Code in Hilfsfunktionen in Klassenfunktionsblöcken oder durch Erstellen einer eigenen Textvorlagenklasse, die von der Microsoft.VisualStudio.TextTemplating.TextTransformation-Klasse erbt.
