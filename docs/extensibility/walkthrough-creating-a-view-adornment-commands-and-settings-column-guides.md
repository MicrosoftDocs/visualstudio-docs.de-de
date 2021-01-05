---
title: Erstellen eines Ansichts Zusatz Elements, von Befehlen und Einstellungen | Microsoft-Dokumentation
description: In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie den Visual Studio-Code-Editor mit Spalten Handbüchern erweitern.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 4a2df0a3-42da-4f7b-996f-ee16a35ac922
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2108abe89a47fa276da53a14439a52451d936eea
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863069"
---
# <a name="walkthrough-create-a-view-adornment-commands-and-settings-column-guides"></a>Exemplarische Vorgehensweise: Erstellen eines Ansichts Zusatz Elements, von Befehlen und Einstellungen (Spalten Handbücher)
Sie können den Visual Studio-Text-/Code-Editor mit Befehlen und Ansichts Effekten erweitern. In diesem Artikel erfahren Sie, wie Sie mit einer beliebten Erweiterungs Funktion (Spalten Handbücher) beginnen. Spalten Handbücher sind visuell helle Linien, die in der Ansicht des Text-Editors gezeichnet werden, um Ihnen die Verwaltung Ihres Codes auf bestimmte Spaltenbreiten zu erleichtern. Der formatierte Code kann insbesondere für Beispiele wichtig sein, die Sie in Dokumenten, in Blogbeiträgen oder in Fehlerberichten einschließen.

In dieser exemplarischen Vorgehensweise führen Sie folgende Aktionen aus:
- Erstellen eines VSIX-Projekts
- Hinzufügen eines Zusatz Elements für eine Editor Ansicht
- Unterstützung für das Speichern und erhalten von Einstellungen hinzufügen (wo die Spalten Handbücher und ihre Farbe gezeichnet werden sollen)
- Befehle hinzufügen (Spalten Handbücher hinzufügen/entfernen, Farbe ändern)
- Die Befehle in den Kontextmenüs "Menü Bearbeiten" und "Textdokument" platzieren
- Hinzufügen von Unterstützung für das Aufrufen der Befehle über das Visual Studio-Befehlsfenster

  Sie können eine Version der Column Guides-Funktion mit dieser Visual Studio Gallery-[Erweiterung](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines)ausprobieren.

  > [!NOTE]
  > In dieser exemplarischen Vorgehensweise fügen Sie eine große Menge an Code in einige Dateien ein, die von Visual Studio-Erweiterungs Vorlagen generiert werden. Diese exemplarische Vorgehensweise bezieht sich jedoch auf eine abgeschlossene Lösung auf GitHub mit anderen Erweiterungs Beispielen. Der abgeschlossene Code unterscheidet sich geringfügig von der Verwendung von echten Befehls Symbolen anstelle von generictemplate-Symbolen.

## <a name="get-started"></a>Erste Schritte
Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Es ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="set-up-the-solution"></a>Einrichten der Lösung
Erstellen Sie zunächst ein VSIX-Projekt, fügen Sie ein Zusatzelement für die Editor-Ansicht hinzu, und fügen Sie dann einen Befehl hinzu (mit dem ein VSPackage zur Eingabe des Befehls hinzugefügt wird). Die grundlegende Architektur lautet wie folgt:
- Sie verfügen über einen Listener zur Erstellung von Text Ansichten, der ein- `ColumnGuideAdornment` Objekt pro Ansicht erstellt. Dieses Objekt lauscht auf Ereignisse bezüglich der Änderung der Sicht oder der Einstellungen ändern, aktualisieren oder Neuzeichnen von Spalten Handbüchern nach Bedarf.
- Es gibt ein `GuidesSettingsManager` , das das Lesen und schreiben aus dem Visual Studio-Einstellungs Speicher behandelt. Der Einstellungs-Manager verfügt auch über Vorgänge zum Aktualisieren der Einstellungen, die die Benutzer Befehle unterstützen (Spalte hinzufügen, Spalte entfernen, Farbe ändern).
- Wenn Sie über Benutzer Befehle verfügen, ist ein VSIP-Paket erforderlich, aber es ist nur ein Code Baustein, der das Implementierungs Objekt der Befehle initialisiert.
- Es gibt ein- `ColumnGuideCommands` Objekt, das die Benutzer Befehle ausführt und die Befehls Handler für Befehle verknüpft, die in der *vsct* -Datei deklariert sind.

  **VSIX**. Verwenden Sie den Befehl **File &#124; New...** , um ein Projekt zu erstellen. Wählen Sie im linken Navigationsbereich unter **c#** den Knoten **Erweiterbarkeit** aus, und wählen Sie im rechten Bereich **VSIX-Projekt** aus. Geben Sie den Namen **columnguides** ein, und wählen Sie **OK** , um das Projekt zu erstellen.

  **Anzeige** Zusatz. Klicken Sie im Projektmappen-Explorer auf die Schaltfläche mit dem rechten Zeiger auf den Projekt Knoten. Wählen Sie den Befehl **&#124; neues Element hinzufügen...** aus, um ein neues Ansichts Zusatzelement hinzuzufügen. Wählen Sie im linken Navigationsbereich die Option **Erweiterbarkeit &#124; Editor** aus, und wählen Sie im rechten Bereich **Editor Viewport** -Zusatzelement aus. Geben Sie den Namen **columnguideadornment** als Elementnamen ein, und klicken Sie auf **Hinzufügen** , um ihn hinzuzufügen.

  Sie können sehen, dass diese Element Vorlage zwei Dateien zum Projekt hinzugefügt hat (sowie Verweise usw.): **ColumnGuideAdornment.cs** und **ColumnGuideAdornmentTextViewCreationListener.cs**. Die Vorlagen zeichnen ein Violettes Rechteck in der Ansicht. Im folgenden Abschnitt ändern Sie einige Zeilen im Ansichts erstellungslistener und ersetzen den Inhalt von **ColumnGuideAdornment.cs**.

  **Befehle**. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf den Projekt Knoten. Wählen Sie den Befehl **&#124; neues Element hinzufügen...** aus, um ein neues Ansichts Zusatzelement hinzuzufügen. Klicken Sie im linken Navigationsbereich auf **Erweiterbarkeit &#124; VSPackage** , und wählen Sie im rechten Bereich **benutzerdefinierter Befehl** aus. Geben Sie den Namen **columnguidecommands** als Elementname ein, und wählen Sie **Hinzufügen** aus. Zusätzlich zu mehreren verweisen wurden durch das Hinzufügen der Befehle und des Pakets auch **ColumnGuideCommands.cs**, **ColumnGuideCommandsPackage.cs** und **columnguidecommandspackage. vsct** hinzugefügt. Im folgenden Abschnitt ersetzen Sie den Inhalt der ersten und letzten Dateien, um die Befehle zu definieren und zu implementieren.

## <a name="set-up-the-text-view-creation-listener"></a>Einrichten des Ansichts erstellerstellers der Textansicht
Öffnen Sie *ColumnGuideAdornmentTextViewCreationListener.cs* im Editor. Mit diesem Code wird ein Handler implementiert, wenn Visual Studio Text Ansichten erstellt. Es gibt Attribute, die Steuern, wann der Handler aufgerufen wird, abhängig von den Merkmalen der Ansicht.

Der Code muss auch eine Zusatzelement-Ebene deklarieren. Wenn der Editor Ansichten aktualisiert, ruft er die Zusatzelement Ebenen für die Ansicht ab, die die Zusatzelement Elemente abruft. Sie können die Reihenfolge der Ebene relativ zu anderen Attributen mit Attributen deklarieren. Ersetzen Sie die folgende Zeile:

```csharp
[Order(After = PredefinedAdornmentLayers.Caret)]
```

mit diesen beiden Zeilen:

```csharp
[Order(Before = PredefinedAdornmentLayers.Text)]
[TextViewRole(PredefinedTextViewRoles.Document)]
```

Die von Ihnen ersetzte Zeile gehört zu einer Gruppe von Attributen, die eine Zusatzelement-Ebene deklarieren. Die erste Zeile, die Sie geändert haben, ändert sich nur, wenn die Spalten Führungslinien angezeigt werden Wenn Sie die Zeilen vor dem Text in der Ansicht zeichnen, bedeutet dies, dass Sie hinter oder unterhalb des Texts angezeigt werden. Die zweite Zeile deklariert, dass die Zusatzelemente des Spalten Handbuchs auf Text Entitäten anwendbar sind, die Ihrem Konzept eines Dokuments entsprechen. Sie können das Zusatzelement jedoch so deklarieren, dass es nur für bearbeitbaren Text funktioniert. Weitere Informationen finden Sie in den [Erweiterungs Punkten für den Sprachdienst und den Editor](../extensibility/language-service-and-editor-extension-points.md) .

