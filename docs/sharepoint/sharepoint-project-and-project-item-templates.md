---
title: SharePoint-Projekt-und Projekt Element Vorlagen | Microsoft-Dokumentation
description: Überprüfen Sie die Beschreibungen der verfügbaren SharePoint-Projekt-und Projekt Element Vorlagen sowie deren Verwendung.
ms.custom: SEO-VS-2020
ms.date: 02/22/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SPE.FirstWizardPage
- VS.SharePointTools.SPE.ListInstance
- VS.SharePointTools.SPE.ListDefinition
- VS.SharePointTools.SPE.ListDefFromContentType
- VS.SharePointTools.SPE.ContentType
- SPE.Wizard
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, project and project item templates
- SharePoint development in Visual Studio, templates
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e6cbcc4d0bc99ce7ab495e0a24591b145c58f377
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "95970375"
---
# <a name="sharepoint-project-and-project-item-templates"></a>SharePoint-Projekt-und Projekt Element Vorlagen
  In den folgenden Abschnitten werden die in SharePoint verfügbaren Projekte und Projektelementvorlagen sowie deren Verwendung beschrieben.

## <a name="project-and-project-item-templates-overview"></a>Übersicht über Projekt-und Projekt Element Vorlagen
 Beim Erstellen eines neuen SharePoint-Projekts in Visual Studio wird dieses zusammen mit allen für den entsprechenden Projekttyp erforderlichen Projektelementen der Projektmappe hinzugefügt. Wenn Sie beispielsweise ein Silverlight-Webpartprojekt erstellen, wird von Visual Studio eine Projektmappe mit einem "Visuelles Webpart"-Projektelement und einem Silverlight-Anwendungsprojektelement erstellt, die auch alle für diese Projektelemente erforderlichen Dateien enthält. Projektelementvorlagen werden verwendet, um einem vorhandenen SharePoint-Projekt Projektelemente hinzuzufügen, z. B. Ereignisempfänger, Websitespalten oder Listen.

 Weitere Informationen zu SharePoint-Grundlagen finden Sie unter [SharePoint Foundation-Bausteine](/previous-versions/office/developer/sharepoint-2010/ee534971(v=office.14)). Fortgeschrittene Benutzer können angepasste Projekt- und Projektelementvorlagen erstellen. Weitere Informationen finden Sie unter [Erweitern des SharePoint-Projektsystems](../sharepoint/extending-the-sharepoint-project-system.md).

## <a name="project-templates"></a>Projektvorlagen
 Im Folgenden finden Sie eine Liste von SharePoint-Projektvorlagen. Um die SharePoint-Projektvorlagen in Visual Studio anzuzeigen, erweitern Sie im Dialogfeld **Neues Projekt** den **SharePoint** -Knoten entweder unter **Visual c#** oder **Visual Basic**, und wählen Sie dann **2010** aus.

### <a name="sharepoint-2010-project"></a>SharePoint 2010-Projekt
 Der Inhalt eines *SharePoint 2010-Projekts* ist in jeder SharePoint-Projektvorlage enthalten. Ein SharePoint 2010-Projekt enthält:

- Eine Projektdatei.

- Eine Projekteigenschaftenseite.

- Ein Ordner **Verweise** , in dem alle Assemblyverweise im Projekt aufgelistet sind.

- Ein **Featureordner, der eine** Featurekonfigurationsdatei enthält, mit der Features für SharePoint Server bereitgestellt werden. *.feature*

- Ein **Paket** Ordner, der eine *Package. Package* -Datei enthält, die zum Bereitstellen der Lösung in SharePoint verwendet wird.

- Eine "key.snk"-Datei (Schlüssel mit starkem Namen), um die Assembly zwecks verbesserter Sicherheit mit einem starken Namen zu signieren.

### <a name="sharepoint-2010-silverlight-web-part"></a>SharePoint 2010 Silverlight-Webpart
 *SharePoint 2010 Silverlight-webpartprojekte* ermöglichen es Ihnen, Webparts für SharePoint zu erstellen, die Silverlight-Anwendungen anzeigen. Beim Erstellen dieses Projekts können Sie angeben, ob eine neue Silverlight-Anwendung hinzugefügt oder auf eine vorhandene verwiesen werden soll. Weitere Informationen finden Sie unter [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) und Exemplarische Vorgehensweise [: Erstellen eines Silverlight-Webparts, das odata für SharePoint anzeigt](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).

