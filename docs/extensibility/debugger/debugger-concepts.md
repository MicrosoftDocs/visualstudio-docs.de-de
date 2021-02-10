---
title: Debugger-Konzepte | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Architekturkonzepte, die beim Entwerfen des Visual Studio-debugpakets verwendet werden, damit Sie auf diesem Paket aufbauen können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK]
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5202ebdb621121e63adbdf5118cb0848689adde6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952407"
---
# <a name="debugger-concepts"></a>Debugger-Konzepte
Zum Erstellen des Visual Studio-debugpakets müssen Sie mit den Architekturkonzepten vertraut sein, die beim Entwerfen des Pakets verwendet werden.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Debugsitzung](../../extensibility/debugger/debug-session.md) Erläutert die Rolle einer Sitzung in der Debugarchitektur.

 [Server](../../extensibility/debugger/servers-visual-studio-sdk.md) Definiert, was ein Server in Bezug auf die debuggingarchitektur ist, sowohl in abstrakten als auch in physischen Begriffen.

 [Port Lieferanten](../../extensibility/debugger/port-suppliers.md) Definiert, was ein Port Lieferant in Bezug auf die debuggingarchitektur ist.

 [Ports](../../extensibility/debugger/ports.md) Definiert, was ein Port in Bezug auf die debuggingarchitektur ist.

 [Prozesse](../../extensibility/debugger/processes.md) Definiert, was ein Prozess in Bezug auf die debuggingarchitektur ist.

 [Programmknoten](../../extensibility/debugger/program-nodes.md) Definiert einen Programmknoten in Bezug auf die Debugarchitektur, einschließlich der Art und Weise, wie er sich selbst und den Prozess identifizieren kann, der in ausgeführt wird.

 [Programme](../../extensibility/debugger/programs.md) Definiert ein Programm in Bezug auf die Debugarchitektur.

 [Threads](../../extensibility/debugger/threads.md) Definiert die Merkmale von Threads in Bezug auf die Debugarchitektur.

 [Stapel Rahmen](../../extensibility/debugger/stack-frames.md) Definiert einen Stapel Rahmen in Bezug auf die Debugarchitektur. Ein Stapel Rahmen ist eine Abstraktion eines Stapels, der den Ausführungs Kontext eines Threads bereitstellt.

 [Module](../../extensibility/debugger/modules.md) Definiert ein Modul in Bezug auf die Debugarchitektur als physischen Container von Code, z. b. eine ausführbare Datei oder eine DLL.

 [Breakpoints](../../extensibility/debugger/breakpoints-visual-studio-sdk.md) Definiert die drei Arten von Haltepunkten – ausstehend, gebunden und Fehler – im Hinblick auf die debuggingarchitektur.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Debugger-Kontexte](../../extensibility/debugger/debugger-contexts.md) Erläutert, wie die Debug-Engine (de) parallel innerhalb von Code-, Dokumentations-und Ausdrucks Auswertungs Kontexten funktioniert. Es wird für jeden der drei Kontexte der Speicherort, die Position oder die Auswertung beschrieben, der bzw. die für ihn relevant ist.

 [Debugger-Komponenten](../../extensibility/debugger/debugger-components.md) Bietet eine Übersicht über die Visual Studio-debuggingkomponenten, die Debug-Engine (de), Ausdrucks Auswertung (EE) und Symbol Handler (SH) enthalten.

 [Aufgaben Debuggen](../../extensibility/debugger/debugging-tasks.md) Enthält Links zu verschiedenen Debuggingaufgaben, z. b. das Starten eines Programms und Auswerten von Ausdrücken.
