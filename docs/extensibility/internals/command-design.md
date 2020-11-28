---
title: Befehls Entwurf | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie einen Befehl für ein VSPackage in Visual Studio entwerfen. Einschließlich, angeben des Orts, an dem es angezeigt wird, wann es verfügbar ist und wie es behandelt werden soll.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ab06ade9be1ccd0683cd298a5e758ddcfa883f8
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304874"
---
# <a name="command-design"></a>Befehls Entwurf
Wenn Sie einem VSPackage einen Befehl hinzufügen, müssen Sie angeben, wo es angezeigt werden soll, wann es verfügbar ist und wie es behandelt werden soll.

## <a name="define-commands"></a>Definieren von Befehlen
 Um neue Befehle zu definieren, fügen Sie eine *vsct*-Datei (Visual Studio Command Table) in das VSPackage-Projekt ein. Wenn Sie ein VSPackage mithilfe der Visual Studio-Paket Vorlage erstellt haben, enthält das Projekt eine dieser Dateien. Weitere Informationen finden Sie unter [Visual Studio-Befehls Tabellen Dateien (vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

 Visual Studio führt alle gefundenen *vsct* -Dateien zusammen, sodass die Befehle angezeigt werden können. Da diese Dateien sich von der Binärdatei des VSPackages unterscheiden, muss Visual Studio das Paket nicht laden, um die Befehle zu finden. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen von Benutzeroberflächen Elementen durch VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).

 Visual Studio verwendet das <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> Registrierungs Attribut, um Menü Ressourcen und Befehle zu definieren. Weitere Informationen finden Sie unter [Befehls Implementierung](../../extensibility/internals/command-implementation.md).

 Befehle können auf verschiedene Arten zur Laufzeit geändert werden. Sie können angezeigt, ausgeblendet, aktiviert oder deaktiviert werden. Sie können unterschiedliche Text-oder Symbol Werte anzeigen oder andere Werte enthalten. Es kann eine große Menge an Anpassungen durchgeführt werden, bevor Visual Studio Ihr VSPackage lädt. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen von Benutzeroberflächen Elementen durch VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).

## <a name="command-handlers"></a>Befehls Handler
 Wenn Sie einen Befehl erstellen, müssen Sie einen Ereignishandler zum Ausführen des Befehls bereitstellen. Wenn der Benutzer den Befehl auswählt, muss er Ordnungs entsprechend weitergeleitet werden. Das Routing eines Befehls bedeutet, dass es an das richtige VSPackage gesendet wird, um es zu aktivieren oder zu deaktivieren, es auszublenden oder anzuzeigen und es auszuführen, wenn der Benutzer dies auswählt. Weitere Informationen finden Sie unter [Befehls Weiterleitungs Algorithmus](../../extensibility/internals/command-routing-algorithm.md).

## <a name="visual-studio-command-environment"></a>Visual Studio-Befehls Umgebung
 Visual Studio kann eine beliebige Anzahl von VSPackages hosten, und jeder kann seinen eigenen Befehlssatz beitragen. Die Umgebung zeigt nur die Befehle an, die für den aktuellen Task geeignet sind. Weitere Informationen finden Sie unter [Befehls Verfügbarkeit](../../extensibility/internals/command-availability.md) und [Auswahl Kontext Objekte](../../extensibility/internals/selection-context-objects.md).

 Ein VSPackage, das neue Befehle, Menüs, Symbolleisten oder Kontextmenüs definiert, stellt die Befehls Informationen für Visual Studio zur Installationszeit über Registrierungseinträge bereit, die auf Ressourcen in systemeigenen oder verwalteten Assemblys verweisen. Jede Ressource verweist dann auf eine binäre Datenressourcen Datei (*. CTO*), die beim Kompilieren einer Visual Studio-Befehls Tabellen Datei (*vsct*) erstellt wird. Dies ermöglicht Visual Studio das Bereitstellen von zusammengeführten Befehlssätzen, Menüs und Symbolleisten, ohne dass jedes installierte VSPackage geladen werden muss.

### <a name="command-organization"></a>Befehls Organisation
 Die Umgebung positioniert Befehle nach Gruppe, Priorität und Menü.

