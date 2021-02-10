---
title: Hinzufügen der Editor-Unterstützung für andere Sprachen
description: Erfahren Sie mehr dazu, wie der Visual Studio-Editor das Lesen von und Navigieren in verschiedenen Computersprachen unterstützt, und wie Sie Unterstützung für weitere Sprachen hinzufügen können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax colorization
- IntelliSense
- IDE, navigation
- documents [Visual Studio], navigation
- TextMate bundle
- TextMate language grammar
- language support
ms.assetid: d78c43ee-4ef2-42e5-984e-d137de4e7e92
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d5e78f632cdfe3e207e7ce71530d06c2a3b3fc6c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914977"
---
# <a name="add-visual-studio-editor-support-for-other-languages"></a>Hinzufügen von Visual Studio-Editor-Unterstützung für andere Sprachen

Erfahren Sie mehr dazu, wie der Visual Studio-Editor das Lesen von und Navigieren in verschiedenen Computersprachen unterstützt und wie Sie dem Visual Studio-Editor Unterstützung für weitere Sprachen hinzufügen können.

## <a name="syntax-colorization-statement-completion-and-navigate-to-support"></a>Farbige Syntaxhervorhebung, Anweisungsvervollständigung und Unterstützung von Navigieren zu

Features wie farbige Syntaxhervorhebung, Anweisungsvervollständigung (auch bekannt als IntelliSense) und _Navigieren zu_ im Visual Studio-Editor erleichtern das Schreiben, Lesen und Bearbeiten Ihres Codes. Der folgende Screenshot zeigt ein Beispiel für die Bearbeitung eines Perl-Skripts in Visual Studio. Die Syntax wird automatisch farbig hervorgehoben. Beispielsweise sind Anmerkungen im Code grün eingefärbt, Code ist schwarz, Pfade sind rot und Anweisungen blau. Der Visual Studio-Editor wendet die farbige Syntaxhervorhebung automatisch auf jede unterstützte Sprache an. Darüber hinaus zeigt die Anweisungsvervollständigung eine Liste der möglichen Anweisungen und Objekte an, sobald Sie mit der Eingabe eines bekannten Sprachschlüsselworts oder -objekts beginnen. Die Anweisungsvervollständigung unterstützt Sie beim schnelleren und einfacheren Schreiben von Code.

![Farbige Syntaxhervorhebung in einem Perl-Skript](../ide/media/vside_perledit.png)

