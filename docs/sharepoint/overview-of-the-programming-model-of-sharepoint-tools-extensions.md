---
title: Übersicht über das Programmiermodell von Erweiterungen für SharePoint-Tools
titleSuffix: ''
description: Lesen Sie eine Übersicht über das Programmiermodell von Erweiterungen für SharePoint-Tools. Implementieren von Erweiterbarkeits Schnittstellen. Verstehen Sie die Objekt Modelle.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- SharePoint development in Visual Studio, extensibility object models
- SharePoint development in Visual Studio, extending tools
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b823aecff4f05208094bd98b559a661c7f23fc5b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970529"
---
# <a name="overview-of-the-programming-model-of-sharepoint-tools-extensions"></a>Übersicht über das Programmiermodell von Erweiterungen für SharePoint-Tools
  Wenn Sie eine Erweiterung für die SharePoint-Tools in Visual Studio erstellen, beginnen Sie damit, indem Sie eine oder mehrere Erweiterungsschnittstellen implementieren, die von den SharePoint-Tools verfügbar gemacht werden. In den meisten Fällen verwenden Sie auch andere von den SharePoint-Tools bereitgestellte Typen, um Funktionen in der Erweiterung zu implementieren. Für einige Szenarien können Sie auch Typen in anderen Objektmodellen verwenden, die von Visual Studio und SharePoint bereitgestellt werden. Sie müssen den Zweck der einzelnen Objektmodelle verstehen und wissen, wie Sie diese miteinander kombinieren können, um Erweiterungen für die SharePoint-Tools zu erstellen.

