---
title: Verwenden von Escapesequenzen in Textvorlagen
description: Erfahren Sie, wie Sie mit Escapesequenzen in Textvorlagen Textvorlagen Tags generieren und Steuerzeichen und Anführungszeichen nur in c#-Code mit Escapezeichen versehen können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 126fe3f4e42c9c6cf0b75bf740e1e7e2c4b269ea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924343"
---
# <a name="use-escape-sequences-in-text-templates"></a>Verwenden von Escapesequenzen in Textvorlagen

Mithilfe von Escapesequenzen in Textvorlagen können Sie Textvorlagen Tags generieren und (nur in c#-Code) Steuerzeichen und Anführungszeichen mit Escapezeichen versehen.

Um öffnende und schließende Tags für einen standardmäßigen Codeblock in der Ausgabedatei zu drucken, versehen Sie die Tags wie folgt:

```
\<# ... \#>
```

Dies können Sie mit anderen Textvorlagen Direktiven und Code Block Tags tun.

Wenn ein TextBlock Zeichen folgen enthält, die zum Escapezeichen von Textvorlagen Tags verwendet werden, können Sie die folgenden Escapesequenzen verwenden:

- Wenn einem Text Template-Tag eine gerade Anzahl von Escapezeichen () vorangestellt ist, \\ enthält der Vorlagen Parser die Hälfte der Escapezeichen und schließt die Sequenz als Textvorlagen-Tag ein. Wenn die Textvorlage beispielsweise vier Escapezeichen enthält, werden \\ in der generierten Datei zwei ""-Zeichen angezeigt.

- Wenn dem Text Template-Tag eine ungerade Anzahl von Escapezeichen () vorangestellt ist \\ , enthält der Vorlagen Parser die Hälfte der " \\ "-Zeichen sowie das Tag selbst ( \<# or #> ). Das-Tag wird nicht als Textvorlagen-Tag betrachtet.

- Wenn ein \\ Escapezeichen () an einer anderen Stelle in einer anderen Sequenz als dem Escapezeichen für ein Steuerzeichen oder ein Anführungszeichen (nur in c#) angezeigt wird, wird das Zeichen direkt ausgegeben.

## <a name="see-also"></a>Weitere Informationen

- [Gewusst wie: Generieren von Vorlagen aus Vorlagen mithilfe von Escapesequenzen](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)
