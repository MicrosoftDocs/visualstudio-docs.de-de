---
title: So wird es gemacht... mit Text Vorlagen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: d1ac2509-0479-47eb-809c-1f171245d0b6
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c55c7a277d3f38b36367008ae6393f58c9c9a2c2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671615"
---
# <a name="how-to--with-text-templates"></a>Gewusst wie: ... mit Textvorlagen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Textvorlagen in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bieten eine nützliche Möglichkeit zum Erstellen von Text beliebiger Art. Sie können Textvorlagen verwenden, um zur Laufzeit Text als Teil der Anwendung zu generieren, und zur Entwurfszeit, um einen Teil des Projekt Codes zu generieren. In diesem Thema werden die am häufigsten gestellten "Gewusst wie...?" zusammengefasst. Anfragen.

 In diesem Thema sind mehrere Antworten, denen Aufzählungs Möglichkeiten vorangestellt sind, alternative Vorschläge.

 Eine allgemeine Einführung in Textvorlagen finden Sie unter [Code Generierung und T4-Textvorlagen](../modeling/code-generation-and-t4-text-templates.md).

## <a name="how-to-"></a>Vorgehensweisen

### <a name="generate-part-of-my-application-code"></a>Einen Teil des Anwendungs Codes generieren
 Ich verfüge über eine Konfiguration oder ein *Modell* in einer Datei oder einer Datenbank. Ein oder mehrere Teile des Codes hängen von diesem Modell ab.

