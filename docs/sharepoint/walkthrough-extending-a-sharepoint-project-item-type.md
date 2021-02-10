---
title: 'Exemplarische Vorgehensweise: Erweitern eines SharePoint-Projekt Elementtyps | Microsoft-Dokumentation'
description: In dieser exemplarischen Vorgehensweise erstellen Sie eine Erweiterung für einen SharePoint-Projekt Elementtyp, z. b. das BDC-Modellprojekt Element (Business Data Connectivity).
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 74d57ae4beca074fbf7711ea3d732d903d8faa4b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952680"
---
# <a name="walkthrough-extend-a-sharepoint-project-item-type"></a>Exemplarische Vorgehensweise: Erweitern eines SharePoint-Projekt Elementtyps
  Mithilfe des Projekt Elements **Business Data Connectivity-Modell** können Sie ein Modell für den Business Data Connectivity (BDC)-Dienst in SharePoint erstellen. Wenn Sie mit diesem Projektelement ein Modell erstellen, werden die Daten Benutzern im Modell standardmäßig nicht angezeigt. Sie müssen zusätlzlich eine externe Liste in SharePoint erstellen, damit Benutzer die Daten einsehen können.

 In dieser exemplarischen Vorgehensweise erstellen Sie eine Erweiterung für das Projekt Element des **Business Data Connectivity-Modells** . Entwickler können mithilfe der Erweiterung eine externe Liste in ihrem Projekt erstellen, die die Daten im BDC-Modell anzeigt. Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:

- Erstellen einer Visual Studio-Erweiterung, die zwei Hauptaufgaben ausführt:

  - Es wird eine externe Liste generiert, die die Daten in einem BDC-Modell anzeigt. Die Erweiterung verwendet das Objektmodell für das SharePoint-Projekt System, um eine *Elements.xml* Datei zu generieren, die die Liste definiert. Außerdem wird die Datei zum Projekt hinzugefügt, damit sie zusammen mit dem BDC-Modell bereitgestellt werden kann.

  - In **Projektmappen-Explorer** wird ein Kontextmenü Element zu den Projekt Elementen des **Business Data Connectivity-Modells** hinzugefügt. Entwickler können auf dieses Menüelement klicken, um eine externe Liste für das BDC-Modell zu generieren.

- Erstellen eines Visual Studio-Erweiterungspakets (VSIX) zum Bereitstellen der Erweiterungsassembly.

- Testen der Erweiterung.

## <a name="prerequisites"></a>Voraussetzungen
 Zum Durchführen dieser exemplarischen Vorgehensweise werden auf dem Entwicklungscomputer die folgenden Komponenten benötigt:

- Unterstützte Editionen von Microsoft Windows, SharePoint und Visual Studio.

