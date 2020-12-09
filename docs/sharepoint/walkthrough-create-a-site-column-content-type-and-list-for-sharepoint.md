---
title: Erstellen einer Website Spalte, eines Inhaltstyps und einer Liste für SharePoint
titleSuffix: ''
description: In dieser exemplarischen Vorgehensweise erstellen Sie eine benutzerdefinierte Website Spalte (Feld), einen benutzerdefinierten Inhaltstyp, der die Website Spalte verwendet, und eine Liste, die den Inhaltstyp in SharePoint verwendet.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.ListDesigner.GeneralMessageHelp
- Microsoft.VisualStudio.SharePoint.Designers.ListDesigner.ViewModels.ListViewModel.SortingAndGrouping
- VS.SharePointTools.ListDesigner.SortingGrouping
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, list definitions
- SharePoint development in Visual Studio, list instances
- SharePoint development in Visual Studio, fields
- SharePoint development in Visual Studio, content types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b1670dfa3c7202e8ebbdb28396f161daeffac491
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914009"
---
# <a name="walkthrough-create-a-site-column-content-type-and-list-for-sharepoint"></a>Exemplarische Vorgehensweise: Erstellen einer Websitespalte, eines Inhaltstyps und einer Liste für SharePoint
  Die folgenden Verfahren veranschaulichen, wie Sie benutzerdefinierte SharePoint-Website Spalten – oder *Felder*– sowie einen Inhaltstyp erstellen, der die Websites Palten verwendet. Außerdem wird gezeigt, wie eine Liste erstellt wird, in der der neue Inhaltstyp verwendet wird.

 Diese exemplarische Vorgehensweise umfasst die folgenden Aufgaben:

