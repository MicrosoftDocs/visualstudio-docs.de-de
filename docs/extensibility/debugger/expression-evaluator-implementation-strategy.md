---
title: Implementierungsstrategie der Ausdrucks Auswertung | Microsoft-Dokumentation
description: Erfahren Sie mehr über eine Strategie zum Erstellen einer Ausdrucks Auswertung, indem Sie zuerst Code implementieren, um lokale Variablen im Fenster "lokal" anzuzeigen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b936b465c3a7becbdcb3ea4f36a16b839260ad74
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560147"
---
# <a name="expression-evaluator-implementation-strategy"></a>Implementierungsstrategie für die Ausdrucks Auswertung
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Ein Ansatz zum schnellen Erstellen eines Ausdrucks Auswerters (EE) besteht darin, zuerst den minimalen Code zu implementieren, der erforderlich ist, um lokale Variablen **im Fenster "** lokal" anzuzeigen. Es ist hilfreich zu wissen, dass jede Zeile im **Fenster "** lokal" den Namen, den Typ und den Wert einer lokalen Variablen anzeigt und alle drei durch ein [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) -Objekt dargestellt werden. Der Name, der Typ und der Wert einer lokalen Variablen werden von einem `IDebugProperty2` Objekt durch Aufrufen der [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) -Methode abgerufen. Weitere Informationen zum Anzeigen von lokalen Variablen **im Fenster "** lokal" finden Sie unter [anzeigen](../../extensibility/debugger/displaying-locals.md)von lokalen Variablen.

## <a name="discussion"></a>Diskussion
 Eine mögliche Implementierungs Sequenz beginnt mit der Implementierung von [idebugexpressionevaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). Die Methoden "Analyse [" und "](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) [getmethodproperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) " müssen implementiert werden, um lokale anzuzeigen. Beim Aufrufen von `IDebugExpressionEvaluator::GetMethodProperty` wird ein Objekt zurückgegeben `IDebugProperty2` , das eine Methode darstellt, d. h. ein [idebugmethodfield](../../extensibility/debugger/reference/idebugmethodfield.md) -Objekt. Die Methoden selbst werden nicht **im Fenster "** lokal" angezeigt.

 Die [enumchildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) -Methode sollte als Nächstes implementiert werden. Die Debug-Engine (de) ruft diese Methode auf, um eine Liste der lokalen Variablen und Argumente durch übergeben `IDebugProperty2::EnumChildren` eines- `guidFilter` Arguments von zu erhalten `guidFilterLocalsPlusArgs` . `IDebugProperty2::EnumChildren` Ruft [enumarguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) und [enumlocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)auf und kombiniert die Ergebnisse in einer einzelnen Enumeration. Weitere Informationen finden Sie unter [lokale Anzeige](../../extensibility/debugger/displaying-locals.md) .

## <a name="see-also"></a>Siehe auch
- [Implementieren einer Ausdrucks Auswertung](../../extensibility/debugger/implementing-an-expression-evaluator.md)
- [Lokale anzeigen](../../extensibility/debugger/displaying-locals.md)
