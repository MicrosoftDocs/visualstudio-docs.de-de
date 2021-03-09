---
title: IManagedAddin::Unload
description: Wird unmittelbar vor dem Entladen eines verwalteten VSTO-Add-Ins aufgerufen.
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Unload method
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e45fd9e6385388b9c6bc32098cf59799618d511b
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2021
ms.locfileid: "102469709"
---
# <a name="imanagedaddinunload"></a>IManagedAddin::Unload
  Wird unmittelbar vor dem Entladen eines verwalteten VSTO-Add-Ins aufgerufen.

## <a name="syntax"></a>Syntax

```csharp
HRESULT Unload();
```

## <a name="return-value"></a>Rückgabewert
 Ein HRESULT-Wert, der angibt, ob die Methode erfolgreich abgeschlossen wurde.

## <a name="remarks"></a>Bemerkungen
 Diese Methode wird von aktuellen Versionen von Microsoft Office nicht aufgerufen. Diese Methode ist für eine spätere Verwendung vorgesehen.

## <a name="see-also"></a>Siehe auch
- [IManagedAddin-Schnittstelle](../vsto/imanagedaddin-interface.md)
- [IManagedAddin::Load](../vsto/imanagedaddin-load.md)
