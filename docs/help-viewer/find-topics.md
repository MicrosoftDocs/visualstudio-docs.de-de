---
title: Suchen von Themen (Help Viewer)
description: Erfahren Sie, wie Sie in der Microsoft Help Viewer nach Themen suchen. Anpassen von Such Vorgängen mithilfe von Platzhalter Ausdrücken, logischen Operatoren und erweiterten Such Operatoren.
ms.date: 11/02/2017
ms.topic: how-to
ms.assetid: 683f1b0c-1551-4bba-91fe-3855f03fdd69
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4ebf3bbd1fe04b13f31de7ebd8c513de670dd480
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944133"
---
# <a name="how-to-search-for-topics"></a>Vorgehensweise: Suchen nach Themen

Mit der Volltextsuche können Sie alle Themen suchen, die ein bestimmtes Wort enthalten. Sie haben außerdem die Möglichkeit, die Suche mithilfe von Platzhalterausdrücken, logischen Operatoren und erweiterten Suchoperatoren einzugrenzen und anzupassen.

Klicken Sie im **Help Viewer**-Fenster auf die Registerkarte **Suche**, oder drücken Sie **STRG**+**E**, wenn Sie eine Tastatur benutzen, um die Registerkarte **Suche** zu öffnen.

## <a name="to-perform-a-full-text-search"></a>So führen Sie eine Volltextsuche aus

1. Geben Sie in das Suchfeld das Wort ein, nach dem Sie suchen möchten.

2. Falls Sie logische oder erweiterte Suchoperatoren verwenden, geben Sie in der Abfrage an, um welche es sich dabei handelt. Verwenden Sie jedoch keine Operatoren, um die verfügbare Hilfe zu durchsuchen.

    > [!NOTE]
    > Im Dialogfeld **Viewer-Optionen** können Sie zusätzliche Einstellungen angeben, z.B. die maximale Anzahl der Suchergebnisse, die gleichzeitig angezeigt werden sollen, oder ob englischsprachige Inhalte enthalten sein dürfen, wenn das primäre Gebietsschema nicht Englisch ist.

3. Drücken Sie die **EINGABETASTE**.

     Eine Suche gibt standardmäßig maximal 200 Treffer zurück. Diese werden im Suchergebnisbereich angezeigt. Je nach Inhalt werden möglicherweise zusätzliche Versionsinformationen zu jedem Treffer angezeigt.

4. Um sich ein Thema anzeigen zu lassen, klicken Sie in der Ergebnisliste auf den Titel.

## <a name="full-text-search-tips"></a>Tipps für die Volltextsuche

Sie können zielgerichtetere Suchen durchführen, die nur die für Sie interessanten Themen zurückgeben, wenn Sie wissen, wie die Syntax die Abfrage beeinflusst. Die Syntax enthält Sonderzeichen, reservierte Wörter und Filter. Dieses Thema stellt Tipps, Vorgehensweisen und detaillierte Syntaxinformationen vor, mit denen Sie bessere Abfragen erstellen können.

### <a name="general-guidelines"></a>Allgemeine Richtlinien

Die folgende Tabelle enthält einige einfache Regeln und Richtlinien für das Entwickeln von Suchabfragen in der Hilfe.

|Syntax|BESCHREIBUNG|
|------------|-----------------|
|Groß- und Kleinschreibung|Groß-/Kleinschreibung wird bei Suchvorgängen nicht beachtet. Entwickeln Sie Ihre Suchkriterien mit Groß-oder Kleinbuchstaben. Beispielsweise werden für „OLE“ und „ole“ die gleichen Ergebnisse zurückgegeben.|
|Zeichenkombinationen|Sie können nicht nur nach einzelnen Buchstaben (a–z) oder Ziffern (0–9) suchen. Wenn Sie versuchen, nach bestimmten reservierten Wörtern wie „und“, „von“ und „mit“ zu suchen, werden diese ignoriert. Weitere Informationen finden Sie unter [Bei der Suche ignorierte Wörter (Stoppwörter)](#stopwords) weiter unten in diesem Thema.|
|Auswertungsreihenfolge|Suchabfragen werden von links nach rechts ausgewertet.|

### <a name="search-syntax"></a>Suchsyntax

Wenn Sie eine Suchzeichenfolge angeben, die mehrere Wörter umfasst, wie etwa „Wort1 Wort2“, ist diese Zeichenfolge äquivalent zu der Eingabe „Wort1 UND Wort2“, die nur Themen zurückgibt, die alle einzelnen Wörter in der Suchzeichenfolge enthalten.

> [!IMPORTANT]
> - Die Suche nach Ausdrücken wird nicht unterstützt. Wenn Sie in einer Suchzeichenfolge mehr als ein Wort angeben, enthalten die zurückgegebenen Themen alle angegebenen Wörter, aber nicht unbedingt genau den Ausdruck, den Sie angegeben haben.
> - Verwenden Sie logische Operatoren, um die Beziehung zwischen den Wörtern in Ihrem Suchausdruck anzugeben. Sie können logische Operatoren, wie etwa UND, ODER, NICHT und NAH eingeben, um Ihre Suche weiter einzugrenzen. Wenn Sie beispielsweise nach „Deklarieren NAH Vereinigungsmenge“ suchen, enthalten die Suchergebnisse Themen, die die Wörter „Deklarieren“ und „Vereinigungsmenge“ durch nicht mehr als ein paar Wörter getrennt enthalten. Weitere Informationen finden Sie unter [Logische Operatoren in Suchausdrücken](../help-viewer/logical-operators-search-expressions.md).

### <a name="filters"></a>Filter

Sie können die Suchergebnisse weiter eingrenzen, indem Sie erweiterte Suchoperatoren verwenden. Die Hilfe enthält drei Kategorien, die Sie zum Filtern von Ergebnissen einer Volltextsuche verwenden können: Titel, Code und Schlüsselwort.

### <a name="ranking-of-search-results"></a>Rangfolge von Suchergebnissen

Der Suchalgorithmus wendet bestimmte Kriterien an, um einen höheren oder niedrigeren Rang von Suchergebnissen in der Ergebnisliste auszuweisen. Im Allgemeinen:

1. Inhalte, die Suchwörter im Titel enthalten, haben einen höheren Rang als Inhalte, auf die das nicht zutrifft.

2. Inhalte die Suchwörter in großer Nähe zueinander enthalten, erhalten einen höheren Rang als Inhalte, auf die das nicht zugrifft.

3. Inhalte, die eine höhere Dichte der Suchwörter aufweisen, erhalten einen höheren Rang als Inhalte mit einer geringeren Dichte der Suchwörter.

### <a name=""></a><a name="stopwords"> Bei der Suche ignorierte Wörter (Stoppwörter) </a>

Häufig auftretende Wörter oder Ziffern, die manchmal als Stoppwörter bezeichnet werden, werden bei der Volltextsuche automatisch ignoriert. Wenn Sie beispielsweise nach dem Ausdruck „übergeben durch“ suchen, zeigen die Suchergebnisse Themen an, die das Wort „übergeben“ enthalten, ignorieren aber das Wort „durch“.

## <a name="see-also"></a>Weitere Informationen

- [Logische Operatoren in Suchausdrücken](../help-viewer/logical-operators-search-expressions.md)
- [Gewusst wie: Suchen von Themen im Index](../help-viewer/find-topics-index.md)
- [Gewusst wie: Suchen nach Themen im Inhaltsverzeichnis](../help-viewer/find-topics-toc.md)
- [Microsoft Help Viewer](../help-viewer/overview.md)