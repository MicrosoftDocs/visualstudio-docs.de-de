---
title: T4-Textvorlagendirektiven
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, import directive
- text templates, include directive
- text templates, assembly directive
- text templates, output directive
- text templates, directives
- text templates, template directive
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f7ceb5139ff133a0005efafd5dc96f20e22b73cf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75591826"
---
# <a name="t4-text-template-directives"></a>T4-Textvorlagendirektiven

Durch Direktiven werden Anweisungen für die Textvorlagen-Transformations-Enginebereitgestellt.

Die Syntax von Anweisungen lautet wie folgt:

```
<#@ DirectiveName [AttributeName = "AttributeValue"] ... #>
```

Alle Attributwerte müssen in doppelte Anführungszeichen eingeschlossen werden. Wenn der Wert selbst Anführungszeichen enthält, müssen diese mit dem Escapezeichen "\" versehen werden.

Anweisungen sind in der Regel die ersten Elemente in einer Vorlagendatei oder einer eingeschlossenen Datei. Platzieren Sie sie nicht in einem Codeblock `<#...#>` und nicht nach einem Klassenfunktionsblock `<#+...#>`.

[T4-Vorlagendirektive](../modeling/t4-template-directive.md)

```
<#@ template [language="VB"] [hostspecific="true|TrueFromBase"] [debug="true"] [inherits="templateBaseClass"] [culture="code"] [compilerOptions="options"] [visibility="internal"] [linePragmas="false"] #>
```

[T4-Parameter-Direktive](../modeling/t4-parameter-directive.md)

```
<#@ parameter type="Full.TypeName" name="ParameterName" #>
```

[T4 Output-Direktive](../modeling/t4-output-directive.md)

```
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>
```

[T4-Assemblydirektive](../modeling/t4-assembly-directive.md)

```
<#@ assembly name="[assembly strong name|assembly file name]" #>
```

[T4-Import-Direktive](../modeling/t4-import-directive.md)

```
<#@ import namespace="namespace" #>
```

[T4-Include-Direktive](../modeling/t4-include-directive.md)

```
<#@ include file="filePath" #>
```

[T4 CleanUpBehavior-Direktive](../modeling/t4-cleanupbehavior-directive.md)

```
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>
```

Darüber hinaus können Sie eigene Direktiven erstellen. Weitere Informationen finden Sie unter [Erstellen von benutzerdefinierten T4](../modeling/creating-custom-t4-text-template-directive-processors.md)-Anweisungs Prozessoren für Text Vorlagen. Wenn Sie mithilfe des Visualisierungs- und Modellierungs-SDKs eine domänenspezifische Sprache (DSL) erstellen, wird ein Anweisungsprozessor als Teil der DSL generiert.
