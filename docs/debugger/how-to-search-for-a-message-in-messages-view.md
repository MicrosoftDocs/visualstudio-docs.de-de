---
title: Suchen einer Meldung in der Meldungsansicht | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie beim Debuggen in Visual Studio mithilfe des Handles, des Typs oder der Meldungs-ID als Suchkriterien nach einer bestimmten Meldung in der Ansicht „Meldungen“ des Spy++-Tools suchen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Message Search dialog box
- Messages view
- messages, searching for
ms.assetid: 732b7ccc-54ea-41db-823b-2b96e3e4083e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c351eacc6fc3793065bcd11eb5456eebdc1864f3
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148584"
---
# <a name="how-to-search-for-a-message-in-messages-view"></a>Vorgehensweise: Suchen einer Meldung in der Meldungsansicht
Sie können in der Meldungsansicht nach einer bestimmten Meldung suchen, indem Sie das Handle, den Typ oder die Meldungs-ID als Suchkriterium verwenden. Diese sind einzeln oder kombiniert als Suchkriterium zulässig. Sie können auch die anfängliche Suchrichtung angeben. Die Felder im Dialogfeld werden vorab mit den Attributen der aktuell ausgewählten Meldung aufgefüllt.

### <a name="to-search-for-a-message-in-messages-view"></a>Suchen einer Meldung in der Meldungsansicht

1. Ordnen Sie die Fenster so an, dass Spy++ und eine aktive [Meldungsansicht](../debugger/messages-view.md) sichtbar sind.

2. Wählen Sie im Menü **Suchen** die Option **Meldung suchen** aus.

    Das Dialogfeld für die [Meldungssuche](../debugger/message-search-dialog-box.md) wird geöffnet.

3. Ziehen Sie das **Suchtool** zum gewünschten Fenster. Während Sie das Tool ziehen, werden im Dialogfeld für die **Meldungssuche** Details zum ausgewählten Fenster angezeigt.

   - ODER

     Wenn Sie das Handle des Fensters kennen, dessen Meldungen Sie untersuchen möchten, geben Sie dieses in das Textfeld **Handle** ein.

   - ODER

     Wenn Sie den gewünschten Meldungstyp und/oder die gewünschte Meldungs-ID kennen, wählen Sie diese in den Dropdownmenüs **Typ** und **Meldung** aus, und deaktivieren Sie das Textfeld **Handle**.

4. Deaktivieren Sie alle Felder, für die Sie keine Werte angeben möchten.

   > [!TIP]
   > Damit der Bildschirm übersichtlich bleibt, wählen Sie die Option **Spy++ ausblenden** aus. Mit dieser Option wird das Spy++-Hauptfenster verborgen, sodass nur das Dialogfeld **Fenster suchen** über den anderen Anwendungen angezeigt wird. Das Spy++-Hauptfenster wird wiederhergestellt, wenn Sie auf **OK** oder **Abbrechen** klicken oder die Option **Spy++ ausblenden** deaktivieren.

5. Sie können auch **Nach oben** oder **Nach unten** als anfängliche Suchrichtung angeben.

6. Klicken Sie auf **OK**.

   Wenn eine übereinstimmende Meldung gefunden wird, wird sie in der Meldungsansicht hervorgehoben. Weitere Informationen finden Sie unter [Meldungsansicht](../debugger/messages-view.md).