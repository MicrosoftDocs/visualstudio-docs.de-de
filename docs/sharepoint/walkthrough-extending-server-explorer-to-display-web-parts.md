---
title: 'Exemplarische Vorgehensweise: Erweitern von Server-Explorer zum anzeigen Webparts | Microsoft-Dokumentation'
titleSuffix: ''
description: Erweitern Sie in dieser exemplarischen Vorgehensweise Server-Explorer, sodass der Webpartkatalog auf jeder verbundenen SharePoint-Website angezeigt wird.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint commands
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: aa190ea6d5376c00584cc5936d1074d245b9509e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952667"
---
# <a name="walkthrough-extend-server-explorer-to-display-web-parts"></a>Exemplarische Vorgehensweise: Erweitern von Server-Explorer zum Anzeigen von Webparts
  In Visual Studio können Sie den Knoten **SharePoint-Verbindungen** von **Server-Explorer** verwenden, um Komponenten auf SharePoint-Sites anzuzeigen. Allerdings werden in **Server-Explorer** standardmäßig einige Komponenten nicht angezeigt. In dieser exemplarischen Vorgehensweise erweitern Sie **Server-Explorer** , sodass der Webpartkatalog auf jeder verbundenen SharePoint-Website angezeigt wird.

 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:

- Erstellen einer Visual Studio-Erweiterung, die **Server-Explorer** wie folgt erweitert:

  - Die Erweiterung fügt unter den einzelnen SharePoint-Website Knoten in **Server-Explorer** einen **Webpartkatalog** -Knoten hinzu. Dieser neue Knoten enthält untergeordnete Knoten, die die einzelnen Webparts in der webpartgalerie der Site darstellen.

  - Die Erweiterung definiert einen neuen Knotentyp, der eine webpartinstanz darstellt. Dieser neue Knotentyp ist die Grundlage für die untergeordneten Knoten unter dem neuen **webpartgalerie** -Knoten. Der neue Webpart-Knotentyp zeigt Informationen im **Eigenschaften** Fenster über das Webpart an, das es darstellt. Der Knotentyp enthält auch ein benutzerdefiniertes Kontextmenü Element, das Sie als Ausgangspunkt für andere Aufgaben verwenden können, die mit dem Webpart in Beziehung stehen.

- Erstellen Sie zwei benutzerdefinierte SharePoint-Befehle, die die Erweiterungsassembly aufruft. SharePoint-Befehle sind Methoden, die von Erweiterungsassemblys aufgerufen werden können, um APIs im Server-Objektmodell für SharePoint zu verwenden. In dieser exemplarischen Vorgehensweise erstellen Sie Befehle, mit denen webpartinformationen von der lokalen SharePoint-Website auf dem Entwicklungs Computer abgerufen werden. Weitere Informationen finden Sie unter " [Aufrufe in die SharePoint-Objekt Modelle](../sharepoint/calling-into-the-sharepoint-object-models.md)".

- Das Entwickeln eines Visual Studio-Erweiterungspakets (VSIX) zum Bereitstellen der Erweiterung.

- Debuggen und Testen der Erweiterung.

> [!NOTE]
> Eine Alternative Version dieser exemplarischen Vorgehensweise, in der das Client Objektmodell für SharePoint anstelle des Server Objektmodells verwendet wird, finden Sie unter Exemplarische Vorgehensweise [: Abrufen des SharePoint-Client Objektmodells in einer Server-Explorer-Erweiterung](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).

## <a name="prerequisites"></a>Voraussetzungen
 Zum Durchführen dieser exemplarischen Vorgehensweise werden auf dem Entwicklungscomputer die folgenden Komponenten benötigt:

- Unterstützte Editionen von Windows, SharePoint und Visual Studio.

