---
title: 'Exemplarische Vorgehensweise: Erstellen eines Codeausschnitts'
description: 'Hier erfahren Sie, wie Sie in drei Schritten einen Codeausschnitt erstellen: Sie müssen nur eine XML-Datei erstellen, die entsprechenden Elemente eintragen und den Code hinzufügen.'
ms.custom: SEO-VS-2020
ms.date: 03/31/2020
ms.topic: how-to
helpviewer_keywords:
- code snippets, creating
- code snippets, shortcut
- code snippets, template
- code snippets, replacements
- code snippets, references
- code snippets, imports
ms.assetid: 0dcaae11-39cf-4463-9c90-2494321251c2
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 61b7f227344f00fe277d4bf062f83bd3c1d79fd5
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479640"
---
# <a name="walkthrough-create-a-code-snippet"></a>Exemplarische Vorgehensweise: Erstellen eines Codeausschnitts

Ein Codeausschnitt kann in wenigen Schritten erstellt werden. Sie müssen nur eine XML-Datei erstellen, die entsprechenden Elemente eintragen und den Code hinzufügen. Sie können optional Ersetzungsparameter und Projektverweise verwenden. Importieren Sie den Codeausschnitt über die Schaltfläche **Importieren** im **Codeausschnitt-Manager** (**Tools** > **Codeausschnitt-Manager**) in Ihre Visual Studio-Installation.

## <a name="snippet-template"></a>Ausschnittvorlage

