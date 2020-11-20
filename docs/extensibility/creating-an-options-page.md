---
title: Erstellen einer Options Seite | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eine einfache Seite "Tools/Optionen" erstellen, die ein Eigenschaften Raster zum Überprüfen und Festlegen von Eigenschaften verwendet.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 41102dfbbf1e49dadb1360ab0182810a47651dca
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2020
ms.locfileid: "94973720"
---
# <a name="create-an-options-page"></a>Erstellen einer Optionsseite

In dieser exemplarischen Vorgehensweise wird eine einfache Seite Extras/Optionen erstellt, die ein Eigenschaften Raster zum Überprüfen und Festlegen von Eigenschaften verwendet.

 Führen Sie die folgenden Schritte aus, um diese Eigenschaften in einer Einstellungsdatei zu speichern und wiederherzustellen. Weitere Informationen finden Sie unter [Erstellen einer Einstellungs Kategorie](../extensibility/creating-a-settings-category.md).

 Das MPF bietet zwei Klassen, die Sie beim Erstellen von Tools-Optionen-Seiten, der <xref:Microsoft.VisualStudio.Shell.Package> -Klasse und der-Klasse unterstützen <xref:Microsoft.VisualStudio.Shell.DialogPage> . Sie erstellen ein VSPackage, um einen Container für diese Seiten bereitzustellen, indem Sie die Klasse Unterklassen `Package` . Sie erstellen jede Tool Optionsseite durch Ableiten von der- `DialogPage` Klasse.

## <a name="prerequisites"></a>Voraussetzungen

 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Sie ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-tools-options-grid-page"></a>Erstellen einer Raster Seite für Extras-Optionen

 In diesem Abschnitt erstellen Sie das Eigenschaften Raster einfache Tools-Optionen. Sie verwenden dieses Raster, um den Wert einer Eigenschaft anzuzeigen und zu ändern.

### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>So erstellen Sie das VSIX-Projekt und fügen ein VSPackage hinzu

