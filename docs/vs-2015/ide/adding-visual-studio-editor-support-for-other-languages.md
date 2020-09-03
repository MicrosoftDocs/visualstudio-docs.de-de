---
title: Hinzufügen der Editor Unterstützung für andere Sprachen | Microsoft-Dokumentation
ms.date: 11/15/2016
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
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9dbd245edd81907197e23c0d193a01cc07424b4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548108"
---
# <a name="adding-visual-studio-editor-support-for-other-languages"></a>Hinzufügen von Visual Studio-Editor-Unterstützung für andere Sprachen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Erfahren Sie mehr dazu, wie der Visual Studio-Editor das Lesen von und Navigieren in verschiedenen Computersprachen unterstützt und wie Sie dem Visual Studio-Editor Unterstützung für weitere Sprachen hinzufügen können.

## <a name="syntax-colorization-statement-completion-and-navigate-to-support"></a>Farbige Syntaxhervorhebung, Anweisungsvervollständigung und Unterstützung von Navigieren zu
 Funktionen wie farbige Syntaxhervorhebung, Anweisungsvervollständigung und Navigieren zu im Visual Studio-Editor können Ihnen helfen, Ihren Code leichter zu lesen, zu erstellen und zu bearbeiten. Der folgende Screenshot zeigt ein Beispiel für die Bearbeitung eines Perl-Skripts in Visual Studio. Die Syntax wird automatisch farbig hervorgehoben. Beispielsweise sind Anmerkungen im Code grün eingefärbt, Code ist schwarz, Pfade sind rot und Anweisungen blau. Der Visual Studio-Editor wendet die farbige Syntaxhervorhebung automatisch auf jede unterstützte Sprache an. Darüber hinaus zeigt die Anweisungsvervollständigung eine Liste der möglichen Anweisungen und Objekte an, sobald Sie mit der Eingabe eines bekannten Sprachschlüsselworts oder -objekts beginnen. Die Anweisungsvervollständigung kann Ihnen helfen, schnell und einfach mehr Code zu erstellen.

 ![Farbige Syntaxhervorhebung in einem Perl-Skript](../ide/media/vside-perledit.png "VSIDE_PerlEdit")

 Visual Studio bietet aktuell farbige Syntaxhervorhebung und Unterstützung für Anweisungsvervollständigung mithilfe von [TextMate Grammatiken](https://manual.macromates.com/en/language_grammars) für die folgenden Sprachen. Wenn sich Ihre bevorzugte Sprache nicht in der Liste findet, braucht Sie das trotzdem nicht zu beunruhigen – Sie können sie hinzufügen.

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

 Über die farbige Syntaxhervorhebung und einfache Anweisungsvervollständigung hinaus bietet Visual Studio noch eine Funktion mit dem Namen [Navigieren zu](https://blogs.msdn.microsoft.com/benwilli/2015/04/09/visual-studio-tip-3-use-navigate-to/). Mithilfe dieses Features können Sie schnell Codedateien, Dateipfade und Codesymbole durchsuchen. Visual Studio bietet Unterstützung für Navigieren zu für die folgenden Sprachen.

- Go

- Java

- JavaScript

- PHP

- TypeScript

- Visual Basic

- Visual C++

- Visual C#

  Alle diese Dateitypen verfügen über die zuvor beschriebenen Funktionen, auch wenn der Support für eine bestimmte Sprache noch nicht installiert wurde. Das Installieren der besonderen Unterstützung für einige Sprachen stellt möglicherweise weitergehende Unterstützung für die betreffende Sprache bereit, wie etwa IntelliSense oder andere erweiterte Sprachfunktionen, wie etwa Glühbirnen.

## <a name="adding-support-for-non-supported-languages"></a>Hinzufügen von Unterstützung für nicht unterstützte Sprachen
 Visual Studio 2015 Update 1 und spätere Versionen bieten Sprachunterstützung im Editor mithilfe von [TextMate-Grammatiken](https://manual.macromates.com/en/language_grammars). Wenn Ihre bevorzugte Programmiersprache aktuell nicht im Visual Studio-Editor unterstützt wird, suchen Sie zuerst im Web – es ist gut möglich, dass bereits ein TextMate-Paket für die Sprache verfügbar ist. Wenn Sie allerdings keins finden können, können Sie in Visual Studio 2015 Update 1 oder später selbst Unterstützung hinzufügen, indem Sie ein TextMate-Paketmodell für die Sprachgrammatik und Codeausschnitte erstellen.

 Fügen Sie eventuelle neue TextMate-Grammatiken für Visual Studio im folgenden Ordner hinzu:

 %userprofile%\\.vs\Extensions

 Fügen Sie unter diesem Basispfad die folgenden Ordner hinzu, wenn sie für Ihren Fall zutreffend sind:

|Ordnername|Beschreibung|
|-----------------|-----------------|
|\\*\<language name>*|Der Sprachordner. Ersetzen Sie *\<language name>* durch den Namen der Sprache. Beispiel: **\Matlab**.|
|\Syntaxes|Der Grammatikordner. Enthält die JSON-Grammatikdateien für die Sprache, wie etwa **Matlab.json**.|
|\Snippets|Der Codeausschnittordner. Enthält die Ausschnitte für die Sprache.|

 In Windows wird% User Profile% in den folgenden Pfad aufgelöst: c:\Users \\ *\<user name>* . Wenn der Erweiterungsordner auf Ihrem System nicht vorhanden ist, müssen Sie ihn erstellen. Wenn der Ordner bereits vorhanden ist, ist er verborgen.

 Detailinformationen zum Erstellen von TextMate-Grammatiken finden Sie unter [TextMate – Introduction to Language Grammars: How to add source code syntax highlighting embedded in HTML](https://developmentality.wordpress.com/2011/02/08/textmate-introduction-to-language-grammars/) (TextMate – Einführung in Sprachgrammatiken: Hinzufügen von Quellcode-Syntaxhervorhebung mit Einbettung in HTML) und [Notes on how to create a Language Grammar and Custom Theme for a Textmate Bundle](https://benparizek.com/notebook/notes-on-how-to-create-a-language-grammar-and-custom-theme-for-a-textmate-bundle) (Anmerkungen zum Erstellen einer Sprachgrammatik und eines benutzerdefinierten Designs für ein TextMate-Paket).

## <a name="see-also"></a>Weitere Informationen
 [Visual Studio 2013 Verbesserungen an Navigieren zu](https://blogs.msdn.microsoft.com/mvpawardprogram/2013/10/22/visual-studio-2013-navigate-to-improvements/) [Exemplarische Vorgehensweise: Erstellen eines Codeausschnitts](../ide/walkthrough-creating-a-code-snippet.md) [Exemplarische Vorgehensweise: Anweisungsvervollständigung anzeigen](../extensibility/walkthrough-displaying-statement-completion.md)
