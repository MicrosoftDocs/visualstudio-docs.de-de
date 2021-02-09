---
title: T4-Textvorlagendirektiven
description: Hier finden Sie Informationen zu T4-Test Vorlagen Direktiven und deren Bereitstellung von Anweisungen für das Textvorlagen-Transformationsmodul.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3ba13cbd31d41e656533aa5b13cf2a09503e58e8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924599"
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
