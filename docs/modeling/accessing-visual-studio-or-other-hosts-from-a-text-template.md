---
title: Zugreifen auf Visual Studio oder andere Hosts von einer Textvorlage
description: Erfahren Sie, wie Sie Methoden und Eigenschaften in einer Textvorlage verwenden können, die vom Host verfügbar gemacht werden, von dem die Vorlage ausgeführt wird.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4c0f19f96ee5f6879ccc3328c29d0e1fa1d2a6d0
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362248"
---
# <a name="access-visual-studio-or-other-hosts-from-a-text-template"></a>Zugreifen auf Visual Studio oder andere Hosts über eine Textvorlage

In einer Textvorlage können Sie Methoden und Eigenschaften verwenden, die vom Host verfügbar gemacht werden, von dem die Vorlage ausgeführt wird. Visual Studio ist ein Beispiel für einen Host.

> [!NOTE]
> Sie können Host Methoden und-Eigenschaften in regulären Textvorlagen verwenden, aber nicht in *vorverarbeiteten* Textvorlagen.

## <a name="obtain-access-to-the-host"></a>Zugriff auf den Host erhalten

Um auf den Host zuzugreifen, legen Sie `hostspecific="true"` in der- `template` Direktive fest. Nun können Sie mit `this.Host` dem Typ [itexttemplatingenginehost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))verwenden. Der [itexttemplatingenginehost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) -Typ enthält Member, die Sie zum Auflösen von Dateinamen und Protokoll Fehlern verwenden können, z. b..

### <a name="resolve-file-names"></a>Auflösen von Dateinamen

Verwenden Sie, um den vollständigen Pfad einer Datei relativ zur Textvorlage zu finden `this.Host.ResolvePath()` .

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

### <a name="display-error-messages"></a>Anzeigen von Fehlermeldungen

In diesem Beispiel werden Nachrichten protokolliert, wenn Sie die Vorlage transformieren. Wenn es sich bei dem Host um Visual Studio handelt, werden die Fehler der **Fehlerliste** hinzugefügt.

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

## <a name="use-the-visual-studio-api"></a>Verwenden der Visual Studio-API

Wenn Sie eine Textvorlage in Visual Studio ausführen, können Sie verwenden, `this.Host` um auf die von Visual Studio bereitgestellten Dienste und alle Pakete oder Erweiterungen zuzugreifen, die geladen werden.

Legen Sie hostspecific = "true" fest `this.Host` , und wandeln Sie in um <xref:System.IServiceProvider> .

In diesem Beispiel wird die Visual Studio-API, <xref:EnvDTE.DTE> , als Dienst abgerufen:

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

## <a name="use-hostspecific-with-template-inheritance"></a>Verwenden von hostspecific mit Vorlagen Vererbung

Geben `hostspecific="trueFromBase"` Sie an, wenn Sie auch das `inherits` -Attribut verwenden und wenn Sie von einer Vorlage erben, die angibt `hostspecific="true"` . Wenn Sie dies nicht tun, erhalten Sie möglicherweise eine Compilerwarnung, dass die Eigenschaft `Host` zweimal deklariert wurde.
