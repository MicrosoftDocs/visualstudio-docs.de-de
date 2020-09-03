---
title: TYPE_INFO | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TYPE_INFO
helpviewer_keywords:
- TYPE_INFO structure
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 82796c1d82dc3ca77151abcec3e1dd6ce13ac59d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713320"
---
# <a name="type_info"></a>TYPE_INFO
Diese Struktur gibt verschiedene Arten von Informationen über den Typ eines Felds an.

## <a name="syntax"></a>Syntax

```cpp
struct _tagTYPE_INFO_UNION {
   dwTYPE_KIND dwKind;
   union {
      METADATA_TYPE typeMeta;
      PDB_TYPE      typePdb;
      BUILT_TYPE    typeBuilt;
      DWORD         unused;
   } type;
} TYPE_INFO;
```

```csharp
public struct TYPE_INFO {
   public uint   dwKind;
   public IntPtr unionmember;
};
```

## <a name="members"></a>Member
 `dwKind`\
 Ein Wert aus der [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) Enumeration, die bestimmt, wie die Union interpretiert werden soll.

 `type.typeMeta`\
 [Nur C++] Enthält eine [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) Struktur, wenn `dwKind` ist `TYPE_KIND_METADATA` .

 `type.typePdb`\
 [Nur C++] Enthält eine [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) Struktur, wenn `dwKind` ist `TYPE_KIND_PDB` .

 `type.typeBuilt`\
 [Nur C++] Enthält eine [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) Struktur, wenn `dwKind` ist `TYPE_KIND_BUILT` .

 `type.unused`\
 Nicht verwendete Auffüll Zeichen.

 `type`\
 Der Name der Union.

 `unionmember`\
 [Nur c#] Mars Hallen dieses in den entsprechenden Strukturtyp, der auf basiert `dwKind` .

## <a name="remarks"></a>Bemerkungen
 Diese Struktur wird an die [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) -Methode übermittelt, wo Sie ausgefüllt ist. Die Art und Weise, wie der Inhalt der-Struktur interpretiert wird, basiert auf dem- `dwKind` Feld.

> [!NOTE]
> [Nur C++] Wenn `dwKind` `TYPE_KIND_BUILT` ist, muss beim zerstören der Struktur das zugrunde liegende [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Objekt freigegeben werden `TYPE_INFO` . Hierzu wird `typeInfo.type.typeBuilt.pUnderlyingField->Release()` aufgerufen.

 [Nur c#] In der folgenden Tabelle wird gezeigt, wie der `unionmember` Member für jede Art von Typ interpretiert wird. Das Beispiel zeigt, wie dies für eine Art von Typ erfolgt.

|`dwKind`|`unionmember` interpretiert als|
|--------------|----------------------------------|
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|

## <a name="example"></a>Beispiel
 In diesem Beispiel wird gezeigt, wie der- `unionmember` Member der- `TYPE_INFO` Struktur in c# interpretiert wird. In diesem Beispiel wird nur ein Typ ( `TYPE_KIND_METADATA` ) interpretiert, die anderen werden jedoch auf die gleiche Weise interpretiert.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(TYPE_INFO ti)
        {
            if (ti.dwKind == (uint)enum_dwTypeKind.TYPE_KIND_METADATA)
            {
                 METADATA_TYPE dataType = (METADATA_TYPE)Marshal.PtrToStructure(ti.unionmember,
                                               typeof(METADATA_TYPE));
            }
        }
    }
}
```

## <a name="requirements"></a>Anforderungen
 Header: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