1. Jede Visual Studio-Erweiterung beginnt mit einem VSIX-Bereitstellungs Projekt, das die Erweiterungs Ressourcen enthält. Erstellen Sie ein [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX-Projekt mit dem Namen `MyToolsOptionsExtension` . Sie finden die VSIX-Projektvorlage im Dialogfeld " **Neues Projekt** ", indem Sie nach "VSIX" suchen.

2. Fügen Sie ein VSPackage hinzu, indem Sie eine Visual Studio-Paket Element Vorlage namens hinzufügen `MyToolsOptionsPackage` . Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie **Add**  >  **Neues Element** hinzufügen aus. Navigieren Sie im **Dialogfeld Neues Element hinzufügen** zu **Visual c# Elemente**  >  **Erweiterbarkeit** , und wählen Sie dann **Visual Studio-Paket** aus. Ändern Sie im Feld **Name** am unteren Rand des Dialog Felds den Dateinamen in `MyToolsOptionsPackage.cs` . Weitere Informationen zum Erstellen eines VSPackage finden Sie unter [Erstellen einer Erweiterung mit einem VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md).

### <a name="to-create-the-tools-options-property-grid"></a>So erstellen Sie das Eigenschaften Raster "Extras Optionen"

1. Öffnen Sie im Code-Editor die Datei " *mytoolsoptionspackage* ".

2. Fügen Sie die folgende using-Anweisung hinzu.

   ```csharp
   using System.ComponentModel;
   ```

3. Deklarieren `OptionPageGrid` Sie eine-Klasse und leiten Sie von ab <xref:Microsoft.VisualStudio.Shell.DialogPage> .

   ```csharp
   public class OptionPageGrid : DialogPage
   {  }
   ```

4. Wenden Sie einen <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> auf die `VSPackage` Klasse an, die der Klasse eine Options Kategorie und einen Options Seitennamen für das OptionPageGrid zuweisen soll. Das Ergebnis sollte wie folgt aussehen:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [Guid(GuidList.guidMyToolsOptionsPkgString)]
    [ProvideOptionPage(typeof(OptionPageGrid),
        "My Category", "My Grid Page", 0, 0, true)]
    public sealed class MyToolsOptionsPackage : Package
    ```

5. Fügen Sie `OptionInteger` der-Klasse eine-Eigenschaft hinzu `OptionPageGrid` .

    - Wenden <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> Sie einen an, der der Eigenschaft eine Eigenschaften Raster Kategorie zugewiesen werden soll.

    - Wenden <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> Sie einen an, um der Eigenschaft einen Namen zuzuweisen.

    - Anwenden eines <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> , das der Eigenschaft eine Beschreibung zugewiesen werden soll.

    ```csharp
    public class OptionPageGrid : DialogPage
    {
        private int optionInt = 256;

        [Category("My Category")]
        [DisplayName("My Integer Option")]
        [Description("My integer option")]
        public int OptionInteger
        {
            get { return optionInt; }
            set { optionInt = value; }
        }
    }
    ```

    > [!NOTE]
    > Die Standard Implementierung von <xref:Microsoft.VisualStudio.Shell.DialogPage> unterstützt Eigenschaften mit entsprechenden Konvertern oder Strukturen oder Arrays, die in Eigenschaften erweitert werden können, die über entsprechende Konverter verfügen. Eine Liste der Konverter finden Sie unter dem- <xref:System.ComponentModel> Namespace.

6. Erstellen Sie das Projekt, und starten Sie das Debugging.

7. Klicken Sie in der experimentellen Instanz von Visual Studio im **Menü Extras** auf **Optionen**.

     Im linken Bereich sollte **Meine Kategorie** angezeigt werden. (Kategorien von Optionen sind in alphabetischer Reihenfolge aufgelistet, sodass Sie ungefähr in der Mitte der Liste angezeigt werden.) Öffnen Sie **Meine Kategorie** , und klicken Sie dann auf **meine Raster Seite**. Das Raster Optionen wird im rechten Bereich angezeigt. Die Eigenschaften Kategorie ist **meine Optionen**, und der Eigenschaftsname ist **meine ganzzahlige Option**. Die Eigenschafts Beschreibung, **meine ganzzahlige Option**, wird am unteren Rand des Bereichs angezeigt. Ändern Sie den Wert von seinem Anfangswert von 256 in etwas anderes. Klicken Sie auf **OK**, und öffnen Sie die **Raster Seite** erneut. Sie können sehen, dass der neue Wert weiterhin besteht.

     Die Seite "Optionen" steht auch über das Suchfeld von Visual Studio zur Verfügung. Geben Sie im Suchfeld am oberen Rand der IDE **Meine Kategorie** ein, und Sie sehen die **Kategorie > meine Raster Seite** , die in den Ergebnissen aufgeführt ist.

## <a name="create-a-tools-options-custom-page"></a>Erstellen einer benutzerdefinierten Seite "Extras"

 In diesem Abschnitt erstellen Sie eine Extras Options Seite mit einer benutzerdefinierten Benutzeroberfläche. Auf dieser Seite können Sie den Wert einer Eigenschaft anzeigen und ändern.

1. Öffnen Sie im Code-Editor die Datei " *mytoolsoptionspackage* ".

2. Fügen Sie die folgende using-Anweisung hinzu.

    ```csharp
    using System.Windows.Forms;
    ```

3. Fügen Sie eine- `OptionPageCustom` Klasse hinzu, direkt vor der- `OptionPageGrid` Klasse. Leiten Sie die neue Klasse von ab `DialogPage` .

    ```csharp
    public class OptionPageCustom : DialogPage
    {
        private string optionValue = "alpha";

        public string OptionString
        {
            get { return optionValue; }
            set { optionValue = value; }
        }
    }
    ```

4. Fügen Sie ein GUID-Attribut hinzu. Optionstring-Eigenschaft hinzufügen:

    ```csharp
    [Guid("00000000-0000-0000-0000-000000000000")]
    public class OptionPageCustom : DialogPage
    {
        private string optionValue = "alpha";

        public string OptionString
        {
            get { return optionValue; }
            set { optionValue = value; }
        }
    }
    ```

5. Wenden Sie ein zweites <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> auf die VSPackage-Klasse an. Dieses Attribut weist der-Klasse eine Options Kategorie und einen Options Seitennamen zu.

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [Guid(GuidList.guidMyToolsOptionsPkgString)]
    [ProvideOptionPage(typeof(OptionPageGrid),
        "My Category", "My Grid Page", 0, 0, true)]
    [ProvideOptionPage(typeof(OptionPageCustom),
        "My Category", "My Custom Page", 0, 0, true)]
    public sealed class MyToolsOptionsPackage : Package
    ```

6. Fügen Sie dem Projekt ein neues **Benutzer Steuer** Element mit dem Namen "MyUserControl" hinzu.

7. Fügen Sie dem Benutzer Steuerelement ein **TextBox** -Steuerelement hinzu.

     Klicken Sie im Fenster **Eigenschaften** auf der Symbolleiste auf die Schaltfläche **Ereignisse** , und doppelklicken Sie dann auf das **Leave** -Ereignis. Der neue Ereignishandler wird im *MyUserControl.cs* -Code angezeigt.

8. Fügen Sie `OptionsPage` der Steuerelement Klasse ein öffentliches Feld, eine `Initialize` Methode hinzu, und aktualisieren Sie den Ereignishandler, um den Optionswert auf den Inhalt des Textfelds festzulegen:

    ```csharp
    public partial class MyUserControl : UserControl
    {
        public MyUserControl()
        {
            InitializeComponent();
        }

        internal OptionPageCustom optionsPage;

        public void Initialize()
        {
            textBox1.Text = optionsPage.OptionString;
        }

        private void textBox1_Leave(object sender, EventArgs e)
        {
            optionsPage.OptionString = textBox1.Text;
        }
    }
    ```

     Das `optionsPage` Feld enthält einen Verweis auf die übergeordnete `OptionPageCustom` Instanz. Die- `Initialize` Methode wird `OptionString` im **Textfeld** angezeigt. Der-Ereignishandler schreibt den aktuellen Wert des **Textfelds** in den, `OptionString` Wenn der Fokus das **Textfeld** verlässt.

9. Fügen Sie der-Klasse in der Paket Code Datei eine außer Kraft setzung für die `OptionPageCustom.Window` -Eigenschaft hinzu, `OptionPageCustom` um eine Instanz von zu erstellen, zu initialisieren und zurückzugeben `MyUserControl` . Die Klasse sollte nun wie folgt aussehen:

    ```csharp
    [Guid("00000000-0000-0000-0000-000000000000")]
    public class OptionPageCustom : DialogPage
    {
        private string optionValue = "alpha";

        public string OptionString
        {
            get { return optionValue; }
            set { optionValue = value; }
        }

        protected override IWin32Window Window
        {
            get
            {
                MyUserControl page = new MyUserControl();
                page.optionsPage = this;
                page.Initialize();
                return page;
            }
        }
    }
    ```

10. Erstellen Sie das Projekt, und führen Sie es aus.

11. **Klicken Sie** in der experimentellen Instanz auf Extras  >  **Optionen**.

12. **Meine Kategorie** und dann **meine benutzerdefinierte Seite** suchen.

13. Ändern Sie den Wert von **optionstring**. Klicken Sie auf **OK**, und öffnen Sie dann die **benutzerdefinierte Seite** erneut. Sie können sehen, dass der neue Wert persistent ist.

## <a name="access-options"></a>Zugriffs Optionen

 In diesem Abschnitt erhalten Sie den Wert einer Option aus dem VSPackage, das die zugehörige Optionsseite Extras hostet. Das gleiche Verfahren kann verwendet werden, um den Wert einer beliebigen öffentlichen Eigenschaft abzurufen.

1. Fügen Sie in der Paket Code Datei der **mytoolsoptionspackage** -Klasse eine öffentliche Eigenschaft mit dem Namen " **OptionInteger** " hinzu.

    ```csharp
    public int OptionInteger
    {
        get
        {
            OptionPageGrid page = (OptionPageGrid)GetDialogPage(typeof(OptionPageGrid));
            return page.OptionInteger;
        }
    }

    ```

     Dieser Code ruft <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> auf, um eine-Instanz zu erstellen oder abzurufen `OptionPageGrid` . `OptionPageGrid` Ruft <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> auf, um die Optionen zu laden, die öffentliche Eigenschaften sind.

2. Fügen Sie nun eine benutzerdefinierte Befehls Element Vorlage mit dem Namen **mytoolsoptionscommand** hinzu, um den Wert anzuzeigen. Navigieren Sie im Dialogfeld **Neues Element hinzufügen** zu **Visual c#**  >  -**Erweiterbarkeit** , und wählen Sie **benutzerdefinierter Befehl** aus. Ändern Sie im Feld **Name** am unteren Rand des Fensters den Namen der Befehlsdatei in *MyToolsOptionsCommand.cs*.

3. Ersetzen Sie in der Datei *mytoolsoptionscommand* den Text der-Methode des Befehls `ShowMessageBox` durch Folgendes:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));
    }

    ```

4. Erstellen Sie das Projekt, und starten Sie das Debugging.

5. Klicken Sie **in der experimentellen Instanz im Menü Extras** auf **mytoolsoptionscommand aufrufen**.

     Ein Meldungs Feld zeigt den aktuellen Wert von an `OptionInteger` .

## <a name="see-also"></a>Weitere Informationen:

- [Optionen und Options Seiten](../extensibility/internals/options-and-options-pages.md)
