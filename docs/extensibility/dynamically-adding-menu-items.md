---
title: Dynamisches Hinzufügen von Menü Elementen | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie das dynamicitemstart-Befehlsflag verwenden, um zur Laufzeit Menü Elemente hinzuzufügen. In diesem Artikel wird gezeigt, wie das Startprojekt in einer Visual Studio-Projekt Mappe festgelegt wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DYNAMICITEMSTART
- menu items, adding dynamically
- menus, adding dynamic items
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81fd495c51eff456f66275f33876038d14e43203
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994809"
---
# <a name="dynamically-add-menu-items"></a>Dynamisches Hinzufügen von Menü Elementen
Sie können Menü Elemente zur Laufzeit hinzufügen, indem Sie das `DynamicItemStart` Befehlsflag in einer Platzhalter-Schaltflächen Definition in der Visual Studio-Befehls Tabellen Datei (*vsct*-Datei) angeben und dann (im Code) die Anzahl der Menü Elemente definieren, die angezeigt und mit den Befehlen verarbeitet werden sollen. Wenn das VSPackage geladen wird, wird der Platzhalter durch die dynamischen Menü Elemente ersetzt.

 Visual Studio verwendet dynamische Listen in der Liste der zuletzt **verwendeten** (MRU), in der die Namen von Dokumenten angezeigt werden, die vor kurzem geöffnet wurden, und die **Windows** -Liste, in der die Namen von Fenstern angezeigt werden, die derzeit geöffnet sind.   Das `DynamicItemStart` Flag für eine Befehls Definition gibt an, dass der Befehl ein Platzhalter ist, bis das VSPackage geöffnet ist. Wenn das VSPackage geöffnet ist, wird der Platzhalter durch 0 oder mehr Befehle ersetzt, die zur Laufzeit erstellt und der dynamischen Liste hinzugefügt werden. Möglicherweise ist es nicht möglich, die Position im Menü anzuzeigen, in der die dynamische Liste angezeigt wird, bis das VSPackage geöffnet ist.  Um die dynamische Liste aufzufüllen, fordert Visual Studio das VSPackage auf, einen Befehl mit einer ID zu suchen, deren erste Zeichen mit der ID des Platzhalters übereinstimmen. Wenn Visual Studio einen übereinstimmenden Befehl findet, wird der dynamische Liste der Name des Befehls hinzugefügt. Anschließend wird die ID erhöht und nach einem weiteren übereinstimmenden Befehl gesucht, der der dynamischen Liste hinzugefügt werden kann, bis keine dynamischen Befehle mehr vorhanden sind.

 In dieser exemplarischen Vorgehensweise wird gezeigt, wie das Startprojekt in einer Visual Studio-Projekt Mappe mit einem Befehl auf der **Projektmappen-Explorer** Symbolleiste festgelegt wird. Er verwendet einen Menü Controller, der über eine dynamische Dropdown Liste der Projekte in der aktiven Projekt Mappe verfügt. Um zu verhindern, dass dieser Befehl angezeigt wird, wenn keine Projekt Mappe geöffnet ist oder wenn die geöffnete Projekt Mappe nur ein Projekt enthält, wird das VSPackage nur geladen, wenn eine Projekt Mappe mehrere Projekte enthält.

 Weitere Informationen zu *vsct* -Dateien finden Sie unter [Visual Studio-Befehls Tabellen Dateien (vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

## <a name="create-an-extension-with-a-menu-command"></a>Erstellen einer Erweiterung mit einem Menübefehl

1. Erstellen Sie ein VSIX-Projekt mit dem Namen `DynamicMenuItems` .

2. Wenn das Projekt geöffnet wird, fügen Sie eine benutzerdefinierte Befehls Element Vorlage hinzu, und nennen Sie Sie **dynamicmenu**. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="setting-up-the-elements-in-the-vsct-file"></a>Einrichten der Elemente in der *vsct* -Datei
 Um einen Menü Controller mit dynamischen Menü Elementen auf einer Symbolleiste zu erstellen, geben Sie die folgenden Elemente an:

- Zwei Befehls Gruppen, eine mit dem Menü Controller und eine weitere, die die Menü Elemente in der Dropdown Liste enthält.

- Ein Menü Element vom Typ `MenuController`

- Zwei Schaltflächen, eine, die als Platzhalter für die Menü Elemente fungiert, und eine andere Schaltfläche, die das Symbol und die QuickInfo auf der Symbolleiste bereitstellt.

1. Definieren Sie in *dynamicmenupackage. vsct* die Befehls-IDs. Wechseln Sie zum Abschnitt "Symbole", und ersetzen Sie die idsymbol-Elemente im **guiddynamicmenupackagecmdset** -Block "guidsymbol". Sie müssen idsymbol-Elemente für die beiden Gruppen, den Menü Controller, den Platzhalter Befehl und den Anker Befehl definieren.

    ```xml
    <GuidSymbol name="guidDynamicMenuPackageCmdSet" value="{ your GUID here }">
        <IDSymbol name="MyToolbarItemGroup" value="0x1020" />
        <IDSymbol name="MyMenuControllerGroup" value="0x1025" />
        <IDSymbol name="MyMenuController" value ="0x1030"/>
        <IDSymbol name="cmdidMyAnchorCommand" value="0x0103" />
        <!-- NOTE: The following command expands at run time to some number of ids.
         Try not to place command ids after it (e.g. 0x0105, 0x0106).
         If you must add a command id after it, make the gap very large (e.g. 0x200) -->
        <IDSymbol name="cmdidMyDynamicStartCommand" value="0x0104" />
    </GuidSymbol>
    ```

2. Löschen Sie im Abschnitt Gruppen die vorhandenen Gruppen, und fügen Sie die beiden soeben definierten Gruppen hinzu:

    ```xml
    <Groups>
        <!-- The group that adds the MenuController on the Solution Explorer toolbar.
             The 0x4000 priority adds this group after the group that contains the
             Preview Selected Items button, which is normally at the far right of the toolbar. -->
        <Group guid="guidDynamicMenuPackageCmdSet" id="MyToolbarItemGroup" priority="0x4000" >
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN" />
        </Group>
        <!-- The group for the items on the MenuController drop-down. It is added to the MenuController submenu. -->
        <Group guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" priority="0x4000" >
            <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" />
        </Group>
    </Groups>
    ```

     Fügen Sie den menucontroller hinzu. Legen Sie das dynamicvisibility-Befehlsflag fest, da es nicht immer sichtbar ist. Der ButtonText wird nicht angezeigt.

    ```xml
    <Menus>
        <!-- The MenuController to display on the Solution Explorer toolbar.
             Place it in the ToolbarItemGroup.-->
        <Menu guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" priority="0x1000" type="MenuController">
            <Parent guid="guidDynamicMenuPackageCmdSet" id="MyToolbarItemGroup" />
            <CommandFlag>DynamicVisibility</CommandFlag>
            <Strings>
               <ButtonText></ButtonText>
           </Strings>
        </Menu>
    </Menus>
    ```

3. Fügen Sie zwei Schaltflächen hinzu, eine als Platzhalter für die dynamischen Menü Elemente und eine als Anker für den menucontroller.

     Das übergeordnete Element der Platzhalter Schaltfläche ist **mymenucontrollergroup**. Fügen Sie die Befehlsflags dynamicitemstart, dynamicvisibility und textchanges der Platzhalter Schaltfläche hinzu. Der ButtonText wird nicht angezeigt.

     Die Anker Schaltfläche enthält das Symbol und den QuickInfo-Text. Das übergeordnete Element der Anker Schaltfläche ist auch **mymenucontrollergroup**. Sie fügen das noshowonmenucontroller-Befehlsflag hinzu, um sicherzustellen, dass die Schaltfläche nicht in der Dropdown Liste Menü Controller angezeigt wird, und das fixmenucontroller-Befehlsflag, um es als permanenten Anker festzulegen.

    ```xml
    <!-- The placeholder for the dynamic items that expand to N items at run time. -->
    <Buttons>
        <Button guid="guidDynamicMenuPackageCmdSet" id="cmdidMyDynamicStartCommand" priority="0x1000" >
          <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" />
          <CommandFlag>DynamicItemStart</CommandFlag>
          <CommandFlag>DynamicVisibility</CommandFlag>
          <CommandFlag>TextChanges</CommandFlag>
          <!-- This text does not appear. -->
          <Strings>
            <ButtonText>Project</ButtonText>
          </Strings>
        </Button>

        <!-- The anchor item to supply the icon/tooltip for the MenuController -->
        <Button guid="guidDynamicMenuPackageCmdSet" id="cmdidMyAnchorCommand" priority="0x0000" >
          <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" />
          <!-- This is the icon that appears on the Solution Explorer toolbar. -->
          <Icon guid="guidImages" id="bmpPicArrows"/>
          <!-- Do not show on the menu controller's drop down list-->
          <CommandFlag>NoShowOnMenuController</CommandFlag>
          <!-- Become the permanent anchor item for the menu controller -->
          <CommandFlag>FixMenuController</CommandFlag>
          <!-- The text that appears in the tooltip.-->
          <Strings>
            <ButtonText>Set Startup Project</ButtonText>
          </Strings>
        </Button>
    </Buttons>
    ```

4. Fügen Sie dem Projekt ein Symbol (im Ordner " *Ressourcen* ") hinzu, und fügen Sie dann den Verweis darauf in der *vsct* -Datei hinzu. In dieser exemplarischen Vorgehensweise verwenden wir das Symbol Pfeile, das in der Projektvorlage enthalten ist.

5. Fügen Sie einen visibilityeinschränkungs Abschnitt außerhalb des Befehls Abschnitts direkt vor dem Abschnitt Symbole hinzu. (Sie erhalten möglicherweise eine Warnung, wenn Sie Sie nach Symbolen hinzufügen.) In diesem Abschnitt wird sichergestellt, dass der Menü Controller nur angezeigt wird, wenn eine Projekt Mappe mit mehreren Projekten geladen wird.

    ```xml
    <VisibilityConstraints>
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>
    </VisibilityConstraints>
    ```

## <a name="implement-the-dynamic-menu-command"></a>Implementieren des dynamischen Menübefehls
 Sie erstellen eine dynamische Menübefehls Klasse, die von erbt <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> . In dieser Implementierung gibt der Konstruktor ein Prädikat an, das für übereinstimmende Befehle verwendet werden soll. Sie müssen die- <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> Methode überschreiben, um dieses Prädikat zum Festlegen der-Eigenschaft zu verwenden <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> , die den aufzurufenden Befehl identifiziert.

1. Erstellen Sie eine neue c#-Klassendatei mit dem Namen *DynamicItemMenuCommand.cs*, und fügen Sie eine Klasse mit dem Namen **dynamicitemmenucommand** hinzu, die von erbt <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> :

    ```csharp
    class DynamicItemMenuCommand : OleMenuCommand
    {

    }

    ```

2. Fügen Sie die folgenden using-Direktiven hinzu:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    using System.ComponentModel.Design;
    ```

3. Fügen Sie ein privates Feld zum Speichern des Match-Prädikats hinzu:

    ```csharp
    private Predicate<int> matches;

    ```

4. Fügen Sie einen Konstruktor hinzu, der vom <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> -Konstruktor erbt und einen Befehls Handler und einen- <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> Handler angibt. Fügen Sie ein Prädikat für die Übereinstimmung mit dem Befehl hinzu:

    ```csharp
    public DynamicItemMenuCommand(CommandID rootId, Predicate<int> matches, EventHandler invokeHandler, EventHandler beforeQueryStatusHandler)
        : base(invokeHandler, null /*changeHandler*/, beforeQueryStatusHandler, rootId)
    {
        if (matches == null)
        {
            throw new ArgumentNullException("matches");
        }

        this.matches = matches;
    }
    ```

5. Überschreiben <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> Sie die-Methode, sodass Sie das Matches-Prädikat aufruft, und legt die- <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> Eigenschaft fest:

    ```csharp
    public override bool DynamicItemMatch(int cmdId)
    {
        // Call the supplied predicate to test whether the given cmdId is a match.
        // If it is, store the command id in MatchedCommandid
        // for use by any BeforeQueryStatus handlers, and then return that it is a match.
        // Otherwise clear any previously stored matched cmdId and return that it is not a match.
        if (this.matches(cmdId))
        {
            this.MatchedCommandId = cmdId;
            return true;
        }

        this.MatchedCommandId = 0;
        return false;
    }
    ```

## <a name="add-the-command"></a>Befehl hinzufügen
 Mit dem dynamicmenu-Konstruktor können Sie Menübefehle einrichten, einschließlich dynamischer Menüs und Menü Elemente.

1. Fügen Sie in *DynamicMenuPackage.cs* die GUID des Befehlssatzes und die Befehls-ID hinzu:

    ```csharp
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    public const uint cmdidMyCommand = 0x104;
    ```

2. Fügen Sie in der Datei *DynamicMenu.cs* die folgenden using-Direktiven hinzu:

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    using System.ComponentModel.Design;
    ```

3. Fügen Sie in der- `DynamicMenu` Klasse ein privates Feld **DTE2** hinzu.

    ```csharp
    private DTE2 dte2;
    ```

4. Fügen Sie ein privates Feld "rootitemid" hinzu:

    ```csharp
    private int rootItemId = 0;
    ```

5. Fügen Sie im dynamicmenu-Konstruktor den Menübefehl hinzu. Im nächsten Abschnitt definieren wir den Befehls Handler, den `BeforeQueryStatus` Ereignishandler und das Match-Prädikat.

    ```csharp
    private DynamicMenu(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException(nameof(package));
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            // Add the DynamicItemMenuCommand for the expansion of the root item into N items at run time.
            CommandID dynamicItemRootId = new CommandID(new Guid(DynamicMenuPackageGuids.guidDynamicMenuPackageCmdSet), (int)DynamicMenuPackageGuids.cmdidMyCommand);
            DynamicItemMenuCommand dynamicMenuCommand = new DynamicItemMenuCommand(dynamicItemRootId,
                IsValidDynamicItem,
                OnInvokedDynamicItem,
                OnBeforeQueryStatusDynamicItem);
                commandService.AddCommand(dynamicMenuCommand);
                }

        dte2 = (DTE2)this.ServiceProvider.GetService(typeof(DTE));
    }
    ```

## <a name="implement-the-handlers"></a>Implementieren von Handlern
 Wenn Sie dynamische Menü Elemente in einem Menü Controller implementieren möchten, müssen Sie den Befehl behandeln, wenn auf ein dynamisches Element geklickt wird. Außerdem müssen Sie die Logik implementieren, mit der der Zustand des Menü Elements festgelegt wird. Fügen Sie die Handler der- `DynamicMenu` Klasse hinzu.

1. Um den Befehl **Set Startup Project** zu implementieren, fügen Sie den **oninvokeddynamicitem** -Ereignishandler hinzu. Er sucht nach dem Projekt, dessen Name mit dem Text des aufgerufenen Befehls identisch ist, und legt ihn als Startprojekt fest, indem der absolute Pfad in der-Eigenschaft festgelegt wird <xref:EnvDTE.SolutionBuild.StartupProjects%2A> .

    ```csharp
    private void OnInvokedDynamicItem(object sender, EventArgs args)
    {
        DynamicItemMenuCommand invokedCommand = (DynamicItemMenuCommand)sender;
        // If the command is already checked, we don't need to do anything
        if (invokedCommand.Checked)
            return;

        // Find the project that corresponds to the command text and set it as the startup project
        var projects = dte2.Solution.Projects;
        foreach (Project proj in projects)
        {
            if (invokedCommand.Text.Equals(proj.Name))
            {
                dte2.Solution.SolutionBuild.StartupProjects = proj.FullName;
                return;
            }
        }
    }
    ```

2. Fügen Sie den `OnBeforeQueryStatusDynamicItem` Ereignishandler hinzu. Dies ist der Handler, der vor einem-Ereignis aufgerufen wird `QueryStatus` . Es bestimmt, ob das Menü Element ein "echtes" Element ist, d. h. nicht das Platzhalter Element und ob das Element bereits aktiviert ist (was bedeutet, dass das Projekt bereits als Startprojekt festgelegt ist).

    ```csharp
    private void OnBeforeQueryStatusDynamicItem(object sender, EventArgs args)
    {
        DynamicItemMenuCommand matchedCommand = (DynamicItemMenuCommand)sender;
        matchedCommand.Enabled = true;
        matchedCommand.Visible = true;

        // Find out whether the command ID is 0, which is the ID of the root item.
        // If it is the root item, it matches the constructed DynamicItemMenuCommand,
         // and IsValidDynamicItem won't be called.
        bool isRootItem = (matchedCommand.MatchedCommandId == 0);

        // The index is set to 1 rather than 0 because the Solution.Projects collection is 1-based.
        int indexForDisplay = (isRootItem ? 1 : (matchedCommand.MatchedCommandId - (int) DynamicMenuPackageGuids.cmdidMyCommand) + 1);

        matchedCommand.Text = dte2.Solution.Projects.Item(indexForDisplay).Name;

        Array startupProjects = (Array)dte2.Solution.SolutionBuild.StartupProjects;
        string startupProject = System.IO.Path.GetFileNameWithoutExtension((string)startupProjects.GetValue(0));

        // Check the command if it isn't checked already selected
        matchedCommand.Checked = (matchedCommand.Text == startupProject);

        // Clear the ID because we are done with this item.
        matchedCommand.MatchedCommandId = 0;
    }
    ```

## <a name="implement-the-command-id-match-predicate"></a>Implementieren des Befehls-ID-Vergleichs Prädikats

Implementieren Sie nun das Match-Prädikat. Wir müssen zwei Dinge ermitteln: Erstens, ob die Befehls-ID gültig ist (Sie ist größer als oder gleich der deklarierten Befehls-ID), und zweitens, ob Sie ein mögliches Projekt angibt (es ist kleiner als die Anzahl der Projekte in der Projekt Mappe).

```csharp
private bool IsValidDynamicItem(int commandId)
{
    // The match is valid if the command ID is >= the id of our root dynamic start item
    // and the command ID minus the ID of our root dynamic start item
    // is less than or equal to the number of projects in the solution.
    return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);
}
```

## <a name="set-the-vspackage-to-load-only-when-a-solution-has-multiple-projects"></a>Legen Sie fest, dass das VSPackage nur geladen wird, wenn eine Projekt Mappe mehrere Projekte enthält.
 Da der Befehl **Set Startup Project** nur dann sinnvoll ist, wenn die aktive Projekt Mappe mehr als ein Projekt enthält, können Sie für Ihr VSPackage nur in diesem Fall die automatische Auslastung festlegen. Sie verwenden <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> zusammen mit dem UI-Kontext <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects> . Fügen Sie in der Datei *DynamicMenuPackage.cs* die folgenden Attribute der dynamicmenupackage-Klasse hinzu:

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
[ProvideMenuResource("Menus.ctmenu", 1)]
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]
[Guid(DynamicMenuPackage.PackageGuidString)]
public sealed class DynamicMenuItemsPackage : Package
{}
```

## <a name="test-the-set-startup-project-command"></a>Testen des Befehls "Startprojekt festlegen"
 Nun können Sie Ihren Code testen.

1. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz sollte angezeigt werden.

2. Öffnen Sie in der experimentellen Instanz eine Projekt Mappe mit mehr als einem Projekt.

     Das Pfeilsymbol sollte auf der **Projektmappen-Explorer** Symbolleiste angezeigt werden. Wenn Sie das Element erweitern, sollten Menü Elemente angezeigt werden, die die verschiedenen Projekte in der Projekt Mappe darstellen.

3. Wenn Sie eines der Projekte überprüfen, wird es zum Startprojekt.

4. Wenn Sie die Projekt Mappe schließen oder eine Projekt Mappe öffnen, die nur über ein Projekt verfügt, sollte das Symbolleisten Symbol ausgeblendet werden.

## <a name="see-also"></a>Weitere Informationen
- [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)
- [Hinzufügen von Elementen der Benutzeroberfläche durch VSPackages](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
