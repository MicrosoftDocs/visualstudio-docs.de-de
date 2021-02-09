---
title: DEBUG_ADDRESS_UNION | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS_UNION
helpviewer_keywords:
- DEBUG_ADDRESS_UNION union
ms.assetid: e3d11aab-de0d-4109-b5dc-11e07e64382d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 76fc15389242de1011851492e3a68dc001534582
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899136"
---
# <a name="debug_address_union"></a>DEBUG_ADDRESS_UNION
Beschreibt verschiedene Arten von Adressen.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagDEBUG_ADDRESS_UNION {
   ADDRESS_KIND dwKind;
   union {
      NATIVE_ADDRESS                  addrNative;
      UNMANAGED_ADDRESS_THIS_RELATIVE addrThisRel;
      UNMANAGED_ADDRESS_PHYSICAL      addrUPhysical;
      METADATA_ADDRESS_METHOD         addrMethod;
      METADATA_ADDRESS_FIELD          addrField;
      METADATA_ADDRESS_LOCAL          addrLocal;
      METADATA_ADDRESS_PARAM          addrParam;
      METADATA_ADDRESS_ARRAYELEM      addrArrayElem;
      METADATA_ADDRESS_RETVAL         addrRetVal;
      DWORD                           unused;
   } addr;
} DEBUG_ADDRESS_UNION;
```

```csharp
public struct DEBUG_ADDRESS_UNION {
   public ADDRESS_KIND dwKind;
   public IntPtr       unionmember;
}
```

## <a name="members"></a>Member
`dwKind`\
Ein Wert aus der [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) Enumeration, der angibt, wie die Union interpretiert werden soll.

`addr.addrNative`\
[Nur C++] Enthält die [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) Struktur, wenn `dwKind` = ADDRESS_KIND_NATIVE.

`addr.addrThisRel`\
[Nur C++] Enthält die[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) Struktur, wenn `dwKind` = ADDRESS_KIND_UNMANAGED_THIS_RELATIVE.

`addr.addUPhysical`\
[Nur C++] Enthält die[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) Struktur, wenn `dwKind` = ADDRESS_KIND_UNMANAGED_PHYSICAL.

`addr.addrMethod`\
[Nur C++] Enthält die[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) Struktur, wenn `dwKind` = ADDRESS_KIND_METHOD.

`addr.addrField`\
[Nur C++] Enthält die[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) Struktur, wenn `dwKind` = ADDRESS_KIND_FIELD.

`addr.addrLocal`\
[Nur C++] Enthält die[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) Struktur, wenn `dwKind` = ADDRESS_KIND_LOCAL.

`addr.addrParam`\
[Nur C++] Enthält die[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) Struktur, wenn `dwKind` = ADDRESS_KIND_PARAM.

`addr.addrArrayElem`\
[Nur C++] Enthält die[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) Struktur, wenn `dwKind` = ADDRESS_KIND_ARRAYELEM.

`addr.addrRetVal`\
[Nur C++] Enthält die[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) Struktur, wenn `dwKind` = ADDRESS_KIND_RETVAL.

`addr.unused`\
[Nur C++] Auffüll Zeichen.

`addr`\
[Nur C++] Der Name der Union.

`unionmember`\
[Nur c#] Dieser Wert muss basierend auf dem entsprechenden Strukturtyp gemarshallt werden `dwKind` . Siehe Hinweise für die Zuordnung zwischen `dwKind` und der Interpretation der Union.

## <a name="remarks"></a>Bemerkungen
Diese Struktur ist Teil der [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) -Struktur und stellt eine Zahl verschiedener Arten von Adressen dar (die- `DEBUG_ADDRESS` Struktur wird durch einen Aufrufen der [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) -Methode ausgefüllt).

 [Nur c#] In der folgenden Tabelle wird gezeigt, wie der `unionmember` Member für jede Art von Adresse interpretiert wird. Das Beispiel zeigt, wie dies für eine Art von Adresse erfolgt.

|`dwKind`|`unionmember` interpretiert als|
|--------------|----------------------------------|
|`ADDRESS_KIND_NATIVE`|[NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)|
|`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`|[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)|
|`ADDRESS_KIND_UNMANAGED_PHYSICAL`|[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)|
|`ADDRESS_KIND_METHOD`|[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)|
|`ADDRESS_KIND_FIELD`|[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)|
|`ADDRESS_KIND_LOCAL`|[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)|
|`ADDRESS_KIND_PARAM`|[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)|
|`ADDRESS_KIND_ARRAYELEM`|[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)|
|`ADDRESS_KIND_RETVAL`|[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)|

## <a name="example"></a>Beispiel
Dieses Beispiel zeigt, wie eine Art von Adresse ( `METADATA_ADDRESS_ARRAYELEM` ) der `DEBUG_ADDRESS_UNION` Struktur in c# interpretiert wird. Die übrigen Elemente können auf genau die gleiche Weise interpretiert werden.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(DEBUG_ADDRESS_UNION dau)
        {
            if (dau.dwKind == (uint)enum_ADDRESS_KIND.ADDRESS_KIND_METADATA_ARRAYELEM)
            {
                 METADATA_ADDRESS_ARRAYELEM arrayElem =
                     (METADATA_ADDRESS_ARRAYELEM)Marshal.PtrToStructure(dau.unionmember,
                                 typeof(METADATA_ADDRESS_ARRAYELEM));
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
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
