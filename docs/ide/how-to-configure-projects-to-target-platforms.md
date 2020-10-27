---
title: 'Vorgehensweise: Konfigurieren von Projekten für Zielplattformen'
description: Hier erfahren Sie, wie es Ihnen Visual Studio ermöglicht, die Anwendungen für unterschiedliche Zielplattformen einschließlich 64-Bit-Plattformen einzurichten.
ms.custom: SEO-VS-2020
ms.date: 08/16/2019
ms.technology: vs-ide-compile
ms.topic: how-to
helpviewer_keywords:
- project settings [Visual Studio], targeting platforms
- platforms, targeting specific CPUs
- project properties [Visual Studio], targeting platforms
- projects [Visual Studio], targeting platforms
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- CPUs, targeting specific
- 64-bit applications [Visual Studio]
ms.assetid: 845302fc-273d-4f81-820a-7296ce91bd76
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 323d118b73649c8c23d9b4a2e3ace2fd2fc6fdea
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2020
ms.locfileid: "92136757"
---
# <a name="how-to-configure-projects-to-target-platforms"></a>Vorgehensweise: Konfigurieren von Projekten für Zielplattformen

Visual Studio ermöglicht es Ihnen, die Anwendungen für unterschiedliche Zielplattformen einzurichten, einschließlich 64-Bit-Plattformen. Weitere Informationen zur Unterstützung von 64-Bit-Plattformen in Visual Studio finden Sie unter [64-Bit-Anwendungen](/dotnet/framework/64-bit-apps).

## <a name="target-platforms-with-the-configuration-manager"></a>Zielplattformen mit dem Konfigurations-Manager

Mit dem **Konfigurations-Manager** können Sie für ein Projekt schnell eine neue Zielplattform hinzufügen. Wenn Sie eine der in Visual Studio enthaltenen Plattformen auswählen, werden die Projekteigenschaften geändert, um das Projekt unter Berücksichtigung der ausgewählten Plattform zu erstellen.

### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>So konfigurieren Sie ein Projekt für eine 64-Bit-Plattform

1. Klicken Sie in der Menüleiste auf **Build** > **Konfigurations-Manager** .

2. Wählen Sie in der Liste **Aktive Projektmappenplattform** eine 64-Bit-Plattform als Zielplattform für die Projektmappe aus, und klicken Sie dann auf die Schaltfläche **Schließen** .

    1. Wählen Sie **Neu** aus, wenn die gewünschte Plattform nicht in der Liste **Aktive Projektmappenplattform** angezeigt wird.

         Das Dialogfeld **Neue Projektmappenplattform** wird angezeigt.

    2. Wählen Sie in der Liste **Neue Plattform eingeben oder auswählen** **x64** aus.

        > [!NOTE]
        > Wenn Sie die Konfiguration neu benennen, müssen Sie möglicherweise die Einstellungen für die gewünschte Zielplattform im **Projekt-Designer** konfigurieren.

    3. Wenn Sie die Einstellungen aus der aktuellen Plattformkonfiguration kopieren möchten, wählen Sie diese aus, und wählen Sie anschließend die Schaltfläche **OK** aus.

Es werden die Eigenschaften für alle Projekte mit der 64-Bit-Plattform als Zielplattform aktualisiert, und der nächste Build des Projekts wird für 64-Bit-Plattformen optimiert.

> [!NOTE]
> Der Plattformname **Win32** wird für C++-Projekte verwendet und bedeutet **x86** . Visual Studio berücksichtigt sowohl Plattformen auf Projekt- als auch auf Projektmappenebene, wobei die Projektplattformen aus den sprachspezifischen Projektsystemen stammen. In C++-Projekten werden **Win32** und **x64** verwendet, aber in Projektmappenplattformen werden **x86** und **x64** verwendet. Wenn Sie **x86** als Projektmappenkonfiguration wählen, wählt Visual Studio für C++-Projekte die Plattform **Win32** aus. Um Plattformeinstellungen auf Projekt- und Projektmappenebene einzusehen, öffnen Sie den **Konfigurations-Manager** , und notieren Sie sich die beiden Plattformeinstellungen. Die Plattform auf Projektmappenebene wird in der Dropdownliste **Aktive Projektmappenplattform** angezeigt. Die Tabelle zeigt für jedes Projekt die Plattform auf Projektebene.
> ![Screenshot der Projektmappenplattform und Projektplattform](media/project-platform-win32.png)

## <a name="target-platforms-in-the-project-designer"></a>Zielplattformen im Projekt-Designer

Mit dem **Projekt-Designer** können Sie ebenfalls unterschiedliche Zielplattformen für Ihr Projekt festlegen. Wenn Sie die gewünschte Zielplattform nicht in der Liste im Dialogfeld **Neue Projektmappenplattform** auswählen können, können Sie eine benutzerdefinierte Konfiguration erstellen und benennen und die Einstellungen für die gewünschte Zielplattform im **Projekt-Designer** konfigurieren.

