---
title: 'Exemplarische Vorgehensweise: Schreiben einer Schnellansicht in Visual Basic | Microsoft-Dokumentation'
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
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: c93bf5a1-3e5e-422f-894e-bd72c9bc1b57
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 954bd976317f5b5ad577b1236c9d7421c2d50315
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65688209"
---
# <a name="walkthrough-writing-a-visualizer-in-visual-basic"></a>Exemplarische Vorgehensweise: Schreiben einer Schnellansicht in Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] eine einfache Schnellansicht schreiben können. Die in dieser exemplarischen Vorgehensweise erstellte Schnellansicht zeigt den Inhalt einer Zeichenfolge in einem Windows Forms-Meldungsfeld an. Nach dem Muster dieser einfachen Zeichenfolgen-Schnellansicht können Sie auch Schnellansichten für andere Datentypen erstellen, die Sie in Ihren Projekten benötigen.  
  
> [!NOTE]
> Die angezeigten Dialogfelder und Menübefehle können sich je nach den aktiven Einstellungen oder der verwendeten Version von den in der Hilfe beschriebenen unterscheiden. Wählen Sie im Menü **Extras** die Option **Importieren und Exportieren** aus, um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Der Code für eine Schnellansicht muss in eine DLL eingefügt werden, die vom Debugger gelesen wird. Deshalb besteht der erste Schritt darin, ein Klassenbibliotheksprojekt für die DLL zu erstellen.  
  
## <a name="create-and-prepare-a-class-library-project"></a>Erstellen und Vorbereiten eines Klassenbibliothekprojekts  
  
#### <a name="to-create-a-class-library-project"></a>So erstellen Sie ein Klassenbibliotheksprojekt  
  
1. Wählen Sie im Menü **Datei** die Option **Neu** aus, und klicken Sie auf **Neues Projekt**.  
  
2. Klicken Sie im Dialogfeld **Neues Projekt** unter **Projekttyp**s auf **Visual Basic**.  
  
3. Klicken Sie im Feld **Vorlagen** auf **Klassenbibliothek**.  
  
4. Geben Sie im Feld **Name** einen geeigneten Namen für die Klassenbibliothek ein, z. b. **MyFirstVisualizer**.  
  
5. Klicken Sie auf **OK**.  
  
   Wenn Sie die Klassenbibliothek erstellt haben, müssen Sie einen Verweis auf Microsoft.VisualStudio.DebuggerVisualizers.DLL hinzufügen, damit die dort definierten Klassen verwendet werden können. Geben Sie dem Projekt zunächst jedoch einen aussagekräftigen Namen.  
  
#### <a name="to-rename-class1vb-and-add-microsoftvisualstudiodebuggervisualizers"></a>So benennen Sie "Class1.vb" um und fügen "Microsoft.VisualStudio.DebuggerVisualizers" hinzu  
  
1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **Class1.vb** und dann im Kontextmenü auf **Umbenennen**.  
  
2. Ändern Sie den Namen von Class1.vb in einen aussagekräftigeren Namen, zum Beispiel DebuggerSide.vb.  
  
    > [!NOTE]
    > [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] passt die Klassendeklaration in DebuggerSide.vb automatisch an den neuen Dateinamen an.  
  
3. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **MyFirstVisualizer**, und klicken Sie dann im Kontextmenü auf **Verweis hinzufügen**.  
  
4. Wählen Sie im Dialogfeld **Verweis hinzufügen** auf der Registerkarte **.NET** den Eintrag „Microsoft.VisualStudio.DebuggerVisualizers.DLL“ aus.  
  
5. Klicken Sie auf **OK**.  
  
6. Fügen Sie in DebuggerSide.vb den `Imports`-Anweisungen die folgende Anweisung hinzu:  
  
    ```  
    Imports Microsoft.VisualStudio.DebuggerVisualizers  
    ```  
  
## <a name="add-the-debugger-side-code"></a>Hinzufügen des Codes für den Debugger  
 Jetzt können Sie den Code für den Debugger erstellen. Dies ist der Code, der innerhalb des Debuggers ausgeführt wird, um die gewünschten Informationen anzuzeigen. Zuerst müssen Sie die Deklaration des `DebuggerSide`-Objekts ändern, sodass es von der `DialogDebuggerVisualizer`-Basisklasse erbt.  
  
#### <a name="to-inherit-from-dialogdebuggervisualizer"></a>So lassen Sie das Objekt von "DialogDebuggerVisualizer" erben  
  
1. Navigieren Sie in DebuggerSide.vb zu folgender Codezeile:  
  
   ```  
   Public Class DebuggerSide  
   ```  
  
2. Ändern Sie den Code folgendermaßen:  
  
   ```  
   Public Class DebuggerSide  
   Inherits DialogDebuggerVisualizer  
   ```  
  
   `DialogDebuggerVisualizer` verfügt über eine abstrakte Methode, `Show`, die Sie überschreiben müssen.  
  
