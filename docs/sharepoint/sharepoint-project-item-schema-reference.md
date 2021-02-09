---
title: Schema Referenz für SharePoint-Projekt Elemente | Microsoft-Dokumentation
description: Weitere Informationen finden Sie in der Übersicht über die XML-Schema Referenz des SharePoint-Projekt Elements (projectitemmodelschema. xsd), die zum Überprüfen des Inhalts von spdata-Dateien verwendet wird.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperty element
- SafeControls element
- SafeControl element
- .spdata files
- ExtensionData element
- FeatureProperties element
- ProjectOutputFile element
- Files element
- ProjectItemFolder element
- ProjectItemFile element
- ExtensionDataItem element
- ProjectItem element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 466bc68ca002914b64698d7cd87f98ff276bfc0e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892280"
---
# <a name="sharepoint-project-item-schema-reference"></a>Schema Referenz für SharePoint-Projekt Elemente
  Visual Studio verwendet das SharePoint-Projekt Element Schema, um den Inhalt von *spdata* -Dateien zu validieren. Eine *spdata* -Datei gibt den Inhalt und das Verhalten eines SharePoint-Projekt Elements an. Weitere Informationen zum Inhalt von SharePoint-Projekt Elementen finden Sie unter [Erstellen von Element Vorlagen und Projektvorlagen für SharePoint-Projekt Elemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Das SharePoint-Projekt Element Schema heißt projectitemmodelschema. xsd und wird standardmäßig in% Program Files (x86)% \ Microsoft Visual Studio 11.0 \ xml\schemas installiert.

 Das root-Element ist das [ProjectItem](../sharepoint/projectitem-element.md) -Element. In der folgenden Tabelle werden alle durch das Schema definierten Elemente beschrieben.

|Element|Beschreibung|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|Stellt eine Auflistung benutzerdefinierter Datenelemente dar, die dem SharePoint-Projekt Element zugeordnet sind.|
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Stellt ein benutzerdefiniertes Datenelement dar, das dem SharePoint-Projekt Element im Schlüssel-Wert-Format zugeordnet ist. Sowohl der Schlüssel als auch der Wert müssen Zeichen folgen sein.|
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Stellt eine Auflistung von Eigenschafts Werten dar, die in einer Funktion enthalten sind, wenn Sie in SharePoint bereitgestellt wird. Nachdem eine Funktion bereitgestellt wurde, können Sie auf die Eigenschaftswerte im Code zugreifen.|
|[FeatureProperty](../sharepoint/featureproperty-element.md)|Stellt eine benutzerdefinierte Eigenschaft dar, die in einer Funktion enthalten ist, wenn Sie in SharePoint bereitgestellt wird. Nachdem eine Funktion bereitgestellt wurde, können Sie auf die-Eigenschaft im Code zugreifen.|
|[Dateien](../sharepoint/files-element.md)|Gibt die Dateien an, die mit dem SharePoint-Projekt Element bereitgestellt werden sollen, z. b. eine featureelementdatei oder die Ausgabe eines Projekts.|
|[ProjectItem](../sharepoint/projectitem-element.md)|Stellt ein SharePoint-Projekt Element dar.|
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|Stellt eine SharePoint-Datei (z. b. eine featureelementdatei) dar, die beim Bereitstellen in SharePoint in das Projekt Element eingeschlossen werden soll.|
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Stellt einen zugeordneten Ordner dar.|
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|Stellt die Ausgabe eines Projekts dar, das in das Projekt Element aufgenommen werden soll, wenn es in SharePoint bereitgestellt wird.|
|[SafeControl](../sharepoint/safecontrol-element.md)|Stellt ein aspx-Steuerelement oder Webpart dar, das für jeden Benutzer auf einer beliebigen ASPX-Seite auf der SharePoint-Website als sicher eingestuft wird.|
|["SafeControls](../sharepoint/safecontrols-element.md)|Stellt eine Auflistung von ASPX-Steuerelementen und Webparts dar, die für jeden Benutzer auf einer beliebigen ASPX-Seite auf der SharePoint-Website als sicher gekennzeichnet sind.|

## <a name="see-also"></a>Weitere Informationen
- [Erstellen von Element Vorlagen und Projektvorlagen für SharePoint-Projekt Elemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
