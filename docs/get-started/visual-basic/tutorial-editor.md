---
title: Einführung in das Bearbeiten von Code für Visual Basic-Entwickler
description: In dieser 10-minütigen Einführung in den Code-Editor von Visual Studio wird erläutert, inwiefern Visual Studio das Schreiben und Verstehen von sowie das Navigieren in Visual Basic-Code vereinfacht.
ms.custom: seodec18, get-started
ms.date: 11/20/2018
ms.technology: vs-ide-general
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 227d54fbc2734290954fc1c847a34846bb6dc5cf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944536"
---
# <a name="learn-to-use-the-code-editor-with-visual-basic"></a>Verwenden des Code-Editors mit Visual Basic

In dieser zehnminütigen Einführung in den Code-Editor von Visual Studio wird Code zu einer Datei hinzugefügt, um zu veranschaulichen, inwiefern Visual Studio das Schreiben, Navigieren und Verstehen von Visual Basic-Code vereinfacht.

::: moniker range="vs-2017"

> [!TIP]
> Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) kostenlos herunterladen.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads) kostenlos herunterladen.

::: moniker-end

In diesem Artikel wird davon ausgegangen, dass Sie bereits mit Visual Basic vertraut sind. Wenn das nicht der Fall ist, sollten Sie sich zunächst Tutorials wie [Erste Schritte mit Visual Basic in Visual Studio](../../get-started/visual-basic/tutorial-console.md) ansehen.

> [!TIP]
> Damit Sie die in diesem Artikel beschriebenen Vorgänge ausführen können, vergewissern Sie sich, dass Sie für Visual Studio die Visual Basic-Einstellungen ausgewählt haben. Weitere Informationen zum Auswählen von Einstellungen für die integrierte Entwicklungsumgebung (Integrated Development Environment, IDE) finden Sie unter [Select environment settings (Auswählen von Umgebungseinstellungen)](visual-studio-ide.md#select-environment-settings).

## <a name="create-a-new-code-file"></a>Erstellen einer neuen Codedatei

Beginnen Sie mit dem Erstellen einer neuen Datei, und fügen Sie dieser Code hinzu.

::: moniker range="vs-2017"

1. Öffnen Sie Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

1. Öffnen Sie Visual Studio. Drücken Sie **ESC**, oder klicken Sie im Startfenster auf **Ohne Code fortfahren**, um die Entwicklungsumgebung zu öffnen.

::: moniker-end

2. Wählen Sie im Menü **Datei** auf der Menüleiste **Neu > Datei** aus.

3. Klicken Sie im Dialogfeld **Neue Datei** unter der Kategorie **Allgemein** auf die Option **Visual Basic-Klasse**, und klicken Sie dann auf **Öffnen**.

   Im Editor öffnet sich eine neue Datei mit dem Gerüst einer Visual Basic-Klasse. (Sie werden feststellen, dass Sie kein vollständiges Visual Studio-Projekt erstellen müssen, um die Vorteile des Code-Editor zu nutzen (z. B. die Syntaxhervorhebung). Sie benötigen lediglich eine Codedatei.)

   ![Visual Basic-Codedatei in Visual Studio](media/tutorial-editor.png)

## <a name="use-code-snippets"></a>Verwenden von Codeausschnitten

Visual Studio stellt nützliche *Codeausschnitte* bereit, die Sie verwenden können, um häufig verwendete Codeblöcke schnell und einfach zu generieren. Die [Codeausschnitte](../../ide/code-snippets.md) sind für verschiedene Programmiersprachen verfügbar, einschließlich Visual Basic, C# und C++. Nun wird ein **Sub**-Snippet (Visual Basic) zur Datei hinzugefügt.

1. Zeigen Sie mit dem Cursor auf die Zeile, die `End Class` enthält, und geben Sie **sub** ein.

   Ein Popup-Dialogfeld mit Informationen zum `Sub`-Schlüsselwort und zum Einfügen des **Sub**-Codeausschnitts wird angezeigt.

   ![IntelliSense für Codeausschnitte in Visual Studio](media/tutorial-intellisense-snippet.png)

1. Drücken Sie zweimal auf die **TAB-TASTE**, um den Codeausschnitt einzufügen.

   Nun wird die Struktur der Sub-Prozedur `MySub()` zur Datei hinzugefügt.

Die verfügbaren Codeausschnitte variieren je nach Programmiersprache. Sie können die verfügbaren Codeausschnitte für Visual Basic unter **Bearbeiten** > **IntelliSense** > **Ausschnitt einfügen** abrufen (oder **STRG**+**K**, **STRG**+**X** drücken). Für Visual Basic sind Codeausschnitte für folgende Kategorien verfügbar:

![Liste der Visual Basic-Codeausschnitte](media/tutorial-code-snippet-list.png)

Es gibt beispielsweise Codeausschnitte, mit denen bestimmt werden kann, ob eine Datei auf dem Computer vorhanden ist, mit denen in eine Textdatei geschrieben oder ein Registrierungswert gelesen werden kann, für das Ausführen von SQL-Abfragen oder für das Erstellen einer [For Each...Next-Anweisung](/dotnet/visual-basic/language-reference/statements/for-each-next-statement).

## <a name="comment-out-code"></a>Auskommentieren von Code

Durch die Symbolleiste – der Zeile mit Schaltflächen unter der Menüleiste in Visual Studio – können Sie Ihre Produktivität beim Codieren steigern. Beispielsweise können Sie den IntelliSense-Vervollständigungsmodus umschalten, Zeileneinzüge vergrößern oder verkleinern oder Code auskommentieren, der nicht kompiliert werden soll. (Bei [IntelliSense](../../ide/using-intellisense.md) handelt es sich um ein Hilfstool für das Programmieren, durch das beispielsweise eine Liste mit übereinstimmenden Methoden angezeigt werden kann.) In diesem Abschnitt wird Code auskommentiert.

![Bearbeiten von Schaltflächen der Symbolleiste](media/tutorial-editor-toolbar.png)

1. Fügen Sie den folgenden Code in den Text der Prozedur `MySub()` ein.

   ```vb
   ' _words is a string array that we'll sort alphabetically
   Dim _words = New String() {
   "the",
   "quick",
   "brown",
   "fox",
   "jumps"
   }

   Dim morewords = New String() {
   "over",
   "the",
   "lazy",
   "dog"
   }

   Dim query = From word In _words
               Order By word.Length
               Select word
   ```

1. Das Array `morewords` wird an dieser Stelle zwar nicht verwendet, allerdings sollte es nicht vollständig gelöscht werden, weil es unter Umständen später noch benötigt wird. Kommentieren Sie diese Zeilen stattdessen aus. Ordnen Sie die komplette Definition von `morewords` der schließenden geschweiften Klammer zu, und klicken Sie anschließend in der Symbolleiste auf die Schaltfläche **Comment out the selected lines** (Ausgewählte Zeilen auskommentieren). Wenn Sie lieber die Tastatur verwenden möchten, drücken Sie **STRG**+**K**, **STRG**+**C**.

   ![Auskommentieren der Schaltfläche](media/tutorial-comment-out.png)

   Das Visual Basic-Kommentarzeichen `'` wird am Anfang jeder ausgewählten Zeile hinzugefügt, um den Code auszukommentieren.

## <a name="collapse-code-blocks"></a>Reduzieren von Codeblöcken

Sie können Codeabschnitte reduzieren, damit Sie sich besser auf die aktuell relevanten Abschnitte konzentrieren können. Reduzieren Sie zur Übung das `_words`-Array auf eine einzelne Codezeile. Klicken Sie auf das kleine graue Feld mit dem Minuszeichen, das sich am Rand neben der Zeile befindet, die `Dim _words = New String() {` enthält. Wenn Sie lieber mit der Tastatur arbeiten, platzieren Sie den Cursor an einer beliebigen Stelle in der Arraydefinition, und drücken Sie **STRG**+**M**, **STRG**+**M**.

![Gliedern der Schaltfläche zum Reduzieren](media/tutorial-collapse.png)

Der Codeblock wird bis auf die erste Zeile reduziert, an die Auslassungspunkte angehängt werden (`...`). Klicken Sie nun auf dasselbe graue Feld, das diesmal mit einem Pluszeichen versehen ist, um den Codeblock erneut zu erweitern, oder drücken Sie zweimal **STRG**+**M**, **STRG**+**M**. Dieses Feature wird als [Gliedern](../../ide/outlining.md) bezeichnet und ist besonders nützlich, wenn Sie lange Methoden oder ganze Klassen reduzieren möchten.

## <a name="view-symbol-definitions"></a>Anzeigen von Symboldefinitionen

Der Visual Studio-Editor erleichtert u.a. die Prüfung der Definition eines Typs oder einer Methode. Sie können z.B. zu der Datei navigieren, die die Definition enthält, indem Sie an einer beliebigen Stelle, an der auf das Symbol verwiesen wird, **Gehe zu Definition** auswählen. Sie können auch die Option [Definition einsehen](../../ide/go-to-and-peek-definition.md#peek-definition) verwenden. Dies stellt eine schnellere Möglichkeit dar, bei der der Fokus weiterhin auf der Datei liegt. Im Folgenden wird die Definition von Typ `String` dargestellt.

1. Klicken Sie erst mit der rechten Maustaste auf das Wort `String` und anschließend im Inhaltsmenü mit der linken auf die Option **Definition einsehen**. Drücken Sie alternativ **ALT**+**F12**.

   Daraufhin wird ein Popupfenster mit der Definition der `String`-Klasse angezeigt. Sie können in dem Popupfenster scrollen oder sogar die Definition eines anderen Typs des eingesehenen Codes einsehen.

   ![Fenster „Definition einsehen“](media/tutorial-peek-definition.png)

1. Schließen Sie das eingesehene Definitionsfenster, indem Sie auf das kleine „x“ in der oberen rechten Ecke des Popupfensters klicken.

## <a name="use-intellisense-to-complete-words"></a>Verwenden von IntelliSense zum Vervollständigen von Wörtern

[IntelliSense](../../ide/using-intellisense.md) ist eine wichtige Ressource beim Codieren. Damit erhalten Sie Informationen zu verfügbaren Members eines Typs oder Parameterdetails für verschiedene Überladungen einer Methode. Sie können IntelliSense auch verwenden, um Wörter zu vervollständigen, nachdem genug Zeichen eingegeben wurden, um sie eindeutig zu machen. Fügen Sie eine einzige Codezeile hinzu, um die geordneten Zeichenfolgen im Konsolenfenster auszugeben. Dies ist der standardmäßige Ort für die Programmausgabe.

1. Beginnen Sie unter der Variable `query` mit dem Eingeben des folgenden Codes:

   ```vb
   For Each str In qu
   ```

   Dann zeigt IntelliSense Ihnen **QuickInfo** zum `query`-Symbol an.

   ![IntelliSense-Wortvervollständigung in Visual Studio](media/tutorial-intellisense-completion-list.png)

1. Drücken Sie die **TAB-TASTE**, um den Rest des Worts `query` über die IntelliSense-Funktion zur Wortvervollständigung einzufügen.

1. Vervollständigen Sie den Codeblock, sodass dieser wie der folgende Code aussieht.

   ```vb
   For Each str In query
       Console.WriteLine(str)
   Next
   ```

## <a name="refactor-a-name"></a>Refactoring eines Namens

Niemandem gelingt das Codieren schon beim ersten Versuch. Es ist also sehr wahrscheinlich, dass Sie irgendwann den Namen einer Variablen oder Methode ändern möchten. Testen Sie die Funktion [Refactoring](../../ide/refactoring-in-visual-studio.md) von Visual Studio, um die `_words`-Variable in `words` umzubenennen.

1. Platzieren Sie den Cursor über der Definition der `_words`-Variable, und klicken Sie im Kontextmenü (Rechtsklick) auf **Umbenennen**.

   Daraufhin wird das Dialogfeld **Umbenennen** in der oberen rechten Ecke des Editors angezeigt.

1. Geben Sie den gewünschten Namen von **words** ein, während die Variable `_words` noch ausgewählt ist. Beachten Sie dabei, dass der Verweis auf `words` in der Abfrage ebenfalls automatisch umbenannt wird. Aktivieren Sie das Kontrollkästchen **Include comments** (Kommentare einschließen) im Popupfeld **Umbenennen**, bevor Sie die **EINGABETASTE** drücken oder auf **Übernehmen** klicken.

   ![Umbenennen (Dialogfeld)](media/tutorial-rename.png)

1. Drücken Sie die **EINGABETASTE**, oder klicken Sie auf **Übernehmen**.

   Beide Instanzen von `words` sowie der Verweis auf `words` im Codekommentar werden umbenannt.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Erfahren Sie mehr über Projekte und Projektmappen](tutorial-projects-solutions.md)

## <a name="see-also"></a>Siehe auch

- [Codeausschnitte](../../ide/code-snippets.md)
- [Navigieren durch den Code](../../ide/navigating-code.md)
- [Gliedern](../../ide/outlining.md)
- [Go To Definition and Peek Definition („Gehe zu Definition“ und „Definition einsehen“)](../../ide/go-to-and-peek-definition.md)
- [Refactoring](../../ide/refactoring-in-visual-studio.md)
- [Verwendung von IntelliSense](../../ide/using-intellisense.md)
