---
title: VSPackages werden geladen | Microsoft-Dokumentation
description: Erfahren Sie mehr über das Laden von VSPackages in Visual Studio, einschließlich des verzögerten Ladens, das nach Möglichkeit verwendet wird, um die Leistung zu steigern.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f87b5bcc94ed11e18de763bd1db7c59bdc4796fc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966382"
---
# <a name="load-vspackages"></a>VSPackages laden
VSPackages werden nur dann in Visual Studio geladen, wenn ihre Funktionalität erforderlich ist. Beispielsweise wird ein VSPackage geladen, wenn Visual Studio eine projektfactory oder einen Dienst verwendet, den das VSPackage implementiert. Diese Funktion wird als verzögertes Laden bezeichnet und wird nach Möglichkeit verwendet, um die Leistung zu verbessern.

> [!NOTE]
> Visual Studio kann bestimmte VSPackage-Informationen wie die von einem VSPackage angebotenen Befehle ermitteln, ohne das VSPackage zu laden.

 VSPackages können in einem bestimmten Benutzeroberflächen Kontext auf "AutoLoad" festgelegt werden, z. b. Wenn eine Projekt Mappe geöffnet ist. Das- <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> Attribut legt diesen Kontext fest.

### <a name="autoload-a-vspackage-in-a-specific-context"></a>Autoload ein VSPackage in einem bestimmten Kontext

- Fügen Sie dem `ProvideAutoLoad` VSPackage-Attribut das-Attribut hinzu:

    ```csharp
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID
    public class MyAutoloadedPackage : Package
    {. . .}
    ```

     <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>Eine Liste der Benutzeroberflächen Kontexte und ihrer GUID-Werte finden Sie in den aufgelisteten Feldern von.

- Legen Sie einen Haltepunkt in der- <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> Methode fest.

- Erstellen Sie das VSPackage, und starten Sie das Debugging.

- Laden Sie eine Projekt Mappe, oder erstellen Sie eine.

     Das VSPackage wird am Haltepunkt geladen und angehalten.

## <a name="force-a-vspackage-to-load"></a>Laden eines VSPackage erzwingen
 Unter bestimmten Umständen kann ein VSPackage erzwingen, dass ein anderes VSPackage geladen wird. Beispielsweise kann ein VSPackage mit einfachem VSPackage in einem Kontext, der nicht als cmduicontext verfügbar ist, ein größeres VSPackage laden.

 Sie können die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> Methode verwenden, um das Laden eines VSPackages zu erzwingen.

- Fügen Sie diesen Code in die- <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> Methode des VSPackage ein, das ein anderes VSPackage erzwingt, das geladen werden soll:

    ```csharp
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;
    if (shell == null) return;

    IVsPackage package = null;
    Guid PackageToBeLoadedGuid =
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);

    ```

     Wenn das VSPackage initialisiert ist, wird das `PackageToBeLoaded` Laden erzwungen.

     Das Erzwingen von Ladevorgängen sollte nicht für die VSPackage-Kommunikation verwendet werden. Verwenden Sie stattdessen, [und stellen Sie Dienste bereit](../extensibility/using-and-providing-services.md) .

## <a name="see-also"></a>Weitere Informationen
- [VSPackages](../extensibility/internals/vspackages.md)
