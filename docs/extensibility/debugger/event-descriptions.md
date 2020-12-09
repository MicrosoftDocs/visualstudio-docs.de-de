---
title: Ereignis Beschreibungen | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Ereignis Typen und die Gründe für deren Verwendung. Jeder Ereignistyp hat einen bestimmten Zweck.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ea477d3d21cd3b7a1a5352c736dc2f78195b99a4
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915608"
---
# <a name="event-descriptions"></a>Ereignis Beschreibungen
Jeder Ereignistyp hat einen bestimmten Zweck.

## <a name="events-and-the-reasons-for-their-use"></a>Ereignisse und die Gründe für deren Verwendung

|Ereignis|Beschreibung|
|-----------|-----------------|
|Dokument Ereignisse aktivieren|Tritt auf, wenn das Debug-Modul (de) möchte, dass die IDE öffnet oder ein Dokument in den Vordergrund bringt.|
|Haltepunkt-oder breakpointfehlerereignisse|Wird gesendet, wenn ein Breakpoint gebunden ist oder wenn ein Haltepunkt nicht gebunden werden kann und ein Fehler zurückgegeben wird.|
|Nicht gebundene Haltepunkt Ereignisse|Tritt auf, wenn ein gebundener Breakpoint die Bindung an Code aufhebt.|
|Ereignisse können beendet werden.|Wird an die IDE gesendet, um zu bestimmen, ob der Benutzer an einem bestimmten Punkt im Code angehalten werden soll.|
|Haltepunkt Ereignisse|Tritt auf, wenn ein Code-oder Daten Haltepunkt getroffen wird.|
|Dokument Text Ereignisse|Tritt auf, wenn Text in einem Dokument geändert wird. Diese Ereignisse werden nicht durch die- `IDebugEventCallBack2::Event` Methode gesendet.|
|Engine-Erstellungs Ereignisse|Wird gesendet, wenn eine Engine erstmalig erstellt wird.|
|Einstiegspunkt Ereignisse|Wird gesendet, wenn das decodierende Programm seinen Initialisierungs Code ausgeführt hat und den ersten Benutzer Einstiegspunkt erreicht hat.|
|Ausnahme Ereignisse|Wird gesendet, wenn ein ausgelaufendes Programm auf eine Ausnahme trifft.|
|Ereignisse beim Abschluss der Ausdrucks Auswertung|Wird gesendet, wenn die asynchrone Ausdrucks Auswertung beendet ist.|
|Symbol Ereignisse suchen|Wird gesendet, wenn der Benutzer den Benutzer zum Suchen von Symbolen für ein Modul auffordern muss.|
|Ereignisse beim Laden vervollständigen|Wird nur gesendet, wenn die anfängliche Programm Last fertiggestellt ist und der erste Code im Programm ausgeführt wird.|
|Nachrichtenereignisse|Wird gesendet, wenn Nachrichten an Benutzer gesendet werden.|
|Modul Lade Ereignisse|Wird gesendet, wenn ein neues Modul geladen oder entladen wird.|
|Ausgabe Zeichen folgen Ereignisse|Wird gesendet, wenn das Programm die Debugausgabe schreibt.|
|Erstellen und zerstören von Ereignissen|Wird gesendet, um die Erstellung oder Zerstörung von Prozessen, Programmen, Eigenschaften, Sitzungen und Threads anzukündigen, damit die Visual Studio-IDE den Zustand der zu debuggenden Programme verfolgen kann.|
|Abgeschlossene Schritt Ereignisse|Wird gesendet, wenn ein Schritt beendet ist.|
|Änderungs Ereignisse für Thread Name|Wird gesendet, wenn der Benutzer den Namen eines Threads ändert.|
|Programmnamen-Änderungs Ereignisse|Wird gesendet, wenn der Benutzer den Namen eines Programms ändert.|

## <a name="see-also"></a>Weitere Informationen
- [Senden von Ereignissen](../../extensibility/debugger/sending-events.md)
