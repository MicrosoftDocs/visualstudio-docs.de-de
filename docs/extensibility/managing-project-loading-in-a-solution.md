---
title: Verwalten des Laden von Projekten in einer Projekt Mappe | Microsoft-Dokumentation
description: Erfahren Sie, wie Entwickler Ladezeiten von Projektmappen reduzieren und das Ladeverhalten von Projekten verwalten können, indem Sie einen Solution Load Manager erstellen
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 093db17990d538bf72ddeab9ba9da2b8db30d8f0
ms.sourcegitcommit: d485b18e46ec4cf08704b5a8d0657bc716ec8393
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2020
ms.locfileid: "97616356"
---
# <a name="manage-project-loading-in-a-solution"></a>Verwalten des Laden von Projekten in einer Projekt Mappe
Visual Studio-Projektmappen können eine große Anzahl von Projekten enthalten. Das Standardverhalten von Visual Studio besteht darin, alle Projekte in einer Projekt Mappe zu dem Zeitpunkt zu laden, zu dem die Projekt Mappe geöffnet wird, und nicht, um dem Benutzer den Zugriff auf Projekte zu gestatten, bis alle Elemente vollständig geladen wurden. Wenn der Ladevorgang für das Projekt mehr als zwei Minuten dauert, wird eine Statusanzeige angezeigt, in der die Anzahl der geladenen Projekte und die Gesamtzahl der Projekte angezeigt wird. Der Benutzer kann Projekte bei der Arbeit in einer Projekt Mappe mit mehreren Projekten entladen, aber dieses Verfahren hat einige Nachteile: die entladenen Projekte werden nicht als Teil des Befehls "Rebuild Solution" erstellt, und IntelliSense-Beschreibungen von Typen und Membern geschlossener Projekte werden nicht angezeigt.

 Entwickler können die Ladezeiten von Projektmappen reduzieren und das Ladeverhalten von Projekten verwalten, indem Sie einen Projektmappen- Der projektmappenload-Manager kann sicherstellen, dass Projekte vor dem Starten eines hintergrundbuilds geladen werden, das Laden im Hintergrund verzögert wird, bis andere Hintergrundaufgaben vollständig sind, und andere Aufgaben zum Laden von Projekten ausführen

## <a name="create-a-solution-load-manager"></a>Erstellen eines projektmappenlade-Managers
 Entwickler können einen projektmappenload-Manager erstellen, indem Sie Visual Studio implementieren und angleichen, dass der Projektmappen- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> Load Manager aktiv

### <a name="activate-a-solution-load-manager"></a>Aktivieren eines projektmappenlade-Managers
 Visual Studio ermöglicht nur einen projektmappenload-Manager zu einem bestimmten Zeitpunkt. Daher müssen Sie Visual Studio anweisen, wenn Sie den Projektmappen-Load Manager aktivieren möchten. Wenn ein zweiter projektmappenload-Manager später aktiviert wird, wird der Projektmappen-Load Manager getrennt.

 Sie müssen den <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> Dienst erhalten und den [__VSPROPID4 festlegen. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) -Eigenschaft:

```csharp
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;
object objLoadMgr = this;   //the class that implements IVsSolutionManager
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);
```

 Die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> Methode wird entweder aufgerufen, wenn Visual Studio heruntergefahren wird oder wenn ein anderes Paket als aktiver projektmappenload-Manager übernommen wurde, indem <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> mit dem-__VSPROPID4 aufgerufen wird [. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) -Eigenschaft.

#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Strategien für verschiedene Arten von Lösung Load Manager
 Sie können projektmappenlade-Manager je nach Art der Lösungen, die Sie verwalten möchten, auf unterschiedliche Weise implementieren.

 Wenn der projektmappenload-Manager im Allgemeinen das Laden von Projektmappen verwalten soll, kann er als Teil eines VSPackage implementiert werden. Das Paket sollte auf "AutoLoad" festgelegt werden, indem Sie <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> für das VSPackage mit dem Wert hinzufügen <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid> . Der projektmappenload-Manager kann dann in der-Methode aktiviert werden <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> .

> [!NOTE]
> Weitere Informationen zu automatischen Paketen finden Sie unter Laden von [VSPackages](../extensibility/loading-vspackages.md).

 Da Visual Studio nur den letzten projektmappenload-Manager erkennt, der aktiviert werden soll, sollten allgemeine projektmappenload-Manager immer erkennen, ob ein Lasten-Manager vorhanden ist, bevor Sie sich selbst aktivieren , Wenn `GetProperty()` für den Lösungs Dienst für [__VSPROPID4 aufgerufen wird. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) gibt zurück `null` , dass kein aktiver projektmappenload-Manager vorhanden ist. Wenn keine NULL-Werte zurückgegeben werden, überprüfen Sie, ob das Objekt dem projektmappenload-Manager entspricht.

 Wenn der projektmappenload-Manager nur wenige Arten von Projektmappen verwalten soll, kann das VSPackage projektmappenlade-Ereignisse abonnieren (durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> ) und den-Ereignishandler für verwenden, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> um den projektmappenlade-Manager zu aktivieren.

 Wenn der projektmappenload-Manager nur bestimmte Lösungen verwalten soll, können die Aktivierungs Informationen als Teil der Projektmappendatei beibehalten werden, indem <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> für den Abschnitt vorab Lösung aufgerufen wird.

 Bestimmte projektmappenload-Manager sollten sich selbst im <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> Ereignishandler deaktivieren, damit kein Konflikt mit anderen projektmappenlade-Managern auftritt.

 Wenn Sie einen projektmappenload-Manager benötigen, um globale Projekt Ladeeigenschaften beizubehalten (z. b. auf einer Options Seite festgelegte Eigenschaften), können Sie den projektmappenload-Manager im <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> Ereignishandler aktivieren, die Einstellung in den Projektmappeneigenschaften beibehalten und dann den Projektmappen-Lasten-Manager deaktivieren.

