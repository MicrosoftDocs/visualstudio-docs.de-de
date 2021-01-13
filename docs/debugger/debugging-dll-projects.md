---
title: Debuggen von DLL-Projekten | Microsoft-Dokumentation
description: Debuggen Sie DDL-Dateien (Dynamic Link Library) in Visual Studio. Verwenden Sie Visual Studio, um DLLs zu erstellen, kompilieren, konfigurieren und debuggen.
ms.custom: SEO-VS-2020
ms.date: 11/06/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging DLLs
- templates, debugging DLLs
- DLLs, debugging
- debugging [Visual Studio], DLLs
ms.assetid: 433cab30-d191-460b-96f7-90d2530ca243
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ec78e9a04062699ea699f45671e1210fc2306631
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728498"
---
# <a name="debug-dlls-in-visual-studio-c-c-visual-basic-f"></a>Debuggen von DLLs in Visual Studio (C#, C++, Visual Basic, F#)

Eine DLL (Dynamic-Link Library) ist eine Bibliothek, die Code und Daten enthält, die von mehreren Apps verwendet werden können. Sie können mit Visual Studio DLLs erstellen, kompilieren, konfigurieren und debuggen.

## <a name="create-a-dll"></a>Erstellen einer DLL

Die folgenden Visual Studio-Projektvorlagen können DLLs erstellen:

- C#, Visual Basic oder F#: Klassenbibliothek
- C# oder Visual Basic: Windows Forms-Steuerelementbibliothek (WCF)
- C++-Dynamic Link Library (DLL)

Weitere Informationen finden Sie unter [MFC Debugging Techniques (MFC-Debugverfahren)](../debugger/mfc-debugging-techniques.md).

Das Debuggen einer WCF-Bibliothek entspricht weitgehend dem Debuggen einer Klassenbibliothek. Weitere Informationen dazu finden Sie unter [Windows Forms-Steuerelemente](/dotnet/framework/winforms/controls/index).

Normalerweise wird eine DLL von einem anderen Projekt aufgerufen. Wenn Sie das aufrufenden Projekt debuggen, können Sie in Abhängigkeit von der DLL-Konfiguration den DLL-Code schrittweise durchlaufen und debuggen.

## <a name="dll-debug-configuration"></a><a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> DLL-Debugkonfiguration

Wenn Sie eine Visual Studio-Projektvorlage zum Erstellen einer App verwenden, werden die erforderlichen Einstellungen für die Debug- und Releasekonfigurationen automatisch durch [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] festgelegt. Sie können diese Einstellungen ggf. ändern. Weitere Informationen finden Sie in den folgenden Artikeln:

