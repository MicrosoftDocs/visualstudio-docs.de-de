---
title: Beispiel Implementierung von lokalen Variablen | Microsoft-Dokumentation
description: Erfahren Sie, wie Visual Studio die lokalen Variablen für eine Methode aus der Ausdrucks Auswertung in diesem Artikel abruft.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aad77c9b9481ed6ae32c66260b1e3ef2a662c836
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847636"
---
# <a name="sample-implementation-of-locals"></a>Beispiel Implementierung von lokalen Variablen
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Im folgenden finden Sie eine Übersicht darüber, wie Visual Studio die lokalen Variablen für eine Methode aus der Ausdrucks Auswertung (EE) abruft:

1. Visual Studio Ruft die (de) [getdebugproperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) -Funktion der Debug-Engine auf, um ein [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) -Objekt zu erhalten, das alle Eigenschaften des Stapel Rahmens (einschließlich der lokalen Variablen) darstellt.

2. `IDebugStackFrame2::GetDebugProperty` Ruft [getmethodproperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) auf, um ein Objekt zu erhalten, das die Methode beschreibt, in der der Breakpoint aufgetreten ist. Die de stellt einen Symbol Anbieter ([idebugsymbolprovider](../../extensibility/debugger/reference/idebugsymbolprovider.md)), eine Adresse ([idebugaddress](../../extensibility/debugger/reference/idebugaddress.md)) und einen Binder ([idebugbinder](../../extensibility/debugger/reference/idebugbinder.md)) bereit.

3. `IDebugExpressionEvaluator::GetMethodProperty` Ruft [getcontainerfield](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) mit dem angegebenen- `IDebugAddress` Objekt auf, um ein [idebugcontainerfield](../../extensibility/debugger/reference/idebugcontainerfield.md) -Objekt zu erhalten, das die Methode darstellt, die die angegebene Adresse enthält.

4. Die- `IDebugContainerField` Schnittstelle wird für die [idebugmethodfield](../../extensibility/debugger/reference/idebugmethodfield.md) -Schnittstelle abgefragt. Diese Schnittstelle ermöglicht den Zugriff auf die lokalen Methoden der Methode.

5. `IDebugExpressionEvaluator::GetMethodProperty` instanziiert eine-Klasse ( `CFieldProperty` die im Beispiel aufgerufen wird), die die `IDebugProperty2` -Schnittstelle ausführt, um die lokalen Methoden der Methode darzustellen. Das `IDebugMethodField` -Objekt wird in diesem- `CFieldProperty` Objekt zusammen mit `IDebugSymbolProvider` den `IDebugAddress` -,-und- `IDebugBinder` Objekten platziert.

6. Wenn das `CFieldProperty` Objekt initialisiert wird, wird [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) für das Objekt aufgerufen, `IDebugMethodField` um eine [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) Struktur zu erhalten, die alle anzeigbaren Informationen über die Methode selbst enthält.

7. `IDebugExpressionEvaluator::GetMethodProperty` Gibt das- `CFieldProperty` Objekt als ein- `IDebugProperty2` Objekt zurück.

8. Visual Studio ruft [enumchildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) für das zurückgegebene `IDebugProperty2` Objekt mit dem Filter auf `guidFilterLocalsPlusArgs` , der ein [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) -Objekt zurückgibt, das die lokalen Methoden der Methode enthält. Diese Enumeration wird durch Aufrufe von [enumlocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) und [enumarguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)ausgefüllt.

9. Visual Studio ruft [als nächstes](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) auf, um eine [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) Struktur für jede lokale zu erhalten. Diese Struktur enthält einen Zeiger auf eine- `IDebugProperty2` Schnittstelle für eine lokale.

10. Visual Studio ruft [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) für jede lokale auf, um den Namen, den Wert und den Typ des lokalen zu erhalten. Diese Informationen werden **im Fenster "** lokal" angezeigt.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Implementieren von getmethodproperty](../../extensibility/debugger/implementing-getmethodproperty.md) Beschreibt eine Implementierung von [getmethodproperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).

 [Lokale aufzählen](../../extensibility/debugger/enumerating-locals.md) Beschreibt, wie die Debug-Engine (de) einen Auflistungsvorgang für lokale Variablen oder Argumente ausführt.

 [Lokale Eigenschaften erhalten](../../extensibility/debugger/getting-local-properties.md) Beschreibt, wie der de aufruft, um den Namen, den Typ und den Wert einer oder mehrerer lokaler Variablen abzurufen.

 [Lokale Werte erhalten](../../extensibility/debugger/getting-local-values.md) Erläutert das erhalten des Werts der lokalen, der die Dienste eines Binder Objekts erfordert, das durch den Auswertungs Kontext angegeben wird.

 [Lokale Auswertung](../../extensibility/debugger/evaluating-locals.md) Erläutert, wie lokale ausgewertet werden.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Auswertungs Kontext](../../extensibility/debugger/evaluation-context.md) Stellt die Argumente bereit, die beim Aufrufen der Ausdrucks Auswertung (EE) durch das-Argument übermittelt werden.

 [Beispiel für mycee](/previous-versions/) Veranschaulicht einen Implementierungs Ansatz zum Erstellen einer Ausdrucks Auswertung für die Sprache Myc.

## <a name="see-also"></a>Siehe auch
- [Anzeigen von lokalen Variablen](../../extensibility/debugger/displaying-locals.md)