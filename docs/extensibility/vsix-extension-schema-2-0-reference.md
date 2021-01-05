---
title: VSIX-Erweiterungs Schema 2,0-Referenz | Microsoft-Dokumentation
description: Das VSIX-Erweiterungs Schema 2,0 definiert das Dateiformat für eine VSIX-Bereitstellungs Manifest-Datei, in der der Inhalt eines VSIX-Pakets beschrieben wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- vsix
- extension schema
ms.assetid: 0da81b98-f5e3-40d3-ba9a-94551378d0b4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b2edd0349555380f6d98d24f7a40c22e48797d12
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863765"
---
# <a name="vsix-extension-schema-20-reference"></a>VSIX-Erweiterungs Schema 2,0-Referenz
In einer VSIX-Bereitstellungs Manifest-Datei wird der Inhalt eines VSIX-Pakets beschrieben. Das Dateiformat wird durch ein Schema geregelt. Version 2,0 dieses Schemas unterstützt das Hinzufügen von benutzerdefinierten Typen und Attributen.  Das Schema des Manifests ist erweiterbar. Das Manifest-Lade Modul ignoriert XML-Elemente und-Attribute, die es nicht versteht.

> [!IMPORTANT]
> Visual Studio 2015 kann VSIX-Dateien in den Formaten Visual Studio 2010, Visual Studio 2012 oder Visual Studio 2013 laden.

## <a name="package-manifest-schema"></a>Paket Manifest-Schema
 Das Stamm Element der Manifest-XML-Datei ist `<PackageManifest>` . Sie verfügt über ein einzelnes Attribut `Version` , das die Version des Manifest-Formats ist. Wenn am Format wesentliche Änderungen vorgenommen werden, wird das Versions Format geändert. Dieser Artikel beschreibt das Manifest-Format, Version 2,0, das im Manifest angegeben ist, indem das- `Version` Attribut auf den Wert von Version = "2.0" festgelegt wird.

### <a name="packagemanifest-element"></a>Packagemanifest-Element
 Innerhalb des `<PackageManifest>` Root-Elements können Sie die folgenden Elemente verwenden:

- `<Metadata>` : Metadaten und Werbeinformationen über das Paket selbst. `Metadata`Im Manifest ist nur ein-Element zulässig.

- `<Installation>` : In diesem Abschnitt wird definiert, wie das Erweiterungspaket installiert werden kann, einschließlich der Anwendungs-SKUs, die in installiert werden können. Im Manifest ist nur ein einzelnes- `Installation` Element zulässig. Ein Manifest muss über ein- `Installation` Element verfügen, oder dieses Paket wird nicht in einer SKU installiert.

- `<Dependencies>` -Eine optionale Liste der Abhängigkeiten für dieses Paket wird hier definiert.

- `<Assets>` Dieser Abschnitt enthält alle in diesem Paket enthaltenen Assets. Ohne diesen Abschnitt stellt dieses Paket keinen Inhalt dar.

- `<AnyElement>*` -Das Manifest-Schema ist flexibel genug, um beliebige andere Elemente zuzulassen. Alle untergeordneten Elemente, die nicht vom Manifest-Loader erkannt werden, werden in der Erweiterungs-Manager-API als zusätzliche XmlElement-Objekte verfügbar gemacht. Mithilfe dieser untergeordneten Elemente können VSIX-Erweiterungen zusätzliche Daten in der Manifestressource definieren, auf die der Code, der in Visual Studio ausgeführt wird, zur Laufzeit zugreifen kann. Siehe [Microsoft. VisualStudio. ExtensionManager. IExtension. additionalelements](/previous-versions/visualstudio/visual-studio-2013/hh265266(v=vs.120)).

### <a name="metadata-element"></a>Metadata-Element
 In diesem Abschnitt handelt es sich um die Metadaten für das Paket, seine Identität und die Werbeinformationen. `<Metadata>` enthält die folgenden Elemente:

