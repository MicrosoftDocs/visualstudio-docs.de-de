---
title: Codeanalyse-Regelsatzreferenz
ms.date: 04/04/2018
description: Erfahren Sie mehr über integrierte Regelsätze in der Visual Studio-Legacy Code Analyse. Weitere Informationen finden Sie unter Ressourcen in den Regelsätzen. Erfahren Sie, wie diese Sätze in angepassten Regelsätzen verwendet werden.
ms.custom: SEO-VS-2020
ms.topic: reference
helpviewer_keywords:
- code analysis, rule sets reference
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cead2d51a13ce4ec137edcd55c7db91d84b04f7f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867775"
---
# <a name="code-analysis-rule-set-reference"></a>Codeanalyse-Regelsatzreferenz

Wenn Sie die Legacy-Analyse für Projekte mit verwaltetem Code in Visual Studio konfigurieren, können Sie aus einer Liste integrierter *Regelsätze* auswählen. Einige Regeln sind in mehr als einem der integrierten Regelsätze enthalten, z. b. enthält der Regelsatz "grundlegende Regeln für Richtigkeit" Regeln, die im Regelsatz für verwaltete Empfohlene Regeln enthalten sind.

> [!NOTE]
> Die Regelsätze in diesem Abschnitt beziehen sich auf die Legacy-Analyse. Weitere Informationen zu Regelsätzen, die für Code Analyzer-Pakete verfügbar sind, finden Sie unter [Verwenden von Regelsätzen mit Code Analyse](/dotnet/fundamentals/code-analysis/code-quality-rule-options)Modulen.

Sie können entweder einen dieser integrierten Regelsätze verwenden, oder Sie können [einen Regelsatz](../code-quality/how-to-create-a-custom-rule-set.md) an Ihre Projektanforderungen anpassen. Wenn Sie mehrere Regelsätze einschließen, die dieselbe Regel in einem benutzerdefinierten Regelsatz enthalten, wird diese Regel nur einmal im benutzerdefinierten Regelsatz angezeigt.

In den Themen in diesem Abschnitt werden die integrierten Regelsätze und die darin enthaltenen Regeln (oder Warnungen) beschrieben.

| Regelsatz | Enthaltene Regeln |
| - | - |
| [Alle Regeln](all-rules-rule-set.md) | Enthält alle verfügbaren verwalteten und C++-Regeln. |
| [Grundlegende Regeln für Richtigkeit](basic-correctness-rules-rule-set-for-managed-code.md) | Schließt verwaltete Empfohlene Regeln sowie Regeln für Logic Errors und Framework-Verwendung ein. |
| [Erweiterte Regeln für Richtigkeit](extended-correctness-rules-rule-set-for-managed-code.md) | Enthält grundlegende Regeln zur Richtigkeit (einschließlich verwalteter empfohlener Regeln) sowie weitere Regeln für Logikfehler und die frameworkverwendung. |
| [Grundlegende Regeln für Entwurfsrichtlinien](basic-design-guideline-rules-rule-set-for-managed-code.md) | Umfasst verwaltete Empfohlene Regeln und Regeln, mit denen sichergestellt werden kann, dass Code einfach zu lesen, zu verstehen und zu warten |
| [Erweiterte Regeln für Entwurfsrichtlinien](extended-design-guidelines-rules-rule-set-for-managed-code.md) | Umfasst grundlegende Regeln für die Entwurfsrichtlinie (einschließlich verwalteter empfohlener Regeln) sowie weitere wart barkeits Regeln, die sich auf die Benennung konzentrieren |
| [Globalisierungsregeln](globalization-rules-rule-set-for-managed-code.md) | Schließt Regeln für Globalisierungs Probleme ein. |
| [Verwaltete Mindestregeln](managed-minimum-rules-rule-set-for-managed-code.md) | Enthält vier Regeln für kritische Probleme mit verwaltetem Code. |
| [Verwaltete empfohlene Regeln](managed-recommended-rules-rule-set-for-managed-code.md) | Schließt verwaltete Mindestregeln und mehr Regeln für kritische Probleme mit verwaltetem Code ein. |
| [Gemischte Mindestregeln](mixed-minimum-rules-rule-set.md) | Schließt Regeln für kritische Probleme in C++-Code für CLR ein. |
| [Gemischte empfohlene Regeln](mixed-recommended-rules-rule-set.md) | Schließt gemischte minimal Regeln und mehr Regeln für kritische Probleme in C++-Code für CLR ein. |
| [Native Mindestregeln](native-minimum-rules-rule-set.md) | Enthält Regeln für kritische Probleme in nativem Code. |
| [Native empfohlene Regeln](native-recommended-rules-rule-set.md) | Umfasst systemeigene Mindestregeln und mehr Regeln für kritische Probleme in System eigenem Code |
| [Sicherheitsregeln](security-rules-rule-set-for-managed-code.md) | Enthält Regeln zum Ermitteln von Sicherheitsrisiken. |