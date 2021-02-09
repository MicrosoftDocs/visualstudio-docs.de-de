---
title: Ports | Microsoft-Dokumentation
description: In diesem Artikel werden die Definition und die Rolle eines Ports in der Debugger-Architektur in Visual Studio beschrieben.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 368d55db8e52d2797041e420d109960c88d96cb6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927183"
---
# <a name="ports"></a>Ports
In der Debugger-Architektur ein *Port*:

- Ist ein Container für eine Gruppe von Prozessen, die auf einem Server ausgeführt werden. Ein Port kann z. b. eine Verbindung mit einem Windows CE basierten Gerät durch ein serielles Kabel oder einen vernetzten nicht-DCOM-Computer darstellen. Ein spezieller Port, der als lokaler Port bezeichnet wird, enthält alle Prozesse, die auf dem lokalen Computer ausgeführt werden.

- Kann sich selbst anhand des Namens oder Bezeichners identifizieren.

- Kann alle Prozesse auflisten, die auf dem Port ausgeführt werden, und diese Prozesse starten und beenden.

- Wird durch eine [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) -Schnittstelle dargestellt, die durch Übergeben eines [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) -Arguments an [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)erstellt wird.

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] stellt einen Standardport bereit, der alle Windows-basierten Prozesse, sowohl System eigen als auch verwaltet, verarbeitet. Ein benutzerdefinierter Port muss für Verbindungen mit externen Geräten eingerichtet werden, die nicht auf Windows basieren. Um solche benutzerdefinierten Ports bereitzustellen, müssen Sie auch einen benutzerdefinierten Port Lieferanten einrichten.

## <a name="see-also"></a>Weitere Informationen
- [Server](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Prozesse](../../extensibility/debugger/processes.md)
- [Debugger-Konzepte](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
