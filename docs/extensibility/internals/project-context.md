---
title: Projektkontext | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51e411f0bca361f96cdffcfd89498908fd21d441
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706588"
---
# <a name="project-context"></a>Projektkontext
Wenn der Benutzer Projekte und Projekt Elemente hinzufügt oder damit arbeitet, verwendet die IDE das Konzept des Projekt Kontexts, um zu bestimmen, wie verschiedene Vorgänge ausgeführt werden sollen.

 In der Regel handelt es sich bei Dateien um die Standard Projekt Objekte, die der Benutzer explizit erstellt, indem er den Befehl " **Neues Projekt** " oder den Befehl " **Projekt öffnen** " im Menü **Datei** auswählt. In diesen Fällen werden Dateien im Kontext eines Projekts erstellt und geöffnet, und der Projekttyp definiert den Kontext für die Bearbeitung des Dokuments.

 Einige Projekte bieten einen sehr umfangreichen Kontext. Das Projekt verwaltet z. b. einen projektbezogenen, programmatischen Namespace oder eine projektbezogene Datenbankverbindung für die Datenbindung. Der Benutzer kann Dateien oder Datenbankverbindungen häufig direkt mithilfe eines bestimmten Projekt Objekts öffnen, z. b. eines in Projektmappen-Explorer angezeigten Projekt Elements.

 Zu anderen Zeiten wird der Projektkontext eines Elements nicht explizit angegeben. Beispielsweise ist der Kontext eines Elements nicht verfügbar, wenn der Benutzer eine Datei öffnet, indem er den Befehl **vorhandene Datei öffnen** im Menü **Datei** auswählt, wenn der Debugger mit einer Datei arbeitet oder wenn der Benutzer im Dialogfeld **Suchen und ersetzen** auf den Befehl **in Dateien suchen** klickt. Um diese Situationen zu behandeln, ruft die IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> auf, um den Prozess der Suche nach dem besten Projekt zum Öffnen eines Dokuments zu verwalten.

## <a name="see-also"></a>Weitere Informationen
- [Projektpriorität](../../extensibility/internals/project-priority.md)
- [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)
