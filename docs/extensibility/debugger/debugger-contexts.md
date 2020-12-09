---
title: Debugger-Kontexte | Microsoft-Dokumentation
description: 'Erfahren Sie, wie die Visual Studio-Debug-Engine innerhalb unterschiedlicher Kontexte funktioniert: Code Kontext, Dokumentations Kontext oder Position und Ausdrucks Auswertungs Kontext.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 355ca667f0f909ebedc6f404ded545b3f862a444
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914685"
---
# <a name="debugger-contexts"></a>Debugger-Kontexte
Beim [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debuggen arbeitet die Debug-Engine (de) in mehreren unterschiedlichen Kontexten gleichzeitig wie folgt:

- Der Code Kontext, der die aktuelle Position im ausführungsstream eines Programms beschreibt.

- Der Dokumentations Kontext oder die Position, in der die aktuelle Position in einem Quelldokument beschrieben wird.

- Der Ausdrucks Auswertungs Kontext, der den Kontext beschreibt, in dem die Ausdrucks Auswertung stattfindet.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Code Kontext](../../extensibility/debugger/code-context.md) Erläutert den Code Kontext als Adresse im Anweisungs Datenstrom eines Programms in den heutigen Lauf Zeit Architekturen im Vergleich zu nicht herkömmlichen Sprachen, in denen Code möglicherweise nicht durch Anweisungen dargestellt wird, aber auf andere Weise.

 [Dokument Position](../../extensibility/debugger/document-position.md) Definiert die Dokument Position im Visual Studio-Debuggen durch eine Abstraktion einer Position in einer Quelldatei, die der IDE bekannt ist.

 [Dokument Kontext](../../extensibility/debugger/document-context.md) Erläutert, was Dokument Kontext in Visual Studio-Debuggen in Bezug auf eine Quelldatei darstellt. Erläutert auch, wie der Symbol Handler einem Dokumentations Kontext einen Code Kontext zuordnet.

 [Ausdrucks Auswertungs Kontext](../../extensibility/debugger/expression-evaluation-context.md) Stellt Informationen zu einem Ausdrucks Auswertungs Kontext in Visual Studio bereit. Ein Ausdrucks Auswertungs Kontext, der einem Stapel Rahmen zugeordnet ist, stellt z. b. den Kontext zum Auswerten von lokalen Variablen, Methoden Parametern und Klassenmembern bereit.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Debug-Konzepte](../../extensibility/debugger/debugger-concepts.md) Beschreibt die wichtigsten Konzepte der debuggingarchitektur.

 [Debugkomponenten](../../extensibility/debugger/debugger-components.md) Bietet eine Übersicht über die Visual Studio-debuggingkomponenten, die Debug-Engine (de), Ausdrucks Auswertung (EE) und Symbol Handler (SH) enthalten.

 [Aufgaben Debuggen](../../extensibility/debugger/debugging-tasks.md) Enthält Links zu verschiedenen Debuggingaufgaben, z. b. das Starten eines Programms und Auswerten von Ausdrücken.
