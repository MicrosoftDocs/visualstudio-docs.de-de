---
title: Öffnen der Meldungsansicht aus dem Fenster „Suchen“ | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie das Dialogfeld „Fenster suchen“ von Spy++ verwenden und dann die Ansicht „Meldungen“ für dieses Fenster öffnen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Messages View in Spy++, opening
- opening Messages View in Spy++
ms.assetid: 601a193e-432a-417b-9406-6fec9e401264
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e66e3e1200e1e08776853f2ac8308537e4b4a17
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148909"
---
# <a name="how-to-open-messages-view-from-find-window"></a>Vorgehensweise: Öffnen der Meldungsansicht aus dem Fenster „Suchen“
Möglicherweise finden Sie es bequem, das Dialogfeld **Fenster suchen** zum Auswählen eines Zielfensters zu verwenden, um dann eine Meldungsansicht dieses Fensters zu öffnen.

### <a name="to-open-a-messages-view-window-using-the-find-window-dialog-box"></a>So öffnen Sie ein Meldungsansichtsfenster mithilfe des Dialogfelds „Fenster suchen“

1. Ordnen Sie Ihre Fenster so an, dass sowohl Spy++ als auch das Zielfenster sichtbar sind.

2. Wählen Sie im Menü **Spy** die Option **Fenster suchen** aus.

    Das [Dialogfeld „Fenster suchen“](../debugger/find-window-dialog-box.md) wird geöffnet.

3. Ziehen Sie das **Suchtool** von der Registerkarte **Fenster** über das Zielfenster. Während Sie das Tool ziehen, werden im Dialogfeld **Fenster suchen** Details zum ausgewählten Fenster angezeigt.

   - ODER

     Wenn Sie über das Handle des zu untersuchenden Fensters verfügen, (z. B. aus dem Debugger kopiert), können Sie es in das Textfeld **Handle** eingeben.

4. Wählen Sie unter **Anzeigen** die Option **Meldungen** aus.

5. Klicken Sie auf **OK**.

    Ein leeres [Meldungsansicht](../debugger/messages-view.md)sfenster wird geöffnet, und der Spy++-Symbolleiste wird ein Menü **Meldungen** hinzugefügt.

6. Wählen Sie im Menü **Meldungen** die Option **Protokollierungsoptionen** aus.

    Das Dialogfeld [Meldungsoptionen](../debugger/message-options-dialog-box.md) wird geöffnet.

7. Wählen Sie die Optionen für die Meldung aus, die Sie anzeigen möchten.

8. Drücken Sie **OK**, um mit der Protokollierung von Meldungen zu beginnen.

    Abhängig von den ausgewählten Optionen wird der Meldungsdatenstrom in das aktive Meldungsansichtsfenster gestartet.

9. Wenn genügend Meldungen eingegangen sind, wählen Sie **Protokollierung beenden** im Menü **Meldungen** aus.
