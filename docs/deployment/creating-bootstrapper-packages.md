---
title: Erstellen von Bootstrapperpaketen
description: Erfahren Sie mehr über das Setup Programm und die Verwendung von XML-Manifesten, die die Metadaten für die Verwaltung der Installation von ClickOnce-Komponenten angeben.
ms.custom: SEO-VS-2020
ms.date: 05/02/2018
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [Visual Studio], prerequisites
- deploying applications [Visual Studio], custom prerequisites
- prerequisites, custom
- RedistList file
- custom prerequisites
- redistributables list
ms.assetid: ba1a785b-693d-446b-bcae-b88cadee73d1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 04cbb0db729d39295ee9c608a19302a109980f10
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912220"
---
# <a name="create-bootstrapper-packages"></a>Erstellen von Bootstrapperpaketen
Das Setupprogramm ist ein generisches Installationsprogramm, das für die Ermittlung und die Installation von weitervertreibbaren Komponenten wie Windows Installer (*MSI*-Format) und ausführbaren Programmen konfiguriert werden kann. Das Installationsprogramm wird auch als Bootstrapper bezeichnet. Der Bootstrapper wird mithilfe einer Reihe von XML-Manifesten programmiert, mit denen die Metadaten zur Verwaltung der Komponenteninstallation angegeben werden.  Jede verteilbare Komponente bzw. erforderliche Komponente **, die im Dialogfeld** für die erforderlichen Komponenten für ClickOnce angezeigt wird, ist ein Bootstrapperpaket. Bei einem Bootstrapperpaket handelt es sich um eine Gruppe von Verzeichnissen und Dateien, die Manifestdateien enthalten, mit denen beschrieben wird, wie die erforderliche Komponente installiert werden muss.

Der Bootstrapper ermittelt zunächst, ob erforderliche Komponenten bereits installiert sind. Ist dies nicht der Fall, werden vom Bootstrapper die Lizenzverträge angezeigt. Nachdem der Endbenutzer die Lizenzverträge akzeptiert hat, beginnt die Installation der erforderlichen Komponenten. Wurden alle erforderlichen Komponenten ermittelt, wird direkt das Installationsprogramm der Anwendung gestartet.

## <a name="create-custom-bootstrapper-packages"></a>Erstellen von benutzerdefinierten Bootstrapperpaketen
Sie können die bootstrappermanifeste mithilfe des XML-Editors in Visual Studio generieren. Ein Beispiel für das Erstellen eines Bootstrapperpakets finden Sie unter Exemplarische Vorgehensweise [: Erstellen eines benutzerdefinierten Boots Trappers mit einer Datenschutz Aufforderung](../deployment/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt.md).

Zum Erstellen eines Bootstrapperpakets müssen Sie ein Produkt Manifest erstellen und für jede lokalisierte Version einer Komponente ebenfalls ein Paket Manifest erstellen.

* Das Produkt Manifest, *product.xml*, enthält alle sprach neutralen Metadaten für das Paket. Es enthält Metadaten, die für alle lokalisierten Versionen der verteilbaren Komponente gleich sind.  Informationen zum Erstellen dieser Datei finden Sie unter Gewusst [wie: Erstellen eines Produkt Manifests](../deployment/how-to-create-a-product-manifest.md).

* Das Paket Manifest, *package.xml*, enthält sprachspezifische Metadaten. Es enthält in der Regel lokalisierte Fehlermeldungen. Eine Komponente benötigt für jede lokalisierte Version dieser Komponente mindestens ein Paketmanifest. Informationen zum Erstellen dieser Datei finden Sie unter Gewusst [wie: Erstellen eines Paket Manifests](../deployment/how-to-create-a-package-manifest.md).

Nachdem diese Dateien erstellt wurden, platzieren Sie die Produktmanifestdatei in einen entsprechend benannten Ordner für den benutzerdefinierten Bootstrapper. Die Paketmanifestdatei muss in einem Ordner, der dem Gebietsschema entsprechend benannt wurde, abgelegt werden. Wenn die Paketmanifestdatei z. B. für die Neuverteilung in englischer Sprache vorgesehen ist, legen Sie die Datei in einen Ordner mit der Bezeichnung "en" ab. Wiederholen Sie diesen Prozess für jedes Gebietsschema, z. B. "ja" für Japanisch und "de" für Deutsch. Das abschließende benutzerdefinierte Bootstrapperpaket könnte beispielsweise über die folgende Ordnerstruktur verfügen.

```
CustomBootstrapperPackage
  product.xml
  CustomBootstrapper.msi
  de
    eula.rtf
    package.xml
  en
    eula.rtf
    package.xml
  ja
    eula.rtf
    package.xml
```

Kopieren Sie als nächstes die verteilbaren Dateien in den Speicherort des bootstrapperordners. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen eines lokalisierten Bootstrapperpakets](../deployment/how-to-create-a-localized-bootstrapper-package.md).

```
*\Program Files (x86)\Microsoft SDKs\ClickOnce Bootstrapper*
```