Der folgende XML-Code ist eine einfache Ausschnittvorlage:

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title></Title>
        </Header>
        <Snippet>
            <Code Language="">
                <![CDATA[]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="create-a-code-snippet"></a>Erstellen eines Codeausschnitts

1. Erstellen Sie eine neue XML-Datei in Visual Studio, und fügen Sie die oben gezeigten Vorlage hinzu.

2. Geben Sie den Titel des Ausschnitts in das Element **Titel** ein. Verwenden Sie den Titel **Square Root**.

3. Tragen Sie die Sprache des Ausschnitts in das **Sprachen**-Attribut des **Code**-Elements ein. Für C# verwenden Sie **CSharp**, für Visual Basic **VB** und für C++ **CPP**.

   > [!TIP]
   > Alle verfügbaren Sprachwerte finden Sie im Abschnitt der [Attribute](code-snippets-schema-reference.md#attributes) für Codeelemente auf der Seite [Schemareferenz für Codeausschnitte](code-snippets-schema-reference.md).

4. Fügen Sie den Codeausschnitt im **CDATA**-Abschnitt innerhalb des Elements **Code** hinzu.

   Für C#:

   ```xml
   <Code Language="CSharp">
       <![CDATA[double root = Math.Sqrt(16);]]>
   </Code>
   ```

   Oder für Visual Basic:

   ```xml
   <Code Language="VB">
       <![CDATA[Dim root = Math.Sqrt(16)]]>
   </Code>
   ```

   > [!NOTE]
   > Sie können nicht angeben, wie Codezeilen im **CDATA**-Abschnitt eines Codeausschnitts eingezogen oder formatiert werden sollten. Beim Einfügen formatiert der Sprachdienst den eingefügten Code automatisch.

5. Speichern Sie den Codeausschnitt als *SquareRoot.snippet* (Sie können einen beliebigen Speicherort auswählen).

## <a name="import-a-code-snippet"></a>Importieren eines Codeausschnitts

1. Sie können einen Codeausschnitt mithilfe des **Codeausschnitt-Managers** in Ihre Visual Studio-Installation importieren. Wählen Sie **Tools** > **Codeausschnitt-Manager** aus.

2. Klicken Sie auf die Schaltfläche **Importieren**.

3. Wechseln Sie zum Speicherort des Codeausschnitts aus der vorherigen Prozedur, klicken Sie zuerst darauf und anschließend auf **Öffnen**.

4. Das Dialogfeld **Codeausschnitt importieren** öffnet sich, und Sie werden aufgefordert, aus den Optionen im rechten Bereich auszuwählen, wo der Ausschnitt hinzugefügt werden soll. Die Option **Meine Codeausschnitte** sollte dabei zur Auswahl stehen. Wählen Sie diese Option aus, klicken Sie auf **Fertig stellen** und anschließend auf **OK**.

5. Der Codeausschnitt wird je nach Codesprache in einen der folgenden Speicherorte kopiert:

   ::: moniker range="vs-2017"

   *%USERPROFILE%\Documents\Visual Studio 2017\Code Snippets\Visual C#\My Code Snippets*  
   *%USERPROFILE%\Documents\Visual Studio 2017\Code Snippets\Visual Basic\My Code Snippets*

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   *%USERPROFILE%\Documents\Visual Studio 2019\Code Snippets\Visual C#\My Code Snippets*  
   *%USERPROFILE%\Documents\Visual Studio 2019\Code Snippets\Visual Basic\My Code Snippets*

   ::: moniker-end

6. Testen Sie den Ausschnitt, indem Sie ein C#- oder Visual Basic-Projekt öffnen. Wenn eine Codedatei im Editor offen ist, wählen Sie im Kontextmenü die Optionen **Codeausschnitte** > **Ausschnitt einfügen** und dann **Meine Codeausschnitte** aus. Es sollte ein Codeausschnitt namens **Square Root** angezeigt werden. Doppelklicken Sie darauf.

   Der Codeausschnitt wird in die Codedatei eingefügt.

## <a name="description-and-shortcut-fields"></a>Beschreibungs- und Verknüpfungsfelder

::: moniker range="vs-2017"

1. Beschreibungsfelder liefern Informationen über den Codeabschnitt, wenn sie im Codeausschnitt-Manager angezeigt werden. Die Verknüpfung ist ein Tag, das Benutzer zum Einfügen Ihres Codeausschnitts eingeben können. Bearbeiten Sie den Ausschnitt, den Sie hinzugefügt haben, indem Sie die Datei *%USERPROFILE%\Documents\Visual Studio 2017\Code Snippets\\[Visual C# oder Visual Basic]\My Code Snippet\SquareRoot.snippet* öffnen.

::: moniker-end

::: moniker range=">=vs-2019"

1. Beschreibungsfelder liefern Informationen über den Codeabschnitt, wenn sie im Codeausschnitt-Manager angezeigt werden. Die Verknüpfung ist ein Tag, das Benutzer zum Einfügen Ihres Codeausschnitts eingeben können. Bearbeiten Sie den Ausschnitt, den Sie hinzugefügt haben, indem Sie die Datei *%USERPROFILE%\Documents\Visual Studio 2019\Code Snippets\\[Visual C# oder Visual Basic]\My Code Snippet\SquareRoot.snippet* öffnen.

::: moniker-end

   > [!TIP]
   > Da Sie die Datei in dem Verzeichnis bearbeiten, in dem sie von Visual Studio platziert wurde, müssen Sie die Datei nicht erneut in Visual Studio importieren.

2. Fügen Sie dem **Header**-Element **Autor**- und **Beschreibungs**-Elemente hinzu, und füllen Sie diese aus.

3. Das **Header**-Element sollte in etwa wie folgt aussehen:

   ```xml
   <Header>
       <Title>Square Root</Title>
       <Author>Myself</Author>
       <Description>Calculates the square root of 16.</Description>
   </Header>
   ```

4. Öffnen Sie den **Codeausschnitt-Manager**, und wählen Sie Ihren Codeausschnitt aus. Beachten Sie, dass die Felder **Beschreibung** und **Autor** im rechten Bereich jetzt aufgefüllt sind.

   ![Beschreibung für Codeausschnitte im Codeausschnitt-Manager](media/code-snippet-description-author.png)

5. Um eine Verknüpfung hinzuzufügen, fügen Sie ein Element **Verknüpfung** im Element **Header** hinzu:

   ```xml
   <Header>
      <Title>Square Root</Title>
      <Author>Myself</Author>
      <Description>Calculates the square root of 16.</Description>
      <Shortcut>sqrt</Shortcut>
    </Header>
   ```

6. Speichern Sie die Ausschnittdatei erneut.

7. Um die Verknüpfung zu testen, öffnen Sie das Projekt, das Sie zuvor verwendet haben, geben Sie **sqrt** im Editor ein, und drücken Sie die **TABULATORTASTE** (einmal für Visual Basic, zweimal für C#).

   Der Codeausschnitt wird eingefügt.

## <a name="replacement-parameters"></a>Ersetzungsparameter

Möglicherweise sollen Teile eines Codeausschnitts vom Benutzer ersetzt werden können. Beispielsweise soll ein Benutzer einen Variablennamen durch einen Namen aus seinem aktuellen Projekt ersetzen können. Sie können zwei Typen von Ersetzungen bereitstellen: Literale und Objekte. Verwenden Sie das [Literalelement](code-snippets-schema-reference.md#literal-element), um eine Ersetzung für ein Codeelement zu kennzeichnen, das zwar vollständig im Ausschnitt enthalten ist, nach dem Einfügen in den Code jedoch wahrscheinlich geändert wird (z.B. eine Zeichenfolge oder ein numerischer Wert). Verwenden Sie das [Objektelement](code-snippets-schema-reference.md#object-element) um ein Element zu kennzeichnen, das vom Codeausschnitt benötigt wird, aber wahrscheinlich außerhalb des Codeausschnitts selbst definiert wird (z.B. eine Objektinstanz oder ein Steuerelement).

1. Um es dem Benutzer zu ermöglichen, problemlos die Zahl zu ersetzen, aus der die Quadratwurzel berechnet werden soll, ändern Sie das Element **Snippet** der Datei *SquareRoot.snippet* wie folgt:

   ```xml
   <Snippet>
     <Code Language="CSharp">
       <![CDATA[double root = Math.Sqrt($Number$);]]>
     </Code>
     <Declarations>
       <Literal>
         <ID>Number</ID>
         <ToolTip>Choose the number you want the square root of.</ToolTip>
         <Default>16</Default>
       </Literal>
     </Declarations>
   </Snippet>
   ```

   Beachten Sie, dass die Literalersetzung eine ID erhält (`Number`). Auf diese ID wird aus dem Codeausschnitt verwiesen, indem sie mit `$`-Zeichen umgeben wird:

   ```xml
   <![CDATA[double root = Math.Sqrt($Number$);]]>
   ```

2. Speichern Sie die Ausschnittdatei.

3. Öffnen Sie ein Projekt, und fügen Sie den Ausschnitt ein.

   Der Codeausschnitt wird eingefügt, und das Literal, das bearbeitet werden kann, wird für die Ersetzung hervorgehoben. Zeigen Sie auf den Ersetzungsparameter, um die QuickInfo für den Wert anzuzeigen.

   ![QuickInfo für Ersetzungsparameter in Codeausschnitt in Visual Studio](media/snippet-replacement-parameter-tooltip.png)

   > [!TIP]
   > Wenn ein Codeausschnitt mehr als einen ersetzbaren Parameter enthält, können Sie die **TABULATORTASTE** drücken, um zwischen den Parametern zu navigieren und die Werte zu ändern.

## <a name="import-a-namespace"></a>Importieren eines Namespace

Sie können einen Codeausschnitt verwenden, um eine `using`-Direktive (C#) oder `Imports`-Anweisung (Visual Basic) hinzufügen, indem Sie das [Imports-Element](code-snippets-schema-reference.md#imports-element) hinzufügen. Bei .NET Framework-Projekten können Sie auch mithilfe des [References-Elements](code-snippets-schema-reference.md#references-element) einen Verweis auf das Projekt hinzufügen.

Der folgende XML-Code zeigt einen Codeausschnitt, der die Methode `File.Exists` im System.IO-Namespace verwendet und daher das **Imports**-Element definiert, um den System.IO-Namespace zu importieren.

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
  <CodeSnippet Format="1.0.0">
    <Header>
      <Title>File Exists</Title>
      <Shortcut>exists</Shortcut>
    </Header>
    <Snippet>
      <Code Language="CSharp">
        <![CDATA[var exists = File.Exists("C:\\Temp\\Notes.txt");]]>
      </Code>
      <Imports>
        <Import>
          <Namespace>System.IO</Namespace>
        </Import>
      </Imports>
    </Snippet>
  </CodeSnippet>
</CodeSnippets>
```

## <a name="see-also"></a>Siehe auch

- [Schemareferenz für Codeausschnitte](../ide/code-snippets-schema-reference.md)
