---
title: Hinzufügen einer Eigenschaft zu einem benutzerdefinierten SharePoint-Projekt Elementtyp
description: Fügen Sie einem benutzerdefinierten SharePoint-Projekt Elementtyp eine Eigenschaft hinzu. Die-Eigenschaft wird in der Eigenschaftenfenster angezeigt, wenn das Projekt Element in Projektmappen-Explorer ausgewählt wird.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b8f690b15f843af9337e16ee803509b72e85d7af
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889667"
---
# <a name="how-to-add-a-property-to-a-custom-sharepoint-project-item-type"></a>Gewusst wie: Hinzufügen einer Eigenschaft zu einem benutzerdefinierten SharePoint-Projekt Elementtyp
  Wenn Sie einen benutzerdefinierten SharePoint-Projekt Elementtyp definieren, können Sie dem Projekt Element eine Eigenschaft hinzufügen. Die-Eigenschaft wird im **Eigenschaften** Fenster angezeigt, wenn das Projekt Element in **Projektmappen-Explorer** ausgewählt wird.

 Bei den folgenden Schritten wird davon ausgegangen, dass Sie bereits einen eigenen SharePoint-Projekt Elementtyp definiert haben. Weitere Informationen finden Sie unter Gewusst [wie: Definieren eines SharePoint-Projekt Elementtyps](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

### <a name="to-add-a-property-to-a-definition-of-a-project-item-type"></a>So fügen Sie einer Definition eines Projekt Elementtyps eine Eigenschaft hinzu

1. Definieren Sie eine Klasse mit einer öffentlichen Eigenschaft, die die Eigenschaft darstellt, die Sie dem benutzerdefinierten Projekt Elementtyp hinzufügen. Wenn Sie einem benutzerdefinierten Projekt Elementtyp mehrere Eigenschaften hinzufügen möchten, können Sie alle Eigenschaften in der gleichen Klasse oder in verschiedenen Klassen definieren.

2. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> Behandeln Sie das- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> Ereignis des *projectItemTypeDefinition* -Parameters in der-Methode Ihrer Implementierung.

3. Fügen Sie im Ereignishandler für das- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> Ereignis der-Auflistung <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> des Ereignis Argument-Parameters eine Instanz Ihrer benutzerdefinierten Eigenschaften Klasse hinzu.

## <a name="example"></a>Beispiel
 Im folgenden Codebeispiel wird veranschaulicht, wie einem benutzerdefinierten Projekt Elementtyp eine Eigenschaft mit dem Namen **example-Eigenschaft** hinzugefügt wird.

 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#11)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#11)]

### <a name="understand-the-code"></a>Grundlegendes zum Code
 Um sicherzustellen, dass bei `CustomProperties` jedem Auftreten des Ereignisses dieselbe Instanz der-Klasse verwendet wird <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> , speichert das Codebeispiel das Properties-Objekt in der- <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> Eigenschaft des Projekt Elements, wenn dieses Ereignis das erste Mal auftritt. Der Code ruft dieses Objekt ab, wenn dieses Ereignis erneut auftritt. Weitere Informationen zur Verwendung der- <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> Eigenschaft zum Speichern von Daten mit Projekt Elementen finden Sie unter [Zuordnen von benutzerdefinierten Daten zu SharePoint-Tools-Erweiterungen](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

 Um Änderungen am Eigenschafts Wert beizubehalten, speichert der **Set** -Accessor für `ExampleProperty` den neuen Wert in der- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> Eigenschaft des-Objekts, dem die- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> Eigenschaft zugeordnet ist. Weitere Informationen zur Verwendung der- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> Eigenschaft zum Speichern von Daten mit Projekt Elementen finden Sie unter [Speichern von Daten in Erweiterungen des SharePoint-Projekt Systems](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

### <a name="specify-the-behavior-of-custom-properties"></a>Angeben des Verhaltens von benutzerdefinierten Eigenschaften
 Sie können definieren, wie eine benutzerdefinierte Eigenschaft im Fenster **Eigenschaften** angezeigt wird und sich verhält, indem Sie Attribute aus dem- <xref:System.ComponentModel> Namespace auf die Eigenschafts Definition anwenden. Die folgenden Attribute sind in vielen Szenarien nützlich:

- <xref:System.ComponentModel.DisplayNameAttribute>: Gibt den Namen der Eigenschaft an, die im **Eigenschaften** Fenster angezeigt wird.

- <xref:System.ComponentModel.DescriptionAttribute>: Gibt die Beschreibungs Zeichenfolge an, die im unteren Bereich des Fensters **Eigenschaften** angezeigt wird, wenn die-Eigenschaft ausgewählt wird.

- <xref:System.ComponentModel.DefaultValueAttribute>: Gibt den Standardwert der Eigenschaft an.

- <xref:System.ComponentModel.TypeConverterAttribute>: Gibt eine benutzerdefinierte Konvertierung zwischen der Zeichenfolge an, die im **Eigenschaften** Fenster angezeigt wird, und einem Eigenschafts Wert, der keine Zeichenfolge ist.

- <xref:System.ComponentModel.EditorAttribute>: Gibt einen benutzerdefinierten Editor an, der zum Ändern der Eigenschaft verwendet werden soll.

## <a name="compile-the-code"></a>Kompilieren des Codes
 Diese Codebeispiele erfordern ein Klassen Bibliotheksprojekt, das Verweise auf die folgenden Assemblys enthält:

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-project-item"></a>Bereitstellen des Projekt Elements
 Um anderen Entwicklern die Verwendung des Projekt Elements zu ermöglichen, erstellen Sie eine Projektvorlage oder eine Projekt Element Vorlage. Weitere Informationen finden Sie unter [Erstellen von Element Vorlagen und Projektvorlagen für SharePoint-Projekt Elemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Erstellen Sie zum Bereitstellen des Projekt Elements ein [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] Erweiterungspaket (VSIX) für die Assembly, die Vorlage und alle anderen Dateien, die Sie mit dem Projekt Element verteilen möchten. Weitere Informationen finden Sie unter Bereitstellen [von Erweiterungen für die SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Weitere Informationen
- [Gewusst wie: Definieren eines SharePoint-Projekt Elementtyps](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [Gewusst wie: Hinzufügen eines Kontextmenü Elements zu einem benutzerdefinierten SharePoint-Projekt Elementtyp](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
- [Definieren von benutzerdefinierten SharePoint-Projekt Elementtypen](../sharepoint/defining-custom-sharepoint-project-item-types.md)
