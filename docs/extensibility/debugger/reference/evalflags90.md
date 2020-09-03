---
title: EVALFLAGS90 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- EVALFLAGS90 enumeration
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 01951885541ba4acce33f3e4f06f7106116ccc62
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737104"
---
# <a name="evalflags90"></a>EVALFLAGS90
Listet die gültigen Werte für Flags auf, die die Ausdrucks Auswertung steuern. Diese Enumeration erweitert die [evalflags](../../../extensibility/debugger/reference/evalflags.md) -Enumeration.

## <a name="syntax"></a>Syntax

```cpp
enum enum_EVALFLAGS90
{
    // VS 8.0 values
    EVAL90_RETURNVALUE                 = 0x0002,
    EVAL90_NOSIDEEFFECTS               = 0x0004,
    EVAL90_ALLOWBPS                    = 0x0008,
    EVAL90_ALLOWERRORREPORT            = 0x0010,
    EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,
    EVAL90_NOFUNCEVAL                  = 0x0080,
    EVAL90_NOEVENTS                    = 0x1000,
    EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,
    EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,

    // Values added in VS 9.0
    EVAL90_FORCE_EVALUATION_NOW        = 0x8000
};
typedef DWORD EVALFLAGS90;
```

```csharp
public enum enum_EVALFLAGS90
{
    // VS 8.0 values
    EVAL90_RETURNVALUE                 = 0x0002,
    EVAL90_NOSIDEEFFECTS               = 0x0004,
    EVAL90_ALLOWBPS                    = 0x0008,
    EVAL90_ALLOWERRORREPORT            = 0x0010,
    EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,
    EVAL90_NOFUNCEVAL                  = 0x0080,
    EVAL90_NOEVENTS                    = 0x1000,
    EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,
    EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,

    // Values added in VS 9.0
    EVAL90_FORCE_EVALUATION_NOW        = 0x8000
};
```

## <a name="fields"></a>Felder
`EVAL90_RETURNVALUE`\
Gibt an, dass der Rückgabewert (sofern vorhanden) ausgewertet werden soll.

`EVAL90_NOSIDEEFFECTS`\
Gibt an, dass Nebeneffekte nicht zulässig sind.

`EVAL90_ALLOWBPS`\
Gibt an, dass Haltepunkte angehalten werden.

`EVAL90_ALLOWERRORREPORT`\
Gibt an, dass eine Fehlermeldung an den Host zulässig ist. Wird hauptsächlich für die Ausdrucks Auswertung in Skripts in Internet Explorer verwendet.

`EVAL90_FUNCTION_AS_ADDRESS`\
Erzwingt, dass Funktionen als Adressen ausgewertet werden, anstatt die Funktion aufzurufen.

`EVAL90_NOFUNCEVAL`\
Verhindert, dass die Funktion ausgewertet wird. Sehen Sie sich beispielsweise das `int` Token im Ausdruck an `myExpression(int) + 10` . Diese Funktion kann ordnungsgemäß als Adresse ausgewertet werden, aber nicht als Wert.

`EVAL90_NOEVENTS`\
Flag, das anzeigt, dass Ereignisse, die während der Ausdrucks Auswertung auftreten, nicht an den Sitzungs-Debug-Manager (SDM) oder an die IDE gesendet werden sollen.

`EVAL90_DESIGN_TIME_EXPR_EVAL`\
Aktiviert die Ausdrucks Auswertung zur Entwurfszeit.

`EVAL90_ALLOW_IMPLICIT_VARS`\
Ermöglicht das Erstellen impliziter Variablen.

`EVAL90_FORCE_EVALUATION_NOW`\
Erzwingt, dass die Auswertung sofort erfolgt. Dies ist nützlich, wenn Sie eine Anforderung verarbeiten, z. b. eine Benutzer Anforderung.

## <a name="requirements"></a>Anforderungen
Header: Msdbg90. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
