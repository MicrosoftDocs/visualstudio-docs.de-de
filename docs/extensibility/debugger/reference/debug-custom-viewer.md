---
title: DEBUG_CUSTOM_VIEWER | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_CUSTOM_VIEWER
helpviewer_keywords:
- DEBUG_CUSTOM_VIEWER structure
ms.assetid: 8e0ef3f0-0107-48e8-a037-6e52b4c4ed9d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6fa8e8d9e07510a10b1b32534f3323dab4c84a22
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899112"
---
# <a name="debug_custom_viewer"></a>DEBUG_CUSTOM_VIEWER
Eine-Struktur, die einen benutzerdefinierten Viewer oder eine typschnell Ansicht identifiziert.

## <a name="syntax"></a>Syntax

```cpp
typedef struct tagDEBUG_CUSTOM_VIEWER {
    DWORD dwID;
    BSTR  bstrMenuName;
    BSTR  bstrDescription;
    GUID  guidLang;
    GUID  guidVendor;
    BSTR  bstrMetric;
} DEBUG_CUSTOM_VIEWER;
```

```csharp
public struct DEBUG_CUSTOM_VIEWER {
    public uint   dwID;
    public string bstrMenuName;
    public string bstrDescription;
    public Guid   guidLang;
    public Guid   guidVendor;
    public string bstrMetric;
};
```

## <a name="members"></a>Member
`dwID`\
Eine ID zur Unterscheidung mehrerer Viewer oder schnell Ansichten, die von einem solchen implementiert werden `GUID` .

`bstrMenuName`\
Der Text, der im Dropdown Menü angezeigt wird.

`bstrDescription`\
Eine Beschreibung des benutzerdefinierten Viewers oder der typschnell Ansicht (muss ein NULL-Wert sein, wenn er nicht verwendet wird).

`guidLang`\
Sprache der Ausdrucks Auswertung für die Bereitstellung.

`guidVendor`\
Hersteller der Bereitstellung der Ausdrucks Auswertung.

`bstrMetric`\
Die Metrik, unter der der benutzerdefinierte Viewer oder die typschnell Ansicht `CLSID` gespeichert wird.

## <a name="remarks"></a>Bemerkungen
Eine Liste dieser Struktur wird durch einen Aufrufen der [getcustomviewerlist](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) -Methode zurückgegeben (und durch Erweiterung die [getcustomviewerlist](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) -Methode).

## <a name="requirements"></a>Anforderungen
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)
