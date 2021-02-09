---
title: Manifest from Resources | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie mit dem Manifest from Resources Tool PNG-oder XAML-Dateien zu einer. imagemanifest-Datei hinzufügen, um Sie mit dem Visual Studio-Image Dienst zu verwenden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 65e4b16beefdef765fe52afd9d84e64a767999fa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839427"
---
# <a name="manifest-from-resources"></a>Manifest aus Ressourcen
Das Manifest from Resources Tool ist eine Konsolenanwendung, die eine Liste von Bild Ressourcen (PNG-oder XAML-Dateien) annimmt und eine imagemanifest-Datei generiert, mit der diese Bilder mit dem Visual Studio-Image Dienst verwendet werden können. Darüber hinaus kann dieses Tool zum Hinzufügen von Bildern zu einem vorhandenen imagemanifest verwendet werden. Dieses Tool ist nützlich, wenn Sie einer Visual Studio-Erweiterung High-dpi-und Designunterstützung für Bilder hinzufügen möchten. Die generierte. imagemanifest-Datei sollte in einer Visual Studio-Erweiterung (VSIX-Datei) enthalten und bereitgestellt werden.

## <a name="how-to-use-the-tool"></a>Verwenden des Tools
 **Syntax**

 ManifestFromResources/Resources: \<Dir1> ; \<Img1> /Assembly: \<AssemblyName>\<Optional Args>

 **Argumente**

|**SwitchName**|**Hinweise**|**Erforderlich oder optional**|
|-|-|-|
|/resources|Eine durch Semikolons getrennte Liste von Bildern oder Verzeichnissen. Diese Liste sollte immer die vollständige Liste der Images enthalten, die im Manifest enthalten sein werden. Wenn nur eine partielle Liste angegeben wird, gehen die Einträge, die nicht eingeschlossen werden, verloren.<br /><br /> Wenn eine bestimmte Ressourcen Datei ein Bildstreifen ist, teilt das Tool Sie in separate Bilder auf, bevor jedes untergeordnete Element dem Manifest hinzugefügt wird.<br /><br /> Wenn das Image eine PNG-Datei ist, wird empfohlen, den Namen so zu formatieren, dass das Tool die richtigen Attribute für das Bild ausfüllen kann: \<Name> . \<Width> . \<Height> . PNG.|Erforderlich|
|/Assembly|Der Name der verwalteten Assembly (ohne die Erweiterung) oder der Lauf Zeit Pfad der systemeigenen Assembly, die die Ressourcen hostet (relativ zum Lauf Zeit Speicherort des Manifests).|Erforderlich|
|/Manifest|Der Name, der der generierten imagemanifest-Datei übergeben werden soll. Dies kann auch einen absoluten oder relativen Pfad enthalten, um die Datei an einem anderen Speicherort zu erstellen. Der Standardname entspricht dem Assemblynamen.<br /><br /> Standard: \<Current Directory> \\<Assembly \> . imagemanifest|Optional|
|/guidName|Der Name, der dem GUID-Symbol für alle Bilder im generierten Manifest übergeben werden soll.<br /><br /> Standard: assetguid|Optional|
|/rootPath|Der Stammpfad, der entfernt werden muss, bevor verwaltete Ressourcen-URIs erstellt werden. (Dieses Flag ist in Fällen hilfreich, in denen das Tool den relativen URI-Pfad falsch abruft, sodass Ressourcen nicht geladen werden können.)<br /><br /> Standardwert: \<Current Directory>|Optional|
|/recursive|Das Festlegen dieses Flags weist das Tool an, alle Verzeichnisse im/Resources-Argument rekursiv zu durchsuchen. Wenn Sie dieses Flag weglassen, führt dies zu einer einzigen Suche der Verzeichnisse der obersten Ebene.|Optional|
|/isNative|Legen Sie dieses Flag fest, wenn das assemblyargument ein Pfad für eine systemeigene Assembly ist. Lassen Sie dieses Flag aus, wenn das assemblyargument der Name einer verwalteten Assembly ist. (Weitere Informationen zu diesem Flag finden Sie im Abschnitt "Hinweise".)|Optional|
|/newGuids|Das Festlegen dieses Flags weist das Tool an, einen neuen Wert für das GUID-Symbol der Bilder zu erstellen, anstatt den aus dem vorhandenen Manifest zu mergen.|Optional|
|/newIds|Das Festlegen dieses Flags weist das Tool an, neue ID-Symbol Werte für jedes Bild zu erstellen, statt Werte aus dem vorhandenen Manifest zusammenzuführen.|Optional|
|/noLogo|Wenn Sie dieses Flag festlegen, werden die Produkt-und Copyright Informationen nicht gedruckt.|Optional|
|/?|Ausdrucken von Hilfe Informationen.|Optional|
|/help|Ausdrucken von Hilfe Informationen.|Optional|

 **Beispiele**

- ManifestFromResources/Resources: d:\Images/Assembly: My. Assembly. Name/isNative

- ManifestFromResources/resources:D:\Images\Image1.png;D: \images\image1.XAML/Assembly: My. Assembly. Name/Manifest: myimagemanifest. imagemanifest