### <a name="sharepoint-2010-visual-web-part"></a>Visuelles SharePoint 2010-Webpart
 Ein *SharePoint 2010 Visual Web Part* -Projekt enthält eine *Elements.xml* Definitionsdatei, ein **Webpartelement** und ein **Benutzer Steuer** Element Element. Sie können die Darstellung des visuellen Webparts durch Ziehen oder Kopieren der Steuerelemente von der Visual Studio-Toolbox auf die Oberfläche des Benutzersteuerelements entwerfen. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen eines SharePoint-Webparts mithilfe eines Designers und eines](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) [Baustein: Webparts](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

### <a name="import-sharepoint-2010-solution-package"></a>SharePoint 2010-Lösungspaket importieren
 *Importieren Sie SharePoint 2010-projektmappenpaketprojekte* , mit denen Sie eine vorhandene SharePoint 2010-Website, die in eine SharePoint-Lösungs Datei (*. wsp*) exportiert wurde, in Visual Studio importieren können. Nach dem Importieren in Visual Studio können Sie die zugehörigen Elemente anpassen und erneut bereitstellen. Weitere Informationen finden Sie unter [Importieren von Elementen aus einer vorhandenen SharePoint-Website](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

### <a name="import-reusable-sharepoint-2010-workflow"></a>Wiederverwendbaren SharePoint 2010-Workflow importieren
 Durch *importieren wiederverwendbarer SharePoint 2010-Workflow* Projekte können Sie einen wiederverwendbaren, deklarativen Workflow importieren, der in SharePoint Designer 2010 in Visual Studio erstellt wurde. Der Workflow wird von der SharePoint-Website als *wsp* -Datei exportiert. Nach dem Importieren in Visual Studio können Sie den Workflow anpassen, Code hinzufügen und anschließend auf einer SharePoint-Website bereitstellen. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Importieren eines wiederverwendbaren Workflows in SharePoint Designer in Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).

## <a name="project-item-templates"></a>Projekt Element Vorlagen
 Im Folgenden finden Sie eine Liste von SharePoint-Projektelementvorlagen. Durch Projektelementvorlagen werden der SharePoint-Lösung Dateien zur Unterstützung von SharePoint-Funktionalität hinzugefügt, z. B. Websitespalten, Listen und Inhaltstypen. Wenn Sie der Projekt Mappe z. b. eine Website Spalte hinzufügen, wird ein Website Spalten Projekt hinzugefügt, das eine *Elements.xml* Definitionsdatei enthält. Wenn Sie ein visuelles Webpart hinzufügen, wird der Projekt Mappe ein visuelles Webpart-Projekt hinzugefügt, das eine *Elements.xml* Datei, ein Benutzer Steuerelement und ein visuelles Webpart-Element enthält.

 Um die SharePoint-Projekt Element Vorlagen anzuzeigen, öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für ein SharePoint-Projekt, und wählen Sie dann **Hinzufügen**, **Neues Element** aus. Erweitern Sie den **SharePoint** -Knoten entweder unter **Visual c#** oder **Visual Basic**, und wählen Sie dann **2010** aus.

### <a name="application-page-farm-solution-only"></a>Anwendungsseite (nur Farm Lösung)
 Mithilfe einer **Anwendungsseite (nur Farm Lösung)** können Sie eine [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] Webseite für eine SharePoint-Website entwerfen. Anwendungsseiten können nur in Farmlösungen verwendet werden. Dieses Projektelement kann nur Farmlösungen hinzugefügt werden. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen einer Anwendungsseite und eines](../sharepoint/how-to-create-an-application-page.md) [Anwendungs _layouts Seiten Typs](/previous-versions/office/aa979604(v=office.14)).

