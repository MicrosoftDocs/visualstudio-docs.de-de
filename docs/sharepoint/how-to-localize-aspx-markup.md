---
title: 'Vorgehensweise: Lokalisieren von ASPX-Markup | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie ASPX-Markup in SharePoint lokalisieren, indem Sie hart codierte Zeichen folgen Werte durch Ausdrücke ersetzen, die auf lokalisierte Ressourcen verweisen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- localizing XML [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1876e06348d60f8a960b352525fd72ad06795101
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931733"
---
# <a name="how-to-localize-aspx-markup"></a>How to: Lokalisieren von ASPX-Markup
  [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] (aspx)-Seiten verwenden in der Regel hart codierte Zeichen folgen Werte. Um diese Zeichen folgen zu lokalisieren, ersetzen Sie Sie durch Ausdrücke, die auf lokalisierte Ressourcen verweisen.

## <a name="localize-aspx-markup"></a>Lokalisieren von ASPX-Markup

#### <a name="to-localize-aspx-markup"></a>So lokalisieren Sie ASPX-Markup

1. Fügen Sie separate Ressourcen Dateien hinzu: einen für die Standardsprache und einen für jede lokalisierte Sprache.

     Wenn Sie nur Markup und nicht Code lokalisieren, fügen Sie ein Projekt Element für eine globale Ressourcen Datei hinzu. Wenn Sie Code und Markup lokalisieren, fügen Sie ein Ressourcen Datei-Projekt Element hinzu.

    1. Öffnen Sie zum Hinzufügen einer globalen Ressourcen Datei in **Projektmappen-Explorer** das Kontextmenü für ein SharePoint-Projekt Element, und wählen Sie dann   >  **Neues Element** hinzufügen aus. Wählen Sie unter dem Knoten SharePoint **2010** die Vorlage **Global Resources File** aus.

    2. Öffnen Sie zum Hinzufügen einer Ressourcen Datei in **Projektmappen-Explorer** das Kontextmenü für ein SharePoint-Projekt Element, und wählen Sie dann   >  **Neues Element** hinzufügen aus. Wählen Sie unter dem Knoten **Visual Basic** oder **Visual c#** die Vorlage **Ressourcen Datei** aus.

    > [!NOTE]
    > Stellen Sie sicher, dass Sie die Ressourcen Dateien einem SharePoint-Projekt Element hinzufügen, um die Eigenschaft Bereitstellungstyp zu aktivieren. Diese Eigenschaft ist später in dieser Prozedur erforderlich. Wenn die Projekt Mappe kein SharePoint-Projekt Element enthält, können Sie ein leeres SharePoint-Projekt hinzufügen und dessen Standard *Elements.xml* Datei entfernen.

2. Benennen Sie die Ressourcen Datei der Standardsprache mit einer *RESX* -Erweiterung, z. b. myappresources. resx. Verwenden Sie für jede lokalisierte Ressourcen Datei denselben Basis Namen, aber fügen Sie die Kultur hinzu [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] . Benennen Sie z. b. eine deutsch lokalisierte Ressource *MyAppResources.de-de. resx*.

3. Ändern Sie den Wert der Eigenschaft **Bereitstellungstyp** jeder Ressourcen Datei in **appglobalresource** , damit Sie im App_GlobalResources Ordner des Servers bereitgestellt werden.

4. Wenn Sie die Ressourcen zum Lokalisieren von Code zusätzlich zu ASPX-Markup verwenden, belassen **Sie den Wert der Eigenschaft** Buildvorgang der einzelnen Dateien als **eingebettete Ressource**. Wenn Sie die Ressourcen Dateien nur zum Lokalisieren von Markup verwenden, können Sie optional den Eigenschafts Wert der Dateien in " **Content**" ändern. Weitere Informationen finden Sie unter [Lokalisieren von SharePoint-Lösungen](../sharepoint/localizing-sharepoint-solutions.md).

5. Öffnen Sie jede Ressourcen Datei, und fügen Sie lokalisierte Zeichen folgen hinzu

6. Ersetzen Sie im [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Markup für die ASPX-Seite oder das Steuerelement die hart codierten Zeichen folgen durch Werte, die das folgende Format aufweisen:

    ```aspx-csharp
    <%$Resources:Resource File Name, String ID%>
    ```

     Um z. b. den Text für ein Label-Steuerelement auf einer Anwendungsseite zu lokalisieren, ändern Sie Folgendes:

    ```aspx-csharp
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">
    <asp:Label ID="lbl" runat="server" Text="Label text"></asp:Label>
    </asp:Content>
    ```

     in

    ```aspx-csharp
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">
    <asp:Label ID="lbl" runat="server" Text="<%$Resources:MyAppResources,String1%>"></asp:Label>
    </asp:Content>
    ```

7. Drücken Sie die Taste **F5** , um die Anwendung zu erstellen und auszuführen.

8. Legen Sie die Anzeigesprache in SharePoint auf eine Sprache fest, die nicht der Standardsprache entspricht.

     In der Anwendung werden die lokalisierten Zeichenfolgen angezeigt. Zum Anzeigen lokalisierter Ressourcen muss auf dem SharePoint-Server ein Sprachpaket installiert sein, das der Kultur der Ressourcendatei entspricht.

## <a name="see-also"></a>Weitere Informationen
- [Lokalisieren von SharePoint-Lösungen](../sharepoint/localizing-sharepoint-solutions.md)
- [How to: Lokalisieren eines Features](../sharepoint/how-to-localize-a-feature.md)
- [How to: Hinzufügen einer Ressourcendatei](../sharepoint/how-to-add-a-resource-file.md)
- [How to: Lokalisieren von Code](../sharepoint/how-to-localize-code.md)
