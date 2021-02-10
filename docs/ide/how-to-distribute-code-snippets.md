---
title: Verteilen von Codeausschnitten als Extension
description: Erfahren Sie, wie Sie Codeausschnitte mit dem Codeausschnitt-Manager an andere Entwickler verteilen.
ms.custom: SEO-VS-2020
ms.date: 03/21/2019
ms.topic: how-to
helpviewer_keywords:
- code snippets, distributing
ms.assetid: 5f717abd-e167-47ae-818c-6b0bae100ceb
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 65b60eb1156fe3d64081724e310a41a38b54af50
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969814"
---
# <a name="how-to-distribute-code-snippets"></a>Vorgehensweise: Verteilen von Codeausschnitten

Sie können die Codeausschnitte Ihren Freunden senden, und diese können die Ausschnitte mithilfe des **Codeausschnitt-Managers** auf ihren Computern installieren. Wenn Sie jedoch viele Ausschnitte verteilen möchten oder eine breitere Verteilung erforderlich ist, können Sie die Ausschnittdatei in eine Visual Studio-Extension einschließen. Visual Studio-Benutzer können die Extension anschließend installieren, um an die Codeausschnitte zu gelangen.

## <a name="prerequisites"></a>Voraussetzungen

Installieren Sie die Workload **Visual Studio-Extensionsentwicklung**, um Zugriff auf die **VSIX-Projekt**-Projektvorlagen zu erhalten.

![Visual Studio-Extensionentwicklung-Workload](media/vs-2019/extension-development-workload.png)

## <a name="set-up-the-extension"></a>Einrichten der Erweiterung

In diesem Verfahren verwenden Sie den „Hallo Welt“-Codeausschnitt aus [Exemplarische Vorgehensweise: Erstellen eines Codeausschnitts](../ide/walkthrough-creating-a-code-snippet.md). Dieser Artikel enthält den XML-Code des Codeausschnitts, Sie brauchen also nicht zurückzugehen und einen Codeausschnitt zu erstellen.

1. Erstellen Sie ein neues Projekt aus der Vorlage **Leeres VSIX-Projekt**, und nennen Sie das Projekt **TestSnippet**.