### <a name="business-data-connectivity-model-farm-solution-only"></a>Business Data Connectivity-Modell (nur Farm Lösung)
 Mit einem **Business Data Connectivity-Modell (nur Farm Lösung)** können Sie Geschäftsdaten in SharePoint integrieren. Geschäftsdaten können von Back-End-Serveranwendungen stammen, z. B. [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)], Siebel und Service Advertising Protocol (SAP). Business Data Connectivity-Modelle können nur in Farmlösungen verwendet werden. Dieses Projektelement kann nur Farmlösungen hinzugefügt werden. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen eines BDC-Modells](../sharepoint/how-to-create-a-bdc-model.md), Gewusst [wie: Verwenden einer Ressourcen Datei zum Angeben von lokalisierten Namen, Eigenschaften und Berechtigungen](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)und [Neuerungen: Business Connectivity Services](/previous-versions/office/developer/sharepoint-2010/ee534979(v=office.14)).

### <a name="content-type"></a>Inhaltstyp
 Mithilfe von *Inhaltstyp* Elementen können Sie benutzerdefinierte Inhaltstypen auf der Grundlage eines vorhandenen Inhaltstyps (Base) erstellen, z. b. ein Dokument, eine Ankündigung oder eine Aufgabe. Von einem benutzerdefinierten Inhaltstyp werden neben denselben Attributen und Feldern wie vom grundlegenden Inhaltstyp auch alle definierten Websitespalten (Felder) bereitgestellt. Beispielsweise können Sie einen benutzerdefinierten Inhaltstyp "Kontakt" erstellen, der auf dem grundlegenden Inhaltstyp "Kontakt" aus SharePoint basiert. Sie können den Inhaltstyp anpassen, indem vorhandene Websitespalten ändern oder zusätzliche Websitespalten zu den bereits im grundlegenden Inhaltstyp enthaltenen hinzufügen.

> [!NOTE]
> Aufgrund einer SharePoint-Einschränkung können Sie keinen Farmprojektmappeninhaltstyp auf Grundlage eines Sandkastenlösungsinhaltstyps erstellen.

 Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Erstellen einer Websites palte, eines Inhaltstyps und einer Liste für SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) und [Baustein: Inhaltstyp](/previous-versions/office/developer/sharepoint-2010/ee535063(v=office.14)).

### <a name="empty-element"></a>Leeres Element
 *Leere Elemente* werden am häufigsten verwendet, um SharePoint-Projekt Elemente zu definieren, die in Visual Studio keine Projekt-oder Projekt Element Vorlage haben. Wenn Sie Ihrem Projekt ein leeres Element hinzufügen, wird ein Knoten mit dem Namen EmptyElement [x] (wobei [x] eine eindeutige Zahl ist) \) erstellt. EmptyElement [x] enthält eine einzelne Datei mit dem Namen *Elements.xml.* Verwenden [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Sie-Anweisungen, um die gewünschten Elemente in *Elements.xml* zu definieren.

### <a name="event-receiver"></a>Ereignis Empfänger
 *Ereignis Empfänger* behandeln Ereignisse für Elemente auf der SharePoint-Website, z. b. Wenn ein Element zu einer Liste hinzugefügt wird, wenn ein Webelement gelöscht wird oder wenn ein Workflow gestartet wurde. Die Projektelementvorlage "Ereignisempfänger" ermöglicht die Behandlung folgender Elemente:

- Listet Ereignisse auf.

- Listenelementereignisse

- Listen-E-Mail-Ereignisse

- Webereignisse

- Listenworkflowereignisse

  Das Ereignis Empfänger-Projekt Element erstellt einen **Ereignis Empfänger** Ordner mit einer einzelnen Klassendatei, die Ereignishandler für alle Ereignisse enthält, die Sie beim Erstellen des Projekts im **SharePoint-Anpassungs-Assistenten** angegeben haben. Die Ereignis Empfängerklasse kann Ereignisse behandeln, die auf der SharePoint-Website auftreten, wenn Elemente wie Dateien, Felder, Elemente, Listen, Anhänge, Webparts und Workflows hinzugefügt, aktualisiert, gelöscht oder entfernt werden. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen eines Ereignis Empfängers](../sharepoint/how-to-create-an-event-receiver.md) und [Baustein: Ereignis Behandlung](/previous-versions/office/developer/sharepoint-2010/ee535057(v=office.14)).

