---
description: Signalisiert der Visual Studio-Debugger-Benutzeroberfläche, den Benutzer zu warnen, dass Symbole für die gestartete ausführbare Datei nicht gefunden werden konnten.
title: IDebugNoSymbolsEvent2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugNoSymbolsEvent2 interface
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 859c9c1d07a5f4660f2d13dcffac4f19659a2bc2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149820"
---
# <a name="idebugnosymbolsevent2"></a>IDebugNoSymbolsEvent2
Signalisiert der [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Debugger-Benutzeroberfläche, den Benutzer zu warnen, dass Symbole für die gestartete ausführbare Datei nicht gefunden werden konnten.

## <a name="syntax"></a>Syntax

```
IDebugNoSymbolsEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Wird von Debug-engines implementiert und von der [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Debugger-Benutzeroberfläche verwendet.

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
