---
title: Erstellen eines Paket Manifests | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Verwendung eines Bootstrapperpakets zum Bereitstellen der erforderlichen Komponenten für die ClickOnce-Anwendung, die ein Paket Manifest für jedes Gebiets Schema enthält.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- package files [Windows Installer]
- package files [ClickOnce]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper packages
ms.assetid: 5aecc507-2764-42f2-ae6f-c227971cf0af
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cef6cd23a1e5ff1e00e2d4d93313ee1e9355ece2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927560"
---
# <a name="how-to-create-a-package-manifest"></a>Vorgehensweise: Erstellen eines Paketmanifests
Zum Bereitstellen der erforderlichen Komponenten für die Anwendung können Sie ein Bootstrapperpaket verwenden. Ein Bootstrapperpaket enthält eine einzelne Produkt Manifest-Datei, aber ein Paket Manifest für jedes Gebiets Schema. Gemeinsam genutzte Funktionen über verschiedene lokalisierte Versionen hinweg sollten in das Produkt Manifest gelangen.

 Weitere Informationen zu Produkt [Manifesten finden Sie unter Gewusst wie: Erstellen eines Produkt Manifests](../deployment/how-to-create-a-product-manifest.md).

## <a name="create-the-package-manifest"></a>Erstellen des Paket Manifests

#### <a name="to-create-the-package-manifest"></a>So erstellen Sie das Paket Manifest

1. Erstellen Sie ein Verzeichnis für das Bootstrapperpaket. In diesem Beispiel wird *c:\Package* verwendet.

2. Erstellen Sie ein Unterverzeichnis mit dem Namen des Gebiets Schemas, z. b. " *en* " für Englisch.

3. Erstellen Sie in Visual Studio eine XML-Datei mit dem Namen *package.xml*, und speichern Sie Sie im Ordner *c:\package\en* .

4. Fügen Sie XML hinzu, um den Namen des Bootstrapperpakets, die Kultur für dieses lokalisierte Paket Manifest und den optionalen Lizenzvertrag aufzulisten. Der folgende XML-Code verwendet die Variablen `DisplayName` und `Culture` , die in einem späteren Element definiert sind.

    ```xml
    <Package
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
        Name="DisplayName"
        Culture="Culture"
        LicenseAgreement="eula.txt">
    ```

5. Fügen Sie XML hinzu, um alle Dateien aufzulisten, die im Gebiets Schema spezifischen Verzeichnis enthalten sind. Der folgende XML-Code verwendet eine Datei mit dem Namen *eula.txt* , die für das Gebiets Schema " **en** " anwendbar ist.

    ```xml
    <PackageFiles>
      <PackageFile Name="eula.txt"/>
    </PackageFiles>
    ```

6. Hinzufügen von XML zum Definieren Lokalisier barer Zeichen folgen für das Bootstrapperpaket. Das folgende XML fügt Fehler Zeichenfolgen für das **en** -Gebiets Schema hinzu.

    ```xml
      <Strings>
        <String Name="DisplayName">Custom Bootstrapper Package</String>
        <String Name="CultureName">en</String>
        <String Name="NotAnAdmin">You must be an administrator to install
    this package.</String>
        <String Name="GeneralFailure">A general error has occurred while
    installing this package.</String>
    </Strings>
    ```

7. Kopieren Sie den Ordner *c:\Package* in das Verzeichnis von Visual Studio Boots Trapper. Für Visual Studio 2010 ist dies das Verzeichnis " *\Programme\Microsoft SDKs\Windows\v7.0a\bootstrapper\packages* ".

## <a name="example"></a>Beispiel
 Das Paket Manifest enthält Gebiets Schema spezifische Informationen, wie z. b. Fehlermeldungen, Software Lizenzbedingungen und Sprachpakete.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Package
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
  Name="DisplayName"
  Culture="Culture"
  LicenseAgreement="eula.txt">

  <PackageFiles>
    <PackageFile Name="eula.txt"/>
  </PackageFiles>

  <Strings>
    <String Name="DisplayName">Custom Bootstrapper Package</String>
    <String Name="Culture">en</String>
    <String Name="NotAnAdmin">You must be an administrator to install this package.</String>
    <String Name="GeneralFailure">A general error has occurred while
installing this package.</String>
  </Strings>
</Package>
```

## <a name="see-also"></a>Weitere Informationen
- [Produkt-und Paket Schema Referenz](../deployment/product-and-package-schema-reference.md)