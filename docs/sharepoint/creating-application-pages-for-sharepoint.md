---
title: Erstellen von Anwendungs Seiten für SharePoint | Microsoft-Dokumentation
description: Erstellen von Anwendungs Seiten für SharePoint. Eine Anwendungsseite ist eine ASP.NET-Webseite, die für die Verwendung auf einer SharePoint-Website konzipiert ist.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, Web pages
- SharePoint development in Visual Studio, content pages
- SharePoint development in Visual Studio, application pages
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9ecd6573573d76c3e47a2c87a4f455cb9890fb31
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949180"
---
# <a name="create-application-pages-for-sharepoint"></a>Erstellen von Anwendungsseiten für SharePoint
  Eine *Anwendungsseite* ist eine ASP.NET-Webseite, die für die Verwendung auf einer SharePoint-Website konzipiert ist. Anwendungs Seiten sind ein spezieller Typ der ASP.NET-Seite. Der Hauptunterschied zwischen einer Anwendungsseite und einer standardmäßigen ASP.NET-Seite besteht darin, dass eine Anwendungsseite Inhalte enthält, die mit einer SharePoint-Master Seite zusammengeführt werden. Eine Master Seite ermöglicht es Anwendungs Seiten, dasselbe Aussehen und Verhalten wie andere Seiten auf einer Website zu verwenden.

 Visual Studio ermöglicht Ihnen das Entwerfen von Anwendungs Seiten mithilfe eines Designers. Der Designer zeigt einen Inhalts Bereich für jeden Inhalts Platzhalter an, der in einer Master Seite definiert ist. Sie können die Anwendungsseite entwerfen, indem Sie Steuerelemente in diese Inhaltsbereiche ziehen.

## <a name="application-pages"></a>Anwendungsseiten
 Anwendungs Seiten werden für alle Websites auf dem Server freigegeben, während eine Website Seite für eine Website spezifisch ist. Weitere Informationen finden Sie unter [SharePoint-Seiten Typen](/previous-versions/office/developer/sharepoint-2010/aa979592(v=office.14)).

 Standardmäßig sind die meisten Seiten, die beim Erstellen einer SharePoint-Website angezeigt werden, Website Seiten. Eine Website Seite kann einer SharePoint-Seiten Bibliothek hinzugefügt werden. Benutzer können eine Website Seite mithilfe von Tools wie SharePoint Designer anpassen. Eine Website Seite kann auch Features wie dynamische Webparts und Webpartzonen hosten.

 Anwendungs Seiten können diese Aktionen nicht ausführen. Eine Anwendungsseite ist jedoch der beste Typ der zu erstellenden Seite, wenn die Seite benutzerdefinierten Code enthalten soll. Obwohl Sie benutzerdefinierten Code zu einer Website Seite hinzufügen können, wird der Code nicht mehr ausgeführt, wenn der Benutzer die Seite mithilfe von Tools wie SharePoint Designer anpasst.

> [!NOTE]
> Visual Studio bietet keine Vorlagen, mit denen Sie Website Seiten für eine SharePoint-Website erstellen können. Weitere Informationen finden Sie unter [SharePoint-Seiten Typen](/previous-versions/office/developer/sharepoint-2010/aa979592(v=office.14)).

## <a name="create-an-application-page"></a>Erstellen einer Anwendungsseite
 Fügen Sie ein **Anwendungs Seiten** Element einem SharePoint-Projekt hinzu, um eine Anwendungsseite zu erstellen. Wenn Sie eine Anwendungsseite erstellen, fügt Visual Studio Ihrem Projekt die folgenden Ordner hinzu:

|Ordner|BESCHREIBUNG|
|------------|-----------------|
|Layouts|Wird dem _layouts virtuellen Verzeichnis des SharePoint-Dateisystems zugeordnet.|
|Unterordner "Layouts"|Enthält die Dateien, aus denen die Anwendungsseite besteht. Standardmäßig hat dieser Ordner denselben Namen wie Ihr Projekt. Sie können diesen Ordner jederzeit umbenennen. Wenn Sie das Projekt ausführen, stellt Visual Studio diesen Ordner im _layouts virtuellen Verzeichnis des SharePoint-Dateisystems bereit.|

 Visual Studio fügt Ihrem Projekt die folgenden Dateien hinzu:

|Datei|BESCHREIBUNG|
|----------|-----------------|
|ASP.net-Auslagerungs Datei (*. aspx*)|Enthält XML-Markup, das die Seite definiert.|
|Codedatei der Anwendungsseite|Enthält Code hinter der Anwendungsseite. Fügen Sie dieser Datei Code hinzu, der Ereignisse behandelt.|
|Codedatei des Anwendungs Seiten-Designers|Enthält Code, der vom Designer generiert wird. Bearbeiten Sie diese Datei nicht direkt.|

## <a name="design-and-debug-an-application-page"></a>Entwerfen und Debuggen einer Anwendungsseite
 Entwerfen Sie den Inhalt einer Anwendungsseite mithilfe der Designer Ansicht in Visual Studio. Dieser Designer wird angezeigt, wenn Sie die Anwendungsseite im Projekt öffnen (indem Sie darauf doppelklicken, oder indem Sie das Kontextmenü öffnen und dann **Öffnen** auswählen) und dann auf die Schaltfläche **Entwurf** am unteren Rand des Editors klicken.

> [!NOTE]
> Sie können die Seite nur in der **Quell** Ansicht des Designers entwerfen. Die **Entwurfs** Ansicht des Designers ist für Anwendungs Seiten deaktiviert.

 Sie können eine Anwendungsseite genauso Debuggen, wie Sie andere SharePoint-Projekt Elemente in Visual Studio debuggen. Wenn Sie den Visual Studio-Debugger starten, wird von Visual Studio die SharePoint-Website geöffnet.

 Um die Anwendungsseite anzuzeigen, müssen Sie manuell zum Speicherort der Anwendungsseite navigieren (z. b.: http://<em>server_name</em>/_layouts/*Project_Name*/ApplicationPage1.aspx).

 Weitere Informationen zum Debuggen von SharePoint-Projekten finden Sie unter [Problembehandlung von SharePoint-Lösungen](../sharepoint/troubleshooting-sharepoint-solutions.md).

## <a name="choose-a-master-page"></a>Master Seite auswählen
 Standardmäßig verweist ein **Anwendungs Seiten** Element auf die Master Seite der Website, die Sie zum Debuggen des Projekts verwenden. Diese Seite heißt V4. Master, und Sie finden Sie im **Masterseiten** Katalog der SharePoint-Website.

 Sie können explizit ändern, welche Master Seite von der Anwendungsseite verwendet wird, indem Sie das- `MasterPageFile` Attribut des Application- `Page` Elements festlegen. (Beispiel: `MasterPageFile="~/_layouts/applicationv4.master"` ). Tatsächlich müssen Sie dieses Attribut festlegen, wenn dynamische Masterseiten auf dem SharePoint-Server nicht aktiviert sind. Weitere Informationen zu Masterseiten in SharePoint finden Sie unter [Masterseiten](/previous-versions/office/developer/sharepoint-2010/ms443795(v=office.14)).

## <a name="see-also"></a>Weitere Informationen
- [Ausführliche Informationen zur SharePoint Foundation-Entwicklung](/previous-versions/office/developer/sharepoint-2010/ee539092(v=office.14))
- [ASP.net Übersicht](/aspnet/overview)
- [ASP.NET-Webseiten 2](/aspnet/web-pages/index)
