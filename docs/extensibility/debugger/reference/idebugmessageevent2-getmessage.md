---
description: Ruft die Meldung ab, die angezeigt werden soll.
title: 'IDebugMessageEvent2:: getMessage | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2::GetMessage
helpviewer_keywords:
- GetMessage method
- IDebugMessageEvent2::GetMessage method
ms.assetid: 9fca7285-f7f1-422d-8565-92bf0e0db60a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 26280ca238b5ffc96b0d8b29f1b2d1a424c544d0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102172471"
---
# <a name="idebugmessageevent2getmessage"></a>IDebugMessageEvent2::GetMessage
Ruft die Meldung ab, die angezeigt werden soll.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetMessage( 
   MESSAGETYPE* pMessageType,
   BSTR*        pbstrMessage,
   DWORD*       pdwType,
   BSTR*        pbstrHelpFileName,
   DWORD*       pdwHelpId
);
```

```csharp
int GetMessage( 
   out enum_MESSAGETYPE pMessageType,
   out string           pbstrMessage,
   out uint             pdwType,
   out string           pbstrHelpFileName,
   out uint             dwHelpId
);
```

## <a name="parameters"></a>Parameter
`pMessageType`\
vorgenommen Gibt einen Wert aus der [MessageType](../../../extensibility/debugger/reference/messagetype.md) -Enumeration zurück, der den Typ der Nachricht beschreibt.

`pbstrMessage`\
vorgenommen Gibt die Nachricht zurück.

`pdwType`\
vorgenommen Gibt den Typ der Nachricht zurück, wobei die Konventionen der Win32- `MessageBox` Funktion verwendet werden. Ausführliche Informationen finden Sie in der [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) -Funktion.

`pbstrHelpFileName`\
[in, out] Gibt den Namen der Hilfedatei zurück. Kann ein NULL-Wert (C++) oder ein leerer Wert (c#) sein, wenn keine Hilfedatei vorhanden ist.

`pdwHelpId`\
[in, out] Gibt den Hilfe Bezeichner zurück. Kann 0 sein, wenn dieser Nachricht keine Hilfe zugeordnet ist.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)
- [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)
