---
title: BP_ERROR_TYPE | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_ERROR_TYPE
helpviewer_keywords:
- BP_ERROR_TYPE enumeration
ms.assetid: c483eaab-db29-46de-bfdb-5c2a9a9cfb68
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2317fafe410cacfca1c77b669a54669ea6e2224a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153535"
---
# <a name="bp_error_type"></a>BP_ERROR_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt den Fehlertyp eines Breakpoints an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_BP_ERROR_TYPE {   
   BPET_NONE            = 0x00000000,  
   BPET_TYPE_WARNING    = 0x00000001,  
   BPET_TYPE_ERROR      = 0x00000002,  
   BPET_SEV_HIGH        = 0x0F000000,  
   BPET_SEV_GENERAL     = 0x07000000,  
   BPET_SEV_LOW         = 0x01000000,  
   BPET_TYPE_MASK       = 0x0000ffff,  
   BPET_SEV_MASK        = 0xffff0000,  
   BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,  
   BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,  
   BPET_ALL             = 0xffffffff  
};  
typedef DWORD BP_ERROR_TYPE;  
```  
  
```csharp  
public enum enum_BP_ERROR_TYPE {   
   BPET_NONE            = 0x00000000,  
   BPET_TYPE_WARNING    = 0x00000001,  
   BPET_TYPE_ERROR      = 0x00000002,  
   BPET_SEV_HIGH        = 0x0F000000,  
   BPET_SEV_GENERAL     = 0x07000000,  
   BPET_SEV_LOW         = 0x01000000,  
   BPET_TYPE_MASK       = 0x0000ffff,  
   BPET_SEV_MASK        = 0xffff0000,  
   BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,  
   BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,  
   BPET_ALL             = 0xffffffff  
};  
```  
  
## <a name="members"></a>Member  
 BPET_NONE  
 Gibt keinen Breakpoint-Fehler an.  
  
 BPET_TYPE_WARNING  
 Gibt einen Haltepunkt Fehler im Warnungs Stil an.  
  
 BPET_TYPE_ERROR  
 Gibt einen Haltepunkt Fehler im Fehler Stil an.  
  
 BPET_SEV_HIGH  
 Gibt einen Breakpoint-Fehler mit hohem Schweregrad an.  
  
 BPET_SEV_GENERAL  
 Gibt einen Breakpoint-Fehler mit mittlerer Schweregrad an.  
  
 BPET_SEV_LOW  
 Gibt einen Haltepunkt Fehler mit niedrigem Schweregrad an.  
  
 BPET_TYPE_MASK  
 Gibt einen Haltepunkt Fehler im Masken Stil an.  
  
 BPET_SEV_MASK  
 Gibt einen Haltepunkt Fehler mit Schweregrad Maske an.  
  
 BPET_GENERAL_WARNING  
 Gibt einen Haltepunkt Fehler im allgemeinen Warn Stil an.  
  
 BPET_GENERAL_ERROR  
 Gibt einen Haltepunkt Fehler im allgemeinen Fehler Stil an.  
  
 BPET_ALL  
 Gibt alle Breakpoint-Fehlertypen an.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Werte können mit einem bitweisen kombiniert `OR` und für den `dwType` Member der [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) Struktur verwendet werden. Wird als Parameter an die [enumerrorbreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) -Methode übergeben.  
  
 Ein breakpointfehlertyp besteht aus einem Typ und einem Schweregrad. Dies bedeutet, dass ein breakpointfehlertyp nie nur ein Typ (z `BPET_TYPE_ERROR` . b.,) oder ein Schweregrad (z `BPET_SEV_GENERAL` . b.) allein ist. `BPET_GENERAL_WARNING` und `BPET_GENERAL_ERROR` stellen vordefinierte Werte für Allgemeine Warn-und Fehler Breakpoints bereit.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
