---
title: Nicht unterstützte Debugszenarios
description: Informationen zu nicht unterstützten Debuggingszenarios im Workflow-Designer, z. b. "die Ausführung kann nicht fortgesetzt werden, nachdem Code bearbeitet wurde".
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: 70620528bd3e2d50b85d67eef5990d9843ea5178
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875132"
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>Im Workflow-Designer nicht unterstützte Debugszenarien

Die Workflow-Designer unterstützt die folgenden Debugszenarien nicht:

- Nach dem Bearbeiten von Code kann die Ausführung nicht fortgesetzt werden.

- Die Ausführung kann an einem beliebigen Punkt im Workflow nicht fortgesetzt werden (Nächste Anweisung festlegen).

- Die Ausführung kann nicht bis zum Cursor fortgesetzt werden (Ausführen bis Cursor).

- Der Workflow-Designer kann nicht verwendet werden, um Workflows zu debuggen, die ohne den Designer direkt im Code erstellt wurden.

- Workflows, die in früheren Versionen von Windows Workflow Foundation (WF) erstellt wurden, können in .NET Framework 4 oder höher nicht debuggten werden.

- Es können keine Haltepunkte auf Verknüpfungen zwischen Aktivitäten oder <xref:System.Activities.Statements.Flowchart>-Knoten definiert werden.

- Die Zwischenablage steht während des Debuggens nicht zur Verfügung.

- Haltepunkte werden nicht beibehalten, wenn Aktivitäten kopiert oder eingefügt werden.

- Im Fenster Aufrufliste können keine Workflowhaltepunkte festgelegt werden.

- Beim Erstellen von Breakpoints im Designer werden die **Zeilen** -und **Zeichen** Einstellungen im Dialogfeld **Neuer Haltepunkt** nicht verwendet.

- Im Haltepunktfenster und im Kontextmenü werden die folgenden Spalten bzw. Optionen für das Debuggen von Workflows nicht unterstützt:

  - Bedingung

  - Trefferanzahl

  - Bei Treffer

  - Funktion

  - Daten

  - Prozess

  - Gehe zu Disassembly
