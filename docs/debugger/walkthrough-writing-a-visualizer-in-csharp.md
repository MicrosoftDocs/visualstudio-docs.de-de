---
title: Schreiben einer Schnellansicht in C# | Microsoft-Dokumentation
description: In diesem Artikel finden Sie eine exemplarische Vorgehensweise zum Erstellen einer einfachen Schnellansicht in C#. Außerdem finden Sie hier die erforderlichen Schritte für die Durchführung mit oder ohne der Elementvorlage für Schnellansichten.
ms.custom: SEO-VS-2020, seodec18
ms.date: 05/27/2020
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: 53467461-8e0f-45ee-9bc4-374bbaeaf00f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: f127d178a8103cfaa01c43970848f5772827440f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884064"
---
# <a name="walkthrough-writing-a-visualizer-in-c"></a>Exemplarische Vorgehensweise: Schreiben einer Schnellansicht in C\#

In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie in C# eine einfache Schnellansicht schreiben können. Die in dieser exemplarischen Vorgehensweise erstellte Schnellansicht zeigt den Inhalt einer Zeichenfolge in einem Windows Forms-Meldungsfeld an. Diese einfache Zeichenfolgen-Schnellansicht ist an sich nicht sehr nützlich, doch wird an ihrem Beispiel die grundlegende Vorgehensweise für das Erstellen besser geeigneter Schnellansichten für andere Datentypen gezeigt.

> [!NOTE]
> Die angezeigten Dialogfelder und Menübefehle können sich je nach den aktiven Einstellungen oder der verwendeten Version von den in der Hilfe beschriebenen unterscheiden. Wählen Sie im Menü **Extras** die Option **Einstellungen importieren und exportieren** aus, um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Reset settings (Zurücksetzen der Einstellungen)](../ide/environment-settings.md#reset-settings).

Schnellansichtcode muss in eine DLL eingefügt werden, die vom Debugger gelesen wird. Deshalb müssen Sie als Erstes ein Klassenbibliotheksprojekt für die DLL erstellen.

## <a name="create-a-visualizer-manually"></a>Manuelles Erstellen einer Schnellansicht

Führen Sie die folgenden Aufgaben aus, um eine Schnellansicht zu erstellen.

### <a name="to-create-a-class-library-project"></a>So erstellen Sie ein Klassenbibliotheksprojekt

1. Erstellen Sie ein neues Klassenbibliotheksprojekt.

    ::: moniker range=">=vs-2019"
    Drücken Sie **ESC**, um das Startfenster zu schließen. Geben Sie **STRG+Q** ein, um das Suchfeld zu öffnen, geben Sie **Klassenbibliothek** ein, wählen Sie **Vorlagen** aus, und wählen Sie dann **Create a new Class Library (.NET Framework)** (Neue Klassenbibliothek erstellen (.NET Framework)) aus. Wählen Sie im angezeigten Dialogfeld **Erstellen** aus.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Klicken Sie oben in der Menüleiste auf **Datei** > **Neu** > **Projekt**. Wählen Sie im linken Bereich des Dialogfelds **Neues Projekt** unter **Visual C#** den Eintrag **.NET Framework** aus. Wählen Sie dann im mittleren Bereich **Klassenbibliothek (.NET Framework)** aus.
    ::: moniker-end

2. Geben Sie einen geeigneten Namen für die Klassenbibliothek ein, z. B. `MyFirstVisualizer`, und klicken Sie dann auf **Erstellen** oder **OK**.

   Nachdem Sie die Klassenbibliothek erstellt haben, müssen Sie einen Verweis auf Microsoft.VisualStudio.DebuggerVisualizers.DLL hinzufügen, damit die dort definierten Klassen verwendet werden können. Bevor Sie den Verweis hinzufügen, müssen Sie aber einige Klassen umbenennen, damit sie aussagekräftige Namen haben.

### <a name="to-rename-class1cs-and-add-microsoftvisualstudiodebuggervisualizers"></a>So benennen Sie Class1.cs um und fügen Microsoft.VisualStudio.DebuggerVisualizers hinzu

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf Class1.cs, und wählen Sie im Kontextmenü die Option **Umbenennen** aus.

2. Ändern Sie den Namen von Class1.cs in einen aussagekräftigeren Namen, zum Beispiel DebuggerSide.cs.

   > [!NOTE]
   > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] passt die Klassendeklaration in DebuggerSide.cs automatisch an den neuen Dateinamen an.

3. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **Verweise**, und wählen Sie im Kontextmenü **Verweis hinzufügen** aus.

