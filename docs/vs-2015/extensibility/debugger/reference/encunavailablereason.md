---
title: "\"Umcunavailablereason\" | Microsoft-Dokumentation"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0ebdc5518579223a0081f30a0affd3a45e91604e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198772"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

`This is for internal use only!` Stellt die Gründe dar, warum " **Bearbeiten und Fortfahren** " nicht verfügbar ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum tagEncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
typedef enum tagEncUnavailableReason EncUnavailableReason;  
```  
  
```csharp  
public enum EncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
```  
  
#### <a name="parameters"></a>Parameter  
 ENCUN_NONE  
 Kein spezieller Grund, warum "Bearbeiten und Fortfahren" nicht verfügbar ist.  
  
 ENCUN_INTEROP  
 "Bearbeiten und Fortfahren" ist während eines Interop-Aufrufes nicht verfügbar.  
  
 ENCUN_SQLCLR  
 "Bearbeiten und Fortfahren" ist während eines SQL-Prozedur Aufrufers, der die Common Language Runtime (CLR) verwendet, nicht verfügbar.  
  
 ENCUN_MINIDUMP  
 "Bearbeiten und Fortfahren" ist während der Verarbeitung eines Mini Abbilds nicht verfügbar.  
  
 ENCUN_EMBEDDED  
 "Bearbeiten und Fortfahren" ist beim Verarbeiten von eingebettetem Code nicht verfügbar.  
  
 ENCUN_ATTACH  
 "Bearbeiten und Fortfahren" ist nicht verfügbar, da die Sitzung an den Debugger angefügt, nicht von diesem gestartet wurde.  
  
 ENCUN_WIN64  
 "Bearbeiten und Fortfahren" ist während der Verarbeitung von 64-Bit-Windows-Code nicht verfügbar  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Enumeration ist nur für die interne Verwendung durch vorgesehen [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] . Die Methoden " [getencavailablestate](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) " und " [disableenumc](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) ", die von einem benutzerdefinierten Port Lieferanten implementiert werden, sollten immer zurückgeben `E_NOTIMPL` .  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. idl  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Disableumc](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)
