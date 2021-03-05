---
description: Gibt die Art der abzurufenden Symbol Informationen an.
title: SYMBOL_SEARCH_INFO_FIELDS | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SYMBOL_SEARCH_INFO_FIELDS
helpviewer_keywords:
- SYMBOL_SEARCH_INFO_FIELDS enumeration
ms.assetid: bce35af0-722d-46d4-afa6-eaae598c51ff
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6bce694110c76fb831dea14026e1810c7c318edd
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221872"
---
# <a name="symbol_search_info_fields"></a>SYMBOL_SEARCH_INFO_FIELDS
Gibt die Art der abzurufenden Symbol Informationen an.

## <a name="syntax"></a>Syntax

```cpp
enum enum_SYMBOL_SEARCH_INFO_FIELDS
{
   SSIF_NONE                = 0x00000000,
   SSIF_VERBOSE_SEARCH_INFO = 0x00000001
};
typedef DWORD SYMBOL_SEARCH_INFO_FIELDS;
```

```csharp
public enum enum_SYMBOL_SEARCH_INFO_FIELDS
{
   SSIF_NONE                = 0x00000000,
   SSIF_VERBOSE_SEARCH_INFO = 0x00000001
};

```

## <a name="fields"></a>Felder
 `SSIF_NONE`\
 Gibt keine Flags an

 `SSIF_VERBOSE_SEARCH_INFO`\
 Gibt alle Suchpfade für die Suche nach Symbolen zurück.

## <a name="remarks"></a>Bemerkungen
 Diese Flags werden als Parameter an die [getsymbolinfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) -Methode übergeben, um die Menge der zurückgegebenen Informationen zu bestimmen.

> [!NOTE]
> Derzeit wird nur `SSIF_VERBOSE_SEARCH_INFO` unterstützt, und es muss als `dwFlags` Parameter für angegeben werden `IDebugModule3::GetSymbolInfo` . Alle anderen Werte geben einen Fehler zurück.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)
