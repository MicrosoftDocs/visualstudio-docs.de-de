---
title: MSBuild-Bedingungen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, conditions
- conditions [MSBuild]
ms.assetid: 9d7aa308-b667-48ed-b4c9-a61e49eb0a85
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 71bb48290d0eb64f91b918d22624755c2edb6153
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "74303118"
---
# <a name="msbuild-conditions"></a>MSBuild-Bedingungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] unterstützt bestimmte Bedingungen, die angewendet werden können, wenn ein `Condition`-Attribut zulässig ist. Diese Bedingungen sind in der folgenden Tabelle angegeben.  
  
|Bedingung|Beschreibung|  
|---------------|-----------------|  
|'`stringA`' == '`stringB`'|Ergibt `true`, wenn `stringA` gleich `stringB`.<br /><br /> Zum Beispiel:<br /><br /> `Condition="'$(CONFIG)'=='DEBUG'"`<br /><br /> Für einfache alphanumerische Zeichenfolgen und boolesche Werte sind keine einfachen Anführungszeichen erforderlich. Allerdings sind einfache Anführungszeichen für leere Werte erforderlich.|  
|'`stringA`' != '`stringB`'|Ergibt `true`, wenn `stringA` ungleich `stringB`.<br /><br /> Zum Beispiel:<br /><br /> `Condition="'$(CONFIG)'!='DEBUG'"`<br /><br /> Für einfache alphanumerische Zeichenfolgen und boolesche Werte sind keine einfachen Anführungszeichen erforderlich. Allerdings sind einfache Anführungszeichen für leere Werte erforderlich.|  
|\<, >, \<=, >=|Wertet die numerischen Werte der Operanden aus. Gibt `true` aus, wenn die relationale Auswertung TRUE ist. Die Auswertung von Operanden muss eine dezimale oder hexadezimale Zahl ergeben. Hexadezimale Zahlen müssen mit „0x“ beginnen. **Hinweis**:  Im XML müssen die Zeichen `<` und `>` mit Escapezeichen versehen werden. Das Symbol `<` wird als `<` dargestellt. Das Symbol `>` wird als `>` dargestellt.|  
|Exists('`stringA`')|Ergibt `true`, wenn eine Datei oder ein Ordner mit dem Namen `stringA` vorhanden ist.<br /><br /> Zum Beispiel:<br /><br /> `Condition="!Exists('$(builtdir)')"`<br /><br /> Für einfache alphanumerische Zeichenfolgen und boolesche Werte sind keine einfachen Anführungszeichen erforderlich. Allerdings sind einfache Anführungszeichen für leere Werte erforderlich.|  
|HasTrailingSlash('`stringA`')|Ergibt `true`, wenn die angegebene Zeichenfolge entweder einen nachgestellten umgekehrten Schrägstrich (\\) oder einen Schrägstrich (/) enthält.<br /><br /> Zum Beispiel:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> Für einfache alphanumerische Zeichenfolgen und boolesche Werte sind keine einfachen Anführungszeichen erforderlich. Allerdings sind einfache Anführungszeichen für leere Werte erforderlich.|  
|!|Ergibt `true`, wenn die Auswertung des Operanden `false` ergibt.|  
|Und|Ergibt `true`, wenn die Auswertung beider Operanden `true` ergibt.|  
|Oder|Ergibt `true`, wenn die Auswertung von mindestens einem Operanden `true` ergibt.|  
|()|Gruppierungsmechanismus, dessen Auswertung `true` ergibt, wenn die Auswertung der darin enthaltenen Ausdrücke `true` ergibt.|  
|$if$ ( %expression% ), $else$, $endif$|Überprüft, ob das angegebene `%expression%` dem Zeichenfolgenwert des übergebenen benutzerdefinierten Vorlagenparameters entspricht. Wenn die Auswertung der `$if$`-Bedingung `true` ergibt, werden die jeweiligen Anweisungen ausgeführt. Andernfalls wird die `$else$`-Bedingung überprüft. Wenn die Auswertung der `$else$`-Bedingung `true` ergibt, werden die jeweiligen Anweisungen ausgeführt. Andernfalls beendet die `$endif$`-Bedingung die Auswertung des Ausdrucks.<br /><br /> Beispiele für die Verwendung finden Sie unter [Visual Studio-Projekt-/Elementvorlagen-Parameter Logik](https://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic).|  
  
## <a name="see-also"></a>Weitere Informationen  
 [MSBuild-Referenz](../msbuild/msbuild-reference.md)   
 [Bedingte Konstrukte](../msbuild/msbuild-conditional-constructs.md)   
 [Exemplarische Vorgehensweise: Erstellen einer MSBuild-Projektdatei von Grund auf](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
