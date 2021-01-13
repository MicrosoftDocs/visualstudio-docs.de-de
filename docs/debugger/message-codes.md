---
title: Meldungscodes | Microsoft-Dokumentation
description: Informieren Sie sich über die Bedeutungen der Meldungscodes, die in den einzelnen Meldungszeilen der Meldungsansicht angezeigt werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e4b836a5d4c1faad6b4c0375e2ec51d759816889
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903609"
---
# <a name="message-codes"></a>Meldungscodes
Jede Meldungszeile, die in der [Meldungsansicht](../debugger/messages-view.md) angezeigt wird, enthält den Code „P“, „S“, „s“ oder „R“. Diese Codes haben folgende Bedeutung:

|Code|Bedeutung|
|----------|-------------|
|P|Die Meldung wurde mit der Funktion **PostMessage** an die Warteschlange gesendet. Zur endgültigen Disposition der Meldung sind keine Informationen verfügbar.|
|S|Die Meldung wurde mit der Funktion **SendMessage** gesendet. Dies bedeutet, dass der Absender die Kontrolle erst wiedererlangt, wenn der Empfänger die Meldung verarbeitet und zurückgibt. Der Empfänger kann daher einen Rückgabewert an den Absender zurückgeben.|
|s|Die Meldung wurde zwar gesendet, doch verhindert die Sicherheit den Zugriff auf den Rückgabewert.|
|R|Jede Zeile mit dem Code „S“ verfügt über eine entsprechende Zeile mit dem Code „R“ (Rückgabe), die den Rückgabewert der Meldung enthält. Manchmal sind Meldungsaufrufe geschachtelt. Das bedeutet, dass ein Meldungshandler eine weitere Nachricht sendet.|