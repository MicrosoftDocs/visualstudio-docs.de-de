---
title: Verwenden eines Shellbefehls mit einer Editor-Erweiterung
description: Erfahren Sie, wie Sie einer Textansicht im Editor ein Zusatzelement hinzufügen, indem Sie einen Menübefehl aufrufen. Aus einem VSPackage können Sie Features wie Menübefehle zum Editor hinzufügen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - add a menu command
ms.assetid: 08526848-a442-4cd4-afa1-b2eac2005adb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 38d855ebe34c54d06159ecd958a8b1d31ae0131f
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877818"
---
# <a name="walkthrough-use-a-shell-command-with-an-editor-extension"></a>Exemplarische Vorgehensweise: Verwenden eines Shellbefehls mit einer Editor-Erweiterung
Aus einem VSPackage können Sie Features wie Menübefehle zum Editor hinzufügen. In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie einer Textansicht im Editor ein Zusatzelement hinzugefügt wird, indem ein Menübefehl aufgerufen wird.

 In dieser exemplarischen Vorgehensweise wird die Verwendung eines VSPackages zusammen mit einem Managed Extensibility Framework Komponenten Teil (MEF) veranschaulicht. Sie müssen ein VSPackage verwenden, um den Menübefehl in der Visual Studio-Shell zu registrieren. Und Sie können den-Befehl verwenden, um auf den MEF-Komponenten Teil zuzugreifen.

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Es ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-menu-command"></a>Erstellen einer Erweiterung mit einem Menübefehl
 Erstellen Sie ein VSPackage, das einen Menübefehl mit dem Namen **Zusatzelement hinzufügen** **im Menü Extras** einfügt.

1. Erstellen Sie ein c#-VSIX-Projekt mit dem Namen `MenuCommandTest` , und fügen Sie einen benutzerdefinierten Befehls Element-Vorlagen Namen **addadornment** hinzu. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Eine Projekt Mappe mit dem Namen menucommandtest wird geöffnet. Die menucommandtestpackage-Datei enthält den Code, der den Menübefehl erstellt und ihn im **Menü Extras** einfügt. An diesem Punkt bewirkt der Befehl lediglich, dass ein Meldungs Feld angezeigt wird. In den nachfolgende Schritten wird gezeigt, wie Sie diesen Wert ändern, um das Kommentar Zusatzelement anzuzeigen.

3. Öffnen Sie im VSIX-Manifest-Editor die Datei " *Source. Extension. vsixmanifest* ". Die `Assets` Registerkarte muss über eine Zeile für ein Microsoft. VisualStudio. VSPackage mit dem Namen menucommandtest verfügen.

4. Speichern und schließen Sie die Datei " *Source. Extension. vsixmanifest* ".

## <a name="add-a-mef-extension-to-the-command-extension"></a>Fügen Sie der Befehls Erweiterung eine MEF-Erweiterung hinzu.

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf den Projektmappenknoten, klicken Sie auf **Hinzufügen** und dann auf **Neues Projekt**. Klicken Sie im Dialogfeld **Neues Projekt hinzufügen** unter **Visual c#** auf **Erweiterbarkeit** und dann auf **VSIX-Projekt**. Benennen Sie das Projekt mit `CommentAdornmentTest`.

2. Da dieses Projekt mit der Assembly mit starkem Namen VSPackage interagieren wird, müssen Sie die Assembly signieren. Sie können die Schlüsseldatei wieder verwenden, die bereits für die VSPackage-Assembly erstellt wurde.

    1. Öffnen Sie die Projekteigenschaften, und wählen Sie die Registerkarte **Signierung** .

    2. Wählen Sie **Assembly signieren** aus.

    3. Wählen Sie unter **Schlüsseldatei mit starkem Namen auswählen** die *Key. snk* -Datei aus, die für die menucommandtest-Assembly generiert wurde.

## <a name="refer-to-the-mef-extension-in-the-vspackage-project"></a>Weitere Informationen finden Sie in der MEF-Erweiterung im VSPackage-Projekt.
 Da Sie dem VSPackage eine MEF-Komponente hinzufügen, müssen Sie beide Arten von Assets im Manifest angeben.

