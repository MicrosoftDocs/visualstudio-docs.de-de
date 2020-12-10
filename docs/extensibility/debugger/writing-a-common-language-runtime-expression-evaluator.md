---
title: Schreiben einer Common Language Runtime-Ausdrucks Auswertung | Microsoft-Dokumentation
description: Erfahren Sie mehr über das Schreiben einer Ausdrucks Auswertung für die Common Language Runtime, die Ausdrücke in der zu decodierende Codesprache auswertet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1674ae8345873ede5d1b4afb04774d6ed0469b4c
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996317"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>Schreiben einer Common Language Runtime Ausdrucks Auswertung
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Die Ausdrucks Auswertung (EE) ist der Teil einer Debug-Engine (de), der die Syntax und Semantik der Programmiersprache behandelt, die den zu debuggenden Code erzeugt hat. Ausdrücke müssen innerhalb des Kontexts einer Programmiersprache ausgewertet werden. In manchen Sprachen bedeutet der Ausdruck "a + B" z. b. "die Summe von A und b". In anderen Sprachen kann derselbe Ausdruck "A" oder "B" bedeuten. Daher muss für jede Programmiersprache, die den in der Visual Studio-IDE zu decodierende Objektcode generiert, ein separates EE geschrieben werden.

 Einige Aspekte des Visual Studio-debugpakets müssen den Code im Kontext der Programmiersprache interpretieren. Wenn die Ausführung z. b. an einem Haltepunkt angehalten wird, müssen alle Ausdrücke, die der Benutzer in ein **Überwachungs** Fenster eingegeben hat, ausgewertet und angezeigt werden. Der Benutzer kann den Wert einer lokalen Variablen ändern, indem er einen Ausdruck in ein **Überwachungs** Fenster oder im **direkt** Fenster eingeben.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Common Language Runtime und Ausdrucks Auswertung](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md) Erläutert, dass Sie, wenn Sie proprietäre Programmiersprache in die Visual Studio-IDE integrieren, das Schreiben eines EE-fähigen Ausdrucks im Kontext der proprietären Sprache ermöglicht die Kompilierung in eine Microsoft Intermediate Language (MSIL), ohne eine Debug-Engine zu schreiben.

 [Architektur der Ausdrucks Auswertung](../../extensibility/debugger/expression-evaluator-architecture.md) Erläutert, wie die erforderlichen EE-Schnittstellen implementiert und die Common Language Runtime Symbol Anbieter (SP) und Binder Schnittstellen aufgerufen werden.

 [Registrieren einer Ausdrucks Auswertung](../../extensibility/debugger/registering-an-expression-evaluator.md) Beachten Sie, dass sich der EE als Klassenfactory mit den Common Language Runtime-und Visual Studio-Laufzeitumgebungen registrieren muss.

 [Implementieren einer Ausdrucks Auswertung](../../extensibility/debugger/implementing-an-expression-evaluator.md) Beschreibt, wie der Prozess der Auswertung eines Ausdrucks die Debug-Engine (de), den Symbol Anbieter (SP), das Binder Objekt und die Ausdrucks Auswertung (EE) enthält.

 [Lokale anzeigen](../../extensibility/debugger/displaying-locals.md) Beschreibt, wie das Debugpaket, wenn die Ausführung angehalten wird, den de aufruft, um eine Liste der lokalen Variablen und Argumente zu erhalten.

 [Auswerten eines Überwachungs Fenster Ausdrucks](../../extensibility/debugger/evaluating-a-watch-window-expression.md) Dokumentiert, wie das Visual Studio-Debugpaket den de aufruft, um den aktuellen Wert der einzelnen Ausdrücke in der Überwachungsliste zu ermitteln.

 [Ändern des Werts eines lokalen](../../extensibility/debugger/changing-the-value-of-a-local.md) Erläutert, dass bei der Änderung des Werts eines lokalen die einzelnen Zeilen des Fensters lokal über ein zugeordnetes-Objekt verfügen, das den Namen, den Typ und den aktuellen Wert eines lokalen bereitstellt.

 [Implementieren von typvisualisierungen und benutzerdefinierten Viewern](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md) Erläutert, welche Schnittstelle von welcher Komponente implementiert werden muss, um typvisualisierungen und benutzerdefinierte Viewer zu unterstützen.

## <a name="see-also"></a>Weitere Informationen
 [Erweiterbarkeit von Visual Studio-Debugger](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