- `<Identity>` : Definiert Identifikationsinformationen für dieses Paket und enthält die folgenden Attribute:

  - `Id` : Dieses Attribut muss eine eindeutige ID für das Paket sein, das von seinem Autor ausgewählt wird. Der Name sollte auf die gleiche Weise qualifiziert werden wie CLR-Typen, die Namespaces sind: Company.Product.Feature.Name. Das- `Id` Attribut ist auf 100 Zeichen beschränkt.

  - `Version` : Definiert die Version dieses Pakets und dessen Inhalt. Dieses Attribut folgt dem Format der CLR-assemblyversionierung: Major. Minor. Build. Revision (1.2.40308.00). Ein Paket mit einer höheren Versionsnummer wird als Updates für das Paket angesehen und kann über die vorhandene installierte Version installiert werden.

  - `Language` : Dieses Attribut ist die Standardsprache für das Paket und entspricht den Textdaten in diesem Manifest. Dieses Attribut folgt der CLR-Gebiets Schema-Code Konvention für Ressourcenassemblys, z. b.: en-US, en, fr-fr. Sie können angeben `neutral` , um eine sprachneutrale Erweiterung zu deklarieren, die in einer beliebigen Version von Visual Studio ausgeführt wird. Standardwert: `neutral`.

  - `Publisher` : Dieses Attribut identifiziert den Herausgeber dieses Pakets, entweder einen Firmennamen oder einen individuellen Namen. Das- `Publisher` Attribut ist auf 100 Zeichen beschränkt.

- `<DisplayName>` -Dieses Element gibt den benutzerfreundlichen Paketnamen an, der auf der Benutzeroberfläche des Erweiterungs-Managers angezeigt wird. Der `DisplayName` Inhalt ist auf 50 Zeichen beschränkt.

- `<Description>` -Dieses optionale Element ist eine kurze Beschreibung des Pakets und seiner Inhalte, das in der Erweiterungs-Manager-Benutzeroberfläche angezeigt wird. Der `Description` Inhalt kann beliebigen Text enthalten, den Sie wünschen, aber er ist auf 1000 Zeichen beschränkt.

- `<MoreInfo>` -Bei diesem optionalen Element handelt es sich um eine URL zu einer Online Seite, die eine vollständige Beschreibung dieses Pakets enthält. Das Protokoll muss als http angegeben werden.

- `<License>` -Dieses optionale Element ist ein relativer Pfad zu einer Lizenzdatei (. txt,. RTF), die im Paket enthalten ist.

- `<ReleaseNotes>` : Dieses optionale Element ist entweder ein relativer Pfad zu einer Datei mit Versions Anmerkungen, die im Paket enthalten ist (txt, RTF), oder es handelt sich um eine URL zu einer Website, auf der die Anmerkungen zu dieser Version angezeigt werden.

- `<Icon>` -Dieses optionale Element ist ein relativer Pfad zu einer Bilddatei (PNG, BMP, JPEG, ICO), die im Paket enthalten ist. Das Symbolbild sollte 32 x 32 Pixel groß sein (oder wird auf diese Größe verkleinert) und in der ListView-Benutzeroberfläche angezeigt. Wenn kein- `Icon` Element angegeben wird, verwendet die Benutzeroberfläche einen Standardwert.

- `<PreviewImage>` -Dieses optionale Element ist ein relativer Pfad zu einer Bilddatei (PNG, BMP, JPEG), die im Paket enthalten ist. Das Vorschaubild sollte 200 x 200 Pixel betragen und in der Detail Benutzeroberfläche angezeigt werden. Wenn kein- `PreviewImage` Element angegeben wird, verwendet die Benutzeroberfläche einen Standardwert.

- `<Tags>` -Dieses optionale Element listet zusätzliche, durch Semikolons getrennte texttags auf, die für Such Hinweise verwendet werden. Das- `Tags` Element ist auf 100 Zeichen beschränkt.

- `<GettingStartedGuide>` : Dieses optionale Element ist entweder ein relativer Pfad zu einer HTML-Datei oder eine URL zu einer Website, die Informationen zur Verwendung der Erweiterung oder des Inhalts in diesem Paket enthält. Dieses Handbuch wird im Rahmen einer Installation von gestartet.

