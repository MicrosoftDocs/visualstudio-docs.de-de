---
title: Entwickeln von SharePoint-Lösungen | Microsoft-Dokumentation
description: Entwickeln von SharePoint-Lösungen. Kennen der Elemente eines SharePoint-Projekts. Verstehen der Eigenschaften von SharePoint-Projekten und -Projektelementen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
f1_keywords:
- VS.SharePointTools.Project.ProjectProperties
- VS.SharePointTools.Project.ProjectItemProperties
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, overview
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 755723dd2ae309e971e86852646ee33d2caa22cf
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "95970389"
---
# <a name="develop-sharepoint-solutions"></a>Entwickeln von SharePoint-Lösungen
  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sind mehrere SharePoint-Projekttypvorlagen zum Erstellen von SharePoint-Websites und -Websiteelementen verfügbar. Eine Liste der verfügbaren Projekttypen finden Sie unter [Vorlagen für SharePoint-Projekte und Projektelemente](../sharepoint/sharepoint-project-and-project-item-templates.md). Im Folgenden finden Sie eine Beschreibung der Elemente und Eigenschaften eines SharePoint-Projekts.

 Informationen zu SharePoint 2013 und SharePoint-Add-Ins finden Sie unter [SharePoint 2013](https://www.microsoft.com/microsoft-365/previous-versions/microsoft-sharepoint-2013) und [Erstellen von SharePoint-Add-Ins](/sharepoint/dev/sp-add-ins/sharepoint-add-ins).

## <a name="elements-of-a-sharepoint-project"></a>Elemente eines SharePoint-Projekts
 Die Knoten unter einem SharePoint-Projekt werden als *SharePoint-Elemente* bezeichnet. SharePoint-Elemente können auch eine oder mehrere Unterdateien enthalten, die als *SharePoint-Elementdateien* bezeichnet werden, z. B. [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] -Konfigurationsdateien, ASPX-Formulare usw.

 Statt Projekte mithilfe von Projektvorlagen zu erstellen, die bereits mit Projektelementdateien aufgefüllt sind, können Sie die Vorlage **Leeres Projekt** verwenden, um ein leeres SharePoint-Projekt zu erstellen, und dann manuell Projektelemente hinzufügen. SharePoint-Projekte können optional auch eine oder mehrere Funktionsdateien (zur Aktivierung in SharePoint) und eine Paketdatei enthalten, in der das Projekt verteilt wird.

### <a name="special-nodes"></a>Spezifische Knoten
 Jedes SharePoint-Projekt enthält zwei Knoten, die nicht umbenannt, gelöscht, ausgeschnitten, kopiert oder aus dem Projekt gezogen werden können. Diese Knoten lauten wie folgt:

- Features
- Paket

  Beide Knoten werden in allen SharePoint-Projekten stets angezeigt, auch wenn keine Funktionen oder Pakete für das Projekt definiert werden.

#### <a name="features-node"></a>Knotenfunktionen
 Der Knoten **Funktionen** enthält eine oder mehrere SharePoint-Projektfunktionen. Eine Funktion ist ein Container mit Erweiterungen für SharePoint. Nachdem eine Funktion auf einem SharePoint-Server bereitgestellt wurde, kann sie in Websitedefinitionen eingeschlossen oder von SharePoint-Administratoren auf SharePoint-Websites einzeln aktiviert werden. Weitere Informationen finden Sie unter [Verwenden von Features](/previous-versions/office/developer/sharepoint-2010/ms460318(v=office.14)).

 Wenn Sie ein Element zu einem SharePoint-Projekt hinzufügen, z. B. einen Inhaltstyp oder eine Listeninstanz, wird dieses einer Funktion im Knoten **Funktionen** hinzugefügt. Der Gültigkeitsbereich des Elements bestimmt, ob es einer neuen oder einer vorhandene Funktion hinzugefügt wird. Wenn das neue Element denselben Gültigkeitsbereich wie eine vorhandene Funktion aufweist, wird es der betreffenden Funktion hinzugefügt. Andernfalls wird das Element einer neuen Funktion hinzugefügt.

 Um eine Funktion manuell hinzuzufügen, führen Sie im Kontextmenü des Funktionsknotens den Befehl **Funktion hinzufügen** aus. Sie können den Inhalt einer Funktion mit dem Funktions-Designer anzeigen oder ändern. Weitere Informationen finden Sie unter [Vorgehensweise: Anpassen einer SharePoint-Funktion](../sharepoint/how-to-customize-a-sharepoint-feature.md).

 Wenn einem SharePoint-Projekt eine Funktion hinzugefügt wird, wird diese im **Projektmappen-Explorer** als Knoten mit dem Standardnamen Funktion *x*.feature angezeigt, wobei *x* eine eindeutige Zahl ist. Nachdem eine Funktion auf dem SharePoint-Server bereitgestellt wurde, kann sie von einem SharePoint-Administrator aktiviert und somit für SharePoint-Websitebenutzer verfügbar gemacht werden.

#### <a name="package-node"></a>Paketknoten
 Der Knoten **Paket** enthält eine einzelne Datei, die als Verteilungsmechanismus für das SharePoint-Projekt fungiert. Diese als *Lösungspaket* bezeichnete Datei ist CAB-basiert und weist die Erweiterung „.wsp“ auf. Ein Lösungspaket ist eine zur Bereitstellung geeignete, wiederverwendbare Datei, die einen Satz von Funktionen, Websitedefinitionen und Assemblys enthält, die für SharePoint-Websites gelten, und die Sie einzeln aktivieren oder deaktivieren können. Der Knoten **Paket** enthält darüber hinaus immer eine Datei mit dem Namen Package.wspdef, eine [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] -Definitionsdatei für das Paket. Sobald ein Paket auf dem Server bereitgestellt wurde, auf dem SharePoint ausgeführt wird, kann der SharePoint-Administrator es installieren und die zugehörigen Funktionen aktivieren.

 Sie können den Inhalt des Pakets im Paket-Designer anzeigen oder ändern, indem Sie entweder auf den Paketknoten doppelklicken oder indem Sie das Kontextmenü öffnen und dann auf **Öffnen** klicken. Weitere Informationen finden Sie unter [Erstellen von SharePoint-Lösungspaketen](../sharepoint/creating-sharepoint-solution-packages.md).

## <a name="sharepoint-project-and-project-item-properties"></a>Eigenschaften von SharePoint-Projekten und -Projektelementen
 Die Eigenschaften von SharePoint-Projekten werden wie bei anderen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Projekten im Eigenschaftenfenster und auf der Eigenschaftenseite angezeigt. Welche Eigenschaften angezeigt werden, hängt vom ausgewählten Knoten ab.

 Wenn ein SharePoint-Projekt, Projektelement, oder Projektelementdateiknoten im **Projektmappen-Explorer** ausgewählt wird, werden die folgenden Eigenschaften im Eigenschaftenfenster oder auf der Eigenschaftenseite angezeigt:

### <a name="project-properties"></a>Projekteigenschaften

|Eigenschaftenname|Beschreibung|
|-------------------|-----------------|
|Aktive Bereitstellungskonfiguration|Gibt die Reihe von Schritten an, die während der Bereitstellung ausgeführt werden. Weitere Informationen finden Sie unter [Vorgehensweise: Bearbeiten einer SharePoint-Bereitstellungskonfiguration](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).|
|Assemblybereitstellungsziel|Bestimmt den Speicherort von *SharePoint-Anwendungsassemblys* . Gültige Werte für den Assemblyspeicherort sind *GlobalAssemblyCache* (Standard) oder *WebApplication*.<br /><br /> Wenn die Eigenschaft *Sandboxed Solution* auf **true** festgelegt ist, wird diese Eigenschaft deaktiviert.|
|Nach Debuggen automatisch zurückziehen|Gibt an, ob die bereitgestellte Projektmappe in SharePoint automatisch zurückgezogen wird, nachdem Sie die Anwendung im Debugmodus in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]ausgeführt haben. Wenn diese Option ausgewählt ist, wird die Projektmappe zurückgezogen, wenn die IDE nach dem Debugging zurück zur Entwurfsansicht wechselt. Wenn die Option nicht ausgewählt ist, wird die Projektmappe nicht zurückgezogen. Weitere Informationen finden Sie unter [Deinstallieren und Zurückziehen einer Farmlösung](/previous-versions/office/developer/sharepoint-2010/aa543958(v=office.14)).|
|Konfigurationen bearbeiten|Gibt die Bereitstellungskonfiguration an, die für das Projekt verwendet werden soll. Weitere Informationen finden Sie unter [Vorgehensweise: Bearbeiten einer SharePoint-Bereitstellungskonfiguration](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) und [Bereitstellen, Veröffentlichen und Aktualisieren von SharePoint-Lösungspaketen](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).|
|Silverlight-Debugging aktivieren (anstelle von Skript-Debugging)|Wenn diese Option ausgewählt ist, wird der Silverlight-Debugger an den Debugprozess angefügt. Ist die Option nicht ausgewählt, wird der Skriptdebugger an den Debugprozess angefügt. Weitere Informationen finden Sie unter [Übersicht zum Debuggen mit Silverlight](/previous-versions/windows/).|
|Assembly in Paket einschließen|Gibt an, ob die Projektassembly zur Buildzeit verpackt wird.|
|Befehlszeile nach der Bereitstellung|Gibt die Befehle an, die nach dem Bereitstellen der SharePoint-Lösung ausgeführt werden sollen. Diese Zeile unterstützt alle Batchbefehle sowie die Auflösung von MSBuild-Variablen. Weitere Informationen finden Sie unter [How to: Set SharePoint Deployment Commands](../sharepoint/how-to-set-sharepoint-deployment-commands.md).|
|Befehlszeile vor der Bereitstellung|Gibt die Befehle an, die vor dem Bereitstellen der SharePoint-Lösung ausgeführt werden sollen. Diese Zeile unterstützt alle Batchbefehle sowie die Auflösung von MSBuild-Variablen. Weitere Informationen finden Sie unter [How to: Set SharePoint Deployment Commands](../sharepoint/how-to-set-sharepoint-deployment-commands.md).|
|Projektdatei|Der Name der Datei, die Build- und Konfigurationsinformationen sowie andere Informationen zum Projekt enthält.|
|Projektordner|Der Speicherort der Projektdatei im System. (Schreibgeschützt.)|
|Sandboxed Solution|Gibt an, ob das Projekt als *Sandkastenlösung* bereitgestellt werden soll (wird auch als *von Benutzern erstellte Lösung* bezeichnet). Sandkastenlösungen sind nicht notwendigerweise vertrauenswürdig. Der Wert **true** bedeutet, dass das Projekt als Sandkastenlösung bereitgestellt wird. Der Wert **false** heißt, dass das Projekt als Farmlösung bereitgestellt wird. Weitere Informationen finden Sie unter [Sandboxed Solution Considerations](../sharepoint/sandboxed-solution-considerations.md) und [Differences Between Sandboxed and Farm Solutions](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).|
|Website-URL|Gibt die [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] der Zielwebsite für das Projekt an.|
|Startelement|Gibt das erste auszuführende Element im Projekt an.|

 Wenn eine SharePoint-Elementdatei (beispielsweise ein Workflow oder eine Funktion im Knoten "Funktionen") ausgewählt wird, werden die folgenden Eigenschaften im Eigenschaftenfenster angezeigt:

