---
title: MSBuild-Toolset (ToolsVersion) | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie unter Verwendung des Attributs „ToolsVersion“ in der MSBuild-Projektdatei ein Toolset mit Aufgaben, Zielen und Werkzeugen zum Erstellen einer Anwendung angeben.
ms.custom: SEO-VS-2020
ms.date: 01/31/2018
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, multitargeting
- targeting a specific .NET framework [MSBuild]
- MSBuild, targeting a specific .NET framework
- multitargeting [MSBuild]
ms.assetid: 40040ee7-4620-4043-a6d8-ccba921421d1
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b146913365583d49f1d70ebd5ca316f54ca89049
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878226"
---
# <a name="msbuild-toolset-toolsversion"></a>MSBuild-Toolset (ToolsVersion)

MSBuild verwendet ein Toolset von Aufgaben, Zielen und Tools für die Erstellung einer Anwendung. Ein MSBuild-Toolset umfasst in der Regel eine Datei mit allgemeinen Aufgaben (*microsoft.common.tasks*), eine Datei mit allgemeinen Zielen (*microsoft.common.targets*) und Compiler wie *csc.exe* und *vbc.exe*. Die meisten Toolsets können verwendet werden, um Anwendungen für mehr als eine Version von .NET Framework und mehr als eine Systemplattform zu kompilieren. Das Toolset MSBuild 2.0 kann allerdings nur für .NET Framework 2.0 verwendet werden.

## <a name="toolsversion-attribute"></a>ToolsVersion-Attribut

::: moniker range=">=vs-2019"
 Geben Sie das Toolset im Attribut `ToolsVersion` des [Project](../msbuild/project-element-msbuild.md)-Elements in der Projektdatei an. Das folgende Beispiel gibt an, dass das Projekt mit dem MSBuild-Toolset „Current“ erstellt werden soll.

```xml
<Project ToolsVersion="Current" ... </Project>
```

::: moniker-end

::: moniker range="vs-2017"
 Geben Sie das Toolset im Attribut `ToolsVersion` des [Project](../msbuild/project-element-msbuild.md)-Elements in der Projektdatei an. Das folgende Beispiel gibt an, dass das Projekt mit dem MSBuild 15.0-Toolset erstellt werden soll.

```xml
<Project ToolsVersion="15.0" ... </Project>
```

::: moniker-end

> [!NOTE]
> Einige Projekttypen verwenden das `sdk`-Attribut anstelle von `ToolsVersion`. Weitere Informationen finden Sie unter [Erweiterungen des CSPROJ-Formats für .NET Core](/dotnet/core/tools/csproj).

## <a name="how-the-toolsversion-attribute-works"></a>So funktioniert das ToolsVersion-Attribut

 Wenn Sie in Visual Studio ein Projekt erstellen oder ein vorhandenes Projekt aktualisieren, ist automatisch ein Attribut mit dem Namen `ToolsVersion` in der Projektdatei vorhanden, und sein Wert entspricht der Version von MSBuild, die in der Visual Studio-Edition enthalten ist. Weitere Informationen finden Sie unter [Übersicht über Frameworkziele](../ide/visual-studio-multi-targeting-overview.md).

 Wenn ein `ToolsVersion`-Wert in einer Projektdatei definiert wird, verwendet MSBuild diesen Wert, um die Werte der Toolseteigenschaften zu bestimmen, die für das Projekt verfügbar sind. Eine Toolseteigenschaft ist `$(MSBuildToolsPath)`, die den Pfad der .NET Framework-Tools angibt. Nur diese Toolseteigenschaft (oder `$(MSBuildBinPath)`) ist erforderlich.

 Ab Visual Studio 2013 ist die Version des MSBuild-Toolsets die gleiche wie die Visual Studio-Versionsnummer. MSBuild weist standardmäßig dieses Toolset in Visual Studio und in der Befehlszeile auf, unabhängig von der in der Projektdatei angegebenen Toolset-Version.  Dieses Verhalten kann durch Verwendung des -ToolsVersion-Flags überschrieben werden. Weitere Informationen erhalten Sie unter [Überschreiben der ToolsVersion-Einstellungen](../msbuild/overriding-toolsversion-settings.md).

 Im folgenden Beispiel findet MSBuild die *Microsoft.CSharp.targets*-Datei mithilfe der reservierten Eigenschaft `MSBuildToolsPath`.

