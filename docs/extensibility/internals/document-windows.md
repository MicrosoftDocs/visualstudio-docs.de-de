---
title: Dokument Fenster | Microsoft-Dokumentation
description: Erfahren Sie mehr über Dokument Fenster in Visual Studio, einschließlich der Implementierung und der Art und Weise, wie die laufende Dokument Tabelle (RDT) ihren Status nachverfolgt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f39c02ece35a36ceb763a2a5b84f8431043a1b50
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480004"
---
# <a name="document-windows"></a>Dokumentfenster
Ein *Dokument Fenster* in Visual Studio ist ein untergeordnetes Fenster, das einem MDI-Fenster (Multiple Document Interface) zugeordnet ist. Dokument Fenster werden in der Regel zum Anzeigen und Ändern von Quellcode oder Text verwendet, Sie können jedoch auch andere funktionale Typen hosten. Dokument Fenster:

- Kann in separaten horizontalen oder vertikalen Registerkarten Gruppen im übergeordneten MDI organisiert werden, sodass mehrere Dateien gleichzeitig angezeigt werden können.

- Kann in beliebiger Reihenfolge in der übergeordneten MDI angedockt werden.

- Kann frei in den Umlauf gebracht werden.

- Sind in der Aktivier Reihenfolge mit anderen MDI-Fenstern verknüpft.

  Die Befehle zum Gruppieren, Andocken und unverankerten finden Sie im Kontextmenü für eine Dokument Fenster-Registerkarte.

  Weitere Informationen zum Fenster Verhalten in Visual Studio finden Sie unter [Anpassen von Fensterlayouts](../../ide/customizing-window-layouts-in-visual-studio.md).

## <a name="document-window-implementation"></a>Dokument Fenster Implementierung
 Dokument Fenster werden erstellt, indem ein Editor implementiert wird. Die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> Schnittstelle erstellt Dokument Fenster als Teil der Instanziierung eines Editors. Weitere Informationen finden Sie unter [Legacy Schnittstellen im Editor](/previous-versions/visualstudio/visual-studio-2015/extensibility/legacy-interfaces-in-the-editor?preserve-view=true&view=vs-2015).

> [!NOTE]
> Implementieren Sie zum Bereitstellen von rückwärts-und vorwärts Navigationspunkten in einem Fenster die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> Schnittstelle. Der Text-Editor verwendet Textmarker zur Identifizierung von Navigationspunkten im Dokument.

## <a name="the-running-document-table"></a>Die laufende Dokument Tabelle
 Die IDE verwendet die laufende dokumententabelle (RDT), um den Status jedes Dokument Fensters zu verfolgen. Der RDT ist der Mechanismus, über den Dokument Fenster über Ereignisse benachrichtigt werden, z. b. Wenn eine Projekt Mappe geschlossen wird oder wenn eine Datei bearbeitet wurde. Weitere Informationen finden Sie unter [Ausführen der Dokument Tabelle](../../extensibility/internals/running-document-table.md).

## <a name="see-also"></a>Siehe auch
- [Verzögerte Dokument Ladevorgänge](../../extensibility/internals/delayed-document-loading.md)