2. Fügen Sie im Projekt **TestSnippet** eine neue XML-Datei hinzu, und nennen Sie sie *VBCodeSnippet.snippet*. Ersetzen Sie den Inhalt durch folgenden XML-Code:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <CodeSnippets
        xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
      <CodeSnippet Format="1.0.0">
        <Header>
          <Title>Hello World VB</Title>
          <Shortcut>HelloWorld</Shortcut>
          <Description>Inserts code</Description>
          <Author>MSIT</Author>
          <SnippetTypes>
            <SnippetType>Expansion</SnippetType>
            <SnippetType>SurroundsWith</SnippetType>
          </SnippetTypes>
        </Header>
        <Snippet>
          <Code Language="VB">
            <![CDATA[Console.WriteLine("Hello, World!")]]>
          </Code>
        </Snippet>
      </CodeSnippet>
    </CodeSnippets>
    ```

### <a name="set-up-the-directory-structure"></a>Einrichten der Verzeichnisstruktur

1. Wählen Sie im **Projektmappen-Explorer** den Projektknoten aus, und fügen Sie einen Ordner mit dem Namen hinzu, den der Ausschnitt im **Codeausschnitt-Manager** aufweisen soll. In diesem Fall sollte der Name **HelloWorldVB** lauten.

2. Verschieben Sie die *SNIPPET*-Datei in den Ordner *HelloWorldVB*.

3. Klicken Sie im **Projektmappen-Explorer** auf die *SNIPPET*-Datei, und stellen Sie sicher, dass im Fenster **Eigenschaften** für die Eigenschaft **Buildvorgang** die Einstellung **Inhalt**, für die Eigenschaft **In Ausgabeverzeichnis kopieren** die Einstellung **Immer kopieren** und für die Eigenschaft **Include in VSIX** (In VSIX einbeziehen) die Einstellung **TRUE** ausgewählt ist.

### <a name="add-the-pkgdef-file"></a>Hinzufügen der PKGDEF-Datei

::: moniker range="vs-2017"

1. Fügen Sie dem Ordner *HelloWorldVB* eine Textdatei hinzu, und nennen Sie sie *HelloWorldVB.pkgdef*. Diese Datei wird verwendet, um der Registrierung bestimmte Schlüssel hinzufügen. In diesem Fall wird ein neuer Unterschlüssel zum Schlüssel **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Languages\CodeExpansions\Basic** hinzugefügt.

::: moniker-end

::: moniker range=">=vs-2019"

1. Fügen Sie dem Ordner *HelloWorldVB* eine Textdatei hinzu, und nennen Sie sie *HelloWorldVB.pkgdef*. Diese Datei wird verwendet, um der Registrierung bestimmte Schlüssel hinzufügen. In diesem Fall wird dem Schlüssel **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\16.0\Languages\CodeExpansions\Basic** ein neuer Unterschlüssel hinzugefügt.

::: moniker-end

2. Fügen Sie der Datei die folgenden Zeilen hinzu.

    ```txt
    // Visual Basic
    [$RootKey$\Languages\CodeExpansions\Basic\Paths]
    "HelloWorldVB"="$PackageFolder$"
    ```

    Wenn Sie diesen Schlüssel untersuchen, sehen Sie, wie verschiedene Sprachen angegeben werden.

3. Wählen Sie im **Projektmappen-Explorer** die *PKGDEF*-Datei aus, und stellen Sie im Fenster **Eigenschaften** Folgendes sicher:

   - **Buildvorgang** ist auf **Inhalt** festgelegt
   - **In Ausgabeverzeichnis kopieren** ist auf **Immer kopieren** festgelegt
   - **Include in VSIX** (In VSIX einbeziehen) ist auf **TRUE** festgelegt

4. Fügen Sie dem VSIX-Manifest die *PKGDEF*-Datei als Ressource hinzu. Wechseln Sie in der Datei *source.extension.vsixmanifest* zur Registerkarte **Objekte**, und klicken Sie auf **Neu**.

5. Legen Sie im Dialogfeld **Neue Anlage hinzufügen** für **Typ** die Einstellung **Microsoft.VisualStudio.VsPackage** fest, für **Quelle** die Einstellung **Datei im Dateisystem** und für **Pfad** die Einstellung **HelloWorldVB.pkgdef** (sollte in der Dropdownliste angezeigt werden).

### <a name="test-the-snippet"></a>Testen des Ausschnitts

1. Jetzt können Sie sicherstellen, dass der Codeausschnitt in der experimentellen Instanz von Visual Studio funktioniert. Die experimentelle Instanz ist eine zweite Kopie von Visual Studio, die unabhängig von der Instanz ist, die Sie zum Schreiben von Code verwenden. So können Sie ohne Auswirkungen auf Ihre Entwicklungsumgebung an einer Erweiterung arbeiten.

2. Erstellen Sie das Projekt, und starten Sie das Debugging.

   Eine zweite Instanz von Visual Studio wird geöffnet.

3. Wechseln Sie in der experimentellen Instanz zu **Extras** > **Codeausschnitt-Manager**, und wählen Sie für **Sprache** die Einstellung **Basic** aus. *HelloWorldVB* sollte als einer der Ordner angezeigt werden, und wenn Sie den Ordner erweitern, sollten Sie den Ausschnitt *HelloWorldVB* sehen.

4. Speichern Sie den Ausschnitt. Öffnen Sie in der experimentellen Instanz ein Visual Basic-Projekt, und öffnen Sie dann eine der Codedateien. Platzieren Sie den Cursor an einer beliebigen Stelle im Code, klicken Sie mit der rechten Maustaste, und wählen Sie im Kontextmenü den Befehl **Ausschnitt einfügen**.

5. *HelloWorldVB* sollte als einer der Ordner angezeigt werden. Doppelklicken Sie darauf. Es sollte ein Popupfenster **Ausschnitt einfügen: HelloWorldVB >** mit der Dropdownliste **HelloWorldVB** angezeigt werden. Klicken Sie auf die Dropdownliste **HelloWorldVB**.

   Die folgende Zeile wird an die Codedatei angefügt:

    ```vb
    Console.WriteLine("Hello, World!")
    ```

## <a name="see-also"></a>Siehe auch

- [Codeausschnitte](../ide/code-snippets.md)