#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>So überschreiben Sie die DialogDebuggerVisualizer.Show-Methode  
  
- Fügen Sie `public class DebuggerSide` folgende Methode hinzu:  
  
  ```  
  Protected Overrides Sub Show(ByVal windowService As Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService, ByVal objectProvider As Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider)  
  
      End Sub  
  ```  
  
  Die `Show`-Methode enthält den Code, der für das Erstellen des Dialogfelds der Schnellansicht oder eines anderen Benutzeroberflächenelements verantwortlich ist. Sie zeigt die Informationen an, die der Debugger an die Schnellansicht übergibt. Den Code, der das Dialogfeld erstellt und die Informationen anzeigt, müssen Sie hinzufügen. In dieser exemplarischen Vorgehensweise wird dazu ein Windows Forms-Meldungsfeld verwendet. Zuerst müssen Sie einen Verweis und eine `Imports`-Anweisung für <xref:System.Windows.Forms> hinzufügen.  
  
#### <a name="to-add-systemwindowsforms"></a>So fügen Sie System.Windows.Forms hinzu  
  
1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **Verweise**, und klicken Sie dann im Kontextmenü auf **Verweis hinzufügen**.  
  
2. Klicken Sie im Dialogfeld **Verweis hinzufügen** auf der Registerkarte **.NET** auf den Eintrag **System.Windows.Forms**.  
  
3. Klicken Sie auf **OK**.  
  
4. Fügen Sie in DebuggerSide.cs den `Imports`-Anweisungen die folgende Anweisung hinzu:  
  
    ```  
    Imports System.Windows.Forms  
    ```  
  
## <a name="create-your-visualizers-user-interface"></a>Erstellen der Benutzeroberfläche der Schnellansicht  
 Als Nächstes fügen Sie Code hinzu, um die Benutzeroberfläche der Schnellansicht zu erstellen und anzuzeigen. Da dies Ihre erste Schnellansicht ist, halten wir die Benutzeroberfläche bewusst einfach und verwenden deshalb ein Meldungsfeld.  
  
#### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>So zeigen Sie die Ausgabe der Schnellansicht in einem Dialogfeld an  
  
1. Fügen Sie der `Show`-Methode folgende Codezeile hinzu:  
  
    ```  
    MessageBox.Show(objectProvider.GetObject().ToString())  
    ```  
  
     Dieser Beispielcode enthält keine Fehlerbehandlung. Sie sollten die Fehlerbehandlung in einer echten Schnellansicht oder in anderen Anwendungen berücksichtigen.  
  
2. Klicken Sie im Menü **Erstellen** auf **MyFirstVisualizer erstellen**. Das Projekt sollte erfolgreich erstellt werden. Korrigieren Sie alle Buildfehler, bevor Sie fortfahren.  
  
## <a name="add-the-necessary-attribute"></a>Hinzufügen des erforderlichen Attributs  
 Damit sind wir mit dem Code für den Debugger fertig. Ein Schritt fehlt allerdings noch: Das Attribut, das der zu debuggenden Seite mitteilt, welche Auflistung von Klassen die Schnellansicht enthält.  
  
#### <a name="to-add-the-debugee-side-code"></a>So fügen Sie den Code für die zu debuggende Seite hinzu  
  
1. Fügen Sie DebuggerSide.vb den folgenden Attributcode hinzu, und zwar nach den `Imports`-Anweisungen und vor `namespace MyFirstVisualizer`:  
  
    ```  
    <Assembly: System.Diagnostics.DebuggerVisualizer(GetType(MyFirstVisualizer.DebuggerSide), GetType(VisualizerObjectSource), Target:=GetType(System.String), Description:="My First Visualizer")>  
    ```  
  
2. Klicken Sie im Menü **Erstellen** auf **MyFirstVisualizer erstellen**. Das Projekt sollte erfolgreich erstellt werden. Korrigieren Sie alle Buildfehler, bevor Sie fortfahren.  
  
## <a name="create-a-test-harness"></a>Erstellen einer Testumgebung  
 Damit ist das Erstellen Ihrer ersten Schnellansicht abgeschlossen. Wenn Sie alle Schritte richtig befolgt haben, können Sie die Schnellansicht problemlos erstellen und in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] installieren. Bevor Sie eine Schnellansicht in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] installieren, sollten Sie jedoch durch Tests sicherstellen, dass sie ordnungsgemäß funktioniert. Als Nächstes erstellen Sie eine Testumgebung, in der Sie die Schnellansicht ohne Installation in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ausführen können.  
  
#### <a name="to-add-a-test-method-to-show-the-visualizer"></a>So fügen Sie eine Testmethode zur Anzeige der Schnellansicht hinzu  
  