```xml
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
```

 Sie können den Wert von `MSBuildToolsPath` ändern, indem Sie ein benutzerdefiniertes Toolset definieren. Weitere Informationen finden Sie unter [Standardmäßige und benutzerdefinierte Toolsetkonfigurationen](../msbuild/standard-and-custom-toolset-configurations.md).

 Wenn Sie eine Lösung in der Befehlszeile erstellen und eine `ToolsVersion` für *msbuild.exe* angeben, werden alle Projekte und ihre projektübergreifenden Abhängigkeiten entsprechend dieser `ToolsVersion` erstellt, auch wenn jedes Projekt in der Lösung seine eigene `ToolsVersion` angibt. Informationen dazu, wie Sie den `ToolsVersion`-Wert projektweise definieren, finden Sie unter [Überschreiben von ToolsVersion-Einstellungen](../msbuild/overriding-toolsversion-settings.md).

 Das Attribut `ToolsVersion` wird auch für die Projektmigration verwendet. Wenn Sie beispielsweise ein Visual Studio 2008-Projekt in Visual Studio 2010 öffnen, wird die Projektdatei so aktualisiert, dass die ToolsVersion="4.0" enthalten ist. Wenn Sie anschließend versuchen, das Projekt in Visual Studio 2008 zu öffnen, erkennt es nicht die aktualisierte `ToolsVersion` und erstellt das Projekt daher so, als wäre das Attribut noch auf 3.5 festgelegt.

 Visual Studio 2010 und Visual Studio 2012 verwenden beide die ToolsVersion 4.0. Visual Studio 2013 verwendet die ToolsVersion 12.0. Visual Studio 2015 verwendet ToolsVersion 14.0 und Visual Studio 2017 ToolsVersion 15.0. In vielen Fällen können Sie das Projekt in mehreren Versionen von Visual Studio ohne Änderung öffnen. Visual Studio verwendet immer das korrekte Toolset, Sie erhalten jedoch eine Benachrichtigung, wenn die verwendete Version nicht mit der Version in der Projektdatei übereinstimmt. In fast allen Fällen hat diese Warnung keine Auswirkungen, da die Toolsets meistens kompatibel sind.

 Mithilfe von Unter-Toolsets, die weiter unten in diesem Thema beschrieben werden, kann MSBuild je nach Kontext, in dem der Build ausgeführt wird, automatisch zwischen den Toolsets wechseln. Beispielsweise verwendet MSBuild in Visual Studio 2012 automatisch ein neueres Toolset als in Visual Studio 2010, ohne dass die Projektdatei explizit geändert werden muss.

## <a name="toolset-implementation"></a>Toolsetimplementierung

 Sie implementieren ein Toolset, indem Sie die Pfade der verschiedenen Tools, Ziele und Aufgaben auswählen, die das Toolset ausmachen. Die Tools im Toolset, das von MSBuild definiert wird, stammen aus den folgenden Quellen:

- .NET Framework-Ordner

- Zusätzliche verwaltete Tools

  Dazu zählen *ResGen.exe* und *TlbImp.exe*.

MSBuild bietet zwei Möglichkeiten, auf das Toolset zuzugreifen:

- Durch Verwendung von Toolseteigenschaften

- Durch Verwendung von <xref:Microsoft.Build.Utilities.ToolLocationHelper>-Methoden

