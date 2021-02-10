---
title: DONT_SAVE_VSGLOG_TO_TEMP | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f94b287f6ed9d4cda0696252ba32d493879ed5c1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880267"
---
# <a name="dont_save_vsglog_to_temp"></a>DONT_SAVE_VSGLOG_TO_TEMP
Definiert durch das Vorhandensein, ob die Grafikprotokolldatei im Verzeichnis der temporären Dateien des Benutzers gespeichert wird.

## <a name="syntax"></a>Syntax

```C++
#define DONT_SAVE_VSGLOG_TO_TEMP
```

## <a name="value"></a>Wert
 Ein Präprozessorsymbol, das durch sein Vorhandensein bzw. seine Abwesenheit bestimmt, ob die Grafikprotokolldatei im Verzeichnis der temporären Dateien des Benutzers gespeichert wird. Wenn dieses Symbol definiert wird, ist der Dateiname, der durch `VSG_DEFAULT_RUN_FILENAME` definiert ist, relativ zum aktuellen Verzeichnis der erfassten App oder ein absoluter Pfad. Andernfalls ist der Dateiname, der durch `VSG_DEFAULT_RUN_FILENAME` definiert ist, relativ zum Verzeichnis der temporären Dateien des Benutzers und kann kein absoluter Pfad sein.

## <a name="remarks"></a>Hinweise
 Abhängig von den Berechtigungen des Benutzers kann die Grafikprotokolldatei möglicherweise nicht an einem beliebigen Speicherort gespeichert werden. Es wird empfohlen, Grafikprotokolle vorzugsweise im Verzeichnis der temporären Dateien des Benutzers oder an einem anderen, als funktionierend bekannten Speicherort zu speichern, wenn Sie unsicher sind, ob in den Speicherort, den Sie auswählen würden, vom Benutzer geschrieben werden kann.

 Um zu verhindern, dass die Grafikprotokolldatei im Verzeichnis der temporären Dateien gespeichert wird, müssen Sie `DONT_SAVE_VSGLOG_TO_TEMP` definieren, bevor Sie `vsgcapture.h` einschließen.

## <a name="example"></a>Beispiel
 Dieses Beispiel zeigt, wie Sie die Grafikprotokolldatei in einem absoluten Pfad auf dem Hostcomputer speichern können.

```cpp
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h
#define DONT_SAVE_VSGLOG_TO_TEMP
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"

#include <vsgcapture.h>
```

## <a name="see-also"></a>Siehe auch
- [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)
