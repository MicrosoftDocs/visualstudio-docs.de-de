---
title: Idebugclassfield | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugClassField
helpviewer_keywords:
- IDebugClassField interface
ms.assetid: 49358cbc-8973-4862-9dcc-79b1248e6712
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2bd5dfaea68abae6730a97efdff088ca6e7c7a00
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696987"
---
# <a name="idebugclassfield"></a>IDebugClassField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle stellt eine Klasse als Typ dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugClassField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Ein Symbol Anbieter implementiert diese Schnittstelle für das gleiche Objekt, das die [idebugcontainerfield](../../../extensibility/debugger/reference/idebugcontainerfield.md) -Schnittstelle implementiert. Diese Schnittstelle ist eine Spezialisierung, die einen Klassentyp darstellt.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Eine Reihe von Schnittstellen verfügt über Methoden, die diese Schnittstelle zurückgeben können, einschließlich [idebugsymbolprovider](../../../extensibility/debugger/reference/idebugsymbolprovider.md), [idebugmethodfield](../../../extensibility/debugger/reference/idebugmethodfield.md)und [idebugcustomattribute](../../../extensibility/debugger/reference/idebugcustomattribute.md). Sie können auch [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) verwenden, um diese Schnittstelle von der [idebugcontainerfield](../../../extensibility/debugger/reference/idebugcontainerfield.md) -Schnittstelle abzurufen, wenn die [getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) -Methode das-Flag zurückgibt `FIELD_TYPE_CLASS` .  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Zusätzlich zu den Methoden in den Schnittstellen [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) und [idebugcontainerfield](../../../extensibility/debugger/reference/idebugcontainerfield.md) implementiert diese Schnittstelle Folgendes:  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[EnumBaseClasses](../../../extensibility/debugger/reference/idebugclassfield-enumbaseclasses.md)|Erstellt einen Enumerator für die Basisklassen dieser Klasse.|  
|[DoesInterfaceExist](../../../extensibility/debugger/reference/idebugclassfield-doesinterfaceexist.md)|Bestimmt, ob eine bestimmte Schnittstelle in der Klasse definiert ist.|  
|[EnumNestedClasses](../../../extensibility/debugger/reference/idebugclassfield-enumnestedclasses.md)|Erstellt einen Enumerator für die in der Klasse aufgeführten Klassen.|  
|[GetEnclosingClass](../../../extensibility/debugger/reference/idebugclassfield-getenclosingclass.md)|Ruft die Klasse ab, die diese Klasse einschließt.|  
|[EnumInterfacesImplemented](../../../extensibility/debugger/reference/idebugclassfield-enuminterfacesimplemented.md)|Erstellt einen Enumerator für die von dieser Klasse implementierten Schnittstellen.|  
|[EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)|Erstellt einen Enumerator für die Konstruktoren dieser Klasse.|  
|[GetDefaultIndexer](../../../extensibility/debugger/reference/idebugclassfield-getdefaultindexer.md)|Ruft den Namen des Standardindexers ab.|  
|[EnumNestedEnums](../../../extensibility/debugger/reference/idebugclassfield-enumnestedenums.md)|Erstellt einen Enumerator für die unter aufgefügten Enumeratoren dieser Klasse.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: sh. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Symbol Anbieter Schnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
