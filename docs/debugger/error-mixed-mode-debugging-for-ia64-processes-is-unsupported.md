---
title: Debuggen im gemischten Modus wird auf Windows 64-Bit-Plattformen nicht unterstützt | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.interop_unsupported_ia64
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 22fa1b7f332d6a9f6481c513a3c2024a3551c7a5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871584"
---
# <a name="error-mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>Fehler: Debuggen im gemischten Modus wird auf Windows 64-Bit-Plattformen nicht unterstützt
Der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Debugger unterstützt das Debuggen von gemischtem systemeigenem und verwaltetem Code in Itanium-basierten Prozessen nicht.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

- Erstellen Sie eine 32-Bit-Version der Anwendung zum Debuggen.

## <a name="see-also"></a>Siehe auch
- [Remote Debugging](../debugger/remote-debugging.md)