---
title: 'Vorgehensweise: Hinzufügen einer Updater-Methode | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie es Benutzern ermöglichen, Geschäftsdaten in einer externen SharePoint-Liste zu aktualisieren, indem Sie eine Updater-Methode hinzufügen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], updating data
- BDC [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating data
- Business Data Connectivity service [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating entity instances
- BDC [SharePoint development in Visual Studio], updating entity instances
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9d06737de7df40efa2bc6259cc0ea53bdda17b8c
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915374"
---
# <a name="how-to-add-an-updater-method"></a>Gewusst wie: Hinzufügen einer Updater-Methode
  Sie können es Benutzern ermöglichen, Geschäftsdaten in einer externen SharePoint-Liste zu aktualisieren, indem Sie eine *Updater* -Methode erstellen. Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-an-updater-method"></a>So erstellen Sie eine Updater-Methode

1. Wählen Sie im BDC-Designer eine Entität aus.

2. Wählen Sie in der Menüleiste **View**  >  **andere Windows**-  >  **BDC-Methoden Details** anzeigen aus.

    Das Fenster BDC-Methoden Details wird geöffnet. Weitere Informationen zu diesem Fenster finden Sie unter [Übersicht über die BDC-Modell Entwurfs Tools](../sharepoint/bdc-model-design-tools-overview.md).

3. Wählen Sie in der Liste **Methode hinzufügen** die Option **Updater-Methode erstellen** aus.

    Visual Studio fügt dem Modell die folgenden Elemente hinzu. Diese Elemente werden im Fenster Details der BDC-Methode angezeigt.

   - Eine Methode mit dem Namen " **Update**".

   - Ein Eingabeparameter für die Methode.

   - Ein Typdeskriptor für den Parameter. Standardmäßig verwendet Visual Studio den Entitätstyp Deskriptor, den Sie für die Finder-Methode definiert haben (z. b. Contact).

   - Eine Methoden Instanz für die Methode.

     Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).

   > [!NOTE]
   > Wenn der Bezeichner des Entitäts Typs ein Feld in einer Datenbanktabelle darstellt, das nicht automatisch generiert wird, legen Sie die Eigenschaft **Pre-Updater Field** auf **true** fest.

4. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü der Dienst Code Datei, die für die Entität generiert wurde, und wählen Sie dann **Code anzeigen** aus.

    Die Entitäts Dienst-Codedatei wird im **Code-Editor** geöffnet. Weitere Informationen zu dieser Datei finden Sie unter [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md).

5. Fügen Sie der Update-Methode Code hinzu, um Daten zu aktualisieren. Im folgenden Beispiel werden Informationen für einen Kontakt in der AdventureWorks-Beispieldatenbank für SQL Server aktualisiert.

   > [!NOTE]
   > Ersetzen Sie den Wert des `ServerName` Felds durch den Namen des Servers.

    [!code-csharp[SP_BDC#5](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#5)]
    [!code-vb[SP_BDC#5](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#5)]

## <a name="see-also"></a>Weitere Informationen
- [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Gewusst wie: Hinzufügen einer Finder-Methode](../sharepoint/how-to-add-a-finder-method.md)
- [Gewusst wie: Hinzufügen einer bestimmten Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Gewusst wie: Hinzufügen einer Creator-Methode](../sharepoint/how-to-add-a-creator-method.md)
- [Gewusst wie: Hinzufügen einer Updater-Methode](../sharepoint/how-to-add-an-updater-method.md)
- [Gewusst wie: Hinzufügen einer Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md)
- [Übersicht über die BDC-Modell Entwurfs Tools](../sharepoint/bdc-model-design-tools-overview.md)
- [Gewusst wie: Hinzufügen eines Parameters zu einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Gewusst wie: Definieren einer Methoden Instanz](../sharepoint/how-to-define-a-method-instance.md)
