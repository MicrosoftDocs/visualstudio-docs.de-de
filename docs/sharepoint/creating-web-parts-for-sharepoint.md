---
title: Erstellen von Webparts für SharePoint | Microsoft-Dokumentation
description: Erstellen von Webparts für SharePoint. Unter Verwendung von Webparts können Benutzer Inhalt, Darstellung und Verhalten der Seiten einer SharePoint-Website mithilfe eines Browsers ändern.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
f1_keywords:
- Microsoft.SharePoint.WebControls.DateTimeControl
- Microsoft.SharePoint.WebControls.CssLink
- Microsoft.SharePoint.WebControls.RssLink
- Microsoft.SharePoint.WebControls.Theme
- Microsoft.SharePoint.WebControls.AspMenu
- Microsoft.SharePoint.WebControls.ListProperty
- Microsoft.SharePoint.WebControls.ProjectProperty
- Microsoft.SharePoint.WebControls.FormsDigest
- Microsoft.SharePoint.WebControls.ScriptLink
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, Web Parts
- Web Parts [SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ae28ab44b12c979f3c405bd7d853d7a2d196aae4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948933"
---
# <a name="create-web-parts-for-sharepoint"></a>Erstellen von Webparts für SharePoint
  Unter Verwendung von Webparts können Benutzer Inhalt, Darstellung und Verhalten der Seiten einer SharePoint-Website mithilfe eines Browsers ändern. Webparts sind serverseitige Steuerelemente, die in einer Webpartseite ausgeführt werden. Diese sind die Bausteine der Seiten, die auf einer SharePoint-Website angezeigt werden. Weitere Informationen finden Sie unter [Baustein: Webparts](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

 Sie können Webparts in einer SharePoint-Website unter Verwendung von Vorlagen aus Visual Studio erstellen und debuggen.

## <a name="create-a-web-part-in-visual-studio"></a>Erstellen eines Webparts in Visual Studio
 Um ein Webpart zu erstellen, fügen Sie jedem SharePoint-Projekt das Element **Webpart** hinzu. Sie können ein Element **Webpart** in einer Sandkastenlösung oder einer Farmlösung verwenden.

 Wenn Sie ein Webpart mit einem Designer visuell entwerfen möchten, erstellen Sie ein Projekt vom Typ **Visuelles Webpart**, oder fügen Sie jedem SharePoint-Projekt ein Element **Visuelles Webpart** hinzu. Sie können ein Element **Visuelles Webpart** nur in einer Farmlösung verwenden.

### <a name="web-part-item"></a>Element „Webpart“
 Das Element **Webpart** stellt Dateien bereit, die Sie verwenden können, um ein Webpart für eine SharePoint-Website zu entwerfen. Wenn Sie das Element **Webpart** hinzufügen, erstellt Visual Studio einen Ordner im Projekt und fügt diesem Ordner dann mehrere Dateien hinzu. In der folgenden Tabelle werden die einzelnen Dateien beschrieben.

|Datei|Beschreibung|
|----------|-----------------|
|*Elements.xml*|Enthält Informationen, die von der Funktionsdefinitionsdatei im Projekt verwendet werden, um das Webpart bereitzustellen.|
|WEBPART-Datei|Stellt Informationen bereit, die SharePoint benötigt, um das Webpart in einem Webpartkatalog anzuzeigen.|
|Codedatei|Enthält Methoden, die Steuerelemente zum Webpart hinzufügen und benutzerdefinierten Inhalt innerhalb des Webparts generieren.|

 Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen eines SharePoint-Webparts](../sharepoint/how-to-create-a-sharepoint-web-part.md).

### <a name="visual-web-part-item"></a>Element „Visuelles Webpart“
 Ein visuelles Webpart ist ein Webpart, das Sie mit dem Visual Web Developer-Designer in Visual Studio erstellen. Ein visuelles Webpart funktioniert genauso wie jedes andere Webpart. Um einem Webpart Steuerelemente wie Schaltflächen und Textfelder hinzuzufügen, fügen Sie einer XML-Datei Code hinzu. Einem visuellen Webpart werden Steuerelemente jedoch hinzugefügt, indem sie aus der **Toolbox** von Visual Studio in das Webpart gezogen oder kopiert werden. Der Designer generiert dann den erforderlichen Code in der XML-Datei. Weitere Informationen finden Sie unter [How to: Erstellen eines SharePoint-Webparts mithilfe eines Designers](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).

## <a name="sharepoint-controls"></a>SharePoint-Steuerelemente
 Visual Studio stellt einige Steuerelemente zum Erstellen von SharePoint-Seiten (beispielsweise Anwendungsseiten) bereit. Diese Steuerelemente werden in der **Toolbox** unter **SharePoint-Steuerelemente** angezeigt. Die Funktionalität dieser Steuerelemente ist vom Namespace [Microsoft.SharePoint.WebControls](/previous-versions/office/sharepoint-server/ms413880(v=office.15)) abgeleitet, der ASP.NET-Serversteuerelemente enthält, die in SharePoint-Website- und Listenseiten verwendet werden.

|Name des Steuerelements|BESCHREIBUNG|
|------------------|-----------------|
|[AspMenu](/previous-versions/office/sharepoint-server/ms454108(v=office.15))|Fügt ein ASP-Menü ein. Weitere Informationen finden Sie unter [Übersicht über das Menu-Steuerelement](/previous-versions/ecs0x9w5(v=vs.140)).|
|[CssLink](/previous-versions/office/sharepoint-server/ms439048(v=office.15))|Fügt ein **LINK**-Element auf der *ASPX*-Seite ein und wendet mindestens ein externes Stylesheet an, das von **CssRegistration** definiert wird.|
|[DateTimeControl](/previous-versions/office/sharepoint-server/ms414993(v=office.15))|Fügt ein DateTime-Steuerelement auf der *ASPX*-Seite ein.|
|[FormDigest](/previous-versions/office/sharepoint-server/ms416616(v=office.15))|Fügt eine Sicherheitsvalidierung auf der *ASPX*-Seite ein.|
|[ListProperty](/previous-versions/office/sharepoint-server/ms455032(v=office.15))|Gibt eine Eigenschaft einer angegebenen Liste zurück.|
|[ProjectProperty](/previous-versions/office/sharepoint-server/ms478990(v=office.15))|Gibt eine globale Eigenschaft der aktuellen Website zurück.|
|[RssLink](/previous-versions/office/sharepoint-server/ms457574(v=office.15))|Fügt einen Link zu einem RSS-Feed auf der *ASPX*-Seite ein.|
|[ScriptLink](/previous-versions/office/sharepoint-server/ms411959(v=office.15))|Stellt Eigenschaften und Methoden zum Registrieren von Ressourcen (beispielsweise Skripts) auf einer Seite bereit, sodass sie angefordert werden können, wenn die Seite gerendert wird.|
|[Design](/previous-versions/office/sharepoint-server/ms460735(v=office.15))|Wendet ein Design auf die *ASPX*-Seite an.|

## <a name="debug-a-web-part"></a>Debuggen eines Webparts
 Sie können ein SharePoint-Projekt, das ein Webpart enthält, auf dieselbe Weise debuggen wie andere Visual Studio-Projekte. Wenn Sie den Visual Studio-Debugger starten, wird von Visual Studio die SharePoint-Website geöffnet.

 Um mit dem Debuggen des Codes zu beginnen, fügen Sie das Webpart einer Webpartseite in SharePoint hinzu.

 Weitere Informationen zum Debuggen von SharePoint-Projekten finden Sie unter [Problembehandlung von SharePoint-Lösungen](../sharepoint/troubleshooting-sharepoint-solutions.md).

## <a name="visual-web-part-limitations"></a>Einschränkungen für visuelle Webparts
 Ab Visual Studio können Sie visuelle Webparts zu SharePoint-Sandkastenlösungen und -Farmlösungen hinzufügen. Allerdings weisen visuelle Webparts die folgenden Einschränkungen auf:

- Visuelle Webparts unterstützen keine ersetzbaren Parameter. Weitere Informationen finden Sie unter [Ersetzbare Parameter](../sharepoint/replaceable-parameters.md).

- Benutzersteuerelemente oder visuelle Webparts können nicht per Drag&amp;Drop in visuelle Webparts verschoben oder in visuelle Webparts kopiert werden. Diese Aktion führt zu Buildfehlern.

- Visuelle Webparts bieten keine direkte Unterstützung von SharePoint-Servertoken wie $SPUrl. Weitere Informationen finden Sie im Abschnitt zu Einschränkungen von Token in visuellen Sandkasten-Webparts im Thema [Problembehandlung von SharePoint-Lösungen](../sharepoint/troubleshooting-sharepoint-solutions.md).

- Visuelle Webparts in einer Sandkastenlösung verursachen gelegentlich den Fehler "Die Sandkasten-Codeausführungsanforderung wurde abgelehnt, weil der Sandkasten-Codeausführungs-Hostdienst zu ausgelastet war, um die Anforderung zu verarbeiten." Weitere Informationen zu diesem Fehler finden Sie in diesem Beitrag im [Blog des SharePoint-Entwicklerteams](/archive/blogs/sharepointdev/error-the-sandboxed-code-execution-request-was-refused-because-the-sandboxed-code-host-service-was-too-busy-to-handle-the-request-ricky-kirkham#10149157).

- Serverseitiges JavaScript-Debugging wird in Visual Studio nicht unterstützt, clientseitiges JavaScript-Debugging hingegen schon.

   Obwohl Sie einer serverseitigen Markupdatei Inline-JavaScript hinzufügen können, wird das Debuggen nicht für die dem Markup hinzugefügten Haltepunkte unterstützt. Um JavaScript zu debuggen, verweisen Sie auf eine externe JavaScript-Datei in der Markupdatei und legen die Haltepunkte in der JavaScript-Datei fest.

- Das Debugging von [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]Inlinecode muss in der generierten Codedatei statt in der Markupdatei ausgeführt werden.

- Visuelle Webparts unterstützen die Verwendung der `<@ Assembly Src=`-Anweisung nicht.

- SharePoint-Websteuerelemente und einige [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]-Steuerelemente werden in der SharePoint-Sandkastenumgebung nicht unterstützt. Wenn nicht unterstützte Steuerelemente für ein visuelles Webpart in einer Sandkastenlösung verwendet werden, wird der Fehler "Der Typ- oder Namespacename 'Theme' ist im Namespace 'Microsoft.SharePoint.WebControls' nicht vorhanden" angezeigt.

  Weitere Informationen zu Sandkastenlösungen finden Sie unter [Unterschiede zwischen Sandkasten- und Farmlösungen](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).

## <a name="create-older-style-sharepoint-based-web-parts"></a>Erstellen von SharePoint-basierten Webparts im älteren Format
 Sie können die Vorlagen in Visual Studio verwenden, um benutzerdefinierte [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)]-Webparts für SharePoint zu erstellen. [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)]-Webparts werden auf Grundlage der [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]-Webpartinfrastruktur erstellt und werden als Typ für neue Projekte empfohlen.

 In seltenen Fällen müssen Sie möglicherweise ein Webpart mit dem SharePoint-basierten Webpart im älteren Format erstellen. Sie können diese Typen von Webparts mithilfe von Visual Studio erstellen, jedoch stellt Visual Studio keine Vorlagen bereit, die speziell für das Erstellen dieser Webparts ausgelegt sind.

 Weitere Informationen zu den Situationen, in denen ein SharePoint-basiertes Webpart im älteren Format erstellt werden sollte, finden Sie unter [Webpartinfrastruktur in SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ms415560(v=office.14)). Weitere Informationen zum Erstellen eines SharePoint-basierten Webparts im älteren Format finden Sie in der [exemplarischen Vorgehensweise zum Erstellen eines grundlegenden SharePoint-Webparts](/previous-versions/office/ms452873(v=office.14)).

