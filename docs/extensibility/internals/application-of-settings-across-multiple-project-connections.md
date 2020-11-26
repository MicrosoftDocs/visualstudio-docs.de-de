---
title: Anwenden von Einstellungen über mehrere Projekt Verbindungen
description: Erfahren Sie, wie Sie mithilfe eines Quellcodeverwaltungs-Plug-ins Einstellungen über mehrere Projekt Verbindungen anwenden, um einen Batch Vorgang auszuführen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cd5b7af98470c1d9a82eb0504c333e74de8c004f
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2020
ms.locfileid: "96190108"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Anwendung von Einstellungen über mehrere Projekt Verbindungen hinweg
Ein Quellcodeverwaltungs-Plug-in, das mithilfe der API-Version 1,2 der Quellcodeverwaltungs-Plug-in erstellt wurde, kann einen Batch Vorgang verwenden, um denselben Quell Code Verwaltungsvorgang für mehrere Projekte oder mehrere Verbindungs Kontexte auszuführen. Batches können verwendet werden, um redundante, pro Projekt geeignete Dialogfelder aus der Benutzer Darstellung auszuschließen.

 Wenn ein Benutzer mehrere Elemente auswählt, die in einem Quellcodeverwaltungs-Plug-in, das mit der Quellcodeverwaltungs-Plug-in-API-Version 1,1 erstellt wurde, zu mehr als einer Verbindung gehört (z. b. zwei Webprojekte auf verschiedenen Dateifreigabe Computern), wird dem Benutzer das gleiche Dialogfeld wiederholt angezeigt. Dieses Szenario tritt auch dann auf, wenn der Benutzer im Dialogfeld auf das Kontrollkästchen **alle anwenden** klickt, da die IDE den Zustand für jeden Verbindungs Kontext zurücksetzt.

## <a name="new-capability-flag"></a>Neues funktionsflag
 Die- `SccBeginBatch` Funktion legt das- `SCC_CAP_BATCH` Flag fest, um anzugeben, dass ein Batch Vorgang ausgeführt wird.

## <a name="new-functions"></a>Neue Funktionen
Die folgenden neuen Funktionen unterstützen den Batch-Vorgang:

- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)

- [SccEndBatch](../../extensibility/sccendbatch-function.md)

Die- `SCCBeginBatch` Funktion startet eine Gruppe von Quell Code Verwaltungs Vorgängen. Die- `SccEndBatch` Funktion schließt die Gruppe. Die Gruppen dürfen nicht gruppiert werden.

## <a name="see-also"></a>Weitere Informationen
- [Neuerungen in der Quellcodeverwaltungs-Plug-in-API, Version 1,2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
