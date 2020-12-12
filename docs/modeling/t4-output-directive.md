---
title: T4 Output-Direktive
description: Erfahren Sie, dass in Visual Studio-Textvorlagen die Output-Direktive verwendet wird, um die Dateinamenerweiterung und die Codierung der transformierten Datei zu definieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9849a326549aa534d9cd558337b825b7e0b8d1f
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363639"
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
 Gibt die zu verwendende Codierung bei der Generierung der Ausgabedatei an. Zum Beispiel:

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
