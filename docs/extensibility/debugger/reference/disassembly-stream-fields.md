---
title: DISASSEMBLY_STREAM_FIELDS | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_FIELDS
helpviewer_keywords:
- DISASSEMBLY_STREAM_FIELDS enumeration
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 34836447af8277141c401302c5a838d5cbe351b9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938953"
---
# <a name="disassembly_stream_fields"></a>DISASSEMBLY_STREAM_FIELDS
Gibt an, welche Informationen über ein disassemblyfeld abgerufen werden sollen.

## <a name="syntax"></a>Syntax

```cpp
enum enum_DISASSEMBLY_STREAM_FIELDS {
    DSF_ADDRESS          = 0x00000001,
    DSF_ADDRESSOFFSET    = 0x00000002,
    DSF_CODEBYTES        = 0x00000004,
    DSF_OPCODE           = 0x00000008,
    DSF_OPERANDS         = 0x00000010,
    DSF_SYMBOL           = 0x00000020,
    DSF_CODELOCATIONID   = 0x00000040,
    DSF_POSITION         = 0x00000080,
    DSF_DOCUMENTURL      = 0x00000100,
    DSF_BYTEOFFSET       = 0x00000200,
    DSF_FLAGS            = 0x00000400,
    DSF_OPERANDS_SYMBOLS = 0x00010000,
    DSF_ALL              = 0x000107ff
};
typedef DWORD DISASSEMBLY_STREAM_FIELDS;
```

```csharp
public enum enum_DISASSEMBLY_STREAM_FIELDS {
    DSF_ADDRESS          = 0x00000001,
    DSF_ADDRESSOFFSET    = 0x00000002,
    DSF_CODEBYTES        = 0x00000004,
    DSF_OPCODE           = 0x00000008,
    DSF_OPERANDS         = 0x00000010,
    DSF_SYMBOL           = 0x00000020,
    DSF_CODELOCATIONID   = 0x00000040,
    DSF_POSITION         = 0x00000080,
    DSF_DOCUMENTURL      = 0x00000100,
    DSF_BYTEOFFSET       = 0x00000200,
    DSF_FLAGS            = 0x00000400,
    DSF_OPERANDS_SYMBOLS = 0x00010000,
    DSF_ALL              = 0x000107ff
};
```

## <a name="fields"></a>Felder
`DSF_ADDRESS`\
Initialisieren Sie das Feld, und verwenden Sie es `bstrAddress` .

`DSF_ADDRESSOFFSET`\
Initialisieren Sie das Feld, und verwenden Sie es `bstrAddressOffset` .

`DSF_CODEBYTES`\
Initialisieren Sie das Feld, und verwenden Sie es `bstrCodeBytes` .

`DSF_OPCODE`\
Initialisieren Sie das Feld, und verwenden Sie es `bstrOpCode` .

`DSF_OPERANDS`\
Initialisieren Sie das Feld, und verwenden Sie es `bstrOperands` .

`DSF_SYMBOL`\
Initialisieren Sie das Feld, und verwenden Sie es `bstrSymbol` .

`DSF_CODELOCATIONID`\
Initialisieren Sie das Feld, und verwenden Sie es `uCodeLocationId` .

`DSF_POSITION`\
Initialisieren/verwenden Sie `posBeg` die `posEnd` Felder und.

`DSF_DOCUMENTURL`\
Initialisieren Sie das Feld, und verwenden Sie es `bstrDocumentUrl` .

`DSF_BYTEOFFSET`\
Initialisieren Sie das Feld, und verwenden Sie es `dwByteOffset` .

`DSF_FLAGS`\
Initialisieren/verwenden Sie das `dwFlags` Feld ([DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)).

`DSF_OPERANDS_SYMBOLS`\
Schließt Symbolnamen in das `bstrOperands` Feld ein.

`DSF_ALL`\
Gibt alle Felder für den disassemblydatenstrom an.

## <a name="remarks"></a>Bemerkungen
Wird als Parameter an die [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) -Methode übergeben, um anzugeben, welche Felder der [disassemblydata](../../../extensibility/debugger/reference/disassemblydata.md) -Struktur initialisiert werden sollen.

Wird für den- `dwFields` Member der `DisassemblyData` -Struktur verwendet, um anzugeben, welche Felder verwendet und gültig sind, wenn die-Struktur zurückgegeben wird.

Diese Werte können mit einem bitweisen kombiniert werden `OR` .

## <a name="requirements"></a>Anforderungen
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [Lesen](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
