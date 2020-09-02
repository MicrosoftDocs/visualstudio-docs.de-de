---
title: Konfigurationsoptionen für .NET Code Quality Analyzer
ms.date: 09/23/2019
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0370688b53e87cf6ea1f5079d2e5c706777dd0c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "88706567"
---
# <a name="rule-scope-options-for-net-code-quality-analyzers"></a>Optionen für den Regelbereich für .NET-Code Qualitätsanalysen

Mit einigen .NET Code Quality Analyzer-Regeln können Sie verfeinern, auf welche Teile Ihrer Codebasis Sie angewendet werden sollen. Auf dieser Seite werden die verfügbaren Optionen für die Bereichs Konfiguration, die zulässigen Werte und die Regeln aufgelistet, auf die Sie angewendet werden können. Wenn Sie diese Optionen verwenden möchten, geben Sie Sie in einer [Editor config-Datei](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project)an.

> [!TIP]
> Die vollständige Liste der verfügbaren Optionen finden Sie in der [Configuration.MD-Analyse Datei](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md). Im folgenden finden Sie ein Beispiel dafür, wie eine Option in der Datei *Analyzer Configuration.MD* dokumentiert wird:
>
> Options Name: `sufficient_IterationCount_for_weak_KDF_algorithm`\
> Optionswerte: ganzzahlige Werte \
> Standardwert: spezifisch für jede konfigurierbare Regel (standardmäßig "100000" für die meisten Regeln) \
> Ein Beispiel: `dotnet_code_quality.CA5387.sufficient_IterationCount_for_weak_KDF_algorithm = 100000`

## <a name="api_surface"></a>api_surface

| Beschreibung | Zulässige Werte | Standardwert | Konfigurierbare Regeln |
| - | - | - | - |
| Der zu analysierende Teil der API-Oberfläche | `public`<br/>`internal` oder `friend`<br/>`private`<br/>`all`<br/><br/>Trennen Sie mehrere Werte durch ein Komma (,). | `public` | [CA1000](ca1000.md) [CA1003](ca1003.md) [CA1008](ca1008.md) [CA1010](ca1010.md)<br/>[CA1012](ca1012.md) [CA1024](ca1024.md) [CA1027](ca1027.md) [CA1028](ca1028.md)<br/>[CA1030](ca1030.md) [CA1036](ca1036.md) [CA1040](ca1040.md) [CA1041](ca1041.md)<br/>[CA1043](ca1043.md) [CA1044](ca1044.md) [CA1051](ca1051.md) [CA1052](ca1052.md)<br/>[CA1054](ca1054.md) [CA1055](ca1055.md) [CA1056](ca1056.md) [CA1058](ca1058.md)<br/>[CA1063](ca1063.md) [CA1708](ca1708.md) [CA1710](ca1710.md) [CA1711](ca1711.md)<br/>[CA1714](ca1714.md) [CA1715](ca1715.md) [CA1716](ca1716.md) [CA1717](ca1717.md)<br/>[CA1720](ca1720.md) [CA1721](ca1721.md) [CA1725](ca1725.md) [CA1801](ca1801.md)<br/>[CA1802](ca1802.md) [CA1815](ca1815.md) [CA1819](ca1819.md) [CA2217](ca2217.md)<br/>[CA2225](ca2225.md) [CA2226](ca2226.md) [CA2231](ca2231.md) [CA2234](ca2234.md)<br/>|

## <a name="exclude_async_void_methods"></a>exclude_async_void_methods

| Beschreibung | Zulässige Werte | Standardwert | Konfigurierbare Regeln |
| - | - | - | - |
| Gibt an, ob asynchrone Methoden ignoriert werden sollen, die keinen Wert zurückgeben. | `true`<br/>`false` | `false` | [CA2007](ca2007.md) |

> [!NOTE]
> In Version 2.6.3 und früher des Analyzer-Pakets hieß diese Option `skip_async_void_methods` .

## <a name="exclude_single_letter_type_parameters"></a>exclude_single_letter_type_parameters

