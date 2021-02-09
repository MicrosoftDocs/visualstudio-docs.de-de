---
title: Entladen und erneutes Laden von Vorgängen
description: Erfahren Sie mehr über die zusätzlichen Schritte, die beim Entladen und erneuten Laden von in Visual Studio ausgeführten Projekten ausgeführt werden müssen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ed91ac56929682205937122a4521ad7233af675f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884649"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Überlegungen zum Entladen und erneuten Laden von in einem Projekt Vorgängen

Beim Implementieren von Typen mit einem anderen Typ müssen Sie beim Entladen und erneuten Laden der Projekte zusätzliche Schritte ausführen. Damit Listener korrekt an projektmappenereignisse benachrichtigt werden, müssen Sie die Ereignisse und ordnungsgemäß ausgeben `OnBeforeUnloadProject` `OnAfterLoadProject` .

Ein Grund, diese Ereignisse zu erhöhen, ist die Quell Code Verwaltung (Source Code Control, SCC). Sie möchten nicht, dass SCC die Elemente vom Server löscht und Sie dann wieder als *neue* hinzufügen, wenn ein `Get` Vorgang von SCC vorliegt. In diesem Fall würde eine neue Datei aus SCC geladen werden. Sie müssten alle Dateien entladen und erneut laden, falls Sie sich unterscheiden.

Aufrufe der Quell Code Verwaltung `ReloadItem` . Implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> Sie die-Schnittstelle, um aufzurufen `OnBeforeUnloadProject` und `OnAfterLoadProject` das Projekt zu löschen und neu zu erstellen. Wenn Sie die-Schnittstelle auf diese Weise implementieren, wird SCC informiert, dass das Projekt vorübergehend gelöscht und erneut hinzugefügt wurde. Daher funktioniert SCC nicht mit dem Projekt, als ob das Projekt *tatsächlich* gelöscht und erneut hinzugefügt wurde.

## <a name="reload-projects"></a>Projekte erneut laden

Um das erneute Laden von in-Projekten zu unterstützen, implementieren Sie die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> Methode. In ihrer Implementierung von `ReloadItem` Schließen Sie die in der Liste der Projekte, und erstellen Sie Sie neu.

Wenn ein Projekt erneut geladen wird, löst die IDE in der Regel die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> -und- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> Ereignisse aus. Für gelöschte und neu geladene Projekte initiiert das übergeordnete Projekt jedoch den Prozess, nicht die IDE. Da das übergeordnete Projekt keine projektmappenereignisse aufhebt und die IDE keine Informationen über die Initialisierung des Prozesses hat, werden die Ereignisse nicht ausgelöst.

Um diesen Prozess zu verarbeiten, ruft das übergeordnete Projekt `QueryInterface` auf der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> Schnittstelle auf. `IVsFireSolutionEvents` verfügt über Funktionen, die die IDE anweisen, das- `OnBeforeUnloadProject` Ereignis zum Entladen des-Projekts aufzurichten, und dann das- `OnAfterLoadProject` Ereignis zum erneuten Laden desselben Projekts aufzurichten.

## <a name="see-also"></a>Weitere Informationen

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- [Schachteln von Projekten](../../extensibility/internals/nesting-projects.md)
