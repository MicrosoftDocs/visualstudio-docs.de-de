---
title: 'Tutorial: Debuggen von C#- und C++-Code (gemischter Modus)'
description: Erfahren Sie, wie Sie eine native DLL aus einer .NET Core- oder .NET Framework-App mithilfe des Debuggens im gemischten Modus debuggen können.
ms.custom: seodec18
ms.date: 11/02/2018
ms.topic: tutorial
dev_langs:
- CSharp
- C++
helpviewer_keywords:
- mixed mode debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 0b51a41a2b2df5ac685caebbf08606ae86b4230a
ms.sourcegitcommit: e132a870ec198fdcec289227f1a0c1c48fef070c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2020
ms.locfileid: "93344526"
---
# <a name="tutorial-debug-c-and-c-in-the-same-debugging-session"></a>Tutorial: Debuggen von C# und C++ in derselben Debugsitzung

In Visual Studio können Sie mehr als einen Debugtyp in einer Debugsitzung aktivieren. Dies wird als Debuggen im gemischten Modus bezeichnet. In diesem Tutorial lernen Sie das Debuggen verwalteten und nativen Codes in einer einzigen Debugsitzung.

Sie lernen, wie Sie nativen Code aus einer verwalteten App debuggen, aber Sie können auch [verwalteten Code aus einer nativen App debuggen](../debugger/how-to-debug-in-mixed-mode.md). Der Debugger unterstützt auch andere Typen des Debuggens im gemischten Modus, wie z.B. das [Debuggen von Python- und nativem Code](../python/debugging-mixed-mode-c-cpp-python-in-visual-studio.md) und das Verwenden des Skriptdebuggers in App-Typen wie ASP.NET.

In diesem Tutorial werden Sie Folgendes durchführen:

> [!div class="checklist"]
> * Erstellen einer einfachen nativen DLL
> * Erstellen einer einfachen .NET Core- oder .NET Framework-App, die die DLL aufruft
> * Konfigurieren des Debuggens im gemischten Modus
> * Starten des Debuggers
> * Erreichen eines Breakpoints in der verwalteten App
> * Schrittweise Ausführung des nativen Codes

## <a name="prerequisites"></a>Voraussetzungen

Visual Studio muss in den folgenden Workloads installiert sein:
- **Desktopentwicklung mit C++**
- Entweder **.NET-Desktopentwicklung** oder **Plattformübergreifende .NET Core-Entwicklung**, je nachdem, welchen App-Typ Sie erstellen möchten

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es unter [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/) kostenlos herunterladen.

Falls Sie bereits über Visual Studio verfügen, aber die Workloads noch installieren müssen, klicken Sie im linken Bereich des Dialogfelds **Neues Projekt** auf den Link **Visual Studio-Installer öffnen**. Wählen Sie im Visual Studio-Installer die benötigten Workloads aus, und klicken Sie dann auf **Modify** (Anpassen).

## <a name="create-a-simple-native-dll"></a>Erstellen einer einfachen nativen DLL

**So erstellen Sie die Dateien für das DLL-Projekt:**

1. Öffnen Sie Visual Studio, und erstellen Sie ein Projekt.

    ::: moniker range=">=vs-2019"
    Drücken Sie **ESC**, um das Startfenster zu schließen. Drücken Sie **STRG+Q**, um das Suchfeld zu öffnen, geben Sie **Leeres Projekt** ein, wählen Sie **Vorlagen** und dann **Leeres Projekt** für C++ aus. Wählen Sie im angezeigten Dialogfeld **Erstellen** aus. Geben Sie anschließend einen Namen wie **Debuggen_im_gemischten_Modus** ein, und klicken Sie auf **Erstellen**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Klicken Sie oben in der Menüleiste auf **Datei** > **Neu** > **Projekt**. Wählen Sie im linken Bereich des Dialogfelds **Neues Projekt** unter **Visual C++** **Andere** aus, und wählen Sie dann im mittleren Bereich **Leeres Projekt** aus. Geben Sie anschließend einen Namen wie **Debuggen_im_gemischten_Modus** ein, und klicken Sie auf **OK**.
    ::: moniker-end

    Wenn die Projektvorlage **Leeres Projekt** nicht angezeigt wird, öffnen Sie unter **Tools** > **Tools und Features abrufen...** den Visual Studio-Installer. Der Visual Studio-Installer wird gestartet. Wählen Sie die Workload **Desktopentwicklung mit C++** , und klicken Sie dann auf **Ändern**.

    Visual Studio erstellt daraufhin das Projekt.

