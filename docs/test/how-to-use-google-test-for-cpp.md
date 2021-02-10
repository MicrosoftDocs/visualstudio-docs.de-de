---
title: Verwenden von Google Test für C++
description: Verwenden von Google Test zum Erstellen von C++-Komponententests in Visual Studio.
ms.date: 05/06/2017
ms.topic: how-to
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 6cf29d16432b677c6e83ba4cbaedb39f0a8d1ed2
ms.sourcegitcommit: 55bc9df751a21656de8cc5b6dbd8a2a1915ec690
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2021
ms.locfileid: "99572992"
---
# <a name="how-to-use-google-test-for-c-in-visual-studio"></a>Verwenden von Google Test für C++ in Visual Studio

In Visual Studio 2017 und höher ist Google Test als Standardkomponente der Workload **Desktopentwicklung mit C++** in die Visual Studio-IDE integriert. Öffnen Sie den Visual Studio-Installer, und suchen Sie Google Test in der Liste der Workloadkomponenten, um sicherzustellen, dass dieses auf Ihrem Computer installiert ist.

![Installieren von Google Test](media/cpp-google-component.png)

::: moniker range="vs-2019"

## <a name="add-a-google-test-project-in-visual-studio-2019"></a>Hinzufügen eines Google Test-Projekts in Visual Studio 2019

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten „Projektmappe“ und dann auf **Hinzufügen** > **Neues Projekt**.
2. Legen Sie **Sprache** auf **C++** fest, und geben Sie **test** in das Suchfeld ein. Wählen Sie in der Ergebnisliste **Google Test-Projekt** aus.
3. Benennen Sie das Testprojekt, und klicken Sie auf **OK**.

![Neues Google Test-Projekt](media/vs-2019/cpp-gtest-new-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

## <a name="add-a-google-test-project-in-visual-studio-2017"></a>Hinzufügen eines Google Test-Projekts in Visual Studio 2017

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten „Projektmappe“ und dann auf **Hinzufügen** > **Neues Projekt**.
2. Klicken Sie im linken Bereich erst auf **Visual C++**  > **Test** und dann auf **Google Test Project** (Google Test-Projekt) im mittleren Bereich.
3. Benennen Sie das Testprojekt, und klicken Sie auf **OK**.

![Neues Google Test-Projekt](media/cpp-gtest-new-project.png)

::: moniker-end

## <a name="configure-the-test-project"></a>Konfigurieren des Testprojekts

Im Dialogfeld **Testprojektkonfiguration**, das Ihnen angezeigt wird, können Sie das Projekt auswählen, das Sie testen möchten. Wenn Sie ein Projekt auswählen, fügt Visual Studio einen Verweis auf das ausgewählte Projekt hinzu. Wenn Sie kein Projekt auswählen, müssen Sie manuell Verweise auf das Projekt hinzufügen, das Sie testen möchten. Bei der Auswahl zwischen statischer und dynamischer Verknüpfung mit den Google Test-Binärdateien müssen die gleichen Aspekte wie bei jedem anderen C++-Programm beachtet werden. Weitere Informationen finden Sie unter [DLLs in Visual C++](/cpp/build/dlls-in-visual-cpp).

![Konfigurieren von Google Test-Projekten](media/cpp-gtest-config.png)

## <a name="set-additional-options"></a>Festlegen von zusätzlichen Optionen

Klicken Sie im Hauptmenü auf **Extras** > **Optionen** > **Testadapter für Google Test**, um zusätzliche Optionen festzulegen. Weitere Informationen zu diesen Einstellungen finden Sie in der Google Test-Dokumentation.

![Google Test-Projekteinstellungen](media/cpp-gtest-settings.png)

## <a name="add-include-directives"></a>Hinzufügen von include-Anweisungen

Fügen Sie Ihrer *CPP*-Testdatei alle erforderlichen `#include`-Anweisungen hinzu, um die Typen und Funktionen Ihres Programms für den Testcode anzuzeigen. In der Regel befindet sich das Programm in der Ordnerhierarchie eine Ebene darüber. Wenn Sie `#include "../"` eingeben, wird ein IntelliSense-Fenster angezeigt, und Sie können den vollständigen Pfad zur Headerdatei auswählen.

![Hinzufügen von #include-Direktiven](media/cpp-gtest-includes.png)

## <a name="write-and-run-tests"></a>Schreiben und Ausführen von Tests

Sie können nun Google Test-Tests schreiben und ausführen. Weitere Informationen über die Testmakros finden Sie unter [Google Test primer (Einführung in Google Test)](https://github.com/google/googletest/blob/master/docs/primer.md). Weitere Informationen zum Ermitteln, Ausführen und Gruppieren Ihrer Tests mithilfe des **Test-Explorers** finden Sie unter [Ausführen von Komponententests mit dem Test-Explorer](run-unit-tests-with-test-explorer.md).

## <a name="see-also"></a>Weitere Informationen

[Schreiben von Komponententests für C/C++](writing-unit-tests-for-c-cpp.md)
