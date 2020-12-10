---
title: 'Vorgehensweise: Get a Service | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie Visual Studio-Dienste für den Zugriff auf verschiedene Features erhalten. Sie können die meisten Dienste mithilfe eines VSPackages erhalten.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0a8f97900f1d400f3208a24ccc45ff9bbd774aeb
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994081"
---
# <a name="how-to-get-a-service"></a>Vorgehensweise: erhalten eines Dienstanbieter

Häufig müssen Sie Visual Studio-Dienste für den Zugriff auf verschiedene Features abrufen. Im Allgemeinen stellt ein Visual Studio-Dienst eine oder mehrere Schnittstellen bereit, die Sie verwenden können. Sie können die meisten Dienste von einem VSPackage erhalten.

Jedes VSPackage, das von abgeleitet <xref:Microsoft.VisualStudio.Shell.Package> ist und ordnungsgemäß positioniert wurde, kann ggf. einen beliebigen globalen Dienst anfordern. Da die- `Package` Klasse implementiert <xref:System.IServiceProvider> , ist jedes VSPackage, das von abgeleitet `Package` wird, auch ein Dienstanbieter.

Wenn Visual Studio eine lädt <xref:Microsoft.VisualStudio.Shell.Package> , übergibt Sie <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> während der Initialisierung ein Objekt an die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> Methode. Dies *wird als "* VSPackage" bezeichnet. Die `Package` Klasse umschließt diesen Dienstanbieter und stellt die <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> Methode zum erhalten von Diensten bereit.

## <a name="getting-a-service-from-an-initialized-vspackage"></a>Dienst von einem initialisierten VSPackage erhalten

1. Jede Visual Studio-Erweiterung beginnt mit einem VSIX-Bereitstellungs Projekt, das die Erweiterungs Ressourcen enthält. Erstellen Sie ein [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX-Projekt mit dem Namen `GetServiceExtension` . Sie finden die VSIX-Projektvorlage im Dialogfeld " **Neues Projekt** ", indem Sie nach "VSIX" suchen.

2. Fügen Sie nun eine benutzerdefinierte Befehls Element Vorlage mit dem Namen **getservicecommand** hinzu. Navigieren Sie im Dialogfeld **Neues Element hinzufügen** zu **Visual c#**  >  -**Erweiterbarkeit** , und wählen Sie **benutzerdefinierter Befehl** aus. Ändern Sie im Feld **Name** am unteren Rand des Fensters den Namen der Befehlsdatei in *GetServiceCommand.cs*. Weitere Informationen zum Erstellen eines benutzerdefinierten Befehls finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md) .

3. Entfernen Sie in *GetServiceCommand.cs* den Text der `MenuItemCommand` -Methode, und fügen Sie den folgenden Code hinzu:

   ```csharp
   IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;
   if (activityLog == null) return;
   System.Windows.Forms.MessageBox.Show("Found the activity log service.");

   ```

    Mit diesem Code wird ein SVsActivityLog-Dienst abgerufen und in eine- <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> Schnittstelle umgewandelt, die zum Schreiben in das Aktivitätsprotokoll verwendet werden kann. Ein Beispiel finden Sie unter Gewusst [wie: Verwenden des Aktivitäts Protokolls](../extensibility/how-to-use-the-activity-log.md).

4. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz wird geöffnet.

5. Suchen Sie **im Menü Extras** der experimentellen Instanz nach der Schaltfläche **getservicecommand aufrufen** . Wenn Sie auf diese Schaltfläche klicken, wird ein Meldungs Feld mit dem Hinweis angezeigt, dass **der Aktivitätsprotokoll Dienst gefunden wurde.**

## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>Dienst von einem Tool Fenster oder Steuerelement Container

Manchmal müssen Sie möglicherweise einen Dienst von einem Tool Fenster oder einem Steuerelement Container erhalten, der nicht mit der sitsierung vertraut ist, oder wenn Sie mit einem Dienstanbieter vertraut sind, der den gewünschten Dienst nicht kennt. Beispielsweise können Sie in einem-Steuerelement in das Aktivitätsprotokoll schreiben.

Die statische- <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> Methode basiert auf einem zwischengespeicherten Dienstanbieter, der initialisiert wird, wenn ein von abgeleitetes VSPackage das erste Mal <xref:Microsoft.VisualStudio.Shell.Package> ist.

Da der VSPackage-Konstruktor aufgerufen wird, bevor das VSPackage positioniert ist, sind globale Dienste in der Regel innerhalb des VSPackage-Konstruktors nicht verfügbar. Weitere Informationen finden [Sie unter Gewusst wie:](../extensibility/how-to-troubleshoot-services.md) Problembehandlung bei Diensten.

Im folgenden finden Sie ein Beispiel für die Art und Weise, wie ein Dienst in einem Tool Fenster oder einem anderen nicht-VSPackage-Element angezeigt wird.

```csharp
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="getting-a-service-from-the-dte-object"></a>Erhalten eines dienstanaus dem DTE-Objekt

Sie können auch Dienste aus dem <xref:EnvDTE.DTEClass> Objekt erhalten. Allerdings müssen Sie das DTE-Objekt als Dienst aus einem VSPackage oder durch Aufrufen der statischen- <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> Methode abrufen.

Das DTE-Objekt implementiert <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> , das Sie verwenden können, um einen Dienst mithilfe von abzufragen <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> .

So erhalten Sie einen Dienst aus dem DTE-Objekt.

```csharp
// Start with the DTE object, for example: 
// using EnvDTE;
// DTE dte = (DTE)GetService(typeof(DTE));

ServiceProvider sp = new ServiceProvider((Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);
if (sp != null)
{
    IVsActivityLog log = sp.GetService(typeof(SVsActivityLog)) as IVsActivityLog;
    if (log != null)
    {
        System.Windows.Forms.MessageBox.Show("Found the activity log service.");
    }
}
```

## <a name="see-also"></a>Weitere Informationen

- [Vorgehensweise: Bereitstellen eines Dienstanbieter](../extensibility/how-to-provide-a-service.md)
- [Verwenden und Bereitstellen von Diensten](../extensibility/using-and-providing-services.md)
- [Service Essentials](../extensibility/internals/service-essentials.md)