> [!NOTE]
> Weitere Informationen zu MEF finden Sie unter [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-refer-to-the-mef-component-in-the-vspackage-project"></a>So verweisen Sie auf die MEF-Komponente im VSPackage-Projekt

1. Öffnen Sie im menucommandtest-Projekt im VSIX-Manifest-Editor die Datei " *Source. Extension. vsixmanifest* ".

2. Klicken Sie auf der Registerkarte **Objekte** auf **neu**.

3. Wählen Sie in der Liste **Typ** den Eintrag **Microsoft. VisualStudio. MEFComponent** aus.

4. Wählen Sie  in der Liste Quelle **ein Projekt in der aktuellen Projekt** Mappe aus.

5. Wählen Sie in der Liste **Projekt** die Option **commentadornmenttest** aus.

6. Speichern und schließen Sie die Datei " *Source. Extension. vsixmanifest* ".

7. Stellen Sie sicher, dass das menucommandtest-Projekt einen Verweis auf das commentadornmenttest-Projekt enthält.

8. Legen Sie im commentadornmenttest-Projekt fest, dass das Projekt eine Assembly erzeugt. Wählen Sie im **Projektmappen-Explorer** das Projekt aus, und suchen Sie im **Eigenschaften** Fenster nach der Eigenschaft **Build-Ausgabe in OutputDirectory kopieren** , und legen Sie Sie auf **true** fest.

## <a name="define-a-comment-adornment"></a>Definieren eines Kommentar Zusatz Elements
 Das Kommentar Zusatzelement selbst besteht aus einem, <xref:Microsoft.VisualStudio.Text.ITrackingSpan> das den ausgewählten Text nachverfolgt, und einigen Zeichen folgen, die den Autor und die Beschreibung des Texts darstellen.

#### <a name="to-define-a-comment-adornment"></a>So definieren Sie ein Kommentar Zusatzelement

1. Fügen Sie im commentadornmenttest-Projekt eine neue Klassendatei hinzu, und benennen Sie Sie `CommentAdornment` .

2. Fügen Sie die folgenden Verweise hinzu:

    1. Microsoft. VisualStudio. coreutility

    2. Microsoft. VisualStudio. Text. Data

    3. Microsoft. VisualStudio. Text. Logic

    4. Microsoft. VisualStudio. Text. UI

    5. Microsoft. VisualStudio. Text. UI. WPF

    6. System.ComponentModel.Composition

    7. PresentationCore

    8. PresentationFramework

    9. WindowsBase

3. Fügen Sie die folgende `using` Direktive hinzu.

    ```csharp
    using Microsoft.VisualStudio.Text;
    ```

4. Die Datei sollte eine Klasse mit dem Namen enthalten `CommentAdornment` .

    ```csharp
    internal class CommentAdornment
    ```

5. Fügen Sie der `CommentAdornment` -Klasse drei Felder für <xref:Microsoft.VisualStudio.Text.ITrackingSpan> , den Autor und die Beschreibung hinzu.

    ```csharp
    public readonly ITrackingSpan Span;
    public readonly string Author;
    public readonly string Text;
    ```

6. Fügen Sie einen Konstruktor hinzu, der die Felder initialisiert.

    ```csharp
    public CommentAdornment(SnapshotSpan span, string author, string text)
    {
        this.Span = span.Snapshot.CreateTrackingSpan(span, SpanTrackingMode.EdgeExclusive);
        this.Author = author;
        this.Text = text;
    }
    ```

## <a name="create-a-visual-element-for-the-adornment"></a>Erstellen eines visuellen Elements für das Zusatzelement
 Definieren Sie ein visuelles Element für das Zusatzelement. Definieren Sie für diese exemplarische Vorgehensweise ein Steuerelement, das von der Windows Presentation Foundation (WPF)-Klasse erbt <xref:System.Windows.Controls.Canvas> .

1. Erstellen Sie im commentadornmenttest-Projekt eine Klasse, und benennen Sie Sie `CommentBlock` .

2. Fügen Sie die folgenden `using` Direktiven hinzu.

    ```csharp
    using Microsoft.VisualStudio.Text;
    using System;
    using System.Windows;
    using System.Windows.Controls;
    using System.Windows.Media;
    using System.Windows.Shapes;
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Utilities;
    ```

3. Legen Sie die `CommentBlock` Klasse von ab <xref:System.Windows.Controls.Canvas> .

    ```csharp
    internal class CommentBlock : Canvas
    { }
    ```

4. Fügen Sie einige private Felder hinzu, um die visuellen Aspekte des Zusatz Elements zu definieren.

    ```csharp
    private Geometry textGeometry;
    private Grid commentGrid;
    private static Brush brush;
    private static Pen solidPen;
    private static Pen dashPen;
    ```

5. Fügen Sie einen Konstruktor hinzu, der das Kommentar Zusatzelement definiert, und fügen Sie den relevanten Text hinzu.

    ```csharp
    public CommentBlock(double textRightEdge, double viewRightEdge,
            Geometry newTextGeometry, string author, string body)
    {
        if (brush == null)
        {
            brush = new SolidColorBrush(Color.FromArgb(0x20, 0x00, 0xff, 0x00));
            brush.Freeze();
            Brush penBrush = new SolidColorBrush(Colors.Green);
            penBrush.Freeze();
            solidPen = new Pen(penBrush, 0.5);
            solidPen.Freeze();
            dashPen = new Pen(penBrush, 0.5);
            dashPen.DashStyle = DashStyles.Dash;
            dashPen.Freeze();
        }

        this.textGeometry = newTextGeometry;

        TextBlock tb1 = new TextBlock();
        tb1.Text = author;
        TextBlock tb2 = new TextBlock();
        tb2.Text = body;

        const int MarginWidth = 8;
        this.commentGrid = new Grid();
        this.commentGrid.RowDefinitions.Add(new RowDefinition());
        this.commentGrid.RowDefinitions.Add(new RowDefinition());
        ColumnDefinition cEdge = new ColumnDefinition();
        cEdge.Width = new GridLength(MarginWidth);
        ColumnDefinition cEdge2 = new ColumnDefinition();
        cEdge2.Width = new GridLength(MarginWidth);
        this.commentGrid.ColumnDefinitions.Add(cEdge);
        this.commentGrid.ColumnDefinitions.Add(new ColumnDefinition());
        this.commentGrid.ColumnDefinitions.Add(cEdge2);

        System.Windows.Shapes.Rectangle rect = new System.Windows.Shapes.Rectangle();
        rect.RadiusX = 6;
        rect.RadiusY = 3;
        rect.Fill = brush;
        rect.Stroke = Brushes.Green;

            Size inf = new Size(double.PositiveInfinity, double.PositiveInfinity);
            tb1.Measure(inf);
            tb2.Measure(inf);
            double middleWidth = Math.Max(tb1.DesiredSize.Width, tb2.DesiredSize.Width);
            this.commentGrid.Width = middleWidth + 2 * MarginWidth;

        Grid.SetColumn(rect, 0);
        Grid.SetRow(rect, 0);
        Grid.SetRowSpan(rect, 2);
        Grid.SetColumnSpan(rect, 3);
        Grid.SetRow(tb1, 0);
        Grid.SetColumn(tb1, 1);
        Grid.SetRow(tb2, 1);
        Grid.SetColumn(tb2, 1);
        this.commentGrid.Children.Add(rect);
        this.commentGrid.Children.Add(tb1);
        this.commentGrid.Children.Add(tb2);

        Canvas.SetLeft(this.commentGrid, Math.Max(viewRightEdge - this.commentGrid.Width - 20.0, textRightEdge + 20.0));
        Canvas.SetTop(this.commentGrid, textGeometry.GetRenderBounds(solidPen).Top);

        this.Children.Add(this.commentGrid);
    }
    ```

6. Implementieren Sie außerdem einen <xref:System.Windows.Controls.Panel.OnRender%2A> Ereignishandler, der das Zusatzelement zeichnet.

    ```csharp
    protected override void OnRender(DrawingContext dc)
    {
        base.OnRender(dc);
        if (this.textGeometry != null)
        {
            dc.DrawGeometry(brush, solidPen, this.textGeometry);
            Rect textBounds = this.textGeometry.GetRenderBounds(solidPen);
            Point p1 = new Point(textBounds.Right, textBounds.Bottom);
            Point p2 = new Point(Math.Max(Canvas.GetLeft(this.commentGrid) - 20.0, p1.X), p1.Y);
            Point p3 = new Point(Math.Max(Canvas.GetLeft(this.commentGrid), p1.X), (Canvas.GetTop(this.commentGrid) + p1.Y) * 0.5);
            dc.DrawLine(dashPen, p1, p2);
            dc.DrawLine(dashPen, p2, p3);
        }
    }
    ```

## <a name="add-an-iwpftextviewcreationlistener"></a>Hinzufügen eines iwpftextviewkreationlistener
 Der <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> ist ein MEF-Komponenten Teil, den Sie verwenden können, um auf Ansichts Erstellungs Ereignisse zu lauschen.

1. Fügen Sie dem commentadornmenttest-Projekt eine Klassendatei hinzu, und benennen Sie Sie `Connector` .

2. Fügen Sie die folgenden `using` Direktiven hinzu.

    ```csharp
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Utilities;
    ```

3. Deklarieren Sie eine Klasse <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> , die implementiert, und exportieren Sie Sie mit <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text" und einem <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> von <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> . Das Inhaltstyp Attribut gibt die Art des Inhalts an, auf den die Komponente angewendet wird. Der Texttyp ist der Basistyp für alle nicht binären Dateitypen. Daher ist fast jede Textansicht, die erstellt wird, von diesem Typ. Das Attribut "Text Ansichts Rolle" gibt die Art der Textansicht an, auf die die Komponente angewendet wird. In Dokument Text Ansichts Rollen wird normalerweise Text angezeigt, der aus Zeilen besteht und in einer Datei gespeichert ist.

     [!code-vb[VSSDKMenuCommandTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_1.vb)]
     [!code-csharp[VSSDKMenuCommandTest#11](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_1.cs)]

4. Implementieren Sie die- <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> Methode, sodass Sie das statische- `Create()` Ereignis von aufruft `CommentAdornmentManager` .

    ```csharp
    public void TextViewCreated(IWpfTextView textView)
    {
        CommentAdornmentManager.Create(textView);
    }
    ```

5. Fügen Sie eine Methode hinzu, mit der Sie den Befehl ausführen können.

    ```csharp
    static public void Execute(IWpfTextViewHost host)
    {
        IWpfTextView view = host.TextView;
        //Add a comment on the selected text. 
        if (!view.Selection.IsEmpty)
        {
            //Get the provider for the comment adornments in the property bag of the view.
            CommentAdornmentProvider provider = view.Properties.GetProperty<CommentAdornmentProvider>(typeof(CommentAdornmentProvider));

            //Add some arbitrary author and comment text. 
            string author = System.Security.Principal.WindowsIdentity.GetCurrent().Name;
            string comment = "Four score....";

            //Add the comment adornment using the provider.
            provider.Add(view.Selection.SelectedSpans[0], author, comment);
        }
    }
    ```

## <a name="define-an-adornment-layer"></a>Definieren einer Zusatzelement-Ebene
 Um ein neues Zusatzelement hinzuzufügen, müssen Sie eine Zusatzelement-Ebene definieren.

### <a name="to-define-an-adornment-layer"></a>So definieren Sie eine Zusatzelement-Ebene

1. `Connector`Deklarieren Sie in der-Klasse ein öffentliches Feld vom Typ <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition> , und exportieren Sie es mit einem, <xref:Microsoft.VisualStudio.Utilities.NameAttribute> das einen eindeutigen Namen für die Zusatzelement-Schicht und einen angibt, <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> der die Z-Reihenfolge Beziehung dieser Zusatzelement-Schicht zu anderen Text Ansichts Schichten (Text, Caretzeichen und Auswahl) definiert.

    ```csharp
    [Export(typeof(AdornmentLayerDefinition))]
    [Name("CommentAdornmentLayer")]
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
    public AdornmentLayerDefinition commentLayerDefinition;

    ```

## <a name="provide-comment-adornments"></a>Bereitstellen von Kommentar Zusatzelementen
 Wenn Sie ein Zusatzelement definieren, implementieren Sie auch einen Kommentar Zusatz Anbieter und einen Kommentar Zusatz-Manager. Der Kommentar Zusatzelement-Anbieter speichert eine Liste von Kommentar Zusatzelementen, lauscht auf <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> Ereignisse auf dem zugrunde liegenden Text Puffer und löscht Kommentar Zusatzelemente, wenn der zugrunde liegende Text gelöscht wird.

1. Fügen Sie dem commentadornmenttest-Projekt eine neue Klassendatei hinzu, und benennen Sie Sie `CommentAdornmentProvider` .

2. Fügen Sie die folgenden `using` Direktiven hinzu.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Collections.ObjectModel;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Editor;
    ```

3. Fügen Sie eine Klasse namens `CommentAdornmentProvider`hinzu.

    ```csharp
    internal class CommentAdornmentProvider
    {
    }
    ```

4. Fügen Sie private Felder für den Text Puffer und die Liste der Kommentar Zusatzelemente hinzu, die mit dem Puffer verknüpft sind.

    ```csharp
    private ITextBuffer buffer;
    private IList<CommentAdornment> comments = new List<CommentAdornment>();

    ```

5. Fügen Sie einen Konstruktor für hinzu `CommentAdornmentProvider` . Dieser Konstruktor sollte privaten Zugriff haben, da der Anbieter von der-Methode instanziiert wird `Create()` . Der-Konstruktor fügt dem- `OnBufferChanged` Ereignis den Ereignishandler hinzu <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> .

    ```csharp
    private CommentAdornmentProvider(ITextBuffer buffer)
    {
        this.buffer = buffer;
        //listen to the Changed event so we can react to deletions. 
        this.buffer.Changed += OnBufferChanged;
    }

    ```

6. Fügen Sie die `Create()`-Methode hinzu.

    ```csharp
    public static CommentAdornmentProvider Create(IWpfTextView view)
    {
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentProvider>(delegate { return new CommentAdornmentProvider(view.TextBuffer); });
    }

    ```

7. Fügen Sie die `Detach()`-Methode hinzu.

    ```csharp
    public void Detach()
    {
        if (this.buffer != null)
        {
            //remove the Changed listener 
            this.buffer.Changed -= OnBufferChanged;
            this.buffer = null;
        }
    }
    ```

8. Fügen Sie den `OnBufferChanged` Ereignishandler hinzu.

     [!code-csharp[VSSDKMenuCommandTest#21](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_2.cs)]
     [!code-vb[VSSDKMenuCommandTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_2.vb)]

9. Fügen Sie eine Deklaration für ein- `CommentsChanged` Ereignis hinzu.

    ```csharp
    public event EventHandler<CommentsChangedEventArgs> CommentsChanged;
    ```

10. Erstellen Sie eine- `Add()` Methode, um das Zusatzelement hinzuzufügen.

    ```csharp
    public void Add(SnapshotSpan span, string author, string text)
    {
        if (span.Length == 0)
            throw new ArgumentOutOfRangeException("span");
        if (author == null)
            throw new ArgumentNullException("author");
        if (text == null)
            throw new ArgumentNullException("text");

        //Create a comment adornment given the span, author and text.
        CommentAdornment comment = new CommentAdornment(span, author, text);

        //Add it to the list of comments. 
        this.comments.Add(comment);

        //Raise the changed event.
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;
        if (commentsChanged != null)
            commentsChanged(this, new CommentsChangedEventArgs(comment, null));
    }

    ```

11. Fügen Sie eine- `RemoveComments()` Methode hinzu.

    ```csharp
    public void RemoveComments(SnapshotSpan span)
    {
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;

        //Get a list of all the comments that are being kept
        IList<CommentAdornment> keptComments = new List<CommentAdornment>(this.comments.Count);

        foreach (CommentAdornment comment in this.comments)
        {
            //find out if the given span overlaps with the comment text span. If two spans are adjacent, they do not overlap. To consider adjacent spans, use IntersectsWith. 
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))
            {
                //Raise the change event to delete this comment. 
                if (commentsChanged != null)
                    commentsChanged(this, new CommentsChangedEventArgs(null, comment));
            }
            else
                keptComments.Add(comment);
        }

        this.comments = keptComments;
    }
    ```

12. Fügen Sie eine `GetComments()` Methode hinzu, die alle Kommentare in einer bestimmten Momentaufnahme Spanne zurückgibt.

    ```csharp
    public Collection<CommentAdornment> GetComments(SnapshotSpan span)
    {
        IList<CommentAdornment> overlappingComments = new List<CommentAdornment>();
        foreach (CommentAdornment comment in this.comments)
        {
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))
                overlappingComments.Add(comment);
        }

        return new Collection<CommentAdornment>(overlappingComments);
    }
    ```

13. Fügen Sie wie folgt eine Klasse mit dem Namen hinzu `CommentsChangedEventArgs` .

    ```csharp
    internal class CommentsChangedEventArgs : EventArgs
    {
        public readonly CommentAdornment CommentAdded;

        public readonly CommentAdornment CommentRemoved;

        public CommentsChangedEventArgs(CommentAdornment added, CommentAdornment removed)
        {
            this.CommentAdded = added;
            this.CommentRemoved = removed;
        }
    }
    ```

## <a name="manage-comment-adornments"></a>Kommentar Zusatzelemente verwalten
 Der Kommentar Zusatz-Manager erstellt das Zusatzelement und fügt es der Zusatzelement-Ebene hinzu. Er lauscht auf das <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> -Ereignis und das- <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> Ereignis, sodass das Zusatzelement verschoben oder gelöscht werden kann. Außerdem lauscht das Ereignis auf das `CommentsChanged` Ereignis, das vom Kommentar Zusatz Anbieter ausgelöst wird, wenn Kommentare hinzugefügt oder entfernt werden.

1. Fügen Sie dem commentadornmenttest-Projekt eine Klassendatei hinzu, und benennen Sie Sie `CommentAdornmentManager` .

2. Fügen Sie die folgenden `using` Direktiven hinzu.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Windows.Media;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Text.Formatting;
    ```

