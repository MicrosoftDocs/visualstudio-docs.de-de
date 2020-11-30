---
title: Benutzerdefinierte Benutzeroberfläche (Quellcodeverwaltungs-VSPackage) | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eine benutzerdefinierte Benutzeroberfläche (UI) in Visual Studio erstellen, indem Sie ein Quellcodeverwaltungs-VSPackage zum Angeben von UI-Elementen verwenden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e1426b271ea8db4d486043c9fbe885a0f428b514
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2020
ms.locfileid: "96328521"
---
# <a name="custom-user-interface-source-control-vspackage"></a>Benutzerdefinierte Benutzeroberfläche (Quellcodeverwaltungs-VSPackage)
Ein VSPackage deklariert seine Menü Elemente und deren Standardzustände über die Visual Studio-Befehls Tabellen Datei (*vsct*). [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]In der integrierten Entwicklungsumgebung (IDE) werden die Menü Elemente in Ihren Standard Zuständen angezeigt, bis das VSPackage geladen wurde. Anschließend wird die- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode aufgerufen, um Menü Elemente zu aktivieren oder zu deaktivieren.

 Ein VSPackage kann einen Registrierungsschlüssel festlegen, sodass das VSPackage automatisch in Abhängigkeit von einem Befehls Benutzeroberflächen Kontext geladen werden kann. in der Regel sollte ein VSPackage für die Quell Code Verwaltung Bedarfs gesteuert geladen werden, anstatt einfach zu einem bestimmten UI-Kontext zu wechseln. Weitere Informationen zum Registrierungsschlüssel " **autoloadpackages** " finden Sie unter [Verwalten von VSPackages](../../extensibility/managing-vspackages.md).

## <a name="vspackage-ui"></a>VSPackage-Benutzeroberfläche
 Ein Quell Code Verwaltungspaket wird als VSPackage implementiert, und es wird keine Benutzeroberfläche von verwendet [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Jedes VSPackage für die Quell Code Verwaltung muss eigene Benutzeroberflächen Elemente angeben, z. b. Menü Elemente, Menü Gruppen, Tool Fenster, Symbolleisten und jede erforderliche Benutzeroberfläche zum Festlegen spezifischer Optionen für das VSPackage der Quell Code Verwaltung. Diese Elemente der Benutzeroberfläche können statisch oder dynamisch aktiviert werden. Statische Benutzeroberflächen Elemente werden in einer *vsct* -Datei definiert und werden angezeigt, unabhängig davon, ob das VSPackage geladen wurde. Dynamische Benutzeroberflächen Elemente sind möglicherweise abhängig von einem bestimmten Befehls Benutzeroberflächen Kontext (z. b.) <xref:EnvDTE.Constants.vsContextNoSolution> oder als Ergebnis eines Aufrufes der- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode sichtbar. Die Sichtbarkeit dynamischer Elemente der Benutzeroberfläche entspricht der Strategie für das verzögerte Laden von VSPackages.

## <a name="ui-constraints-on-source-control-vspackages"></a>UI-Einschränkungen für Quellcodeverwaltungs-VSPackages
 Da das VSPackage der Quell Code Verwaltung nicht aus der IDE entfernt werden kann, nachdem es geladen wurde, muss das VSPackage in der Lage sein, in den inaktiven Zustand zu wechseln. Wenn ein VSPackage benachrichtigt, dass es nicht mehr aktiv ist, deaktiviert das VSPackage die Benutzeroberfläche und ignoriert jegliche externe IDE-Interaktion. Die VSPackage-Implementierung der- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode sollte Befehle ausblenden, wenn das VSPackage nicht aktiv ist.

 Jedes VSPackage der Quell Code Verwaltung muss die- `IVsSccProvider` Schnittstelle implementieren. Zwei Methoden für die-Schnittstelle, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A> , müssen durch das VSPackage implementiert werden.

 Das VSPackage der Quell Code Verwaltung hat möglicherweise verschiedene IDE-Ereignisse abonniert, die von <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> , <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> usw. implementiert werden. Außerdem kann das VSPackage Registrierungs aktivierte Rückruf Schnittstellen implementiert haben, z <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> . b.. Diese Schnittstellen müssen alle ignoriert werden, wenn Sie inaktiv sind.

 Die folgende Liste zeigt die Schnittstellen, die vom aktiven Zustand eines VSPackage für die Quell Code Verwaltung betroffen sind:

- Nachverfolgen von Projekt Dokumenten Ereignissen.

- Projektmappenereignisse.

- Schnittstellen für Lösungs Persistenz. Wenn inaktiv, sollten Pakete nicht in *sln* -und *suo* -Dateien schreiben.

- Eigenschaftenextender.

  Die erforderlichen <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> sowie alle optionalen Schnittstellen, die der Quell Code Verwaltung zugeordnet sind, werden nicht aufgerufen, wenn das VSPackage der Quell Code Verwaltung inaktiv ist.

  Wenn die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE gestartet wird, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] legt den Befehls Benutzeroberflächen Kontext auf die ID der aktuellen VSPackage-ID der Standard Quell Code Verwaltung fest. Dies bewirkt, dass die statische Benutzeroberfläche des aktiven Quell Code Verwaltungs-VSPackage in der IDE angezeigt wird, ohne das VSPackage tatsächlich zu laden. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hält das VSPackage für die Registrierung bei [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] über an, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> bevor das VSPackage aufgerufen wird.

  In der folgenden Tabelle werden spezifische Details dazu beschrieben, wie die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE verschiedene Elemente der Benutzeroberfläche ausblendet.

| UI-Element | BESCHREIBUNG |
| - | - |
| Menüs und Symbolleisten | Das Quell Code Verwaltungspaket muss das anfängliche Menü und die Sichtbarkeit der Symbolleiste auf die ID des Quell Code Verwaltungs Pakets im Abschnitt [visibilityeinschränkungs](../../extensibility/visibilityconstraints-element.md) der *vsct* -Datei festlegen. Dies ermöglicht der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, den Zustand der Menü Elemente entsprechend festzulegen, ohne das VSPackage zu laden und eine Implementierung der-Methode aufzurufende <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> . |
| Toolfenster | Das VSPackage der Quell Code Verwaltung Blendet alle Tool Fenster aus, die es besitzt, wenn es inaktiv ist. |
| Quellcodeverwaltungs-VSPackage-spezifische Options Seiten | Mit dem Registrierungsschlüssel " **hklm\software\microsoft\visualstudio\x.y\toolsoptionspages\visibilitycmduicontexts** " kann ein VSPackage die Kontexte festlegen, in denen die Options Seiten angezeigt werden müssen. Ein Registrierungs Eintrag unter diesem Schlüssel muss mithilfe der Dienst-ID (SID) des Quell Code Verwaltungs Dienstanbieter erstellt werden, und ihm muss ein DWORD-Wert von 1 zugewiesen werden. Wenn ein UI-Ereignis in einem Kontext auftritt, bei dem das VSPackage der Quell Code Verwaltung bei registriert ist, wird das VSPackage aufgerufen, wenn es aktiv ist. |

## <a name="see-also"></a>Siehe auch
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>
- <xref:EnvDTE.Constants.vsContextNoSolution>
- [Verwalten von VSPackages](../../extensibility/managing-vspackages.md)
