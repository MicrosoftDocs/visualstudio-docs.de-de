---
description: Listet die gültigen Werte auf, die die Arten von Informationen darstellen, die von einem idebugfield-Objekt übernommen und dem Benutzer angezeigt werden.
title: Display Kind | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- DisplayKind enumeration
ms.assetid: 940968c5-6065-4bda-8ee6-c31597db4d71
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5632c6844a38f1891070311fe3c7c65a0220def5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151023"
---
# <a name="displaykind"></a>DisplayKind
Listet die gültigen Werte auf, die die Arten von Informationen darstellen, die von einem [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Objekt übernommen und dem Benutzer angezeigt werden.

## <a name="syntax"></a>Syntax

```cpp
enum enum_DisplayKind
{
    DisplayKind_Value = 0x1,
    DisplayKind_Name = 0x2,
    DisplayKind_Type = 0x3,
};
typedef DWORD DisplayKind;
```

```csharp
public enum enum_DisplayKind
{
    DisplayKind_Value = 0x1,
    DisplayKind_Name = 0x2,
    DisplayKind_Type = 0x3,
};
```

## <a name="fields"></a>Felder
`DisplayKind_Value`\
Der Wert des Felds.

`DisplayKind_Name`\
Der Name des Felds.

`DisplayKind_Type`\
Der Feldtyp.

## <a name="requirements"></a>Requirements (Anforderungen)
Header: EE. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)
