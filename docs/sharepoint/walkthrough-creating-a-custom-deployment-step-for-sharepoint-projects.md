---
title: Erstellen eines benutzerdefinierten Bereitstellungs Schritts für SharePoint-Projekte
description: In dieser exemplarischen Vorgehensweise erstellen Sie einen benutzerdefinierten Bereitstellungs Schritt zum Aktualisieren von SharePoint-Projektlösungen auf einem Server, auf dem SharePoint ausgeführt wird.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8d42726cddb0565af66e161b41c16c94cfe2cb2b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839135"
---
# <a name="walkthrough-create-a-custom-deployment-step-for-sharepoint-projects"></a>Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Bereitstellungs Schritts für SharePoint-Projekte
  Wenn Sie ein SharePoint-Projekt bereitstellen, führt Visual Studio eine Reihe von Bereitstellungs Schritten in einer bestimmten Reihenfolge aus. Visual Studio enthält viele integrierte Bereitstellungs Schritte, aber Sie können auch eigene erstellen.

 In dieser exemplarischen Vorgehensweise erstellen Sie einen benutzerdefinierten Bereitstellungs Schritt, um Lösungen auf einem Server zu aktualisieren, auf dem SharePoint ausgeführt wird. Visual Studio enthält integrierte Bereitstellungs Schritte für viele Aufgaben, z. b. das zurückziehen oder Hinzufügen von Lösungen, bietet aber keinen Bereitstellungs Schritt für die Aktualisierung von Lösungen. Wenn Sie eine SharePoint-Lösung bereitstellen, wird die Projekt Mappe von Visual Studio standardmäßig zurückgezogen (wenn Sie bereits bereitgestellt wurde), und anschließend wird die gesamte Projekt Mappe erneut bereitgestellt. Weitere Informationen zu den integrierten Bereitstellungs Schritten finden Sie unter Bereitstellen [, veröffentlichen und Aktualisieren von SharePoint-Lösungs Paketen](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).

 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:

- Erstellen einer Visual Studio-Erweiterung, die zwei Hauptaufgaben ausführt:

  - Die Erweiterung definiert einen benutzerdefinierten Bereitstellungs Schritt zum Aktualisieren von SharePoint-Lösungen.

  - Die Erweiterung erstellt eine Projekt Erweiterung, die eine neue Bereitstellungs Konfiguration definiert. Hierbei handelt es sich um einen Satz von Bereitstellungs Schritten, die für ein bestimmtes Projekt ausgeführt werden. Die neue Bereitstellungs Konfiguration umfasst den benutzerdefinierten Bereitstellungs Schritt und mehrere integrierte Bereitstellungs Schritte.

- Erstellen Sie zwei benutzerdefinierte SharePoint-Befehle, die die Erweiterungsassembly aufruft. SharePoint-Befehle sind Methoden, die von Erweiterungsassemblys aufgerufen werden können, um APIs im Server-Objektmodell für SharePoint zu verwenden. Weitere Informationen finden Sie unter " [Aufrufe in die SharePoint-Objekt Modelle](../sharepoint/calling-into-the-sharepoint-object-models.md)".

- Entwickeln eines Visual Studio-Erweiterungspakets (VSIX) zum Bereitstellen beider Assemblys.

- Testen des neuen Bereitstellungs Schritts.

## <a name="prerequisites"></a>Voraussetzungen
 Zum Durchführen dieser exemplarischen Vorgehensweise werden auf dem Entwicklungscomputer die folgenden Komponenten benötigt:

- Unterstützte Editionen von Windows, SharePoint und Visual Studio.

