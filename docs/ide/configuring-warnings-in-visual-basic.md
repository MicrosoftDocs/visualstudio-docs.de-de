---
title: Konfigurieren von Warnungen in Visual Basic
description: Erfahren Sie, wie Sie Warnungen in Visual Basic konfigurieren können, was Ihnen erleichtert, sauberen, schnelleren und besseren Code mit weniger Fehlern zu schreiben.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Basic], warnings
- run-time errors, warnings
- warnings, configuring
ms.assetid: 99cf4781-bd4d-47b4-91b9-217933509f82
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a59ee0e3aed10b5fd48fcbf57d9cb69aca3f929e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907644"
---
# <a name="configuring-warnings-in-visual-basic"></a>Konfigurieren von Warnungen in Visual Basic

Der [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]-Compiler enthält eine Reihe von Warnungen zu Code, der möglicherweise Laufzeitfehler verursacht. Mithilfe dieser Informationen können Sie saubereren, schnelleren und besseren Code mit weniger Fehlern schreiben. So gibt der Compiler z.B. eine Warnung aus, wenn der Benutzer versucht, einen Member einer nicht zugewiesenen Objektvariablen aufzurufen, eine Funktion ohne Angabe eines Rückgabewerts zu beenden oder einen `Try`-Block auszuführen, der Programmfehler im Code für das Abfangen von Ausnahmen enthält.

In einigen Fällen stellt der Compiler auch zusätzliche Funktionen bereit, die es dem Benutzer ermöglichen, sich auf die konkrete Aufgabe zu konzentrieren, statt sich um möglicherweise auftretende Fehler zu kümmern. In früheren Versionen von [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] wurde **Option Strict** verwendet, um die zusätzlichen Funktionen einzuschränken, die der [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]-Compiler bietet. Durch die Konfiguration von Warnungen können Sie diese Funktionalität auf der Ebene der einzelnen Warnungen und somit wesentlich genauer kontrollieren.

So können Sie Projekte an Ihre Anforderungen anpassen und einzelne Warnungen deaktivieren, die für Ihre Anwendung nicht relevant sind, oder bestimmte Warnungen in Fehlermeldungen umwandeln. Auf dieser Seite wird das Aktivieren und Deaktivieren einzelner Warnungen erläutert.

## <a name="turning-warnings-off-and-on"></a>Aktivieren und Deaktivieren von Warnungen
Sie können Warnungen auf zwei Arten konfigurieren: Mit dem **Projekt-Designer** oder mit den Compileroptionen **/warnaserror** und **/nowarn**.

Im **Projekt-Designer** können Sie Warnungen auf der Registerkarte **Kompilieren** aktivieren und deaktivieren. Wenn Sie alle Warnungen deaktivieren möchten, aktivieren Sie das Kontrollkästchen **Alle Warnungen deaktivieren**. Wenn alle Warnungen als Fehler behandelt werden sollen, aktivieren Sie das Kontrollkästchen **Alle Warnungen als Fehler behandeln**. Einige Warnungen können in der angezeigten Tabelle je nach Bedarf als Fehler oder als Warnungen konfiguriert werden.

Wenn **Option Strict** auf **Off** festgelegt ist, können Warnungen im Zusammenhang mit **Option Strict** nicht unabhängig voneinander behandelt werden. Wenn **Option Strict** auf **On** festgelegt ist, werden die zugeordneten Warnungen unabhängig von deren Status als Fehler behandelt. Wenn **Option Strict** durch Angabe von `/optionstrict:custom` im Befehlszeilencompiler auf **Custom** festgelegt ist, können **Option Strict**-Warnungen unabhängig voneinander aktiviert bzw. deaktiviert werden.

Mithilfe der Befehlszeilenoption **/warnaserror** des Compilers kann ebenfalls festgelegt werden, ob Warnungen als Fehler behandelt werden. Sie können bei dieser Option mit den Zeichen + bzw. - in einer durch Trennzeichen getrennten Liste angeben, welche Warnungen als Fehler behandelt werden sollen. In der folgenden Tabelle werden die möglichen Optionen aufgeführt.

|Befehlszeilenoption|Bedeutung|
| - |---------------|
|`/warnaserror+`|Alle Warnungen als Fehler behandeln.|
|`/warnsaserror`-|Warnungen nicht als Fehler behandeln. Dies ist die Standardeinstellung.|
|`/warnaserror+:<warning list` `>`|Bestimmte Warnungen, die mit ihrer Fehler-ID in einer durch Trennzeichen getrennten Liste angegeben werden, als Fehler behandeln.|
|`/warnaserror-:<warning list>`|Bestimmte Warnungen, die mit ihrer Fehler-ID in einer durch Trennzeichen getrennten Liste angegeben werden, nicht als Fehler behandeln.|
|`/nowarn`|Keine Warnungen ausgeben.|
|`/nowarn:<warning list>`|Bestimmte Warnungen, die mit ihrer Fehler-ID in einer durch Trennzeichen getrennten Liste angegeben werden, nicht ausgeben.|

Die Liste mit Warnungen enthält die Fehler-IDs der Warnungen, die als Fehler behandelt werden sollen. Auf diese Weise können bestimmte Warnungen mithilfe von Befehlszeilenoptionen aktiviert bzw. deaktiviert werden. Wenn die Liste der Warnungen eine ungültige ID enthält, wird ein Fehler ausgegeben.

## <a name="examples"></a>Beispiele
In dieser Tabelle mit Beispielen für Befehlszeilenargumente wird die Bedeutung der einzelnen Argumente beschrieben.

