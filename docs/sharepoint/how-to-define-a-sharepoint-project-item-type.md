---
title: 'Vorgehensweise: Definieren eines SharePoint-Projekt Elementtyps | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie einen Projekt Elementtyp definieren, wenn Sie ein benutzerdefiniertes SharePoint-Projekt Element erstellen möchten.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 78b10e6878301a878de14306f92f425402e1cc17
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903610"
---
# <a name="how-to-define-a-sharepoint-project-item-type"></a>Gewusst wie: Definieren eines SharePoint-Projekt Elementtyps
  Definieren Sie einen Projekt Elementtyp, wenn Sie ein benutzerdefiniertes SharePoint-Projekt Element erstellen möchten. Weitere Informationen finden Sie unter [Definieren von benutzerdefinierten SharePoint-Projekt Elementtypen](../sharepoint/defining-custom-sharepoint-project-item-types.md).

### <a name="to-define-a-project-item-type"></a>So definieren Sie einen Projekt Elementtyp

1. Erstellen Sie ein Klassenbibliotheksprojekt.

2. Fügen Sie Verweise auf die folgenden Assemblys hinzu:

    - Microsoft.VisualStudio.SharePoint

    - System.ComponentModel.Composition

3. Erstellen Sie eine Klasse, die die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>-Schnittstelle implementiert.

4. Fügen Sie der-Klasse die folgenden Attribute hinzu:

    - <xref:System.ComponentModel.Composition.ExportAttribute>. Mit diesem Attribut kann Visual Studio Ihre Implementierung ermitteln und laden <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> . Übergeben <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> Sie den Typ an den Attributkonstruktor.

    - <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. In einer Projekt Elementtyp Definition gibt dieses Attribut den Zeichen folgen Bezeichner für das neue Projekt Element an. Es wird empfohlen, dass Sie das Format *Firmenname* verwenden. *Funktionsname* , um sicherzustellen, dass alle Projekt Elemente einen eindeutigen Namen aufweisen.

    - <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute>. Dieses Attribut gibt das Symbol an, das für dieses Projekt Element in **Projektmappen-Explorer** angezeigt wird. Dieses Attribut ist optional. Wenn Sie Sie nicht auf Ihre Klasse anwenden, zeigt Visual Studio ein Standard Symbol für das Projekt Element an. Wenn Sie dieses Attribut festlegen, übergeben Sie den voll qualifizierten Namen eines Symbols oder einer Bitmap, das in die Assembly eingebettet ist.

5. Verwenden Sie in ihrer Implementierung der- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> Methode Member des *projectItemTypeDefinition* -Parameters, um das Verhalten des Projekt Elementtyps zu definieren. Dieser Parameter ist ein <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> Objekt, das den Zugriff auf die in den <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> Schnittstellen und definierten Ereignisse ermöglicht <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> . Um auf eine bestimmte Instanz des Projekt Elementtyps zuzugreifen, behandeln Sie <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> Ereignisse wie <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> und <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized> .

## <a name="example"></a>Beispiel
 Im folgenden Codebeispiel wird veranschaulicht, wie ein einfacher Projekt Elementtyp definiert wird. Dieser Projekt Elementtyp schreibt eine Meldung in das **Ausgabe** Fenster und **Fehlerliste** Fenster, wenn ein Benutzer ein Projekt Element dieses Typs zu einem Projekt hinzufügt.

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemtype.vb#2)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemtype.cs#2)]

 In diesem Beispiel wird der SharePoint-Projekt Dienst verwendet, um die Nachricht in das **Ausgabe** Fenster und **Fehlerliste** Fenster zu schreiben. Weitere Informationen finden Sie unter [Verwenden des SharePoint-Projekt Dienstanbieter](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Kompilieren des Codes
 Dieses Beispiel erfordert Verweise auf die folgenden Assemblys:

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-project-item"></a>Bereitstellen des Projekt Elements
 Um anderen Entwicklern die Verwendung des Projekt Elements zu ermöglichen, erstellen Sie eine Projektvorlage oder eine Projekt Element Vorlage. Weitere Informationen finden Sie unter [Erstellen von Element Vorlagen und Projektvorlagen für SharePoint-Projekt Elemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Erstellen Sie zum Bereitstellen des Projekt Elements ein [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] Erweiterungspaket (VSIX) für die Assembly, die Vorlage und alle anderen Dateien, die Sie mit dem Projekt Element verteilen möchten. Weitere Informationen finden Sie unter Bereitstellen [von Erweiterungen für die SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Weitere Informationen
- [Definieren von benutzerdefinierten SharePoint-Projekt Elementtypen](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Erstellen von Element Vorlagen und Projektvorlagen für SharePoint-Projekt Elemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Aktionsprojekt Elements mit einer Element Vorlage, Teil 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Exemplarische Vorgehensweise: Erstellen eines Projekt Elements für eine Website Spalte mit einer Projektvorlage, Teil 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Gewusst wie: Hinzufügen einer Eigenschaft zu einem benutzerdefinierten SharePoint-Projekt Elementtyp](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [Gewusst wie: Hinzufügen eines Kontextmenü Elements zu einem benutzerdefinierten SharePoint-Projekt Elementtyp](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