## <a name="related-topics"></a>Verwandte Themen

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[How to: Erstellen eines SharePoint-Webparts](../sharepoint/how-to-create-a-sharepoint-web-part.md)|Zeigt das Erstellen von Webparts für SharePoint-Seiten.|
|[How to: Erstellen eines SharePoint-Webparts mithilfe eines Designers](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|Zeigt das Erstellen von Webparts für SharePoint mithilfe einer visuellen Entwurfsoberfläche.|
|[How to: Erstellen eines Benutzersteuerelements für eine SharePoint-Anwendungsseite oder ein SharePoint-Webpart](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Zeigt, wie Sie benutzerdefinierte, wiederverwendbare Steuerelemente erstellen, die von Anwendungsseiten und Webparts genutzt werden können, die in SharePoint ausgeführt werden.|
|[Exemplarische Vorgehensweise: Erstellen eines Webparts für SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|Beschreibt, wie ein Webpart für SharePoint entworfen wird.|
|[Exemplarische Vorgehensweise: Erstellen eines Webparts für SharePoint mithilfe eines Designers](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|Beschreibt, wie ein Webpart für SharePoint durch Ziehen von Steuerelementen auf eine visuelle Entwurfsoberfläche entworfen wird.|
|[Exemplarische Vorgehensweise: Erstellen eines Silverlight-Webparts, das OData für SharePoint anzeigt](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|Beschreibt, wie ein Webpart für SharePoint entworfen wird, das eine Silverlight-Anwendung hostet und Daten aus SharePoint-Listen anzeigt.|