- Das Visual Studio SDK. In dieser exemplarischen Vorgehensweise wird die **VSIX-Projekt** Vorlage im SDK verwendet, um ein VSIX-Paket zum Bereitstellen der Erweiterung zu erstellen. Weitere Informationen finden Sie unter [Erweitern der SharePoint-Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Kenntnisse der folgenden Konzepte sind hilfreich, wenn auch für die Durchführung der exemplarischen Vorgehensweise nicht erforderlich:

- Verwenden des Server Objektmodells für SharePoint. Weitere Informationen finden Sie unter [Verwenden des SharePoint Foundation Server-Side-Objektmodells](/previous-versions/office/developer/sharepoint-2010/ee538251(v=office.14)).

- SharePoint-Lösungen. Weitere Informationen finden Sie unter [Übersicht über Lösungen](/previous-versions/office/developer/sharepoint-2010/aa543214(v=office.14)).

- Aktualisieren von SharePoint-Lösungen. Weitere Informationen finden Sie unter [Aktualisieren einer Lösung](/previous-versions/office/developer/sharepoint-2010/aa543659(v=office.14)).

## <a name="create-the-projects"></a>Erstellen der Projekte
 Um diese exemplarische Vorgehensweise abzuschließen, müssen Sie drei Projekte erstellen:

- Ein VSIX-Projekt, um das VSIX-Paket zum Bereitstellen der Erweiterung zu erstellen.

- Ein Klassen Bibliotheksprojekt, das die Erweiterung implementiert. Dieses Projekt muss den .NET Framework 4,5 als Ziel haben.

- Ein Klassen Bibliotheksprojekt, das die benutzerdefinierten SharePoint-Befehle definiert. Dieses Projekt muss den .NET Framework 3,5 als Ziel haben.

  Beginnen Sie mit der exemplarischen Vorgehensweise, indem Sie beide Projekte erstellen.

#### <a name="to-create-the-vsix-project"></a>So erstellen Sie das VSIX-Projekt

1. Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**.

3. Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Visual c#** oder **Visual Basic** , und wählen Sie dann den Knoten **Erweiterbarkeit** aus.

    > [!NOTE]
    > Der **Erweiterbarkeits** Knoten ist nur verfügbar, wenn Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie weiter oben in diesem Thema im Abschnitt zu den erforderlichen Komponenten.

4. Wählen Sie oben im Dialogfeld **.NET Framework 4,5** in der Liste der .NET Framework Versionen aus.

5. Wählen Sie die Vorlage **VSIX-Projekt** aus, benennen Sie das Projekt **UpgradeDeploymentStep**, und klicken Sie dann auf die Schaltfläche **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt das Projekt **UpgradeDeploymentStep** zu **Projektmappen-Explorer** hinzu.

#### <a name="to-create-the-extension-project"></a>So erstellen Sie das Erweiterungsprojekt

1. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für den Projektmappenknoten UpgradeDeploymentStep, klicken Sie auf **Hinzufügen**, und wählen Sie dann **Neues Projekt** aus.

2. Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Visual c#** oder **Visual Basic** , und wählen Sie dann den Knoten **Windows** aus.

3. Wählen Sie oben im Dialogfeld **.NET Framework 4,5** in der Liste der .NET Framework Versionen aus.

4. Wählen Sie die Projektvorlage **Klassenbibliothek** aus, benennen Sie das Projekt **DeploymentStepExtension**, und wählen Sie dann die Schaltfläche **OK** aus.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt der Projekt Mappe das Projekt **DeploymentStepExtension** hinzu und öffnet die standardmäßige Class1-Codedatei.

5. Löschen Sie die Class1-Codedatei aus dem Projekt.

#### <a name="to-create-the-sharepoint-command-project"></a>So erstellen Sie das SharePoint-Befehls Projekt

1. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für den Projektmappenknoten UpgradeDeploymentStep, klicken Sie auf **Hinzufügen**, und wählen Sie dann **Neues Projekt** aus.

2. Erweitern Sie im Dialogfeld **Neues Projekt** den Eintrag **Visual c#** , oder **Visual Basic**, und wählen Sie dann den Knoten **Windows** aus.

3. Wählen Sie oben im Dialogfeld **.NET Framework 3,5** in der Liste der .NET Framework Versionen aus.

4. Wählen Sie die Projektvorlage **Klassenbibliothek** aus, benennen Sie das Projekt **SharePointCommands**, und klicken Sie dann auf die Schaltfläche **OK** .

     Visual Studio fügt der Projekt Mappe das Projekt **SharePointCommands** hinzu und öffnet die standardmäßige Class1-Codedatei.

5. Löschen Sie die Class1-Codedatei aus dem Projekt.

## <a name="configure-the-projects"></a>Konfigurieren der Projekte
 Bevor Sie Code zum Erstellen des benutzerdefinierten Bereitstellungs Schritts schreiben, müssen Sie Code Dateien und Assemblyverweise hinzufügen, und Sie müssen die Projekte konfigurieren.

#### <a name="to-configure-the-deploymentstepextension-project"></a>So konfigurieren Sie das Projekt DeploymentStepExtension

1. Fügen Sie im Projekt **DeploymentStepExtension** zwei Code Dateien mit den folgenden Namen hinzu:

    - Upgradezstep

    - DeploymentConfigurationExtension

2. Öffnen Sie das Kontextmenü für das Projekt DeploymentStepExtension, und wählen Sie dann **Verweis hinzufügen** aus.

3. Aktivieren Sie auf der Registerkarte **Framework** das Kontrollkästchen für die Assembly System. ComponentModel. Composition.

4. Aktivieren Sie auf der Registerkarte **Erweiterungen** das Kontrollkästchen für die Microsoft. VisualStudio. SharePoint-Assembly, und klicken Sie dann auf die Schaltfläche **OK** .

#### <a name="to-configure-the-sharepointcommands-project"></a>So konfigurieren Sie das SharePointCommands-Projekt

1. Fügen Sie im Projekt **SharePointCommands** eine Codedatei mit dem Namen Befehle hinzu.

2. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü des **SharePointCommands** -Projekt Knotens, und wählen Sie dann **Verweis hinzufügen** aus.

3. Aktivieren Sie auf der Registerkarte **Erweiterungen** die Kontrollkästchen für die folgenden Assemblys, und klicken Sie dann auf die Schaltfläche **OK** auswählen.

    - Microsoft.SharePoint

    - Microsoft.VisualStudio.SharePoint.Commands

## <a name="define-the-custom-deployment-step"></a>Definieren des benutzerdefinierten Bereitstellungs Schritts
 Erstellen Sie eine Klasse, die den Schritt Upgradebereitstellung definiert. Zum Definieren des Bereitstellungs Schritts implementiert die-Klasse die- <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> Schnittstelle. Implementieren Sie diese Schnittstelle immer dann, wenn Sie einen benutzerdefinierten Bereitstellungs Schritt definieren möchten.

#### <a name="to-define-the-custom-deployment-step"></a>So definieren Sie den benutzerdefinierten Bereitstellungs Schritt

1. Öffnen Sie im Projekt **DeploymentStepExtension** die Codedatei UpgradeStep, und fügen Sie den folgenden Code in die Datei ein.

    > [!NOTE]
    > Nachdem Sie diesen Code hinzugefügt haben, enthält das Projekt einige Kompilierungsfehler, aber Sie werden entfernt, wenn Sie Code in späteren Schritten hinzufügen.

     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#1)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#1)]

## <a name="create-a-deployment-configuration-that-includes-the-custom-deployment-step"></a>Erstellen einer Bereitstellungs Konfiguration, die den benutzerdefinierten Bereitstellungs Schritt einschließt
 Erstellen Sie eine Projekt Erweiterung für die neue Bereitstellungs Konfiguration, die mehrere integrierte Bereitstellungs Schritte und den neuen Schritt Upgradebereitstellung umfasst. Durch das Erstellen dieser Erweiterung helfen Sie SharePoint-Entwicklern, den upgradebereitstellungs-Schritt in SharePoint-Projekten zu verwenden.

 Zum Erstellen der Bereitstellungs Konfiguration implementiert die-Klasse die- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> Schnittstelle. Implementieren Sie diese Schnittstelle immer dann, wenn Sie eine SharePoint-Projekt Erweiterung erstellen möchten.

#### <a name="to-create-the-deployment-configuration"></a>So erstellen Sie die Bereitstellungs Konfiguration

1. Öffnen Sie im Projekt **DeploymentStepExtension** die Codedatei DeploymentConfigurationExtension, und fügen Sie den folgenden Code in die Datei ein.

     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/deploymentconfigurationextension.cs#2)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/deploymentconfigurationextension.vb#2)]

## <a name="create-the-custom-sharepoint-commands"></a>Erstellen der benutzerdefinierten SharePoint-Befehle
 Erstellen Sie zwei benutzerdefinierte Befehle, die das Server-Objektmodell für SharePoint aufruft. Ein Befehl bestimmt, ob bereits eine Projekt Mappe bereitgestellt wurde. der andere Befehl aktualisiert eine Projekt Mappe.

#### <a name="to-define-the-sharepoint-commands"></a>So definieren Sie die SharePoint-Befehle

1. Öffnen Sie im Projekt **SharePointCommands** die Codedatei "Befehle", und fügen Sie den folgenden Code in die Datei ein.

     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#4)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#4)]

## <a name="checkpoint"></a>Prüfpunkt
 An dieser Stelle der exemplarischen Vorgehensweise befinden sich der gesamte Code für den benutzerdefinierten Bereitstellungs Schritt und die SharePoint-Befehle jetzt in den Projekten. Erstellen Sie diese, um sicherzustellen, dass Sie fehlerfrei kompiliert werden.

#### <a name="to-build-the-projects"></a>So erstellen Sie die Projekte

1. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für das Projekt **DeploymentStepExtension** , und wählen Sie dann **Erstellen** aus.

2. Öffnen Sie das Kontextmenü für das Projekt **SharePointCommands** , und wählen Sie dann **Erstellen** aus.

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Erstellen eines VSIX-Pakets zum Bereitstellen der Erweiterung
 Zum Bereitstellen der Erweiterung erstellen Sie anhand des VSIX-Projekts in der Lösung ein VSIX-Paket. Konfigurieren Sie zunächst das VSIX-Paket, indem Sie die Datei "Source. Extension. vsixmanifest" im VSIX-Projekt ändern. Erstellen Sie dann das VSIX-Paket, indem Sie die Lösung erstellen.

#### <a name="to-configure-and-create-the-vsix-package"></a>So erstellen und konfigurieren Sie das VSIX-Paket

1. Öffnen Sie in **Projektmappen-Explorer** unter dem Projekt **UpgradeDeploymentStep** das Kontextmenü für die Datei " **Source. Extension. vsixmanifest** ", und wählen Sie dann **Öffnen** aus.

     Die Datei wird von Visual Studio im Manifest-Editor geöffnet. Die Datei "source.extension.vsixmanifest" bildet die Grundlage für die Datei "extension.vsixmanifest", die für alle VSIX-Pakete erforderlich ist. Weitere Informationen zu dieser Datei finden Sie in der [Referenz zu VSIX-Erweiterungs Schema 1,0](/previous-versions/dd393700(v=vs.110)).

2. Geben Sie im Feld **Produkt Name** den **Schritt upgradebereitstellungs Schritt für SharePoint-Projekte** ein.

3. **Geben Sie** im Feld **Autor** den Text "" ein.

4. Geben Sie im Feld **Beschreibung** **einen benutzerdefinierten upgradebereitstellungs-Schritt ein, der in SharePoint-Projekten verwendet werden kann**.

5. Wählen Sie im Editor auf der Registerkarte **Objekte** die Schaltfläche **neu** aus.

     Das Dialogfeld **Neues Objekt hinzufügen** wird angezeigt.

6. Wählen Sie in der Liste **Typ** den Eintrag **Microsoft. VisualStudio. MEFComponent** aus.

    > [!NOTE]
    > Dieser Wert entspricht dem `MefComponent`-Element in der Datei "extension.vsixmanifest". Von diesem Element wird der Name einer Erweiterungsassembly im VSIX-Paket angegeben. Weitere Informationen finden Sie unter [MEFComponent-Element (VSX-Schema)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. Wählen Sie  in der Liste Quelle **ein Projekt in der aktuellen Projekt** Mappe aus.

8. Wählen Sie in der Liste **Projekt** den Eintrag **DeploymentStepExtension** aus, und klicken Sie dann auf die Schaltfläche **OK** .

9. Wählen Sie im Manifest-Editor erneut die Schaltfläche **neu** aus.

     Das Dialogfeld **Neues Objekt hinzufügen** wird angezeigt.

10. Geben Sie in der Liste **Typ** den Namen **SharePoint. Commands. v4** ein.

    > [!NOTE]
    > Dieses Element gibt eine benutzerdefinierte Erweiterung an, die Sie in die Visual Studio-Erweiterung einschließen möchten. Weitere Informationen finden Sie unter [Asset-Element (VSX-Schema)](/previous-versions/dd393737(v=vs.110)).

11. Wählen Sie  in der Liste Quelle **ein Projekt in der aktuellen Projekt** Mappe aus.

12. Wählen Sie in der Liste **Projekt** die Option **SharePointCommands** aus, und klicken Sie dann auf die Schaltfläche **OK** .

13. Wählen Sie in der Menüleiste Buildprojektmappe **Erstellen** aus, und vergewissern Sie sich,  >  dass die Projekt Mappe ohne Fehler kompiliert wird.

14. Stellen Sie sicher, dass der Buildausgabeordner für das Projekt UpgradeDeploymentStep nun die Datei UpgradeDeploymentStep. vsix enthält.

     Standardmäßig handelt es sich beim Buildausgabeordner um den Ordner "...\bin\Debug" in dem Ordner mit der Projektdatei.

## <a name="prepare-to-test-the-upgrade-deployment-step"></a>Vorbereiten des Testlaufs für die Upgradebereitstellung
 Um den Schritt Upgradebereitstellung zu testen, müssen Sie zunächst eine Beispiellösung auf der SharePoint-Website bereitstellen. Beginnen Sie, indem Sie die Erweiterung in der experimentellen Instanz von Visual Studio debuggen. Erstellen Sie dann eine Listen Definition und eine Listen Instanz, die zum Testen des Bereitstellungs Schritts verwendet werden soll, und stellen Sie Sie dann auf der SharePoint-Website bereit. Ändern Sie als nächstes die Listen Definition und Listen Instanz, und stellen Sie Sie erneut bereit, um zu veranschaulichen, wie der Standard Bereitstellungs Prozesslösungen auf der SharePoint-Website überschreibt.

 Später in dieser exemplarischen Vorgehensweise ändern Sie die Listen Definition und Listen Instanz und aktualisieren Sie dann auf der SharePoint-Website.

#### <a name="to-start-debugging-the-extension"></a>So debuggen Sie die Erweiterung

1. Starten Sie Visual Studio mit Administrator Anmelde Informationen neu, und öffnen Sie dann die Projekt Mappe "UpgradeDeploymentStep".

2. Öffnen Sie im Projekt DeploymentStepExtension die Codedatei UpgradeStep, und fügen Sie der ersten Codezeile in der `CanExecute` -Methode und der-Methode einen Haltepunkt hinzu `Execute` .

3. Starten Sie das Debugging, indem Sie die **F5** -Taste drücken oder in der Menüleiste **Debuggen**  >  **Debuggen starten** auswählen.

4. Visual Studio installiert die Erweiterung unter%USERPROFILE%\appdata\local\microsoft\visualstudio\11.0exp\extensions\condeso\upgradebereitstellungsschritt für SharePoint project\1.0 und startet eine experimentelle Instanz von Visual Studio. Sie testen den Schritt Upgradebereitstellung in dieser Instanz von Visual Studio.

#### <a name="to-create-a-sharepoint-project-with-a-list-definition-and-a-list-instance"></a>So erstellen Sie ein SharePoint-Projekt mit einer Listen Definition und einer Listen Instanz

1. Wählen Sie in der experimentellen Instanz von Visual Studio in der Menüleiste **Datei**  >  **neu**  >  **Projekt** aus.

2. Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Visual c#** oder den Knoten **Visual Basic** , erweitern Sie den Knoten **SharePoint** , und wählen Sie dann den Knoten **2010** aus.

3. Stellen Sie oben im Dialogfeld sicher, dass **.NET Framework 3,5** in der Liste der .NET Framework Versionen angezeigt wird.

    Projekte für [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] und [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] erfordern diese Version der .NET Framework.

4. Wählen Sie in der Liste der Projektvorlagen **SharePoint 2010-Projekt** aus, benennen Sie das Projekt "Mitarbeiter **Listen Definition**", und wählen Sie dann die Schaltfläche **OK** .

5. Geben Sie im Assistenten zum Anpassen von **SharePoint** die URL der Website ein, die Sie zum Debuggen verwenden möchten.

6. Wählen Sie unter **Was ist die Vertrauens Ebene für diese SharePoint-Lösung**? das Optionsfeld **als Farm Lösung** bereitstellen aus.

   > [!NOTE]
   > Der upgradebereitstellungs-Schritt unterstützt keine Sandkasten Lösungen.

7. Klicken Sie auf die Schaltfläche **Fertig stellen**.

    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] erstellt das Projektmitarbeiter List Definition.

8. Öffnen Sie das Kontextmenü für das Projektmitarbeiter List Definition, wählen Sie **Hinzufügen** aus, und wählen Sie dann **Neues Element** aus.

9. Erweitern Sie im Dialogfeld **Neues Element hinzufügen-Mitarbeiter Listen Definition** den **SharePoint** -Knoten, und wählen Sie dann den Knoten **2010** aus.

10. Wählen Sie die Vorlage Element **auflisten** aus, benennen Sie die **Liste Element Mitarbeiter**, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.

     Der Assistent zum Anpassen von SharePoint wird angezeigt.

11. Überprüfen Sie auf der Seite **Listen Einstellungen auswählen** die folgenden Einstellungen, und klicken Sie dann auf die Schaltfläche **Fertig** stellen:

    1. Die **Liste der Mitarbeiter** wird im Feld **welcher Name soll für die Liste angezeigt werden?** angezeigt.

    2. Die Options Schaltfläche **eine anpassbare Liste basierend auf: Erstellen** wird ausgewählt.

    3. Der **Standardwert (leer)** wird in der Liste **Erstellen einer anpassbaren Liste basierend auf:** ausgewählt.

       [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] erstellt das Mitarbeiter Listenelement mit einer Titel Spalte und einer einzelnen leeren Instanz und öffnet den Listen-Designer.

12. Wählen Sie im Listen-Designer auf der Registerkarte **Spalten** die Zeile **neuen oder vorhandenen Spaltennamen eingeben** aus, und fügen Sie dann die folgenden Spalten in der Liste **Spalten Anzeige Name** hinzu:

    1. First Name (Vorname)

    2. Company

    3. Telefon (geschäftlich)

    4. E-Mail

13. Speichern Sie alle Dateien, und schließen Sie dann den Listen-Designer.

14. Erweitern Sie in **Projektmappen-Explorer** den Knoten **Mitarbeiterliste** , und erweitern Sie dann den untergeordneten Knoten **Employees List instance** .

15. Ersetzen Sie in der *Elements.xml* -Datei den Standard-XML-Code in dieser Datei durch den folgenden XML-Code. Dieser XML-Code ändert den Namen der Liste in **Mitarbeiter** und fügt Informationen für einen Mitarbeiter mit dem Namen Jim Hance hinzu.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">
      <ListInstance Title="Employees"
                    OnQuickLaunch="TRUE"
                    TemplateType="10000"
                    Url="Lists/Employees"
                    Description="Simple list to test upgrade deployment step">
        <Data>
          <Rows>
            <Row>
              <Field Name="Title">Hance</Field>
              <Field Name="FirstName">Jim</Field>
              <Field Name="Company">Contoso</Field>
              <Field Name="Business Phone">555-555-5555</Field>
              <Field Name="E-Mail">jim@contoso.com</Field>
            </Row>
          </Rows>
        </Data>
      </ListInstance>
    </Elements>
    ```

16. Speichern und schließen Sie die Datei *Elements.xml* .

17. Öffnen Sie das Kontextmenü für das Projektmitarbeiter List Definition, und wählen Sie dann **Öffnen** oder **Eigenschaften** aus.

     Der Eigenschaften-Designer wird geöffnet.

18. Deaktivieren Sie auf der Registerkarte **SharePoint** das Kontrollkästchen **nach dem Debuggen automatisch zurückziehen** , und speichern Sie dann die Eigenschaften.

#### <a name="to-deploy-the-list-definition-and-list-instance"></a>So stellen Sie die Listen Definition und Listen Instanz bereit

1. Wählen Sie in **Projektmappen-Explorer** den Projekt Knoten Mitarbeiter **ListDefinition** aus.

2. Stellen Sie im **Eigenschaften** Fenster sicher, dass die Eigenschaft **aktive Bereitstellungs Konfiguration** auf **Standard** festgelegt ist.

3. Drücken Sie die Taste **F5** , oder wählen Sie in der Menüleiste **Debuggen**  >  **Debuggen starten** aus.

4. Vergewissern Sie sich, dass das Projekt erfolgreich erstellt wurde, dass der Webbrowser mit der SharePoint-Website geöffnet wird, dass das **Listen** Element in der Schnellstartleiste die neue Liste der **Mitarbeiter** enthält und dass die Liste der **Mitarbeiter** den Eintrag für Jim Hance enthält.

5. Schließen Sie den Webbrowser.

#### <a name="to-modify-the-list-definition-and-list-instance-and-redeploy-them"></a>So ändern Sie die Listen Definition und Listen Instanz und stellen Sie erneut bereit

1. Öffnen Sie im Projektmitarbeiter ListDefinition die *Elements.xml* Datei, die dem Projekt Element der **Employee List-Instanz** untergeordnet ist.

2. Entfernen `Data` Sie das-Element und seine untergeordneten Elemente, um den Eintrag für Jim Hance aus der Liste zu entfernen.

     Wenn Sie fertig sind, sollte die Datei den folgenden XML-Code enthalten.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">
      <ListInstance Title="Employees"
                    OnQuickLaunch="TRUE"
                    TemplateType="10000"
                    Url="Lists/Employees"
                    Description="Simple list to test upgrade deployment step">
      </ListInstance>
    </Elements>
    ```

3. Speichern und schließen Sie die Datei *Elements.xml* .

4. Öffnen Sie das Kontextmenü für das Projekt Element für die **Mitarbeiterliste** , und wählen Sie dann **Öffnen** oder **Eigenschaften** aus.

5. Wählen Sie im Listen-Designer die Registerkarte **Sichten** aus.

6. Wählen Sie in der Liste **Ausgewählte Spalten** die Option **Anlagen** aus, und wählen Sie dann den < Schlüssel aus, um die Spalte in die Liste **Verfügbare Spalten** zu verschieben.

7. Wiederholen Sie den vorherigen Schritt, um die Spalte **geschäftlich (geschäftlich** ) aus der Liste **Ausgewählte Spalten** in die Liste **Verfügbare Spalten** zu verschieben.

     Durch diese Aktion werden diese Felder aus der Standardansicht der **Employees** -Liste auf der SharePoint-Website entfernt.

8. Starten Sie das Debugging, indem Sie die **F5** -Taste drücken oder in der Menüleiste **Debuggen**  >  **Debuggen starten** auswählen.

9. Überprüfen Sie, ob das Dialogfeld **Bereitstellungs Konflikte** angezeigt wird.

     Dieses Dialogfeld wird angezeigt, wenn Visual Studio versucht, eine Projekt Mappe (die Listen Instanz) auf einer SharePoint-Website bereitzustellen, auf der diese Lösung bereits bereitgestellt wurde. Dieses Dialogfeld wird nicht angezeigt, wenn Sie den Schritt zur Upgradebereitstellung später in dieser exemplarischen Vorgehensweise ausführen.

10. Wählen Sie im Dialogfeld **Bereitstellungs Konflikte** die Options Schaltfläche **automatisch auflösen** aus.

     Visual Studio löscht die Listen Instanz auf der SharePoint-Website, stellt das Listenelement im Projekt bereit und öffnet dann die SharePoint-Website.

11. Wählen Sie im **Listen** Abschnitt der Schnellstartleiste die Liste **Employees (Mitarbeiter** ) aus, und überprüfen Sie dann die folgenden Details:

    - Die Spalten **Anlagen** und **Privat telefonspalten** werden in dieser Ansicht der Liste nicht angezeigt.

    - Die Liste ist leer. Wenn Sie die Lösung mit der **Standard** Bereitstellungs Konfiguration erneut bereitgestellt haben, wurde die Liste der **Mitarbeiter** durch die neue leere Liste in Ihrem Projekt ersetzt.

## <a name="test-the-deployment-step"></a>Testen des Bereitstellungs Schritts
 Nun können Sie den Schritt Upgradebereitstellung testen. Fügen Sie zunächst der Listen Instanz in SharePoint ein Element hinzu. Ändern Sie dann die Listen Definition und Listen Instanz, aktualisieren Sie Sie auf der SharePoint-Website, und vergewissern Sie sich, dass das neue Element durch den upgradebereitstellungs Schritt nicht überschrieben wird

#### <a name="to-manually-add-an-item-to-the-list"></a>So fügen Sie der Liste manuell ein Element hinzu

1. Wählen Sie im Menüband auf der SharePoint-Website auf der Registerkarte **Listen Tools** die Registerkarte **Elemente** aus.

2. Wählen Sie in der **neuen** Gruppe die Option **Neues Element** aus.

     Als Alternative können Sie den Link **Neues Element hinzufügen** in der Elementliste selbst auswählen.

3. Geben Sie im Fenster **Mitarbeiter-neues Element** im Feld **Titel den Text** **Facility Manager** ein.

4. Geben Sie im Feld **Vorname** den Namen **Andy** ein.

5. **Geben Sie** im Feld **Company** den Namen "Configuration Manager" ein.

6. Wählen Sie die Schaltfläche **Speichern** aus, vergewissern Sie sich, dass das neue Element in der Liste angezeigt wird, und schließen Sie dann den Webbrowser.

     Später in dieser exemplarischen Vorgehensweise verwenden Sie dieses Element, um sicherzustellen, dass der Inhalt dieser Liste nicht durch den Schritt "Upgradebereitstellung" überschrieben wird.

#### <a name="to-test-the-upgrade-deployment-step"></a>So testen Sie den Schritt der Upgradebereitstellung

1. Öffnen Sie in der experimentellen Instanz von Visual Studio in **Projektmappen-Explorer** das Kontextmenü für den Projekt Knoten Mitarbeiter **ListDefinition** , und wählen Sie dann **Eigenschaften** aus.

    Der Eigenschaften-Editor/-Designer wird geöffnet.

2. Legen Sie auf der Registerkarte **SharePoint** die Eigenschaft **aktive Bereitstellungs Konfiguration** auf **Upgrade** fest.

    Diese benutzerdefinierte Bereitstellungs Konfiguration umfasst den neuen Schritt Upgradebereitstellung.

3. Öffnen Sie das Kontextmenü für das Projekt Element für die **Mitarbeiterliste** , und wählen Sie dann **Eigenschaften** oder **Öffnen** aus.

    Der Eigenschaften-Editor/-Designer wird geöffnet.

4. Wählen Sie auf der Registerkarte **Ansichten** die Spalte **E-Mail** aus, und wählen Sie dann den **<** Schlüssel aus, um die Spalte aus der Liste **Ausgewählte Spalten** in die Liste **Verfügbare Spalten** zu verschieben.

    Durch diese Aktion werden diese Felder aus der Standardansicht der **Employees** -Liste auf der SharePoint-Website entfernt.

5. Starten Sie das Debugging, indem Sie die **F5** -Taste drücken oder in der Menüleiste **Debuggen**  >  **Debuggen starten** auswählen.

6. Überprüfen Sie, ob die Codeausführung in der anderen Instanz von Visual Studio an dem Haltepunkt unterbrochen wird, den Sie zuvor in der `CanExecute`-Methode festgelegt haben.

7. Drücken Sie erneut **F5** , oder wählen Sie in der Menüleiste die Option **Debuggen**  >  **fortsetzen**.

8. Vergewissern Sie sich, dass der Code am Haltepunkt anhält, den Sie zuvor in der-Methode festgelegt haben `Execute` .

9. Drücken Sie die Taste **F5** , oder wählen Sie in der Menüleiste die Option **Debuggen**  >  **fortfahren** .

     Der Webbrowser öffnet die SharePoint-Website.

10. Wählen Sie in der Liste "Schnellstart" im Bereich " **Listen** " die Liste der **Mitarbeiter** aus, und überprüfen Sie dann die folgenden Details:

    - Das Element, das Sie zuvor manuell hinzugefügt haben (für Andy, den Facility Manager), ist noch nicht in der Liste enthalten.

    - Die Spalten Telefon und **e-Mail-Adresse** des **Unternehmens** werden in dieser Ansicht der Liste nicht angezeigt.

      Die  upgradebereitstellungskonfiguration ändert die vorhandene **Employees** -Listen Instanz auf der SharePoint-Website. Wenn Sie anstelle der **upgradekonfiguration** die **Standard** Bereitstellungs Konfiguration verwendet haben, wird ein Bereitstellungs Konflikt auftreten. Visual Studio löst den Konflikt durch Ersetzen der **Mitarbeiter** Liste aus, und das Element für Andy, der Einrichtungen-Manager, würde gelöscht werden.

## <a name="clean-up-the-development-computer"></a>Bereinigen des Entwicklungs Computers
 Nachdem Sie das Testen des Schritts zur Upgradebereitstellung abgeschlossen haben, entfernen Sie die Listen Instanz und Listen Definition von der SharePoint-Website, und entfernen Sie die Erweiterung für die Bereitstellungs Schritte aus Visual Studio.

#### <a name="to-remove-the-list-instance-from-the-sharepoint-site"></a>So entfernen Sie die Listen Instanz von der SharePoint-Website

1. Öffnen Sie die Liste der **Mitarbeiter** auf der SharePoint-Website, wenn die Liste nicht bereits geöffnet ist.

2. Wählen Sie im Menüband auf der SharePoint-Website die Registerkarte **Tools auflisten** aus, und klicken Sie dann auf die Registerkarte **Liste** .

3. Wählen Sie in der Gruppe **Einstellungen** das Element **Listen Einstellungen** aus.

4. Wählen Sie unter **Berechtigungen und Verwaltung** den Befehl **Diese Liste löschen** aus, **Klicken** Sie auf OK, um zu bestätigen, dass Sie die Liste an den Papierkorb senden möchten, und schließen Sie dann den Webbrowser.

#### <a name="to-remove-the-list-definition-from-the-sharepoint-site"></a>So entfernen Sie die Listen Definition von der SharePoint-Website

1. Wählen Sie in der experimentellen Instanz von Visual Studio auf der Menüleiste die Option **Build**  >  **zurückziehen** aus.

     Visual Studio zieht die Listen Definition von der SharePoint-Website zurück.

#### <a name="to-uninstall-the-extension"></a>So deinstallieren Sie die Erweiterung

1. Wählen Sie in der experimentellen Instanz von Visual Studio auf der Menüleiste Extras   >  **Erweiterungen und Updates** aus.

     Das Dialogfeld **Erweiterungen und Updates** wird geöffnet.

2. Wählen Sie in der Liste der Erweiterungen die Option **Bereitstellungs Schritt für SharePoint-Projekte aktualisieren aus**, und wählen Sie dann den Befehl **deinstallieren** aus.

3. Klicken Sie im angezeigten Dialogfeld auf **Ja** , um zu bestätigen, dass Sie die Erweiterung deinstallieren möchten, und wählen Sie dann **jetzt neu starten** aus, um die Deinstallation abzuschließen.

4. Schließen Sie beide Instanzen von Visual Studio (die experimentelle Instanz und die Instanz von Visual Studio, in der die UpgradeDeploymentStep-Projekt Mappe geöffnet ist).

## <a name="see-also"></a>Weitere Informationen
- [Erweiterte SharePoint-Paket Erstellung und-Bereitstellung](../sharepoint/extending-sharepoint-packaging-and-deployment.md)