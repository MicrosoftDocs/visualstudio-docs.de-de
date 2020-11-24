---
title: Hinzufügen der Suche zu einem Tool Fenster | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie einem Tool Fenster in Visual Studio Suchfunktionen hinzufügen, einschließlich ein Suchfeld, eine Filterung und eine Statusanzeige.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d117ab18022285e5cd52f18a1de01adeafbc5df3
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/24/2020
ms.locfileid: "95597638"
---
# <a name="add-search-to-a-tool-window"></a>Hinzufügen der Suche zu einem Tool Fenster
Wenn Sie ein Tool Fenster in ihrer Erweiterung erstellen oder aktualisieren, können Sie dieselbe Suchfunktion hinzufügen, die an anderer Stelle in Visual Studio angezeigt wird. Diese Funktion umfasst die folgenden Features:

- Ein Suchfeld, das sich immer in einem benutzerdefinierten Bereich der Symbolleiste befindet.

- Eine Statusanzeige, die im Suchfeld selbst überlagert wird.

- Die Möglichkeit, Ergebnisse anzuzeigen, sobald Sie die einzelnen Zeichen eingeben (sofortige Suche) oder erst nach Auswahl der **Eingabe** Taste (nach Bedarf suchen).

- Eine Liste, die die Begriffe anzeigt, nach denen Sie zuletzt gesucht haben.

- Die Möglichkeit zum Filtern von Such Vorgängen nach bestimmten Feldern oder Aspekten der Such Ziele.

In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie die folgenden Aufgaben ausführen:

1. Erstellen Sie ein VSPackage-Projekt.

2. Erstellen Sie ein Tool Fenster, das ein UserControl-Steuerelement mit einem schreibgeschützten Textfeld enthält.

3. Fügen Sie dem Tool Fenster ein Suchfeld hinzu.

4. Fügen Sie die Such Implementierung hinzu.

5. Aktivieren Sie die sofortige Suche und die Anzeige einer Statusanzeige.

6. Fügen Sie eine Übereinstimmungs **Fall** Option hinzu.

7. Fügen Sie einen Filter zum reinen **Suchen von Zeilen** hinzu.

## <a name="to-create-a-vsix-project"></a>So erstellen Sie ein VSIX-Projekt

