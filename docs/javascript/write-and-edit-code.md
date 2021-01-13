---
title: Einführung in das Bearbeiten von Code für JavaScript-Entwickler
description: In dieser Einführung in den Code-Editor von Visual Studio wird erläutert, inwiefern Visual Studio das Schreiben und Verstehen von sowie das Navigieren in JavaScript-Code vereinfacht.
ms.date: 12/13/2018
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: bd1b12be2dba1526301cd0ea9a4356fb9cc14c14
ms.sourcegitcommit: 105e7b5a486262bc92939980383ceee068098a11
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/30/2020
ms.locfileid: "97815736"
---
# <a name="learn-to-use-the-code-editor-for-javascript"></a>Verwenden des Code-Editors mit JavaScript

In dieser kurzen Einführung in den Code-Editor von Visual Studio wird erläutert, inwiefern Visual Studio das Schreiben und Verstehen von sowie das Navigieren in Code vereinfacht.

> [!TIP]
> Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/) kostenlos herunterladen. Je nachdem, welche Art von App-Entwicklung Sie wählen, müssen Sie die **Workload für die Node.js-Entwicklung** zusammen mit Visual Studio installieren. Weitere Informationen dazu, wie Sie den Sprachdienst für TypeScript erhalten, finden Sie unter [TypeScript-Unterstützung](../javascript/javascript-in-vs-2019.md#typescript-support).

In diesem Artikel wird vorausgesetzt, dass Sie bereits mit der JavaScript-Entwicklung vertraut sind. Wenn dies nicht der Fall ist, sollten Sie sich zunächst ein Tutorial dazu ansehen, z. B.: [Erstellen einer Node.js- und Express-App in Visual Studio](../javascript/tutorial-nodejs.md).

## <a name="add-a-new-project-file"></a>Hinzufügen einer neuen Projektdatei

Sie können mithilfe der IDE neue Dateien zu Ihrem Projekt hinzufügen.

1. Öffnen Sie Ihr Projekt in Visual Studio, klicken Sie im Projektmappen-Explorer (auf der rechten Seite) mit der rechten Maustaste auf einen Ordner oder Ihren Projektknoten, und klicken Sie anschließend auf **Hinzufügen** > **Neues Element**.

1. Wählen Sie unter der Kategorie **Allgemein** im Dialogfeld **Neue Datei** den Dateityp (z. B. **JavaScript-Datei**) aus, der hinzugefügt werden soll, und klicken Sie anschließend auf **Öffnen**.

    Dann wird die neue Datei zu Ihrem Projekt hinzugefügt und im Editor geöffnet.

## <a name="use-intellisense-to-complete-words"></a>Verwenden von IntelliSense zum Vervollständigen von Wörtern

IntelliSense ist eine wichtige Ressource beim Programmieren. Damit erhalten Sie Informationen zu verfügbaren Members eines Typs oder Parameterdetails für verschiedene Überladungen einer Methode. Wenn Sie beim folgenden Code `Router()` eingeben, werden die Argumenttypen angezeigt, die übergeben werden können. Dies wird als Signaturhilfe bezeichnet.

![Screenshot eines Visual Studio-Codefensters, in dem JavaScript-Code eingegeben wird. IntelliSense-Informationen werden für die Router()-Funktion angezeigt.](../javascript/media/write-code-signature-checking.png)

Sie können IntelliSense auch verwenden, um Wörter zu vervollständigen, nachdem genug Zeichen eingegeben wurden, um sie eindeutig zu machen. Wenn Sie Ihren Cursor im folgenden Code am Ende der `data`-Zeichenfolge platzieren und `get` eingeben, zeigt IntelliSense Ihnen Funktionen an, die an einer früheren Stelle im Code oder in der Bibliothek eines Drittanbieters definiert wurden, die Sie zu dem Projekt hinzugefügt haben.

![Screenshot eines Visual Studio-Codefensters, in dem das Wort „get“ eingegeben wird. IntelliSense-Informationen werden für alle Funktionen angezeigt, beginnend mit „get“.](../javascript/media/write-code-intellisense.png)

Außerdem kann IntelliSense Ihnen Informationen zu Typen anzeigen, wenn Sie mit dem Cursor auf Programmierelemente zeigen.

Der Sprachdienst kann TypeScript-Dateien (*d.ts*) und JSDoc-Kommentare verwenden, um IntelliSense-Informationen bereitzustellen. Für die am häufigsten verwendeten JavaScript-Bibliotheken werden *D.TS*-Dateien automatisch abgerufen. Weitere Informationen zum Abrufen von IntelliSense-Informationen finden Sie unter [JavaScript-IntelliSense](../ide/javascript-intellisense.md?toc=/visualstudio/javascript/toc.json).

## <a name="check-syntax"></a>Überprüfen der Syntax

Der Sprachdienst verwendet ESLint zur Bereitstellung von Linting und der Syntaxprüfung. Wenn Sie Optionen für die Syntaxprüfung im Editor festlegen müssen, klicken Sie auf **Extras** > **Optionen** > **JavaScript/TypeScript** > **Linting**. Die Lintingoptionen verweisen auf die globale ESLint-Konfigurationsdatei.

Im folgenden Code werden Syntaxelemente im Ausdruck mit grünen Wellenlinien hervorgehoben. Zeigen Sie auf die Syntaxhervorhebung.

![Syntaxfehler anzeigen](../javascript/media/write-code-syntax-checking.png)

Die letzte Zeile dieser Meldung besagt, dass der Sprachdienst ein Komma (`,`) erwartet hat. Die grüne Wellenlinie deutet auf eine Warnung hin. Rote Wellenlinien werden bei Fehlern angezeigt.

Im unteren Bereich können Sie auf die Registerkarte **Fehlerliste** klicken, um die Warnung und die Beschreibung sowie den Dateinamen und die Zeilennummer anzuzeigen.

![Fehlerliste anzeigen](../javascript/media/write-code-error-list.png)

Sie können den Code korrigieren, indem Sie das Komma (`,`) vor `"data"` hinzufügen.

Weitere Informationen zum Linten finden Sie unter [Linting](https://github.com/microsoft/JSTSdocs/blob/master/articles/editor/linting.md).

## <a name="comment-out-code"></a>Auskommentieren von Code

Durch die Symbolleiste – der Zeile mit Schaltflächen unter der Menüleiste in Visual Studio – können Sie Ihre Produktivität beim Codieren steigern. Sie können beispielsweise den IntelliSense-Beendigungsmodus umschalten ([IntelliSense](../ide/using-intellisense.md) ist eine Codierungshilfe, die u.a. eine Liste von übereinstimmenden Methoden anzeigt), einen Zeileneinzug verkleinern oder vergrößern oder Code auskommentieren, der nicht kompiliert werden soll. In diesem Abschnitt wird Code auskommentiert.

Wählen Sie mindestens eine Codezeile im Editor aus, und klicken Sie anschließend in der Symbolleiste auf die Schaltfläche **Comment out the selected lines** (Ausgewählte Zeilen auskommentieren) ![Schaltfläche „Auskommentieren“](../javascript/media/write-code-comment-out.png). Wenn Sie lieber die Tastatur verwenden möchten, drücken Sie **STRG**+**K**, **STRG**+**C**.

Die JavaScript-Kommentarzeichen `//` werden am Anfang jeder ausgewählten Zeile hinzugefügt, um den Code auszukommentieren.

## <a name="collapse-code-blocks"></a>Reduzieren von Codeblöcken

Wenn Sie die Ansicht für einige Coderegionen übersichtlicher gestalten möchten, können Sie diese reduzieren. Klicken Sie auf das kleine graue Feld mit dem Minuszeichen, das sich am Rand der ersten Zeile einer Funktion befindet. Wenn Sie lieber mit der Tastatur arbeiten, platzieren Sie den Cursor an einer beliebigen Stelle im Konstruktorcode, und drücken Sie **STRG**+**M**, **STRG**+**M**.

![Gliedern der Schaltfläche zum Reduzieren](../javascript/media/write-code-collapse-code.png)

Der Codeblock wird bis auf die erste Zeile reduziert, an die Auslassungspunkte angehängt werden (`...`). Klicken Sie nun auf dasselbe graue Feld, das diesmal mit einem Pluszeichen versehen ist, um den Codeblock erneut zu erweitern, oder drücken Sie zweimal **STRG**+**M**, **STRG**+**M**. Dieses Feature wird als [Gliedern](../ide/outlining.md) bezeichnet und ist besonders nützlich, wenn Sie lange Funktionen oder ganze Klassen reduzieren möchten.

## <a name="view-definitions"></a>Anzeigen von Definitionen

Der Visual Studio-Editor erleichtert u. a. die Prüfung der Definition eines Typs oder einer Funktion. Sie können z. B. zu der Datei mit der Definition navigieren, indem Sie an einer beliebigen Stelle, an der auf das Programmierelement verwiesen wird, auf **Gehe zu Definition** klicken. Sie können auch die Option [Definition einsehen](../ide/go-to-and-peek-definition.md#peek-definition) verwenden. Dies stellt eine schnellere Möglichkeit dar, bei der der Fokus weiterhin auf der Datei liegt. Sehen Sie sich die Definition der `render`-Methode im nachfolgenden Beispiel an.

Klicken Sie erst mit der rechten Maustaste auf `render` und anschließend im Inhaltsmenü mit der linken auf die Option **Definition einsehen**. Drücken Sie alternativ **ALT**+**F12**.

   Daraufhin wird ein Popupfenster mit der Definition der `render`-Methode angezeigt. Sie können in dem Popupfenster scrollen oder sogar die Definition eines anderen Typs des eingesehenen Codes einsehen.

   ![Fenster „Definition einsehen“](../javascript/media/write-code-peek-definition.png)

Schließen Sie das eingesehene Definitionsfenster, indem Sie auf das kleine „x“ in der oberen rechten Ecke des Popupfensters klicken.

## <a name="use-code-snippets"></a>Verwenden von Codeausschnitten

Visual Studio stellt nützliche *Codeausschnitte* bereit, die Sie verwenden können, um häufig verwendete Codeblöcke schnell und einfach zu generieren. Die [Codeausschnitte](../ide/code-snippets.md) sind für verschiedene Programmiersprachen verfügbar, einschließlich JavaScript. Fügen Sie nun eine `for`-Schleife zu Ihrer Codedatei hinzu.

Platzieren Sie den Cursor an einer beliebigen Stelle, um den Codeausschnitt einzufügen, führen Sie einen Rechtsklick durch, und wählen Sie **Ausschnitt** > **Ausschnitt einfügen** aus.

![Codeausschnitt in Visual Studio](../javascript/media/write-code-insert-snippet.png)

Dann wird das Feld **Ausschnitt einfügen** im Editor angezeigt. Klicken Sie erst auf **Allgemein**, und doppelklicken Sie anschließend auf das **for**-Element in der Liste.

![Codeausschnitt für eine for-Schleife in Visual Studio](../javascript/media/write-code-insert-snippet-for-loop.png)

Dadurch wird der Codeausschnitt für die `for`-Schleife zu Ihrem Code hinzugefügt:

```javascript
for (var i = 0; i < length; i++) {

}
```

Sie können sich die für Ihre Sprache verfügbaren Codeausschnitte anzeigen lassen, indem Sie **Bearbeiten** > **IntelliSense** > **Ausschnitt einfügen** und anschließend den Ordner für Ihre Sprache auswählen.

## <a name="see-also"></a>Siehe auch

- [Codeausschnitte](../ide/code-snippets.md)
- [Navigieren durch den Code](../ide/navigating-code.md)
- [Gliedern](../ide/outlining.md)
- [Go To Definition and Peek Definition („Gehe zu Definition“ und „Definition einsehen“)](../ide/go-to-and-peek-definition.md)
- [Refactoring](../ide/refactoring-in-visual-studio.md)
- [Verwendung von IntelliSense](../ide/using-intellisense.md)
