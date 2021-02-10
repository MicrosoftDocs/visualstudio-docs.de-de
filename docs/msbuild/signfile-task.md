---
title: SignFile-Aufgabe| Microsoft-Dokumentation
description: Erfahren Sie, wie MSBuild mithilfe der Aufgabe „SignFile“ die angegebene Datei mit dem angegebenen Zertifikat signiert.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#SignFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, SignFile task
- SignFile task [MSBuild]
ms.assetid: edef1819-ddeb-4e09-95de-fc7063ba9388
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9eef76a3757d9a2ff8ece5da5c18968097bd7618
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878161"
---
# <a name="signfile-task"></a>SignFile-Aufgabe

Signiert die angegebene Datei mit dem angegebenen Zertifikat.

## <a name="parameters"></a>Parameter

 In der folgenden Tabelle werden die Parameter der `SignFile` -Aufgabe beschrieben.

 Beachten Sie, dass SHA-256-Zertifikate nur auf Computern zulässig sind, auf denen .NET 4.5 und höher installiert ist.

> [!WARNING]
> Ab Visual Studio 2013 Update 3 hat diese Aufgabe eine neue Signatur, mit der Sie die Zielframeworkversion für die Datei angeben können. Sie sollen die neue Signatur verwenden, wo immer möglich, weil der MSBuild-Prozess SHA-256-Hashes nur dann verwendet, wenn das Zielframework .NET 4.5 oder höher ist. Wenn das Zielframework .NET 4.0 oder älter ist, wird der SHA-256-Hash nicht verwendet.

|Parameter|Beschreibung|
|---------------|-----------------|
|`CertificateThumbprint`|Erforderlicher `String` -Parameter.<br /><br /> Gibt das zum Signieren zu verwendende Zertifikat an. Dieses Zertifikat muss sich im persönlichen Speicher des aktuellen Benutzers befinden.|
|`SigningTarget`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem> -Parameter.<br /><br /> Gibt die EXE- oder DLL-Dateien an, die mit dem Zertifikat signiert werden sollen.|
|`TimestampUrl`|Optionaler `String`-Parameter.<br /><br /> Gibt die URL eines Zeitstempelservers an.|
|`TargetFrameworkVersion`|Die Version des .NET Framework, die für das Ziel verwendet wird.|

## <a name="remarks"></a>Hinweise

 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Utilities.Task>-Klasse. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [Taskbasisklasse](../msbuild/task-base-class.md).

## <a name="example"></a>Beispiel

 Im folgenden Beispiel wird die `SignFile`-Aufgabe zum Signieren der Dateien verwendet, die in der `FilesToSign`-Elementauflistung mit dem in der `CertificateThumbprint`-Eigenschaft angegebenen Zertifikat angegeben werden.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <FileToSign Include="File.exe" />
    </ItemGroup>
    <PropertyGroup>
        <Certificate>Cert.cer</Certificate>
    </PropertyGroup>
    <Target Name="Sign">
        <SignFile
            CertificateThumbprint="$(CertificateThumbprint)"
            SigningTarget="@(FileToSign)"
            TargetFrameworkVersion="v4.5" />
    </Target>
</Project>
```

> [!NOTE]
> Der Zertifikatfingerabdruck ist der SHA1-Hash des Zertifikats. Weitere Informationen finden Sie unter [Abrufen des SHA-1-Hashs eines vertrauenswürdigen Stammzertifizierungsstellen-Zertifikats](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc733076\(v\=ws.10\)). Stellen Sie sicher, dass Sie das zusätzliche (3F) unsichtbare Zeichen beim Kopieren und Einfügen des Fingerabdrucks aus den Zertifikatdetails nicht kopieren, da dies verhindern kann, dass `SignFile` das Zertifikat findet.

## <a name="see-also"></a>Siehe auch

- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
- [Aufgaben](../msbuild/msbuild-tasks.md)