### <a name="project-item-properties"></a>Eigenschaften von Projektelementen

|Eigenschaftenname|Beschreibung|
|-------------------|-----------------|
|Bereitstellungskonfliktlösung|Gibt die zu ergreifende Maßnahme beim Bereitstellen eines Projektelements an, dessen Eigenschaften mit denen eines bereits auf dem Server vorhandenen Elements identisch sind. Weitere Informationen finden Sie unter [Troubleshooting SharePoint Packaging and Deployment](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).|
|Funktionseigenschaften|Gibt einen Satz von Werten (gespeichert als Schlüssel-Wert-Paare) an, der beim Bereitstellen für SharePoint in eine Funktion eingeschlossen wird. Nach dem Bereitstellen der Funktion können Sie im Code auf die Eigenschaftswerte zugreifen. Weitere Informationen finden Sie unter [Providing Packaging and Deployment Information in Project Items](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|
|Funktionsempfänger|Stellt Code bereit, der ausgeführt wird, wenn für die Funktion, in der ein Projektelement enthalten ist, bestimmte Ereignisse auftreten. Weitere Informationen finden Sie unter [Providing Packaging and Deployment Information in Project Items](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|
|Ordnername|Der Name des SharePoint-Projektelementordners.|
|Projektausgabeverweise|Gibt eine Abhängigkeit (z. B. eine Assembly) an, die zum Ausführen des Projektelements benötigt wird. Weitere Informationen finden Sie unter [Providing Packaging and Deployment Information in Project Items](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|
|Einträge für sicheres Steuerelement|Gibt Steuerelemente an, die sicher sind und von nicht vertrauenswürdigen Benutzern bearbeitet werden können. Weitere Informationen finden Sie unter [Providing Packaging and Deployment Information in Project Items](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|

### <a name="project-item-file-properties"></a>Eigenschaften von Projektelementdateien

|Eigenschaftenname|Beschreibung|
|-------------------|-----------------|
|Buildvorgang|Gibt die Beziehung der Datei zu den Build- und Bereitstellungsvorgängen an. Weitere Informationen finden Sie unter [Dateieigenschaften](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|
|In Ausgabeverzeichnis kopieren|Gibt an, ob die Quelldatei bzw. die Quelldateien in das Ausgabeverzeichnis kopiert wird/werden. Es kann sich um einen der folgenden Werte handeln:<br /><br /> -   *Nicht kopieren*<br />-   *Immer kopieren*<br />-   *Kopieren, wenn neuer*<br /><br /> Weitere Informationen finden Sie unter [Dateieigenschaften](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|
|Benutzerdefiniertes Tool|Gibt ggf. den Namen eines Tools an, das die Datei zur Entwurfszeit umwandelt und die Ausgabe der Umwandlung in einer anderen Datei platziert. Eine DataSet-Datei (.[!INCLUDE[TLA2#tla_xsd](../sharepoint/includes/tla2sharptla-xsd-md.md)]) enthält beispielsweise ein benutzerdefiniertes Standardtool. Weitere Informationen finden Sie unter [Dateieigenschaften](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|
|Namespace des benutzerdefinierten Tools|Der Namespace, in den die Ausgabe des benutzerdefinierten Tools kopiert wird. Weitere Informationen finden Sie unter [Dateieigenschaften](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|
|Bereitstellungsort|Der vollqualifizierte Pfad der Datei auf dem SharePoint-Server. Dieser Pfad setzt sich aus den untergeordneten Bereitstellungsstamm- und Bereitstellungspfadeigenschaften zusammen.|
|Bereitstellungspfad|Der relative Pfad der Datei zur SharePoint-Serverdatei, z. B. Workflow1\\. Der vollqualifizierte Pfad für die Datei wird erstellt, indem der Wert *Deployment Path* mit dem Ende des Werts *Deployment Root* verkettet wird.<br /><br /> Wenn Sie für die Eigenschaft *Bereitstellungstyp* den Wert von *RootFile* auswählen, wird die Eigenschaft *Deployment Root* in \<SharePointRoot>\\ geändert, was zu einem voll qualifizierten Pfad von \<SharePointRoot>\Workflow1\\ führt. Weitere Informationen finden Sie unter [Packen und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md).|
|Deployment Root|Eine Zeichenfolge. Der Stammordner, in dem die Datei auf dem SharePoint-Server bereitgestellt wird. Beispielsweise \<SharePointRoot>\Template\Features\\\<FeatureName>\\.<br /><br /> Der Wert der *Deployment Root* -Eigenschaft wird vom Wert der *Deployment Type* -Einstellung bestimmt.|
|Bereitstellungstyp|Der Bereitstellungstyp der Datei, der den zugehörigen *Deployment Root* -Wert bestimmt. Es kann sich um einen der folgenden Werte handeln:<br /><br /> NoDeployment: *\<no value>*<br /><br /> ElementManifest: *\<SharePointRoot>\Template\Features\\\<FeatureName>* \\<br /><br /> ElementFile: *\<SharePointRoot>\Template\Features\\\<FeatureName>\\*<br /><br /> TemplateFile: *\<SharePointRoot>\Template\\*<br /><br /> RootFile: *\<SharePointRoot>\\*<br /><br /> GlobalResource: *\<SharePointRoot>\Resources\\*<br /><br /> ClassResource: *\<ClassResourcePath>\\*<br /><br /> Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.SharePoint.DeploymentType>.|
|Dateiname|Der Name der Datei oder des Ordners für die Elementdatei.|
|Vollständiger Pfad|Der Speicherort der Datei für das Element. (Schreibgeschützt.)|

## <a name="related-topics"></a>Verwandte Themen

|Titel|Beschreibung|
|-----------|-----------------|
|[Vorlagen für SharePoint-Projekte und Projektelemente](../sharepoint/sharepoint-project-and-project-item-templates.md)|Beschreibt die in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]verfügbaren Vorlagen für SharePoint-Projekte und Projektelemente.|
|[Vorgehensweise: Hinzufügen von Elementen zu einem SharePoint-Projekt](../sharepoint/how-to-add-items-to-a-sharepoint-project.md)|Beschreibt, wie einem [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -SharePoint-Projekt neue oder vorhandene Elemente hinzugefügt werden.|
|[Exemplarische Vorgehensweise: Erstellen einer Websitespalte, eines Inhaltstyps und einer Liste für SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|Enthält eine schrittweise Einführung in das Erstellen von Kundenfeldern, Inhaltstypen, Listendefinitionen und Listeninstanzen.|
|[How to: Erstellen eines Ereignisempfängers](../sharepoint/how-to-create-an-event-receiver.md)|Beschreibt, wie ein Ereignisempfänger für das in [Exemplarische Vorgehensweise: Erstellen einer Websitespalte, eines Inhaltstyps und einer Liste für SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) erstellte Projekt hinzugefügt wird.|
|[Erstellen von SharePoint-Workflow-Projektmappen](../sharepoint/creating-sharepoint-workflow-solutions.md)|Beschreibt, wie Workflowprojekte erstellt werden, die Workflowzuordnungsformulare und Workflowinitiierungsformulare einschließen.|
|[Erstellen von Seiten für SharePoint](../sharepoint/creating-pages-for-sharepoint.md)|Beschreibt, wie Sie Seiten (beispielsweise Anwendungsseiten, Websiteseiten, Gestaltungsvorlagen und Seitenlayouts) für SharePoint erstellen können.|
|[Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Beschreibt, wie Sie Steuerelemente hinzufügen, mit denen Benutzer Inhalt, Darstellung und Verhalten der Seiten einer SharePoint-Website direkt im Browser ändern können.|
|[Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Beschreibt, wie Benutzersteuerelemente erstellt werden, die von Anwendungsseiten und Webparts genutzt werden können, die in SharePoint ausgeführt werden.|
|[Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|Beschreibt, wie Daten von Webdiensten und Back-End-Serveranwendungen in eine SharePoint-Anwendung integriert werden.|
|[Erstellen von Websitedefinitionen für SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md)|Beschreibt, wie Websitedefinitionen erstellt werden: Vorlagen, die zum Erstellen von SharePoint-Websites verwendet werden.|
|[Importieren von Elementen aus einer vorhandenen SharePoint-Website](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)|Beschreibt, wie Elemente wie Inhaltstypen und Module von einer vorhandenen SharePoint-Website in ein [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -SharePoint-Projekt importiert werden.|
|[Verwenden von Modulen zum Einfügen von Dateien in die Projektmappe](../sharepoint/using-modules-to-include-files-in-the-solution.md)|Beschreibt, wie Module verwendet werden, um Dateien aus dem [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Projekt auf der SharePoint-Website bereitzustellen.|
|[Durchsuchen von SharePoint-Verbindungen mit dem Server-Explorer](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)|Beschreibt, wie lokale SharePoint-Websites mit Server-Explorer durchsucht werden.|
|[Bereitstellen von Pack- und Bereitstellungsinformationen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)|Beschreibt, wie Projektelementeigenschaften verwendet werden, um Verpackungs- und Bereitstellungsinformationen für Projekte bereitzustellen, z. B. Einträge für sichere Steuerelemente, Projektausgabeverweise und Funktionseigenschaften.|
|[How to: Hinzufügen und Entfernen zugeordneter Ordner](../sharepoint/how-to-add-and-remove-mapped-folders.md)|Beschreibt, wie dem Projekt zugeordnete Ordner hinzugefügt werden können, um den Zugriff auf SharePoint-Ressourcen zu erleichtern.|
|[Überlegungen zu Sandkastenlösungen](../sharepoint/sandboxed-solution-considerations.md)|Beschreibt die mit Sandkastenlösungen zusammenhängenden Probleme.|
|[Sicherheit für SharePoint-Lösungen](../sharepoint/security-for-sharepoint-solutions.md)|Erläutert Sicherheitsaspekte bei der Entwicklung von SharePoint-Lösungen in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|
|[URL-Auswahldialogfeld &#40SharePoint-Entwicklung in Visual Studio&#41;](../sharepoint/url-picker-dialog-box-sharepoint-development-in-visual-studio.md)|Beschreibt ein Dialogfeld, mit dem Sie Pfadverweise auf Ressourcen im Projekt oder auf dem lokalen SharePoint-Server hinzufügen können.|

## <a name="see-also"></a>Weitere Informationen
- [Erste Schritte &#40;SharePoint-Entwicklung in Visual Studio&#41;](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)
- [Durchsuchen von SharePoint-Verbindungen mit dem Server-Explorer](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [Erstellen und Debuggen von SharePoint-Lösungen](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Packen und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
