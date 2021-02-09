---
title: Befehle, Menüs und Symbolleisten | Microsoft-Dokumentation
description: Erfahren Sie mehr über Befehle, Menüs und Symbolleisten in Visual Studio, einschließlich der Informationen und ihrer Funktionsweise in VSPackages.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- commands [Visual Studio]
- toolbars [Visual Studio], commands
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 49ae9c27b27a1b3e32338521315007903d9e6825
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884766"
---
# <a name="commands-menus-and-toolbars"></a>Befehle, Menüs und Symbolleisten
Mit Menüs und Symbolleisten können Benutzer auf Befehle in Ihrem VSPackage zugreifen. Befehle sind Funktionen, mit denen Aufgaben wie das Drucken eines Dokuments, das Aktualisieren einer Ansicht oder das Erstellen einer neuen Datei ausgeführt werden können. Menüs und Symbolleisten stellen eine praktische Methode für die grafische Darstellung von Befehlen für Benutzer dar. In der Regel sind verwandte Befehle zusammen im gleichen Menü oder auf derselben Symbolleiste gruppiert.

- Menüs werden in der Regel als aus einem Wort bestehende Zeichenfolgen in einer Zeile im oberen Bereich der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) oder oben in einem Toolfenster gruppiert angezeigt. Menüs können auch durch Klicken mit der rechten Maustaste angezeigt werden. In diesem Kontext werden sie als Kontextmenüs bezeichnet. Beim Klicken auf ein Menü wird das Menü erweitert, sodass mindestens ein Befehl angezeigt wird. Wenn Sie auf Befehle klicken, können Aufgaben ausgeführt oder Untermenüs, die zusätzliche Befehle enthaltenen, geöffnet werden. Einige bekannte Menü Namen sind " **File**", " **Edit**", " **View**" und " **Window**". Weitere Informationen finden Sie unter [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md).

- Symbolleisten sind in der Regel Zeilen, in denen Schaltflächen und andere Steuerelemente wie Kombinationsfelder, Listenfelder, Textfelder und Menüsteuerelemente angezeigt werden. Allen Symbolleisten-Steuerelementen sind Befehle zugeordnet. Wenn Sie auf eine Symbolleistenschaltfläche klicken, wird der zugeordnete Befehl aktiviert. Symbolleistenschaltflächen weisen normalerweise Symbole auf, die die zugrunde liegenden Befehle veranschaulichen. Ein Beispiel hierfür ist ein Drucker für den Befehl "Drucken". Bei Dropdownlisten-Steuerelementen ist jedes Element in der Liste einem anderen Befehl zugeordnet. Ein Menüsteuerelement ist eine Mischform, bei der eine Seite des Steuerelements eine Symbolleistenschaltfläche und die andere Seite ein Dropdownpfeil ist. Wenn Sie auf den Dropdownpfeil klicken, werden zusätzliche Befehle angezeigt. Weitere Informationen finden Sie unter [Hinzufügen eines Menü Controllers zu einer Symbolleiste](../../extensibility/adding-a-menu-controller-to-a-toolbar.md).

- Wenn Sie einen Befehl erstellen, müssen Sie auch einen Ereignishandler für diesen Befehl erstellen. Der Ereignishandler bestimmt, wann der Befehl angezeigt oder aktiviert wird, ermöglicht Ihnen, den zugehörigen Text zu ändern, und stellt sicher, dass der Befehl entsprechend "reagiert", wenn er aktiviert wird. In den meisten Fällen verarbeitet die IDE Befehle mit der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>-Schnittstelle. In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] werden Befehle hierarchisch weitergeleitet, beginnend mit dem innersten Befehlskontext, basierend auf der lokalen Auswahl, bis zum äußersten Kontext, basierend auf der globalen Auswahl. Befehle, die dem Hauptmenü hinzugefügt werden, sind sofort für die Skripterstellung verfügbar. Weitere Informationen finden Sie unter [MenuCommands im Vergleich zu olemenucommands](/previous-versions/visualstudio/visual-studio-2015/misc/menucommands-vs-olemenucommands?preserve-view=true&view=vs-2015) und [Auswahl Kontext Objekten](../../extensibility/internals/selection-context-objects.md).

  Wenn Sie neue Menüs und Symbolleisten definieren möchten, müssen Sie diese in einer *vsct*-Datei (Visual Studio Command Table) beschreiben. Diese Datei wird von der Visual Studio-Paket Vorlage zusammen mit den erforderlichen Elementen zur Unterstützung der Befehle, Symbolleisten und Editoren erstellt, die Sie in der Vorlage ausgewählt haben. Alternativ können Sie Ihre eigene *vsct* -Datei mithilfe des hier beschriebenen XML-Schemas schreiben: [vsct XML Schema Reference](../../extensibility/vsct-xml-schema-reference.md).

  Weitere Informationen zum Arbeiten mit *vsct* -Dateien finden Sie unter [Visual Studio-Befehls Tabellen Dateien (vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

  In den Themen in diesem Abschnitt wird erläutert, wie Befehle, Menüs und Symbolleisten in VSPackages funktionieren.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Hinzufügen von Elementen der Benutzeroberfläche durch VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Eine ausführliche Beschreibung der Befehls Tabellen-Format Spezifikation.

- [Vsct-Dateien (Visual Studio-Befehls Tabelle)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

 Beschreibt eine XML-basierte Syntax und einen Compiler für Befehls Tabellen.

- [Standardmäßige Befehls-, Gruppen-und Symbolleisten Platzierung](../../extensibility/internals/default-command-group-and-toolbar-placement.md)

 Beschreibt vordefinierte Befehle, Gruppen, Menüs und Symbolleisten.

- [IDE-definierte Befehle, Menüs und Gruppen](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)

 Gibt die vordefinierten Menüs, Befehle und Befehls Gruppen an, die für die Verwendung durch die IDE verfügbar sind [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Befehls Entwurf](../../extensibility/internals/command-design.md)

 Erläutert das Entwerfen von Befehlen.

- [Menü-und Symbolleisten Befehle optimieren](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)

 Gibt Richtlinien für Befehle an.

- [Verfügbar machen von Befehlen](../../extensibility/internals/making-commands-available.md)

 Erläutert, wie Sie Visual Studio Befehle zur Verfügung stellen können.

- [Befehle und Menüs, die Interop-Assemblys verwenden](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

 Erläutert das Implementieren von Befehlen, die Interop-Assemblys verwenden.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Befehls Routing in VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)

 Erläutert das Befehls Routing in VSPackages.