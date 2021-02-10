---
title: Wo sind die Win32-Fehlercodes zu finden? | Microsoft-Dokumentation
description: Sie können einen Win32-Fehlercode suchen, indem Sie ihn in „Überwachung“ oder „Schnellüberwachung“ eingeben. Zum Beispiel den Fehlercode „0x80000004,hr“. Die Fehlercodedefinitionen finden Sie unter INCLUDE\WINERROR.H.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vc.errors
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- error codes, Win32
- Win32, error codes
ms.assetid: 8fb4ff42-b8eb-4152-b49e-b802d194b05e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c4eb61a6eda5848277a1da95f9282b396b413ad5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883830"
---
# <a name="where-can-i-look-up-win32-error-codes"></a>Wo sind die Win32-Fehlercodes zu finden?
WINERROR.H im Verzeichnis INCLUDE der Standardsysteminstallation enthält die Definitionen der Fehlercodes für die Win32-API-Funktionen.

 Sie können den Fehlercode nachsehen, indem Sie den Code im **Überwachungsfenster** oder im Dialogfeld **Schnellüberwachung** eingeben. Zum Beispiel:

`0x80000004,hr`

## <a name="see-also"></a>Siehe auch
- [FAQs zum Debuggen von nativem Code](../debugger/debugging-native-code-faqs.md)
- [Debuggen von nativem Code](../debugger/debugging-native-code.md)