- [Erstellen Sie benutzerdefinierte Website Spalten](#create-custom-site-columns).

- [Erstellen Sie einen benutzerdefinierten Inhaltstyp](#create-a-custom-content-type).

- [Erstellen Sie eine Liste](#create-a-list).

- [Testen Sie die Anwendung](#test-the-application).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- Unterstützte Editionen von Windows und SharePoint.

- [!INCLUDE[vsprvs-current](../sharepoint/includes/vsprvs-current-md.md)]

## <a name="create-custom-site-columns"></a>Erstellen von benutzerdefinierten Websites Palten
 Dieses Beispiel erstellt eine Liste zum Verwalten von Patienten in einem Krankenhaus. Zuerst müssen Sie ein SharePoint-Projekt in Erstellen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] und diesem wie folgt Websites Palten hinzufügen.

#### <a name="to-create-the-project"></a>So erstellen Sie das Projekt

1. Wählen Sie im Menü [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **Datei** die Optionsfolge **Neu** > **Projekt** aus.
::: moniker range="=vs-2017"
2. Erweitern Sie im Dialogfeld **Neues Projekt** unter **Visual c#** oder **Visual Basic** den Knoten **Office/SharePoint** , und wählen Sie dann **SharePoint-Lösungen** aus.

3. Wählen Sie im Bereich **Vorlagen** das **leere SharePoint-Projekt** für die bestimmte Version von SharePoint aus, die Sie installiert haben. Wenn Sie z. b. SharePoint 2016-Installation haben, wählen Sie die **Projektvorlage SharePoint 2016-Empty** aus.  

4. Ändern Sie den Namen des Projekts in **Clinic**, und klicken Sie dann auf die Schaltfläche **OK** .

5. Geben Sie im Dialogfeld **Geben Sie den Standort und die Sicherheitsstufe für das Debuggen** an die URL für die lokale SharePoint-Website ein, der Sie das neue benutzerdefinierte Feld Element hinzufügen möchten, oder verwenden Sie den Standard Speicherort ( `http://<` *Systemname*) `>/)` .

6. Verwenden Sie im Abschnitt **Was ist die Vertrauens Ebene für diese SharePoint-Lösung?** den Standardwert, der **als Sandkasten Lösung** bereitgestellt wird.

     Weitere Informationen zu Sandkasten-und Farm Lösungen finden Sie unter [Überlegungen zu Sandkasten](../sharepoint/sandboxed-solution-considerations.md)Lösungen.

7. Klicken Sie auf die Schaltfläche **Fertig stellen**. Das Projekt ist nun in **Projektmappen-Explorer** aufgeführt.
::: moniker-end
::: moniker range=">=vs-2019"
2.  Wählen Sie im Dialogfeld **Neues Projekt erstellen** das **leere SharePoint-Projekt** für die bestimmte Version von SharePoint aus, die Sie installiert haben. Wenn Sie z. b. SharePoint 2016-Installation haben, wählen Sie die **Projektvorlage SharePoint 2016-Empty** aus.
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

3. Ändern Sie den Namen des Projekts in **Clinic**, und wählen Sie dann die Schaltfläche **Erstellen** aus.

4. Geben Sie im Dialogfeld **Geben Sie den Standort und die Sicherheitsstufe für das Debuggen** an die URL für die lokale SharePoint-Website ein, der Sie das neue benutzerdefinierte Feld Element hinzufügen möchten, oder verwenden Sie den Standard Speicherort ( `http://<` *Systemname*) `>/)` .

5. Verwenden Sie im Abschnitt **Was ist die Vertrauens Ebene für diese SharePoint-Lösung?** den Standardwert, der **als Sandkasten Lösung** bereitgestellt wird.

     Weitere Informationen zu Sandkasten-und Farm Lösungen finden Sie unter [Überlegungen zu Sandkasten](../sharepoint/sandboxed-solution-considerations.md)Lösungen.

6. Klicken Sie auf die Schaltfläche **Fertig stellen**. Das Projekt ist nun in **Projektmappen-Explorer** aufgeführt.
::: moniker-end

#### <a name="to-add-site-columns"></a>So fügen Sie Site Spalten hinzu

1. Fügen Sie eine neue Website Spalte hinzu. Klicken Sie hierzu in **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt **Clinic** , und wählen Sie dann **Add**  >  **Neues Element** hinzufügen aus.

2. Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option **Website Spalte** aus, ändern Sie den Namen in **patientName**, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.

3. Belassen Sie in der *Elements.xml* -Datei der Website den **Typ** " **Text**", und ändern Sie die **Gruppen** Einstellung in " **Clinic Site Columns**". Nach Abschluss des Vorgangs sollte die *Elements.xml* Datei der Website Spalte wie im folgenden Beispiel aussehen.

    ```xml
    <Field
         ID="{f9ba60d1-5631-41fb-b016-a38cf48eef63}"
         Name="PatientName"
         DisplayName="Patient Name"
         Type="Text"
         Required="FALSE"
         Group="Clinic Site Columns">
    </Field>
    ```

    > [!TIP]
    > Visual Studio fügt dem Display Name automatisch ein Leerzeichen hinzu, wenn Sie die Kamel-Schreibweise im Namen der Website Spalte verwenden.
    > Es wird empfohlen, keine Leerzeichen im Spaltennamen der Website zu verwenden, da dies Probleme verursachen kann, wenn Sie versuchen, die Lösung in SharePoint bereitzustellen.

4. Fügen Sie dem Projekt zwei weitere Website Spalten mit demselben Verfahren hinzu: **patientID** (Type = "Integer") und **Doctor Name** (Type = "Text"). Legen Sie Ihren Gruppenwert auf **Clinic-Standort Spalten** fest.

## <a name="create-a-custom-content-type"></a>Erstellen eines benutzerdefinierten Inhaltstyp
 Erstellen Sie als nächstes einen Inhaltstyp – basierend auf dem Inhaltstyp "Contacts" –, der die Website Spalten enthält, die Sie im vorherigen Verfahren erstellt haben. Wenn Sie einen Inhaltstyp auf einem vorhandenen Inhaltstyp basieren, können Sie Zeit sparen, da der Basis Inhaltstyp mehrere Site Spalten zur Verwendung im neuen Inhaltstyp bereitstellt.

#### <a name="to-create-a-custom-content-type"></a>So erstellen Sie einen benutzerdefinierten Inhaltstyp

1. Fügen Sie dem Projekt einen Inhaltstyp hinzu. Wählen Sie hierzu in **Projektmappen-Explorer** den Projekt Knoten aus.

2. Wählen Sie in der Menüleiste **Projekt** > **Neues Element hinzufügen** aus.

3. Erweitern Sie unter **Visual c#** oder **Visual Basic** den Knoten **SharePoint** , und wählen Sie dann den Knoten **2010** aus.

4. Wählen Sie im Bereich **Vorlagen** die Vorlage **Inhaltstyp** aus, ändern Sie den Namen in **Patienteninformationen**, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.

     Der Assistent zum Anpassen von **SharePoint** wird geöffnet.

5. Wählen Sie in der Liste **welcher Basis Inhaltstyp soll dieser Inhaltstyp erben von** der Liste **Kontakt** als Inhaltstyp aus, auf dem der neue Inhaltstyp basieren soll, und klicken Sie dann auf die Schaltfläche **Fertig** stellen.

     Dadurch erhalten Sie zusätzlich zu den zuvor definierten Website Spalten Zugriff auf andere potenziell nützliche Websites Palten im Inhaltstyp "Contact".

6. Nachdem der Inhaltstyp-Designer angezeigt wird, fügen Sie auf der Registerkarte **Spalten** die drei zuvor definierten Websites Palten hinzu: **Patientenname**, **Patienten-ID** und **Name des Arztes**. Wenn Sie diese Spalten hinzufügen möchten, wählen Sie das erste Listenfeld in der Liste Website Spalten unter **Anzeige Name** aus, und wählen Sie dann alle Website Spalten in der Liste nacheinander aus.

    > [!TIP]
    > Um die Standort Spalten schneller auszuwählen, Filtern Sie die Liste, indem Sie die ersten Buchstaben des Namens der Spalte eingeben.

7. Fügen Sie zusätzlich zu den drei benutzerdefinierten Websites Palten die Spalte **Kommentare** -Website aus der Liste Website Spalten hinzu.

8. Aktivieren Sie das Kontrollkästchen **erforderlich** für die Spalten " **Patienten Name** " und " **Patienten-ID** ", um die erforderlichen Felder zu erstellen.

9. Vergewissern Sie sich, dass der Inhaltstyp auf der Registerkarte **Inhaltstyp** **Patienten** Informationen ist, und ändern Sie dann die Beschreibung in **Patienten Informationskarte**.

10. Ändern Sie den **Gruppennamen** in **Clinic-Inhaltstypen**, und belassen Sie die anderen Einstellungen auf die Standardwerte.

11. Klicken Sie in der Menüleiste auf **Datei**  >  **Alle speichern**, und schließen Sie dann den Inhaltstyp-Designer.

## <a name="create-a-list"></a>Erstelle eine Liste.
 Erstellen Sie nun eine Liste, in der der neue Inhaltstyp und die Website Spalten verwendet werden.

#### <a name="to-create-a-list"></a>So erstellen Sie eine Liste

1. Fügen Sie dem Projekt eine Liste hinzu. Wählen Sie hierzu in **Projektmappen-Explorer** den Projekt Knoten aus.

2. Wählen Sie in der Menüleiste **Projekt** > **Neues Element hinzufügen** aus.

3. Erweitern Sie unter **Visual c#** oder **Visual Basic** den **SharePoint** -Knoten.

4. Wählen Sie im Bereich **Vorlagen** die Vorlage **Liste** aus, ändern Sie den Namen in **Patienten**, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.

5. Belassen Sie die **Liste auf der Grundlage** der Einstellung als **Standard (benutzerdefinierte Liste)** anpassen, und wählen Sie dann die Schaltfläche **Fertig** stellen aus.

6. Wählen Sie im Listen-Designer die Schaltfläche **Inhaltstypen** aus, um das Dialogfeld **Inhaltstyp Einstellungen** anzuzeigen.

7. Wählen Sie die neue Zeile aus, wählen Sie den Inhaltstyp **Patienteninformationen** in der Liste der Inhaltstypen aus, und klicken Sie dann auf die Schaltfläche **OK** .

     Dadurch werden alle Site Spalten aus dem Inhaltstyp **Patienteninformationen** in die Liste eingefügt.

8. Löschen Sie alle Site Spalten in der Liste mit Ausnahme der folgenden:

    - Patienten-ID

    - Patienten Name

    - Telefon privat

    - E-Mail

    - Name des Arztes

    - Kommentare

9. Wählen Sie unter **Spalten Anzeige Name** eine leere Zeile aus, fügen Sie eine benutzerdefinierte Listen Spalte hinzu, und benennen Sie Sie als **Krankenhaus**. Belassen Sie den Datentyp als **einzelne Textzeile**.

     Die benutzerdefinierte Listen Spalte gilt nur für diese Liste. Wenn Sie einer Liste eine benutzerdefinierte Listen Spalte hinzufügen, wird ein neuer Listen Inhaltstyp erstellt und als Standardliste festgelegt, einschließlich aller der Liste hinzugefügten Spalten.

    > [!TIP]
    > Wenn Sie in der Liste der Website Spalten eine Spalte auswählen, wird eine vorhandene Website Spalte verwendet. Wenn Sie jedoch einen Spaltennamen eingeben, ohne Spalten in der Liste auszuwählen, wird eine benutzerdefinierte Listen Spalte erstellt, auch wenn bereits eine Spalte mit demselben Namen in der Liste vorhanden ist.

     Anstatt den Datentyp für die benutzerdefinierte Listen Spalte auf eine **einzelne Textzeile** festzulegen, können Sie stattdessen den Datentyp für diese Spalte auf Lookup festlegen, und die zugehörigen Werte werden aus einer Tabelle oder einer anderen Liste abgerufen. Weitere Informationen zu Such Spalten finden Sie unter [Auflisten von Beziehungen in SharePoint 2010](/previous-versions/msp-n-p/ff798514(v=pandp.10)) und suchen [und Auflisten von Beziehungen](/previous-versions/office/developer/sharepoint-2010/ff623048(v=office.14)).

10. Aktivieren Sie neben den Feldern **Patienten-ID** und **Patienten Name** das Kontrollkästchen **erforderlich** .

11. Wählen Sie auf der Registerkarte **Sichten** eine leere Zeile aus, um eine Ansicht zu erstellen. Geben Sie die **Patienten Details** in einer leeren Zeile unter der Spalte " **View Name** " ein.

     Auf der Registerkarte **Sichten** können Sie die Spalten angeben, die in der SharePoint-Liste angezeigt werden sollen.

12. Wählen Sie die Zeile neue **Patienten Details** aus, und wählen Sie dann die Schaltfläche **als Standard festlegen** aus.

     Die neue Ansicht ist nun die Standardansicht für die Liste.

13. Fügen Sie die folgenden Spalten in der Liste **Ausgewählte Spalten** in der folgenden Reihenfolge hinzu:

    - Patienten-ID

    - Patienten Name

    - Telefon privat

    - E-Mail

    - Name des Arztes

    - Hospital

    - Kommentare

14. Wählen Sie in der Liste **Eigenschaften** die Eigenschaft **Sortieren und Gruppieren** aus, und klicken Sie dann auf das ![Symbol](../sharepoint/media/ellipsisicon.gif "Symbol "Ellipse"") mit den Auslassungs Punkten mit den Auslassungs Punkten, um das Dialogfeld **Sortieren und Gruppieren** anzuzeigen.

15. Wählen Sie in der Liste **Spaltenname** den **Namen Patienten Name** aus, stellen Sie sicher, dass die **Sortier** Spalte auf **Aufsteigend** festgelegt ist, und klicken Sie dann auf die Schaltfläche **OK** .

## <a name="test-the-application"></a>Testen der Anwendung
 Nachdem die benutzerdefinierten Websites Spalten, der Inhaltstyp und die Liste bereit sind, stellen Sie Sie in SharePoint bereit, und führen Sie die Anwendung aus, um Sie zu testen.

#### <a name="to-test-the-application"></a>So testen Sie die Anwendung

1. Klicken Sie in der Menüleiste auf **Datei** > **Alle speichern**.

2. Drücken Sie die Taste **F5** , um die Anwendung auszuführen.

     Die Anwendung wird kompiliert, und dann werden die zugehörigen Funktionen in SharePoint bereitgestellt und aktiviert.

3. Wählen Sie auf der Navigationsleiste den Link **Patienten** aus, um die Liste **Patienten** anzuzeigen.

     Die Spaltennamen in der Liste sollten mit denjenigen identisch sein, die Sie auf der Registerkarte **Sichten** in eingegeben haben [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

4. Wählen Sie den Link **Neues Element hinzufügen** aus, um eine Patienten Informationskarte zu erstellen.

5. Geben Sie Informationen in die Felder ein, und klicken Sie dann auf die Schaltfläche **Speichern** .

     Der neue Datensatz wird in der Liste angezeigt.

## <a name="see-also"></a>Weitere Informationen
- [Erstellen von Websitespalten, Inhaltstypen und Listen für SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)
- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)
- [Gewusst wie: Erstellen eines benutzerdefinierten Feldtyps](/previous-versions/office/developer/sharepoint-2010/bb862248(v=office.14))
- [Inhaltstypen](/previous-versions/office/developer/sharepoint-2010/ms479905(v=office.14))
- [Spalten](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14))
