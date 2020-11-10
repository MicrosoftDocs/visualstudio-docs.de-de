---
title: MSBuild-Zielframework und -Zielplattform | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie ein MSBuild-Projekt zur Ausführung in einer bestimmten .NET Framework-Zielversion, für eine gewünschte Zielplattform oder Softwarearchitektur erstellen können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: df6517c5-edd6-4cc4-97ad-b3cdfc78e799
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d29c4e4659e8e6a5564e3fb41f54615bf29171d2
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93049097"
---
# <a name="msbuild-target-framework-and-target-platform"></a>MSBuild-Zielframework und -Zielplattform

Ein Projekt kann erstellt werden, um in einem *Zielframework* , bei dem es sich um eine bestimmte Version von .NET Framework handelt, und auf einer *Zielplattform* , bei der es sich um eine bestimmte Softwarearchitektur handelt, ausgeführt zu werden.  Beispielsweise können Sie eine Anwendung für die Ausführung in .NET Framework 2.0 auf einer 32-Bit-Plattform entwickeln, die mit der 80x86-Prozessorfamilie („x86“) kompatibel ist. Die Kombination von Zielframework und Zielplattform wird als *Zielkontext* bezeichnet.

> [!IMPORTANT]
> In diesem Artikel wird die alte Methode zum Angeben eines Zielframeworks beschrieben. Projekte im SDK-Format ermöglichen unterschiedliche Zielframeworks wie .NET Standard. Weitere Informationen finden Sie unter [Zielframeworks](/dotnet/standard/frameworks).

## <a name="target-framework-and-profile"></a>Zielframework und -profil

 Ein Zielframework ist eine bestimmte Version von .NET Framework, mit der das Projekt ausgeführt werden soll. Die Angabe eines Zielframeworks ist erforderlich, da es Compilerfunktionen und Assemblyverweise ermöglicht, die nur für diese Version des Frameworks gelten.

 Derzeit werden die folgenden Versionen von .NET Framework unterstützt:

- .NET Framework 2.0 (enthalten in Visual Studio 2005)

- .NET Framework 3.0 (enthalten in Windows Vista)

- .NET Framework 3.5 (enthalten in Visual Studio 2008)

- .NET Framework 4.5.2

- .NET Framework 4.6 (enthalten in Visual Studio 2015)

- .NET Framework 4.6.1

- .NET Framework 4.6.2

- .NET Framework 4.7

- .NET Framework 4.7.1

- .NET Framework 4.7.2

- .NET Framework 4.8

Die Versionen von .NET Framework unterscheiden sich in der Liste der Assemblys, die als Verweise zur Verfügung stehen. Beispielsweise können Sie Windows Presentation Foundation (WPF)-Anwendungen nur erstellen, wenn Ihr Projekt auf die .NET Framework-Version 3.0 oder höher ausgelegt ist.

Das Zielframework wird in der `TargetFrameworkVersion`-Eigenschaft in einer Projektdatei angegeben. Sie können das Zielframework für ein Projekt ändern, indem Sie die Projekteigenschaftenseiten in der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) von Visual Studio verwenden. Weitere Informationen finden Sie unter [Vorgehensweise: .NET Framework-Version als Ziel](../ide/visual-studio-multi-targeting-overview.md). Die verfügbaren Werte für `TargetFrameworkVersion` sind `v2.0`, `v3.0`, `v3.5`, `v4.5.2`, `v4.6`, `v4.6.1`, `v4.6.2`, `v4.7`, `v4.7.1`, `v4.7.2` und `v4.8`.

```xml
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>
```

 Ein *Zielprofil* ist eine Teilmenge eines Zielframeworks. Beispielsweise enthält das .NET Framework 4-Clientprofil keine Verweise auf die MSBuild-Assemblys.

 > [!NOTE]
 > Zielprofile gelten nur für [portable Klassenbibliotheken](/dotnet/standard/cross-platform/cross-platform-development-with-the-portable-class-library).

 Das Zielprofil wird in der `TargetFrameworkProfile`-Eigenschaft in einer Projektdatei angegeben. Sie können das Zielprofil ändern, indem Sie das Zielframeworksteuerelement in den Projekteigenschaftenseiten der IDE verwenden.

```xml
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>
<TargetFrameworkProfile>Client</TargetFrameworkProfile>
```

## <a name="target-platform"></a>Zielplattform

 Eine *Plattform* ist eine Kombination aus Hardware und Software, die eine bestimmte Laufzeitumgebung definiert. Ein auf ein Objekt angewendeter

- `x86` steht für ein 32-Bit-Windows-Betriebssystem, das auf einem Intel 80x86-Prozessor oder einem vergleichbaren Prozessor ausgeführt wird.

- `x64` steht für ein 64-Bit-Windows-Betriebssystem, das auf einem Intel x64-Prozessor oder einem vergleichbaren Prozessor ausgeführt wird.

- `Xbox` steht für die Microsoft Xbox 360-Plattform.

Eine *Zielplattform* ist die spezielle Plattform, auf der Ihr Projekt ausgeführt werden kann. Die Zielplattform wird in der `PlatformTarget`-Buildeigenschaft in einer Projektdatei angegeben. Sie können die Zielplattform ändern, indem Sie die Projekteigenschaftenseiten oder den **Konfigurations-Manager** in der IDE verwenden.

```xml
<PropertyGroup>
   <PlatformTarget>x86</PlatformTarget>
</PropertyGroup>

```

Eine *Zielkonfiguration* ist eine Teilmenge einer Zielplattform. `x86` `Debug`-Konfiguration enthält z. B. die meisten Codeoptimierungen nicht. Die Zielkonfiguration wird in der `Configuration`-Buildeigenschaft in einer Projektdatei angegeben. Sie können die Zielkonfiguration ändern, indem Sie die Projekteigenschaftenseiten oder den **Konfigurations-Manager** verwenden.

```xml
<PropertyGroup>
   <PlatformTarget>x86</PlatformTarget>
   <Configuration>Debug</Configuration>
</PropertyGroup>

```

## <a name="see-also"></a>Siehe auch

- [Festlegen von Zielversionen](../msbuild/msbuild-multitargeting-overview.md)