## <a name="implement-the-settings-manager"></a>Implementieren des Einstellungs-Managers
Ersetzen Sie den Inhalt der *GuidesSettingsManager.cs* durch den folgenden Code (unten erläutert):

```csharp
using Microsoft.VisualStudio.Settings;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Settings;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Windows.Media;

namespace ColumnGuides
{
    internal static class GuidesSettingsManager
    {
        // Because my code is always called from the UI thred, this succeeds.
        internal static SettingsManager VsManagedSettingsManager =
            new ShellSettingsManager(ServiceProvider.GlobalProvider);

        private const int _maxGuides = 5;
        private const string _collectionSettingsName = "Text Editor";
        private const string _settingName = "Guides";
        // 1000 seems reasonable since primary scenario is long lines of code
        private const int _maxColumn = 1000;

        static internal bool AddGuideline(int column)
        {
            if (! IsValidColumn(column))
                throw new ArgumentOutOfRangeException(
                    "column",
                    "The paramenter must be between 1 and " + _maxGuides.ToString());
            var offsets = GuidesSettingsManager.GetColumnOffsets();
            if (offsets.Count() >= _maxGuides)
                return false;
            // Check for duplicates
            if (offsets.Contains(column))
                return false;
            offsets.Add(column);
            WriteSettings(GuidesSettingsManager.GuidelinesColor, offsets);
            return true;
        }

        static internal bool RemoveGuideline(int column)
        {
            if (!IsValidColumn(column))
                throw new ArgumentOutOfRangeException(
                    "column", "The paramenter must be between 1 and 10,000");
            var columns = GuidesSettingsManager.GetColumnOffsets();
            if (! columns.Remove(column))
            {
                // Not present.  Allow user to remove the last column
                // even if they're not on the right column.
                if (columns.Count != 1)
                    return false;

                columns.Clear();
            }
            WriteSettings(GuidesSettingsManager.GuidelinesColor, columns);
            return true;
        }

        static internal bool CanAddGuideline(int column)
        {
            if (!IsValidColumn(column))
                return false;
            var offsets = GetColumnOffsets();
            if (offsets.Count >= _maxGuides)
                return false;
            return ! offsets.Contains(column);
        }

        static internal bool CanRemoveGuideline(int column)
        {
            if (! IsValidColumn(column))
                return false;
            // Allow user to remove the last guideline regardless of the column.
            // Okay to call count, we limit the number of guides.
            var offsets = GuidesSettingsManager.GetColumnOffsets();
            return offsets.Contains(column) || offsets.Count() == 1;
        }

        static internal void RemoveAllGuidelines()
        {
            WriteSettings(GuidesSettingsManager.GuidelinesColor, new int[0]);
        }

        private static bool IsValidColumn(int column)
        {
            // zero is allowed (per user request)
            return 0 <= column && column <= _maxColumn;
        }

        // This has format "RGB(<int>, <int>, <int>) <int> <int>...".
        // There can be any number of ints following the RGB part,
        // and each int is a column (char offset into line) where to draw.
        static private string _guidelinesConfiguration;
        static private string GuidelinesConfiguration
        {
            get
            {
                if (_guidelinesConfiguration == null)
                {
                    _guidelinesConfiguration =
                        GetUserSettingsString(
                            GuidesSettingsManager._collectionSettingsName,
                            GuidesSettingsManager._settingName)
                        .Trim();
                }
                return _guidelinesConfiguration;
            }

            set
            {
                if (value != _guidelinesConfiguration)
                {
                    _guidelinesConfiguration = value;
                    WriteUserSettingsString(
                        GuidesSettingsManager._collectionSettingsName,
                        GuidesSettingsManager._settingName, value);
                    // Notify ColumnGuideAdornments to update adornments in views.
                    var handler = GuidesSettingsManager.SettingsChanged;
                    if (handler != null)
                        handler();
                }
            }
        }

        internal static string GetUserSettingsString(string collection, string setting)
        {
            var store = GuidesSettingsManager
                            .VsManagedSettingsManager
                            .GetReadOnlySettingsStore(SettingsScope.UserSettings);
            return store.GetString(collection, setting, "RGB(255,0,0) 80");
        }

        internal static void WriteUserSettingsString(string key, string propertyName,
                                                     string value)
        {
            var store = GuidesSettingsManager
                            .VsManagedSettingsManager
                            .GetWritableSettingsStore(SettingsScope.UserSettings);
            store.CreateCollection(key);
            store.SetString(key, propertyName, value);
        }

        // Persists settings and sets property with side effect of signaling
        // ColumnGuideAdornments to update.
        static private void WriteSettings(Color color, IEnumerable<int> columns)
        {
            string value = ComposeSettingsString(color, columns);
            GuidelinesConfiguration = value;
        }

        private static string ComposeSettingsString(Color color,
                                                    IEnumerable<int> columns)
        {
            StringBuilder sb = new StringBuilder();
            sb.AppendFormat("RGB({0},{1},{2})", color.R, color.G, color.B);
            IEnumerator<int> columnsEnumerator = columns.GetEnumerator();
            if (columnsEnumerator.MoveNext())
            {
                sb.AppendFormat(" {0}", columnsEnumerator.Current);
                while (columnsEnumerator.MoveNext())
                {
                    sb.AppendFormat(", {0}", columnsEnumerator.Current);
                }
            }
            return sb.ToString();
        }

        // Parse a color out of a string that begins like "RGB(255,0,0)"
        static internal Color GuidelinesColor
        {
            get
            {
                string config = GuidelinesConfiguration;
                if (!String.IsNullOrEmpty(config) && config.StartsWith("RGB("))
                {
                    int lastParen = config.IndexOf(')');
                    if (lastParen > 4)
                    {
                        string[] rgbs = config.Substring(4, lastParen - 4).Split(',');

                        if (rgbs.Length >= 3)
                        {
                            byte r, g, b;
                            if (byte.TryParse(rgbs[0], out r) &&
                                byte.TryParse(rgbs[1], out g) &&
                                byte.TryParse(rgbs[2], out b))
                            {
                                return Color.FromRgb(r, g, b);
                            }
                        }
                    }
                }
                return Colors.DarkRed;
            }

            set
            {
                WriteSettings(value, GetColumnOffsets());
            }
        }

        // Parse a list of integer values out of a string that looks like
        // "RGB(255,0,0) 1, 5, 10, 80"
        static internal List<int> GetColumnOffsets()
        {
            var result = new List<int>();
            string settings = GuidesSettingsManager.GuidelinesConfiguration;
            if (String.IsNullOrEmpty(settings))
                return new List<int>();

            if (!settings.StartsWith("RGB("))
                return new List<int>();

            int lastParen = settings.IndexOf(')');
            if (lastParen <= 4)
                return new List<int>();

            string[] columns = settings.Substring(lastParen + 1).Split(',');

            int columnCount = 0;
            foreach (string columnText in columns)
            {
                int column = -1;
                // VS 2008 gallery extension didn't allow zero, so per user request ...
                if (int.TryParse(columnText, out column) && column >= 0)
                {
                    columnCount++;
                    result.Add(column);
                    if (columnCount >= _maxGuides)
                        break;
                }
            }
            return result;
        }

        // Delegate and Event to fire when settings change so that ColumnGuideAdornments
        // can update.  We need nothing special in this event since the settings manager
        // is statically available.
        //
        internal delegate void SettingsChangedHandler();
        static internal event SettingsChangedHandler SettingsChanged;

    }
}

```

Der größte Teil dieses Codes erstellt und analysiert das Einstellungs Format: "RGB ( \<int> , \<int> , \<int> ) \<int> , \<int> ,...".  Die ganzen Zahlen am Ende sind die einbasierten Spalten, in denen Sie Spalten Handbücher benötigen. Die Erweiterung der Spalten Handbücher erfasst alle Einstellungen in einer einzelnen Einstellungs Wert Zeichenfolge.

Es sind einige Teile des Codes hervorzuheben. Mit der folgenden Codezeile wird der verwaltete Visual Studio-Wrapper für den Einstellungs Speicher abgerufen. Größtenteils abstrahiert dies die Windows-Registrierung, aber diese API ist unabhängig vom Speichermechanismus.

```csharp
internal static SettingsManager VsManagedSettingsManager =
    new ShellSettingsManager(ServiceProvider.GlobalProvider);
```

Der Speicher der Visual Studio-Einstellungen verwendet einen Kategoriebezeichner und einen Einstellungs Bezeichner, um alle Einstellungen eindeutig zu identifizieren:

```csharp
private const string _collectionSettingsName = "Text Editor";
private const string _settingName = "Guides";
```

Sie müssen nicht `"Text Editor"` als Kategoriename verwenden. Sie können alles auswählen, was Sie möchten.