Visual Studio bietet aktuell farbige Syntaxhervorhebung und Unterstützung für Anweisungsvervollständigung mithilfe von [TextMate Grammatiken](https://manual.macromates.com/en/language_grammars) für die folgenden Sprachen. Wenn Sie Ihre bevorzugte Sprache nicht in der Liste finden, können Sie sie hinzufügen.


- Bat
- F#
- Java
- Markdown
- Rust
- Visual Basic
- Clojure
- Gehe zu
- JavaDoc
- Objective-C
- ShaderLab
- C#
- CMake
- Groovy
- JSON
- Perl
- ShellScript
- Visual C++
- CoffeeScript
- HTML
- LESS
- Python
- SQL
- VBNet
- CSS
- INI
- LUA
- R
- Swift
- XML
- Docker
- Jade
- Make
- Ruby
- TypeScript
- YAML

Über die farbige Syntaxhervorhebung und einfache Anweisungsvervollständigung hinaus bietet Visual Studio noch eine Funktion mit dem Namen [Navigieren zu](/archive/blogs/benwilli/visual-studio-tip-3-use-navigate-to). Mithilfe dieses Features können Sie schnell Codedateien, Dateipfade und Codesymbole durchsuchen. Visual Studio bietet Unterstützung für Navigieren zu für die folgenden Sprachen.

- C#

- C++

- TypeScript

- JavaScript

- Visual Basic

- Gehe zu

- Java

- PHP

Alle diese Dateitypen verfügen über die zuvor beschriebenen Features, auch wenn der Support für eine bestimmte Sprache noch nicht installiert wurde. Das Installieren der besonderen Unterstützung für einige Sprachen stellt möglicherweise weitergehende Unterstützung für die betreffende Sprache bereit, wie etwa IntelliSense oder andere erweiterte Sprachfeatures wie Glühbirnen.

## <a name="add-support-for-non-supported-languages"></a>Hinzufügen von Unterstützung für nicht unterstützte Sprachen

Visual Studio bietet Sprachunterstützung im Editor mithilfe von [TextMate-Grammatiken](https://manual.macromates.com/en/language_grammars). Wenn Ihre bevorzugte Programmiersprache aktuell nicht im Visual Studio-Editor unterstützt wird, suchen Sie zuerst im Web&mdash;es ist gut möglich, dass bereits ein TextMate-Paket für die Sprache verfügbar ist. Wenn Sie allerdings keins finden können, können Sie selbst Unterstützung hinzufügen, indem Sie ein TextMate-Paketmodell für die Sprachgrammatik und die Codeausschnitte erstellen.

Fügen Sie eventuelle neue TextMate-Grammatiken für Visual Studio im folgenden Ordner hinzu:

*%userprofile%\\.vs\Extensions*

Fügen Sie unter diesem Basispfad die folgenden Ordner hinzu, wenn sie für Ihren Fall zutreffend sind:

|Ordnername|Beschreibung|
|-----------------|-----------------|
|\\*\<language name>*|Der Sprachordner. Ersetzen Sie *\<language name>* durch den Namen der Sprache. Beispiel: *\Matlab*.|
|*\Syntaxes*|Der Grammatikordner. Enthält die *JSON*-Grammatikdateien für die Sprache, wie etwa *Matlab.json*.|
|*\Snippets*|Der Codeausschnittordner. Enthält die Ausschnitte für die Sprache.|

Unter Windows wird *%userprofile%* in den Pfad *C:\Benutzer\\\<user name>* aufgelöst. Wenn der *Erweiterungsordner* auf Ihrem System nicht vorhanden ist, müssen Sie ihn erstellen. Wenn der Ordner bereits vorhanden ist, ist er verborgen.

> [!TIP]
> Wenn Sie Dateien im Editor geöffnet haben, müssen Sie sie schließen und erneut öffnen, um die Syntaxhervorhebung anzuzeigen, nachdem Sie die TextMate-Grammatiken hinzugefügt haben.

Detailinformationen zum Erstellen von TextMate-Grammatiken finden Sie unter [TextMate – Introduction to Language Grammars](https://developmentality.wordpress.com/2011/02/08/textmate-introduction-to-language-grammars/) (TextMate – Einführung in Sprachgrammatiken) und [Notes on how to create a Language Grammar and Custom Theme for a Textmate Bundle](https://benparizek.com/notebook/notes-on-how-to-create-a-language-grammar-and-custom-theme-for-a-textmate-bundle) (Anmerkungen zum Erstellen einer Sprachgrammatik und eines benutzerdefinierten Designs für ein TextMate-Paket).

## <a name="see-also"></a>Siehe auch

- [Hinzufügen einer Erweiterung für das Sprachserverprotokoll](../extensibility/adding-an-lsp-extension.md)
- [Exemplarische Vorgehensweise: Create a code snippet (Exemplarische Vorgehensweise: Erstellen eines Codeausschnitts)](../ide/walkthrough-creating-a-code-snippet.md)
- [Exemplarische Vorgehensweise: Anzeigen von Anweisungsvervollständigung](../extensibility/walkthrough-displaying-statement-completion.md)
- [Beispielcode: TextMate-Grammatik](https://github.com/microsoft/VSSDK-Extensibility-Samples/tree/master/TextmateGrammar)
- [Beispielcode: Benutzerdefinierte Sprachunterstützung](https://github.com/microsoft/VSSDK-Extensibility-Samples/tree/master/Ook_Language_Integration)