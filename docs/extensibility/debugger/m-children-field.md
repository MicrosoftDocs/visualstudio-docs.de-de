---
title: m_children Feld | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 12bf76c5c9b62184a74006ddf288c7e581215ce0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925282"
---
# <a name="m_children-field"></a>m_children Feld
Die Liste der untergeordneten Aufgaben, die bei dieser Aufgabe registriert sind.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib.dll*)

 Da Sie nicht über das .NET Framework auf dieses interne Element zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.

## <a name="syntax"></a>Syntax

```csharp
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children
```

## <a name="remarks"></a>Bemerkungen
 Während die Aufgabe ausgeführt wird, sollte nur der Thread, der die Aufgabe ausführt, auf dieses Array zugreifen.

 Wenn die Aufgabe abgeschlossen ist, können andere Threads auf dieses Feld zugreifen, solange Sie nichts hinzufügen oder daraus entfernen.

## <a name="see-also"></a>Weitere Informationen
- [Contingentproperties-Klasse](../../extensibility/debugger/contingentproperties-class-internal-members.md)