- Das Visual Studio SDK. In dieser exemplarischen Vorgehensweise wird die **VSIX-Projekt** Vorlage im SDK verwendet, um ein VSIX-Paket zum Bereitstellen des Projekt Elements zu erstellen. Weitere Informationen finden Sie unter [Erweitern der SharePoint-Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Kenntnisse der folgenden Konzepte sind hilfreich, wenn auch für die Durchführung der exemplarischen Vorgehensweise nicht erforderlich:

- Verwenden des Server Objektmodells für SharePoint. Weitere Informationen finden Sie unter [Verwenden des SharePoint Foundation Server-Side-Objektmodells](/previous-versions/office/developer/sharepoint-2010/ee538251(v=office.14)).

- Webparts in SharePoint-Lösungen. Weitere Informationen finden Sie unter [Webparts Übersicht](/previous-versions/office/ms432401(v=office.14)).

## <a name="create-the-projects"></a>Erstellen der Projekte
 Um diese exemplarische Vorgehensweise abzuschließen, müssen Sie drei Projekte erstellen:

- Ein VSIX-Projekt, um das VSIX-Paket zum Bereitstellen der Erweiterung zu erstellen.

- Ein Klassen Bibliotheksprojekt, das die Erweiterung implementiert. Dieses Projekt muss den .NET Framework 4,5 als Ziel haben.

- Ein Klassen Bibliotheksprojekt, das die benutzerdefinierten SharePoint-Befehle definiert. Für dieses Projekt muss .NET Framework 3.5 als Zielversion verwendet werden.

  Beginnen Sie mit der exemplarischen Vorgehensweise, indem Sie beide Projekte erstellen.

#### <a name="to-create-the-vsix-project"></a>So erstellen Sie das VSIX-Projekt

1. Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**.

3. Erweitern Sie im Dialogfeld  **Neues Projekt** den Knoten **Visual c#** oder **Visual Basic** , und wählen Sie dann den Knoten **Erweiterbarkeit** aus.

    > [!NOTE]
    > Der **Erweiterbarkeits** Knoten ist nur verfügbar, wenn Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie weiter oben in diesem Thema im Abschnitt zu den erforderlichen Komponenten.

4. Wählen Sie oben im Dialogfeld **.NET Framework 4,5** in der Liste der .NET Framework Versionen aus.

5. Wählen Sie die Vorlage **VSIX-Projekt** aus, benennen Sie das Projekt **WebPartNode**, und klicken Sie dann auf die Schaltfläche **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]fügt **Projektmappen-Explorer** das **WebPartNode** -Projekt hinzu.

#### <a name="to-create-the-extension-project"></a>So erstellen Sie das Erweiterungsprojekt

1. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für den Projektmappenknoten, wählen Sie **Hinzufügen** aus, und wählen Sie dann **Neues Projekt** aus.

2. Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Visual c#** oder **Visual Basic** Knoten, und klicken Sie dann auf den Knoten **Windows** auswählen.

3. Wählen Sie oben im Dialogfeld **.NET Framework 4,5** in der Liste der .NET Framework Versionen aus.

4. Wählen Sie in der Liste der Projektvorlagen die Option **Klassenbibliothek** aus, benennen Sie das Projekt **WebPartNodeExtension**, und wählen Sie dann die Schaltfläche **OK** aus.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt der Projekt Mappe das **WebPartNodeExtension** -Projekt hinzu und öffnet die standardmäßige Class1-Codedatei.

5. Löschen Sie die Class1-Codedatei aus dem Projekt.

#### <a name="to-create-the-sharepoint-commands-project"></a>So erstellen Sie das SharePoint-Befehlsprojekt

1. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für den Projektmappenknoten, wählen Sie **Hinzufügen** aus, und wählen Sie dann **Neues Projekt** aus.

2. Erweitern Sie im Dialogfeld  **Neues Projekt** den Knoten **Visual c#** oder **Visual Basic** Knoten, und wählen Sie dann den Knoten **Windows** aus.

3. Wählen Sie oben im Dialogfeld **.NET Framework 3,5** in der Liste der .NET Framework Versionen aus.

4. Wählen Sie in der Liste der Projektvorlagen die Option **Klassenbibliothek** aus, benennen Sie das Projekt mit **webpartcommands**, und wählen Sie dann die Schaltfläche **OK** aus.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt der Projekt Mappe das **webpartcommands** -Projekt hinzu und öffnet die standardmäßige Class1-Codedatei.

5. Löschen Sie die Class1-Codedatei aus dem Projekt.

