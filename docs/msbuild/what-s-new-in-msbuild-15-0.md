---
title: Neuerungen in MSBuild 15 | Microsoft-Dokumentation
description: Erfahren Sie mehr über geänderte, aktualisierte und neue Features von MSBuild 15, die für das .NET Core SDK und für das Entwickeln von .NET Core-Projekten unter Windows, macOS und Linux zur Verfügung stehen.
ms.custom: SEO-VS-2020
ms.date: 03/01/2017
ms.topic: conceptual
ms.assetid: 9976b6fd-d052-4017-b848-35b5bf4b2f66
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2017'
ms.openlocfilehash: 3ab22ac92cdf995c56d8244225a45fc350e9d360
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047805"
---
# <a name="whats-new-in-msbuild-15"></a>Neues in MSBuild 15

MSBuild ist jetzt als Teil des [.NET Core SDK](https://www.microsoft.com/net/download/core) verfügbar und ermöglicht die Erstellung von .NET Core-Projekten unter Windows, macOS und Linux.

## <a name="changed-path"></a>Geänderter Pfad

 MSBuild wird jetzt in einem Ordner unterhalb der einzelnen Versionen von Visual Studio installiert. Z.B. *C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\MSBuild*. Sie können MSBuild auch mit dem folgenden PowerShell-Modul suchen: [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell).

 MSBuild wird nicht mehr im globalen Assemblycache installiert. Um programmgesteuert auf MSBuild zu verweisen, verwenden Sie NuGet-Pakete. Weitere Informationen finden Sie unter [Aktualisieren einer vorhandenen Anwendung für MSBuild 15.0](../msbuild/updating-an-existing-application.md).

## <a name="changed-properties"></a>Geänderte Eigenschaften

 Die folgenden MSBuild-Eigenschaften wurden aufgrund der neuen Versionsnummer aktualisiert.

- `MSBuildToolsVersion` für diese Version der Tools ist 15.0. Die Assemblyversion ist 15.1.0.0.

- `MSBuildToolsPath` weist keinen festgelegten Speicherort mehr auf. Standardmäßig befindet er sich im Ordner *MSBuild\15.0\Bin* relativ zum Visual Studio-Installationspfad. Der Visual Studio-Installationspfad kann jedoch zur Installationszeit geändert werden.

- `ToolsVersion`-Werte werden nicht mehr in der Registrierung festgelegt.

- Die Eigenschaften `SDK35ToolsPath` und `SDK40ToolsPath` verweisen auf das .NET Framework SDK, das mit dieser Version von Visual Studio geliefert wird (beispielsweise 10.0A für die 4.X-Tools).

## <a name="updates"></a>Updates

- Das [Project-Element](../msbuild/project-element-msbuild.md) verfügt über ein neues `SDK`-Attribut. Das `Xmlns`-Attribut ist zudem jetzt optional. Weitere Informationen zum `SDK`-Attribut finden Sie unter [Vorgehensweise: Verwenden von MSBuild-Projekt-SDKs](../msbuild/how-to-use-project-sdk.md), [Pakete, Metapakete und Frameworks](/dotnet/core/packages) und [Erweiterungen des CSPROJ-Formats für .NET Core](/dotnet/core/tools/csproj).
- Das [Item-Element](../msbuild/item-element-msbuild.md) verfügt außerhalb von Zielen über ein neues `Update`-Attribut. Auch die Einschränkung für das `Remove`-Attribut wurde entfernt.
- Bei *Directory.Build.props* handelt es sich um eine benutzerdefinierte Datei, die Anpassungen für Projekte in einem Verzeichnis bereitstellt. Diese Datei wird automatisch aus *Microsoft.Common.props* importiert, wenn die Eigenschaft `ImportDirectoryBuildTargets` nicht auf **FALSE** festgelegt wird. *Directory.Build.targets* wird durch *Microsoft.Common.targets* importiert.
- Alle Metadaten mit einem Namen, der der aktuellen Liste der Attribute nicht widerspricht, können optional als Attribut ausgedrückt werden. Weitere Informationen finden Sie unter [Item-Element](../msbuild/item-element-msbuild.md).

## <a name="new-property-functions"></a>Neue Eigenschaftenfunktionen

- `EnsureTrailingSlash` fügt einem Pfad einen nachgestellten Schrägstrich hinzu, falls keiner vorhanden ist.
- `NormalizePath` kombiniert Pfadelemente und stellt sicher, dass die ausgegebene Zeichenfolge die richtigen Verzeichnistrennzeichen für das aktuelle Betriebssystem aufweist.
- `NormalizeDirectory` kombiniert Pfadelemente, sorgt für die Verwendung eines nachgestellten Schrägstrichs und stellt sicher, dass die ausgegebene Zeichenfolge die richtigen Verzeichnistrennzeichen für das aktuelle Betriebssystem aufweist.
- `GetPathOfFileAbove` gibt den Pfad der unmittelbar vorangehenden Datei zurück. Dies ist zum Aufruf von `<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />` funktional äquivalent.

## <a name="see-also"></a>Weitere Informationen

- [MSBuild](../msbuild/msbuild.md)
