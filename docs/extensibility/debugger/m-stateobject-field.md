---
description: Ein-Objekt, das Daten darstellt, die von der Aktion verwendet werden.
title: m_stateObject Feld | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 92fdad68506c62440c7f3e130caee49b4fe780da
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158760"
---
# <a name="m_stateobject-field"></a>m_stateObject Feld
Ein-Objekt, das Daten darstellt, die von der Aktion verwendet werden.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib.dll*)

 Da Sie nicht über das .NET Framework auf dieses interne Element zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.

## <a name="syntax"></a>Syntax

```
.field assembly object m_stateObject
```

## <a name="remarks"></a>Bemerkungen
 Dies ist der `state` Parameter im <xref:System.Threading.Tasks.Task.%23ctor%2A> Konstruktor. Es ist auch das Unterstützungs Feld für die- <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> Eigenschaft.

## <a name="see-also"></a>Weitere Informationen
- [Task class (Task-Klasse)](../../extensibility/debugger/task-class-internal-members.md)
