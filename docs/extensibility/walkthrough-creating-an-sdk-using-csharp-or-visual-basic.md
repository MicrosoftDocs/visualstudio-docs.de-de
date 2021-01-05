---
title: 'Exemplarische Vorgehensweise: Erstellen eines SDK mit c# oder Visual Basic | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie ein einfaches Math Library SDK mithilfe von Visual c# erstellen und dann das SDK als Visual Studio-Erweiterung mithilfe dieser exemplarischen Vorgehensweise verpacken.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CSharp
- VB
ms.openlocfilehash: b9000290b146275ca495b49211c9823422b0a32f
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2021
ms.locfileid: "97862955"
---
# <a name="walkthrough-create-an-sdk-using-c-or-visual-basic"></a>Exemplarische Vorgehensweise: Erstellen eines SDK mit c# oder Visual Basic
In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie ein einfaches Math Library SDK mithilfe von Visual c# erstellen und das SDK dann als Visual Studio-Erweiterung (VSIX) verpacken. Führen Sie die folgenden Schritte aus:

- [So erstellen Sie die simplemath-Windows-Runtime Komponente](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)

- [So erstellen Sie das simplemathvsix-Erweiterungsprojekt](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)
- [So erstellen Sie eine Beispiel-APP, die die Klassenbibliothek verwendet](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)

## <a name="prerequisites"></a>Voraussetzungen
 Um dieser exemplarischen Vorgehensweise folgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-simplemath-windows-runtime-component"></a><a name="createClassLibrary"></a> So erstellen Sie die simplemath-Windows-Runtime Komponente

1. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**.

2. Erweitern Sie in der Liste der Vorlagen die Option **Visual c#** , oder **Visual Basic**, wählen Sie den Knoten **Windows Store** aus, und wählen Sie dann die Vorlage **Windows-Runtime Komponenten** aus.

3. Geben Sie im Feld **Name den Namen** **simplemath** an, und klicken Sie dann auf die Schaltfläche **OK** .

4. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für den Projekt Knoten **simplemath** , und wählen Sie dann **Eigenschaften** aus.

5. Benennen Sie **Class1.cs** in **Arithmetic.cs** um, und aktualisieren Sie ihn entsprechend dem folgenden Code:

    [!code-csharp[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.cs)]
    [!code-vb[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.vb)]

6. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für den Projektmappen-Knoten **"simplemath"** , und wählen Sie dann **Configuration Manager** aus.

    Das Dialogfeld **Configuration Manager** wird geöffnet.

7. Wählen Sie in der Liste **aktive Projektmappenkonfiguration** die Option **Release** aus.

8. Überprüfen Sie in der Spalte **Konfiguration** , ob die Zeile **simplemath** auf **Release** festgelegt ist, und wählen Sie dann die Schaltfläche **Schließen** , um die Änderung zu übernehmen.

   > [!IMPORTANT]
   > Das SDK für die simplemath-Komponente enthält nur eine Konfiguration. Diese Konfiguration muss der Releasebuild sein, oder apps, die die Komponente verwenden, erhalten keine Zertifizierung für das [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)] .

9. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für den Projekt Knoten **simplemath** , und wählen Sie dann **Erstellen** aus.

## <a name="to-create-the-simplemathvsix-extension-project"></a><a name="createVSIX"></a> So erstellen Sie das simplemathvsix-Erweiterungsprojekt

1. Wählen Sie im Kontextmenü für den Projektmappen-Knoten **"simplemath"** die Option   >  **Neues Projekt** hinzufügen aus.

2. Erweitern Sie in der Liste der Vorlagen die Option **Visual c#** , oder **Visual Basic**, wählen Sie den Knoten **Erweiterbarkeit** aus, und wählen Sie dann die Vorlage **VSIX-Projekt** aus.

3. Geben Sie im Feld **Name den Namen** **simplemathvsix** an, und klicken Sie dann auf die Schaltfläche **OK** .

4. Wählen Sie in **Projektmappen-Explorer** das Element **Source. Extension. vsixmanifest** aus.

5. Wählen Sie in der Menüleiste **Ansicht** > **Code** aus.

