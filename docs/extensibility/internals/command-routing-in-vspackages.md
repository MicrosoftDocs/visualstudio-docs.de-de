---
title: Befehls Routing in VSPackages | Microsoft-Dokumentation
description: Erfahren Sie mehr über das Befehls Routing in VSPackages und darüber, wie Befehle basierend auf dem Kontext weitergeleitet werden, in dem Sie in Visual Studio ausgeführt werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d05612f9d15c3670411a7901157570fbb3e315a3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939993"
---
# <a name="command-routing-in-vspackages"></a>Befehls Routing in VSPackages
Ein Befehl wird in auf [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] der Grundlage des Kontexts weitergeleitet, in dem er ausgeführt wird. Sie wird vom ursprünglichen Kontext nach außen an den globalen Kontext weitergeleitet.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Befehls Weiterleitungs Algorithmus](../../extensibility/internals/command-routing-algorithm.md)

 Beschreibt die Reihenfolge der Befehls Routing Auflösung.

- [Befehls Verfügbarkeit](../../extensibility/internals/command-availability.md)

 Erläutert das Befehls Routing.

- [Befehle und Menüs, die Interop-Assemblys verwenden](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

 Erläutert Überlegungen zum Routing von Befehlen zwischen verwaltetem Code und com.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Auswahl Kontext Objekte](../../extensibility/internals/selection-context-objects.md)

 Erläutert das Modell, wie Sie den Fokus des Auswahl Kontexts des Benutzers auf ein Fenster festlegen können.

- [Befehle, Menüs und Symbolleisten](../../extensibility/internals/commands-menus-and-toolbars.md)

 Erläutert, wie eine Benutzeroberfläche mit Menüs, Symbolleisten und Kombinationsfeldern für Befehle erstellt wird.
