---
title: Einstieg in die debuggererweiterbarkeit | Microsoft-Dokumentation
description: Beginnen Sie mit dem Erstellen und Anpassen von Debugger-Komponenten, die zum Debuggen von Programmen in der Visual Studio-Umgebung verwendet werden
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6949b9b8a9168915c64bc6183f6b1391a1c79220
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560034"
---
# <a name="get-started-with-debugger-extensibility"></a>Einstieg in die Erweiterbarkeit des Debuggers
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]Stellt die Informationen bereit, die Sie zum Erstellen und Anpassen von Debugger-Komponenten benötigen, die zum Debuggen von Programmen in der Umgebung verwendet werden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] beim Debuggen wurden Verbesserungen hinzugefügt, die von den umfassenden Nutz barkeits Tests für vorherige [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugger abgeleitet wurden Sie können das [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debuggen verwenden, um eine mehrsprachige Anwendung zu durchlaufen, oder Sie können die dynamische Bearbeitung von Variablen beim Debuggen von Anwendungen und mehrsprachigen Lösungen implementieren.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] das Debuggen wird außerhalb des Prozesses ausgeführt, während das Programm gedebuggt wird und daher im Prozessbereich der Anwendung weniger eindringlich ist. Folglich ist es einfacher, Komponenten zu schreiben, die mit dem Debugger interagieren, ohne dass sich dies auf das debugprogramm auswirkt.

 Um das bestmögliche zu verwenden [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , sollten Sie mit den folgenden Elementen vertraut sein:

- Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (Integrated Development Environment, IDE)

- Programmiersprache C++

- ATL-COM

## <a name="in-this-section"></a>In diesem Abschnitt
 [Roadmap für die Erweiterung des Debuggers](../../extensibility/debugger/roadmap-for-extending-the-debugger.md) Beschreibt den Prozess der Implementierung des Debuggens in Ihrem Produkt, abhängig von Ihrem Compiler und seiner Ausgabe.

 [Debugger-Komponenten](../../extensibility/debugger/debugger-components.md) Bietet eine Übersicht über die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debuggingkomponenten, einschließlich Debug-Engine (de), Ausdrucks Auswertung (EE) und Symbol Handler (SH).

 [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md) beschreibt die wichtigsten Architekturkonzepte für das Debuggen.

 [Debugger-Kontexte](../../extensibility/debugger/debugger-contexts.md) Erläutert, wie die Debug-Engine (de) parallel innerhalb von Code-, Dokumentations-und Ausdrucks Auswertungs Kontexten funktioniert. Es wird für jeden der drei Kontexte der Speicherort, die Position oder die Auswertung beschrieben, der bzw. die für ihn relevant ist.

 [Debugtasks](../../extensibility/debugger/debugging-tasks.md) Enthält Links zu verschiedenen Debuggingaufgaben, z. b. das Starten eines Programms und Auswerten von Ausdrücken.
