---
title: Erstellen eines Business Data Connectivity-Modells | Microsoft-Dokumentation
description: Erstellen Sie ein Business Data Connectivity-Modell (BDC), oder passen Sie ein vorhandenes BDC-Modell mithilfe von Visual Studio an. Jedes SharePoint-Projekt kann nur ein Modell enthalten.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], model
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- SharePoint development in Visual Studio, Business Data Connectivity service
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0486ce6ac53850b1b607f9e7f859806cdc3ef8fe
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850467"
---
# <a name="create-a-business-data-connectivity-model"></a>Erstellen eines Business Data Connectivity-Modells
  Sie können ein BDC-Modell (Business Data Connectivity) erstellen oder ein vorhandenes BDC-Modell mithilfe von Visual Studio anpassen. Jedes SharePoint-Projekt kann nur ein Modell enthalten. Weitere Informationen finden Sie unter [integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).

## <a name="create-a-new-model"></a>Erstellen Sie ein neues Modell.
 Um ein neues Modell zu erstellen, erstellen Sie ein **Business Data Connectivity-Modell** Projekt, oder fügen Sie ein **Business Data Connectivity-Modell** Element zu einem **leeren SharePoint-Projekt** hinzu.

> [!NOTE]
> Sie müssen [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] auf dem Computer installiert haben.

 Visual Studio fügt dem Projekt einen Ordner hinzu. Dieser Ordner enthält den Namen, den Sie im Dialogfeld **Neues Element hinzufügen** für das Element **Business Data Connectivity-Modell** angeben. Wenn Sie ein neues Projekt für den **Business Data Connectivity-Modell** erstellen, benennt Visual Studio den Ordner **BdcModel1**.

 Visual Studio fügt die folgenden Dateien in den neuen Ordner ein:

|Datei|BESCHREIBUNG|
|----------|-----------------|
|Modell Definitionsdatei|Enthält XML, das die Entitäten, Methoden, Line-of-Business (LOB)-Systemobjekte und andere Metadaten definiert, die das Modell beschreiben.<br /><br /> Ändern Sie die Metadaten in dieser Datei, indem Sie den BDC-Designer, den **BDC-Explorer**, das **BDC-Methoden Details** -Fenster und das **Eigenschaften** Fenster verwenden.|
|Entitäts Dienst-Codedatei|Enthält Methoden, die Instanzen der Standard Entität abrufen, aktualisieren und löschen.|

 Um die Eigenschaften einer Entität zu definieren, bearbeiten Sie die Entitäts Code Datei. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen einer Entität zu einem Modell](../sharepoint/how-to-add-an-entity-to-a-model.md).

 Um Instanzen einer Entität abzurufen, zu aktualisieren und zu löschen, fügen Sie der Entitäts Dienst-Codedatei Code hinzu. Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).

 Wenn Sie das Projekt kompilieren, erstellt Visual Studio eine Assembly. Stellen Sie sicher, dass Sie dem Projekt keine weiteren Elemente hinzufügen, die der Projektassembly Code hinzufügen (z. b. ein **sequenzielles Workflow** Element oder ein **Webpartelement** ). Der Code für dieses Element wird nicht ausgeführt, wenn Sie die Lösung bereitstellen, da das Projektmappenpaket die Assembly nicht in den globalen Assemblycache kopiert.  Das Lösungspaket stellt die Assembly nur in der BDC-Datenbank in SharePoint bereit.

> [!NOTE]
> Visual Studio kopiert die Assembly an beide Speicherorte auf dem lokalen Computer, wenn Sie das Projekt Debuggen.

## <a name="add-an-existing-model"></a>Vorhandenes Modell hinzufügen
 Sie können ein Modell importieren, das mit anderen Tools wie SharePoint Designer erstellt wurde. In den folgenden Situationen können Sie ein vorhandenes Modell in das Projekt importieren:

- Zum Anpassen eines Modells, das bereits in einer SharePoint-Serverfarm bereitgestellt wurde.

- Zum Packen und Bereitstellen eines vorhandenen Modells in mehreren SharePoint-Serverfarmen.

  In beiden Fällen sind die in dem Modell definierten LOB-Systeme, die Sie importieren, nicht betroffen und funktionieren weiterhin wie erwartet. Wenn Sie einem SharePoint-Projekt ein vorhandenes Modell hinzufügen möchten, verwenden Sie das Visual Studio-Dialogfeld **Vorhandenes Element hinzufügen** . Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen einer vorhandenen BDC-Modelldatei zu einem SharePoint-Projekt](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md).

  Sie können dem importierten Modell ein Branchen System vom Typ .NET Framework-Assembly hinzufügen, indem Sie im **Add .NET Assembly LobSystem** eine Option auswählen. Dies ermöglicht es Ihnen, benutzerdefinierten Code zu schreiben und einen Designer zu verwenden, um die Metadaten für das importierte Modell zu definieren.

## <a name="related-topics"></a>Verwandte Themen

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[Vorgehensweise: Erstellen eines BDC-Modells](../sharepoint/how-to-create-a-bdc-model.md)|Zeigt, wie ein neues BDC-Modell erstellt wird.|
|[How to: Hinzufügen einer vorhandenen BDC-Modelldatei zu einem SharePoint-Projekt](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)|Zeigt, wie Sie ein vorhandenes Modell in ein SharePoint-Projekt importieren.|
|[How to: Angeben von lokalisierten Namen, Eigenschaften und Berechtigungen mithilfe einer Ressourcendatei](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)|Beschreibt, wie Zeichen folgen bereitgestellt werden, die mit Modell Metadaten zusammengeführt werden, wenn das Modell von einem Webpart oder einer Webseite verwendet wird.|
|[Vorgehensweise: Einschließen einer benutzerdefinierten Assembly in eine BDC-Funktion](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)|Zeigt, wie Sie eine benutzerdefinierte Assembly in die Funktion einschließen.|
