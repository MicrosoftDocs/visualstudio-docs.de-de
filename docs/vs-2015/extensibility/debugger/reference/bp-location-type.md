---
title: BP_LOCATION_TYPE | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_LOCATION_TYPE
helpviewer_keywords:
- BP_LOCATION_TYPE structure
ms.assetid: 0248430a-3b61-4809-87a9-e9b6bb7d1130
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fb8074317e52b43806a61d6486c53d7409333e2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153402"
---
# <a name="bp_location_type"></a>BP_LOCATION_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt den Speicherorttyp des Breakpoints für eine Haltepunkt Anforderung an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_BP_LOCATION_TYPE {   
   BPLT_NONE               = 0x00000000,  
   BPLT_FILE_LINE          = 0x00010000,  
   BPLT_FUNC_OFFSET        = 0x00020000,  
   BPLT_CONTEXT            = 0x00030000,  
   BPLT_STRING             = 0x00040000,  
   BPLT_ADDRESS            = 0x00050000,  
   BPLT_RESOLUTION         = 0x00060000,  
   BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,  
   BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,  
   BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,  
   BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,  
   BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,  
   BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,  
   BPLT_TYPE_MASK          = 0x0000FFFF,  
   BPLT_LOCATION_TYPE_MASK = 0xFFFF0000  
};  
typedef DWORD BP_LOCATION_TYPE;  
```  
  
```csharp  
public enum enum_BP_LOCATION_TYPE {   
   BPLT_NONE               = 0x00000000,  
   BPLT_FILE_LINE          = 0x00010000,  
   BPLT_FUNC_OFFSET        = 0x00020000,  
   BPLT_CONTEXT            = 0x00030000,  
   BPLT_STRING             = 0x00040000,  
   BPLT_ADDRESS            = 0x00050000,  
   BPLT_RESOLUTION         = 0x00060000,  
   BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,  
   BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,  
   BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,  
   BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,  
   BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,  
   BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,  
   BPLT_TYPE_MASK          = 0x0000FFFF,  
   BPLT_LOCATION_TYPE_MASK = 0xFFFF0000  
};  
```  
  
## <a name="members"></a>Member  
 BPLT_NONE  
 Gibt keine Haltepunkt Position an.  
  
 BPLT_FILE_LINE  
 Gibt den Speicherorttyp des Breakpoints als Datei Zeile an.  
  
 BPLT_FUNC_OFFSET  
 Gibt den Speicherorttyp des Breakpoints als Funktions Offset an.  
  
 BPLT_CONTEXT  
 Gibt den Speicherorttyp des Breakpoints als Kontext an.  
  
 BPLT_STRING  
 Gibt den Speicherorttyp des Breakpoints als Zeichenfolge an.  
  
 BPLT_ADDRESS  
 Gibt den Speicherorttyp des Breakpoints als Adresse an.  
  
 BPLT_RESOLUTION  
 Gibt den Speicherorttyp des Breakpoints als Auflösung an.  
  
 BPLT_CODE_FILE_LINE  
 Gibt den Speicherorttyp des Breakpoints als Zeile des Quellcodes an.  
  
 BPLT_CODE_FUNC_OFFSET  
 Gibt den Speicherorttyp des Breakpoints als Offset der Code Funktion an.  
  
 BPLT_CODE_CONTEXT  
 Gibt den Speicherorttyp des Breakpoints als Code Kontext an.  
  
 BPLT_CODE_STRING  
 Gibt den Speicherorttyp des Breakpoints als Code Zeichenfolge an.  
  
 BPLT_CODE_ADDRESS  
 Gibt den Speicherorttyp des Breakpoints als Code Adresse an.  
  
 BPLT_DATA_STRING  
 Gibt den Speicherorttyp des Breakpoints als Daten Zeichenfolge an.  
  
 BPLT_TYPE_MASK  
 Gibt eine Bitmaske an, sodass der breakpointtyp aus dem Wert extrahiert werden kann.  
  
 BPLT_LOCATION_TYPE_MASK  
 Gibt eine Bitmaske an, sodass der breakpointtyp aus dem Wert extrahiert werden kann.  
  
## <a name="remarks"></a>Bemerkungen  
 Wird als Parameter an die [getlocationtype](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md) -Methode übergeben.  
  
 Ein breakpointtyp besteht aus einem breakpointtyp und einem lokationstyp. Dies bedeutet, dass ein breakpointtyp nie nur ein breakpointtyp (z. b. `BPT_CODE` ) oder ein Location-Type (z `BPLT_FILE_LINE` . b.) ist. Vordefinierte Konstanten für alle derzeit unterstützten Haltepunkt-Speicherort Typen sind in dieser Enumeration ( `BPLT_CODE_FILE_LINE` bis `BPLT_DATA_STRING` ) enthalten.  
  
 `BPT_CODE` und `BPT_DATA` sind Member der [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) -Enumeration.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Getlocationtype](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)   
 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
