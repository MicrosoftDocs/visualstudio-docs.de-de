---
title: Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten | Microsoft-Dokumentation
titleSuffix: ''
description: Erstellen Sie in Visual Studio benutzerdefinierte, wiederverwendbare Steuerelemente (Benutzersteuerelemente) für in SharePoint ausgeführte Anwendungsseiten und Webparts.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- user controls [SharePoint development in Visual Studio], creating
- SharePoint development in Visual Studio, user controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2e9d2f3a99e3e43ebf40208bf8dfc01d5ac92dca
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850597"
---
# <a name="create-reusable-controls-for-web-parts-or-application-pages"></a>Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten
  In Visual Studio können Sie benutzerdefinierte, wiederverwendbare Steuerelemente für in SharePoint ausgeführte Anwendungsseiten und Webparts erstellen. Diese Steuerelemente werden als Benutzersteuerelemente bezeichnet. Ein Benutzersteuerelement ist ein zusammengesetztes Steuerelement, das ähnlich wie eine ASP.NET-Webseite funktioniert: Sie können einem Benutzersteuerelement vorhandene Webserver-Steuerelemente und Markup hinzufügen und Eigenschaften und Methoden für das Steuerelement definieren. Anschließend können Sie all dies in ASP.NET-Webseiten einbetten, wo es als Einheit fungiert.

## <a name="create-a-user-control"></a>Erstellen eines Benutzersteuerelements
 Fügen Sie einem **leeren SharePoint-Projekt** ein **Benutzersteuerelement** hinzu, um ein Benutzersteuerelement zu erstellen. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen eines Benutzersteuerelements für eine SharePoint-Anwendungsseite oder ein SharePoint-Webpart](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md).

 Wenn Sie das Element **Benutzersteuerelement** hinzufügen, erstellt Visual Studio einen Ordner im Projekt und fügt diesem Ordner dann mehrere Dateien hinzu. In der folgenden Tabelle werden die einzelnen Dateien beschrieben.

|Datei|BESCHREIBUNG|
|----------|-----------------|
|Datei des Benutzersteuerelements|Enthält die Definition des Benutzersteuerelements. Entwerfen Sie das Benutzersteuerelement, indem Sie dieser Datei Steuerelemente und Markup hinzufügen.|
|Codedatei|Enthält den Code hinter dem Benutzersteuerelement. Fügen Sie dieser Datei Code hinzu, um die Verarbeitung von Ereignissen zu konfigurieren.|
|Datei des Designercodes|Beinhaltet vom Designer generierten Code und sollte nicht direkt bearbeitet werden|

## <a name="design-the-user-control"></a>Entwerfen des Benutzersteuerelements
 Entwerfen Sie das Benutzersteuerelement mit dem Visual Web Developer-Designer in Visual Studio. Dieser Designer wird angezeigt, wenn Sie die Datei des Benutzersteuerelements in Ihrem Projekt öffnen und auf die Registerkarte **Entwurf** klicken.

## <a name="consume-the-user-control"></a>Verwenden des Benutzersteuerelements
 Benutzersteuerelemente werden erst in SharePoint angezeigt, wenn Sie diese in eine Anwendungsseite oder ein Webpart einbetten.

 Öffnen Sie dazu die Webseite, der Sie das ASP.NET-Benutzersteuerelement hinzufügen möchten. Wechseln Sie zur Designansicht, klicken Sie im Projektmappen-Explorer auf die Datei des benutzerdefinierten Benutzersteuerelements, und ziehen Sie diese auf die Seite. Das ASP.NET-Benutzersteuerelement wird der Seite hinzugefügt, und der Designer erstellt die erforderliche „@ Register“-Anweisung, damit die Seite das Benutzersteuerelement erkennt. Nun können Sie mit den öffentlichen Eigenschaften und Methoden des Steuerelements arbeiten.

 Fügen Sie das Benutzersteuerelement in der Codedatei des Webparts der <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A>-Sammlung hinzu, um ein Benutzersteuerelement in ein Webpart einzubetten. Im folgenden Beispiel wird ein Benutzersteuerelement der <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A>-Sammlung eines Webparts hinzugefügt.

 [!code-vb[SP_VisualWebPart#5](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1.vb#5)]
 [!code-csharp[SP_VisualWebPart#5](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1.cs#5)]

## <a name="debug-a-user-control"></a>Debuggen eines Benutzersteuerelements
 Stellen Sie zum Debuggen eines Benutzersteuerelements sicher, dass das Benutzersteuerelement in einer Anwendungsseite oder einem Webpart in Ihrem SharePoint-Projekt enthalten ist. Wenn dem so ist, können Sie den Code im Benutzersteuerelement genauso wie jeden anderen Code in einem beliebigen Visual Studio-Projekt debuggen.

 Wenn Sie den Visual Studio-Debugger starten, wird von Visual Studio die SharePoint-Website geöffnet.

 Öffnen Sie in SharePoint die Anwendungsseite, die das Benutzersteuerelement enthält. Wenn das Benutzersteuerelement in einem Webpart enthalten ist, fügen Sie das Webpart in SharePoint zu einer Webpartseite hinzu.

 Weitere Informationen zum Debuggen von SharePoint-Projekten finden Sie unter [Problembehandlung von SharePoint-Lösungen](../sharepoint/troubleshooting-sharepoint-solutions.md).

## <a name="related-topics"></a>Verwandte Themen

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[How to: Erstellen eines Benutzersteuerelements für eine SharePoint-Anwendungsseite oder ein SharePoint-Webpart](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|In diesem Artikel erfahren Sie, wie Sie benutzerdefinierte, wiederverwendbare Steuerelemente für in SharePoint ausgeführte Anwendungsseiten und Webparts erstellen.|