Die ersten Funktionen sind die Einstiegspunkte, um die Einstellungen zu ändern. Sie überprüfen Einschränkungen auf hoher Ebene wie die maximal zulässige Anzahl von Handbüchern.  Dann rufen Sie auf `WriteSettings` , wodurch eine Einstellungs Zeichenfolge verfasst und die-Eigenschaft festgelegt wird `GuideLinesConfiguration` . Durch Festlegen dieser Eigenschaft wird der Einstellungs Wert in den Visual Studio-Einstellungs Speicher gespeichert, und das- `SettingsChanged` Ereignis wird ausgelöst, um alle-Objekte zu aktualisieren `ColumnGuideAdornment` , die jeweils mit einer Textansicht verknüpft sind.

Es gibt mehrere Einstiegspunkt Funktionen, wie z. b. `CanAddGuideline` , die zum Implementieren von Befehlen verwendet werden, die Einstellungen ändern. Wenn Visual Studio Menüs anzeigt, werden Befehls Implementierungen abgefragt, um zu überprüfen, ob der Befehl derzeit aktiviert ist, was der Name ist usw.  Im folgenden erfahren Sie, wie Sie diese Einstiegspunkte für die Befehls Implementierungen verbinden können. Weitere Informationen zu Befehlen finden Sie unter [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md).

## <a name="implement-the-columnguideadornment-class"></a>Implementieren der columnguideadornment-Klasse
Die- `ColumnGuideAdornment` Klasse wird für jede Textansicht instanziiert, die Zusatzelemente aufweisen kann. Diese Klasse lauscht auf Ereignisse über das Ändern der Sicht oder Einstellungen und die Aktualisierungs-oder neuzeichenführungs Handbücher nach Bedarf.

Ersetzen Sie den Inhalt der *ColumnGuideAdornment.cs* durch den folgenden Code (unten erläutert):

```csharp
using System;
using System.Windows.Media;
using Microsoft.VisualStudio.Text.Editor;
using System.Collections.Generic;
using System.Windows.Shapes;
using Microsoft.VisualStudio.Text.Formatting;
using System.Windows;

namespace ColumnGuides
{
    /// <summary>
    /// Adornment class, one instance per text view that draws a guides on the viewport
    /// </summary>
    internal sealed class ColumnGuideAdornment
    {
        private const double _lineThickness = 1.0;
        private IList<Line> _guidelines;
        private IWpfTextView _view;
        private double _baseIndentation;
        private double _columnWidth;

        /// <summary>
        /// Creates editor column guidelines
        /// </summary>
        /// <param name="view">The <see cref="IWpfTextView"/> upon
        /// which the adornment will be drawn</param>
        public ColumnGuideAdornment(IWpfTextView view)
        {
            _view = view;
            _guidelines = CreateGuidelines();
            GuidesSettingsManager.SettingsChanged +=
                new GuidesSettingsManager.SettingsChangedHandler(SettingsChanged);
            view.LayoutChanged +=
                new EventHandler<TextViewLayoutChangedEventArgs>(OnViewLayoutChanged);
            _view.Closed += new EventHandler(OnViewClosed);
        }

        void SettingsChanged()
        {
            _guidelines = CreateGuidelines();
            UpdatePositions();
            AddGuidelinesToAdornmentLayer();
        }

        void OnViewClosed(object sender, EventArgs e)
        {
            _view.LayoutChanged -= OnViewLayoutChanged;
            _view.Closed -= OnViewClosed;
            GuidesSettingsManager.SettingsChanged -= SettingsChanged;
        }

        private bool _firstLayoutDone;

        void OnViewLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)
        {
            bool fUpdatePositions = false;

            IFormattedLineSource lineSource = _view.FormattedLineSource;
            if (lineSource == null)
            {
                return;
            }
            if (_columnWidth != lineSource.ColumnWidth)
            {
                _columnWidth = lineSource.ColumnWidth;
                fUpdatePositions = true;
            }
            if (_baseIndentation != lineSource.BaseIndentation)
            {
                _baseIndentation = lineSource.BaseIndentation;
                fUpdatePositions = true;
            }
            if (fUpdatePositions ||
                e.VerticalTranslation ||
                e.NewViewState.ViewportTop != e.OldViewState.ViewportTop ||
                e.NewViewState.ViewportBottom != e.OldViewState.ViewportBottom)
            {
                UpdatePositions();
            }
            if (!_firstLayoutDone)
            {
                AddGuidelinesToAdornmentLayer();
                _firstLayoutDone = true;
            }
        }

        private static IList<Line> CreateGuidelines()
        {
            Brush lineBrush = new SolidColorBrush(GuidesSettingsManager.GuidelinesColor);
            DoubleCollection dashArray = new DoubleCollection(new double[] { 1.0, 3.0 });
            IList<Line> result = new List<Line>();
            foreach (int column in GuidesSettingsManager.GetColumnOffsets())
            {
                Line line = new Line()
                {
                    // Use the DataContext slot as a cookie to hold the column
                    DataContext = column,
                    Stroke = lineBrush,
                    StrokeThickness = _lineThickness,
                    StrokeDashArray = dashArray
                };
                result.Add(line);
            }
            return result;
        }

        void UpdatePositions()
        {
            foreach (Line line in _guidelines)
            {
                int column = (int)line.DataContext;
                line.X2 = _baseIndentation + 0.5 + column * _columnWidth;
                line.X1 = line.X2;
                line.Y1 = _view.ViewportTop;
                line.Y2 = _view.ViewportBottom;
            }
        }

        void AddGuidelinesToAdornmentLayer()
        {
            // Grab a reference to the adornment layer that this adornment
            // should be added to
            // Must match exported name in ColumnGuideAdornmentTextViewCreationListener
            IAdornmentLayer adornmentLayer =
                _view.GetAdornmentLayer("ColumnGuideAdornment");
            if (adornmentLayer == null)
                return;
            adornmentLayer.RemoveAllAdornments();
            // Add the guidelines to the adornment layer and make them relative
            // to the viewport
            foreach (UIElement element in _guidelines)
                adornmentLayer.AddAdornment(AdornmentPositioningBehavior.OwnerControlled,
                                            null, null, element, null);
        }
    }

}
```

Instanzen dieser Klasse behalten die zugeordnete <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> und eine Liste von- `Line` Objekten bei, die in der Ansicht gezeichnet werden.

Der Konstruktor (von dem aufgerufen wird, `ColumnGuideAdornmentTextViewCreationListener` Wenn Visual Studio neue Sichten erstellt) erstellt die Spalten Leit Faden `Line` Objekte.  Der-Konstruktor fügt auch Handler für das `SettingsChanged` -Ereignis (definiert in `GuidesSettingsManager` ) und die Ansichts Ereignisse `LayoutChanged` und hinzu `Closed` .

Das `LayoutChanged` Ereignis wird aufgrund verschiedener Arten von Änderungen in der Ansicht ausgelöst, einschließlich der Erstellung der Ansicht durch Visual Studio. Der `OnViewLayoutChanged` Handler ruft `AddGuidelinesToAdornmentLayer` auf, um auszuführen. Der Code in `OnViewLayoutChanged` bestimmt, ob Zeilen Positionen auf der Grundlage von Änderungen wie z. b. Schriftart Größenänderungen, Ansichts-guttern, horizontaler Scrollen usw. aktualisiert werden müssen. Der Code in `UpdatePositions` bewirkt, dass Führungslinien zwischen Zeichen oder direkt hinter der Spalte mit Text zeichnen, die sich im angegebenen Zeichen Offset in der Textzeile befindet.

Jedes Mal, wenn Einstellungen geändert `SettingsChanged` werden, werden alle `Line` Objekte mit den neuen Einstellungen neu erstellt. Nach dem Festlegen der Zeilen Positionen entfernt der Code alle vorherigen `Line` Objekte aus der Zusatzelement `ColumnGuideAdornment` Ebene und fügt die neuen Objekte hinzu.

## <a name="define-the-commands-menus-and-menu-placements"></a>Hiermit werden die Befehle, Menüs und Menü Platzierungen definiert.
Es kann viel zum Deklarieren von Befehlen und Menüs, zum Platzieren von Gruppen von Befehlen oder Menüs in verschiedenen anderen Menüs und zum Einbinden von Befehls Handlern geben. In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Befehle in dieser Erweiterung funktionieren. Weitere Informationen finden Sie unter [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md).

### <a name="introduction-to-the-code"></a>Einführung in den Code
Die Erweiterung der Spalten Handbücher zeigt, wie Sie eine Gruppe von Befehlen deklarieren, die zusammengehören (Spalte hinzufügen, Spalte entfernen, Zeilen Farbe ändern) und diese Gruppe dann in einem Untermenü des Kontextmenüs des Editors platzieren.  Die Erweiterung für die Spalten Handbücher fügt die Befehle auch dem Haupt Menü **Bearbeiten** hinzu, behält sie aber unsichtbar bei, die als häufiges Muster behandelt werden.

