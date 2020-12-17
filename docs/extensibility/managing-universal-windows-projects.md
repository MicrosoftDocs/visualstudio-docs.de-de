---
title: Verwalten von universellen Windows-Projekten | Microsoft-Dokumentation
description: Um universelle Windows-apps zu unterstützen, sollten Visual Studio-Erweiterungen, die Projekte verwalten, die universelle Windows-App-Projektstruktur beachten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f86edd33e7719dc326aa2c5d252d11322509de64
ms.sourcegitcommit: d485b18e46ec4cf08704b5a8d0657bc716ec8393
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2020
ms.locfileid: "97615563"
---
# <a name="manage-universal-windows-projects"></a>Universelle Windows-Projekte verwalten

Universelle Windows-apps sind apps, die sowohl Windows 8.1 als auch Windows Phone 8,1 als Ziel verwenden, sodass Entwickler Code und andere Ressourcen auf beiden Plattformen verwenden können. Der freigegebene Code und die Ressourcen werden in einem freigegebenen Projekt aufbewahrt, während der plattformspezifische Code und die Ressourcen in separaten Projekten aufbewahrt werden, einer für Windows und der andere für Windows phone. Weitere Informationen zu universellen Windows-apps finden Sie unter [universelle Windows-apps](/windows/uwp/get-started/create-uwp-apps). Visual Studio-Erweiterungen, die Projekte verwalten, sollten beachten, dass universelle Windows-App-Projekte eine Struktur aufweisen, die sich von apps mit einer einzelnen Plattform unterscheidet In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie im freigegebenen Projekt navigieren und die freigegebenen Elemente verwalten.

## <a name="prerequisites"></a>Voraussetzungen

Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Es ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="navigate-the-shared-project"></a>Navigieren im freigegebenen Projekt

1. Erstellen Sie ein c#-VSIX-Projekt mit dem Namen **testuniversalproject**. (**Datei**  >  **Neu**  >  **Project** und anschließend **c#**-  >  **Erweiterbarkeit**  >  **Visual Studio-Paket**). Fügen Sie eine **benutzerdefinierte Befehls** Projekt Element Vorlage hinzu (Klicken Sie auf dem **Projektmappen-Explorer** mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie neues Element **Hinzufügen** und  >  dann zu **Erweiterbarkeit**). Nennen Sie die Datei **testuniversalproject**.

2. Fügen Sie einen Verweis auf *Microsoft.VisualStudio.Shell.Interop.12.1.DesignTime.dll* und *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll* (im Abschnitt **Erweiterungen** ) hinzu.

3. Öffnen Sie *TestUniversalProject.cs* , und fügen Sie die folgenden `using` Anweisungen hinzu:

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.PlatformUI;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    using System.Collections.Generic;
    using System.IO;
    using System.Windows.Forms;
    ```

4. Fügen Sie in der- `TestUniversalProject` Klasse ein privates Feld hinzu, das auf das **Ausgabe** Fenster zeigt.

    ```csharp
    public sealed class TestUniversalProject
    {
        IVsOutputWindowPane output;
    . . .
    }
    ```

5. Legen Sie den Verweis auf den Ausgabebereich im testuniversalproject-Konstruktor fest:

    ```csharp
    private TestUniversalProject(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException("package");
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);
            EventHandler eventHandler = this.ShowMessageBox;
            MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);
            commandService.AddCommand(menuItem);
        }

        // get a reference to the Output window
        output = (IVsOutputWindowPane)ServiceProvider.GetService(typeof(SVsGeneralOutputWindowPane));
    }
    ```

6. Entfernen Sie den vorhandenen Code aus der- `ShowMessageBox` Methode:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
    }
    ```