|Argument|BESCHREIBUNG|
|--------------|-----------------|
|`vbc /warnaserror`|Gibt an, dass alle Warnungen als Fehler behandelt werden sollen.|
|`vbc /warnaserror:42024`|Gibt an, dass die Warnung 42024 als Fehler behandelt werden soll.|
|`vbc /warnaserror:42024,42025`|Gibt an, dass die Warnungen 42024 und 42025 als Fehler behandelt werden sollen.|
|`vbc /nowarn`|Gibt an, dass keine Warnungen ausgegeben werden sollen.|
|`vbc /nowarn:42024`|Gibt an, dass die Warnung 42024 nicht ausgegeben werden soll.|
|`vbc /nowarn:42024,42025`|Gibt an, dass die Warnungen 42024 und 42025 nicht ausgegeben werden sollen.|

## <a name="types-of-warnings"></a>Arten von Warnungen
Im Folgenden wird eine Liste von Warnungen aufgeführt, die als Fehler behandelt werden können.

### <a name="implicit-conversion-warning"></a>Implizite Konvertierung
Wird bei impliziten Konvertierungen generiert. Hierzu zählen keine impliziten Konvertierungen aus einem systeminternen numerischen Typ in eine Zeichenfolge bei Verwendung des Operators `&`. Für neue Projekte standardmäßig deaktiviert.

ID: 42016

### <a name="late-bound-method-invocation-and-overload-resolution-warning"></a>Aufruf spät gebundener Methoden und Warnungen zur Überladungsauflösung
Wird bei später Bindung generiert. Für neue Projekte standardmäßig deaktiviert.

ID: 42017

### <a name="operands-of-type-object-warnings"></a>Warnungen zum Operanden vom Typ „Object“
Wird generiert, wenn Operanden vom Typ `Object` vorkommen, die bei Verwendung von **Option Strict On** einen Fehler verursachen würden. Für neue Projekte standardmäßig aktiviert.

ID: 42018 und 42019

### <a name="declarations-require-as-clause-warnings"></a>Für Deklarationen ist eine As-Klausel erforderlich
Wird generiert, wenn eine Variablen-, Funktions- oder Eigenschaftendeklaration ohne `As`-Klausel bei Verwendung von **Option Strict On** einen Fehler verursachen würde. Bei Variablen, denen kein Typ zugeordnet ist, wird davon ausgegangen, dass diese vom Typ `Object` sind. Für neue Projekte standardmäßig aktiviert.

ID: 42020 (Variablendeklaration), 42021 (Funktionsdeklaration) und 42022 (Eigenschaftendeklaration)

### <a name="possible-null-reference-exception-warnings"></a>Warnungen zu Ausnahmen bei möglichem NULL-Verweis
Wird generiert, wenn eine Variable verwendet wird, bevor dieser ein Wert zugewiesen wurde. Für neue Projekte standardmäßig aktiviert.

ID: 42104, 42030

### <a name="unused-local-variable-warning"></a>Warnung zu nicht verwendeten lokalen Variablen
Wird generiert, wenn eine lokale Variable deklariert, aber nie auf diese verwiesen wird. Standardmäßig aktiviert.

ID: 42024

### <a name="access-of-shared-member-through-instance-variable-warning"></a>Warnung zum Zugriff auf freigegebenen Member durch Instanzvariable
Wird generiert, wenn beim Zugriff auf einen freigegebenen Member durch eine Instanz Nebeneffekte auftreten könnten oder wenn der Zugriff auf einen freigegebenen Member durch eine Instanzvariable nicht auf der rechten Seite eines Ausdrucks erfolgt oder als Parameter übergeben wird. Für neue Projekte standardmäßig aktiviert.

ID: 42025

### <a name="recursive-operator-or-property-access-warnings"></a>Warnungen zum rekursiven Zugriff auf Operator oder Eigenschaft
Wird generiert, wenn im Rumpf einer Routine derselbe Operator oder dieselbe Eigenschaft verwendet wird, in dem oder der die Routine definiert ist. Für neue Projekte standardmäßig aktiviert.

ID: 42004 (Operator), 42026 (Eigenschaft)

### <a name="function-or-operator-without-return-value-warning"></a>Warnung zu Funktion oder Operator ohne Rückgabewert
Wird generiert, wenn für eine Funktion oder einen Operator kein Rückgabewert angegeben wurde. Dazu zählt auch das Auslassen von `Set` für die implizite lokale Variable, die denselben Namen wie die Funktion hat. Für neue Projekte standardmäßig aktiviert.

ID: 42105 (Funktion), 42016 (Operator)

### <a name="overloads-modifier-used-in-a-module-warning"></a>Warnung zur Verwendung eines Overloads-Modifizierers in einem Modul
Wird generiert, wenn `Overloads` in einem `Module` verwendet wird. Für neue Projekte standardmäßig aktiviert.

ID: 42028

### <a name="duplicate-or-overlapping-catch-blocks-warnings"></a>Warnung zu doppelten oder sich überschneidenden catch-Blöcken
Wird generiert, wenn ein `Catch`-Block durch dessen Beziehung zu anderen definierten `Catch`-Blöcken nie erreicht wird. Für neue Projekte standardmäßig aktiviert.

ID: 42029, 42031

## <a name="see-also"></a>Weitere Informationen

- [Fehlertypen](/dotnet/visual-basic/programming-guide/language-features/error-types)
- [Try...Catch...Finally-Anweisung](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)
- [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn)
- [/warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror)
- [Seite „Kompilieren“, Projekt-Designer (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md)
- [Standardmäßig deaktivierte Compilerwarnungen](/cpp/preprocessor/compiler-warnings-that-are-off-by-default)
