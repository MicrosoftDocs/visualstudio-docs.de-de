---
title: 'Gewusst wie: Hinzufügen einer Eigenschaft zu SharePoint-Projekten | Microsoft-Dokumentation'
description: Verwenden Sie eine Projekt Erweiterung zum Hinzufügen einer Eigenschaft zu einem SharePoint-Projekt. Eine Eigenschaft wird in der Eigenschaftenfenster angezeigt, wenn Sie das Projekt in Projektmappen-Explorer auswählen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 62766b704d140805a3b76dbc3c00acaf6257f5e5
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850155"
---
# <a name="how-to-add-a-property-to-sharepoint-projects"></a>Gewusst wie: Hinzufügen einer Eigenschaft zu SharePoint-Projekten
  Sie können eine Projekt Erweiterung verwenden, um einem SharePoint-Projekt eine Eigenschaft hinzuzufügen. Die-Eigenschaft wird im **Eigenschaften** Fenster angezeigt, wenn das Projekt in **Projektmappen-Explorer** ausgewählt wird.

 Bei den folgenden Schritten wird davon ausgegangen, dass Sie bereits eine Projekt Erweiterung erstellt haben. Weitere Informationen finden Sie unter Vorgehens [Weise: Erstellen einer SharePoint-Projekt Erweiterung](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

### <a name="to-add-a-property-to-a-sharepoint-project"></a>So fügen Sie einem SharePoint-Projekt eine Eigenschaft hinzu

1. Definieren Sie eine Klasse mit einer öffentlichen Eigenschaft, die die Eigenschaft darstellt, die Sie SharePoint-Projekten hinzufügen. Wenn Sie mehrere Eigenschaften hinzufügen möchten, können Sie alle Eigenschaften in der gleichen Klasse oder in verschiedenen Klassen definieren.

2. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> Behandeln Sie das- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> Ereignis des *ProjectService* -Parameters in der-Methode Ihrer Implementierung.

3. Fügen Sie im Ereignishandler für das- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> Ereignis der-Auflistung <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A> des Ereignis Argument-Parameters eine Instanz der Properties-Klasse hinzu.

## <a name="example"></a>Beispiel
 Im folgenden Codebeispiel wird veranschaulicht, wie SharePoint-Projekten zwei Eigenschaften hinzugefügt werden. Eine Eigenschaft speichert Ihre Daten in der Projekt Benutzer Optionsdatei (die Datei " *. csproj. User* " oder " *. vbproj. User* "). Die andere Eigenschaft speichert Ihre Daten in der Projektdatei (*csproj* -Datei oder *vbproj* -Datei).

 [!code-vb[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#1)]
 [!code-csharp[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#1)]

### <a name="understand-the-code"></a>Grundlegendes zum Code
 Um sicherzustellen, dass bei `CustomProjectProperties` jedem Auftreten des Ereignisses dieselbe Instanz der-Klasse verwendet wird, wird im <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> Codebeispiel das Properties-Objekt der-Eigenschaft des Projekts hinzugefügt, wenn <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> Dieses Ereignis das erste Mal auftritt. Der Code ruft dieses Objekt ab, wenn dieses Ereignis erneut auftritt. Weitere Informationen zum Zuordnen von Daten zu Projekten mithilfe der- <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> Eigenschaft finden Sie unter [Zuordnen von benutzerdefinierten Daten zu SharePoint-Tools-Erweiterungen](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

 Um Änderungen an den Eigenschafts Werten beizubehalten, verwenden die **Set** -Accessoren für die Eigenschaften die folgenden APIs:

- `CustomUserFileProperty` verwendet die- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> Eigenschaft, um den Wert in der Projekt Benutzer Optionsdatei zu speichern.

- `CustomProjectFileProperty` verwendet die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> Methode, um den Wert in der Projektdatei zu speichern.

  Weitere Informationen zum Beibehalten von Daten in diesen Dateien finden Sie unter [Speichern von Daten in Erweiterungen des SharePoint-Projekt Systems](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

### <a name="specify-the-behavior-of-custom-properties"></a>Angeben des Verhaltens von benutzerdefinierten Eigenschaften
 Sie können definieren, wie eine benutzerdefinierte Eigenschaft im Fenster **Eigenschaften** angezeigt wird und sich verhält, indem Sie Attribute aus dem- <xref:System.ComponentModel> Namespace auf die Eigenschafts Definition anwenden. Die folgenden Attribute sind in vielen Szenarien nützlich:

- <xref:System.ComponentModel.DisplayNameAttribute>: Gibt den Namen der Eigenschaft an, die im **Eigenschaften** Fenster angezeigt wird.

- <xref:System.ComponentModel.DescriptionAttribute>: Gibt die Beschreibungs Zeichenfolge an, die im unteren Bereich des Fensters **Eigenschaften** angezeigt wird, wenn die-Eigenschaft ausgewählt wird.

- <xref:System.ComponentModel.DefaultValueAttribute>: Gibt den Standardwert der Eigenschaft an.

- <xref:System.ComponentModel.TypeConverterAttribute>: Gibt eine benutzerdefinierte Konvertierung zwischen der Zeichenfolge an, die im **Eigenschaften** Fenster angezeigt wird, und einem Eigenschafts Wert, der keine Zeichenfolge ist.

- <xref:System.ComponentModel.EditorAttribute>: Gibt einen benutzerdefinierten Editor an, der zum Ändern der Eigenschaft verwendet werden soll.

## <a name="compile-the-code"></a>Kompilieren des Codes
 Dieses Beispiel erfordert Verweise auf die folgenden Assemblys:

- Microsoft.VisualStudio.SharePoint

- Microsoft. VisualStudio. Shell

- Microsoft. VisualStudio. Shell. Interop

- Microsoft. VisualStudio. Shell. Interop. 8.0

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Bereitstellen der Erweiterung
 Zum Bereitstellen der Erweiterung erstellen [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] Sie ein Erweiterungspaket (VSIX) für die Assembly und alle anderen Dateien, die Sie mit der Erweiterung verteilen möchten. Weitere Informationen finden Sie unter Bereitstellen [von Erweiterungen für die SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Siehe auch
- [Erweitern von SharePoint-Projekten](../sharepoint/extending-sharepoint-projects.md)
- [Vorgehensweise: Erstellen einer SharePoint-Projekt Erweiterung](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [Gewusst wie: Hinzufügen eines Kontextmenü Elements zu SharePoint-Projekten](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)
- [Erweitern des SharePoint-Projektsystems](../sharepoint/extending-the-sharepoint-project-system.md)
