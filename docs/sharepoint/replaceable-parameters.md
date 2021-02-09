---
title: Austauschbare Parameter | Microsoft-Dokumentation
description: Überprüfen Sie die ersetzbaren Parameter (Token), die Werte in Projektdateien für SharePoint-Lösungs Elemente angeben, deren tatsächliche Werte zur Entwurfszeit nicht bekannt sind.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, tokens
- tokens [SharePoint development in Visual Studio]
- replaceable parameters [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, replaceable parameters
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload: office
ms.openlocfilehash: 3eb6e737a1f939e05e6a6be7f2c9ba950fc411d6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889498"
---
# <a name="replaceable-parameters"></a>Austauschbare Parameter
  Ersetzbare Parameter oder *Token* können innerhalb von Projektdateien verwendet werden, um Werte für SharePoint-Lösungs Elemente bereitzustellen, deren tatsächliche Werte zur Entwurfszeit nicht bekannt sind. Sie ähneln den Standardvorlagen Token in der Funktion [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Weitere Informationen finden Sie unter [Vorlagen Parameter](../ide/template-parameters.md).

## <a name="token-format"></a>Tokenformat
 Token beginnen und enden mit einem Dollarzeichen ($). Bei der Bereitstellung werden alle verwendeten Token durch tatsächliche Werte ersetzt, wenn ein Projekt in ein SharePoint-Lösungspaket (*wsp* -Datei) gepackt wird. Beispielsweise kann das Token **$SharePoint. Package.Name $** in die Zeichenfolge "Test SharePoint Package" aufgelöst werden.

## <a name="token-rules"></a>Tokenregeln
 Die folgenden Regeln gelten für Token:

- Token können an beliebiger Stelle in einer Zeile angegeben werden.

- Token können nicht mehrere Zeilen umfassen.

- Das gleiche Token kann in derselben Zeile und in derselben Datei mehrmals angegeben werden.

- In derselben Zeile können unterschiedliche Token angegeben werden.

  Token, die diese Regeln nicht einhalten, werden ignoriert und führen nicht zu einer Warnung oder einem Fehler.

  Die Ersetzung von Token nach Zeichen folgen Werten erfolgt unmittelbar nach der Transformation für das Manifest. Diese Ersetzung ermöglicht dem Benutzer, die Manifest-Vorlagen mit Token zu bearbeiten.

### <a name="token-name-resolution"></a>Tokennamensauflösung
 In den meisten Fällen wird ein Token zu einem bestimmten Wert aufgelöst, unabhängig davon, wo es enthalten ist. Wenn das Token jedoch mit einem Paket oder einer Funktion verknüpft ist, hängt der Wert des Tokens davon ab, wo es enthalten ist. Wenn sich z. b. eine Funktion in Package a befindet, wird das Token in `$SharePoint.Package.Name$` den Wert "Package a" aufgelöst. Wenn das gleiche Feature in Paket b ist, wird in `$SharePoint.Package.Name$` "Package b" aufgelöst.

## <a name="tokens-list"></a>Tokenliste
 In der folgenden Tabelle sind die verfügbaren Token aufgelistet.

|Name|Beschreibung|
|----------|-----------------|
|$SharePoint. Project. filename $|Der Name der enthaltenden Projektdatei, z. b. *newproj. csproj*.|
|$SharePoint. Project. datamewithoutextension $|Der Name der enthaltenden Projektdatei ohne die Dateinamenerweiterung. Beispiel: "newproj".|
|$SharePoint. Project. AssemblyFullName $|Der Anzeige Name (starker Name) der Ausgabeassembly des enthaltenden Projekts.|
|$SharePoint. Project. assemblyFileName $|Der Name der Ausgabeassembly des enthaltenden Projekts.|
|$SharePoint. Project. assemblydateinamewithoutextension $|Der Name der Ausgabeassembly des enthaltenden Projekts ohne die Dateinamenerweiterung.|
|$SharePoint. Project. assemblypublickeytoken $|Das Token des öffentlichen Schlüssels der Ausgabeassembly des enthaltenden Projekts, das in eine Zeichenfolge konvertiert wird. (16-Zeichen im Hexadezimal Format "x2".)|
|$SharePoint. Package.Name $|Der Name des enthaltenden Pakets.|
|$SharePoint. Package. filename $|Der Name der Definitionsdatei des enthaltenden Pakets.|
|$SharePoint. Package. datamewithoutextension $|Der Name (ohne Erweiterung) der Definitionsdatei des enthaltenden Pakets.|
|$SharePoint. Package.ID $|Die SharePoint-ID für das enthaltende Paket. Wenn eine Funktion in mehr als einem Paket verwendet wird, ändert sich dieser Wert.|
|$SharePoint. Feature. filename $|Der Name der Definitionsdatei der enthaltenden Funktion, z. b *. Feature1. Feature*.|
|$SharePoint. Feature. datamewithoutextension $|Der Name der Featuredefinitionsdatei ohne die Dateinamenerweiterung.|
|$SharePoint. Feature. DeploymentPath $|Der Name des Ordners, der die Funktion im Paket enthält. Dieses Token entspricht der Eigenschaft "Bereitstellungs Pfad" im Funktions-Designer. Ein Beispiel Wert ist, "Project1_Feature1".|
|$SharePoint. Feature.ID $|Die SharePoint-ID der enthaltenden Funktion. Dieses Token kann wie alle Token auf Featureebene nur von Dateien verwendet werden, die über eine Funktion in einem Paket enthalten sind, und nicht direkt zu einem Paket außerhalb eines Features hinzugefügt werden.|
|$SharePoint. ProjectItem.Name $|Der Name des Projekt Elements (nicht dessen Dateiname), wie von **ISharePointProjectItem.Name** abgerufen.|
|$SharePoint \<GUID> . Type.. AssemblyQualifiedName $|Der qualifizierte AssemblyName des Typs, der mit dem des Tokens übereinstimmt [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] . Das Format des [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] ist Kleinbuchstaben und entspricht dem Format GUID. ToString ("D") (das heißt, xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).|
|$SharePoint \<GUID> . Type.. FullName $|Der vollständige Name des Typs, der mit der GUID im Token übereinstimmt. Das Format der GUID ist Kleinbuchstaben und entspricht dem Format GUID. ToString ("D") (das heißt, xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).|

## <a name="add-extensions-to-the-token-replacement-file-extensions-list"></a>Hinzufügen von Erweiterungen zur Liste der Dateierweiterungen für Tokenersetzung
 Obwohl Token theoretisch von jeder Datei verwendet werden können, die zu einem SharePoint-Projekt Element gehört, das im Paket enthalten ist, sucht standardmäßig [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nur in Paketdateien, Manifest-Dateien und Dateien, die über die folgenden Erweiterungen verfügen, nach Token:

- [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]

- ASCX

- ASPX

- Webpart

- DWP

  Diese Erweiterungen werden durch das- `<TokenReplacementFileExtensions>` Element in der Datei "Microsoft. VisualStudio. SharePoint. targets" definiert, die sich im Ordner "... \\<Programme \> \msbuild\microsoft\visualstudio\v11.0\sharepointtools" befindet.

  Sie können jedoch zusätzliche Dateierweiterungen zur Liste hinzufügen. Fügen Sie einer `<TokenReplacementFileExtensions>` PropertyGroup in der SharePoint-Projektdatei, die vor dem \<Import> der SharePoint-Zieldatei definiert ist, ein-Element hinzu.

> [!NOTE]
> Da die Tokenersetzung nach der Kompilierung eines Projekts erfolgt, sollten Sie keine Dateierweiterungen für Dateitypen hinzufügen, die kompiliert werden, wie z *. b.. cs*, *. vb* oder *. resx*. Token werden nur in Dateien ersetzt, die nicht kompiliert werden.

 Wenn Sie z. b. der Liste der Dateinamen Erweiterungen für die Tokenersetzung die Dateinamen Erweiterungen (*. MyExtension* und *. yourextension*) hinzufügen möchten, fügen Sie einer Projektdatei (*. csproj*) Folgendes hinzu:

```xml
<Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
    <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
.
.
.
    <!-- Define the following property to add your extension to the list of token replacement file extensions.  -->
<TokenReplacementFileExtensions>myextension;yourextension</TokenReplacementFileExtensions>
</PropertyGroup>
```

 Sie können die Erweiterung direkt *der targets-Datei (Targets*) hinzufügen. Durch das Hinzufügen der Erweiterung ändert sich jedoch die Liste der Erweiterungen für alle SharePoint-Projekte, die auf dem lokalen System verpackt sind, und nicht nur Ihre eigenen. Diese Erweiterung ist möglicherweise praktisch, wenn Sie der einzige Entwickler auf dem System sind oder die meisten ihrer Projekte Sie benötigen. Da es jedoch systemspezifisch ist, kann dieser Ansatz nicht portabel sein, und es wird daher empfohlen, stattdessen alle Erweiterungen zur Projektdatei hinzuzufügen.

## <a name="see-also"></a>Weitere Informationen
- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)
