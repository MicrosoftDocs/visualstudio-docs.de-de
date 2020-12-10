---
title: Verfügbar machen von Eigenschaften im Eigenschaften Fenster | Microsoft-Dokumentation
description: Erfahren Sie mehr über die öffentlichen Eigenschaften eines Objekts. Die Änderungen, die Sie an diesen Eigenschaften vornehmen, werden in der Eigenschaftenfenster widergespiegelt.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], exposing in Property Browser
- properties [Visual Studio SDK]
- Property Browser, exposing properties
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6f2668f8410b6e5f18b23c82202c1d33f8c67b4d
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994692"
---
# <a name="expose-properties-to-the-properties-window"></a>Eigenschaften für den Eigenschaftenfenster verfügbar machen

In dieser exemplarischen Vorgehensweise werden die öffentlichen Eigenschaften eines Objekts im **Eigenschaften** Fenster von verfügbar gemacht. Die Änderungen, die Sie an diesen Eigenschaften vornehmen, werden im Fenster **Eigenschaften** angezeigt.

## <a name="prerequisites"></a>Voraussetzungen

Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Sie ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="expose-properties-to-the-properties-window"></a>Eigenschaften für den Eigenschaftenfenster verfügbar machen

In diesem Abschnitt erstellen Sie ein benutzerdefiniertes Tool Fenster und zeigen die öffentlichen Eigenschaften des zugeordneten Fensterbereich-Objekts im **Eigenschaften** Fenster an.

### <a name="to-expose-properties-to-the-properties-window"></a>So machen Sie Eigenschaften für den Eigenschaftenfenster verfügbar

