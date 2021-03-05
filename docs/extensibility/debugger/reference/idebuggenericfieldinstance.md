---
description: Stellt eine Instanz eines Felds für einen generischen verwalteten Codetyp dar.
title: Idebuggenericfieldinstance | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericFieldInstance interface
ms.assetid: f68b4761-be8b-4801-9d4b-cde90e01d95e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1e593e3e739831ac8478a277962201d4be8f9554
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165344"
---
# <a name="idebuggenericfieldinstance"></a>IDebugGenericFieldInstance
Stellt eine Instanz eines Felds für einen generischen verwalteten Codetyp dar.

## <a name="syntax"></a>Syntax

```
IDebugGenericFieldInstance : IUnknown
```

## <a name="methods"></a>Methoden
 Diese Schnittstelle implementiert die folgenden Methoden:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetTypeArguments](../../../extensibility/debugger/reference/idebuggenericfieldinstance-gettypearguments.md)|Ruft die Typparameter Argumente für diese Instanz ab.|
|[TypeArgumentCount](../../../extensibility/debugger/reference/idebuggenericfieldinstance-typeargumentcount.md)|Gibt die Anzahl der Typparameter Argumente für diese Instanz zurück.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
