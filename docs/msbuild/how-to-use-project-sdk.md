---
title: 'Gewusst wie: Verweis auf MSBuild-Projekt-SDK | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie MSBuild-Projekt-SDKs nutzen, um die Verwendung von Software Development Kits zu vereinfachen, für die Eigenschaften und Ziele importiert werden müssen.
ms.custom: SEO-VS-2020
ms.date: 01/25/2018
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, SDKs, SDK
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e6303efce016a9e678e4c9e8aa62c91aa116e44f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914219"
---
# <a name="how-to-use-msbuild-project-sdks"></a>Vorgehensweise: Verwenden von MSBuild-Projekt SDKs

In MSBuild 15.0 wurde das Konzept des „Projekt-SDK“ eingeführt: Dadurch wurde die Verwendung von Software Development Kits vereinfacht, die das Importieren von Eigenschaften und Zielen erfordern.

```xml
<Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>
</Project>
```

Während der Auswertung des Projekts fügt MSBuild implizite Importe im oberen und unteren Bereich der Projektdatei hinzu:

```xml
<Project>
    <!-- Implicit top import -->
    <Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />

    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>

    <!-- Implicit bottom import -->
    <Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />
</Project>
```

## <a name="reference-a-project-sdk"></a>Verweisen auf ein Projekt SDK

Es gibt drei Möglichkeiten, auf ein Projekt SDK zu verweisen:

- Verwenden Sie das `Sdk`-Attribut des `<Project/>`-Elements:

    ```xml
    <Project Sdk="My.Custom.Sdk">
        ...
    </Project>
    ```

    Wie zuvor erläutert, wird im oberen bzw. unteren Bereich des Projekts ein impliziter Import hinzugefügt.
    
    Zum Angeben einer bestimmten SDK-Version fügen Sie die Version an das `Sdk`-Attribut an:

    ```xml
    <Project Sdk="My.Custom.Sdk/1.2.3">
        ...
    </Project>
    ```

- Verwenden Sie das `<Sdk/>`-Element der obersten Ebene:

    ```xml
    <Project>
        <Sdk Name="My.Custom.Sdk" Version="1.2.3" />
        ...
    </Project>
   ```

   Wie zuvor erläutert, wird im oberen bzw. unteren Bereich des Projekts ein impliziter Import hinzugefügt.
   
   Das `Version`-Attribut ist nicht erforderlich.

- Verwenden Sie das `<Import/>`-Element an einer beliebigen Stelle in Ihrem Projekt:

    ```xml
    <Project>
        <PropertyGroup>
            <MyProperty>Value</MyProperty>
        </PropertyGroup>
        <Import Project="Sdk.props" Sdk="My.Custom.Sdk" />
        ...
        <Import Project="Sdk.targets" Sdk="My.Custom.Sdk" />
    </Project>
   ```

   Explizites Einbeziehen der Importe in Ihr Projekt erlaubt Ihnen die vollständige Kontrolle über die Reihenfolge.

   Bei Verwendung des `<Import/>`-Elements können Sie auch ein optionales `Version`-Attribut angeben. Sie können z.B. `<Import Project="Sdk.props" Sdk="My.Custom.Sdk" Version="1.2.3" />` festlegen.

## <a name="how-project-sdks-are-resolved"></a>Lösen von Projekt SDKs

Beim Auswerten des Imports löst MSBuild den Pfad zum Projekt-SDK dynamisch anhand des Namens und der Version auf, die Sie angegeben haben.  MSBuild bietet auch eine Liste der registrierten SDK-Resolver. Dabei handelt es sich um Plug-Ins, die Projekt-SDKs auf Ihrem Computer suchen. Zu diesen Plug-Ins zählen:

- Ein NuGet-basierter Resolver, der Ihre konfigurierten Paketfeeds auf NuGet-Pakete abfragt, die der ID und Version des von Ihnen angegebenen SDK entsprechen.

   Dieser Resolver ist nur aktiv, wenn Sie eine optionale Version angegeben haben. Das Programm kann für jedes beliebige benutzerdefinierte Projekt-SDK verwendet werden.
   
- .NET SDK-Konfliktlöser, der MSBuild-SDKs auflöst, die mit dem [.NET SDK](/dotnet/core/sdk/) installiert wurden.

   Dieser Resolver sucht Projekt-SDKs wie z. B. `Microsoft.NET.Sdk` und `Microsoft.NET.Sdk.Web`, die Bestandteil des Produkts sind.
   
- Ein standardmäßiger Resolver, der mit MSBuild installierte SDKs auflöst.

Der NuGet-basierte SDK-Resolver unterstützt die Angabe einer Version in der Datei [global.json](/dotnet/core/tools/global-json). So können Sie die Projekt-SDK-Version zentral an einem Ort anstatt nur in einzelnen Projekten steuern:

```json
{
    "msbuild-sdks": {
        "My.Custom.Sdk": "5.0.0",
        "My.Other.Sdk": "1.0.0-beta"
    }
}
```

Nur eine Version jedes Projekt-SDK kann während eines Builds verwendet werden. Wenn Sie auf zwei unterschiedliche Versionen desselben Projekt-SDK verweisen, gibt MSBuild eine Warnung aus. Sie sollten **keine** Version in Ihren Projekten angeben, wenn die Datei *global.json* eine Versionsangabe enthält.

## <a name="see-also"></a>Weitere Informationen

- [MSBuild-Grundlagen](../msbuild/msbuild-concepts.md)
- [Customize your build (Anpassen Ihres Builds)](../msbuild/customize-your-build.md)
- [Pakete, Metadaten und Frameworks](/dotnet/core/packages)
- [Erweiterungen des CSPROJ-Formats für .NET Core](/dotnet/core/tools/csproj)