### <a name="list"></a>List
 Bei einer Liste handelt es sich um eine Instanz einer wiederverwendbaren, grundlegenden SharePoint-Listendefinition, z. B. ein Kalender oder eine Aufgabenliste. Nach dem Hinzufügen einer Liste zu Ihrer Lösung können Sie mit dem Listen-Designer Websitespalten zur Liste hinzufügen und benutzerdefinierte Listenspalten erstellen. Dazu gehören Websitespalten aus Inhaltstypen. Sie können die *Ansicht* für die Liste angeben, mit der die Spalten bestimmt werden, die in der Liste angezeigt werden. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Erstellen einer Websites palte, eines Inhaltstyps und einer Liste für SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) und [Baustein: Listen und Dokument Bibliotheken](/previous-versions/office/developer/sharepoint-2010/ee534985(v=office.14)).

### <a name="module"></a>Modul
 *Module* (nicht zu verwechseln mit [!include[vbprvb](../sharepoint/includes/vbprvb-md.md)] Modulen) enthalten alle Dateien, die Sie auf dem SharePoint-Server bereitstellen möchten, z. b. Bilder oder Notizen. Das Modul Projekt Element enthält einen **Modul** Knoten. Der Modul Knoten enthält zwei Projekt Element Vorlagen: eine XML-Definitionsdatei, die als Manifest für das Modul fungiert, und eine *sample.txt* Datei, eine Platzhalter Datei. Weitere Informationen finden Sie unter [Verwenden von Modulen zum Einschließen von Dateien in der](../sharepoint/using-modules-to-include-files-in-the-solution.md) Projekt Mappe und in den [Modulen](/previous-versions/office/developer/sharepoint-2010/ms453137(v=office.14)).

### <a name="sequential-workflow-farm-solution-only"></a>Sequenzieller Workflow (nur Farm Lösung)
 Bei einem *sequenziellen Workflow* handelt es sich um eine Reihe von Geschäftslogik Schritten, die nacheinander ausgeführt werden, bis der letzte Schritt abgeschlossen ist. Sequenzielle Workflows werden verwendet, um Prozesse zu verwalten, die SharePoint-Elemente wie Listen und Dokumente einschließen. Sie können Workflows auf Websiteebene (global) oder auf Listenebene (lokal) erstellen, und Sie können auswählen, ob ein Workflow automatisch oder manuell startet. Dieses Projektelement kann nur in Farmlösungen verwendet werden. Dieses Projektelement kann nur Farmlösungen hinzugefügt werden. Weitere Informationen finden Sie unter [Erstellen von SharePoint-Workflow Lösungen](../sharepoint/creating-sharepoint-workflow-solutions.md), [Workflows in SharePoint Server 2010](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14))und [Neuerungen: Workflow Verbesserungen](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14)).

### <a name="silverlight-web-part"></a>Silverlight-Webpart
 Mit *Silverlight-Webpart* -Projekt Elementen können Sie Webparts für SharePoint erstellen, die Silverlight-Anwendungen anzeigen. Wenn Sie dieses Projektelement in Ihre Lösung einfügen, können Sie entweder eine neue Silverlight-Anwendung hinzufügen oder zu einem späteren Zeitpunkt auf eine vorhandene verweisen. Weitere Informationen finden Sie unter [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) und Exemplarische Vorgehensweise [: Erstellen eines Silverlight-Webparts, das odata für SharePoint anzeigt](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).

### <a name="site-column"></a>Websites palte
 Eine *Websites palte*, auch als *Feld* bezeichnet, ist eines der grundlegendsten Elemente, die Sie einem SharePoint-Projekt hinzufügen können. Eine Websitespalte stellt einen Datentyp dar, z. B. eine Telefonnummer, ein Textkommentar oder der Name der Stadt eines Kontakts in einer Kontaktliste. Weitere Informationen finden Sie unter [Erstellen von Websites Palten, Inhaltstypen und Listen für SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md) und [Spalten](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14)).

### <a name="site-definition-farm-solution-only"></a>Site Definition (nur Farm Lösung)
 *Website Definitions* Projekt Elemente enthalten einen Site Definitions Ordner, der die folgenden Dateien enthält:

- Eine ASPX-Standardseite, die als Standardwebseite für die Website verwendet wird.

