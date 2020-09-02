---
title: Zugreifen auf Visual Studio 2015 oder andere Hosts über eine Text Vorlage | Microsoft-Dokumentation
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: a68886da-7416-4785-8145-3796bb382cba
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0e8cedc66d6b52f80239364a3e51b73e93a69aa4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655323"
---
# <a name="accessing-visual-studio-or-other-hosts-from-a-text-template"></a>Zugreifen auf Visual Studio oder andere Hosts von einer Textvorlage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In einer Textvorlage können Sie Methoden und Eigenschaften verwenden, die vom Host verfügbar gemacht werden, der die Vorlage ausführt, z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . b..

 Dies gilt für reguläre Textvorlagen, nicht für vorverarbeitete Textvorlagen.

## <a name="obtaining-access-to-the-host"></a>Zugriff auf den Host erhalten

`hostspecific="true"`In der- `template` Direktive festgelegt. Auf diese Weise können Sie mit  `this.Host` dem Typ [itexttemplatingenginehost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))verwenden. Dieser Typ enthält Member, die Sie verwenden können, um z. b. Dateinamen aufzulösen und Fehler zu protokollieren.

### <a name="resolving-file-names"></a>Auflösen von Dateinamen
 Um den vollständigen Pfad einer Datei relativ zur Textvorlage zu finden, verwenden Sie diese. Host. resolvepath ().

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.IO" #>
<#
 // Find a path within the same project as the text template:
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));
#>
Content of myFile is:
<#= myFile #>

```

### <a name="displaying-error-messages"></a>Anzeigen von Fehlermeldungen
 In diesem Beispiel werden Nachrichten protokolliert, wenn Sie die Vorlage transformieren. Wenn der Host ist [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , werden diese dem Fehler Fenster hinzugefügt.

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.CodeDom.Compiler" #>
<#
  string message = "test message";
  this.Host.LogErrors(new CompilerErrorCollection()
    { new CompilerError(
       this.Host.TemplateFile, // Identify the source of the error.
       0, 0, "0",   // Line, column, error ID.
       message) }); // Message displayed in error window.
#>

```

## <a name="using-the-visual-studio-api"></a>Verwenden der Visual Studio-API
 Wenn Sie in eine Textvorlage ausführen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , können Sie verwenden, `this.Host` um auf die von bereitgestellten Dienste [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] und alle Pakete oder Erweiterungen zuzugreifen, die geladen werden.

 Legen Sie hostspecific = "true" fest `this.Host` , und wandeln Sie in um <xref:System.IServiceProvider> .

 In diesem Beispiel wird die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] API, <xref:EnvDTE.DTE> , als Dienst abgerufen:

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="EnvDTE" #>
<#
 IServiceProvider serviceProvider = (IServiceProvider)this.Host;
 DTE dte = serviceProvider.GetService(typeof(DTE)) as DTE;
#>
Number of projects in this solution: <#=  dte.Solution.Projects.Count #>

```

## <a name="using-hostspecific-with-template-inheritance"></a>Verwenden von hostspecific mit Vorlagen Vererbung
 Geben `hostspecific="trueFromBase"` Sie an, wenn Sie auch das `inherits` -Attribut verwenden und wenn Sie von einer Vorlage erben, die angibt `hostspecific="true"` . Dadurch wird eine Compilerwarnung vermieden, die besagt, dass die Eigenschaft `Host` zweimal deklariert wurde.
