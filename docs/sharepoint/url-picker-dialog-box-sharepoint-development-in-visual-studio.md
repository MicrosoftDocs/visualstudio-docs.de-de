---
title: URL-Auswahl Dialogfeld (SharePoint-Entwicklung)
description: Informieren Sie sich über das Dialogfeld URL-Auswahl, mit dem Benutzer Dateien auswählen können, die sich in Ihrem Projekt oder auf dem lokalen Server befinden, auf dem SharePoint ausgeführt wird.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.VWD.URLPicker
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, URL picker
- SharePoint development in Visual Studio, designer
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 584b77ab714cb692069fadd6c6fad50e20d46f80
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442533"
---
# <a name="url-picker-dialog-box-sharepoint-development-in-visual-studio"></a>URL-Auswahl Dialogfeld (SharePoint-Entwicklung in Visual Studio)
  Im Dialogfeld URL-Auswahl können Sie Dateien auswählen, z. b. Masterseiten Dateien oder Bilddateien, die sich im Projekt oder auf dem lokalen Server befinden, auf dem SharePoint ausgeführt wird.

 Dieses Dialogfeld wird angezeigt, wenn Sie eine Datei auswählen können, um eine Eigenschaft festzulegen. Sie können dieses Dialogfeld öffnen, indem Sie die Schaltfläche mit den Auslassungs Punkten (![ASP.NET Mobile Designer Ellipse](../sharepoint/media/mwellipsis.gif "Auslassungszeichen im ASP.NET Mobile-Designer")) neben den verschiedenen Eigenschaften im **Eigenschaften** Fenster auswählen. Die Schaltfläche mit den Auslassungs Punkten wird auch als IntelliSense-Eingabeaufforderung angezeigt, wenn Sie bestimmten Attributen in der **Quell** Ansicht des Designers Werte zuweisen.

## <a name="uielement-list"></a>UIElement-Liste
 **Projektordner** Zeigt eine Liste der Ordner an, die im Projekt oder auf dem lokalen Server definiert sind, auf dem SharePoint ausgeführt wird. Wählen Sie die Schaltfläche Erweiterung aus, um Unterordner anzuzeigen.

 Erweitern Sie den **Projekt** Knoten, um Dateien in Ihrem Projekt auszuwählen. Um im Dialogfeld als ausgewählt angezeigt zu werden, müssen die Dateien in Ihrem Projekt die folgenden Kriterien erfüllen:

- Die Datei muss in einem zugeordneten Ordner enthalten sein.

- Die Datei muss dem Projektmappenpaket hinzugefügt werden.

- Die Datei kann nicht in einem anderen Projekt gefunden werden.

  Wenn Sie auf Dateien verweisen möchten, die diese Kriterien nicht erfüllen, müssen Sie den Pfad der Datei manuell eingeben.

  Erweitern Sie den **Server** Knoten, um Dateien auszuwählen, die sich auf dem lokalen Server befinden, auf dem SharePoint ausgeführt wird. Diese Dateien müssen die folgenden Kriterien erfüllen, damit Sie im Dialogfeld als auswählbar angezeigt werden:

- Die Datei muss sich in einem der folgenden zugeordneten Ordner befinden: **Bilder**, **Layouts** oder **ControlTemplates**.

- Die Datei kann in der SharePoint-Inhalts Datenbank nicht gefunden werden.

  Wenn Sie auf Dateien verweisen möchten, die diese Kriterien nicht erfüllen, müssen Sie den Pfad der Datei manuell eingeben.

  **Inhalt des Ordners** Zeigt eine Liste der Dateien im ausgewählten Ordner an. Wählen Sie eine Datei aus, und wählen Sie dann die Schaltfläche **OK** aus, um das Dialogfeld zu schließen und die Auswahl an den Prozess zu senden, der Sie aufgerufen hat

  **Dateityp** Ermöglicht Ihnen die Auswahl aus einer Liste von Dateien, die für die Aufgabe geeignet sind, die Sie ausführen.

## <a name="see-also"></a>Siehe auch
- [Erstellen von Anwendungsseiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
