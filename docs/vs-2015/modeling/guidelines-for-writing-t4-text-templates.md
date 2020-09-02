---
title: Richtlinien zum Schreiben von T4-Text Vorlagen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 04dd3fc4-10e8-488a-bdea-4d615f50f063
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d1e15a8c00a0614d020defd2df7b06665289a8b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666052"
---
# <a name="guidelines-for-writing-t4-text-templates"></a>Richtlinien für das Verfassen von T4-Textvorlagen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese allgemeinen Richtlinien können hilfreich sein, wenn Sie Programmcode oder andere Anwendungs Ressourcen in Erstellen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Es handelt sich nicht um Fixed-Regeln.

## <a name="guidelines-for-design-time-t4-templates"></a>Richtlinien für T4-Vorlagen zur Entwurfszeit
 T4-Vorlagen für die Entwurfszeit sind Vorlagen, die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zur Entwurfszeit Code in Ihrem Projekt generieren. Weitere Informationen finden Sie unter [Entwurfszeit Code Generierung mithilfe von T4-Text Vorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

 Generieren Sie Variablen Aspekte der Anwendung.
Die Code Generierung ist besonders nützlich für die Aspekte der Anwendung, die sich während des Projekts ändern können, oder sich zwischen verschiedenen Versionen der Anwendung ändert. Trennen Sie diese Variablen Aspekte von den mehr invarianten Aspekten, damit Sie leichter bestimmen können, was generiert werden muss. Wenn Ihre Anwendung z. b. eine Website bereitstellt, trennen Sie die Standardseiten für Funktionen von der Logik, die die Navigationspfade von einer Seite zu einer anderen definiert.

 Codieren der Variablen Aspekte in einem oder mehreren Quell Modellen.
Bei einem Modell handelt es sich um eine Datei oder Datenbank, die jede Vorlage liest, um bestimmte Werte für Variablen Teile des Codes zu erhalten, die generiert werden sollen. Modelle können Datenbanken, XML-Dateien Ihrer eigenen Entwurfs-, Diagramm-oder domänenspezifischen Sprachen sein. In der Regel wird ein Modell verwendet, um viele Dateien in einem Projekt zu generieren [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Jede Datei wird aus einer separaten Vorlage generiert.

 Sie können mehr als ein Modell in einem Projekt verwenden. Beispielsweise können Sie ein Modell für die Navigation zwischen Webseiten und ein separates Modell für das Layout der Seiten definieren.

 Konzentrieren Sie sich auf das Modell auf die Anforderungen und das Vokabular der Benutzer, nicht auf Ihre Implementierung.
Beispielsweise erwarten Sie in einer Website Anwendung, dass das Modell auf Webseiten und Hyperlinks verweist.

 Im Idealfall wählen Sie eine Form der Präsentation aus, die der Art der vom Modell dargestellten Informationen entspricht. Ein Modell der Navigationspfade über eine Website könnte beispielsweise ein Diagramm von Feldern und Pfeilen sein.

 Testen Sie den generierten Code.
Verwenden Sie manuelle oder automatisierte Tests, um zu überprüfen, ob der resultierende Code für die Benutzer erforderlich ist. Vermeiden Sie das Generieren von Tests aus dem Modell, von dem aus der Code generiert wird.

 In einigen Fällen können allgemeine Tests direkt für das Modell durchgeführt werden. Beispielsweise können Sie einen Test schreiben, mit dem sichergestellt wird, dass jede Seite auf der Website durch Navigation von jedem anderen erreicht werden kann.

 Benutzerdefinierten Code zulassen: Generieren Sie partielle Klassen.
Hiermit wird der Code, den Sie per Hand schreiben, zusätzlich zum generierten Code zugelassen. Es ist nicht ungewöhnlich, dass ein Code Generierungs Schema alle möglichen Abweichungen berücksichtigen kann, die auftreten können. Daher sollten Sie davon ausgehen, dass Sie einen Teil des generierten Codes hinzufügen oder überschreiben. Wenn sich das generierte Material in einer .NET-Sprache, z. b. [!INCLUDE[csprcs](../includes/csprcs-md.md)] oder [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] , befindet, sind zwei Strategien besonders nützlich:

- Die generierten Klassen sollten partiell sein. Auf diese Weise können Sie dem generierten Code Inhalte hinzufügen.

- Klassen sollten in Paaren generiert werden, von denen eine von der anderen erbt. Die Basisklasse sollte alle generierten Methoden und Eigenschaften enthalten, und die abgeleitete Klasse sollte nur die Konstruktoren enthalten. Dadurch kann der handgeschriebene Code eine beliebige der generierten Methoden überschreiben.

  Verwenden Sie in anderen generierten Sprachen, wie z. b. XML, die- `<#@include#>` Direktive, um einfache Kombinationen von handgeschriebenen und generierten Inhalten zu erstellen. In komplexeren Fällen müssen Sie möglicherweise einen nach Verarbeitungsschritt schreiben, der die generierte Datei mit jeder handgeschriebenen Datei kombiniert.

  Verschieben allgemeiner Materialien in include-Dateien oder Lauf Zeit Vorlagen, um zu vermeiden, dass ähnliche Textblöcke und Code in mehreren Vorlagen wiederholt werden, verwenden Sie die- `<#@ include #>` Direktive. Weitere Informationen finden Sie unter [T4 include-Direktive](../modeling/t4-include-directive.md).

  Sie können auch Lauf Zeit Textvorlagen in einem separaten Projekt erstellen und diese dann über die Entwurfszeit Vorlage abrufen. Verwenden Sie hierzu die- `<#@ assembly #>` Direktive, um auf das separate Projekt zuzugreifen.

  Erwägen Sie, große Code Blöcke in eine separate Assembly zu verschieben.
  Wenn Sie über umfangreiche Code Blöcke und Klassen Funktionsblöcke verfügen, kann es hilfreich sein, einen Teil dieses Codes in Methoden zu verschieben, die Sie in einem separaten Projekt kompilieren. Sie können die- `<#@ assembly #>` Direktive verwenden, um auf den Code in der Vorlage zuzugreifen. Weitere Informationen finden Sie unter [T4-Assemblydirektive](../modeling/t4-assembly-directive.md).

  Sie können die Methoden in einer abstrakten Klasse platzieren, die von der Vorlage geerbt werden kann. Die abstrakte Klasse muss von Erben <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName> . Weitere Informationen finden Sie unter [T4 Template-Direktive](../modeling/t4-template-directive.md).

  Code generieren, nicht Konfigurationsdateien eine Methode zum Schreiben einer Variablen Anwendung ist das Schreiben von generischem Programmcode, der eine Konfigurationsdatei akzeptiert. Eine auf diese Weise geschriebene Anwendung ist sehr flexibel und kann neu konfiguriert werden, wenn sich die Geschäftsanforderungen ändern, ohne die Anwendung neu zu erstellen. Ein Nachteil dieses Ansatzes ist jedoch, dass die Anwendung weniger gut als eine spezifischere Anwendung durchgeführt wird. Außerdem ist der Programmcode schwieriger zu lesen und zu warten, weil er immer mit den meisten generischen Typen umzugehen ist.

  Im Gegensatz dazu kann eine Anwendung, deren Variablen Teile vor der Kompilierung generiert werden, stark typisiert werden. Dadurch wird es viel einfacher und zuverlässiger, handgeschriebenen Code zu schreiben und ihn in die generierten Teile der Software zu integrieren.

  Um den vollständigen Vorteil der Codegenerierung zu erhalten, versuchen Sie, Programmcode anstelle von Konfigurationsdateien zu generieren.

  Verwenden Sie einen generierten Code Ordner, um die Vorlagen und die generierten Dateien in einem Projektordner mit dem Namen " **generierter Code**" zu platzieren, damit klar ist, dass es sich nicht um Dateien handelt, die direkt bearbeitet werden sollten Wenn Sie benutzerdefinierten Code erstellen, um die generierten Klassen zu überschreiben oder zu hinzuzufügen, platzieren Sie diese Klassen in einem Ordner mit dem Namen **benutzerdefinierter Code**. Die Struktur eines typischen Projekts sieht wie folgt aus:

```
MyProject
   Custom Code
      Class1.cs
      Class2.cs
   Generated Code
      Class1.tt
          Class1.cs
      Class2.tt
          Class2.cs
   AnotherClass.cs

```

## <a name="guidelines-for-run-time-preprocessed-t4-templates"></a>Richtlinien für Lauf Zeit Vorlagen (vorverarbeitete) T4-Vorlagen
 Verschieben von gemeinsamem Material in geerbte Vorlagen Sie können die Vererbung verwenden, um Methoden und Textblöcke zwischen T4-Textvorlagen freizugeben. Weitere Informationen finden Sie unter [T4 Template-Direktive](../modeling/t4-template-directive.md).

 Sie können auch include-Dateien verwenden, die über Lauf Zeit Vorlagen verfügen.

 Verschieben Sie große Textkörper in eine partielle Klasse.
Jede Lauf Zeit Vorlage generiert eine partielle Klassendefinition mit dem gleichen Namen wie die Vorlage. Sie können eine Codedatei schreiben, die eine andere partielle Definition der gleichen Klasse enthält. Sie können der Klasse Methoden, Felder und Konstruktoren auf diese Weise hinzufügen. Diese Member können aus den Code Blöcken in der Vorlage aufgerufen werden.

 Der Vorteil besteht darin, dass der Code einfacher zu schreiben ist, da IntelliSense verfügbar ist. Außerdem können Sie eine bessere Trennung zwischen der Präsentation und der zugrunde liegenden Logik erzielen.

 Beispielsweise in **MyReportText.tt**:

 `The total is: <#= ComputeTotal() #>`

 In **MyReportText-methods.cs**:

 `private string ComputeTotal() { ... }`

 Benutzerdefinierten Code zulassen: Geben Sie Erweiterungs Punkte an, um virtuelle Methoden in zu erstellen \<#+ class feature blocks #> . Dadurch kann eine einzelne Vorlage in vielen Kontexten ohne Änderungen verwendet werden. Anstatt die Vorlage zu ändern, können Sie eine abgeleitete Klasse erstellen, die die minimale zusätzliche Logik bereitstellt. Die abgeleitete Klasse kann entweder regulärer Code sein, oder es kann sich um eine Lauf Zeit Vorlage handeln.

 Beispielsweise in MyStandardRunTimeTemplate.tt:

```
This page is copyright <#= CompanyName() #>.
<#+ protected virtual string CompanyName() { return ""; } #>
```

 Im Code einer Anwendung:

```
class FabrikamTemplate : MyStandardRunTimeTemplate
{
  protected override string CompanyName() { return "Fabrikam"; }
}
...
  string PageToDisplay = new FabrikamTemplate().TextTransform();

```

## <a name="guidelines-for-all-t4-templates"></a>Richtlinien für alle T4-Vorlagen
 Getrennte Datenerfassung aus der Textgenerierung versuchen Sie, die Berechnung und die Textblöcke nicht zu mischen. Verwenden Sie in jeder Textvorlage den ersten, \<# code block #> um Variablen festzulegen und komplexe Berechnungen auszuführen. Vermeiden Sie lange Ausdrücke vom ersten Text Block bis zum Ende der Vorlage oder des ersten Texts \<#+ class feature block #> , und vermeiden Sie Schleifen und Bedingungen, es sei denn, Sie enthalten Textblöcke. Diese Vorgehensweise erleichtert das Lesen und warten der Vorlage.

 Nicht `.tt` für Includedateien verwenden verwenden Sie eine andere Dateinamenerweiterung, z `.ttinclude` . b. für Includedateien. Verwenden `.tt` Sie nur für Dateien, die Sie entweder als Lauf Zeit Vorlage oder als Entwurfszeit-Textvorlagen verarbeiten möchten. In einigen Fällen werden [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] `.tt` Dateien von erkannt, und ihre Eigenschaften werden automatisch für die Verarbeitung festgelegt.

 Starten Sie jede Vorlage als einen Fixed-Prototyp.
Schreiben Sie ein Beispiel für den Code oder Text, den Sie generieren möchten, und stellen Sie sicher, dass es korrekt ist. Ändern Sie dann die Erweiterung in. tt, und fügen Sie Code hinzu, durch den der Inhalt durchlesen des Modells geändert wird.

 Sie sollten typisierte Modelle verwenden.
Obwohl Sie ein XML-oder Datenbankschema für Ihre Modelle erstellen können, kann es hilfreich sein, eine domänenspezifische Sprache (DSL) zu erstellen. Eine DSL hat den Vorteil, dass Sie eine Klasse generiert, die jeden Knoten im Schema darstellt, und Eigenschaften, die die Attribute darstellen. Dies bedeutet, dass Sie im Rahmen des Geschäftsmodells programmieren können. Beispiel:

```
Team Members:
<# foreach (Person p in team.Members)
 { #>
    <#= p.Name #>
<# } #>
```

 Sie sollten Diagramme für Ihre Modelle verwenden.
Viele Modelle werden am effektivsten als Text Tabellen dargestellt und verwaltet, insbesondere wenn Sie sehr groß sind.

 Allerdings ist es für einige Arten von Geschäftsanforderungen wichtig, komplexe Sätze von Beziehungen und Workflows zu verdeutlichen, und Diagramme sind das am besten geeignete Medium. Ein Vorteil eines Diagramms ist, dass es problemlos mit Benutzern und anderen Projekt beteiligten besprochen werden kann. Wenn Sie Code aus einem Modell auf der Ebene der Geschäftsanforderungen erstellen, machen Sie Ihren Code flexibler, wenn sich die Anforderungen ändern.

 UML-Klassen-und Aktivitätsdiagramme können für diese Zwecke häufig angepasst werden. Sie können auch einen eigenen Diagrammtyp als domänenspezifische Sprache (DSL) entwerfen. Code kann sowohl von UML als auch von DSLs generiert werden. Weitere Informationen finden Sie unter [analysieren und modellieren der Architektur](../modeling/analyze-and-model-your-architecture.md) und [analysieren und modellieren der Architektur](../modeling/analyze-and-model-your-architecture.md).

## <a name="see-also"></a>Weitere Informationen
 [Code Generierung zur Entwurfszeit mithilfe von T4-Textvorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md) [Lauf Zeit Textgenerierung mit T4-Textvorlagen](../modeling/run-time-text-generation-with-t4-text-templates.md)
