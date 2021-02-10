---
title: MSBuild-Aufgaben | Microsoft-Dokumentation
description: Erfahren Sie, wie MSBuild-Aufgaben – Einheiten von ausführbarem Code – verwendet, um während des Buildprozesses unteilbare Buildvorgänge auszuführen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tasks
- MSBuild, tasks
ms.assetid: 5d3cc4a7-e5db-4f73-b707-8b6882fddcf8
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6b3bb4c1a17cd5d1481be2fa942686bce3861bb2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918919"
---
# <a name="msbuild-tasks"></a>MSBuild-Aufgaben

Eine Buildplattform muss während des Buildprozesses eine beliebige Anzahl von Aktionen auszuführen können. MSBuild verwendet *Aufgaben* zum Ausführen dieser Aktionen. Eine Aufgabe ist eine Einheit von ausführbarem Code, der von MSBuild verwendet wird, um unteilbare Buildvorgänge auszuführen.

## <a name="task-logic"></a>Aufgabenlogik

 Das XML-Projektdateiformat von MSBuild kann Buildvorgänge selbst nicht vollständig ausführen. Daher muss die Aufgabenlogik außerhalb der Projektdatei implementiert werden.

 Die Ausführungslogik einer Aufgabe wird als .NET-Klasse implementiert, die die <xref:Microsoft.Build.Framework.ITask>-Schnittstelle implementiert, die im <xref:Microsoft.Build.Framework>-Namespace definiert ist.

 Die Aufgabenklasse definiert darüber hinaus die für eine Aufgabe in der Projektdatei verfügbaren Eingabe- und Ausgabeparameter. Auf alle konfigurierbaren öffentlichen nicht statischen und nicht abstrakten Eigenschaften, die von der Aufgabenklasse verfügbar gemacht werden, kann in der Projektdatei zugegriffen werden, indem ein entsprechendes Attribut mit demselben Namen im [Task](../msbuild/task-element-msbuild.md)-Element platziert wird.

 Sie können eine eigene Aufgabe schreiben, indem Sie eine verwaltete Klasse erstellen, die die <xref:Microsoft.Build.Framework.ITask>-Schnittstelle implementiert. Weitere Informationen finden Sie unter [Schreiben von Aufgaben](../msbuild/task-writing.md).

## <a name="execute-a-task-from-a-project-file"></a>Ausführen einer Aufgabe aus einer Projektdatei

 Vor dem Ausführen einer Aufgabe in der Projektdatei müssen Sie zuerst den Typ in der Assembly zuordnen, der die Aufgabe mithilfe des Elements [UsingTask](../msbuild/usingtask-element-msbuild.md) in den Aufgabennamen implementiert. Auf diese Weise weiß MSBuild, wo es nach der Ausführungslogik der Aufgabe suchen muss, wenn diese in der Projektdatei gefunden wird.

 Erstellen Sie ein Element mit dem Namen der Aufgabe als untergeordnetes Element eines `Target`-Elements, um eine Aufgabe in einer MSBuild-Projektdatei auszuführen. Wenn eine Aufgabe Parameter akzeptiert, werden diese als Attribute des Elements übergeben.

 MSBuild-Elementlisten und -Eigenschaften können als Parameter verwendet werden. Der folgende Code ruft z. B. die Aufgabe `MakeDir` auf und legt für die `Directories`-Eigenschaft des `MakeDir`-Objekts denselben Wert wie für die `BuildDir`-Eigenschaft fest:

```xml
<Target Name="MakeBuildDirectory">
    <MakeDir
        Directories="$(BuildDir)" />
</Target>
```

 Aufgaben können zudem Informationen an die Projektdatei zurückgeben, die für die spätere Verwendung in Elementen oder Eigenschaften gespeichert werden können. Der folgende Code ruft z.B. die `Copy`-Aufgabe auf und speichert die Informationen aus der `CopiedFiles`-Ausgabeeigenschaft in der `SuccessfullyCopiedFiles`-Elementliste.

```xml
<Target Name="CopyFiles">
    <Copy
        SourceFiles="@(MySourceFiles)"
        DestinationFolder="@(MyDestFolder)">
        <Output
            TaskParameter="CopiedFiles"
            ItemName="SuccessfullyCopiedFiles"/>
     </Copy>
</Target>
```

## <a name="included-tasks"></a>Verfügbare Aufgaben

 MSBuild stellt zahlreiche Aufgaben bereit, z. B. [Copy](../msbuild/copy-task.md) zum Kopieren von Dateien, [MakeDir](../msbuild/makedir-task.md) zum Erstellen von Verzeichnissen und [Csc](../msbuild/csc-task.md) zum Kompilieren von C#-Quellcodedateien. Eine vollständige Liste der verfügbaren Aufgaben sowie Nutzungsinformationen finden Sie unter [Aufgabenreferenz](../msbuild/msbuild-task-reference.md).

## <a name="overridden-tasks"></a>Überschriebene Aufgaben

 MSBuild sucht an verschiedenen Speicherorten nach Aufgaben. Beim ersten Speicherort handelt es sich um Dateien mit der Erweiterung *.OverrideTasks*, die in den .NET Framework-Verzeichnissen gespeichert sind. Aufgaben in diesen Dateien überschreiben alle anderen Aufgaben mit denselben Namen, einschließlich Aufgaben in der Projektdatei. Beim zweiten Speicherort handelt es sich um Dateien mit der Erweiterung *.Tasks*, die in den .NET Framework-Verzeichnissen gespeichert sind. Wird die Aufgabe in keinem dieser beiden Speicherorte gefunden, so wird die Aufgabe in der Projektdatei verwendet.

## <a name="see-also"></a>Siehe auch

- [MSBuild-Grundlagen](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [Schreiben von Aufgaben](../msbuild/task-writing.md)
- [Inlineaufgaben](../msbuild/msbuild-inline-tasks.md)