- `<AnyElement>*` -Das Manifest-Schema ist flexibel genug, um beliebige andere Elemente zuzulassen. Alle untergeordneten Elemente, die nicht vom Manifest-Lade Modul erkannt werden, werden als Liste von XmlElement-Objekten verfügbar gemacht. Mithilfe dieser untergeordneten Elemente können VSIX-Erweiterungen zusätzliche Daten in der Manifest-Datei definieren und diese zur Laufzeit auflisten.

### <a name="installation-element"></a>Installations Element
 In diesem Abschnitt wird die Art und Weise definiert, wie dieses Paket installiert werden kann, und die Anwendungs-SKUs, die es in installieren kann Dieser Abschnitt enthält die folgenden Attribute:

- `Experimental` -Legen Sie dieses Attribut auf "true" fest, wenn Sie eine Erweiterung haben, die zurzeit für alle Benutzer installiert ist, Sie jedoch eine aktualisierte Version auf demselben Computer entwickeln. Wenn Sie z. b. MyExtension 1,0 für alle Benutzer installiert haben, aber MyExtension 2,0 auf demselben Computer debuggen möchten, legen Sie experimentell = "true" fest. Dieses Attribut ist in Visual Studio 2015 Update 1 und höher verfügbar.

- `Scope` : Dieses Attribut kann den Wert "Global" oder "productextension" annehmen:

  - "Global" gibt an, dass die Installation nicht für eine bestimmte SKU festgelegt ist. Dieser Wert wird z. b. verwendet, wenn ein Erweiterungs-SDK installiert wird.

  - "Productextension" gibt an, dass eine herkömmliche VSIX-Erweiterung (Version 1,0), die sich auf einzelne Visual Studio-SKUs bezieht, installiert ist. Dies ist der Standardwert.

