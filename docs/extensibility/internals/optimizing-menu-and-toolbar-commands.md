---
title: Optimieren von Menüs und Symbolleisten Befehlen | Microsoft-Dokumentation
description: Erfahren Sie, wie Visual Studio Befehls Verwirrung minimieren kann, die durch Hinzufügen von VSPackages und den entsprechenden Befehlen verursacht wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands [Visual Studio], menus
- commands [Visual Studio], toolbars
- menus [Visual Studio SDK], commands
- menu commands, implementing
- toolbars [Visual Studio], commands
ms.assetid: 8385f1a6-1e98-4dca-83d2-fcbed7177242
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e9df95efc1021ad5bd75c1d009627c5747152b37
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895530"
---
# <a name="optimizing-menu-and-toolbar-commands"></a>Optimieren von Menü- und Symbolleistenbefehlen
Durch das Hinzufügen von VSPackages und die zugehörigen Befehle zu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kann eine überfüllte Benutzeroberfläche verursacht werden. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bietet Möglichkeiten, um die Verwirrung von UI-Befehlen zu minimieren.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Verfügbarmachen von Befehlen](../../extensibility/internals/making-commands-available.md)

 Bietet allgemeine Richtlinien zum Minimieren der Überfüllung der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Benutzeroberfläche beim Hinzufügen von VSPackages.

- [Richtlinien zur Platzierung](../../extensibility/internals/command-placement-guidelines.md)

 Bietet spezifische Richtlinien für die Implementierung eines VSPackage entsprechend der Größe des Befehlssatzes.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Befehle, Menüs und Symbolleisten](../../extensibility/internals/commands-menus-and-toolbars.md)

 Erläutert, wie eine Benutzeroberfläche mit Menüs, Symbolleisten und Kombinationsfeldern für Befehle erstellt wird.
