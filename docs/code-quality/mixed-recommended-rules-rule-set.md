---
title: Regelsatz für gemischte empfohlene Mindestregeln
ms.date: 11/04/2016
description: Erfahren Sie mehr über den gemischten Regel Satz für empfohlene Regeln in Visual Studio. Siehe Beschreibungen von Regeln für C++-Projekte, die die Common Language Runtime unterstützen.
ms.custom: SEO-VS-2020
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bc30012dc025c5fc92f6d589c8e40740d689a86b
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94437069"
---
# <a name="mixed-recommended-rules-rule-set"></a>Regelsatz für gemischte empfohlene Mindestregeln

Die gemischten empfohlenen Regeln von Microsoft konzentrieren sich auf die häufigsten und wichtigsten Probleme in Ihren C++-Projekten, die die Common Language Runtime unterstützen, einschließlich möglicher Sicherheitslücken, Anwendungs Abstürze und anderer wichtiger Logik-und Entwurfs Fehler. Dieser Regelsatz enthält alle Regeln im Regelsatz für [gemischte Mindestregeln](mixed-minimum-rules-rule-set.md) .

Fügen Sie diesen Regelsatz in einen benutzerdefinierten Regelsatz ein, den Sie für Ihre C++-Projekte erstellen, die die Common Language Runtime unterstützen.

