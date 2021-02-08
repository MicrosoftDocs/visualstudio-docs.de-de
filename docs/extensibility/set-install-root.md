---
title: Installieren außerhalb des Ordners "Erweiterungen" mit VSIX v3 | Microsoft-Dokumentation
description: Erfahren Sie mehr über das Installieren von Visual Studio SDK-Erweiterungs Objekten außerhalb des Ordners "Erweiterungen" und die gültigen Speicherorte.
ms.custom: SEO-VS-2020
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d0a6e955d2ceb4ef8f4f2d4edcd8221badee8caf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836656"
---
# <a name="install-outside-the-extensions-folder"></a>Installieren außerhalb des Ordners für Erweiterungen

Ab Visual Studio 2017 und VSIX v3 (Version 3) können Erweiterungs Objekte außerhalb des Ordners "Erweiterungen" installiert werden. Derzeit sind die folgenden Speicherorte als gültige Installations Pfade aktiviert (wobei [INSTALLDIR] dem Installationsverzeichnis der Visual Studio-Instanz zugeordnet ist):

* [INSTALLDIR] \msbuild
* [INSTALLDIR] \Xml\Schemas
* [INSTALLDIR] \common7\ide\publicassemblies
* [INSTALLDIR] \lizenzen
* [INSTALLDIR] \common7\ide\referenceassemblys
* [INSTALLDIR] \common7\ide\remotedebugger
* [INSTALLDIR] \common7\ide\vc\vctargets (wird nur für Visual Studio 2017 unterstützt, veraltet für Visual Studio 2019 und höher)

> [!NOTE]
> Das VSIX-Format lässt nicht zu, dass Sie außerhalb der Visual Studio-Installationsordner Struktur installieren. 

Um die Installation in diesen Verzeichnissen zu unterstützen, muss die VSIX-Instanz "pro Instanz pro Computer" installiert sein. Dies kann aktiviert werden, indem Sie das Kontrollkästchen "alle Benutzer" im Extension. vsixmanifest-Designer aktivieren:

![alle Benutzer überprüfen](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>Festlegen von InstallRoot

Zum Festlegen der Installationsverzeichnisse können Sie das **Eigenschaften** Fenster in Visual Studio verwenden. Beispielsweise können Sie die- `InstallRoot` Eigenschaft eines Projekt Verweises auf einen der oben genannten Speicherorte festlegen:

![Installieren von root-Eigenschaften](media/install-root-properties.png)

Dadurch werden der entsprechenden `ProjectReference` Eigenschaft in der CSPROJ-Datei des VSIX-Projekts einige Metadaten hinzugefügt:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

> [!NOTE]
> Wenn Sie möchten, können Sie die CSPROJ-Datei direkt bearbeiten.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>Festlegen eines untergeordneten Pfads unter "InstallRoot"

Wenn Sie in einen untergeordneten Pfad unter der installieren möchten `InstallRoot` , können Sie dies tun, indem Sie die- `VsixSubPath` Eigenschaft genau wie die- `InstallRoot` Eigenschaft festlegen. Nehmen wir beispielsweise an, dass die Ausgabe des Projekt Verweises in "[INSTALLDIR] \msbuild\mycompany\mysdk\1.0" installiert werden soll. Dies lässt sich problemlos mit dem Eigenschaften-Designer erreichen:

![Unterpfad festlegen](media/set-subpath.png)

Die entsprechenden csproj-Änderungen sehen wie folgt aus:

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>Zusätzliche Informationen

Die Änderungen an den Eigenschaften-Designern gelten für mehr als nur Projekt Verweise. Sie können auch die `InstallRoot` Metadaten für Elemente in Ihrem Projekt festlegen (mit den oben beschriebenen Methoden).
