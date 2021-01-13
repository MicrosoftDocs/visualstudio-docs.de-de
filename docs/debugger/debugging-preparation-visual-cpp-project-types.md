---
title: Vorbereitung zum Debuggen von C++-Projekten | Microsoft-Dokumentation
description: In diesem Artikel finden Sie Informationen zur Vorbereitung des Debuggens der grundlegenden Projekttypen, die mit den Visual C++-Projektvorlagen in Visual Studio erstellt werden.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- project templates, debugging
- C++ projects, debugging
- debug builds, project settings
- debugging [C++]
ms.assetid: 912b4ba2-7719-43d5-b087-db33e3f9329a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 1e399b28d3ddce07cae263550b536c21ad1db028
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728303"
---
# <a name="debugging-preparation-c-project-types"></a>Vorbereitung des Debugvorgangs: C++-Projekttypen
In diesem Abschnitt wird das Debuggen grundlegender Projekttypen erläutert, die mithilfe von [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]-Projektvorlagen erstellt wurden.

 Beachten Sie, dass Projekttypen, die DLLs als Ausgabe erstellen, aufgrund ihrer gemeinsamen Features unter [Debuggen von DLL-Projekten](../debugger/debugging-dll-projects.md) besprochen werden.

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> In diesem Thema
 [Empfohlene Eigenschafteneinstellungen](#BKMK_Recommended_Property_Settings)

 [Win32-Projekte](#BKMK_Win32_Projects)

- [Debuggen einer in C oder C++ geschriebenen Win32-Anwendung](#BKMK_To_debug_a_C_or_C___Win32_application)

- [Manuelles Festlegen einer Debugkonfiguration](#BKMK_To_manually_set_a_Debug_configuration)

  [Windows Forms-Anwendungen (.NET)](#BKMK_Windows_Forms_Applications___NET_)

## <a name="recommended-property-settings"></a><a name="BKMK_Recommended_Property_Settings"></a> Empfohlene Eigenschafteneinstellungen
 Bestimmte Eigenschaften sollten für alle Szenarios des nicht verwalteten Debuggens gleich festgelegt werden. Die folgenden Tabellen zeigen die empfohlenen Eigenschafteneinstellungen. Die hier nicht aufgeführten Einstellungen können je nach verwaltetem Projekttyp unterschiedlich sein. Weitere Informationen finden Sie unter [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md).

### <a name="configuration-properties-124-cc-124-optimization-node"></a>Konfigurationseigenschaften &#124; C/C++ &#124; Optimierungsknoten

|Eigenschaftenname|Einstellung|
|-------------------|-------------|
|**Optimization**|Legen Sie für diese Eigenschaft **Deaktiviert (/ 0d)** fest. Optimierter Code ist schwieriger zu debuggen, da die generierten Anweisungen nicht direkt mit dem Quellcode übereinstimmen. Wenn das Programm einen Fehler aufweist, der nur im optimierten Code auftritt, können Sie diese Einstellung aktivieren. Beachten Sie jedoch, dass der im **Disassembly**-Fenster angezeigte Code aus optimiertem Code generiert wurde, der u. U. nicht mit dem Inhalt der Quellcodefenster übereinstimmt. Andere Funktionen, z. B. die Ausführung in Einzelschritten, verhalten sich möglicherweise nicht wie erwartet.|

### <a name="configuration-properties-124-linker-124-debugging-node"></a>Konfigurationseigenschaften &#124; Linker &#124; Debugknoten

|Eigenschaftenname|Einstellung|
|-------------------|-------------|
|**Debuginformationen generieren**|Sie sollten diese Option beim Erstellen von Debugsymbolen und Dateien, die für das Debuggen benötigt werden, immer auf **Ja (/DEBUG)** festlegen. Wenn die Anwendung in Produktion geht, können Sie die Option wieder deaktivieren.|

 [Inhalt](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)

## <a name="win32-projects"></a><a name="BKMK_Win32_Projects"></a> Win32-Projekte
 Win32-Anwendungen sind herkömmliche in C oder C++ geschriebene Windows-Programme. Das Debuggen dieses Anwendungstyps in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ist einfach.

 Win32-Anwendungen enthalten MFC-Anwendungen und ATL-Projekte. Sie verwenden Windows-APIs und u. U. auch MFC oder ATL, nutzen jedoch nicht die Common Language Runtime (CLR). Sie können aber verwalteten Code aufrufen, der die CLR verwendet.

 Die unten stehende Prozedur beschreibt, wie ein Win32-Projekt aus [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] heraus gedebuggt wird. Sie können eine Win32-Anwendung jedoch auch debuggen, indem sie sie außerhalb von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] starten und dann eine Verbindung zu ihr herstellen. Weitere Informationen finden Sie unter [Anfügen an laufende Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

### <a name="to-debug-a-c-or-c-win32-application"></a><a name="BKMK_To_debug_a_C_or_C___Win32_application"></a> Debuggen einer in C oder C++ geschriebenen Win32-Anwendung

1. Öffnen Sie das Projekt in Visual Studio.

2. Wählen Sie im Menü **Debuggen** den Befehl **Starten** aus.

3. Debuggen Sie mithilfe der Verfahren, die in [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md) erläutert werden.

### <a name="to-manually-set-a-debug-configuration"></a><a name="BKMK_To_manually_set_a_Debug_configuration"></a> Manuelles Festlegen einer Debugkonfiguration

1. Klicken Sie im Menü **Ansicht** auf die Option **Eigenschaftenseiten**.

2. Klicken Sie auf den Knoten **Konfigurationseigenschaften**, um diesen zu öffnen, sofern er nicht bereits geöffnet ist.

3. Wählen Sie **Allgemein** aus, und legen Sie den Wert der Zeile **Ausgabe** auf **Debuggen** fest.

4. Öffnen Sie den Knoten **C/C++** , und wählen Sie **Allgemein** aus.

    Geben Sie in der Zeile **Debuggen** den Typ der Debuginformationen an, die vom Compiler generiert werden sollen. Als Werte können Sie u. a. **Programmdatenbank (/Zi)** oder **Programmdatenbank zum Bearbeiten und Fortfahren (/ZI)** auswählen.

5. Wählen Sie **Optimierung** aus, und wählen Sie in der Zeile **Optimierung** aus der Dropdownliste die Option **Deaktiviert (/0d)** aus.

    Optimierter Code ist schwieriger zu debuggen, da die generierten Anweisungen nicht direkt mit dem Quellcode übereinstimmen. Wenn das Programm einen Fehler aufweist, der nur im optimierten Code auftritt, können Sie diese Einstellung aktivieren. Beachten Sie jedoch, dass der im Disassembly-Fenster angezeigte Code aus optimiertem Code generiert wurde, der u. U. nicht mit dem Inhalt der Quellcodefenster übereinstimmt. Funktionen wie die schrittweise Ausführung zeigen die Haltepunkte und den Ausführungspunkt möglicherweise nicht korrekt an.

6. Öffnen Sie den Knoten **Linker**, und wählen Sie **Debuggen** aus. Wählen Sie in der ersten **Generieren**-Zeile aus der Dropdownliste die Option **Ja (/DEBUG)** aus. Wählen Sie beim Debuggen immer diese Einstellung.

   Weitere Informationen finden Sie unter [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md).

   [Inhalt](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)

## <a name="windows-forms-applications-net"></a><a name="BKMK_Windows_Forms_Applications___NET_"></a> Windows Forms-Anwendungen (.NET)
 Die Vorlage der **Windows Forms-Anwendung (.NET)** erstellt eine [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]-Windows Forms-Anwendung. Weitere Informationen finden Sie unter [Vorgehensweise: Create a New Windows Forms Application Project (Vorgehensweise: Erstellen Sie ein Windows-Anwendungsprojekt)](/previous-versions/visualstudio/visual-studio-2010/42wc9kk5(v=vs.100)).

 Das Debuggen dieses Anwendungstyps in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ist mit dem Debuggen in verwalteten Windows Forms-Anwendungen vergleichbar.

 Wenn Sie ein Windows Forms-Projekt mit der Projektvorlage erstellen, werden die erforderlichen Einstellungen für die Debug- und Releasekonfigurationen automatisch durch [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] festgelegt. Wenn erforderlich, können Sie diese Einstellungen im Dialogfeld **Eigenschaftenseiten von \<project name>** ändern. Weitere Informationen finden Sie unter [Set debug and release configurations in Visual Studio (Festlegen von Debug- und Releasekonfigurationen in Visual Studio)](../debugger/how-to-set-debug-and-release-configurations.md).

 Weitere Informationen finden Sie unter [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md).

 Eine weitere Möglichkeit zum Debuggen einer Windows Forms-Anwendung besteht darin, die Anwendung außerhalb von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zu starten und dann eine Verbindung zu ihr herzustellen. Weitere Informationen finden Sie unter [Attach to running processes with the Visual Studio debugger (Anfügen an laufende Prozesse mit dem Visual Studio Debugger)](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

 [Inhalt](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)

## <a name="see-also"></a>Siehe auch
- [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)
- [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Attach to running processes with the Visual Studio debugger (Anfügen an laufende Prozesse mit dem Visual Studio Debugger)](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Set debug and release configurations in Visual Studio (Festlegen von Debug- und Releasekonfigurationen in Visual Studio)](../debugger/how-to-set-debug-and-release-configurations.md)
- [How to: Create a New Windows Forms Application Project (Vorgehensweise: Erstellen Sie ein Windows-Anwendungsprojekt)](/previous-versions/visualstudio/visual-studio-2010/42wc9kk5(v=vs.100))