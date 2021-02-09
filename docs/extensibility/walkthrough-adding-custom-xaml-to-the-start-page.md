---
title: 'Exemplarische Vorgehensweise: Hinzufügen von benutzerdefiniertem XAML zur Start Seite | Microsoft-Dokumentation'
description: In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie eine benutzerdefinierte Visual Studio-Startseite erstellen, die einen Webbrowser enthält.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 47c83906b84263af966737a309de0b5096031f94
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926870"
---
# <a name="walkthrough-add-custom-xaml-to-the-start-page"></a>Exemplarische Vorgehensweise: Hinzufügen von benutzerdefiniertem XAML zur Startseite

In dieser exemplarischen Vorgehensweise wird gezeigt, wie eine benutzerdefinierte Visual Studio-Startseite erstellt wird, die einen Webbrowser enthält.

## <a name="add-custom-xaml"></a>Benutzerdefiniertes XAML hinzufügen

1. Erstellen Sie eine Startseite, indem Sie die Anweisungen unter [Erstellen einer benutzerdefinierten Startseite](../extensibility/creating-a-custom-start-page.md)befolgen.

2. Suchen Sie in der Datei " *MainWindow. XAML* " den \<Grid> Abschnitt.

3. Fügen Sie im \<TabControl> -Element ein-Element und ein-Element hinzu \<TabItem> \< Grid> , wie im folgenden Beispiel gezeigt.

    ```xml
    <Grid>
        <TabControl>
            <TabItem Header="Bing" Height="Auto">
                <Frame Source="http://www.bing.com" />
            </TabItem>
        </TabControl>
    </Grid>
    ```

4. Fügen Sie eine Sekunde \<TabItem> mit einem-Element hinzu, \<Button> das ein neues Projekt öffnet:

    ```xml
    <Grid>
        <TabControl>
            <TabItem Header="MyButton" Height="Auto">
                <Button Name="btnNewProj" Content="New Project"
                    Command="{x:Static vscom:VSCommands.ExecuteCommand}"
                    CommandParameter="File.NewProject" >
                </Button>
            </TabItem>
            <TabItem Header="Bing" Height="Auto">
                <Frame Source="http://www.bing.com" />
            </TabItem>
        </TabControl>
    </Grid>
    ```

## <a name="test-the-custom-start-page"></a>Testen der benutzerdefinierten Startseite

1. Drücken Sie **F5**.

     Die experimentelle Instanz von Visual Studio wird geöffnet, und die benutzerdefinierte Startseite ist installiert, aber nicht ausgewählt.

2. Öffnen Sie in der experimentellen Instanz von Visual Studio die Seite Extras **/options/Umgebung** .

3. Wählen Sie **Start** aus. Wählen Sie in der Liste **Start Seite anpassen** die *XAML* -Datei aus, und klicken Sie auf **OK**.

4. Klicken Sie im Menü **Ansicht** auf **Startseite**.

5. Klicken Sie **auf die Register** Karte "von

     Sie sollten eine Seite mit der Seite "Web" sehen.

6. Klicken Sie auf die Registerkarte **myButton** .

     Es sollte eine Schaltfläche " **MyProject** " angezeigt werden, die das Dialogfeld " **Neues Projekt** " öffnet.

7. Schließen Sie die experimentelle Instanz.

Wählen Sie zum Anwenden der benutzerdefinierten Start Seite unter Extras  >  **Optionen**  >  **Umgebung** die Option **Start** aus. Wählen Sie in der Liste **Start Seite anpassen** die *XAML* -Datei aus, und klicken Sie auf **OK**.

## <a name="next-steps"></a>Nächste Schritte

Die Visual Studio-Startseite enthält jetzt eine Registerkarte, auf der eine Registerkarte mit dem Webbrowser und die Registerkarte MyButton angezeigt wird. Sie können benutzerdefinierte Startseiten mit anderer Funktionalität erstellen, indem Sie das *Code Behind-* Modell zum Hinzufügen einer benutzerdefinierten DLL verwenden, wie unter [Hinzufügen eines Benutzer Steuer Elements zur Startseite](../extensibility/adding-user-control-to-the-start-page.md)gezeigt. Sie können benutzerdefinierte Startseiten für andere Benutzer freigeben, indem Sie die resultierende vsix-Datei auf der [Visual Studio Marketplace](https://marketplace.visualstudio.com/) -Website oder auf einer anderen Website oder Netzwerkfreigabe veröffentlichen. Weitere Informationen finden Sie unter [Deploying Custom Start Pages](../extensibility/deploying-custom-start-pages.md).

## <a name="see-also"></a>Weitere Informationen

- [Anpassen der Startseite](../ide/customizing-the-start-page-for-visual-studio.md)
- [WPF-Container Steuerelemente](/previous-versions/bb675291(v=vs.110))