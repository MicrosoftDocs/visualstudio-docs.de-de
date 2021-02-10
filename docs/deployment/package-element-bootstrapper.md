---
title: '&lt;Package- &gt; Element (Boots Trapper) | Microsoft-Dokumentation'
description: Das Package-Element ist das XML-Element der obersten Ebene in einer Paketdatei. Das Paket Element ist erforderlich.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <package> element [bootstrapper]
ms.assetid: ecd06658-ad02-4440-bccd-88437b7fb816
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2ddb1feb3e5234b26e2ebceb9f899554d55b3015
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940344"
---
# <a name="ltpackagegt-element-bootstrapper"></a>&lt;Package- &gt; Element (Boots Trapper)
Das `Package` -Element ist das XML-Element der obersten Ebene in einer Paketdatei.

## <a name="syntax"></a>Syntax

```xml
<Package
    Culture
    Name
    LicenseAgreement
>
    <InstallChecks>
        <AssemblyCheck
            Property
            Name
            PublicKeyToken
            Version
            Language
            ProcessorArchitecture
        />
        <RegistryCheck
            Property
            Key
            Value
        />
        <ExternalCheck
            PackageFile
            Property
            Arguments
            Log
        />
        <FileCheck
            Property
            FileName
            SearchPath
            SpecialFolder
            SearchDepth
        />
        <MsiProductCheck
            Property
            Product
            Feature
        />
        <RegistryFileCheck
            Property
            Key
            Value
            File
            SearchDepth
        />
    </InstallChecks>

    <Commands
        Reboot
    >
        <Command
            PackageFile
            Arguments
            EstimatedInstallSeconds
            EstimatedDiskBytes
            EstimatedTempBytes
            Log
        >
            <InstallConditions>
                <BypassIf
                    Property
                    Compare
                    Value
                    Schedule
                />
                <FailIf
                    Property
                    Compare
                    Value
                    String
                    Schedule
                />
            </InstallConditions>
            <ExitCodes>
                <ExitCode
                    Value
                    Result
                    String
                />
            </ExitCodes>
        </Command>
    </Commands>

    <PackageFiles
        CopyAllComponents
    >
        <PackageFile
            Name
            Path
            HomeSite
            PublicKey
        />
    </PackageFiles>

    <Strings>
        <String
            Name
        >
        </String>
    </Strings>

    <Schedules>
        <Schedule
            Name
        >
           <BuildList />
           <BeforePackage />
           <AfterPackage />
        </Schedule>
    </Schedules>
</Package>
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Das `Package`-Element ist erforderlich. Es verfügt über die folgenden Attribute:

| attribute | Beschreibung |
|--------------------| - |
| `Culture` | Erforderlich. Definiert die Kultur für dieses Paket, das die zu verwendende Sprache bestimmt. Dieses Attribut ist ein Schlüssel für das- `Strings` Element, das kulturspezifische Zeichen folgen für Produktnamen und Fehlermeldungen während der Installation auflistet. |
| `Name` | Erforderlich. Der Name des Pakets, das dem Entwickler in einem Tool wie angezeigt wird [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Dieses Attribut ist ein Schlüssel in das- `Strings` Element, das ein-Element enthalten sollte, dessen-Eigenschaft und-Eigenschaft `String` entsprechend `Name` `Culture` den `Name` -und-Eigenschaften von festgelegt werden `Culture` `Package` . |
| `LicenseAgreement` | Dies ist optional. Gibt den Namen der Datei im Verteilungs Paket an, die den End-User Lizenzvertrag (EULA) enthält.  Bei dieser Datei kann es sich entweder um *Klartext (* (*RTF*) |

## <a name="example"></a>Beispiel
 Das folgende Codebeispiel zeigt eine komplette Paketdatei zum erneuten Verteilen des .NET Framework 2,0.

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Package
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
  Name="DisplayName"
  Culture="Culture"
  LicenseAgreement="eula.rtf"
>

    <PackageFiles>
        <PackageFile Name="eula.rtf"/>
    </PackageFiles>

    <!-- Defines a localizable string table for error messages-->
    <Strings>
        <String Name="DisplayName">.NET Framework 2.0</String>
        <String Name="Culture">en</String>
        <String Name="AdminRequired">Administrator permissions are required to install the .NET Framework 2.0. Contact your administrator.</String>
        <String Name="InvalidPlatformWin9x">Installation of the .NET Framework 2.0 is not supported on Windows 95. Contact your application vendor.</String>
        <String Name="InvalidPlatformWinNT">Installation of the .NET Framework 2.0 is not supported on Windows NT 4.0. Contact your application vendor.</String>
        <String Name="InvalidPlatformIE">Installation of the .NET Framework 2.0 requires Internet Explorer 5.01 or greater. Contact your application vendor.</String>
        <String Name="InvalidPlatformArchitecture">This version of the .NET Framework 2.0 is not supported on a 64-bit operating system. Contact your application vendor.</String>
        <String Name="WindowsInstallerImproperInstall">Due to an error with Windows Installer, the installation of the .NET Framework 2.0 cannot proceed.</String>
        <String Name="AnotherInstanceRunning">Another instance of setup is already running. The running instance must complete before this setup can proceed.</String>
        <String Name="BetaNDPFailure">A beta version of the .NET Framework was detected on the computer. Uninstall any previous beta versions of .NET Framework before continuing.</String>
        <String Name="GeneralFailure">A failure occurred attempting to install the .NET Framework 2.0.</String>
        <String Name="DotNetFXExe">http://go.microsoft.com/fwlink/?LinkId=37283</String>
        <String Name="InstMsiAExe">http://go.microsoft.com/fwlink/?LinkId=37285</String>
        <String Name="Msi30Exe">http://go.microsoft.com/fwlink/?LinkId=37287</String>
    </Strings>

</Package>
```

## <a name="see-also"></a>Weitere Informationen
- [Produkt-und Paket Schema Referenz](../deployment/product-and-package-schema-reference.md)