4. Wählen Sie im Dialogfeld **Verweis hinzufügen** auf der Registerkarte **Durchsuchen** den Eintrag **Durchsuchen** aus, und suchen Sie nach Microsoft.VisualStudio.DebuggerVisualizers.DLL.

    Sie finden die DLL im Unterverzeichnis *\<Visual Studio Install Directory>\Common7\IDE\PublicAssemblies* des Installationsverzeichnisses von Visual Studio.

5. Klicken Sie auf **OK**.

6. Fügen Sie in DebuggerSide.cs Folgendes zu den `using`-Anweisungen hinzu:

   ```csharp
   using Microsoft.VisualStudio.DebuggerVisualizers;
   ```

   Jetzt können Sie den debuggerseitigen Code erstellen. Dies ist der Code, der innerhalb des Debuggers ausgeführt wird, um die gewünschten Informationen anzuzeigen. Zuerst müssen Sie die Deklaration des `DebuggerSide`-Objekts ändern, sodass es von der `DialogDebuggerVisualizer`-Basisklasse erbt.

### <a name="to-inherit-from-dialogdebuggervisualizer"></a>So lassen Sie das Objekt von "DialogDebuggerVisualizer" erben

1. Gehen Sie in DebuggerSide.cs zu folgender Codezeile:

   ```csharp
   public class DebuggerSide
   ```

2. Ändern Sie den Code in:

   ```csharp
   public class DebuggerSide : DialogDebuggerVisualizer
   ```

   `DialogDebuggerVisualizer` verfügt über eine abstrakte Methode (`Show`), die Sie überschreiben müssen.

#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>So überschreiben Sie die DialogDebuggerVisualizer.Show-Methode

- Fügen Sie die folgende **Methode** in `public class DebuggerSide` hinzu:

  ```csharp
  protected override void Show(IDialogVisualizerService windowService, IVisualizerObjectProvider objectProvider)
  {
  }
  ```

  Die `Show`-Methode enthält den Code, der für das Erstellen des Dialogfelds der Schnellansicht oder eines anderen Benutzeroberflächenelements verantwortlich ist. Sie zeigt die Informationen an, die der Debugger an die Schnellansicht übergibt. Den Code, der das Dialogfeld erstellt und die Informationen anzeigt, müssen Sie hinzufügen. In dieser exemplarischen Vorgehensweise verwenden Sie dazu ein Windows Forms-Meldungsfeld. Zunächst müssen Sie einen Verweis und eine `using`-Anweisung für System.Windows.Forms hinzufügen.

### <a name="to-add-systemwindowsforms"></a>So fügen Sie System.Windows.Forms hinzu

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **Verweise**, und wählen Sie im Kontextmenü **Verweis hinzufügen** aus.

2. Wählen Sie im Dialogfeld **Verweis hinzufügen** auf der Registerkarte **Durchsuchen** die Option **Durchsuchen** aus, und suchen Sie nach System.Windows.Forms.DLL.

    Sie finden die DLL unter *C:\Windows\Microsoft.NET\Framework\v4.0.30319*.

3. Klicken Sie auf **OK**.

4. Fügen Sie in DebuggerSide.cs Folgendes zu den `using`-Anweisungen hinzu:

   ```csharp
   using System.Windows.Forms;
   ```

   Als Nächstes fügen Sie Code hinzu, um die Benutzeroberfläche der Schnellansicht zu erstellen und anzuzeigen. Da dies Ihre erste Schnellansicht ist, halten wir die Benutzeroberfläche bewusst einfach und verwenden deshalb ein Meldungsfeld.

### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>So zeigen Sie die Ausgabe der Schnellansicht in einem Dialogfeld an

1. Fügen Sie der `Show`-Methode folgende Codezeile hinzu:

   ```csharp
   MessageBox.Show(objectProvider.GetObject().ToString());
   ```

    Dieser Beispielcode enthält keine Fehlerbehandlung. Sie sollten die Fehlerbehandlung in einer echten Schnellansicht oder in anderen Anwendungen berücksichtigen.

2. Wählen Sie im Menü **Erstellen** die Option **MyFirstVisualizer erstellen** aus. Das Projekt sollte erfolgreich erstellt werden. Korrigieren Sie alle Buildfehler, bevor Sie fortfahren.

   Damit ist der debuggerseitige Code fertig. Ein Schritt fehlt allerdings noch: Das Attribut, das der zu debuggenden Seite mitteilt, welche Auflistung von Klassen die Schnellansicht enthält.

### <a name="to-add-the-type-to-visualize-for-the-debuggee-side-code"></a>So fügen Sie den Typ hinzu, der für den zu debuggenden Code visualisiert werden soll

