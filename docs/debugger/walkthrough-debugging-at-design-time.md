---
title: Debuggen zur Entwurfszeit | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie das Direktfenster zum Debuggen von Code zur Entwurfszeit verwenden, ohne die App auszuführen. Sie können eine Funktion ausführen und den Zustand überprüfen, wenn ein Breakpoint erreicht wird.
ms.custom: SEO-VS-2020
ms.date: 01/10/2019
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f127c630cec0e0b64ab5602e81f2b314a3896b16
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148846"
---
# <a name="debug-at-design-time-in-visual-studio-c-ccli-visual-basic-f"></a>Debuggen zur Entwurfszeit in Visual Studio (C#, C++/CLI, Visual Basic, F#)

Zum Debuggen von Code zur Entwurfszeit statt während der Ausführung einer App können Sie das Fenster **Direkt** verwenden.

Wenn Sie XAML-Code für eine App aus dem XAML-Designer debuggen möchten, z. B. in Szenarien mit deklarativer Datenbindung, können Sie **Debuggen** > **An Prozess anhängen** verwenden.

## <a name="use-the-immediate-window"></a>Verwenden des Fensters „Direkt“

Über das Fenster **Direkt** in Visual Studio können Sie eine Funktion oder Unterroutine ausführen, ohne Ihre App auszuführen. Wenn die Funktion oder die Unterroutine einen Haltepunkt enthält, unterbricht Visual Studio die Ausführung am Haltepunkt. Sie können dann die Debuggerfenster verwenden, um den Programmzustand zu überprüfen. Dieses Feature wird *Debuggen zur Entwurfszeit* genannt.

Das folgende Beispiel ist in Visual Basic. Sie können das Fenster **Direkt** auch zur Entwurfszeit in C#-, F#- und C++/CLI-Apps verwenden.

1. Fügen Sie den folgenden Code in eine leere Visual Basic-Konsolen-App ein:

   ```vb
   Module Module1

       Sub Main()
           MySub()
       End Sub

       Function MyFunction() As Decimal
           Static i As Integer
           i = i + 1
           Return i
       End Function

       Sub MySub()
           MyFunction()

       End Sub
   End Module
   ```

1. Legen Sie einen Haltepunkt in der Zeile **End Function** fest.

1. Öffnen Sie das Fenster **Direkt**, indem Sie **Debuggen** > **Fenster** > **Direkt** auswählen. Geben Sie `?MyFunction` im Fenster ein, und drücken Sie dann die **EINGABETASTE**.

   Der Haltepunkt wird erreicht, und der Wert von **MyFunction** im Fenster **Lokal** ist **1**. Sie können die Aufrufliste und andere Debugfenster überprüfen, während sich die App im Unterbrechungsmodus befindet.

1. Wählen Sie auf der Visual Studio-Symbolleiste **Weiter** aus. Die App wird beendet, und **1** wird im Fenster **Direkt** zurückgegeben. Stellen Sie sicher, dass noch immer der Entwurfsmodus aktiv ist.

1. Geben Sie `?MyFunction` erneut im Fenster **Direkt** ein, und drücken Sie die **EINGABETASTE**. Der Haltepunkt wird erreicht, und der Wert von **MyFunction** im Fenster **Lokal** ist **2**.

1. Wählen Sie nicht **Weiter** aus, sondern geben Sie `?MySub()` im Fenster **Direkt** ein, und drücken Sie dann die **EINGABETASTE**. Der Haltepunkt wird erreicht, und der Wert von **MyFunction** im Fenster **Lokal** ist **3**. Sie können den App-Status überprüfen, während sich die App im Unterbrechungsmodus befindet.

1. Wählen Sie **Weiter**. Der Haltepunkt wird erneut erreicht, und der Wert von **MyFunction** im Fenster **Lokal** ist jetzt **2**. Das Fenster **Direkt** gibt **Der Ausdruck wurde ausgewertet und weist keinen Wert auf** zurück.