1. Wählen Sie im **Projektmappen-Explorer** **Quelldateien** aus, und klicken sie dann auf **Projekt** > **Neues Element hinzufügen**. Klicken Sie alternativ auf **Quelldateien**, und wählen Sie **Hinzufügen** > **Neues Element** aus.

1. Klicken Sie im Dialogfeld **Neues Element** auf **C++-Datei (.cpp)** . Geben Sie im Feld **Name** **Mixed_Mode.cpp** ein, und klicken Sie dann auf **Hinzufügen**.

    Visual Studio fügt eine neue C++-Datei im **Projektmappen-Explorer** hinzu.

1. Kopieren Sie den folgenden Code in die Datei *Mixed_Mode.cpp*:

    ```cpp
    #include "Mixed_Mode.h"
    ```

1. Wählen Sie im **Projektmappen-Explorer** **Headerdateien** aus, und klicken sie dann auf **Projekt** > **Neues Element hinzufügen**. Klicken Sie alternativ auf **Headerdateien**, und wählen Sie **Hinzufügen** > **Neues Element** aus.

1. Klicken Sie im Dialogfeld **Neues Element** auf **Headerdatei (.h)** . Geben Sie im Feld **Name** **Mixed_Mode.h** ein, und klicken Sie dann auf **Hinzufügen**.

   Visual Studio fügt eine neue Headerdatei im **Projektmappen-Explorer** hinzu.

1. Kopieren Sie den folgenden Code in die Datei *Mixed_Mode.h*:

    ```cpp
    #ifndef MIXED_MODE_MULTIPLY_HPP
    #define MIXED_MODE_MULTIPLY_HPP

    extern "C"
    {
      __declspec(dllexport) int __stdcall mixed_mode_multiply(int a, int b) {
        return a * b;
      }
    }
    #endif
    ```

1. Klicken Sie auf **Datei** > **Alle speichern**, oder drücken Sie **STRG**+**UMSCHALT**+**S**, um die Datei zu speichern.

**So erstellen und konfigurieren Sie das DLL-Projekt:**

1. Wählen Sie auf der Visual Studio-Symbolleiste die Konfiguration **Debuggen** und entweder **x86** oder **x64** für die Plattform aus. Wenn die aufrufende App eine .NET Core-App ist, die immer im 64-Bit-Modus ausgeführt wird, wählen Sie **x64** als Plattform aus.

1. Wählen Sie im **Projektmappen-Explorer** den Projektknoten **Mixed_Mode_Debugging** aus, und klicken Sie auf das **Eigenschaftensymbol**. Klicken Sie alternativ auf den Projektknoten und dann auf **Eigenschaften**.

1. Achten Sie darauf, dass die **Konfiguration** oben im **Eigenschaftenpanel** auf **Active(Debug)** festgelegt ist und die **Plattform** mit der in der Symbolleiste angegeben Einstellung übereinstimmt (**x64** oder **Win32** für die x86-Plattform).

   > [!IMPORTANT]
   > Wenn Sie die Plattform von **x86** in **x64** (oder andersherum) ändern, müssen Sie die Eigenschaften für die neue Plattform erneut festlegen.

1. Wählen Sie links unter **Konfigurationseigenschaften** **Linker** > **Erweitert** aus, und wählen Sie in der Dropdownliste neben **Kein Einstiegspunkt** **Nein** aus. Wenn Sie die Einstellung in **Nein** geändert haben, klicken Sie auf **Anwenden**.

