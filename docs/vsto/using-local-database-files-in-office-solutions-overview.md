---
title: Verwenden lokaler Datenbankdateien in der Übersicht über Office-Lösungen
description: Erfahren Sie, wie Sie eine Datenbankdatei, z. b. eine SQL Server Express Datei (. mdf) oder eine Microsoft Office Zugriffsdatei (. mdb), in Ihre Office-Projekt Mappe einschließen können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- data [Office development in Visual Studio], local
- local data [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 857038700a29f423250f006e743152bceea43c14
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838229"
---
# <a name="use-local-database-files-in-office-solutions-overview"></a>Verwenden lokaler Datenbankdateien in der Übersicht über Office-Lösungen
  Sie können eine Datenbankdatei, z. b. eine SQL Server Express Datei (*. mdf*) oder eine Microsoft Office Zugriffsdatei (*. mdb*), in Ihre Office-Projekt Mappe einschließen. Dies ermöglicht es Endbenutzern, eine lokale Datenbank in Situationen zu verwalten, in denen die Verwaltung einer zentralisierten Datenbank nicht erforderlich ist, z. b. in einer lokalen Inventur Lösung, die nur auf einem einzelnen Computer verwendet wird.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="import-the-database-file-into-a-project"></a>Importieren der Datenbankdatei in ein Projekt
 Um die Datenbankdatei in Ihr Projekt zu importieren, verwenden Sie den **Assistenten zum Konfigurieren von Datenquellen** , um auf der Grundlage der Datenbankdatei eine Datenquelle zu erstellen. Der Assistent fügt dem Projekt die Datenbankdatei und ein typisiertes Dataset hinzu.

## <a name="deploy-the-database-file"></a>Bereitstellen der Datenbankdatei
 Der **Assistent zum Konfigurieren von Datenquellen** verwendet einen relativen Pfad zum Erstellen von Verbindungen mit der lokalen Datenbankdatei. Dies ermöglicht es Ihnen, die Projekt Mappe von einem Computer auf einen anderen zu kopieren, wenn Sie die relativen Positionen der Dateien beibehalten.

 Wenn Sie die Lösung auf einem Server bereitstellen und dann das Dokument an jeden Endbenutzer verteilen, müssen Sie die Datenbankdatei auch manuell verteilen und in Relation zum Dokument an derselben Position installieren. Dies bedeutet, dass der Endbenutzer das Dokument nicht an einen neuen Speicherort auf seinem Computer verschieben kann, es sei denn, er verschiebt auch die Datenbankdatei.

## <a name="local-database-files-and-caching-the-dataset"></a>Lokale Datenbankdateien und Zwischenspeichern des Datasets
 In Projektmappen auf Dokument Ebene für Microsoft Office Excel und Microsoft Office Word können Sie Datasets im Dokument zwischenspeichern, indem Sie die Datasetinstanz mit dem-Attribut markieren <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> . Wenn Sie die Datenbankdatei mithilfe des Assistenten zum Konfigurieren von **Datenquellen** zu Ihrem Projekt hinzufügen, wird dem Projekt automatisch ein typisiertes DataSet hinzugefügt. Es ist nur selten erforderlich, <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> auf dieses DataSet anzuwenden, da die Daten auf dem Computer des Benutzers bereits lokal vorhanden sind. Weitere Informationen finden Sie unter zwischen [Speichern von Daten](../vsto/caching-data.md).

## <a name="see-also"></a>Weitere Informationen
- [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Gewusst wie: Auffüllen von Dokumenten mit Daten aus einer Datenbank](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Vorgehensweise: Aktualisieren einer Datenquelle mit Daten eines Host Steuer Elements](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Bereitstellen einer Office-Projekt Mappe](../vsto/deploying-an-office-solution.md)
- [Daten zwischenspeichern](../vsto/caching-data.md)
