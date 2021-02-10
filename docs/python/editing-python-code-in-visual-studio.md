---
title: Bearbeiten von Python-Code
description: In Visual Studio stehen für Python umfassende IntelliSense-Funktionen, Codeausschnitte und Navigationsfunktionen sowie Formatierung, Linting und Umgestaltung zur Verfügung.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: fa0caa8184f3c52a010df1dd1f82718d44be700b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888055"
---
# <a name="edit-python-code"></a>Bearbeiten von Python-Code

Da Sie einen Großteil Ihrer Entwicklungszeit im Code-Editor verbringen, bietet [die Python-Unterstützung in Visual Studio](installing-python-support-in-visual-studio.md) Funktionen, die Ihre Produktivität erhöhen. Zu den Funktionen gehören die Syntaxhervorhebung von IntelliSense, die automatische Vervollständigung, Signaturhilfe, Methodenüberschreibungen, die Suche und die Navigation.

Der Editor ist darüber hinaus auch im **interaktiven** Fenster in Visual Studio integriert, sodass der Austausch von Code zwischen den beiden sehr leicht ist. Weitere Informationen finden Sie unter [Tutorial Schritt 3: Verwenden des interaktiven REPL-Fensters](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md) und [Verwenden des interaktiven Fensters: Befehl „An Interactive senden“](python-interactive-repl-in-visual-studio.md#send-to-interactive-command).

Eine allgemeine Dokumentation zur Codebearbeitung in Visual Studio finden Sie unter [Features des Code-Editors](../ide/writing-code-in-the-code-and-text-editor.md). Lesen Sie auch den Artikel [Gliedern](../ide/outlining.md), um sich auf bestimmte Abschnitte Ihres Codes zu konzentrieren.

Sie können darüber hinaus den Visual Studio-**Objektkatalog** (**Ansicht** > **Weitere Fenster** > **Objektkatalog** oder **STRG**+**W** > **J**) verwenden, um die in den einzelnen Modulen definierten Python-Klassen und die in diesen Klassen definierten Funktionen zu überprüfen.

## <a name="intellisense"></a>IntelliSense

IntelliSense bietet [Vervollständigung](#completions), [Signaturhilfe](#signature-help), [QuickInfos](#quick-info) und [Codefarben](#code-coloring). Visual Studio 2017 Version 15.7 und höher unterstützt auch [Typhinweise](#type-hints).

Zur Verbesserung der Leistung nutzt IntelliSense in Visual Studio 2017 Version 15.5 und früher eine Vervollständigungsdatenbank, die für jede Python-Umgebung in Ihrem Projekt generiert wird. Sie müssen Datenbanken möglicherweise aktualisieren, wenn Sie Pakete hinzufügen, entfernen oder aktualisieren. Der Status der Datenbank wird im Fenster **Python-Umgebungen** (dem **Projektmappen-Explorer** gleichgeordnet) auf der Registerkarte **IntelliSense** angezeigt (siehe [Referenz zu den Registerkarten im Fenster „Python-Umgebungen“](python-environments-window-tab-reference.md)).

Visual Studio 2017 Version 15.6 und höher ermöglicht auf andere Weise IntelliSense-Vervollständigungen, die nicht von der Datenbank abhängig sind.

### <a name="completions"></a>Vervollständigungen

Vervollständigungen werden für Anweisungen, Bezeichner oder andere Wörter angezeigt, die an der aktuellen Position im Editor eingegeben werden können. Die in der Liste angezeigten Elemente richten sich nach dem Kontext und werden gefiltert, um falsche oder störende Optionen auszulassen. Vervollständigungen werden häufig durch Eingabe verschiedener Anweisungen (z.B. `import`) und Operatoren (einschließlich eines Punkts) ausgelöst. Sie können sie jedoch auch jederzeit durch Drücken von **STRG**+**J** > **LEERTASTE** anzeigen.

![Membervervollständigung im Visual Studio-Editor](media/code-editing-completions-simple.png)

Wenn eine Vervollständigungsliste geöffnet ist, können Sie mithilfe der Pfeiltasten, der Maus oder durch weitere Eingabe nach der gewünschten Vervollständigung suchen. Je mehr Buchstaben Sie eingeben, desto genauer wird die Liste gefiltert, um wahrscheinliche Vervollständigungen anzuzeigen. Ebenso können Sie diese Tastaturkombinationen verwenden:

- Eingeben von Buchstaben, die sich nicht am Anfang des gesuchten Begriffs befinden, z.B. „parse“ zum Suchen nach „argparse“
- Eingeben von Anfangsbuchstaben, z.B. „abc“ zum Suchen nach „AbstractBaseClass“ oder „air“ zum Suchen nach „as_integer_ratio“
- Auslassen von Buchstaben, z.B. „b64“ zum Suchen nach „base64“

Einige Beispiele:

![Membervervollständigung mit Filterung im Visual Studio-Editor](media/code-editing-completion-filtering.png)

Membervervollständigungen werden automatisch angezeigt, wenn Sie nach einer Variable oder einem Wert einen Punkt zusammen mit dem Methoden und Attributen der möglichen Typen eingeben. Wenn eine Variable mehr als einen Typ aufweisen kann, enthält die Liste alle Möglichkeiten aller Typen und zeigt zusätzliche Informationen dazu an, welche Typen von der jeweiligen Vervollständigung unterstützt werden. Wenn eine Vervollständigung von allen möglichen Typen unterstützt wird, wird sie ohne Anmerkung angezeigt.

![Membervervollständigung für mehrere Typen im Visual Studio-Editor](media/code-editing-completion-types.png)

Standardmäßig werden „dunder“-Member, die mit einem doppelten Unterstrich beginnen und enden, nicht angezeigt. Auf diese Member sollte grundsätzlich nicht direkt zugegriffen werden. Wenn Sie aber einen benötigen, können sie die doppelten Unterstriche vom Anfang eingeben, sodass diese Vervollständigungen der Liste hinzugefügt werden:

![Private Membervervollständigung im Visual Studio-Editor](media/code-editing-completion-dunder.png)

Die Anweisungen `import` und `from ... import` zeigen eine Liste von Modulen an,die importiert werden können. Mit `from ... import` enthält die Liste Member, die aus dem angegebenen Modul importiert werden können.

![Abschluss des Imports im Visual Studio-Editor](media/code-editing-completion-import.png)

Die Anweisungen `raise` und `except` zeigen Listen mit Klassen an, bei denen es sich wahrscheinlich um Fehlertypen handelt. Diese umfasst möglicherweise nicht alle benutzerdefinierten Ausnahmen, hilft Ihnen aber dabei, schnell passende integrierte Ausnahmen zu finden:

![Ausnahmevervollständigung im Visual Studio-Editor](media/code-editing-completion-exception.png)

Die Eingabe von @ startet einen Decorator und zeigt potenzielle Decorators an. Viele dieser Elemente können nicht als Decorator verwendet werden. Schauen Sie in der Dokumentation der Bibliothek nach, um zu ermitteln, welche Elemente Sie verwenden können:

![Decoratorvervollständigung im Visual Studio-Editor](media/code-editing-completion-decorator.png)

> [!Tip]
> Über **Extras** > **Optionen** > **Text-Editor** > **Python** > **Erweitert** können Sie das Verhalten von Vervollständigungen konfigurieren. Einige Beispiele: **Liste basierend auf Suchzeichenfolge filtern** filtert die Vorschläge zur Vervollständigung während der Eingabe (diese Option ist standardmäßig aktiviert). **Membervervollständigung zeigt Schnittmenge der Member an** zeigt nur Vervollständigungen an, die von allen möglichen Typen unterstützt werden (diese Option ist standardmäßig deaktiviert). Informationen finden Sie unter [Optionen: Vervollständigungsergebnisse](python-support-options-and-settings-in-visual-studio.md#completion-results).

### <a name="type-hints"></a>Typhinweise

*Visual Studio 2017 Version 15.7 und höher.*

Bei „Typhinweisen“ in Python 3.5+ ([PEP 484](https://www.python.org/dev/peps/pep-0484/), python.org) handelt es sich um eine Anmerkungssyntax für Funktionen und Klassen, die die Typen der Argumente, Rückgabewerte und Klassenattribute angeben. IntelliSense zeigt Typhinweise an, wenn Sie auf Funktionsaufrufe, Argumente und Variablen zeigen, die diese Anmerkungen aufweisen.

Im folgenden Beispiel ist die `Vector`-Klasse als `List[float]` deklariert, und die `scale`-Funktion enthält Typhinweise sowohl für ihre Argumente als auch für ihren Rückgabewert. Wenn mit dem Mauszeiger auf einen Aufruf dieser Funktion gezeigt wird, werden die Typhinweise angezeigt:

![Zeigen mit dem Mauszeiger auf einen Funktionsaufruf, um Typhinweise offenzulegen](media/code-editing-type-hints1.png)

Im folgenden Beispiel sehen Sie, wie die mit Anmerkungen versehenen Attribute der `Employee`-Klasse im IntelliSense-Vervollständigungspopupfenster für ein Attribut angezeigt werden:

![Anzeigen von Typhinweisen in der IntelliSense-Vervollständigung](media/code-editing-type-hints2.png)

Es ist ferner hilfreich, Typhinweise während Ihres Projekts zu überprüfen, da Fehler üblicherweise erst während der Laufzeit zutage treten. Hierzu integriert Visual Studio das Branchenstandard-Tool „MyPy“ über den Kontextmenübefehl **Python** > **MyPy ausführen** in den **Projektmappen-Explorer**:

![Ausführen des MyPy-Kontextmenübefehls im Projektmappen-Explorer](media/code-editing-type-hints-run-mypy.png)

Beim Ausführen des Befehls werden Sie ggf. aufgefordert, das mypy-Paket zu installieren. Visual Studio führt dann mypy aus, um Typhinweise in allen Python-Dateien im Projekt zu überprüfen. Fehler werden im Fenster **Fehlerliste** von Visual Studio angezeigt. Wenn ein Element im Fenster ausgewählt wird, erfolgt der Sprung zur entsprechenden Zeile in Ihrem Code.

Als einfaches Beispiel enthält die folgende Funktionsdefinition einen Typhinweis, um anzugeben, dass es sich bei dem `input`-Argument um den Typ `str` handelt, während der Aufruf der Funktion versucht, eine ganze Zahl zu übergeben:

```python
def commas_to_colons(input: str):
    items = input.split(',')
    items = [x.strip() for x in items]
    return ':'.join(items)

commas_to_colons(1)
```

Mithilfe des Befehls **Mypy ausführen** für diesen Code wird der folgende Fehler generiert:

![Beispielergebnis für die Mypy-Überprüfung von Typhinweisen](media/code-editing-type-hints-validation-error.png)

::: moniker range="vs-2017"
> [!Tip]
> Für Versionen von Python vor 3.5 zeigt Visual Studio auch Typhinweise an, die Sie über Typeshed-*Stub-Dateien* ( *.pyi*) angeben. Sie können Stub-Dateien immer dann verwenden, wenn Sie Typhinweise nicht direkt in Ihren Code einschließen möchten oder wenn Sie Typhinweise für eine Bibliothek erstellen wollen, die diese nicht direkt verwendet. Weitere Informationen finden Sie unter [Create Stubs for Python Modules (Erstellen von Stubs für Python-Module)](https://github.com/python/mypy/wiki/Creating-Stubs-For-Python-Modules) im Projekt-Wiki für MyPy.
>
> Derzeit unterstützt Visual Studio keine Typhinweise in Kommentaren.
::: moniker-end
::: moniker range=">=vs-2019"
> [!Tip]
> Für Versionen von Python vor 3.5 zeigt Visual Studio auch Typhinweise an, die Sie über Typeshed-*Stub-Dateien* ( *.pyi*) angeben. Sie können Stub-Dateien immer dann verwenden, wenn Sie Typhinweise nicht direkt in Ihren Code einschließen möchten oder wenn Sie Typhinweise für eine Bibliothek erstellen wollen, die diese nicht direkt verwendet. Weitere Informationen finden Sie unter [Create Stubs for Python Modules (Erstellen von Stubs für Python-Module)](https://github.com/python/mypy/wiki/Creating-Stubs-For-Python-Modules) im Projekt-Wiki für MyPy.
>
> Visual Studio enthält gebündelte Typeshed-Dateien für Python 2 und 3. So werden keine zusätzlichen Downloads benötigt. Wenn Sie andere Dateien verwenden möchten, können Sie den Pfad unter **Tools** > **Optionen** > **Python** > **Sprache** angeben. Siehe [Optionen – Sprachserver](python-support-options-and-settings-in-visual-studio.md#language-server-options).
>
> Derzeit unterstützt Visual Studio keine Typhinweise in Kommentaren.
::: moniker-end

### <a name="signature-help"></a>Signaturhilfe

Wenn Sie Code schreiben, der eine Funktion aufruft, wird die Signaturhilfe angezeigt, sobald Sie die öffnende Klammer (`(`) eingeben. Die Signaturhilfe zeigt alle verfügbaren Informationen zu Dokumentation und Parametern an. Sie können die Signaturhilfe auch innerhalb eines Funktionsaufrufs mit **STRG**+**UMSCHALTTASTE**+**LEERTASTE** öffnen. Die angezeigten Informationen hängen von den Dokumentationszeichenfolgen im Quellcode der Funktion ab, enthalten aber alle Standardwerte.

![Signaturhilfe im Visual Studio-Editor.](media/code-editing-signature-help.png)

> [!Tip]
> Um die Signaturhilfe zu deaktivieren, wechseln Sie zu **Extras** > **Optionen** > **Text-Editor** > **Python** > **Allgemein**, und deaktivieren Sie die Option **Anweisungsvervollständigung** > **Parameterinformationen**.

### <a name="quick-info"></a>QuickInfo

Wenn Sie den Mauszeiger über einen Bezeichner bewegen, wird eine QuickInfo angezeigt. Je nach Bezeichner zeigt QuickInfo die möglichen Werte oder Typen, die verfügbare Dokumentation, Rückgabetypen und Definitionsspeicherorte an:

![QuickInfo im Visual Studio-Editor](media/code-editing-quick-info.png)

### <a name="code-coloring"></a>Codefarben

Codefarben verwenden Informationen aus der Codeanalyse, um Variablen, Anweisungen und andere Teile Ihres Codes farbig hervorzuheben. Einige Beispiele: Variablen, die auf Module oder Klassen verweisen, werden in einer anderen Farbe angezeigt als Funktionen oder andere Werte. Parameternamen weisen eine andere Farbe auf als lokale oder globale Variablen: (Funktionen werden standardmäßig nicht fett hervorgehoben):

![Code- und Syntaxfarben im Visual Studio-Editor](media/code-editing-code-coloring.png)

Um die Farben anzupassen, wechseln Sie zu **Extras** > **Optionen** > **Umgebung** > **Schriftarten und Farben**, und bearbeiten Sie die Einträge für **Python** in der Liste **Elemente anzeigen**:

![Optionen für Schriftarten und Farben in Visual Studio](media/code-editing-customize-colors.png)

> [!Tip]
> Um Codefarben zu deaktivieren, wechseln Sie zu **Extras** > **Optionen** > **Text-Editor** > **Python** > **Erweitert**, und deaktivieren Sie die Option **Sonstige Optionen** > **Farbnamen basierend auf Typen**. Siehe [Options - Miscellaneous options (Optionen: Sonstige Optionen)](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options).

## <a name="code-snippets"></a>Codeausschnitte

Codeausschnitte sind Codefragmente, die Sie durch Tastenkombination und Drücken der **TAB**-TASTE in Ihre Dateien einfügen können. Alternativ dazu können Sie die Befehle **Bearbeiten** > **IntelliSense** > **Codeausschnitt einfügen** und **Umgeben mit** verwenden, **Python** und dann den gewünschten Codeausschnitt auswählen.

Beispielsweise ist `class` eine Kurzform für einen Codeausschnitt, der eine Klassendefinition einfügt. Wenn Sie `class` eingeben, sehen Sie, dass der Codeausschnitt in der Liste für automatische Vervollständigung angezeigt wird:

![Codeausschnitt für die Klassenkurzform](media/code-editing-code-snippet-class.png)

Durch Drücken der **TAB**-TASTE wird der Rest der Klasse generiert. Sie können dann in die Namens- und Basisliste schreiben, indem Sie mit der **TAB-TASTE** zwischen den hervorgehobenen Feldern navigieren und dann die **EINGABETASTE** drücken, um mit dem Eingeben des Texts zu beginnen.

![Hervorhebungen von Bereichen eines Codeausschnitts, die Sie vervollständigen können](media/code-editing-code-snippets.png)

### <a name="menu-commands"></a>Menübefehle

Bei Verwendung des Menübefehls **Bearbeiten** > **IntelliSense** > **Codeausschnitt einfügen** wählen Sie zunächst **Python** und dann einen Ausschnitt aus:

![Auswählen eines Codeausschnitts über den Befehl „Codeausschnitt einfügen“](media/code-editing-code-snippet-insert.png)

Der Befehl **Bearbeiten** > **IntelliSense** > **Umgeben mit** platziert auf ähnliche Weise die aktuelle Auswahl im Text-Editor in einem ausgewählten Strukturelement. Sie haben z.B. einen Codeabschnitt wie den folgenden:

```python
sum = 0
for x in range(1, 100):
    sum = sum + x
```

Bei Auswahl dieses Codes und des Befehls **Umschließen mit** wird eine Liste der verfügbaren Ausschnitte angezeigt. Bei Auswahl von **def** aus der Liste wird der ausgewählte Code innerhalb einer Funktionsdefinition platziert, und Sie können die **TAB**-TASTE zum Navigieren zwischen dem markierten Funktionsnamen und Argumenten verwenden:

![Verwenden des Befehls „Umschließen mit“ für Codeausschnitte](media/code-editing-code-snippet-surround-with.png)

### <a name="examine-available-snippets"></a>Untersuchen verfügbarer Ausschnitte

Sie können die verfügbaren Codeausschnitte im durch den Menübefehl **Extras** > **Codeausschnitt-Manager** geöffneten **Codeausschnitt-Manager** anzeigen, indem Sie **Python** als Sprache auswählen:

![Codeausschnitt-Manager in Visual Studio](media/code-editing-code-snippets-manager.png)

Informationen zum Erstellen eigener Codeausschnitte finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Codeausschnitts](../ide/walkthrough-creating-a-code-snippet.md).

Wenn Sie einen Codeausschnitt geschrieben haben, den Sie gerne für andere Benutzer freigeben möchten, posten Sie ihn in einem Gist, und [informieren Sie uns darüber](https://github.com/Microsoft/PTVS/issues). Möglicherweise verwenden wir den Codeausschnitt in einer zukünftigen Version von Visual Studio.

## <a name="navigate-your-code"></a>Navigieren in Ihrem Code

Die Python-Unterstützung in Visual Studio bietet verschiedene Möglichkeiten, schnell im Code zu navigieren, darunter Bibliotheken, für die Quellcode verfügbar ist: die [Navigationsleiste](#navigation-bar), [**Gehe zu Definition**](#go-to-definition)[**Navigieren zu**](#navigate-to) und [**Alle Verweise suchen**](#find-all-references). Sie können auch den [**Objektkatalog**](../ide/viewing-the-structure-of-code.md#BKMK_ObjectBrowser) von Visual Studio verwenden.

### <a name="navigation-bar"></a>Navigationsleiste

Die Navigationsleiste wird am oberen Rand jedes Editor-Fensters angezeigt und enthält eine Liste mit Definitionen auf zwei Ebenen. Die linke Dropdownliste enthält Klassen- und Funktionsdefinitionen auf oberster Ebene in der aktuellen Datei. Die rechte Dropdownliste zeigt eine Liste der Definitionen innerhalb des links gezeigten Geltungsbereichs. Wenn Sie sich im Editor bewegen, werden die Listen aktualisiert und zeigen den aktuellen Kontext an. Sie können auch einen Eintrag aus diesen Listen auswählen, um direkt an die entsprechende Stelle zu springen.

![Navigationsleiste im Visual Studio-Editor](media/code-editing-navigation-bar.png)

> [!Tip]
> Um die Navigationsleiste auszublenden, wechseln Sie zu **Extras** > **Optionen** > **Text-Editor** > **Python** > **Allgemein**, und deaktivieren Sie die Option **Einstellungen** > **Navigationsleiste**.

### <a name="go-to-definition"></a>Gehe zu Definition

Mit **Gehe zu Definition** wechseln Sie schnell von einem Bezeichner (z.B. einem Funktionsnamen, einer Klasse oder einer Variablen) zu dem Quellcode, in dem dieser definiert ist. Um den Quellcode aufzurufen, klicken Sie mit der rechten Maustaste auf einen Bezeichner und wählen **Gehe zu Definition** aus, oder platzieren Sie den Textcursor in den Bezeichner und drücken Sie **F12**. Dies funktioniert für Ihren gesamten Code und alle externen Bibliotheken, vorausgesetzt, der Quellcode ist verfügbar. Wenn der Quellcode der Bibliothek nicht verfügbar ist, springt **Gehe zu Definition** zur entsprechenden `import`-Anweisung für einen Modulverweis oder zeigt einen Fehler an.

![Befehl „Gehe zu Definition“ in Visual Studio](media/code-editing-go-to-definition.png)

### <a name="navigate-to"></a>Navigieren zu

Der Befehl **Bearbeiten** > **Navigieren zu** (**STRG**+ **,** ) zeigt ein Suchfeld im Editor an, in das Sie eine beliebige Zeichenfolge eingeben und mögliche Übereinstimmungen in Ihrem Code anzeigen können, der eine Funktion, eine Klasse oder eine Variable definiert, die diese Zeichenfolge enthält. Diese Funktion bietet eine ähnliche Funktionalität wie **Gehe zu Definition**, ohne jedoch die Verwendung eines Bezeichners suchen zu müssen.

Indem Sie auf einen beliebigen Namen doppelklicken oder einen Namen mit den Pfeiltasten auswählen und die **EINGABETASTE** drücken, gelangen Sie zur Definition dieses Bezeichners.

![Befehl „Navigieren zu“ in Visual Studio](media/code-editing-navigate-to.png)

### <a name="find-all-references"></a>Alle Verweise suchen

**Alle Verweise suchen** ist eine nützliche Möglichkeit herauszufinden, wo ein bestimmter Bezeichner definiert und verwendet wird, einschließlich Importen und Zuweisungen. Um diese Funktionalität aufzurufen, klicken Sie mit der rechten Maustaste auf einen Bezeichner und wählen **Alle Verweise suchen** aus, oder platzieren Sie den Textcursor in den Bezeichner und drücken Sie **UMSCHALTTASTE**+**F12**. Durch Doppelklicken auf ein Element in der Liste navigieren Sie zur entsprechenden Position.

![Ergebnisse von „Alle Verweise suchen“](media/code-editing-find-all-references.png)

## <a name="see-also"></a>Siehe auch

- [Formatting](formatting-python-code.md)
- [Refactoring](refactoring-python-code.md)
- [Use a linter (Verwenden eines Linters)](linting-python-code.md)