1. Wählen Sie unter **Konfigurationseigenschaften** **Allgemein** aus, und wählen Sie aus der Dropdownliste neben **Konfigurationstyp** **Dynamische Bibliothek (DLL)** aus. Klicken Sie auf **Anwenden** und dann auf **OK**.

   ![Native DLL ändern](../debugger/media/mixed-mode-set-as-native-dll.png)

1. Wählen Sie das Projekt im **Projektmappen-Explorer** aus, und wählen Sie dann **Erstellen** > **Projektmappe erstellen** aus. Drücken Sie anschließend **F7**, oder klicken Sie mit der rechten Maustaste auf das Projekt, und klicken Sie auf **Erstellen**.

   Das Projekt wird fehlerfrei erstellt.

## <a name="create-a-simple-managed-app-to-call-the-dll"></a>Erstellen einer einfachen verwalteten App, die die DLL aufruft

1. Öffnen Sie Visual Studio, und erstellen Sie ein neues Projekt.

    ::: moniker range=">=vs-2019"
    Drücken Sie **ESC**, um das Startfenster zu schließen. Geben Sie **STRG+Q** ein, um das Suchfeld zu öffnen, geben Sie **Konsole** ein, und klicken Sie auf **Vorlagen**, und wählen Sie dann **Konsolen-App (.NET Core)** oder **Konsolen-App (.NET Framework)** für C# aus. Wählen Sie im angezeigten Dialogfeld **Erstellen** aus.

    Geben Sie dann einen Namen wie **Anruf_App_im_gemischten_Modus** ein, und klicken Sie auf **Erstellen**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Klicken Sie oben in der Menüleiste auf **Datei** > **Neu** > **Projekt**. Wählen Sie im linken Bereich des Dialogfelds **Neues Projekt** unter **Visual C#** **Windows Desktop** und dann im mittleren Bereich **Konsolen-App (.NET Framework)** oder **Konsolen-App (.NET Core)** aus.

    Geben Sie dann einen Namen wie **Anruf_App_im_gemischten_Modus** ein, und klicken Sie auf **OK**.
    ::: moniker-end

    Wenn die Vorlage **Konsolen-App** nicht angezeigt wird, öffnen Sie unter **Tools** > **Tools und Features abrufen...** den Visual Studio-Installer. Wählen Sie beispielsweise die Workload **.NET-Desktopentwicklung** aus, und klicken Sie anschließend auf **Ändern**.

    > [!NOTE]
    > Sie können das neue verwaltete Projekt auch Ihrer vorhandenen C++-Projektmappe hinzufügen. Wir erstellen das Projekt in einer neuen Projektmappe, um das Debuggen im gemischten Modus schwieriger zu gestalten.

   Visual Studio erstellt das leere Projekt und zeigt es im **Projektmappen-Explorer** an.

1. Ersetzen Sie den gesamten Code in *Program.cs* durch den folgenden:

    ```csharp
    using System;
    using System.Runtime.InteropServices;

    namespace Mixed_Mode_Calling_App
    {
        public class Program
        {
            // Replace the file path shown here with the
            // file path on your computer. For .NET Core, the typical (default) path
            // for a 64-bit DLL might look like this:
            // C:\Users\username\source\repos\Mixed_Mode_Debugging\x64\Debug\Mixed_Mode_Debugging.dll
            // Here, we show a typical path for a DLL targeting the **x86** option.
            [DllImport(@"C:\Users\username\source\repos\Mixed_Mode_Debugging\Debug\Mixed_Mode_Debugging.dll", EntryPoint =
            "mixed_mode_multiply", CallingConvention = CallingConvention.StdCall)]
            public static extern int Multiply(int x, int y);
            public static void Main(string[] args)
            {
                int result = Multiply(7, 7);
                Console.WriteLine("The answer is {0}", result);
                Console.ReadKey();
            }
        }
    }
    ```

1. Ersetzen Sie im neuen Code den Dateipfad in `[DllImport]` durch den Dateipfad zur *Mixed_Mode_Debugging.dll*, die Sie gerade erstellt haben. Weitere Informationen finden Sie in den Codekommentaren. Achten Sie darauf, dass Sie den Platzhalter *username* entsprechend ersetzen.