## <a name="extend-the-sharepoint-tools-by-implementing-extensibility-interfaces"></a>Erweitern der SharePoint-Tools durch Implementieren von Erweiterbarkeits Schnittstellen
 Visual Studio verwendet das Managed Extensibility Framework (MEF) in .NET Framework 4 zum Bereitstellen des Erweiterungsmodells für die SharePoint-Tools. MEF ist eine API (implementiert in der System.ComponentModel.Compositions-Assembly), die Anwendungen ermöglicht, Erweiterungspunkte verfügbar zu machen und Erweiterungen zur Laufzeit zu ermitteln und zu laden. Weitere Informationen zu MEF finden Sie unter [Managed Extensibility Framework &#40;MEF&#41;](/dotnet/framework/mef/index).

 Um die SharePoint-Tools zu erweitern, implementieren Sie eine oder mehrere Erweiterungsschnittstellen, die von Visual Studio bereitgestellt werden. Sie müssen auch das <xref:System.ComponentModel.Composition.ExportAttribute> sowie bei Bedarf weitere für die SharePoint-Tools spezifische Attribute auf Ihre Schnittstellenimplementierung anwenden. In der folgenden Tabelle sind die Schnittstellen aufgeführt, die Sie zum Erweitern der SharePoint-Tools implementieren können.

|Schnittstelle|BESCHREIBUNG|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>|Implementieren Sie diese Schnittstelle, um einen neuen Typ von SharePoint-Projektelement zu definieren. Ein Beispiel finden Sie unter Gewusst [wie: Definieren eines SharePoint-Projekt Elementtyps](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>|Implementieren Sie diese Schnittstelle, um einen SharePoint-Projektelementtyp zu erweitern, der in Visual Studio bereits installiert ist. Ein Beispiel finden Sie unter Gewusst [wie: Erstellen einer SharePoint-Projekt Element Erweiterung](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>|Implementieren Sie diese Schnittstelle, um SharePoint-Projekte zu erweitern. Ein Beispiel finden Sie unter Gewusst [wie: Erstellen einer SharePoint-Projekt Erweiterung](../sharepoint/how-to-create-a-sharepoint-project-extension.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>|Implementieren Sie diese Schnittstelle, um einen neuen Bereitstellungsschritt zu definieren, der beim Bereitstellen oder Zurückziehen eines SharePoint-Projektelements ausgeführt werden kann. Ein Beispiel finden Sie unter Exemplarische Vorgehensweise [: Erstellen eines benutzerdefinierten Bereitstellungs Schritts für SharePoint-Projekte](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>|Implementieren Sie diese Schnittstelle, um einen vorhandenen Knoten unter dem Knoten **SharePoint-Verbindungen** im Fenster **Server-Explorer** zu erweitern. Ein Beispiel finden Sie unter Gewusst [wie: Erweitern eines SharePoint-Knotens in Server-Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>|Implementieren Sie diese Schnittstelle, um unter dem Knoten **SharePoint-Verbindungen** im Fenster **Server-Explorer** einen neuen Knotentyp zu definieren. Ein Beispiel finden Sie unter Gewusst [wie: Erweitern eines SharePoint-Knotens in Server-Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>|Implementieren Sie diese Schnittstelle, um eine benutzerdefinierte Funktionsvalidierungsregel zu definieren. Ein Beispiel finden Sie unter Gewusst [wie: Erstellen von benutzerdefinierten Funktions-und Paket Validierungsregeln für SharePoint-Lösungen](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>|Implementieren Sie diese Schnittstelle, um eine benutzerdefinierte Paketvalidierungsregel zu definieren. Ein Beispiel finden Sie unter Gewusst [wie: Erstellen von benutzerdefinierten Funktions-und Paket Validierungsregeln für SharePoint-Lösungen](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|

 Nachdem Sie eine Erweiterung der SharePoint-Tools implementiert haben, müssen Sie die Erweiterungsassembly in einem Visual Studio-Erweiterungspaket (VSIX) bereitstellen, damit Visual Studio die Erweiterung ermitteln und laden kann. Weitere Informationen finden Sie unter Bereitstellen [von Erweiterungen für die SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="understand-the-object-models-that-you-use-in-sharepoint-tools-extensions"></a>Informationen zu den Objekt Modellen, die Sie in Erweiterungen für SharePoint-Tools verwenden
 Es gibt verschiedene Objektmodelle, die Sie beim Erstellen von Erweiterungen für die SharePoint-Tools verwenden können:

- *Objektmodell für SharePoint-Tools*. Dieses Objektmodell stellt die Erweiterungsschnittstellen bereit, die Sie zum Erstellen von SharePoint-Tools-Erweiterungen und anderen verwandten Typen implementieren.

- *Automatisierungs-und Integrations Objekt Modelle von Visual Studio*. Verwenden Sie diesen Objektmodelle, um auf Visual Studio-Funktionen zuzugreifen, die nicht im Bereich des Objektmodells der SharePoint-Tools liegen.

    > [!NOTE]
    > Mit dem SharePoint-Projektdienst können Sie einige Objekte des SharePoint-Tools-Objektmodells in Automatisierungs- und Integratonsobjektmodelle von Visual Studio konvertieren und umgekehrt. Weitere Informationen finden Sie unter [Konvertieren zwischen SharePoint-Projekt Systemtypen und anderen Visual Studio-Projekttypen](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).

- *SharePoint-Server-und-Client-Objekt Modelle*. Mit diesen Objektmodellen können Sie eine SharePoint-Website ändern oder Daten aus einer SharePoint-Website im Kontext einer SharePoint-Tools-Erweiterung abrufen.

### <a name="sharepoint-tools-object-model"></a>Objektmodell für SharePoint-Tools
 In jeder SharePoint-Tools-Erweiterung werden mit Typen im SharePoint-Tools-Objektmodell das Kernverhalten und die Kernfunktionen der Erweiterung definiert. In den folgenden Tabellen werden die Namespaces, die in diesem Objektmodell enthalten sind, von der Assembly beschrieben, in der Sie enthalten sind.

#### <a name="microsoftvisualstudiosharepointdll"></a>Microsoft.VisualStudio.SharePoint.dll

|Namespace|BESCHREIBUNG|
|-|-|
|<xref:Microsoft.VisualStudio.SharePoint>|Enthält Typen, mit denen Sie das SharePoint-Projektsystem erweitern und automatisieren können. Sie können z. B. die integrierten SharePoint-Projekte und -Projektelemente erweitern, oder Sie können eigene Projektelemente erstellen. Weitere Informationen finden Sie unter [Erweitern des SharePoint-Projektsystems](../sharepoint/extending-the-sharepoint-project-system.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Deployment>|Enthält Typen, mit denen Sie den Bereitstellungsprozess für SharePoint-Projekte erweitern können, beispielsweise durch Erstellen eigener Bereitstellungsschritte und Bereitstellungskonfigurationen. Weitere Informationen finden Sie unter [Erweitern der SharePoint-Paket Erstellung und-Bereitstellung](../sharepoint/extending-sharepoint-packaging-and-deployment.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Explorer>|Enthält Typen, die Sie verwenden, um Knoten unter dem Knoten **SharePoint-Verbindungen** im Fenster **Server-Explorer** zu erweitern oder um neue Knoten Typen zu definieren. Weitere Informationen finden Sie unter [Erweitern des SharePoint-Verbindungsknotens im Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Features>|Enthält Typen, mit denen Sie in einem SharePoint-Projekt auf die Definition von Funktionen zugreifen können.|
|<xref:Microsoft.VisualStudio.SharePoint.Packages>|Enthält Typen, mit denen Sie auf die Paketdefinition in einer SharePoint-Lösung zugreifen können.|
|<xref:Microsoft.VisualStudio.SharePoint.Validation>|Enthält Typen, mit denen Sie das Funktions- und Paketvalidierungsverhalten für SharePoint-Projekte anpassen können. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von benutzerdefinierten Feature- und Paketvalidierungsregeln für SharePoint-Lösungen](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|

#### <a name="microsoftvisualstudiosharepointcommandsdll"></a>Microsoft.VisualStudio.SharePoint.Commands.dll

|Namespace|BESCHREIBUNG|
|-|-|
|<xref:Microsoft.VisualStudio.SharePoint.Commands>|Enthält Typen, die Sie zum Erstellen von benutzerdefinierten *SharePoint-Befehlen* verwenden können. Ein SharePoint-Befehl ist eine Methode, die einen Aufruf in das SharePoint-Serverobjektmodell von einer SharePoint-Tools-Erweiterung aus durchführt. Weitere Informationen finden Sie unter " [Aufrufe in die SharePoint-Objekt Modelle](../sharepoint/calling-into-the-sharepoint-object-models.md)".|

#### <a name="microsoftvisualstudiosharepointexplorerextensionsdll"></a>Microsoft.VisualStudio.SharePoint.Explorer.Extensions.dll

|Namespace|BESCHREIBUNG|
|-|-|
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions>|Enthält Typen, die Sie verwenden können, um Informationen über integrierte **Server-Explorer** Knoten zu erhalten, die einzelne Komponenten auf einer SharePoint-Website darstellen, z. b. einen Knoten, der eine Liste, ein Feld oder einen Inhaltstyp darstellt. Weitere Informationen finden Sie unter [Erweitern des SharePoint-Verbindungsknotens im Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).|

### <a name="visual-studio-automation-object-model"></a>Visual Studio-Automatisierungs Objektmodell
 Das Automatisierungsobjektmodell von Visual Studio stellt APIs bereit, mit denen Sie Visual Studio-Projekte und die IDE automatisieren können. Führen Sie projektbezogene Aufgaben, die nicht spezifisch für SharePoint-Projekte sind, oder andere allgemeine Automatisierungsaufgaben in Visual Studio mit diesem Visual Studio-Objektmodell aus. Dieses Objektmodell wird in der Regel häufig in Visual Studio-Add-Ins und -Makros verwendet, Sie können es aber auch in SharePoint-Tools-Erweiterungen verwenden.

 Der Hauptteil des Visual Studio-Automatisierungs Objektmodells ist in der *EnvDTE.dll* -Assembly definiert. Die Assemblys " *svdte \\ \<version> . dll* " bieten zusätzliche Funktionen, die in bestimmten Versionen von Visual Studio eingeführt wurden. Diese Assemblys sind in Visual Studio enthalten.

 Weitere Informationen zum Automatisierungs Objektmodell finden Sie unter [Visual Studio SDK-Referenz](../extensibility/visual-studio-sdk-reference.md).

### <a name="visual-studio-integration-object-model"></a>Visual Studio-Integrations Objektmodell
 Das Integrations Objektmodell stellt APIs bereit, mit denen Sie Visual Studio Funktionen hinzufügen können, indem Sie ein *VSPackage* erstellen. Ein VSPackage ist ein Modul, das die Visual Studio-IDE durch benutzerdefinierte Funktionen wie Toolfenster, Editoren, Designer, Dienste und Projekte erweitert.

 Sie können das Integrationsobjektmodell verwenden, wenn Sie eine neue Visual Studio-Funktion hinzufügen möchten, die zusammen mit den integrierten SharePoint-Tools verwendet wird. Wenn Sie z. B. ein benutzerdefiniertes SharePoint-Projektelement erstellen, das eine benutzerdefinierte Aktion für eine SharePoint-Website darstellt, können Sie auch ein VSPackage erstellen, das einen Designer für die benutzerdefinierte Aktion implementiert. Sie können den Designer der benutzerdefinierten Aktion zuordnen, indem Sie dem Projekt Element, das die benutzerdefinierte Aktion in **Projektmappen-Explorer** darstellt, ein Kontextmenü Element hinzufügen. Sie können den Designer öffnen, indem **Sie das Kontext** Menü öffnen (Klicken Sie dazu mit der rechten Maustaste auf das Projekt Element "benutzerdefinierte Aktion", oder wählen Sie es aus, und wählen Sie dann die Tastenkombination + **F10** ) und dann **Öffnen** aus.

 Dieses Objektmodell ist in einem Satz mehrerer Assemblys definiert, die im Visual Studio-SDK enthalten sind. Einige der Hauptassemblys in diesem Objektmodell umfassen *Microsoft.VisualStudio.Shell.11.0.dll*, *Microsoft.VisualStudio.Shell.Interop.dll* und *Microsoft.VisualStudio.OLE.Interop.dll*.

 Weitere Informationen zum Integrations Objektmodell finden Sie unter Übersicht über das [Automatisierungs Modell](../extensibility/internals/automation-model-overview.md) und [Visual Studio SDK-Referenz](../extensibility/visual-studio-sdk-reference.md).

### <a name="sharepoint-object-models"></a>SharePoint-Objekt Modelle
 SharePoint-Tools-Erweiterungen können SharePoint-APIs verwenden, um eine SharePoint-Website zu ändern oder Daten von einer SharePoint-Website abzurufen. [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] und [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] stellen zwei unterschiedliche Objektmodelle bereit: ein Serverobjektmodell und ein Clientobjektmodell.

 Sie können APIs aus beiden Objektmodellen in einer SharePoint-Tools-Erweiterung verwenden. Beide Objektmodelle haben jedoch bestimmte Vor- und Nachteile im Kontext der SharePoint-Tools-Erweiterungen. Weitere Informationen finden Sie unter " [Aufrufe in die SharePoint-Objekt Modelle](../sharepoint/calling-into-the-sharepoint-object-models.md)".

|Objektmodell|BESCHREIBUNG|
|------------------|-----------------|
|Serverobjektmodell|Das Serverobjektmodell bietet Zugriff auf alle Funktionen, die [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] und [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] programmgesteuert verfügbar machen. Dieses Objektmodell wurde für SharePoint-Lösungen entworfen, die auf dem SharePoint-Server ausgeführt werden. Der Großteil dieses Objektmodells wird in der *Microsoft.SharePoint.dll* -Assembly definiert. Weitere Informationen zum Server Objektmodell finden [Sie unter Verwenden des SharePoint Foundation Server-Side-Objektmodells](/previous-versions/office/developer/sharepoint-2010/ee538251(v=office.14)).|
|Clientobjektmodell|Das Clientobjektmodell ist eine Teilmenge des Serverobjektmodells und kann verwendet werden, um die SharePoint-Daten auf einem Remoteclient oder einem Server zu verarbeiten. Beim Entwurf wurde darauf geachtet, die Anzahl der Roundtrips zu minimieren, die zum Ausführen häufiger Aufgaben notwendig ist. Der Großteil des Client Objektmodells wird in den *Microsoft.SharePoint.Client.dll* -und *Microsoft.SharePoint.Client.Runtime.dll* Assemblys definiert. Weitere Informationen zum Client Objektmodell finden Sie unter [verwaltetes Client Objektmodell](/previous-versions/office/developer/sharepoint-2010/ee537247(v=office.14)).|

## <a name="see-also"></a>Weitere Informationen
- [Erweitern der SharePoint-Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Aufrufe in die SharePoint-Objekt Modelle](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Verwenden des SharePoint-Projekt Dienstanbieter](../sharepoint/using-the-sharepoint-project-service.md)
