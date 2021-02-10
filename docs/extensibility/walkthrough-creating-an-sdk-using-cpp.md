---
title: 'Exemplarische Vorgehensweise: Erstellen eines SDK mit C++ | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie ein natives C++ Math Library-SDK erstellen, das SDK als Visual Studio-Erweiterung verpacken und es dann zum Erstellen einer App mithilfe dieser exemplarischen Vorgehensweise verwenden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f3f9b9efc625b435f304b192d3ca52f514e682e8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951913"
---
# <a name="walkthrough-create-an-sdk-using-c"></a>Exemplarische Vorgehensweise: Erstellen eines SDK mithilfe von C++
In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie ein System eigenes C++ Math Library SDK erstellen, das SDK als Visual Studio-Erweiterung (VSIX) verpacken und dann zum Erstellen einer App verwenden. Die exemplarische Vorgehensweise ist in die folgenden Schritte unterteilt:

- [So erstellen Sie Native und Windows-Runtime-Bibliotheken](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)

- [So erstellen Sie das nativemathvsix-Erweiterungsprojekt](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)

- [So erstellen Sie eine Beispiel-APP, die die Klassenbibliothek verwendet](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)

## <a name="prerequisites"></a>Voraussetzungen
 Um dieser exemplarischen Vorgehensweise folgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a> So erstellen Sie Native und Windows-Runtime-Bibliotheken

1. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**.

2. Erweitern Sie in der Liste der Vorlagen die Option **Visual C++**  >  **universelle Windows**-Plattform, und wählen Sie dann die Vorlage **dll (universelle Windows-Apps)** aus. Geben Sie im Feld **Name den Namen** an `NativeMath` , und klicken Sie dann auf die Schaltfläche **OK** .

