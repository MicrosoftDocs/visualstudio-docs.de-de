---
title: 'Vorgehensweise: Bereitstellen eines asynchronen Visual Studio-Dienstanbieter | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie einen asynchronen Visual Studio-Dienst bereitstellen. Mit diesem Ansatz können Sie einen Dienst abrufen, ohne den UI-Thread zu blockieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4cbdd539437bce6f160dfa8661f514bf9f40b134
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965329"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Vorgehensweise: Bereitstellen eines asynchronen Visual Studio-Dienstanbieter
Wenn Sie einen Dienst abrufen möchten, ohne den UI-Thread zu blockieren, sollten Sie einen asynchronen Dienst erstellen und das Paket in einem Hintergrund Thread laden. Zu diesem Zweck können Sie <xref:Microsoft.VisualStudio.Shell.AsyncPackage> anstelle eines verwenden <xref:Microsoft.VisualStudio.Shell.Package> und den Dienst mit den speziellen asynchronen Methoden des asynchronen Pakets hinzufügen.

 Weitere Informationen zum Bereitstellen synchroner Visual Studio-Dienste finden Sie unter Vorgehens [Weise: Bereitstellen eines Diensts](../extensibility/how-to-provide-a-service.md).

## <a name="implement-an-asynchronous-service"></a>Implementieren eines asynchronen Dienstanbieter

1. Erstellen Sie ein VSIX-Projekt (**Datei**  >  **neu**  >  **Projekt**  >  **Visual c#**  >  **extensiblity**  >  **VSIX-Projekt**). Nennen Sie das Projekt **testasync**.

2. Fügen Sie dem Projekt ein VSPackage hinzu. Wählen Sie den Projekt Knoten im **Projektmappen-Explorer** aus, und klicken Sie auf Neues Element **Hinzufügen**  >    >  **Visual c# Elemente**  >  **Erweiterbarkeit**  >  **Visual Studio-Paket**. Benennen Sie diese Datei *TestAsyncPackage.cs*.

3. Ändern Sie in *TestAsyncPackage.cs* das Paket, um von zu erben, `AsyncPackage` anstelle von `Package` :

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. Um einen Dienst zu implementieren, müssen Sie drei Typen erstellen:

    - Eine Schnittstelle, die den Dienst identifiziert. Viele dieser Schnittstellen sind leer, d. h. Sie verfügen über keine Methoden, da Sie nur zum Abfragen des Dienstanbieter verwendet werden.

    - Eine Schnittstelle, die die Dienst Schnittstelle beschreibt. Diese Schnittstelle schließt die zu implementierenden Methoden ein.

    - Eine Klasse, die sowohl den Dienst als auch die Dienst Schnittstelle implementiert.

5. Das folgende Beispiel zeigt eine grundlegende Implementierung der drei Typen. Der Konstruktor der Dienstklasse muss den Dienstanbieter festlegen. In diesem Beispiel fügen wir den Dienst einfach der Paket Codedatei hinzu.

6. Fügen Sie die folgenden using-Direktiven der Paketdatei hinzu:

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    using Microsoft.VisualStudio.Threading;
    using IAsyncServiceProvider = Microsoft.VisualStudio.Shell.IAsyncServiceProvider;
    using Task = System.Threading.Tasks.Task;
    ```

7. Hier ist die asynchrone Dienst Implementierung. Beachten Sie, dass Sie den asynchronen Dienstanbieter anstelle des synchronen Dienstanbieters im Konstruktor festlegen müssen:

    ```csharp
    public class TextWriterService : STextWriterService, ITextWriterService
    {
        private IAsyncServiceProvider asyncServiceProvider;

        public TextWriterService(IAsyncServiceProvider provider)
        {
            // constructor should only be used for simple initialization
            // any usage of Visual Studio service, expensive background operations should happen in the
            // asynchronous InitializeAsync method for best performance
            asyncServiceProvider = provider;
        }

        public async Task InitializeAsync(CancellationToken cancellationToken)
        {
            await TaskScheduler.Default;
            // do background operations that involve IO or other async methods

            await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);
            // query Visual Studio services on main thread unless they are documented as free threaded explicitly.
            // The reason for this is the final cast to service interface (such as IVsShell) may involve COM operations to add/release references.

            IVsShell vsShell = this.asyncServiceProvider.GetServiceAsync(typeof(SVsShell)) as IVsShell;
            // use Visual Studio services to continue initialization
        }

        public async Task WriteLineAsync(string path, string line)
        {
            StreamWriter writer = new StreamWriter(path);
            await writer.WriteLineAsync(line);
            writer.Close();
        }
    }

    public interface STextWriterService
    {
    }

    public interface ITextWriterService
    {
        System.Threading.Tasks.Task WriteLineAsync(string path, string line);
    }
    ```

## <a name="register-a-service"></a>Registrieren eines Dienstanbieter
 Um einen Dienst zu registrieren, fügen Sie dem Paket, das <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> den Dienst bereitstellt, das hinzu. Zum Registrieren eines synchronen Dienstanbieter müssen Sie sicherstellen, dass sowohl das Paket als auch der Dienst Async-laden unterstützt:

- Sie müssen das Feld **allowsbackgroundload = true** hinzufügen, <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> um sicherzustellen, dass das Paket asynchron initialisiert werden kann. Weitere Informationen zu packageregistrationattribute finden Sie unter [registrieren und Aufheben der Registrierung von VSPackages](../extensibility/registering-and-unregistering-vspackages.md).

- Sie müssen das Feld **isasyncquervable = true** hinzufügen, <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> um sicherzustellen, dass die Dienst Instanz asynchron initialisiert werden kann.

  Im folgenden finden Sie ein Beispiel für eine `AsyncPackage` mit einer asynchronen Dienst Registrierung:

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="add-a-service"></a>Hinzufügen eines Diensts

1. Entfernen Sie in *TestAsyncPackage.cs* die `Initialize()` -Methode, und überschreiben Sie die- `InitializeAsync()` Methode. Fügen Sie den Dienst hinzu, und fügen Sie eine Rückruf Methode hinzu, um die Dienste zu erstellen. Im folgenden finden Sie ein Beispiel für den asynchronen Initialisierer, der einen Dienst hinzufügt:

    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }

    ```
    Um diesen Dienst außerhalb dieses Pakets sichtbar zu machen, legen Sie den Wert für das Promote-Flag als letzten Parameter auf " *true* " fest:  `this.AddService(typeof(STextWriterService), CreateTextWriterService, true);`

