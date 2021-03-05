---
description: Beschreibt die Attribute eines Dokuments.
title: TEXT_DOC_ATTR_2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TEXT_DOC_ATTR_2
helpviewer_keywords:
- TEXT_DOC_ATTR_2 enumeration
ms.assetid: 2333b33b-042b-4ac6-9ebe-e66f95f52f51
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c8351753c5e8da9a320bd93c17e8138dedaff03d
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221859"
---
# <a name="text_doc_attr_2"></a>TEXT_DOC_ATTR_2
Beschreibt die Attribute eines Dokuments.

## <a name="syntax"></a>Syntax

```cpp
typedef DWORD TEXT_DOC_ATTR_2;
const TEXT_DOC_ATTR_2 TEXT_DOC_ATTR_READONLY_2 = 0x00000001;
```

```csharp
public const uint TEXT_DOC_ATTR_READONLY_2 = 0x00000001;
```

## <a name="members"></a>Members
 `TEXT_DOC_ATTR_READONLY_2`\
 Gibt an, dass das Dokument schreibgeschützt ist.

## <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Dieser Wert ist in der Assembly für c# nicht tatsächlich definiert. Stattdessen müssen Sie die Definition in die Quelldatei kopieren.

 Wird als Argument an die [onupdatedocumentattributormethode](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md) übermittelt.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)
