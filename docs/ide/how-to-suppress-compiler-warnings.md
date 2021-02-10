---
title: Unterdrücken von Warnungen für Projekte und NuGet-Pakete
description: Hier erfahren Sie, wie Sie mithilfe von Visual Studio die Übersichtlichkeit eines Buildprotokolls verbessern, indem Sie eine oder mehrere Arten von Compilerwarnungen herausfiltern.
ms.custom: SEO-VS-2020
ms.date: 01/24/2018
ms.technology: vs-ide-compile
ms.topic: how-to
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ab79521cfd4cc122fa398f88b56ca37e2f2673a1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869179"
---
# <a name="how-to-suppress-compiler-warnings"></a>Vorgehensweise: Unterdrücken von Compilerwarnungen

Sie können die Übersichtlichkeit eines Buildprotokolls verbessern, indem Sie eine oder mehrere Arten von Compilerwarnungen herausfiltern. Möglicherweise möchten Sie nur einen Teil der Ausgabe überprüfen, der beim Festlegen der Ausführlichkeit für Buildprotokolle auf **Normal**, **Ausführlich** oder **Diagnose** generiert wird. Weitere Informationen zur Ausführlichkeit erhalten Sie im Artikel [Vorgehensweise: Anzeigen, Speichern und Konfigurieren von Buildprotokolldateien](../ide/how-to-view-save-and-configure-build-log-files.md).

## <a name="suppress-specific-warnings-for-visual-c-or-f"></a>Unterdrücken bestimmter Warnungen für Visual C# oder F\#

Verwenden Sie die Eigenschaftenseite **Build**, um bestimmte Warnungen für C#- und F#-Projekte zu unterdrücken.

1. Wählen Sie im **Projektmappen-Explorer** das Projekt aus, in dem Sie Warnungen unterdrücken möchten.

1. Wählen Sie in der Menüleiste **Ansicht** >  **Eigenschaftenseiten** aus.

1. Wählen Sie die Seite **Erstellen** aus.

1. Geben Sie im Feld **Warnungen unterdrücken** durch Semikola getrennt die Fehlercodes der Warnungen an, die unterdrückt werden sollen.

1. Generieren Sie die Projektmappe neu.

## <a name="suppress-specific-warnings-for-c"></a>Unterdrücken bestimmter Warnungen für C++

Verwenden Sie die Seite **Konfigurationseigenschaften**, um bestimmte Warnungen für C++-Projekte zu unterdrücken.

1. Wählen Sie im **Projektmappen-Explorer** das Projekt oder die Quelldatei aus, für das bzw. die Sie Warnungen unterdrücken möchten.

1. Wählen Sie in der Menüleiste **Ansicht** >  **Eigenschaftenseiten** aus.

1. Wählen Sie die Kategorie **Konfigurationseigenschaften** aus, wählen Sie die Kategorie **C/C++** und dann die Seite **Erweitert** aus.

1. Führen Sie einen der folgenden Schritte aus:

    - Geben Sie im Feld **Bestimmte Warnungen deaktivieren** die Fehlercodes der Warnungen an, die Sie unterdrücken möchten, durch Semikola getrennt.

    - Wählen Sie im Feld **Bestimmte Warnungen deaktivieren** den Befehl **Bearbeiten** aus, um weitere Optionen anzuzeigen.

1. Wählen Sie die Schaltfläche **OK** aus, und erstellen Sie die Projektmappe dann erneut.

## <a name="suppress-warnings-for-visual-basic"></a>Unterdrücken von Warnungen für Visual Basic

Sie können bestimmte Compilerwarnungen für Visual Basic unterdrücken, indem Sie die *VBPROJ*-Datei für das Projekt bearbeiten. Um Warnungen nach *Kategorie* zu unterdrücken, können Sie die Seite [Compilereigenschaften](../ide/reference/compile-page-project-designer-visual-basic.md) verwenden. Weitere Informationen finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).

### <a name="to-suppress-specific-warnings-for-visual-basic"></a>So unterdrücken Sie bestimmte Warnungen für Visual Basic

In diesem Beispiel wird gezeigt, wie Sie die *VBPROJ*-Datei zum Unterdrücken bestimmter Compilerwarnungen bearbeiten.

1. Wählen Sie im **Projektmappen-Explorer** das Projekt aus, in dem Sie Warnungen unterdrücken möchten.

1. Wählen Sie in der Menüleiste **Projekt** > **Projekt entladen** aus.

1. Öffnen Sie im **Projektmappen-Explorer** per Rechtsklick das Kontextmenü für das Projekt, und klicken Sie dann auf **\<ProjectName>.vbproj bearbeiten**.

    Die XML-Projektdatei wird im Code-Editor geöffnet.