1. Jede Visual Studio-Erweiterung beginnt mit einem VSIX-Bereitstellungs Projekt, das die Erweiterungs Ressourcen enthält. Erstellen Sie ein [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX-Projekt mit dem Namen `MyObjectPropertiesExtension` . Sie finden die VSIX-Projektvorlage im Dialogfeld " **Neues Projekt** ", indem Sie nach "VSIX" suchen.

2. Fügen Sie ein Tool Fenster hinzu, indem Sie eine benutzerdefinierte Tool Fensterelement Vorlage namens hinzufügen `MyToolWindow` . Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie   >  **Neues Element** hinzufügen aus. Wechseln Sie im **Dialogfeld Neues Element hinzufügen** zu **Visual c# Elemente**  >  **Erweiterbarkeit** , und wählen Sie **benutzerdefiniertes Tool Fenster** aus. Ändern Sie im Feld **Name** am unteren Rand des Dialog Felds den Dateinamen in *MyToolWindow.cs*. Weitere Informationen zum Erstellen eines benutzerdefinierten Tool Fensters finden Sie unter [Erstellen einer Erweiterung mit einem Tool Fenster](../extensibility/creating-an-extension-with-a-tool-window.md).

3. Öffnen Sie *MyToolWindow.cs* , und fügen Sie die folgende using-Anweisung hinzu:

   ```csharp
   using System.Collections;
   using System.ComponentModel;
   using Microsoft.VisualStudio.Shell.Interop;
   ```

4. Fügen Sie nun der-Klasse die folgenden Felder hinzu `MyToolWindow` .

   ```csharp
   private ITrackSelection trackSel;
   private SelectionContainer selContainer;

   ```

5. Fügen Sie der `MyToolWindow` -Klasse den folgenden Code hinzu.

   ```csharp
   private ITrackSelection TrackSelection
   {
       get
       {
           if (trackSel == null)
               trackSel =
                  GetService(typeof(STrackSelection)) as ITrackSelection;
           return trackSel;
       }
   }

   public void UpdateSelection()
   {
       ITrackSelection track = TrackSelection;
       if (track != null)
           track.OnSelectChange((ISelectionContainer)selContainer);
   }

   public void SelectList(ArrayList list)
   {
       selContainer = new SelectionContainer(true, false);
       selContainer.SelectableObjects = list;
       selContainer.SelectedObjects = list;
       UpdateSelection();
   }

   public override void OnToolWindowCreated()
   {
       ArrayList listObjects = new ArrayList();
       listObjects.Add(this);
       SelectList(listObjects);
   }
   ```

    Die- `TrackSelection` Eigenschaft verwendet, `GetService` um einen- `STrackSelection` Dienst abzurufen, der eine- <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> Schnittstelle bereitstellt. Der `OnToolWindowCreated` Ereignishandler und die- `SelectList` Methode erstellen eine Liste ausgewählter Objekte, die nur das Tool Fenster Pane-Objekt selbst enthält. Die- `UpdateSelection` Methode weist das **Eigenschaften** Fenster an, die öffentlichen Eigenschaften des Tool Fenster Bereichs anzuzeigen.

6. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz von Visual Studio sollte angezeigt werden.

7. Wenn das **Eigenschaften** Fenster nicht sichtbar ist, öffnen Sie es, indem Sie **F4** drücken.

8. Öffnen Sie das Fenster " **mytoolwindow** ". Sie finden ihn in der **Ansicht**  >  **andere Fenster**.

    Das Fenster wird geöffnet, und die öffentlichen Eigenschaften des Fenster Bereichs werden im Fenster **Eigenschaften** angezeigt.

9. Ändern Sie die **Beschriftung** -Eigenschaft im **Eigenschaften** Fenster in **meine Objekteigenschaften**.

     Die Beschriftung des Fensters mytoolwindow ändert sich entsprechend.

## <a name="expose-tool-window-properties"></a>Tool Fenster Eigenschaften verfügbar machen

In diesem Abschnitt fügen Sie ein Tool Fenster hinzu und machen seine Eigenschaften verfügbar. Die Änderungen, die Sie an Eigenschaften vornehmen, werden im Fenster **Eigenschaften** angezeigt.

### <a name="to-expose-tool-window-properties"></a>So machen Sie Tool Fenster Eigenschaften verfügbar

1. Öffnen Sie *MyToolWindow.cs*, und fügen Sie die öffentliche boolesche Eigenschaft, die IsChecked ist, der- `MyToolWindow` Klasse hinzu.

    ```csharp
    [Category("My Properties")]
    [Description("MyToolWindowControl properties")]
    public bool IsChecked
    {
        get {
            if (base.Content == null)  return false;
            return (bool)(( MyToolWindowControl) base.Content).checkBox.IsChecked;
        }
        set {
            ((MyToolWindowControl) base.Content).checkBox.IsChecked = value;
        }
    }
    ```

     Diese Eigenschaft ruft ihren Zustand aus dem WPF-Kontrollkästchen ab, das Sie später erstellen werden.

2. Öffnen Sie *MyToolWindowControl.XAML.cs* , und ersetzen Sie den mytoolwindowcontrol-Konstruktor durch den folgenden Code.

    ```vb
    private MyToolWindow pane;
    public MyToolWindowControl(MyToolWindow pane)
    {
        InitializeComponent();
        this.pane = pane;
        checkBox.IsChecked = false;
    }
    ```

     Dadurch erhalten `MyToolWindowControl` Sie Zugriff auf den Bereich `MyToolWindow` .

3. Ändern Sie in *MyToolWindow.cs* den `MyToolWindow` Konstruktor wie folgt:

    ```csharp
    base.Content = new MyToolWindowControl(this);
    ```

4. Wechseln Sie zur Entwurfs Ansicht von mytoolwindowcontrol.

5. Löschen Sie die Schaltfläche, und fügen Sie ein Kontrollkästchen aus der **Toolbox** in die linke obere Ecke ein.

6. Fügen Sie die aktivierten und deaktivierten Ereignisse hinzu. Aktivieren Sie das Kontrollkästchen in der Entwurfs Ansicht. Klicken Sie im **Eigenschaften** Fenster auf die Schaltfläche Ereignishandler (in der oberen rechten Ecke des Fensters **Eigenschaften** ). Suchen Sie die **Option aktiviert** **checkbox_Unchecked** **, und** geben Sie **checkbox_Checked** in das Textfeld ein.

7. Fügen Sie die Kontrollkästchen-Ereignishandler hinzu:

    ```csharp
    private void checkbox_Checked(object sender, RoutedEventArgs e)
    {
        pane.IsChecked = true;
        pane.UpdateSelection();
    }
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)
    {
        pane.IsChecked = false;
        pane.UpdateSelection();
    }
    ```

8. Erstellen Sie das Projekt, und starten Sie das Debugging.

9. Öffnen Sie in der experimentellen Instanz das Fenster **mytoolwindow** .

     Suchen Sie im **Eigenschaften** Fenster nach den Eigenschaften des Fensters. Die **IsChecked** -Eigenschaft wird am unteren Rand des Fensters unter der Kategorie **meine Eigenschaften** angezeigt.

10. Aktivieren Sie das Kontrollkästchen im Fenster " **mytoolwindow** ". Im **Eigenschaften** Fenster wird die **IsChecked** -Eigenschaft in **true** geändert. Deaktivieren Sie das Kontrollkästchen im Fenster " **mytoolwindow** ". Im Fenster **Eigenschaften** wird die **IsChecked** -Eigenschaft in **false** geändert. Ändern Sie den Wert von **IsChecked** im **Eigenschaften** Fenster. Das Kontrollkästchen im Fenster " **mytoolwindow** " ändert sich entsprechend dem neuen Wert.

    > [!NOTE]
    > Wenn Sie ein im **Eigenschaften** Fenster angezeigtes Objekt verwerfen müssen, können Sie `OnSelectChange` zuerst mit einem `null` Auswahl Container aufzurufen. Nachdem Sie die Eigenschaft oder das Objekt verworfen haben, können Sie zu einem Auswahl Container wechseln, der aktualisiert wurde, <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> und <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> Listen.

## <a name="change-selection-lists"></a>Auswahllisten ändern

 In diesem Abschnitt fügen Sie eine Auswahlliste für eine Basis Eigenschaften Klasse hinzu und verwenden die Tool Fenster Schnittstelle, um auszuwählen, welche Auswahlliste angezeigt werden soll.

### <a name="to-change-selection-lists"></a>So ändern Sie Auswahllisten

1. Öffnen Sie *MyToolWindow.cs* , und fügen Sie eine öffentliche Klasse namens hinzu `Simple` .

    ```csharp
    public class Simple
    {
        private string someText = "";

        [Category("My Properties")]
        [Description("Simple Properties")]
        [DisplayName("My Text")]
        public string SomeText
        {
            get { return someText; }
            set { someText = value; }
        }

        [Category("My Properties")]
        [Description("Read-only property")]
        public bool ReadOnly
        {
            get { return false; }
        }
    }
    ```

2. Fügen Sie `SimpleObject` der-Klasse eine Eigenschaft hinzu `MyToolWindow` , und fügen Sie zwei Methoden hinzu, um die Auswahl des **Eigenschaften** Fensters zwischen dem Fensterbereich und dem-Objekt zu ändern `Simple` .

    ```csharp
    private Simple simpleObject = null;
    public Simple SimpleObject
    {
        get
        {
            if (simpleObject == null) simpleObject = new Simple();
            return simpleObject;
        }
    }

    public void SelectSimpleList()
    {
        ArrayList listObjects = new ArrayList();
        listObjects.Add(SimpleObject);
        SelectList(listObjects);
    }

    public void SelectThisList()
    {
        ArrayList listObjects = new ArrayList();
        listObjects.Add(this);
        SelectList(listObjects);
    }
    ```

3. Ersetzen Sie in *MyToolWindowControl.cs* die Kontrollkästchen Handler durch die folgenden Codezeilen:

    ```csharp
    private void checkbox_Checked(object sender, RoutedEventArgs e)
     {
        pane.IsChecked = true;
        pane.SelectSimpleList();
        pane.UpdateSelection();
    }
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)
    {
        pane.IsChecked = false;
        pane.SelectThisList();
        pane.UpdateSelection();
    }
    ```

4. Erstellen Sie das Projekt, und starten Sie das Debugging.

5. Öffnen Sie in der experimentellen Instanz das Fenster **mytoolwindow** .

6. Aktivieren Sie das Kontrollkästchen im Fenster " **mytoolwindow** ". Im Fenster **Eigenschaften** werden die `Simple` Objekteigenschaften, **etwas Text** und schreibgeschützt angezeigt. Deaktivieren Sie das Kontrollkästchen. Die öffentlichen Eigenschaften des Fensters werden im Fenster **Eigenschaften** angezeigt.

    > [!NOTE]
    > Der Anzeige Name von **sometext** ist **mein Text**.

## <a name="best-practice"></a>Bewährte Methode

In dieser exemplarischen Vorgehensweise <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> wird implementiert, sodass die auswählbare Objekt Auflistung und die ausgewählte Objekt Auflistung dieselbe Auflistung sind. Nur das ausgewählte Objekt wird in der Eigenschaften Browser Liste angezeigt. Eine umfassendere ISelectionContainer-Implementierung finden Sie in den Beispielen für "Reference. ToolWindow".

Visual Studio-Tool Fenster bleiben zwischen Visual Studio-Sitzungen erhalten. Weitere Informationen zum Beibehalten des Tool Fenster Zustands finden Sie unter <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> .

## <a name="see-also"></a>Weitere Informationen

- [Erweitern von Eigenschaften und des Eigenschaften Fensters](../extensibility/extending-properties-and-the-property-window.md)
