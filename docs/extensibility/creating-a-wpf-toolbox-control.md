---
title: Erstellen eines WPF-Toolbox-Steuer Elements | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie mithilfe der Vorlage "WPF-Toolbox-Steuerelement" ein Toolbox-Steuerelement erstellen, das Sie an andere Benutzer verteilen können.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- toolbox control
- toolbox
- wpf
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9b401baf1605a869772ba41ce83ad906061f8144
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851438"
---
# <a name="create-a-wpf-toolbox-control"></a>Erstellen eines WPF-Toolbox-Steuer Elements

Mit der Toolbox-Steuerelement Vorlage von WPF (Windows Presentation Framework) können Sie WPF-Steuerelemente erstellen, die bei der Installation der Erweiterung automatisch zur **Toolbox** hinzugefügt werden. In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie mithilfe der Vorlage ein **Toolbox** -Steuerelement erstellen, das Sie an andere Benutzer verteilen können.

Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Sie ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-toolbox-control"></a>Erstellen des Toolbox-Steuer Elements

### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>Erstellen einer Erweiterung mit einem WPF-Toolbox-Steuerelement

1. Erstellen Sie ein VSIX-Projekt mit dem Namen `MyToolboxControl` . Sie finden die VSIX-Projektvorlage im Dialogfeld " **Neues Projekt** ", indem Sie nach "VSIX" suchen.

2. Wenn das Projekt geöffnet wird, fügen Sie eine **WPF-Toolbox-Steuer** Element Vorlage mit dem Namen hinzu `MyToolboxControl` . Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie   >  **Neues Element** hinzufügen aus. Navigieren Sie im Dialogfeld **Neues Element hinzufügen** zu **Visual c#**  >  -**Erweiterbarkeit** , und wählen Sie **WPF-Toolbox-Steuer** Element aus. Ändern Sie im Feld **Name** am unteren Rand des Fensters den Namen der Befehlsdatei in *MyToolboxControl.cs*.

    Die Lösung enthält jetzt ein Benutzer Steuerelement, ein, `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> das das Steuerelement der **Toolbox** hinzufügt, und einen **Microsoft. VisualStudio. ToolboxControl** -Asset-Eintrag im VSIX-Manifest für die Bereitstellung.

#### <a name="to-create-the-control-ui"></a>So erstellen Sie eine Steuerelement-Benutzeroberfläche

1. Öffnen Sie " *mytoolboxcontrol. XAML* " im Designer.

    Der Designer zeigt ein <xref:System.Windows.Controls.Grid>-Steuerelement an, das ein <xref:System.Windows.Controls.Button>-Steuerelement enthält.

2. Ordnen Sie das Raster Layout an. Wenn Sie das Steuerelement auswählen <xref:System.Windows.Controls.Grid> , werden blaue Steuer leisten am oberen und linken Rand des Rasters angezeigt. Sie können dem Raster Zeilen und Spalten hinzufügen, indem Sie auf die Balken klicken.

3. Fügen Sie dem Raster untergeordnete Steuerelemente hinzu. Sie können ein untergeordnetes Steuerelement positionieren, indem Sie es aus der **Toolbox** in einen Abschnitt des Rasters ziehen oder indem Sie dessen `Grid.Row` -und- `Grid.Column` Attribute im XAML-Code festlegen. Im folgenden Beispiel werden zwei Bezeichnungen in der oberen Zeile des Rasters und eine Schaltfläche in der zweiten Zeile hinzugefügt.

    ```xaml
    <Grid>
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />
    </Grid>
    ```

## <a name="renaming-the-control"></a>Umbenennen des Steuer Elements

 Standardmäßig wird das Steuerelement in der **Toolbox** als **mytoolboxcontrol** in einer Gruppe mit dem Namen **mytoolboxcontrol. mytoolboxcontrol** angezeigt. Sie können diese Namen in der *MyToolboxControl.XAML.cs* -Datei ändern.

1. Öffnen Sie *MyToolboxControl.XAML.cs* in der Code Ansicht.

2. Suchen `MyToolboxControl` Sie die-Klasse, und benennen Sie Sie in testControl um. (Die schnellste Möglichkeit hierfür besteht darin, die Klasse umzubenennen und dann im Kontextmenü die Option **Umbenennen** auszuwählen und die Schritte abzuschließen. (Weitere Informationen zum **Rename** -Befehl finden Sie unter [Rename Refactoring (c#)](../ide/reference/rename.md).)

3. Wechseln Sie zum `ProvideToolboxControl` -Attribut, und ändern Sie den Wert des ersten zu **testenden** Parameters. Dies ist der Name der Gruppe, die das Steuerelement in der **Toolbox** enthält.

    Der resultierende Code sollte wie folgt aussehen:

    ```csharp
    [ProvideToolboxControl("Test", true)]
    public partial class TestControl : UserControl
    {
        public TestControl()
        {
            InitializeComponent();
        }
    }
    ```

## <a name="build-test-and-deployment"></a>Build, Test und Bereitstellung

 Wenn Sie das Projekt Debuggen, sollten Sie das Steuerelement finden, das in der **Toolbox** der experimentellen Instanz von Visual Studio installiert ist.

### <a name="to-build-and-test-the-control"></a>So erstellen Sie das Steuerelement und testen es

1. Erstellen Sie das Projekt neu, und starten Sie das Debugging.

2. Erstellen Sie in der neuen Instanz von Visual Studio ein WPF-Anwendungsprojekt. Stellen Sie sicher, dass die XAML-Designer geöffnet ist.

3. Suchen Sie in der **Toolbox** nach dem Steuerelement, und ziehen Sie es dann auf die Entwurfsoberfläche.

4. Starten Sie das Debuggen der WPF-Anwendung.

5. Vergewissern Sie sich, dass das Steuerelement angezeigt wird

### <a name="to-deploy-the-control"></a>So stellen Sie das Steuerelement bereit

1. Nachdem Sie das getestete Projekt erstellt haben, finden Sie die *VSIX* -Datei im Ordner * \bin\debug \* des Projekts.

2. Sie können es auf einem lokalen Computer installieren, indem Sie auf die *VSIX* -Datei doppelklicken und nach der Installation Vorgehen. Um das Steuerelement zu deinstallieren, wechseln Sie **zu Extras**  >  **Erweiterungen und Updates** , suchen Sie die Steuerelement Erweiterung, und klicken Sie dann auf **deinstallieren**

3. Laden Sie die *VSIX* -Datei in ein Netzwerk oder auf eine Website hoch.

    Wenn Sie die Datei auf die [Visual Studio Marketplace](https://marketplace.visualstudio.com/) Website hochladen, können andere Benutzer die **Tools**  >  **Erweiterungen und Updates** in Visual Studio verwenden, um das Steuerelement online zu finden und zu installieren.
