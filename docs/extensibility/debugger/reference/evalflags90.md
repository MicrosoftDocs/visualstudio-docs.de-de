---
description: Listet die gültigen Werte für Flags auf, die die Ausdrucks Auswertung steuern.
title: EVALFLAGS90 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- EVALFLAGS90 enumeration
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2080eba4b8319045dcd4d3603d1e6441fafed97d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150925"
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

## <a name="requirements"></a>Requirements (Anforderungen)
Header: Msdbg90. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
