---
title: '&lt;Commands- &gt; Element (Boots Trapper) | Microsoft-Dokumentation'
description: Das Commands-Element implementiert Tests in den Elementen unterhalb von InstallChecks und deklariert das zu installierende Paket, wenn der ClickOnce-bootstrappertest fehlschlägt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Commands> element [bootstrapper]
ms.assetid: e61d5787-fe1f-4ebf-b0cf-0d7909be7ffb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 65c63d52290962d8c9878edf025bbc05487103da
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383052"
---
# <a name="ltcommandsgt-element-bootstrapper"></a>&lt;Commands- &gt; Element (Boots Trapper)
Das `Commands` -Element implementiert Tests, die von den Elementen unterhalb des- `InstallChecks` Elements beschrieben werden, und deklariert das Paket, das der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Boots Trapper installieren soll, wenn der Test fehlschlägt.

## <a name="syntax"></a>Syntax

```xml
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
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Das `Commands`-Element ist erforderlich. Das Element weist das folgende Attribut auf.

|attribute|Beschreibung|
|---------------|-----------------|
|`Reboot`|Optional. Bestimmt, ob das System neu gestartet werden soll, wenn eines der Pakete einen Neustart-Exitcode zurückgibt. In der folgenden Liste werden die gültigen Werte angezeigt:<br /><br /> `Defer`. Der Neustart wird bis zu einem späteren Zeitpunkt verzögert.<br /><br /> `Immediate`. Verursacht einen sofortigen Neustart, wenn eines der Pakete einen Neustart-Exitcode zurückgegeben hat.<br /><br /> `None`. Bewirkt, dass alle Neustart Anforderungen ignoriert werden.<br /><br /> Der Standardwert ist `Immediate`.|

## <a name="command"></a>Get-Help
 Das `Command`-Element ist ein untergeordnetes Element des `Commands`-Elements. Ein- `Commands` Element kann ein oder mehrere- `Command` Elemente aufweisen. Das Element weist folgende Attribute auf.

|attribute|Beschreibung|
|---------------|-----------------|
|`PackageFile`|Erforderlich. Der Name des zu installierenden Pakets, wenn eine oder mehrere der durch angegebenen Bedingungen `InstallConditions` false zurückgeben. Das Paket muss in derselben Datei mit einem-Element definiert werden `PackageFile` .|
|`Arguments`|Optional. Ein Satz von Befehlszeilen Argumenten, die an die Paketdatei übergeben werden sollen.|
|`EstimatedInstallSeconds`|Optional. Die geschätzte Zeit (in Sekunden), die für die Installation des Pakets benötigt wird. Dieser Wert bestimmt die Größe der Statusanzeige, die der Boots Trapper dem Benutzer anzeigt. Der Standardwert ist 0 (null). in diesem Fall wird keine Zeit Schätzung angegeben.|
|`EstimatedDiskBytes`|Optional. Die geschätzte Menge an Speicherplatz (in Bytes), die das Paket nach Abschluss der Installation einnimmt. Dieser Wert wird bei Anforderungen an den Festplatten Speicherplatz verwendet, die dem Benutzer vom Boots Trapper angezeigt werden. Der Standardwert ist 0 (null). in diesem Fall zeigt der Boots Trapper keine Anforderungen an den Festplatten Speicherplatz an.|
|`EstimatedTempBytes`|Optional. Die geschätzte Menge an temporärem Speicherplatz (in Bytes), die das Paket benötigt.|
|`Log`|Optional. Der Pfad zu der Protokolldatei, die das Paket generiert, relativ zum Stammverzeichnis des Pakets.|

## <a name="installconditions"></a>InstallConditions
 Das- `InstallConditions` Element ist ein untergeordnetes `Command` Element des-Elements. Jedes `Command` Element kann höchstens ein Element aufweisen `InstallConditions` . Wenn kein- `InstallConditions` Element vorhanden ist, wird das von angegebene Paket `Condition` immer ausgeführt.

## <a name="bypassif"></a>BypassIf
 Das `BypassIf` -Element ist ein untergeordnetes `InstallConditions` Element des-Elements und beschreibt eine positive Bedingung, unter der der Befehl nicht ausgeführt werden soll. Jedes `InstallConditions` Element kann über 0 (null) oder mehr `BypassIf` Elemente verfügen.

 `BypassIf` weist die folgenden Attribute auf.

|attribute|Beschreibung|
|---------------|-----------------|
|`Property`|Erforderlich. Der Name der zu testenden Eigenschaft. Die-Eigenschaft muss zuvor durch ein untergeordnetes Element des-Elements definiert worden sein `InstallChecks` . Weitere Informationen finden Sie unter [\<InstallChecks>Element](../deployment/installchecks-element-bootstrapper.md).|
|`Compare`|Erforderlich. Der Typ des auszuführenden Vergleichs. In der folgenden Liste werden die gültigen Werte angezeigt:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|
|`Value`|Erforderlich. Der Wert, der mit der Eigenschaft verglichen werden soll.|
|`Schedule`|Optional. Der Name eines `Schedule` Tags, der definiert, wann diese Regel ausgewertet werden soll.|

## <a name="failif"></a>FailIf
 Das `FailIf` -Element ist ein untergeordnetes Element des `InstallConditions` -Elements und beschreibt eine positive Bedingung, unter der die Installation beendet werden soll. Jedes `InstallConditions` Element kann über 0 (null) oder mehr `FailIf` Elemente verfügen.

 `FailIf` weist die folgenden Attribute auf.

|attribute|Beschreibung|
|---------------|-----------------|
|`Property`|Erforderlich. Der Name der zu testenden Eigenschaft. Die-Eigenschaft muss zuvor durch ein untergeordnetes Element des-Elements definiert worden sein `InstallChecks` . Weitere Informationen finden Sie unter [\<InstallChecks>Element](../deployment/installchecks-element-bootstrapper.md).|
|`Compare`|Erforderlich. Der Typ des auszuführenden Vergleichs. In der folgenden Liste werden die gültigen Werte angezeigt:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|
|`Value`|Erforderlich. Der Wert, der mit der Eigenschaft verglichen werden soll.|
|`String`|Optional. Der Text, der dem Benutzer bei einem Fehler angezeigt werden soll.|
|`Schedule`|Optional. Der Name eines `Schedule` Tags, der definiert, wann diese Regel ausgewertet werden soll.|

## <a name="exitcodes"></a>ExitCodes
 Das- `ExitCodes` Element ist ein untergeordnetes `Command` Element des-Elements. Das- `ExitCodes` Element enthält ein oder mehrere- `ExitCode` Elemente, die bestimmen, was die Installation als Reaktion auf einen Exitcode eines Pakets tun soll. Unterhalb eines-Elements kann ein optionales-Element vorhanden sein `ExitCode` `Command` . `ExitCodes` weist keine Attribute auf.

## <a name="exitcode"></a>ExitCode
 Das- `ExitCode` Element ist ein untergeordnetes `ExitCodes` Element des-Elements. Das- `ExitCode` Element bestimmt, was die Installation als Reaktion auf einen Exitcode aus einem Paket tun soll. `ExitCode` enthält keine untergeordneten Elemente und verfügt über die folgenden Attribute.

|attribute|Beschreibung|
|---------------|-----------------|
|`Value`|Erforderlich. Der Exitcodewert, auf den dieses `ExitCode` Element angewendet wird.|
|`Result`|Erforderlich. Gibt an, wie die Installation auf diesen Exitcode reagieren soll. In der folgenden Liste werden die gültigen Werte angezeigt:<br /><br /> `Success`. Gibt an, dass das Paket erfolgreich installiert wurde.<br /><br /> `SuccessReboot`. Gibt das Paket als erfolgreich installiert an und weist das System an, neu zu starten.<br /><br /> `Fail`. Markiert das Paket als fehlgeschlagen.<br /><br /> `FailReboot`. Gibt das Paket als fehlerhaft an und weist das System an, neu zu starten.|
|`String`|Optional. Der Wert, der dem Benutzer als Reaktion auf diesen Exitcode angezeigt werden soll.|
|`FormatMessageFromSystem`|Optional. Bestimmt, ob die vom System bereitgestellte Fehlermeldung verwendet werden soll, die dem Exitcode entspricht, oder verwendet den in bereitgestellten Wert `String` . Gültige Werte sind. Dies bedeutet, dass `true` der vom System bereitgestellte Fehler verwendet wird, und `false` , was bedeutet, dass die von bereitgestellte Zeichenfolge verwendet wird `String` . Der Standardwert ist `false`. Wenn diese Eigenschaft ist `false` , aber `String` nicht festgelegt ist, wird der vom System bereitgestellte Fehler verwendet.|

## <a name="example"></a>Beispiel
 Im folgenden Codebeispiel werden Befehle zum Installieren des .NET Framework 2,0 definiert.

```xml
<Commands Reboot="Immediate">
    <Command PackageFile="instmsia.exe"
             Arguments= ' /q /c:"msiinst /delayrebootq"'
             EstimatedInstallSeconds="20" >
        <InstallConditions>
           <BypassIf Property="VersionNT" Compare="ValueExists"/>
             BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="2.0"/>
        </InstallConditions>
        <ExitCodes>
            <ExitCode Value="0" Result="SuccessReboot"/>
            <ExitCode Value="1641" Result="SuccessReboot"/>
            <ExitCode Value="3010" Result="SuccessReboot"/>
            <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />
        </ExitCodes>
    </Command>
    <Command PackageFile="WindowsInstaller-KB884016-v2-x86.exe"
             Arguments= '/quiet /norestart'
             EstimatedInstallSeconds="20" >
      <InstallConditions>
          <BypassIf Property="Version9x" Compare="ValueExists"/>
          <BypassIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3"/>
          <BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="3.0"/>
          <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>
      </InstallConditions>
      <ExitCodes>
          <ExitCode Value="0" Result="Success"/>
          <ExitCode Value="1641" Result="SuccessReboot"/>
          <ExitCode Value="3010" Result="SuccessReboot"/>
          <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />
      </ExitCodes>
    </Command>
    <Command PackageFile="dotnetfx.exe"
         Arguments=' /q:a /c:"install /q /l"'
         EstimatedInstalledBytes="21000000"
         EstimatedInstallSeconds="300">

        <!-- These checks determine whether the package is to be installed -->
        <InstallConditions>
            <!-- Either of these properties indicates the .NET Framework is already installed -->
            <BypassIf Property="DotNetInstalled" Compare="ValueNotEqualTo" Value="0"/>

            <!-- Block install if user does not have adminpermissions -->
            <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>

            <!-- Block install on Windows 95 -->
            <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatformWin9x"/>

            <!-- Block install on Windows 2000 SP 2 or less -->
            <FailIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3" String="InvalidPlatformWinNT"/>

            <!-- Block install if Internet Explorer 5.01 or later is not present -->
            <FailIf Property="IEVersion" Compare="ValueNotExists" String="InvalidPlatformIE" />
            <FailIf Property="IEVersion" Compare="VersionLessThan" Value="5.01" String="InvalidPlatformIE" />

            <!-- Block install if the operating system does not support x86 -->
            <FailIf Property="ProcessorArchitecture" Compare="ValueNotEqualTo" Value="Intel" String="InvalidPlatformArchitecture" />
       </InstallConditions>

        <ExitCodes>
            <ExitCode Value="0" Result="Success"/>
            <ExitCode Value="3010" Result="SuccessReboot"/>
            <ExitCode Value="4097" Result="Fail" String="AdminRequired"/>
            <ExitCode Value="4098" Result="Fail" String="WindowsInstallerComponentFailure"/>
            <ExitCode Value="4099" Result="Fail" String="WindowsInstallerImproperInstall"/>
            <ExitCode Value="4101" Result="Fail" String="AnotherInstanceRunning"/>
            <ExitCode Value="4102" Result="Fail" String="OpenDatabaseFailure"/>
            <ExitCode Value="4113" Result="Fail" String="BetaNDPFailure"/>
            <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />
        </ExitCodes>

    </Command>
</Commands>
```

## <a name="see-also"></a>Siehe auch
- [Produkt-und Paket Schema Referenz](../deployment/product-and-package-schema-reference.md)
- [\<InstallChecks> gewisses](../deployment/installchecks-element-bootstrapper.md)