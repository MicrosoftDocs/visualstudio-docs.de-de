---
title: Debugging von DLL-Projekten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging DLLs
- templates, debugging DLLs
- DLLs, debugging
- debugging [Visual Studio], DLLs
ms.assetid: 433cab30-d191-460b-96f7-90d2530ca243
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4a4533c304f84d9dc59ec6b05328528870e49655
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691400"
---
# <a name="debugging-dll-projects"></a>Debuggen von DLL-Projekten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die folgenden Vorlagen erstellen DLLs:  
  
- (C++, C# und Visual Basic): Klassenbibliothek  
  
- (C++, C# und Visual Basic): Windows Forms-Steuerelementbibliothek  
  
   Das Debuggen einer Windows-Steuerelementbibliothek entspricht weitgehend dem Debuggen eines Klassenbibliotheksprojekts. In den meisten Fällen wird das Windows-Steuerelement über ein anderes Projekt aufgerufen. Beim Debuggen des aufrufenden Projekts können Sie in den Code des Windows-Steuerelements springen, Haltepunkte festlegen und andere Debugoperationen ausführen. Weitere Informationen finden Sie unter [Steuerelemente für Windows Forms](https://msdn.microsoft.com/library/f050de8f-4ebd-4042-94b8-edf9a1dbd52a).  
  
- (C# und Visual Basic): Websteuerelementbibliothek  
  
   Weitere Informationen finden Sie unter [Web Control Library (Managed Code)](../debugger/web-control-library-managed-code.md).  
  
- (C++): MFC-ActiveX-Steuerelement und MFC-ActiveX-Steuerelement für intelligente Geräte  
  
   ActiveX-Steuerelemente können über das Internet auf einen Clientcomputer heruntergeladen sowie auf Webseiten angezeigt und aktiviert werden.  
  
   Das Debuggen von ActiveX-Steuerelementen ist mit dem Debuggen anderer Steuerelemente vergleichbar: Beide können nicht eigenständig ausgeführt werden, sondern müssen in eine HTML-Webseite eingebettet sein. Weitere Informationen finden Sie unter [How to: Debug an ActiveX Control](../debugger/how-to-debug-an-activex-control.md).  
  
- (C++): MFC-DLL für intelligente Geräte  
  
   Weitere Informationen finden Sie unter [MFC-Debuggingverfahren](../debugger/mfc-debugging-techniques.md).  
  
  Dieser Abschnitt enthält außerdem Informationen über die folgenden Themen:  
  
- [Gewusst wie: Debuggen aus einem DLL-Projekt](../debugger/how-to-debug-from-a-dll-project.md)  
  
- [Gewusst wie: Debuggen im gemischten Modus](../debugger/how-to-debug-in-mixed-mode.md)  
  
  Dieses Thema enthält folgende Abschnitte mit Hinweisen dazu, wie Sie das Debuggen von Klassenbibliotheken vorbereiten:  
  
- [Erstellen einer Debugversion](#vxtskdebuggingdllprojectsbuildingadebugversion)  
  
- [Debuggen im gemischten Modus](#vxtskdebuggingdllprojectsmixedmodedebugging)  
  
- [Ändern von Standardkonfigurationen](#vxtskdebuggingdllprojectschangingdefaultconfigurations)  
  
- [Möglichkeiten zum Debuggen einer DLL](#vxtskdebuggingdllprojectswaystodebugthedll)  
  
- [Die aufrufende Anwendung](#vxtskdebuggingdllprojectsthecallingapplication)  
  
- [Steuerelemente auf einer Webseite](#vxtskdebuggingdllprojectscontrolsonawebpage)  
  
- [Das „Direktfenster“](#vxtskdebuggingdllprojectstheimmediatewindow)  
  
## <a name="building-a-debug-version"></a><a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> Entwickeln einer Debugversion  
 Unabhängig davon, wie Sie die Debugsitzung starten, sollten Sie darauf achten, zuerst die Debugversion der DLL zu erstellen, und anschließend sicherstellen, dass die Debugversion an dem Speicherort abgelegt ist, an dem sie von der Anwendung gesucht wird. Dies scheint zwar auf der Hand zu liegen, kann aber, wenn Sie diesen Schritt auslassen, dazu führen, dass die Anwendung eine andere Version der DLL findet und lädt. Das Programm wird dann weiter ausgeführt, während Sie sich fragen, warum der Haltepunkt nicht getroffen wurde. Sie können die vom Programm geladenen DLLs beim Debuggen überprüfen, indem Sie im Debugger das Fenster **Module** öffnen. Im Fenster **Module** werden alle DLL- und EXE-Dateien aufgelistet, die im gedebuggten Prozess geladen sind. Weitere Informationen finden Sie unter Gewusst [wie: Verwenden des Fensters "Module](../debugger/how-to-use-the-modules-window.md)".  
  
 Damit der Debugger an C++-Code angefügt werden kann, muss der Code `DebuggableAttribute`ausgeben. Sie können dieses Attribut automatisch in den Code einfügen, indem Sie eine Verknüpfung über die [/ASSEMBLYDEBUG](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982) -Linkeroption herstellen.  
  
## <a name="mixed-mode-debugging"></a><a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Debuggen im gemischten Modus  
 Die aufrufende Anwendung (d. h. die Anwendung, durch die die DLL aufgerufen wird) kann in verwaltetem oder systemeigenem Code geschrieben sein. Wenn eine verwaltete DLL von systemeigenem Code aufgerufen wird und Sie beide debuggen möchten, müssen Sie sowohl den verwalteten als auch den systemeigenen Debugger aktivieren. Sie können diese Option im Dialogfeld bzw. im Fenster ** \<Project> Eigenschaften Seiten** auswählen. Wie Sie dabei vorgehen, hängt davon ab, ob Sie den Debugvorgang über das DLL-Projekt oder über das Projekt für die aufrufende Anwendung starten. Weitere Informationen finden Sie unter Gewusst [wie: Debuggen im gemischten Modus](../debugger/how-to-debug-in-mixed-mode.md).  
  
## <a name="changing-default-configurations"></a><a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> Ändern von Standardkonfigurationen  
 Wenn Sie ein Konsolenanwendungsprojekt mit einer Projektvorlage erstellen, werden die erforderlichen Einstellungen für die Debugkonfiguration und die Releasekonfiguration automatisch durch [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] festgelegt. Diese Einstellungen können ggf. geändert werden. Weitere Informationen finden Sie unter [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md), [Projekteinstellungen für c#-Debugkonfigurationen](../debugger/project-settings-for-csharp-debug-configurations.md), [Projekteinstellungen für eine Visual Basic Debugkonfiguration](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)und Gewusst [wie: Festlegen von Debug-und Releasekonfigurationen](../debugger/how-to-set-debug-and-release-configurations.md).  
  
## <a name="ways-to-debug-the-dll"></a><a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> Möglichkeiten zum Debuggen der dll  
 Jedes Projekt in diesem Abschnitt erstellt eine DLL. Eine DLL kann nicht direkt ausgeführt werden, sondern muss von einer Anwendung (normalerweise einer EXE-Datei) aufgerufen werden. Weitere Informationen finden Sie unter [Creating and Managing Visual C++ Projects](https://msdn.microsoft.com/library/11003cd8-9046-4630-a189-a32bf3b88047). Die aufrufende Anwendung kann einem der folgenden Kriterien entsprechen:  
  
- Eine Anwendung, die in einem anderen Projekt in derselben [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Projektmappe erstellt wurde, in der die Klassenbibliothek enthalten ist.  
  
- Eine vorhandene Anwendung, die bereits auf einem Test- oder Produktionscomputer bereitgestellt wurde.  
  
- Eine Anwendung im Web, auf die über eine URL zugegriffen wird.  
  
- Eine Webanwendung mit einer Webseite, in die die DLL eingebettet ist.  
  
### <a name="debugging-the-calling-application"></a><a name="vxtskdebuggingdllprojectsthecallingapplication"></a> Debuggen der aufrufenden Anwendung  
 Um eine DLL zu debuggen, beginnen Sie mit dem Debuggen der aufrufenden Anwendung. Dies ist für gewöhnlich entweder eine EXE-Datei oder eine Webanwendung. Für das Debuggen haben Sie verschiedene Möglichkeiten.  
  
- Falls ein Projekt für die aufrufende Anwendung vorhanden ist, öffnen Sie das Projekt, und starten Sie die Ausführung über das Menü **Debuggen** . Weitere Informationen finden Sie unter [How to: Start Execution](https://msdn.microsoft.com/b0fe0ce5-900e-421f-a4c6-aa44ddae453c).  
  
- Wenn es sich bei der aufrufenden Anwendung um ein vorhandenes Programm handelt, das bereits auf einem Test- oder Produktionscomputer bereitgestellt ist, können Sie den Debugger an die Anwendung anfügen. Verwenden Sie diese Methode, wenn es sich bei der DLL um ein von Internet Explorer gehostetes Steuerelement oder um ein Steuerelement auf einer Webseite handelt. Weitere Informationen finden Sie unter Gewusst [wie: Anfügen an einen laufenden Prozess](https://msdn.microsoft.com/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4).  
  
- Sie können über das DLL-Projekt debuggen. Weitere Informationen finden Sie unter Gewusst [wie: Debuggen aus einem DLL-Projekt](../debugger/how-to-debug-from-a-dll-project.md).  
  
- Sie können in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **Immediate** window. In diesem Fall übernimmt das **Direktfenster** die Funktion der Anwendung.  
  
  Bevor Sie mit dem Debuggen der aufrufenden Anwendung beginnen, werden Sie gewöhnlich einen Haltepunkt in der Klassenbibliothek festlegen. Weitere Informationen finden Sie unter [Breakpoints and Tracepoints](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583). Sobald der Haltepunkt getroffen wird, können Sie den Code schrittweise ausführen und die in den einzelnen Zeilen ausgeführten Aktionen beobachten, bis Sie das Problem eingegrenzt haben. Weitere Informationen finden Sie unter [Code Stepping Overview](https://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9).  
  
### <a name="controls-on-a-web-page"></a><a name="vxtskdebuggingdllprojectscontrolsonawebpage"></a> Steuerelemente auf einer Webseite  
 Erstellen Sie zum Debuggen eines Webseitensteuerelements – falls nicht bereits vorhanden – eine [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] -Seite, in die das Webseitensteuerelement eingebettet wird. Legen Sie anschließend Haltepunkte im Webseitencode und im Steuerelementcode fest. Rufen Sie anschließend die Webseite mit [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]auf.  
  
 Bevor Sie mit dem Debuggen der aufrufenden Anwendung beginnen, werden Sie gewöhnlich einen Haltepunkt in der DLL festlegen. Sobald der Haltepunkt getroffen wird, können Sie den Code schrittweise ausführen und die in den einzelnen Zeilen ausgeführten Aktionen beobachten, bis Sie das Problem eingegrenzt haben. Weitere Informationen finden Sie unter [Breakpoints and Tracepoints](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
### <a name="the-immediate-window"></a><a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> Das direkt Fenster  
 Sie können Funktionen oder Methoden in der DLL auswerten, ohne dass Sie über eine aufrufende Anwendung verfügen müssen. Sie verwenden dazu das Entwurfszeitdebuggen und das **Direktfenster** . Um auf diese Weise zu debuggen, führen Sie folgende Schritte aus, während das DLL-Projekt geöffnet ist:  
  
1. Öffnen Sie das **Direktfenster** des Debuggers.  
  
2. Um eine Methode mit dem Namen `Test` in der `Class1`-Klasse zu testen, instanziieren Sie ein Objekt vom Typ `Class1` , indem Sie den folgenden C#-Code im Direktfenster eingeben. Dieser verwaltete Code kann mit den entsprechenden Syntaxänderungen in Visual Basic und C++ eingesetzt werden:  
  
    ```  
    Class1 obj = new Class1();  
    ```  
  
     In C# müssen alle Namen vollqualifiziert sein. Außerdem müssen sich alle Methoden und Variablen im aktuellen Gültigkeitsbereich und Kontext der Debugsitzung befinden.  
  
3. Vorausgesetzt, dass `Test` einen `int` -Parameter annimmt, werten Sie `Test` mit dem **Direktfenster** aus:  
  
    ```  
    ?obj.Test(10)  
    ```  
  
     Das Ergebnis wird im **Direktfenster** ausgegeben.  
  
4. Sie können mit dem Debuggen von `Test` fortfahren, indem Sie einen Haltepunkt einfügen und anschließend die Funktion erneut auswerten:  
  
    ```  
    ?obj.Test(10);  
    ```  
  
     Sobald der Haltepunkt erreicht ist, können Sie `Test`in Einzelschritten ausführen. Nach der Ausführung von `Test`befindet sich der Debugger wieder im Entwurfsmodus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Debugging von verwaltetem Code](../debugger/debugging-managed-code.md)   
 [Visual C++ Projekttypen](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [C#-, F #-und Visual Basic-Projekttypen](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Projekteinstellungen für c#-Debugkonfigurationen](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Projekteinstellungen für eine Visual Basic Debugkonfiguration](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Debuggersicherheit](../debugger/debugger-security.md)
