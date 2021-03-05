---
description: Enthält zusätzliche Eigenschaften für ein System. Threading. Tasks. Task-Objekt.
title: 'Contingentproperties-Klasse: interne Member | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2303318c7a5f36027ce7709c5b09b5846fc6fab6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154976"
---
# <a name="contingentproperties-class---internal-members"></a>Contingentproperties-Klasse-interne Member
Enthält zusätzliche Eigenschaften für ein- <xref:System.Threading.Tasks.Task> Objekt.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in mscorlib.dll)

 Da Sie nicht auf diese internen Member vom .NET Framework aus zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.

## <a name="syntax"></a>Syntax

```csharp
.class auto ansi nested assembly beforefieldinit ContingentProperties
       extends System.Object
```

## <a name="members"></a>Members

### <a name="fields"></a>Felder

|Name|BESCHREIBUNG|
|----------|-----------------|
|[m_children](../../extensibility/debugger/m-children-field.md)|Die Liste der untergeordneten Aufgaben, die bei dieser Aufgabe registriert sind.|

## <a name="remarks"></a>Bemerkungen
 Der .NET Framework initialisiert die Felder dieser Klasse nur dann, wenn Sie benötigt werden.

## <a name="see-also"></a>Weitere Informationen
- [Parallele Erweiterungs internale für die .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
