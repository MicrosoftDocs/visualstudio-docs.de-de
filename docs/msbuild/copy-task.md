---
title: Copy-Aufgabe | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die MSBuild-Aufgabe „Copy“ verwenden, um Dateien an einen neuen Datei- oder Ordnerspeicherort im Dateisystem zu kopieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Copy
- MSBuild.Copy.SourceFileNotFound
- MSBuild.Copy.Retrying
- MSBuild.Copy.ExceededRetries
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Copy task
- Copy task [MSBuild]
ms.assetid: a46ba9da-3e4e-4890-b4ea-09a099b6bc40
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00544b6d1e797a1fd8a7a197197480cae5620f10
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796225"
---
# <a name="copy-task"></a>Copy-Aufgabe

Kopiert Dateien an einen neuen Speicherort im Dateisystem.

## <a name="parameters"></a>Parameter

In der folgenden Tabelle werden die Parameter der `Copy` -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`CopiedFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Enthält die Elemente, die erfolgreich kopiert wurden, *einschließlich* derer, die nicht tatsächlich kopiert sondern übersprungen wurden, weil sie bereits auf dem neuesten Stand sind und `SkipUnchangedFiles` den Wert `true` aufweist.|
|`DestinationFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Gibt die Liste der Dateien an, in die die Quelldateien kopiert werden sollen. Diese Liste soll der im `SourceFiles`-Parameter angegebenen Liste eins zu eins entsprechen. Das heißt, die erste in `SourceFiles` angegebene Datei wird an den ersten in `DestinationFiles` angegebenen Speicherort kopiert usw.|
|`DestinationFolder`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>-Parameter.<br /><br /> Gibt das Verzeichnis an, in das die Dateien kopieren werden sollen. Es muss sich um ein Verzeichnis handeln, nicht um eine Datei. Wenn das Verzeichnis nicht vorhanden ist, wird es automatisch erstellt.|
|`OverwriteReadOnlyFiles`|Optionaler `Boolean`-Parameter.<br /><br /> Überschreibt Dateien, auch wenn diese als schreibgeschützte gekennzeichnet sind|
|`Retries`|Optionaler `Int32`-Parameter.<br /><br /> Gibt die Anzahl der vorgesehenen Kopierversuche an, wenn alle vorherigen Versuche fehlgeschlagen sind. Der Standardwert ist 0 (null).<br /><br /> **Vorsicht** : Die Verwendung von Wiederholungen kann ein Synchronisierungsproblem im Buildprozess maskieren.<br /><br /> **Hinweis** : Der Standardwert für *task* sind 0 Wiederholungen, allerdings wird durch Verwendungen des Tasks häufig `$(CopyRetryCount)` übergeben, ///was standardmäßig nicht 0 ist.|
|`RetryDelayMilliseconds`|Optionaler `Int32`-Parameter.<br /><br /> Gibt die Verzögerung zwischen jeglichen erforderlichen Wiederholungen an. Standardwert ist das RetryDelayMillisecondsDefault-Argument, das an den CopyTask-Konstruktor übergeben wird.|
|`SkipUnchangedFiles`|Optionaler `Boolean`-Parameter.<br /><br /> Wenn der Wert `true` lautet, werden Dateien, die an der Quelle und am Ziel identisch sind, beim Kopieren übersprungen. In der `Copy`-Aufgabe werden Dateien als identisch betrachtet, wenn diese dieselbe Größe aufweisen und zur selben Zeit zuletzt geändert wurden. <br /><br /> **Hinweis:** Wenn Sie diesen Parameter auf `true` festlegen, sollten Sie für das enthaltende Ziel aus folgendem Grund nicht die Abhängigkeitsanalyse verwenden: Die Aufgabe wird nur dann ausgeführt, wenn die letzte Änderung der Quelldateien weniger lange zurück liegt als die letzte Änderung der Zieldateien.|
|`SourceFiles`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter.<br /><br /> Gibt die zu kopierenden Dateien an.|
|`UseHardlinksIfPossible`|Optionaler `Boolean`-Parameter.<br /><br /> Wenn `true`, werden für die kopierten Dateien feste Links erstellt, statt die Dateien zu kopieren.|

## <a name="warnings"></a>Warnungen

Warnungen werden protokolliert, darunter:

- `Copy.DestinationIsDirectory`

- `Copy.SourceIsDirectory`

- `Copy.SourceFileNotFound`

- `Copy.CreatesDirectory`

- `Copy.HardLinkComment`

- `Copy.RetryingAsFileCopy`

- `Copy.FileComment`

- `Copy.RemovingReadOnlyAttribute`

## <a name="remarks"></a>Hinweise

Es muss entweder der `DestinationFolder`-Parameter oder der `DestinationFiles`-Parameter angegeben werden, jedoch nicht beide. Wenn beide angegeben werden, schlägt der Task fehl, und ein Fehler wird protokolliert.

Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

## <a name="example-1"></a>Beispiel 1

Im folgenden Beispiel werden die Elemente in der `MySourceFiles`-Elementauflistung in den Ordner *C:\MyProject\Destination* kopiert.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MySourceFiles Include="a.cs;b.cs;c.cs"/>
    </ItemGroup>

    <Target Name="CopyFiles">
        <Copy
            SourceFiles="@(MySourceFiles)"
            DestinationFolder="c:\MyProject\Destination"
        />
    </Target>

</Project>
```

## <a name="example-2"></a>Beispiel 2

Im folgenden Beispiel wird veranschaulicht, wie ein rekursiver Kopiervorgang ausgeführt wird. In diesem Projekt werden alle Dateien rekursiv von *C:\MySourceTree* nach *C:\MyDestinationTree* kopiert, wobei die Verzeichnisstruktur beibehalten wird.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MySourceFiles Include="c:\MySourceTree\**\*.*"/>
    </ItemGroup>

    <Target Name="CopyFiles">
        <Copy
            SourceFiles="@(MySourceFiles)"
            DestinationFiles="@(MySourceFiles->'c:\MyDestinationTree\%(RecursiveDir)%(Filename)%(Extension)')"
        />
    </Target>

</Project>
```

## <a name="see-also"></a>Weitere Informationen

- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