1. Fügen Sie der `public DebuggerSide`-Klasse folgende Methode hinzu:  
  
   ```  
   Shared Public Sub TestShowVisualizer(ByVal objectToVisualize As Object)  
       Dim visualizerHost As New VisualizerDevelopmentHost(objectToVisualize, GetType(DebuggerSide))  
   visualizerHost.ShowVisualizer()  
   End Sub  
   ```  
  
2. Klicken Sie im Menü **Erstellen** auf **MyFirstVisualizer erstellen**. Das Projekt sollte erfolgreich erstellt werden. Korrigieren Sie alle Buildfehler, bevor Sie fortfahren.  
  
   Als Nächstes müssen Sie ein ausführbares Projekt erstellen, um die Schnellansichts-DLL aufzurufen. Verwenden Sie der Einfachheit halber ein Konsolenanwendungsprojekt.  
  
#### <a name="to-add-a-console-application-project-to-the-solution"></a>So fügen Sie der Projektmappe ein Konsolenanwendungsprojekt hinzu  
  
1. Klicken Sie im Menü **Datei** auf **Hinzufügen**, und klicken Sie dann auf **Neues Projekt**.  
  
2. Klicken Sie im Dialogfeld **Neues Projekt hinzufügen** im Feld **Vorlagen** auf **Konsolenanwendung**.  
  
3. Geben Sie im Feld **Name** einen aussagekräftigen Namen für die Konsolenanwendung ein, zum Beispiel **MyTestConsole**.  
  
4. Klicken Sie auf **OK**.  
  
   Jetzt müssen Sie die notwendigen Verweise hinzufügen, damit MyFirstVisualizer von MyTestConsole aufgerufen werden kann.  
  
#### <a name="to-add-necessary-references-to-mytestconsole"></a>So fügen Sie MyTestConsole die erforderlichen Verweise hinzu  
  
1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **MyTestConsole**, und klicken Sie dann im Kontextmenü auf **Verweis hinzufügen**.  
  
2. Wählen Sie im Dialogfeld **Verweis hinzufügen** auf der Registerkarte **.NET** den Eintrag „Microsoft.VisualStudio.DebuggerVisualizers“ aus.  
  
3. Klicken Sie auf **OK**.  
  
4. Klicken Sie mit der rechten Maustaste auf **MyTestConsole**, und klicken Sie erneut auf **Verweis hinzufügen**.  
  
5. Klicken Sie im Dialogfeld **Verweis hinzufügen** auf die Registerkarte **Projekte**, und wählen Sie dann „MyFirstVisualizer“ aus.  
  
6. Klicken Sie auf **OK**.  
  
## <a name="finish-your-test-harness-and-test-your-visualizer"></a>Fertigstellen der Testumgebung und Testen der Schnellansicht  
 Als Nächstes fügen Sie den Code hinzu und stellen damit die Testumgebung fertig.  
  
#### <a name="to-add-code-to-mytestconsole"></a>So fügen Sie MyTestConsole Code hinzu  
  
1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **Program.vb** und dann im Kontextmenü auf **Umbenennen**.  
  
2. Ändern Sie den Namen „Module1.vb“ in einen passenden Namen, z.B. **TestConsole.vb**.  
  
    [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] passt die Klassendeklaration in TestConsole.vb automatisch an den neuen Dateinamen an.  
  
3. Fügen Sie in „TestConsole. vb“ Sie die folgende `Imports`-Anweisung hinzu:  
  
   ```  
   Imports MyFirstVisualizer  
   ```  
  
4. Fügen Sie der `Main`-Methode den folgenden Code hinzu:  
  
   ```  
   Dim myString As String = "Hello, World"  
   DebuggerSide.TestShowVisualizer(myString)  
   ```  
  
   Jetzt können Sie Ihre erste Schnellansicht testen.  
  
#### <a name="to-test-the-visualizer"></a>So testen Sie die Schnellansicht  
  
1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **MyTestConsole**, und klicken Sie im Kontextmenü auf **Als Startprojekt festlegen**.  
  
2. Klicken Sie im Menü **Debuggen** auf **Starten**.  
  
    Die Konsolenanwendung wird gestartet. Die Schnellansicht wird mit der Zeichenfolge "Hello, World" angezeigt.  
  
   Herzlichen Glückwunsch! Sie haben soeben Ihre erste Schnellansicht erstellt und getestet.  
  
   Wenn Sie die Schnellansicht in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] und nicht nur innerhalb der Testumgebung verwenden möchten, dann müssen Sie die Schnellansicht installieren. Weitere Informationen finden Sie unter [Vorgehensweise: Install a Visualizer (Vorgehensweise: Installieren einer Schnellansicht)](../debugger/how-to-install-a-visualizer.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Architektur der Schnellansicht](../debugger/visualizer-architecture.md)   
 [Gewusst wie: Installieren einer Schnellansicht](../debugger/how-to-install-a-visualizer.md)   
 [Erstellen benutzerdefinierter Schnellansichten](../debugger/create-custom-visualizers-of-data.md)