- Gruppen sind logische Auflistungen verwandter Befehle, z. b. die **Ausschneide**-, **Kopier**-und **Einfüge** Befehlsgruppe. Gruppen sind die Befehle, die in Menüs angezeigt werden.

- Priorität bestimmt die Reihenfolge, in der einzelne Befehle in einer Gruppe im Menü angezeigt werden.

- Menüs fungieren als Container für Gruppen.

  In der Umgebung sind einige Befehle, Gruppen und Menüs vordefiniert. Weitere Informationen finden Sie unter [Standard Befehls-, Gruppen-und Symbolleisten Platzierung](../../extensibility/internals/default-command-group-and-toolbar-placement.md).

  Ein Befehl kann einer primären Gruppe zugewiesen werden. Die primäre Gruppe steuert die Position des Befehls in der Haupt Menüstruktur und im Dialogfeld **Anpassen** . Ein Befehl kann in mehreren Gruppen angezeigt werden. Beispielsweise kann sich ein Befehl im Hauptmenü, in einem Kontextmenü und auf einer Symbolleiste befinden. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen von Benutzeroberflächen Elementen durch VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).

### <a name="command-routing"></a>Befehlsrouting
 Der Vorgang zum Aufrufen und Routing von Befehlen für VSPackages unterscheidet sich vom Aufrufen von Methoden für Objektinstanzen.

 Die Umgebung leitet Befehle sequenziell aus dem innersten (lokalen) Befehls Kontext, der auf der aktuellen Auswahl basiert, in den äußersten (globalen) Kontext weiter. Der erste Kontext, in dem der Befehl ausgeführt werden kann, ist der, der ihn verarbeitet. Weitere Informationen finden Sie unter [Befehls Weiterleitungs Algorithmus](../../extensibility/internals/command-routing-algorithm.md).

 In den meisten Fällen verarbeitet die Umgebung Befehle mithilfe der- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle. Da das Befehls Routing Schema viele verschiedene Objekte für die Behandlung von Befehlen ermöglicht, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> kann von einer beliebigen Anzahl von Objekten implementiert werden. Hierzu gehören Microsoft ActiveX-Steuerelemente, Fenster Ansichts Implementierungen, Dokument Objekte, Projekt Hierarchien und VSPackage-Objekte selbst (für globale Befehle). In einigen spezialisierten Fällen, z. b. beim Routing von Befehlen in einer Hierarchie, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> muss die Schnittstelle implementiert werden.

## <a name="related-topics"></a>Verwandte Themen

|Titel|Beschreibung|
|-----------|-----------------|
|[Befehls Implementierung](../../extensibility/internals/command-implementation.md)|Beschreibt, wie Befehle in einem VSPackage implementiert werden.|
|[Befehls Verfügbarkeit](../../extensibility/internals/command-availability.md)|Beschreibt, wie der Visual Studio-Kontext bestimmt, welche Befehle verfügbar sind.|
|[Befehls Weiterleitungs Algorithmus](../../extensibility/internals/command-routing-algorithm.md)|Beschreibt, wie die Visual Studio-Befehls Routing Architektur die Verarbeitung von Befehlen durch verschiedene VSPackages ermöglicht.|
|[Richtlinien zur Befehls Platzierung](../../extensibility/internals/command-placement-guidelines.md)|Schlägt vor, wie Befehle in der Visual Studio-Umgebung positioniert werden.|
|[Hinzufügen von Elementen der Benutzeroberfläche durch VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|Beschreibt, wie VSPackages die Visual Studio-Befehls Architektur am besten nutzen können.|
|[Standardmäßige Befehls-, Gruppen-und Symbolleisten Platzierung](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|Beschreibt, wie VSPackages die Befehle, die in Visual Studio enthalten sind, am besten verwenden können.|
|[Verwalten von VSPackages](../../extensibility/managing-vspackages.md)|Beschreibt, wie Visual Studio VSPackages lädt.|
|[Vsct-Dateien (Visual Studio-Befehls Tabelle)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|Stellt Informationen zu XML-basierten *vsct* -Dateien bereit, die verwendet werden, um das Layout und die Darstellung von Befehlen in VSPackages zu beschreiben.|