- ManifestFromResources/resources:D:\Images\Image1.png;D: \images\image1.XAML/Assembly: My. Assembly. Name/guidName: myImages/newGuids/newIds

## <a name="notes"></a>Notizen

- Das Tool unterstützt nur PNG-und XAML-Dateien. Alle anderen Bild-oder Dateitypen werden ignoriert. Für alle nicht unterstützten Typen, die beim Generieren der Ressourcen auftreten, wird eine Warnung generiert. Wenn keine unterstützten Images gefunden werden, nachdem das Tool die Ressourcenverarbeitung abgeschlossen hat, wird ein Fehler generiert.

- Wenn das Tool auf das empfohlene Format für PNG-Bilder folgt, legt das Tool den Wert für die Größe bzw. den Dimensions Wert für die PNG-Datei auf das Format fest, auch wenn es von der tatsächlichen Größe des Bilds abweicht.

- Das width/height-Format kann für PNG-Bilder ausgelassen werden, aber das Tool liest die tatsächliche Breite bzw. Höhe des Bilds und verwendet diese für den Größen-/Dimensionswert des Bilds.

- Wenn Sie dieses Tool mehrmals auf demselben Bildstreifen ausführen, werden doppelte Manifest-Einträge ausgegeben, da das Tool versucht, den Bildstreifen in eigenständige Bilder aufzuteilen und diese dem vorhandenen Manifest hinzuzufügen.

- Das Zusammenführen (Weglassen von/newGuids oder/newIds) sollte nur für Tool generierte Manifeste erfolgen. Manifeste, die auf andere Weise angepasst oder generiert wurden, werden möglicherweise nicht ordnungsgemäß zusammengeführt.

- Manifeste, die für Native Assemblys generiert werden, müssen möglicherweise nach der Generierung Hand bearbeitet werden, damit die ID-Symbole den Ressourcen-IDs aus der RC-Datei der systemeigenen Assembly entsprechen.

## <a name="sample-output"></a>Beispielausgabe
 **Einfaches Bild Manifest**

 Ein Bild Manifest ähnelt dieser XML-Datei:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- This file was generated by the ManifestFromResources tool.-->
<!-- Version: 14.0.15197 -->
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">
  <Symbols>
    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/Images" />
    <Guid Name="AssetsGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />
    <ID Name="MyImage" Value="0" />
  </Symbols>
  <Images>
    <Image Guid="$(AssetsGuid)" ID="$(MyImage)">
      <Source Uri="$(Resources)/Xaml/MyImage.xaml" />
      <Source Uri="$(Resources)/Png/MyImage.16.16.png">
        <Size Value="16" />
      </Source>
    </Image>
  </Images>
  <ImageLists />
</ImageManifest>
```

 **Bild-Manifest für einen Bildstreifen**

 Ein Bild-Manifest für einen Bildstreifen ähnelt dieser XML-Datei:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- This file was generated by the ManifestFromResources tool.-->
<!-- Version: 14.0.15197 -->
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">
  <Symbols>
    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/ImageStrip" />
    <Guid Name="AssetsGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />
    <ID Name="MyImageStrip_0" Value="1" />
    <ID Name="MyImageStrip_1" Value="2" />
    <ID Name="MyImageStrip" Value="3" />
  </Symbols>
  <Images>
    <Image Guid="$(AssetsGuid)" ID="$(MyImageStrip_0)">
      <Source Uri="$(Resources)/MyImageStrip_0.png">
        <Size Value="16" />
      </Source>
    </Image>
    <Image Guid="$(AssetsGuid)" ID="$(MyImageStrip_1)">
      <Source Uri="$(Resources)/MyImageStrip_1.png">
        <Size Value="16" />
      </Source>
    </Image>
  </Images>
  <ImageLists>
    <ImageList Guid="$(AssetsGuid)" ID="$(MyImageStrip)">
      <ContainedImage Guid="$(AssetsGuid)" ID="$(MyImageStrip_0)" />
      <ContainedImage Guid="$(AssetsGuid)" ID="$(MyImageStrip_1)" />
    </ImageList>
  </ImageLists>
</ImageManifest>
```

 **Bild Manifest für Native assemblybildressourcen**

 Ein Bild Manifest für Native Images ähnelt dieser XML-Datei:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- This file was generated by the ManifestFromResources tool.-->
<!-- Version: 14.0.15198 -->
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">
  <Symbols>
    <String Name="Resources" Value="..\Assembly\Folder\My.Assembly.Name" />
    <Guid Name="AssetsGuid" Value="{442d8739-efde-46a4-8f29-e3a1e5e7f8b4}" />
    <ID Name="MyImage1" Value="0" />
    <ID Name="MyImage2" Value="1" />
  </Symbols>
  <Images>
    <Image Guid="$(AssetsGuid)" ID="$(MyImage1)">
      <Source Uri="$(Resources)">
        <Size Value="16" />
        <NativeResource ID="$(MyImage1)" Type="PNG" />
      </Source>
    </Image>
    <Image Guid="$(AssetsGuid)" ID="$(MyImage2)">
      <Source Uri="$(Resources)">
        <Size Value="16" />
        <NativeResource ID="$(MyImage2)" Type="PNG" />
      </Source>
    </Image>
  </Images>
  <ImageLists />
</ImageManifest>
```
