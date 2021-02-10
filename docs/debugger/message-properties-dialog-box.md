---
title: Dialogfeld „Meldungseigenschaften“ | Microsoft-Dokumentation
description: Unter „Meldungseigenschaften“ finden Sie weitere Informationen zu einer Meldung, die in der Meldungsansicht angezeigt wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message options
- message options, General
ms.assetid: 58e9dc24-baf6-4ab8-916c-aea28b72e3b0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: eee5d21e013dd43a361a229a3189cc44d6294e70
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891747"
---
# <a name="message-properties-dialog-box"></a>Dialogfeld "Meldungseigenschaften"
Verwenden Sie dieses Dialogfeld, um mehr über eine bestimmte Meldung zu erfahren. Um dieses Dialogfeld anzuzeigen, verschieben Sie den Fokus in ein [Meldungsansichtsfenster](../debugger/messages-view.md). Wählen Sie einen beliebigen Meldungsknoten in der Struktur aus, und wählen Sie anschließend im Menü **Ansicht** die Option **Eigenschaften** aus.

 Die Registerkarte **Allgemein** wird als einzige Registerkarte angezeigt. Die folgenden Einstellungen sind verfügbar:

 **Fensterhandle**: Die eindeutige ID dieses Fensters. Die Nummern von Fensterhandles werden wiederverwendet. Sie identifizieren ein Fenster nur während dessen Lebensdauer. Wählen Sie diesen Wert aus, um die Eigenschaften dieses Fensters anzuzeigen.

 **Schachtelungsebene**: Schachtelungstiefe dieser Meldung, wobei 0 keine Schachtelung bedeutet.

 **Meldung**: Nummer, Status und Name der im Fenster ausgewählten Meldung.

 **lResult**: Wert des Parameters *lResult* (sofern vorhanden).

 **wParam**: Wert des Parameters *wParam* (sofern vorhanden).

 **lParam**: Wert des Parameters *lParam* (sofern vorhanden). Dieser Wert wird decodiert, wenn es sich um einen Zeiger auf eine Zeichenfolge oder Struktur handelt.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Dialogfeld „Meldungsoptionen“](../debugger/message-options-dialog-box.md): Dient zur Auswahl der in der aktiven Meldungsansicht angezeigten Meldungen.

 [Dialogfeld „Meldungssuche“](../debugger/message-search-dialog-box.md): Dient zum Suchen des Knotens für eine bestimmte Meldung in der Meldungsansicht.

 [Spy++-Referenz](../debugger/spy-increment-reference.md): Enthält Abschnitte mit Beschreibungen der einzelnen Menüs und Dialogfelder von Spy++.

 [Öffnen der Meldungsansicht über „Fenster suchen“](../debugger/how-to-open-messages-view-from-find-window.md): Erläutert, wie die Meldungsansicht im Dialogfeld „Fenster suchen“ geöffnet wird.

 [Suchen einer Meldung in der Meldungsansicht](../debugger/how-to-search-for-a-message-in-messages-view.md): Erläutert, wie Sie in der Meldungsansicht eine bestimmte Meldung finden.

 [Meldungsansicht](../debugger/messages-view.md): Zeigt den Meldungsdatenstrom an, der einem Fenster, einem Prozess oder einem Thread zugeordnet ist.

 [Spy++-Ansichten](../debugger/spy-increment-views.md): Erläutert die Spy++-Strukturansichten von Fenstern, Meldungen, Prozessen und Threads.

 [Verwenden von Spy++](../debugger/using-spy-increment.md): Bietet eine Einführung in das Tool Spy++ und erläutert, wie es verwendet werden kann.