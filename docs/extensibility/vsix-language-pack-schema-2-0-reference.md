---
title: VSIX-Sprachpaket Schema 2,0-Referenz | Microsoft-Dokumentation
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- language pack
- localize vsix
- localize package
- localize extension
ms.assetid: 2a2932bc-cdbe-4d32-91fa-a3e0474f9098
author: acangialosi
ms.author: anthc
manager: jillfra
ms.openlocfilehash: f0eee51c0654c6e517209e23baf43c6b262d8f73
ms.sourcegitcommit: c31815e140f2ec79e00a9a9a19900778ec11e860
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/08/2020
ms.locfileid: "91830706"
---
# <a name="vsix-language-pack-schema-20-reference"></a>VSIX-Sprachpaket Schema 2,0 Referenz

Das VSIX-Sprachpaket Schema enthält lokalisierte Installationsinformationen für VSIX-Pakete. In Version 2,0 dieses Schemas werden zusätzliche Lokalisierungs Elemente unterstützt.

## <a name="language-pack-schema"></a>Sprachpaket Schema

Das Stamm Element der Language Pack-Datei ist `<PackageLanguagePackManifest>` mit dem-Attribut `Version` , das die Version des Sprachpaket Formats ist. In diesem Artikel wird die Version 2,0 des Sprachpaket Formats beschrieben, das im Manifest angegeben ist, indem das- `Version` Attribut auf den Wert festgelegt wird `Version="2.0.0"` . Das root-Element enthält genau ein untergeordnetes `<Metadata>` Element.

### <a name="packagelanguagepackmanifest-element"></a>Packagelanguagepackmanifest-Element

Innerhalb des- `<PackageLanguagePackManifest>` Elements muss das folgende-Element vorhanden sein:

|Titel|Beschreibung|
|-----------|-----------------|
|`<Metadata>`| Das enthaltende Element für alle lokalisierten Paket Metadaten.

### <a name="metadata-element"></a>Metadata-Element

Innerhalb des- `<Metadata>` Elements können Sie über die folgenden Elemente verfügen:

|Titel|Beschreibung|
|-----------|-----------------|
|`<DisplayName>`|Der lokalisierte Name der zu installierenden Erweiterung.|
|`<Description>`|Die lokalisierte Beschreibung der zu installierenden Erweiterung.|
|`<License>`| Ein Pfad zu einer lokalisierten Version der Lizenz der Erweiterung.|
|`<MoreInfo>`| Ein Link zu lokalisierten Informationen über die Erweiterung|
|`<ReleaseNotes>`| Einen Pfad oder einen Link zu einer lokalisierten Version der Versions Anmerkungen|
|`<Icon>`| Ein Pfad zu einer lokalisierten Version des Erweiterungs Symbols.|

### <a name="sample-manifest"></a>Beispielmanifest

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageLanguagePackManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <DisplayName>Arbol de Familia</DisplayName>
    <Description> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</Description>
    <MoreInfo> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
</PackageLanguagePackManifest>
```

## <a name="see-also"></a>Siehe auch

|Titel|Beschreibung|
|-----------|-----------------|
|[Lokalisieren von VSIX-Paketen](../extensibility/localizing-vsix-packages.md)|Zeigt, wie Sie eine lokalisierte Installationsunterstützung für ein VSIX-Paket bereitstellen.|
|[VSIX-Erweiterungs Schema 2,0-Referenz](../extensibility/vsix-extension-schema-2-0-reference.md)|Ein VSIX-Manifest beschreibt den Inhalt einer *VSIX* -Bereitstellungs Datei. Mithilfe der Bereitstellungs Datei können Sie eine Visual Studio-Erweiterung im Dialogfeld **Erweiterungen und Updates** installieren.|
|[Suchen und Verwenden von Visual Studio-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md)|Zeigt, wie Sie mit dem Dialogfeld **Erweiterungen und Updates** Erweiterungen installieren, entfernen, aktivieren und deaktivieren können.|