3. Fügen Sie eine Klasse namens `CommentAdornmentManager`hinzu.

    ```csharp
    internal class CommentAdornmentManager
        {
        }
    ```

4. Fügen Sie einige private Felder hinzu.

    ```csharp
    private readonly IWpfTextView view;
    private readonly IAdornmentLayer layer;
    private readonly CommentAdornmentProvider provider;
    ```

5. Fügen Sie einen Konstruktor hinzu, der den Manager für das <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> -Ereignis und das-Ereignis abonniert <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> , und auch für das- `CommentsChanged` Ereignis. Der Konstruktor ist privat, da der Manager von der statischen-Methode instanziiert wird `Create()` .

    ```csharp
    private CommentAdornmentManager(IWpfTextView view)
    {
        this.view = view;
        this.view.LayoutChanged += OnLayoutChanged;
        this.view.Closed += OnClosed;

        this.layer = view.GetAdornmentLayer("CommentAdornmentLayer");

        this.provider = CommentAdornmentProvider.Create(view);
        this.provider.CommentsChanged += OnCommentsChanged;
    }
    ```

6. Fügen Sie die `Create()` Methode hinzu, die einen Anbieter abruft, oder erstellen Sie bei Bedarf eine.

    ```csharp
    public static CommentAdornmentManager Create(IWpfTextView view)
    {
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentManager>(delegate { return new CommentAdornmentManager(view); });
    }
    ```