## <a name="handle-solution-load-events"></a>Behandeln von projektmappenlade Ereignissen
 Um Projektmappen-Lade Ereignisse zu abonnieren, wenden Sie an, wenn Sie den Projektmappen- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> Load Manager Wenn Sie implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents> , können Sie auf Ereignisse reagieren, die sich auf verschiedene Projekt Ladeeigenschaften beziehen.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Dieses Ereignis wird ausgelöst, bevor eine Projekt Mappe geöffnet wird.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Dieses Ereignis wird ausgelöst, nachdem die Projekt Mappe vollständig geladen wurde, aber bevor das Laden im Hintergrund wiederholt wird.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Dieses Ereignis wird ausgelöst, nachdem eine Projekt Mappe anfänglich vollständig geladen wurde, unabhängig davon, ob ein projektmappenload-Manager vorhanden ist. Sie wird auch ausgelöst, wenn die Projekt Mappe vollständig geladen wird, nachdem die Projekt Mappe vollständig geladen wurde. Gleichzeitig <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> wird erneut aktiviert.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Dieses Ereignis wird ausgelöst, bevor ein Projekt (oder Projekte) geladen wird. Um sicherzustellen, dass andere Hintergrundprozesse abgeschlossen sind, bevor die Projekte geladen werden, legen `pfShouldDelayLoadToNextIdle` Sie auf **true** fest.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Dieses Ereignis wird ausgelöst, wenn ein Batch von Projekten geladen wird. Wenn `fIsBackgroundIdleBatch` true ist, werden die Projekte im Hintergrund geladen. Wenn `fIsBackgroundIdleBatch` false ist, werden die Projekte als Ergebnis einer Benutzer Anforderung synchron geladen, z. b. wenn der Benutzer ein ausstehendes Projekt in Projektmappen-Explorer erweitert. Sie können dieses Ereignis verarbeiten, um aufwändige Aufgaben durchzuführen, die andernfalls in ausgeführt werden müssen <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> .

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Dieses Ereignis wird ausgelöst, nachdem ein Batch von Projekten geladen wurde.

## <a name="detect-and-manage-solution-and-project-loading"></a>Erkennen und Verwalten von Projektmappen und Projekten
 Um den Ladestatus von Projekten und Projektmappen zu ermitteln, müssen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> mit den folgenden Werten aufzurufen:

- [__VSPROPID4. VSPROPID_IsSolutionFullyLoaded](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsSolutionFullyLoaded>): `var` gibt zurück `true` , wenn die Projekt Mappe und alle zugehörigen Projekte geladen werden, andernfalls `false` .

- [__VSPROPID4. VSPROPID_IsInBackgroundIdleLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInBackgroundIdleLoadProjectBatch>): `var` gibt zurück `true` , wenn ein Batch von Projekten gegenwärtig im Hintergrund geladen wird; andernfalls `false` .

- [__VSPROPID4. VSPROPID_IsInSyncDemandLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInSyncDemandLoadProjectBatch>): `var` gibt zurück `true` , wenn ein Batch von Projekten momentan aufgrund eines Benutzer Befehls oder einer anderen expliziten Auslastung synchron geladen wird; andernfalls `false` .

- [__VSPROPID2. VSPROPID_IsSolutionClosing](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2.VSPROPID_IsSolutionClosing>): `var` gibt zurück `true` , wenn die Projekt Mappe gerade geschlossen wird; andernfalls `false` .

- [__VSPROPID. VSPROPID_IsSolutionOpening](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID.VSPROPID_IsSolutionOpening>): `var` gibt zurück `true` , wenn eine Projekt Mappe gerade geöffnet wird; andernfalls `false` .

Sie können auch sicherstellen, dass Projekte und Projektmappen geladen werden, indem Sie eine der folgenden Methoden aufrufen:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: durch Aufrufen dieser Methode wird erzwungen, dass die Projekte in einer Projekt Mappe geladen werden, bevor die Methode zurückgibt.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: durch das Aufrufen dieser Methode wird erzwungen, dass die Projekte in `guidProject` geladen werden, bevor die Methode zurückgibt.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: durch das Aufrufen dieser Methode wird erzwungen, dass das Projekt in `guidProjectID` geladen wird, bevor die Methode zurückgibt.
