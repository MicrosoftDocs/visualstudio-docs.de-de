---
title: Bereitstellen von Erweiterungen für die SharePoint-Tools in Visual Studio | Microsoft-Dokumentation
description: Stellen Sie Erweiterungen für SharePoint-Tools in Visual Studio bereit. Verwenden Sie Projekte der Visual Studio-Erweiterung (VSIX), um VSIX-Pakete zu erstellen.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying extensions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9c8b05b5cb74a28157436f95f01992515c716e6a
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672677"
---
# <a name="deploy-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Bereitstellen von Erweiterungen für die SharePoint-Tools in Visual Studio

Erstellen Sie zum Bereitstellen einer Erweiterung für SharePoint-Tools ein [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Erweiterungspaket (VSIX), das die Erweiterungsassembly und alle anderen Dateien enthält, die Sie mit der Erweiterung verteilen möchten. Bei einem VSIX-Paket handelt es sich um eine komprimierte Datei, die dem OPC-Standard (Open Packaging Conventions) folgt. VSIX-Pakete verfügen über die Erweiterung *. vsix* .

Nachdem Sie ein VSIX-Paket erstellt haben, können andere Benutzer die vsix-Datei ausführen, um die Erweiterung zu installieren. Wenn ein Benutzer die Erweiterung installiert, werden alle Dateien im Ordner%UserProfile%\appdata\local\microsoft\visualstudio\11.0\Extensions installiert. Zum Bereitstellen der Erweiterung können Sie das VSIX-Paket auf die [Visual Studio Marketplace](https://marketplace.visualstudio.com/) -Website hochladen, oder Sie können das Paket auf andere Weise an Ihre Kunden verteilen, z. b. das Hosting des Pakets auf einer Netzwerkfreigabe oder eine andere Website.

Weitere Informationen zum Erstellen von VSIX-Paketen und deren Bereitstellung für die [Visual Studio Marketplace](https://marketplace.visualstudio.com/)finden Sie unter [Shipping Visual Studio Extensions](../extensibility/shipping-visual-studio-extensions.md).

 Sie können ein VSIX-Paket erstellen, indem Sie die **VSIX-Projekt** Vorlage in Visual Studio verwenden, oder Sie können ein VSIX-Paket manuell erstellen.

## <a name="use-vsix-projects-to-create-vsix-packages"></a>Verwenden von VSIX-Projekten zum Erstellen von VSIX-Paketen

Mit der **VSIX-Projekt** Vorlage, die vom Visual Studio SDK bereitgestellt wird, können VSIX-Pakete für Erweiterungen für SharePoint-Tools erstellt werden. Die Verwendung eines VSIX-Projekts bietet verschiedene Vorteile gegenüber der manuellen Erstellung eines VSIX-Pakets:

- Visual Studio generiert automatisch das VSIX-Paket, wenn Sie das Projekt erstellen. Aufgaben, wie z. b. das Hinzufügen der Bereitstellungs Dateien zum Paket und das Erstellen der Datei [Content_Types]. XML für das Paket, werden für Sie ausgeführt.

- Sie können das VSIX-Projekt so konfigurieren, dass die Buildausgabe des Erweiterungsprojekts und andere Dateien (z. b. Projektvorlagen und Element Vorlagen) im VSIX-Paket enthalten sind.

Weitere Informationen zur Verwendung eines VSIX-Projekts finden Sie unter [VSIX-Projektvorlage](../extensibility/vsix-project-template.md).

### <a name="organize-your-projects"></a>Organisieren von Projekten

Standardmäßig generieren VSIX-Projekte nur VSIX-Pakete, nicht Assemblys. Daher implementieren Sie in der Regel keine SharePoint-Tools-Erweiterung in einem VSIX-Projekt. Im Allgemeinen arbeiten Sie mit mindestens zwei Projekten:

- Ein VSIX-Projekt.

- Ein Klassen Bibliotheksprojekt, das Ihre Erweiterung implementiert.

Sie können auch mit zusätzlichen Projekten für bestimmte Erweiterungs Typen arbeiten:

- Ein Klassen Bibliotheksprojekt, das alle SharePoint-Befehle implementiert, die von der Erweiterung verwendet werden. Eine exemplarische Vorgehensweise, die dieses Szenario veranschaulicht, finden Sie unter Exemplarische Vorgehensweise [: Erweitern von Server-Explorer zum Anzeigen von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

- Eine Element Vorlage oder ein Projektvorlagen Projekt, das eine Element Vorlage oder eine Projektvorlage erstellt, wenn die Erweiterung einen neuen Typ von SharePoint-Projekt Element definiert. Eine exemplarische Vorgehensweise, die dieses Szenario veranschaulicht, finden Sie unter Exemplarische [Vorgehensweise: Erstellen eines benutzerdefinierten Aktionsprojekt Elements mit einer Element Vorlage, Teil 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

- Ein Klassen Bibliotheksprojekt, das einen benutzerdefinierten Assistenten für eine Element Vorlage oder eine Projektvorlage implementiert, wenn die Erweiterung eine Vorlage enthält. Eine exemplarische Vorgehensweise, die dieses Szenario veranschaulicht, finden Sie unter Exemplarische [Vorgehensweise: Erstellen eines benutzerdefinierten Aktionsprojekt Elements mit einer Element Vorlage, Teil 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

Wenn Sie alle Projekte in dieselbe Visual Studio-Projekt Mappe einschließen, können Sie die Datei "Source. Extension. vsixmanifest" im VSIX-Projekt so ändern, dass Sie die Buildausgabe der Klassen Bibliotheks Projekte einschließt.

### <a name="edit-the-vsix-manifest"></a>VSIX-Manifest bearbeiten

Sie müssen die Datei "Source. Extension. vsixmanifest" im VSIX-Projekt bearbeiten, um Einträge für alle Elemente einzuschließen, die Sie in die Erweiterung einschließen möchten. Wenn Sie die Datei "Source. Extension. vsixmanifest" über das Kontextmenü öffnen, wird die Datei in einem Designer angezeigt, der eine Benutzeroberfläche zum Bearbeiten des XML-Codes in der Datei bereitstellt. Weitere Informationen finden Sie unter [VSIX Manifest-Designer](../extensibility/vsix-manifest-designer.md).

Sie müssen der Datei "Source. Extension. vsixmanifest" Einträge für die folgenden Elemente hinzufügen:

- Die Erweiterungsassembly.

- Die Assembly, die alle SharePoint-Befehle implementiert, die von der Erweiterung verwendet werden.

- Alle Projektvorlagen oder Element Vorlagen, die der Erweiterung zugeordnet sind.

- Ein benutzerdefinierter Assistent für eine Vorlage, die der Erweiterung zugeordnet ist.

In den folgenden Prozeduren wird beschrieben, wie Sie für jedes dieser Elemente der vsixmanifest-Datei Einträge hinzufügen.

#### <a name="to-include-the-extension-assembly"></a>So schließen Sie die Erweiterungsassembly ein

1. Öffnen Sie im VSIX-Projekt das Kontextmenü für die Datei "Source. Extension. vsixmanifest", und wählen Sie dann **Öffnen** aus.

     Die Datei wird im Designer geöffnet.

2. Wählen Sie im Editor auf der Registerkarte **Objekte** die Schaltfläche **neu** aus.

     Das Dialogfeld **Neues Objekt hinzufügen** wird geöffnet.

3. Wählen Sie in der Liste **Typ** den Eintrag **Microsoft. VisualStudio. MEFComponent** aus.

4. Führen Sie in der Liste **Quelle** einen der folgenden Schritte aus:

    - Wenn die Erweiterungsassembly aus einem Projekt erstellt wird, das sich in derselben Projekt Mappe wie das VSIX-Projekt befindet, wählen Sie **ein Projekt in der aktuellen** Projekt Mappe aus. Wählen Sie in der Liste **Projekt** den Namen des Projekts aus.

    - Wenn die Erweiterungsassembly als Datei in Ihrem Projekt enthalten ist, wählen Sie **Datei im Dateisystem** aus. Geben Sie in der Liste **Pfad** den vollständigen Pfad der Erweiterungs-Assemblydatei ein, oder verwenden Sie die Schaltfläche **Durchsuchen** , um die Assemblydatei zu suchen und auszuwählen

5. Klicken Sie auf die Schaltfläche **OK** .

#### <a name="to-include-a-sharepoint-command-assembly"></a>So schließen Sie eine SharePoint-befehlsassembly ein

1. Öffnen Sie im VSIX-Projekt das Kontextmenü für die Datei "Source. Extension. vsixmanifest", und wählen Sie dann die Schaltfläche **Öffnen** aus.

     Die Datei wird im Designer geöffnet.

2. Klicken Sie im Abschnitt **Assets** des Editors auf die Schaltfläche **neu** .

     Das Dialogfeld **Neues Objekt hinzufügen** wird geöffnet.

3. Geben Sie im Feld **Typ** den Text **SharePoint. Commands. v4** ein.

4. Führen Sie in der Liste **Quelle** einen der folgenden Schritte aus:

    - Wenn die befehlsassembly aus einem Projekt erstellt wird, das sich in derselben Projekt Mappe wie das VSIX-Projekt befindet, wählen Sie **ein Projekt in der aktuellen** Projekt Mappe aus. Wählen Sie in der Liste **Projekt** den Namen des Projekts aus.

    - Wenn die befehlsassembly als Datei in Ihrem Projekt enthalten ist, wählen Sie **Datei im Dateisystem** aus. Geben Sie in der Liste **Pfad** den vollständigen Pfad der Erweiterungs-Assemblydatei ein, oder verwenden Sie die Schaltfläche **Durchsuchen** , um die Assemblydatei zu suchen und auszuwählen

5. Klicken Sie auf die Schaltfläche **OK** .

#### <a name="to-include-a-template-that-you-create"></a>So fügen Sie eine Vorlage ein, die Sie erstellen

1. Öffnen Sie im VSIX-Projekt das Kontextmenü für die Datei "Source. Extension. vsixmanifest", und wählen Sie dann die Schaltfläche **Öffnen** aus.

     Die Datei wird im Designer geöffnet.

2. Klicken Sie im Abschnitt **Assets** des Editors auf die Schaltfläche **neu** .

     Das Dialogfeld **Neues Objekt hinzufügen** wird geöffnet.

3. Wählen Sie in der Liste **Typ** den Eintrag **Microsoft. VisualStudio. ProjectTemplate** oder **Microsoft. VisualStudio. ItemTemplate** aus.

4. Wählen Sie **Source** in der Liste Quelle **ein Projekt in der aktuellen Projekt** Mappe aus.

5. Wählen Sie in der Liste **Projekt** den Namen des Projekts aus, und klicken Sie dann auf die Schaltfläche **OK** .

6. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für die Projektvorlage oder das Element Vorlagen Projekt, und wählen Sie dann **Projekt entladen** aus.

7. Öffnen Sie erneut das Kontextmenü für den Projekt Knoten, und wählen Sie dann _yourtemplateprojectname_**. csproj** **Bearbeiten** oder _yourtemplateprojectname_**. vbproj** **Bearbeiten** aus.

8. Suchen Sie das folgende `VSTemplate`-Element in der Projektdatei.

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
    ```

9. Ersetze dieses Element durch folgenden XML-Code.

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     Das `OutputSubPath`-Element gibt weitere Ordner in dem Pfad an, unter dem die Projektvorlage beim Erstellen des Projekts erstellt wird. Mit den hier angegebenen Ordnern wird sichergestellt, dass die Element Vorlage nur verfügbar ist, wenn Kunden das Dialogfeld **Neues Projekt hinzufügen** öffnen, den **SharePoint** -Knoten erweitern und dann den Knoten **2010** auswählen.

10. Speichern und schließen Sie die Datei.

11. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für die Projektvorlage oder das Element Vorlagen Projekt, und wählen Sie dann **Projekt erneut laden** aus.

#### <a name="to-include-a-template-that-you-create-manually"></a>So fügen Sie eine Vorlage ein, die Sie manuell erstellen

1. Fügen Sie dem Projekt im VSIX-Projekt einen neuen Ordner hinzu, in dem die Vorlage enthalten sein soll.

2. Erstellen Sie unter diesem neuen Ordner die folgenden Unterordner, und fügen Sie dann die Vorlagen Datei (ZIP-Datei) dem Ordner *Locale ID* hinzu.

     *Yourtemplatefolder*

     **SharePoint**

     **SharePoint14**

     *Gebietsschemakennung*

     *YourTemplateName*. zip

     Wenn Sie z. b. über eine Element Vorlage mit dem Namen ContosoCustomAction.zip verfügen, die das Gebiets Schema Englisch (USA) unterstützt, kann der vollständige Pfad *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip* sein.

3. Wählen Sie in **Projektmappen-Explorer** die Vorlagen Datei (*YourTemplateName*. zip) aus.

4. Legen Sie im Fenster **Eigenschaften** die Eigenschaft **Buildaktion** auf **Inhalt** fest.

5. Öffnen Sie das Kontextmenü für die Datei "Source. Extension. vsixmanifest", und wählen Sie dann **Öffnen** aus.

     Die Datei wird im Designer geöffnet.

6. Klicken Sie im Abschnitt **Assets** des Editors auf die Schaltfläche **neu** .

     Das Dialogfeld **Neues Objekt hinzufügen** wird geöffnet.

7. Wählen Sie in der Liste **Typ** den Eintrag **Microsoft. VisualStudio. ItemTemplate** oder **Microsoft. VisualStudio. ProjectTemplate** aus.

8. Wählen Sie in der Liste **Quelle** die Option **Datei im Dateisystem** aus.

9. Geben Sie im Feld **Pfad** den vollständigen Pfad zur Assembly ein (z. b. *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*, oder verwenden Sie die Schaltfläche **Durchsuchen** , um die Assembly zu suchen und auszuwählen, und klicken Sie dann auf die Schaltfläche **OK** .

#### <a name="to-include-a-wizard-for-a-project-template-or-item-template"></a>So schließen Sie einen Assistenten für eine Projektvorlage oder Element Vorlage ein

1. Öffnen Sie im VSIX-Projekt das Kontextmenü für die Datei "Source. Extension. vsixmanifest", und wählen Sie dann **Öffnen** aus.

     Die Datei wird im Designer geöffnet.

2. Klicken Sie im Abschnitt **Assets** des Editors auf die Schaltfläche **neu** .

     Das Dialogfeld **Neues Objekt hinzufügen** wird geöffnet.

3. Wählen Sie in der Liste **Typ** den Eintrag **Microsoft. VisualStudio. Assembly** aus.

4. Führen Sie in der Liste **Quelle** einen der folgenden Schritte aus:

    - Wenn die Assistenten-Assembly aus einem Projekt erstellt wird, das sich in derselben Projekt Mappe wie das VSIX-Projekt befindet, wählen Sie **ein Projekt in der aktuellen** Projekt Mappe aus. Wählen Sie in der Liste **Projekt** den Namen des Projekts aus.

    - Wenn die Assistenten-Assembly als Datei in Ihrem Projekt enthalten ist, wählen Sie **Datei im Dateisystem** aus. Geben Sie im Feld **Pfad** den vollständigen Pfad zur Assemblydatei ein, oder verwenden Sie die Schaltfläche **Durchsuchen** , um die Assembly zu suchen und auszuwählen.

5. Klicken Sie auf die Schaltfläche **OK** .

### <a name="related-walkthroughs"></a>Verwandte Exemplarische Vorgehensweisen

In der folgenden Tabelle finden Sie Exemplarische Vorgehensweisen, die veranschaulichen, wie ein VSIX-Projekt verwendet wird, um unterschiedliche Typen von Erweiterungen für SharePoint-Tools

|Erweiterungstyp|Verwandte Exemplarische Vorgehensweisen|
|--------------------|--------------------------|
|Eine Erweiterung, die nur die Erweiterungsassembly einschließt.|[Exemplarische Vorgehensweise: Erweitern eines SharePoint-Projekt Elementtyps](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)<br /><br /> [Exemplarische Vorgehensweise: Erstellen einer SharePoint-Projekt Erweiterung](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)<br /><br /> [Exemplarische Vorgehensweise: Abrufen des SharePoint-Client Objektmodells in einer Server-Explorer-Erweiterung](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)|
|Eine Erweiterung, die SharePoint-Befehle enthält.|[Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Bereitstellungs Schritts für SharePoint-Projekte](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)<br /><br /> [Exemplarische Vorgehensweise: Erweitern von Server-Explorer zum Anzeigen von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)<br /><br /> [Exemplarische Vorgehensweise: Erstellen eines Projekt Elements für eine Website Spalte mit einer Projektvorlage, Teil 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|
|Eine Erweiterung, die eine Visual Studio-Vorlage enthält.|[Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Aktionsprojekt Elements mit einer Element Vorlage, Teil 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)<br /><br /> [Exemplarische Vorgehensweise: Erstellen eines Projekt Elements für eine Website Spalte mit einer Projektvorlage, Teil 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)|
|Eine Erweiterung, die einen Vorlagen-Assistenten enthält.|[Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Aktionsprojekt Elements mit einer Element Vorlage, Teil 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)<br /><br /> [Exemplarische Vorgehensweise: Erstellen eines Projekt Elements für eine Website Spalte mit einer Projektvorlage, Teil 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|

## <a name="create-vsix-packages-manually"></a>Manuelles Erstellen von VSIX-Paketen

Wenn Sie das VSIX-Paket für die Erweiterung der SharePoint-Tools manuell erstellen möchten, führen Sie die folgenden Schritte aus:

1. Erstellen Sie die Datei "Extension. vsixmanifest" und die Datei "[Content_Types]. xml" in einem neuen Ordner. Weitere Informationen finden Sie unter [Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md).

2. Klicken Sie in Windows Explorer mit der rechten Maustaste auf den Ordner, der die beiden XML-Dateien enthält, klicken Sie auf Senden an, und klicken Sie dann auf ZIP-komprimierter Ordner. Benennen Sie die resultierende ZIP-Datei in Dateiname.vsix um, wobei Dateiname der Name der verteilbaren Datei ist, mit der das Paket installiert wird.

3. Fügen Sie die Erweiterungsassembly dem VSIX-Paket hinzu. Wenn die Erweiterung einen SharePoint-Befehl enthält, fügen Sie dem VSIX-Paket auch die Assembly hinzu, die den SharePoint-Befehl implementiert.

4. Ändern Sie die Datei "Extension. vsixmanifest":

    - Fügen Sie `Microsoft.VisualStudio.MefComponent` unter dem `Assets` -Element ein-Element hinzu, und legen Sie dann den Wert des neuen-Elements auf den relativen Pfad der Assembly fest, die ihre Erweiterung im VSIX-Paket implementiert. Weitere Informationen finden Sie unter [MEFComponent-Element (VSX-Schema)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

    - Wenn die Erweiterung einen SharePoint-Befehl enthält, der das Server-Objektmodell für SharePoint aufruft, fügen Sie `Microsoft.VisualStudio.Assembly` unter dem-Element ein-Element hinzu `Assets` . Legen Sie den Wert des neuen Elements auf den relativen Pfad der Assembly fest, die den SharePoint-Befehl im VSIX-Paket implementiert. Weitere Informationen finden Sie unter [Asset-Element (VSX-Schema)](/previous-versions/dd393737(v=vs.110)).

    - Wenn die Erweiterung eine Projektvorlage oder Element Vorlage enthält, fügen Sie `ProjectTemplate` unter dem-Element ein-oder- `ItemTemplate` Element hinzu `Assets` . Legen Sie den Wert des neuen Elements auf den relativen Pfad des Ordners fest, der die Vorlage im VSIX-Paket enthält. Weitere Informationen finden Sie unter [ProjectTemplate-Element (VSX-Schema)](/previous-versions/visualstudio/visual-studio-2010/dd393735\(v\=vs.100\)) und [ItemTemplate-Element (VSX-Schema)](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\)).

    - Wenn die Erweiterung einen benutzerdefinierten Assistenten für eine Projektvorlage oder Element Vorlage enthält, fügen Sie `Assembly` unter dem-Element ein-Element hinzu `Assets` . Legen Sie den Wert des neuen Elements auf den relativen Pfad der Assembly im VSIX-Paket fest, und legen Sie dann das- `AssemblyName` Attribut auf den vollständigen Assemblynamen (einschließlich Version, Kultur und öffentliches Schlüssel Token) fest. Weitere Informationen finden Sie unter [Abhängigkeits Element (VSX-Schema)](/previous-versions/dd393682(v=vs.110)).

### <a name="example"></a>Beispiel

Das folgende Beispiel zeigt den Inhalt einer Erweiterung. vsixmanifest-Datei für eine Erweiterung der SharePoint-Tools. Die Erweiterung wird in einer Assembly mit dem Namen Contoso.ProjectExtension.dll implementiert. Die Erweiterung enthält eine SharePoint-befehlsassembly mit dem Namen Contoso.ExtensionCommands.dll und eine Element Vorlage in einem Ordner mit dem Namen **ItemTemplates** im VSIX-Paket. In diesem Beispiel wird davon ausgegangen, dass sich beide Assemblys im gleichen Ordner befinden wie die Dateierweiterung. vsixmanifest im VSIX-Paket.

```xml
<PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <Identity Id="CustomActionProjectItem.Microsoft.b99efe4d-cef3-4afd-b9af-034ca0c52743" Version="1.0" Language="en-US" Publisher="Microsoft" />
    <DisplayName>CustomActionProjectItem</DisplayName>
    <Description>Empty VSIX Project.</Description>
  </Metadata>
  <Installation>
    <InstallationTarget Id="Microsoft.VisualStudio.Pro" Version="11.0" />
  </Installation>
  <Dependencies>
    <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" Version="4.5" />
  </Dependencies>
  <Assets>
    <Asset Type="Microsoft.VisualStudio.ItemTemplate" Path="ItemTemplates" />
    <Asset Type="Microsoft.VisualStudio.MefComponent" Path="ProjectItemDefinition.dll" />
  </Assets>
</PackageManifest>
```

## <a name="see-also"></a>Siehe auch

- [Erweitern des SharePoint-Projektsystems](../sharepoint/extending-the-sharepoint-project-system.md)
- [Erweitern des Knotens „SharePoint-Verbindungen“ im Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Aufrufe in die SharePoint-Objekt Modelle](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Debuggen von Erweiterungen für die SharePoint-Tools in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)