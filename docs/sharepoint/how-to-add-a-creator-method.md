---
title: 'Gewusst wie: Hinzufügen einer Creator-Methode | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], Creator
- BDC [SharePoint development in Visual Studio], adding entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entity instances
- BDC [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Creator
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 962e353b5ae82f6dd3eccc2898385fd4b9ee30ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "86017060"
---
# <a name="how-to-add-a-creator-method"></a>Gewusst wie: Hinzufügen einer Creator-Methode
  Eine Creator-Methode fügt der Datenquelle einer Entität neue Daten hinzu. Der Business Data Connectivity (BDC)-Dienst ruft diese Methode auf, wenn Benutzer die Schaltfläche **Neues Element** auf dem **Menüband** einer Liste auswählen, die auf dem Modell basiert. Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-add-a-creator-method"></a>So fügen Sie eine Creator-Methode hinzu

1. Wählen Sie im **BDC-Designer**eine Entität aus.

2. Wählen Sie in der Menüleiste **View**  >  **andere Windows**-  > **BDC-Methoden Details**anzeigen aus.

    Das Fenster **BDC-Methoden Details** wird geöffnet. Weitere Informationen zu diesem Fenster finden Sie unter [Übersicht über die Entwurfs Tools für BDC-Modelle](../sharepoint/bdc-model-design-tools-overview.md).

3. Wählen Sie in der Liste **Methode hinzufügen** die Option **Create Creator-Methode**aus.

    Visual Studio fügt dem Modell die folgenden Elemente hinzu, und diese Elemente werden im Fenster " **BDC-Methoden Details** " angezeigt.

   - Eine Methode mit dem Namen **Create**.

   - Ein Eingabeparameter für die Methode.

   - Ein Rückgabe Parameter für die Methode.

   - Typdeskriptoren für die Parameter.

   - Eine Methoden Instanz für die Methode.

     Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).

4. Öffnen Sie in **Projektmappen-Explorer**das Kontextmenü der Dienst Code Datei, die für die Entität generiert wurde, und wählen Sie dann **Code anzeigen**aus.

    Die Entitäts Dienst-Codedatei wird im Code-Editor geöffnet. Weitere Informationen zur Entitäts Dienst-Codedatei finden Sie unter [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md).

5. Fügen Sie der Ersteller-Methode Code hinzu, der der Datenquelle Daten hinzufügt. Im folgenden Beispiel wird ein Kontakt zur AdventureWorks-Beispieldatenbank für SQL Server hinzugefügt.

   > [!NOTE]
   > Ersetzen Sie den Wert des `ServerName` Felds durch den Namen des Servers.

    [!code-csharp[SP_BDC#4](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#4)]
    [!code-vb[SP_BDC#4](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#4)]

## <a name="see-also"></a>Weitere Informationen
- [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Gewusst wie: Hinzufügen einer Finder-Methode](../sharepoint/how-to-add-a-finder-method.md)
- [Gewusst wie: Hinzufügen einer bestimmten Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Gewusst wie: Hinzufügen einer Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md)
- [Gewusst wie: Hinzufügen einer Updater-Methode](../sharepoint/how-to-add-an-updater-method.md)
- [Übersicht über die BDC-Modell Entwurfs Tools](../sharepoint/bdc-model-design-tools-overview.md)
- [Gewusst wie: Hinzufügen eines Parameters zu einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Gewusst wie: Definieren einer Methoden Instanz](../sharepoint/how-to-define-a-method-instance.md)
