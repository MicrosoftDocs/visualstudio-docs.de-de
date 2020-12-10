---
title: Verwenden von asyncpackage zum Laden von VSPackages im Hintergrund
description: Erfahren Sie, wie Sie die asyncpackage-Klasse verwenden, die das Laden von Paketen in einem Hintergrund Thread ermöglicht, was die Reaktionsfähigkeit von Datenträger-e/a verhindern kann.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
author: acangialosi
ms.author: anthc
ms.workload:
- vssdk
ms.openlocfilehash: e8b5917a42e7083f7357ce76762bf8b51a1b60f9
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "96993483"
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>Gewusst wie: Verwenden von asyncpackage zum Laden von VSPackages im Hintergrund
Das Laden und Initialisieren eines vs-Pakets kann zu Datenträger-e/a-Vorgängen führen. Wenn solche e/a-Vorgänge im UI-Thread durchgeführt werden, kann dies zu Reaktions Problemen führen. Um dies zu beheben, wurde in Visual Studio 2015 die-Klasse eingeführt, die das  <xref:Microsoft.VisualStudio.Shell.AsyncPackage> Laden von Paketen in einem Hintergrund Thread ermöglicht.

## <a name="create-an-asyncpackage"></a>Erstellen eines asyncpackage
 Sie können beginnen, indem Sie ein VSIX-Projekt (**Datei**  >  **Neues**  >  **Projekt**  >  **Visual c#**-  >  **Erweiterbarkeits**-  >  **VSIX-Projekt**) erstellen und dem Projekt ein VSPackage hinzufügen (Klicken Sie mit der rechten Maustaste auf das Projekt, und fügen Sie das   >  **neue Element**  >  **c#-Element**  >  **Erweiterbarkeit**  >  **Visual Studio-Paket** hinzu). Anschließend können Sie Ihre Dienste erstellen und diese Dienste zu Ihrem Paket hinzufügen.

1. Leiten Sie das Paket von ab <xref:Microsoft.VisualStudio.Shell.AsyncPackage> .

2. Wenn Sie Dienste bereitstellen, deren Abfragen möglicherweise dazu führen, dass das Paket geladen wird:

    Um Visual Studio mitzuteilen, dass das Paket für das Laden im Hintergrund sicher ist, und um dieses Verhalten zu abonnieren, <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> sollte die **allowsbackgroundload** -Eigenschaft im Attributkonstruktor auf true festgelegt werden.

   ```csharp
   [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]

   ```

    Um Visual Studio mitzuteilen, dass es sicher ist, dass der Dienst in einem Hintergrund Thread instanziiert werden kann, sollten Sie die- <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> Eigenschaft im <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> Konstruktor auf true festlegen.

   ```csharp
   [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]

   ```

3. Wenn Sie über UI-Kontexte laden, sollten Sie **packageautoloadflags. backgroundload** für den <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> oder den Wert (0x2) in den Flags angeben, die als Wert für den automatischen Lade Eintrag Ihres Pakets geschrieben wurden.

   ```csharp
   [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]

   ```

4. Wenn Sie die asynchrone Initialisierung durchführen möchten, sollten Sie überschreiben <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A> . Entfernen Sie die `Initialize()` von der VSIX-Vorlage bereitgestellte Methode. (Die- `Initialize()` Methode in **asyncpackage** ist versiegelt). Sie können eine beliebige Methode verwenden <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> , um dem Paket asynchrone Dienste hinzuzufügen.

    Hinweis: um aufzurufen `base.InitializeAsync()` , können Sie Ihren Quellcode ändern in:

   ```csharp
   await base.InitializeAsync(cancellationToken, progress);
   ```

5. Es ist nicht erforderlich, RPCs (Remote Prozedur Aufrufe) über den asynchronen Initialisierungs Code (in **initializeasync**) zu erstellen. Diese können auftreten, wenn Sie <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> direkt oder indirekt aufgerufen werden.  Wenn Synchronisierungs Lasten erforderlich sind, wird der UI-Thread mithilfe von blockiert <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> . Das standardmäßige Blockierungs Modell deaktiviert RPCs. Dies bedeutet Folgendes: Wenn Sie versuchen, eine RPC-Methode aus den Async-Tasks zu verwenden, wird ein Deadlock auftreten, wenn der UI-Thread selbst auf das Laden des Pakets wartet. Die allgemeine Alternative besteht darin, den Code ggf. in den UI-Thread zu Mars Hallen, indem er etwas ähnliches wie verbundene aufgabenfactory <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> oder einen anderen Mechanismus verwendet, der keinen RPC verwendet.  Verwenden Sie **threadhelper. Generic.** Call nicht, oder blockieren Sie in der Regel den aufrufenden Thread, der darauf wartet, zum UI-Thread zu gelangen.

    Hinweis: Sie sollten die Verwendung von **GetService** oder **QueryService** in der- `InitializeAsync` Methode vermeiden. Wenn Sie diese verwenden müssen, müssen Sie zuerst zum UI-Thread wechseln. Die Alternative ist die Verwendung <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> von aus dem **asyncpackage** (durch Umwandeln in <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider> ).

   C#: Erstellen eines asyncpackage:

```csharp
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]
public sealed class TestPackage : AsyncPackage
{
    protected override Task InitializeAsync(System.Threading.CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        this.AddService(typeof(SMyTestService), CreateService, true);
        return Task.FromResult<object>(null);
    }
}
```

## <a name="convert-an-existing-vspackage-to-asyncpackage"></a>Konvertieren eines vorhandenen VSPackages in asyncpackage
 Der Großteil der Arbeit entspricht dem Erstellen eines neuen **asyncpackage**. Führen Sie die obigen Schritte 1 bis 5 aus. Außerdem müssen Sie mit den folgenden Empfehlungen besonders vorsichtig vorgehen:

1. Denken Sie daran, die außer Kraft Setzung zu entfernen, die `Initialize` Sie in Ihrem Paket

2. Vermeiden von Deadlocks: in Ihrem Code könnten verborgene RPCs vorhanden sein. Dies geschieht nun in einem Hintergrund Thread. Stellen Sie sicher, dass Sie bei einem RPC (z. b. **GetService**) entweder (1) zum Haupt Thread wechseln müssen, oder (2) verwenden Sie die asynchrone Version der API, sofern vorhanden (z. b. **getserviceasync**).

3. Wechseln Sie nicht zu häufig zwischen Threads. Versuchen Sie, die Arbeit zu lokalisieren, die in einem Hintergrund Thread auftreten kann, um die Ladezeit zu verringern.

## <a name="querying-services-from-asyncpackage"></a>Abfragen von Diensten von asyncpackage
 Ein **asyncpackage** kann abhängig vom Aufrufer asynchron geladen werden. Beispiel:

- Wenn der Aufrufer **GetService** oder **QueryService** (synchrone APIs) oder

- Wenn der Aufrufer **IVsShell:: LoadPackage** (oder **IVsShell5:: loadpackagewithcontext**) oder

- Die Auslastung wird durch einen UI-Kontext ausgelöst, aber Sie haben nicht angegeben, dass der UI-Kontext Mechanismus Sie asynchron laden kann.

  Anschließend wird das Paket synchron geladen.

  Das Paket hat weiterhin die Möglichkeit (in der asynchronen Initialisierungsphase), den UI-Thread zu bearbeiten, obwohl der UI-Thread für den Abschluss der Arbeit blockiert wird. Wenn der Aufrufer **iasyncserviceprovider** verwendet, um den Dienst asynchron abzufragen, werden die Auslastung und Initialisierung asynchron ausgeführt, wenn Sie das resultierende Aufgaben Objekt nicht sofort blockieren.

  C#: Asynchrones Abfragen des Diensts:

```csharp
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Interop;

IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;
IMyTestService testService = await asyncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;
```
