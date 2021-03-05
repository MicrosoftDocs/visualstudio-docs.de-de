---
description: Bezieht eine angegebene Schnittstelle über Prozess Grenzen hinweg.
title: 'IDebugProviderProgramNode2:: unmarshalbebuggeeinterface | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
helpviewer_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0f51484ae1e9acbb9b94fe546f8157145673e22f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167866"
---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
Bezieht eine angegebene Schnittstelle über Prozess Grenzen hinweg.

## <a name="syntax"></a>Syntax

```cpp
HRESULT UnmarshalDebuggeeInterface(
   REFIID riid,
   void** ppvObject
);
```

```csharp
int UnmarshalDebuggeeInterface(
   ref Guid   riid,
   out IntPtr ppvObject
);
```

## <a name="parameters"></a>Parameter
`riid`\
in GUID der abzurufenden Schnittstelle.

`ppvObject`\
vorgenommen Gibt das Objekt zurück, das die gewünschte Schnittstelle implementiert. [C++] Dies kann direkt in den gewünschten Schnittstellentyp umgewandelt werden. [C#] verwenden Sie die- <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> Methode, um die gewünschte Schnittstelle zu erhalten.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode wird verwendet, wenn die Debug-Engine im [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Prozessbereich ausgeführt wird und das zu debuggende Programm in einem eigenen Prozessbereich ausgeführt wird.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)