oder für ältere Versionen von Visual Studio

```
*\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
```

oder

```
*\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
```

Sie können auch den Speicherort des bootstrapperordners über den **Pfad** Wert im folgenden Registrierungsschlüssel finden:

```
*HKLM\Software\Microsoft\GenericBootstrapper*
```

Auf 64-Bit-Systemen verwenden Sie den folgenden Registrierungsschlüssel:

```
*HKLM\Software\Wow6432Node\Microsoft\GenericBootstrapper*
```

Jede verteilbare Komponente wird unter dem Paketverzeichnis in einem eigenen Unterordner angezeigt. Das Produkt Manifest und verteilbare Dateien müssen in diesem Unterordner abgelegt werden. Lokalisierte Versionen der Komponenten-und Paket Manifeste müssen in Unterordnern abgelegt werden, die entsprechend dem Kultur Namen benannt sind.

Nachdem diese Dateien in den Bootstrapperordner kopiert wurden, wird das Bootstrapperpaket in Visual Studio automatisch im Dialogfeld **Erforderliche Komponenten** angezeigt. Wird das benutzerdefinierte Bootstrapperpaket nicht angezeigt, schließen Sie das Dialogfeld **Erforderliche Komponenten**, und öffnen Sie es erneut. Weitere Informationen finden Sie unter [Dialogfeld "Voraussetzungen](../ide/reference/prerequisites-dialog-box.md)".

In der folgenden Tabelle werden die Eigenschaften angezeigt, die automatisch vom Bootstrapper eingetragen werden.

|Eigenschaft|BESCHREIBUNG|
|--------------|-----------------|
|ApplicationName|Der Namen der Anwendung.|
|ProcessorArchitecture|Der Prozessor und die Bits pro Wort für die Plattform, auf die eine ausführbare Datei zielt. Folgende Werte sind gültig:<br /><br /> –   Intel<br />–   IA64<br />–   AMD64|
|[Version9x](/windows/desktop/Msi/version9x)|Die Versionsnummer für Microsoft Windows 95, Windows 98 oder Windows ME. Die Syntax der Version lautet "Major.Minor.ServicePack".|
|[VersionNT](/windows/desktop/Msi/versionnt)|Die Versionsnummer für Windows NT, Windows 2000, Windows XP, Windows Vista, Windows Server 2008 oder Windows 7. Die Syntax der Version lautet "Major.Minor.ServicePack".|
|[VersionMSI](/windows/desktop/Msi/versionmsi)|Die Version der Windows Installer Assembly (msi.dll), die während der Installation ausgeführt werden soll.|
|[AdminUser](/windows/desktop/Msi/adminuser)|Diese Eigenschaft wird festgelegt, wenn der Benutzer über Administratorrechte verfügt. Gültige Werte sind "true" und "false".|
|InstallMode|Der Installationsmodus gibt an, von welchem Speicherort die Komponente installiert werden muss. Folgende Werte sind gültig:<br /><br /> –   HomeSite: Die erforderlichen Komponenten werden von der Website des Anbieters installiert.<br />–   SpecificSite: Die erforderlichen Komponenten werden vom ausgewählten Speicherort installiert.<br />–   SameSite: Die erforderlichen Komponenten werden vom gleichen Speicherort wie die Anwendung installiert.|

## <a name="separate-redistributables-from-application-installations"></a>Getrennte verteilbare Komponenten von Anwendungs Installationen
Sie können die Bereitstellung von verteilbaren Dateien in Setupprojekten auch deaktivieren. Erstellen Sie hierzu im Ordner "RedistList" im Verzeichnis von .NET Framework eine verteilbare Liste:

`%ProgramFiles%\Microsoft.NET\RedistList`

Die verteilbare Liste ist eine XML-Datei, die Sie im folgenden Format benennen sollten: *\<Company Name> . \<Component Name>.RedistList.xml*. Beispiel: Wenn die Komponente „DataWidgets“ heißt und von der Firma Acme stammt, nennen Sie die Datei *Acme.DataWidgets.RedistList.xml*. Der Inhalt der verteilbaren Liste könnte in etwa so aussehen:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<FileList Redist="Acme.DataWidgets" >
<File AssemblyName="Acme.DataGrid" Version="1.0.0.0" PublicKeyToken="b03f5f7f11d50a3a" Culture="neutral" ProcessorArchitecture="MSIL" InGAC="true" />
</FileList>
```

## <a name="see-also"></a>Weitere Informationen
- [Gewusst wie: Installieren von erforderlichen Komponenten mit einer ClickOnce-Anwendung](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [Dialogfeld für erforderliche Komponenten](../ide/reference/prerequisites-dialog-box.md)
- [Produkt-und Paket Schema Referenz](../deployment/product-and-package-schema-reference.md)
- [Artikel zum Verwenden des Visual Studio 2005-Bootstrappers zum Starten der Installation](/archive/msdn-magazine/2004/october/visual-studio-2005-bootstrapper-start-kick-your-installation)
