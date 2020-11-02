---
title: Delete-Aufgabe | Microsoft-Dokumentation
description: Erfahren Sie mehr über Parameter und Überlegungen bei Verwendung der MSBuild-Aufgabe „Delete“ zum Löschen angegebener Dateien.
ms.custom: SEO-VS-2020
ms.date: 06/11/2020
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Delete
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Delete task [MSBuild]
- MSBuild, Delete task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41d5312434f87d75db80095ff01734cd37894a94
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796484"
---
# <a name="delete-task"></a>Delete-Aufgabe

Löscht die angegebene Datei.

## <a name="parameters"></a>Parameter

In der folgenden Tabelle werden die Parameter der `Delete` -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`DeletedFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Ausgabeparameter.<br /><br /> Gibt die Dateien an, die erfolgreich gelöscht wurden.|
|`Files`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter.<br /><br /> Legt die zu löschenden Dateien fest.|
|`TreatErrorsAsWarnings`|Optionaler `Boolean`-Parameter<br /><br /> Wenn `true`, werden Fehler als Warnungen protokolliert. Der Standardwert ist `false`.|

## <a name="remarks"></a>Hinweise

Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

> [!WARNING]
> Seien Sie vorsichtig, wenn Sie Platzhalter mit dem `Delete`-Task verwenden. Es kann schnell passieren, dass Sie mit Ausdrücken wie `$(SomeProperty)\**\*.*` oder `$(SomeProperty)/**/*.*` die falschen Dateien löschen, insbesondere dann, wenn die Eigenschaft als leere Zeichenfolge ausgewertet wird. In diesem Fall kann der `Files`-Parameter in das Stammverzeichnis Ihres Laufwerks ausgewertet werden, was dazu führen kann, dass deutlich mehr gelöscht wird als gewünscht.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird die Datei *MyApp.pdb* gelöscht, wenn Sie das Ziel `DeleteDebugSymbolFile` erstellen.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

    <PropertyGroup>
        <AppName>ConsoleApp1</AppName>
    </PropertyGroup>

    <Target Name="DeleteDebugSymbolFile">
        <Message Text="Deleting $(OutDir)$(AppName).pdb"/>
        <Delete Files="$(OutDir)$(AppName).pdb" />
    </Target>
  
</Project>

```

Wenn Sie die gelöschten Dateien nachverfolgen müssen, legen Sie `TaskParameter` auf `DeletedFiles` mit dem Elementnamen wie folgt fest:

```xml
      <Target Name="DeleteDebugSymbolFile">
        <Delete Files="$(OutDir)$(AppName).pdb" >
              <Output TaskParameter="DeletedFiles" ItemName="DeletedList"/>
        </Delete>
        <Message Text="Deleted files: '@(DeletedList)'"/>
    </Target>
```

Anstatt Platzhalterzeichen direkt in der `Delete`-Aufgabe zu verwenden, erstellen Sie eine `ItemGroup` von zu löschenden Dateien und wenden danach die `Delete`-Aufgabe auf diese an. Stellen Sie jedoch sicher, dass Sie die `ItemGroup` überlegt platzieren. Wenn Sie in einer Projektdatei eine `ItemGroup` auf der obersten Ebene platzieren, wird sie schon frühzeitig noch vor Beginn des Builds ausgewertet, sodass sie keine Dateien enthält, die beim Buildprozess erstellt wurden. Platzieren Sie daher die `ItemGroup`, die die Liste der zu löschenden Elemente erstellt, in einem Ziel in der Nähe der `Delete`-Aufgabe. Sie können auch eine Bedingung angeben, um zu prüfen, dass die Eigenschaft nicht leer ist, damit Sie keine Elementliste mit einem Pfad erstellen, der beim Stammverzeichnis des Laufwerks beginnt.

Die `Delete`-Aufgabe dient zum Löschen von Dateien. Wenn Sie ein Verzeichnis löschen möchten, verwenden Sie [RemoveDir](removedir-task.md).

Die `Delete`-Aufgabe bietet keine Option zum Löschen schreibgeschützter Dateien. Um schreibgeschützte Dateien zu löschen, können Sie die `Exec`-Aufgabe verwenden, um den Befehl `del` oder einen gleichwertigen Befehl mit der entsprechenden Option zum Aktivieren des Löschens schreibgeschützter Dateien auszuführen. Sie müssen auf die Länge der Eingabeelementliste achten, da eine Längenbeschränkung für die Befehlszeile gilt. Außerdem müssen Sie dafür sorgen, dass Dateinamen mit Leerzeichen wie in diesem Beispiel behandelt werden:

```xml
<Target Name="DeleteReadOnly">
  <ItemGroup>
    <FileToDelete Include="read only file.txt"/>
  </ItemGroup>
  <Exec Command="del /F /Q &quot;@(FileToDelete)&quot;"/>
</Target>
```

Berücksichtigen Sie beim Schreiben von Buildskripts im Allgemeinen, ob Ihr Löschvorgang logisch Teil eines `Clean`-Vorgangs ist. Wenn Sie einige Dateien festlegen müssen, die als Teil eines normalen `Clean`-Vorgangs bereinigt werden sollen, können Sie sie zur Liste `@(FileWrites)` hinzufügen, damit sie beim nächsten `Clean`-Vorgang gelöscht werden. Wenn mehr benutzerdefinierte Verarbeitung erforderlich ist, definieren Sie ein Ziel. Geben Sie an, dass es ausgeführt werden soll, indem Sie das Attribut `BeforeTargets="Clean"` oder `AfterTargets="Clean"` festlegen, oder definieren Sie Ihre benutzerdefinierte Version der Ziele `BeforeClean` oder `AfterClean`. Weitere Informationen finden Sie unter [Anpassen Ihres Builds](customize-your-build.md).

## <a name="see-also"></a>Siehe auch

- [RemoveDir-Aufgabe](removedir-task.md)
- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