- `AllUsers` -Dieses optionale Attribut gibt an, ob dieses Paket für alle Benutzer installiert wird. Standardmäßig ist dieses Attribut false, das angibt, dass das Paket pro Benutzer ist. (Wenn Sie diesen Wert auf "true" festlegen, muss der Benutzer, der die Installation durchführt, auf die Administrator Berechtigungsebene herauf Stufen, um die resultierenden VSIX

- `InstalledByMsi` -Dieses optionale Attribut gibt an, ob dieses Paket von einer MSI installiert wird. Von einer MSI installierte Pakete werden von MSI (Programme und Funktionen) und nicht vom Erweiterungs-Manager von Visual Studio installiert und verwaltet.  Standardmäßig ist dieses Attribut auf false festgelegt, das angibt, dass das Paket nicht von einer MSI-Installation installiert wird.

- `SystemComponent` -Dieses optionale Attribut gibt an, ob dieses Paket als Systemkomponente angesehen werden soll. System Komponenten werden in der Erweiterungs-Manager-Benutzeroberfläche nicht angezeigt und können nicht aktualisiert werden. Standardmäßig ist dieses Attribut false, das angibt, dass das Paket keine Systemkomponente ist.

- `AnyAttribute*` -Das- `Installation` Element akzeptiert einen geöffneten Satz von Attributen, der zur Laufzeit als Name-Wert-Paar Wörterbuch verfügbar gemacht wird.

- `<InstallationTarget>` -Dieses Element steuert den Speicherort, an dem das VSIX-Installationsprogramm das Paket installiert. Wenn der Wert des `Scope` Attributs "productextension" ist, muss das Paket eine SKU als Ziel haben, die eine Manifest-Datei als Teil des Inhalts installiert hat, um die Verfügbarkeit für Erweiterungen ankündigen zu können. Das- `<InstallationTarget>` Element weist die folgenden Attribute auf, wenn das `Scope` Attribut den expliziten oder Standardwert "productextension" hat:

  - `Id` : Dieses Attribut identifiziert das Paket.  Das-Attribut folgt der-Namespace Konvention: Company.Product.Feature.Name. Das `Id` Attribut darf nur alphanumerische Zeichen enthalten und ist auf 100 Zeichen beschränkt. Erwartete Werte:

    - Microsoft. VisualStudio. integratedshell

    - Microsoft.VisualStudio.Pro

    - Microsoft. VisualStudio. Premium

    - Microsoft. VisualStudio. Ultimate

    - Microsoft. VisualStudio. VWDExpress

    - Microsoft. VisualStudio. vpdexpress

    - Microsoft. VisualStudio. vswinexpress

    - Microsoft. VisualStudio. vsls

    - My. Shell. app

  - `Version` : Dieses Attribut gibt einen Versions Bereich mit den minimalen und maximal unterstützten Versionen dieser SKU an. Ein Paket kann die Versionen der SKUs detailliert beschreiben, die es unterstützt. Die Notation des Versions Bereichs ist [10,0-11,0], wobei

    - [-Minimale inklusive Version.

    - ]-maximale Version einschließlich.

    - (-mindestens Version exklusiv.

    - )-maximale Version exklusiv.

    - Einzelne Version #-nur die angegebene Version.

    > [!IMPORTANT]
    > Version 2,0 des VSIX-Schemas wurde in Visual Studio 2012 eingeführt. Um dieses Schema zu verwenden, muss Visual Studio 2012 oder höher auf dem Computer installiert sein, und der VSIXInstaller.exe, der Teil des Produkts ist, muss verwendet werden. Sie können frühere Versionen von Visual Studio mit einem vsixinstaller von Visual Studio 2012 oder höher als Ziel verwenden, jedoch nur mit den neueren Versionen des Installationsprogramms.

    Visual Studio 2017-Versionsnummern finden Sie unter [Visual Studio-Buildnummern und Veröffentlichungstermine](../install/visual-studio-build-numbers-and-release-dates.md).

    Wenn Sie die Version für Visual Studio 2017-Releases Ausdrücken, sollte die neben Version immer **0** sein. Beispielsweise sollte Visual Studio 2017 Version 15.3.26730.0 als [15.0.26730.0, 16,0) ausgedrückt werden. Dies ist nur für Visual Studio 2017 und spätere Versionsnummern erforderlich.

  - `AnyAttribute*` -Das- `<InstallationTarget>` Element ermöglicht einen offenen Satz von Attributen, der zur Laufzeit als Name-Wert-Paar Wörterbuch verfügbar gemacht wird.

### <a name="dependencies-element"></a>Abhängigkeiten-Element
 Dieses Element enthält eine Liste mit Abhängigkeiten, die von diesem Paket deklariert werden. Wenn Abhängigkeiten angegeben werden, müssen diese Pakete (identifiziert durch ihre `Id` ) vor installiert werden.

- `<Dependency>` -Element: dieses untergeordnete Element weist die folgenden Attribute auf:

  - `Id` : Dieses Attribut muss eine eindeutige ID für das abhängige Paket sein. Dieser Identitäts Wert muss mit dem `<Metadata><Identity>Id` Attribut eines Pakets, von dem dieses Paket abhängt, identisch sein. Das- `Id` Attribut folgt der-Namespace Konvention: Company.Product.Feature.Name. Das Attribut darf nur alphanumerische Zeichen enthalten und ist auf 100 Zeichen beschränkt.

  - `Version` : Dieses Attribut gibt einen Versions Bereich mit den minimalen und maximal unterstützten Versionen dieser SKU an. Ein Paket kann die Versionen der SKUs detailliert beschreiben, die es unterstützt. Die Notation für den Versions Bereich ist [12,0, 13,0], wobei Folgendes gilt:

    - [-Minimale inklusive Version.

    - ]-maximale Version einschließlich.

    - (-mindestens Version exklusiv.

    - )-maximale Version exklusiv.

    - Einzelne Version #-nur die angegebene Version.

  - `DisplayName` : Dieses Attribut ist der Anzeige Name des abhängigen Pakets, das in Benutzeroberflächen Elementen wie Dialogfeldern und Fehlermeldungen verwendet wird. Das-Attribut ist optional, es sei denn, das abhängige Paket wird von MSI installiert.

  - `Location` : Dieses optionale Attribut gibt entweder den relativen Pfad innerhalb dieser VSIX zu einem geschachtelten VSIX-Paket oder eine URL zum Download Speicherort für die Abhängigkeit an. Dieses Attribut wird verwendet, um den Benutzer beim Auffinden des erforderlichen Pakets zu unterstützen.

  - `AnyAttribute*` -Das- `Dependency` Element akzeptiert einen geöffneten Satz von Attributen, der zur Laufzeit als Name-Wert-Paar Wörterbuch verfügbar gemacht wird.

### <a name="assets-element"></a>Assets-Element
 Dieses Element enthält eine Liste von `<Asset>` Tags für jede Erweiterung bzw. jedes Inhalts Element, das von diesem Paket angezeigt wird.

- `<Asset>` -Dieses Element enthält die folgenden Attribute und Elemente:

  - `Type` : Der Typ der Erweiterung oder des Inhalts, der durch dieses Element dargestellt wird. Jedes `<Asset>` Element muss über ein einzelnes verfügen `Type` , aber mehrere `<Asset>` Elemente haben möglicherweise dieselbe `Type` . Dieses Attribut sollte gemäß den Namespace Konventionen als voll qualifizierter Name dargestellt werden. Die bekannten Typen lauten wie folgt:

    1. Microsoft. VisualStudio. VSPackage

    2. Microsoft.VisualStudio.MefComponent

    3. Microsoft. VisualStudio. ToolboxControl

    4. Microsoft. VisualStudio. Samples

    5. Microsoft. VisualStudio. ProjectTemplate

    6. Microsoft. VisualStudio. ItemTemplate

    7. Microsoft. VisualStudio. Assembly

       Sie können eigene Typen erstellen und Ihnen eindeutige Namen zuordnen. Zur Laufzeit innerhalb von Visual Studio kann Ihr Code diese benutzerdefinierten Typen mithilfe der Erweiterungs-Manager-API auflisten und darauf zugreifen.

  - `Path` : der relative Pfad zur Datei oder zum Ordner innerhalb des Pakets, das das Medienobjekt enthält.

  - `TargetVersion` -der Versions Bereich, für den das angegebene Asset gilt. Wird zum Versenden mehrerer Versionen von Assets an verschiedene Versionen von Visual Studio verwendet. Erfordert, dass Visual Studio 2017,3 oder höher wirksam ist.

  - `AnyAttribute*` : Ein offener Satz von Attributen, der zur Laufzeit als Name-Wert-Paar Wörterbuch verfügbar gemacht wird.

    `<AnyElement>*` -Jeder strukturierte Inhalt ist zwischen einem `<Asset>` Begin-und einem Endtag zulässig. Alle-Elemente werden als Liste von XmlElement-Objekten verfügbar gemacht. VSIX-Erweiterungen können strukturierte typspezifische Metadaten in der Manifest-Datei definieren und diese zur Laufzeit auflisten.

### <a name="sample-manifest"></a>Beispielmanifest

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
  <Metadata>
    <Identity Id="0000000-0000-0000-0000-000000000000" Version="1.0" Language="en-US" Publisher="Company" />
    <DisplayName>Test Package</DisplayName>
    <Description>Information about my package</Description>
    <MoreInfo>http://www.fabrikam.com/Extension1/</MoreInfo>
    <License>eula.rtf</License>
    <ReleaseNotes>notes.txt</ReleaseNotes>
    <Icon>Images\icon.png</Icon>
    <PreviewImage>Images\preview.png</PreviewImage>
  </Metadata>
  <Installation InstalledByMsi="false" AllUsers="false" SystemComponent="false" Scope="ProductExtension">
    <InstallationTarget Id="Microsoft.VisualStudio.Pro" Version="[11.0, 12.0]" />
  </Installation>
  <Dependencies>
    <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="[4.5,)" />
    <Dependency Id="Microsoft.VisualStudio.MPF.12.0" DisplayName="Visual Studio MPF 12.0" d:Source="Installed" Version="[12.0]" />
  </Dependencies>
  <Assets>
    <Asset Type="Microsoft.VisualStudio.VsPackage" d:Source="Project" d:ProjectName="%CurrentProject%" Path="|%CurrentProject%;PkgdefProjectOutputGroup|" />
  </Assets>
</PackageManifest>
```

## <a name="see-also"></a>Weitere Informationen

- [Lieferumfang von Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md)