1. Erstellen Sie ein VSIX-Projekt `TestToolWindowSearch` mit dem Namen und einem Tool Fenster mit dem Namen **testsearch**. Wenn Sie Hilfe benötigen, finden Sie weitere Informationen unter [Erstellen einer Erweiterung mit einem Tool Fenster](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="to-create-a-tool-window"></a>So erstellen Sie ein Tool Fenster

1. Öffnen Sie im `TestToolWindowSearch` Projekt die Datei " *testsearchcontrol. XAML* ".

2. Ersetzen Sie den vorhandenen- `<StackPanel>` Block durch den folgenden-Block, der <xref:System.Windows.Controls.TextBox> der <xref:System.Windows.Controls.UserControl> im Tool Fenster einen schreibgeschützten hinzufügt.

    ```xaml
    <StackPanel Orientation="Vertical">
        <TextBox Name="resultsTextBox" Height="800.0"
            Width="800.0"
            IsReadOnly="True">
        </TextBox>
    </StackPanel>
    ```

3. Fügen Sie in der Datei *TestSearchControl.XAML.cs* die folgende using-Direktive hinzu:

    ```csharp
    using System.Text;
    ```

4. Entfernen Sie die- `button1_Click()` Methode.

     Fügen Sie in der **testsearchcontrol** -Klasse den folgenden Code hinzu.

     Dieser Code fügt eine öffentliche <xref:System.Windows.Controls.TextBox> Eigenschaft mit dem Namen **searchresultstextbox** und eine öffentliche Zeichen folgen Eigenschaft mit dem Namen **searchcontent** hinzu. Im Konstruktor ist searchresultstextbox auf das Textfeld festgelegt, und searchcontent wird mit einem durch Trennzeichen getrennten Satz von Zeichen folgen initialisiert. Der Inhalt des Textfelds wird auch mit dem Satz von Zeichen folgen initialisiert.

     [!code-csharp[ToolWindowSearch#1](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs)]
     [!code-vb[ToolWindowSearch#1](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]

5. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz von Visual Studio wird angezeigt.

6. Wählen Sie in der Menüleiste **View** die Option  >  **andere Windows**-  >  **Testsuche** anzeigen aus.

     Das Tool Fenster wird angezeigt, aber das Such Steuerelement wird noch nicht angezeigt.

## <a name="to-add-a-search-box-to-the-tool-window"></a>So fügen Sie dem Tool Fenster ein Suchfeld hinzu

1. Fügen Sie der-Klasse in der Datei *TestSearch.cs* den folgenden Code hinzu `TestSearch` . Der Code überschreibt die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> Eigenschaft, sodass der Get-Accessor zurückgibt `true` .

     Um die Suche zu aktivieren, müssen Sie die-Eigenschaft überschreiben <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> . Die <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> -Klasse implementiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> und stellt eine Standard Implementierung bereit, die die Suche nicht ermöglicht.

    ```csharp
    public override bool SearchEnabled
    {
        get { return true; }
    }
    ```

2. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz wird geöffnet.

3. Öffnen Sie **testsearch** in der experimentellen Instanz von Visual Studio.

     Am oberen Rand des Tool Fensters wird ein Such Steuerelement mit einem **Such** Wasserzeichen und einem Lupensymbol angezeigt. Die Suche funktioniert jedoch noch nicht, da der Suchprozess nicht implementiert wurde.

## <a name="to-add-the-search-implementation"></a>So fügen Sie die Such Implementierung hinzu
 Wenn Sie die Suche in einer aktivieren <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> , wie im vorherigen Verfahren, erstellt das Tool Fenster einen suchhost. Dieser Host richtet Suchprozesse ein und verwaltet diese, die immer in einem Hintergrund Thread auftreten. Da die <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> -Klasse die Erstellung des suchhosts und die Einrichtung der Suche verwaltet, müssen Sie nur eine Suchaufgabe erstellen und die Search-Methode bereitstellen. Der Suchvorgang erfolgt in einem Hintergrund Thread, und Aufrufe des Tool Fenster-Steuer Elements treten im UI-Thread auf. Daher müssen Sie die Methode [threadhelper. aufrufen *](https://msdn.microsoft.com/data/ee197798(v=vs.85)) verwenden, um alle Aufrufe zu verwalten, die Sie im Umgang mit dem Steuerelement vornehmen.

1. Fügen Sie in der Datei *TestSearch.cs* die folgenden- `using` Anweisungen hinzu:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Runtime.InteropServices;
    using System.Text;
    using System.Windows.Controls;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.PlatformUI;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

2. Fügen Sie in der- `TestSearch` Klasse den folgenden Code hinzu, der die folgenden Aktionen ausführt:

    - Überschreibt die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> Methode, um eine Suchaufgabe zu erstellen.

    - Überschreibt die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> Methode, um den Zustand des Textfelds wiederherzustellen. Diese Methode wird aufgerufen, wenn ein Benutzer eine Suchaufgabe abbricht und wenn ein Benutzeroptionen oder Filter festlegt bzw. aufhebt. <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A>Und <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> werden im UI-Thread aufgerufen. Daher müssen Sie nicht über die [threadhelper. aufrufen *](https://msdn.microsoft.com/data/ee197798(v=vs.85)) -Methode auf das Textfeld zugreifen.

    - Erstellt eine Klasse mit dem Namen, die `TestSearchTask` von erbt <xref:Microsoft.VisualStudio.Shell.VsSearchTask> und eine Standard Implementierung von bereitstellt <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask> .

         In `TestSearchTask` legt der Konstruktor ein privates Feld fest, das auf das Tool Fenster verweist. Um die Suchmethode bereitzustellen, überschreiben Sie die <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> -Methode und die-Methode <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A> . Bei der- <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> Methode wird der Suchprozess implementiert. Dieser Prozess umfasst das Ausführen der Suche, das Anzeigen der Suchergebnisse im Textfeld und das Aufrufen der Basisklassen Implementierung dieser Methode, um zu melden, dass die Suche vollständig ist.

    ```csharp
    public override IVsSearchTask CreateSearch(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback)
    {
        if (pSearchQuery == null || pSearchCallback == null)
            return null;
         return new TestSearchTask(dwCookie, pSearchQuery, pSearchCallback, this);
    }

    public override void ClearSearch()
    {
        TestSearchControl control = (TestSearchControl)this.Content;
        control.SearchResultsTextBox.Text = control.SearchContent;
    }

    internal class TestSearchTask : VsSearchTask
    {
        private TestSearch m_toolWindow;

        public TestSearchTask(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback, TestSearch toolwindow)
            : base(dwCookie, pSearchQuery, pSearchCallback)
        {
            m_toolWindow = toolwindow;
        }

        protected override void OnStartSearch()
        {
            // Use the original content of the text box as the target of the search.
            var separator = new string[] { Environment.NewLine };
            TestSearchControl control = (TestSearchControl)m_toolWindow.Content;
            string[] contentArr = control.SearchContent.Split(separator, StringSplitOptions.None);

            // Get the search option.
            bool matchCase = false;
            // matchCase = m_toolWindow.MatchCaseOption.Value;

                // Set variables that are used in the finally block.
                StringBuilder sb = new StringBuilder("");
                uint resultCount = 0;
                this.ErrorCode = VSConstants.S_OK;

                try
                {
                    string searchString = this.SearchQuery.SearchString;

                    // Determine the results.
                    uint progress = 0;
                    foreach (string line in contentArr)
                    {
                        if (matchCase == true)
                        {
                            if (line.Contains(searchString))
                            {
                                sb.AppendLine(line);
                                resultCount++;
                            }
                        }
                        else
                            {
                                if (line.ToLower().Contains(searchString.ToLower()))
                                {
                                    sb.AppendLine(line);
                                    resultCount++;
                                }
                            }

                            // SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));

                            // Uncomment the following line to demonstrate the progress bar.
                            // System.Threading.Thread.Sleep(100);
                        }
                    }
                    catch (Exception e)
                    {
                        this.ErrorCode = VSConstants.E_FAIL;
                    }
                    finally
                    {
                        ThreadHelper.Generic.Invoke(() =>
                        { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });

                        this.SearchResults = resultCount;
                    }

            // Call the implementation of this method in the base class.
            // This sets the task status to complete and reports task completion.
            base.OnStartSearch();
        }

        protected override void OnStopSearch()
        {
            this.SearchResults = 0;
        }
    }
    ```

3. Testen Sie Ihre Such Implementierung, indem Sie die folgenden Schritte ausführen:

    1. Erstellen Sie das Projekt neu, und starten Sie das Debugging.

    2. Öffnen Sie in der experimentellen Instanz von Visual Studio erneut das Tool Fenster, geben Sie im Suchfenster den Suchtext ein, und **drücken** Sie die EINGABETASTE.

         Es sollten die richtigen Ergebnisse angezeigt werden.

## <a name="to-customize-the-search-behavior"></a>So passen Sie das Suchverhalten an
 Durch Ändern der Sucheinstellungen können Sie eine Vielzahl von Änderungen an der Anzeige des Such Steuer Elements und der Art der Durchführung der Suche vornehmen. Beispielsweise können Sie das Wasserzeichen (den Standardtext im Suchfeld), die minimale und die maximale Breite des Such Steuer Elements ändern und festlegen, ob eine Statusanzeige angezeigt werden soll. Sie können auch den Punkt ändern, an dem die Suchergebnisse angezeigt werden (Bedarfs gesteuert oder sofort Suche) und eine Liste von Begriffen anzeigen, nach denen Sie zuletzt gesucht haben. Die komplette Liste der Einstellungen finden Sie in der- <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource> Klasse.

1. Fügen Sie in der Datei * TestSearch.cs * der-Klasse den folgenden Code hinzu `TestSearch` . Dieser Code ermöglicht die sofortige Suche anstelle der bedarfsgesteuerten Suche (was bedeutet, dass der Benutzer nicht auf die **Eingabe** Taste klicken muss). Der Code überschreibt die- `ProvideSearchSettings` Methode in der- `TestSearch` Klasse, die erforderlich ist, um die Standardeinstellungen zu ändern.

    ```csharp
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)
    {
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchStartTypeProperty.Name,
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}
    ```

2. Testen Sie die neue Einstellung, indem Sie die Projekt Mappe neu erstellen und den Debugger neu starten.

     Suchergebnisse werden jedes Mal angezeigt, wenn Sie ein Zeichen in das Suchfeld eingeben.

3. Fügen Sie in der- `ProvideSearchSettings` Methode die folgende Zeile hinzu, die die Anzeige einer Statusanzeige ermöglicht.

    ```csharp
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)
    {
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchStartTypeProperty.Name,
             (uint)VSSEARCHSTARTTYPE.SST_INSTANT);
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchProgressTypeProperty.Name,
             (uint)VSSEARCHPROGRESSTYPE.SPT_DETERMINATE);
    }
    ```

     Damit die Statusanzeige angezeigt wird, muss der Fortschritt gemeldet werden. Um den Status zu melden, heben Sie die Auskommentierung des folgenden Codes in der- `OnStartSearch` Methode der- `TestSearchTask` Klasse auf:

    ```csharp
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));
    ```

4. Um die Verarbeitung so zu verlangsamen, dass die Statusanzeige sichtbar ist, heben Sie die Auskommentierung der folgenden Zeile in der- `OnStartSearch` Methode der- `TestSearchTask` Klasse auf:

    ```csharp
    System.Threading.Thread.Sleep(100);
    ```

5. Testen Sie die neuen Einstellungen, indem Sie die Projekt Mappe neu erstellen und mit dem Debugging beginnen.

     Die Statusanzeige wird bei jeder Durchführung der Suche im Suchfenster (als blaue Linie unter dem Suchtextfeld) angezeigt.

## <a name="to-enable-users-to-refine-their-searches"></a>So können Sie es Benutzern ermöglichen, Ihre Suchvorgänge zu verfeinern
 Sie können es Benutzern ermöglichen, Ihre Suchvorgänge mithilfe von **Optionen wie z** **. b** Optionen können ein boolescher Wert sein, der als Kontrollkästchen angezeigt wird, oder Befehle, die als Schaltflächen angezeigt werden. In dieser exemplarischen Vorgehensweise erstellen Sie eine boolesche Option.

1. Fügen Sie der-Klasse in der Datei *TestSearch.cs* den folgenden Code hinzu `TestSearch` . Der Code überschreibt die- `SearchOptionsEnum` Methode, die es der Such Implementierung ermöglicht, zu erkennen, ob eine bestimmte Option aktiviert oder deaktiviert ist. Der Code in `SearchOptionsEnum` Fügt eine Option hinzu, um die Groß-/Kleinschreibung einem <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions> Enumerator zuzuordnen. Die Option zum Vergleichen der Groß-/Kleinschreibung wird auch als-Eigenschaft zur Verfügung gestellt `MatchCaseOption` .

    ```csharp
    private IVsEnumWindowSearchOptions m_optionsEnum;
    public override IVsEnumWindowSearchOptions SearchOptionsEnum
    {
        get
        {
            if (m_optionsEnum == null)
            {
                List<IVsWindowSearchOption> list = new List<IVsWindowSearchOption>();

                list.Add(this.MatchCaseOption);

                m_optionsEnum = new WindowSearchOptionEnumerator(list) as IVsEnumWindowSearchOptions;
            }
            return m_optionsEnum;
        }
    }

    private WindowSearchBooleanOption m_matchCaseOption;
    public WindowSearchBooleanOption MatchCaseOption
    {
        get
        {
            if (m_matchCaseOption == null)
            {
                m_matchCaseOption = new WindowSearchBooleanOption("Match case", "Match case", false);
            }
            return m_matchCaseOption;
        }
    }
    ```

2. Entfernen Sie in der- `TestSearchTask` Klasse die Auskommentierung der folgenden Zeile in der- `OnStartSearch` Methode:

    ```csharp
    matchCase = m_toolWindow.MatchCaseOption.Value;
    ```

3. Testen Sie die Option:

    1. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz wird geöffnet.

    2. Wählen Sie im Tool Fenster den Pfeil nach unten auf der rechten Seite des Textfelds aus.

         Das Kontrollkästchen Groß- **/Kleinschreibung** suchen wird angezeigt.

    3. Aktivieren Sie das Kontrollkästchen **Groß-/Kleinschreibung** suchen, und führen Sie dann einige suchen aus

## <a name="to-add-a-search-filter"></a>So fügen Sie einen Suchfilter hinzu
 Sie können Suchfilter hinzufügen, die es Benutzern ermöglichen, den Satz von Suchzielen zu verfeinern. Sie können z. b. Dateien im Datei-Explorer nach den Datumsangaben filtern, an denen Sie zuletzt geändert wurden, und deren Dateinamen Erweiterungen. In dieser exemplarischen Vorgehensweise fügen Sie nur Zeilen einen Filter hinzu. Wenn der Benutzer diesen Filter auswählt, fügt der suchhost die von Ihnen angegebenen Zeichen folgen der Suchabfrage hinzu. Anschließend können Sie diese Zeichen folgen in der Suchmethode identifizieren und die Suchziele entsprechend filtern.

1. Fügen Sie der-Klasse in der Datei *TestSearch.cs* den folgenden Code hinzu `TestSearch` . Der Code implementiert `SearchFiltersEnum` durch Hinzufügen eines <xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter> , das angibt, dass die Suchergebnisse so gefiltert werden, dass nur noch Zeilen angezeigt werden.

    ```csharp
    public override IVsEnumWindowSearchFilters SearchFiltersEnum
    {
        get
        {
            List<IVsWindowSearchFilter> list = new List<IVsWindowSearchFilter>();
            list.Add(new WindowSearchSimpleFilter("Search even lines only", "Search even lines only", "lines", "even"));
            return new WindowSearchFilterEnumerator(list) as IVsEnumWindowSearchFilters;
        }
    }

    ```

     Das Such Steuerelement zeigt nun den Suchfilter an `Search even lines only` . Wenn der Benutzer den Filter auswählt, wird die Zeichenfolge `lines:"even"` im Suchfeld angezeigt. Andere Suchkriterien können zur gleichen Zeit wie der Filter angezeigt werden. Such Zeichenfolgen können vor dem Filter, nach dem Filter oder beidem angezeigt werden.

2. Fügen Sie in der Datei *TestSearch.cs* der-Klasse die folgenden Methoden hinzu `TestSearchTask` , die sich in der- `TestSearch` Klasse befinden. Diese Methoden unterstützen die- `OnStartSearch` Methode, die Sie im nächsten Schritt ändern.

    ```csharp
    private string RemoveFromString(string origString, string stringToRemove)
    {
        int index = origString.IndexOf(stringToRemove);
        if (index == -1)
            return origString;
        else 
             return (origString.Substring(0, index) + origString.Substring(index + stringToRemove.Length)).Trim();
    }

    private string[] GetEvenItems(string[] contentArr)
    {
        int length = contentArr.Length / 2;
        string[] evenContentArr = new string[length];

        int indexB = 0;
        for (int index = 1; index < contentArr.Length; index += 2)
        {
            evenContentArr[indexB] = contentArr[index];
            indexB++;
        }

        return evenContentArr;
    }
    ```

3. Aktualisieren Sie die-Methode in der- `TestSearchTask` Klasse `OnStartSearch` mit dem folgenden Code. Diese Änderung aktualisiert den Code, um den Filter zu unterstützen.

    ```csharp
    protected override void OnStartSearch()
    {
        // Use the original content of the text box as the target of the search. 
        var separator = new string[] { Environment.NewLine };
        string[] contentArr = ((TestSearchControl)m_toolWindow.Content).SearchContent.Split(separator, StringSplitOptions.None);

        // Get the search option. 
        bool matchCase = false;
        matchCase = m_toolWindow.MatchCaseOption.Value;

        // Set variables that are used in the finally block.
        StringBuilder sb = new StringBuilder("");
        uint resultCount = 0;
        this.ErrorCode = VSConstants.S_OK;

        try
        {
            string searchString = this.SearchQuery.SearchString;

            // If the search string contains the filter string, filter the content array. 
            string filterString = "lines:\"even\"";

            if (this.SearchQuery.SearchString.Contains(filterString))
            {
                // Retain only the even items in the array.
                contentArr = GetEvenItems(contentArr);

                // Remove 'lines:"even"' from the search string.
                searchString = RemoveFromString(searchString, filterString);
            }

            // Determine the results. 
            uint progress = 0;
            foreach (string line in contentArr)
            {
                if (matchCase == true)
                {
                    if (line.Contains(searchString))
                    {
                        sb.AppendLine(line);
                        resultCount++;
                    }
                }
                else
                {
                    if (line.ToLower().Contains(searchString.ToLower()))
                    {
                        sb.AppendLine(line);
                        resultCount++;
                    }
                }

                SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));

                // Uncomment the following line to demonstrate the progress bar. 
                // System.Threading.Thread.Sleep(100);
            }
        }
        catch (Exception e)
        {
            this.ErrorCode = VSConstants.E_FAIL;
        }
        finally
        {
            ThreadHelper.Generic.Invoke(() =>
            { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });

            this.SearchResults = resultCount;
        }

        // Call the implementation of this method in the base class. 
        // This sets the task status to complete and reports task completion. 
        base.OnStartSearch();
    }
    ```

4. Testen Sie Ihren Code.

5. Erstellen Sie das Projekt, und starten Sie das Debugging. Öffnen Sie in der experimentellen Instanz von Visual Studio das Tool Fenster, und wählen Sie dann den Pfeil nach unten auf dem Steuerelement suchen aus.

     Das Kontrollkästchen Groß- **/Kleinschreibung** suchen und der Filter **nur Zeilen suchen** werden angezeigt.

6. Wählen Sie den Filter aus.

     Das Suchfeld enthält **Zeilen: "even"**, und die folgenden Ergebnisse werden angezeigt:

     2 gut

     4 gut

     6-Goodbye

7. Löschen `lines:"even"` Sie im Suchfeld das Kontrollkästchen Groß- **/Kleinschreibung** aktivieren, und geben Sie dann `g` in das Suchfeld ein.

     Die folgenden Ergebnisse werden angezeigt:

     1 go

     2 gut

     5.

8. Wählen Sie das X auf der rechten Seite des Suchfelds aus.

     Die Suche wird gelöscht, und der ursprüngliche Inhalt wird angezeigt. Das Kontrollkästchen **Groß-/Kleinschreibung** ist jedoch weiterhin aktiviert.