- Generieren einiger Code Dateien aus Textvorlagen. Weitere Informationen finden Sie unter [Entwurfszeit Code Generierung mithilfe von T4-Text Vorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md) und [Was ist die beste Möglichkeit, um mit dem Schreiben einer Vorlage zu beginnen?](#starting).

### <a name="generate-files-at-run-time-passing-data-into-the-template"></a>Generieren von Dateien zur Laufzeit und übergeben von Daten an die Vorlage
 Zur Laufzeit generiert meine Anwendung Textdateien, z. b. Berichte, die eine Mischung aus Standardtext und-Daten enthalten. Ich möchte vermeiden, Hunderte von Anweisungen zu schreiben `write` .

- Fügen Sie dem Projekt eine Lauf Zeit Textvorlage hinzu. Mit dieser Vorlage wird eine Klasse in Ihrem Code erstellt, die Sie instanziieren und zum Generieren von Text verwenden können. Sie können Daten in den Konstruktorparametern an ihn übergeben. Weitere Informationen finden Sie unter [Lauf Zeit Generierung von Text mit T4-Textvorlagen](../modeling/run-time-text-generation-with-t4-text-templates.md).

- Wenn Sie aus Vorlagen generieren möchten, die nur zur Laufzeit verfügbar sind, können Sie Standardtext Vorlagen verwenden. Wenn Sie eine Erweiterung schreiben [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , können Sie den Textvorlagen Dienst aufrufen. Weitere Informationen finden Sie unter [Aufrufen von Text Transformation in einer vs-Erweiterung](../modeling/invoking-text-transformation-in-a-vs-extension.md). In anderen Kontexten können Sie die Textvorlagen-Engine verwenden. Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>.

     Verwenden Sie die- \<#@parameter#> Direktive, um Parameter an diese Vorlagen zu übergeben. Weitere Informationen finden Sie unter [T4-Parameter Direktive](../modeling/t4-parameter-directive.md).

### <a name="read-another-project-file-from-a-template"></a>Lesen einer anderen Projektdatei aus einer Vorlage
 So lesen Sie eine Datei aus demselben [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Projekt wie die Vorlage:

- Fügen Sie `hostSpecific="true"` in die `<#@template#>`-Anweisung ein.

     Verwenden Sie in Ihrem Code, `this.Host.ResolvePath(filename)` um den vollständigen Pfad der Datei abzurufen.

### <a name="invoke-methods-from-a-template"></a>Aufrufen von Methoden aus einer Vorlage
 Wenn die Methoden bereits vorhanden sind, z. b. in Standard [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Klassen:

- Verwenden Sie die \<#@assembly#> -Anweisung, um die Assembly zu laden, und verwenden \<#@import#> Sie, um den Namespace Kontext festzulegen. Weitere Informationen finden Sie unter [T4 Import-Direktive](../modeling/t4-import-directive.md).

   Wenn Sie häufig denselben Satz von Assemblys und Import Direktiven verwenden, sollten Sie ggf. einen Direktivenprozessor schreiben. In jeder Vorlage können Sie den Direktivenprozessor aufrufen, der die Assemblys und die Modelldateien laden und den Namespace Kontext festlegen kann. Weitere Informationen finden Sie unter [Erstellen von benutzerdefinierten T4](../modeling/creating-custom-t4-text-template-directive-processors.md)-Anweisungs Prozessoren für Text Vorlagen.

  Wenn Sie die Methoden selbst schreiben:

- Wenn Sie eine Lauf Zeit Textvorlage schreiben, schreiben Sie eine partielle Klassendefinition, die den gleichen Namen wie Ihre Lauf Zeit Textvorlage hat. Fügen Sie dieser Klasse die zusätzlichen Methoden hinzu.

- Schreiben Sie einen Klassen Funktions Kontroll Block `<#+ ... #>` , in dem Sie Methoden, Eigenschaften und private Klassen deklarieren können. Wenn die Textvorlage kompiliert wird, wird Sie in eine Klasse transformiert. Die Standard Kontroll Blöcke `<#...#>` und-Text werden in eine einzelne Methode transformiert, und Klassen Funktionsblöcke werden als separate Member eingefügt. Weitere Informationen finden Sie unter [Text Vorlagen-Kontroll Blöcke](../modeling/text-template-control-blocks.md).

   Als Klassen Funktionen definierte Methoden können auch eingebettete Textblöcke einschließen.

   Erwägen Sie, Klassen Features in einer separaten Datei zu platzieren, die Sie `<#@include#>` in eine oder mehrere Vorlagen Dateien einfügen können.

- Schreiben Sie die Methoden in einer separaten Assembly (Klassenbibliothek), und nennen Sie Sie aus ihrer Vorlage. Verwenden `<#@assembly#>` Sie die-Direktive, um die Assembly zu laden und `<#@import#>` den Namespace Kontext festzulegen. Beachten Sie, dass Sie zum erneuten Erstellen der Assembly während des Debuggens möglicherweise beendet und neu gestartet werden müssen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Weitere Informationen finden Sie unter [T4-Text Vorlagen Direktiven](../modeling/t4-text-template-directives.md).

### <a name="generate-many-files-from-one-model-schema"></a>Generieren von vielen Dateien aus einem Modell Schema
 Wenn Sie häufig Dateien aus Modellen generieren, die das gleiche XML-oder Datenbankschema aufweisen:

- Schreiben Sie einen Direktivenprozessor in Erwägung. Dies ermöglicht es Ihnen, mehrere Assemblyanweisungen und Import-Anweisungen in jeder Vorlage durch eine einzelne benutzerdefinierte Direktive zu ersetzen. Der Direktivenprozessor kann auch die Modelldatei laden und analysieren. Weitere Informationen finden Sie unter [Erstellen von benutzerdefinierten T4](../modeling/creating-custom-t4-text-template-directive-processors.md)-Anweisungs Prozessoren für Text Vorlagen.

### <a name="generate-files-from-a-complex-model"></a>Generieren von Dateien aus einem komplexen Modell

- Es empfiehlt sich, eine domänenspezifische Sprache (DSL) zu erstellen, um das Modell darzustellen. Dies erleichtert das Schreiben von Vorlagen, da Sie Typen und Eigenschaften verwenden, die die Namen der Elemente in Ihrem Modell widerspiegeln. Es ist nicht erforderlich, die Datei zu analysieren oder XML-Knoten zu navigieren. Beispiel:

     `foreach (Book book in this.Library) { ... }`

     Weitere Informationen finden Sie unter [Einstieg in domänenspezifische Sprachen](../modeling/getting-started-with-domain-specific-languages.md) und [Erstellen von Code aus einer domänenspezifischen Sprache](../modeling/generating-code-from-a-domain-specific-language.md).

- Sie sollten Code aus einem UML-Modell erstellen. Der Code muss den UML nicht direkt widerspiegeln. Beispielsweise ist es nicht erforderlich, eine Klasse für jede Klasse im UML-Modell zu generieren. Stattdessen können Sie das UML-Klassendiagramm verwenden, um eine Website darzustellen, und eine Webseite aus jeder UML-Klasse generieren. Wählen Sie den Diagrammtyp, der Ihren Anforderungen am ehesten entspricht. Wählen Sie z. b. Aktivitätsdiagramme aus, um einen beliebigen Typ von Workflow darzustellen. Sie können Stereotype definieren, um den einzelnen Elementtypen Informationen für Ihre Anwendung hinzuzufügen.

     Durch die Erstellung aus einem UML-Modell können Sie das Modell in einem diagrammatischen Format zeichnen und bearbeiten, ohne dass Sie einen eigenen Diagrammtyp entwerfen müssen, wie es bei einer DSL der Fall wäre.

     Weitere Informationen finden Sie unter [Erstellen von Modellen für Ihre APP](../modeling/create-models-for-your-app.md) und [Generieren von Dateien aus einem UML-Modell](../modeling/generate-files-from-a-uml-model.md).

### <a name="get-data-from-vsprvs"></a>Daten erhalten von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]
 Wenn Sie in bereitgestellte Dienste verwenden möchten [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , legen Sie das `hostSpecific` -Attribut fest, und laden Sie die `EnvDTE` Assembly. Beispiel:

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#
  IServiceProvider serviceProvider = (IServiceProvider)this.Host;
  EnvDTE.DTE dte = (EnvDTE.DTE) serviceProvider.GetService(typeof(EnvDTE.DTE));
#>

Number of projects in this VS solution:  <#= dte.Solution.Projects.Count #>

```

### <a name="execute-text-templates-in-the-build-process"></a>Ausführen von Textvorlagen im Buildprozess

- Weitere Informationen finden Sie unter [Code Generierung in einem Buildprozess](../modeling/code-generation-in-a-build-process.md).

## <a name="more-general-questions"></a>Allgemeinere Fragen

### <a name="what-is-the-best-way-to-start-writing-a-text-template"></a><a name="starting"></a> Was ist die beste Möglichkeit, eine Textvorlage zu schreiben?

1. Schreiben Sie ein bestimmtes Beispiel für die generierte Datei.

2. Fügen Sie Sie in eine Textvorlage ein, indem Sie die `<#@template #>` -Direktive und die Anweisungen und den Code einfügen, die zum Laden der Eingabedatei oder des Modells erforderlich sind.

3. Progressiv ersetzt Teile der Datei durch Ausdrucks-und Code Blöcke.

### <a name="what-is-a-model"></a>Was ist ein „Modell“?

- Die von Ihrer Vorlage gelesene Eingabe. Sie kann sich in einer Datei oder in einer Datenbank befinden. Dabei kann es sich um XML, eine Visio-Zeichnung oder eine domänenspezifische Sprache (DSL) oder ein UML-Modell oder um nur-Text-Zeichen handeln. Sie kann auf mehrere Dateien verteilt werden. In der Regel liest mehr als eine Vorlage ein Modell.

     Der Begriff "Modell" impliziert, dass er einen Aspekt Ihres Geschäfts direkt als den generierten Programmcode oder andere Dateien darstellt. Beispielsweise könnte Sie den Plan eines Kommunikationsnetzwerks darstellen, das von der generierten Software überwacht wird.

### <a name="what-is-the-benefit-of-using-text-templates"></a>Was ist der Vorteil der Verwendung von Textvorlagen?
 In der Regel generieren Sie mehrere Code oder andere Dateien aus einem Modell. Das Modell stellt die Anforderungen mehr direkt als der generierte Code dar. Es lässt Implementierungsdetails aus und wird in Bezug auf die Anforderungen und nicht auf den Code geschrieben. Wenn die Anforderungen – wie in der Regel – geändert werden, können Sie das Modell leichter und zuverlässiger aktualisieren als die verschiedenen Teile des Programmcodes.

 Die Code Generierung ist daher ein wertvolles Tool aus der Perspektive von Agile-Entwicklungsmethoden.

### <a name="what-best-practices-are-there-for-text-templates"></a>Was sind die bewährten Methoden für Textvorlagen?

- Weitere Informationen finden Sie unter [Richtlinien zum Schreiben von T4-Text Vorlagen](../modeling/guidelines-for-writing-t4-text-templates.md).

### <a name="what-is-t4"></a>Was ist "T4"?

- Ein anderer Name für die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Textvorlagen Funktionen, die hier beschrieben werden. Die vorherige Version, die nicht veröffentlicht wurde, war eine Abkürzung für die Text Vorlagen Transformation.
