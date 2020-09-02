---
title: Target-Element (MSBuild) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Target
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Target element [MSBuild]
- <Target> element [MSBuild]
ms.assetid: 350f6fc2-86b3-45f2-a31e-ece0e6bd4dca
caps.latest.revision: 38
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f14815502a33fb7d49a10c2724c57a4a0d86e9f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144315"
---
# <a name="target-element-msbuild"></a>Target-Element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Enthält eine Reihe von Aufgaben, die [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] sequenziell ausführt.  
  
 \<Project>  
 \<Target>  
  
## <a name="syntax"></a>Syntax  
  
```  
<Target Name="Target Name"  
        Inputs="Inputs"  
        Outputs="Outputs"  
        Returns="Returns"  
        KeepDuplicateOutputs="true/false"  
        BeforeTargets="Targets"  
        AfterTargets="Targets"  
        DependsOnTargets="DependentTarget"  
        Condition="'String A' == 'String B'">  
        Label="Label">  
    <Task>... </Task>  
    <PropertyGroup>… </PropertyGroup>  
    <ItemGroup>… </ItemGroup>  
    <OnError... />  
</Target>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|attribute|Beschreibung|  
|---------------|-----------------|  
|`Name`|Erforderliches Attribut.<br /><br /> Der Name des Ziels.|  
|`Condition`|Optionales Attribut.<br /><br /> Die auszuwertende Bedingung. Ergibt die Bedingung `false`, führt das Ziel den Hauptteil des Ziels oder alle Ziele nicht aus, die im `DependsOnTargets`-Attribut festgelegt sind. Weitere Informationen zu Bedingungen finden Sie unter [Bedingungen](../msbuild/msbuild-conditions.md).|  
|`Inputs`|Optionales Attribut.<br /><br /> Die Dateien, die Eingaben in das Ziel bilden. Mehrere Dateien werden durch Semikolons getrennt. Der Zeitstempel der Dateien wird mit den Zeitstempeln von Dateien in `Outputs` verglichen, um festzustellen, ob die `Target` aktuell ist. Weitere Informationen finden Sie unter [inkrementelle Builds](../msbuild/incremental-builds.md), Gewusst [wie: Inkrementelles Erstellen](../msbuild/how-to-build-incrementally.md)und [Transformationen](../msbuild/msbuild-transforms.md).|  
|`Outputs`|Optionales Attribut.<br /><br /> Die Dateien, die Ausgaben für dieses Ziel bilden. Mehrere Dateien werden durch Semikolons getrennt. Der Zeitstempel der Dateien wird mit den Zeitstempeln von Dateien in `Inputs` verglichen, um festzustellen, ob die `Target` aktuell ist. Weitere Informationen finden Sie unter [inkrementelle Builds](../msbuild/incremental-builds.md), Gewusst [wie: Inkrementelles Erstellen](../msbuild/how-to-build-incrementally.md)und [Transformationen](../msbuild/msbuild-transforms.md).|  
|`Returns`|Optionales Attribut.<br /><br /> Eine Reihe von Elementen, die Aufgaben zur Verfügung gestellt werden, die dieses Ziel aufrufen, z.B. MSBuild-Aufgaben. Mehrere Zahlen werden durch Semikolons getrennt. Wenn die Ziele in der Datei keine `Returns` Attribute haben, werden stattdessen die Ausgabeattribute für diesen Zweck verwendet.|  
|`KeepDuplicateOutputs`|Optionales boolesches Attribut.<br /><br /> Wenn `true`, werden mehrere Verweise auf dasselbe Element in den Rückgaben des Ziels erfasst.  Standardmäßig ist dieses Attribut `false`.|  
|`BeforeTargets`|Optionales Attribut.<br /><br /> Eine durch Semikolon getrennte Liste von Zielnamen.  Wenn angegeben, bedeutet dies, dass das Ziel vor dem oder den angegebenen Zielen ausgeführt werden soll. Der Projektautor erweitert dann einen vorhandenen Satz von Zielen, ohne sie direkt zu ändern. Weitere Informationen finden Sie unter [zielbuildreihenfolge](../msbuild/target-build-order.md).|  
|`AfterTargets`|Optionales Attribut.<br /><br /> Eine durch Semikolon getrennte Liste von Zielnamen. Wenn angegeben, bedeutet dies, dass das Ziel nach dem oder den angegebenen Zielen ausgeführt werden soll. Der Projektautor erweitert dann einen vorhandenen Satz von Zielen, ohne sie direkt zu ändern. Weitere Informationen finden Sie unter [zielbuildreihenfolge](../msbuild/target-build-order.md).|  
|`DependsOnTargets`|Optionales Attribut.<br /><br /> Die Ziele müssen ausgeführt werden, bevor das Ziel ausgeführt oder eine Abhängigkeitsanalyse der obersten Ebene stattfinden kann. Mehrere Zahlen werden durch Semikolons getrennt.|  
|`Label`|Optionales Attribut.<br /><br /> Ein Bezeichner, der System- und Benutzerelemente identifizieren oder ordnen kann.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Aufgabe](../msbuild/task-element-msbuild.md)|Erstellt und führt eine Instanz einer [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Aufgabe aus. Ein Ziel kann null oder mehrere Elemente enthalten.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Enthält eine Reihe von benutzerdefinierten `Property`-Elementen. Seit .NET Framework 3.5 enthält ein `Target`-Element möglicherweise `PropertyGroup`-Elemente.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Enthält eine Reihe von benutzerdefinierten `Item`-Elementen. Seit .NET Framework 3.5 enthält ein `Target`-Element möglicherweise `ItemGroup`-Elemente. Weitere Informationen finden Sie unter [Elemente](../msbuild/msbuild-items.md).|  
|[OnError](../msbuild/onerror-element-msbuild.md)|Bewirkt, dass mindestens ein Element ausgeführt wird, wenn das `ContinueOnError`-Attribut für eine fehlgeschlagene Aufgabe ErrorAndStop (oder `false`) ist. Ein Ziel kann null oder mehrere `OnError`-Elemente enthalten. Wenn `OnError`-Elemente vorhanden sind, müssen sie die letzten Elemente im `Target`-Element sein.<br /><br /> Weitere Informationen zum- `ContinueOnError` Attribut finden Sie unter [Task-Element (MSBuild)](../msbuild/task-element-msbuild.md).|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Projekt](../msbuild/project-element-msbuild.md)|Erforderliches Stammelement einer [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] -Projektdatei.|  
  
## <a name="remarks"></a>Hinweise  
 Das erste auszuführende Ziel wird zur Laufzeit angegeben. Ziele können von anderen Zielen abhängig sein. Ein Ziel für die Bereitstellung beispielsweise ist von einem Ziel für die Kompilierung abhängig. Die [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Engine führt Abhängigkeiten in der Reihenfolge aus, in der sie im `DependsOnTargets`-Attribut erscheinen, d.h. von links nach rechts. Weitere Informationen finden Sie unter [Ziele](../msbuild/msbuild-targets.md).  
  
 Ein Ziel wird nur einmal während eines Builds ausgeführt, auch wenn mehrere Ziele eine Abhängigkeit aufweisen.  
  
 Wenn ein Ziel übersprungen wird, da sein `Condition`-Attribut `false` ergibt, kann es dennoch ausgeführt werden, wenn es später im Build aufgerufen wird und sein `Condition`-Attribut zu diesem Zeitpunkt `true` ergibt.  
  
 Vor MSBuild 4 hat `Target` alle Elemente zurückgegeben, die im `Outputs`-Attribut angegeben waren.  Zu diesem Zweck musste MSBuild diese Elemente für den Fall aufzeichnen, dass sie später im Build von Aufgaben angefordert werden. Da nicht angegeben werden konnte, welche Ziele Ausgaben hatten, die Aufrufer anfordern würden, sammelte MSBuild alle Elemente aus allen `Outputs` für alle aufgerufenen `Target`. Dies führte zu Skalierungsproblemen bei Builds, die eine große Anzahl von Ausgabeelementen hatten.  
  
 Wenn der Benutzer ein `Returns` für ein `Target`-Element in einem Projekt angibt, erfassen nur die `Target` mit einem `Returns`-Attribut diese Elemente.  
  
 Ein `Target` kann ein `Outputs`-Attribut und ein `Returns`-Attribut enthalten.  `Outputs` wird mit `Inputs` verwendet, um festzustellen, ob das Ziel aktuell ist. `Returns`, falls vorhanden, überschreibt den Wert von `Outputs`, um zu bestimmen, welche Elemente an Aufrufer zurückgegeben werden.  Wenn `Returns` nicht vorhanden ist, wird `Outputs`, außer in dem weiter oben beschriebenen Fall, für Anrufer verfügbar gemacht.  
  
 Vor MSBuild 4 wurden jedes Mal, wenn ein `Target` mehrere Verweise auf dasselbe Element in seinem `Outputs` enthielt, doppelte Elemente aufgezeichnet. In sehr großen Builds mit einer großen Anzahl von Ausgaben und vielen Projektabhängigkeiten wurde dadurch viel Speicher vergeudet, da die doppelten Elemente nicht von Nutzen waren. Wenn das `KeepDuplicateOutputs`-Attribut auf `true` festgelegt ist, werden die doppelten Elemente aufgezeichnet.  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel zeigt ein `Target`-Element, das die `Csc`-Aufgabe ausführt.  
  
```  
<Target Name="Compile" DependsOnTargets="Resources" Returns="$(TargetPath)">  
    <Csc Sources="@(CSFile)"  
          TargetType="library"  
          Resources="@(CompiledResources)"  
          EmitDebugInformation="$(includeDebugInformation)"  
          References="@(Reference)"  
          DebugType="$(debuggingType)" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
    </Csc>  
</Target>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Lern](../msbuild/msbuild-targets.md)   
 [Referenz zum Projektdatei Schema](../msbuild/msbuild-project-file-schema-reference.md)
