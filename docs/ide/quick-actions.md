---
title: Schnelle Aktionen, Glühbirnen und Schraubendreher
description: Erfahren Sie, wie Sie mit einer einzelnen schnellen Aktion Code umgestalten, generieren oder anderweitig ändern können.
ms.custom: SEO-VS-2020
ms.date: 03/28/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e1d9c257bcf0e2a88a384c22010abb08894483ec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951094"
---
# <a name="quick-actions"></a>Schnelle Aktionen

Mit schnellen Aktionen können Sie ganz leicht Code mit einer einzelnen Aktion umgestalten, generieren oder anderweitig ändern. Schnelle Aktionen sind für C#-, [C++](/cpp/ide/writing-and-refactoring-code-cpp)- und Visual Basic-Codedateien verfügbar. Einige der Aktionen sind für eine Sprache spezifisch, während andere für alle Sprachen gelten.

Schnelle Aktionen können für Folgendes verwendet werden:

- Anwenden einer Codefehlerbehebung für eine Verletzung einer Regel des [Codeanalysetools](../code-quality/roslyn-analyzers-overview.md)

::: moniker range=">=vs-2019"

- [Unterdrücken](../code-quality/use-roslyn-analyzers.md#suppress-violations) einer Verletzung einer Regel des Codeanalysetools oder [Konfigurieren](../code-quality/use-roslyn-analyzers.md#set-rule-severity-from-the-light-bulb-menu) des Schweregrads

::: moniker-end

::: moniker range="vs-2017"

- [Unterdrücken](../code-quality/use-roslyn-analyzers.md#suppress-violations) einer Verletzung einer Regel des Codeanalysetools

::: moniker-end

- Anwenden eines Refactorings (z.B. [Inlinesetzen einer temporären Variable](../ide/reference/inline-temporary-variable.md))

- Generieren von Code (z.B. [Einführen einer lokalen Variable](../ide/reference/introduce-local-variable.md))

> [!NOTE]
> Dieses Thema gilt für Visual Studio unter Windows. Informationen zu Visual Studio für Mac finden sie unter [Refactoring (Visual Studio für Mac)](/visualstudio/mac/refactoring).

Schnelle Aktionen können mithilfe der Glühbirne ![Glühbirnensymbol](media/light-bulb-icon.png), des Schraubendrehers ![Schraubendrehersymbol](media/screwdriver-icon.png) oder durch Drücken der Tasten **STRG**+ **.** angewendet werden, wenn Ihr Cursor sich auf einer Codezeile befindet, für die eine Aktion verfügbar ist. Eine Glühbirne mit einem roten Warnzeichen ![Glühbirnensymbol](media/error-light-bulb-icon.png) wird angezeigt. Das deutet auf einen Fehler hin, für den in Visual Studio eine Problemlösung verfügbar ist.

Drittanbieter können für jede Sprache benutzerdefinierte Diagnosen und Empfehlungen bereitstellen, beispielsweise als Bestandteil eines SDKs. Basierend auf diesen Regeln leuchten die Visual Studio-Glühbirnen dann auf.

## <a name="icons"></a>Symbole

Das Symbol, das angezeigt wird, wenn eine schnelle Aktion verfügbar ist, erläutert den Typ der verfügbaren Fehlerkorrektur oder des Refactorings. Der *Schraubendreher* ![Schraubendrehersymbol](media/screwdriver-icon.png) gibt nur an, dass Aktionen für die Änderung des Codes verfügbar sind, Sie diese jedoch nicht unbedingt verwenden müssen. Die *gelbe Glühbirne* ![Symbol für gelbe Glühbirne](media/light-bulb-icon.png) zeigt, dass Aktionen verfügbar sind, die Sie *durchführen sollten*, um Ihren Code zu verbessern. Die *Glühbirne mit Warnzeichen* ![Symbol für Glühbirne mit Warnzeichen](media/error-light-bulb-icon.png) zeigt, dass eine Aktion verfügbar ist, die einen Fehler in Ihrem Code beheben kann.

## <a name="to-see-a-light-bulb-or-screwdriver"></a>So zeigen Sie eine Glühbirne oder einen Schraubendreher an

Wenn eine Fehlerkorrektur verfügbar ist, werden Glühbirnen angezeigt:

- Beim Zeigen mit der Maus auf die Position eines Fehlers

   ![Glühbirne mit Mauszeigerbewegung](../ide/media/vs2015_lightbulb_hover.png)

- Am linken Rand des Editors, wenn Sie das Caretzeichen (Cursor) in der entsprechenden Codezeile bewegen

Sie können auch **STRG**+ **drücken.** um eine Liste verfügbarer schneller Aktionen und Refactorings anzuzeigen.

Klicken Sie neben der Glühbirne auf den Pfeil nach unten oder auf den Link **Mögliche Korrekturen anzeigen**, um potenzielle Fehlerbehebungen anzuzeigen. Eine Liste der verfügbaren Schnellaktionen wird angezeigt.

![Erweiterte Glühbirne](../ide/media/vs2015_lightbulb_hover_expanded.png)

## <a name="see-also"></a>Weitere Informationen

- [Codegenerierung in Visual Studio](../ide/code-generation-in-visual-studio.md)
- [Häufige schnelle Aktionen](../ide/common-quick-actions.md)
- [Codeformate und Schnellaktionen](../ide/code-styles-and-code-cleanup.md)
- [Schreiben und Refactoring von Code (C++)](/cpp/ide/writing-and-refactoring-code-cpp)
- [Refactoring (Visual Studio für Mac)](/visualstudio/mac/refactoring)
