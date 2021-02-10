---
title: Linting für R-Code
description: Erfahren Sie mehr über das Arbeiten mit der integrierten Linting-Unterstützung für R von Visual Studio, einschließlich der Linter-Optionen.
ms.date: 07/02/2018
ms.topic: conceptual
f1_keywords:
- vs.toolsoptionspages.text_editor.r.lint
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 1c32bffbd25a39ff2053dea22930365860ed04a7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873657"
---
# <a name="lint-r-code-in-visual-studio"></a>Linting für R-Code in Visual Studio

Ein Linter analysiert Code, um potenzielle Fehler, Formatierungsprobleme und andere Störfaktoren bei Codes (z.B. falschen Leerraum) aufzudecken. Die Verwendung eines Linters hilft auch dabei, bestimmte Codierungskonventionen zu fördern, z.B. die Benennung von Bezeichnern. Konventionen wie diese sind innerhalb von Teams und für andere kooperative Situationen hilfreich.

R Tools für Visual Studio (RTVS) bieten einen integrierten Linter für R, dessen Verhalten durch eine Vielzahl von Optionen gesteuert wird. Diese werden im vorliegenden Artikel beschrieben. Diese Optionen finden Sie unter **Extras** > **Optionen** > **Text-Editor** > **R** > **Lint**.

Die Option „Lint“ ist standardmäßig deaktiviert. Legen Sie die Option **Alle** > **Lint aktivieren** auf **TRUE** fest, um sie zu aktivieren.

Wenn die Option aktiviert ist, wird der Linter während der Eingabe im Editor ausgeführt. Probleme werden als grüne Wellenlinien angezeigt. In der folgenden Grafik hat RTVS beispielsweise sechs Lint-Probleme identifiziert, darunter die Verwendung von `=` anstelle von `<-` für eine Zuweisung, fehlende Abstände um Funktionsargumente, die Verwendung von Bezeichnern in Pascal-Schreibweise und Großbuchstaben sowie die Verwendung eines Semikolons. Beim Bewegen des Mauszeigers über einem Problem wird eine Beschreibung eingeblendet.

![Beispiele der Linter-Ausgabe für R-Code](media/linting-01.png)

Sie ändern die Linter-Optionen je nach den Anforderungen eines Projekts oder einer Datei häufig. Beispielcode eines Onlinekurses kann beispielsweise `=` anstelle von `<-` zusammen mit Bezeichnern in Pascal-Schreibweise verwenden. Ein solcher Code würde häufig Linter-Warnungen anzeigen, da die Linter-Standardoptionen diese Schreibweisen kennzeichnen. Beim Arbeiten mit diesem Code können Sie die Optionen dann deaktivieren, statt sich mit der Korrektur der einzelnen Instanzen befassen zu müssen.

## <a name="assignment-group"></a>Zuweisungsgruppe

| Option | Standardwert | Lint-Effekt |
| --- | --- | --- |
| **\<- erzwingen** | **True** | Ermittelt, wenn `<-` nicht für die Zuweisung verwendet wird. |

## <a name="naming-group"></a>Gruppe „Benennung“

Diese Optionen kennzeichnen Bezeichner, die unterschiedliche Namenskonventionen nutzen:

| Option | Standardwert | Lint-Effekt |
| --- | --- | --- |
| **camelCase markieren** | **False** | Kennzeichnet Bezeichner mit gemischter Groß-/Kleinschreibung. |
| **Lange Namen markieren** | **False** | Kennzeichnet Bezeichner, deren Namen die Einstellung **Maximale Namenslänge** überschreiten. |
| **Mehrere Punkte markieren** | **True** | Kennzeichnet Bezeichner mit mehreren Punkten. |
| **PascalCase markieren** | **True** | Kennzeichnet Bezeichner in Pascal-Schreibweise. |
| **snake_case markieren** | **False** | Kennzeichnet Bezeichner mit Unterstrichen. |
| **GROSSBUCHSTABEN markieren** | **True** | Kennzeichnet Bezeichner in GROßBUCHSTABEN. |
| **Maximale Namenslänge** | **32** | Die über die Einstellung **Lange Namen markieren** zugewiesene Länge. |

## <a name="spacing-group"></a>Gruppe „Abstand“

Diese Optionen, die alle standardmäßig auf **TRUE** festgelegt sind, steuern, wo der Linter Abstandsprobleme erkennt: hinter Funktionsnamen, um Kommas herum, um Operatoren herum, Position der öffnenden und schließenden geschweiften Klammer, Leerzeichen vor ( und Leerzeichen innerhalb von ().

## <a name="statements-group"></a>Gruppe „Anweisungen“

| Option | Standardwert | Lint-Effekt |
| --- | --- | --- |
| **Mehrere** | **True** | Ermittelt, wenn sich mehrere Anweisungen in derselben Zeile befinden. |
| **Semikolons** | **True** | Ermittelt die Verwendung von Semikolons. |

## <a name="text-group"></a>Gruppe „Text“

| Option | Standardwert | Lint-Effekt |
| --- | --- | --- |
| **Grenzwert für Zeilenlänge** | **False** | Legt fest, ob der Linter Zeilen markiert, die länger als die Option **Maximale Zeilenlänge** sind. |
| **Maximale Zeilenlänge** | **80** | Legt die Zeilenlänge fest, die durch die Option **Grenzwert für Zeilenlänge** zugewiesen wird. |

## <a name="whitespace-group"></a>Gruppe „Leerraum“

Diese Optionen, die alle standardmäßig auf **TRUE** festgelegt sind, steuern, wo der Linter Leerraumprobleme ermittelt: Verwendung von Tabulatoren, Verwendung von doppelten Anführungszeichen, nachstehende leere Zeilen und nachstehender Leerraum.