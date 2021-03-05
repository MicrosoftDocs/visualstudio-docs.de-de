---
description: In diesem Thema werden die internen Member der System. Runtime. CompilerServices. asynctaskmethodbuilder-Klasse beschrieben.
title: 'Asynctaskmethodbuilder &lt; TResult &gt; -Struktur: interne Member | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- AsyncTaskMethodBuilder<TResult> structure [.NET Framework debug engines]
- debug engines, AsyncTaskMethodBuilder<TResult> structure [.NET Framework]
ms.assetid: 17ebc340-8170-4aff-bf54-dc4548c83632
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 35e1ca4d19727383bdd7c957bc59fd6b6568c9f5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145650"
---
# <a name="asynctaskmethodbuilderlttresultgt-structure---internal-members"></a>Asynctaskmethodbuilder &lt; TResult &gt; -Struktur: interne Member
In diesem Thema werden die internen Member der- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> Klasse beschrieben. Allgemeine Informationen zu dieser Klasse finden Sie im <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> Referenz Thema.

 **Namespace:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Assembly:** mscorlib (in mscorlib.dll)

 Da Sie nicht auf diese internen Member vom .NET Framework aus zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.

## <a name="syntax"></a>Syntax

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder`1<TResult>
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Interne Member

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Objectidfordebugger-Eigenschaft](../../extensibility/debugger/asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)|Ruft ein Objekt ab, das verwendet werden kann, um diesen Generator für den Debugger eindeutig zu identifizieren.|
|[m_task Feld](../../extensibility/debugger/asynctaskmethodbuilder-tresult-m-task-field.md)|Stellt die verzögert initialisierte erstellter Aufgabe dar.|

## <a name="see-also"></a>Weitere Informationen
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>
- [Parallele Erweiterungs internale für die .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