- [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Project settings for C# debug configurations (Projekteinstellungen für C#-Debugkonfigurationen)](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Projekteinstellungen für eine Visual Basic-Debugkonfiguration](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [How to: Festlegen von Debug- und Releasekonfigurationen](../debugger/how-to-set-debug-and-release-configurations.md)

### <a name="set-c-debuggableattribute"></a>Festlegen des C++-Attributs „Debuggable“

Damit der Debugger an eine C++-DLL angefügt werden kann, muss der C++-Code `DebuggableAttribute` ausgeben.

**Zum Festlegen von`DebuggableAttribute`:**

1. Wählen Sie das C++-DLL-Projekt im **Projektmappen-Explorer** aus, und wählen Sie das Symbol **Eigenschaften** aus, oder klicken Sie mit der rechten Maustaste auf das Projekt, und wählen Sie dann **Eigenschaften** aus.

1. Wählen Sie im Bereich **Eigenschaften** unter **Linker** > **Debuggen** die Option **Ja (/ASSEMBLYDEBUG)** für **Debugfähige Assembly** aus.

Weitere Informationen finden Sie unter [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute).

### <a name="set-cc-dll-file-locations"></a><a name="vxtskdebuggingdllprojectsexternal"></a> Festlegen von C/C++-DLL-Dateispeicherorten

Zum Debuggen einer externen DLL muss ein aufrufendes Projekt in der Lage sein, die DLL, ihre [PDB-Datei](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) und alle anderen Dateien zu finden, die die DLL benötigt. Sie können eine benutzerdefinierte Buildaufgabe erstellen, um diese Dateien in den *\<project folder>\Debug*-Ausgabeordner zu kopieren, oder Sie können die Dateien manuell dorthin kopieren.

Für C/C++-Projekte können Sie Header- und LIB-Dateispeicherorte in den Projekteigenschaftenseiten festlegen, anstatt sie in den Ausgabeordner zu kopieren.

**So legen Sie C/C++-Header- und LIB-Dateispeicherorte fest:**

1. Wählen Sie das C/C++-DLL-Projekt im **Projektmappen-Explorer** aus, und wählen Sie das Symbol **Eigenschaften** aus, oder klicken Sie mit der rechten Maustaste auf das Projekt, und wählen Sie dann **Eigenschaften** aus.

1. Wählen Sie oben im Bereich **Eigenschaften** unter **Konfiguration** die Option **Alle Konfigurationen** aus.

1. Geben Sie unter **C/C++**  > **Allgemein** > **Zusätzliche Includeverzeichnisse** den Ordner an, der die Headerdateien enthält.

1. Geben Sie unter **Linker** > **Allgemein** > **Zusätzliche Bibliotheksverzeichnisse** den Ordner mit LIB-Dateien an.

1. Geben Sie unter **Linker** > **Eingabe** > **Zusätzliche Abhängigkeiten** den vollständigen Pfad und Dateinamen für die LIB-Dateien an.

1. Klicken Sie auf **OK**.

Weitere Informationen zu C++-Projekteinstellungen finden Sie unter [Referenz zur C++ Windows-Eigenschaftenseite](/cpp/build/reference/property-pages-visual-cpp).

## <a name="build-a-debug-version"></a><a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> Erstellen einer Debugversion

Stellen Sie sicher, dass Sie eine Debugversion der DLL erstellen, bevor Sie mit dem Debuggen beginnen. Zum Debuggen einer DLL muss eine aufrufende App in der Lage sein, ihre [PDB-Datei](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) und alle anderen Dateien zu finden, die die DLL benötigt.

Sie können eine benutzerdefinierte Buildaufgabe erstellen, um diese DLL-Dateien in den *\<calling project folder>\Debug*-Ausgabeordner zu kopieren, oder Sie können die Dateien manuell dorthin kopieren.

Stellen Sie sicher, dass die DLL am richtigen Speicherort aufgerufen wird. Dies mag offensichtlich erscheinen, aber wenn eine aufrufenden App eine andere Kopie der DLL findet und lädt, wird der Debugger nie die von Ihnen festgelegten Haltepunkte erreichen.

## <a name="debug-a-dll"></a><a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> Debuggen einer DLL

Eine DLL kann nicht direkt ausgeführt werden. Sie muss von einer App aufgerufen werden, in der Regel von einer *EXE-Datei*. Weitere Informationen dazu finden Sie unter [Visual Studio-Projekte: C++](/cpp/ide/creating-and-managing-visual-cpp-projects).

Um eine DLL zu debuggen, können Sie [das Debuggen aus der aufrufenden App](#vxtskdebuggingdllprojectsthecallingapplication) starten oder [aus dem DLL-Projekt debuggen](how-to-debug-from-a-dll-project.md), indem Sie die aufrufenden App angeben. Sie können auch das [Direktfenster](#vxtskdebuggingdllprojectstheimmediatewindow) des Debuggers verwenden, um DLL-Funktionen oder -Methoden zur Entwurfszeit auszuwerten, ohne eine aufrufende App zu verwenden.

Weitere Informationen dazu finden Sie unter [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md).

### <a name="start-debugging-from-the-calling-app"></a><a name="vxtskdebuggingdllprojectsthecallingapplication"></a> Starten des Debuggens aus der aufrufenden App

Die folgenden Apps können eine DLL aufrufen:

- Eine App aus einem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Projekt in derselben oder einer anderen Projektmappe als die DLL.
- Eine vorhandene App, die bereits auf einem Test- oder Produktionscomputer bereitgestellt wurde und dort ausgeführt wird.
- Eine App im Web, auf die über eine URL zugegriffen wird.
- Eine Web-App mit einer Webseite, die die DLL einbettet.

Zum Debuggen einer DLL aus einer aufrufenden App können Sie folgendermaßen vorgehen:

- Öffnen Sie das Projekt für die aufrufenden App, und starten Sie das Debuggen, indem Sie **Debuggen** > **Debuggen starten** auswählen oder **F5** drücken.

  oder

- Fügen Sie den Debugger an eine vorhandene App an, die bereits auf einem Test- oder Produktionscomputer bereitgestellt wurde und dort ausgeführt wird. Verwenden Sie diese Methode für DLLs auf Websites oder in Web-Apps. Weitere Informationen finden Sie unter [Vorgehensweise: Anfügen an einen laufenden Prozess](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

Bevor Sie mit dem Debuggen der aufrufenden App beginnen, legen Sie einen Breakpoint in der DLL fest. Weitere Informationen finden Sie unter [Verwenden von Breakpoints](../debugger/using-breakpoints.md). Sobald der DLL-Haltepunkt erreicht wird, können Sie den Code schrittweise ausführen und die in den einzelnen Zeilen ausgeführten Aktionen beobachten. Weitere Informationen finden Sie unter [Navigieren im Code im Debugger](../debugger/navigating-through-code-with-the-debugger.md).

Während des Debuggens können Sie das Fenster **Module** verwenden, um die DLLs und *EXE-Dateien* zu überprüfen, die von der App geladen werden. Wählen Sie zum Öffnen des Fensters **Module** während des Debuggens **Debuggen** > **Windows** > **Module** aus. Weitere Informationen finden Sie unter [Vorgehensweise: Verwenden des Modulfensters](../debugger/how-to-use-the-modules-window.md).

### <a name="use-the-immediate-window"></a><a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> Verwenden des „Direktfensters“

Sie können das **Direktfenster** verwenden, um DLL-Funktionen oder -Methoden zur Entwurfszeit auszuwerten. Das **Direktfenster** übernimmt die Rolle einer aufrufenden App.

>[!NOTE]
>Sie können das **Direktfenster** zur Entwurfszeit mit den meisten Projekttypen verwenden. Dies wird für SQL, Webprojekte oder Skripts nicht unterstützt.

Um beispielsweise eine Methode mit dem Namen `Test` in der Klasse `Class1` zu testen, gehen Sie folgendermaßen vor:

1. Öffnen Sie bei geöffneter DLL-Projekt das **Direktfenster**, indem Sie **Debuggen** > **Windows** > **Direkt** auswählen oder **STRG**+**ALT**+**I** drücken.

1. Instanziieren Sie ein Objekt vom Typ `Class1`, indem Sie den folgenden C#-Code in das **Direktfenster** eingeben und die **EINGABETASTE** drücken. Dieser verwaltete Code kann mit entsprechenden Syntaxänderungen in C# und Visual Basic eingesetzt werden:

   ```csharp
   Class1 obj = new Class1();
   ```

   In C# müssen alle Namen vollqualifiziert sein. Alle Methoden oder Variablen müssen sich im aktuellen Gültigkeitsbereich und Kontext befinden, wenn der Sprachdienst versucht, den Ausdruck auszuwerten.

1. Vorausgesetzt, dass `Test` einen `int` -Parameter annimmt, werten Sie `Test` mit dem **Direktfenster** aus:

   ```csharp
   ?obj.Test(10);
   ```

   Das Ergebnis wird im **Direktfenster** ausgegeben.

1. Sie können mit dem Debuggen von `Test` fortfahren, indem Sie einen Haltepunkt einfügen und anschließend die Funktion erneut auswerten.

   Sobald der Breakpoint erreicht ist, können Sie `Test` in Einzelschritten durchlaufen. Nach der Ausführung von `Test` befindet sich der Debugger wieder im Entwurfsmodus.

## <a name="mixed-mode-debugging"></a><a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Debuggen im gemischten Modus

Sie können eine aufrufende App für eine DLL in verwaltetem oder nativem Code schreiben. Wenn Ihre native App eine verwaltete DLL aufruft und Sie beide debuggen möchten, können Sie sowohl die verwalteten als auch die nativen Debugger in den Projekteigenschaften aktivieren. Die genaue Vorgehensweise hängt davon ab, ob Sie den Debugvorgang über das DLL-Projekt oder über das Projekt der aufrufende Anwendung starten möchten. Weitere Informationen finden Sie unter [Vorgehensweise: Debuggen im gemischten Modus](../debugger/how-to-debug-in-mixed-mode.md).

Sie können eine native DLL auch aus einem verwalteten aufrufenden Projekt debuggen. Weitere Informationen finden Sie unter [Vorgehensweise: Debuggen von verwaltetem und nativem Code](how-to-debug-managed-and-native-code.md).

## <a name="see-also"></a>Siehe auch
- [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)
- [Vorbereitung zum Debuggen von C++-Projekten](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [C#-, F#- und Visual Basic-Projekttypen](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Project settings for a C++ Debug configuration (Projekteinstellungen für eine C++-Debugkonfiguration)](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Project settings for C# Debug configurations (Projekteinstellungen für C#-Debugkonfigurationen)](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Project settings for a Visual Basic Debug configuration (Projekteinstellungen für eine Visual Basic-Debugkonfiguration)](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Debuggersicherheit](../debugger/debugger-security.md)
