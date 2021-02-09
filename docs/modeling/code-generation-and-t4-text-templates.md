---
title: Codegenerierung und T4-Textvorlagen
description: Erfahren Sie mehr über T4-Textvorlagen, die eine Mischung von Textblöcken und steuernder Logik sind, über die eine Textdatei generiert werden kann.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
f1_keywords:
- VS.ToolsOptionsPages.TextTemplating.TextTemplating
helpviewer_keywords:
- generating text
- .tt files
- code generation
- text templates
- generating code
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 262ab0638a128fe94561debabe35e20723fb6615
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861815"
---
# <a name="code-generation-and-t4-text-templates"></a>Codegenerierung und T4-Textvorlagen

In Visual Studio besteht eine *T4-Textvorlage* aus einer Mischung aus Textblöcken und steuernder Logik, über die eine Textdatei generiert werden kann. Die steuernde Logik wird als Programmcodefragmente in [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] oder [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]geschrieben. In Visual Studio 2015 Update 2 und höher können Sie Funktionen von C# Version 6.0 in T4-template-Direktiven verwenden. Die generierte Datei kann Text beliebiger Art enthalten, z. B. eine Webseite, eine Ressourcendatei oder Programmquellcode in einer beliebigen Sprache.

Es gibt zwei Arten von T4-Textvorlagen: Laufzeit und Entwurfszeit.

## <a name="run-time-t4-text-templates"></a>T4-Textvorlagen zur Laufzeit

Laufzeitvorlagen (also „vorverarbeitete“ Vorlagen) werden in Ihrer Anwendung ausgeführt, um Textzeichenfolgen zu erstellen (meist als Teil der Ausgabe der Anwendung). Sie könnten beispielsweise eine Vorlage erstellen, um eine HTML-Seite zu definieren:

```
<html><body>
 The date and time now is: <#= DateTime.Now #>
</body></html>
```

Sie sehen, dass die Vorlage der generierten Ausgabe ähnelt. Die Ähnlichkeit der Vorlage mit der resultierenden Ausgabe hilft Ihnen dabei, Fehler zu vermeiden, wenn Sie die Vorlage ändern möchten.

Außerdem enthält die Vorlage Programmcodefragmente. Sie können diese Fragmente verwenden, um Abschnitte des Texts zu wiederholen, bedingte Abschnitte zu erstellen und Daten aus Ihrer Anwendung anzuzeigen.

Um die Ausgabe zu generieren, ruft die Anwendung eine Funktion auf, die über die Vorlage generiert wurde. Beispiel:

```csharp
string webResponseText = new MyTemplate().TransformText();
```

Ihre Anwendung kann auf einem Computer ausgeführt werden, auf dem Visual Studio nicht installiert ist.

Um eine Laufzeitvorlage zu erstellen, fügen Sie Ihrem Projekt eine **Vorverarbeitete Textvorlage** -Datei hinzu. Alternativ können Sie eine Nur-Text-Datei hinzufügen und deren Eigenschaft **Benutzerdefiniertes Tool** auf **TextTemplatingFilePreprocessor** festlegen.

Weitere Informationen finden Sie unter [Laufzeittextgenerierung mithilfe von T4-Textvorlagen](../modeling/run-time-text-generation-with-t4-text-templates.md). Weitere Informationen zur Syntax von Vorlagen finden Sie unter [Schreiben einer T4-Textvorlage](../modeling/writing-a-t4-text-template.md).

## <a name="design-time-t4-text-templates"></a>T4-Entwurfszeit-Textvorlagen

T4-Entwurfszeit-Textvorlagenvorlagen definieren einen Teil des Quellcodes sowie andere Ressourcen Ihrer Anwendung. Üblicherweise verwenden Sie mehrere Vorlagen, über die die Daten aus einer einzelnen Eingabedatei oder Datenbank gelesen und einige Ihrer *.cs*, *.vb*- oder sonstigen Quelldateien generiert werden. Aus jeder Vorlage wird eine Datei generiert. Sie werden in Visual Studio oder MSBuild ausgeführt.

Ihre Eingabedaten könnten beispielsweise Konfigurationsdaten in einer XML-Datei sein. Immer dann, wenn Sie die XML-Datei während der Entwicklung bearbeitet haben, werden mit den Textvorlagen Teile des Anwendungscodes neu generiert. Eine der Vorlagen könnte so wie im folgenden Beispiel aussehen:

```
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml" #>
<#
 System.Xml.XmlDocument configurationData = ...; // Read a data file here.
#>
namespace Fabrikam.<#= configurationData.SelectSingleNode("jobName").Value #>
{
  ... // More code here.
}
```

Abhängig von den Werten in der XML-Datei würde die generierte *.cs*-Datei in etwa wie folgt aussehen:

```
namespace Fabrikam.FirstJob
{
  ... // More code here.
}
```

Ein weiteres Beispiel: Die Eingabe könnte ein Diagramm des Workflows in einer Geschäftsaktivität sein. Wenn die Benutzer ihren Geschäftsworkflow ändern oder wenn Sie beginnen, mit neuen Benutzern zu arbeiten, die einen anderen Workflow haben, kann der Code problemlos neu generiert werden, damit er dem neuen Modell entspricht.

Entwurfszeitvorlagen ermöglichen es, die Konfiguration schneller und zuverlässiger zu ändern, wenn sich die Anforderungen geändert haben. In der Regel ist die Eingabe hinsichtlich Geschäftsanforderungen definiert (wie im Workflowbeispiel). Dies erleichtert die Erörterung von Änderungen mit den Benutzern. Entwurfszeitvorlagen sind daher ein nützliches Tool in dynamischen Entwicklungsprozessen.

Um eine Entwurfszeitvorlage zu erstellen, fügen Sie Ihrem Projekt eine **Textvorlage** -Datei hinzu. Alternativ können Sie eine Nur-Text-Datei hinzufügen und deren Eigenschaft **Benutzerdefiniertes Tool** auf **TextTemplatingFileGenerator** festlegen.

Weitere Informationen finden Sie unter [Generieren von Code zur Entwurfszeit mithilfe von T4-Textvorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md). Weitere Informationen zur Syntax von Vorlagen finden Sie unter [Schreiben einer T4-Textvorlage](../modeling/writing-a-t4-text-template.md).

> [!NOTE]
> Der Begriff *Modell* wird manchmal verwendet, um Daten zu beschreiben, die von mindestens einer Vorlage gelesen werden. Das Modell kann in einem beliebigen Format in einer beliebigen Art von Datei oder Datenbank vorliegen. Es muss weder ein UML-Modell noch ein domänenspezifisches Sprachmodell sein. Der Begriff „Modell“ gibt lediglich an, dass die Daten hinsichtlich der Geschäftskonzepte definiert werden können, statt so auszusehen wie Code.

Die Transformationsfunktion für Textvorlagen wird als *T4* bezeichnet.

## <a name="see-also"></a>Weitere Informationen

- [Generieren von Code für eine domänenspezifische Sprache](../modeling/generating-code-from-a-domain-specific-language.md)
