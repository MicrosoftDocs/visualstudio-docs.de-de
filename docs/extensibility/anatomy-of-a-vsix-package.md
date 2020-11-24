---
title: Anatomie eines VSIX-Pakets | Microsoft-Dokumentation
description: Erfahren Sie mehr über den Inhalt eines VSIX-Pakets in Visual Studio, eine Datei, die mindestens eine Visual Studio-Erweiterung und eine metadatenmanifestressdatei enthält.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3fc65cda5eb969e361e90771e0245fdaeaeebcd1
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/24/2020
ms.locfileid: "95598158"
---
# <a name="anatomy-of-a-vsix-package"></a>Anatomie eines VSIX-Pakets
Bei einem VSIX-Paket handelt es sich um eine *VSIX* -Datei, die eine oder mehrere Visual Studio-Erweiterungen enthält, sowie die Metadaten, die Visual Studio zum klassifizieren und Installieren der Erweiterungen verwendet. Diese Metadaten sind im VSIX-Manifest und in der Datei *[Content_Types]. XML* enthalten. Ein VSIX-Paket kann auch eine oder mehrere *Extension. vsixlangpack* -Dateien enthalten, um lokalisierten Setup Text bereitzustellen, und kann weitere VSIX-Pakete enthalten, um Abhängigkeiten zu installieren.

 Das VSIX-Paketformat folgt dem OPC-Standard (Open Packaging Conventions). Das Paket enthält Binärdateien und unterstützende Dateien sowie eine *[Content_Types]. XML* -Datei und eine *VSIX* -Manifest-Datei. Ein VSIX-Paket kann die Ausgabe mehrerer Projekte oder sogar mehrerer Pakete enthalten, die eigene Manifeste enthalten.

> [!NOTE]
> Die Namen der Dateien, die in VSIX-Paketen enthalten sind, dürfen keine Leerzeichen und keine Zeichen enthalten, die in URI (Uniform Resource Identifier) reserviert sind, wie unter [ \[ rfc2396 \] ](https://www.rfc-editor.org/rfc/rfc2396.txt)definiert.

## <a name="the-vsix-manifest"></a>Das VSIX-Manifest
 Das VSIX-Manifest enthält Informationen über die zu installierende Erweiterung und folgt dem VSX-Schema. Weitere Informationen finden Sie in der [Referenz zum VSIX-Erweiterungs Schema 1,0](/previous-versions/dd393700(v=vs.110)). Ein Beispiel für ein VSIX-Manifest finden Sie unter [packagemanifest-Element (Stamm Element, VSX-Schema)](/previous-versions/dd393754(v=vs.110)).

 Das VSIX-Manifest muss benannt werden, `extension.vsixmanifest` Wenn es in einer ^. vsix *-Datei enthalten ist.

## <a name="the-content"></a>der Inhalt
 Ein VSIX-Paket kann Vorlagen, Toolbox Elemente, VSPackages oder eine beliebige andere Art von Erweiterung enthalten, die von Visual Studio unterstützt wird.

## <a name="language-packs"></a>Sprachpakete
 Ein VSIX-Paket kann eine oder mehrere *Extension. vsixlangpack* -Dateien enthalten, um lokalisierten Text während der Installation bereitzustellen. Weitere Informationen finden Sie unter [Lokalisieren von VSIX-Paketen](../extensibility/localizing-vsix-packages.md).

## <a name="dependencies-and-references"></a>Abhängigkeiten und Verweise
 Ein VSIX-Paket kann andere VSIX-Pakete als Verweise enthalten. Jedes dieser anderen Pakete muss ein eigenes VSIX-Manifest enthalten.

 Wenn ein Benutzer versucht, eine Erweiterung zu installieren, die Abhängigkeiten aufweist, wird vom Installationsprogramm überprüft, ob die erforderlichen Assemblys auf dem Benutzersystem installiert sind. Wenn die erforderlichen Assemblys nicht gefunden werden, wird in **Erweiterungen und Updates** eine Liste der fehlenden Assemblys angezeigt.

 Wenn das Erweiterungs Manifest ein oder mehrere [Verweis](/previous-versions/visualstudio/visual-studio-2010/dd393687(v=vs.100)) Elemente enthält, vergleicht **Erweiterungen und Updates** das Manifest jedes Verweises mit den Erweiterungen, die auf dem System installiert sind, und installiert die referenzierte Erweiterung, wenn Sie nicht bereits installiert ist. Wenn eine frühere Version einer Erweiterung installiert ist, auf die verwiesen wird, ersetzt Sie die neuere Version.

 Wenn ein Projekt in einer Projekt Mappe mit mehreren Projekten einen Verweis auf ein anderes Projekt in der gleichen Projekt Mappe enthält, enthält das VSIX-Paket die Abhängigkeiten des Projekts. Sie können dieses Verhalten überschreiben, indem Sie den Verweis für das interne Projekt auswählen und dann im **Eigenschaften** Fenster die in der **VSIX-Eigenschaft enthaltenen Ausgabe Gruppen** auf festlegen `BuiltProjectOutputGroup` .

 Um Satelliten-DLLs aus referenzierten Assemblys im VSIX-Paket einzuschließen, fügen Sie `SatelliteDllsProjectOutputGroup` den **in der VSIX-Eigenschaft enthaltenen Ausgabe Gruppen** hinzu.

## <a name="installation-location"></a>Installationspfad
 Während der Installation sucht **Extensions und Updates** nach dem Inhalt des VSIX-Pakets in einem Ordner unter *%LocalAppData%\microsoft\visualstudio\14.0\Extensions*.

 Standardmäßig gilt die Installation nur für den aktuellen Benutzer, da *% LocalAppData%* ein benutzerspezifisches Verzeichnis ist. Wenn Sie jedoch das [ALLUSERS](/previous-versions/ee191547(v=vs.110)) -Element des Manifests auf festlegen `True` , wird die Erweiterung unter installiert <em>. \\ </em> Visualstudioinstallationfolder<em>\common7\ide\Extensions</em> und steht allen Benutzern des Computers zur Verfügung.

## <a name="content_typesxml"></a>[Content_Types]. XML
 Die Datei *[Content_Types]. XML* identifiziert die Dateitypen in der erweiterten *VSIX* -Datei. Visual Studio verwendet diese Datei bei der Installation des Pakets, installiert die Datei jedoch nicht selbst. Weitere Informationen zu dieser Datei finden Sie [in der Struktur der Datei [Content_Types]. XML](the-structure-of-the-content-types-dot-xml-file.md).

 Eine *[Content_Types]. XML* -Datei wird vom OPC-Standard (Open Packaging Conventions) benötigt. Weitere Informationen zu OPC finden Sie unter [OPC: ein neuer Standard zum Verpacken Ihrer Daten](/archive/blogs/msdnmagazine/opc-a-new-standard-for-packaging-your-data) auf der MSDN-Website.