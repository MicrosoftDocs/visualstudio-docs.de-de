---
title: Erstellen eines Produkt Manifests | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie erforderliche Komponenten für Ihre ClickOnce-Anwendung mit einem Paket bereitstellen, das ein einzelnes Produkt Manifest und ein Paket Manifest für jedes Gebiets Schema enthält.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- product files [ClickOnce]
- product files [Windows Installer]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper package
ms.assetid: 2d316aaa-8bc0-4ce5-90ab-23b3eac0b5dd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ab7156635914d46dfc1849717d29ac0416e2d9fa
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351218"
---
# <a name="how-to-create-a-product-manifest"></a>Vorgehensweise: Erstellen eines Produktmanifests
Zum Bereitstellen der erforderlichen Komponenten für die Anwendung können Sie ein Bootstrapperpaket erstellen. Ein Bootstrapperpaket enthält eine einzelne Produkt Manifest-Datei, aber ein Paket Manifest für jedes Gebiets Schema. Das Paket Manifest enthält Lokalisierungs spezifische Aspekte des Pakets. Hierzu gehören Zeichen folgen, Endbenutzer-Lizenzverträge und Sprachpakete.

 Weitere Informationen zu Paket [Manifesten finden Sie unter Gewusst wie: Erstellen eines Paket Manifests](../deployment/how-to-create-a-package-manifest.md).

## <a name="create-the-product-manifest"></a>Erstellen des Produkt Manifests

#### <a name="to-create-the-product-manifest"></a>So erstellen Sie das Produkt Manifest

1. Erstellen Sie ein Verzeichnis für das Bootstrapperpaket. In diesem Beispiel wird c:\packageverwendet.

2. Erstellen Sie in Visual Studio eine neue XML-Datei mit dem Namen *product.xml* , und speichern Sie Sie im Ordner *c:\Package* .

3. Fügen Sie folgenden XML-Code hinzu, um den XML-Namespace und den Produktcode für das Paket zu beschreiben. Ersetzen Sie den Produktcode durch einen eindeutigen Bezeichner für das Paket.

    ```xml
    <Product
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
    ProductCode="Custom.Bootstrapper.Package">
    ```

4. Fügen Sie XML hinzu, um anzugeben, dass das Paket eine Abhängigkeit aufweist. In diesem Beispiel wird eine Abhängigkeit von Microsoft Windows Installer 3,1 verwendet.

    ```xml
    <RelatedProducts>
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />
      </RelatedProducts>
    ```

5. Fügen Sie XML hinzu, um alle Dateien aufzulisten, die im Bootstrapperpaket enthalten sind. In diesem Beispiel wird der Name der Paketdatei *CorePackage.msi* verwendet.

    ```xml
    <PackageFiles>
        <PackageFile Name="CorePackage.msi"/>
    </PackageFiles>
    ```

6. Kopieren Sie die *CorePackage.msi* Datei, oder verschieben Sie Sie in den Ordner *c:\Package* .

7. Fügen Sie XML hinzu, um das Paket mithilfe von Boots Trapper-Befehlen zu installieren. Der Boots Trapper fügt der *MSI* -Datei automatisch das Flag **/QN** hinzu, das im Hintergrund installiert wird. Wenn es sich bei der Datei um eine *exe* -Datei handelt, führt der Boots Trapper die *exe* -Datei mithilfe der Shell aus. Der folgende XML-Code zeigt keine Argumente für *CorePackage.msi* an, aber Sie können das Befehlszeilenargument in das- `Arguments` Attribut einfügen.

    ```xml
    <Commands>
        <Command PackageFile="CorePackage.msi" Arguments="">
    ```

8. Fügen Sie folgenden XML-Code hinzu, um zu überprüfen, ob dieses Bootstrapperpaket installiert ist. Ersetzen Sie den Produktcode durch die GUID für die verteilbare Komponente.

    ```xml
    <InstallChecks>
        <MsiProductCheck
            Property="IsMsiInstalled"
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>
    </InstallChecks>
    ```

9. Fügen Sie XML hinzu, um das bootstrapperverhalten zu ändern, je nachdem, ob die bootstrapperkomponente bereits installiert ist. Wenn die Komponente installiert ist, wird das Bootstrapperpaket nicht ausgeführt. Der folgende XML-Code überprüft, ob der aktuelle Benutzer ein Administrator ist, da diese Komponente Administratorrechte erfordert.

    ```xml
    <InstallConditions>
        <BypassIf
           Property="IsMsiInstalled"
           Compare="ValueGreaterThan" Value="0"/>
        <FailIf Property="AdminUser"
            Compare="ValueNotEqualTo" Value="True"
            String="NotAnAdmin"/>
    </InstallConditions>
    ```

10. Fügen Sie XML hinzu, um Exitcodes festzulegen, wenn die Installation erfolgreich ist und ein Neustart erforderlich ist. Im folgenden XML werden die Exitcodes Fail und failreboot veranschaulicht, die darauf hinweisen, dass der Boots Trapper die Installation von Paketen nicht fortsetzen kann.

    ```xml
    <ExitCodes>
        <ExitCode Value="0" Result="Success"/>
        <ExitCode Value="1641" Result="SuccessReboot"/>
        <ExitCode Value="3010" Result="SuccessReboot"/>
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>
    </ExitCodes>
    ```

11. Fügen Sie den folgenden XML-Code hinzu, um den Abschnitt für bootstrapperbefehle zu beenden.

    ```xml
        </Command>
    </Commands>
    ```

12. Verschieben Sie den Ordner *c:\Package* in das Verzeichnis von Visual Studio Boots Trapper. Für Visual Studio 2010 ist dies das Verzeichnis " *\Programme\Microsoft SDKs\Windows\v7.0a\bootstrapper\packages* ".

## <a name="example"></a>Beispiel
 Das Produkt Manifest enthält Installationsanweisungen für benutzerdefinierte Voraussetzungen.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Product
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
  ProductCode="Custom.Bootstrapper.Package">

  <RelatedProducts>
    <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />
  </RelatedProducts>

  <PackageFiles>
    <PackageFile Name="CorePackage.msi"/>
  </PackageFiles>

  <InstallChecks>
    <MsiProductCheck Product="IsMsiInstalled"
      Property="{XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>
  </InstallChecks>

  <Commands>
    <Command PackageFile="CorePackage.msi" Arguments="">

      <InstallConditions>
        <BypassIf Property="IsMsiInstalled"
          Compare="ValueGreaterThan" Value="0"/>
        <FailIf Property="AdminUser"
          Compare="ValueNotEqualTo" Value="True"
         String="NotAnAdmin"/>
      </InstallConditions>

      <ExitCodes>
        <ExitCode Value="0" Result="Success"/>
        <ExitCode Value="1641" Result="SuccessReboot"/>
        <ExitCode Value="3010" Result="SuccessReboot"/>
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>
      </ExitCodes>
    </Command>
  </Commands>
</Product>
```

## <a name="see-also"></a>Weitere Informationen
- [Produkt-und Paket Schema Referenz](../deployment/product-and-package-schema-reference.md)