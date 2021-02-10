---
title: Erweitern von Eigenschaften, Aufgabenliste, Ausgabe, Fenster "Optionen"
description: Erfahren Sie, wie Sie Informationen zu Ihrem Tool Fenster in Visual Studio in eine neue Options Seite und eine neue Einstellung auf der Eigenschaften Seite integrieren.
ms.date: 11/04/2016
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- properties pane
- task list
- output window
- properties window
- tutorials
- tool windows
ms.assetid: 06990510-5424-44b8-9fd9-6481acec5c76
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2586618b16afa8f8bfd6b7aa529486adf1d9ce41
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938134"
---
# <a name="extend-the-properties-task-list-output-and-options-windows"></a>Erweitern der Fenster Eigenschaften, Aufgabenliste, Ausgabe und Optionen
Sie können auf ein beliebiges Tool Fenster in Visual Studio zugreifen. In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie Informationen zu Ihrem Tool Fenster in eine neue **options** Seite und eine neue Einstellung auf der **Eigenschaften** Seite integrieren und wie Sie in die **Aufgabenliste** -und **Ausgabe** Fenster schreiben.

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Sie ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-tool-window"></a>Erstellen einer Erweiterung mit einem Tool Fenster

1. Erstellen Sie ein Projekt mit **dem Namen "** **dedolist** " mithilfe der VSIX-Vorlage, und fügen Sie eine benutzerdefinierte Tool Fenster-Element Vorlage mit dem Namen ""

    > [!NOTE]
    > Weitere Informationen zum Erstellen einer Erweiterung mit einem Tool Fenster finden Sie unter [Erstellen einer Erweiterung mit einem Tool Fenster](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="set-up-the-tool-window"></a>Einrichten des Tool Fensters
 Fügen Sie ein Textfeld hinzu, in das Sie ein neues TODO-Element, eine Schaltfläche zum Hinzufügen des neuen Elements zur Liste und ein ListBox-Element eingeben, um die Elemente in der Liste anzuzeigen.

1. Löschen Sie in " *dedowindow. XAML*" die Steuerelemente Button, TextBox und StackPanel aus dem UserControl-Steuerelement.

    > [!NOTE]
    > Dadurch wird der **Button1_Click** Ereignishandler nicht gelöscht, den Sie in einem späteren Schritt wieder verwenden.

2. Ziehen Sie im Abschnitt **alle WPF** -Steuerelemente der **Toolbox** ein **Canvas** -Steuerelement in das Raster.

3. Ziehen Sie ein **Textfeld**, eine **Schaltfläche** und ein **ListBox** in den Zeichenbereich. Ordnen Sie die Elemente so an, dass sich das Textfeld und die Schaltfläche auf derselben Ebene befinden, und das ListBox-Steuerelement füllt den restlichen Fenster unterhalb aus, wie in der folgenden Abbildung dargestellt.

     ![Fertig gestelltes Toolfenster](../extensibility/media/t5-toolwindow.png "T5-ToolWindow")

4. Suchen Sie im XAML-Bereich die Schaltfläche, und legen Sie deren Content-Eigenschaft auf **Add** fest. Verbinden Sie den Schaltflächen-Ereignishandler erneut mit dem Schaltflächen-Steuerelement, indem Sie ein- `Click="button1_Click"` Attribut Der Canvas-Block sollte wie folgt aussehen:

    ```xml
    <Canvas HorizontalAlignment="Left" Width="306">
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>
    </Canvas>
    ```

### <a name="customize-the-constructor"></a>Anpassen des Konstruktors

1. Fügen Sie in der Datei *TodoWindowControl.XAML.cs* die folgende using-Direktive hinzu:

    ```csharp
    using System;
    ```

2. Fügen Sie einen öffentlichen Verweis auf das todowindow-Element hinzu, und lassen Sie den todowindowcontrol-Konstruktor einen todowindow-Parameter verwenden. Der Code sollte wie folgt aussehen:

    ```csharp
    public TodoWindow parent;

    public TodoWindowControl(TodoWindow window)
    {
        InitializeComponent();
        parent = window;
    }
    ```

3. Ändern Sie in *TodoWindow.cs* den "dedowindowcontrol"-Konstruktor, sodass er den Parameter "dedowindow" enthält. Der Code sollte wie folgt aussehen:

    ```csharp
    public TodoWindow() : base(null)
    {
        this.Caption = "TodoWindow";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;

         this.Content = new TodoWindowControl(this);
    }
    ```

## <a name="create-an-options-page"></a>Erstellen einer Options Seite
 Sie können im Dialogfeld **Optionen** eine Seite angeben, sodass die Benutzereinstellungen für das Tool Fenster ändern können. Zum Erstellen einer Options Seite muss sowohl eine Klasse, die die Optionen beschreibt, als auch ein Eintrag in der Datei *TodoListPackage.cs* oder *todolistpackage. vb* beschrieben werden.

1. Fügen Sie eine Klasse namens `ToolsOptions.cs`hinzu. Legen Sie die `ToolsOptions` Klasse von ab <xref:Microsoft.VisualStudio.Shell.DialogPage> .

   ```csharp
   class ToolsOptions : DialogPage
   {
   }
   ```

2. Fügen Sie Folgendes mithilfe einer Direktive hinzu:

   ```csharp
   using Microsoft.VisualStudio.Shell;
   ```

3. Die Seite Optionen in dieser exemplarischen Vorgehensweise enthält nur eine Option mit dem Namen daysahead. Fügen Sie der-Klasse ein privates Feld mit dem Namen **daysahead** und eine Eigenschaft mit dem Namen **daysahead** hinzu `ToolsOptions` :

   ```csharp
   private double daysAhead;

   public double DaysAhead
   {
       get { return daysAhead; }
       set { daysAhead = value; }
   }
   ```

   Nun müssen Sie das Projekt auf dieser Options Seite erkennen.

### <a name="make-the-options-page-available-to-users"></a>Verfügbar machen der Options Seite für Benutzer

1. Fügen Sie in *TodoWindowPackage.cs* <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> der Klasse einen hinzu `TodoWindowPackage` :

    ```csharp
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]
    ```

2. Der erste Parameter für den provideoptionpage-Konstruktor ist der Typ der-Klasse `ToolsOptions` , den Sie zuvor erstellt haben. Der zweite Parameter, "ToDo", ist der Name der Kategorie im Dialogfeld " **Optionen** ". Der dritte Parameter, "Allgemein", ist der Name der Unterkategorie des Dialog Felds " **Optionen** ", in dem die Optionsseite verfügbar ist. Die nächsten zwei Parameter sind Ressourcen-IDs für Zeichen folgen. der erste ist der Name der Kategorie, und der zweite ist der Name der Unterkategorie. Der Final-Parameter bestimmt, ob mithilfe von Automation auf diese Seite zugegriffen werden kann.

     Wenn ein Benutzer die Options Seite öffnet, sollte er der folgenden Abbildung ähneln.

     ![Seite "Optionen"](../extensibility/media/t5optionspage.gif "T5OptionsPage")

     Beachten Sie die Kategorie **TODO** und die Unterkategorie **Allgemein**.

## <a name="make-data-available-to-the-properties-window"></a>Verfügbar machen von Daten für die Eigenschaftenfenster
 Sie können ToDo-Listen Informationen verfügbar machen, indem Sie eine Klasse mit dem Namen erstellen `TodoItem` , die Informationen zu den einzelnen Elementen in der TODO-Liste speichert.

1. Fügen Sie eine Klasse namens `TodoItem.cs`hinzu.

     Wenn das Tool Fenster für Benutzer verfügbar ist, werden die Elemente im ListBox-Element durch "dedoitems" dargestellt. Wenn der Benutzer eines dieser Elemente im Listenfeld auswählt, werden im Fenster **Eigenschaften** Informationen zu dem Element angezeigt.

     Um Daten im **Eigenschaften** Fenster verfügbar zu machen, können Sie die Daten in öffentliche Eigenschaften mit zwei speziellen Attributen (und) umwandeln `Description` `Category` . `Description` der Text, der am unteren Rand des Fensters **Eigenschaften** angezeigt wird. `Category` bestimmt, wo die-Eigenschaft angezeigt werden soll, wenn das **Eigenschaften** Fenster in der **kategorisierten** Ansicht angezeigt wird. In der folgenden Abbildung befindet sich das Fenster **Eigenschaften** in **der kategorisierten** Ansicht, die Eigenschaft **Name** in der Kategorie **TODO-Felder** ist ausgewählt, und die Beschreibung der Eigenschaft **Name** wird unten im Fenster angezeigt.

     ![Eigenschaftenfenster](../extensibility/media/t5properties.png "T5Properties")

2. Fügen Sie die folgenden using-Direktiven der *TodoItem.cs* -Datei hinzu.

    ```csharp
    using System.ComponentModel;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. Fügen Sie der `public` Klassen Deklaration den Zugriffsmodifizierer hinzu.

    ```csharp
    public class TodoItem
    {
    }
    ```

     Fügen Sie die beiden Eigenschaften `Name` und hinzu `DueDate` . Wir führen `UpdateList()` und später aus `CheckForErrors()` .

    ```csharp
    public class TodoItem
    {
        private TodoWindowControl parent;
        private string name;
        [Description("Name of the ToDo item")]
        [Category("ToDo Fields")]
        public string Name
        {
            get { return name; }
            set
            {
                name = value;
                parent.UpdateList(this);
            }
        }

        private DateTime dueDate;
        [Description("Due date of the ToDo item")]
        [Category("ToDo Fields")]
        public DateTime DueDate
        {
            get { return dueDate; }
            set
            {
                dueDate = value;
                parent.UpdateList(this);
                parent.CheckForErrors();
            }
        }
    }
    ```

4. Fügen Sie dem Benutzer Steuerelement einen privaten Verweis hinzu. Fügen Sie einen Konstruktor hinzu, der das Benutzer Steuerelement und den Namen für dieses TODO-Element annimmt. Um den Wert für zu ermitteln `daysAhead` , wird die Options Seiten Eigenschaft abgerufen.

    ```csharp
    private TodoWindowControl parent;

    public TodoItem(TodoWindowControl control, string itemName)
    {
        parent = control;
        name = itemName;
        dueDate = DateTime.Now;

        double daysAhead = 0;
        IVsPackage package = parent.parent.Package as IVsPackage;
        if (package != null)
        {
            object obj;
            package.GetAutomationObject("ToDo.General", out obj);

            ToolsOptions options = obj as ToolsOptions;
            if (options != null)
            {
                daysAhead = options.DaysAhead;
            }
        }

        dueDate = dueDate.AddDays(daysAhead);
    }
    ```

5. Da Instanzen der `TodoItem` -Klasse im Listenfeld gespeichert werden und das ListBox-Steuerfeld die- `ToString` Funktion aufruft, müssen Sie die-Funktion überladen `ToString` . Fügen Sie *TodoItem.cs* nach dem-Konstruktor und vor dem Ende der-Klasse den folgenden Code hinzu.

    ```csharp
    public override string ToString()
    {
        return name + " Due: " + dueDate.ToShortDateString();
    }
    ```

6. Fügen Sie in *TodoWindowControl.XAML.cs* der-Klasse Stub `TodoWindowControl` -Methoden für die `CheckForError` -Methode und die- `UpdateList` Methode hinzu. Platzieren Sie Sie nach ProcessDialogChar und vor dem Ende der Datei.

    ```csharp
    public void CheckForErrors()
    {
    }
    public void UpdateList(TodoItem item)
    {
    }
    ```

     Die `CheckForError` -Methode ruft eine Methode auf, die im übergeordneten Objekt denselben Namen hat, und diese Methode prüft, ob Fehler aufgetreten sind, und behandelt diese ordnungsgemäß. Die `UpdateList` -Methode aktualisiert das ListBox-Element im übergeordneten Steuerelement. die-Methode wird aufgerufen, wenn die `Name` -Eigenschaft und die-Eigenschaft `DueDate` in dieser Klasse geändert werden Sie werden später implementiert.

## <a name="integrate-into-the-properties-window"></a>Integrieren in die Eigenschaftenfenster
 Schreiben Sie nun den Code, mit dem das ListBox-Steuerfeld verwaltet wird, das an das **Eigenschaften** Fenster gebunden wird.

 Sie müssen den Click-Handler der Schaltfläche ändern, um das Textfeld zu lesen, ein todoitem-Element zu erstellen und es dem ListBox-Element hinzufügen.

1. Ersetzen Sie die vorhandene `button1_Click` Funktion durch Code, der ein neues todoitem erstellt und es dem ListBox-Element hinzufügt. Sie ruft auf `TrackSelection()` , das später definiert wird.

    ```csharp
    private void button1_Click(object sender, RoutedEventArgs e)
    {
        if (textBox.Text.Length > 0)
        {
            var item = new TodoItem(this, textBox.Text);
            listBox.Items.Add(item);
            TrackSelection();
            CheckForErrors();
        }
    }
    ```

2. Wählen Sie im Designansicht das ListBox-Steuerelement aus. Klicken Sie im **Eigenschaften** Fenster auf die Schaltfläche **Ereignishandler** , und suchen Sie nach dem Ereignis **SelectionChanged** . Füllen Sie das Textfeld mit **listBox_SelectionChanged** aus. Dadurch wird ein Stub für einen SelectionChanged-Handler hinzugefügt und dem Ereignis zugewiesen.

3. Implementieren Sie die `TrackSelection()`-Methode. Da Sie die Dienste erhalten müssen, müssen Sie den Zugriff auf die Dienste von "" auf "" festlegen <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> . Fügen Sie der `TodoWindow`-Klasse die folgende Methode hinzu:

    ```
    internal object GetVsService(Type service)
    {
        return GetService(service);
    }
    ```

4. Fügen Sie die folgenden using-Direktiven zu *TodoWindowControl.XAML.cs* hinzu:

    ```csharp
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.Shell.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    ```

5. Füllen Sie den SelectionChanged-Handler wie folgt aus:

    ```
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)
    {
        TrackSelection();
    }
    ```

6. Füllen Sie nun die TrackSelection-Funktion aus, die die Integration mit dem **Eigenschaften** Fenster ermöglicht. Diese Funktion wird aufgerufen, wenn der Benutzer ein Element in das ListBox-Element einfügt oder auf ein Element im Listenfeld klickt. Der Inhalt des ListBox-Steuer Felds wird einem SelectionContainer hinzugefügt, und der SelectionContainer wird an den-Ereignishandler des **Eigenschaften** Fensters weitergeleitet <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> . Der TrackSelection-Dienst verfolgt die ausgewählten Objekte in der Benutzeroberfläche und zeigt deren Eigenschaften an.

    ```csharp
    private SelectionContainer mySelContainer;
    private System.Collections.ArrayList mySelItems;
    private IVsWindowFrame frame = null;

    private void TrackSelection()
    {
        if (frame == null)
        {
            var shell = parent.GetVsService(typeof(SVsUIShell)) as IVsUIShell;
            if (shell != null)
            {
                var guidPropertyBrowser = new
                Guid(ToolWindowGuids.PropertyBrowser);
                shell.FindToolWindow((uint)__VSFINDTOOLWIN.FTW_fForceCreate,
                ref guidPropertyBrowser, out frame);
            }
        }
        if (frame != null)
            {
                frame.Show();
            }
        if (mySelContainer == null)
        {
            mySelContainer = new SelectionContainer();
        }

        mySelItems = new System.Collections.ArrayList();

        var selected = listBox.SelectedItem as TodoItem;
        if (selected != null)
        {
            mySelItems.Add(selected);
        }

        mySelContainer.SelectedObjects = mySelItems;

        ITrackSelection track = parent.GetVsService(typeof(STrackSelection))
                                as ITrackSelection;
        if (track != null)
        {
            track.OnSelectChange(mySelContainer);
        }
    }
    ```

     Nachdem Sie nun über eine Klasse verfügen, die im **Eigenschaften** Fenster verwendet werden kann, können Sie das Fenster **Eigenschaften** in das Tool Fenster integrieren. Wenn der Benutzer auf ein Element im Listenfeld im Tool Fenster klickt, sollte das **Eigenschaften** Fenster entsprechend aktualisiert werden. Ebenso sollte das zugeordnete Element aktualisiert werden, wenn der Benutzer ein TODO-Element im **Eigenschaften** Fenster ändert.

7. Fügen Sie jetzt den Rest des UpdateList-Funktions Codes in *TodoWindowControl.XAML.cs* hinzu. Er sollte das geänderte Element "Element" aus dem Listenfeld löschen und erneut hinzufügen.

    ```csharp
    public void UpdateList(TodoItem item)
    {
        var index = listBox.SelectedIndex;
        listBox.Items.RemoveAt(index);
        listBox.Items.Insert(index, item);
        listBox.SelectedItem = index;
    }
    ```

8. Testen Sie Ihren Code. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz sollte angezeigt werden.

9. Öffnen Sie **die**  >  **options** Seite Extras. Die Kategorie TODO sollte im linken Bereich angezeigt werden. Kategorien sind in alphabetischer Reihenfolge aufgelistet. sehen Sie sich daher die TS an.

10. Auf der Optionsseite für **TODO** sollten Sie sehen, dass die- `DaysAhead` Eigenschaft auf **0** festgelegt ist. Ändern Sie den Wert in **2**.

11. Öffnen Sie im Menü **Ansicht/andere Fenster** den Befehl **todowindow**. Geben Sie im Textfeld **EndDate** ein, und klicken Sie auf **Hinzufügen**.

12. Im Listenfeld sollte das Datum zwei Tage später als heute angezeigt werden.

## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>Fügen Sie dem Ausgabefenster Text und den Elementen den Aufgabenliste
 Für den **Aufgabenliste** erstellen Sie ein neues Objekt vom Typ Task und fügen dieses Aufgaben Objekt dann der **Aufgabenliste** hinzu, indem Sie die zugehörige- `Add` Methode aufrufen. Um in das **Ausgabe** Fenster zu schreiben, rufen Sie die zugehörige- `GetPane` Methode auf, um ein Pane-Objekt zu erhalten, und rufen Sie dann die- `OutputString` Methode des Pane-Objekts auf.

1. Fügen Sie in *TodoWindowControl.XAML.cs* in der- `button1_Click` Methode Code hinzu, um den **allgemeinen** Bereich des **Ausgabe** Fensters (standardmäßig) zu erhalten, und schreiben Sie darin. Die Methode sollte wie folgt aussehen:

    ```csharp
    private void button1_Click(object sender, EventArgs e)
    {
        if (textBox.Text.Length > 0)
        {
            var item = new TodoItem(this, textBox.Text);
            listBox.Items.Add(item);

            var outputWindow = parent.GetVsService(
                typeof(SVsOutputWindow)) as IVsOutputWindow;
            IVsOutputWindowPane pane;
            Guid guidGeneralPane = VSConstants.GUID_OutWindowGeneralPane;
            outputWindow.GetPane(ref guidGeneralPane, out pane);
            if (pane != null)
            {
                 pane.OutputString(string.Format(
                    "To Do item created: {0}\r\n",
                 item.ToString()));
        }
            TrackSelection();
            CheckForErrors();
        }
    }
    ```

2. Um dem Aufgabenliste Elemente hinzuzufügen, benötigen Sie eine, um der Klasse "" von "" die Klasse "" von "" zu "". Die-Klasse muss von abgeleitet werden <xref:Microsoft.VisualStudio.Shell.TaskProvider> . Fügen Sie am Ende der-Klasse den folgenden Code hinzu `TodoWindowControl` .

    ```csharp
    [Guid("72de1eAD-a00c-4f57-bff7-57edb162d0be")]
    public class TodoWindowTaskProvider : TaskProvider
    {
        public TodoWindowTaskProvider(IServiceProvider sp)
            : base(sp)
        {
        }
    }
    ```

3. Fügen Sie als nächstes der-Klasse einen privaten Verweis auf `TodoTaskProvider` und eine- `CreateProvider()` Methode hinzu `TodoWindowControl` . Der Code sollte wie folgt aussehen:

    ```csharp
    private TodoWindowTaskProvider taskProvider;
    private void CreateProvider()
    {
        if (taskProvider == null)
        {
            taskProvider = new TodoWindowTaskProvider(parent);
            taskProvider.ProviderName = "To Do";
        }
    }
    ```

4. Fügen Sie hinzu `ClearError()` , um die Aufgabenliste zu löschen, und `ReportError()` , wodurch der-Klasse ein Eintrag in Aufgabenliste der-Klasse hinzugefügt wird `TodoWindowControl` .

    ```csharp
    private void ClearError()
    {
        CreateProvider();
        taskProvider.Tasks.Clear();
    }
    private void ReportError(string p)
    {
        CreateProvider();
        var errorTask = new Task();
        errorTask.CanDelete = false;
        errorTask.Category = TaskCategory.Comments;
        errorTask.Text = p;

        taskProvider.Tasks.Add(errorTask);

        taskProvider.Show();

        var taskList = parent.GetVsService(typeof(SVsTaskList))
            as IVsTaskList2;
        if (taskList == null)
        {
            return;
        }

        var guidProvider = typeof(TodoWindowTaskProvider).GUID;
         taskList.SetActiveProvider(ref guidProvider);
    }
    ```

5. Implementieren Sie nun die- `CheckForErrors` Methode wie folgt.

    ```csharp
    public void CheckForErrors()
    {
        foreach (TodoItem item in listBox.Items)
        {
            if (item.DueDate < DateTime.Now)
            {
                ReportError("To Do Item is out of date: "
                    + item.ToString());
            }
        }
    }
    ```

## <a name="try-it-out"></a>Ausprobieren

1. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz wird geöffnet.

2. Öffnen Sie das **Fenster "todowindow** " (  >  **Weitere Fenster**"  >  **todowindow**" anzeigen).

3. Geben Sie im Textfeld etwas ein, und klicken Sie dann auf **Hinzufügen**.

     Ein Fälligkeitsdatum, das 2 Tage nach dem heutigen Tag dem Listenfeld hinzugefügt wird. Es werden keine Fehler generiert, und der **Aufgabenliste** (**View**  >  **Aufgabenliste**) sollte keine Einträge enthalten.

4. Ändern Sie **nun die Einstellung auf der** TODO-Seite Extras-  >  **Optionen**  >   von **2** zurück auf **0**.

5. Geben Sie im **Fenster Fenster** einen anderen Text ein, und klicken Sie dann erneut auf **Hinzufügen** . Dadurch wird ein Fehler und ein Eintrag in der **Aufgabenliste** ausgelöst.

     Wenn Sie Elemente hinzufügen, wird das Anfangsdatum auf jetzt plus 2 Tage festgelegt.

6. Klicken Sie im Menü **Ansicht** auf **Ausgabe** , um das Fenster **Ausgabe** zu öffnen.

     Beachten Sie, dass im **Aufgabenliste** Bereich eine Meldung angezeigt wird, wenn Sie ein Element hinzufügen.

7. Klicken Sie auf eines der Elemente im Listenfeld.

     Das Fenster **Eigenschaften** zeigt die zwei Eigenschaften für das Element an.

8. Ändern Sie eine der Eigenschaften, und drücken **Sie** dann die EINGABETASTE.

     Das Element wird im Listenfeld aktualisiert.
