---
title: Verwenden des SharePoint-Projekt Dienstanbieter | Microsoft-Dokumentation
description: Verwenden Sie den SharePoint-Projekt Dienst zum Ausführen von Aufgaben im Zusammenhang mit dem Projekt System. Anzeigen einer Liste von Project Service-Funktionen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
- SharePoint development in Visual Studio, extensibility features
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5366be3ed60da9225eaf10b19f58ccd77bffbb90
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892189"
---
# <a name="use-the-sharepoint-project-service"></a>Verwenden des SharePoint-Projekt Dienstanbieter
  Das SharePoint-Projektsystem beinhaltet einen Projektdienst, den Sie verwenden können, um mit dem Projektsystem zusammenhängende Aufgaben auszuführen. Der Projektdienst ist ein <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>-Objekt.

 Sie können in jeder SharePoint-Tools-Erweiterung auf den SharePoint-Projektdienst zugreifen. Sie können auch in anderen Arten von Visual Studio-Erweiterungen, z. B. Add-Ins und VSPackages, auf ihn zugreifen. Weitere Informationen finden Sie unter Gewusst [wie: Abrufen des SharePoint-Projekt Dienstanbieter](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).

## <a name="project-service-features"></a>Project Service-Funktionen
 In der folgenden Tabelle sind die Aufgaben aufgelistet, die Sie mithilfe des SharePoint-Projektdiensts und der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>-Methode oder -Eigenschaft ausführen können, um die einzelnen Aufgaben auszuführen.

|Aufgabe|Zu verwendender Member|
|----------|-------------------|
|Zugriff auf beliebige SharePoint-Projekte, die in Visual Studio geöffnet sind.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Projects%2A>-Eigenschaft.|
|Zugriff auf alle verfügbaren SharePoint-Projektelementtypen (einschließlich integrierter und benutzerdefinierter Projektelementtypen).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ProjectItemTypes%2A>-Eigenschaft.|
|Zugriff auf alle die Bereitstellungsschritte, die für SharePoint-Projekte verfügbar sind (einschließlich integrierter und benutzerdefinierter Bereitstellungsschritte).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.DeploymentSteps%2A>-Eigenschaft.|
|Zugriff auf Ereignisse, die ausgelöst werden, wenn ein Entwickler Code in einem SharePoint-Projekt umgestaltet.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.CodeRefactoringEvents%2A>-Eigenschaft.|
|Führen Sie einen benutzerdefinierten *SharePoint-Befehl* aus, der das SharePoint-Server Objektmodell aufruft. Weitere Informationen zu SharePoint-Befehlen finden Sie unter " [Aufrufe in die SharePoint-Objekt Modelle](../sharepoint/calling-into-the-sharepoint-object-models.md)".|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A>-Eigenschaft.|
|Konvertieren eines Typs im SharePoint-Projektsystem in einen Typ im Visual Studio-Automatisierungsobjektmodell oder -Integrationsobjektmodell und umgekehrt. Weitere Informationen finden Sie unter [Konvertieren zwischen SharePoint-Projekt Systemtypen und anderen Visual Studio-Projekttypen](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> -Methode.|
|Schreiben von Nachrichten in das **Ausgabe** Fenster oder **Fehlerliste** Fenster in Visual Studio.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Logger%2A>-Eigenschaft.|
|Zugriff auf andere in Visual Studio verfügbare Dienste.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ServiceProvider%2A>-Eigenschaft.|
|Abrufen des Pfads zum Installationsordner der lokalen SharePoint-Website, der zum Debuggen der Projektmappe verwendet wird.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointInstallPath%2A>-Eigenschaft.|
|Bestimmt, ob [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] oder [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] auf dem Computer installiert ist.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.IsSharePointInstalled%2A>-Eigenschaft.|
|Überprüfen einer Funktion oder eines Pakets in einer SharePoint-Lösung.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.PackageValidationProvider%2A>-Eigenschaft.|

## <a name="see-also"></a>Weitere Informationen
- [Konvertieren zwischen SharePoint-Projekt Systemtypen und anderen Visual Studio-Projekttypen](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [Vorgehensweise: Abrufen des SharePoint-Projekt Dienstanbieter](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)
- [Erweitern der SharePoint-Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Übersicht über das Programmiermodell von Erweiterungen für SharePoint-Tools](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [Gewusst wie: Abrufen eines Diensts vom DTE-Objekt](/previous-versions/bb166401(v=vs.140))