---
description: Stellt eine Funktion dar und erweitert die idebugfunctionobject-Schnittstelle.
title: IDebugFunctionObject2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2 interface
ms.assetid: 56b2fdff-146d-4138-a34c-59a9c65a3ddd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 86ceda2742f82cae172c22d12f2753936779171f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151817"
---
# <a name="idebugfunctionobject2"></a>IDebugFunctionObject2
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Stellt eine Funktion dar und erweitert die [idebugfunctionobject](../../../extensibility/debugger/reference/idebugfunctionobject.md) -Schnittstelle.

## <a name="syntax"></a>Syntax

```
IDebugFunctionObject2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Eine Ausdrucks Auswertung (EE) implementiert diese Schnittstelle, um eine Funktion darzustellen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Methoden dieser Schnittstelle verzögern die von **idebugfunctionobject** auf folgende Weise:

- Die **idebugevaluate** -Methode nimmt Flags an.

- Die Methode " **kreateobject** " übernimmt Flags und ein Timeout.

- Die Methode " **kreatestringobjectwithlength** " benötigt eine Länge.

## <a name="methods"></a>Methoden
 Diese Schnittstelle implementiert die folgenden Methoden:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject2-createobject.md)|Erstellt ein-Objekt, das einen Konstruktor mit den angegebenen Auswertungs Kennzeichen-Einstellungen und einem Timeout Wert verwendet.|
|[CreateStringObjectWithLength](../../../extensibility/debugger/reference/idebugfunctionobject2-createstringobjectwithlength.md)|Erstellt ein Zeichen folgen Objekt mit der angegebenen Länge.|
|[Evaluieren](../../../extensibility/debugger/reference/idebugfunctionobject2-evaluate.md)|Ruft die-Funktion auf und gibt den resultierenden Wert als-Objekt zurück.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: EE. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