7. Holen Sie sich das DTE-Objekt, das wir in dieser exemplarischen Vorgehensweise für verschiedene Zwecke verwenden werden. Stellen Sie außerdem sicher, dass eine Projekt Mappe geladen wird, wenn auf die Menü Schaltfläche geklickt wird.

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var dte = (EnvDTE.DTE)this.ServiceProvider.GetService(typeof(EnvDTE.DTE));
        if (dte.Solution != null)
        {
            . . .
        }
        else
        {
            MessageBox.Show("No solution is open");
            return;
        }
    }
    ```

8. Suchen Sie das freigegebene Projekt. Das freigegebene Projekt ist ein reiner Container. Es werden keine Ausgaben erstellt oder erzeugt. Die folgende Methode sucht das erste freigegebene Projekt in der Projekt Mappe durchsuchen nach dem- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Objekt, das über die Funktion des freigegebenen Projekts verfügt.

    ```csharp
    private IVsHierarchy FindSharedProject()
    {
        var sln = (IVsSolution)this.ServiceProvider.GetService(typeof(SVsSolution));
        Guid empty = Guid.Empty;
        IEnumHierarchies enumHiers;

        //get all the projects in the solution
        ErrorHandler.ThrowOnFailure(sln.GetProjectEnum((uint)__VSENUMPROJFLAGS.EPF_LOADEDINSOLUTION, ref empty, out enumHiers));
        foreach (IVsHierarchy hier in ComUtilities.EnumerableFrom(enumHiers))
        {
            if (PackageUtilities.IsCapabilityMatch(hier, "SharedAssetsProject"))
            {
                return hier;
            }
        }
        return null;
    }
    ```

9. Geben Sie in der- `ShowMessageBox` Methode die Beschriftung (den Projektnamen, der in der **Projektmappen-Explorer** angezeigt wird) des freigegebenen Projekts aus.

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));

        if (dte.Solution != null)
        {
            var sharedHier = this.FindSharedProject();
            if (sharedHier != null)
            {
                string sharedCaption = HierarchyUtilities.GetHierarchyProperty<string>(sharedHier, (uint)VSConstants.VSITEMID.Root,
                     (int)__VSHPROPID.VSHPROPID_Caption);
                output.OutputStringThreadSafe(string.Format("Found shared project: {0}\n", sharedCaption));
            }
            else
            {
                MessageBox.Show("Solution has no shared project");
                return;
            }
        }
        else
        {
            MessageBox.Show("No solution is open");
            return;
        }
    }
    ```

10. Holen Sie sich das aktive Platt Form Projekt. Platt Form Projekte sind Projekte, die plattformspezifischen Code und Ressourcen enthalten. Die folgende Methode verwendet das neue Feld <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy> , um das aktive Platt Form Projekt zu erhalten.

    ```csharp
    private IVsHierarchy GetActiveProjectContext(IVsHierarchy hierarchy)
    {
        IVsHierarchy activeProjectContext;
        if (HierarchyUtilities.TryGetHierarchyProperty(hierarchy, (uint)VSConstants.VSITEMID.Root,
             (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, out activeProjectContext))
        {
            return activeProjectContext;
        }
        else
        {
            return null;
        }
    }
    ```

