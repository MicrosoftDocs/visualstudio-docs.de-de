---
title: UpdateManifestForBrowserApplication-Aufgabe | Microsoft-Dokumentation
description: Erfahren Sie, wie MSBuild die Aufgabe „UpdateManifestForBrowserApplication“ ausführt, um dem Anwendungsmanifest das Element „hostInBrowser“ hinzuzufügen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UpdateManifestForBrowserApplication task [WPF MSBuild]
- adding the <hostInBrowser /> element to the application manifest [WPF MSBuild]
- building XBAP projects [WPF MSBuild]
- UpdateManifestForBrowserApplication task [WPF MSBuild], parameters
ms.assetid: 653339f7-654b-4d64-a26a-5c9f27036895
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9e71e11988d4dd853b0f97c745b6d720a45adcdc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961546"
---
# <a name="updatemanifestforbrowserapplication-task"></a>UpdateManifestForBrowserApplication-Aufgabe

Der Task <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> wird ausgeführt, um dem Anwendungsmanifest ( *\<projectname>.exe.manifest*) das Element **\<hostInBrowser />** hinzuzufügen, wenn ein XAML-Browseranwendungsprojekt (XBAP) erstellt wird.

## <a name="task-parameters"></a>Aufgabenparameter

|Parameter|Beschreibung|
|---------------|-----------------|
|`ApplicationManifest`|Erforderlicher **ITaskItem[]** -Parameter.<br /><br /> Gibt den Pfad und den Namen der Anwendungsmanifestdatei an, der Sie das `<hostInBrowser />` Element hinzufügen möchten.|
|`HostInBrowser`|Erforderlicher **boolescher** Parameter.<br /><br /> Gibt an, ob das Anwendungsmanifest geändert werden soll, um das **\<hostInBrowser />** -Element einzufügen. Wenn **true**, ist ein neues **\<hostInBrowser />** -Element im **\<entryPoint />** -Element enthalten. Der Einschluss von Elementen ist kumulativ: Wenn ein **\<hostInBrowser />** -Element bereits vorhanden ist, wird es weder entfernt noch überschrieben. Stattdessen wird ein zusätzliches **\<hostInBrowser />** -Element erstellt. Wenn **false**, dann ist das Anwendungsmanifest nicht geändert.|

## <a name="remarks"></a>Hinweise

 XBAPs werden mithilfe der ClickOnce-Bereitstellung ausgeführt und müssen aus diesem Grund mit unterstützenden Bereitstellungs- und Anwendungsmanifesten veröffentlicht werden. MSBuild verwendet die [GenerateApplicationManifest](generateapplicationmanifest-task.md)-Aufgabe zum Generieren eines Anwendungsmanifests.

 Anschließend muss ein zusätzliches Element, **\<hostInBrowser />** , dem Anwendungsmanifest hinzugefügt werden, um eine Anwendung zu konfigurieren, die von einem Browser gehostet wird, wie im folgenden Beispiel gezeigt:

```xml
<!--MyXBAPApplication.exe.manifest-->
<?xml version="1.0" encoding="utf-8"?>
<asmv1:assembly ... >
    <asmv1:assemblyIdentity ... />
    <application />
    <entryPoint>
      ...
      <hostInBrowser xmlns="urn:schemas-microsoft-com:asm.v3" />
    </entryPoint>
  ...
/>
```

 Die Aufgabe <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> wird ausgeführt, wenn ein XBAP-Projekt erstellt wird, um das `<hostInBrowser />`-Element hinzuzufügen.

## <a name="example"></a>Beispiel

 Das folgende Beispiel zeigt, wie Sie sicherstellen, dass das `<hostInBrowser />`-Element in eine Anwendungsmanifestdatei eingefügt wird.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="UpdateManifestForBrowserApplicationTask">
    <UpdateManifestForBrowserApplication
      ApplicationManifest="MyXBAPApplication.exe.manifest"
      HostInBrowser="true" />
  </Target>
</Project>
```

## <a name="see-also"></a>Siehe auch

- [WPF-MSBuild-Referenz](../msbuild/wpf-msbuild-reference.md)
- [Referenz zu MSBuild-Tasks](../msbuild/wpf-msbuild-task-reference.md)
- [MSBuild-Referenz](../msbuild/msbuild-reference.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
- [Erstellen einer WPF-Anwendung (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Übersicht über WPF-XAML-Browseranwendungen](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)