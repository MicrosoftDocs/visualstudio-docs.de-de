---
title: 'Vorgehensweise: Erstellen einer SharePoint-Projekt Element Erweiterung | Microsoft-Dokumentation'
description: Weitere Informationen zum Erstellen einer Projekt Element Erweiterung finden Sie unter Hinzufügen von Funktionen zu einem SharePoint-Projekt Element, das bereits in Visual Studio installiert ist.
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
ms.openlocfilehash: 0f55eb3ba06f2541bf1f4777c24927993444c6b1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873605"
---
# <a name="how-to-create-a-sharepoint-project-item-extension"></a>Vorgehensweise: Erstellen einer SharePoint-Projekt Element Erweiterung
  Erstellen Sie eine Projekt Element Erweiterung, wenn Sie einem SharePoint-Projekt Element, das bereits in Visual Studio installiert ist, Funktionen hinzufügen möchten. Weitere Informationen finden Sie unter [Erweitern von SharePoint-Projekt Elementen](../sharepoint/extending-sharepoint-project-items.md).

### <a name="to-create-a-project-item-extension"></a>So erstellen Sie eine Projekt Element Erweiterung

1. Erstellen Sie ein Klassenbibliotheksprojekt.

2. Fügen Sie Verweise auf die folgenden Assemblys hinzu:

    - Microsoft.VisualStudio.SharePoint

    - System.ComponentModel.Composition

3. Erstellen Sie eine Klasse, die die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>-Schnittstelle implementiert.

4. Fügen Sie der-Klasse die folgenden Attribute hinzu:

    - <xref:System.ComponentModel.Composition.ExportAttribute>. Mit diesem Attribut kann Visual Studio Ihre Implementierung ermitteln und laden <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> . Übergeben <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> Sie den Typ an den Attributkonstruktor.

    - <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. In einer Projekt Element Erweiterung identifiziert dieses Attribut das Projekt Element, das Sie erweitern möchten. Übergeben Sie die ID des Projekt Elements an den Attributkonstruktor. Eine Liste der IDs der Projekt Elemente, die in Visual Studio enthalten sind, finden Sie unter [Erweitern von SharePoint-Projekt Elementen](../sharepoint/extending-sharepoint-project-items.md).

5. Verwenden Sie in ihrer Implementierung der- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> Methode Member des *projectItemType* -Parameters, um das Verhalten der Erweiterung zu definieren. Dieser Parameter ist ein <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> Objekt, das den Zugriff auf die in den <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> Schnittstellen und definierten Ereignisse ermöglicht <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> . Um auf eine bestimmte Instanz des Projekt Elementtyps zuzugreifen, den Sie erweitern, behandeln Sie <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> Ereignisse wie z <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> . b <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized> . und.

## <a name="example"></a>Beispiel
 Im folgenden Codebeispiel wird veranschaulicht, wie eine einfache Erweiterung für das Ereignis Empfänger-Projekt Element erstellt wird. Jedes Mal, wenn der Benutzer ein Ereignis Empfänger-Projekt Element einem SharePoint-Projekt hinzufügt, schreibt diese Erweiterung eine Meldung in das **Ausgabe** Fenster und **Fehlerliste** Fenster.

 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemextension.cs#1)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemextension.vb#1)]

 In diesem Beispiel wird der SharePoint-Projekt Dienst verwendet, um die Nachricht in das **Ausgabe** Fenster und **Fehlerliste** Fenster zu schreiben. Weitere Informationen finden Sie unter [Verwenden des SharePoint-Projekt Dienstanbieter](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Kompilieren des Codes
 Dieses Beispiel erfordert Verweise auf die folgenden Assemblys:

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Bereitstellen der Erweiterung
 Zum Bereitstellen der Erweiterung erstellen [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] Sie ein Erweiterungspaket (VSIX) für die Assembly und alle anderen Dateien, die Sie mit der Erweiterung verteilen möchten. Weitere Informationen finden Sie unter Bereitstellen [von Erweiterungen für die SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Weitere Informationen
- [Erweitern von SharePoint-Projekt Elementen](../sharepoint/extending-sharepoint-project-items.md)
- [Exemplarische Vorgehensweise: Erweitern eines SharePoint-Projekt Elementtyps](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
