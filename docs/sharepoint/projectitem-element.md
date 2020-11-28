---
title: ProjectItem-Element | Microsoft-Dokumentation
description: Hier finden Sie Referenzinformationen zum ProjectItem-Element, das ein SharePoint-Projekt Element in der XML-Schema Referenz des SharePoint-Projekt Elements darstellt.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItem element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3e211aa44b1402d6667fc3e02ca7e271a29c3ec7
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305054"
---
# <a name="projectitem-element"></a>ProjectItem-Element
  Stellt ein SharePoint-Projekt Element dar. Dieses Element ist das erforderliche Stamm Element der *spdata* -Datei.

## <a name="syntax"></a>Syntax

```xml
<ProjectItem DefaultFile = "File that opens in the editor when you open the project item"
    FeatureReceiverClass = "Class that implements a feature receiver for the project item"
    FeatureReceiverAssembly = "Assembly that defines a feature receiver for the project item"
    SupportedTrustLevels = "Trust levels that the project item supports"
    SupportedDeploymentScopes = "Deployment scopes that the project item supports"
    Type="Identifier for the project item">
  <Files>...</Files>
  <ProjectItemFolder>...</ProjectItemFolder>
  <SafeControls>...</SafeControls>
  <FeatureProperties>...</FeatureProperties>
  <ExtensionData>...</ExtensionData>
</ProjectItem>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|Beschreibung|
|---------------|-----------------|
|**DefaultFile**|Optionales **xs: String** -Attribut.<br /><br /> Der relative Pfad (einschließlich des Datei namens) der Datei, die im Visual Studio-Editor geöffnet wird, wenn Sie das SharePoint-Projekt Element in **Projektmappen-Explorer** öffnen. Der Pfad ist relativ zum Ordner, der die *spdata* -Datei enthält.|
|**Featurereceiverclass**|Optionales **xs: String** -Attribut.<br /><br /> Der voll qualifizierte Name einer Funktions Empfängerklasse für dieses SharePoint-Projekt Element. Weitere Informationen zu Funktions Empfängern finden Sie unter [Bereitstellen von Verpackungs-und Bereitstellungs Informationen in Projekt Elementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|
|**Featurereceiverassembly**|Optionales **xs: String** -Attribut.<br /><br /> Gibt den voll qualifizierten Namen einer Assembly an, die einen Funktions Empfänger für dieses SharePoint-Projekt Element definiert. Weitere Informationen zu Funktions Empfängern finden Sie unter [Bereitstellen von Verpackungs-und Bereitstellungs Informationen in Projekt Elementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md). Weitere Informationen zu voll qualifizierten Assemblynamen finden [Assembly Names](/dotnet/framework/app-domains/assembly-names)Sie unter Assemblynamen.|
|**SupportedTrustLevels**|Optionales **xs: String** -Attribut.<br /><br /> Gibt die Vertrauens Ebenen an, die von diesem SharePoint-Projekt Element unterstützt werden. Bei diesem Wert kann es sich um eine der folgenden Zeichen folgen handeln: Sandbox, FullTrust oder all. Der Wert all gibt sowohl Sandboxed als auch FullTrust an.<br /><br /> In einem benutzerdefinierten SharePoint-Projekt Elementtyp entspricht der Wert dieses Attributs dem Wert, den Sie der- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> Eigenschaft in der Implementierung der- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> Methode zuweisen. Wenn Sie einen anderen Wert für dieses Attribut angeben, überschreibt Visual Studio den Wert, sodass er die gleiche Vertrauens Ebene angibt, die Sie in der- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> Eigenschaft angeben.|
|**SupportedDeploymentScopes**|Optionales **xs: String** -Attribut.<br /><br /> Gibt die Bereitstellungs Bereiche an, die dieses SharePoint-Projekt Element unterstützt. Dieser Wert ist eine durch Trennzeichen getrennte Zeichenfolge, die aus einer oder mehreren der folgenden Zeichen folgen besteht: Farm, Site, Web, WebApplication oder Package. Beispiel: `Web, Site`<br /><br /> In einem benutzerdefinierten SharePoint-Projekt Elementtyp entspricht der Wert dieses Attributs dem Wert, den Sie der- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> Eigenschaft in der Implementierung der- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> Methode zuweisen. Wenn Sie einen anderen Wert für dieses Attribut angeben, überschreibt Visual Studio den Wert, sodass er die gleiche Vertrauens Ebene angibt, die Sie in der- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> Eigenschaft angeben.|
|**Type**|Erforderliches **xs: String** -Attribut.<br /><br /> Der Bezeichner für das SharePoint-Projekt Element. In einem benutzerdefinierten SharePoint-Projekt Elementtyp ist der Bezeichner die Zeichenfolge, die Sie an das-Objekt übergeben <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> . Weitere Informationen finden Sie unter Gewusst [wie: Definieren eines SharePoint-Projekt Elementtyps](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).<br /><br /> Eine Liste der Bezeichner für die integrierten SharePoint-Projekt Elemente, die in Visual Studio enthalten sind, finden Sie unter [Erweitern von SharePoint-Projekt Elementen](../sharepoint/extending-sharepoint-project-items.md).|

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|Optionales Element.<br /><br /> Stellt eine Auflistung benutzerdefinierter Datenelemente dar, die dem SharePoint-Projekt Element zugeordnet sind.<br /><br /> Sie können nur ein **ExtensionData** -Element einschließen.|
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Optionales Element.<br /><br /> Stellt eine Auflistung von Eigenschafts Werten dar, die in einer Funktion enthalten sind, wenn Sie in SharePoint bereitgestellt wird.<br /><br /> Sie können nur ein **FeatureProperties** -Element einschließen.|
|[Dateien](../sharepoint/files-element.md)|Optionales **filecollectiontype** -Element.<br /><br /> Gibt die Dateien an, die mit dem SharePoint-Projekt Element bereitgestellt werden sollen, z. b. featureelementdateien und die Ausgabe abhängiger nicht-SharePoint-Projekte.<br /><br /> Fügen Sie entweder eine- **Datei** oder ein **projectitemfolder** -Element ein, aber nicht beides.|
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Optionales **projectitemfoldertype** -Element.<br /><br /> Stellt einen zugeordneten Ordner dar.<br /><br /> Fügen Sie entweder eine- **Datei** oder ein **projectitemfolder** -Element ein, aber nicht beides.|
|["SafeControls](../sharepoint/safecontrols-element.md)|Optionales Element.<br /><br /> Stellt eine Auflistung von ASPX-Steuerelementen und Webparts dar, die für jeden Benutzer auf einer beliebigen ASPX-Seite auf der SharePoint-Website als sicher gekennzeichnet sind.<br /><br /> Sie können nur ein **SafeControls** -Element einschließen.|

### <a name="parent-elements"></a>Übergeordnete Elemente
 Keine.

## <a name="element-information"></a>Elementinformationen

|Eigenschaft|Wert|
|-|-|
|**Namespace**|http: \/ \/ Schemas.Microsoft.com/VisualStudio/<br>2010/sharepointtools/sharepointprojectitemmodel|
|**Schemaname**|SharePoint-Projekt Element Schema|
|**Validierungs Datei**|Projectitemmodelschema. xsd|
|**Kann leer sein**|Nein|

## <a name="see-also"></a>Weitere Informationen
[Schema-rseference für SharePoint-Projekt Element](../sharepoint/sharepoint-project-item-schema-reference.md)
