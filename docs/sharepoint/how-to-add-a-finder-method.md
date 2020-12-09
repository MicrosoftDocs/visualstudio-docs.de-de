---
title: 'Vorgehensweise: Hinzufügen einer Finder-Methode | Microsoft-Dokumentation'
description: Fügen Sie in Visual Studio eine Finder-Methode hinzu, mit der der Business Data Connectivity (BDC)-Dienst eine Liste von Entitäten in einem SharePoint-Webpart oder einer SharePoint-Liste anzeigen kann.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], get entities
- Business Data Connectivity service [SharePoint development in Visual Studio], return entities
- BDC [SharePoint development in Visual Studio], return entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Finder method
- Business Data Connectivity service [SharePoint development in Visual Studio], get entities
- BDC [SharePoint development in Visual Studio], Finder method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b7e2bb74278194878ed4496c12c918707cdc1e6e
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915088"
---
# <a name="how-to-add-a-finder-method"></a>Gewusst wie: Hinzufügen einer Finder-Methode
  Um den BDC-Dienst (Business Data Connectivity) zum Anzeigen einer Liste von Entitäten in einem Webpart oder einer Liste zu aktivieren, müssen Sie eine *Finder* -Methode erstellen. Eine Finder-Methode ist eine spezielle Methode, die eine Auflistung von Entitäts Instanzen zurückgibt. Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-finder-method"></a>So erstellen Sie eine Finder-Methode

1. Wählen Sie im **BDC-Designer** eine Entität aus.

    Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen einer Entität zu einem Modell](../sharepoint/how-to-add-an-entity-to-a-model.md).

2. Wählen Sie in der Menüleiste **View**  >  **andere Windows**-  >  **BDC-Methoden Details** anzeigen aus.

    Das Fenster **BDC-Methoden Details** wird geöffnet. Weitere Informationen zum Details-Fenster der **BDC-Methode** finden Sie unter Übersicht über die [BDC-Modell Entwurfs Tools](../sharepoint/bdc-model-design-tools-overview.md).

3. Wählen Sie in der Liste **Methode hinzufügen** die Option **Finder-Methode erstellen** aus.

    Visual Studio fügt eine Methode, einen Rückgabe Parameter und einen Typdeskriptor hinzu.

4. Konfigurieren Sie den Typdeskriptor als einen entitätsammlungstyp-Deskriptor. Weitere Informationen zum Erstellen eines Deskriptors für den entitätsammlungstyp finden Sie unter Gewusst [wie: Definieren des Typdeskriptors für einen Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

   > [!NOTE]
   > Sie müssen diesen Schritt nicht ausführen, wenn Sie der Entität eine bestimmte Finder-Methode hinzugefügt haben. Visual Studio verwendet den Typdeskriptor, den Sie in der spezifischen Finder-Methode definiert haben.

5. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü der Dienst Code Datei, die für die Entität generiert wurde, und wählen Sie dann **Code anzeigen** aus. Weitere Informationen zur Dienst Code Datei finden Sie unter [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md).

6. Fügen Sie der Finder-Methode Code hinzu. Mit diesem Code werden die folgenden Aufgaben durchgeführt:

   - Ruft Daten aus einer Datenquelle ab.

   - Gibt eine Liste von Entitäten für den BDC-Dienst zurück.

     Im folgenden Beispiel wird eine Auflistung von `Contact` Entitäten zurückgegeben, indem Daten aus der AdventureWorks-Beispieldatenbank für SQL Server verwendet werden.

   > [!NOTE]
   > Ersetzen Sie den Wert des `ServerName` Felds durch den Namen des Servers.

    [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
    [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]

## <a name="see-also"></a>Weitere Informationen
- [Übersicht über die BDC-Modell Entwurfs Tools](../sharepoint/bdc-model-design-tools-overview.md)
- [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Gewusst wie: Hinzufügen einer bestimmten Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Gewusst wie: Hinzufügen einer Creator-Methode](../sharepoint/how-to-add-a-creator-method.md)
- [Gewusst wie: Hinzufügen einer Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md)
- [Gewusst wie: Hinzufügen einer Updater-Methode](../sharepoint/how-to-add-an-updater-method.md)
- [Gewusst wie: Hinzufügen eines Parameters zu einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Gewusst wie: Definieren einer Methoden Instanz](../sharepoint/how-to-define-a-method-instance.md)
