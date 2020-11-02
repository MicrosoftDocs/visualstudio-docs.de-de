---
title: GenerateApplicationManifest-Aufgabe | Microsoft-Dokumentation
description: Verwenden Sie die MSBuild-Aufgabe „GenerateApplicationManifest“, um ein ClickOnce-Anwendungsmanifest oder ein natives Manifest zu generieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateApplicationManifest
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateApplicationManifest task
- HostInBrowser property (MSBuild)
- GenerateApplicationManifest task [MSBuild]
ms.assetid: a494102b-0cb2-4755-8e2a-d2c0f39fac1d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c4752e4b736a6ba2f8b4a209824b22f94d8036c2
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436547"
---
# <a name="generateapplicationmanifest-task"></a>GenerateApplicationManifest-Aufgabe

Generiert ein ClickOnce-Anwendungsmanifest oder ein natives Manifest. Ein systemeigenes Manifest beschreibt eine Komponente, indem eine eindeutige Identität für die Komponente definiert wird und alle Assemblys und Dateien, aus denen die Komponente besteht, bezeichnet werden. Ein ClickOnce-Anwendungsmanifest erweitert ein systemeigenes Manifest durch die Angabe des Einstiegspunkts und der Sicherheitsebene der Anwendung.

## <a name="parameters"></a>Parameter

In der folgenden Tabelle werden die Parameter für die `GenerateApplicationManifest`-Aufgabe beschrieben.

