---
description: Stellt die Gründe dar, warum "Bearbeiten und Fortfahren" nicht verfügbar ist.
title: "\"Umcunavailablereason\" | Microsoft-Dokumentation"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e1f80dc1454cb1c15feddd099411bcb339dbc58c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151003"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
`This is for internal use only!` Stellt die Gründe dar, warum " **Bearbeiten und Fortfahren** " nicht verfügbar ist.

## <a name="syntax"></a>Syntax

```cpp
enum tagEncUnavailableReason {
    ENCUN_NONE,
    ENCUN_INTEROP,
    ENCUN_SQLCLR,
    ENCUN_MINIDUMP,
    ENCUN_EMBEDDED,
    ENCUN_ATTACH,
    ENCUN_WIN64
};
typedef enum tagEncUnavailableReason EncUnavailableReason;
```

```csharp
public enum EncUnavailableReason {
    ENCUN_NONE,
    ENCUN_INTEROP,
    ENCUN_SQLCLR,
    ENCUN_MINIDUMP,
    ENCUN_EMBEDDED,
    ENCUN_ATTACH,
    ENCUN_WIN64
};
```

## <a name="fields"></a>Felder
`ENCUN_NONE`\
Kein spezieller Grund, warum "Bearbeiten und Fortfahren" nicht verfügbar ist.

`ENCUN_INTEROP`\
"Bearbeiten und Fortfahren" ist während eines Interop-Aufrufes nicht verfügbar.

`ENCUN_SQLCLR`\
"Bearbeiten und Fortfahren" ist während eines SQL-Prozedur Aufrufers, der die Common Language Runtime (CLR) verwendet, nicht verfügbar.

`ENCUN_MINIDUMP`\
"Bearbeiten und Fortfahren" ist während der Verarbeitung eines Mini Abbilds nicht verfügbar.

`ENCUN_EMBEDDED`\
"Bearbeiten und Fortfahren" ist beim Verarbeiten von eingebettetem Code nicht verfügbar.

`ENCUN_ATTACH`\
"Bearbeiten und Fortfahren" ist nicht verfügbar, da die Sitzung an den Debugger angefügt, nicht von diesem gestartet wurde.

`ENCUN_WIN64`\
"Bearbeiten und Fortfahren" ist während der Verarbeitung von 64-Bit-Windows-Code nicht verfügbar

## <a name="remarks"></a>Bemerkungen
Diese Enumeration ist nur für die interne Verwendung durch vorgesehen [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] . Die Methoden " [getencavailablestate](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) " und " [disableenumc](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) ", die von einem benutzerdefinierten Port Lieferanten implementiert werden, sollten immer zurückgeben `E_NOTIMPL` .

## <a name="requirements"></a>Requirements (Anforderungen)
Header: msdbg. idl

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)

- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)

- [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)
