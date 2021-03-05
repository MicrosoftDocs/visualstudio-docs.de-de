---
description: In diesem Artikel werden die internen Member der System. Runtime. CompilerServices. asynctaskmethodbuilder-Klasse beschrieben.
title: AsyncTaskMethodBuilder-Struktur – interne Member
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncTaskMethodBuilder structure [.NET Framework]
- AsyncTaskMethodBuilder structure [.NET Framework debug engines]
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 241b4f3aae50ac70afc8320b637535035ee427e2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145689"
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>Asynctaskmethodbuilder-Struktur: interne Member
In diesem Thema werden die internen Member der- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> Klasse beschrieben. Allgemeine Informationen zu dieser Klasse finden Sie im <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> Referenz Thema.

 **Namespace:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Assembly:** mscorlib (in mscorlib.dll)

 Da Sie nicht auf diese internen Member vom .NET Framework aus zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.

## <a name="syntax"></a>Syntax

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Interne Member

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Objectidfordebugger-Eigenschaft](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|Ruft ein Objekt ab, das verwendet werden kann, um diesen Generator für den Debugger eindeutig zu identifizieren.|
|[m_builder Feld](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|Stellt das generische Generator Objekt dar, an das diese nicht generische Instanz delegiert.|

## <a name="see-also"></a>Weitere Informationen
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>
- [Parallele Erweiterungs internale für die .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