| Beschreibung | Zulässige Werte | Standardwert | Konfigurierbare Regeln |
| - | - | - | - |
| Ob [Typparameter](/dotnet/csharp/programming-guide/generics/generic-type-parameters) mit einem Zeichen aus der Regel ausgeschlossen werden sollen, z. b. `S` in `Collection<S>` | `true`<br/>`false` | `false` | [CA1715](ca1715.md) |

> [!NOTE]
> In Version 2.6.3 und früher des Analyzer-Pakets hieß diese Option `allow_single_letter_type_parameters` .

## <a name="output_kind"></a>output_kind

| Beschreibung | Zulässige Werte | Standardwert | Konfigurierbare Regeln |
| - | - | - | - |
| Gibt an, dass Code in einem Projekt analysiert werden soll, das diesen Assemblytyp generiert. | Ein oder mehrere Felder der- <xref:Microsoft.CodeAnalysis.OutputKind> Enumeration.<br/><br/>Trennen Sie mehrere Werte durch ein Komma (,). | Alle Ausgabearten | [CA2007](ca2007.md) |

## <a name="required_modifiers"></a>required_modifiers

| Beschreibung | Zulässige Werte | Standardwert | Konfigurierbare Regeln |
| - | - | - | - |
| Gibt die erforderlichen modifiziererer für APIs an, die analysiert werden sollen. | Mindestens ein Wert aus der unten angegebenen Tabelle mit den Modifiziererwerten<br/><br/>Trennen Sie mehrere Werte durch ein Komma (,). | Hängt von jeder Regel ab | [CA1802](ca1802.md) |

| Zulässiger Modifizierer | Zusammenfassung |
| --- | --- |
| `none` | Keine modifiziereranforderung |
| `static` oder `Shared` | Muss in Visual Basic als "static" ("Shared") deklariert werden. |
| `const` | Muss als "Konstanten" deklariert werden. |
| `readonly` | Muss als ' schreibgeschützt ' deklariert werden |
| `abstract` | Muss als "abstract" deklariert werden |
| `virtual` | Muss als "Virtual" deklariert werden |
| `override` | Muss als ' override ' deklariert werden |
| `sealed` | Muss als ' sealed ' deklariert werden |
| `extern` | Muss als "extern" deklariert werden |
| `async` | Muss als "Async" deklariert werden. |

## <a name="exclude_extension_method_this_parameter"></a>exclude_extension_method_this_parameter

| Beschreibung | Zulässige Werte | Standardwert | Konfigurierbare Regeln |
| - | - | - | - |
| Ob die Analyse für den `this` Parameter der Erweiterungs Methoden übersprungen werden soll. | `true`<br/>`false` | `false` | [CA1062](ca1062.md) |

## <a name="null_check_validation_methods"></a>null_check_validation_methods

| Beschreibung | Zulässige Werte | Standardwert | Konfigurierbare Regeln |
| - | - | - | - |
| Namen der Überprüfungsmethoden zur Validierung von Null-Überprüfungen, die die an die Methode übergebenen Argumente überprüfen | Zulässige Methodennamen Formate (durch Trennzeichen getrennt `|` ):<br/> -Nur Methodenname (schließt alle Methoden mit dem Namen ein, unabhängig vom enthaltenden Typ oder Namespace)<br/> -Voll qualifizierte Namen im [Dokumentations-ID-Format](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)des Symbols mit einem optionalen `M:` Präfix | Keine | [CA1062](ca1062.md) |

## <a name="additional_string_formatting_methods"></a>additional_string_formatting_methods

| Beschreibung | Zulässige Werte | Standardwert | Konfigurierbare Regeln |
| - | - | - | - |
| Namen von zusätzlichen Zeichen folgen-Formatierungs Methoden | Zulässige Methodennamen Formate (durch Trennzeichen getrennt `|` ):<br/> -Nur Methodenname (schließt alle Methoden mit dem Namen ein, unabhängig vom enthaltenden Typ oder Namespace)<br/> -Voll qualifizierte Namen im [Dokumentations-ID-Format](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)des Symbols mit einem optionalen `M:` Präfix | Keine | [CA2241](ca2241.md) |