1. Wählen Sie noch einmal **Weiter** aus. Die App wird beendet, und **2** wird im Fenster **Direkt** zurückgegeben. Stellen Sie sicher, dass noch immer der Entwurfsmodus aktiv ist.

1. Um den Inhalt des Fensters **Direkt** zu löschen, klicken Sie mit der rechten Maustaste in das Fenster, und wählen Sie **Alles löschen** aus.

## <a name="debug-a-custom-xaml-control-at-design-time-by-attaching-to-xaml-designer"></a>Debuggen eines benutzerdefinierten XAML-Steuerelements zur Entwurfszeit durch Anhängen an den XAML-Designer

1. Öffnen Sie Ihre Projektmappe oder Ihr Projekt in Visual Studio.

1. Erstellen Sie die Projektmappe bzw. das Projekt.

1. Öffnen Sie die XAML-Seite mit dem benutzerdefinierten Steuerelement, das Sie debuggen möchten.

   Bei UWP-Projekten für Windows Build 16299 oder höher wird mit diesem Schritt der Prozess *UwpSurface.exe* gestartet. Bei WPF-Projekten für Windows Build 16299 oder höher wird mit diesem Schritt der Prozess *WpfSurface.exe* gestartet. Bei WPF- oder UWP-Versionen vor Windows Build 16299 wird mit diesem Schritt der Prozess *XDesProc.exe* gestartet. 

1. Öffnen Sie eine zweite Instanz von Visual Studio. Öffnen Sie keine Projektmappe bzw. kein Projekt in der zweiten Instanz.

1. Öffnen Sie in der zweiten Instanz von Visual Studio das Menü **Debuggen**, und wählen Sie **An Prozess anhängen...** aus.

1. Wählen Sie je nach Projekttyp (siehe vorherige Schritte) den Prozess *UwpSurface.exe*, *WpfSurface.exe* oder *XDesProc.exe* aus der Liste der verfügbaren Prozesse aus.

1. Wählen Sie im Dialogfeld **Anfügen an Prozess** im Feld **Anfügen an** den richtigen Codetyp für das benutzerdefinierte Steuerelement aus, das Sie debuggen möchten.

   Wenn Ihr benutzerdefiniertes Steuerelement in einer .NET-Sprache geschrieben wurde, wählen Sie den entsprechenden .NET-Codetyp aus, z. B. **Verwaltet (CoreCLR)** . Wenn Ihr benutzerdefiniertes Steuerelement in C++ geschrieben wurde, wählen Sie **Nativ** aus.

1. Fügen Sie die zweite Instanz von Visual Studio an, indem Sie auf die Schaltfläche **Anfügen** klicken.

1. Öffnen Sie in der zweiten Instanz von Visual Studio die Codedateien, die dem benutzerdefinierten Steuerelement zugeordnet sind, das Sie debuggen möchten. Stellen Sie sicher, dass Sie nur die Dateien öffnen, nicht die gesamte Projektmappe oder das gesamte Projekt.

1. Platzieren Sie die erforderlichen Haltepunkte in den zuvor geöffneten Dateien.

1. Schließen Sie in der ersten Instanz von Visual Studio die XAML-Seite mit dem benutzerdefinierten Steuerelement, das Sie debuggen möchten (dieselbe Seite, die Sie in den vorherigen Schritten geöffnet haben).

1. Öffnen Sie in der ersten Instanz von Visual Studio die XAML-Seite, die Sie im vorherigen Schritt geschlossen haben. Dadurch hält der Debugger am ersten Haltepunkt an, den Sie in der zweiten Instanz von Visual Studio festgelegt haben.

1. Debuggen Sie den Code in der zweiten Instanz von Visual Studio.

## <a name="see-also"></a>Siehe auch
- [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)
- [Debuggersicherheit](../debugger/debugger-security.md)