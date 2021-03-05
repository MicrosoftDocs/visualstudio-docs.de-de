---
description: Ermöglicht der Visual Studio-Benutzeroberfläche das Anzeigen von Text im Abschnitt Transport Informationen des Dialog Felds an den Prozess anhängen.
title: IDebugPortSupplierDescription2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8c3cd8d6fbeaf020ea772c9bd5cae783b6e8d127
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150379"
---
# <a name="idebugportsupplierdescription2"></a>IDebugPortSupplierDescription2
Ermöglicht der [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Benutzeroberfläche, Text innerhalb des Abschnitts **Transport Informationen** im Dialogfeld **an den Prozess anhängen** anzuzeigen.

## <a name="syntax"></a>Syntax

```
IDebugPortSupplierDescription2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird von Port Lieferanten implementiert.

## <a name="methods"></a>Methoden
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugPortSupplierDescription2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|Ruft die Beschreibungs-und Beschreibungs Metadaten für den Port Lieferanten ab.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
