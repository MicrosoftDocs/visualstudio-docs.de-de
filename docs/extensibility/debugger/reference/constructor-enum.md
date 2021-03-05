---
description: Wählt verschiedene Typen von Konstruktoren aus.
title: CONSTRUCTOR_ENUM | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONSTRUCTOR_ENUM
helpviewer_keywords:
- CONSTRUCTOR_ENUM enumeration
ms.assetid: 6d335b2c-66bc-460c-a4a6-4f3f1b697c2c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4e3a8eaae37b304c438c18ec2a683c19da00ab16
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170795"
---
# <a name="constructor_enum"></a>CONSTRUCTOR_ENUM
Wählt verschiedene Typen von Konstruktoren aus.

## <a name="syntax"></a>Syntax

```cpp
typedef enum ConstructorMatchOptions {
    crAll       = 0,
    crNonStatic = 1,
    crStatic    = 2
} CONSTRUCTOR_ENUM;
```

```csharp
public enum ConstructorMatchOptions {
    crAll       = 0,
    crNonStatic = 1,
    crStatic    = 2
};
```

## <a name="fields"></a>Felder
`crAll`\
Wählt alle Konstruktoren aus.

`crNonStatic`\
Wählt nicht statische Konstruktoren aus.

`crStatic`\
Wählt statische Konstruktoren aus.

## <a name="remarks"></a>Bemerkungen
Übergeben als Argument an die [enumconstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md) -Methode.

## <a name="requirements"></a>Requirements (Anforderungen)
Header: sh. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
