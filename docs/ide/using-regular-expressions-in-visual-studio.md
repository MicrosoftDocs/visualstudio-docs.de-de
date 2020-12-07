---
title: Reguläre Ausdrücke verwenden
description: Hier erfahren Sie mehr über einige Zeichen, Operatoren, Konstrukte und Musterbeispiele, die Sie in Visual Studio für reguläre Ausdrücke verwenden können.
ms.custom: SEO-VS-2020
ms.date: 09/13/2019
ms.topic: conceptual
f1_keywords:
- vsregularexpressionhelp
- vs.regularexpressionhelp
- vs.wildcardsbuilder
- vs.netregularexpressionhelp
- vs.wildcards
helpviewer_keywords:
- regular expressions [Visual Studio]
- regular expressions
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8648eb48c68e0220b1d36a851619edec2b51ceb7
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "96478990"
---
# <a name="use-regular-expressions-in-visual-studio"></a>Verwenden von regulären Ausdrücken in Visual Studio

Visual Studio verwendet [reguläre .NET-Ausdrücke](/dotnet/standard/base-types/regular-expressions) zum Suchen und Ersetzen von Text.

## <a name="regular-expression-examples"></a>Beispiele für reguläre Ausdrücke

Die folgende Tabelle enthält eine Auswahl an Zeichen, Operatoren, Konstrukten und Musterbeispielen für reguläre Ausdrücke. Eine vollständige Referenz finden Sie unter [Sprachelemente für reguläre Ausdrücke](/dotnet/standard/base-types/regular-expression-language-quick-reference).

