---
title: Suchen eines Prozesses in der Prozessansicht | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie beim Debuggen in Visual Studio in der Ansicht „Prozesse“ des Spy++-Tools nach einem bestimmten Prozess suchen, indem Sie die Prozess-ID oder die Modulzeichenfolge als Suchkriterium verwenden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Processes view
- processes, searching for
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 85b2c2bab29316846620c7dbec935b41eec1d9df
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99845073"
---
# <a name="how-to-search-for-a-process-in-processes-view"></a>Vorgehensweise: Suchen eines Prozesses in der Prozessansicht
Sie können in der Prozessansicht nach einem bestimmten Prozess suchen, indem Sie die Prozess-ID oder die Modulzeichenfolge als Suchkriterium verwenden. Sie können auch die anfängliche Richtung der Suche angeben. In den Feldern im Dialogfeld werden die Attribute des ausgewählten Prozesses in der Prozessstruktur angezeigt.

### <a name="to-search-for-a-process-in-processes-view"></a>So suchen Sie einen Prozess in der Prozessansicht

1. Ordnen Sie die Fenster so an, dass Spy++ und ein aktives [Prozessansichtsfenster](../debugger/processes-view.md) sichtbar sind.

2. Wählen Sie im Menü **Suchen** die Option **Prozess suchen** aus.

    Das [Dialogfeld „Prozesssuche“](../debugger/process-search-dialog-box.md) wird geöffnet.

3. Geben Sie die Prozess-ID oder eine Modulzeichenfolge als Suchkriterium ein.

4. Deaktivieren Sie alle Felder, für die Sie keine Werte angeben möchten.

   > [!TIP]
   > Um alle Prozesse zu suchen, die sich im Besitz eines Moduls befinden, deaktivieren Sie das Feld **Prozess**, und geben Sie im Feld **Modul** den Modulnamen ein. Verwenden Sie dann **Weitersuchen**, um mit der Suche nach Prozessen fortzufahren.

5. Sie können auch **Nach oben** oder **Nach unten** als anfängliche Suchrichtung angeben.

6. Klicken Sie auf **OK**.

   Wenn ein übereinstimmender Prozess gefunden wird, wird er im **Prozessansichtsfenster** hervorgehoben.