11. Geben Sie in der- `ShowMessageBox` Methode die Beschriftung des aktiven Platt Form Projekts aus.

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));

        if (dte.Solution != null)
        {
            var sharedHier = this.FindSharedProject();
            if (sharedHier != null)
            {
                string sharedCaption = HierarchyUtilities.GetHierarchyProperty<string>(sharedHier, (uint)VSConstants.VSITEMID.Root,
                     (int)__VSHPROPID.VSHPROPID_Caption);
                output.OutputStringThreadSafe(string.Format("Shared project: {0}\n", sharedCaption));

                var activePlatformHier = this.GetActiveProjectContext(sharedHier);
                if (activePlatformHier != null)
                {
                    string activeCaption = HierarchyUtilities.GetHierarchyProperty<string>(activePlatformHier,
                         (uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_Caption);
                    output.OutputStringThreadSafe(string.Format("Active platform project: {0}\n", activeCaption));
                }
                else
                {
                    MessageBox.Show("Shared project has no active platform project");
                }
            }
            else
            {
                MessageBox.Show("Solution has no shared project");
            }
        }
        else
        {
            MessageBox.Show("No solution is open");
        }
    }
    ```

12. Iterieren Sie die Platt Form Projekte. Mit der folgenden Methode werden alle importierten (Plattform-) Projekte aus dem freigegebenen Projekt abgerufen.

    ```csharp
    private IEnumerable<IVsHierarchy> EnumImportingProjects(IVsHierarchy hierarchy)
    {
        IVsSharedAssetsProject sharedAssetsProject;
        if (HierarchyUtilities.TryGetHierarchyProperty(hierarchy, (uint)VSConstants.VSITEMID.Root,
            (int)__VSHPROPID7.VSHPROPID_SharedAssetsProject, out sharedAssetsProject)
            && sharedAssetsProject != null)
        {
            foreach (IVsHierarchy importingProject in sharedAssetsProject.EnumImportingProjects())
            {
                yield return importingProject;
            }
        }
    }
    ```

    > [!IMPORTANT]
    > Wenn der Benutzer ein C++ Universal Windows-App-Projekt in der experimentellen Instanz geöffnet hat, löst der obige Code eine Ausnahme aus. Dies ist ein bekanntes Problem. Um die Ausnahme zu vermeiden, ersetzen Sie den `foreach` obigen Block durch Folgendes:

    ```csharp
    var importingProjects = sharedAssetsProject.EnumImportingProjects();
    for (int i = 0; i < importingProjects.Count; ++i)
    {
        yield return importingProjects[i];
    }
    ```

13. Geben Sie in der- `ShowMessageBox` Methode die Beschriftung der einzelnen Platt Form Projekte aus. Fügen Sie den folgenden Code nach der Zeile ein, die die Beschriftung des aktiven Platt Form Projekts ausgibt. Nur die geladenen Platt Form Projekte werden in dieser Liste angezeigt.

    ```csharp
    output.OutputStringThreadSafe("Platform projects:\n");

    IEnumerable<IVsHierarchy> projects = this.EnumImportingProjects(sharedHier);

    bool isActiveProjectSet = false;
    foreach (IVsHierarchy platformHier in projects)
    {
        string platformCaption = HierarchyUtilities.GetHierarchyProperty<string>(platformHier, (uint)VSConstants.VSITEMID.Root,
            (int)__VSHPROPID.VSHPROPID_Caption);
        output.OutputStringThreadSafe(string.Format(" * {0}\n", platformCaption));
    }
    ```

14. Ändern Sie das aktive Platt Form Projekt. Mit der folgenden Methode wird das aktive Projekt mithilfe von festgelegt <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A> .

    ```csharp
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)
    {
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);
    }
    ```

15. Ändern Sie in der- `ShowMessageBox` Methode das aktive Platt Form Projekt. Fügen Sie diesen Code in den- `foreach` Block ein.

    ```csharp
    bool isActiveProjectSet = false;
    string platformCaption = null;
    foreach (IVsHierarchy platformHier in projects)
    {
        platformCaption = HierarchyUtilities.GetHierarchyProperty<string>(platformHier, (uint)VSConstants.VSITEMID.Root,
             (int)__VSHPROPID.VSHPROPID_Caption);
        output.OutputStringThreadSafe(string.Format(" * {0}\n", platformCaption));

        // if this project is neither the shared project nor the current active platform project,
        // set it to be the active project
        if (!isActiveProjectSet && platformHier != activePlatformHier)
        {
            this.SetActiveProjectContext(sharedHier, platformHier);
            activePlatformHier = platformHier;
            isActiveProjectSet = true;
        }
    }
    output.OutputStringThreadSafe("set active project: " + platformCaption +'\n');
    ```

16. Probieren Sie es jetzt aus. Drücken Sie F5, um die experimentelle Instanz zu starten. Erstellen Sie ein c#-Universal Hub-App-Projekt in der experimentellen Instanz (im Dialogfeld **Neues Projekt** , **Visual c#**  >  **Windows**  >  **Windows 8**  >  **Universal**  >  **Hub-App**). Nachdem die Projekt Mappe geladen wurde, wechseln Sie **zum Menü Extras** , klicken Sie auf **testuniversalproject aufrufen**, und überprüfen Sie dann den Text im **Ausgabe** Bereich. Folgendes sollte angezeigt werden:

    ```
    Found shared project: HubApp.Shared
    The active platform project: HubApp.Windows
    Platform projects:
     * HubApp.Windows
     * HubApp.WindowsPhone
    set active project: HubApp.WindowsPhone
    ```

### <a name="manage-the-shared-items-in-the-platform-project"></a>Verwalten der freigegebenen Elemente im Platt Form Projekt

1. Suchen Sie die freigegebenen Elemente im Platt Form Projekt. Die Elemente im freigegebenen Projekt werden im Platt Form Projekt als freigegebene Elemente angezeigt. Sie können Sie nicht im **Projektmappen-Explorer** sehen, aber Sie können die Projekt Hierarchie durchlaufen, um Sie zu finden. Mit der folgenden Methode wird die Hierarchie durchlaufen und alle freigegebenen Elemente erfasst. Optional gibt Sie die Beschriftung der einzelnen Elemente aus. Die freigegebenen Elemente werden durch die neue-Eigenschaft identifiziert <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_IsSharedItem> .

    ```csharp
    private void InspectHierarchyItems(IVsHierarchy hier, uint itemid, int level, List<uint> itemIds, bool getSharedItems, bool printItems)
    {
        string caption = HierarchyUtilities.GetHierarchyProperty<string>(hier, itemid, (int)__VSHPROPID.VSHPROPID_Caption);
        if (printItems)
            output.OutputStringThreadSafe(string.Format("{0}{1}\n", new string('\t', level), caption));

        // if getSharedItems is true, inspect only shared items; if it's false, inspect only unshared items
        bool isSharedItem;
        if (HierarchyUtilities.TryGetHierarchyProperty(hier, itemid, (int)__VSHPROPID7.VSHPROPID_IsSharedItem, out isSharedItem)
            && (isSharedItem == getSharedItems))
        {
            itemIds.Add(itemid);
        }

        uint child;
        if (HierarchyUtilities.TryGetHierarchyProperty(hier, itemid, (int)__VSHPROPID.VSHPROPID_FirstChild, Unbox.AsUInt32, out child)
            && child != (uint)VSConstants.VSITEMID.Nil)
        {
            this.InspectHierarchyItems(hier, child, level + 1, itemIds, isSharedItem, printItems);

            while (HierarchyUtilities.TryGetHierarchyProperty(hier, child, (int)__VSHPROPID.VSHPROPID_NextSibling, Unbox.AsUInt32, out child)
                && child != (uint)VSConstants.VSITEMID.Nil)
            {
                this.InspectHierarchyItems(hier, child, level + 1, itemIds, isSharedItem, printItems);
            }
        }
    }
    ```

2. Fügen Sie in der- `ShowMessageBox` Methode den folgenden Code hinzu, um die Hierarchie Elemente der Plattform zu durchlaufen. Fügen Sie Sie in den- `foreach` Block ein.

    ```csharp
    output.OutputStringThreadSafe("Walk the active platform project:\n");
    var sharedItemIds = new List<uint>();
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ```

3. Lesen Sie die freigegebenen Elemente. Die freigegebenen Elemente werden im Platt Form Projekt als verborgene verknüpfte Dateien angezeigt, und Sie können alle Eigenschaften als normale verknüpfte Dateien lesen. Der folgende Code liest den vollständigen Pfad des ersten freigegebenen Elements.

    ```csharp
    var sharedItemId = sharedItemIds[0];
    string fullPath;
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));
    ```

4. Probieren Sie es jetzt aus. Drücken Sie **F5** , um die experimentelle Instanz zu starten. Erstellen eines universellen c#-Hub-App-Projekts in der experimentellen Instanz (im Dialogfeld **Neues Projekt** , **Visual c#**  >  **Windows**  >  **Windows 8**  >  **Universal**  >  **Hub-App**)  wechseln Sie zum Menü Extras, klicken Sie auf **testuniversalproject aufrufen**, und überprüfen Sie dann den Text im **Ausgabe** Bereich. Folgendes sollte angezeigt werden:

    ```
    Found shared project: HubApp.Shared
    The active platform project: HubApp.Windows
    Platform projects:
     * HubApp.Windows
     * HubApp.WindowsPhone
    set active project: HubApp.WindowsPhone
    Walk the active platform project:
        HubApp.WindowsPhone
            <HubApp.Shared>
                App.xaml
                    App.xaml.cs
                Assets
                    DarkGray.png
                    LightGray.png
                    MediumGray.png
                Common
                    NavigationHelper.cs
                    ObservableDictionary.cs
                    RelayCommand.cs
                    SuspensionManager.cs
                DataModel
                    SampleData.json
                    SampleDataSource.cs
                HubApp.Shared.projitems
                Strings
                    en-US
                        Resources.resw
            Assets
                HubBackground.theme-dark.png
                HubBackground.theme-light.png
                Logo.scale-240.png
                SmallLogo.scale-240.png
                SplashScreen.scale-240.png
                Square71x71Logo.scale-240.png
                StoreLogo.scale-240.png
                WideLogo.scale-240.png
            HubPage.xaml
                HubPage.xaml.cs
            ItemPage.xaml
                ItemPage.xaml.cs
            Package.appxmanifest
            Properties
                AssemblyInfo.cs
            References
                .NET for Windows Store apps
                HubApp.Shared
                Windows Phone 8.1
            SectionPage.xaml
                SectionPage.xaml.cs
    ```

### <a name="detect-changes-in-platform-projects-and-shared-projects"></a>Erkennen von Änderungen in Platt Form Projekten und freigegebenen Projekten

1. Sie können Hierarchie-und Projekt Ereignisse verwenden, um Änderungen in freigegebenen Projekten wie bei Platt Form Projekten zu erkennen. Die Projekt Elemente im freigegebenen Projekt sind jedoch nicht sichtbar, was bedeutet, dass bestimmte Ereignisse nicht ausgelöst werden, wenn freigegebene Projekt Elemente geändert werden.

    Sehen Sie sich die Reihenfolge der Ereignisse an, wenn eine Datei in einem Projekt umbenannt wird:

   1. Der Dateiname wird auf dem Datenträger geändert.

   2. Die Projektdatei wird so aktualisiert, dass Sie den neuen Namen der Datei enthält.

      Hierarchie Ereignisse (z. b <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents> .) verfolgen im Allgemeinen die Änderungen, die in der Benutzeroberfläche angezeigt werden, wie in der **Projektmappen-Explorer**. Hierarchie Ereignisse stellen einen Datei Umbenennungs Vorgang in Erwägung, der aus einer Datei Löschung und einer Datei Addition besteht. Wenn jedoch unsichtbare Elemente geändert werden, löst das Hierarchie-Ereignis System ein Ereignis aus, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> aber kein <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> Ereignis. Wenn Sie eine Datei in einem Platt Form Projekt umbenennen, erhalten Sie daher sowohl <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> als auch <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> , aber wenn Sie eine Datei in einem freigegebenen Projekt umbenennen, erhalten Sie nur einen <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> .

      Zum Nachverfolgen von Änderungen in Projekt Elementen können Sie DTE-Projekt Element Ereignisse (die in gefunden <xref:EnvDTE.ProjectItemsEventsClass> ) behandeln. Wenn Sie jedoch eine große Anzahl von Ereignissen verarbeiten, können Sie eine bessere Leistung erzielen, wenn Sie die Ereignisse in verarbeiten <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> . In dieser exemplarischen Vorgehensweise werden nur die Hierarchie Ereignisse und die DTE-Ereignisse angezeigt. In diesem Verfahren fügen Sie einen Ereignislistener zu einem freigegebenen Projekt und einem Platt Form Projekt hinzu. Wenn Sie dann eine Datei in einem freigegebenen Projekt und eine andere Datei in einem Platt Form Projekt umbenennen, werden die Ereignisse angezeigt, die für jeden Umbenennungs Vorgang ausgelöst werden.

      In diesem Verfahren fügen Sie einen Ereignislistener zu einem freigegebenen Projekt und einem Platt Form Projekt hinzu. Wenn Sie dann eine Datei in einem freigegebenen Projekt und eine andere Datei in einem Platt Form Projekt umbenennen, werden die Ereignisse angezeigt, die für jeden Umbenennungs Vorgang ausgelöst werden.

2. Fügen Sie einen Ereignislistener hinzu. Fügen Sie dem Projekt eine neue Klassendatei hinzu, und nennen Sie Sie *HierarchyEventListener.cs*.

3. Öffnen Sie die Datei *HierarchyEventListener.cs* , und fügen Sie die folgenden using-Anweisungen hinzu:

   ```csharp
   using Microsoft.VisualStudio.Shell.Interop;
   using Microsoft.VisualStudio;
   using System.IO;
   ```

4. Implementieren Sie die- `HierarchyEventListener` Klasse <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents> :

   ```csharp
   class HierarchyEventListener : IVsHierarchyEvents
   { }
   ```

5. Implementieren Sie die Member von <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents> , wie im folgenden Code dargestellt.

   ```csharp
   class HierarchyEventListener : IVsHierarchyEvents
   {
       private IVsHierarchy hierarchy;
       IVsOutputWindowPane output;

       internal HierarchyEventListener(IVsHierarchy hierarchy, IVsOutputWindowPane outputWindow) {
            this.hierarchy = hierarchy;
            this.output = outputWindow;
       }

       int IVsHierarchyEvents.OnInvalidateIcon(IntPtr hIcon) {
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnInvalidateItems(uint itemIDParent) {
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnItemAdded(uint itemIDParent, uint itemIDSiblingPrev, uint itemIDAdded) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemAdded: " + itemIDAdded + "\n");
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnItemDeleted(uint itemID) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemDeleted: " + itemID + "\n");
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnItemsAppended(uint itemIDParent) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemsAppended\n");
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnPropertyChanged(uint itemID, int propID, uint flags) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnPropertyChanged: item ID " + itemID + "\n");
           return VSConstants.S_OK;
       }
   }
   ```

6. Fügen Sie in derselben Klasse einen weiteren Ereignishandler für das DTE-Ereignis hinzu <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> , das auftritt, wenn ein Projekt Element umbenannt wird.

   ```csharp
   public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)
   {
       output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",
            oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));
   }
   ```

7. Registrieren Sie sich für die Hierarchie Ereignisse. Sie müssen sich für jedes Projekt, das Sie nachverfolgen, separat registrieren. Fügen Sie den folgenden Code in `ShowMessageBox` , einen für das freigegebene Projekt und den anderen für eines der Platt Form Projekte hinzu.

   ```csharp
   // hook up the event listener for hierarchy events on the shared project
   HierarchyEventListener listener1 = new HierarchyEventListener(sharedHier, output);
   uint cookie1;
   sharedHier.AdviseHierarchyEvents(listener1, out cookie1);

   // hook up the event listener for hierarchy events on the
   active project
   HierarchyEventListener listener2 = new HierarchyEventListener(activePlatformHier, output);
   uint cookie2;
   activePlatformHier.AdviseHierarchyEvents(listener2, out cookie2);
   ```

8. Registrieren Sie sich für das DTE-Projekt Element-Ereignis <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> . Fügen Sie den folgenden Code hinzu, nachdem Sie den zweiten Listener eingebunden haben.

   ```csharp
   // hook up DTE events for project items
   Events2 dteEvents = (Events2)dte.Events;
   dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;
   ```

9. Ändern Sie das freigegebene Element. Freigegebene Elemente in einem Platt Form Projekt können nicht geändert werden. Stattdessen müssen Sie Sie im freigegebenen Projekt ändern, bei dem es sich um den eigentlichen Besitzer dieser Elemente handelt. Sie können die entsprechende Element-ID im freigegebenen Projekt mit <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> dem vollständigen Pfad des freigegebenen Elements erhalten. Anschließend können Sie das freigegebene Element ändern. Die Änderung wird an die Platt Form Projekte weitergegeben.

    > [!IMPORTANT]
    > Vor der Änderung sollten Sie herausfinden, ob ein Projekt Element ein frei gegebenes Element ist.

     Die folgende Methode ändert den Namen einer Projekt Element Datei.

    ```csharp
    private void ModifyFileNameInProject(IVsHierarchy project, string path)
    {
        int found;
        uint projectItemID;
        VSDOCUMENTPRIORITY[] priority = new VSDOCUMENTPRIORITY[1];
        if (ErrorHandler.Succeeded(((IVsProject)project).IsDocumentInProject(path, out found, priority, out projectItemID))
            && found != 0)
        {
            var name = DateTime.Now.Ticks.ToString() + Path.GetExtension(path);
            project.SetProperty(projectItemID, (int)__VSHPROPID.VSHPROPID_EditLabel, name);
            output.OutputStringThreadSafe(string.Format("Renamed {0} to {1}\n", path,name));
        }
    }
    ```

10. Diese Methode nach dem gesamten anderen Code in aufzurufen `ShowMessageBox` , um den Dateinamen des Elements im freigegebenen Projekt zu ändern. Fügen Sie dies nach dem Code ein, der den vollständigen Pfad des Elements im freigegebenen Projekt abruft.

    ```csharp
    // change the file name of an item in a shared project
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));
    this.ModifyFileNameInProject(sharedHier, fullPath);
    ```

11. Erstellen Sie das Projekt, und führen Sie es aus. Erstellen Sie eine universelle c#-Hub-app in der experimentellen Instanz. wechseln Sie **zum Menü Extras** , klicken Sie auf **testuniversalproject aufrufen**, und überprüfen Sie den Text im Bereich allgemeine Ausgabe. Der Name des ersten Elements im freigegebenen Projekt (erwartet wird, dass es sich um die Datei " *app. XAML* " handelt) muss geändert werden, und Sie sollten sehen, dass das <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> Ereignis ausgelöst wurde. Da in diesem Fall das Umbenennen von *app. XAML* bewirkt, dass *app.XAML.cs* ebenfalls umbenannt wird, sollten vier Ereignisse angezeigt werden (zwei für jedes Platt Form Projekt). (DTE-Ereignisse verfolgen die Elemente im freigegebenen Projekt nicht nach.) Es sollten zwei <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> Ereignisse angezeigt werden (eine für jedes der Platt Form Projekte), aber keine <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> Ereignisse.

12. Versuchen Sie jetzt, eine Datei in einem Platt Form Projekt umzubenennen, und Sie können den Unterschied in den Ereignissen sehen, die ausgelöst werden. Fügen Sie nach dem-Befehl in den folgenden Code ein `ShowMessageBox` `ModifyFileName` .

    ```csharp
    // change the file name of an item in a platform project
    var unsharedItemIds = new List<uint>();
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, unsharedItemIds, false, false);

    var unsharedItemId = unsharedItemIds[0];
    string unsharedPath;
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(unsharedItemId, out unsharedPath));
    output.OutputStringThreadSafe(string.Format("Platform project item ID = {0}, full path = {1}\n", unsharedItemId, unsharedPath));

    this.ModifyFileNameInProject(activePlatformHier, unsharedPath);
    ```

13. Erstellen Sie das Projekt, und führen Sie es aus. Erstellen Sie ein universelles c#-Projekt in der experimentellen Instanz. wechseln Sie **zum Menü Extras** , klicken Sie auf **testuniversalproject aufrufen**, und überprüfen Sie den Text im Bereich allgemeine Ausgabe. Nachdem die Datei im Platt Form Projekt umbenannt wurde, sollten ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> Ereignis und ein Ereignis angezeigt werden <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> . Da das Ändern der Datei dazu geführt hat, dass keine anderen Dateien geändert wurden, und da Änderungen an Elementen in einem Platt Form Projekt nicht an einer beliebigen Stelle weitergegeben werden, gibt es nur eines dieser Ereignisse.