---
title: GenerateBootstrapper-Aufgabe | Microsoft-Dokumentation
description: Verwenden Sie die MSBuild-Aufgabe „GenerateBootstrapper“ für eine automatisierte Methode zum Erkennen, Herunterladen und Installieren einer Anwendung sowie ihrer erforderlichen Komponenten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateBootstrapper
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateBootstrapper task
- GenerateBootstrapper task [MSBuild]
ms.assetid: ca3ba2c6-d2ea-41f2-b7e3-0fc2b0730460
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 83bb6b44713ba61d14c508c0db2a51391a350015
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436470"
---
# <a name="generatebootstrapper-task"></a>GenerateBootstrapper-Aufgabe

Bietet eine automatisierte Methode zum Erkennen, Herunterladen und Installieren einer Anwendung sowie ihrer erforderlichen Komponenten. Sie dient als einzelner Installer, der den separaten Installer für alle Komponenten integriert, die zu einer Anwendung gehören.

## <a name="task-parameters"></a>Aufgabenparameter

Im Folgenden werden die Parameter der `GenerateBootstrapper`-Aufgabe beschrieben.

- `ApplicationFile`

   Optionaler `String`-Parameter.

   Gibt die Datei an, mit der der Bootstrapper die Installation der Anwendung startet, nachdem alle erforderlichen Komponenten installiert wurde. Wenn weder der Parameter `BootstrapperItems` noch `ApplicationFile` angegeben werden, wird ein Buildfehler erzeugt.

- `ApplicationName`

   Optionaler `String`-Parameter.

   Gibt den Namen der Anwendung an, die vom Bootstrapper installiert wird. Dieser Name wird in der Benutzeroberfläche angezeigt, die vom Bootstrapper während der Installation verwendet wird.

- `ApplicationRequiresElevation`

   Optionaler `Boolean`-Parameter.

   Wenn `true`, wird die Komponente mit erweiterten Berechtigungen ausgeführt, wenn sie auf einem Ziel-Computer installiert wird.

- `ApplicationUrl`

   Optionaler `String`-Parameter.

   Gibt die Webadresse an, die das Installationsprogramm der Anwendung hostet

- `BootstrapperComponentFiles`

   Optionaler `String[]`-Ausgabeparameter.

   Gibt den Erstellungsort von Bootstrapper-Paketdateien an.

- `BootstrapperItems`

   Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter

   Gibt die Produkte an, die im Bootstrapper erstellt werden. Die Elemente, die an diesen Parameter übergeben werden, sollten folgende Syntax haben:

  ```xml
  <BootstrapperItem
      Include="ProductCode">
      <ProductName>
          ProductName
      </ProductName>
  </BootstrapperItem>
  ```

   Das Attribut `Include` stellt den Namen einer erforderlichen Komponente dar, die installiert werden sollte. Die `ProductName`-Elementmetadaten sind optional und werden von der Build-Engine als benutzerfreundlicher Name verwendet, falls das Paket nicht gefunden werden kann. Diese Elemente sind keine erforderlichen Eingabeparameter von MSBuild, sofern kein `ApplicationFile`-Parameter angegeben ist. Sie sollten ein Element für jede erforderliche Komponente einfügen, die für Ihre Anwendung installiert werden muss.

   Wenn weder der Parameter `BootstrapperItems` noch `ApplicationFile` angegeben werden, wird ein Buildfehler erzeugt.

- `BootstrapperKeyFile`

   Optionaler `String`-Ausgabeparameter.

   Gibt den Erstellungsort von *setup.exe* an.

- `ComponentsLocation`

   Optionaler `String`-Parameter.

   Gibt einen Speicherort für den Bootstrapper an, an dem nach zu installierenden Voraussetzungen für die Installation gesucht wird. Dieser Parameter kann die folgenden Werte aufweisen:

  - `HomeSite`: Gibt an, dass die erforderliche Komponente vom Komponentenanbieter gehostet wird.

  - `Relative`: Gibt an, dass sich die erforderliche Komponente am gleichen Speicherort der Anwendung befindet.

  - `Absolute`: Gibt an, dass sich alle Komponenten bei einer zentralisierten URL befinden. Dieser Wert sollte zusammen mit dem Eingabeparameter `ComponentsUrl` verwendet werden.

    Wenn `ComponentsLocation` nicht angegeben ist, wird `HomeSite` standardmäßig verwendet.

- `ComponentsUrl`

   Optionaler `String`-Parameter.

   Gibt die URL an, die die Voraussetzung für die Installation enthält.

- `CopyComponents`

   Optionaler `Boolean`-Parameter.

   Wenn `true`, kopiert der Bootstrapper alle Ausgabedateien in den Pfad, der im Parameter `OutputPath` angegeben ist. Die Werte des Parameters `BootstrapperComponentFiles` sollten alle auf diesen Pfad basieren. Wenn `false`, werden die Dateien nicht kopiert. Die `BootstrapperComponentFiles`-Werte basieren dann auf den Wert des Parameters `Path`.  Der Standardwert dieses Parameters ist `true`.

- `Culture`

   Optionaler `String`-Parameter.

   Gibt die Kultur an, die für die Bootstrapper-Benutzeroberfläche und die Voraussetzungen für die Installation verwendet werden soll. Wenn die angegebene Kultur nicht verfügbar ist, verwendet die Aufgabe den Wert des Parameters `FallbackCulture`.

- `FallbackCulture`

   Optionaler `String`-Parameter.

   Gibt die sekundäre Kultur für die Bootstrapper-Benutzeroberfläche und die Voraussetzungen für die Installation an.

- `OutputPath`

   Optionaler `String`-Parameter.

   Gibt den Speicherort zum Kopieren von *setup.exe* und aller Paketdateien an.

- `Path`

   Optionaler `String`-Parameter.

   Gibt den Speicherort für alle verfügbaren erforderlichen Pakete an.

- `SupportUrl`

   Optionaler `String`-Parameter.

   Gibt die URL an, die bei einem Fehler der Bootstrapper-Installation bereitgestellt werden soll.

- `Validate`

   Optionaler `Boolean`-Parameter.

   Wenn `true`, führt der Bootstrapper die XSD-Validierung der angegebenen Bootstrapper-Eingabeelemente durch. Der Standardwert dieses Parameters ist `false`.

## <a name="remarks"></a>Hinweise

Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird der Task `GenerateBootstrapper` zur Installation einer Anwendung verwendet, für die als Voraussetzung .NET Framework 2.0 installiert sein muss.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <BootstrapperFile Include="Microsoft.Net.Framework.2.0">
            <ProductName>Microsoft .NET Framework 2.0</ProductName>
        </BootstrapperFile>
    </ItemGroup>

    <Target Name="BuildBootstrapper">
        <GenerateBootstrapper
            ApplicationFile="WindowsApplication1.application"
            ApplicationName="WindowsApplication1"
            ApplicationUrl="http://mycomputer"
            BootstrapperItems="@(BootstrapperFile)"
            OutputPath="C:\output" />
    </Target>

</Project>
```

## <a name="see-also"></a>Weitere Informationen

- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