- Eine *onet.xml* -Datei, die die Komponenten der Site definiert.

- Eine Webtemp-XML-Datei, die die Site Definitions Konfigurationen angibt, die im Abschnitt **Vorlagen Auswahl** der Seite **neue SharePoint-Website** angezeigt werden.

  Nach dem Hinzufügen einer Websitedefinition fügen Sie Code und Dateien hinzu, um Funktionen bereitzustellen. Dieses Projektelement kann nur in Farmlösungen verwendet werden. Dieses Projektelement kann nur Farmlösungen hinzugefügt werden. Weitere Informationen finden Sie unter [Erstellen von Website Definitionen für SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md) und [Site Definitionen und Konfigurationen](/previous-versions/office/developer/sharepoint-2010/aa978512(v=office.14)).

### <a name="state-machine-workflow-farm-solution-only"></a>Zustandsautomatworkflow (nur Farm Lösung)
 Ein *Zustands Automaten Workflow* besteht aus einem Satz von Geschäftslogik Zuständen, Übergängen und Aktionen. Die Schritte in einem Zustandsautomatworkflow werden nicht nacheinander ausgeführt, sondern von Aktionen und Zuständen ausgelöst. Ebenso wie sequenzielle Workflows werden Zustandsautomatworkflows SharePoint-Elementen wie Listen und Dokumenten zugeordnet. Auch in diesem Fall können Sie Workflows auf Websiteebene (global) oder auf Listenebene (lokal) erstellen. Außerdem können Sie auswählen, ob ein Workflow automatisch oder manuell startet. Dieses Projektelement kann nur in Farmlösungen verwendet werden. Dieses Projektelement kann nur Farmlösungen hinzugefügt werden. Weitere Informationen finden Sie unter [Erstellen von SharePoint-Workflow Lösungen](../sharepoint/creating-sharepoint-workflow-solutions.md), [Workflows in SharePoint Server 2010](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14))und [Neuerungen: Workflow Verbesserungen](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14)).

### <a name="user-control-farm-solution-only"></a>Benutzer Steuerelement (nur Farm Lösung)
 Ein *Benutzer Steuer* Element ist ein benutzerdefiniertes, wiederverwendbares Steuerelement, mit dem Sie weitere ASP.NET-Steuerelemente und SharePoint-Steuerelemente Das Benutzersteuerelement kann in SharePoint ausgeführten Anwendungsseiten und Webparts hinzugefügt werden. Dieses Projektelement kann nur in Farmlösungen verwendet werden. Dieses Projektelement kann nur Farmlösungen hinzugefügt werden. Weitere Informationen finden Sie unter [Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungs Seiten](creating-reusable-controls-for-web-parts-or-application-pages.md).

### <a name="visual-web-part"></a>Visuelles Webpart
 Ein *visuelles Webpart* -Projekt Element enthält eine *Elements.xml* Definitionsdatei, ein **Webpartelement** und ein **Benutzer Steuer** Element-Element. Sie können die Darstellung des visuellen Webparts durch Ziehen oder Kopieren der Steuerelemente von der Visual Studio-Toolbox auf die Oberfläche des Benutzersteuerelements entwerfen. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen eines SharePoint-Webparts mithilfe eines Designers und eines](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) [Baustein: Webparts](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

### <a name="web-part"></a>Webpart
 Bei einem *Webpart* handelt es sich um ein serverseitiges Steuerelement, das in einem speziellen Seitentyp ausgeführt wird, der als Webpartseite bezeichnet wird. Dies sind die Bausteine von auf SharePoint-Websites angezeigten Seiten. Vom Webpartelement werden Dateien bereitgestellt, mit denen Sie ein Webpart für eine SharePoint-Website entwerfen können. Weitere Informationen finden Sie unter Vorgehens [Weise: Erstellen eines SharePoint-Webparts und Erstellen eines](../sharepoint/how-to-create-a-sharepoint-web-part.md) [Blocks: Webparts](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

## <a name="see-also"></a>Weitere Informationen
- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)
- [SharePoint-Produkte und -Technologien](/previous-versions/office/developer/sharepoint-2010/dd776256(v=office.12))
