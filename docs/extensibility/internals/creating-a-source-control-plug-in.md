---
title: Erstellen eines Quellcodeverwaltungs-Plug-ins | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie ein Quellcodeverwaltungs-Plug-in erstellen, mit dem der integrierten Entwicklungsumgebung (IDE) von Visual Studio eine Quell Code Verwaltungsfunktion hinzugefügt wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: c7e69fa4-150e-469a-a6fc-fa1260bdbb07
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 489aea2ba5b12dafa161ce70a49f81f60b38ba5d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878759"
---
# <a name="create-a-source-control-plug-in"></a>Erstellen eines Quellcodeverwaltungs-Plug-ins
Das Visual Studio SDK bietet Ressourcen, mit denen Sie der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) Funktionen zur Quell Code Verwaltung hinzufügen können. Sie können jede Plug-in-dll verwenden, die der in dieser Dokumentation beschriebenen Quellcodeverwaltungs-Plug-in-API entspricht.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Erste Schritte](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)

 Beschreibt, wie Sie ein Quellcodeverwaltungs-Plug-in installieren und die derzeit verfügbaren API-Versionen für Quellcodeverwaltungs-Plug-ins hervorheben.

- [Aufbau](../../extensibility/internals/source-control-plug-in-architecture.md)

 Erläutert die Integration eines Quellcodeverwaltungs-Plug-ins in die IDE mithilfe eines Architektur Diagramms [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Test Handbuch](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

 Enthält Anleitungen zum Testen der Installation und des Betriebs eines Quellcodeverwaltungs-Plug-ins.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Quellcodeverwaltungs-VSPackage erstellen](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Erläutert das Erstellen eines Quellcodeverwaltungs-VSPackages, das nicht nur Quell Code Verwaltungsfunktionen bereitstellt, sondern die Benutzeroberfläche der Quell Code Verwaltung ersetzt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Quellcodeverwaltungs-Plug-ins](../../extensibility/source-control-plug-ins.md)

 Stellt eine vollständige Auflistung aller Elemente in der Quellcodeverwaltungs-Plug-in-API bereit.

- [Quellcodeverwaltung](../../extensibility/internals/source-control.md)

 Erläutert die Optionen zum Implementieren der Quell Code Verwaltung als integriertes Feature von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .
