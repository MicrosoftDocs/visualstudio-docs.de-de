---
description: Ruft die Prozess-ID des Ports selbst ab.
title: 'IDebugPortEx2:: getportprocessid | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::GetPortProcessId
helpviewer_keywords:
- IDebugPortEx2::GetPortProcessId
ms.assetid: be85be66-47e6-415f-b0ca-24599aa5f13c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e10dbc648f8233a826c440c261308c6c3688fa30
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169430"
---
# <a name="idebugportex2getportprocessid"></a>IDebugPortEx2::GetPortProcessId
Ruft die Prozess-ID des Ports selbst ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetPortProcessId ( 
   DWORD* pdwProcessId
);
```

```csharp
int GetPortProcessId ( 
   out uint pdwProcessId
);
```

## <a name="parameters"></a>Parameter
`pdwProcessId`\
vorgenommen Gibt die physische Prozess-ID des Ports selbst zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Im Win32-Lauf Zeit Modul ruft diese Methode beispielsweise in der Regel die Win32-Funktion `GetCurrentProcessId` auf, um die physische Prozess-ID zu erhalten.

## <a name="see-also"></a>Weitere Informationen
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
