---
description: Stellt eine angepasste Benutzeroberfläche zum Auswählen des Ports dar.
title: Idebugportpicker | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 335a954603505d064f32e8f901ce428d6cb8dfa1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142635"
---
# <a name="idebugportpicker"></a>IDebugPortPicker
Stellt eine angepasste Benutzeroberfläche zum Auswählen des Ports dar.

## <a name="syntax"></a>Syntax

```
IDebugPortPicker : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird von Port Lieferanten implementiert. Ein Port Lieferant definiert seine Port Auswahl, indem er ihn als CLSID verfügbar macht und die `metricPortPickerCLSID` Metrik an der verfügbar gemachten CLSID zeigt.

## <a name="methods"></a>Methoden
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugPortPicker` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|Zeigt das angegebene Dialogfeld an, in dem der Benutzer einen Port auswählen kann.|
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|Legt den Dienstanbieter fest.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