1. Suchen Sie nach dem `<NoWarn>`-Element für die Buildkonfiguration, mit der Sie arbeiten, und fügen Sie eine oder mehrere Warnungsnummern als Wert des `<NoWarn>`-Elements hinzu. Wenn Sie mehrere Warnungsnummern angeben, trennen Sie diese durch Kommas.

     Das folgende Beispiel zeigt das Element `<NoWarn>` für die *Debug*-Buildkonfiguration auf einer x86-Plattform, bei der zwei Compilerwarnungen unterdrückt sind:

    ```xml
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86' ">
        <PlatformTarget>x86</PlatformTarget>
        <DebugSymbols>true</DebugSymbols>
        <DebugType>full</DebugType>
        <Optimize>false</Optimize>
        <OutputPath>bin\Debug\</OutputPath>
        <DefineDebug>true</DefineDebug>
        <DefineTrace>true</DefineTrace>
        <ErrorReport>prompt</ErrorReport>
        <NoWarn>40059,42024</NoWarn>
        <WarningLevel>1</WarningLevel>
      </PropertyGroup>
    ```

   > [!NOTE]
   > .NET Core-Projekte enthalten standardmäßig keine Eigenschaftengruppen für die Buildkonfiguration. Um Warnungen in einem .NET Core-Projekt zu unterdrücken, fügen sie der Datei den Abschnitt für die Buildkonfiguration manuell hinzu. Zum Beispiel:
   >
   > ```xml
   > <Project Sdk="Microsoft.NET.Sdk">
   >   <PropertyGroup>
   >     <OutputType>Exe</OutputType>
   >     <TargetFramework>netcoreapp2.0</TargetFramework>
   >     <RootNamespace>VBDotNetCore_1</RootNamespace>
   >   </PropertyGroup>
   >   <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
   >     <NoWarn>42016,41999,42017</NoWarn>
   >   </PropertyGroup>
   > </Project>
   > ```

1. Speichern Sie die Änderungen an der *VBPROJ*-Datei.

1. Wählen Sie in der Menüleiste **Projekt** > **Projekt erneut laden** aus.

1. Wählen Sie in der Menüleiste **Erstellen** > **Projektmappe neu erstellen** aus.

    Das Fenster **Ausgabe** zeigt die von Ihnen angegebenen Warnungen jetzt nicht mehr an.

Weitere Informationen finden Sie im Abschnitt zur [Compileroption /nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) für den Visual Basic-Befehlszeilencompiler.

## <a name="suppress-warnings-for-nuget-packages"></a>Unterdrücken von Warnungen für NuGet-Pakete

In einigen Fällen möchten Sie möglicherweise NuGet-Compilerwarnungen nicht für ein gesamtes Projekt, sondern nur für ein einzelnes NuGet-Paket unterdrücken. Diese Warnungen erfüllen einen Zweck, deshalb sollten sie nicht auf Projektebene unterdrückt werden. Beispielsweise könnten Sie in einer der NuGet-Warnungen darüber informiert werden, dass das Paket nicht vollständig mit Ihrem Projekt kompatibel ist. Wenn Sie die Warnung auf Projektebene unterdrücken und später ein weiteres NuGet-Paket hinzufügen, wissen Sie nie, ob die Kompatibilitätswarnung von diesem Paket ausgelöst wurde.

### <a name="to-suppress-a-specific-warning-for-a-single-nuget-package"></a>So unterdrücken Sie eine bestimmte Warnung für ein einzelnes NuGet-Paket

1. Wählen Sie im **Projektmappen-Explorer** das NuGet-Paket aus, für das Sie Compilerwarnungen unterdrücken möchten.

   ![NuGet-Paket im Projektmappen-Explorer](media/nuget-package-with-warning.png)

1. Wählen Sie im Kontextmenü (Rechtsklick) **Eigenschaften** aus.

1. Geben Sie im Feld **NoWarn** der Paketeigenschaften die Warnungsnummer ein, die Sie für dieses Paket unterdrücken möchten. Wenn Sie mehr als eine Warnung unterdrücken möchten, verwenden Sie ein Komma zum Trennen der Warnungsnummern.

   ![NuGet-Paketeigenschaften](media/nuget-properties-nowarn.png)

   Die Warnung wird im **Projektmappen-Explorer** und in der **Fehlerliste** nicht mehr angezeigt.

## <a name="see-also"></a>Siehe auch

- [Exemplarische Vorgehensweise: Erstellen einer Anwendung](../ide/walkthrough-building-an-application.md)
- [How to: Anzeigen, Speichern und Konfigurieren von Buildprotokolldateien](../ide/how-to-view-save-and-configure-build-log-files.md)
- [Kompilieren und Erstellen](../ide/compiling-and-building-in-visual-studio.md)
