---
title: C++-Formatierungskonventionen für EditorConfig
titleSuffix: ''
description: Erfahren Sie, wie Sie mit EditorConfig C++-Code in Visual Studio formatieren.
ms.date: 9/14/2020
author: jureid
ms.author: jureid
manager: jmartens
dev_langs:
- CPP
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: reference
ms.workload:
- cplusplus
monikerRange: vs-2019
ms.openlocfilehash: 490a7b29d6e3d8a2dc63c27b9e9d7226b5d22662
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970880"
---
# <a name="c-editorconfig-formatting-conventions"></a>C++-Formatierungskonventionen für EditorConfig

Der Visual Studio C++-Formatierer verfügt über einen umfangreichen Satz an konfigurierbaren Einstellungen, die global angewendet werden können. Um C++-Formatierungseinstellungen für einen bestimmten Arbeitsbereich festzulegen, verwenden Sie [clangformat](https://clang.llvm.org/docs/ClangFormat.html) oder [EditorConfig](https://editorconfig.org/). Sowohl Visual Studio als auch Visual Studio Code verfügen für jede der globalen Visual Studio C++-Formatierungseinstellungen über integrierte EditorConfig-Unterstützung, wobei die EditorConfig-Einstellungen Vorrang haben. Dies bedeutet, dass Sie EditorConfig-Dateien Ihrem Arbeitsbereich hinzufügen können, um die C++-Formatierung auf einer differenzierteren Ebene zu konfigurieren und ein konsistentes Codeformat für alle Benutzer zu erzwingen, die zum Projekt beitragen.

## <a name="c-formatting-conventions"></a>C++-Formatierungskonventionen

EditorConfig-Einstellungen für die C++-Formatierung ist `cpp_` vorangestellt. Im Folgenden finden Sie ein Beispiel dafür, wie die EditorConfig-Datei aussehen könnte:

```ini
[*.{c++,cc,cpp,cxx,h,h++,hh,hpp,hxx,inl,ipp,tlh,tli}]

cpp_indent_case_contents_when_block = true
cpp_new_line_before_open_brace_namespace = same_line
```

Im restlichen Abschnitt dieses Dokuments werden alle EditorConfig-C++-Formatierungseinstellungen aufgelistet, die von Visual Studio und VS Code unterstützt werden.

### <a name="indentation-settings"></a>Einzugseinstellungen

**Geschweifte Klammern einrücken**

- Name: `cpp_indent_braces`
- Werte: `true`, `false`

**Jede Zeile einziehen relativ zu**

- Name: `cpp_indent_multi_line_relative_to`
- Werte:
  - `outermost_parenthesis` – Bei Eingabe einer neuen Zeile wird diese relativ zur äußersten öffnenden Klammer eingezogen.
  - `innermost_parenthesis` – Bei Eingabe einer neuen Zeile wird diese relativ zur innersten öffnenden Klammer eingezogen.
  - `statement_begin` – Bei Eingabe einer neuen Zeile wird diese relativ zum Anfang der aktuellen Anweisung eingezogen.

**Neue Zeilen beim Eingeben innerhalb von Klammern ausrichten**

- Name: `cpp_indent_within_parentheses`
- Werte:
  - `align_to_parenthesis` – Inhalte an öffnender Klammer ausrichten.
  - `indent` – Neue Zeilen einrücken.

**Verwenden Sie in vorhandenem Code nicht die Einstellung für das Ausrichten neuer Zeilen innerhalb von Klammern.**

- Name: `cpp_indent_preserve_within_parentheses`
- Werte: `true`, `false`

**Inhalte einrücken**

- Name: `cpp_indent_case_contents`
- Werte: `true`, `false`

**case-Bezeichnungen einziehen**

- Name: `cpp_indent_case_labels`
- Werte: `true`, `false`

**Auf case-Anweisung folgende geschweifte Klammern einrücken**

- Name: `cpp_indent_case_contents_when_block`
- Werte: `true`, `false`

**Geschweifte Klammern von als Parameter genutzten Lambdafunktionen einrücken**

- Name: `cpp_indent_lambda_braces_when_parameter`
- Werte: `true`, `false`

**Position der goto-Bezeichnungen**

- Name: `cpp_indent_goto_labels`
- Werte:
  - `one_left` – Einmal einrücken nach links
  - `leftmost_column` – Nach Spalte ganz links verschieben
  - `none` – Eingerückt lassen

**Position von Präprozessordirektiven**

- Name: `cpp_indent_preprocessor`
- Werte:
  - `one_left` – Einmal einrücken nach links
  - `leftmost_column` – Nach Spalte ganz links verschieben
  - `none` – Eingerückt lassen

**Zugriffsspezifizierer einrücken**

- Name: `cpp_indent_access_specifiers`
- Werte: `true`, `false`

**Namespace-Inhalte einziehen**

- Name: `cpp_indent_namespace_contents`
- Werte: `true`, `false`

**Einzug von Kommentaren beibehalten**

- Name: `cpp_indent_preserve_comments`
- Werte: `true`, `false`

### <a name="newline-settings"></a>Zeilenumbrucheinstellungen

**Position von öffnenden geschweiften Klammern für Namespaces**

- Name: `cpp_new_line_before_open_brace_namespace`
- Werte:
  - `new_line` – In neue Zeile verschieben
  - `same_line` – In derselben Zeile belassen, jedoch voranstehendes Leerzeichen hinzufügen
  - `ignore` – Position nicht automatisch ändern

**Position von öffnenden geschweiften Klammern für Typen**

- Name: `cpp_new_line_before_open_brace_type`
- Werte:
  - `new_line` – In neue Zeile verschieben
  - `same_line` – In derselben Zeile belassen, jedoch voranstehendes Leerzeichen hinzufügen
  - `ignore` – Position nicht automatisch ändern

**Position von öffnenden geschweiften Klammern für Funktionen**

- Name: `cpp_new_line_before_open_brace_function`
- Werte:
  - `new_line` – In neue Zeile verschieben
  - `same_line` – In derselben Zeile belassen, jedoch voranstehendes Leerzeichen hinzufügen
  - `ignore` – Position nicht automatisch ändern

**Position von öffnenden geschweiften Klammern für Kontrollblöcke**

- Name: `cpp_new_line_before_open_brace_block`
- Werte:
  - `new_line` – In neue Zeile verschieben
  - `same_line` – In derselben Zeile belassen, jedoch voranstehendes Leerzeichen hinzufügen
  - `ignore` – Position nicht automatisch ändern

**Position von öffnenden geschweiften Klammern für Lambdafunktionen**

- Name: `cpp_new_line_before_open_brace_lambda`
- Werte:
  - `new_line` – In neue Zeile verschieben
  - `same_line` – In derselben Zeile belassen, jedoch voranstehendes Leerzeichen hinzufügen
  - `ignore` – Position nicht automatisch ändern
 
**Geschweifte Bereichsklammern in getrennten Zeilen positionieren**

- Name: `cpp_new_line_scope_braces_on_separate_lines`
- Werte: `true`, `false`

**Schließende geschweifte Klammern für leere Typen in dieselbe Zeile wie öffnende geschweifte Klammern verschieben**

- Name: `cpp_new_line_close_brace_same_line_empty_type`
- Werte: `true`, `false`

**In leeren Funktionsrümpfen schließende geschweifte Klammern in dieselbe Zeile wie öffnende geschweifte Klammern verschieben**

- Name: `cpp_new_line_close_brace_same_line_empty_function`
- Werte: `true`, `false`

**"catch" und ähnliche Schlüsselwörter in neuer Zeile platzieren**

- Name: `cpp_new_line_before_catch`
- Werte: `true`, `false`

**else-Anweisung in neuer Zeile anordnen**

- Name: `cpp_new_line_before_else`
- Werte: `true`, `false`

**'while' in einer do-while-Schleife in einer neuen Zeile platzieren**

- Name: `cpp_new_line_before_while_in_do_while`
- Werte: `true`, `false`

### <a name="spacing-settings"></a>Abstandseinstellungen

**Abstand zwischen Funktionsnamen und öffnenden Klammern von Argumentenlisten**

- Name: `cpp_space_before_function_open_parenthesis`
- Werte:
  - `insert` – Leerzeichen einfügen
  - `remove` – Leerzeichen entfernen
  - `ignore` – Leerzeichen nicht ändern

**– Leerzeichen zwischen den Klammern einer Argumentliste einfügen**

- Name: `cpp_space_within_parameter_list_parentheses` Werte: `true`, `false`

**Leerzeichen zwischen Klammern einfügen, wenn die Argumentliste leer ist**

- Name: `cpp_space_between_empty_parameter_list_parentheses`
- Werte: `true`, `false`

**In Anweisungen für die Ablaufsteuerung zwischen Schlüsselwort und öffnender Klammer Leerzeichen einfügen**

- Name: `cpp_space_after_keywords_in_control_flow_statements`
- Werte: `true`, `false`

**Leerzeichen zwischen Klammern für Steueranweisung einfügen**

- Name: `cpp_space_within_control_flow_statement_parentheses`
- Werte: `true`, `false`

**Leerzeichen vor öffnender Klammer der Lambdaargumentliste einfügen**

- Name: `cpp_space_before_lambda_open_parenthesis`
- Werte: `true`, `false`

**Leerzeichen zwischen Klammern für Umwandlungen im C-Stil einfügen**

- Name: `cpp_space_within_cast_parentheses`
- Werte: `true`, `false`

**Nach schließender Klammer der Umwandlung im C-Stil Leerzeichen einfügen**

- Name: `cpp_space_after_cast_close_parenthesis`
- Werte: `true`, `false`

**Leerzeichen zwischen Klammern eines in Klammern gesetzten Ausdrucks einfügen**

- Name: `cpp_space_within_expression_parentheses`
- Werte: `true`, `false`

**Leerzeichen vor öffnender geschweifter Klammer eines Blocks einfügen**

- Name: `cpp_space_before_block_open_brace`
- Werte: `true`, `false`

**Leerzeichen zwischen leeren geschweiften Klammern einfügen**

- Name: `cpp_space_between_empty_braces`
- Werte: `true`, `false`

**Leerzeichen vor öffnender geschweifter Klammer einer einheitlichen Initialisierung und Initialisiererlisten einfügen**

- Name: `cpp_space_before_initializer_list_open_brace`
- Werte: `true`, `false`

**Leerzeichen zwischen geschweiften Klammern einer einheitlichen Initialisierung und den Initialisiererlisten einfügen**

- Name: `cpp_space_within_initializer_list_braces`
- Werte: `true`, `false`

**Leerzeichen innerhalb von einheitlicher Initialisierung und Initialisiererlisten beibehalten**

- Name: `cpp_space_preserve_in_initializer_list`
- Werte: `true`, `false`

**Leerzeichen vor öffnenden eckigen Klammern einfügen**

- Name: `cpp_space_before_open_square_bracket`
- Werte: `true`, `false`

**Leerzeichen zwischen eckigen Klammern einfügen**

- Name: `cpp_space_within_square_brackets`
- Werte: `true`, `false`

**Leerzeichen vor leeren eckigen Klammern einfügen**

- Name: `cpp_space_before_empty_square_brackets`
- Werte: `true`, `false`

**Leerzeichen zwischen leeren eckigen Klammern einfügen**

- Name: `cpp_space_between_empty_square_brackets`
- Werte: `true`, `false`

**Eckige Klammern für mehrdimensionale Arrays gemeinsam gruppieren**

- Name: `cpp_space_group_square_brackets`
- Werte: `true`, `false`

**Leerzeichen zwischen eckigen Klammern für Lambdafunktionen einfügen**

- Name: `cpp_space_within_lambda_brackets`
- Werte: `true`, `false`

**SpaceBetweenEmptyLambdaBrackets**

- Name: `cpp_space_between_empty_lambda_brackets`
- Werte: `true`, `false`

**Leerzeichen vor Kommas einfügen**

- Name: `cpp_space_before_comma`
- Werte: `true`, `false`

**Leerzeichen nach Kommas einfügen**

- Name: `cpp_space_after_comma`
- Werte: `true`, `false`

**Leerzeichen vor und nach Memberoperatoren entfernen**

- Name: `cpp_space_remove_around_member_operators`
- Werte: `true`, `false`

**In Typdeklarationen Leerzeichen vor Doppelpunkt für Basis einfügen**

- Name: `cpp_space_before_inheritance_colon`
- Werte: `true`, `false`

**Leerzeichen vor Doppelpunkt für Konstruktoren einfügen**

- Name: `cpp_space_before_constructor_colon`
- Werte: `true`, `false`

**Leerzeichen vor Semikolons entfernen**

- Name: `cpp_space_remove_before_semicolon`
- Werte: `true`, `false`

**Leerzeichen nach Semikolons einfügen**

- Name: `cpp_space_after_semicolon`
- Werte: `true`, `false`

**Leerzeichen zwischen unären Operatoren und deren Operanden entfernen**

- Name: `cpp_space_remove_around_unary_operator`
- Werte: `true`, `false`

**Abstand für binäre Operatoren**

- Name: `cpp_space_around_binary_operator`
- Werte:
  - `insert` – Leerzeichen vor und nach binären Operatoren einfügen.
  - `remove` – Leerzeichen um binäre Operatoren entfernen.
  - `ignore` – Leerzeichen um binäre Operatoren nicht ändern.

**Abstand für Zuweisungsoperatoren**

- Name: `cpp_space_around_assignment_operator`
- Werte:
  - `insert` – Leerzeichen um Zuweisungsoperatoren einfügen.
  - `remove` – Leerzeichen um Zuweisungsoperatoren entfernen.
  - `ignore` – Leerzeichen um Zuweisungsoperatoren nicht ändern.

**Zeiger-/Verweisausrichtung**

- Name: `cpp_space_pointer_reference_alignment`
- Werte:
  - `left` – Links ausrichten.
  - `center` – Zentriert ausrichten.
  - `right` – Rechts ausrichten.
  - `ignore` – Unverändert lassen.

**Abstand für bedingte Operatoren**

- Name: `cpp_space_around_ternary_operator`
- Werte:
  - `insert` – Leerzeichen um bedingte Operatoren einfügen.
  - `remove` – Leerzeichen um bedingte Operatoren entfernen.
  - `ignore` – Leerzeichen um bedingte Operatoren nicht ändern.

### <a name="wrapping-options"></a>Umbruchoptionen

**Umbruchoptionen für Blöcke**

- Name: `cpp_wrap_preserve_blocks`
- Werte:
  - `one_liners` – Einzeilige Codeblöcke nicht umbrechen.
  - `all_one_line_scopes` – Codeblöcke nicht so umbrechen, dass sich öffnende und schließende geschweifte Klammern in der nächsten Zeile befinden.
  - `never` – Für Blöcke stets Zeilenwechseleinstellungen anwenden.

## <a name="see-also"></a>Weitere Informationen

- [EditorConfig.org](https://editorconfig.org/)
- [Supporting EditorConfig for a language service (Unterstützen von EditorConfig für einen Sprachdienst)](../extensibility/supporting-editorconfig.md)
- [Features des Code-Editors](writing-code-in-the-code-and-text-editor.md)