Die Implementierung der Befehle besteht aus drei Teilen: ColumnGuideCommandsPackage.cs, columnguidecommandspackage. vsct und ColumnGuideCommands.cs. Der von den Vorlagen generierte Code fügt einen Befehl in das **Menü Extras** ein, das ein Dialogfeld als Implementierung auffüllt. Sie können sich ansehen, wie dies in den *vsct* -und *ColumnGuideCommands.cs* -Dateien implementiert wird, da es unkompliziert ist. Ersetzen Sie den Code in diesen Dateien unten.

Der Paket Code enthält Code Bausteine, die für Visual Studio erforderlich sind, um zu ermitteln, ob die Erweiterung Befehle anbietet, und um zu ermitteln, wo die Befehle platziert werden sollen. Beim Initialisieren des Pakets wird die Implementierungs Klasse der Befehle instanziiert. Weitere Informationen zu Paketen in Bezug auf Befehle finden Sie unter [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md).

### <a name="a-common-commands-pattern"></a>Ein gemeinsames Befehls Muster
Die Befehle in der Erweiterung der Spalten Handbücher sind ein Beispiel für ein sehr gängiges Muster in Visual Studio. Sie fügen verwandte Befehle in eine Gruppe ein, und Sie platzieren diese Gruppe in einem Hauptmenü, das häufig mit " `<CommandFlag>CommandWellOnly</CommandFlag>` " festgelegt wird, damit der Befehl unsichtbar wird.  Durch das Einfügen von Befehlen in die Hauptmenüs (z. b. **Bearbeiten**) erhalten Sie praktische Namen (z **. b. Edit. addcolumnguide**), die zum Suchen von Befehlen beim erneuten Zuweisen von Tasten Zuordnungen in den **Tools-Optionen** nützlich sind. Es ist auch hilfreich, wenn Sie Befehle im **Befehlsfenster** aufrufen.

Dann fügen Sie die Gruppe der Befehle zu Kontextmenüs oder Untermenüs hinzu, in denen Sie erwarten, dass der Benutzer die Befehle verwendet. Visual Studio behandelt `CommandWellOnly` nur ein insichtbarkeits-Flag für die Hauptmenüs. Wenn Sie dieselbe Gruppe von Befehlen in einem Kontextmenü oder Untermenü platzieren, sind die Befehle sichtbar.

Im Rahmen des allgemeinen Musters erstellt die Erweiterung der Spalten Handbücher eine zweite Gruppe, die ein einzelnes Untermenü enthält. Das Untermenü enthält wiederum die erste Gruppe mit den vier Spalten-Führungs Befehlen. Die zweite Gruppe, in der das Untermenü enthalten ist, ist das wiederverwendbare Asset, das Sie in verschiedenen Kontextmenüs platzieren, das ein Untermenü in diesen Kontextmenüs einfügt.

### <a name="the-vsct-file"></a>Die vsct-Datei
Die *vsct* -Datei deklariert die Befehle und wo Sie zusammen mit Symbolen usw. angezeigt werden. Ersetzen Sie den Inhalt der *vsct* -Datei durch den folgenden Code (unten erläutert):

```xml
<?xml version="1.0" encoding="utf-8"?>
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">

  <!--  This is the file that defines the actual layout and type of the commands.
        It is divided in different sections (e.g. command definition, command
        placement, ...), with each defining a specific set of properties.
        See the comment before each section for more details about how to
        use it. -->

  <!--  The VSCT compiler (the tool that translates this file into the binary
        format that VisualStudio will consume) has the ability to run a preprocessor
        on the vsct file; this preprocessor is (usually) the C++ preprocessor, so
        it is possible to define includes and macros with the same syntax used
        in C++ files. Using this ability of the compiler here, we include some files
        defining some of the constants that we will use inside the file. -->

  <!--This is the file that defines the IDs for all the commands exposed by
      VisualStudio. -->
  <Extern href="stdidcmd.h"/>

  <!--This header contains the command ids for the menus provided by the shell. -->
  <Extern href="vsshlids.h"/>

  <!--The Commands section is where commands, menus, and menu groups are defined.
      This section uses a Guid to identify the package that provides the command
      defined inside it. -->
  <Commands package="guidColumnGuideCommandsPkg">
    <!-- Inside this section we have different sub-sections: one for the menus, another
    for the menu groups, one for the buttons (the actual commands), one for the combos
    and the last one for the bitmaps used. Each element is identified by a command id
    that is a unique pair of guid and numeric identifier; the guid part of the identifier
    is usually called "command set" and is used to group different command inside a
    logically related group; your package should define its own command set in order to
    avoid collisions with command ids defined by other packages. -->

    <!-- In this section you can define new menu groups. A menu group is a container for
         other menus or buttons (commands); from a visual point of view you can see the
         group as the part of a menu contained between two lines. The parent of a group
         must be a menu. -->
    <Groups>

      <!-- The main group is parented to the edit menu. All the buttons within the group
           have the "CommandWellOnly" flag, so they're actually invisible, but it means
           they get canonical names that begin with "Edit". Using placements, the group
           is also placed in the GuidesSubMenu group. -->
      <!-- The priority 0xB801 is chosen so it goes just after
           IDG_VS_EDIT_COMMANDWELL -->
      <Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
             priority="0xB801">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />
      </Group>

      <!-- Group for holding the "Guidelines" sub-menu anchor (the item on the menu that
           drops the sub menu). The group is parented to
           the context menu for code windows. That takes care of most editors, but it's
           also placed in a couple of other windows using Placements -->
      <Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
             priority="0x0600">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_CTXT_CODEWIN" />
      </Group>

    </Groups>

    <Menus>
      <Menu guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" priority="0x1000"
            type="Menu">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup" />
        <Strings>
          <ButtonText>&Column Guides</ButtonText>
        </Strings>
      </Menu>
    </Menus>

    <!--Buttons section. -->
    <!--This section defines the elements the user can interact with, like a menu command or a button
        or combo box in a toolbar. -->
    <Buttons>
      <!--To define a menu group you have to specify its ID, the parent menu and its
          display priority.
          The command is visible and enabled by default. If you need to change the
          visibility, status, etc, you can use the CommandFlag node.
          You can add more than one CommandFlag node e.g.:
              <CommandFlag>DefaultInvisible</CommandFlag>
              <CommandFlag>DynamicVisibility</CommandFlag>
          If you do not want an image next to your command, remove the Icon node or
          set it to <Icon guid="guidOfficeIcon" id="msotcidNoIcon" /> -->

      <Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"
              priority="0x0100" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <Icon guid="guidImages" id="bmpPicAddGuide" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <CommandFlag>AllowParams</CommandFlag>
        <Strings>
          <ButtonText>&Add Column Guide</ButtonText>
        </Strings>
      </Button>

      <Button guid="guidColumnGuidesCommandSet" id="cmdidRemoveColumnGuide"
              priority="0x0101" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <Icon guid="guidImages" id="bmpPicRemoveGuide" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <CommandFlag>AllowParams</CommandFlag>
        <Strings>
          <ButtonText>&Remove Column Guide</ButtonText>
        </Strings>
      </Button>

      <Button guid="guidColumnGuidesCommandSet" id="cmdidChooseGuideColor"
              priority="0x0103" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <Icon guid="guidImages" id="bmpPicChooseColor" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <Strings>
          <ButtonText>Column Guide &Color...</ButtonText>
        </Strings>
      </Button>

      <Button guid="guidColumnGuidesCommandSet" id="cmdidRemoveAllColumnGuides"
              priority="0x0102" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <Strings>
          <ButtonText>Remove A&ll Columns</ButtonText>
        </Strings>
      </Button>
    </Buttons>

    <!--The bitmaps section is used to define the bitmaps that are used for the
        commands.-->
    <Bitmaps>
      <!--  The bitmap id is defined in a way that is a little bit different from the
            others:
            the declaration starts with a guid for the bitmap strip, then there is the
            resource id of the bitmap strip containing the bitmaps and then there are
            the numeric ids of the elements used inside a button definition. An important
            aspect of this declaration is that the element id
            must be the actual index (1-based) of the bitmap inside the bitmap strip. -->
      <Bitmap guid="guidImages" href="Resources\ColumnGuideCommands.png"
              usedList="bmpPicAddGuide, bmpPicRemoveGuide, bmpPicChooseColor" />
    </Bitmaps>

  </Commands>

  <CommandPlacements>

    <!-- Define secondary placements for our groups -->

    <!-- Place the group containing the three commands in the sub-menu -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
                      priority="0x0100">
      <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />
    </CommandPlacement>

    <!-- The HTML editor context menu, for some reason, redefines its own groups
         so we need to place a copy of our context menu there too. -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_HTML" />
    </CommandPlacement>

    <!-- The HTML context menu in Dev12 changed. -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp_Dev12" id="IDMX_HTM_SOURCE_HTML_Dev12" />
    </CommandPlacement>

    <!-- Similarly for Script -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_SCRIPT" />
    </CommandPlacement>

    <!-- Similarly for ASPX  -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_ASPX" />
    </CommandPlacement>

    <!-- Similarly for the XAML editor context menu -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x0600">
      <Parent guid="guidXamlUiCmds" id="IDM_XAML_EDITOR" />
    </CommandPlacement>

  </CommandPlacements>

  <!-- This defines the identifiers and their values used above to index resources
       and specify commands. -->
  <Symbols>
    <!-- This is the package guid. -->
    <GuidSymbol name="guidColumnGuideCommandsPkg"
                value="{e914e5de-0851-4904-b361-1a3a9d449704}" />

    <!-- This is the guid used to group the menu commands together -->
    <GuidSymbol name="guidColumnGuidesCommandSet"
                value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">
      <IDSymbol name="GuidesContextMenuGroup" value="0x1020" />
      <IDSymbol name="GuidesMenuItemsGroup" value="0x1021" />
      <IDSymbol name="GuidesSubMenu" value="0x1022" />
      <IDSymbol name="cmdidAddColumnGuide" value="0x0100" />
      <IDSymbol name="cmdidRemoveColumnGuide" value="0x0101" />
      <IDSymbol name="cmdidChooseGuideColor" value="0x0102" />
      <IDSymbol name="cmdidRemoveAllColumnGuides" value="0x0103" />
    </GuidSymbol>

    <GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">
      <IDSymbol name="bmpPicAddGuide" value="1" />
      <IDSymbol name="bmpPicRemoveGuide" value="2" />
      <IDSymbol name="bmpPicChooseColor" value="3" />
    </GuidSymbol>

    <GuidSymbol name="CMDSETID_HtmEdGrp_Dev12"
                value="{78F03954-2FB8-4087-8CE7-59D71710B3BB}">
      <IDSymbol name="IDMX_HTM_SOURCE_HTML_Dev12" value="0x1" />
    </GuidSymbol>

    <GuidSymbol name="CMDSETID_HtmEdGrp" value="{d7e8c5e1-bdb8-11d0-9c88-0000f8040a53}">
      <IDSymbol name="IDMX_HTM_SOURCE_HTML" value="0x33" />
      <IDSymbol name="IDMX_HTM_SOURCE_SCRIPT" value="0x34" />
      <IDSymbol name="IDMX_HTM_SOURCE_ASPX" value="0x35" />
    </GuidSymbol>

    <GuidSymbol name="guidXamlUiCmds" value="{4c87b692-1202-46aa-b64c-ef01faec53da}">
      <IDSymbol name="IDM_XAML_EDITOR" value="0x103" />
    </GuidSymbol>
  </Symbols>

</CommandTable>

```