## <a name="configure-the-projects"></a>Konfigurieren der Projekte
 Bevor Sie Code schreiben, um die Erweiterung zu erstellen, müssen Sie Code Dateien und Assemblyverweise hinzufügen und die Projekteinstellungen konfigurieren.

#### <a name="to-configure-the-webpartnodeextension-project"></a>So konfigurieren Sie das WebPartNodeExtension-Projekt

1. Fügen Sie im Projekt WebPartNodeExtension vier Code Dateien mit den folgenden Namen hinzu:

    - SiteNodeExtension

    - Webpartnodebug-Provider

    - Webpartnodeinfo

    - Webpartcommandids

2. Öffnen Sie das Kontextmenü für das **WebPartNodeExtension** -Projekt, und wählen Sie dann **Verweis hinzufügen** aus.

3. Wählen Sie im Dialogfeld **Verweis-Manager-WebPartNodeExtension** die Registerkarte **Framework** aus, und aktivieren Sie dann das Kontrollkästchen für jede der folgenden Assemblys:

    - System.ComponentModel.Composition

    - System.Windows.Forms

4. Wählen Sie die Registerkarte **Erweiterungen** aus, aktivieren Sie das Kontrollkästchen für die Microsoft. VisualStudio. SharePoint-Assembly, und wählen Sie dann die Schaltfläche **OK** .

5. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für den Projekt Knoten **WebPartNodeExtension** , und wählen Sie dann **Eigenschaften** aus.

     Der **Projekt-Designer** wird geöffnet.

6. Wählen Sie die Registerkarte **Anwendung** aus.

