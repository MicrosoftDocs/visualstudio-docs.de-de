---
title: Erstellen von Funktions-und Paket Überprüfungen für SharePoint-Lösungen
titleSuffix: ''
description: Erstellen Sie benutzerdefinierte Validierungsregeln, um das von Visual Studio generierte Projektmappenpaket zu überprüfen oder ein gesamtes Feature zu überprüfen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
- SharePoint development in Visual Studio, validation rules
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8f76abeee6ace851025a29ce6d85b894bf479dfa
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903688"
---
# <a name="create-feature-and-package-validations-for-sharepoint-solutions"></a>Erstellen von Funktions-und Paket Überprüfungen für SharePoint-Lösungen

  Sie können benutzerdefinierte Validierungsregeln erstellen, um das von Visual Studio generierte Lösungspaket zu überprüfen. Sie können eine vollständige Validierung für ein gesamtes Feature oder Paket durchführen, indem Sie im Kontextmenü eines Pakets oder einer Funktion in **PackagingExplorer** über **prüfen auswählen.** Die partielle Validierung wird ausgeführt, wenn Sie dem Projekt neue SharePoint-Projekt Elemente oder-Funktionen hinzufügen, um zu bestimmen, ob sich das Paket oder die Funktion in einem gültigen Zustand befinden würde.

### <a name="to-create-a-custom-package-validation-rule"></a>So erstellen Sie eine benutzerdefinierte Paket Validierungs Regel

1. Erstellen Sie ein Klassenbibliotheksprojekt.

2. Fügen Sie Verweise auf die folgenden Assemblys hinzu:

    - Microsoft.VisualStudio.SharePoint

    - System.ComponentModel.Composition

3. Erstellen Sie eine Klasse, die eine der folgenden Schnittstellen implementiert:

    - Implementieren Sie die-Schnittstelle, um eine Paket Validierungs Regel zu erstellen <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> .

    - Zum Erstellen einer featurevalidierungsregel implementieren Sie die- <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> Schnittstelle.

4. Fügen Sie der- <xref:System.ComponentModel.Composition.ExportAttribute> Klasse hinzu. Mit diesem Attribut kann Visual Studio die Validierungs Regel ermitteln und laden. Übergeben Sie den- <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> oder- <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> Typ an den Attributkonstruktor.

## <a name="example"></a>Beispiel
 Im folgenden Codebeispiel wird veranschaulicht, wie eine benutzerdefinierte Funktions Validierungs Regel erstellt wird.

 [!code-vb[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/VisualBasic/featurevalidation/extension/customvalidationrule.vb#1)]
 [!code-csharp[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/CSharp/featurevalidation/extension/customfeaturevalidationrule.cs#1)]

## <a name="compile-the-code"></a>Kompilieren des Codes
 Dieses Beispiel erfordert Verweise auf die folgenden Assemblys:

- Microsoft. VisualStudio. SharePoint.

- System. ComponentModel. Composition.

## <a name="deploy-the-extension"></a>Bereitstellen der Erweiterung
 Zum Bereitstellen der Erweiterung erstellen [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] Sie ein Erweiterungspaket (VSIX) für die Assembly und alle anderen Dateien, die Sie mit der Erweiterung verteilen möchten. Weitere Informationen finden Sie unter Bereitstellen [von Erweiterungen für die SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Weitere Informationen
- [Erweiterte SharePoint-Paket Erstellung und-Bereitstellung](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
