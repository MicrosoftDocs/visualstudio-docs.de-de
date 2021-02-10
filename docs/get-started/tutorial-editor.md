---
title: Einführung in das Bearbeiten im Code-Editor
description: Lernen Sie, mit dem Code-Editor in Visual Studio einer Datei Code hinzuzufügen, und außerdem, wie Sie Code schreiben, dorthin navigieren und ihn umgestalten.
ms.date: 11/30/2017
ms.technology: vs-ide-general
ms.custom:
- get-started
- SEO-VS-2020
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: f76eb5ba3ccab85a4cf6c8ca5ad4a8fa3e021f47
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951211"
---
# <a name="learn-to-use-the-code-editor"></a>Informationen zur Verwendung des Code-Editors

In dieser Einführung in den Code-Editor von Visual Studio, die etwa zehn Minuten Ihrer Zeit in Anspruch nehmen wird, wird Code zu einer Datei hinzugefügt, um zu veranschaulichen, inwiefern Visual Studio das Schreiben, Navigieren und Verstehen von Code vereinfacht.

::: moniker range="vs-2017"

> [!TIP]
> Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) kostenlos herunterladen.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads) kostenlos herunterladen.

::: moniker-end

In diesem Artikel wird davon ausgegangen, dass Sie bereits mit einer Programmiersprache vertraut sind. Sollte dies nicht der Fall sein, empfehlen wir Ihnen, sich zuerst einen der Schnellstarts zum Thema Programmierung anzusehen, beispielsweise zum Erstellen einer Web-App mit [Python](../ide/quickstart-python.md) oder [C#](../get-started/csharp/tutorial-aspnet-core.md) oder zum Erstellen einer Konsolen-App mit [Visual Basic](../ide/quickstart-visual-basic-console.md) oder [C++](/cpp/get-started/tutorial-console-cpp).

## <a name="create-a-new-code-file"></a>Erstellen einer neuen Codedatei

Beginnen Sie mit dem Erstellen einer neuen Datei, und fügen Sie dieser Code hinzu.

::: moniker range="vs-2017"

1. Öffnen Sie Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

1. Öffnen Sie Visual Studio. Drücken Sie **ESC**, oder klicken Sie im Startfenster auf **Ohne Code fortfahren**, um die Entwicklungsumgebung zu öffnen.

::: moniker-end

2. Wählen Sie im Menü **Datei** auf der Menüleiste **Neu** > **Datei** aus.

3. Klicken Sie im Dialogfeld **Neue Datei** unter der Kategorie **Allgemein** auf die Option **Visual C#-Klasse**, und klicken Sie dann auf **Öffnen**.

   Im Editor öffnet sich eine neue Datei mit dem Skelett einer C#-Klasse. (Beachten Sie, dass Sie kein vollständiges Visual Studio-Projekt erstellen müssen, um einen Nutzen aus dem Code-Editor zu ziehen; Sie benötigen lediglich eine Codedatei.)

   ![C#-Codedatei in Visual Studio](media/tutorial-editor.png)

## <a name="use-code-snippets"></a>Verwenden von Codeausschnitten

Visual Studio stellt nützliche *Codeausschnitte* bereit, die Sie verwenden können, um häufig verwendete Codeblöcke schnell und einfach zu generieren. Die [Codeausschnitte](../ide/code-snippets.md) sind für verschiedene Programmiersprachen verfügbar, einschließlich C#, Visual Basic und C++. Fügen Sie den C#-Ausschnitt `void Main` zu Ihrer Datei hinzu.

1. Platzieren Sie den Cursor unmittelbar vor der letzten schließenden Klammer **}** in der Datei, und geben Sie `svm` ein. (`svm` steht für `static void Main`. Die [Main()](/dotnet/csharp/programming-guide/main-and-command-args/)-Methode ist der Einstiegspunkt für C#-Anwendungen.)

   Ein Popup-Dialogfeld mit Informationen zum Codeausschnitt `svm` wird angezeigt.

   ![IntelliSense für Codeausschnitte in Visual Studio](media/tutorial-intellisense-snippet.png)

1. Drücken Sie zweimal auf die **TAB-TASTE**, um den Codeausschnitt einzufügen.

   Daraufhin wir die Methodensignatur `static void Main()` zu der Datei hinzugefügt.

Die verfügbaren Codeausschnitte variieren je nach Programmiersprache. Sie können sich die für Ihre Sprache verfügbaren Codeausschnitte anzeigen lassen, indem Sie **Bearbeiten** > **IntelliSense** > **Ausschnitt einfügen** und anschließend den Ordner für Ihre Sprache auswählen. Für C# sieht die Liste wie folgt aus:

![Liste der Codeausschnitte für C#](media/tutorial-code-snippet-list.png)

Die Liste enthält u.a. Ausschnitte zum Erstellen einer [Klasse](/dotnet/csharp/programming-guide/classes-and-structs/classes), eines [Konstruktors](/dotnet/csharp/programming-guide/classes-and-structs/constructors), einer [for](/dotnet/csharp/language-reference/keywords/for)-Schleife und einer [if](/dotnet/csharp/language-reference/keywords/if-else)- oder [switch](/dotnet/csharp/language-reference/keywords/switch)-Anweisung.

## <a name="comment-out-code"></a>Auskommentieren von Code

Durch die Symbolleiste – der Zeile mit Schaltflächen unter der Menüleiste in Visual Studio – können Sie Ihre Produktivität beim Codieren steigern. Sie können beispielsweise den IntelliSense-Beendigungsmodus umschalten ([IntelliSense](../ide/using-intellisense.md) ist eine Codierungshilfe, die u.a. eine Liste von übereinstimmenden Methoden anzeigt), einen Zeileneinzug verkleinern oder vergrößern oder Code auskommentieren, der nicht kompiliert werden soll. In diesem Abschnitt wird Code auskommentiert.

![Editor-Symbolleiste](media/tutorial-editor-toolbar.png)

1. Fügen Sie den folgenden Code in den Methodentext `Main()` ein.

    ```csharp
    // _words is a string array that we'll sort alphabetically
    string[] _words = {
        "the",
        "quick",
        "brown",
        "fox",
        "jumps"
    };

    string[] morewords = {
        "over",
        "the",
        "lazy",
        "dog"
    };

    IEnumerable<string> query = from word in _words
                                orderby word.Length
                                select word;
    ```

1. Die Variable `morewords` wird an dieser Stelle zwar nicht verwendet, allerdings sollte sie nicht vollständig gelöscht werden, weil sie unter Umständen später noch benötigt wird. Kommentieren Sie diese Zeilen stattdessen aus. Ordnen Sie die komplette Definition von `morewords` dem Semikolon zu, das zum Abschluss gesetzt wird, und klicken Sie anschließend in der Symbolleiste auf die Schaltfläche **Comment out the selected lines** (Ausgewählte Zeilen auskommentieren). Wenn Sie lieber die Tastatur verwenden möchten, drücken Sie **STRG**+**K**, **STRG**+**C**.

   ![Auskommentieren der Schaltfläche](media/tutorial-comment-out.png)

   Die C#-Kommentarzeichen `//` werden am Anfang jeder ausgewählten Zeile hinzugefügt, um den Code auszukommentieren.

## <a name="collapse-code-blocks"></a>Reduzieren von Codeblöcken

Es soll kein leerer [Konstruktor](/dotnet/csharp/programming-guide/classes-and-structs/constructors) für die generierte `Class1` angezeigt werden. Reduzieren Sie daher die Ansicht des Codes, damit unnötige Informationen ausgeblendet werden. Klicken Sie auf das kleine graue Feld mit dem Minuszeichen auf dem Rand neben der ersten Zeile des Konstruktors. Wenn Sie lieber mit der Tastatur arbeiten, platzieren Sie den Cursor an einer beliebigen Stelle im Konstruktorcode, und drücken Sie **STRG**+**M**, **STRG**+**M**.

![Gliedern der Schaltfläche zum Reduzieren](media/tutorial-collapse.png)

Der Codeblock wird bis auf die erste Zeile reduziert, an die Auslassungspunkte angehängt werden (`...`). Klicken Sie nun auf dasselbe graue Feld, das diesmal mit einem Pluszeichen versehen ist, um den Codeblock erneut zu erweitern, oder drücken Sie zweimal **STRG**+**M**, **STRG**+**M**. Dieses Feature wird als [Gliedern](../ide/outlining.md) bezeichnet und ist besonders nützlich, wenn Sie lange Methoden oder ganze Klassen reduzieren möchten.

## <a name="view-symbol-definitions"></a>Anzeigen von Symboldefinitionen

Der Visual Studio-Editor erleichtert u.a. die Prüfung der Definition eines Typs oder einer Methode. Sie können z.B. zu der Datei navigieren, die die Definition enthält, indem Sie an einer beliebigen Stelle, an der auf das Symbol verwiesen wird, **Gehe zu Definition** auswählen. Sie können auch die Option [Definition einsehen](../ide/go-to-and-peek-definition.md#peek-definition) verwenden. Dies stellt eine schnellere Möglichkeit dar, bei der der Fokus weiterhin auf der Datei liegt. Im Folgenden wird die Definition von Typ `string` dargestellt.

1. Klicken Sie mit der rechten Maustaste auf eine beliebige Darstellung von `string`, und wählen Sie im Inhaltsmenü die Option **Definition einsehen** aus. Drücken Sie alternativ **ALT**+**F12**.

   Daraufhin wird ein Popupfenster mit der Definition der `String`-Klasse angezeigt. Sie können in dem Popupfenster scrollen oder sogar die Definition eines anderen Typs des eingesehenen Codes einsehen.

   ![Fenster „Definition einsehen“](media/tutorial-peek-definition.png)

1. Schließen Sie das eingesehene Definitionsfenster, indem Sie auf das kleine „x“ in der oberen rechten Ecke des Popupfensters klicken.

## <a name="use-intellisense-to-complete-words"></a>Verwenden von IntelliSense zum Vervollständigen von Wörtern

[IntelliSense](../ide/using-intellisense.md) ist eine wichtige Ressource beim Codieren. Damit erhalten Sie Informationen zu verfügbaren Members eines Typs oder Parameterdetails für verschiedene Überladungen einer Methode. Sie können IntelliSense auch verwenden, um Wörter zu vervollständigen, nachdem genug Zeichen eingegeben wurden, um sie eindeutig zu machen. Fügen Sie eine einzige Codezeile hinzu, um die geordneten Zeichenfolgen im Konsolenfenster auszugeben. Dies ist der standardmäßige Ort für die Programmausgabe.

1. Beginnen Sie unter der Variable `query` mit dem Eingeben des folgenden Codes:

   ```csharp
   foreach (string str in qu
   ```

   Dann zeigt IntelliSense Ihnen **QuickInfo** zum `query`-Symbol an.

   ![IntelliSense-Wortvervollständigung in Visual Studio](media/tutorial-intellisense-completion-list.png)

1. Drücken Sie die **TAB-TASTE**, um den Rest des Worts `query` über die IntelliSense-Funktion zur Wortvervollständigung einzufügen.

1. Vervollständigen Sie den Codeblock, sodass dieser wie der folgende Code aussieht. Sie können das Verwenden von Codeausschnitten noch einmal üben, indem Sie `cw` eingeben und dann zweimal die **TAB-TASTE** drücken, um den `Console.WriteLine`-Code zu generieren.

   ```csharp
   foreach (string str in query)
   {
      Console.WriteLine(str);
   }
   ```

## <a name="refactor-a-name"></a>Refactoring eines Namens

Niemandem gelingt das Codieren schon beim ersten Versuch. Es ist also sehr wahrscheinlich, dass Sie irgendwann den Namen einer Variablen oder Methode ändern möchten. Testen Sie die Funktion [Refactoring](../ide/refactoring-in-visual-studio.md) von Visual Studio, um die `_words`-Variable in `words` umzubenennen.

1. Platzieren Sie den Cursor über der Definition der `_words`-Variable, und klicken Sie im Kontextmenü (Rechtsklick) auf **Umbenennen**, oder drücken Sie **STRG**+**R**, **STRG**+**R**.

   Daraufhin wird das Dialogfeld **Umbenennen** in der oberen rechten Ecke des Editors angezeigt.

1. Geben Sie den gewünschten Namen **Wörter** ein. Beachten Sie dabei, dass der Verweis auf `words` in der Abfrage ebenfalls automatisch umbenannt wird. Aktivieren Sie das Kontrollkästchen **Kommentare einbeziehen** im Dialogfeld **Umbenennen**, bevor Sie auf die **EINGABETASTE** drücken.

   ![Umbenennen (Dialogfeld)](media/tutorial-rename.png)

1. Drücken Sie die **EINGABETASTE**.

   Beide Instanzen von `words` sowie der Verweis auf `words` im Codekommentar wurden umbenannt.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Erfahren Sie mehr über Projekte und Projektmappen](../get-started/tutorial-projects-solutions.md)

## <a name="see-also"></a>Siehe auch

- [Codeausschnitte](../ide/code-snippets.md)
- [Navigieren durch den Code](../ide/navigating-code.md)
- [Gliedern](../ide/outlining.md)
- [Go To Definition and Peek Definition („Gehe zu Definition“ und „Definition einsehen“)](../ide/go-to-and-peek-definition.md)
- [Refactoring](../ide/refactoring-in-visual-studio.md)
- [Verwendung von IntelliSense](../ide/using-intellisense.md)
