---
title: Auswertung von aufrufsstapeln | Microsoft-Dokumentation
description: Erfahren Sie mehr über die enumframeinfo-Methode und deren Implementierung zum Anzeigen der Stapel Rahmen der aufrufsstapel im Break-Modus.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fc637ff3ce2fe596eed48684523da7114fe0a03a
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914672"
---
# <a name="call-stack-evaluation"></a>Auswertung von aufrufstapeln
Um die Stapel Rahmen der aufzurufenden Auflistung im Break-Modus anzuzeigen, müssen Sie die [enumframeinfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) -Methode implementieren.

## <a name="methods-for-evaluation"></a>Methoden für die Auswertung
 Für eine einfache Debug-Engine (de) gibt es möglicherweise nur einen Stapel Rahmen. Um den Stapel Rahmen im Break-Modus zu untersuchen, müssen Sie die folgenden Methoden von [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)implementieren.

|Methode|Beschreibung|
|------------|-----------------|
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Ruft den Code Kontext für einen Stapel Rahmen ab. Der Code Kontext stellt den aktuellen Anweisungs Zeiger in einem Stapel Rahmen dar.|
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Ruft den Dokument Kontext für einen Stapel Rahmen ab. Der Dokument Kontext stellt die aktuelle Position im Quellcode für einen Stapel Rahmen dar. Erforderlich zum Anzeigen des Quellcodes, wenn Sie in einem Programm angehalten werden.|

 Diese Methoden erfordern die Implementierung mehrerer kontextbezogener Schnittstellen und Methoden. Daher müssen Sie die [getdocumentcontext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) -Methode und die folgenden Methoden von [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md)implementieren.

|Methode|Beschreibung|
|------------|-----------------|
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Ruft den Datei Anweisungs Bereich eines Dokument Kontexts ab.|

 Um Code Kontexte aufzulisten, müssen Sie alle Methoden von [IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)implementieren.

## <a name="see-also"></a>Weitere Informationen
- [Ausführungs Steuerung und Zustands Auswertung](../../extensibility/debugger/execution-control-and-state-evaluation.md)
