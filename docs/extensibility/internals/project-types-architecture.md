---
title: Architektur von Projekttypen | Microsoft-Dokumentation
description: Dieser Artikel enthält Links zu Artikeln, die ausführliche Informationen zur Architektur von Projekttypen in Visual Studio enthalten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f6c9463604cda8c26a53cb02802252dfe40d309b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970126"
---
# <a name="project-types-architecture"></a>Architektur von Projekttypen
Dieser Abschnitt enthält ausführliche Informationen zur Architektur von Projekttypen in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="in-this-section"></a>In diesem Abschnitt
- [Elemente eines Projektmodells](../../extensibility/internals/elements-of-a-project-model.md)

 Listet die Dienste auf, die von einem Projekttyp genutzt werden können, sowie die Schnittstellen, die

- [Hauptkomponenten eines Projektmodells](../../extensibility/internals/project-model-core-components.md)

 Beschreibt die Schnittstellen, die sowohl implementiert als auch implementiert werden können, um zusätzliche Funktionalität bereitzustellen.

- [Gründe für das Erstellen von Projekttypen](../../extensibility/internals/when-to-create-project-types.md)

 Hilft Ihnen bei der Entscheidung, wann Sie einen Projekttyp erstellen müssen, und wann Sie ein anderes [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Erweiterbarkeits Feature wie VSPackages und Editoren verwenden können, um das gleiche Ziel zu erreichen.

- [Hierarchien und Auswahl](../../extensibility/internals/hierarchies-and-selection.md)

 Beschreibt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , wie Hierarchien und Auswahl Kontext verwendet werden, um ein konsistentes und vereinfachtes Benutzer Verhalten bereitzustellen.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Projektuntertypen](../../extensibility/internals/project-subtypes.md)

 Erläutert, wie Sie mit Projekt Untertypen das Verhalten der Projektsysteme von und anpassen können [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] .

- [Projekttypen](../../extensibility/internals/project-types.md)

 Bietet eine Übersicht über Projekte als grundlegende Bausteine der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung (Integrated Development Environment, IDE). Links werden für weitere Themen bereitgestellt, in denen erläutert wird, wie Projekte das Erstellen und Kompilieren von Code steuern.
