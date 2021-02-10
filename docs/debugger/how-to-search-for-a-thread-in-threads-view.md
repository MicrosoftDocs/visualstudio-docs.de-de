---
title: Suchen nach einem Thread in der Threadansicht | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie beim Debuggen in Visual Studio in der Ansicht „Threads“ des Spy++-Tools nach einem bestimmten Thread suchen, indem Sie die Thread-ID oder die Modulzeichenfolge als Suchkriterium verwenden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- threads, searching
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 85d82897144a0ed366d95dfa590a09224a875f55
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99845060"
---
# <a name="how-to-search-for-a-thread-in-threads-view"></a>Vorgehensweise: Suchen nach einem Thread in der Threadansicht
Sie können in der Threadansicht nach einem bestimmten Thread suchen, indem Sie die Thread-ID oder die Modulzeichenfolge als Suchkriterium verwenden. Sie können auch die anfängliche Richtung der Suche angeben. In den Feldern im Dialogfeld werden die Attribute des ausgewählten Threads in der Threadstruktur angezeigt.

### <a name="to-search-for-a-thread-in-threads-view"></a>Suchen nach einem Thread in der Threadansicht

1. Ordnen Sie die Fenster so an, dass Spy++ und ein aktives [Threadansichtsfenster](../debugger/threads-view.md) sichtbar sind.

2. Klicken Sie im Menü **Suche** auf **Thread suchen**.

    Das Dialogfeld [Threadsuche](../debugger/thread-search-dialog-box.md) wird geöffnet.

3. Geben Sie die Thread-ID oder eine Modulzeichenfolge als Suchkriterium ein.

4. Deaktivieren Sie alle Felder, für die Sie keine Werte angeben möchten.

   > [!TIP]
   > Deaktivieren Sie das Textfeld **Thread**, und geben Sie im Feld **Modul** den Modulnamen ein, um alle Threads zu suchen, die sich im Besitz eines Moduls befinden. Verwenden Sie dann **Weitersuchen**, um mit der Suche nach Threads fortzufahren.

5. Sie können auch **Nach oben** oder **Nach unten** als anfängliche Suchrichtung angeben.

6. Klicken Sie auf **OK**.

   Wenn ein übereinstimmender Thread gefunden wird, wird er im Threadansichtsfenster hervorgehoben.