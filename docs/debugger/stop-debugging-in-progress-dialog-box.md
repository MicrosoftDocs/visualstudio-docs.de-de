---
title: Dialogfeld „Debuggen wird abgebrochen“ | Microsoft-Dokumentation
description: In diesem Artikel wird das Dialogfeld „Debuggen wird abgebrochen“ erläutert, das angezeigt wird, wenn der Debugger versucht, eine Debugsitzung zu beenden, aber das Beenden der Sitzung dauert eine Weile.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.stopnow
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Stop Debugging in Progress dialog box
ms.assetid: ed7ef49d-e25f-4a4d-9396-9bc7b4143117
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ae8cb1935a5f88335411d5284f32267a9a65e4da
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904979"
---
# <a name="stop-debugging-in-progress-dialog-box"></a>Debuggen wird beendet (Dialogfeld)
Dieses Dialogfeld wird angezeigt, wenn vom Debugger versucht wird, eine Debugsitzung zu beenden, der Beendigungsvorgang jedoch einige Zeit dauert. Das Beenden einer Debugsitzung erfolgt normalerweise sehr schnell, sodass dieses Dialogfeld nicht angezeigt wird. Manchmal dauert es jedoch eine Weile, bis alle derzeit debuggten Prozesse getrennt sind. Wenn das Beenden der Sitzung mehrere Sekunden dauert (bzw. ein Fehler beim Trennen auftritt), wird dieses Dialogfeld angezeigt. Bei wiederholtem Auftreten kann dies auf ein internes Problem hindeuten. Nehmen Sie ggf. Kontakt zum Produktsupport auf.

 Sie können entweder warten, bis alle Prozesse getrennt sind und dieses Dialogfeld ausgeblendet wird, oder Sie erzwingen über die Schaltfläche **Jetzt beenden** die sofortige Beendigung.

 **Jetzt beenden**: Klicken Sie auf diese Schaltfläche, um die Debugsitzung sofort zu beenden. Durch **Jetzt beenden** werden die debuggten Prozesse beendet, aber nicht getrennt. Wenn Sie Systemprozesse debuggen und die Prozesse mit **Jetzt beenden** stoppen, kann es zu unerwarteten und unerwünschten Folgen kommen.

## <a name="see-also"></a>Siehe auch
- [Debuggersicherheit](../debugger/debugger-security.md)
- [Trennen von Programmen](/previous-versions/visualstudio/visual-studio-2010/x1thkxez(v=vs.100))