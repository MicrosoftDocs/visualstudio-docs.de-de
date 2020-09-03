---
title: 'Asynctaskmethodbuilder &lt; TResult &gt; -Struktur: interne Member | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- AsyncTaskMethodBuilder<TResult> structure [.NET Framework debug engines]
- debug engines, AsyncTaskMethodBuilder<TResult> structure [.NET Framework]
ms.assetid: 17ebc340-8170-4aff-bf54-dc4548c83632
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7e4999b71ae8f654aa3d362ba16c6cf5bc6574da
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182266"
---
# <a name="asynctaskmethodbuilderlttresultgt-structure---internal-members"></a>Asynctaskmethodbuilder &lt; TResult &gt; -Struktur: interne Member
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In diesem Thema werden die internen Member der- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> Klasse beschrieben. Allgemeine Informationen zu dieser Klasse finden Sie im <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> Referenz Thema.  
  
 **Namespace:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in mscorlib.dll)  
  
 Da Sie nicht auf diese internen Member vom .NET Framework aus zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder`1<TResult>  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>Interne Mitglieder  
  
|Name|Beschreibung|  
|----------|-----------------|  
|[Objectidfordebugger-Eigenschaft](../../extensibility/debugger/asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)|Ruft ein Objekt ab, das verwendet werden kann, um diesen Generator für den Debugger eindeutig zu identifizieren.|  
|[m_task Feld](../../extensibility/debugger/asynctaskmethodbuilder-tresult-m-task-field.md)|Stellt die verzögert initialisierte erstellter Aufgabe dar.|  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>   
 [Interne Elemente der parallelen Erweiterung für das .NET-Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
