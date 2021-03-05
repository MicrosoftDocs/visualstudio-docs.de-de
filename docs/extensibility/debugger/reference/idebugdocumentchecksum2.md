---
description: Stellt eine Prüfsumme für ein debugdokument dar und ermöglicht die Übergabe der Prüfsumme zwischen Komponenten.
title: IDebugDocumentChecksum2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c5b39f381817cd98fd94b1c746cbdccde31e0b1f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165565"
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
Stellt eine Prüfsumme für ein debugdokument dar und ermöglicht die Übergabe der Prüfsumme zwischen Komponenten.

## <a name="syntax"></a>Syntax

```
IDebugDocumentChecksum2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle kann von jeder Komponente implementiert werden, die die [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) -Schnittstelle verfügbar macht. Sie wird jedoch in erster Linie von Debug-engines implementiert, sodass die in eine Symbol Datei (*. pdb) eingebettete Prüfsumme an die IDE zurückgegeben und beim Suchen nach einer Quelle verwendet werden kann.

## <a name="methods"></a>Methoden
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugDocumentChecksum2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|Ruft die Prüfsumme des Dokuments und den Algorithmusbezeichner anhand der maximalen Anzahl von Bytes ab, die verwendet werden sollen.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
