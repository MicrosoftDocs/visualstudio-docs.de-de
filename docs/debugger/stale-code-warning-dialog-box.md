---
title: 'Dialogfeld „Warnung: Veralteter Code“ | Microsoft-Dokumentation'
description: 'In diesem Artikel erfahren Sie mehr über das Dialogfeld „Warnung: Veralteter Code“, die angezeigt wird, wenn Sie Änderungen an nativem Code vorgenommen haben, die nicht vom Feature „Bearbeiten und fortfahren“ direkt angewendet werden konnten.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.ENC.stalecode
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Stale Code Warning dialog box
- code, stale code warning
- warnings, Stale Code Warning dialog box
- Edit and Continue, stale code
ms.assetid: 594b894c-e652-4e13-a980-9909473d5712
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5bb2666b3b57c8f84c81e181355f096674543445
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150326"
---
# <a name="stale-code-warning-dialog-box"></a>Warnung: Veralteter Code (Dialogfeld)

Dieses Dialogfeld wird angezeigt, wenn Sie Änderungen an nativem Code vorgenommen haben, die von der **Bearbeiten und Fortfahren**-Funktion nicht sofort übernommen werden konnten. Dadurch ist ein Teil des nativen Codes im aktuellen Stapelrahmen nicht mehr aktuell (veraltet). Weitere Informationen hierzu finden Sie unter [Bearbeiten und Fortfahren (C++)](edit-and-continue-visual-cpp.md).

**Dieses Dialogfeld nicht mehr anzeigen**

Wenn Sie dieses Kontrollkästchen aktivieren, werden Codeänderungen zukünftig ohne Rückfrage von "Bearbeiten und Fortfahren" übernommen. Sie können diese Warnung erneut aktivieren, indem Sie im Dialogfeld **Optionen** den Ordner **Debuggen** öffnen, auf die Seite **Bearbeiten und Fortfahren** klicken und die Option **Warnung bei veraltetem Code** auswählen.

## <a name="see-also"></a>Siehe auch

- [Unterstützte Codeänderungen (C++)](supported-code-changes-cpp.md)
- [Bearbeiten und Fortfahren, Debuggen, Dialogfeld „Optionen“](edit-and-continue.md)