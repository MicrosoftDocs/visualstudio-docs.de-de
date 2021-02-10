---
title: WriteAllTLogs | Microsoft-Dokumentation
description: Erfahren Sie mehr über Syntax, Anforderungen und Rückgabewert für die Funktion „WriteAllTLogs“ zum Schreiben von Nachverfolgungsprotokollen für alle Threads und Kontexte.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- WriteAllTLogs
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- WriteAllTLogs
ms.assetid: 1fa3e10b-263c-4960-a9ad-485c02a7a872
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 65e0610c8148ab6ff32d8c19f6fd378ba46d76d5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933595"
---
# <a name="writealltlogs"></a>WriteAllTLogs

Schreibt Nachverfolgungsprotokolle für alle Threads und Kontexte

## <a name="syntax"></a>Syntax

```cpp
HRESULT WINAPI WriteAllTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);
```

#### <a name="parameters"></a>Parameter

[in] `intermediateDirectory`

 Das Verzeichnis, in dem das Nachverfolgungsprotokoll gespeichert werden soll

[in] `tlogRootName`

 Der Stammname des Namens der Protoktolldatei

## <a name="return-value"></a>Rückgabewert

 Ein **HRESULT**, bei dem **SUCCEEDED** festgelegt ist, wenn der Nachverfolgungskontext erstellt wurde

## <a name="requirements"></a>Anforderungen

 **Header:** *FileTracker.h*

## <a name="see-also"></a>Weitere Informationen:

- [WriteContextTLogs](../msbuild/writecontexttlogs.md)