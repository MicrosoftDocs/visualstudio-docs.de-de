---
title: Implementieren und Registrieren eines Port Anbieters | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie einen Port Lieferanten implementieren und registrieren, der Ports nachverfolgt und bereitstellt, die Prozesse verwalten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d5639c45fd6dff6702ebc197d46c2eafe482e1d0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926360"
---
# <a name="implement-and-register-a-port-supplier"></a>Implementieren und Registrieren eines Port Anbieters
Die Rolle eines Port Lieferanten besteht im nachverfolgen und Bereitstellen von Ports, die wiederum Prozesse verwalten. Wenn ein Port erstellt werden muss, wird der Port Lieferant mithilfe von CoCreate mit der GUID des portanbieters instanziiert (der Sitzungs-Debug-Manager [SDM] verwendet den vom Benutzer ausgewählten Port Anbieter oder den vom Projekt System angegebenen Port Lieferanten). Der SDM ruft dann [canaddport](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) auf, um zu überprüfen, ob Ports hinzugefügt werden können. Wenn ein Port hinzugefügt werden kann, wird ein neuer Port angefordert, indem [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) aufgerufen und ein [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) übergeben wird, der den Port beschreibt. `AddPort` Gibt einen neuen von einer [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) -Schnittstelle dargestellten Port zurück.

## <a name="discussion"></a>Diskussion
 Ein Port wird von einem Port Lieferanten erstellt, der einem Computer oder einem debugserver zugeordnet ist. Ein Server listet seine Port Lieferanten über die[enumportsuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) -Methode auf, und ein Port Lieferant listet seine Ports über die [enumports](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) -Methode auf.

 Neben der typischen com-Registrierung muss sich ein Port Lieferant bei Visual Studio registrieren, indem er seine CLSID und den Namen an bestimmten Registrierungsstellen platziert. Eine debugginghilfsfunktion `SetMetric` , die aufgerufen wird, behandelt dieses Chore: Sie wird für jedes zu registrierende Element einmal aufgerufen, sodass Folgendes gilt:

```cpp
SetMetric(metrictypePortSupplier,
          <GUID of your port supplier>,
          metricCLSID,
          <CLSID of your port supplier>,
          false,
          NULL)
SetMetric(metrictypePortSupplier,
          <GUID of your port supplier>,
          metricName,
          <name of your port supplier>,
          false,
          NULL);
```

 Ein Port Lieferant hebt die Registrierung selbst `RemoveMetric` auf, indem er für jedes registrierte Element einmal aufruft (eine andere debugginghilfsfunktion):

```cpp
RemoveMetric(metrictypePortSupplier,
             <GUID of your port supplier>,
             metricCLSID,
             NULL);
RemoveMetric(metrictypePortSupplier,
             <GUID of your port supplier>,
             metricName,
             NULL);
```

> [!NOTE]
> Die [SDK-Hilfsprogramme für das Debuggen](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` und `RemoveMetric` sind statische Funktionen, die in " *dbgmetric. h* " definiert und in *ad2de. lib* kompiliert werden. Die Hilfsprogramme `metrictypePortSupplier` , `metricCLSID` und `metricName` werden auch in *dbgmetric. h* definiert.

 Ein Port Lieferant kann seinen Namen und die GUID über die Methoden " [getportsuppliername](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) " und " [getportsupplierid](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)" angeben.

## <a name="see-also"></a>Weitere Informationen
- [Implementieren eines Port Anbieters](../../extensibility/debugger/implementing-a-port-supplier.md)
- [SDK-Hilfsprogramme zum Debuggen](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Port Lieferanten](../../extensibility/debugger/port-suppliers.md)
