---
title: Regelsatz für gemischte Mindestregeln
ms.date: 11/04/2016
description: Erfahren Sie mehr über den gemischten Regelsatz für Mindestregeln in Visual Studio. Siehe Beschreibungen von Regeln für C++-Projekte, die die Common Language Runtime unterstützen.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: bc8df61c-19af-40ab-a871-315807e5f4bf
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 54ba61f3d4f82a5db25d0079193955a5569afa8a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867879"
---
# <a name="mixed-minimum-rules-rule-set"></a>Regelsatz für gemischte Mindestregeln

Die gemischten minimal Regeln von Microsoft konzentrieren sich auf die kritischsten Probleme in C++-Projekten, die die Common Language Runtime unterstützen, einschließlich potenzieller Sicherheitslücken und Anwendungs Abstürze.

Fügen Sie diesen Regelsatz in einen benutzerdefinierten Regelsatz ein, den Sie für Ihre C++-Projekte erstellen, die die Common Language Runtime unterstützen.

|Regel|Beschreibung|
|----------|-----------------|
|[C6001](/cpp/code-quality/c6001)|Nicht initialisierter Speicher wird verwendet|
|[C6011](/cpp/code-quality/c6011)|Dereferenzierender NULL-Zeiger|
|[C6029](/cpp/code-quality/c6029)|Verwendung von ungeprüftem Wert|
|[C6053](/cpp/code-quality/c6053)|0 (null)-Abbruch des Aufrufs|
|[C6059](/cpp/code-quality/c6059)|Fehlerhafte Verkettung|
|[C6063](/cpp/code-quality/c6063)|Fehlendes Zeichenfolgenargument für Formatfunktion|
|[C6064](/cpp/code-quality/c6064)|Fehlendes Ganzzahlargument für Formatfunktion|
|[C6066](/cpp/code-quality/c6066)|Fehlendes Zeigerargument für Formatfunktion|
|[C6067](/cpp/code-quality/c6067)|Fehlendes Zeichenfolgenzeigerargument für Formatfunktion|
|[C6101](/cpp/code-quality/c6101)|Rückgabe von nicht initialisiertem Speicher|
|[C6200](/cpp/code-quality/c6200)|Index überschreitet maximale Puffergröße|
|[C6201](/cpp/code-quality/c6201)|Index überschreitet maximale Puffergröße|
|[C6270](/cpp/code-quality/c6270)|Fehlendes Gleitkommaargument für Formatfunktion|
|[C6271](/cpp/code-quality/c6271)|Zusätzliches Argument für Formatfunktion|
|[C6272](/cpp/code-quality/c6272)|Nicht-Gleitkommaargument für Formatfunktion|
|[C6273](/cpp/code-quality/c6273)|Nicht-Ganzzahlargument für Formatfunktion|
|[C6274](/cpp/code-quality/c6274)|Nicht-Zeichenargument für Formatfunktion|
|[C6276](/cpp/code-quality/c6276)|Ungültige Zeichenfolgenumwandlung|
|[C6277](/cpp/code-quality/c6277)|Ungültiger CreateProcess-Aufruf|
|[C6284](/cpp/code-quality/c6284)|Ungültiges Objekt-Argument für Formatfunktion|
|[C6290](/cpp/code-quality/c6290)|Logischer NOT-Operator hat Vorrang gegenüber bitweisem AND-Operator|
|[C6291](/cpp/code-quality/c6291)|Logischer NOT-Operator hat Vorrang gegenüber bitweisem OR-Operator|
|[C6302](/cpp/code-quality/c6302)|Ungültiges Zeichenfolgenargument für Formatfunktion|
|[C6303](/cpp/code-quality/c6303)|Ungültiges Zeichenfolgenargument für breite Zeichen zu Formatfunktion|
|[C6305](/cpp/code-quality/c6305)|Keine Übereinstimmung bei Größe und Count-Verwendung|
|[C6306](/cpp/code-quality/c6306)|Falscher Variablenargument-Funktionsaufruf|
|[C6328](/cpp/code-quality/c6328)|Möglicher Argumenttypenkonflikt|
|[C6385](/cpp/code-quality/c6385)|Leseüberlauf|
|[C6386](/cpp/code-quality/c6386)|Schreibüberlauf|
|[C6387](/cpp/code-quality/c6387)|Ungültiger Parameterwert|
|[C6500](/cpp/code-quality/c6500)|Ungültige Attributeigenschaft|
|[C6501](/cpp/code-quality/c6501)|In Konflikt stehende Attributeigenschaftswerte|
|[C6503](/cpp/code-quality/c6503)|Verweise dürfen nicht NULL sein.|
|[C6504](/cpp/code-quality/c6504)|NULL auf Nichtzeiger|
|[C6505](/cpp/code-quality/c6505)|MustCheck für "void"|
|[C6506](/cpp/code-quality/c6506)|Puffergröße auf Nichtzeiger oder Array|
|[C6508](/cpp/code-quality/c6508)|Schreibzugriff auf Konstante|
|[C6509](/cpp/code-quality/c6509)|Rückgabe wurde für Vorbedingung verwendet|
|[C6510](/cpp/code-quality/c6510)|NULL für Nichtzeiger abgebrochen|
|[C6511](/cpp/code-quality/c6511)|MustCheck Muss "Ja" oder "Nein" lauten|
|[C6513](/cpp/code-quality/c6513)|Elementgröße ohne Puffergröße|
|[C6514](/cpp/code-quality/c6514)|Puffergröße übersteigt Arraygröße|
|[C6515](/cpp/code-quality/c6515)|Puffergröße auf Nichtzeiger|
|[C6516](/cpp/code-quality/c6516)|Keine Eigenschaften für Attribut|
|[C6517](/cpp/code-quality/c6517)|Zulässige Größe für nicht lesbaren Puffer|
|[C6518](/cpp/code-quality/c6518)|Schreibbare Größe für Puffer, der nicht geschrieben werden kann|
|[C6522](/cpp/code-quality/c6522)|Ungültiger Größenzeichenfolgentyp|
|[C6525](/cpp/code-quality/c6525)|Ungültiger Größenzeichenfolgenstandort|
|[C6527](/cpp/code-quality/c6527)|Ungültige Anmerkung: Die 'NeedsRelease'-Eigenschaft kann nicht für Werte des void-Typs verwendet werden.|
|[C6530](/cpp/code-quality/c6530)|Unbekannter Formatzeichenfolgenstil|
|[C6540](/cpp/code-quality/c6540)|Bei Verwendung von Attributanmerkungen für diese Funktion werden alle vorhandenen, zugehörigen __declspec-Anmerkungen ungültig|
|[C6551](/cpp/code-quality/c6551)|Ungültige Größenangabe: Ausdruck nicht analysierbar|
|[C6552](/cpp/code-quality/c6552)|Ungültiger Deref= oder Notref=: Ausdruck nicht analysierbar|
|[C6701](/cpp/code-quality/c6701)|Der Wert ist kein gültiger Yes/No/Maybe-Wert|
|[C6702](/cpp/code-quality/c6702)|Der Wert ist kein Zeichenfolgenwert|
|[C6703](/cpp/code-quality/c6703)|Der Wert ist keine Zahl|
|[C6704](/cpp/code-quality/c6704)|Unerwarteter Ausdrucksfehler der Anmerkung|
|[C6705](/cpp/code-quality/c6705)|Erwartete Anzahl von Argumenten für die Anmerkung stimmt nicht mit tatsächlicher Anzahl von Argumenten für die Anmerkung überein|
|[C6706](/cpp/code-quality/c6706)|Unerwarteter Anmerkungsfehler für Anmerkung|
|[C28021](/cpp/code-quality/c28021)|Der Parameter, der mit Anmerkungen versehen ist, muss ein Zeiger sein.|
|[C28182](/cpp/code-quality/c28182)|Dereferenzierender NULL-Zeiger. Der Zeit enthält denselben NULL-Wert wie ein anderer Zeiger.|
|[C28202](/cpp/code-quality/c28202)|Illegaler Verweis auf nicht statischen Member|
|[C28203](/cpp/code-quality/c28203)|Mehrdeutiger Verweis auf Klassenmember.|
|[C28205](/cpp/code-quality/c28205)|\_Erfolg \_ oder \_ bei fehlgeschlagener \_ \_ Verwendung in unzulässigem Kontext|
|[C28206](/cpp/code-quality/c28206)|„->“ verwenden, wenn linker Operand auf eine Struktur zeigt|
|[C28207](/cpp/code-quality/c28207)|„.“ verwenden, wenn linker Operand eine Struktur ist|
|[C28210](/cpp/code-quality/c28210)|Anmerkungen für den _On_failure_-Kontext dürfen sich nicht im expliziten Vorkontext befinden.|
|[C28211](/cpp/code-quality/c28211)|Statischer Kontextname für SAL_context erwartet|
|[C28212](/cpp/code-quality/c28212)|Zeigerausdruck für Anmerkung erwartet|
|[C28213](/cpp/code-quality/c28213)|Die Anmerkung \_ use \_ decl \_ Anmerkungen \_ muss verwendet werden, um eine vorherige Deklaration ohne Änderung zu verweisen.|
|[C28214](/cpp/code-quality/c28214)|Attributparameternamen müssen p1...p9 sein.|
|[C28215](/cpp/code-quality/c28215)|Der Typefix kann nicht auf einen Parameter angewendet werden, der bereits über einen Typefix verfügt.|
|[C28216](/cpp/code-quality/c28216)|Die checkReturn-Anmerkung gilt nur für Nachbedingungen für den bestimmten Funktionsparameter.|
|[C28217](/cpp/code-quality/c28217)|Für die Funktion stimmt die Anzahl der Parameter für die Anmerkung nicht mit der in der Datei gefundenen überein|
|[C28218](/cpp/code-quality/c28218)|Für den Funktionsparameter stimmt der Parameter der Anmerkung nicht mit der in der Datei gefundenen ab.|
|[C28219](/cpp/code-quality/c28219)|Member von Enumeration für den Parameter in der Anmerkung erwartet|
|[C28220](/cpp/code-quality/c28220)|Für den Parameter in der Anmerkung erwarteter Ganzzahlausdruck|
|[C28221](/cpp/code-quality/c28221)|Für den Parameter in der Anmerkung erwarteter Zeichenfolgeausdruck|
|[C28222](/cpp/code-quality/c28222)|__yes, \___no oder \___maybe für die Anmerkung erwartet|
|[C28223](/cpp/code-quality/c28223)|Erwartetes Token/Bezeichner für Anmerkung, Parameter nicht gefunden|
|[C28224](/cpp/code-quality/c28224)|Anmerkung erfordert Parameter|
|[C28225](/cpp/code-quality/c28225)|Korrekte Anzahl erforderlicher Parameter konnten in Anmerkung nicht gefunden werden|
|[C28226](/cpp/code-quality/c28226)|Anmerkung kann nicht zusätzlich ein PrimOp sein (in der aktuellen Deklaration).|
|[C28227](/cpp/code-quality/c28227)|Anmerkung kann nicht zusätzlich ein PrimOp sein (siehe vorherige Deklaration).|
|[C28228](/cpp/code-quality/c28228)|Anmerkungsparameter: Typ kann nicht in Anmerkungen verwendet werden.|
|[C28229](/cpp/code-quality/c28229)|Anmerkung unterstützt keine Parameter.|
|[C28230](/cpp/code-quality/c28230)|Der Parametertyp weist keinen Member auf.|
|[C28231](/cpp/code-quality/c28231)|Anmerkung ist nur im Array gültig.|
|[C28232](/cpp/code-quality/c28232)|Pre, post oder deref wurden auf keine Anmerkung angewendet.|
|[C28233](/cpp/code-quality/c28233)|Pre, post oder deref wurden auf einen Block angewendet.|
|[C28234](/cpp/code-quality/c28234)|_At_-Ausdruck gilt nicht für die aktuelle Funktion.|
|[C28235](/cpp/code-quality/c28235)|Die Funktion kann nicht als Anmerkung alleine stehen.|
|[C28236](/cpp/code-quality/c28236)|Die Anmerkung kann nicht in einem Ausdruck verwendet werden.|
|[C28237](/cpp/code-quality/c28237)|Die Anmerkung zum Parameter wird nicht mehr unterstützt.|
|[C28238](/cpp/code-quality/c28238)|Die Anmerkung zum Parameter verfügt über mehrere Werte vom Typ "value", "stringValue" und "longValue". Verwenden Sie paramn=xxx.|
|[C28239](/cpp/code-quality/c28239)|Für die Anmerkung zum Parameter wurden sowohl value, stringValue oder longValue sowie paramn=xxx definiert. Verwenden Sie nur paramn=xxx.|
|[C28240](/cpp/code-quality/c28240)|Die Anmerkung zum Parameter verfügt über param2, jedoch nicht über param1.|
|[C28241](/cpp/code-quality/c28241)|Die Anmerkung für die Funktion zum Parameter wird nicht erkannt.|
|[C28243](/cpp/code-quality/c28243)|Die Anmerkung für die Funktion zum Parameter erfordert eine größere Anzahl von Dereferenzierungen, als der derzeit angemerkte Typ zulässt.|
|[C28245](/cpp/code-quality/c28245)|Die Anmerkung für die Funktion merkt „this“ in einer Nicht-Member-Funktion an.|
|[C28246](/cpp/code-quality/c28246)|Die Parameteranmerkung für die Funktion stimmt nicht mit dem Parametertyp überein.|
|[C28250](/cpp/code-quality/c28250)|Inkonsistente Anmerkung für die Funktion: die vorherige Instanz weist einen Fehler auf.|
|[C28251](/cpp/code-quality/c28251)|Inkonsistente Anmerkung für die Funktion: diese Instanz weist einen Fehler auf.|
|[C28252](/cpp/code-quality/c28252)|Inkonsistente Anmerkung für die Funktion: der Parameter weist andere Anmerkungen für diese Instanz auf.|
|[C28253](/cpp/code-quality/c28253)|Inkonsistente Anmerkung für die Funktion: der Parameter weist andere Anmerkungen für diese Instanz auf.|
|[C28254](/cpp/code-quality/c28254)|dynamic_cast<>() wird in Anmerkungen nicht unterstützt.|
|[C28262](/cpp/code-quality/c28262)|Ein Syntaxfehler in der Anmerkung wurde in der Funktion für Anmerkung gefunden|
|[C28263](/cpp/code-quality/c28263)|Ein Syntaxfehler in einer bedingten Anmerkung wurde gefunden für systeminterne Anmerkung|
|[C28267](/cpp/code-quality/c28267)|Ein Syntaxfehler in den Anmerkungen wurde in Anmerkung in der Funktion gefunden.|
|[C28272](/cpp/code-quality/c28272)|Die Anmerkung für Funktion, Parameter, beim Untersuchen von ist inkonsistent mit der Funktionsdeklaration.|
|[C28273](/cpp/code-quality/c28273)|Für Funktion sind die Hinweise inkonsistent mit der Funktionsdeklaration.|
|[C28275](/cpp/code-quality/c28275)|Der Parameter für den \_ Makro \_ Wert \_ ist NULL.|
|[C28279](/cpp/code-quality/c28279)|Für Symbol wurde ein 'begin' ohne zugehöriges 'end' gefunden.|
|[C28280](/cpp/code-quality/c28280)|Für Symbol wurde ein 'end' ohne zugehöriges 'begin' gefunden.|
|[C28282](/cpp/code-quality/c28282)|Formatzeichenfolgen müssen sich in Vorbedingungen befinden|
|[C28285](/cpp/code-quality/c28285)|Syntaxfehler im Parameter für Funktion|
|[C28286](/cpp/code-quality/c28286)|Für Funktion wurde ein Syntaxfehler gegen Ende gefunden.|
|[C28287](/cpp/code-quality/c28287)|Syntaxfehler in der Anmerkung \_At()\_ für die Funktion (unbekannter Parametername)|
|[C28288](/cpp/code-quality/c28288)|Syntaxfehler in der Anmerkung \_At()\_ für die Funktion (ungültiger Parametername)|
|[C28289](/cpp/code-quality/c28289)|Für Funktion: ReadableTo oder WritableTo enthielt keine Begrenzungsangabe als Parameter.|
|[C28290](/cpp/code-quality/c28290)|Die Anmerkung für Funktion enthält mehr Externe als die tatsächliche Anzahl von Parametern.|
|[C28291](/cpp/code-quality/c28291)|Post null/notnull auf deref-Ebene 0 ist ohne Bedeutung für Funktion.|
|[C28300](/cpp/code-quality/c28300)|Ausdrucksoperanden von inkompatiblen Typen für Operator|
|[C28301](/cpp/code-quality/c28301)|Keine Anmerkungen für die erste Deklaration der Funktion.|
|[C28302](/cpp/code-quality/c28302)|Ein zusätzlicher \_Deref\_-Operator wurde in der Anmerkung gefunden.|
|[C28303](/cpp/code-quality/c28303)|Ein mehrdeutiger \_Deref\_-Operator wurde in der Anmerkung gefunden.|
|[C28304](/cpp/code-quality/c28304)|Ein falsch platzierter \_Notref\_-Operator wurde gefunden, der auf das Token angewendet wird.|
|[C28305](/cpp/code-quality/c28305)|Fehler beim Analysieren eines Token.|
|[C28350](/cpp/code-quality/c28350)|Die Anmerkung beschreibt eine Situation, die nicht bedingt anwendbar ist.|
|[C28351](/cpp/code-quality/c28351)|Die Anmerkung beschreibt, wo ein dynamischer Wert (eine Variable) in der Bedingung nicht verwendet werden darf.|
|[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001)|Typen, die löschbare Felder besitzen, müssen gelöscht werden können.|
|[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821)|Leere Finalizer entfernen.|
|[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213)|Verwerfbare Felder verwerfen.|
|[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231)|Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals.|