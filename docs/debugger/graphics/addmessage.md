---
title: AddMessage | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie die AddMessage-Methode der VsgDbg-Klasse verwenden, um eine benutzerdefinierte Nachricht zum Grafikdiagnose-HUD (Head-Up-Display) hinzuzufügen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d9d51e4415d9707b2df4bb0912290d4f5aa7825f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874638"
---
# <a name="addmessage"></a>AddMessage
Fügt dem Grafikdiagnose-*HUD* (Head-Up Display) eine benutzerdefinierte Meldung hinzu.

## <a name="syntax"></a>Syntax

```C++
void AddMessage(
  wchar_t const * szMessage
);
```

#### <a name="parameters"></a>Parameter
 `szMessage` Die dem HUD hinzuzufügende Meldung.

## <a name="remarks"></a>Hinweise
 Das Grafikdiagnose-HUD wird in der linken oberen Ecke der App angezeigt, die unter der Grafikdiagnose ausgeführt wird. Es werden Laufzeitinformationen über die App und die Erfassung von Grafikinformationen sowie Meldungen angezeigt, die hinzugefügt werden, indem diese Funktion aufgerufen wird.

 Um dem HUD eine Meldung hinzuzufügen, müssen Sie Grafikinformationen nicht aktiv erfassen – d.h. eine Meldung kann durch eine Instanz der `VsgDbg`-Klasse hinzugefügt werden, die Memberfunktion [Init](init.md) muss jedoch nicht zuerst aufgerufen werden. Meldungen werden nur im HUD angezeigt, sie werden nicht in der Grafikprotokolldatei aufgezeichnet.