7. Geben Sie im Feld **Standard Namespace** (c#) oder im Feld Stamm **Namespace** () den Wert [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] **Server Explorer. SharePointConnections. WebPartNode** ein.

#### <a name="to-configure-the-webpartcommands-project"></a>So konfigurieren Sie das webpartcommands-Projekt

1. Fügen Sie im webpartcommands-Projekt eine Codedatei mit dem Namen webpartcommands hinzu.

2. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für den Projekt Knoten **webpartcommands** , wählen Sie **Hinzufügen** aus, und wählen Sie dann **Vorhandenes Element** aus.

3. Navigieren Sie im Dialogfeld **Vorhandenes Element hinzufügen** zu dem Ordner, der die Code Dateien für das WebPartNodeExtension-Projekt enthält, und wählen Sie dann die Code Dateien webpartnodeinfo und webpartcommandids aus.

4. Wählen Sie den Pfeil neben der Schaltfläche **Hinzufügen** aus, und wählen Sie dann im angezeigten Menü die Option **als Link hinzufügen** aus.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt die Code Dateien dem Projekt webpartcommands als Links hinzu. Daher befinden sich die Code Dateien im WebPartNodeExtension-Projekt, der Code in den Dateien wird jedoch auch im webpartcommands-Projekt kompiliert.

5. Öffnen Sie erneut das Kontextmenü für das **webpartcommands** -Projekt, und wählen Sie **Verweis hinzufügen** aus.

6. Wählen Sie im Dialogfeld **Verweis-Manager-webpartbefehle** die Registerkarte **Erweiterungen** aus, aktivieren Sie das Kontrollkästchen für jede der folgenden Assemblys, und wählen Sie dann die Schaltfläche **OK** aus:

    - Microsoft.SharePoint

    - Microsoft.VisualStudio.SharePoint.Commands

7. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für das **webpartcommands** -Projekt erneut, und wählen Sie dann **Eigenschaften** aus.

     Der **Projekt-Designer** wird geöffnet.

8. Wählen Sie die Registerkarte **Anwendung** aus.

9. Geben Sie im Feld **Standard Namespace** (c#) oder im Feld Stamm **Namespace** () den Wert [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] **Server Explorer. SharePointConnections. WebPartNode** ein.

## <a name="create-icons-for-the-new-nodes"></a>Symbole für die neuen Knoten erstellen
 Erstellen Sie zwei Symbole für die **Server-Explorer** Erweiterung: ein Symbol für den neuen **Webpartkatalog** -Knoten und ein weiteres Symbol für jeden untergeordneten webpartknoten unter dem **Webpartkatalog** -Knoten. Später in dieser exemplarischen Vorgehensweise schreiben Sie Code, der diese Symbole den Knoten zuordnet.

#### <a name="to-create-icons-for-the-nodes"></a>So erstellen Sie Symbole für die Knoten

1. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für das **WebPartNodeExtension** -Projekt, und wählen Sie dann **Eigenschaften** aus.

2. Der **Projekt-Designer** wird geöffnet.

3. Wählen Sie die Registerkarte **Ressourcen** aus, und wählen Sie dann das **Projekt enthält keine Standard Ressourcen Datei aus. Klicken Sie hier, um einen Link zu erstellen** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] erstellt eine Ressourcen Datei und öffnet Sie im Designer.

4. Wählen Sie oben im Designer den Pfeil neben dem Menübefehl **Ressource hinzufügen** aus, und wählen Sie dann im angezeigten Menü die Option **Neues Symbol hinzufügen** aus.

5. Benennen Sie im Dialogfeld **neue Ressource hinzufügen** das neue Symbol **WebPartsNode**, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.

     Das neue Symbol wird im **Bild-Editor** geöffnet.

6. Bearbeiten Sie die 16x16-Version des Symbols, damit Sie über einen Entwurf verfügt, den Sie problemlos erkennen können.

7. Öffnen Sie das Kontextmenü für die 32 x 32-Version des Symbols, und wählen Sie dann **Bildtyp löschen** aus.

8. Wiederholen Sie die Schritte 5 bis 8, um den Projektressourcen ein zweites Symbol hinzuzufügen, und benennen Sie das Symbol **Webpart**.

9. Öffnen Sie in **Projektmappen-Explorer** im Ordner **Ressourcen** für das **WebPartNodeExtension** -Projekt das Kontextmenü für **WebPartsNode. ico**.

10. Wählen Sie im Fenster **Eigenschaften** den Pfeil neben **Build Action** aus, und wählen Sie dann im angezeigten Menü **eingebettete Ressource** aus.

11. Wiederholen Sie die letzten beiden Schritte für **WebPart. ico**.

## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>Fügen Sie den Webpart-Katalog Knoten zu Server-Explorer
 Erstellen Sie eine Klasse, die dem einzelnen SharePoint-Website Knoten den neuen **webpartgalerie** -Knoten hinzufügt. Um den neuen Knoten hinzuzufügen, implementiert die-Klasse die- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> Schnittstelle. Implementieren Sie diese Schnittstelle, wenn Sie das Verhalten eines vorhandenen Knotens in **Server-Explorer** erweitern möchten, z. b. durch Hinzufügen eines untergeordneten Knotens zu einem Knoten.

#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>So fügen Sie den Webpartkatalog-Knoten Server-Explorer hinzu

1. Öffnen Sie im Projekt WebPartNodeExtension die Codedatei SiteNodeExtension, und fügen Sie den folgenden Code in die Datei ein.

    > [!NOTE]
    > Nachdem Sie diesen Code hinzugefügt haben, enthält das Projekt einige Kompilierungsfehler, aber Sie werden entfernt, wenn Sie Code in späteren Schritten hinzufügen.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]

## <a name="define-a-node-type-that-represents-a-web-part"></a>Definieren eines Knoten Typs, der ein Webpart darstellt
 Erstellen Sie eine Klasse, die einen neuen Knotentyp definiert, der ein Webpart darstellt. Visual Studio verwendet diesen neuen Knotentyp, um untergeordnete Knoten unter dem **Webpartkatalog** -Knoten anzuzeigen. Jeder untergeordnete Knoten stellt ein einzelnes Webpart auf der SharePoint-Website dar.

 Um den neuen Knotentyp zu definieren, implementiert die-Klasse die- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> Schnittstelle. Implementieren Sie diese Schnittstelle immer dann, wenn Sie einen neuen Knotentyp in **Server-Explorer** definieren möchten.

#### <a name="to-define-the-web-part-node-type"></a>So definieren Sie den Webpart-Knotentyp

1. Öffnen Sie im WebPartNodeExtension-Projekt die Codedatei webpartnodetypeprovder, und fügen Sie den folgenden Code in die Datei ein.

     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodetypeprovider.cs#2)]

