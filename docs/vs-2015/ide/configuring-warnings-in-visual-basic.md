---
title: Konfigurieren von Warnungen in Visual Basic| Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Basic], warnings
- run-time errors, warnings
- warnings, configuring
ms.assetid: 99cf4781-bd4d-47b4-91b9-217933509f82
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d09a251dc5f98080b317e1560423dcb7c8bf0805
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72619311"
---
# <a name="configuring-warnings-in-visual-basic"></a>Konfigurieren von Warnungen in Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]-Compiler enthält eine Reihe von Warnungen zu Code, der möglicherweise Laufzeitfehler verursacht. Mithilfe dieser Informationen können Sie saubereren, schnelleren und besseren Code mit weniger Fehlern schreiben. So gibt der Compiler z.B. eine Warnung aus, wenn der Benutzer versucht, einen Member einer nicht zugewiesenen Objektvariablen aufzurufen, eine Funktion ohne Angabe eines Rückgabewerts zu beenden oder einen `Try`-Block auszuführen, der Programmfehler im Code für das Abfangen von Ausnahmen enthält.

 In einigen Fällen stellt der Compiler auch zusätzliche Funktionen bereit, die es dem Benutzer ermöglichen, sich auf die konkrete Aufgabe zu konzentrieren, statt sich um möglicherweise auftretende Fehler zu kümmern. In früheren Versionen von [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] wurde `Option Strict` verwendet, um die zusätzlichen Funktionen einzuschränken, die der [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]-Compiler bietet. Durch die Konfiguration von Warnungen können Sie diese Funktionalität auf der Ebene der einzelnen Warnungen und somit wesentlich genauer kontrollieren.

 So können Sie Projekte an Ihre Anforderungen anpassen und einzelne Warnungen deaktivieren, die für Ihre Anwendung nicht relevant sind, oder bestimmte Warnungen in Fehlermeldungen umwandeln. Auf dieser Seite wird das Aktivieren und Deaktivieren einzelner Warnungen erläutert.

## <a name="turning-warnings-off-and-on"></a>Aktivieren und Deaktivieren von Warnungen
 Sie können Warnungen auf zwei Arten konfigurieren: Mit dem **Projekt-Designer** oder mit den Compileroptionen **/warnaserror** und **/nowarn**.

 Im **Projekt-Designer** können Sie Warnungen auf der Registerkarte **Kompilieren** aktivieren und deaktivieren. Wenn Sie alle Warnungen deaktivieren möchten, aktivieren Sie das Kontrollkästchen **Alle Warnungen deaktivieren**. Wenn alle Warnungen als Fehler behandelt werden sollen, aktivieren Sie das Kontrollkästchen **Alle Warnungen als Fehler behandeln**. Einige Warnungen können in der angezeigten Tabelle je nach Bedarf als Fehler oder als Warnungen konfiguriert werden.

 Wenn **Option Strict** auf **Off** festgelegt ist, können Warnungen im Zusammenhang mit **Option Strict** nicht unabhängig voneinander behandelt werden. Wenn **Option Strict** auf **On** festgelegt ist, werden die zugeordneten Warnungen unabhängig von deren Status als Fehler behandelt. Wenn **Option Strict** durch Angabe von `/optionstrict:custom` im Befehlszeilencompiler auf **Custom** festgelegt ist, können **Option Strict**-Warnungen unabhängig voneinander aktiviert bzw. deaktiviert werden.

 Mithilfe der Befehlszeilenoption **/warnaserror** des Compilers kann ebenfalls festgelegt werden, ob Warnungen als Fehler behandelt werden. Sie können bei dieser Option mit den Zeichen + bzw. - in einer durch Trennzeichen getrennten Liste angeben, welche Warnungen als Fehler behandelt werden sollen. In der folgenden Tabelle werden die möglichen Optionen aufgeführt.

|Befehlszeilenoption|Bedeutung|
|--------------------------|---------------|
|`/warnaserror+`|Alle Warnungen als Fehler behandeln.|
|`/warnsaserror`-|Warnungen nicht als Fehler behandeln. Dies ist die Standardeinstellung.|
|`/warnaserror+:<warning list` `>`|Bestimmte Warnungen, die mit ihrer Fehler-ID in einer durch Trennzeichen getrennten Liste angegeben werden, als Fehler behandeln.|
|`/warnaserror-:<warning list>`|Bestimmte Warnungen, die mit ihrer Fehler-ID in einer durch Trennzeichen getrennten Liste angegeben werden, nicht als Fehler behandeln.|
|`/nowarn`|Keine Warnungen ausgeben.|
|`/nowarn:<warning list>`|Bestimmte Warnungen, die mit ihrer Fehler-ID in einer durch Trennzeichen getrennten Liste angegeben werden, nicht ausgeben.|

 Die Liste mit Warnungen enthält die Fehler-IDs der Warnungen, die als Fehler behandelt werden sollen. Auf diese Weise können bestimmte Warnungen mithilfe von Befehlszeilenoptionen aktiviert bzw. deaktiviert werden. Wenn die Liste der Warnungen eine ungültige ID enthält, wird ein Fehler ausgegeben.

