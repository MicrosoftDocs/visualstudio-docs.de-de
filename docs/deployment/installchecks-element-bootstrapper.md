---
title: '&lt;InstallChecks- &gt; Element (Boots Trapper) | Microsoft-Dokumentation'
description: Das InstallChecks-Element unterstützt das Starten einer Vielzahl von Tests auf dem lokalen Computer, um sicherzustellen, dass alle Voraussetzungen für eine Anwendung installiert wurden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <InstallChecks> element [bootstrapper]
ms.assetid: ad329c87-b0ad-4304-84de-ae9496514c42
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 550baf52347c1128ef50509e7787861355c9428f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903402"
---
# <a name="ltinstallchecksgt-element-bootstrapper"></a>&lt;InstallChecks- &gt; Element (Boots Trapper)
Das- `InstallChecks` Element unterstützt das Starten einer Vielzahl von Tests auf dem lokalen Computer, um sicherzustellen, dass alle erforderlichen Voraussetzungen für eine Anwendung installiert wurden.

## <a name="syntax"></a>Syntax

```xml
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
        FileName
        SearchDepth
    />
</InstallChecks>
```

## <a name="assemblycheck"></a>AssemblyCheck
 Dieses Element ist ein optionales untergeordnetes Element von `InstallChecks` . `AssemblyCheck`Der Boots Trapper stellt für jede Instanz von sicher, dass die durch das-Element identifizierte Assembly im globalen Assemblycache (GAC) vorhanden ist. Sie enthält keine Elemente und verfügt über die folgenden Attribute.

|attribute|Beschreibung|
|---------------|-----------------|
|`Property`|Erforderlich. Der Name der Eigenschaft, in der das Ergebnis gespeichert werden soll. Auf diese Eigenschaft kann von einem Test unterhalb des- `InstallConditions` Elements verwiesen werden, das ein untergeordnetes `Command` Element des-Elements ist. Weitere Informationen finden Sie unter [\<Commands>Element](../deployment/commands-element-bootstrapper.md).|
|`Name`|Erforderlich. Der voll qualifizierte Name der zu Überprüfung enden Assembly.|
|`PublicKeyToken`|Erforderlich. Die abgekürzte Form des öffentlichen Schlüssels, der dieser Assembly mit starkem Namen zugeordnet ist. Alle im GAC gespeicherten Assemblys müssen einen Namen, eine Version und einen öffentlichen Schlüssel aufweisen.|
|`Version`|Erforderlich. Die Version der Assembly.<br /><br /> Die Versionsnummer hat das Format \<*major version*> . \<*minor version*> . \<*build version*> . \<*revision version*> .|
|`Language`|Dies ist optional. Die Sprache einer lokalisierten Assembly. Der Standardwert ist `neutral`.|
|`ProcessorArchitecture`|Dies ist optional. Der Computer Prozessor, der Ziel dieser Installation ist. Der Standardwert ist `msil`.|

## <a name="externalcheck"></a>ExternalCheck
 Dieses Element ist ein optionales untergeordnetes Element von `InstallChecks` . Für jede Instanz von `ExternalCheck` führt der Boots Trapper das benannte externe Programm in einem separaten Prozess aus und speichert den Exitcode in der durch angegebenen Eigenschaft `Property` . `ExternalCheck` ist nützlich, um komplexe Abhängigkeits Überprüfungen zu implementieren, oder wenn die einzige Möglichkeit zum Überprüfen, ob eine Komponente vorhanden ist, instanziiert wird.

 `ExternalCheck` enthält keine Elemente und verfügt über die folgenden Attribute.

|attribute|Beschreibung|
|---------------|-----------------|
|`Property`|Erforderlich. Der Name der Eigenschaft, in der das Ergebnis gespeichert werden soll. Auf diese Eigenschaft kann von einem Test unterhalb des- `InstallConditions` Elements verwiesen werden, das ein untergeordnetes `Command` Element des-Elements ist. Weitere Informationen finden Sie unter [\<Commands>Element](../deployment/commands-element-bootstrapper.md).|
|`PackageFile`|Erforderlich. Das auszuführende externe Programm. Das Programm muss Teil des Setup Verteilungs Pakets sein.|
|`Arguments`|Dies ist optional. Gibt Befehlszeilenargumente für die ausführbare Datei an, die von benannt wird `PackageFile` .|

