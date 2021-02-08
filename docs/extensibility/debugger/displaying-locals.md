---
title: Anzeigen von lokalen Variablen | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Liste der lokalen Variablen und Argumente, die zusammen mit den lokalen Variablen der Methode bezeichnet werden, die angezeigt werden, wenn die Ausführung angehalten wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 31e0ebeb4155fef551f98a81f93e02ecdf2ecb9b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840768"
---
# <a name="display-locals"></a>Lokale anzeigen
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Die Ausführung erfolgt immer innerhalb des Kontexts einer Methode, die auch als enthaltende Methode oder aktuelle Methode bezeichnet wird. Wenn die Ausführung angehalten wird, ruft Visual Studio die Debug-Engine (de) auf, um eine Liste der lokalen Variablen und Argumente zu erhalten, die zusammen als lokale Variablen der Methode bezeichnet werden. Visual Studio zeigt diese lokalen Variablen und ihre Werte im **Fenster "** lokal" an.

 Um lokale anzuzeigen, ruft der de die [getmethodproperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) -Methode auf, die zum EE gehört, und gibt ihm einen Auswertungs Kontext, d. h. einen Symbol Anbieter (SP), die aktuelle Ausführungs Adresse und ein Binder Objekt. Weitere Informationen finden Sie unter [Evaluierungs Kontext](../../extensibility/debugger/evaluation-context.md). Wenn der-Befehl erfolgreich ausgeführt wird, `IDebugExpressionEvaluator::GetMethodProperty` gibt die Methode ein [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) -Objekt zurück, das die Methode darstellt, die die aktuelle Ausführungs Adresse enthält.

 Der de ruft [enumchildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) auf, um ein [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) -Objekt zu erhalten, das so gefiltert wird, dass nur die lokalen Elemente zurückgegeben werden, und die Enumeration, um eine Liste mit [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) Jede Struktur enthält den Namen, den Typ und den Wert eines lokalen. Der Typ und der Wert werden als formatierte Zeichen folgen gespeichert, die für die Anzeige geeignet sind. Der Name, der Typ und der Wert werden in der Regel in einer Zeile des **Fensters "** lokal" angezeigt.

> [!NOTE]
> Im Fenster **schnell Überwachung** und **Überwachung** werden auch Variablen mit dem gleichen Format wie Name, Wert und Typ angezeigt. Diese Werte werden jedoch abgerufen, indem [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) anstelle von aufgerufen wird `IDebugProperty2::EnumChildren` .

## <a name="in-this-section"></a>In diesem Abschnitt
 [Beispiel Implementierung von lokalen](../../extensibility/debugger/sample-implementation-of-locals.md) Variablen Verwendet Beispiele, um den Prozess der Implementierung von lokalen Variablen zu durchlaufen.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Auswertungs Kontext](../../extensibility/debugger/evaluation-context.md) Erläutert, dass die Debug-Engine (de) die Ausdrucks Auswertung (EE) aufruft, die drei Argumente übergibt.

## <a name="see-also"></a>Weitere Informationen
 [Schreiben einer CLR-Ausdrucks Auswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
