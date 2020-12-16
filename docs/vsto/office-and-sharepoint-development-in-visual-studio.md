---
title: Office-und SharePoint-Entwicklung in Visual Studio
description: Erfahren Sie, wie Sie Microsoft Office und SharePoint erweitern können, indem Sie eine Lightweight-APP oder ein Add-in erstellen, die Benutzer aus dem Office Store herunterladen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], about developing applications
- Office development in Visual Studio
- Office projects
- Visual Studio Tools for Office, see Office development in Visual Studio
- Office applications [Office development in Visual Studio]
- Office Business Applications
- applications [Office development in Visual Studio]
- programming [Office development in Visual Studio]
- VSTO, see Office development in Visual Studio
- Office, development with Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: abd9d3aac289df702554790673cb6561a6e2488d
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525330"
---
# <a name="office-and-sharepoint-development-in-visual-studio"></a>Office-und SharePoint-Entwicklung in Visual Studio
  Sie können Microsoft Office und SharePoint erweitern, indem Sie eine einfache App oder ein Add-In erstellen, die Benutzer im [Office Store](https://store.office.com/) oder einem Unternehmenskatalog herunterladen, oder indem sie eine.NET Framework-basierte Lösung erstellen, die von Benutzern auf einem Computer installiert wird.

 In diesem Thema:

- [Erstellen von Add-Ins für Office und SharePoint](#Apps)

- [Erstellen eines VSTO-Add-ins](#Add-ins)

- [Erstellen einer SharePoint-Lösung](#Solutions)

## <a name="create-add-ins-for-office-and-sharepoint"></a><a name="Apps"></a> Erstellen von Add-Ins für Office und SharePoint
 Office 2013 und SharePoint 2013 stellen ein neues Add-In-Modell vor, das Ihnen hilft, Add-Ins als Erweiterungen von Office und SharePoint zu erstellen, zu verteilen und damit Geld zu verdienen.  Diese Add-Ins können in Office oder SharePoint online ausgeführt werden, und Benutzer können von vielen Geräten mit ihnen interagieren.

 Erfahren Sie, wie Sie das neue [Office-Add-in-Modell](/office/dev/add-ins/overview/office-add-ins) verwenden können, um die Office-Benutzeroberflächen für Ihre Benutzer zu erweitern.

 Diese Add-ins haben im Vergleich zu VSTO-Add-Ins und-Projektmappen geringfügige Merkmale, und Sie können Sie mit nahezu allen webprogrammierungs Technologien wie HTML5, JavaScript, CSS3 und XML erstellen.  Verwenden Sie zunächst das Office Developer Tools in Visual Studio, mit dem Sie Projekte erstellen, Code schreiben und Ihre Add-Ins in einem Browser ausführen können.

 ![Konzeptmodell für Apps für Office und SharePoint](../vsto/media/officeandsharepointapps2015.png "Konzeptmodell für Apps für Office und SharePoint")

### <a name="build-an-office-add-in"></a>Erstellen eines Office-Add-ins
 Um die Funktionalität von Office zu erweitern, erstellen Sie ein Office-Add-In. Es handelt sich im Grunde um eine Webseite, die in einer Office-Anwendung wie Excel, Word, Outlook und PowerPoint gehostet wird. Ihre Anwendung kann zu Dokumenten, Arbeitsblättern, e-Mail-Nachrichten, Terminen, Präsentationen und Projekten Funktionalität hinzufügen.

 Sie können Ihre Anwendung im Office Store verkaufen.  Im [Office Store](https://store.office.com/) können Sie Ihre Add-Ins einfach verkaufen, Updates verwalten und die Telemetrie nachverfolgen. Sie können Ihre Anwendung für Benutzer über einen Anwendungskatalog in SharePoint oder auf dem Exchange Server veröffentlichen.

 Die folgende Anwendung für Office zeigt Arbeitsblatt-Daten in einer Bing-Karte.

 ![Inhalts-App für Office](../vsto/media/appforoffice.png "Inhalts-App für Office")

 **Weitere Informationen**

|Beschreibung|Siehe|
|--------|---------|
|Erfahren Sie mehr über Office-Add-Ins, und erstellen Sie dann eins.|[Office-Add-ins](/office/dev/add-ins/publish/publish)|
|Vergleichen Sie die verschiedenen Möglichkeiten, mit denen Sie Office erweitern können, und entscheiden Sie, ob Sie eine Anwendung oder ein Office-Add-In verwenden möchten.|[Roadmap für Office-Add-Ins, VSTO und VBA](/archive/blogs/officeapps/roadmap-for-apps-for-office-vsto-and-vba)|

### <a name="build-a-sharepoint-add-in"></a>Erstellen eines SharePoint-Add-ins
 Um SharePoint für Ihre Benutzer zu erweitern, erstellen Sie ein SharePoint-Add-In. Es handelt sich im Grunde um eine kleine, benutzerfreundliche, eigenständige Anwendung, die einen Bedarf für Ihre Benutzer oder Ihr Unternehmen löst.

 Sie können Ihre App für SharePoint im [Office Store](https://store.office.com/)verkaufen. Sie können Ihr Add-In für Benutzer auch über einen Add-In-Katalog in SharePoint veröffentlichen.  Websitebesitzer können Ihr Add-In ohne einen Farmserver oder Websiteauflistungsadministrator auf ihren SharePoint-Websites installieren, aktualisieren und deinstallieren.

 Im folgenden finden Sie ein Beispiel für eine APP für SharePoint, die Benutzern hilft, geschäftliche Kontakte zu verwalten.

 ![Geschäftskontaktmanager-App für SharePoint](../vsto/media/appforsharepoint.png "Geschäftskontaktmanager-App für SharePoint")

 **Weitere Informationen**

|Beschreibung|Siehe|
|--------|---------|
|Erfahren Sie mehr über SharePoint-Add-Ins, und erstellen Sie dann eins.|[SharePoint-Add-Ins](/sharepoint/dev/sp-add-ins/sharepoint-add-ins)|
|Vergleichen Sie Add-Ins für SharePoint mit herkömmlichen SharePoint-Lösungen.|[SharePoint-Add-Ins im Vergleich zu SharePoint-Lösungen](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|
|Wählen Sie aus, ob Sie SharePoint-Add-In oder eine SharePoint-Lösung erstellen möchten.|[Entscheiden zwischen SharePoint-Add-Ins und SharePoint-Lösungen](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|

## <a name="create-a-vsto-add-in"></a><a name="Add-ins"></a> Erstellen eines VSTO-Add-ins
 Erstellen Sie ein VSTO-Add-in für das Ziel von Office 2007 oder Office 2010, oder erweitern Sie Office 2013 und Office 2016 über das, was mit Office-Add-Ins möglich ist. VSTO-Add-Ins werden nur auf dem Desktop ausgeführt. Benutzer müssen VSTO-Add-ins installieren, sodass Sie in der Regel schwieriger bereitzustellen und zu unterstützen sind.  Allerdings kann das VSTO-Add-In stärker in Office integriert werden. Sie können z. B. die Office-Multifunktionsleiste Registerkarten und Steuerelemente hinzufügen und erweiterte Automatisierung-Aufgaben wie das Zusammenführen von Dokumenten oder das Ändern von Diagrammen durchführen. Sie können das .NET Framework einsetzen und C# und Visual Basic zur Interaktion mit Office-Objekten verwenden.

 Im folgenden finden Sie ein Beispiel für ein VSTO-Add-in. Dieses VSTO-Add-In fügt Menübandsteuerelemente, einen benutzerdefinierten Aufgabenbereich und ein Dialogfeld zu PowerPoint hinzu.

 ![PowerPoint-Add-in-Lösung](../vsto/media/powerpointaddin.png "PowerPoint-Add-In-Lösung")

 **Weitere Informationen**

|Beschreibung|Lesen|
|--------|----------|
|Vergleichen Sie die verschiedenen Möglichkeiten, mit denen Sie Office erweitern können, und entscheiden Sie, ob Sie ein VSTO-Add-In oder ein Office-Add-In verwenden möchten.|[Roadmap für Office-Add-Ins, VSTO und VBA](/archive/blogs/officeapps/roadmap-for-apps-for-office-vsto-and-vba)|
|Erstellen eines VSTO-Add-Ins|[Mit Visual Studio erstellte VSTO-Add-Ins](create-vsto-add-ins-for-office-by-using-visual-studio.md)|

## <a name="create-a-sharepoint-solution"></a><a name="Solutions"></a> Erstellen einer SharePoint-Lösung
 Erstellen Sie eine SharePoint-Lösung für SharePoint Foundation 2010-und SharePoint-Server 2010, oder um SharePoint 2013 und SharePoint 2016 in einer Weise zu erweitern, die über die möglichen Elemente eines SharePoint-Add-ins hinausgeht.

 SharePoint-Lösungen erfordern lokale SharePoint-Farm-Server. Administratoren müssen sie installieren, und da Lösungen in SharePoint ausgeführt werden, können sie die Leistung des Servers beeinträchtigen. Allerdings bieten Lösungen einen tieferen Zugriff auf SharePoint-Objekte. Wenn Sie eine SharePoint-Lösung erstellen, können Sie außerdem das .NET Framework und C# und Visual Basic für die Interaktion mit SharePoint-Objekte verwenden.

 **Weitere Informationen**

|Beschreibung|Siehe|
|--------|---------|
|Vergleichen Sie SharePoint-Lösungen und SharePoint-Add-Ins.|[SharePoint-Add-Ins im Vergleich zu SharePoint-Lösungen](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|
|Erstellen Sie eine SharePoint-Lösung.|[Erstellen von SharePoint-Lösungen](../sharepoint/create-sharepoint-solutions.md)|