## <a name="define-the-web-part-data-class"></a>Definieren der Webpart-Datenklasse
 Definieren Sie eine Klasse, die Daten zu einem einzelnen Webpart auf der SharePoint-Website enthält. Später in dieser exemplarischen Vorgehensweise erstellen Sie einen benutzerdefinierten SharePoint-Befehl, der Daten zu jedem Webpart auf der Website abruft und die Daten dann Instanzen dieser Klasse zuweist.

#### <a name="to-define-the-web-part-data-class"></a>So definieren Sie die Webpart-Datenklasse

1. Öffnen Sie im WebPartNodeExtension-Projekt die webpartnodeinfo-Codedatei, und fügen Sie den folgenden Code in die Datei ein.

     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodeinfo.vb#3)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodeinfo.cs#3)]

## <a name="define-the-ids-for-the-sharepoint-commands"></a>Definieren der IDs für die SharePoint-Befehle
 Definieren Sie mehrere Zeichen folgen, die die benutzerdefinierten SharePoint-Befehle identifizieren. Sie implementieren diese Befehle später in dieser exemplarischen Vorgehensweise.

#### <a name="to-define-the-command-ids"></a>So definieren Sie die Befehls-IDs

1. Öffnen Sie im WebPartNodeExtension-Projekt die webpartcommandids-Codedatei, und fügen Sie den folgenden Code in die Datei ein.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartcommandids.cs#4)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartcommandids.vb#4)]

## <a name="create-the-custom-sharepoint-commands"></a>Erstellen der benutzerdefinierten SharePoint-Befehle
 Erstellen Sie benutzerdefinierte Befehle, die das Server Objektmodell für SharePoint aufrufen, um Daten zum Webparts auf der SharePoint-Website abzurufen. Jeder Befehl ist eine Methode, auf die <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> angewendet wird.

#### <a name="to-define-the-sharepoint-commands"></a>So definieren Sie die SharePoint-Befehle

1. Öffnen Sie im webpartcommands-Projekt die webpartcommands-Codedatei, und fügen Sie den folgenden Code in die Datei ein.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/CSharp/WebPartNode/WebPartCommands/WebPartCommands.cs#6)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartcommands/webpartcommands.vb#6)]

## <a name="checkpoint"></a>Prüfpunkt
 An dieser Stelle der exemplarischen Vorgehensweise befinden sich der gesamte Code für den **Webpartkatalog** -Knoten und die SharePoint-Befehle jetzt in den Projekten. Erstellen Sie die Lösung, um sicherzustellen, dass beide Projekte fehlerfrei kompiliert werden.

#### <a name="to-build-the-solution"></a>So erstellen Sie die Projektmappe

1. Wählen Sie auf der Menüleiste **Erstellen** > **Projektmappe erstellen** aus.

    > [!WARNING]
    > An diesem Punkt kann das WebPartNode-Projekt einen Buildfehler aufweisen, da die VSIX-Manifest-Datei keinen Wert für Author hat. Dieser Fehler wird entfernt, wenn Sie in späteren Schritten einen Wert hinzufügen.

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Erstellen eines VSIX-Pakets zum Bereitstellen der Erweiterung
 Zum Bereitstellen der Erweiterung erstellen Sie anhand des VSIX-Projekts in der Lösung ein VSIX-Paket. Konfigurieren Sie zunächst das VSIX-Paket, indem Sie die Datei "Source. Extension. vsixmanifest" im VSIX-Projekt ändern. Erstellen Sie anschließend das VSIX-Paket, indem Sie die Lösung erstellen.

#### <a name="to-configure-the-vsix-package"></a>So konfigurieren Sie das VSIX-Paket

1. Öffnen Sie in **Projektmappen-Explorer** im WebPartNode-Projekt die Datei " **Source. Extension. vsixmanifest** " im Manifest-Editor.

     Die Datei "source.extension.vsixmanifest" bildet die Grundlage für die Datei "extension.vsixmanifest", die für alle VSIX-Pakete erforderlich ist. Weitere Informationen zu dieser Datei finden Sie in der [Referenz zu VSIX-Erweiterungs Schema 1,0](/previous-versions/dd393700(v=vs.110)).

2. Geben Sie im Feld **Produkt Name** den **Webpartkatalog-Knoten für Server-Explorer** ein.

