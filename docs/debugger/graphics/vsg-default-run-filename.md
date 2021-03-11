---
description: Definiert den Standarddateinamen der Grafikprotokolldatei.
title: VSG_DEFAULT_RUN_FILENAME | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5f6bd07e54fc90bcc99f7462cc087ba01866727c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160479"
---
# <a name="vsg_default_run_filename"></a>VSG_DEFAULT_RUN_FILENAME
Definiert den Standarddateinamen der Grafikprotokolldatei.

## <a name="syntax"></a>Syntax

```C++
#define VSG_DEFAULT_FILENAME filename
```

#### <a name="parameters"></a>Parameter
 `filename` Der Dateiname, der der Grafikprotokolldatei standardmäßig zugewiesen wird, wenn Grafikinformationen programmgesteuert erfasst werden.

## <a name="value"></a>Wert
 Ein Zeichenfolgenliteral, das den Dateinamen der Grafikprotokolldatei darstellt. Standardmäßig ist dies L"default.vsglog".

```C++
#define VSG_DEFAULT_FILENAME L"default.vsglog"
```

## <a name="remarks"></a>Hinweise
 Wenn das Präprozessorsymbol `DONT_SAVE_VSGLOG_TO_TEMP` definiert ist, ist der Dateiname relativ zum aktuellen Verzeichnis der aufgezeichneten App oder ein absoluter Pfad. Andernfalls ist er relativ zum Verzeichnis der temporären Dateien des Benutzers und kann kein absoluter Pfad sein.

 Um den definierten Dateinamen zu ändern, müssen Sie ihn erneut definieren, bevor Sie `vsgcapture.h` in Ihr Programm einschließen.

## <a name="example"></a>Beispiel
 Dieses Beispiel zeigt, wie der Standarddateiname der Erfassungsdatei geändert wird:

```C++
// Redefine the default capture filename before including vsgcapture.h
#define VSG_DEFAULT_FILENAME L"capture.vsglog"

#include <vsgcapture.h>
```

## <a name="see-also"></a>Siehe auch
- [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)
