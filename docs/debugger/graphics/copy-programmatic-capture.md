---
title: Kopieren (programmgesteuerte Aufzeichnung) | Microsoft-Dokumentation
description: Verwenden Sie die Copy-Methode der VsgDbg-Klasse, um den Inhalt der aktiven Grafikprotokolldatei (.vsglog) in eine neue Datei zu kopieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 62140f279d805e5162661c22110671871afff1ae
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879188"
---
# <a name="copy-programmatic-capture"></a>Kopieren (Programmgesteuerte Aufzeichnung)
Kopiert den Inhalt der aktiven Grafikprotokolldatei (VSGLOG) in eine neue Datei.

## <a name="syntax"></a>Syntax

```C++
void Copy(
  wchar_t const * szNewVSGLog
);
```

#### <a name="parameters"></a>Parameter
 `szNewVSGLog` Der Dateiname der neuen Grafikprotokolldatei.

## <a name="remarks"></a>Hinweise
 Um die Grafikinformationen in eine neuen Datei zu kopieren, müssen Sie bereits einige Grafikinformationen erfasst haben, andernfalls geschieht nichts.