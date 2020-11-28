---
title: Zusammenführen von XML in Funktions-und Paket Manifesten | Microsoft-Dokumentation
description: Von Merge-Designer generierter und vom Benutzer hinzugefügter XML-Code in SharePoint-Funktions-und Paket Manifesten Erlernen Sie Funktions-und Paket Manifest-Elemente und Merge-Ausnahmen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 16305ed63f48d9f14e35aeb8d37e35f23f40be25
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304229"
---
# <a name="merge-xml-in-feature-and-package-manifests"></a>Zusammenführen von XML in Funktions-und Paket Manifesten
  Funktionen und Pakete werden durch [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Manifest-Dateien definiert. Diese gepackten Manifeste stellen eine Kombination aus Daten dar, die von Designern generiert werden, und benutzerdefinierte Daten, [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] die von Benutzern in der Zum Zeitpunkt der Paket Erstellung werden [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] die benutzerdefinierten [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Anweisungen mit dem vom Designer bereitgestellten zusammengeführt, [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] um die gepackte Manifest-Datei zu bilden [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Ähnliche Elemente, mit den Ausnahmen, die später in mergeausnahmen notiert werden, werden zusammengeführt, um [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Validierungs Fehler zu vermeiden, nachdem Sie die Dateien in SharePoint bereitgestellt haben, und um die Manifest-Dateien zu verkleinern und effizienter zu gestalten.

## <a name="modify-the-manifests"></a>Ändern der Manifeste
 Sie können die gepackten Manifest-Dateien erst direkt ändern, wenn Sie die Funktion oder die Paket-Designer deaktivieren. Allerdings können Sie benutzerdefinierte [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Elemente manuell der Manifest-Vorlage hinzufügen, entweder über die Funktions-und Paket-Designer oder den [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Editor. Weitere Informationen finden Sie unter Gewusst [wie: Anpassen einer SharePoint-Funktion](../sharepoint/how-to-customize-a-sharepoint-feature.md) und Gewusst [wie: Anpassen eines SharePoint-Lösungs Pakets](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

## <a name="feature-and-package-manifest-merge-process"></a>Merge-Prozess für Funktions-und Paket Manifest
 Wenn Sie benutzerdefinierte Elemente zusammen mit vom Designer bereitgestellten Elementen kombinieren, wird von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] der folgende Prozess verwendet. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] überprüft, ob jedes Element über einen eindeutigen Schlüsselwert verfügt. Wenn ein Element keinen eindeutigen Schlüsselwert aufweist, wird es an die gepackte Manifest-Datei angehängt. Ebenso können Elemente, die über mehrere Schlüssel verfügen, nicht zusammengeführt werden. Daher werden Sie an die Manifest-Datei angehängt.

 Wenn ein Element über einen eindeutigen Schlüssel verfügt, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vergleicht die Werte des Designers und der benutzerdefinierten Schlüssel. Wenn die Werte stimmen, werden Sie zu einem einzelnen Wert zusammengeführt. Wenn sich die Werte unterscheiden, wird der Designer Schlüsselwert verworfen, und der benutzerdefinierte Schlüsselwert wird verwendet. Sammlungen werden ebenfalls zusammengeführt. Wenn beispielsweise der vom Designer generierte [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] und die benutzerdefinierten beide eine assemblyauflistung [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] enthalten, enthält das Paket Manifest nur eine assemblyauflistung.

## <a name="merge-exceptions"></a>Merge-Ausnahmen
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] führt die meisten Designer [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Elemente zusammen mit ähnlichen benutzerdefinierten [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Elementen zusammen, sofern Sie über ein einzelnes eindeutiges identifizierendes Attribut verfügen. Einige Elemente fehlen jedoch dem eindeutigen Bezeichner, der für die Zusammenführung erforderlich ist [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] . Diese Elemente werden als *Merge-Ausnahmen* bezeichnet. In diesen Fällen werden [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] die benutzerdefinierten Elemente nicht [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] zusammen mit den vom Designer bereitgestellten [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Elementen zusammengeführt, sondern an die gepackte Manifest-Datei angehängt.

 Im folgenden finden Sie eine Liste von Merge-Ausnahmen für Feature-und Paket [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Manifest-Dateien.

|Designer|XML-Element|
|--------------|-----------------|
|Funktions-Designer|Activationabhängigkeit|
|Funktions-Designer|Upgradeaction|
|Paket-Designer|SafeControl|
|Paket-Designer|CodeAccessSecurity|

## <a name="feature-manifest-elements"></a>Feature-Manifest-Elemente
 In der folgenden Tabelle finden Sie eine Liste aller featuremanifeselemente, die zusammengeführt werden können, und deren eindeutiger Schlüssel für den Abgleich.

|Elementname|Eindeutiger Schlüssel|
|------------------|----------------|
|Feature (alle Attribute)|*Attribut Name* (jeder Attribut Name des Feature-Elements ist ein eindeutiger Schlüssel.)|
|ElementFile|Speicherort|
|Elementmanifests/Element Manifest|Speicherort|
|Eigenschaften/Eigenschaft|Key|
|Customupgradeaction|Name|
|Customupgradebug-Parameter|Name|

> [!NOTE]
> Da sich die einzige Möglichkeit zum Ändern des customupgradeaction-Elements im benutzerdefinierten [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Editor befindet, ist die Auswirkung der nicht Zusammenführung gering.

## <a name="package-manifest-elements"></a>Paket Manifest-Elemente
 Die folgende Tabelle ist eine Liste aller Paket Manifest-Elemente, die zusammengeführt werden können, und ihrer eindeutigen Schlüssel, der für den Abgleich verwendet wird.

|Elementname|Eindeutiger Schlüssel|
|------------------|----------------|
|Lösung (alle Attribute)|*Attribut Name* (jeder Attribut Name des projektmappenelements ist ein eindeutiger Schlüssel.)|
|ApplicationResourceFiles/ApplicationResourceFile|Speicherort|
|Assemblys/Assembly|Speicherort|
|ClassResources/ClassResource|Speicherort|
|DwpFiles/DwpFile|Speicherort|
|Featuremanifeste/FeatureManifest|Speicherort|
|Ressourcen/Ressource|Speicherort|
|RootFiles/RootFile|Speicherort|
|SiteDefinitionManifests/SiteDefinitionManifest|Speicherort|
|WebTempFile|Speicherort|
|TemplateFiles/TemplateFile|Speicherort|
|Solutionabhängigkeit|SolutionID|

## <a name="manually-add-deployed-files"></a>Manuell bereitgestellte Dateien hinzufügen
 Einige Manifest-Elemente, wie z. b. ApplicationResourceFile und DwpFiles, geben einen Speicherort an, der einen Dateinamen enthält. Durch das Hinzufügen eines Datei namens Eintrags zur Manifest-Vorlage wird jedoch nicht die zugrunde liegende Datei zum Paket hinzugefügt. Sie müssen die Datei dem Projekt hinzufügen, um Sie in das Paket einzuschließen, und die zugehörige Eigenschaft des Bereitstellungs Typs entsprechend festlegen.

## <a name="see-also"></a>Siehe auch
- [Packen und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [Erstellen und Debuggen von SharePoint-Lösungen](../sharepoint/building-and-debugging-sharepoint-solutions.md)
