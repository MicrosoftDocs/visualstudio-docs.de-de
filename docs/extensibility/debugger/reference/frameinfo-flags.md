---
title: FRAMEINFO_FLAGS | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO_FLAGS
helpviewer_keywords:
- FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9dcdb555e4355d6f22c8218f98899c01b3b3e2e0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904785"
---
# <a name="frameinfo_flags"></a>FRAMEINFO_FLAGS
Gibt die Informationen an, die über ein Stapel Rahmen Objekt abgerufen werden sollen.

## <a name="syntax"></a>Syntax

```cpp
enum enum_FRAMEINFO_FLAGS {
    FIF_FUNCNAME              = 0x00000001,
    FIF_RETURNTYPE            = 0x00000002,
    FIF_ARGS                  = 0x00000004,
    FIF_LANGUAGE              = 0x00000008,
    FIF_MODULE                = 0x00000010,
    FIF_STACKRANGE            = 0x00000020,
    FIF_FRAME                 = 0x00000040,
    FIF_DEBUGINFO             = 0x00000080,
    FIF_STALECODE             = 0x00000100,
    FIF_ANNOTATEDFRAME        = 0x00000200,
    FIF_DEBUG_MODULEP         = 0x00000400,
    FIF_FUNCNAME_FORMAT       = 0x00001000,
    FIF_FUNCNAME_RETURNTYPE   = 0x00002000,
    FIF_FUNCNAME_ARGS         = 0x00004000,
    FIF_FUNCNAME_LANGUAGE     = 0x00008000,
    FIF_FUNCNAME_MODULE       = 0x00010000,
    FIF_FUNCNAME_LINES        = 0x00020000,
    FIF_FUNCNAME_OFFSET       = 0x00040000,
    FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,
    FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,
    FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,
    FIF_FUNCNAME_ARGS_ALL     = 0x00700000,
    FIF_ARGS_TYPES            = 0x01000000,
    FIF_ARGS_NAMES            = 0x02000000,
    FIF_ARGS_VALUES           = 0x04000000,
    FIF_ARGS_ALL              = 0x07000000,
    FIF_ARGS_NOFORMAT         = 0x08000000,
    FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,
    FIF_FILTER_NON_USER_CODE  = 0x20000000,
    FIF_ARGS_NO_TOSTRING      = 0x40000000,
    FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000
};
typedef DWORD FRAMEINFO_FLAGS;
```

```csharp
public enum enum_FRAMEINFO_FLAGS {
    FIF_FUNCNAME              = 0x00000001,
    FIF_RETURNTYPE            = 0x00000002,
    FIF_ARGS                  = 0x00000004,
    FIF_LANGUAGE              = 0x00000008,
    FIF_MODULE                = 0x00000010,
    FIF_STACKRANGE            = 0x00000020,
    FIF_FRAME                 = 0x00000040,
    FIF_DEBUGINFO             = 0x00000080,
    FIF_STALECODE             = 0x00000100,
    FIF_ANNOTATEDFRAME        = 0x00000200,
    FIF_DEBUG_MODULEP         = 0x00000400,
    FIF_FUNCNAME_FORMAT       = 0x00001000,
    FIF_FUNCNAME_RETURNTYPE   = 0x00002000,
    FIF_FUNCNAME_ARGS         = 0x00004000,
    FIF_FUNCNAME_LANGUAGE     = 0x00008000,
    FIF_FUNCNAME_MODULE       = 0x00010000,
    FIF_FUNCNAME_LINES        = 0x00020000,
    FIF_FUNCNAME_OFFSET       = 0x00040000,
    FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,
    FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,
    FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,
    FIF_FUNCNAME_ARGS_ALL     = 0x00700000,
    FIF_ARGS_TYPES            = 0x01000000,
    FIF_ARGS_NAMES            = 0x02000000,
    FIF_ARGS_VALUES           = 0x04000000,
    FIF_ARGS_ALL              = 0x07000000,
    FIF_ARGS_NOFORMAT         = 0x08000000,
    FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,
    FIF_FILTER_NON_USER_CODE  = 0x20000000,
    FIF_ARGS_NO_TOSTRING      = 0x40000000,
    FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000
};
```

## <a name="fields"></a>Felder
`FIF_FUNCNAME`\
Initialisieren Sie das Feld, und verwenden Sie es `m_bstrFuncName` .

`FIF_RETURNTYPE`\
Initialisieren Sie das Feld, und verwenden Sie es `m_bstrReturnType` .

`FIF_ARGS`\
Initialisieren Sie das Feld, und verwenden Sie es `m_bstrArgs` .

`FIF_LANGUAGE`\
Initialisieren Sie das Feld, und verwenden Sie es `m_bstrLanguage` .

`FIF_MODULE`\
Initialisieren Sie das Feld, und verwenden Sie es `m_bstrModule` .

`FIF_STACKRANGE`\
Initialisieren/verwenden Sie `m_addrMin` die `m_addrMax` Felder und (Stapelbereich).