**GUIDs**. Damit Ihre Befehls Handler von Visual Studio gefunden und aufgerufen werden können, müssen Sie sicherstellen, dass die in der *ColumnGuideCommandsPackage.cs* -Datei (generiert aus der Projekt Element Vorlage) deklarierte Paket-GUID mit der in der *vsct* -Datei deklarierten Paket-GUID übereinstimmt (von oben kopiert). Wenn Sie diesen Beispielcode wieder verwenden, sollten Sie sicherstellen, dass Sie über eine andere GUID verfügen, damit Sie nicht in Konflikt mit anderen Personen stehen, die diesen Code möglicherweise kopiert haben.

Diese Zeile in *ColumnGuideCommandsPackage.cs* suchen und die GUID zwischen den Anführungszeichen kopieren:

```csharp
public const string PackageGuidString = "ef726849-5447-4f73-8de5-01b9e930f7cd";
```

Fügen Sie dann die GUID in die *vsct* -Datei ein, sodass Ihre Deklarationen die folgende Zeile enthalten `Symbols` :

```xml
<GuidSymbol name="guidColumnGuideCommandsPkg"
            value="{ef726849-5447-4f73-8de5-01b9e930f7cd}" />
```

Die GUIDs für den Befehlssatz und die Bitmap-Bilddatei sollten auch für Ihre Erweiterungen eindeutig sein:

```xml
<GuidSymbol name="guidColumnGuidesCommandSet"
            value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">
<GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">
```

Sie müssen jedoch in dieser exemplarischen Vorgehensweise nicht die Befehlssatz-und Bitmap-Image-GUIDs ändern, damit der Code funktioniert. Die Befehlssatz-GUID muss der Deklaration in der *ColumnGuideCommands.cs* -Datei entsprechen, aber Sie ersetzen auch den Inhalt dieser Datei. Daher stimmen die GUIDs ab.

Andere GUIDs in der *vsct* -Datei identifizieren bereits vorhandene Menüs, denen die Befehle des Spalten Handbuchs hinzugefügt werden, sodass Sie sich nie ändern.

**Datei Abschnitte**. Die *vsct* -Datei enthält drei äußere Abschnitte: Befehle, Platzierungen und Symbole. Der Abschnitt "Befehle" definiert Befehls Gruppen, Menüs, Schaltflächen oder Menü Elemente und Bitmaps für Symbole. Der Abschnitt "Platzierungs" deklariert, wo Gruppen in Menüs oder zusätzlichen Platzierungs Vorplätzen in bereits vorhandene Menüs gelangen. Im Abschnitt "Symbole" werden Bezeichner deklariert, die an anderer Stelle in der *vsct* -Datei verwendet werden, wodurch der *vsct* -Code besser lesbar ist als bei allen GUIDs und hexadezimal Zahlen.

**Abschnitt "Befehle", Gruppendefinitionen**. Der Befehls Abschnitt definiert zuerst Befehls Gruppen. Gruppen von Befehlen sind Befehle, die in Menüs mit geringfügigen grauen Zeilen angezeigt werden, die die Gruppen trennen. Eine Gruppe kann auch ein gesamtes Untermenü ausfüllen, wie in diesem Beispiel gezeigt, und in diesem Fall werden keine grauen Trennlinien angezeigt. Die *vsct* -Dateien deklarieren zwei Gruppen, das, das `GuidesMenuItemsGroup` dem `IDM_VS_MENU_EDIT` (dem Haupt Menü **Bearbeiten** ) übergeordnet ist, und das-Element, das `GuidesContextMenuGroup` der übergeordnet ist `IDM_VS_CTXT_CODEWIN` (das Kontextmenü des Code-Editors).

Die zweite Gruppen Deklaration hat eine `0x0600` Priorität:

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
             priority="0x0600">
```

Die Idee besteht darin, das Untermenü für die Spalten Handbücher am Ende eines beliebigen Kontextmenüs zu platzieren, dem Sie die unter Menü Gruppe hinzufügen. Sie sollten jedoch nicht davon ausgehen, dass Sie am besten Wissen und das Untermenü so erzwingen, dass es immer mit der Priorität von angezeigt wird `0xFFFF` . Sie müssen mit der Zahl experimentieren, um zu sehen, wo sich Ihr Untermenü in den Kontextmenüs befindet, in denen Sie es platzieren. In diesem Fall `0x0600` ist hoch genug, um Sie am Ende der Menüs zu platzieren, so weit, wie Sie sehen können, aber es bleibt Platz für eine andere Person, ihre Erweiterung so zu entwerfen, dass Sie niedriger ist als die Erweiterung der Spalten Handbücher, wenn dies wünschenswert ist.

**Befehls Abschnitt, Menü Definition**. Als nächstes definiert der Befehls Abschnitt das Untermenü `GuidesSubMenu` , das dem zugeordnet ist `GuidesContextMenuGroup` . `GuidesContextMenuGroup`Ist die Gruppe, die Sie allen relevanten Kontextmenüs hinzufügen. Im Abschnitt Placement platziert der Code die Gruppe mit den vier spaltigen Führungs Befehlen in diesem Untermenü.

**Befehls Abschnitt, Schaltflächen Definitionen**. Der Abschnitt "Befehle" definiert dann die Menü Elemente oder Schaltflächen, die die vier spaltigen Befehle sind. `CommandWellOnly`, wie oben erläutert, bedeutet, dass die Befehle unsichtbar sind, wenn Sie in einem Hauptmenü abgelegt werden. Zwei der Schaltflächen Deklarationen für Menü Elemente (Leitfaden zum Hinzufügen und entfernen) haben ebenfalls ein `AllowParams` Flag:

```xml
<CommandFlag>AllowParams</CommandFlag>
```

Dieses Flag ermöglicht, zusammen mit der Platzierung von Hauptmenü-Menüs, den Befehl, Argumente zu empfangen, wenn Visual Studio den Befehls Handler aufruft.  Wenn der Benutzer den Befehl im Befehlsfenster ausführt, wird das Argument in den Ereignis Argumenten an den Befehls Handler übermittelt.

**Befehls Abschnitte, Bitmaps-Definitionen**. Schließlich werden im Abschnitt "Befehle" die Bitmaps oder Symbole deklariert, die für die Befehle verwendet werden. Bei diesem Abschnitt handelt es sich um eine einfache Deklaration, die die Projekt Ressource identifiziert und einbasierte Indizes von verwendeten Symbolen auflistet. Der Abschnitt "Symbole" der *vsct* -Datei deklariert die Werte der Bezeichner, die als Indizes verwendet werden. Diese exemplarische Vorgehensweise verwendet den bitmapstrip, der mit der dem Projekt hinzugefügten benutzerdefinierten Befehls Element Vorlage bereitgestellt wird.

**Platzierungs Abschnitt**. Der Abschnitt "Befehle" ist der Abschnitt "Placement". Der erste Punkt, in dem der Code die oben erörterte erste Gruppe hinzufügt, die die vier spaltigen Führungs Befehle enthält, wird im Untermenü angezeigt, in dem die Befehle angezeigt werden:

```xml
<CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
                  priority="0x0100">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />
</CommandPlacement>
```

Alle anderen Platzierungs Platzierungen fügen den `GuidesContextMenuGroup` (der das enthält `GuidesSubMenu` ) zu anderen Editor-Kontextmenüs hinzu. Wenn der Code den deklariert `GuidesContextMenuGroup` hat, wurde er dem Kontextmenü des Code-Editors übergeordnet. Aus diesem Grund wird eine Platzierung für das Kontextmenü des Code-Editors nicht angezeigt.

**Abschnitt "Symbole**". Wie oben bereits erwähnt, deklariert der Abschnitt "Symbole" Bezeichner, die an anderer Stelle in der *vsct* -Datei verwendet werden, wodurch der *vsct* -Code besser lesbar ist als bei allen GUIDs und hexadezimal Zahlen. Die wichtigen Punkte in diesem Abschnitt bestehen darin, dass der Paket-GUID mit der Deklaration in der Paket Klasse übereinstimmen muss. Und die Befehlssatz-GUID muss mit der Deklaration in der Befehls Implementierungs Klasse übereinstimmen.

## <a name="implement-the-commands"></a>Implementieren der Befehle
Die Datei *ColumnGuideCommands.cs* implementiert die Befehle und verknüpft die Handler. Wenn Visual Studio das Paket lädt und es initialisiert, ruft das Paket wiederum `Initialize` die Implementierungs Klasse der Befehle auf. Die Initialisierung der Befehle instanziiert einfach die-Klasse, und der-Konstruktor verknüpft alle Befehls Handler.

Ersetzen Sie den Inhalt der *ColumnGuideCommands.cs* -Datei durch den folgenden Code (unten erläutert):

```csharp
using System;
using System.ComponentModel.Design;
using System.Globalization;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Interop;
using Microsoft.VisualStudio.TextManager.Interop;
using Microsoft.VisualStudio.Text.Editor;
using Microsoft.VisualStudio;

namespace ColumnGuides
{
    /// <summary>
    /// Command handler
    /// </summary>
    internal sealed class ColumnGuideCommands
    {

        const int cmdidAddColumnGuide = 0x0100;
        const int cmdidRemoveColumnGuide = 0x0101;
        const int cmdidChooseGuideColor = 0x0102;
        const int cmdidRemoveAllColumnGuides = 0x0103;

        /// <summary>
        /// Command menu group (command set GUID).
        /// </summary>
        static readonly Guid CommandSet =
            new Guid("c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e");

        /// <summary>
        /// VS Package that provides this command, not null.
        /// </summary>
        private readonly Package package;

        OleMenuCommand _addGuidelineCommand;
        OleMenuCommand _removeGuidelineCommand;

        /// <summary>
        /// Initializes the singleton instance of the command.
        /// </summary>
        /// <param name="package">Owner package, not null.</param>
        public static void Initialize(Package package)
        {
            Instance = new ColumnGuideCommands(package);
        }

        /// <summary>
        /// Gets the instance of the command.
        /// </summary>
        public static ColumnGuideCommands Instance
        {
            get;
            private set;
        }

        /// <summary>
        /// Initializes a new instance of the <see cref="ColumnGuideCommands"/> class.
        /// Adds our command handlers for menu (commands must exist in the command
        /// table file)
        /// </summary>
        /// <param name="package">Owner package, not null.</param>
        private ColumnGuideCommands(Package package)
        {
            if (package == null)
            {
                throw new ArgumentNullException("package");
            }

            this.package = package;

            // Add our command handlers for menu (commands must exist in the .vsct file)

            OleMenuCommandService commandService =
                this.ServiceProvider.GetService(typeof(IMenuCommandService))
                    as OleMenuCommandService;
            if (commandService != null)
            {
                // Add guide
                _addGuidelineCommand =
                    new OleMenuCommand(AddColumnGuideExecuted, null,
                                       AddColumnGuideBeforeQueryStatus,
                                       new CommandID(ColumnGuideCommands.CommandSet,
                                                     cmdidAddColumnGuide));
                _addGuidelineCommand.ParametersDescription = "<column>";
                commandService.AddCommand(_addGuidelineCommand);
                // Remove guide
                _removeGuidelineCommand =
                    new OleMenuCommand(RemoveColumnGuideExecuted, null,
                                       RemoveColumnGuideBeforeQueryStatus,
                                       new CommandID(ColumnGuideCommands.CommandSet,
                                                     cmdidRemoveColumnGuide));
                _removeGuidelineCommand.ParametersDescription = "<column>";
                commandService.AddCommand(_removeGuidelineCommand);
                // Choose color
                commandService.AddCommand(
                    new MenuCommand(ChooseGuideColorExecuted,
                                    new CommandID(ColumnGuideCommands.CommandSet,
                                                  cmdidChooseGuideColor)));
                // Remove all
                commandService.AddCommand(
                    new MenuCommand(RemoveAllGuidelinesExecuted,
                                    new CommandID(ColumnGuideCommands.CommandSet,
                                                  cmdidRemoveAllColumnGuides)));
            }
        }

        /// <summary>
        /// Gets the service provider from the owner package.
        /// </summary>
        private IServiceProvider ServiceProvider
        {
            get
            {
                return this.package;
            }
        }

        private void AddColumnGuideBeforeQueryStatus(object sender, EventArgs e)
        {
            int currentColumn = GetCurrentEditorColumn();
            _addGuidelineCommand.Enabled =
                GuidesSettingsManager.CanAddGuideline(currentColumn);
        }

        private void RemoveColumnGuideBeforeQueryStatus(object sender, EventArgs e)
        {
            int currentColumn = GetCurrentEditorColumn();
            _removeGuidelineCommand.Enabled =
                GuidesSettingsManager.CanRemoveGuideline(currentColumn);
        }

        private int GetCurrentEditorColumn()
        {
            IVsTextView view = GetActiveTextView();
            if (view == null)
            {
                return -1;
            }

            try
            {
                IWpfTextView textView = GetTextViewFromVsTextView(view);
                int column = GetCaretColumn(textView);

                // Note: GetCaretColumn returns 0-based positions. Guidelines are 1-based
                // positions.
                // However, do not subtract one here since the caret is positioned to the
                // left of
                // the given column and the guidelines are positioned to the right. We
                // want the
                // guideline to line up with the current caret position. e.g. When the
                // caret is
                // at position 1 (zero-based), the status bar says column 2. We want to
                // add a
                // guideline for column 1 since that will place the guideline where the
                // caret is.
                return column;
            }
            catch (InvalidOperationException)
            {
                return -1;
            }
        }

        /// <summary>
        /// Find the active text view (if any) in the active document.
        /// </summary>
        /// <returns>The IVsTextView of the active view, or null if there is no active
        /// document or the
        /// active view in the active document is not a text view.</returns>
        private IVsTextView GetActiveTextView()
        {
            IVsMonitorSelection selection =
                this.ServiceProvider.GetService(typeof(IVsMonitorSelection))
                                                    as IVsMonitorSelection;
            object frameObj = null;
            ErrorHandler.ThrowOnFailure(
                selection.GetCurrentElementValue(
                    (uint)VSConstants.VSSELELEMID.SEID_DocumentFrame, out frameObj));

            IVsWindowFrame frame = frameObj as IVsWindowFrame;
            if (frame == null)
            {
                return null;
            }

            return GetActiveView(frame);
        }

        private static IVsTextView GetActiveView(IVsWindowFrame windowFrame)
        {
            if (windowFrame == null)
            {
                throw new ArgumentException("windowFrame");
            }

            object pvar;
            ErrorHandler.ThrowOnFailure(
                windowFrame.GetProperty((int)__VSFPROPID.VSFPROPID_DocView, out pvar));

            IVsTextView textView = pvar as IVsTextView;
            if (textView == null)
            {
                IVsCodeWindow codeWin = pvar as IVsCodeWindow;
                if (codeWin != null)
                {
                    ErrorHandler.ThrowOnFailure(codeWin.GetLastActiveView(out textView));
                }
            }
            return textView;
        }

