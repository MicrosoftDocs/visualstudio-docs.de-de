---
title: 'Gewusst wie: Hinzufügen einer Eigenschaft zu einer SharePoint-Projekt Element Erweiterung | Microsoft-Dokumentation'
titleSuffix: ''
description: Verwenden Sie eine SharePoint-Projekt Element Erweiterung zum Hinzufügen einer Eigenschaft zu einem SharePoint-Projekt Element, das bereits in Visual Studio installiert ist.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3d721c8d4f381e99a814852839de0e808d326b3a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889641"
---
# <a name="how-to-add-a-property-to-a-sharepoint-project-item-extension"></a>Gewusst wie: Hinzufügen einer Eigenschaft zu einer SharePoint-Projekt Element Erweiterung
  Sie können eine Projekt Element Erweiterung verwenden, um einem SharePoint-Projekt Element, das bereits in Visual Studio installiert ist, eine Eigenschaft hinzuzufügen. Die-Eigenschaft wird im **Eigenschaften** Fenster angezeigt, wenn das Projekt Element in **Projektmappen-Explorer** ausgewählt wird.

 Bei den folgenden Schritten wird davon ausgegangen, dass Sie bereits eine Projekt Element Erweiterung erstellt haben. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen einer SharePoint-Projekt Element Erweiterung](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

### <a name="to-add-a-property-to-a-project-item-extension"></a>So fügen Sie einer Projekt Element Erweiterung eine Eigenschaft hinzu

1. Definieren Sie eine Klasse mit einer öffentlichen Eigenschaft, die die Eigenschaft darstellt, die Sie einem Projekt Elementtyp hinzufügen. Wenn Sie einem Projekt Elementtyp mehrere Eigenschaften hinzufügen möchten, können Sie alle Eigenschaften in der gleichen Klasse oder in verschiedenen Klassen definieren.

2. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> Behandeln Sie das- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> Ereignis des *projectItemType* -Parameters in der-Methode Ihrer Implementierung.

3. Fügen Sie im Ereignishandler für das- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> Ereignis der-Auflistung <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> des Ereignis Argument-Parameters eine Instanz der Properties-Klasse hinzu.

## <a name="example"></a>Beispiel
 Im folgenden Codebeispiel wird veranschaulicht, wie dem Ereignis Empfänger-Projekt Element eine Eigenschaft mit dem Namen **example-Eigenschaft** hinzugefügt wird.

 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionproperty.cs#8)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionproperty.vb#8)]

### <a name="understand-the-code"></a>Grundlegendes zum Code
 Um sicherzustellen, dass bei `CustomProperties` jedem Auftreten des Ereignisses dieselbe Instanz der-Klasse verwendet wird, wird im <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> Codebeispiel das Properties-Objekt der- <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> Eigenschaft des Projekt Elements beim ersten Auftreten dieses Ereignisses hinzugefügt. Der Code ruft dieses Objekt ab, wenn dieses Ereignis erneut auftritt. Weitere Informationen zum Zuordnen von Daten zu Projekt Elementen mithilfe der- <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> Eigenschaft finden Sie unterzuordnen von [benutzerdefinierten Daten zu SharePoint-Tools-Erweiterungen](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

 Um Änderungen am Eigenschafts Wert beizubehalten, speichert der **Set** -Accessor für `ExampleProperty` den neuen Wert in der- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> Eigenschaft des-Objekts, dem die- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> Eigenschaft zugeordnet ist. Weitere Informationen zur Verwendung der- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> Eigenschaft zum Speichern von Daten mit Projekt Elementen finden Sie unter [Speichern von Daten in Erweiterungen des SharePoint-Projekt Systems](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

### <a name="specify-the-behavior-of-custom-properties"></a>Angeben des Verhaltens von benutzerdefinierten Eigenschaften
 Sie können definieren, wie eine benutzerdefinierte Eigenschaft im Fenster **Eigenschaften** angezeigt wird und sich verhält, indem Sie Attribute aus dem- <xref:System.ComponentModel> Namespace auf die Eigenschafts Definition anwenden. Die folgenden Attribute sind in vielen Szenarien nützlich:

- <xref:System.ComponentModel.DisplayNameAttribute>: Gibt den Namen der Eigenschaft an, die im **Eigenschaften** Fenster angezeigt wird.

- <xref:System.ComponentModel.DescriptionAttribute>: Gibt die Beschreibungs Zeichenfolge an, die im unteren Bereich des Fensters **Eigenschaften** angezeigt wird, wenn die-Eigenschaft ausgewählt wird.

- <xref:System.ComponentModel.DefaultValueAttribute>: Gibt den Standardwert der Eigenschaft an.

- <xref:System.ComponentModel.TypeConverterAttribute>: Gibt eine benutzerdefinierte Konvertierung zwischen der Zeichenfolge an, die im **Eigenschaften** Fenster angezeigt wird, und einem Eigenschafts Wert, der keine Zeichenfolge ist.

- <xref:System.ComponentModel.EditorAttribute>: Gibt einen benutzerdefinierten Editor an, der zum Ändern der Eigenschaft verwendet werden soll.

## <a name="compile-the-code"></a>Kompilieren des Codes
 Diese Beispiele erfordern ein Klassen Bibliotheksprojekt, das Verweise auf die folgenden Assemblys enthält:

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Bereitstellen der Erweiterung
 Zum Bereitstellen der Erweiterung erstellen [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] Sie ein Erweiterungspaket (VSIX) für die Assembly und alle anderen Dateien, die Sie mit der Erweiterung verteilen möchten. Weitere Informationen finden Sie unter Bereitstellen [von Erweiterungen für die SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Weitere Informationen
- [Vorgehensweise: Erstellen einer SharePoint-Projekt Element Erweiterung](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [Gewusst wie: Hinzufügen eines Kontextmenü Elements zu einer SharePoint-Projekt Element Erweiterung](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)
- [Erweitern von SharePoint-Projekt Elementen](../sharepoint/extending-sharepoint-project-items.md)
- [Exemplarische Vorgehensweise: Erweitern eines SharePoint-Projekt Elementtyps](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
