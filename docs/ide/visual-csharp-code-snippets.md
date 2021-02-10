---
title: C#-Codeausschnitte
description: In Visual Studio können Sie Codeausschnitte zum Hinzufügen von häufig verwendetem Code zu den C#-Codedateien verwenden.
ms.custom: SEO-VS-2020
ms.date: 06/05/2017
ms.topic: reference
helpviewer_keywords:
- snippets [C#]
- code snippets [C#]
- Code Snippet Inserter [C#]
- C#, code snippets
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: e4656e0769075be26db5bd06108093a49fb5e2af
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941540"
---
# <a name="c-code-snippets"></a>C#-Codeausschnitte

Codeausschnitte sind vorgefertigte Ausschnitte aus Code, die Sie schnell in Ihren Code einfügen können. Beispielsweise erstellt der `for`-Codeausschnitt eine leere `for`-Schleife. Einige Codeausschnitte sind umschließende Codeausschnitte, mit deren Hilfe Sie Codezeilen markieren und dann einen Codeausschnitt auswählen können, der die markierten Codezeilen einschließt. Durch das Markieren von Codezeilen und das anschließende Aktivieren des `for`-Codeausschnitts wird beispielsweise eine `for`-Schleife erstellt, die die markierten Codezeilen innerhalb des Schleifenblocks enthält. Durch Codeausschnitte kann das Erstellen von Programmcode schneller, einfacher und zuverlässiger werden.

Sie können einen Codeausschnitt an der Cursorposition einfügen oder einen umgebenden Codeausschnitt einfügen, der den aktuell ausgewählten Code einschließt. Der Codeausschnitteinfüger wird im Menü **IntelliSense** über die Befehle **Codeausschnitt einfügen** oder **Umschließen mit** oder durch die Tastenkombinationen **STRG**+**K**>**X** bzw. **STRG**+**K**>**S** aufgerufen.

Der **Codeausschnitteinfüger** zeigt den Codeausschnittnamen für alle verfügbaren Codeausschnitte an. Darüber hinaus umfasst der Codeausschnitteinfüger ein Eingabedialogfeld, in dem Sie den Namen des Codeausschnitts vollständig oder teilweise eingeben können. Daraufhin wird im Codeausschnitteinfüger der Eintrag hervorgehoben, der dem Namen eines Codeausschnitts am besten entspricht. Durch Drücken der **TAB-TASTE** können Sie den Codeausschnitteinfüger jederzeit schließen und den zu diesem Zeitpunkt ausgewählten Codeausschnitt einfügen. Durch Drücken der **ESC-TASTE** oder Klicken mit der Maus im Code-Editor wird der Codeausschnitteinfüger geschlossen, ohne dass ein Codeausschnitt eingefügt wird.

## <a name="default-code-snippets"></a>Standardcodeausschnitte

Die folgenden Codeausschnitte sind für C# standardmäßig in Visual Studio enthalten.

|Name (oder Verknüpfung)|BESCHREIBUNG|Mögliche Stellen zum Einfügen des Ausschnitts|
| - |-----------------| - |
|#if|Erstellt eine [#if](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-if)-Direktive und eine [#endif](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endif)-Direktive.|Beliebig.|
|#region|Erstellt eine [#region](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-region)-Direktive und eine [#endregion](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endregion)-Direktive.|Beliebig.|
|~|Erstellt einen [Finalizer](/dotnet/csharp/programming-guide/classes-and-structs/destructors) (Destruktor) für die enthaltende Klasse.|Innerhalb einer Klasse.|
|Attribut|Erstellt eine Deklaration für eine <xref:System.Attribute> abgeleitete Klasse.|In einem Namespace (einschließlich des globalen Namespaces), einer Klasse oder einer Struktur.|
|checked|Erstellt einen [checked](/dotnet/csharp/language-reference/keywords/checked)-Block.|In einer Methode, einem Indexer, einem Eigenschaftenaccessor oder einem Ereignisaccessor.|
|class|Erstellt eine Klassendeklaration.|In einem Namespace (einschließlich des globalen Namespaces), einer Klasse oder einer Struktur.|
|ctor|Erstellt einen Konstruktor für die enthaltende Klasse.|Innerhalb einer Klasse.|
|cw|Erstellt einen Aufruf an <xref:System.Console.WriteLine%2A>.|In einer Methode, einem Indexer, einem Eigenschaftenaccessor oder einem Ereignisaccessor.|
|do|Erstellt eine [do](/dotnet/csharp/language-reference/keywords/do) `while`-Schleife.|In einer Methode, einem Indexer, einem Eigenschaftenaccessor oder einem Ereignisaccessor.|
|else|Erstellt einen [else](/dotnet/csharp/language-reference/keywords/if-else)-Block.|In einer Methode, einem Indexer, einem Eigenschaftenaccessor oder einem Ereignisaccessor.|
|enum|Erstellt eine [enum](/dotnet/csharp/language-reference/keywords/enum)-Deklaration.|In einem Namespace (einschließlich des globalen Namespaces), einer Klasse oder einer Struktur.|
|equals|Erstellt eine Methodendeklaration, die die in der <xref:System.Object>-Klasse definierte <xref:System.Object.Equals%2A>-Methode außer Kraft setzt.|Innerhalb einer Klasse oder Struktur.|
|exception|Erstellt eine Deklaration für eine Klasse, die von einer Ausnahme abgeleitet wird (standardmäßig <xref:System.Exception>).|In einem Namespace (einschließlich des globalen Namespaces), einer Klasse oder einer Struktur.|
|für|Erstellt eine [for](/dotnet/csharp/language-reference/keywords/for)-Schleife.|In einer Methode, einem Indexer, einem Eigenschaftenaccessor oder einem Ereignisaccessor.|
|foreach|Erstellt eine [foreach](/dotnet/csharp/language-reference/keywords/foreach-in)-Schleife.|In einer Methode, einem Indexer, einem Eigenschaftenaccessor oder einem Ereignisaccessor.|
|forr|Erstellt eine [for](/dotnet/csharp/language-reference/keywords/for)-Schleife, deren Schleifenvariable nach jeder Iteration verringert wird.|In einer Methode, einem Indexer, einem Eigenschaftenaccessor oder einem Ereignisaccessor.|
|if|Erstellt einen [if](/dotnet/csharp/language-reference/keywords/if-else)-Block.|In einer Methode, einem Indexer, einem Eigenschaftenaccessor oder einem Ereignisaccessor.|
|Indexer|Erstellt eine Indexerdeklaration.|Innerhalb einer Klasse oder Struktur.|
|interface|Erstellt eine [interface](/dotnet/csharp/language-reference/keywords/interface)-Deklaration.|In einem Namespace (einschließlich des globalen Namespaces), einer Klasse oder einer Struktur.|
|invoke|Erstellt einen Block, durch den ein Ereignis sicher aufgerufen wird.|In einer Methode, einem Indexer, einem Eigenschaftenaccessor oder einem Ereignisaccessor.|
|Iterator|Erstellt einen Iterator.|Innerhalb einer Klasse oder Struktur.|
|iterindex|Erstellt ein „benanntes“ Iterator-/Indexerpaar unter Verwendung einer geschachtelten Klasse.|Innerhalb einer Klasse oder Struktur.|
|Sperre|Erstellt einen [lock](/dotnet/csharp/language-reference/keywords/lock-statement)-Block.|In einer Methode, einem Indexer, einem Eigenschaftenaccessor oder einem Ereignisaccessor.|
|mbox|Erstellt einen Aufruf an <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName>. Sie müssen möglicherweise einen Verweis auf *System.Windows.Forms.dll* hinzufügen.|In einer Methode, einem Indexer, einem Eigenschaftenaccessor oder einem Ereignisaccessor.|
|namespace|Erstellt eine [namespace](/dotnet/csharp/language-reference/keywords/namespace)-Deklaration.|In einem Namespace (einschließlich des globalen Namespaces).|
|prop|Erstellt eine Deklaration mit [automatisch implementierter Eigenschaft](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties).|Innerhalb einer Klasse oder Struktur.|
|propfull|Erstellt eine Eigenschaftendeklaration mit `get`-Accessor und `set`-Accessor.|Innerhalb einer Klasse oder Struktur.|
|propg|Erstellt eine schreibgeschützte [automatisch implementierte Eigenschaft](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties) mit einem privaten `set`-Accessor.|Innerhalb einer Klasse oder Struktur.|
|sim|Erstellt eine Deklaration der Main-Methode mit [static](/dotnet/csharp/language-reference/keywords/static) [int](/dotnet/csharp/language-reference/keywords/int).|Innerhalb einer Klasse oder Struktur.|
|struct|Erstellt eine [struct](/dotnet/csharp/language-reference/keywords/struct)-Deklaration.|In einem Namespace (einschließlich des globalen Namespaces), einer Klasse oder einer Struktur.|
|svm|Erstellt eine Deklaration der Main-Methode mit [static](/dotnet/csharp/language-reference/keywords/static) [void](/dotnet/csharp/language-reference/keywords/void).|Innerhalb einer Klasse oder Struktur.|
|switch|Erstellt einen [switch](/dotnet/csharp/language-reference/keywords/switch)-Block.|In einer Methode, einem Indexer, einem Eigenschaftenaccessor oder einem Ereignisaccessor.|
|Versuch|Erstellt einen [try-catch](/dotnet/csharp/language-reference/keywords/try-catch)-Block.|In einer Methode, einem Indexer, einem Eigenschaftenaccessor oder einem Ereignisaccessor.|
|tryf|Erstellt einen [try-finally](/dotnet/csharp/language-reference/keywords/try-finally)-Block.|In einer Methode, einem Indexer, einem Eigenschaftenaccessor oder einem Ereignisaccessor.|
|unchecked|Erstellt einen [unchecked](/dotnet/csharp/language-reference/keywords/unchecked)-Block.|In einer Methode, einem Indexer, einem Eigenschaftenaccessor oder einem Ereignisaccessor.|
|unsafe|Erstellt einen [unsafe](/dotnet/csharp/language-reference/keywords/unsafe)-Block.|In einer Methode, einem Indexer, einem Eigenschaftenaccessor oder einem Ereignisaccessor.|
|using|Erstellt eine [using](/dotnet/csharp/language-reference/keywords/using-directive)-Direktive.|In einem Namespace (einschließlich des globalen Namespaces).|
|while|Erstellt eine [while](/dotnet/csharp/language-reference/keywords/while)-Schleife.|In einer Methode, einem Indexer, einem Eigenschaftenaccessor oder einem Ereignisaccessor.|

## <a name="see-also"></a>Siehe auch

- [Codeausschnittfunktionen](../ide/code-snippet-functions.md)
- [Codeausschnitte](../ide/code-snippets.md)
- [Vorlagenparameter](../ide/template-parameters.md)
- [Vorgehensweise: Verwenden von umschließenden Codeausschnitten](../ide/how-to-use-surround-with-code-snippets.md)