|Regel|Beschreibung|
|----------|-----------------|
|[C6001](/cpp/code-quality/c6001)|Nicht initialisierter Speicher wird verwendet|
|[C6011](/cpp/code-quality/c6011)|Dereferenzierender NULL-Zeiger|
|[C6029](/cpp/code-quality/c6029)|Verwendung von ungeprüftem Wert|
|[C6031](/cpp/code-quality/c6031)|Rückgabewert wird ignoriert.|
|[C6053](/cpp/code-quality/c6053)|0 (null)-Abbruch des Aufrufs|
|[C6054](/cpp/code-quality/c6054)|Keine Beendigung fehlt.|
|[C6059](/cpp/code-quality/c6059)|Fehlerhafte Verkettung|
|[C6063](/cpp/code-quality/c6063)|Fehlendes Zeichenfolgenargument für Formatfunktion|
|[C6064](/cpp/code-quality/c6064)|Fehlendes Ganzzahlargument für Formatfunktion|
|[C6066](/cpp/code-quality/c6066)|Fehlendes Zeigerargument für Formatfunktion|
|[C6067](/cpp/code-quality/c6067)|Fehlendes Zeichenfolgenzeigerargument für Formatfunktion|
|[C6101](/cpp/code-quality/c6101)|Rückgabe von nicht initialisiertem Speicher|
|[C6200](/cpp/code-quality/c6200)|Index überschreitet maximale Puffergröße|
|[C6201](/cpp/code-quality/c6201)|Index überschreitet maximale Puffergröße|
|[C6214](/cpp/code-quality/c6214)|Ungültige Umwandlung von HRESULT in bool|
|[C6215](/cpp/code-quality/c6215)|Ungültige Umwandlung von bool in HRESULT.|
|[C6216](/cpp/code-quality/c6216)|Ungültige Compiler-Inserted Umwandlung von bool in HRESULT|
|[C6217](/cpp/code-quality/c6217)|Ungültiger HRESULT-Test mit Not|
|[C6220](/cpp/code-quality/c6220)|Ungültiger HRESULT-Vergleich mit-1.|
|[C6226](/cpp/code-quality/c6226)|Ungültige HRESULT-Zuweisung zu-1.|
|[C6230](/cpp/code-quality/c6230)|Ungültige HRESULT-Verwendung als boolescher Wert.|
|[C6235](/cpp/code-quality/c6235)|Konstante ungleich 0 (null) mit Logical-Or|
|[C6236](/cpp/code-quality/c6236)|Logical-Or mit konstanter Konstante|
|[C6237](/cpp/code-quality/c6237)|NULL, wenn Logical-And Nebeneffekte verliert|
|[C6242](/cpp/code-quality/c6242)|Lokale Entladung erzwungen|
|[C6248](/cpp/code-quality/c6248)|Erstellen einer NULL-DACL|
|[C6250](/cpp/code-quality/c6250)|Nicht freigegebene Adress Deskriptoren|
|[C6255](/cpp/code-quality/c6255)|Ungeschützte Verwendung von "Zuweisung"|
|[C6258](/cpp/code-quality/c6258)|Verwenden des Beendigungs Threads|
|[C6259](/cpp/code-quality/c6259)|Unzustellbaren Code in Bitwise-Or eingeschränkten Switch|
|[C6260](/cpp/code-quality/c6260)|Verwendung von Byte-Arithmetik|
|[C6262](/cpp/code-quality/c6262)|Übermäßige Stapel Verwendung|
|[C6263](/cpp/code-quality/c6263)|Verwenden von "Zuweisung in Schleife"|
|[C6268](/cpp/code-quality/c6268)|Fehlende Klammern in Umwandlung|
|[C6269](/cpp/code-quality/c6269)|Zeiger Dereferenzierung wird ignoriert.|
|[C6270](/cpp/code-quality/c6270)|Fehlendes Gleitkommaargument für Formatfunktion|
|[C6271](/cpp/code-quality/c6271)|Zusätzliches Argument für Formatfunktion|
|[C6272](/cpp/code-quality/c6272)|Nicht-Gleitkommaargument für Formatfunktion|
|[C6273](/cpp/code-quality/c6273)|Nicht-Ganzzahlargument für Formatfunktion|
|[C6274](/cpp/code-quality/c6274)|Nicht-Zeichenargument für Formatfunktion|
|[C6276](/cpp/code-quality/c6276)|Ungültige Zeichenfolgenumwandlung|
|[C6277](/cpp/code-quality/c6277)|Ungültiger CreateProcess-Aufruf|
|[C6278](/cpp/code-quality/c6278)|Array-New Scalar-Delete stimmen nicht überein.|
|[C6279](/cpp/code-quality/c6279)|Scalar-New Array-Delete stimmen nicht überein.|
|[C6280](/cpp/code-quality/c6280)|Nicht übereinstimmender Arbeitsspeicher Allocation-Deallocation|
|[C6281](/cpp/code-quality/c6281)|Bitweise Beziehungs Rangfolge|
|[C6282](/cpp/code-quality/c6282)|Zuweisung ersetzt Test|
|[C6283](/cpp/code-quality/c6283)|Primitive Array-New Scalar-Delete nicht übereinstimmende|
|[C6284](/cpp/code-quality/c6284)|Ungültiges Objekt-Argument für Formatfunktion|
|[C6285](/cpp/code-quality/c6285)|Logical-Or von Konstanten|
|[C6286](/cpp/code-quality/c6286)|Logical-Or ungleich 0 (null), ohne Nebeneffekte zu verlieren|
|[C6287](/cpp/code-quality/c6287)|Redundanter Test|
|[C6288](/cpp/code-quality/c6288)|Die gegenseitige Einbindung über Logical-And ist false.|
|[C6289](/cpp/code-quality/c6289)|Gegenseitiger Ausschluss über Logical-Or ist "true"|
|[C6290](/cpp/code-quality/c6290)|Logischer NOT-Operator hat Vorrang gegenüber bitweisem AND-Operator|
|[C6291](/cpp/code-quality/c6291)|Logischer NOT-Operator hat Vorrang gegenüber bitweisem OR-Operator|
|[C6292](/cpp/code-quality/c6292)|Schleife zählt vom Maximum nach oben|
|[C6293](/cpp/code-quality/c6293)|Schleife zählt vom Minimalbetrag|
|[C6294](/cpp/code-quality/c6294)|Schleifen Text wurde nie ausgeführt.|
|[C6295](/cpp/code-quality/c6295)|Unendliche Schleife|
|[C6296](/cpp/code-quality/c6296)|Schleife wird nur einmal ausgeführt|
|[C6297](/cpp/code-quality/c6297)|Ergebnis der UMSCHALT Umwandlung in eine größere Größe|
|[C6299](/cpp/code-quality/c6299)|Bitfeld zu booleschem Vergleich|
|[C6302](/cpp/code-quality/c6302)|Ungültiges Zeichenfolgenargument für Formatfunktion|
|[C6303](/cpp/code-quality/c6303)|Ungültiges Zeichenfolgenargument für breite Zeichen zu Formatfunktion|
|[C6305](/cpp/code-quality/c6305)|Keine Übereinstimmung bei Größe und Count-Verwendung|
|[C6306](/cpp/code-quality/c6306)|Falscher Variablenargument-Funktionsaufruf|
|[C6308](/cpp/code-quality/c6308)|Rezuweisung-Leck|
|[C6310](/cpp/code-quality/c6310)|Ungültige Ausnahme Filter Konstante|
|[C6312](/cpp/code-quality/c6312)|Ausnahme Ausführungs Schleife fortsetzen|
|[C6314](/cpp/code-quality/c6314)|Bitwise-Or Rangfolge|
|[C6317](/cpp/code-quality/c6317)|Nicht Komplement|
|[C6318](/cpp/code-quality/c6318)|Ausnahme Suche fortsetzen|
|[C6319](/cpp/code-quality/c6319)|Durch Komma ignoriert|
|[C6324](/cpp/code-quality/c6324)|Zeichen folgen Kopie anstelle von Zeichen folgen Vergleich|
|[C6328](/cpp/code-quality/c6328)|Möglicher Argumenttypenkonflikt|
|[C6331](/cpp/code-quality/c6331)|Ungültige VirtualFree-Flags|
|[C6332](/cpp/code-quality/c6332)|Ungültiger VirtualFree-Parameter|
|[C6333](/cpp/code-quality/c6333)|Ungültige VirtualFree-Größe|
|[C6335](/cpp/code-quality/c6335)|Verlust des Prozess Handles|
|[C6381](/cpp/code-quality/c6381)|Informationen zum Herunterfahren fehlen|
|[C6383](/cpp/code-quality/c6383)|Element-Count Byte-Count Pufferüberlauf|
|[C6384](/cpp/code-quality/c6384)|Zeigergrößendivision|
|[C6385](/cpp/code-quality/c6385)|Leseüberlauf|
|[C6386](/cpp/code-quality/c6386)|Schreibüberlauf|
|[C6387](/cpp/code-quality/c6387)|Ungültiger Parameterwert|
|[C6388](/cpp/code-quality/c6388)|Ungültiger Parameterwert|
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
|[C6995](/cpp/code-quality/c6995)|Fehler beim Speichern der XML-Protokolldatei.|
|[C26100](/cpp/code-quality/c26100)|Racebedingung|
|[C26101](/cpp/code-quality/c26101)|Fehler bei der ordnungsgemäßen Verwendung des Interlocked-Vorgangs.|
|[C26110](/cpp/code-quality/c26110)|Fehler des Aufrufers bei der Sperre|
|[C26111](/cpp/code-quality/c26111)|Fehler beim Freigeben der Sperre|
|[C26112](/cpp/code-quality/c26112)|Der Aufrufer kann keine Sperre enthalten|
|[C26115](/cpp/code-quality/c26115)|Fehler beim Freigeben der Sperre.|
|[C26116](/cpp/code-quality/c26116)|Fehler beim Abrufen oder Speichern der Sperre.|
|[C26117](/cpp/code-quality/c26117)|Aufheben der nicht gehaltenen Sperre|
|[C26140](/cpp/code-quality/c26140)|Nebenläufigkeitsfehler bei SAL-Anmerkung.|
|[C28020](/cpp/code-quality/c28020)|Der Ausdruck ist bei diesem Befehl nicht "true".|
|[C28021](/cpp/code-quality/c28021)|Der Parameter, der mit Anmerkungen versehen ist, muss ein Zeiger sein.|
|[C28022](/cpp/code-quality/c28022)|Die Funktionsklassen in dieser Funktion stimmen nicht mit den Funktionsklassen in der typedef, die zum Definieren der Funktion verwendet wird, ab.|
|[C28023](/cpp/code-quality/c28023)|Die Funktion, die zugewiesen oder übermittelt wird, sollte über eine \_ Funktions \_ Klassen \_ Anmerkung für mindestens eine der Klassen (es) verfügen.|
|[C28024](/cpp/code-quality/c28024)|Der Funktionszeiger, der zugewiesen wird, wird mit der Funktionsklasse kommentiert, die nicht in der Liste der Funktionsklassen enthalten ist.|
|[C28039](/cpp/code-quality/c28039)|Der Typ des tatsächlichen Parameters sollte genau mit dem Typ übereinstimmen.|
|[C28112](/cpp/code-quality/c28112)|Auf eine Variable, auf die über eine Interlocked-Funktion zugegriffen wird, muss immer über eine Interlocked-Funktion zugegriffen werden.|
|[C28113](/cpp/code-quality/c28113)|Zugreifen auf eine lokale Variable über eine Interlocked-Funktion|
|[C28125](/cpp/code-quality/c28125)|Die Funktion muss innerhalb eines try/with-Blocks aufgerufen werden.|
|[C28137](/cpp/code-quality/c28137)|Das Variablen Argument sollte stattdessen eine (Literale) Konstante sein.|
|[C28138](/cpp/code-quality/c28138)|Das Constant-Argument sollte stattdessen eine Variable sein.|
|[C28159](/cpp/code-quality/c28159)|Verwenden Sie stattdessen ggf. eine andere Funktion.|
|[C28160](/cpp/code-quality/c28160)|Fehleranmerkung|
|[C28163](/cpp/code-quality/c28163)|Die Funktion sollte nie innerhalb eines try/with-Blocks aufgerufen werden.|
|[C28164](/cpp/code-quality/c28164)|Das Argument wird an eine Funktion übermittelt, die einen Zeiger auf ein Objekt erwartet (kein Zeiger auf einen Zeiger).|
|[C28182](/cpp/code-quality/c28182)|Dereferenzierender NULL-Zeiger. Der Zeit enthält denselben NULL-Wert wie ein anderer Zeiger.|
|[C28183](/cpp/code-quality/c28183)|Das Argument könnte ein Wert sein und eine Kopie des im Zeiger gefundenen Werts sein.|
|[C28193](/cpp/code-quality/c28193)|Die Variable enthält einen Wert, der untersucht werden muss.|
|[C28196](/cpp/code-quality/c28196)|Die Anforderung wird nicht erfüllt. (Der Ausdruck wird nicht mit "True" ausgewertet.)|
|[C28202](/cpp/code-quality/c28202)|Illegaler Verweis auf nicht statischen Member|
|[C28203](/cpp/code-quality/c28203)|Mehrdeutiger Verweis auf Klassenmember.|
|[C28205](/cpp/code-quality/c28205)|\_Erfolg \_ oder \_ bei fehlgeschlagener \_ \_ Verwendung in unzulässigem Kontext|
|[C28206](/cpp/code-quality/c28206)|„->“ verwenden, wenn linker Operand auf eine Struktur zeigt|
|[C28207](/cpp/code-quality/c28207)|„.“ verwenden, wenn linker Operand eine Struktur ist|
|[C28209](/cpp/code-quality/c28209)|Die Deklaration für das Symbol hat eine widersprüchliche Deklaration.|
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
|[C28244](/cpp/code-quality/c28244)|Die Anmerkung für die Funktion verfügt über einen nicht parameterbaren Parameter/eine externe Anmerkung.|
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
|[C28306](/cpp/code-quality/c28306)|Die Anmerkung für den Parameter ist veraltet.|
|[C28307](/cpp/code-quality/c28307)|Die Anmerkung für den Parameter ist veraltet.|
|[C28350](/cpp/code-quality/c28350)|Die Anmerkung beschreibt eine Situation, die nicht bedingt anwendbar ist.|
|[C28351](/cpp/code-quality/c28351)|Die Anmerkung beschreibt, wo ein dynamischer Wert (eine Variable) in der Bedingung nicht verwendet werden darf.|
|[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001)|Typen, die löschbare Felder besitzen, müssen gelöscht werden können.|
|[CA1009](../code-quality/ca1009.md)|Ereignishandler korrekt deklarieren.|
|[CA1016](/dotnet/fundamentals/code-analysis/quality-rules/ca1016)|Assemblys mit AssemblyVersionAttribute markieren.|
|[CA1033](/dotnet/fundamentals/code-analysis/quality-rules/ca1033)|Schnittstellenmethoden sollten von untergeordneten Typen aufgerufen werden können.|
|[CA1049](../code-quality/ca1049.md)|Typen, die native Ressourcen besitzen, müssen gelöscht werden können.|
|[CA1060](/dotnet/fundamentals/code-analysis/quality-rules/ca1060)|P/Invokes in NativeMethods-Klasse verschieben.|
|[CA1061](/dotnet/fundamentals/code-analysis/quality-rules/ca1061)|Basisklassenmethoden nicht ausblenden.|
|[CA1063](/dotnet/fundamentals/code-analysis/quality-rules/ca1063)|IDisposable korrekt implementieren.|
|[CA1065](/dotnet/fundamentals/code-analysis/quality-rules/ca1065)|Keine Ausnahmen an unerwarteten Speicherorten auslösen.|
|[CA1301](../code-quality/ca1301.md)|Doppelte Zugriffstasten vermeiden.|
|[CA1400](../code-quality/ca1400.md)|Für P/Invoke müssen Einstiegspunkte vorhanden sein.|
|[CA1401](/dotnet/fundamentals/code-analysis/quality-rules/ca1401)|P/Invokes dürfen nicht sichtbar sein.|
|[CA1403](../code-quality/ca1403.md)|Typen mit automatischem Layout sollten nicht für COM sichtbar sein.|
|[CA1404](../code-quality/ca1404.md)|GetLastError unmittelbar nach P/Invoke aufrufen.|
|[CA1405](../code-quality/ca1405.md)|Für COM sichtbare Basistypen sollten für COM sichtbar sein.|
|[CA1410](../code-quality/ca1410.md)|Die COM-Registrierungsmethoden müssen übereinstimmen.|
|[CA1415](../code-quality/ca1415.md)|P/Invokes korrekt deklarieren.|
|[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821)|Leere Finalizer entfernen.|
|[CA1900](../code-quality/ca1900.md)|Werttypfelder sollten portabel sein.|
|[CA1901](../code-quality/ca1901.md)|Deklarationen von P/Invoke müssen portabel sein.|
|[CA2002](/dotnet/fundamentals/code-analysis/quality-rules/ca2002)|Auf Objekten mit schwacher Identität nicht sperren.|
|[CA2100](/dotnet/fundamentals/code-analysis/quality-rules/ca2100)|SQL-Abfragen auf Sicherheitsrisiken überprüfen.|
|[CA2101](/dotnet/fundamentals/code-analysis/quality-rules/ca2101)|Marshalling für P/Invoke-Zeichenfolgenargumente festlegen.|
|[CA2108](../code-quality/ca2108.md)|Deklarative Sicherheit auf Werttypen überprüfen.|
|[CA2111](../code-quality/ca2111.md)|Zeiger sollten nicht sichtbar sein.|
|[CA2112](../code-quality/ca2112.md)|Gesicherte Typen sollten keine Felder verfügbar machen.|
|[CA2114](../code-quality/ca2114.md)|Methodensicherheit sollte Superset des Typs sein.|
|[CA2116](../code-quality/ca2116.md)|APTCA-Methoden sollten nur APTCA-Methoden aufrufen.|
|[CA2117](../code-quality/ca2117.md)|APTCA-Typen sollten nur APTCA-Basistypen erweitern.|
|[CA2122](../code-quality/ca2122.md)|Methoden mit Linkaufrufen nicht indirekt verfügbar machen.|
|[CA2123](../code-quality/ca2123.md)|Überschreibungslinkaufrufe sollten mit der Basis identisch sein.|
|[CA2124](../code-quality/ca2124.md)|Anfällige finally-Klauseln mit äußerem try-Block umschließen.|
|[CA2126](../code-quality/ca2126.md)|Typlinkaufrufe erfordern Vererbungsanforderungen.|
|[CA2131](../code-quality/ca2131.md)|Sicherheitskritische Typen dürfen nicht an Typäquivalenz beteiligt sein.|
|[CA2132](../code-quality/ca2132.md)|Standardkonstruktoren müssen mindestens so kritisch sein wie die Standardkonstruktoren des Basistyps.|
|[CA2133](../code-quality/ca2133.md)|Delegaten müssen an Methoden mit konsistenter Transparenz gebunden werden.|
|[CA2134](../code-quality/ca2134.md)|Methoden müssen beim Überschreiben von Basismethoden eine konsistente Transparenz wahren.|
|[CA2137](../code-quality/ca2137.md)|Transparente Methoden dürfen nur überprüfbare IL enthalten.|
|[CA2138](../code-quality/ca2138.md)|Transparente Methoden dürfen keine Methoden mit dem SuppressUnmanagedCodeSecurity-Attribut aufrufen.|
|[CA2140](../code-quality/ca2140.md)|Transparenter Code darf nicht auf sicherheitskritische Elemente verweisen.|
|[CA2141](../code-quality/ca2141.md)|Transparente Methoden dürfen keine LinkDemand-Anforderungen erfüllen.|
|[CA2146](../code-quality/ca2146.md)|Typen müssen mindestens genauso kritisch sein wie ihre Basistypen und Schnittstellen.|
|[CA2147](../code-quality/ca2147.md)|Transparente Methoden dürfen keine Sicherheitsassertionen verwenden.|
|[CA2149](../code-quality/ca2149.md)|Transparente Methoden dürfen keine Aufrufe in nativen Code durchführen.|
|[CA2200](/dotnet/fundamentals/code-analysis/quality-rules/ca2200)|Erneut ausführen, um Stapeldetails beizubehalten.|
|[CA2202](../code-quality/ca2202.md)|Objekte nicht mehrmals verwerfen.|
|[CA2207](/dotnet/fundamentals/code-analysis/quality-rules/ca2207)|Statische Felder für Werttyp inline initialisieren.|
|[CA2212](../code-quality/ca2212.md)|ServicedComponents nicht mit WebMethod markieren.|
|[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213)|Verwerfbare Felder verwerfen.|
|[CA2214](/dotnet/fundamentals/code-analysis/quality-rules/ca2214)|Überschreibbare Methoden in Konstruktoren nicht aufrufen.|
|[CA2216](/dotnet/fundamentals/code-analysis/quality-rules/ca2216)|Verwerfbare Typen sollten einen Finalizer deklarieren.|
|[CA2220](../code-quality/ca2220.md)|Finalizer sollten Basisklassen-Finalizer aufrufen.|
|[CA2229](/dotnet/fundamentals/code-analysis/quality-rules/ca2229)|Serialisierungskonstruktoren implementieren.|
|[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231)|Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals.|
|[CA2232](../code-quality/ca2232.md)|Windows Forms-Einstiegspunkte mit STAThread markieren.|
|[CA2235](/dotnet/fundamentals/code-analysis/quality-rules/ca2235)|Alle nicht serialisierbaren Felder markieren.|
|[CA2236](../code-quality/ca2236.md)|Basisklassenmethoden auf ISerializable-Typen aufrufen.|
|[CA2237](/dotnet/fundamentals/code-analysis/quality-rules/ca2237)|ISerializable-Typen mit SerializableAttribute markieren.|
|[CA2238](../code-quality/ca2238.md)|Serialisierungsmethoden korrekt implementieren.|
|[CA2240](../code-quality/ca2240.md)|ISerializable ordnungsgemäß implementieren.|
|[CA2241](/dotnet/fundamentals/code-analysis/quality-rules/ca2241)|Geben Sie die korrekte Anzahl für Formatierungsmethoden an.|
|[CA2242](/dotnet/fundamentals/code-analysis/quality-rules/ca2242)|Ordnungsgemäß auf NaN testen.|