Die für diese Aufgabe erforderlichen Schritte sind je nach Programmiersprache unterschiedlich. Weitere Informationen finden Sie unter den folgenden Links:

- Informationen zu -[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]Projekten finden Sie unter [/platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform).

- Informationen zu [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]-Projekten finden Sie unter [Seite „Erstellen“, Projekt-Designer (C#)](../ide/reference/build-page-project-designer-csharp.md).

- Informationen zu [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]-Projekten finden Sie unter [/clr (Common Language Runtime-Kompilierung)](/cpp/build/reference/clr-common-language-runtime-compilation).

## <a name="manually-editing-the-project-file"></a>Manuelles Bearbeiten der Projektdatei

Manchmal müssen Sie die Projektdatei für eine benutzerdefinierte Konfiguration manuell bearbeiten. Ein Beispiel dafür ist, wenn Sie Bedingungen verwenden, die in der IDE nicht angegeben werden können, z.B. ein Verweis, der für zwei verschiedene Plattformen unterschiedlich ist, wie im folgenden Beispiel gezeigt.

### <a name="example-referencing-x86-and-x64-assemblies-and-dlls"></a>Beispiel: Verweisen auf x86- und x64-Assemblys und -DLLs

Möglicherweise verfügen Sie über eine .NET-Assembly oder -DLL mit x86- und x64-Versionen. Um das Projekt für die Verwendung dieser Verweise einzurichten, fügen Sie zunächst den Verweis hinzu, und öffnen Sie dann die Projektdatei, und bearbeiten Sie diese, um eine `ItemGroup` mit einer Bedingung hinzuzufügen, die auf die Konfiguration und die Zielplattform verweist.  Angenommen, die Binärdatei, auf die Sie verweisen, ist ClassLibrary1, und es gibt unterschiedliche Pfade für Debug- und Releasekonfigurationen sowie x86- und x64-Versionen.  Verwenden Sie dann vier `ItemGroup`-Elemente mit allen Kombinationen von Einstellungen wie folgt:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.0</TargetFramework>
    <Platforms>AnyCPU;x64;x86</Platforms>
  </PropertyGroup>

  <ItemGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x64'">
    <Reference Include="ClassLibrary1">
      <HintPath>..\..\ClassLibrary1\ClassLibrary1\bin\x64\Debug\netstandard2.0\ClassLibrary1.dll</HintPath>
    </Reference>
  </ItemGroup>

  <ItemGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|x64'">
    <Reference Include="ClassLibrary1">
      <HintPath>..\..\ClassLibrary1\ClassLibrary1\bin\x64\Release\netstandard2.0\ClassLibrary1.dll</HintPath>
    </Reference>
  </ItemGroup>

  <ItemGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86'">
    <Reference Include="ClassLibrary1">
      <HintPath>..\..\ClassLibrary1\ClassLibrary1\bin\x86\Debug\netstandard2.0\ClassLibrary1.dll</HintPath>
    </Reference>
  </ItemGroup>
  
  <ItemGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|x86'">
    <Reference Include="ClassLibrary1">
      <HintPath>..\..\ClassLibrary1\ClassLibrary1\bin\x86\Release\netstandard2.0\ClassLibrary1.dll</HintPath>
    </Reference>
  </ItemGroup>
</Project>
```

::: moniker range="vs-2017"
> [!NOTE]
> In Visual Studio 2017 müssen Sie das Projekt entladen, bevor Sie die Projektdatei bearbeiten können. Klicken Sie mit der rechten Maustaste auf den Projektknoten, und wählen Sie dann **Projekt entladen** aus. Wenn Sie die Bearbeitung abgeschlossen haben, speichern Sie die Änderungen, und laden Sie das Projekt erneut, indem Sie mit der rechten Maustaste auf den Projektknoten und dann auf **Projekt erneut laden** klicken.
::: moniker-end

Weitere Informationen zur Projektdatei finden Sie unter [Referenz zum MSBuild-Projektdateischema](../msbuild/msbuild-project-file-schema-reference.md).

## <a name="see-also"></a>Siehe auch

- [Grundlagen zu Buildplattformen](../ide/understanding-build-platforms.md)
- [/platform (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)
- [64-Bit-Anwendungen](/dotnet/framework/64-bit-apps)
- [Visual Studio-IDE-64-Bit-Unterstützung](../ide/visual-studio-ide-64-bit-support.md)
- [Grundlegendes zur Projektdatei](/aspnet/web-forms/overview/deployment/web-deployment-in-the-enterprise/understanding-the-project-file)
