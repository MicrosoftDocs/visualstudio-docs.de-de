---
title: Erstellen einer externen Liste in SharePoint mithilfe von Geschäftsdaten
description: Erstellen Sie ein Modell für den BDC-Dienst, das Informationen zu Kontakten in einer Geschäftsdatenbank zurückgibt, und erstellen Sie dann mithilfe dieses Modells eine externe Liste in SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], business data in a Web Part
- BDC [SharePoint development in Visual Studio], external list
- Business Data Connectivity service [SharePoint development in Visual Studio], business data in a SharePoint list
- BDC [SharePoint development in Visual Studio], business data in a SharePoint list
- BDC [SharePoint development in Visual Studio], business data in a Web Part
- BDC [SharePoint development in Visual Studio], entity backed list
- Business Data Connectivity service [SharePoint development in Visual Studio], entity backed list
- Business Data Connectivity service [SharePoint development in Visual Studio], external list
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a791f94e46e16369392465e075ade92a833e2868
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915335"
---
# <a name="walkthrough-create-an-external-list-in-sharepoint-by-using-business-data"></a>Exemplarische Vorgehensweise: Erstellen einer externen Liste in SharePoint mithilfe von Geschäftsdaten

Der Business Data Connectivity (BDC)-Dienst ermöglicht SharePoint das Anzeigen von Geschäftsdaten aus Back-End-Server Anwendungen, Webdiensten und Datenbanken.

In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie ein Modell für den BDC-Dienst erstellen, der Informationen zu Kontakten in einer Beispieldatenbank zurückgibt. Anschließend erstellen Sie eine externe Liste in SharePoint mithilfe dieses Modells.

In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Erstellen eines Projekts.
- Hinzufügen einer Entität zum Modell.
- Hinzufügen einer Finder-Methode.
- Hinzufügen einer bestimmten Finder-Methode.
- Testen des Projekts.

## <a name="prerequisites"></a>Voraussetzungen

Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- Unterstützte Editionen von Windows und SharePoint.

- Zugriff auf die AdventureWorks-Beispieldatenbank. Weitere Informationen zum Installieren der AdventureWorks-Datenbank finden Sie unter [SQL Server-Beispiel Datenbanken](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).

## <a name="create-a-project-that-contains-a-bdc-model"></a>Erstellen eines Projekts, das ein BDC-Modell enthält

1. Wählen Sie in Visual Studio auf der Menüleiste **Datei**  >  **neu**  >  **Projekt** aus.

     Das Dialogfeld **Neues Projekt** wird angezeigt.

2. Erweitern Sie unter **Visual c#** oder **Visual Basic** den Knoten **SharePoint** , und wählen Sie dann das Element **2010** aus.

3. Wählen Sie im Bereich **Vorlagen** die Option **SharePoint 2010-Projekt** aus, benennen Sie das Projekt **adventureworkstest**, und wählen Sie dann die Schaltfläche **OK** aus.

     Der Assistent zum Anpassen von **SharePoint** wird angezeigt. In diesem Assistenten können Sie die Website angeben, mit der Sie das Projekt Debuggen und die Vertrauens Ebene der Projekt Mappe festlegen.

4. Wählen Sie das Optionsfeld **als Farm Lösung** bereitstellen aus, um die Vertrauens Ebene festzulegen.

5. Wählen Sie die Schaltfläche **Fertig** stellen, um die standardmäßige lokale SharePoint-Website zu akzeptieren

6. Wählen Sie in **Projektmappen-Explorer** den SharePoint-Projekt Knoten aus.

7. Wählen Sie in der Menüleiste **Projekt** > **Neues Element hinzufügen** aus.

     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.

8. Wählen Sie im Bereich **Vorlagen** die **Option Business Data Connectivity-Modell (nur Farm Lösung)** aus, benennen Sie das Projekt **adventureworkscontacts**, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.

## <a name="add-data-access-classes-to-the-project"></a>Hinzufügen von Datenzugriffsklassen zum Projekt

1. Wählen Sie in der Menüleiste **Tools**  >  **Verbindung mit Datenbank herstellen** aus.

     Das Dialogfeld **Verbindung hinzufügen** wird geöffnet.

