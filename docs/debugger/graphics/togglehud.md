---
title: ToggleHUD | Microsoft-Dokumentation
description: Verwenden der ToggleHUD()-Methode von VsgDbg zum Umschalten, ob das HUD (Head-Up Display) der Grafikdiagnose angezeigt wird, wenn die App ausgeführt wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6cde6549551156f3655f313c23dc66659d2830cf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905051"
---
# <a name="togglehud"></a>ToggleHUD
Schaltet die *HUD*-Überlagerung (Head-Up Display) der Grafikdiagnose ein oder aus.

## <a name="syntax"></a>Syntax

```C++
void ToggleHUD();
```

## <a name="remarks"></a>Hinweise
 Das Grafikdiagnose-HUD wird in der linken oberen Ecke der App angezeigt, die unter der Grafikdiagnose ausgeführt wird. Es werden Laufzeitinformationen zur App und zur Erfassung von Grafikinformationen sowie Meldungen angezeigt, die durch Aufrufen der Memberfunktion [AddMessage](addmessage.md) hinzugefügt werden.

 Um das HUD ein- und auszuschalten, müssen Sie Grafikinformationen nicht aktiv aufzeichnen – d.h. es kann durch eine Instanz der `VsgDbg`-Klasse ein- und ausgeschaltet werden, aber die Memberfunktion [Init](init.md) muss nicht zuerst aufgerufen werden.