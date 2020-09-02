---
title: Item-Element (MSBuild) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Item Element [MSBuild]
- <Item> Element [MSBuild]
ms.assetid: dcef5f91-0613-4bfc-8ee9-d7004bb6d3a9
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cc3d606bb890b5f95089bfc7b1e83b2d34cd56ba
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192606"
---
# <a name="item-element-msbuild"></a>Item-Element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Enthält ein benutzerdefiniertes Element und die zugehörigen Metadaten. Jedes Element, das in einem [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Projekt verwendet wird, muss als untergeordnetes Element eines `ItemGroup` Elements angegeben werden.  
  
 \<Project>  
 \<ItemGroup>  
 \<Item>  
  
## <a name="syntax"></a>Syntax  
  
```  
<Item Include="*.cs"  
        Exclude="MyFile.cs"  
        Remove="RemoveFile.cs"  
        Condition="'String A'=='String B'" >  
    <ItemMetadata1>...</ItemMetadata1>  
    <ItemMetadata2>...</ItemMetadata2>  
</Item>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|attribute|Beschreibung|  
|---------------|-----------------|  
|`Include`|Erforderliches Attribut.<br /><br /> Die Datei oder der Platzhalter, die bzw. der in die Liste der Elemente eingeschlossen werden soll.|  
|`Exclude`|Optionales Attribut.<br /><br /> Die Datei oder der Platzhalter, die bzw. der aus der Liste der Elemente ausgeschlossen werden soll.|  
|`Condition`|Optionales Attribut.<br /><br /> Die auszuwertende Bedingung. Weitere Informationen finden Sie unter [Conditions](../msbuild/msbuild-conditions.md) (MSBuild-Bedingungen).|  
|`Remove`|Optionales Attribut.<br /><br /> Die Datei oder der Platzhalter, die bzw. der aus der Liste der Elemente entfernt werden soll.<br /><br /> Dieses Attribut ist nur gültig, wenn es für ein Element in einer `ItemGroup` angegeben wird, die sich in einem `Target` befindet.|  
|`KeepMetadata`|Optionales Attribut.<br /><br /> Die Metadaten für die Quellelemente, die den Zielelementen hinzugefügt werden sollen. Nur die Metadaten, deren Namen in der durch Semikolon getrennten Liste angegeben werden, werden von einem Quellelement in ein Zielelement übertragen. Weitere Informationen finden Sie unter [Elemente](../msbuild/msbuild-items.md).<br /><br /> Dieses Attribut ist nur gültig, wenn es für ein Element in einer `ItemGroup` angegeben wird, die sich in einem `Target` befindet.|  
|`RemoveMetadata`|Optionales Attribut.<br /><br /> Die Metadaten für die Quellelemente, die nicht an der Zielelemente übertragen werden sollen. Alle Metadaten werden aus einem Quellelement in ein Zielelement mit Ausnahme von Metadaten übertragen, deren Namen in der durch Semikolons getrennten Liste der Namen enthalten sind. Weitere Informationen finden Sie unter [Elemente](../msbuild/msbuild-items.md).<br /><br /> Dieses Attribut ist nur gültig, wenn es für ein Element in einer `ItemGroup` angegeben wird, die sich in einem `Target` befindet.|  
|`KeepDuplicates`|Optionales Attribut.<br /><br /> Gibt an, ob ein Element der Zielgruppe hinzugefügt werden soll, wenn es sich um ein exaktes Duplikat eines vorhandenen Elements handelt. Wenn das Quell- und Zielelement den gleichen `Include`-Wert aber unterschiedliche Metadaten aufweisen, wird das Element auch dann hinzugefügt, wenn `KeepDuplicates` auf `false` festgelegt ist. Weitere Informationen finden Sie unter [Elemente](../msbuild/msbuild-items.md).<br /><br /> Dieses Attribut ist nur gültig, wenn es für ein Element in einer `ItemGroup` angegeben wird, die sich in einem `Target` befindet.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[ItemMetadata](../msbuild/itemmetadata-element-msbuild.md)|Ein benutzerdefinierter Elementmetadatenschlüssel, der den Elementmetadatenwert enthält. Es kann keine oder mehrere `ItemMetadata`-Elemente in einem Element geben.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Grouping-Element für Elemente.|  
  
## <a name="remarks"></a>Hinweise  
 `Item`-Elemente definieren Eingaben ins Buildsystem und sind basierend auf ihren benutzerdefinierten Auflistungsnamen in Elementauflistungen gruppiert. Diese Elementtypen können als Parameter für [Aufgaben](../msbuild/msbuild-tasks.md) verwendet werden, die mithilfe der einzelnen Elemente in den Auflistungen die Schritte des Buildprozesses ausführen. Weitere Informationen finden Sie unter [Elemente](../msbuild/msbuild-items.md).  
  
 Mithilfe der Notation `@(` *MyType* `)` kann eine Auflistung von Elementen vom Typ *MyType* in eine durch Semikolons getrennte Liste von Zeichen folgen erweitert und an einen Parameter übergeben werden. Wenn der Parameter vom Typ `string` ist, entspricht der Wert des Parameters der Liste der Elemente, die durch Semikolons getrennt sind. Wenn der Parameter ein Array von Zeichenfolgen ist (`string[]`), werden die einzelnen Elemente ins Array basierend auf der Position der Semikolons eingefügt. Ist der Task-Parameter vom Typ <xref:Microsoft.Build.Framework.ITaskItem>`[]`, entspricht der Wert dem Inhalt der Elementauflistung einschließlich ggf. angefügter Metadaten. Verwenden Sie die Syntax `@(` *MyType* `, '` *Separator*, um die einzelnen Elemente mit einem anderen Zeichen als einem Semikolon zu begrenzen `')` .  
  
 Die [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Engine kann Platzhalter wie `*` und `?` sowie rekursive Platzhalter wie `/**/*.cs` auswerten. Weitere Informationen finden Sie unter [Elemente](../msbuild/msbuild-items.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, wie zwei Elemente vom Typ `CSFile` deklariert werden. Das zweite deklarierte Element enthält Metadaten, für die `MyMetadata` auf `HelloWorld` festgelegt ist.  
  
```  
<ItemGroup>  
    <CSFile Include="engine.cs; form.cs" />  
    <CSFile Include="main.cs" >  
        <MyMetadata>HelloWorld</MyMetadata>  
    </CSFile>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Punkte](../msbuild/msbuild-items.md)   
 [MSBuild-Eigenschaften](msbuild-properties1.md)   
 [Referenz zum Projektdatei Schema](../msbuild/msbuild-project-file-schema-reference.md)
