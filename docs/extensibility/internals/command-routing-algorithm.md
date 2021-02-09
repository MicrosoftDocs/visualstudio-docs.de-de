---
title: Befehls Weiterleitungs Algorithmus | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Reihenfolge der Befehls Auflösung in Visual Studio, da Befehle von verschiedenen Komponenten behandelt und vom innersten zum äußersten Kontext weitergeleitet werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 47991a3d1140893c4695e4edb7b76b808ab2917a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907731"
---
# <a name="command-routing-algorithm"></a>Befehls Weiterleitungs Algorithmus
In Visual Studio werden Befehle von einer Reihe unterschiedlicher Komponenten behandelt. Befehle werden vom innersten Kontext, der auf der aktuellen Auswahl basiert, zum äußersten (auch als globaler Kontext bezeichnet) weitergeleitet. Weitere Informationen finden Sie unter [Command Availability](../../extensibility/internals/command-availability.md).

## <a name="order-of-command-resolution"></a>Reihenfolge der Befehls Auflösung
 Befehle werden über die folgenden Ebenen des Befehls Kontexts übermittelt:

1. Add-Ins: die Umgebung stellt dem Befehl zuerst alle Add-Ins zur Verfügung, die vorhanden sind.

2. Prioritäts Befehle: Diese Befehle werden mithilfe von registriert <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget> . Sie werden für jeden Befehl in Visual Studio aufgerufen und in der Reihenfolge aufgerufen, in der Sie registriert wurden.

3. Kontextmenü Befehle: ein Befehl, der sich in einem Kontextmenü befindet, wird zuerst für das Befehls Ziel angeboten, das im Kontextmenü bereitgestellt wird, und danach für das typische Routing.

4. Befehls Ziele für Symbolleisten Sätze: Diese Befehls Ziele werden registriert, wenn aufgerufen wird <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A> . Der- `pCmdTarget` Parameter kann sein `null` . Wenn dies nicht der Fall ist `null` , wird dieses Befehls Ziel verwendet, um alle Befehle zu aktualisieren, die sich auf der Symbolleiste befinden, die Sie einrichten. Wenn die Shell die Symbolleiste einrichtet, übergibt Sie den Fensterrahmen als, `pCmdTarget` sodass alle Aktualisierungen der Befehle auf der Symbolleiste durch den Fensterrahmen fließen, auch wenn Sie nicht im Fokus sind.

5. Tool Fenster: Tool Fenster, die in der Regel die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> Schnittstelle implementieren, sollten auch die- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle implementieren, damit Visual Studio das Befehls Ziel erhalten kann, wenn das Tool Fenster das aktive Fenster ist. Wenn das Tool Fenster, das den Fokus besitzt, jedoch das **Projekt** Fenster ist, wird der Befehl an die Schnittstelle weitergeleitet, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> das gemeinsame übergeordnete Element der ausgewählten Elemente ist. Wenn diese Auswahl mehrere Projekte umfasst, wird der Befehl an die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> Hierarchie weitergeleitet. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> -Schnittstelle enthält die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> -Methode und die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> Methode, die analog zu den entsprechenden Befehlen der- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle sind

6. Dokument Fenster: Wenn für den Befehl das `RouteToDocs` Flag in der *vsct* -Datei festgelegt ist, sucht Visual Studio nach einem Befehls Ziel für das Dokument Ansichts Objekt, bei dem es sich entweder um eine Instanz einer <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> Schnittstelle oder um eine Instanz eines Dokument Objekts handelt (in der Regel eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> Schnittstelle oder eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> Schnittstelle). Wenn das Dokument Ansichts Objekt den Befehl nicht unterstützt, leitet Visual Studio den Befehl an die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> zurückgegebene Schnittstelle weiter. (Hierbei handelt es sich um eine optionale Schnittstelle für Dokument Datenobjekte.)

7. Aktuelle Hierarchie: die aktuelle Hierarchie kann das Projekt sein, das das aktive Dokument Fenster oder die Hierarchie besitzt, die in **Projektmappen-Explorer** ausgewählt ist. Visual Studio sucht nach der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle, die für die aktuelle oder aktive Hierarchie implementiert ist. Die Hierarchie sollte Befehle unterstützen, die gültig sind, wenn die Hierarchie aktiv ist, auch wenn ein Dokument Fenster eines Projekt Elements den Fokus besitzt. Allerdings müssen Befehle, die nur angewendet werden, wenn **Projektmappen-Explorer** den Fokus besitzt, mithilfe der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> -Schnittstelle und der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> -und- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> Methoden unterstützt werden

     Zum **Ausschneiden**, **Kopieren**, **Einfügen**, **Löschen**, **Umbenennen**, **eingeben** und **Doppelklicken auf** Befehle ist eine spezielle Behandlung erforderlich. Informationen zum Behandeln von **Lösch** -und **Entfernungs** Befehlen in Hierarchien finden Sie unter der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> Schnittstelle.

8. Global: Wenn ein Befehl nicht von den zuvor erwähnten Kontexten behandelt wurde, versucht Visual Studio, ihn an das VSPackage weiterzuleiten, das einen Befehl besitzt, der die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle implementiert. Wenn das VSPackage nicht bereits geladen wurde, wird es nicht geladen, wenn Visual Studio die- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode aufruft. Das VSPackage wird nur geladen, wenn die- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Methode aufgerufen wird.

## <a name="see-also"></a>Weitere Informationen
- [Befehls Entwurf](../../extensibility/internals/command-design.md)