7. Fügen Sie den- `CommentsChanged` Handler hinzu.

    ```csharp
    private void OnCommentsChanged(object sender, CommentsChangedEventArgs e)
    {
        //Remove the comment (when the adornment was added, the comment adornment was used as the tag). 
        if (e.CommentRemoved != null)
            this.layer.RemoveAdornmentsByTag(e.CommentRemoved);

        //Draw the newly added comment (this will appear immediately: the view does not need to do a layout). 
        if (e.CommentAdded != null)
            this.DrawComment(e.CommentAdded);
    }
    ```

8. Fügen Sie den- <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> Handler hinzu.

    ```csharp
    private void OnClosed(object sender, EventArgs e)
    {
        this.provider.Detach();
        this.view.LayoutChanged -= OnLayoutChanged;
        this.view.Closed -= OnClosed;
    }
    ```

9. Fügen Sie den- <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> Handler hinzu.

    ```csharp
    private void OnLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)
    {
        //Get all of the comments that intersect any of the new or reformatted lines of text.
        List<CommentAdornment> newComments = new List<CommentAdornment>();

        //The event args contain a list of modified lines and a NormalizedSpanCollection of the spans of the modified lines.  
        //Use the latter to find the comments that intersect the new or reformatted lines of text. 
        foreach (Span span in e.NewOrReformattedSpans)
        {
            newComments.AddRange(this.provider.GetComments(new SnapshotSpan(this.view.TextSnapshot, span)));
        }

        //It is possible to get duplicates in this list if a comment spanned 3 lines, and the first and last lines were modified but the middle line was not. 
        //Sort the list and skip duplicates.
        newComments.Sort(delegate(CommentAdornment a, CommentAdornment b) { return a.GetHashCode().CompareTo(b.GetHashCode()); });

        CommentAdornment lastComment = null;
        foreach (CommentAdornment comment in newComments)
        {
            if (comment != lastComment)
            {
                lastComment = comment;
                this.DrawComment(comment);
            }
        }
    }
    ```

