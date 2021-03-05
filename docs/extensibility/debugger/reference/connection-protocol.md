---
description: Gibt das Protokoll an, das für die Kommunikation zwischen einem debugserver und dem Debugpaket (de) verwendet wird.
title: CONNECTION_PROTOCOL | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONNECTION_PROTOCOL
helpviewer_keywords:
- CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 24ac267552166bea43df77f31cb79d8198fb7514
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170860"
---
# <a name="connection_protocol"></a>CONNECTION_PROTOCOL
Gibt das Protokoll an, das für die Kommunikation zwischen einem debugserver und dem Debugpaket (de) verwendet wird.

## <a name="syntax"></a>Syntax

```cpp
typedef enum tagCONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
} CONNECTION_PROTOCOL;
```

```csharp
public enum CONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
};
```

## <a name="fields"></a>Felder
`CONNECTION_NONE`\
Es wurde keine Verbindung mit einem Server hergestellt.

`CONNECTION_UNKNOWN`\
Es wurde eine Verbindung hergestellt, Sie weist jedoch einen unbekannten Typ auf.

`CONNECTION_LOCAL`\
Die Verbindung wird mit einem lokalen Server hergestellt.

`CONNECTION_PIPE`\
Die Verbindung erfolgt über eine Named Pipe.

`CONNECTION_TCPIP`\
Die Verbindung verwendet TCP/IP.

`CONNECTION_HTTP`\
Verbindung verwendet HTTP (über einen Webserver).

`CONNECTION_OTHER`\
Ein anderer Verbindungstyp wurde hergestellt (dieser Wert wird derzeit nicht verwendet).

## <a name="remarks"></a>Bemerkungen
Diese Werte werden von der [getconnectionprotocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md) -Methode zurückgegeben.

## <a name="requirements"></a>Requirements (Anforderungen)
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)
