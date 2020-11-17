---
title: Erweitern der SharePoint-Paket Erstellung und-Bereitstellung | Microsoft-Dokumentation
description: Erweitern der SharePoint-Paket Erstellung und-Bereitstellung. Erstellen Sie Bereitstellungs Schritte und-Konfigurationen. Behandeln von Bereitstellungs Konflikten. Anpassen von Validierungsregeln.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9f0f9eb6c863a961a527fcb6fb330a2a4f88669e
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672586"
---
# <a name="extend-sharepoint-packaging-and-deployment"></a>Erweiterte SharePoint-Paket Erstellung und-Bereitstellung
  Sie können den Paketerstellungs- und Bereitstellungsprozess für SharePoint-Projekte erweitern.

## <a name="create-deployment-steps"></a>Erstellen von Bereitstellungs Schritten
 Wenn Sie ein SharePoint-Projekt bereitstellen, führt [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] eine Reihe von Schritten zur Bereitstellung aus. Visual Studio umfasst integrierte Bereitstellungsschritte für viele Aufgaben wie das Zurückziehen und Hinzufügen von Projektmappen. Sie können jedoch auch eigene Bereitstellungsschritte erstellen.

 Eine exemplarische Vorgehensweise, die die Erstellung eines Bereitstellungs Schritts veranschaulicht, finden Sie unter Exemplarische Vorgehensweise [: Erstellen eines benutzerdefinierten Bereitstellungs Schritts für SharePoint-Projekte](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="create-deployment-configurations"></a>Erstellen von Bereitstellungs Konfigurationen
 Bei einer Bereitstellungskonfiguration handelt es sich um eine Reihe von Bereitstellungsschritten. Sie werden für ein angegebenes Projekt ausgeführt, können sich aber auf alle SharePoint-Projektelemente auswirken. Jede Bereitstellungskonfiguration umfasst einen Satz an Schritten, der beim Bereitstellen des Projekts ausgeführt wird, und einen anderen Satz, der ausgeführt wird, wenn das Projekt zurückgezogen wird. [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] enthält zwei integrierte Bereitstellungs Konfigurationen, aber Sie können auch eigene bereit Stellungen erstellen. Beim Erstellen einer Bereitstellungskonfiguration können Sie integrierte und von Ihnen erstellte Bereitstellungsschritte einbeziehen.

 Eine exemplarische Vorgehensweise, die das Erstellen einer Bereitstellungs Konfiguration veranschaulicht, finden Sie unter Exemplarische Vorgehensweise [: Erstellen eines benutzerdefinierten Bereitstellungs Schritts für SharePoint-Projekte](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="run-code-when-a-sharepoint-solution-is-deployed-or-retracted"></a>Ausführen von Code beim Bereitstellen oder zurückziehen einer SharePoint-Lösung
 Sie können Ereignisse verarbeiten, um zusätzliche Aufgaben auszuführen, wenn eine SharePoint-Lösung bereitgestellt oder zurückgezogen wird. Visual Studio löst Ereignisse aus, die Sie in den folgenden Szenarien behandeln können:

- Vor und nach der Ausführung jedes Bereitstellungsschritts für ein SharePoint-Projektelement. Weitere Informationen finden Sie unter Gewusst [wie: Ausführen von Code bei der Ausführung von Bereitstellungs Schritten](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md).

- Vor und nach der Bereitstellung oder Zurückziehung eines SharePoint-Projekts. Weitere Informationen finden Sie unter Gewusst [wie: Ausführen von Code beim Bereitstellen oder zurückziehen eines SharePoint-Projekts](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md).

## <a name="handle-deployment-conflicts"></a>Behandeln von Bereitstellungs Konflikten
 Einige SharePoint-Projektelementtypen, einschließlich Module, Webparts, Listeninstanzen und Inhaltstypen, bieten eine integrierte Bereitstellungskonfliktlösung. Beim Bereitstellen einer Lösung, die eins dieser Projektelemente enthält, prüft Visual Studio zunächst, ob eine Datei bereits auf der SharePoint-Website mit demselben Namen, der URL oder ID wie die Datei im Element vorhanden ist, die Sie bereitstellen. Wenn ein Konflikt vorhanden ist, kann Visual Studio den Konflikt automatisch lösen, alternativ kann es Sie auffordern zu bestimmen, ob Visual Studio den Konflikt beheben oder ob die Bereitstellung abgebrochen werden soll. Weitere Informationen finden Sie unter [Troubleshooting SharePoint Packaging and Deployment](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).

 Sie können diese Funktion erweitern, indem Sie Ihren eigenen Code bereitstellen, der nach Bereitstellungskonflikten sucht und diese behebt. Weitere Informationen finden Sie unter Vorgehens [Weise: Behandeln von Bereitstellungs Konflikten](../sharepoint/how-to-handle-deployment-conflicts.md).

## <a name="run-command-line-operations-before-or-after-a-project-is-deployed"></a>Ausführen von Befehlszeilen Vorgängen vor oder nach der Bereitstellung eines Projekts
 Wenn Sie beim Bereitstellen einer SharePoint-Lösung einen Befehlszeilenvorgang ausführen möchten, können Sie die Eigenschaften <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PreDeploymentCommand%2A> und <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PostDeploymentCommand%2A> eines <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>-Objekts festlegen. Visual Studio führt diese Befehle vor und nach der Bereitstellung des Projekts aus.

 In einigen Fällen werden möglicherweise Bereitstellungskonflikte angezeigt. Es gibt mehrere Möglichkeiten, Konflikte zu lösen. Weitere Informationen finden Sie unter Problembehandlung bei der [SharePoint-Paket Erstellung und-Bereitstellung](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).

## <a name="customize-validation-rules"></a>Anpassen von Validierungsregeln
 Vor dem Bereitstellen eines Lösungspakets (.wsp) können Sie benutzerdefinierte Funktions- und Paketvalidierungsregeln erstellen, um sicherzustellen, dass die Funktion oder das Paket gültig ist. Beispielsweise können Sie Entwicklern Informationen, Warnungen oder Fehler melden, um sie beim Beheben von Validierungsproblemen zu unterstützen. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von benutzerdefinierten Feature- und Paketvalidierungsregeln für SharePoint-Lösungen](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).

## <a name="see-also"></a>Siehe auch
- [Gewusst wie: Ausführen von Code bei der Ausführung von Bereitstellungs Schritten](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
- [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Bereitstellungs Schritts für SharePoint-Projekte](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)
- [Vorgehensweise: Erstellen von benutzerdefinierten Funktions-und Paket Validierungsregeln für SharePoint-Lösungen](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)
- [Erweitern des SharePoint-Projektsystems](../sharepoint/extending-the-sharepoint-project-system.md)