- Die [!include[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. In dieser exemplarischen Vorgehensweise wird die **VSIX-Projekt** Vorlage im SDK verwendet, um ein VSIX-Paket zum Bereitstellen des Projekt Elements zu erstellen. Weitere Informationen finden Sie unter [Erweitern der SharePoint-Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Kenntnisse der folgenden Konzepte sind hilfreich, wenn auch für die Durchführung der exemplarischen Vorgehensweise nicht erforderlich:

- Den BDC-Dienst in [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]. Weitere Informationen finden Sie unter [BDC-Architektur](/previous-versions/office/developer/sharepoint-2010/ee558876(v=office.14)).

- Das XML-Schema für BDC-Modelle. Weitere Informationen finden Sie unter [Infrastruktur des BDC-Modells](/previous-versions/office/developer/sharepoint-2010/ee556378(v=office.14)).

## <a name="create-the-projects"></a>Erstellen der Projekte
 Zum Abschließen dieser exemplarischen Vorgehensweise müssen Sie zwei Projekte erstellen:

- Ein VSIX-Projekt für die Erstellung des VSIX-Pakets zum Bereitstellen der Projektelementerweiterung

- Ein Klassenbibliotheksprojekt, das die Projektelementerweiterung implementiert

  Beginnen Sie mit der exemplarischen Vorgehensweise, indem Sie beide Projekte erstellen.

#### <a name="to-create-the-vsix-project"></a>So erstellen Sie das VSIX-Projekt

1. Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**.

3. Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Visual c#** oder **Visual Basic** , und wählen Sie dann den Knoten **Erweiterbarkeit** aus.

    > [!NOTE]
    > Der **Erweiterbarkeits** Knoten ist nur verfügbar, wenn Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie weiter oben in diesem Thema im Abschnitt zu den erforderlichen Komponenten.

4. Wählen Sie in der Liste am oberen Rand des Dialog Felds **Neues Projekt** die Option **.NET Framework 4,5** aus.

     Für SharePoint-Tools-Erweiterungen werden Funktionen aus dieser .NET Framework-Version benötigt.

5. Wählen Sie die **VSIX-Projekt** Vorlage aus.

6. Geben Sie im Feld **Name den Namen** **generateexternaldatalisten** ein, und klicken Sie dann auf die Schaltfläche **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]fügt **Projektmappen-Explorer** das **generateexternaldatalisten** -Projekt hinzu.

7. Wenn die Datei "Source. Extension. vsixmanifest" nicht automatisch geöffnet wird, öffnen Sie das zugehörige Kontextmenü im Projekt generateexternaldatalisten, und wählen Sie dann **Öffnen** aus.

8. Stellen Sie sicher, dass im Feld "Autor" der Datei "source.extension.vsixmanifest" ein Eintrag vorhanden ist (geben Sie "Contoso" ein), und speichern und schließen Sie dann die Datei.

#### <a name="to-create-the-extension-project"></a>So erstellen Sie das Erweiterungsprojekt

1. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für den Projektmappenknoten **generateexternaldatalisten** , wählen Sie **Hinzufügen** aus, und wählen Sie dann **Neues Projekt** aus.

2. Erweitern Sie im Dialogfeld **Neues Projekt hinzufügen** den Knoten **Visual c#** oder **Visual Basic** , und wählen Sie dann den Knoten **Windows** aus.

3. Wählen Sie in der Liste am oberen Rand des Dialog Felds **.NET Framework 4,5** aus.

4. Wählen Sie in der Liste der Projektvorlagen die Option **Klassenbibliothek** aus.

5. Geben Sie im Feld **Name den Namen** **BdcProjectItemExtension** ein, und klicken Sie dann auf die Schaltfläche **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt der Projekt Mappe das Projekt " **BdcProjectItemExtension** " hinzu und öffnet die standardmäßige Class1-Codedatei.

6. Löschen Sie die Class1-Codedatei aus dem Projekt.

## <a name="configure-the-extension-project"></a>Konfigurieren des Erweiterungsprojekts
 Bevor Sie Code zum Erstellen der Projektelementerweiterung schreiben, fügen Sie dem Erweiterungsprojekt Codedateien und Assemblyverweise hinzu.

#### <a name="to-configure-the-project"></a>So konfigurieren Sie das Projekt

1. Fügen Sie im Projekt "BdcProjectItemExtension" zwei Codedateien mit den folgenden Namen hinzu:

    - ProjectItemExtension

    - GenerateExternalDataLists

2. Wählen Sie das Projekt BdcProjectItemExtension aus, und klicken Sie dann auf der Menüleiste auf **Projekt**  >  **Verweis hinzufügen**.

3. Wählen Sie **unter dem Knoten** Assemblys den Knoten **Framework** aus, und aktivieren Sie das Kontrollkästchen für jede der folgenden Assemblys:

    - System.ComponentModel.Composition

    - WindowsBase

4. Wählen Sie **unter dem Knoten** Assemblys den Knoten **Erweiterungen** aus, und aktivieren Sie dann das Kontrollkästchen für die folgende Assembly:

    - Microsoft.VisualStudio.SharePoint

5. Klicken Sie auf die Schaltfläche **OK** .

## <a name="define-the-project-item-extension"></a>Definieren der Projekt Element Erweiterung
 Erstellen Sie eine Klasse, die die Erweiterung für das Projekt Element des **Business Data Connectivity-Modells** definiert. Die Klasse implementiert die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>-Schnittstelle, um die Erweiterung zu definieren. Implementieren Sie diese Schnittstelle immer dann, wenn Sie einen vorhandenen Projektelementtyp erweitern möchten.

#### <a name="to-define-the-project-item-extension"></a>So definieren Sie eine Projektelementerweiterung

1. Fügen Sie den folgenden Code in die Codedatei "projectitemextension" ein.

    > [!NOTE]
    > Nach dem Hinzufügen dieses Codes weist das Projekt einige Kompilierungsfehler auf. Diese Fehler werden durch Code behoben, den Sie in späteren Schritten hinzufügen.

     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/projectitemextension.cs#1)]
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/projectitemextension.vb#1)]

## <a name="create-the-external-data-lists"></a>Erstellen der externen Daten Listen
 Fügen Sie eine partielle Definition der `GenerateExternalDataListsExtension`-Klasse hinzu, die im BDC-Modell eine externe Datenliste für jede Entität erstellt. Um die externe Datenliste zu erstellen, werden im Code zuerst die Entitätsdaten aus dem BDC-Modell gelesen, indem die XML-Daten in der BDC-Modelldatei analysiert werden. Anschließend wird eine Listeninstanz basierend auf dem BDC-Modell erstellt und zum Projekt hinzugefügt.

#### <a name="to-create-the-external-data-lists"></a>So erstellen Sie die externen Datenlisten

1. Fügen Sie in der Codedatei "GenerateExternalDataLists" folgenden Code ein.

     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.cs#2)]

## <a name="checkpoint"></a>Prüfpunkt
 Ab diesem Punkt in der exemplarischen Vorgehensweise wurde der gesamte für die Projektelementerweiterung benötigte Code in das Projekt eingefügt. Erstellen Sie die Projektmappe, um sicherzustellen, dass das Projekt ohne Fehler kompiliert wird.

#### <a name="to-build-the-solution"></a>So erstellen Sie die Projektmappe

1. Wählen Sie auf der Menüleiste **Erstellen** > **Projektmappe erstellen** aus.

## <a name="create-a-vsix-package-to-deploy-the-project-item-extension"></a>Erstellen eines VSIX-Pakets zum Bereitstellen der Projekt Element Erweiterung
 Zum Bereitstellen der Erweiterung erstellen Sie anhand des VSIX-Projekts in der Lösung ein VSIX-Paket. Konfigurieren Sie zuerst das VSIX-Paket, indem Sie die im VSIX-Projekt enthaltene Datei "source.extension.vsixmanifest" ändern. Erstellen Sie anschließend das VSIX-Paket, indem Sie die Lösung erstellen.

#### <a name="to-configure-and-create-the-vsix-package"></a>So erstellen und konfigurieren Sie das VSIX-Paket

1. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für die Datei "Source. Extension. vsixmanifest" im Projekt generateexternaldatalisten, und wählen Sie dann **Öffnen** aus.

     Die Datei wird von Visual Studio im Manifest-Editor geöffnet. Die Datei "source.extension.vsixmanifest" bildet die Grundlage für die Datei "extension.vsixmanifest", die für alle VSIX-Pakete erforderlich ist. Weitere Informationen zu dieser Datei finden Sie in der [Referenz zu VSIX-Erweiterungs Schema 1,0](/previous-versions/dd393700(v=vs.110)).

2. Geben Sie im Feld **Produkt Name den Namen** **externer Daten Listen-Generator** ein.

3. **Geben Sie** im Feld **Autor** den Text "" ein.

4. Geben Sie im Feld **Beschreibung** **eine Erweiterung für Projekt Elemente des Business Data Connectivity-Modells ein, die verwendet werden können, um externe Daten Listen zu generieren**.

5. Wählen Sie im Editor auf der Registerkarte **Objekte** die Schaltfläche **neu** aus.

     Das Dialogfeld **Neues Objekt hinzufügen** wird angezeigt.

6. Wählen Sie in der Liste **Typ** den Eintrag **Microsoft. VisualStudio. MEFComponent** aus.

    > [!NOTE]
    > Dieser Wert entspricht dem `MefComponent`-Element in der Datei "extension.vsixmanifest". Von diesem Element wird der Name einer Erweiterungsassembly im VSIX-Paket angegeben. Weitere Informationen finden Sie unter [MEFComponent-Element (VSX-Schema)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. Wählen Sie  in der Liste Quelle **ein Projekt in der aktuellen Projekt** Mappe aus.

8. Wählen Sie in der Liste **Projekt** die **Option BdcProjectItemExtension** aus, und klicken Sie dann auf die Schaltfläche **OK** .

9. Wählen Sie auf der Menüleiste **Erstellen** > **Projektmappe erstellen** aus.

10. Stellen Sie sicher, dass das Projekt fehlerfrei kompiliert und erstellt wird.

11. Überprüfen Sie, ob im Buildausgabeordner des Projekts "GenerateExternalDataLists" jetzt die Datei "GenerateExternalDataLists.vsix" vorhanden ist.

     Standardmäßig handelt es sich beim Buildausgabeordner um den Ordner "...\bin\Debug" in dem Ordner mit der Projektdatei.

## <a name="test-the-project-item-extension"></a>Testen der Projekt Element Erweiterung
 Jetzt können Sie die Projektelementerweiterung testen. Debuggen Sie das Erweiterungsprojekt zunächst in der experimentellen Instanz von Visual Studio. Verwenden Sie die Erweiterung dann in der experimentellen Instanz von Visual Studio, um eine externe Liste für ein BDC-Modell zu generieren. Öffnen Sie abschließend die externe Liste auf der SharePoint-Website, um sicherzustellen, dass die Liste einwandfrei funktioniert.

#### <a name="to-start-debugging-the-extension"></a>So debuggen Sie die Erweiterung

1. Starten Sie ggf. Visual Studio mit Administratoranmeldeinformationen neu, und öffnen Sie dann die Projektmappe "GenerateExternalDataLists".

2. Öffnen Sie im Projekt "BdcProjectItemExtension" die Codedatei "ProjectItemExtension", und fügen Sie dann der Codezeile in der `Initialize`-Methode einen Haltepunkt hinzu.

3. Öffnen Sie die Codedatei "GenerateExternalDataLists", und fügen Sie dann der ersten Codezeile in der `GenerateExternalDataLists_Execute`-Methode einen Haltepunkt hinzu.

4. Starten Sie das Debugging, indem Sie die **F5** -Taste drücken oder in der Menüleiste **Debuggen**  >  **Debuggen starten** auswählen.

     Die Erweiterung wird unter "%UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\External Data List Generator\1.0" installiert, und eine experimentelle Instanz von Visual Studio wird gestartet. Sie testen das Projektelement in dieser Instanz von Visual Studio.

#### <a name="to-test-the-extension"></a>So testen Sie die Erweiterung

1. Wählen Sie in der experimentellen Instanz von Visual Studio in der Menüleiste **Datei**  >  **neu**  >  **Projekt** aus.

2. Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Vorlagen** , erweitern Sie den Knoten **Visual c#** , erweitern Sie den Knoten **SharePoint** , und wählen Sie dann **2010** aus.

3. Stellen Sie sicher, dass in der Liste am oberen Rand des Dialog Felds **.NET Framework 3,5** ausgewählt ist. Projekte für [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] erfordern diese Version von .NET Framework.

4. Wählen Sie in der Liste der Projektvorlagen **SharePoint 2010-Projekt** aus.

5. Geben Sie im Feld **Name den Namen** **sharepointprojecttestbdc** ein, und klicken Sie dann auf die Schaltfläche **OK** .

6. Geben Sie im Assistenten zum Anpassen von SharePoint die URL der Website ein, die Sie zum Debuggen verwenden möchten, wählen Sie **als Farm Lösung** bereitstellen aus, und klicken Sie dann auf die Schaltfläche **Fertig** stellen.

7. Öffnen Sie das Kontextmenü für das Projekt sharepointprojecttestbdc, wählen Sie **Hinzufügen** und dann **Neues Element** aus.

8. Erweitern Sie im Dialogfeld **netwitem-sharepointprojecttestbdc hinzufügen** den Knoten installierte Sprache, und erweitern Sie den **SharePoint** -Knoten.

9. Wählen Sie den Knoten **2010** aus, und wählen Sie dann die Vorlage **Business Data Connectivity-Modell (nur Farm Lösung)** aus.

10. Geben Sie im Feld **Name den Namen** **TestBDCModel** ein, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.

11. Überprüfen Sie, ob die Codeausführung in der anderen Instanz von Visual Studio an dem Haltepunkt unterbrochen wird, den Sie in der `Initialize`-Methode der Codedatei "ProjectItemExtension" festgelegt haben.

12. Wählen Sie in der beendeten Instanz von Visual Studio die **F5** -Taste, oder klicken Sie in der Menüleiste auf **Debuggen**  >  **fortsetzen** , um das Debuggen des Projekts fortzusetzen.

13. Wählen Sie in der experimentellen Instanz von Visual Studio die **F5** -Taste, oder wählen Sie in der Menüleiste   >  **Debuggen Debuggen starten** aus, um das Projekt **TestBDCModel** zu erstellen, bereitzustellen und auszuführen.

     Im Webbrowser wird die Standardseite der für das Debugging angegebenen SharePoint-Website geöffnet.

14. Vergewissern Sie sich, dass der Abschnitt **Listen** im Bereich Schnellstart noch keine Liste enthält, die auf dem standardmäßigen BDC-Modell im Projekt basiert. Sie müssen zuerst eine externe Datenliste erstellen, entweder mit der SharePoint-Benutzeroberfläche oder mit der Projektelementerweiterung.

15. Schließen Sie den Webbrowser.

16. Öffnen Sie in der Instanz von Visual Studio, in der das Projekt TestBDCModel geöffnet ist, das Kontextmenü für den Knoten **TestBDCModel** in **Projektmappen-Explorer**, und wählen Sie dann **externe Datenliste generieren** aus.

17. Überprüfen Sie, ob die Codeausführung in der anderen Instanz von Visual Studio an dem Haltepunkt unterbrochen wird, den Sie in der `GenerateExternalDataLists_Execute`-Methode festgelegt haben. Drücken Sie die Taste **F5** , oder klicken Sie in der Menüleiste auf **Debuggen**  >  **fortsetzen** , um das Debuggen des Projekts fortzusetzen.

18. Die experimentelle Instanz von Visual Studio fügt dem Projekt "TestBDCModel" eine Listen Instanz mit dem Namen **Entity1DataList** hinzu, und die Instanz generiert außerdem eine Funktion mit dem Namen **Feature2** für die Listen Instanz.

19. Drücken Sie die Taste **F5** , oder wählen Sie in der Menüleiste   >  **Debuggen Debuggen starten** aus, um das Projekt TestBDCModel zu erstellen, bereitzustellen und auszuführen.

     Im Webbrowser wird die Standardseite der SharePoint-Website geöffnet, die zum Debugging verwendet wird.

20. Wählen Sie im Abschnitt " **Listen** " im Bereich "Schnellstart" die Liste **Entity1DataList** aus.

21. Überprüfen Sie, ob die Liste neben den Spalten "Identifier1" und "Message" ebenfalls ein Element mit dem Wert "0" für "Identifier1" und dem Wert "Hello World" für "Message" enthält.

     Die Projektvorlage **Business Data Connectivity Model** generiert das BDC-Standardmodell, das alle diese Daten bereitstellt.

22. Schließen Sie den Webbrowser.

## <a name="clean-up-the-development-computer"></a>Bereinigen des Entwicklungs Computers
 Nachdem Sie die Tests der Projektelementerweiterung abgeschlossen haben, entfernen Sie die externe Liste und das BDC-Modell von der SharePoint-Website, und entfernen Sie die Projektelementerweiterung aus Visual Studio.

#### <a name="to-remove-the-external-data-list-from-the-sharepoint-site"></a>So entfernen Sie die externe Datenliste von der SharePoint-Website

1. Wählen Sie im Bereich Schnellstart der SharePoint-Website die Liste **Entity1DataList** aus.

2. Wählen Sie im Menüband auf der SharePoint-Website die Registerkarte **Liste** aus.

3. Wählen Sie auf der Registerkarte **Liste** in der Gruppe **Einstellungen** die Option **Listen Einstellungen** aus.

4. Wählen Sie unter **Berechtigungen und Verwaltung** die Option **Diese Liste löschen** aus, und klicken Sie dann auf **OK** , um zu bestätigen, dass Sie die Liste an den Papierkorb senden möchten.

5. Schließen Sie den Webbrowser.

#### <a name="to-remove-the-bdc-model-from-the-sharepoint-site"></a>So entfernen Sie das BDC-Modell von der SharePoint-Website

1. Wählen Sie in der experimentellen Instanz von Visual Studio auf der Menüleiste die Option **Build**  >  **zurückziehen** aus.

     Das BDC-Modell wird aus der SharePoint-Website entfernt.

#### <a name="to-remove-the-project-item-extension-from-visual-studio"></a>So entfernen Sie die Projektelementerweiterung aus Visual Studio

1. Wählen Sie in der experimentellen Instanz von Visual Studio auf der Menüleiste Extras   >  **Erweiterungen und Updates** aus.

     Das Dialogfeld **Erweiterungen und Updates** wird geöffnet.

2. Wählen Sie in der Liste der Erweiterungen **externer Daten Listen-Generator** aus, und wählen Sie dann die Schaltfläche **deinstallieren** aus.

3. Klicken Sie im angezeigten Dialogfeld auf **Ja** , um zu bestätigen, dass Sie die Erweiterung deinstallieren möchten.

4. Wählen Sie **jetzt neu starten** , um die Installation abzuschließen.

5. Schließen Sie beide Visual Studio-Instanzen (sowohl die experimentelle als auch die Instanz mit der geöffneten Projektmappe "GenerateExternalDataLists").

## <a name="see-also"></a>Weitere Informationen
- [Erweitern des SharePoint-Projektsystems](../sharepoint/extending-the-sharepoint-project-system.md)
- [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)