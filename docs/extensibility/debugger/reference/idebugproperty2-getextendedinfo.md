---
title: 'IDebugProperty2:: getextendecodinfo | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetExtendedInfo
helpviewer_keywords:
- IDebugProperty2::GetExtendedInfo
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1bb9fe21b1dc004d5a124a1146e6f7610fbe8699
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99916055"
---
# <a name="idebugproperty2getextendedinfo"></a>IDebugProperty2::GetExtendedInfo
Ruft erweiterte Informationen für die-Eigenschaft ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetExtendedInfo ( 
   REFGUID* guidExtendedInfo,
   VARIANT* pExtendedInfo
);
```

```csharp
int GetExtendedInfo ( 
   ref Guid guidExtendedInfo,
   out object pExtendedInfo
);
```

## <a name="parameters"></a>Parameter
`guidExtendedInfo`\
in GUID, die den Typ der erweiterten Informationen bestimmt, die abgerufen werden sollen. Einzelheiten finden Sie in den Hinweisen.

`pExtendedInfo`\
vorgenommen Gibt ein `VARIANT` (C++) oder ein-Objekt (c#) zurück, das zum Abrufen der erweiterten Eigenschaften Informationen verwendet werden kann. Dieser Parameter kann z. b. eine `IUnknown` Schnittstelle zurückgeben, die für eine [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) -Schnittstelle abgefragt werden kann. Einzelheiten finden Sie in den Hinweisen.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird der Fehlercode zurückgegeben. Gibt zurück `S_GETEXTENDEDINFO_NO_EXTENDEDINFO` , wenn keine erweiterten Informationen zum Abrufen vorhanden sind.

## <a name="remarks"></a>Bemerkungen
 Diese Methode ist für das Abrufen von Informationen vorhanden, die nicht durch Aufrufen der [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) -Methode abgerufen werden können.

 Die folgenden GUIDs werden in der Regel von dieser Methode erkannt (die GUID-Werte werden für c# angegeben, da der Name in keiner Assembly verfügbar ist). Für die interne Verwendung können zusätzliche GUIDs erstellt werden.

|Name|GUID|Beschreibung|
|----------|----------|-----------------|
|guiddocument|{3F 98debug-84-fee9-11D0-b47f -00a0244a1dd2}|Gibt eine- `IUnknown` Schnittstelle für das Dokument zurück. In der Regel kann die [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) -Schnittstelle von dieser `IUnknown` Schnittstelle abgerufen werden.|
|guidcodecontext|{e2fc65e-56ce-11d1-B528-00aax004a8797}|Gibt eine `IUnknown` Schnittstelle zum Dokument Kontext zurück. In der Regel kann die [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) -Schnittstelle von dieser `IUnknown` Schnittstelle abgerufen werden.|
|guidcustomviewersupported|{d9c9da31-ffbe-4eeb-9186-23121e3c088c}|Gibt eine Zeichenfolge zurück, die die CLSID eines benutzerdefinierten Viewers enthält, der in der Regel durch eine Ausdrucks Auswertung implementiert wird.|
|guidextende dinfoslot|{6df235ad-82c6-4292-9c97-7389770bc42f}|Gibt eine 32-Bit-Zahl zurück, die die gewünschte Slot-Nummer darstellt, wenn diese Eigenschaft eine lokale Adresse des verwalteten Codes darstellt.|
|guidextendedinfosignature|{b5fb6d46-f805-417f-96a3-8ba737073ffd}|Gibt eine Zeichenfolge zurück, die die Signatur der dem Eigenschafts Objekt zugeordneten Variablen enthält.|

## <a name="see-also"></a>Weitere Informationen
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
