---
title: Projekt Konfigurationsobjekt | Microsoft-Dokumentation
description: Erfahren Sie, wie das Projekt Konfigurationsobjekt die Anzeige von Konfigurationsinformationen für die Benutzeroberfläche verwaltet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4d91f640abc4fd91b68341e825b312b8bfb0d6f6
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875491"
---
# <a name="project-configuration-object"></a>Projektkonfigurationsobjekt
Das Projekt Konfigurationsobjekt verwaltet die Anzeige der Konfigurationsinformationen für die Benutzeroberfläche.

 ![Visual Studio-Projekt Konfiguration](../../extensibility/internals/media/vsprojectcfg.gif "vsprojectcfg") Eigenschaften Seiten für die Projekt Konfiguration

 Der Projekt Konfigurations Anbieter verwaltet die Projekt Konfigurationen. Die Umgebung und andere Pakete, um Zugriff auf die und das Abrufen von Informationen über die Konfigurationen eines Projekts zu erhalten, rufen Sie die Schnittstellen auf, die an das Projekt Konfigurations Anbieter Objekt angefügt

> [!NOTE]
> Projektmappenkonfigurationsdateien können nicht Programm gesteuert erstellt oder bearbeitet werden. Hierzu muss `DTE.SolutionBuilder` verwendet werden. Weitere [](../../extensibility/internals/solution-configuration.md) Informationen finden Sie unter Projektmappenkonfiguration.

 Um einen anzeigen Amen zu veröffentlichen, der in der Konfigurations Benutzeroberfläche verwendet werden soll, sollte das Projekt implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A> . Die-Umgebung Ruft auf <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> , wodurch eine Liste von Zeigern zurückgegeben wird, die `IVsCfg` Sie verwenden können, um die anzeigen Amen für die Konfigurations-und Platt Form Informationen zu erhalten, die in der Benutzeroberfläche der Umgebung aufgeführt werden Die aktive Konfiguration und Plattform werden durch die Konfiguration des Projekts festgelegt, die in der aktiven Projektmappenkonfiguration gespeichert ist. Die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> Methode kann verwendet werden, um die aktive Projekt Konfiguration abzurufen.

 Das-Objekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> kann optional für das-Objekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> mit dem-Objekt implementiert werden <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> , damit Sie ein `IVsProjectCfg2` Objekt basierend auf dem Namen der kanonischen Projekt Konfiguration abrufen können.

 Eine andere Möglichkeit, die Umgebung und andere Projekte mit Zugriff auf Projekt Konfigurationen bereitzustellen, besteht darin, dass-Projekte eine Implementierung der-Methode bereitstellen `IVsCfgProvider2::GetCfgs` , um mindestens ein Konfigurationsobjekt zurückzugeben. Die Projekte können auch implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> , das von `IVsProjectCfg` und somit von erbt `IVsCfg` , um Konfigurations spezifische Informationen bereitzustellen. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> unterstützt Plattformen und Funktionen zum Hinzufügen, löschen und Umbenennen von Projekt Konfigurationen.

> [!NOTE]
> Da Visual Studio nicht mehr auf zwei Konfigurationstypen beschränkt ist, sollte der Code, der Konfigurationen verarbeitet, nicht mit Annahmen über die Anzahl der Konfigurationen geschrieben werden, und er sollte nicht mit der Annahme geschrieben werden, dass ein Projekt, das nur über eine Konfiguration verfügt, notwendigerweise entweder Debug oder Retail ist. Dadurch wird die Verwendung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> und als <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> veraltet markiert.

 Durch Aufrufen von `QueryInterface` für das von zurückgegebene Objekt wird `IVsGetCfgProvider::GetCfgProvider` abgerufen `IVsCfgProvider2` . Wenn `IVsGetCfgProvider` nicht gefunden wird, indem für `QueryInterface` das `IVsProject3` Project-Objekt aufgerufen wird, können Sie auf das Konfigurations Anbieter Objekt zugreifen, indem Sie für `QueryInterface` das Hierarchie Stamm Browser-Objekt für das-Objekt aufrufen, das für zurückgegeben `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)` wurde, oder durch einen Zeiger auf den für zurückgegebenen Konfigurations Anbieter `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`

 `IVsProjectCfg2` bietet primär Zugriff auf Build-, Debug-und bereitstellungsverwaltungsobjekte und ermöglicht es Projekten, Ausgaben zu gruppieren. Die-Methoden von `IVsProjectCfg` und `IVsProjectCfg2` können zur Implementierung von verwendet werden <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> , um den Buildprozess zu verwalten, und <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> Zeiger für die Ausgabe Gruppen einer Konfiguration.

 Das Projekt muss die gleiche Anzahl von Gruppen für jede Konfiguration zurückgeben, die unterstützt wird, obwohl die Anzahl der in einer Gruppe enthaltenen Ausgaben von der Konfiguration bis zur Konfiguration abweichen kann. Die Gruppen müssen auch die gleichen Bezeichnerinformationen (Kanonischer Name, Anzeige Name und Gruppeninformationen) aufweisen, von der Konfiguration bis zur Konfiguration innerhalb eines Projekts. Weitere Informationen finden Sie unter [Projekt Konfiguration für die Ausgabe](../../extensibility/internals/project-configuration-for-output.md).

 Um das Debuggen zu aktivieren, sollten Ihre Konfigurationen implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> . `IVsDebuggableProjectCfg` ist eine optionale Schnittstelle, die von-Projekten implementiert wird, damit der Debugger eine-Konfiguration starten kann und für das Konfigurationsobjekt mit und implementiert wird `IVsCfg` `IVsProjectCfg` . Die Umgebung ruft Sie auf, wenn der Benutzer die Option zum Starten des Debuggers durch Drücken von F5 wählt.

 `ISpecifyPropertyPages` und `IDispatch` werden zusammen mit Eigenschaften Seiten verwendet, um dem Benutzer Konfigurations abhängige Informationen abzurufen und anzuzeigen. Weitere Informationen finden Sie unter [Eigenschaften Seiten](../../extensibility/internals/property-pages.md).

## <a name="see-also"></a>Weitere Informationen
- [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md)
- [Projektkonfiguration beim Erstellen](../../extensibility/internals/project-configuration-for-building.md)
- [Projektkonfiguration für die Ausgabe](../../extensibility/internals/project-configuration-for-output.md)
- [Eigenschaftenseiten](../../extensibility/internals/property-pages.md)
- [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md)
