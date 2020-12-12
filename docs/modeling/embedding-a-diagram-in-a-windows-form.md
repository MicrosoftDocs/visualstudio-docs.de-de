---
title: Einbetten eines Diagramms in Windows Form
description: Erfahren Sie, wie Sie ein DSL-Diagramm in ein Windows-Steuerelement einbetten können, das im Visual Studio-Fenster angezeigt wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4338bfa824b511ee0be40516e1396a75901188a1
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361702"
---
# <a name="embed-a-diagram-in-a-windows-form"></a>Einbetten eines Diagramms in Windows Form

Sie können ein DSL-Diagramm in ein Windows-Steuerelement einbetten, das im Visual Studio-Fenster angezeigt wird.

## <a name="embed-a-dsl-diagram-in-a-windows-control"></a>Einbinden eines DSL-Diagramms in ein Windows-Steuerelement

1. Fügen Sie dem dslpackage-Projekt eine neue **Benutzer Steuer** Element Datei hinzu.

2. Fügen Sie dem Benutzer Steuerelement ein Panel-Steuerelement hinzu. Dieser Bereich enthält das DSL-Diagramm.

     Fügen Sie weitere Steuerelemente hinzu, die Sie benötigen.

     Legen Sie die Anker Eigenschaften der Steuerelemente fest.

3. Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf die Benutzer Steuerelement Datei, und klicken Sie auf **Code anzeigen**. Fügen Sie den folgenden Konstruktor und die Variable dem Code hinzu:

    ```csharp
    internal UserControl1(MyDSLDocView docView, Control content)
      : this()
    {
      panel1.Controls.Add(content);
      this.docView = docView;
    }
    private MyDSLDocView docView;
    ```

4. Fügen Sie dem dslpackage-Projekt eine neue Datei mit folgendem Inhalt hinzu:

    ```csharp
    using System.Windows.Forms;
    namespace Company.MyDSL
    {
      partial class MyDSLDocView
      {
        private UserControl1 container;
        public override IWin32Window Window
        {
          get
          {
            if (container == null)
            {
              // Put our own form inside the DSL window:
              container = new UserControl1(this,
                (Control)base.Window);
            }
            return container;
    } } } }
    ```

5. Um die DSL zu testen, drücken Sie **F5** , und öffnen Sie eine Beispielmodell Datei. Das Diagramm wird im-Steuerelement angezeigt. Die Toolbox und andere Features funktionieren normal.

## <a name="update-the-form-using-store-events"></a>Aktualisieren des Formulars mithilfe von Store-Ereignissen

1. Fügen Sie im Formular-Designer ein **Listenfeld** mit dem Namen hinzu `listBox1` . Dadurch wird eine Liste der Elemente im Modell angezeigt. Sie wird mit dem Modell mithilfe von *Store-Ereignissen* synchronisiert. Weitere Informationen finden Sie unter [Ereignishandler verbreiten Änderungen außerhalb des Modells](../modeling/event-handlers-propagate-changes-outside-the-model.md).

2. Überschreiben Sie in der benutzerdefinierten Codedatei weitere Methoden für die DocView-Klasse:

    ```csharp
    partial class MyDSLDocView
    {
     /// <summary>
     /// Register store event listeners.
     /// This method is called when the model and diagram
     /// have completed loading.
     /// </summary>
     protected override bool LoadView()
      {
        bool result = base.LoadView();
        Store store = this.DocData.Store;
        EventManagerDirectory emd = store.EventManagerDirectory;
        DomainClassInfo componentClass = store.DomainDataDirectory.FindDomainClass(typeof(ExampleElement));
        emd.ElementAdded.Add(componentClass, new EventHandler<ElementAddedEventArgs>(AddElement));
        emd.ElementDeleted.Add(componentClass, new EventHandler<ElementDeletedEventArgs>(RemoveElement));

        // Do the initial parts list:
        container.SetUpFormFromModel();
        return result;
      }
     /// <summary>
     /// Listener method called on creation of each instance of
     /// the ExampleElement class or its subclasses.
     /// </summary>
     private void AddElement(object sender, ElementAddedEventArgs e)
     {
       container.Add(e.ModelElement as ExampleElement);
     }
     /// <summary>
     /// Listener method called after deletion of each instance of
     /// the ExampleElement class or its subclasses.
     /// </summary>
     private void RemoveElement(object sender, ElementDeletedEventArgs e)
     {
       container.Remove(e.ModelElement as ExampleElement);
     }
    ```

3. Fügen Sie im Code hinter dem Benutzer Steuerelement Methoden zum lauschen auf Elemente hinzu, die hinzugefügt und entfernt wurden:

    ```csharp
    public partial class UserControl1 : UserControl { ...

    private ExampleModel modelRoot;

    internal void Add(ExampleElement e) { UpdatePartsList(); }
    internal void Remove(ExampleElement e) { UpdatePartsList(); }

    internal void SetUpFormFromModel()
    {
      modelRoot = this.docView.CurrentDiagram.ModelElement as ExampleModel;
      UpdatePartsList();
    }

    private void UpdatePartsList()
    {
      StringBuilder builder = new StringBuilder();
      listBox1.Items.Clear();
      foreach (ExampleElement c in modelRoot.Elements)
      {
        listBox1.Items.Add(c.Name);
      }
    }
    ```

4. Um die DSL zu testen, drücken Sie **F5** , und öffnen Sie in der experimentellen Instanz von Visual Studio eine Beispielmodell Datei.

     Beachten Sie, dass im Listenfeld eine Liste der Elemente im Modell angezeigt wird und dass Sie nach dem Hinzufügen oder löschen und nach dem Rückgängigmachen und wiederholen korrekt ist.

## <a name="see-also"></a>Siehe auch

- [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Schreiben von Code zum Anpassen einer domänenspezifischen Sprache](../modeling/writing-code-to-customise-a-domain-specific-language.md)
