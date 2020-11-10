---
title: Bekannte MSBuild-Elementmetadaten | Microsoft-Dokumentation
description: Erfahren Sie mehr über MSBuild-Metadaten, die jedem Element bei seiner Erstellung zugewiesen werden, sowie über einige optionale MSBuild-Metadaten, die Sie zum Steuern des Buildverhaltens definieren können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, item metadata
- MSBuild, well-known item metadata
ms.assetid: b5e791b5-c68f-4978-ad8a-9247d03bb6c0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 047fe5ef6edc57681b8382a9f2a1069991e0f513
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93049009"
---
# <a name="msbuild-well-known-item-metadata"></a>Bekannte MSBuild-Elementmetadaten

Elementmetadaten sind an Elemente angefügte Werte. Einige werden den Elementen von MSBuild zugewiesen, wenn die Elemente erstellt werden, aber Sie können auch jegliche benötigten Metadaten selbst definieren. Einige benutzerdefinierte Metadatenwerte haben eine Bedeutung in MSBuild, in bestimmten Aufgaben oder in SDKs wie z. B. dem .NET SDK.

In der ersten Tabelle in diesem Artikel werden die jedem Element bei der Erstellung zugewiesenen Metadaten beschrieben. Die nächste Tabelle zeigt einige optionale Metadaten, die eine Bedeutung in MSBuild haben und die Sie zum Steuern des Buildverhaltens definieren können. In jedem Beispiel wurde die folgende Elementdeklaration verwendet, um die Datei *C:\MyProject\Source\Program.cs* in das Projekt aufzunehmen.

```xml
<ItemGroup>
    <MyItem Include="Source\Program.cs" />
</ItemGroup>
```

|Elementmetadaten|Beschreibung|
|-------------------|-----------------|
|%(FullPath)|Enthält den vollständigen Pfad des Elements. Beispiel:<br /><br /> *C:\MyProject\Source\Program.cs*|
|%(RootDir)|Enthält das Stammverzeichnis des Elements. Beispiel:<br /><br /> *C:\\*|
|%(Filename)|Enthält den Dateinamen des Elements ohne Erweiterung. Beispiel:<br /><br /> *Program*|
|%(Extension)|Enthält die Dateierweiterung des Elements. Beispiel:<br /><br /> *.cs*|
|%(RelativeDir)|Enthält den im `Include`-Attribut angegebenen Pfad, bis zum abschließenden umgekehrten Schrägstrich (\\). Zum Beispiel:<br /><br /> *Source\\*<br /><br /> Wenn das `Include`-Attribut ein vollständiger Pfad ist, beginnt `%(RelativeDir)` mit dem Stammverzeichnis `%(RootDir)`.  Beispiel: <br /><br /> *C:\MyProject\Source\\*|
|%(Directory)|Enthält das Verzeichnis des Elements ohne das Stammverzeichnis. Zum Beispiel:<br /><br /> *MyProject\\Source\\*|
|%(RecursiveDir)|Wenn das `Include`-Attribut das Platzhalterzeichen \*\* enthält, geben diese Metadaten den Teil des Pfads an, der das Platzhalterzeichen ersetzt. Weitere Informationen zu Platzhaltern finden Sie unter [Vorgehensweise: Auswählen von Dateien für den Buildvorgang](../msbuild/how-to-select-the-files-to-build.md).<br /><br /> Wenn der Ordner *C:\MySolution\MyProject\Source\\* die Datei *Program.cs* enthält, und wenn die Projektdatei dieses Element enthält:<br /><br /> `<ItemGroup>`<br /><br /> `<MyItem Include="C:\**\Program.cs" />`<br /><br /> `</ItemGroup>`<br /><br /> ist der Wert von `%(MyItem.RecursiveDir)` gleich *\MyProject\Source\\* .|
|%(Identity)|Das im `Include`-Attribut angegebene Element. Beispiel:<br /><br /> *Source\Program.cs*|
|%(ModifiedTime)|Enthält den Zeitstempel vom Zeitpunkt der letzten Änderung des Elements. Zum Beispiel:<br /><br /> `2004-07-01 00:21:31.5073316`|
|%(CreatedTime)|Enthält den Zeitstempel vom Zeitpunkt der Erstellung des Elements. Zum Beispiel:<br /><br /> `2004-06-25 09:26:45.8237425`|
|%(AccessedTime)|Enthält den Zeitstempel vom Zeitpunkt des letzten Zugriffs auf das Element.<br /><br /> `2004-08-14 16:52:36.3168743`|

## <a name="see-also"></a>Siehe auch

- [Gemeinsame MSBuild-Elementmetadaten](common-msbuild-item-metadata.md)
- [Elemente](../msbuild/msbuild-items.md)
- [Batchverarbeitung](../msbuild/msbuild-batching.md)
- [MSBuild-Referenz](../msbuild/msbuild-reference.md)
