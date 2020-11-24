---
title: Speichern von Daten in Erweiterungen des SharePoint-Projekt Systems | Microsoft-Dokumentation
titleSuffix: ''
description: Erfahren Sie, wie Sie die Zeichen folgen Daten speichern, die nach dem Schließen eines SharePoint-Projekts beibehalten werden, das eine Erweiterung enthält.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
helpviewer_keywords:
- SharePoint project items, saving string data
- project items [SharePoint development in Visual Studio], saving string data
- projects [SharePoint development in Visual Studio], saving string data
- SharePoint projects, saving string data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1e3c05b9ad570febcfc28fec367a8d180dd2b222
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440648"
---
# <a name="save-data-in-extensions-of-the-sharepoint-project-system"></a>Speichern von Daten in Erweiterungen des SharePoint-Projekt Systems
  Wenn Sie das SharePoint-Projekt System erweitern, können Sie Zeichen folgen Daten speichern, die nach dem Schließen eines SharePoint-Projekts beibehalten werden. Die Daten sind in der Regel mit einem bestimmten Projekt Element oder dem Projekt selbst verknüpft.

 Wenn Sie über Daten verfügen, die nicht persistent gespeichert werden müssen, können Sie die Daten zu jedem Objekt im SharePoint-Tools-Objektmodell hinzufügen, das die- <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> Schnittstelle implementiert. Weitere Informationen finden Sie unter [Zuordnen von benutzerdefinierten Daten zu Erweiterungen für SharePoint-Tools](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

## <a name="save-data-that-is-associated-with-a-project-item"></a>Speichern von Daten, die einem Projekt Element zugeordnet sind
 Wenn Sie über Daten verfügen, die einem bestimmten SharePoint-Projekt Element zugeordnet sind, z. b. den Wert einer Eigenschaft, die Sie einem Projekt Element hinzufügen, können Sie die Daten in der *spdata* -Datei für das Projekt Element speichern. Verwenden Sie hierzu die- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> Eigenschaft eines <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> Objekts. Daten, die Sie dieser Eigenschaft hinzufügen, werden im **ExtensionData** -Element in der *spdata* -Datei für das Projekt Element gespeichert. Weitere Informationen finden Sie unter [ExtensionData-Element](../sharepoint/extensiondata-element.md).

 Im folgenden Codebeispiel wird veranschaulicht, wie die- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> Eigenschaft verwendet wird, um den Wert einer Zeichen folgen Eigenschaft zu speichern, die in einem benutzerdefinierten SharePoint-Projekt Elementtyp definiert ist. Um dieses Beispiel im Kontext eines größeren Beispiels anzuzeigen, finden Sie weitere Informationen unter Gewusst [wie: Hinzufügen einer Eigenschaft zu einem benutzerdefinierten SharePoint-Projekt Elementtyp](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).

 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#14)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#14)]

## <a name="save-data-that-is-associated-with-a-project"></a>Speichern von Daten, die einem Projekt zugeordnet sind
 Wenn Sie über Daten auf Projektebene verfügen, z. b. den Wert einer Eigenschaft, die Sie SharePoint-Projekten hinzufügen, können Sie die Daten in der Projektdatei ( *csproj* -Datei oder *vbproj* -Datei) oder in der Projekt Benutzer Optionsdatei ( *csproj. User* -Datei oder *vbproj. User* -Datei) speichern. Die Datei, in der Sie die Daten speichern möchten, hängt davon ab, wie die Daten verwendet werden sollen:

- Wenn Sie möchten, dass die Daten für alle Entwickler verfügbar sind, die das SharePoint-Projekt öffnen, speichern Sie die Daten in der Projektdatei. Diese Datei ist immer in Quellcodeverwaltungs-Datenbanken eingecheckt, sodass die Daten in dieser Datei anderen Entwicklern zur Verfügung stehen, die das Projekt Auschecken.

- Wenn Sie möchten, dass die Daten nur für den aktuellen Entwickler verfügbar sind, in dem das SharePoint-Projekt in Visual Studio geöffnet ist, speichern Sie die Daten in der Projekt Benutzer Optionsdatei. Diese Datei wird in der Regel nicht in Quell Code Verwaltungs Datenbanken eingecheckt, sodass die Daten in dieser Datei anderen Entwicklern, die das Projekt Auschecken, nicht zur Verfügung stehen.

### <a name="save-data-to-the-project-file"></a>Speichern von Daten in der Projektdatei
 Konvertieren Sie ein <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> Objekt in ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> -Objekt, und verwenden Sie dann die-Methode, um Daten in der Projektdatei zu speichern <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> . Im folgenden Codebeispiel wird veranschaulicht, wie mit dieser Methode der Wert einer Projekt Eigenschaft in der Projektdatei gespeichert wird. Um dieses Beispiel im Kontext eines größeren Beispiels anzuzeigen, finden Sie weitere Informationen unter Gewusst [wie: Hinzufügen einer Eigenschaft zu SharePoint-Projekten](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

 [!code-vb[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#3)]
 [!code-csharp[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#3)]

 Weitere Informationen zum Konvertieren von <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> Objekten in andere Typen im Visual Studio-Automatisierungs Objektmodell oder im Integrations Objektmodell finden Sie unter [Konvertieren zwischen SharePoint-Projekt Systemtypen und anderen Visual Studio-Projekttypen](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).

### <a name="save-data-to-the-project-user-option-file"></a>Speichern von Daten in der Optionsdatei der Projekt Benutzer
 Verwenden Sie die-Eigenschaft eines-Objekts, um Daten in der Projekt Benutzer Optionsdatei zu speichern <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> . Im folgenden Codebeispiel wird veranschaulicht, wie diese Eigenschaft verwendet wird, um den Wert einer Projekt Eigenschaft in der Projekt Benutzer Optionsdatei zu speichern. Um dieses Beispiel im Kontext eines größeren Beispiels anzuzeigen, finden Sie weitere Informationen unter Gewusst [wie: Hinzufügen einer Eigenschaft zu SharePoint-Projekten](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

 [!code-vb[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#2)]
 [!code-csharp[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#2)]

## <a name="see-also"></a>Siehe auch
- [Erweitern des SharePoint-Projektsystems](../sharepoint/extending-the-sharepoint-project-system.md)
- [Zuordnen von benutzerdefinierten Daten zu SharePoint-Tools-Erweiterungen](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
- [Konvertieren zwischen SharePoint-Projekt Systemtypen und anderen Visual Studio-Projekttypen](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