3. **Geben Sie** im Feld **Autor** den Text "" ein.

4. Geben Sie im Feld **Beschreibung** den Knoten **benutzerdefinierte webpartgalerie zum Knoten SharePoint-Verbindungen in Server-Explorer hinzu. Diese Erweiterung verwendet einen benutzerdefinierten SharePoint-Befehl, um das Server Objektmodell aufzurufen.**

5. Wählen Sie im Editor die Registerkarte **Objekte** aus, und klicken Sie dann auf die Schaltfläche **neu** .

     Das Dialogfeld **Neues Objekt hinzufügen** wird angezeigt.

6. Wählen Sie in der Liste **Typ** den Eintrag **Microsoft. VisualStudio. MEFComponent** aus.

    > [!NOTE]
    > Dieser Wert entspricht dem `MefComponent`-Element in der Datei "extension.vsixmanifest". Von diesem Element wird der Name einer Erweiterungsassembly im VSIX-Paket angegeben. Weitere Informationen finden Sie unter [MEFComponent-Element (VSX-Schema)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. Wählen Sie  in der Liste Quelle **ein Projekt in der aktuellen Projekt** Mappe aus.

8. Wählen Sie in der Liste **Projekt** die Option **WebPartNodeExtension** aus, und klicken Sie dann auf die Schaltfläche **OK** .

9. Wählen Sie im Manifest-Editor erneut die Schaltfläche **neu** aus.

     Das Dialogfeld **Neues Objekt hinzufügen** wird angezeigt.

10. Geben Sie im Feld **Typ** den Text **SharePoint. Commands. v4** ein.

    > [!NOTE]
    > Dieses Element gibt eine benutzerdefinierte Erweiterung an, die Sie in die Visual Studio-Erweiterung einschließen möchten. Weitere Informationen finden Sie unter [Asset-Element (VSX-Schema)](/previous-versions/dd393737(v=vs.110)).

11. Wählen Sie in der Liste **Quelle** das Element **ein Projekt in der aktuellen Projekt Mappe aus** .

12. Wählen Sie in der Liste **Projekt** die Option **webpartcommands** aus, und klicken Sie dann auf die Schaltfläche **OK** .

13. Wählen Sie in der Menüleiste Buildprojektmappe **Erstellen** aus, und vergewissern Sie sich,  >  dass die Projekt Mappe ohne Fehler kompiliert wird.

14. Stellen Sie sicher, dass der Buildausgabeordner für das WebPartNode-Projekt jetzt die Datei WebPartNode. vsix enthält.

     Standardmäßig handelt es sich beim Buildausgabeordner um den Ordner "...\bin\Debug" in dem Ordner mit der Projektdatei.

## <a name="test-the-extension"></a>Testen der Erweiterung
 Sie sind jetzt bereit, den neuen **Webpartkatalog** -Knoten in **Server-Explorer** zu testen. Beginnen Sie zunächst mit dem Debuggen der Erweiterung in einer experimentellen Instanz von Visual Studio. Verwenden Sie dann den neuen Knoten **Webparts** in der experimentellen Instanz von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

#### <a name="to-start-debugging-the-extension"></a>So debuggen Sie die Erweiterung

1. Starten Sie mit Administrator Anmelde Informationen neu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , und öffnen Sie dann die Projekt Mappe WebPartNode.

2. Öffnen Sie im WebPartNodeExtension-Projekt die Codedatei SiteNodeExtension, und fügen Sie der ersten Codezeile in der `NodeChildrenRequested` -Methode und der-Methode einen Haltepunkt hinzu `CreateWebPartNodes` .

3. Drücken Sie **F5** , um das Debuggen zu starten.

     Visual Studio installiert die Erweiterung in%USERPROFILE%\appdata\local\microsoft\visualstudio\11.0exp\extensions\condeso\web Part Gallery Node Extension for Server explorer\1.0 und startet eine experimentelle Instanz von Visual Studio. Sie testen das Projektelement in dieser Instanz von Visual Studio.

#### <a name="to-test-the-extension"></a>So testen Sie die Erweiterung

1. Wählen Sie in der experimentellen Instanz von in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] der Menüleiste Server-Explorer **anzeigen** aus  >  .