## <a name="examples"></a>Beispiele
 In dieser Tabelle mit Beispielen für Befehlszeilenargumente wird die Bedeutung der einzelnen Argumente beschrieben.

|Argument|Beschreibung|
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

### <a name="late-bound-method-invocation-and-overload-resolution-warning"></a>Aufruf spät gebundener Methoden und Überladungsauflösung
 Wird bei später Bindung generiert. Für neue Projekte standardmäßig deaktiviert.

 ID: 42017

### <a name="operands-of-type-object-warnings"></a>Operanden vom Typ Objekt
 Wird generiert, wenn Operanden vom Typ `Object` vorkommen, die bei Verwendung von `Option Strict On` einen Fehler verursachen würden. Für neue Projekte standardmäßig aktiviert.

 ID: 42018 und 42019

### <a name="declarations-require-as-clause-warnings"></a>Für Deklarationen ist eine 'As'-Klausel erforderlich
 Wird generiert, wenn eine Variablen-, Funktions- oder Eigenschaftendeklaration ohne `As`-Klausel bei Verwendung von `Option Strict On` einen Fehler verursachen würde. Bei Variablen, denen kein Typ zugeordnet ist, wird davon ausgegangen, dass diese vom Typ `Object` sind. Für neue Projekte standardmäßig aktiviert.

 ID: 42020 (Variablendeklaration), 42021 (Funktionsdeklaration) und 42022 (Eigenschaftendeklaration)

### <a name="possible-null-reference-exception-warnings"></a>Ausnahme bei möglichem NULL-Verweis
 Wird generiert, wenn eine Variable verwendet wird, bevor dieser ein Wert zugewiesen wurde. Für neue Projekte standardmäßig aktiviert.

 ID: 42104, 42030

### <a name="unused-local-variable-warning"></a>Nicht verwendete lokale Variable
 Wird generiert, wenn eine lokale Variable deklariert, aber nie auf diese verwiesen wird. Standardmäßig aktiviert.

 ID: 42024

### <a name="access-of-shared-member-through-instance-variable-warning"></a>Zugriff auf freigegebenen Member durch Instanzvariable
 Wird generiert, wenn beim Zugriff auf einen freigegebenen Member durch eine Instanz Nebeneffekte auftreten könnten oder wenn der Zugriff auf einen freigegebenen Member durch eine Instanzvariable nicht auf der rechten Seite eines Ausdrucks erfolgt oder als Parameter übergeben wird. Für neue Projekte standardmäßig aktiviert.

 ID: 42025

### <a name="recursive-operator-or-property-access-warnings"></a>Rekursiver Zugriff auf Operator oder Eigenschaft
 Wird generiert, wenn im Rumpf einer Routine derselbe Operator oder dieselbe Eigenschaft verwendet wird, in dem oder der die Routine definiert ist. Für neue Projekte standardmäßig aktiviert.

 ID: 42004 (Operator), 42026 (Eigenschaft)

### <a name="function-or-operator-without-return-value-warning"></a>Funktion oder Operator ohne Rückgabewert
 Wird generiert, wenn für eine Funktion oder einen Operator kein Rückgabewert angegeben wurde. Dazu zählt auch das Auslassen von `Set` für die implizite lokale Variable, die denselben Namen wie die Funktion hat. Für neue Projekte standardmäßig aktiviert.

 ID: 42105 (Funktion), 42016 (Operator)

### <a name="overloads-modifier-used-in-a-module-warning"></a>Verwendung eines Overloads-Modifizierers in einem Modul
 Wird generiert, wenn `Overloads` in einem `Module` verwendet wird. Für neue Projekte standardmäßig aktiviert.

 ID: 42028

### <a name="duplicate-or-overlapping-catch-blocks-warnings"></a>Doppelte oder sich überschneidende catch-Blöcke
 Wird generiert, wenn ein `Catch`-Block durch dessen Beziehung zu anderen definierten `Catch`-Blöcken nie erreicht wird. Für neue Projekte standardmäßig aktiviert.

 ID: 42029, 42031

## <a name="see-also"></a>Weitere Informationen
 [Fehlertypen](https://msdn.microsoft.com/library/3048aabf-8c97-4e13-9150-853769cb5f6f) des [Ausnahmen-Assistenten (Dialog Feld](../debugger/exception-assistant-dialog-box.md) ) [try... Catch... Letzte Anweisung](https://msdn.microsoft.com/library/d6488026-ccb3-42b8-a810-0d97b9d6472b) [/nowarn](https://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) [/warnaserror (Visual Basic)](https://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1) [Kompilierungs Seite, Projekt-Designer (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md) [Compilerwarnungen, die standardmäßig deaktiviert sind](https://msdn.microsoft.com/library/69809cfb-a38a-4035-b154-283a61938df8)