3. Aktualisieren Sie *nativemath. h* entsprechend dem folgenden Code.

     [!code-cpp[CreatingAnSDKUsingCpp#1](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]

4. Aktualisieren Sie *nativemath. cpp* entsprechend dem folgenden Code:

     [!code-cpp[CreatingAnSDKUsingCpp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]

5. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für die Projekt Mappe **"nativemath"**, und wählen Sie dann   >  **Neues Projekt** hinzufügen aus.

6. Erweitern Sie in der Liste der Vorlagen die **Visual C++**, und wählen Sie dann die Vorlage **Windows-Runtime Komponenten** aus. Geben Sie im Feld **Name den Namen** an `NativeMathWRT` , und klicken Sie dann auf die Schaltfläche **OK** .

7. Aktualisieren Sie *Class1. h* entsprechend dem folgenden Code:

     [!code-cpp[CreatingAnSDKUsingCpp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]

8. Aktualisieren Sie *Class1. cpp* entsprechend dem folgenden Code:

     [!code-cpp[CreatingAnSDKUsingCpp#4](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]

9. Wählen Sie auf der Menüleiste **Erstellen** > **Projektmappe erstellen** aus.

## <a name="to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a> So erstellen Sie das nativemathvsix-Erweiterungsprojekt

1. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für die Projekt Mappe **"nativemath"**, und wählen Sie dann   >  **Neues Projekt** hinzufügen aus.

2. Erweitern Sie in der Liste der Vorlagen die Option **Visual c#**  >  -**Erweiterbarkeit**, und wählen Sie dann **VSIX-Projekt** aus. Geben Sie im Feld **Name den Namen** **nativemathvsix** an, und klicken Sie dann auf die Schaltfläche **OK** .

3. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für " **Source. Extension. vsixmanifest**", und wählen Sie dann **Code anzeigen** aus.

4. Verwenden Sie das folgende XML, um den vorhandenen XML-Code zu ersetzen.

    [!code-xml[CreatingAnSDKUsingCpp#6](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

5. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für das Projekt **nativemathvsix** , und wählen Sie dann   >  **Neues Element** hinzufügen aus.

6. Erweitern Sie in der Liste der **Visual c#-Elemente den Knoten** **Daten**, und wählen Sie dann **XML-Datei** aus. Geben Sie im Feld **Name den Namen** an `SDKManifest.xml` , und klicken Sie dann auf die Schaltfläche **OK** .

7. Verwenden Sie diese XML-Datei, um den Inhalt der Datei zu ersetzen:

     [!code-xml[CreatingAnSDKUsingCpp#5](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]

8. Erstellen Sie in **Projektmappen-Explorer** unter dem Projekt **nativemathvsix** diese Ordnerstruktur:

    ```xml
    \DesignTime
          \CommonConfiguration
                \Neutral
                      \Include
          \Debug
                \x86
    \Redist
          \Debug
                \x86
    \References
          \CommonConfiguration
                \Neutral
    ```

9. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für die Projekt Mappe **"nativemath"**, und wählen Sie dann **Ordner in Datei-Explorer öffnen** aus.

10. Kopieren Sie im **Datei-Explorer** *$solutionroot $ \nativemath\nativemath.h*, und fügen Sie ihn dann in **Projektmappen-Explorer** unter dem **nativemathvsix** -Projekt in den Ordner *$solutionroot $ \nativemathvsix\designtime\commonconfiguration\neutral\include \\* ein.

     Kopieren Sie *$solutionroot $ \Debug \ nativemath\nativemath.lib*, und fügen Sie ihn dann in den Ordner *$solutionroot $ \nativemathvsix\designtime\debug \\ \ x86* ein.

     Kopieren Sie *$solutionroot $\Debug\NativeMath\NativeMath.dll* , und fügen Sie ihn in den Ordner *$solutionroot $ \nativemathvsix\redist\debug \\ \ x86* ein.

     Kopieren Sie *$solutionroot $\Debug\NativeMathWRT\NativeMathWRT.dll* , und fügen Sie ihn in den Ordner *$solutionroot $ \nativemathvsix\redist\debug \ x86* ein.
     Kopieren Sie *$solutionroot $ \dbug\nativemathwrt\nativemathwrt.winmd* , und fügen Sie ihn in den Ordner *$solutionroot $ \nativemathvsix\references\commonconfiguration\neutral* ein.

     Kopieren Sie *$solutionroot $ \Debug \ nativemathwrt\nativemathwrt.pri* , und fügen Sie Sie in den Ordner *$solutionroot $ \nativemathvsix\references\commonconfiguration\neutral* ein.

11. Erstellen Sie im Ordner *$solutionroot $ \nativemathvsix\designtime\debug\x86 \\* eine Textdatei mit dem Namen *nativemathsdk.*-Eigenschaften, und fügen Sie den folgenden Inhalt in die Datei ein:

    [!code-xml[CreatingAnSDKUsingCpp#7](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]

12. Wählen Sie in der Menüleiste   >  **Weitere Fenster**  >  **Eigenschaften** anzeigen aus (Tastatur: Wählen Sie die **F4** -Taste).

13. Wählen Sie in **Projektmappen-Explorer** die Datei **nativemathwrt. winmd** aus. Ändern Sie im **Eigenschaften** Fenster die Eigenschaft **Buildaktion** in **Inhalt**, und ändern Sie dann die Eigenschaft **in VSIX einschließen** in **true**.

     Wiederholen Sie diesen Vorgang für die Datei " **nativemath. h** ".

     Wiederholen Sie diesen Vorgang für die Datei **nativemathwrt. pri** .

     Wiederholen Sie diesen Vorgang für die Datei " **nativemath. lib** ".

     Wiederholen Sie diesen Vorgang für die Datei **nativemathsdk.** -Eigenschaften.

14. Wählen Sie in **Projektmappen-Explorer** die Datei **nativemath. h** aus. Ändern Sie im **Eigenschaften** Fenster die Eigenschaft **in VSIX einschließen** in **true**.

     Wiederholen Sie diesen Vorgang für die **NativeMath.dll** Datei.

     Wiederholen Sie diesen Vorgang für die **NativeMathWRT.dll** Datei.

     Wiederholen Sie diesen Vorgang für die **SDKManifest.xml** Datei.

15. Wählen Sie auf der Menüleiste **Erstellen** > **Projektmappe erstellen** aus.

16. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für das Projekt **nativemathvsix** , und wählen Sie dann **Ordner in Datei-Explorer öffnen** aus.

17. Navigieren Sie im **Datei-Explorer** zum Ordner *$solutionroot $ \nativemathvsix\bin\debug* , und führen Sie dann *nativemathvsix. vsix* aus, um mit der Installation zu beginnen.

18. Wählen Sie die Schaltfläche **Installieren** aus, warten Sie, bis die Installation abgeschlossen ist, und öffnen Sie dann Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> So erstellen Sie eine Beispiel-APP, die die Klassenbibliothek verwendet

1. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**.

2. Erweitern Sie in der Liste der Vorlagen **Visual C++**  >  **Windows Universal** , und wählen Sie dann **leere App** aus. Geben Sie im Feld **Name den Namen** **nativemathsdksample** ein, und klicken Sie dann auf die Schaltfläche **OK** .

3. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für das Projekt **nativemathsdksample** , und wählen Sie dann Verweis **Hinzufügen** aus  >  .

4. Erweitern Sie im Dialogfeld **Verweis hinzufügen** in der Liste der Verweis Typen den Knoten **universelle Fenster**, und wählen Sie dann **Erweiterungen** aus. Aktivieren Sie abschließend das Kontrollkästchen **native Math SDK** , und klicken Sie dann auf die Schaltfläche **OK** .

5. Zeigen Sie die Projekteigenschaften für nativemathsdksample an.

    Die Eigenschaften, die Sie in *nativemathsdk.* Properties definiert haben, wurden beim Hinzufügen des Verweises angewendet. Sie können überprüfen, ob die Eigenschaften angewendet wurden, indem Sie die Eigenschaft **VC + +-Verzeichnisse** der **Konfigurations Eigenschaften** des Projekts überprüfen.

6. Öffnen Sie in **Projektmappen-Explorer** die Datei " **MainPage. XAML**", und ersetzen Sie dann den Inhalt mit dem folgenden XAML-Code:

    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]

7. Aktualisieren Sie " *MainPage. XAML. h* " entsprechend dem folgenden Code:

    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]

8. Aktualisieren Sie " *MainPage. XAML. cpp* " entsprechend dem folgenden Code:

     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]

9. Drücken Sie die Taste **F5** , um die APP auszuführen.

10. Geben Sie in der APP zwei Zahlen ein, wählen Sie einen Vorgang aus, und wählen Sie dann die **=** Schaltfläche aus.

     Das richtige Ergebnis wird angezeigt.

    In dieser exemplarischen Vorgehensweise wurde veranschaulicht, wie ein Erweiterungs-SDK erstellt und verwendet wird, um eine [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] Bibliothek und eine nicht--Bibliothek aufzurufen [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] .

## <a name="next-steps"></a>Nächste Schritte

## <a name="see-also"></a>Weitere Informationen
- [Exemplarische Vorgehensweise: Erstellen eines SDK mit c# oder Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Erstellen einer Software Development Kit](../extensibility/creating-a-software-development-kit.md)
