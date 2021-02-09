---
title: 'Vorgehensweise: Hinzufügen einer bestimmten Finder-Methode | Microsoft-Dokumentation'
description: Sie erhalten eine Entitäts Instanz durch Hinzufügen einer Finder-Methode. Der BDC-Dienst ruft die-Methode auf, wenn ein Benutzer eine Entität in einem Geschäftsdaten-Webpart oder einer externen Liste auswählt.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], Specific Finder
- BDC [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], get an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], Specific Finder
- Business Data Connectivity service [SharePoint development in Visual Studio], get an entity
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 237cd28bffece4517e80b979602ac8d2ed357aa2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882686"
---
# <a name="how-to-add-a-specific-finder-method"></a>Gewusst wie: Hinzufügen einer bestimmten Finder-Methode
  Sie können eine einzelne Entitäts Instanz zurückgeben, indem Sie eine *bestimmte Finder* -Methode erstellen. Der Business Data Connectivity (BDC)-Dienst führt die spezifische Finder-Methode aus, wenn ein Benutzer eine Entität in einem Geschäftsdaten-Webpart oder einer externen Liste auswählt. Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-specific-finder-method"></a>So erstellen Sie eine bestimmte Finder-Methode

1. Wählen Sie im **BDC-Designer** eine Entität aus.

    Weitere Informationen zum Hinzufügen einer Entität zum **BDC-Designer** in Visual Studio finden Sie unter Gewusst [wie: Hinzufügen einer Entität zu einem Modell](../sharepoint/how-to-add-an-entity-to-a-model.md).

2. Wählen Sie in der Menüleiste die Option  >  **Weitere Fenster** anzeigen, **Details der BDC-Methode** aus.

    Das Fenster **BDC-Methoden Details** wird geöffnet. Weitere Informationen zu diesem Fenster finden Sie unter [Übersicht über die Entwurfs Tools für BDC-Modelle](../sharepoint/bdc-model-design-tools-overview.md).

3. Wählen Sie in der Liste **Methode hinzufügen** die Option **spezifische Finder-Methode erstellen** aus.

    Visual Studio fügt dem Modell die folgenden Elemente hinzu. Diese Elemente werden im Fenster **Details der BDC-Methode** angezeigt.

   - eine Methode

   - Ein Eingabeparameter für die Methode.

   - Ein Rückgabe Parameter für die Methode.

   - Ein Typdeskriptor für jeden Parameter.

   - Eine Methoden Instanz für die Methode.

     Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).

4. Öffnen Sie das Visual Studio- **Eigenschaften** Fenster.

5. Konfigurieren Sie den Typdeskriptor des Rückgabe Parameters als Entitätstyp Deskriptor. Weitere Informationen zum Erstellen eines Entitäts Typen Deskriptors finden Sie unter Gewusst [wie: Definieren des Typdeskriptors für einen Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

   > [!NOTE]
   > Sie müssen diesen Schritt nicht ausführen, wenn Sie der Entität eine Finder-Methode hinzugefügt haben. Visual Studio verwendet den Typdeskriptor, den Sie in der Finder-Methode definiert haben.

   > [!NOTE]
   > Wenn das Bezeichnerfeld des Entitäts Typs ein Feld in einer Datenbanktabelle darstellt, das automatisch generiert wird, legen **Sie** die schreibgeschützte Eigenschaft des Bezeichnerfelds auf **true** fest.

6. Wählen Sie im Fenster " **Methoden Details** " die Methoden Instanz der Methode aus.

7. Legen Sie im **Eigenschaften Fenster** die Eigenschaft **Name des Rückgabe Parameters** auf den Namen des Rückgabe Parameters der Methode fest. Weitere Informationen zu Methoden Instanzeigenschaften finden Sie unter [MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)).

8. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü der Dienst Code Datei, die für die Entität generiert wurde, und wählen Sie dann **Code anzeigen** aus.

    Die Entitäts Dienst-Codedatei wird im Code-Editor geöffnet. Weitere Informationen zur Entitäts Dienst-Codedatei finden Sie unter [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md).

9. Fügen Sie der spezifischen Finder-Methode Code hinzu. Mit diesem Code werden die folgenden Aufgaben durchgeführt:

   - Ruft einen Datensatz aus einer Datenquelle ab.

   - Gibt eine Entität an den BDC-Dienst zurück.

     Im folgenden Beispiel wird ein Kontakt aus der AdventureWorks-Beispieldatenbank für SQL Server zurückgegeben.

     > [!NOTE]
     > Ersetzen Sie den Wert des `ServerName` Felds durch den Namen des Servers.

     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]

## <a name="see-also"></a>Weitere Informationen
- [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Gewusst wie: Hinzufügen einer Finder-Methode](../sharepoint/how-to-add-a-finder-method.md)
- [Gewusst wie: Hinzufügen einer Creator-Methode](../sharepoint/how-to-add-a-creator-method.md)
- [Gewusst wie: Hinzufügen einer Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md)
- [Gewusst wie: Hinzufügen einer Updater-Methode](../sharepoint/how-to-add-an-updater-method.md)
- [Übersicht über die BDC-Modell Entwurfs Tools](../sharepoint/bdc-model-design-tools-overview.md)
- [Gewusst wie: Hinzufügen eines Parameters zu einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Gewusst wie: Definieren einer Methoden Instanz](../sharepoint/how-to-define-a-method-instance.md)
