---
title: Implementieren der Befehls Behandlung für in der Liste eingefügte Projekte Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2092fc8033d5a5cc53b12bd63a945bd9865ca30e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707600"
---
# <a name="implementing-command-handling-for-nested-projects"></a>Implementieren der Befehlsbehandlung für geschachtelte Projekte
Die IDE kann Befehle übergeben, die über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> -Schnittstelle und die- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle an untergeordnete Projekte übergeben werden, oder übergeordnete Projekte können die Befehle filtern oder außer Kraft setzen.

> [!NOTE]
> Es können nur Befehle gefiltert werden, die normalerweise von dem übergeordneten Projekt behandelt werden. Befehle wie **Build** **und bereit** Stellung, die von der IDE verarbeitet werden, können nicht gefiltert werden.

 In den folgenden Schritten wird der Prozess zum Implementieren der Befehls Behandlung beschrieben.

## <a name="procedures"></a>Prozeduren

#### <a name="to-implement-command-handling"></a>So implementieren Sie die Befehls Behandlung

1. Wenn der Benutzer ein geclustertes Projekt oder einen Knoten in einem geclusterte Projekt auswählt:

   1. Die IDE Ruft die- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode auf.

      \- oder -

   2. Wenn der Befehl in einem Hierarchie Fenster (z. b. einem Kontextmenü Befehl in Projektmappen-Explorer) stammt, ruft die IDE die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> -Methode für das übergeordnete Element des Projekts auf.

2. Das übergeordnete Projekt kann die an zu über gebenden Parameter untersuchen `QueryStatus` , z. b. `pguidCmdGroup` und `prgCmds` , um zu bestimmen, ob das übergeordnete Projekt die Befehle filtern soll. Wenn das übergeordnete Projekt zum Filtern von Befehlen implementiert ist, sollte Folgendes festgelegt werden:

   ```
   prgCmds[0].cmdf = OLECMDF_SUPPORTED;
   // make sure it is disabled
   prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;
   ```

    Dann sollte das übergeordnete Projekt zurückgeben `S_OK` .

    Wenn das übergeordnete Projekt den Befehl nicht filtert, sollte es einfach zurückgeben `S_OK` . In diesem Fall leitet die IDE automatisch den Befehl an das untergeordnete Projekt weiter.

    Das übergeordnete Projekt muss den Befehl nicht an das untergeordnete Projekt weiterleiten. Die IDE führt diese Aufgabe aus.

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Befehle, Menüs und Symbolleisten](../../extensibility/internals/commands-menus-and-toolbars.md)
- [Schachteln von Projekten](../../extensibility/internals/nesting-projects.md)
