---
title: GetFileHash-Aufgabe | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die MSBuild-Aufgabe „GetFileHash“ verwenden, um Prüfsummen der Inhalte einer oder mehrerer Dateien zu berechnen.
ms.custom: SEO-VS-2020
ms.date: 01/28/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFileHash task [MSBuild]
- MSBuild, GetFileHash task
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e9e6e30cf8a224bfdfbde2c728545092bd1494b
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436855"
---
# <a name="getfilehash-task"></a>GetFileHash-Aufgabe

Berechnet Prüfsummen der Inhalte einer Datei oder mehrerer Dateien.

Diese Aufgabe wurde in Version 15.8 hinzugefügt, für die Verwendung für MSBuild-Versionen unter Version 16.0 ist jedoch ein [Workaround](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272) erforderlich.

## <a name="task-parameters"></a>Aufgabenparameter

 In der folgenden Tabelle werden die Parameter der `GetFileHash` -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`Files`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter.<br /><br />Die Dateien, die gehasht werden sollen.|
|`Items`|<xref:Microsoft.Build.Framework.ITaskItem>`[]`-Ausgabeparameter.<br /><br />Die `Files`-Eingabe mit zusätzlichen Metadaten für den Dateihash.|
|`Hash`|`String`-Ausgabeparameter.<br /><br />Der Hash der Datei. Diese Ausgabe wird nur festgelegt, wenn genau ein Element übergeben wurde.|
|`Algorithm`|Optionaler `String`-Parameter.<br /><br />Der Algorithmus. Zulässige Werte: `SHA256`, `SHA384` und `SHA512`. Standard = `SHA256`.|
|`MetadataName`|Optionaler `String`-Parameter.<br /><br />Der Name der Metadaten, in denen der Hash in jedem Element gespeichert ist. Wird standardmäßig auf `FileHash` festgelegt.|
|`HashEncoding`|Optionaler `String`-Parameter.<br /><br />Die Codierung für die generierten Hashes. Wird standardmäßig auf `hex` festgelegt. Zulässige Werte: `hex` und `base64`.|

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird die Aufgabe `GetFileHash` verwendet, um die Prüfsumme der `FilesToHash`-Elemente zu ermitteln und auszugeben.

```xml
<Project>
  <ItemGroup>
    <FilesToHash Include="$(MSBuildThisFileDirectory)\*" />
  </ItemGroup>
  <Target Name="GetHash">
    <GetFileHash Files="@(FilesToHash)">
      <Output
          TaskParameter="Items"
          ItemName="FilesWithHashes" />
    </GetFileHash>

    <Message Importance="High"
             Text="@(FilesWithHashes->'%(Identity): %(FileHash)')" />
  </Target>
</Project>
```

## <a name="see-also"></a>Weitere Informationen

- [Aufgaben](../msbuild/msbuild-tasks.md)

- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)