## <a name="filecheck"></a>FileCheck
 Dieses Element ist ein optionales untergeordnetes Element von `InstallChecks` . Für jede Instanz von `FileCheck` bestimmt der Boots Trapper, ob die benannte Datei vorhanden ist, und gibt die Versionsnummer der Datei zurück. Wenn die Datei keine Versionsnummer hat, legt der Boots Trapper die Eigenschaft mit dem Namen `Property` auf 0 fest. Wenn die Datei nicht vorhanden ist, `Property` wird auf keinen Wert festgelegt.

 `FileCheck` enthält keine Elemente und verfügt über die folgenden Attribute.

| attribute | Beschreibung |
|-----------------| - |
| `Property` | Erforderlich. Der Name der Eigenschaft, in der das Ergebnis gespeichert werden soll. Auf diese Eigenschaft kann von einem Test unterhalb des- `InstallConditions` Elements verwiesen werden, das ein untergeordnetes `Command` Element des-Elements ist. Weitere Informationen finden Sie unter [\<Commands>Element](../deployment/commands-element-bootstrapper.md). |
| `FileName` | Erforderlich. Der Name der zu suchenden Datei. |
| `SearchPath` | Erforderlich. Der Datenträger oder Ordner, in dem nach der Datei gesucht werden soll. Dabei muss es sich um einen relativen Pfad handeln, wenn `SpecialFolder` zugewiesen wird. andernfalls muss es sich um einen absoluten Pfad handeln. |
| `SpecialFolder` | Dies ist optional. Ein Ordner, der für Windows oder für eine besondere Bedeutung hat [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Der Standardwert ist die Interpretation `SearchPath` als absoluter Pfad. Gültige Werte sind:<br /><br /> `AppDataFolder`. Der Anwendungsdatenordner für diese [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung, spezifisch für den aktuellen Benutzer.<br /><br /> `CommonAppDataFolder`. Der Ordner "Anwendungsdaten", der von allen Benutzern verwendet wird.<br /><br /> `CommonFilesFolder`. Der Ordner "gemeinsame Dateien" für den aktuellen Benutzer.<br /><br /> `LocalDataAppFolder`. Der Datenordner für nicht roaminganwendungen.<br /><br /> `ProgramFilesFolder`. Der standardmäßige Programmdateien-Ordner für 32-Bit-Anwendungen.<br /><br /> `StartUpFolder`. Der Ordner, der alle Anwendungen enthält, die beim Systemstart gestartet wurden.<br /><br /> `SystemFolder`. Der Ordner, der 32-Bit-System-DLLs enthält.<br /><br /> `WindowsFolder`. Der Ordner, der die Windows-Systeminstallation enthält.<br /><br /> `WindowsVolume`. Laufwerk oder Partition, das die Windows-Systeminstallation enthält. |
| `SearchDepth` | Dies ist optional. Die Tiefe, in der die Unterordner nach der benannten Datei durchsucht werden sollen. Die Suche erfolgt ausführlich. Der Standardwert ist 0, wodurch die Suche auf den Ordner der obersten Ebene beschränkt wird, der von `SpecialFolder` und **SearchPath** angegeben wird. |

## <a name="msiproductcheck"></a>MsiProductCheck
 Dieses Element ist ein optionales untergeordnetes Element von `InstallChecks` . Für jede Instanz von `MsiProductCheck` prüft der Boots Trapper, ob die angegebene Microsoft Windows Installer Installation bis zum Abschluss ausgeführt wurde. Der Eigenschafts Wert wird abhängig vom Status des installierten Produkts festgelegt. Ein positiver Wert gibt an, dass das Produkt installiert ist, 0 oder-1 gibt an, dass es nicht installiert ist. (Weitere Informationen finden Sie in der Windows Installer SDK-Funktion MsiQueryFeatureState.) . Wenn Windows Installer nicht auf dem Computer installiert ist, `Property` wird nicht festgelegt.

 `MsiProductCheck` enthält keine Elemente und verfügt über die folgenden Attribute.

|attribute|Beschreibung|
|---------------|-----------------|
|`Property`|Erforderlich. Der Name der Eigenschaft, in der das Ergebnis gespeichert werden soll. Auf diese Eigenschaft kann von einem Test unterhalb des- `InstallConditions` Elements verwiesen werden, das ein untergeordnetes `Command` Element des-Elements ist. Weitere Informationen finden Sie unter [\<Commands>Element](../deployment/commands-element-bootstrapper.md).|
|`Product`|Erforderlich. Die GUID für das installierte Produkt.|
|`Feature`|Dies ist optional. Der GUID für eine bestimmte Funktion der installierten Anwendung.|

## <a name="registrycheck"></a>RegistryCheck
 Dieses Element ist ein optionales untergeordnetes Element von `InstallChecks` . Für jede Instanz von `RegistryCheck` prüft der Boots Trapper, ob der angegebene Registrierungsschlüssel vorhanden ist oder ob er den angegebenen Wert aufweist.

 `RegistryCheck` enthält keine Elemente und verfügt über die folgenden Attribute.

|attribute|Beschreibung|
|---------------|-----------------|
|`Property`|Erforderlich. Der Name der Eigenschaft, in der das Ergebnis gespeichert werden soll. Auf diese Eigenschaft kann von einem Test unterhalb des- `InstallConditions` Elements verwiesen werden, das ein untergeordnetes `Command` Element des-Elements ist. Weitere Informationen finden Sie unter [\<Commands>Element](../deployment/commands-element-bootstrapper.md).|
|`Key`|Erforderlich. Der Name des Registrierungsschlüssels.|
|`Value`|Dies ist optional. Der Name des abzurufenden Registrierungs Werts. Standardmäßig wird der Text des Standardwerts zurückgegeben. `Value` muss entweder eine Zeichenfolge oder ein DWORD sein.|

## <a name="registryfilecheck"></a>RegistryFileCheck
 Dieses Element ist ein optionales untergeordnetes Element von `InstallChecks` . Für jede Instanz von `RegistryFileCheck` ruft der Boots Trapper die Version der angegebenen Datei ab und versucht zunächst, den Pfad zu der Datei aus dem angegebenen Registrierungsschlüssel abzurufen. Dies ist besonders nützlich, wenn Sie eine Datei in einem Verzeichnis suchen möchten, das als Wert in der Registrierung angegeben ist.

 `RegistryFileCheck` enthält keine Elemente und verfügt über die folgenden Attribute.

|attribute|Beschreibung|
|---------------|-----------------|
|`Property`|Erforderlich. Der Name der Eigenschaft, in der das Ergebnis gespeichert werden soll. Auf diese Eigenschaft kann von einem Test unterhalb des- `InstallConditions` Elements verwiesen werden, das ein untergeordnetes `Command` Element des-Elements ist. Weitere Informationen finden Sie unter [\<Commands>Element](../deployment/commands-element-bootstrapper.md).|
|`Key`|Erforderlich. Der Name des Registrierungsschlüssels. Der Wert wird als Pfad zu einer Datei interpretiert, es sei denn, das- `File` Attribut ist festgelegt. Wenn dieser Schlüssel nicht vorhanden ist, `Property` wird nicht festgelegt.|
|`Value`|Dies ist optional. Der Name des abzurufenden Registrierungs Werts. Standardmäßig wird der Text des Standardwerts zurückgegeben. `Value` muss eine Zeichenfolge sein.|
|`FileName`|Dies ist optional. Der Name einer Datei. Wenn angegeben, wird davon ausgegangen, dass es sich bei dem vom Registrierungsschlüssel erhaltenen Wert um einen Verzeichnispfad handelt und dieser Name angefügt wird. Wenn kein Wert angegeben wird, wird davon ausgegangen, dass der von der Registrierung zurückgegebene Wert der vollständige Pfad zu einer Datei ist.|
|`SearchDepth`|Dies ist optional. Die Tiefe, in der die Unterordner nach der benannten Datei durchsucht werden sollen. Die Suche erfolgt ausführlich. Der Standardwert ist 0, wodurch die Suche auf den Ordner der obersten Ebene beschränkt wird, der durch den Wert des Registrierungsschlüssels angegeben wird.|

## <a name="remarks"></a>Bemerkungen
 Während die untergeordneten Elemente die auszuführenden `InstallChecks` Tests definieren, werden Sie nicht ausgeführt. Zum Ausführen der Tests müssen Sie `Command` Elemente unterhalb des- `Commands` Elements erstellen.

## <a name="example"></a>Beispiel
 Im folgenden Codebeispiel wird das-Element veranschaulicht, das `InstallChecks` in der Produktdatei für die .NET Framework verwendet wird.

```xml
<InstallChecks>
    <ExternalCheck Property="DotNetInstalled" PackageFile="dotnetchk.exe" />
    <RegistryCheck Property="IEVersion" Key="HKLM\Software\Microsoft\Internet Explorer" Value="Version" />
</InstallChecks>
```

## <a name="installconditions"></a>InstallConditions
 Wenn `InstallChecks` ausgewertet wird, werden Eigenschaften erzeugt. Die Eigenschaften werden dann von verwendet, `InstallConditions` um zu bestimmen, ob ein Paket installiert, umgangen oder fehlschlägt. In der folgenden Tabelle sind die aufgeführt `InstallConditions` :

|Bedingung|Beschreibung|
|-|-|
|`FailIf`|Wenn eine `FailIf` Bedingung als "true" ausgewertet wird, schlägt das Paket fehl. Die restlichen Bedingungen werden nicht ausgewertet.|
|`BypassIf`|Wenn eine `BypassIf` Bedingung als "true" ausgewertet wird, wird das Paket umgangen. Die restlichen Bedingungen werden nicht ausgewertet.|

## <a name="predefined-properties"></a>Vordefinierte Eigenschaften
 In der folgenden Tabelle sind die `BypassIf` -und- `FailIf` Elemente aufgelistet:

|Eigenschaft|Notizen|Mögliche Werte|
|--------------|-----------|---------------------|
|`Version9X`|Versionsnummer eines Windows 9X-Betriebssystems.|4,10 = Windows 98|
|`VersionNT`|Versionsnummer eines Windows NT-basierten Betriebssystems.|Major.Minor.ServicePack<br /><br /> 5.0 = Windows 2000<br /><br /> 5.1.0 = Windows XP<br /><br /> 5.1.2 = Windows XP Professional SP2<br /><br /> 5.2.0 = Windows Server 2003|
|`VersionNT64`|Versionsnummer eines Windows NT-basierten 64-Bit-Betriebssystems.|Wie bereits erwähnt.|
|`VersionMsi`|Die Versionsnummer des Windows Installer Dienstanbieter.|2,0 = Windows Installer 2,0|
|`AdminUser`|Gibt an, ob ein Benutzer auf einem Windows NT-basierten Betriebssystem über Administratorrechte verfügt.|0 = keine Administratorrechte<br /><br /> 1 = Administratorrechte|

 Verwenden Sie z. b. folgenden Code, um die Installation auf einem Computer zu blockieren, auf dem Windows 95 ausgeführt wird:

```xml
    <!-- Block install on Windows 95 -->
    <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatform"/>
```

 Um das Ausführen von Installations Prüfungen zu überspringen, wenn eine FailIf-oder BypassIf-Bedingung erfüllt ist, verwenden Sie das beforeinstallchecks-Attribut.  Beispiel:

```xml
    <!-- Block install and do not evaluate install checks if user does not have admin privileges -->
    <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired" BeforeInstallChecks="true"/>
```

>[!NOTE]
>Das- `BeforeInstallChecks` Attribut wird ab dem Release von Visual Studio 2019 Update 9 unterstützt.

## <a name="see-also"></a>Weitere Informationen
- [\<Commands>-Element](../deployment/commands-element-bootstrapper.md)
- [Produkt-und Paket Schema Referenz](../deployment/product-and-package-schema-reference.md)