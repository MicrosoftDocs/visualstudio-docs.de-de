---
title: Befehle und Menüs, die Interop-Assemblys verwenden | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Aufgaben, die beim Implementieren von Menü-und Symbolleisten Befehlen in einem VSPackage mithilfe von Interop-Assemblys ausgeführt werden müssen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e4bf3c1843db67fdadcf0fe177aa17e0f17a627e
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304799"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Befehle und Menüs, die Interop-Assemblys verwenden
Ein VSPackage, das Menü-und Symbolleisten Befehle mithilfe von Interop-Assemblys implementiert, muss:

- Informieren [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Sie die integrierte Entwicklungsumgebung (Integrated Development Environment, IDE) über die unterstützten Befehle und ob Sie zurzeit aktiviert sind.

- Befolgen Sie die Regeln (Vertrag) für die Verarbeitung von Befehlen.

- Implementieren Sie die Befehls Verarbeitung explizit mithilfe der- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> oder- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Schnittstelle.

  Im folgenden Abschnitt wird beschrieben, wie Sie diese Aufgaben ausführen.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Ermitteln des Befehlsstatus mithilfe von Interop-Assemblys](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)

 Beschreibt, wie ein VSPackage der IDE mitteilt, welche Befehle unterstützt werden und ob Sie derzeit aktiviert sind.

- [Befehls Verträge in Interop-Assemblys](../../extensibility/internals/command-contracts-in-interop-assemblies.md)

 Stellt eine Definition des grundlegenden Befehls Vertrags bereit, der von allen VSPackages verwendet wird, die Befehle mit Interopassemblys implementieren.

- [Befehls Implementierung](../../extensibility/internals/command-implementation.md)

 Bietet einen Überblick darüber, wie ein VSPackage einen Befehl implementiert.

- [Befehls Handler für Interop-Assembly registrieren](../../extensibility/internals/registering-interop-assembly-command-handlers.md)

 Beschreibt die Registrierungseinträge, die zum Benachrichtigen der IDE erforderlich sind, dass ein VSPackage einen Befehls Handler bereitstellt.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Befehls Verfügbarkeit](../../extensibility/internals/command-availability.md)

 Beschreibt die Kriterien, die von der IDE verwendet werden, um zu bestimmen, welche VSPackage-Befehle verfügbar sind und welches Objekt Sie behandelt.

- [Hinzufügen von Elementen der Benutzeroberfläche durch VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Bietet ausführliche Informationen zum Erstellen einer Benutzeroberfläche, die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Befehls Unterstützung verwendet.

- [Befehls Routing in VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)

 Eine Übersicht über den Prozess, der verwendet wird, um ein Objekt mit der richtigen Befehls Anforderung zu verknüpfen.