2. Führen Sie die folgenden Schritte aus, wenn die SharePoint-Website, die Sie zum Testen verwenden möchten, nicht unter dem Knoten **SharePoint-Verbindungen** in **Server-Explorer** angezeigt wird:

    1. Öffnen Sie in **Server-Explorer** das Kontextmenü für **SharePoint-Verbindungen**, und wählen Sie dann **Verbindung hinzufügen** aus.

    2. Geben Sie im Dialogfeld **SharePoint-Verbindung hinzufügen** die URL für die SharePoint-Website ein, mit der Sie eine Verbindung herstellen möchten, und klicken Sie dann auf die Schaltfläche **OK** .

         Geben Sie ein, um die SharePoint-Website auf dem Entwicklungs Computer anzugeben **http://localhost** .

3. Erweitern Sie den Knoten Standort Verbindung (der die URL Ihres Standorts anzeigt), und erweitern Sie dann einen untergeordneten Standort Knoten (z. b. **Team Site**).

4. Vergewissern Sie sich, dass der Code in der anderen Instanz von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] an dem Haltepunkt angehalten wird, den Sie zuvor in der `NodeChildrenRequested` -Methode festgelegt haben, und drücken Sie dann **F5** , um das Projekt zu Debuggen

5. Überprüfen Sie in der experimentellen Instanz von Visual Studio, ob ein neuer Knoten mit dem Namen **Webpartkatalog** unter dem Standort Knoten der obersten Ebene angezeigt wird, und erweitern Sie dann den Knoten **Webpartkatalog** .

6. Vergewissern Sie sich, dass der Code in der anderen Instanz von Visual Studio an dem Haltepunkt anhält, den Sie zuvor in der Methode festgelegt `CreateWebPartNodes` haben, und drücken Sie dann die Taste **F5** , um das Debuggen des Projekts fortzusetzen.

7. Überprüfen Sie in der experimentellen Instanz von Visual Studio, ob alle Webparts auf dem verbundenen Standort unter dem Knoten **Webpartkatalog** in **Server-Explorer** angezeigt werden.

8. Öffnen Sie in **Server-Explorer** das Kontextmenü für eine der Webparts, und wählen Sie dann **Eigenschaften** aus.

9. Vergewissern Sie sich, dass in der Instanz von, die [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Sie Debuggen, die Details zum Webpart im **Eigenschaften** Fenster angezeigt werden.

## <a name="uninstall-the-extension-from-visual-studio"></a>Deinstallieren der Erweiterung aus Visual Studio
 Nachdem Sie das Testen der Erweiterung abgeschlossen haben, deinstallieren Sie die Erweiterung aus Visual Studio.

#### <a name="to-uninstall-the-extension"></a>So deinstallieren Sie die Erweiterung

1. Wählen Sie in der experimentellen Instanz von in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] der Menüleiste Extras   >  **Erweiterungen und Updates** aus.

     Das Dialogfeld **Erweiterungen und Updates** wird geöffnet.

2. Wählen Sie in der Liste der Erweiterungen **für Server-Explorer Webpart-Katalog Knoten Erweiterung aus**, und klicken Sie dann auf die Schaltfläche **deinstallieren** .

3. Wählen Sie im angezeigten Dialogfeld die Schaltfläche **Ja** , um zu bestätigen, dass Sie die Erweiterung deinstallieren möchten, und wählen Sie dann die Schaltfläche **jetzt neu starten** aus, um die Deinstallation abzuschließen.

4. Schließen Sie beide Instanzen von Visual Studio (die experimentelle Instanz und die Instanz von Visual Studio, in der die WebPartNode-Projekt Mappe geöffnet ist).

## <a name="see-also"></a>Weitere Informationen
- [Erweitern des Knotens „SharePoint-Verbindungen“ im Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Exemplarische Vorgehensweise: Abrufen des SharePoint-Client Objektmodells in einer Server-Explorer-Erweiterung](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)
- [Bildbearbeitung für Symbole](/cpp/windows/image-editor-for-icons)
- [Erstellen eines Symbols oder anderen Bilds &#40;Bildbearbeitung für Symbole&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)