| Parameter | Beschreibung |
|---------------------------------| - |
| `AssemblyName` | Optionaler `String`-Parameter.<br /><br /> Gibt das `Name`-Feld der Assemblyidentität für das generierte Manifest an. Wenn dieser Parameter nicht angegeben wird, wird der Name vom `EntryPoint`-Parameter oder `InputManifest`-Parameter abgeleitet. Wenn kein Name erstellt werden kann, löst die Aufgabe einen Fehler aus. |
| `AssemblyVersion` | Optionaler `String`-Parameter.<br /><br /> Gibt das `Version`-Feld der Assemblyidentität für das generierte Manifest an. Wenn dieser Parameter nicht angegeben wird, wird der Standardwert "1.0.0.0" verwendet. |
| `ClrVersion` | Optionaler `String`-Parameter.<br /><br /> Gibt die für die Anwendung erforderliche Mindestversion der Common Language Runtime (CLR) an. Der Standardwert ist die vom Buildsystem verwendete CLR-Version. Wenn die Aufgabe ein natives Manifest generiert, wird dieser Parameter ignoriert. |
| `ConfigFile` | Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Gibt an, welches Element die Anwendungskonfigurationsdatei enthält. Wenn die Aufgabe ein natives Manifest generiert, wird dieser Parameter ignoriert. |
| `Dependencies` | Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Gibt eine Elementliste an, die die abhängigen Assemblys für das generierte Manifest definiert. Jedes Element wird ggf. anhand von Elementmetadaten näher beschrieben, um zusätzlich den Bereitstellungszustand und den Typ der Abhängigkeit anzugeben. Weitere Informationen finden Sie unter [Elementmetadaten](#item-metadata). |
| `Description` | Optionaler `String`-Parameter.<br /><br /> Gibt die Beschreibung der Anwendung oder Komponente an. |
| `EntryPoint` | Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Gibt ein einzelnes Element an, das den Einstiegspunkt für die generierte Manifestassembly bezeichnet.<br /><br /> Bei einem ClickOnce-Anwendungsmanifest gibt dieser Parameter die Assembly an, die beim Ausführen der Anwendung gestartet wird. |
| `ErrorReportUrl` | Optionaler <xref:System.String?displayProperty=fullName>-Parameter.<br /><br /> Gibt die URL der Webseite an, die bei Fehlerberichten während ClickOnce-Installationen in den Dialogfeldern angezeigt wird. |
| `FileAssociations` | Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Gibt eine Liste mit mindestens einem Dateityp an, der dem ClickOnce-Bereitstellungsmanifest zugeordnet ist.<br /><br /> Dateizuordnungen sind nur gültig, wenn als Ziel .NET Framework 3.5 oder höher verwendet wird. |
| `Files` | Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Die Dateien, die in das Manifest eingeschlossen werden sollen. Geben Sie den vollständigen Pfad für jede Datei an. |
| `HostInBrowser` | Optionaler <xref:System.Boolean>-Parameter.<br /><br /> Bei `true` wird die Anwendung in einem Browser gehostet (wie WPF-Webbrowseranwendungen). |
| `IconFile` | Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Gibt die Anwendungssymboldatei an. Das Anwendungssymbol wird im generierten Anwendungsmanifest ausgedrückt und im **Startmenü** sowie im Dialogfeld **Software** verwendet. Erfolgt diese Angabe nicht, wird ein Standardsymbol verwendet. Wenn die Aufgabe ein natives Manifest generiert, wird dieser Parameter ignoriert. |
| `InputManifest` | Optionaler <xref:Microsoft.Build.Framework.ITaskItem>-Parameter.<br /><br /> Gibt ein Eingabe-XML-Dokument an, das als Basis für den Manifestgenerator dienen soll. Dadurch können strukturierte Daten, z. B. für Anwendungssicherheit oder benutzerdefinierte Manifestdefinitionen, im Ausgabemanifest dargestellt werden. Das Stammelement im XML-Dokument muss ein Assemblyknoten im "asmv1"-Namespace sein. |
| `IsolatedComReferences` | Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Gibt COM-Komponenten an, die im generierten Manifest isoliert werden sollen. Dieser Parameter unterstützt das Isolieren von COM-Komponenten für die Bereitstellung über "COM-Interop ohne Registrierung". Zu diesem Zweck wird automatisch ein Manifest mit standardmäßigen COM-Registrierungsdefinitionen generiert. Die COM-Komponenten müssen jedoch auf dem Buildcomputer registriert werden, damit dies ordnungsgemäß funktioniert. |
| `ManifestType` | Optionaler `String`-Parameter.<br /><br /> Gibt an, welcher Manifesttyp generiert werden soll. Dieser Parameter kann die folgenden Werte aufweisen:<br /><br /> -   `Native`<br />-   `ClickOnce`<br /><br /> Wird dieser Parameter nicht angegeben, verwendet die Aufgabe standardmäßig `ClickOnce`. |
| `MaxTargetPath` | Optionaler `String`-Parameter.<br /><br /> Gibt die maximal zulässige Länge eines Dateipfads in einer ClickOnce-Anwendungsbereitstellung an. Wenn dieser Wert angegeben wird, wird die Länge jedes Dateipfads in der Anwendung mit dem Grenzwert verglichen. Alle Elemente, die den Grenzwert übersteigen, lösen eine Buildwarnung aus. Wenn dieser Parameter nicht angegeben wird oder den Wert 0 (null) hat, wird keine Prüfung ausgeführt. Wenn die Aufgabe ein natives Manifest generiert, wird dieser Parameter ignoriert. |
| `OSVersion` | Optionaler `String`-Parameter.<br /><br /> Gibt die für die Anwendung mindestens erforderliche Betriebssystemversion an. Der Wert "5.1.2600.0" gibt z. B. an, dass es sich um das Betriebssystem Windows XP handelt. Wenn dieser Parameter nicht angegeben wird, wird der Wert "4.10.0.0" verwendet, der Windows 98 Zweite Ausgabe bezeichnet, also das Betriebssystem, das für .Net Framework mindestens erforderlich ist. Wenn die Aufgabe ein natives Manifest generiert, wird diese Eingabe ignoriert. |
| `OutputManifest` | Optionaler <xref:Microsoft.Build.Framework.ITaskItem>-Ausgabeparameter.<br /><br /> Gibt den Namen der generierten Ausgabemanifestdatei an. Wenn dieser Parameter nicht angegeben wird, wird der Name der Ausgabedatei von der Identität des generierten Manifests abgeleitet. |
| `Platform` | Optionaler `String`-Parameter.<br /><br /> Gibt die Zielplattform für die Anwendung an. Dieser Parameter kann die folgenden Werte aufweisen:<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> Wird dieser Parameter nicht angegeben, verwendet die Aufgabe standardmäßig `AnyCPU`. |
| `Product` | Optionaler `String`-Parameter.<br /><br /> Gibt den Namen der Anwendung an. Wenn dieser Parameter nicht angegeben wird, wird der Name von der Identität des generierten Manifests abgeleitet. Dieser Name wird für die Verknüpfung im **Startmenü** verwendet und ist Teil des Namens, der im Dialogfeld **Software** angezeigt wird. |
| `Publisher` | Optionaler `String`-Parameter.<br /><br /> Gibt den Herausgeber der Anwendung an. Wenn dieser Parameter nicht angegeben ist, wird der Name vom registrierten Benutzer oder von der Identität des generierten Manifests abgeleitet. Dieser Name wird für den Ordnernamen im **Startmenü** verwendet und ist Teil des Namens, der im Dialogfeld **Software** angezeigt wird. |
| `RequiresMinimumFramework35SP1` | Optionaler `Boolean`-Parameter.<br /><br /> Bei "true" ist für die Anwendung .NET Framework 3.5 SP1 oder eine aktuellere Version erforderlich. |
| `TargetCulture` | Optionaler `String`-Parameter.<br /><br /> Identifiziert die Kultur der Anwendung und gibt das `Language`-Feld der Assemblyidentität für das generierte Manifest an. Wenn dieser Parameter nicht angegeben ist, wird davon ausgegangen, dass die Anwendung kulturunabhängig ist. |
| `TargetFrameworkMoniker` | Optionaler `String`-Parameter.<br /><br /> Gibt den Zielframeworkmoniker an. |
| `TargetFrameworkProfile` | Optionaler `String`-Parameter.<br /><br /> Gibt das Zielframeworkprofil an. |
| `TargetFrameworkSubset` | Optionaler `String`-Parameter.<br /><br /> Gibt den Namen der .NET Framework-Teilmenge an, auf die abgezielt wird. |
| `TargetFrameworkVersion` | Optionaler `String`-Parameter.<br /><br /> Gibt das .NET Framework-Ziel des Projekts an. |
| `TrustInfoFile` | Optionaler <xref:Microsoft.Build.Framework.ITaskItem>-Parameter.<br /><br /> Bezeichnet ein XML-Dokument, das die Anwendungssicherheit angibt. Das Stammelement im XML-Dokument muss ein trustInfo-Knoten im asmv2-Namespace sein. Wenn die Aufgabe ein natives Manifest generiert, wird dieser Parameter ignoriert. |
| `UseApplicationTrust` | Optionaler `Boolean`-Parameter.<br /><br /> Bei "true" werden die Eigenschaften `Product`, `Publisher` und `SupportUrl` in das Anwendungsmanifest geschrieben. |

## <a name="remarks"></a>Hinweise

Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.GenerateManifestBase>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste der Parameter der Aufgabenklasse finden Sie unter [Task-Basisklasse](../msbuild/task-base-class.md).

Weitere Informationen zum Verwenden der `GenerateDeploymentManifest`-Aufgabe finden Sie unter [GenerateApplicationManifest-Aufgabe](../msbuild/generateapplicationmanifest-task.md).

Die Eingaben für Abhängigkeiten und Dateien können um Elementmetadaten ergänzt werden, die zusätzlich den Bereitstellungszustand für jedes Element angeben.

## <a name="item-metadata"></a>Elementmetadaten

|Metadatenname|Beschreibung|
|-------------------|-----------------|
|`DependencyType`|Gibt an, ob die Abhängigkeit veröffentlicht und mit der Anwendung installiert wird oder als erforderliche Komponente vorhanden sein muss. Diese Metadaten sind für alle Abhängigkeiten gültig, werden für Dateien jedoch nicht verwendet. Für diese Metadaten sind folgende Werte verfügbar:<br /><br /> -   `Install`<br />-   `Prerequisite`<br /><br /> Der Standardwert lautet "Install".|
|`AssemblyType`|Gibt an, ob die Abhängigkeit eine verwaltete oder eine systemeigene Assembly ist. Diese Metadaten sind für alle Abhängigkeiten gültig, werden für Dateien jedoch nicht verwendet. Für diese Metadaten sind folgende Werte verfügbar:<br /><br /> -   `Managed`<br />-   `Native`<br />-   `Unspecified`<br /><br /> Der Standardwert lautet `Unspecified`. Er gibt an, dass der Manifest-Generator den Assemblytyp automatisch bestimmt.|
|`Group`|Gibt die Gruppe für den bedarfsabhängigen Download zusätzlicher Dateien an. Der Gruppenname wird von der Anwendung definiert und kann eine beliebige Zeichenfolge sein. Eine leere Zeichenfolge gibt an, dass die Datei nicht zu einer Downloadgruppe gehört. Dies ist die Standardeinstellung. Dateien, die nicht zu einer Gruppe gehören, sind Teil des anfänglichen Anwendungsdownloads. Dateien in einer Gruppe werden nur heruntergeladen, wenn die Anwendung diese mit <xref:System.Deployment.Application> explizit anfordert.<br /><br /> Diese Metadaten gelten für alle Dateien, bei denen `IsDataFile` den Wert `false` aufweist, und für alle Abhängigkeiten, bei denen `DependencyType` den Wert `Install` aufweist.|
|`TargetPath`|Gibt an, wie der Pfad im generierten Manifest definiert werden soll. Dieses Attribut ist für alle Dateien gültig. Wenn dieses Attribut nicht angegeben wird, wird die Elementspezifikation verwendet. Dieses Attribut gilt für alle Dateien und Abhängigkeiten, bei denen `DependencyType` den Wert `Install` aufweist.|
|`IsDataFile`|Ein `Boolean`-Metadatenwert, der angibt, ob die Datei eine Datendatei ist. Eine Datendatei ist insofern ein Sonderfall, als sie bei Anwendungsupdates migriert wird. Diese Metadaten gelten nur für Dateien. Der Standardwert lautet `False`.|

## <a name="example-1"></a>Beispiel 1

Im folgenden Beispiel wird mithilfe der `GenerateApplicationManifest`-Aufgabe ein ClickOnce-Anwendungsmanifest und mithilfe der `GenerateDeploymentManifest`-Aufgabe ein Bereitstellungsmanifest für eine Anwendung mit einer einzigen Assembly generiert. Anschließend wird die `SignFile`-Aufgabe verwendet, um die Manifeste zu signieren.

Dies ist das einfachste mögliche Szenario für das Generieren von Manifesten, in dem ClickOnce-Manifeste für ein einzelnes Programm generiert werden. Ein Standardname und eine Identität für das Manifest werden von der Assembly abgeleitet.

> [!NOTE]
> Im folgenden Beispiel sind alle Binärdateien der Anwendung bereits erstellt, sodass Sie besonders auf die Aspekte der Generierung von Manifesten achten können. In diesem Beispiel wird eine voll funktionsfähige ClickOnce-Bereitstellung erstellt.
>
> [!NOTE]
> Weitere Informationen zur `Thumbprint`-Eigenschaft, die in diesem Beispiel in der `SignFile`-Aufgabe verwendet wird, finden Sie unter [SignFile-Aufgabe](../msbuild/signfile-task.md).

```xml
<Project DefaultTargets="Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <EntryPoint Include="SimpleWinApp.exe" />
    </ItemGroup>

    <PropertyGroup>
        <Thumbprint>
             <!-- Insert generated thumbprint here -->
        </Thumbprint>
    </PropertyGroup>

    <Target Name="Build">

        <GenerateApplicationManifest
            EntryPoint="@(EntryPoint)">
            <Output
                ItemName="ApplicationManifest"
                TaskParameter="OutputManifest"/>
        </GenerateApplicationManifest>

        <GenerateDeploymentManifest
            EntryPoint="@(ApplicationManifest)">
            <Output
                ItemName="DeployManifest"
                TaskParameter="OutputManifest"/>
        </GenerateDeploymentManifest>

        <SignFile
            CertificateThumbprint="$(Thumbprint)"
            SigningTarget="@(ApplicationManifest)"/>

        <SignFile
            CertificateThumbprint="$(Thumbprint)"
            SigningTarget="@(DeployManifest)"/>

    </Target>
</Project>
```

## <a name="example-2"></a>Beispiel 2

Im folgenden Beispiel werden die `GenerateApplicationManifest`-Aufgabe und die `GenerateDeploymentManifest`-Aufgabe verwendet, um ein ClickOnce-Anwendungsmanifest und Bereitstellungsmanifeste für eine Anwendung mit einer einzelnen Assembly zu generieren und jeweils den Namen und die Identität der Manifeste anzugeben.

Dieses Beispiel ist mit dem vorherigen Beispiel vergleichbar und unterscheidet sich von diesem nur dadurch, dass der Name und die Identität der Manifeste explizit angegeben werden. Zudem wird in diesem Beispiel statt einer installierten Anwendung eine Onlineanwendung konfiguriert.

> [!NOTE]
> Im folgenden Beispiel sind alle Binärdateien der Anwendung bereits erstellt, sodass Sie besonders auf die Aspekte der Generierung von Manifesten achten können. In diesem Beispiel wird eine voll funktionsfähige ClickOnce-Bereitstellung erstellt.
>
> [!NOTE]
> Weitere Informationen zur `Thumbprint`-Eigenschaft, die in diesem Beispiel in der `SignFile`-Aufgabe verwendet wird, finden Sie unter [SignFile-Aufgabe](../msbuild/signfile-task.md).

```xml
<Project DefaultTargets="Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <EntryPoint Include="SimpleWinApp.exe" />
    </ItemGroup>

    <PropertyGroup>
        <Thumbprint>
             <!-- Insert generated thumbprint here -->
        </Thumbprint>
    </PropertyGroup>

    <Target Name="Build">

        <GenerateApplicationManifest
            AssemblyName="SimpleWinApp.exe"
            AssemblyVersion="1.0.0.0"
            EntryPoint="@(EntryPoint)"
            OutputManifest="SimpleWinApp.exe.manifest">
            <Output
                ItemName="ApplicationManifest"
                TaskParameter="OutputManifest"/>
        </GenerateApplicationManifest>

        <GenerateDeploymentManifest
                AssemblyName="SimpleWinApp.application"
                AssemblyVersion="1.0.0.0"
                EntryPoint="@(ApplicationManifest)"
                Install="false"
                OutputManifest="SimpleWinApp.application">
                <Output
                    ItemName="DeployManifest"
                    TaskParameter="OutputManifest"/>
        </GenerateDeploymentManifest>

        <SignFile
            CertificateThumbprint="$(Thumbprint)"
            SigningTarget="@(ApplicationManifest)"/>

        <SignFile
            CertificateThumbprint="$(Thumbprint)"
            SigningTarget="@(DeployManifest)"/>

    </Target>
</Project>
```

## <a name="example-3"></a>Beispiel 3

Im folgenden Beispiel werden die `GenerateApplicationManifest`-Aufgabe und die `GenerateDeploymentManifest`-Aufgabe verwendet, um ein ClickOnce-Anwendungsmanifest und Bereitstellungsmanifeste für eine Anwendung mit mehreren Dateien und Assemblys zu generieren.

> [!NOTE]
> Im folgenden Beispiel sind alle Binärdateien der Anwendung bereits erstellt, sodass Sie besonders auf die Aspekte der Generierung von Manifesten achten können. In diesem Beispiel wird eine voll funktionsfähige ClickOnce-Bereitstellung erstellt.
>
> [!NOTE]
> Weitere Informationen zur `Thumbprint`-Eigenschaft, die in diesem Beispiel in der `SignFile`-Aufgabe verwendet wird, finden Sie unter [SignFile-Aufgabe](../msbuild/signfile-task.md).

```xml
<Project DefaultTargets="Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <EntryPoint Include="SimpleWinApp.exe" />
    </ItemGroup>

    <PropertyGroup>
        <Thumbprint>
             <!-- Insert generated thumbprint here -->
        </Thumbprint>
        <DeployUrl>
            <!-- Insert the deployment URL here -->
        </DeployUrl>
        <SupportUrl>
            <!-- Insert the support URL here -->
        </SupportUrl>
    </PropertyGroup>

    <Target Name="Build">

    <ItemGroup>
        <EntryPoint Include="SimpleWinApp.exe"/>
        <Dependency Include="ClassLibrary1.dll">
            <AssemblyType>Managed</AssemblyType>
            <DependencyType>Install</DependencyType>
        </Dependency>
        <Dependency Include="ClassLibrary2.dll">
            <AssemblyType>Managed</AssemblyType>
            <DependencyType>Install</DependencyType>
            <Group>Secondary</Group>
        </Dependency>
        <Dependency Include="MyAddIn1.dll">
            <AssemblyType>Managed</AssemblyType>
            <DependencyType>Install</DependencyType>
            <TargetPath>Addins\MyAddIn1.dll</TargetPath>
        </Dependency>
        <Dependency Include="ClassLibrary3.dll">
            <AssemblyType>Managed</AssemblyType>
            <DependencyType>Prerequisite</DependencyType>
        </Dependency>

        <File Include="Text1.txt">
            <TargetPath>Text\Text1.txt</TargetPath>
            <Group>Text</Group>
        </File>
        <File Include="DataFile1.xml ">
            <TargetPath>Data\DataFile1.xml</TargetPath>
            <IsDataFile>true</IsDataFile>
        </File>

        <IconFile Include="Heart.ico"/>
        <ConfigFile Include="app.config">
            <TargetPath>SimpleWinApp.exe.config</TargetPath>
        </ConfigFile>
        <BaseManifest Include="app.manifest"/>
    </ItemGroup>

    <Target Name="Build">

        <GenerateApplicationManifest
            AssemblyName="SimpleWinApp.exe"
            AssemblyVersion="1.0.0.0"
            ConfigFile="@(ConfigFile)"
            Dependencies="@(Dependency)"
            Description="TestApp"
            EntryPoint="@(EntryPoint)"
            Files="@(File)"
            IconFile="@(IconFile)"
            InputManifest="@(BaseManifest)"
            OutputManifest="SimpleWinApp.exe.manifest">
            <Output
                ItemName="ApplicationManifest"
                TaskParameter="OutputManifest"/>
        </GenerateApplicationManifest>

        <GenerateDeploymentManifest
            AssemblyName="SimpleWinApp.application"
            AssemblyVersion="1.0.0.0"
            DeploymentUrl="$(DeployToUrl)"
            Description="TestDeploy"
            EntryPoint="@(ApplicationManifest)"
            Install="true"
            OutputManifest="SimpleWinApp.application"
            Product="SimpleWinApp"
            Publisher="Microsoft"
            SupportUrl="$(SupportUrl)"
            UpdateEnabled="true"
            UpdateInterval="3"
            UpdateMode="Background"
            UpdateUnit="weeks">
            <Output
                ItemName="DeployManifest"
                TaskParameter="OutputManifest"/>
        </GenerateDeploymentManifest>

        <SignFile
            CertificateThumbprint="$(Thumbprint)"
            SigningTarget="@(ApplicationManifest)"/>

        <SignFile
            CertificateThumbprint="$(Thumbprint)"
            SigningTarget="@(DeployManifest)"/>

    </Target>
</Project>
```

## <a name="example-4"></a>Beispiel 4

Im folgenden Beispiel wird die `GenerateApplicationManifest`-Aufgabe verwendet, um ein natives Manifest für die Anwendung *Test.exe* zu generieren, in dem auf die native Komponente *Alpha.dll* und eine isolierte COM-Komponente mit dem Namen *Bravo.dll* verwiesen wird.

In diesem Beispiel wird *Test.exe.manifest* erstellt, wodurch die Anwendung mit XCOPY bereitgestellt werden kann und die Vorteile vom COM ohne Registrierung verwendet.

> [!NOTE]
> Im folgenden Beispiel sind alle Binärdateien der Anwendung bereits erstellt, sodass Sie besonders auf die Aspekte der Generierung von Manifesten achten können. In diesem Beispiel wird eine voll funktionsfähige ClickOnce-Bereitstellung erstellt.

```xml
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <File Include="Test.exe" />
        <Dependency Include="Alpha.dll">
            <AssemblyType>Native</AssemblyType>
            <DependencyType>Install</DependencyType>
        </Dependency>
        <ComComponent Include="Bravo.dll" />
    </ItemGroup>

    <Target Name="Build">
        <GenerateApplicationManifest
            AssemblyName="Test.exe"
            AssemblyVersion="1.0.0.0"
            Dependencies="@(Dependency)"
            Files="@(File)"
            IsolatedComReferences="@(ComComponent)"
            ManifestType="Native">
            <Output
                ItemName="ApplicationManifest"
                TaskParameter="OutputManifest"/>
        </GenerateApplicationManifest>

    </Target>
</Project>
```

## <a name="see-also"></a>Weitere Informationen

- [Aufgaben](../msbuild/msbuild-tasks.md)
- [GenerateDeploymentManifest-Aufgabe](../msbuild/generatedeploymentmanifest-task.md)
- [SignFile-Aufgabe](../msbuild/signfile-task.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
