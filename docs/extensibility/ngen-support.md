---
title: Ngen-Unterstützung in VSIX v3 | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie den nativen Image Generator aktivieren. Hierbei handelt es sich um ein Tool, mit dem Erweiterungs Entwickler die Leistung verwalteter Anwendungen verbessern können.
ms.custom: SEO-VS-2020
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 064176a0a28e3621e796bf60ede552f9cda155b0
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2021
ms.locfileid: "97864028"
---
# <a name="ngen-support-in-vsix-v3"></a>NGen-Unterstützung in VSIX v3

Mit Visual Studio 2017 und dem neuen VSIX v3 (Version 3)-Erweiterungs Manifest-Format können Erweiterungs Entwickler nun Ihre Assemblys zur Installationszeit "ngen".

Im folgenden finden Sie einen Auszug aus MSDN, in dem erläutert wird, was "ngen" funktioniert:

>Der Native Image Generator (*Ngen.exe*) ist ein Tool, das die Leistung verwalteter Anwendungen verbessert. *Ngen.exe* erstellt native Images, bei denen es sich um Dateien mit kompiliertem Prozessor spezifischem Computercode handelt, und installiert diese im Cache für Native Images auf dem lokalen Computer. Die Laufzeit kann systemeigene Abbilder aus dem Cache nutzen und muss nicht den JIT (Just-In-Time)-Compiler verwenden, um die ursprüngliche Assembly zu kompilieren.
>
>aus [Ngen.exe (Native Image Generator)](/dotnet/framework/tools/ngen-exe-native-image-generator)

Um eine Assembly "ngen" zu erhalten, muss die VSIX-Instanz "pro Instanz pro Computer" installiert sein. Dies kann aktiviert werden, indem Sie das Kontrollkästchen "alle Benutzer" im `extension.vsixmanifest` Designer aktivieren:

![alle Benutzer überprüfen](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Aktivieren von Ngen

Zum Aktivieren von NGen für eine Assembly können Sie das **Eigenschaften** Fenster in Visual Studio verwenden.

Es gibt vier Eigenschaften, die festgelegt werden können:

1. **Ngen** (Boolean): Wenn der Wert true ist, wird die Assembly vom Visual Studio-Installer "ngen" angezeigt.
2. **Ngen-Anwendung** (String): ngen bietet die Möglichkeit, die *app.config* Datei einer Anwendung zum Auflösen von Assemblyabhängigkeiten zu verwenden. Dieser Wert sollte auf eine Anwendung festgelegt werden, deren *app.config* Sie verwenden möchten (relativ zum Visual Studio-Installationsverzeichnis).
3. **Ngen-Architektur** (Enum): die Architektur, mit der die Assembly System intern kompiliert wird. Die Optionen lauten: a. Nicht angegeben b. X86 c. X64 d. Alle
4. **Ngen-Priorität** (Integer zwischen 1 und 3): die ngen-Prioritätsstufe wird auf [Ngen.exe Prioritätsstufen](/dotnet/framework/tools/ngen-exe-native-image-generator#priority-levels)dokumentiert.

Hier sehen Sie das **Eigenschaften** Fenster in Aktion:

![ngen in Eigenschaften](media/ngen-in-properties.png)

Hierdurch werden dem Projekt Verweis Metadaten in der *csproj* -Datei des VSIX-Projekts hinzugefügt:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
    <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
    <Name>ClassLibrary1</Name>
    <Ngen>True</Ngen>
    <NgenApplication>vsn.exe</NgenApplication>
    <NgenArchitecture>X86</NgenArchitecture>
    <NgenPriority>2</NgenPriority>
</ProjectReference>
```

> [!NOTE]
> Wenn Sie möchten, können Sie die CSPROJ-Datei direkt bearbeiten.

## <a name="extra-information"></a>Zusätzliche Informationen

Die Änderungen an den Eigenschaften-Designern gelten für mehr als nur Projekt Verweise. Sie können auch die ngen-Metadaten für Elemente in Ihrem Projekt festlegen (mit den oben beschriebenen Methoden), sofern es sich bei den Elementen um .NET-Assemblys handelt.
