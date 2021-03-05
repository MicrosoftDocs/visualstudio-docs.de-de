---
description: Ruft die angegebene Anzahl von Bytes aus dem-Objekt ab.
title: 'Ieedatastorage:: GetData | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f28533ad07bc7626f1576ef4422d6d20725b9450
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102227306"
---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
Ruft die angegebene Anzahl von Bytes aus dem-Objekt ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetData(
   ULONG  dataSize,
   ULONG* sizeGotten,
   BYTE*  data
);
```

```csharp
int GetData(
   uint     dataSize,
   out uint sizeGotten,
   byte[]   data
);
```

## <a name="parameters"></a>Parameter
`dataSize`\
in Die Anzahl der abzurufenden bytes (das `data` Array muss mindestens diese Anzahl von Bytes enthalten).

`sizeGotten`\
vorgenommen Gibt die Anzahl der tatsächlich abgerufenen Bytes zurück.

`data`\
[in, out] Das Array, das mit den angeforderten Daten aufgefüllt werden soll.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die empfohlene Verwendung dieser Methode besteht darin, alle Daten Bytes in ein lokales Array abzurufen, da es keine Möglichkeit gibt, die Bytes im Abruf Vorgang zu überspringen. In diesem Fall sollte der-Parameter `dataSize` der Wert sein, der von der [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md) -Methode zurückgegeben wird.

## <a name="see-also"></a>Weitere Informationen
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)
