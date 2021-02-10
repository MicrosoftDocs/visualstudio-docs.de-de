---
title: Dateinachverfolgung | Microsoft-Dokumentation
description: Verwenden Sie die MSBuild-Dateinachverfolgungsfunktionen, um Aufrufe an das Windows-Dateisystem für einen Prozess und seine untergeordneten Prozesse zu protokollieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d61c3478515f2c8fa867666e6ff4ff72a0d4e65b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877121"
---
# <a name="file-tracking"></a>Dateinachverfolgung

Die Dateinachverfolgung protokolliert Aufrufe an das Windows-Dateisystem für einen Prozess und dessen untergeordnete Prozesse. Durch das Aufrufen der unten aufgeführten Funktionen wird gesteuert, wann diese Protokollierung aktiviert oder deaktiviert wird, und die zu verwendende Protokolldatei angegeben.

- [EndTrackingContext:](../msbuild/endtrackingcontext.md) Beendet der Nachverfolgung des aktuellen Kontexts.

- [ResumeTracking:](../msbuild/resumetracking.md) Setzt die Nachverfolgung nach einem Aufruf von [SuspendTracking](../msbuild/suspendtracking.md) fort.

- [SetThreadCount:](../msbuild/setthreadcount.md) Legt die Anzahl der Threads fest, die zur Nachverfolgung verwendet werden sollen.

- [StartTrackingContext:](../msbuild/starttrackingcontext.md) Startet einen neuen Nachverfolgungskontext.

- [StartTrackingContextWithRoot:](../msbuild/starttrackingcontextwithroot.md) Startet einen neuen Nachverfolgungskontext mit einem angegebenen Stamm.

- [StopTrackingAndCleanup:](../msbuild/stoptrackingandcleanup.md) Beendet die Nachverfolgung und gibt die verwendeten Ressourcen frei.

- [SuspendTracking:](../msbuild/suspendtracking.md) Hält die Nachverfolgung vorübergehend an.

- [WriteAllTLogs:](../msbuild/writealltlogs.md) Erstellt Nachverfolgungsprotokolle für alle Kontexte.

- [WriteContextTLogs:](../msbuild/writecontexttlogs.md) Erstellt ein Nachverfolgungsprotokoll für den aktuellen Kontext.