|Zweck|Ausdruck|Beispiel|
|-------------|----------------|-------------|
|Übereinstimmung mit beliebigem Zeichen (mit Ausnahme des Zeilenumbruchs). Weitere Informationen finden Sie unter [Alle Zeichen](/dotnet/standard/base-types/character-classes-in-regular-expressions#any-character-).|.|`a.o` findet „aro“ in „around“ und „abo“ in „about“, jedoch nicht „acro“ in „across“.|
|Übereinstimmung mit keinem oder mehreren Vorkommen des vorhergehenden Ausdrucks (wobei die Übereinstimmung möglichst viele Zeichen umfasst). Weitere Informationen finden Sie unter [Übereinstimmung mit null oder mehr Vorkommen](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-zero-or-more-times-).|*|`a*r` findet „r“ in „rack“, „ar“ in „ark“ und „aar“ in „aardvark“.|
|Übereinstimmung mit keinem oder mehreren beliebigen Zeichen.|.*|`c.*e` findet „cke“ in „racket“, „comme“ in „comment“ und „code“ in „code“.|
|Übereinstimmung mit einem oder mehreren Vorkommen des vorhergehenden Ausdrucks (wobei die Übereinstimmung möglichst viele Zeichen umfasst). Weitere Informationen finden Sie unter [Übereinstimmung mit null oder mehr Vorkommen](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-one-or-more-times-).|+|`e+d` findet „eed“ in „feeder“ und „ed“ in „faded“.|
|Entspricht einem oder mehreren die oft ausgegebene Befehlszeilen  Zeichen.|.+|`e.+e` findet „eede“ in „feeder“, aber findet keine Übereinstimmung in „feed“.|
|Übereinstimmung mit keinem oder mehreren Vorkommen des vorhergehenden Ausdrucks (wobei die Übereinstimmung möglichst wenig Zeichen umfasst). Weitere Informationen finden Sie unter [Übereinstimmung mit null oder mehr Vorkommen (träger Abgleich)](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-zero-or-more-times-lazy-match-).|*?|`\w*?d` findet „fad“ und „ed“ in „faded“, aber aufgrund eines trägen Abgleichs nicht das ganze Wort „faded“.|
|Übereinstimmung mit einem oder mehreren Vorkommen des vorhergehenden Ausdrucks (wobei die Übereinstimmung möglichst wenig Zeichen umfasst). Weitere Informationen finden Sie unter [Übereinstimmung mit einem oder mehr Vorkommen (träger Abgleich)](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-one-or-more-times-lazy-match-).|+?|`e\w+?` findet „ee“ in „asleep“ und „ed“ in „faded“, aber findet keine Übereinstimmungen in „fade“.|
|Verankert die übereinstimmende Zeichenfolge am [Anfang einer Zeile oder Zeichenfolge](/dotnet/standard/base-types/anchors-in-regular-expressions#start-of-string-or-line-).|^|`^car` findet das Wort „car“ nur, wenn es am Anfang einer Zeile angezeigt wird.|
|Verankert die übereinstimmende Zeichenfolge [am Ende einer Zeile](/dotnet/standard/base-types/anchors-in-regular-expressions#end-of-string-or-line-).|\r?$|`car\r?$` findet „car“ nur, wenn es am Ende einer Zeile angezeigt wird.|
|Verankern der übereinstimmende Zeichenfolge am Ende der Datei|$|`car$` findet „car“ nur, wenn es am Ende der Datei angezeigt wird.|
|Übereinstimmung mit beliebigem Zeichen in einem Satz|[abc]|`b[abc]` findet „ba“, „bb“ und „bc“.|
|Übereinstimmung mit beliebigem Zeichen in einem Bereich von Zeichen|[a-f]|`be[n-t]` findet „bet“ in „between“, „ben“ in „beneath“ und „bes“ in „beside“, aber findet keine Übereinstimmungen in „below“.|
|Erfassung und implizite Nummerierung des in Klammern befindlichen Ausdrucks|()|`([a-z])X\1` findet „aXa“ und „bXb“, jedoch nicht „aXb“. „\1“ bezieht sich auf die erste Ausdrucksgruppe „[a-z]“. Weitere Informationen finden Sie unter [Erfassungsgruppen und Ersetzungsmuster](#capture-groups-and-replacement-patterns). |
|Aufheben der Gültigkeit einer Übereinstimmung|(?!abc)|`real(?!ity)` findet „real“ in „realty“ und „really“, jedoch nicht in „reality“. Findet außerdem das zweite "real" (jedoch nicht das erste "real") in "realityreal".|
|Übereinstimmung mit beliebigem Zeichen, das sich nicht in einem angegebenen Satz von Zeichen befindet. Weitere Informationen finden Sie unter [Negative Zeichengruppe](/dotnet/standard/base-types/character-classes-in-regular-expressions#negative-character-group-).|[^abc]|`be[^n-t]` findet „bef“ in „before“, „beh“ in „behind“ und „bel“ in „below“, aber findet keine Übereinstimmungen in „beneath“.|
|Übereinstimmung mit dem Ausdruck vor oder nach dem Symbol.|&#124;|`(sponge|mud) bath` findet „sponge bath“ und „mud bath“.|
|[Versehen des Zeichens hinter dem umgekehrten Schrägstrich mit Escapezeichen](/dotnet/standard/base-types/character-escapes-in-regular-expressions).| \\ |`\^` findet das Zeichen „^“.|
|Angeben der Anzahl von Vorkommen des vorherigen Zeichens oder der Gruppe. Weitere Informationen finden Sie unter [Übereinstimmung mit genau n Vorkommen](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-exactly-n-times-n).|{n}, wobei n die Anzahl von Vorkommen ist.|`x(ab){2}x` findet „xababx“.<br/>`x(ab){2,3}x` findet „xababx“ und „xabababx“, jedoch nicht „xababababx“.|
|[Übereinstimmung mit Text in einer Unicode-Kategorie](/dotnet/standard/base-types/character-classes-in-regular-expressions#unicode-category-or-unicode-block-p). Weitere Informationen zu Unicode-Zeichenklassen finden Sie unter [Unicode Standard 5.2 Character Properties](http://www.unicode.org/versions/Unicode5.2.0/ch04.pdf).|\p{X}, wobei "X" die Unicode-Nummer angibt.|`\p{Lu}` findet „T“ und „D“ in „Thomas Doe“.|
|[Übereinstimmung mit einer Wortgrenze](/dotnet/standard/base-types/anchors-in-regular-expressions#word-boundary-b)|\b (Außerhalb einer Zeichenklasse gibt `\b` eine Wortgrenze, innerhalb einer Zeichenklasse gibt `\b` eine Rücktaste an.)|`\bin` findet „in“ in „inside“, findet aber keine Übereinstimmungen in „pinto“.|
|Übereinstimmung mit Zeilenumbruch (d.h. ein Wagenrücklaufzeichen gefolgt von einer neuen Zeile).|\r?\n|`End\r?\nBegin` findet „End“ und „Begin“ nur, wenn „End“ die letzte Zeichenfolge in einer Zeile ist und „Begin“ die erste Zeichenfolge in der darauffolgenden Zeile ist.|
|Übereinstimmung mit einem beliebigen [Wortzeichen](/dotnet/standard/base-types/character-classes-in-regular-expressions#word-character-w).|\w|`a\wd` findet „add“ und „a1d“, jedoch nicht „a d“.|
|Übereinstimmung mit [beliebigem Leerzeichen](/dotnet/standard/base-types/character-classes-in-regular-expressions#whitespace-character-s).|\s|`Public\sInterface` findet den Begriff „Public Interface“.|
|Übereinstimmung mit beliebigem [Dezimalzahlzeichen](/dotnet/standard/base-types/character-classes-in-regular-expressions#decimal-digit-character-d).|\d|`\d` findet „4“ und „0“ in „wd40“.|

`\b0[xX]([0-9a-fA-F]+\)\b` ist ein Beispiel für einen regulären Ausdruck, der einige Operatoren und Konstrukte kombiniert, um eine hexadezimale Zahl zu finden. Dieser Ausdruck findet „0xc67f“, aber nicht „0xc67g“.

> [!TIP]
> In Windows-Betriebssystemen enden die meisten Zeilen auf „\r\n“ (ein Wagenrücklaufzeichen gefolgt von einer neuen Zeile). Diese Zeichen sind nicht sichtbar, aber im Editor vorhanden und werden an den .NET-Dienst regulärer Ausdrücke übergeben.

## <a name="capture-groups-and-replacement-patterns"></a>Erfassungsgruppen und Ersetzungsmuster

Eine Erfassungsgruppe beschreibt einen Teilausdruck eines regulären Ausdrucks und erfasst eine Teilzeichenfolge einer Eingabezeichenfolge. Sie können erfasste Gruppen innerhalb des regulären Ausdrucks selbst (z.B. um nach einem wiederholten Wort zu suchen) oder in einem Ersetzungsmuster verwenden. Weitere Informationen finden Sie unter [Gruppierungskonstrukte in regulären Ausdrücken](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions).

Um eine nummerierte Erfassungsgruppe zu erstellen, setzen Sie den Teilausdruck im Muster eines regulären Ausdrucks in Klammern. Erfassungen werden automatisch von links nach rechts nummeriert, und zwar basierend auf der Position der öffnenden Klammer im regulären Ausdruck. So greifen Sie auf die erfasste Gruppe zu

- **im regulären Ausdruck**: Verwenden Sie `\number`. So verweist beispielsweise `\1` im regulären Ausdruck `(\w+)\s\1` auf die erste Erfassungsgruppe `(\w+)`.

- **in einem Ersetzungsmuster**: Verwenden Sie `$number`. Der gruppierte reguläre Ausdruck `(\d)([a-z])` definiert beispielsweise zwei Gruppen: die erste Gruppe enthält eine einzelne Dezimalstelle, und die zweite Gruppe enthält ein einzelnes Zeichen zwischen **a** und **z**. Der Ausdruck findet vier Übereinstimmungen in der folgenden Zeichenfolge: **1a 2b 3c 4d**. Die Ersetzungszeichenfolge `z$1` verweist nur auf die erste Gruppe (`$1`) und konvertiert die Zeichenfolge in **z1 z2 z3 z4**.

Die folgende Abbildung zeigt den regulären Ausdruck `(\w+)\s\1` und die Ersetzungszeichenfolge `$1`. Sowohl der reguläre Ausdruck als auch das Ersetzungsmuster verweisen auf die erste Erfassungsgruppe, die automatisch mit der Nummer 1 versehen wurde. Wenn Sie in Visual Studio im Dialogfeld **Schnellersetzung** auf **Alle ersetzen** klicken, werden wiederholte Wörter aus dem Text entfernt.

![In „Schnellersetzung“ wird eine nummerierte Erfassungsgruppe in Visual Studio gezeigt](media/numbered-capture-group.png)

> [!TIP]
> Vergewissern Sie sich, dass die Schaltfläche **Reguläre Ausdrücke verwenden** im Dialogfeld **Schnellersetzung** ausgewählt ist.

### <a name="named-capture-groups"></a>Benannte Erfassungsgruppen

Anstatt auf die automatische Nummerierung einer Erfassungsgruppe zu vertrauen, können Sie ihr einen Namen geben. Die Syntax für eine benannte Erfassungsgruppe ist `(?<name>subexpression)`.

Benannte Erfassungsgruppen können wie nummerierte Erfassungsgruppen innerhalb des regulären Ausdrucks selbst oder in einem Ersetzungsmuster verwendet werden. So greifen Sie auf die benannte Erfassungsgruppe zu

- **im regulären Ausdruck**: Verwenden Sie `\k<name>`. So verweist beispielsweise `\k<repeated>` im regulären Ausdruck `(?<repeated>\w+)\s\k<repeated>` auf die Erfassungsgruppe, die `repeated` heißt und deren Teilausdruck `\w+` ist.

- **in einem Ersetzungsmuster**: Verwenden Sie `${name}`. Beispiel: `${repeated}`.

Die folgende Abbildung zeigt als Beispiel den regulären Ausdruck `(?<repeated>\w+)\s\k<repeated>` und die Ersetzungszeichenfolge `${repeated}`. Sowohl der reguläre Ausdruck als auch das Ersetzungsmuster verweisen auf Erfassungsgruppe mit dem Namen `repeated`. Wenn Sie in Visual Studio im Dialogfeld **Schnellersetzung** auf **Alle ersetzen** klicken, werden wiederholte Wörter aus dem Text entfernt.

![In „Schnellersetzung“ wird eine genannte Erfassungsgruppe in Visual Studio gezeigt](media/named-capture-group.png)

> [!TIP]
> Vergewissern Sie sich, dass die Schaltfläche **Reguläre Ausdrücke verwenden** im Dialogfeld **Schnellersetzung** ausgewählt ist.

Weitere Informationen zu benannten Erfassungsgruppen finden Sie unter [Benannte übereinstimmende Teilausdrücke](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions#named-matched-subexpressions). Weitere Informationen zu regulären Ausdrücken, die in Ersetzungsmustern verwendet werden, finden Sie unter [Ersetzungen in regulären Ausdrücken](/dotnet/standard/base-types/substitutions-in-regular-expressions).

## <a name="see-also"></a>Siehe auch

- [Sprachelemente für reguläre Ausdrücke](/dotnet/standard/base-types/regular-expression-language-quick-reference)
- [Suchen und Ersetzen von Text](../ide/finding-and-replacing-text.md)