2. Fügen Sie eine Verbindung mit der SQL Server AdventureWorks-Beispieldatenbank hinzu.

     Weitere Informationen finden Sie unter [Add/Modify Connection (Microsoft SQL Server)](/previous-versions/dxb6fxah(v=vs.140)).

3. Wählen Sie im **Projektmappen-Explorer** den Projektknoten aus.

4. Wählen Sie in der Menüleiste **Projekt** > **Neues Element hinzufügen** aus.

5. Wählen Sie im Bereich **installierte Vorlagen** den Knoten **Daten** aus.

6. Wählen Sie im Bereich **Vorlagen** die Option **LINQ to SQL Klassen** aus.

7. Geben Sie im Feld **Name den Namen** **AdventureWorks** an, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.

     Dem Projekt wird eine DBML-Datei hinzugefügt, und der objektrelationaler Designer (O/R-Designer) wird geöffnet.

8. Wählen Sie in der Menüleiste **View**  >  **Server-Explorer** anzeigen aus.

9. Erweitern Sie in **Server-Explorer** den Knoten, der die AdventureWorks-Beispieldatenbank darstellt, und erweitern Sie dann den Knoten **Tabellen** .

10. Fügen Sie die Tabelle **Contact (Person)** dem O/R-Designer hinzu.

     Eine Entitätsklasse wird erstellt und auf der Entwurfsoberfläche angezeigt. Die Entitäts Klasse verfügt über Eigenschaften, die den Spalten in der Contact-Tabelle (Person) zugeordnet sind.

## <a name="remove-the-default-entity-from-the-bdc-model"></a>Entfernen der Standard Entität aus dem BDC-Modell

Das **Business Data Connectivity-Modell** Projekt fügt dem Modell eine Standard Entität mit dem Namen Entity1 hinzu. Entfernen Sie diese Entität. Später fügen Sie eine neue Entität hinzu. Beginnend mit einem leeren Modell verringert sich die Anzahl der Schritte, die zum Durchführen der exemplarischen Vorgehensweise erforderlich sind.

1. Erweitern Sie in **Projektmappen-Explorer** den Knoten **BdcModel1** , und öffnen Sie dann die Datei *BdcModel1. bdcm* .

2. Die Datei für das Business Data Connectivity-Modell wird im BDC-Designer geöffnet.

3. Öffnen Sie im Designer das Kontextmenü für **Entity1**, und wählen Sie dann **Löschen** aus.

4. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für *Entity1. vb* (in Visual Basic) oder *Entity1.cs* (in c#), und wählen Sie dann **Löschen** aus.

5. Öffnen Sie das Kontextmenü für *Entity1Service. vb* (in Visual Basic) oder *Entity1Service.cs* (in c#), und wählen Sie dann **Löschen** aus.

## <a name="add-an-entity-to-the-model"></a>Hinzufügen einer Entität zum Modell

Fügen Sie dem Modell eine Entität hinzu. Sie können Entitäten aus der Visual Studio- **Toolbox** auf den BDC-Designer hinzufügen.

1. Wählen Sie in der Menüleiste **View**  >  **Toolbox** anzeigen aus.

2. Fügen Sie auf der Registerkarte **BusinessDataConnectivity** der **Toolbox** eine **Entität** in den BDC-Designer ein.

     Die neue Entität wird im Designer angezeigt. Visual Studio fügt dem Projekt eine Datei mit dem Namen *entityservice. vb* (in Visual Basic) oder *EntityService.cs* (in c#) hinzu.

3. Wählen Sie in der Menüleiste **Ansicht**  >  **Eigenschaften**  >  **Fenster** aus.

4. Legen Sie im Fenster **Eigenschaften** den **Name** -Eigenschafts Wert auf **Contact** fest.

5. Öffnen Sie im Designer das Kontextmenü für die Entität, wählen Sie **Hinzufügen** aus, und wählen Sie dann **Bezeichner** aus.

     In der Entität wird ein neuer Bezeichner angezeigt.

6. Ändern Sie im Fenster **Eigenschaften** den Namen des Bezeichners in **ContactID**.

7. Wählen Sie in der Liste **Typname** die Option **System. Int32** aus.

## <a name="add-a-specific-finder-method"></a>Hinzufügen einer bestimmten Finder-Methode

Um den BDC-Dienst zum Anzeigen eines bestimmten Kontakts zu aktivieren, müssen Sie eine bestimmte Finder-Methode hinzufügen. Der BDC-Dienst ruft die spezifische Finder-Methode auf, wenn ein Benutzer ein Element in einer Liste auswählt und dann im Menüband die Schaltfläche **Element anzeigen** auswählt.

Fügen Sie der Entität "Contact" mithilfe des Fensters " **BDC-Methoden Details** " eine bestimmte Finder-Methode hinzu. Fügen Sie der-Methode Code hinzu, um eine bestimmte Entität zurückzugeben.

1. Wählen Sie im BDC-Designer die **Contact** -Entität aus.

2. Wählen Sie in der Menüleiste **View**  >  **andere Windows**-  >  **BDC-Methoden Details** anzeigen aus.

     Das Fenster BDC-Methoden Details wird geöffnet.

3. Wählen Sie in der Liste **Methode hinzufügen** die Option **spezifische Finder-Methode erstellen** aus.

     Visual Studio fügt dem Modell die folgenden Elemente hinzu. Diese Elemente werden im Fenster **Details der BDC-Methode** angezeigt.

    - Eine Methode mit dem Namen "ReadItem".

    - Ein Eingabeparameter für die Methode.

    - Ein Rückgabe Parameter für die Methode.

    - Ein Typdeskriptor für jeden Parameter.

    - Eine Methoden Instanz für die Methode.

4. Öffnen Sie im Fenster **BDC-Methoden Details** die Liste, die für den **Kontakttyp** Deskriptor angezeigt wird, und wählen Sie dann **Bearbeiten** aus.

     Der **BDC-Explorer** wird geöffnet und bietet eine hierarchische Ansicht des Modells.

5. Öffnen Sie im Fenster **Eigenschaften** die Liste neben der Eigenschaft **tykame** , wählen Sie die Registerkarte **Aktuelles Projekt** aus, und wählen Sie dann die Eigenschaft **Contact** aus.

6. Öffnen Sie im **BDC-Explorer** das Kontextmenü des **Kontakts**, und wählen Sie dann **Typdeskriptor hinzufügen** aus.

     Ein neuer Typdeskriptor mit dem Namen **TypeDescriptor1** wird im **BDC-Explorer** angezeigt.

7. Legen Sie im Fenster **Eigenschaften** den **Name** -Eigenschafts Wert auf **ContactID** fest.

8. Öffnen Sie die Liste neben der **typame** -Eigenschaft, und wählen Sie dann **Int32** aus.

9. Öffnen Sie die Liste neben der Eigenschaft **Bezeichner** , und wählen Sie dann **ContactID** aus.

10. Wiederholen Sie Schritt 6, um einen Typdeskriptor für jedes der folgenden Felder zu erstellen.

    |Name|Typname|
    |----------|---------------|
    |FirstName|System.String|
    |LastName|System.String|
    |Phone|System.String|
    |EmailAddress|System.String|
    |EmailPromotion|System.Int32|
    |NameStyle|System.Boolean|
    |PasswordHash|System.String|
    |PasswordSalt|System.String|

11. Öffnen Sie im BDC-Designer in der **Contact** -Entität die **ReadItem** -Methode.

     Die Contact Service-Codedatei wird im Code-Editor geöffnet.

12. Ersetzen Sie in der- `ContactService` Klasse die- `ReadItem` Methode durch den folgenden Code. Mit diesem Code werden die folgenden Aufgaben durchgeführt:

    - Ruft einen Datensatz aus der Contact-Tabelle der AdventureWorks-Datenbank ab.

    - Gibt eine Contact-Entität an den BDC-Dienst zurück.

    > [!NOTE]
    > Ersetzen Sie den Wert des `ServerName` Felds durch den Namen des Servers.

     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]

## <a name="add-a-finder-method"></a>Hinzufügen einer Finder-Methode

Damit der BDC-Dienst die Kontakte in einer Liste anzeigen kann, müssen Sie eine Finder-Methode hinzufügen. Fügen Sie der Entität "Contact" mithilfe des Fensters " **BDC-Methoden Details** " eine Finder-Methode hinzu. Fügen Sie der-Methode Code hinzu, um eine Auflistung von Entitäten an den BDC-Dienst zurückzugeben.

1. Wählen Sie im BDC-Designer die **Contact** -Entität aus.

2. Reduzieren Sie im Fenster **BDC-Methoden Details** den Knoten **ReadItem** .

3. Wählen Sie in der Liste **Methode hinzufügen** unter der Methode "read **List** " die Option **Finder-Methode erstellen** aus.

     Visual Studio fügt eine Methode, einen Rückgabe Parameter und einen Typdeskriptor hinzu.

4. Öffnen Sie im BDC-Designer in der Entität " **Contact** " die Methode "read **List** ".

     Die Codedatei für den Contact-Dienst wird im Code-Editor geöffnet.

5. Ersetzen Sie in der- `ContactService` Klasse die- `ReadList` Methode durch den folgenden Code. Mit diesem Code werden die folgenden Aufgaben durchgeführt:

   - Ruft Daten aus der Contact-Tabelle der AdventureWorks-Datenbank ab.

   - Gibt eine Liste von Contact-Entitäten an den BDC-Dienst zurück.

     > [!NOTE]
     > Ersetzen Sie den Wert des `ServerName` Felds durch den Namen des Servers.

     [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]

## <a name="test-the-project"></a>Testen des Projekts

Wenn Sie das Projekt ausführen, wird die SharePoint-Website geöffnet, und Visual Studio fügt ihr Modell dem Business Data Connectivity-Dienst hinzu. Erstellen Sie eine externe Liste in SharePoint, die auf die Contact-Entität verweist. Die Daten für Kontakte in der AdventureWorks-Datenbank werden in der Liste angezeigt.

> [!NOTE]
> Möglicherweise müssen Sie Ihre Sicherheitseinstellungen in SharePoint ändern, bevor Sie Ihre Lösung Debuggen können. Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).

1. Drücken Sie die Taste **F5**.

     Die SharePoint-Website wird geöffnet.

2. Wählen Sie im Menü **Website Aktionen** den Befehl **Weitere Optionen** aus.

3. Wählen Sie auf der Seite **Erstellen** die Vorlage **externe Liste** aus, und klicken Sie dann auf die Schaltfläche **Erstellen** .

4. Nennen Sie die benutzerdefinierte Liste **Kontakte**.

5. Wählen Sie die Schaltfläche Durchsuchen neben dem Feld **externer Inhaltstyp** aus.

6. Wählen Sie im Dialogfeld **externe Inhaltstyp** Auswahl das Element **adventureworkscontacts. BdcModel1. Contact** aus, und wählen Sie dann die Schaltfläche **Erstellen** aus.

     SharePoint erstellt eine externe Liste, die Kontakte aus der AdventureWorks-Beispieldatenbank enthält.

7. Um die spezifische Finder-Methode zu testen, wählen Sie einen Kontakt in der Liste aus.

8. Wählen Sie im Menüband die Registerkarte **Elemente** aus, und wählen Sie dann den Befehl **Element anzeigen** aus.

     Die Details des ausgewählten Kontakts werden in einem Formular angezeigt.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Entwerfen von Modellen für den BDC-Dienst in SharePoint finden Sie in den folgenden Themen:

- Gewusst [wie: Hinzufügen einer Creator-Methode](../sharepoint/how-to-add-a-creator-method.md)
- Gewusst [wie: Hinzufügen einer Updater-Methode](../sharepoint/how-to-add-an-updater-method.md)
- Gewusst [wie: Hinzufügen einer Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md)

## <a name="see-also"></a>Weitere Informationen

[Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md) 
 [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md) 
 [Übersicht über](../sharepoint/bdc-model-design-tools-overview.md) 
 die BDC-Modell Entwurfs Tools [Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)