10. Fügen Sie die private Methode hinzu, die den Kommentar zeichnet.

     [!code-csharp[VSSDKMenuCommandTest#35](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_3.cs)]
     [!code-vb[VSSDKMenuCommandTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_3.vb)]

## <a name="use-the-menu-command-to-add-the-comment-adornment"></a>Verwenden Sie den Menübefehl, um das Kommentar Zusatzelement hinzuzufügen.
 Sie können den Menübefehl verwenden, um ein Kommentar Zusatzelement zu erstellen, indem Sie die- `MenuItemCallback` Methode des VSPackage implementieren.

1. Fügen Sie dem menucommandtest-Projekt die folgenden Verweise hinzu:

    - Microsoft. VisualStudio. Text Manager. Interop

    - Microsoft. VisualStudio. Editor

    - Microsoft. VisualStudio. Text. UI. WPF

2. Öffnen Sie die Datei *AddAdornment.cs* , und fügen Sie die folgenden `using` Direktiven hinzu.

    ```csharp
    using Microsoft.VisualStudio.TextManager.Interop;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Editor;
    using CommentAdornmentTest;
    ```

3. Löschen `Execute()` Sie die-Methode, und fügen Sie den folgenden Befehls Handler hinzu.

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
    }
    ```

4. Fügen Sie Code hinzu, um die aktive Ansicht zu erhalten. Sie müssen das `SVsTextManager` der Visual Studio-Shell erhalten, um das aktive zu erhalten `IVsTextView` .

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
        IVsTextManager txtMgr = (IVsTextManager) await ServiceProvider.GetServiceAsync(typeof(SVsTextManager));
        IVsTextView vTextView = null;
        int mustHaveFocus = 1;
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);
    }
    ```

5. Handelt es sich bei dieser Textansicht um eine Instanz einer Editor-Textansicht, können Sie Sie in die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> Schnittstelle umwandeln und dann die und deren zugeordnete erhalten <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> . Verwenden <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> Sie, um die-Methode aufzurufen `Connector.Execute()` , die den Kommentar Zusatz Anbieter abruft und das Zusatzelement hinzufügt. Der Befehls Handler sollte nun wie der folgende Code aussehen:

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
        IVsTextManager txtMgr = (IVsTextManager) await ServiceProvider.GetServiceAsync(typeof(SVsTextManager));
        IVsTextView vTextView = null;
        int mustHaveFocus = 1;
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);
        IVsUserData userData = vTextView as IVsUserData;
         if (userData == null)
        {
            Console.WriteLine("No text view is currently open");
            return;
        }
        IWpfTextViewHost viewHost;
        object holder;
        Guid guidViewHost = DefGuidList.guidIWpfTextViewHost;
        userData.GetData(ref guidViewHost, out holder);
        viewHost = (IWpfTextViewHost)holder;
        Connector.Execute(viewHost);
    }
    ```

6. Legen Sie die addadornmenthandler-Methode als Handler für den addadornment-Befehl im addadornment-Konstruktor fest.

    ```csharp
    private AddAdornment(AsyncPackage package, OleMenuCommandService commandService)
    {
        this.package = package ?? throw new ArgumentNullException(nameof(package));
        commandService = commandService ?? throw new ArgumentNullException(nameof(commandService));

        var menuCommandID = new CommandID(CommandSet, CommandId);
        var menuItem = new MenuCommand(this.AddAdornmentHandler, menuCommandID);
        commandService.AddCommand(menuItem);
    }
    ```

## <a name="build-and-test-the-code"></a>Erstellen und Testen des Codes

1. Erstellen Sie die Projektmappe, und beginnen Sie mit dem Debuggen. Die experimentelle Instanz sollte angezeigt werden.

2. Erstellen einer Textdatei Geben Sie Text ein, und wählen Sie ihn aus.

3. Klicken Sie **im Menü Extras** auf die Option **Zusatzelement hinzufügen**. Eine Sprechblase sollte auf der rechten Seite des Text Fensters angezeigt werden und sollte Text enthalten, der dem folgenden Text ähnelt.

     IhrBenutzername

     Vierscore...

## <a name="see-also"></a>Weitere Informationen
- [Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