2. Fügen Sie einen Verweis auf *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll* hinzu.

3. Implementieren Sie die Rückruf Methode als asynchrone Methode, die den Dienst erstellt und zurückgibt.

    ```csharp
    public async Task<object> CreateTextWriterService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)
    {
        TextWriterService service = new TextWriterService(this);
        await service.InitializeAsync(cancellationToken);
        return service;
    }

    ```

## <a name="use-a-service"></a>Verwenden eines Dienstanbieter
 Nun können Sie den Dienst erhalten und seine Methoden verwenden.

1. Dies wird im Initialisierer gezeigt, aber Sie können den Dienst überall dort aufrufen, wo Sie den Dienst verwenden möchten.

    ```csharp
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);

        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;
        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");
    }

    ```

     Vergessen Sie nicht, `userpath` zu einem Dateinamen und einem Pfad zu wechseln, der auf Ihrem Computer sinnvoll ist.

2. Erstellen und Ausführen des Codes. Wenn die experimentelle Instanz von Visual Studio angezeigt wird, öffnen Sie eine Projekt Mappe. Dies bewirkt, dass die-Authentifizierung durch bewirkt `AsyncPackage` . Wenn der Initialisierer ausgeführt wurde, sollten Sie eine Datei in dem von Ihnen angegebenen Speicherort finden.

## <a name="use-an-asynchronous-service-in-a-command-handler"></a>Verwenden eines asynchronen Dienstanbieter in einem Befehls Handler
 Im folgenden finden Sie ein Beispiel für die Verwendung eines asynchronen Dienstanbieter in einem Menübefehl. Sie können den hier gezeigten Vorgang verwenden, um den Dienst in anderen nicht asynchronen Methoden zu verwenden.

1. Fügen Sie dem Projekt einen Menübefehl hinzu. (Wählen Sie im **Projektmappen-Explorer** den Projekt Knoten aus, klicken Sie mit der rechten Maustaste, und wählen Sie **Hinzufügen**  >  aus. **Neues Element**  >  **Erweiterbarkeit**  >  **Benutzerdefinierter Befehl**.) Benennen Sie die Befehlsdatei *TestAsyncCommand.cs*.

2. Die benutzerdefinierte Befehls Vorlage fügt die- `Initialize()` Methode der *TestAsyncPackage.cs* -Datei erneut hinzu, um den Befehl zu initialisieren. Kopieren Sie in der- `Initialize()` Methode die Zeile, in der der Befehl initialisiert wird. Diese sollte wie folgt aussehen:

    ```csharp
    TestAsyncCommand.Initialize(this);
    ```

     Verschieben Sie diese Zeile in die- `InitializeAsync()` Methode in der Datei *AsyncPackageForService.cs* . Da dies in einer asynchronen Initialisierung vorliegt, müssen Sie zum Haupt Thread wechseln, bevor Sie den Befehl mit initialisieren <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> . Dies sollte jetzt wie folgt aussehen:

    ```csharp

    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);

        ITextWriterService textService =
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;
        
        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");

        await this.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);
        TestAsyncCommand.Initialize(this);
    }

    ```

3. Löschen Sie die- `Initialize()` Methode.

4. Suchen Sie in der Datei *TestAsyncCommand.cs* die- `MenuItemCallback()` Methode. Löschen Sie den Text der-Methode.

5. Fügen Sie eine using-Anweisung hinzu:

    ```csharp
    using System.IO;
    ```

6. Fügen Sie eine asynchrone Methode mit dem Namen hinzu `UseTextWriterAsync()` , die den Dienst abruft und seine Methoden verwendet:

    ```csharp
    private async System.Threading.Tasks.Task UseTextWriterAsync()
    {
        // Query text writer service asynchronously to avoid a blocking call.
        ITextWriterService textService =
           await AsyncServiceProvider.GlobalProvider.GetServiceAsync(typeof(STextWriterService))
              as ITextWriterService;

        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");
       }

    ```

7. Diese Methode wird von der- `MenuItemCallback()` Methode aufgerufen:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        UseTextWriterAsync();
    }

    ```

8. Erstellen Sie die Projektmappe, und beginnen Sie mit dem Debuggen. Wenn die experimentelle Instanz von Visual Studio angezeigt wird, navigieren Sie zum Menü "Extras", und suchen Sie nach **dem Menü Element** " **testasynccommand aufrufen** ". Wenn Sie darauf klicken, schreibt der textschreibdienst in die angegebene Datei. (Sie müssen keine Projekt Mappe öffnen, da das Aufrufen des Befehls auch bewirkt, dass das Paket geladen wird.)

## <a name="see-also"></a>Weitere Informationen
- [Verwenden und Bereitstellen von Diensten](../extensibility/using-and-providing-services.md)
