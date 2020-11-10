---
title: XmlPoke-Aufgabe | Microsoft-Dokumentation
description: Erfahren Sie, wie MSBuild mithilfe der Aufgabe „XmlPoke“ die Werte in einer XML-Datei gemäß Angabe in einer XPath-Abfrage festlegt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XmlPoke task [MSBuild]
- MSBuild, XmlPoke task
ms.assetid: 6ba1953c-be3b-4df8-8561-e133408f8270
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 35e29004116807092452a08d3835ba3e5e1dabcd
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047227"
---
# <a name="xmlpoke-task"></a>XmlPoke-Aufgabe

Legt die Werte einer XML-Datei wie von der XPath-Abfrage angegeben fest

## <a name="parameters"></a>Parameter

 In der folgenden Tabelle werden die Parameter der `XmlPoke` -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`Namespaces`|Optionaler `String`-Parameter.<br /><br /> Gibt die Namespaces für die Präfixe von XPath-Abfragen an `Namespaces` ist ein XML-Ausschnitt, der aus `Namespace`-Elementen mit den Attributen `Prefix` und `Uri` besteht. Das Attribut `Prefix` gibt das Präfix an, das dem im `Uri`-Attribut angegebenen Namespace zugeordnet werden soll. Verwenden Sie kein leeres `Prefix`-Attribut.|
|`Query`|Optionaler `String`-Parameter.<br /><br /> Gibt die XPath-Abfrage an|
|`Value`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem> -Parameter.<br /><br /> Gibt den Wert an, der in den angegebenen Pfad eingefügt werden soll.|
|`XmlInputPath`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>-Parameter.<br /><br /> Gibt die XML-Eingabe als Dateipfad an|

## <a name="remarks"></a>Hinweise

 Zusätzlich zu den in der Tabelle aufgeführten Parametern erbt dieser Task Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Beispiel

Dies ist ein einfach zu bearbeitender sample.xml-Code:

```xml
<Package xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
         xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" >
<Identity Name="Sample.Product " Publisher="CN=1234" Version="1.0.0.0" />
<mp:PhoneIdentity PhoneProductId="456" PhonePublisherId="0" />
</Package>
```

Wenn Sie in diesem Beispiel `/Package/mp:PhoneIdentity/PhoneProductId` ändern möchten, gehen Sie folgendermaßen vor:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <Namespace>
        <Namespace Prefix="dn" Uri="http://schemas.microsoft.com/appx/manifest/foundation/windows10" />
        <Namespace Prefix="mp" Uri="http://schemas.microsoft.com/appx/2014/phone/manifest" />
        <Namespace Prefix="uap" Uri="http://schemas.microsoft.com/appx/manifest/uap/windows10" />
    </Namespace>
</PropertyGroup>

<Target Name="Poke">
  <XmlPoke
    XmlInputPath="Sample.xml"
    Value="MyId"
    Query="/dn:Package/mp:PhoneIdentity/@PhoneProductId"
    Namespaces="$(Namespace)"/>
</Target>
</Project>
```

`dn` wird hier als künstliches Namespacepräfix für den Standardnamespace verwendet.

## <a name="see-also"></a>Siehe auch

- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