## <a name="excluded_type_names_with_derived_types"></a>excluded_type_names_with_derived_types

| Beschreibung | Zulässige Werte | Standardwert | Konfigurierbare Regeln |
| - | - | - | - |
| Namen von Typen, sodass der Typ und alle abgeleiteten Typen für die Analyse ausgeschlossen sind | Zulässige Symbolnamen Formate (durch Trennzeichen getrennt `|` ):<br/> -Nur Typname (schließt alle Typen mit dem Namen ein, unabhängig vom enthaltenden Typ oder Namespace)<br/> -Voll qualifizierte Namen im [Dokumentations-ID-Format](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)des Symbols mit einem optionalen `T:` Präfix | Keine | [CA1303](ca1303.md) |

## <a name="excluded_symbol_names"></a>excluded_symbol_names

| Beschreibung | Zulässige Werte | Standardwert | Konfigurierbare Regeln |
| - | - | - | - |
| Namen von Symbolen, die für die Analyse ausgeschlossen sind | Zulässige Symbolnamen Formate (durch Trennzeichen getrennt `|` ):<br/> -Nur Symbol Name (schließt alle Symbole mit dem Namen ein, unabhängig vom enthaltenden Typ oder Namespace)<br/> -Voll qualifizierte Namen im [Dokumentations-ID-Format](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)des Symbols. Jeder Symbol Name erfordert ein Symbolart-Präfix, z. b. "M:"-Präfix für Methoden, "T:"-Präfix für Typen, "N:"-Präfix für Namespaces usw.<br/> - `.ctor` für Konstruktoren und `.cctor` für statische Konstruktoren | Keine | [CA1062](ca1062.md) [CA1303](ca1303.md) [CA2000](ca2000.md) [CA2100](ca2100.md) [CA2301](ca2301.md) [CA2302](ca2302.md)<br/>[CA2311](ca2311.md) [CA2312](ca2312.md) [CA2321](ca2321.md) [CA2322](ca2322.md) [CA2327](ca2327.md) [CA2328](ca2328.md)<br/>[CA2329](ca2329.md) [CA2330](ca2330.md) [CA3001](ca3001.md) [CA3002](ca3002.md) [CA3003](ca3003.md) [CA3004](ca3004.md)<br/>[CA3005](ca3005.md) [CA3006](ca3006.md) [CA3007](ca3007.md) [CA3008](ca3008.md) [CA3009](ca3009.md) [CA3010](ca3010.md)<br/>[CA3011](ca3011.md) [CA3012](ca3012.md) [CA5361](ca5361.md) CA5376 CA5377 [CA5378](ca5378.md)<br/>[CA5380](ca5380.md) [CA5381](ca5381.md) CA5382 CA5383 CA5384 CA5387<br/>CA5388 [CA5389](ca5389.md) CA5390 |

## <a name="disallowed_symbol_names"></a>disallowed_symbol_names

| Beschreibung | Zulässige Werte | Standardwert | Konfigurierbare Regeln |
| - | - | - | - |
| Namen von Symbolen, die im Kontext der Analyse nicht zulässig sind | Zulässige Symbolnamen Formate (durch Trennzeichen getrennt `|` ):<br/> -Nur Symbol Name (schließt alle Symbole mit dem Namen ein, unabhängig vom enthaltenden Typ oder Namespace)<br/> -Voll qualifizierte Namen im [Dokumentations-ID-Format](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)des Symbols. Jeder Symbol Name erfordert ein Symbolart-Präfix, z. b. "M:"-Präfix für Methoden, "T:"-Präfix für Typen, "N:"-Präfix für Namespaces usw.<br/> - `.ctor` für Konstruktoren und `.cctor` für statische Konstruktoren | Keine | [CA1031](ca1031.md) |