`FIF_FRAME`\
Initialisieren Sie das Feld, und verwenden Sie es `m_pFrame` .

`FIF_DEBUGINFO`\
Initialisieren Sie das Feld, und verwenden Sie es `m_fHasDebugInfo` .

`FIF_STALECODE`\
Initialisieren Sie das Feld, und verwenden Sie es `m_fStaleCode` .

`FIF_ANNOTATEDFRAME`\
Initialisieren Sie das Feld, und verwenden Sie es `m_fAnnotatedFrame` .

`FIF_DEBUG_MODULEP`\
Initialisieren Sie das Feld, und verwenden Sie es `m_pModule` .

`FIF_FUNCNAME_FORMAT`\
Formatiert den Funktionsnamen. Das Ergebnis wird im Feld zurückgegeben `m_bstrFunName` , und es werden keine anderen Felder ausgefüllt.

`FIF_FUNCNAME_RETURNTYPE`\
Fügt dem Feld den Rückgabetyp hinzu `m_bstrFuncName` .

`FIF_FUNCNAME_ARGS`\
Fügt dem Feld die Argumente hinzu `m_bstrFuncName` .

`FIF_FUNCNAME_LANGUAGE`\
Fügt dem Feld die Sprache hinzu `m_bstrFuncName` .

`FIF_FUNCNAME_MODULE`\
Fügt dem Feld den Modulnamen hinzu `m_bstrFuncName` .

`FIF_FUNCNAME_LINES`\
Fügt dem Feld die Anzahl von Zeilen hinzu `m_bstrFuncName` .

`FIF_FUNCNAME_OFFSET`\
Fügt dem- `m_bstrFuncName` Feld den Offset in Bytes vom Anfang der Zeile hinzu, wenn `FIF_FUNCNAME_LINES` angegeben wird. Wenn `FIF_FUNCNAME_LINES` nicht angegeben wird oder wenn Zeilennummern nicht verfügbar sind, wird der Offset in Bytes vom Anfang der Funktion hinzugefügt.

`FIF_FUNCNAME_ARGS_TYPES`\
Fügt dem Feld den Typ der einzelnen Funktionsargumente hinzu `m_bstrFuncName` .

`FIF_FUNCNAME_ARGS_NAMES`\
Fügt dem Feld den Namen der einzelnen Funktionsargumente hinzu `m_bstrFuncName` .

`FIF_FUNCNAME_ARGS_VALUES`\
Fügt dem Feld den Wert der einzelnen Funktionsargumente hinzu `m_bstrFuncName` .

`FIF_FUNCNAME_ARGS_ALL`\
Fügt dem Feld den Typ, den Namen und den Wert aller Argumente hinzu `m_bstrFuncName` .

`FIF_ARGS_TYPES`\
Die Argument Typen werden abgerufen und formatiert.

`FIF_ARGS_NAMES`\
Die Argument Namen werden abgerufen und formatiert.

`FIF_ARGS_VALUES`\
Die Argument Werte werden abgerufen und formatiert.

`FIF_ARGS_ALL`\
Rufen Sie den Typ, den Namen und den Wert aller Argumente ab, und formatieren Sie ihn.

`FIF_ARGS_NOFORMAT`\
Gibt an, dass die Argumente nicht formatiert werden (z. b. Fügen Sie keine öffnenden und schließenden Klammern um die Argumentliste hinzu, und fügen Sie kein Trennzeichen zwischen Argumenten hinzu).

`FIF_ARGS_NO_FUNC_EVAL`\
Gibt an, dass die Funktions Auswertung (Eigenschaft) beim Abrufen von Argument Werten nicht verwendet werden soll.

`FIF_FILTER_NON_USER_CODE`\
Die Debug-Engine dient zum Filtern von Nichtbenutzer Code Frames, damit Sie nicht eingeschlossen werden.

`FIF_ARGS_NO_TOSTRING`\
`ToString()`Beim Zurückgeben von Funktions Argumenten dürfen keine Funktions Auswertung oder-Formatierung zulässig sein.

`FIF_DESIGN_TIME_EXPR_EVAL`\
Frame Informationen sollten von der gehosteten App-Domäne und nicht vom Hostingprozess abgerufen werden.

## <a name="remarks"></a>Bemerkungen
Diese Flags werden an die [enumframeinfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) -Methode und die [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) -Methode übermittelt, um anzugeben, welche Felder in der [frameInfo](../../../extensibility/debugger/reference/frameinfo.md) -Struktur oder-Strukturen initialisiert werden sollen.

Diese Flags werden auch verwendet, um anzugeben, welche Felder der [frameInfo](../../../extensibility/debugger/reference/frameinfo.md) -Struktur verwendet und gültig sind, wenn die Struktur zurückgegeben wird. Diese Werte können mit einem bitweisen kombiniert werden `OR` .

## <a name="requirements"></a>Anforderungen
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