1. Klicken Sie auf **Datei** > **Save Program.cs** (Program.cs speichern), oder drücken Sie **STRG**+**S**, um die Datei zu speichern.

## <a name="configure-mixed-mode-debugging"></a>Konfigurieren des Debuggens im gemischten Modus

1. Wählen Sie im **Projektmappen-Explorer** den Projektknoten **Mixed_Mode_Calling_App** aus, und klicken Sie auf das **Eigenschaftensymbol**. Klicken Sie alternativ auf den Projektknoten und dann auf **Eigenschaften**.

1. Wählen Sie im rechten Bereich **Debuggen** aus, aktivieren Sie das Kontrollkästchen **Debuggen von nativem Code aktivieren**, und schließen Sie anschließend die Eigenschaftenseite, um die Änderungen zu speichern.

    ![Debuggen im gemischten Modus aktivieren](../debugger/media/mixed-mode-enable-native-code-debugging.png)

## <a name="set-a-breakpoint-and-start-debugging"></a>Festlegen eines Breakpoints und Starten des Debuggens

1. Öffnen Sie im C#-Projekt die Datei *Program.cs*. Legen Sie einen Breakpoint in der folgenden Codezeile fest, indem Sie auf den linken Rand klicken, die Zeile auswählen und dann **F9** drücken. Alternativ können Sie mit der rechten Maustaste auf die Codezeile klicken und **Breakpoint** > **Breakpoint einfügen** auswählen.

    ```csharp
    int result = Multiply(7, 7);
    ```

    Am linken Rand wird an der Stelle des Breakpoints ein roter Kreis angezeigt.

1. Drücken Sie **F5**, und klicken Sie auf den grünen Pfeil auf der Visual Studio-Symbolleiste, oder klicken Sie auf **Debuggen** > **Debuggen starten**, um das Debuggen zu starten.

   Der Debugger hält an dem Breakpoint an, den Sie festlegen. Ein gelber Pfeil markiert die Stelle, an der der Debugger gerade angehalten hat.

## <a name="step-in-and-out-of-native-code"></a>Einzelschritt und Ausführen bis Rücksprung in nativem Code

1. Wenn das Debuggen in der verwalteten App angehalten ist, drücken Sie **F11**, oder klicken Sie auf **Debuggen** > **Einzelschritt**.

   Die native Headerdatei *Mixed_Mode.h* wird geöffnet, und der gelbe Pfeil gibt die Stelle an, an der der Debugger sich gerade befindet.

   ![Schrittweise Ausführung des nativen Codes](../debugger/media/mixed-mode-step-into-native-code.png)

1. Jetzt können Sie Breakpoints festlegen und erreichen und sich Variablen im nativen oder verwalteten Code ansehen.

   - Zeigen Sie mit der Maus auf Variablen im Quellcode, um deren Werte anzuzeigen.

   - Sehen Sie sich Variablen und deren Werte in den Fenstern **Auto** und **Lokal** an.

   - Wenn der Debugger angehalten hat, können Sie auch die Fenster **Überwachen** und **Aufrufliste** verwenden.

1. Drücken Sie erneut **F11**, um den Debugger eine Zeile weiter laufen zu lassen.

1. Drücken sie **UMSCHALT**+**F11**, oder klicken Sie auf **Debuggen** > **Ausführen bis Rücksprung**, um in der verwalteten App mit der Ausführung fortzufahren und diese anzuhalten.

1. Drücken Sie **F5**, oder klicken Sie auf den grünen Pfeil, um mit dem Debuggen der App fortzufahren.

Herzlichen Glückwunsch! Damit haben Sie das Tutorial zum Debuggen im gemischten Modus abgeschlossen.

## <a name="next-step"></a>Nächster Schritt

In diesem Tutorial haben Sie gelernt, wie Sie nativen Code einer verwalteten App debuggen, indem Sie das Debuggen im gemischten Modus aktivieren. Einen Überblick über andere Debuggerfeatures finden Sie in folgendem Artikel:

> [!div class="nextstepaction"]
> [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)
