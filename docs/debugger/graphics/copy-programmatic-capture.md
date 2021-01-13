---
title: Kopieren (programmgesteuerte Aufzeichnung) | Microsoft-Dokumentation
description: Verwenden Sie die Copy-Methode der VsgDbg-Klasse, um den Inhalt der aktiven Grafikprotokolldatei (.vsglog) in eine neue Datei zu kopieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 126b1d7a2fa9064a343e7eadbe83dd1eeecccb83
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727843"
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