        private static IWpfTextView GetTextViewFromVsTextView(IVsTextView view)
        {

            if (view == null)
            {
                throw new ArgumentNullException("view");
            }

            IVsUserData userData = view as IVsUserData;
            if (userData == null)
            {
                throw new InvalidOperationException();
            }

            object objTextViewHost;
            if (VSConstants.S_OK
                   != userData.GetData(Microsoft.VisualStudio
                                                .Editor
                                                .DefGuidList.guidIWpfTextViewHost,
                                       out objTextViewHost))
            {
                throw new InvalidOperationException();
            }

            IWpfTextViewHost textViewHost = objTextViewHost as IWpfTextViewHost;
            if (textViewHost == null)
            {
                throw new InvalidOperationException();
            }

            return textViewHost.TextView;
        }

        /// <summary>
        /// Given an IWpfTextView, find the position of the caret and report its column
        /// number. The column number is 0-based
        /// </summary>
        /// <param name="textView">The text view containing the caret</param>
        /// <returns>The column number of the caret's position. When the caret is at the
        /// leftmost column, the return value is zero.</returns>
        private static int GetCaretColumn(IWpfTextView textView)
        {
            // This is the code the editor uses to populate the status bar.
            Microsoft.VisualStudio.Text.Formatting.ITextViewLine caretViewLine =
                textView.Caret.ContainingTextViewLine;
            double columnWidth = textView.FormattedLineSource.ColumnWidth;
            return (int)(Math.Round((textView.Caret.Left - caretViewLine.Left)
                                       / columnWidth));
        }

        /// <summary>
        /// Determine the applicable column number for an add or remove command.
        /// The column is parsed from command arguments, if present. Otherwise
        /// the current position of the caret is used to determine the column.
        /// </summary>
        /// <param name="e">Event args passed to the command handler.</param>
        /// <returns>The column number. May be negative to indicate the column number is
        /// unavailable.</returns>
        /// <exception cref="ArgumentException">The column number parsed from event args
        /// was not a valid integer.</exception>
        private int GetApplicableColumn(EventArgs e)
        {
            var inValue = ((OleMenuCmdEventArgs)e).InValue as string;
            if (!string.IsNullOrEmpty(inValue))
            {
                int column;
                if (!int.TryParse(inValue, out column) || column < 0)
                    throw new ArgumentException("Invalid column");
                return column;
            }

            return GetCurrentEditorColumn();
        }

        /// <summary>
        /// This function is the callback used to execute a command when the a menu item
        /// is clicked. See the Initialize method to see how the menu item is associated
        /// to this function using the OleMenuCommandService service and the MenuCommand
        /// class.
        /// </summary>
        private void AddColumnGuideExecuted(object sender, EventArgs e)
        {
            int column = GetApplicableColumn(e);
            if (column >= 0)
            {
                GuidesSettingsManager.AddGuideline(column);
            }
        }

        private void RemoveColumnGuideExecuted(object sender, EventArgs e)
        {
            int column = GetApplicableColumn(e);
            if (column >= 0)
            {
                GuidesSettingsManager.RemoveGuideline(column);
            }
        }

        private void RemoveAllGuidelinesExecuted(object sender, EventArgs e)
        {
            GuidesSettingsManager.RemoveAllGuidelines();
        }

        private void ChooseGuideColorExecuted(object sender, EventArgs e)
        {
            System.Windows.Media.Color color = GuidesSettingsManager.GuidelinesColor;

            using (System.Windows.Forms.ColorDialog picker =
                new System.Windows.Forms.ColorDialog())
            {
                picker.Color = System.Drawing.Color.FromArgb(255, color.R, color.G,
                                                             color.B);
                if (picker.ShowDialog() == System.Windows.Forms.DialogResult.OK)
                {
                    GuidesSettingsManager.GuidelinesColor =
                        System.Windows.Media.Color.FromRgb(picker.Color.R,
                                                           picker.Color.G,
                                                           picker.Color.B);
                }
            }
        }

    }
}

```

**Korrektur von verweisen**. An dieser Stelle fehlt ein Verweis. Klicken Sie im Projektmappen-Explorer auf die Schaltfläche mit dem rechten Zeiger auf den Knoten Verweise. Wählen Sie den Befehl **hinzufügen...** aus. Das Dialogfeld **Verweis hinzufügen** enthält ein Suchfeld in der oberen rechten Ecke. Geben Sie "Editor" (ohne doppelte Anführungszeichen) ein. Wählen Sie das Element **Microsoft. VisualStudio. Editor** aus. (Sie müssen das Kontrollkästchen auf der linken Seite des Elements aktivieren, nicht nur das Element auswählen) und dann auf **OK** klicken, um den Verweis hinzuzufügen.

**Initialisierung**.  Wenn die Paket Klasse initialisiert, ruft Sie `Initialize` für die Implementierungs Klasse der Befehle auf. Die `ColumnGuideCommands` Initialisierung instanziiert die-Klasse und speichert die-Klasseninstanz und den Paket Verweis in Klassenmembern.

Sehen wir uns einen der Befehls Handler-Hook-ups aus dem Klassenkonstruktor an:

```csharp
_addGuidelineCommand =
    new OleMenuCommand(AddColumnGuideExecuted, null,
                       AddColumnGuideBeforeQueryStatus,
                       new CommandID(ColumnGuideCommands.CommandSet,
                                     cmdidAddColumnGuide));

```

Sie erstellen einen `OleMenuCommand` . Visual Studio verwendet das Befehlssystem Microsoft Office. Die wichtigsten Argumente beim Instanziieren eines `OleMenuCommand` ist die Funktion, die den Befehl implementiert ( `AddColumnGuideExecuted` ), die Funktion, die aufgerufen werden soll, wenn Visual Studio ein Menü mit dem Befehl ( `AddColumnGuideBeforeQueryStatus` ) und der Befehls-ID anzeigt. Visual Studio Ruft die Abfrage Status Funktion auf, bevor ein Befehl in einem Menü angezeigt wird, sodass der Befehl für eine bestimmte Anzeige des Menüs unsichtbar oder abgeblendet werden kann (z. b. beim Deaktivieren der **Kopie** , wenn keine Auswahl vorhanden ist), dessen Symbol geändert wird oder sogar den Namen ändert (z. b. von etwas hinzufügen, um etwas zu entfernen) usw. Die Befehls-ID muss mit einer in der *vsct* -Datei deklarierten Befehls-ID identisch sein. Die Zeichen folgen für den Befehlssatz und der Befehl zum Hinzufügen von Spalten Handbüchern müssen mit der *vsct* -Datei und der *ColumnGuideCommands.cs*-Datei identisch sein.

Die folgende Zeile bietet Unterstützung für den Fall, dass Benutzer den Befehl über das Befehlsfenster aufrufen (siehe unten):

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";
```

 **Abfrage Status**. Die Abfrage Status Funktionen `AddColumnGuideBeforeQueryStatus` und `RemoveColumnGuideBeforeQueryStatus` überprüfen einige Einstellungen (z. b. die maximale Anzahl von Führungslinien oder eine maximale Spalten Anzahl) oder, wenn ein zu entfern Endes Spalten Handbuch vorhanden ist. Sie aktivieren die Befehle, wenn die Bedingungen richtig sind.  Abfrage Status Funktionen müssen effizient sein, da Sie jedes Mal ausgeführt werden, wenn Visual Studio ein Menü und für jeden Befehl im Menü anzeigt.

 **Addcolumnguideausgeführte Funktion**. Der interessante Teil des Hinzufügens eines Handbuchs besteht darin, die aktuelle Editor-Ansicht und die Position der Einfügemarke zu ermitteln.  Zuerst ruft diese Funktion `GetApplicableColumn` auf, die überprüft, ob ein vom Benutzer bereitgestelltes Argument in den Ereignis Argumenten des Befehls Handlers vorhanden ist. wenn keine vorhanden ist, überprüft die Funktion die Ansicht des Editors:

```csharp
private int GetApplicableColumn(EventArgs e)
{
    var inValue = ((OleMenuCmdEventArgs)e).InValue as string;
    if (!string.IsNullOrEmpty(inValue))
    {
        int column;
        if (!int.TryParse(inValue, out column) || column < 0)
            throw new ArgumentException("Invalid column");
        return column;
    }

    return GetCurrentEditorColumn();
}

```

