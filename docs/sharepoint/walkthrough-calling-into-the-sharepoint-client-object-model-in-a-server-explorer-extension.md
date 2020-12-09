---
title: 'Server-Explorer: Erweitern des SharePoint-Verbindungs Knotens'
titleSuffix: ''
description: In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie das SharePoint-Client Objektmodell aus einer Erweiterung für den Knoten SharePoint-Verbindungen in Server-Explorer abrufen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint commands [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c323f05d341af810eecafae43e8d04d3cba29054
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96913944"
---
# <a name="walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension"></a>Exemplarische Vorgehensweise: Aufrufen des SharePoint-Client Objektmodells in einer Server-Explorer-Erweiterung
  In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie das SharePoint-Client Objektmodell aus einer Erweiterung für den Knoten **SharePoint-Verbindungen** in **Server-Explorer** aufgerufen wird. Weitere Informationen zur Verwendung des SharePoint-Client Objektmodells finden Sie unter " [Aufrufe in die SharePoint-Objekt Modelle](../sharepoint/calling-into-the-sharepoint-object-models.md)".

 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:

- Erstellen einer [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Erweiterung, die den Knoten **SharePoint-Verbindungen** von **Server-Explorer** auf folgende Weise erweitert:

  - Die Erweiterung fügt unter den einzelnen SharePoint-Website Knoten in **Server-Explorer** einen **Webpartkatalog** -Knoten hinzu. Dieser neue Knoten enthält untergeordnete Knoten, die die einzelnen Webparts in der webpartgalerie der Site darstellen.

  - Die Erweiterung definiert einen neuen Knotentyp, der eine webpartinstanz darstellt. Dieser neue Knotentyp ist die Grundlage für die untergeordneten Knoten unter dem neuen **webpartgalerie** -Knoten. Der neue Webpart-Knotentyp zeigt Informationen im **Eigenschaften** Fenster über das Webpart an, das der Knoten darstellt.

- Das Entwickeln eines Visual Studio-Erweiterungspakets (VSIX) zum Bereitstellen der Erweiterung.

- Debuggen und Testen der Erweiterung.

> [!NOTE]
> Die Erweiterung, die Sie in dieser exemplarischen Vorgehensweise erstellen, ähnelt der in Exemplarische Vorgehensweise [: Erweitern von Server-Explorer zum Anzeigen von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)erstellten Erweiterung. In dieser exemplarischen Vorgehensweise wird das SharePoint-Server Objektmodell verwendet, in dieser exemplarischen Vorgehensweise werden jedoch die gleichen Aufgaben durch die Verwendung des Client Objektmodells ausgeführt.

## <a name="prerequisites"></a>Voraussetzungen
 Zum Durchführen dieser exemplarischen Vorgehensweise werden auf dem Entwicklungscomputer die folgenden Komponenten benötigt:

- Unterstützte Editionen von Windows, SharePoint und Visual Studio.

- Das Visual Studio SDK. In dieser exemplarischen Vorgehensweise wird die **VSIX-Projekt** Vorlage im SDK verwendet, um ein VSIX-Paket zum Bereitstellen der Erweiterung zu erstellen. Weitere Informationen finden Sie unter [Erweitern der SharePoint-Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

Kenntnisse der folgenden Konzepte sind hilfreich, wenn auch für die Durchführung der exemplarischen Vorgehensweise nicht erforderlich:

- Verwenden des SharePoint-Client Objektmodells. Weitere Informationen finden Sie unter [verwaltetes Client Objektmodell](/previous-versions/office/developer/sharepoint-2010/ee537247(v=office.14)).

- Webparts in SharePoint. Weitere Informationen finden Sie unter [Webparts Übersicht](/previous-versions/office/ms432401(v=office.14)).

## <a name="create-the-projects"></a>Erstellen der Projekte
 Um diese exemplarische Vorgehensweise abzuschließen, müssen Sie zwei Projekte erstellen:

- Ein VSIX-Projekt zum Erstellen des VSIX-Pakets zum Bereitstellen der **Server-Explorer** Erweiterung.

- Ein Klassen Bibliotheksprojekt, das die **Server-Explorer** Erweiterung implementiert.

  Beginnen Sie mit der exemplarischen Vorgehensweise, indem Sie beide Projekte erstellen.

#### <a name="to-create-the-vsix-project"></a>So erstellen Sie das VSIX-Projekt

1. Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**.

3. Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Visual c#** oder **Visual Basic** , und wählen Sie dann **Erweiterbarkeit** aus.

    > [!NOTE]
    > Der **Erweiterbarkeits** Knoten ist nur verfügbar, wenn Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie weiter oben in diesem Thema im Abschnitt zu den erforderlichen Komponenten.

4. Wählen Sie oben im Dialogfeld **.NET Framework 4,5** in der Liste der .NET Framework Versionen aus.

     Erweiterungen für SharePoint-Tools erfordern Features in dieser Version der .NET Framework.

5. Wählen Sie die **VSIX-Projekt** Vorlage aus.

6. Geben Sie im Feld **Name den Namen** **WebPartNode** ein, und klicken Sie dann auf die Schaltfläche **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]fügt **Projektmappen-Explorer** das **WebPartNode** -Projekt hinzu.

#### <a name="to-create-the-extension-project"></a>So erstellen Sie das Erweiterungsprojekt

1. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für den Projektmappenknoten, wählen Sie **Hinzufügen** aus, und wählen Sie dann **Neues Projekt** aus.

2. Erweitern Sie im Dialogfeld  **Neues Projekt** den Knoten **Visual c#** oder **Visual Basic** , und wählen Sie dann **Windows** aus.

3. Wählen Sie oben im Dialogfeld **.NET Framework 4,5** in der Liste der .NET Framework Versionen aus.

4. Wählen Sie in der Liste der Projektvorlagen die Option **Klassenbibliothek** aus.

5. Geben Sie im Feld **Name den Namen** **WebPartNodeExtension** ein, und klicken Sie dann auf die Schaltfläche **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt der Projekt Mappe das **WebPartNodeExtension** -Projekt hinzu und öffnet die standardmäßige Class1-Codedatei.

6. Löschen Sie die Class1-Codedatei aus dem Projekt.

## <a name="configure-the-extension-project"></a>Konfigurieren des Erweiterungsprojekts
 Bevor Sie Code schreiben, um die Erweiterung zu erstellen, müssen Sie dem Projekt Code Dateien und Assemblyverweise hinzufügen, und Sie müssen den Standard Namespace aktualisieren.

#### <a name="to-configure-the-project"></a>So konfigurieren Sie das Projekt

1. Fügen Sie im Projekt **WebPartNodeExtension** zwei Code Dateien mit den Namen SiteNodeExtension und WebPartNodeTypeProvider hinzu.

2. Öffnen Sie das Kontextmenü für das WebPartNodeExtension-Projekt, und wählen Sie dann **Verweis hinzufügen** aus.

3. Wählen Sie im Dialogfeld **Verweis-Manager-WebPartNodeExtension** den Knoten **Framework** aus, und aktivieren Sie dann die Kontrollkästchen für die Assemblys System. ComponentModel. Composition und System. Windows. Forms.

4. Wählen Sie den Knoten **Erweiterungen** aus, aktivieren Sie das Kontrollkästchen für jede der folgenden Assemblys, und wählen Sie dann die Schaltfläche **OK** aus:

    - Microsoft. SharePoint. Client

    - Microsoft. SharePoint. Client. Runtime

    - Microsoft.VisualStudio.SharePoint

5. Öffnen Sie das Kontextmenü für das **WebPartNodeExtension** -Projekt, und wählen Sie dann **Eigenschaften** aus.

     Der **Projekt-Designer** wird geöffnet.

6. Wählen Sie die Registerkarte **Anwendung** aus.

7. Geben Sie im Feld **Standard Namespace** (c#) oder im Feld Stamm **Namespace** (Visual Basic) den Wert **Server Explorer. SharePointConnections. WebPartNode** ein.

## <a name="create-icons-for-the-new-nodes"></a>Symbole für die neuen Knoten erstellen
 Erstellen Sie zwei Symbole für die **Server-Explorer** Erweiterung: ein Symbol für den neuen **Webpartkatalog** -Knoten und ein weiteres Symbol für jeden untergeordneten webpartknoten unter dem **Webpartkatalog** -Knoten. Später in dieser exemplarischen Vorgehensweise schreiben Sie Code, der diese Symbole den Knoten zuordnet.

#### <a name="to-create-icons-for-the-nodes"></a>So erstellen Sie Symbole für die Knoten

1. Wählen Sie im **Projekt-Designer** für das WebPartNodeExtension-Projekt die Registerkarte **Ressourcen** aus.

2. Wählen Sie den Link **dieses Projekt enthält keine Standard Ressourcen Datei aus. Klicken Sie hier, um eine zu erstellen.**

     Visual Studio erstellt eine Ressourcen Datei und öffnet Sie im Designer.

3. Wählen Sie oben im Designer den Pfeil im Menübefehl **Ressource hinzufügen** aus, und wählen Sie dann **Neues Symbol hinzufügen** aus.

4. Geben Sie für den neuen Symbolnamen **WebPartsNode** ein, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.

     Das neue Symbol wird im **Bild-Editor** geöffnet.

5. Bearbeiten Sie die 16x16-Version des Symbols, damit Sie über einen Entwurf verfügt, den Sie problemlos erkennen können.

6. Öffnen Sie das Kontextmenü für die 32 x 32-Version des Symbols, und wählen Sie dann **Bildtyp löschen** aus.

7. Wiederholen Sie die Schritte 3 bis 7, um den Projektressourcen ein zweites Symbol hinzuzufügen, und benennen Sie das Symbol **Webpart**.

8. Wählen Sie in **Projektmappen-Explorer** im **Ressourcen** Ordner für das **WebPartNodeExtension** -Projekt *WebPartsNode. ico* aus.

9. Öffnen **Sie im Fenster** **Eigenschaften** die Liste Buildvorgang, und wählen Sie dann **eingebettete Ressource** aus.

10. Wiederholen Sie die letzten beiden Schritte für *WebPart. ico*.

## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>Fügen Sie den Webpart-Katalog Knoten zu Server-Explorer
 Erstellen Sie eine Klasse, die dem einzelnen SharePoint-Website Knoten den neuen **webpartgalerie** -Knoten hinzufügt. Um den neuen Knoten hinzuzufügen, implementiert die-Klasse die- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> Schnittstelle. Implementieren Sie diese Schnittstelle immer dann, wenn Sie das Verhalten eines vorhandenen Knotens in **Server-Explorer** erweitern möchten, z. b. durch Hinzufügen eines neuen untergeordneten Knotens zu einem Knoten.

#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>So fügen Sie den Webpartkatalog-Knoten Server-Explorer hinzu

1. Fügen Sie den folgenden Code in die Codedatei **SiteNodeExtension** für das **WebPartNodeExtension** -Projekt ein.

    > [!NOTE]
    > Nach dem Hinzufügen dieses Codes weist das Projekt einige Kompilierungsfehler auf. Diese Fehler werden durch Code behoben, den Sie in späteren Schritten hinzufügen.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]

## <a name="define-a-node-type-that-represents-a-web-part"></a>Definieren eines Knoten Typs, der ein Webpart darstellt
 Erstellen Sie eine Klasse, die einen neuen Knotentyp definiert, der ein Webpart darstellt. Visual Studio verwendet diesen neuen Knotentyp, um untergeordnete Knoten unter dem **Webpartkatalog** -Knoten anzuzeigen. Jeder dieser untergeordneten Knoten stellt ein einzelnes Webpart auf der SharePoint-Website dar.

 Um den neuen Knotentyp zu definieren, implementiert die-Klasse die- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> Schnittstelle. Implementieren Sie diese Schnittstelle immer dann, wenn Sie einen neuen Knotentyp in **Server-Explorer** definieren möchten.

#### <a name="to-define-the-web-part-node-type"></a>So definieren Sie den Webpart-Knotentyp

1. Fügen Sie den folgenden Code in die Codedatei **WebPartNodeTypeProvider** für das **WebPartNodeExtension** -Projekt ein.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/webpartnodetypeprovider.cs#2)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]

## <a name="checkpoint"></a>Prüfpunkt
 An dieser Stelle der exemplarischen Vorgehensweise befindet sich der gesamte Code für den **Webpartkatalog** -Knoten jetzt im Projekt. Erstellen Sie das **WebPartNodeExtension** -Projekt, um sicherzustellen, dass es ohne Fehler kompiliert wird.

#### <a name="to-build-the-project"></a>So erstellen Sie das Projekt

1. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für das **WebPartNodeExtension** -Projekt, und wählen Sie dann **Erstellen** aus.

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Erstellen eines VSIX-Pakets zum Bereitstellen der Erweiterung
 Zum Bereitstellen der Erweiterung erstellen Sie anhand des VSIX-Projekts in der Lösung ein VSIX-Paket. Konfigurieren Sie zunächst das VSIX-Paket durch Ändern der Datei "Source. Extension. vsixmanifest", die im Projekt enthalten ist. Erstellen Sie dann das VSIX-Paket, indem Sie die Lösung erstellen.

#### <a name="to-configure-the-vsix-package"></a>So konfigurieren Sie das VSIX-Paket

1. Öffnen Sie in **Projektmappen-Explorer** im **WebPartNode** -Projekt im Manifest-Editor die Datei " **Source. Extension. vsixmanifest** ".

     Die Datei "source.extension.vsixmanifest" bildet die Grundlage für die Datei "extension.vsixmanifest", die für alle VSIX-Pakete erforderlich ist. Weitere Informationen zu dieser Datei finden Sie in der [Referenz zu VSIX-Erweiterungs Schema 1,0](/previous-versions/dd393700(v=vs.110)).

2. Geben Sie im Feld **Produkt Name** den **Webpartkatalog-Knoten für Server-Explorer** ein.

3. **Geben Sie** im Feld **Autor** den Text "" ein.

4. Geben Sie im Feld **Beschreibung** den Knoten **benutzerdefinierte webpartgalerie zum Knoten SharePoint-Verbindungen in Server-Explorer hinzu**.

5. Wählen Sie im Editor auf der Registerkarte **Objekte** die Schaltfläche **neu** aus.

6. Wählen Sie im Dialogfeld **Neues Objekt hinzufügen** in der Liste **Typ** den Eintrag **Microsoft. VisualStudio. MEFComponent** aus.

    > [!NOTE]
    > Dieser Wert entspricht dem `MefComponent`-Element in der Datei "extension.vsixmanifest". Von diesem Element wird der Name einer Erweiterungsassembly im VSIX-Paket angegeben. Weitere Informationen finden Sie unter [MEFComponent-Element (VSX-Schema)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. Wählen Sie **Source** in der Liste Quelle **ein Projekt in der aktuellen Projekt** Mappe aus.

8. Wählen Sie in der Liste **Projekt** die Option **WebPartNodeExtension** aus, und klicken Sie dann auf die Schaltfläche **OK** .

9. Wählen Sie in der Menüleiste Buildprojektmappe **Erstellen** aus, und vergewissern Sie sich,  >  **Build Solution** dass die Projekt Mappe ohne Fehler kompiliert wird.

10. Stellen Sie sicher, dass der Buildausgabeordner für das WebPartNode-Projekt jetzt die Datei WebPartNode. vsix enthält.

     Standardmäßig handelt es sich beim Buildausgabeordner um den Ordner "...\bin\Debug" in dem Ordner mit der Projektdatei.

## <a name="test-the-extension"></a>Testen der Erweiterung
 Sie können nun den neuen **Webpartkatalog** -Knoten in **Server-Explorer** testen. Beginnen Sie zunächst mit dem Debuggen des Erweiterungsprojekts in einer experimentellen Instanz von Visual Studio. Verwenden Sie dann den neuen Knoten **Webparts** in der experimentellen Instanz von Visual Studio.

#### <a name="to-start-debugging-the-extension"></a>So debuggen Sie die Erweiterung

1. Starten Sie Visual Studio mit Administrator Anmelde Informationen neu, und öffnen Sie dann die Projekt Mappe **WebPartNode** .

2. Öffnen Sie im WebPartNodeExtension-Projekt die Codedatei **SiteNodeExtension** , und fügen Sie dann einen Haltepunkt zu den ersten Codezeilen in der `NodeChildrenRequested` -Methode und der- `CreateWebPartNodes` Methode hinzu.

3. Drücken Sie **F5** , um das Debuggen zu starten.

     Visual Studio installiert die Erweiterung in%USERPROFILE%\appdata\local\microsoft\visualstudio\11.0exp\extensions\condeso\web Part Gallery Node Extension for Server explorer\1.0 und startet eine experimentelle Instanz von Visual Studio. Sie testen das Projektelement in dieser Instanz von Visual Studio.

#### <a name="to-test-the-extension"></a>So testen Sie die Erweiterung

1. Wählen Sie in der experimentellen Instanz von Visual Studio auf der Menüleiste Server-Explorer **anzeigen** aus  >  **Server Explorer**.

2. Vergewissern Sie sich, dass die SharePoint-Website, die Sie für Tests verwenden möchten, unter dem Knoten **SharePoint-Verbindungen** in **Server-Explorer** angezeigt wird. Wenn Sie nicht aufgeführt ist, führen Sie die folgenden Schritte aus:

    1. Öffnen Sie das Kontextmenü für **SharePoint-Verbindungen**, und wählen Sie dann **Verbindung hinzufügen** aus.

    2. Geben Sie im Dialogfeld **SharePoint-Verbindung hinzufügen** die URL für die SharePoint-Website ein, mit der Sie eine Verbindung herstellen möchten, und klicken Sie dann auf die Schaltfläche **OK** .

         Geben Sie ein, um die SharePoint-Website auf dem Entwicklungs Computer anzugeben **http://localhost** .

3. Erweitern Sie den Knoten Standort Verbindung (der die URL Ihres Standorts anzeigt), und erweitern Sie dann einen untergeordneten Standort Knoten (z. b. **Team Site**).

4. Vergewissern Sie sich, dass der Code in der anderen Instanz von Visual Studio an dem Haltepunkt anhält, den Sie zuvor in der Methode festgelegt `NodeChildrenRequested` haben, und drücken Sie dann die Taste **F5** , um das Debuggen des Projekts fortzusetzen.

5. Erweitern Sie in der experimentellen Instanz von Visual Studio den Knoten **Webpartkatalog** , der unter dem Standort Knoten der obersten Ebene angezeigt wird.

6. Vergewissern Sie sich, dass der Code in der anderen Instanz von Visual Studio an dem Haltepunkt anhält, den Sie zuvor in der Methode festgelegt `CreateWebPartNodes` haben, und drücken Sie dann die Taste **F5** , um das Debuggen des Projekts fortzusetzen.

7. Überprüfen Sie in der experimentellen Instanz von Visual Studio, ob alle Webparts auf dem verbundenen Standort unter dem Knoten **Webpartkatalog** in **Server-Explorer** angezeigt werden.

8. Öffnen Sie das Kontextmenü für ein Webpart, und wählen Sie dann **Eigenschaften** aus.

9. Vergewissern Sie sich, dass im Fenster **Eigenschaften** die Details zum Webpart angezeigt werden.

10. Öffnen Sie in **Server-Explorer** das Kontextmenü für das gleiche Webpart, und wählen Sie dann **Meldung anzeigen** aus.

     Wählen Sie im angezeigten Meldungs Feld die Schaltfläche **OK** aus.

## <a name="uninstall-the-extension-from-visual-studio"></a>Deinstallieren der Erweiterung aus Visual Studio
 Nachdem Sie das Testen der Erweiterung abgeschlossen haben, deinstallieren Sie diese aus Visual Studio.

#### <a name="to-uninstall-the-extension"></a>So deinstallieren Sie die Erweiterung

1. Wählen Sie in der experimentellen Instanz von Visual Studio auf der Menüleiste Extras **Tools**  >  **Erweiterungen und Updates** aus.

     Das Dialogfeld **Erweiterungen und Updates** wird geöffnet.

2. Wählen Sie in der Liste der Erweiterungen den **Knoten Webpartkatalog aus**, und wählen Sie dann die Schaltfläche **deinstallieren** Server-Explorer aus.

3. Wählen Sie im angezeigten Dialogfeld die Schaltfläche **Ja** aus.

4. Wählen Sie die Schaltfläche **jetzt neu starten** aus, um die Installation abzuschließen.

     Das Projekt Element wird ebenfalls deinstalliert.

5. Schließen Sie beide Instanzen von Visual Studio (die experimentelle Instanz und die Instanz von Visual Studio, in der die WebPartNode-Projekt Mappe geöffnet ist).

## <a name="see-also"></a>Weitere Informationen
- [Aufrufe in die SharePoint-Objekt Modelle](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Erweitern des Knotens „SharePoint-Verbindungen“ im Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Exemplarische Vorgehensweise: Erweitern von Server-Explorer zum Anzeigen von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Bildbearbeitung für Symbole](/cpp/windows/image-editor-for-icons)
- [Erstellen eines Symbols oder anderen Bilds &#40;Bildbearbeitung für Symbole&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)