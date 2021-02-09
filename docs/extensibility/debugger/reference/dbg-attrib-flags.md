---
title: DBG_ATTRIB_FLAGS | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DBG_ATTRIB_FLAGS
helpviewer_keywords:
- DBGPROP_ATTRIB_FLAGS enumerations
ms.assetid: 2f13e601-dadc-476e-a8ec-01c4515082e7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e1093ab5252aa14418bebf4129d0c7d050d0e11d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899161"
---
# <a name="dbg_attrib_flags"></a>DBG_ATTRIB_FLAGS
Beschreibt verschiedene Attribute für eine [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) -oder [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) -Schnittstelle. Member der [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Struktur.

## <a name="syntax"></a>Syntax

```cpp
#define DBG_ATTRIB_NONE                 0x0000000000000000,
#define DBG_ATTRIB_ALL                  0x00000000ffffffff,

// Attributes about the object itself

#define DBG_ATTRIB_OBJ_IS_EXPANDABLE    0x0000000000000001,
#define DBG_ATTRIB_OBJ_HAS_ID           0x0000000000000002,
#define DBG_ATTRIB_OBJ_CAN_HAVE_ID      0x0000000000000004,

// Attributes about the value of the object

#define DBG_ATTRIB_VALUE_READONLY       0x0000000000000010,
#define DBG_ATTRIB_VALUE_ERROR          0x0000000000000020,
#define DBG_ATTRIB_VALUE_SIDE_EFFECT    0x0000000000000040,
#define DBG_ATTRIB_OVERLOADED_CONTAINER 0x0000000000000080,
#define DBG_ATTRIB_VALUE_BOOLEAN        0x0000000000000100,
#define DBG_ATTRIB_VALUE_BOOLEAN_TRUE   0x0000000000000200,
#define DBG_ATTRIB_VALUE_INVALID        0x0000000000000400,
#define DBG_ATTRIB_VALUE_NAT            0x0000000000000800,
#define DBG_ATTRIB_VALUE_AUTOEXPANDED   0x0000000000001000,
#define DBG_ATTRIB_VALUE_TIMEOUT        0x0000000000002000,
#define DBG_ATTRIB_VALUE_RAW_STRING     0x0000000000004000,
#define DBG_ATTRIB_VALUE_CUSTOM_VIEWER  0x0000000000008000,

// Attributes about field access types for the object

#define DBG_ATTRIB_ACCESS_NONE          0x0000000000010000,
#define DBG_ATTRIB_ACCESS_PUBLIC        0x0000000000020000,
#define DBG_ATTRIB_ACCESS_PRIVATE       0x0000000000040000,
#define DBG_ATTRIB_ACCESS_PROTECTED     0x0000000000080000,
#define DBG_ATTRIB_ACCESS_FINAL         0x0000000000100000,
#define DBG_ATTRIB_ACCESS_ALL           0x00000000001f0000,

// Attributes for the storage types of the object

#define DBG_ATTRIB_STORAGE_NONE         0x0000000001000000,
#define DBG_ATTRIB_STORAGE_GLOBAL       0x0000000002000000,
#define DBG_ATTRIB_STORAGE_STATIC       0x0000000004000000,
#define DBG_ATTRIB_STORAGE_REGISTER     0x0000000008000000,
#define DBG_ATTRIB_STORAGE_ALL          0x000000000f000000,

// Attributes for the type modifiers on the object

#define DBG_ATTRIB_TYPE_NONE            0x0000000100000000,
#define DBG_ATTRIB_TYPE_VIRTUAL         0x0000000200000000,
#define DBG_ATTRIB_TYPE_CONSTANT        0x0000000400000000,
#define DBG_ATTRIB_TYPE_SYNCHRONIZED    0x0000000800000000,
#define DBG_ATTRIB_TYPE_VOLATILE        0x0000001000000000,
#define DBG_ATTRIB_TYPE_ALL             0x0000001f00000000,

// Attributes that describe the type of object

#define DBG_ATTRIB_DATA                 0x0000010000000000,
#define DBG_ATTRIB_METHOD               0x0000020000000000,
#define DBG_ATTRIB_PROPERTY             0x0000040000000000,
#define DBG_ATTRIB_CLASS                0x0000080000000000,
#define DBG_ATTRIB_BASECLASS            0x0000100000000000,
#define DBG_ATTRIB_INTERFACE            0x0000200000000000,
#define DBG_ATTRIB_INNERCLASS           0x0000400000000000,
#define DBG_ATTRIB_MOSTDERIVED          0x0000800000000000,
#define DBG_ATTRIB_CHILD_ALL            0x0000ff0000000000,

// Miscellaneous attributes

#define DBG_ATTRIB_MULTI_CUSTOM_VIEWERS 0x0001000000000000

typedef UINT64 DBG_ATTRIB_FLAGS;
```

```csharp
public const int DBG_ATTRIB_NONE                 = 0x0000000000000000,
public const int DBG_ATTRIB_ALL                  = 0x00000000ffffffff,

// Attributes about the object itself

public const int DBG_ATTRIB_OBJ_IS_EXPANDABLE    = 0x0000000000000001,
public const int DBG_ATTRIB_OBJ_HAS_ID           = 0x0000000000000002,
public const int DBG_ATTRIB_OBJ_CAN_HAVE_ID      = 0x0000000000000004,

// Attributes about the value of the object

public const int DBG_ATTRIB_VALUE_READONLY       = 0x0000000000000010,
public const int DBG_ATTRIB_VALUE_ERROR          = 0x0000000000000020,
public const int DBG_ATTRIB_VALUE_SIDE_EFFECT    = 0x0000000000000040,
public const int DBG_ATTRIB_OVERLOADED_CONTAINER = 0x0000000000000080,
public const int DBG_ATTRIB_VALUE_BOOLEAN        = 0x0000000000000100,
public const int DBG_ATTRIB_VALUE_BOOLEAN_TRUE   = 0x0000000000000200,
public const int DBG_ATTRIB_VALUE_INVALID        = 0x0000000000000400,
public const int DBG_ATTRIB_VALUE_NAT            = 0x0000000000000800,
public const int DBG_ATTRIB_VALUE_AUTOEXPANDED   = 0x0000000000001000,
public const int DBG_ATTRIB_VALUE_TIMEOUT        = 0x0000000000002000,
public const int DBG_ATTRIB_VALUE_RAW_STRING     = 0x0000000000004000,
public const int DBG_ATTRIB_VALUE_CUSTOM_VIEWER  = 0x0000000000008000,

// Attributes about field access types for the object

public const int DBG_ATTRIB_ACCESS_NONE          = 0x0000000000010000,
public const int DBG_ATTRIB_ACCESS_PUBLIC        = 0x0000000000020000,
public const int DBG_ATTRIB_ACCESS_PRIVATE       = 0x0000000000040000,
public const int DBG_ATTRIB_ACCESS_PROTECTED     = 0x0000000000080000,
public const int DBG_ATTRIB_ACCESS_FINAL         = 0x0000000000100000,
public const int DBG_ATTRIB_ACCESS_ALL           = 0x00000000001f0000,

// Attributes for the storage types of the object

public const int DBG_ATTRIB_STORAGE_NONE         = 0x0000000001000000,
public const int DBG_ATTRIB_STORAGE_GLOBAL       = 0x0000000002000000,
public const int DBG_ATTRIB_STORAGE_STATIC       = 0x0000000004000000,
public const int DBG_ATTRIB_STORAGE_REGISTER     = 0x0000000008000000,
public const int DBG_ATTRIB_STORAGE_ALL          = 0x000000000f000000,

// Attributes for the type modifiers on the object

public const int DBG_ATTRIB_TYPE_NONE            = 0x0000000100000000,
public const int DBG_ATTRIB_TYPE_VIRTUAL         = 0x0000000200000000,
public const int DBG_ATTRIB_TYPE_CONSTANT        = 0x0000000400000000,
public const int DBG_ATTRIB_TYPE_SYNCHRONIZED    = 0x0000000800000000,
public const int DBG_ATTRIB_TYPE_VOLATILE        = 0x0000001000000000,
public const int DBG_ATTRIB_TYPE_ALL             = 0x0000001f00000000,

// Attributes that describe the type of object

public const int DBG_ATTRIB_DATA                 = 0x0000010000000000,
public const int DBG_ATTRIB_METHOD               = 0x0000020000000000,
public const int DBG_ATTRIB_PROPERTY             = 0x0000040000000000,
public const int DBG_ATTRIB_CLASS                = 0x0000080000000000,
public const int DBG_ATTRIB_BASECLASS            = 0x0000100000000000,
public const int DBG_ATTRIB_INTERFACE            = 0x0000200000000000,
public const int DBG_ATTRIB_INNERCLASS           = 0x0000400000000000,
public const int DBG_ATTRIB_MOSTDERIVED          = 0x0000800000000000,
public const int DBG_ATTRIB_CHILD_ALL            = 0x0000ff0000000000,

// Miscellaneous attributes

public const int DBG_ATTRIB_MULTI_CUSTOM_VIEWERS = 0x0001000000000000
```

## <a name="members"></a>Member
 `DBG_ATTRIB_NONE`\
 Gibt keine Attribute an.

 `DBG_ATTRIB_ALL`\
 Gibt alle Attribute an.

 `DBG_ATTRIB_OBJ_IS_EXPANDABLE`\
 Gibt an, dass der Verweis oder die Eigenschaft über untergeordnete Elemente verfügt.

 `DBG_ATTRIB_OBJ_HAS_ID`\
 Gibt an, dass eine ID für dieses Objekt erstellt wurde.

 `DBG_ATTRIB_OBJ_CAN_HAVE_ID`\
 Gibt an, dass eine ID für dieses Objekt erstellt werden kann.

 `DBG_ATTRIB_VALUE_READONLY`\
 Gibt an, dass der Wert schreibgeschützt ist.

 `DBG_ATTRIB_VALUE_ERROR`\
 Gibt an, dass der Wert ein Fehler ist.

 `DBG_ATTRIB_VALUE_SIDE_EFFECT`\
 Gibt an, dass die Auswertung einen Nebeneffekt hat.

 `DBG_ATTRIB_OVERLOADED_CONTAINER`\
 Gibt an, dass diese Eigenschaft tatsächlich ein Container von über Ladungen ist.

 `DBG_ATTRIB_VALUE_BOOLEAN`\
 Gibt an, dass der Wert in `DEBUG_PROPERTY_INFO::bstrValue` Boolesch ist.

 `DBG_ATTRIB_VALUE_BOOLEAN_TRUE`\
 Gibt an, dass der Wert in `DEBUG_PROPERTY_INFO::bstrValue` Boolean und ist `TRUE` .

 `DBG_ATTRIB_VALUE_INVALID`\
 Gibt an, dass der Wert im `DEBUG_PROPERTY_INFO::bstrValue` ungültig ist.

 `DBG_ATTRIB_VALUE_NAT`\
 Gibt an, dass der Wert in `DEBUG_PROPERTY_INFO::bstrValue` "*not a Thing*" (NAT) ist. NAT beschreibt ein registerflag in Intel 64-Bit-Prozessoren, das verzögerte spekulative Ausnahmen angibt.

 `DBG_ATTRIB_VALUE_AUTOEXPANDED`\
 Gibt an, dass der Wert in `DEBUG_PROPERTY_INFO::bstrValue` möglicherweise automatisch erweitert wurde.

 `DBG_ATTRIB_VALUE_TIMEOUT`\
 Gibt an, dass für eine Auswertung ein Timeout aufgetreten ist.

 `DBG_ATTRIB_VALUE_RAW_STRING`\
 Gibt an, dass der Wert in durch eine unformatierte `DEBUG_PROPERTY_INFO::bstrValue` Zeichenfolge dargestellt werden kann.

 `DBG_ATTRIB_VALUE_CUSTOM_VIEWER`\
 Gibt an, dass dieser Eigenschaft mindestens ein benutzerdefinierter Viewer zugeordnet ist.

 `DBG_ATTRIB_ACCESS_NONE`\
 Gibt ein Objekt an, das weder `public` , `private` noch den `protected` Typzugriff hat.

 `DBG_ATTRIB_ACCESS_PUBLIC`\
 Gibt ein Objekt mit öffentlichem Zugriff an.

 `DBG_ATTRIB_ACCESS_PRIVATE`\
 Gibt ein Objekt mit privatem Zugriff an.

 `DBG_ATTRIB_ACCESS_PROTECTED`\
 Gibt ein Objekt mit geschütztem Zugriff an.

 `DBG_ATTRIB_ACCESS_FINAL`\
 Gibt ein Objekt mit endgültigem Zugriff an.

 `DBG_ATTRIB_ACCESS_ALL`\
 Maske zum Extrahieren der Zugriffs Attribute aus `DBG_ATTRIB_FLAGS` .

 `DBG_ATTRIB_STORAGE_NONE`\
 Gibt an, dass kein Speichertyp angegeben wurde.

 `DBG_ATTRIB_STORAGE_GLOBAL`\
 Zeigt einen globalen Speicher an.

 `DBG_ATTRIB_STORAGE_STATIC`\
 Zeigt einen statischen Speicher an.

 `DBG_ATTRIB_STORAGE_REGISTER`\
 Gibt den Speicher im Register an.

 `DBG_ATTRIB_STORAGE_ALL`\
 Maske zum Extrahieren der Speicher Attribute `DBG_ATTRIB_FLAGS` .

 `DBG_ATTRIB_TYPE_NONE`\
 Gibt an, dass kein Typmodifizierer vorhanden ist.

 `DBG_ATTRIB_TYPE_VIRTUAL`\
 Gibt an, dass der Objekttyp virtuell ist.

 `DBG_ATTRIB_TYPE_CONSTANT`\
 Gibt an, dass der Objekttyp konstant ist.

 `DBG_ATTRIB_TYPE_SYNCHRONIZED`\
 Gibt an, dass der Objekttyp synchronisiert ist.

 `DBG_ATTRIB_TYPE_VOLATILE`\
 Gibt an, dass der Objekttyp flüchtig ist.

 `DBG_ATTRIB_TYPE_ALL`\
 Maske zum Extrahieren der Typattribute aus `DBG_ATTRIB_FLAGS` .

 `DBG_ATTRIB_DATA`\
 Gibt an, dass dieses Objekt ein Datenfeld ist.

 `DBG_ATTRIB_METHOD`\
 Gibt an, dass dieses Objekt eine Methode ist.

 `DBG_ATTRIB_PROPERTY`\
 Gibt an, dass dieses Objekt eine Eigenschaft ist.

 `DBG_ATTRIB_CLASS`\
 Gibt an, dass dieses Objekt eine Klasse ist.

 `DBG_ATTRIB_BASECLASS`\
 Gibt an, dass dieses Objekt eine Basisklasse ist.

 `DBG_ATTRIB_INTERFACE`\
 Gibt an, dass dieses Objekt eine Schnittstelle ist.

 `DBG_ATTRIB_INNERCLASS`\
 Gibt an, dass dieses Objekt eine innere Klasse ist.

 `DBG_ATTRIB_MOSTDERIVED`\
 Gibt an, dass dieses Objekt '*Most-abgeleitet*' ist. Der Begriff "*Most-abgeleitet*" bezeichnet den tatsächlichen Objekttyp und nicht den Typ des Verweises.

 `DBG_ATTRIB_CHILD_ALL`\
 Gibt eine Maske von `DBG_ATTRIB_DATA` bis an `DBG_ATTRIB_MOSTDERIVED` .

 `DBG_ATTRIB_MULTI_CUSTOM_VIEWERS`\
 Gibt an, dass dem Objekt mehrere benutzerdefinierte Viewer zugeordnet sind.

## <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Die Werte in dieser Enumeration sind nicht in der Assembly für c# definiert. Stattdessen müssen Sie die Definitionen in die Quelldatei kopieren.

 Diese Flags werden auch verwendet, um untergeordnete Elemente eines Objekts zu filtern, z. b., wenn Sie als Argument an [enumchildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)übermittelt werden. Die Werte können mit einem bitweisen kombiniert werden `OR` .

 Das- `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` Flag ist ein Hinweis auf, [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] um die [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) -Schnittstelle von der [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) -Schnittstelle abzurufen und [getcustomviewerlist](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) für eine Liste benutzerdefinierter Viewer aufzurufen.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