In den Toolseteigenschaften sind die Pfade der Tools angegeben. Ab Visual Studio 2017 ist für MSBuild kein Speicherort mehr festgelegt. Standardmäßig befindet sich MSBuild im Ordner *MSBuild\15.0\Bin* relativ zum Installationsort von Visual Studio. In früheren Versionen verwendet MSBuild den Wert des `ToolsVersion`-Attributs in der Projektdatei, um den entsprechenden Registrierungsschlüssel zu suchen, und verwendet dann die Informationen im Registrierungsschlüssel, um die Toolseteigenschaften festzulegen. Wenn `ToolsVersion` z. B. den Wert `12.0` hat, dann legt MSBuild die Toolseteigenschaften entsprechend diesem Registrierungsschlüssel fest: **HKLM\Software\Microsoft\MSBuild\ToolsVersions\12.0**.

 Dies sind die Toolseteigenschaften:

- `MSBuildToolsPath` gibt den Pfad der MSBuild-Binärdateien an.

- `SDK40ToolsPath` gibt den Pfad der zusätzlichen verwalteten Tools für MSBuild 4.x (4.0 oder 4.5).

- `SDK35ToolsPath` gibt den Pfad der zusätzlichen verwalteten Tools für MSBuild 3,5 an.

Alternativ können Sie die Toolsets programmgesteuert bestimmen, indem Sie die Methoden der <xref:Microsoft.Build.Utilities.ToolLocationHelper>-Klasse aufrufen. Die Klasse beinhaltet diese Methoden:

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFramework%2A> gibt den Pfad des .NET Framework-Ordners zurück.

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkFile%2A> gibt den Pfad einer Datei im .NET Framework-Ordner zurück.

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdk%2A> gibt den Pfad des Ordners der verwalteten Tools zurück.

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdkFile%2A> gibt den Pfad einer Datei zurück, die sich in der Regel im Ordner mit verwalteten Tools befindet.

- [GetPathToBuildTools](/previous-versions/visualstudio/visual-studio-2013/dn251121(v=vs.121)) gibt den Pfad der Build-Tools zurück.

### <a name="sub-toolsets"></a>Unter-Toolsets

 In MSBuild-Versionen für Version 15.0 verwendet MSBuild einen Registrierungsschlüssel, um den Pfad der grundlegenden Tools anzugeben. Wenn der Schlüssel einen Unterschlüssel hat, verwendet MSBuild ihn, um den Pfad eines Unter-Toolsets anzugeben, das zusätzliche Tools enthält. In diesem Fall wird das Toolset definiert, indem die in beiden Schlüsseln definierten Eigenschaftendefinitionen kombiniert werden.

> [!NOTE]
> Wenn bei Toolseteigenschaftennamen Konflikte auftreten, überschreibt der Wert, der für den Unterschlüsselpfad definiert ist, den Wert, der für den Stammschlüsselpfad definiert ist.

 Unter-Toolsets werden bei Vorhandensein der Buildeigenschaft `VisualStudioVersion` aktiv. Diese Eigenschaft verwendet einen der folgenden Werte:

- "10.0" specifies the .NET Framework 4 sub-toolset

- "11.0" specifies the .NET Framework 4.5 sub-toolset

- "12.0" specifies the .NET Framework 4.5.1 sub-toolset

Die Unter-Toolsets 10.0 und 11.0 sollten mit der ToolsVersion 4.0 verwendet werden. In späteren Versionen sollten die Version der Unter-Toolsets und die ToolsVersion übereinstimmen.

Während eines Builds ermittelt MSBuild automatisch den Wert für die Eigenschaft `VisualStudioVersion` und legt einen Standardwert fest, wenn er noch nicht definiert ist.

MSBuild stellt Überladungen für die `ToolLocationHelper`-Methoden bereit, die einen `VisualStudioVersion`-Enumerationswert als Parameter hinzufügen.

Unter-Toolsets wurden in .NET Framework 4.5 eingeführt.

## <a name="see-also"></a>Siehe auch

- [Standardmäßige und benutzerdefinierte Toolsetkonfigurationen](../msbuild/standard-and-custom-toolset-configurations.md)
- [Festlegen von Zielversionen](../msbuild/msbuild-multitargeting-overview.md)
