---
title: Seite "Buildereignisse", Projekt-Designer (C#)
description: Hier erfahren Sie, wie Sie Anweisungen für Buildkonfigurationen angeben. Außerdem können Sie die Bedingungen angeben, unter denen sämtliche Postbuildereignisse ausgeführt werden.
ms.custom: SEO-VS-2020
ms.date: 10/17/2019
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuildEvents
helpviewer_keywords:
- build events
- Project Designer, Build Events page
- pre-build events
- post-build events
ms.assetid: 3fff9ae5-213c-46ea-a660-1d70acb6c922
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5f70557338a48931a3d109f345714d219f428f50
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2020
ms.locfileid: "92136848"
---
# <a name="build-events-page-project-designer-c"></a>Seite "Buildereignisse", Projekt-Designer (C#)

Verwenden Sie die Seite **Buildereignisse** des **Projekt-Designers** , um die Anweisungen der Buildkonfiguration anzugeben. Außerdem können Sie die Bedingungen angeben, unter denen sämtliche Postbuildereignisse ausgeführt werden. Weitere Informationen finden Sie unter [Vorgehensweise: Angeben von Buildereignissen (C#)](../../ide/how-to-specify-build-events-csharp.md) und [Vorgehensweise: Angeben von Buildereignissen (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).

## <a name="uielement-list"></a>UIElement-Liste

**Configuration**

Dieses Steuerelement kann auf dieser Seite nicht bearbeitet werden. Eine Beschreibung dieses Steuerelements finden Sie unter [Seite „Erstellen“, Projekt-Designer (C#)](../../ide/reference/build-page-project-designer-csharp.md).

**Plattform**

Dieses Steuerelement kann auf dieser Seite nicht bearbeitet werden. Eine Beschreibung dieses Steuerelements finden Sie unter [Seite „Erstellen“, Projekt-Designer (C#)](../../ide/reference/build-page-project-designer-csharp.md).

**Befehlszeile für Präbuildereignis**

Gibt sämtliche Befehle an, die vor dem Start des Buildvorgangs ausgeführt werden sollen. Klicken Sie auf **Präbuild bearbeiten...** , um das [Dialogfeld „Befehlszeile für Präbuildereignis“/„Befehlszeile für Postbuildereignis“](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md) anzuzeigen. In dieses Feld können Sie lange Befehle eingeben.

> [!NOTE]
> Präbuildereignisse werden nicht ausgeführt, wenn das Projekt auf dem neuesten Stand ist, und es wird kein Build gestartet.

**Befehlszeile für Postbuildereignis**

Gibt sämtliche Befehle an, die nach dem Abschluss des Buildvorgangs ausgeführt werden sollen. Klicken Sie auf **Postbuild bearbeiten...** , um das **Dialogfeld „Befehlszeile für Präbuildereignis“/„Befehlszeile für Postbuildereignis“** anzuzeigen. In dieses Feld können Sie lange Befehle eingeben.

> [!NOTE]
> Fügen Sie allen Postbuildbefehlen, die BAT-Dateien ausführen, eine `call`-Anweisung hinzu. Zum Beispiel: `call C:\MyFile.bat` oder `call C:\MyFile.bat call C:\MyFile2.bat`.

**Postbuildereignis ausführen**

Gibt die folgenden Bedingungen für das auszuführende Postbuildereignis an, wie in der folgenden Tabelle dargestellt.

|Option|Ergebnis|
|------------|------------|
|**Always**|Das Postbuildereignis wird ausgeführt, unabhängig davon, ob der Buildvorgang erfolgreich ist.|
|**Bei erfolgreichem Erstellen**|Das Postbuildereignis wird ausgeführt, wenn der Buildvorgang erfolgreich ist. Deshalb wird das Ereignis sogar für ein aktuelles Projekt ausgeführt, solange der Buildvorgang erfolgreich ist.|
|**Wenn der Build die Projektausgabe aktualisiert**|Das Postbuildereignis wird nur ausgeführt, wenn sich die Ausgabedatei des Compilers (.exe or .dll) von der vorherigen Ausgabedatei des Compilers unterscheidet. Deshalb wird kein Postbuildereignis ausgeführt, wenn das Projekt aktuell ist.|

## <a name="in-the-project-file"></a>In der Projektdatei

In früheren Versionen von Visual Studio fügt Visual Studio beim Ändern der Einstellung **PreBuildEvent** oder **PostBuildEvent** in der IDE der Projektdatei die Eigenschaft `PreBuildEvent` oder `PostBuildEvent` hinzu. Beispiel: Wenn Ihre Befehlszeileneinstellung **PreBuildEvent** in der IDE wie folgt lautet:

```input
"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)"
```

dann ist die Projektdateieinstellung wie folgt:

```xml
<PropertyGroup>
    <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)" />
</PropertyGroup>
```

Für .NET Core-Projekte fügt Visual Studio 2019 (und Visual Studio 2017 mit den neuesten Updates) den Einstellungen **PreBuildEvent** und **PostBuildEvent** ein MSBuild-Ziel namens `PreBuild` oder `PostBuild` hinzu. Diese Ziele verwenden die **BeforeTargets** - und **AfterTargets** -Attribute, die von MSBuild erkannt werden. Beispielsweise generiert Visual Studio für das vorherige Beispiel nun den folgenden Code:

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>
```

Verwenden Sie für ein Ereignis nach dem Buildvorgang den Namen `PostBuild`, und legen Sie das Attribut `AfterTargets` auf `PostBuildEvent` fest.

```xml
<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
> Diese Änderungen an der Projektdatei wurden vorgenommen, um Projekte im SDK-Format zu unterstützen. Wenn Sie eine Projektdatei manuell vom alten Format zum SDK-Format migrieren, müssen Sie die Eigenschaften `PreBuildEvent` und `PostBuildEvent` löschen und durch die Ziele `PreBuild` und `PostBuild` ersetzen (siehe den vorherigen Code). Informationen, wie Sie feststellen können, ob Ihr Projekt das SDK-Format hat, finden Sie unter [Überprüfen des Projektformats](/nuget/resources/check-project-format).

## <a name="see-also"></a>Siehe auch

- [Gewusst wie: Festlegen von Buildereignissen (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Gewusst wie: Angeben von Buildereignissen (C#)](../../ide/how-to-specify-build-events-csharp.md)
- [Projekteigenschaftenverweise](../../ide/reference/project-properties-reference.md)
- [Kompilieren und Erstellen](../../ide/compiling-and-building-in-visual-studio.md)