Geben Sie den zu visualisierenden Typ (die Objektquelle) für die zu debuggende Komponente mit dem <xref:System.Diagnostics.DebuggerVisualizerAttribute>-Attribut im debuggerseitigen Code an. Die `Target`-Eigenschaft legt den zu visualisierenden Typ fest.

1. Fügen Sie DebuggerSide.cs den folgenden Attributcode hinzu, und zwar nach den `using`-Anweisungen und vor `namespace MyFirstVisualizer`:

   ```csharp
   [assembly:System.Diagnostics.DebuggerVisualizer(
   typeof(MyFirstVisualizer.DebuggerSide),
   typeof(VisualizerObjectSource),
   Target = typeof(System.String),
   Description = "My First Visualizer")]
   ```

2. Wählen Sie im Menü **Erstellen** die Option **MyFirstVisualizer erstellen** aus. Das Projekt sollte erfolgreich erstellt werden. Korrigieren Sie alle Buildfehler, bevor Sie fortfahren.

   Damit ist das Erstellen Ihrer ersten Schnellansicht abgeschlossen. Wenn Sie alle Schritte richtig befolgt haben, können Sie die Schnellansicht problemlos erstellen und in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] installieren. Bevor Sie eine Schnellansicht in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] installieren, sollten Sie jedoch durch Tests sicherstellen, dass sie ordnungsgemäß funktioniert. Als Nächstes erstellen Sie eine Testumgebung, in der Sie die Schnellansicht ohne Installation in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ausführen können.

### <a name="to-add-a-test-method-to-show-the-visualizer"></a>So fügen Sie eine Testmethode zur Anzeige der Schnellansicht hinzu

1. Fügen Sie der `public DebuggerSide`-Klasse folgende Methode hinzu:

   ```csharp
   public static void TestShowVisualizer(object objectToVisualize)
   {
      VisualizerDevelopmentHost visualizerHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));
      visualizerHost.ShowVisualizer();
   }
   ```

2. Wählen Sie im Menü **Erstellen** die Option **MyFirstVisualizer erstellen** aus. Das Projekt sollte erfolgreich erstellt werden. Korrigieren Sie alle Buildfehler, bevor Sie fortfahren.

   Als Nächstes müssen Sie ein ausführbares Projekt erstellen, um die Schnellansichts-DLL aufzurufen. Der Einfachheit halber verwenden wir ein Konsolenanwendungsprojekt.

### <a name="to-add-a-console-application-project-to-the-solution"></a>So fügen Sie der Projektmappe ein Konsolenanwendungsprojekt hinzu

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf die Projektmappe, und wählen Sie **Hinzufügen** und dann **Neues Projekt** aus.

    ::: moniker range=">=vs-2019"
    Geben Sie im Suchfeld **Konsolen-App** ein, wählen Sie **Vorlagen** und danach **Create a new Console App (.NET Framework)** (Neue Konsolen-App erstellen (.NET Framework)) aus. Wählen Sie im angezeigten Dialogfeld **Erstellen** aus.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Klicken Sie oben in der Menüleiste auf **Datei** > **Neu** > **Projekt**. Wählen Sie im linken Bereich des Dialogfelds **Neues Projekt** unter **Visual C#** **Windows Desktop** und dann im mittleren Bereich **Konsolen-App (.NET Framework)** aus.
    ::: moniker-end

2. Geben Sie einen geeigneten Namen für die Klassenbibliothek ein, z. B. `MyTestConsole`, und klicken Sie dann auf **Erstellen** oder **OK**.

   Jetzt müssen Sie die notwendigen Verweise hinzufügen, damit MyFirstVisualizer von MyTestConsole aufgerufen werden kann.

### <a name="to-add-necessary-references-to-mytestconsole"></a>So fügen Sie MyTestConsole die erforderlichen Verweise hinzu

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **MyTestConsole**, und wählen Sie im Kontextmenü **Verweis hinzufügen** aus.

2. Wählen Sie im Dialogfeld **Verweis hinzufügen** auf der Registerkarte **Durchsuchen** Microsoft.VisualStudio.DebuggerVisualizers.DLL aus.

3. Klicken Sie auf **OK**.

4. Klicken Sie mit der rechten Maustaste auf **MyTestConsole**, und klicken Sie erneut auf **Verweis hinzufügen**.

5. Klicken Sie im Dialogfeld **Verweis hinzufügen** auf die Registerkarte **Projekte**, und klicken Sie dann auf MyFirstVisualizer.

