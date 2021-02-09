---
title: T4 Output-Direktive
description: Erfahren Sie, dass in Visual Studio-Textvorlagen die Output-Direktive verwendet wird, um die Dateinamenerweiterung und die Codierung der transformierten Datei zu definieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 58e7c255d767e9b35764e03a76f9cda516dbe606
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899602"
---
# <a name="t4-output-directive"></a>T4 Output-Direktive

In Visual Studio-Textvorlagen `output` wird die-Direktive verwendet, um die Dateinamenerweiterung und die Codierung der transformierten Datei zu definieren.

 Wenn Ihr Visual Studio-Projekt beispielsweise eine Vorlagen Datei mit dem Namen **MyTemplate.tt** enthält, die die folgende Anweisung enthält:

 `<#@output extension=".cs"#>`

 dann generiert Visual Studio eine Datei mit dem Namen **MyTemplate.cs** .

 Die `output`-Anweisung ist in einer Laufzeitvorlage (vorverarbeiteten Vorlage) nicht erforderlich. Stattdessen erhält die Anwendung die generierte Zeichenfolge durch Aufruf von `TextTransform()`. Weitere Informationen finden Sie unter [Laufzeittextgenerierung mithilfe von T4-Textvorlagen](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="using-the-output-directive"></a>Verwenden der Ausgabeanweisung

```
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>
```

 In jeder Textvorlage sollte es nicht mehr als eine `output`-Anweisung geben.

## <a name="extension-attribute"></a>Erweiterungs Attribut
 Gibt die Dateierweiterung der generierten Textausgabedatei an.

 Der Standardwert ist " **. cs".**

 Beispiele: `<#@ output extension=".txt" #>`

 `<#@ output extension=".htm" #>`

 `<#@ output extension=".cs" #>`

 `<#@ output extension=".vb" #>`

 Zulässige Werte: eine beliebige gültige Dateinamenerweiterung.

## <a name="encoding-attribute"></a>Encoding-Attribut
 Gibt die zu verwendende Codierung bei der Generierung der Ausgabedatei an. Beispiel:

 `<#@ output encoding="utf-8"#>`

 Der Standardwert ist die Codierung, die von der Textvorlagendatei verwendet wird.

 Zulässige Werte: `us-ascii`

 `utf-16BE`

 `utf-16`

 `utf-8`

 `utf-7`

 `utf-32`

 `0` (System Standard)

 Im Allgemeinen können Sie die WebName-Zeichenfolge oder die CodePage-Zahl aller von <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName> zurückgegebenen Codierungen verwenden.
