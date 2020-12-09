---
title: 'Exemplarische Vorgehensweise: Erstellen einer SharePoint-Projekt Erweiterung | Microsoft-Dokumentation'
description: Erstellen Sie eine SharePoint-Projekt Erweiterung, mit der Sie auf Ereignisse auf Projektebene reagieren können, z. b. Wenn ein Projekt hinzugefügt, gelöscht oder umbenannt wird.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b815f8ea4656cc5a144f8cf12396391e55123ece
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914867"
---
# <a name="walkthrough-create-a-sharepoint-project-extension"></a>Exemplarische Vorgehensweise: Erstellen einer SharePoint-Projekt Erweiterung
  In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Sie eine Erweiterung für SharePoint-Projekte erstellen. Sie können eine Projekt Erweiterung zum reagieren auf Ereignisse auf Projektebene verwenden, z. b. Wenn ein Projekt hinzugefügt, gelöscht oder umbenannt wird. Sie können auch benutzerdefinierte Eigenschaften hinzufügen oder reagieren, wenn sich ein Eigenschafts Wert ändert. Im Gegensatz zu Projekt Element Erweiterungen können Projekt Erweiterungen nicht einem bestimmten SharePoint-Projekttyp zugeordnet werden. Wenn Sie eine Projekt Erweiterung erstellen, wird die Erweiterung geladen, wenn eine beliebige Art von SharePoint-Projekt in geöffnet wird [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

 In dieser exemplarischen Vorgehensweise erstellen Sie eine benutzerdefinierte boolesche Eigenschaft, die zu einem beliebigen in erstellten SharePoint-Projekt hinzugefügt wird [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Wenn diese Eigenschaft auf **true** festgelegt ist, fügt die neue Eigenschaft dem Projekt einen Bild Ressourcen Ordner hinzu, oder ordnet diesen zu. Wenn der Wert auf **false** festgelegt ist, wird der Ordner Images entfernt, sofern vorhanden. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen und entfernen](../sharepoint/how-to-add-and-remove-mapped-folders.md)von zugeordneten Ordnern.

 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:

- Erstellen einer [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Erweiterung für SharePoint-Projekte, die Folgendes bewirkt:

  - Fügt der Eigenschaftenfenster eine benutzerdefinierte Projekt Eigenschaft hinzu. Die-Eigenschaft gilt für jedes SharePoint-Projekt.

  - Verwendet das SharePoint-Projekt Objektmodell zum Hinzufügen eines zugeordneten Ordners zu einem Projekt.

  - Verwendet das [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Automatisierungs Objektmodell (DTE) zum Löschen eines zugeordneten Ordners aus dem Projekt.

- Das Entwickeln eines [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Erweiterungspakets (VSIX) zum Bereitstellen der Erweiterungsassembly der Projekt Eigenschaft.

- Debuggen und Testen der Projekt Eigenschaft.

## <a name="prerequisites"></a>Voraussetzungen
 Zum Durchführen dieser exemplarischen Vorgehensweise werden auf dem Entwicklungscomputer die folgenden Komponenten benötigt:

- Unterstützte Editionen von [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] , SharePoint und [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- Die [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. In dieser exemplarischen Vorgehensweise wird die **VSIX-Projekt** Vorlage im verwendet [!INCLUDE[TLA2#tla_sdk](../sharepoint/includes/tla2sharptla-sdk-md.md)] , um ein VSIX-Paket zum Bereitstellen der Projekteigenschaften Erweiterung zu erstellen. Weitere Informationen finden Sie unter [Erweitern der SharePoint-Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

## <a name="create-the-projects"></a>Erstellen der Projekte
 Um diese exemplarische Vorgehensweise abzuschließen, müssen Sie zwei Projekte erstellen:

- Ein VSIX-Projekt zum Erstellen des VSIX-Pakets zum Bereitstellen der Projekt Erweiterung.

- Ein Klassen Bibliotheksprojekt, das die Projekt Erweiterung implementiert.

  Beginnen Sie mit der exemplarischen Vorgehensweise, indem Sie beide Projekte erstellen.

#### <a name="to-create-the-vsix-project"></a>So erstellen Sie das VSIX-Projekt

1. Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**.

3. Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Visual c#** oder **Visual Basic** , und wählen Sie dann den Knoten **Erweiterbarkeit** aus.

    > [!NOTE]
    > Dieser Knoten ist nur verfügbar, wenn Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie weiter oben in diesem Thema im Abschnitt zu den erforderlichen Komponenten.

4. Wählen Sie oben im Dialogfeld **.NET Framework 4,5** in der Liste der .NET Framework Versionen aus, und wählen Sie dann die **VSIX-Projekt** Vorlage aus.

5. Geben Sie im Feld **Name den Namen** **ProjectExtensionPackage** ein, und klicken Sie dann auf die Schaltfläche **OK** .

     Das Projekt **ProjectExtensionPackage** wird in **Projektmappen-Explorer** angezeigt.

#### <a name="to-create-the-extension-project"></a>So erstellen Sie das Erweiterungsprojekt

1. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für den Projektmappenknoten, wählen Sie **Hinzufügen** aus, und wählen Sie dann **Neues Projekt** aus.

2. Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Visual c#** oder **Visual Basic** , und wählen Sie dann **Windows** aus.

3. Wählen Sie oben im Dialogfeld **.NET Framework 4,5** in der Liste der .NET Framework Versionen aus, und wählen Sie dann die Projektvorlage **Klassenbibliothek** aus.

4. Geben Sie im Feld **Name** den **Text ProjectExtension** ein, und klicken Sie dann auf die Schaltfläche **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt der Projekt Mappe das Projekt **ProjectExtension** hinzu und öffnet die standardmäßige Class1-Codedatei.

5. Löschen Sie die Class1-Codedatei aus dem Projekt.

## <a name="configure-the-project"></a>Konfigurieren des Projekts
 Bevor Sie Code zum Erstellen der Projekt Erweiterung schreiben, fügen Sie dem Erweiterungsprojekt Code Dateien und Assemblyverweise hinzu.

#### <a name="to-configure-the-project"></a>So konfigurieren Sie das Projekt

1. Fügen Sie dem Projekt ProjectExtension eine Codedatei mit dem Namen **CustomProperty** hinzu.

2. Öffnen Sie das Kontextmenü für das Projekt **ProjectExtension** , und wählen Sie dann **Verweis hinzufügen** aus.

3. Wählen Sie im Dialogfeld **Verweis-Manager-CustomProperty** den Knoten **Framework** aus, und aktivieren Sie dann das Kontrollkästchen neben den Assemblys System. ComponentModel. Composition und System. Windows. Forms.

4. Wählen Sie den Knoten **Erweiterungen** aus, aktivieren Sie das Kontrollkästchen neben den Assemblys Microsoft. VisualStudio. SharePoint und svdte, und klicken Sie dann auf die Schaltfläche **OK** .

5. Wählen Sie in **Projektmappen-Explorer** unter dem Ordner **Verweise** für das Projekt **ProjectExtension** die Option **umvdte** aus.

6. Ändern Sie im Fenster **Eigenschaften** die Eigenschaft **Interop-Typen einbetten** in **false**.

## <a name="define-the-new-sharepoint-project-property"></a>Definieren der neuen SharePoint-Projekt Eigenschaft
 Erstellen Sie eine Klasse, die die Projekt Erweiterung und das Verhalten der neuen Projekt Eigenschaft definiert. Zum Definieren der neuen Projekt Erweiterung implementiert die-Klasse die- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> Schnittstelle. Implementieren Sie diese Schnittstelle immer dann, wenn Sie eine Erweiterung für ein SharePoint-Projekt definieren möchten. Fügen Sie außerdem die der- <xref:System.ComponentModel.Composition.ExportAttribute> Klasse hinzu. Mit diesem Attribut können Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ihre-Implementierung ermitteln und laden <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> . Übergeben <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> Sie den Typ an den Konstruktor des Attributs.

#### <a name="to-define-the-new-sharepoint-project-property"></a>So definieren Sie die neue SharePoint-Projekt Eigenschaft

1. Fügen Sie den folgenden Code in die CustomProperty-Codedatei ein.

     [!code-vb[SPExt_ProjectExtension#1](../sharepoint/codesnippet/VisualBasic/projectextension/customproperty.vb#1)]
     [!code-csharp[SPExt_ProjectExtension#1](../sharepoint/codesnippet/CSharp/projectextension/customproperty.cs#1)]

## <a name="build-the-solution"></a>Erstellen der Projektmappe
 Erstellen Sie als nächstes die Projekt Mappe, um sicherzustellen, dass Sie fehlerfrei kompiliert wird.

#### <a name="to-build-the-solution"></a>So erstellen Sie die Projektmappe

1. Wählen Sie auf der Menüleiste **Erstellen** > **Projektmappe erstellen** aus.

## <a name="create-a-vsix-package-to-deploy-the-project-property-extension"></a>Erstellen eines VSIX-Pakets zum Bereitstellen der Projekteigenschaften Erweiterung
 Verwenden Sie zum Bereitstellen der Projekt Erweiterung das VSIX-Projekt in der Projekt Mappe, um ein VSIX-Paket zu erstellen. Konfigurieren Sie zuerst das VSIX-Paket, indem Sie die im VSIX-Projekt enthaltene Datei "source.extension.vsixmanifest" ändern. Erstellen Sie anschließend das VSIX-Paket, indem Sie die Lösung erstellen.

#### <a name="to-configure-and-create-the-vsix-package"></a>So erstellen und konfigurieren Sie das VSIX-Paket

1. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für die Datei "Source. Extension. vsixmanifest", und wählen Sie dann die Schaltfläche **Öffnen** aus.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Öffnet die Datei im Manifest-Designer. Die Informationen, die auf der Registerkarte **Metadaten** angezeigt werden, werden auch in den **Erweiterungen und Updates** angezeigt. Alle VSIX-Pakete benötigen die Dateierweiterung. vsixmanifest. Weitere Informationen zu dieser Datei finden Sie in der [Referenz zu VSIX-Erweiterungs Schema 1,0](/previous-versions/dd393700(v=vs.110)).

2. Geben Sie im Feld **Produkt Name** die **Eigenschaft benutzerdefiniertes Projekt** ein.

3. **Geben Sie** im Feld **Autor** den Text "" ein.

4. Geben Sie im Feld **Beschreibung** **eine benutzerdefinierte SharePoint-Projekt Eigenschaft ein, die die Zuordnung des Images-Ressourcen Ordners zum Projekt schaltet**.

5. Wählen Sie die Registerkarte **Assets** aus, und klicken Sie dann auf die Schaltfläche **neu** .

     Das Dialogfeld **Neues Objekt hinzufügen** wird angezeigt.

6. Wählen Sie in der Liste **Typ** den Eintrag **Microsoft. VisualStudio. MEFComponent** aus.

    > [!NOTE]
    > Dieser Wert entspricht dem `MEFComponent`-Element in der Datei "extension.vsixmanifest". Von diesem Element wird der Name einer Erweiterungsassembly im VSIX-Paket angegeben. Weitere Informationen finden Sie unter [MEFComponent-Element (VSX-Schema)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. Wählen Sie in der Liste **Quelle** das Optionsfeld **ein Projekt in der aktuellen Projekt** Mappe aus.

8. Wählen Sie in der Liste **Projekt** die Option **ProjectExtension** aus.

     Dieser Wert gibt den Namen der Assembly an, die Sie im Projekt aufbauen.

9. Wählen Sie **OK** aus, um das Dialogfeld **Neues Objekt hinzufügen** zu schließen.

10. Klicken Sie in der Menüleiste auf **Datei**  >  **Alle speichern** , wenn Sie fertig sind, und schließen Sie dann den Manifest-Designer.

11. Wählen Sie in der Menüleiste Buildprojektmappe **Erstellen** aus, und vergewissern Sie sich,  >  **Build Solution** dass das Projekt ohne Fehler kompiliert wird.

12. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für das Projekt **ProjectExtensionPackage** , und wählen Sie **im Datei-Explorer** die Schaltfläche Ordner öffnen aus.

13. Öffnen Sie im **Datei-Explorer** den Buildausgabeordner für das Projekt ProjectExtensionPackage, und überprüfen Sie dann, ob der Ordner eine Datei mit dem Namen ProjectExtensionPackage. vsix enthält.

     Standardmäßig handelt es sich beim Buildausgabeordner um den Ordner "...\bin\Debug" in dem Ordner mit der Projektdatei.

## <a name="test-the-project-property"></a>Testen der Projekt Eigenschaft
 Nun können Sie die benutzerdefinierte Projekt Eigenschaft testen. Am einfachsten ist es, die neue Projekteigenschaften Erweiterung in einer experimentellen Instanz von zu Debuggen und zu testen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Diese Instanz von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] wird erstellt, wenn Sie ein VSIX-Projekt oder ein anderes Erweiterbarkeits Projekt ausführen. Nachdem Sie das Projekt debuggt haben, können Sie die Erweiterung auf dem System installieren und dann in einer regulären Instanz von weiter Debuggen und testen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

#### <a name="to-debug-and-test-the-extension-in-an-experimental-instance-of-visual-studio"></a>So debuggen und testen Sie die Erweiterung in einer experimentellen Instanz von Visual Studio

1. Starten Sie mit Administrator Anmelde Informationen neu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , und öffnen Sie dann die Projekt Mappe ProjectExtensionPackage.

2. Starten Sie einen Debugbuild des Projekts, indem Sie entweder die **F5** -Taste drücken oder in der Menüleiste **Debuggen**  >  **Debuggen starten** auswählen.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] installiert die Erweiterung in%USERPROFILE%\appdata\local\microsoft\visualstudio\11.0exp\extensions\condeso\custom Project Property\1.0 und startet eine experimentelle Instanz von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

3. Erstellen Sie in der experimentellen Instanz von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ein SharePoint-Projekt für eine Farm Lösung, und verwenden Sie die Standardwerte für die anderen Werte im Assistenten.

    1. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**.

    2. Wählen Sie oben im Dialogfeld **Neues Projekt** in der Liste mit den .NET Framework Versionen **.NET Framework 3,5** aus.

         Erweiterungen für SharePoint-Tools erfordern Funktionen in dieser Version von [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] .

    3. Erweitern Sie unter dem Knoten **Vorlagen** den Knoten **Visual c#** oder **Visual Basic** , wählen Sie den Knoten **SharePoint** aus, und wählen Sie dann den Knoten **2010** aus.

    4. Wählen Sie die **SharePoint 2010-Projekt** Vorlage aus, und geben Sie dann **moduletest** als Namen für das Projekt ein.

4. Wählen Sie in **Projektmappen-Explorer** den Projekt Knoten **moduletest** aus.

     Im Fenster **Eigenschaften** wird ein neuer benutzerdefinierter Eigenschafts Zuordnungs **Bildordner** mit dem Standardwert **false** angezeigt.

5. Ändern Sie den Wert dieser Eigenschaft in **true**.

     Dem SharePoint-Projekt wird ein Bild Ressourcen Ordner hinzugefügt.

6. Ändern Sie den Wert dieser Eigenschaft zurück in **false**.

     Wenn Sie im Dialogfeld **Bilder Ordner löschen?** die Schaltfläche **Ja** auswählen, wird der Ressourcen Ordner Images aus dem SharePoint-Projekt gelöscht.

7. Schließen Sie die experimentelle Instanz von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

## <a name="see-also"></a>Weitere Informationen
- [Erweitern von SharePoint-Projekten](../sharepoint/extending-sharepoint-projects.md)
- [Gewusst wie: Hinzufügen einer Eigenschaft zu SharePoint-Projekten](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [Konvertieren zwischen SharePoint-Projekt Systemtypen und anderen Visual Studio-Projekttypen](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [Speichern von Daten in Erweiterungen des SharePoint-Projekt Systems](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [Zuordnen von benutzerdefinierten Daten zu SharePoint-Tools-Erweiterungen](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)