`GetCurrentEditorColumn` muss ein wenig kennenlernen, um eine <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> Ansicht des Codes zu erhalten.  Wenn Sie die Ablauf Verfolgung durch `GetActiveTextView` , `GetActiveView` und durch `GetTextViewFromVsTextView` führen, sehen Sie, wie Sie dies tun können. Der folgende Code ist der relevante Code, der mit der aktuellen Auswahl abstrahiert wird, anschließend den Rahmen der Auswahl erhält und dann die DocView des Frames als erhält. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> anschließend erhält er eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> aus der IVsTextView und erhält dann einen Ansichts Host und schließlich die iwpftextview:

```csharp
   IVsMonitorSelection selection =
       this.ServiceProvider.GetService(typeof(IVsMonitorSelection))
           as IVsMonitorSelection;
   object frameObj = null;

ErrorHandler.ThrowOnFailure(selection.GetCurrentElementValue(
                                (uint)VSConstants.VSSELELEMID.SEID_DocumentFrame,
                                out frameObj));

   IVsWindowFrame frame = frameObj as IVsWindowFrame;
   if (frame == null)
       <<do nothing>>;

...
   object pvar;
   ErrorHandler.ThrowOnFailure(frame.GetProperty((int)__VSFPROPID.VSFPROPID_DocView,
                                                  out pvar));

   IVsTextView textView = pvar as IVsTextView;
   if (textView == null)
   {
       IVsCodeWindow codeWin = pvar as IVsCodeWindow;
       if (codeWin != null)
       {
           ErrorHandler.ThrowOnFailure(codeWin.GetLastActiveView(out textView));
       }
   }

...
   if (textView == null)
       <<do nothing>>

   IVsUserData userData = textView as IVsUserData;
   if (userData == null)
       <<do nothing>>

   object objTextViewHost;
   if (VSConstants.S_OK
           != userData.GetData(Microsoft.VisualStudio.Editor.DefGuidList
                                                            .guidIWpfTextViewHost,
                                out objTextViewHost))
   {
       <<do nothing>>
   }

   IWpfTextViewHost textViewHost = objTextViewHost as IWpfTextViewHost;
   if (textViewHost == null)
       <<do nothing>>

   IWpfTextView textView = textViewHost.TextView;

```

Sobald Sie über eine iwpftextview verfügen, können Sie die Spalte erhalten, in der sich die Einfügemarke befindet:

```csharp
private static int GetCaretColumn(IWpfTextView textView)
{
    // This is the code the editor uses to populate the status bar.
    Microsoft.VisualStudio.Text.Formatting.ITextViewLine caretViewLine =
        textView.Caret.ContainingTextViewLine;
    double columnWidth = textView.FormattedLineSource.ColumnWidth;
    return (int)(Math.Round((textView.Caret.Left - caretViewLine.Left)
                                / columnWidth));
}

```

Mit der aktuellen Spalte, auf die der Benutzer geklickt hat, ruft der Code nur im Einstellungs-Manager auf, um die Spalte hinzuzufügen oder zu entfernen. Der Einstellungs-Manager löst das Ereignis aus, auf das alle `ColumnGuideAdornment` Objekte lauschen. Wenn das Ereignis ausgelöst wird, aktualisieren diese Objekte ihre zugeordneten Text Ansichten mit neuen Spalten Leit Faden Einstellungen.

## <a name="invoke-command-from-the-command-window"></a>Befehl "aufrufen" im Befehlsfenster
Im Beispiel mit den Spalten Handbüchern können Benutzer zwei Befehle im Befehlsfenster als Erweiterbarkeits Form aufrufen. Wenn Sie den Befehl **&#124; anderen Windows &#124; Befehlsfenster anzeigen** verwenden, wird das Befehlsfenster angezeigt. Sie können mit dem Befehlsfenster interagieren, indem Sie "Bearbeiten" eingeben, und mit dem Abschluss des Befehlsnamens und der Angabe des Arguments 120 haben Sie folgendes Ergebnis:

```csharp
> Edit.AddColumnGuide 120
>
```

Die Teile des Beispiels, die dieses Verhalten ermöglichen, sind in den *vsct* -Datei Deklarationen, dem `ColumnGuideCommands` Klassenkonstruktor, wenn er Befehls Handler anbindet, und den befehlshandlerimplementierungen, die Ereignis Argumente überprüfen.

Sie haben " `<CommandFlag>CommandWellOnly</CommandFlag>` " in der *vsct* -Datei und im Menü " **Bearbeiten** " angezeigt, obwohl die Befehle nicht in der Benutzeroberfläche des **Bearbeitungs** Menüs angezeigt werden. Wenn Sie diese im Hauptmenü **Bearbeiten** , haben Sie Namen wie **Edit. addcolumnguide**. Die Befehls Gruppen Deklaration, die die vier Befehle enthält, hat die Gruppe direkt im Menü **Bearbeiten** platziert:

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
             priority="0xB801">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />
      </Group>

```

Der Schaltflächen Abschnitt hat später die Befehle deklariert `CommandWellOnly` , damit Sie im Hauptmenü unsichtbar bleiben und mit deklariert werden `AllowParams` :

```xml
<Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"
        priority="0x0100" type="Button">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
  <Icon guid="guidImages" id="bmpPicAddGuide" />
  <CommandFlag>CommandWellOnly</CommandFlag>
  <CommandFlag>AllowParams</CommandFlag>

```

Sie haben gesehen, dass der Befehls Handler-Hook-Code im `ColumnGuideCommands` Klassenkonstruktor eine Beschreibung des zulässigen Parameters bereitgestellt hat:

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";

```

Sie haben gesehen, `GetApplicableColumn` dass die Funktion `OleMenuCmdEventArgs` auf einen Wert überprüft, bevor die Ansicht des Editors für eine aktuelle Spalte überprüft wird:

```csharp
private int GetApplicableColumn(EventArgs e)
{
    var inValue = ((OleMenuCmdEventArgs)e).InValue as string;
    if (!string.IsNullOrEmpty(inValue))
    {
        int column;
        if (!int.TryParse(inValue, out column) || column < 0)
            throw new ArgumentException("Invalid column");
        return column;
    }

```

## <a name="try-your-extension"></a>Testen Sie Ihre Erweiterung
Sie können jetzt **F5** drücken, um die Erweiterung für die Spalten Handbücher auszuführen. Öffnen Sie eine Textdatei, und verwenden Sie das Kontextmenü des Editors, um Führungslinien hinzuzufügen, zu entfernen und ihre Farbe zu ändern. Klicken Sie in den Text (kein Leerzeichen, das das Ende der Zeile überschritten hat), um ein Spalten Handbuch hinzuzufügen, oder der Editor fügt es der letzten Spalte in der Zeile hinzu. Wenn Sie das Befehlsfenster verwenden und die Befehle mit einem Argument aufrufen, können Sie an jedem beliebigen Ort Spalten Handbücher hinzufügen.

Wenn Sie verschiedene Befehls Platzierungen ausprobieren, Namen ändern, Symbole ändern usw. und Probleme mit Visual Studio haben, in denen der aktuelle Code in Menüs angezeigt wird, können Sie die experimentelle Struktur zurücksetzen, in der Sie Debuggen. Öffnen Sie das **Windows-Startmenü** , und geben Sie "Reset" ein. Suchen und führen Sie den Befehl aus, und **setzen Sie die nächste experimentelle Instanz von Visual Studio zurück**. Mit diesem Befehl wird die experimentelle Registrierungs Struktur aller Erweiterungs Komponenten bereinigt. Die Einstellungen der Komponenten werden nicht bereinigt, sodass alle Handbücher, die Sie beim Herunterfahren der experimentellen Struktur von Visual Studio verwendet haben, noch dort vorhanden sind, wenn Ihr Code beim nächsten Start den Einstellungs Speicher liest.

## <a name="finished-code-project"></a>Fertiggestelltes Code Projekt
In Kürze wird ein GitHub-Projekt mit Visual Studio-Erweiterbarkeits Beispielen angezeigt, und das fertige Projekt ist vorhanden. Dieser Artikel wird aktualisiert, um darauf zu verweisen, wenn dies geschieht. Das abgeschlossene Beispiel Projekt weist möglicherweise unterschiedliche GUIDs auf und hat für die Befehls Symbole einen anderen bitmapstrip.

Sie können eine Version der Column Guides-Funktion mit dieser Visual Studio Gallery-[Erweiterung](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines)ausprobieren.

## <a name="see-also"></a>Weitere Informationen
- [Innerhalb des Editors](../extensibility/inside-the-editor.md)
- [Erweitern des Editors und der Sprachdienste](../extensibility/extending-the-editor-and-language-services.md)
- [Sprachdienst-und Editor-Erweiterungs Punkte](../extensibility/language-service-and-editor-extension-points.md)
- [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md)
- [Hinzufügen eines Untermenüs zu einem Menü](../extensibility/adding-a-submenu-to-a-menu.md)
- [Erstellen einer Erweiterung mit einer Editor-Element Vorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md)