6. Ersetzen Sie den vorhandenen XML-Code durch den folgenden XML-Code:

     [!code-xml[CreatingAnSDKUsingWinRT#1](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]

7. Wählen Sie in **Projektmappen-Explorer** das Projekt **simplemathvsix** aus.

8. Wählen Sie in der Menüleiste **Projekt** > **Neues Element hinzufügen** aus.

9. Erweitern Sie in der Liste der **allgemeinen Elemente** den Knoten **Daten**, und wählen Sie dann **XML-Datei** aus.

10. Geben Sie im Feld **Name** an `SDKManifest.xml` , und wählen Sie dann die Schaltfläche **Hinzufügen** aus.

11. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für `SDKManifest.xml` , wählen **Sie Eigenschaften** aus, und ändern Sie dann den Wert der Eigenschaft **in VSIX einschließen** in **true**.

12. Ersetzen Sie den Inhalt der Datei durch folgendes XML:

    **C#**

    ```xml
    <FileList
      DisplayName="WinRT Math Library (CS)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">
    </FileList>
    ```

    **Visual Basic**

    ```xml
    <FileList
      DisplayName="WinRT Math Library (VB)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">
    </FileList>
    ```

13. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für das Projekt **simplemathvsix** , wählen Sie **Hinzufügen** aus, und wählen Sie dann **neuer Ordner** aus.

14. Benennen Sie den Ordner in um `references` .

15. Öffnen Sie das Kontextmenü für den Ordner **Verweise** , wählen Sie **Hinzufügen** aus, und wählen Sie dann **neuer Ordner** aus.

16. Benennen Sie den Unterordner in um `commonconfiguration` , erstellen Sie einen Unterordner darin, und benennen Sie den Unterordner `neutral` .

17. Wiederholen Sie die vorherigen vier Schritte, und benennen Sie dabei den ersten Ordner in um `redist` .

     Das Projekt enthält jetzt die folgende Ordnerstruktur:

    ```xml
    references\commonconfiguration\neutral
    redist\commonconfiguration\neutral
    ```

18. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für das Projekt **simplemath** , und wählen Sie dann **Ordner in Datei-Explorer öffnen** aus.

19. Navigieren Sie im **Datei-Explorer** zum Ordner " *bin\Release* ", öffnen Sie das Kontextmenü für die Datei " **simplemath. winmd** ", und wählen Sie dann **Kopieren** aus.

20. Fügen Sie die Datei in **Projektmappen-Explorer** in den Ordner " *references\commonconfiguration\neutral* " im Projekt **simplemathvsix** ein.

21. Wiederholen Sie den vorherigen Schritt, und legen Sie die Datei **simplemath. pri** in den Ordner *redist\commonconfiguration\neutral* des Projekts **simplemathvsix** ein.

22. Wählen Sie in **Projektmappen-Explorer** die Option **simplemath. winmd** aus.

23. Wählen Sie in der Menüleiste   >  **Eigenschaften** anzeigen aus (Tastatur: Wählen Sie die **F4** -Taste).

24. Ändern Sie im **Eigenschaften** Fenster die Eigenschaft **Buildaktion** in **Inhalt**, und ändern Sie dann die Eigenschaft **in VSIX einschließen** in **true**.

25. Wiederholen Sie diesen Vorgang in **Projektmappen-Explorer** für **simplemath. pri**.

26. Wählen Sie in **Projektmappen-Explorer** das Projekt **simplemathvsix** aus.

27. Wählen Sie in der Menüleiste **Build**  >  **simplemathvsix** erstellen aus.

28. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für das Projekt **simplemathvsix** , und wählen Sie dann **Ordner in Datei-Explorer öffnen** aus.

29. Navigieren Sie im **Datei-Explorer** zu *\bin\releaseordner* , und führen Sie dann *simplemathvsix. vsix* aus, um es zu installieren.

30. Wählen Sie die Schaltfläche **Installieren** aus, warten Sie, bis die Installation abgeschlossen ist, und starten Sie Visual Studio neu.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> So erstellen Sie eine Beispiel-APP, die die Klassenbibliothek verwendet

1. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**.

2. Erweitern Sie in der Liste der Vorlagen die Option **Visual c#** , oder **Visual Basic**, und wählen Sie dann den Knoten **Windows Store** aus.

3. Wählen Sie die Vorlage **leere App** aus, benennen Sie das Projekt mit dem Namen **arithmeticui**, und wählen Sie dann die Schaltfläche **OK** .

4. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für das **arithmeticui** -Projekt, und wählen Sie dann Verweis **Hinzufügen** aus  >  .

5. Erweitern Sie in der Liste der Verweis Typen **Windows**, und klicken Sie dann auf **Erweiterungen**.

6. Wählen Sie im Detailbereich die Erweiterung **WinRT Math Library** aus.

    Weitere Informationen zu Ihrem SDK werden angezeigt. Sie können den Link **Weitere Informationen** zum Öffnen auswählen https://msdn.microsoft.com/ , wie Sie in der SDKManifest.xml-Datei zuvor in dieser exemplarischen Vorgehensweise angegeben haben.

7. Aktivieren Sie im Dialogfeld **Verweis-Manager** das Kontrollkästchen **WinRT Math Library** , und klicken Sie dann auf die Schaltfläche **OK** .

8. Wählen Sie in der Menüleiste   >  **Objektkatalog** anzeigen aus.

9. Wählen Sie in der Liste **Durchsuchen** die Option **simple math** aus.

     Nun können Sie die Neuerungen im SDK untersuchen.

10. Öffnen Sie in **Projektmappen-Explorer** die Datei " **MainPage. XAML**", und ersetzen Sie deren Inhalt durch den folgenden XAML-Code:

    **C#**

    ```xml
    <Page
        x:Class="ArithmeticUI.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:SimpleMath"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```

    **Visual Basic**

    ```xml
    <Page
        x:Class="ArithmeticUI.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:SimpleMath"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```

11. Aktualisieren Sie **MainPage.XAML.cs** entsprechend dem folgenden Code:

     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.cs)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.vb)]

12. Drücken Sie die Taste **F5** , um die APP auszuführen.

13. Geben Sie in der APP zwei Zahlen ein, wählen Sie einen Vorgang aus, und wählen Sie dann die **=** Schaltfläche aus.

     Das richtige Ergebnis wird angezeigt.

    Sie haben erfolgreich ein Erweiterungs-SDK erstellt und verwendet.

## <a name="see-also"></a>Weitere Informationen
- [Exemplarische Vorgehensweise: Erstellen eines SDK mithilfe von C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [Exemplarische Vorgehensweise: Erstellen eines SDK mithilfe von JavaScript](../extensibility/walkthrough-creating-an-sdk-using-javascript.md)
- [Erstellen eines Software Development Kits](../extensibility/creating-a-software-development-kit.md)