6. Klicken Sie auf **OK**.

   Als Nächstes fügen Sie den Code hinzu und stellen damit die Testumgebung fertig.

### <a name="to-add-code-to-mytestconsole"></a>So fügen Sie MyTestConsole Code hinzu

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf Program.cs, und wählen Sie im Kontextmenü **Umbenennen** aus.

2. Vergeben Sie für den Namen Program.cs eine aussagekräftigere Bezeichnung, zum Beispiel TestConsole.cs.

    > [!NOTE]
    > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] passt die Klassendeklaration in TestConsole.cs automatisch an den neuen Dateinamen an.

3. Fügen Sie in TestConsole.cs den `using`-Anweisungen den folgenden Code hinzu:

   ```csharp
   using MyFirstVisualizer;
   ```

4. Fügen Sie der `Main`-Methode den folgenden Code hinzu:

   ```csharp
   String myString = "Hello, World";
   DebuggerSide.TestShowVisualizer(myString);
   ```

   Jetzt sind Sie soweit, dass Sie Ihre erste Schnellansicht testen können.

### <a name="to-test-the-visualizer"></a>So testen Sie die Schnellansicht

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **MyTestConsole**, und wählen Sie im Kontextmenü **Als Startprojekt festlegen** aus.

2. Wählen Sie im Menü **Debuggen** den Befehl **Starten** aus.

    Die Konsolenanwendung wird gestartet und die Schnellansicht mit der Zeichenfolge "Hello, World" angezeigt.

   Herzlichen Glückwunsch! Sie haben soeben Ihre erste Schnellansicht erstellt und getestet.

   Wenn Sie die Schnellansicht in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und nicht nur innerhalb der Testumgebung verwenden möchten, dann müssen Sie die Schnellansicht installieren. Weitere Informationen finden Sie unter [Vorgehensweise: Install a Visualizer (Vorgehensweise: Installieren einer Schnellansicht)](../debugger/how-to-install-a-visualizer.md).

::: moniker range="vs-2017"

## <a name="create-a-visualizer-using-the-visualizer-item-template"></a>Erstellen einer Schnellansicht mithilfe der Schnellansichtelementvorlage

Bis jetzt wurde in dieser exemplarischen Vorgehensweise erläutert, wie eine Schnellansicht manuell erstellt wird. Dies war eine Lernübung. Da Sie jetzt wissen, wie eine simple Schnellansicht funktioniert, können Sie diese auch auf einfachere Weise mithilfe der Schnellansichtelementvorlage erstellen.

Zuerst müssen Sie ein neues Klassenbibliotheksprojekt erstellen.

### <a name="to-create-a-new-class-library"></a>So erstellen Sie eine neue Klassenbibliothek

1. Klicken Sie im Menü **Datei** auf **Neu > Projekt**.

2. Wählen Sie im Dialogfeld **Neues Projekt** unter **Visual C#** die Option **.NET Framework** aus.

3. Wählen Sie im mittleren Bereich die Option **Klassenbibliothek** aus.

4. Geben Sie im Feld **Name** für die Klassenbibliothek einen entsprechenden Namen ein, zum Beispiel „MySecondVisualizer“.

5. Klicken Sie auf **OK**.

   Jetzt können Sie ein Schnellansichtelement hinzufügen:

### <a name="to-add-a-visualizer-item"></a>So fügen Sie ein Schnellansichtelement hinzu

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf MySecondVisualizer.

2. Wählen Sie im Kontextmenü die Option **Hinzufügen** aus, und klicken Sie danach auf **Neues Element**.

3. Wählen Sie im Dialogfeld **Neues Element hinzufügen** unter **Visual C#-Elemente** die Option **Debuggerschnellansicht** aus.

4. Geben Sie im Feld **Name** einen passenden Namen ein, zum Beispiel „SecondVisualizer.cs“.

5. Klicken Sie auf **Hinzufügen**.

   Das ist auch schon alles! Sehen Sie sich die Datei SecondVisualizer.cs und den Code an, den die Vorlage hinzugefügt hat. Experimentieren Sie ruhig mit dem Code. Mit den erlernten Grundlagen können Sie in Zukunft komplexere und nützlichere Schnellansichten nach Ihren eigenen Vorstellungen erstellen.
::: moniker-end

## <a name="see-also"></a>Siehe auch

- [Schnellansichtarchitektur](../debugger/visualizer-architecture.md)
- [How to: Install a Visualizer (Vorgehensweise: Installieren einer Schnellansicht)](../debugger/how-to-install-a-visualizer.md).
- [Erstellen benutzerdefinierter Schnellansichten](../debugger/create-custom-visualizers-of-data.md)
