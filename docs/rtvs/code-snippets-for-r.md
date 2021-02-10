---
title: Codeausschnitte für R
description: Codeausschnitte für R in Visual Studio bieten Verknüpfungen zum schnellen Einfügen von Codeblöcken mit beliebiger Länge – so kann das wiederholte Eingeben von ähnlichem Code vermieden werden.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: ca2bc533f26843dcfc22eb1129a66020cd8a5a03
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885806"
---
# <a name="code-snippets-for-r"></a>Codeausschnitte für R

Codeausschnitte in Visual Studio bieten Verknüpfungen zum schnellen Einfügen von Codeblöcken mit beliebiger Länge, und es wird vermieden, dass der gleiche Code immer wieder eingegeben werden muss. Die R Tools für Visual Studio (RTVS) fügen Dutzende nützlicher R-Ausschnitte zur Sammlung von Visual Studio hinzu.

Geben Sie den abgekürzten Namen des Ausschnitts ein (IntelliSense wird bereitgestellt), und drücken Sie dann die **TAB-Taste**, um den Ausschnitt einzufügen.

Hier sind einige einfache Beispiele:

- geben Sie `=` ein, was mithilfe der TAB-Taste und RTVS zum Zuweisungsoperator `<-` erweitert wird.
- geben Sie `>` ein, was mithilfe der TAB-Taste und RTVS zum Pipeoperator `%>%` erweitert wird.

Ausschnitte können viel mehr sein als nur die Zeichenvervollständigung von Zeichen. Durch einen Ausschnitt zum Lesen einer CSV-Datei mit der `read.csv`-Funktion müssen Sie sich zum Beispiel nicht mehr die Namen und Parameter merken:

![Animation der Verwendung eines Codeausschnitts zum Einfügen eines Aufrufs von „read.csv“](media/code-snippet-expansion.gif)

In diesem Fall zeigt IntelliSense eine Vervollständigungsliste an, wenn Sie `readc` eintippen. Wenn Sie den vervollständigten Eintrag in der Dropdownliste auswählen und die **TAB-Taste** drücken, wird `readc` ausgewählt. Wenn Sie erneut die **TAB-Taste** drücken, wird der Ausschnitt erweitert. (Aus diesem Grund wird die Ausschnitterweiterung oft mit „den Ausschnitt eintippen und die TAB-Taste zweimal drücken“ gleichgesetzt). In den meisten Fällen beendet das erste Drücken der TAB-Taste die IntelliSense-Auswahl, und ein erneutes Drücken der TAB-Taste löst die Erweiterung aus.

Öffnen Sie das Dialogfeld **Extras** > **Codeausschnitt-Manager** (**STRG**+**K**,**B**), und wählen Sie für **Sprache****R** aus, um alle verfügbaren Ausschnitte anzuzeigen. Erweitern Sie die Gruppen, und wählen Sie einzelne Ausschnitte aus, um eine Beschreibung sowie den Verknüpfungstext anzuzeigen:

![Dialogfeld „Codeausschnitt-Manager“ für R](media/code-snippet-dialog.png)

Führen Sie die Schritte unter [Exemplarische Vorgehensweise: Erstellen eines Codeausschnitts](../ide/walkthrough-creating-a-code-snippet.md) aus, um benutzerdefinierte Codeausschnitte zu erstellen. Letztendlich ist ein Codeausschnitt nur eine XML-Datei. Der folgende Code stellt beispielsweise den Ausschnitt für einen Pipevorgang dar (Verknüpfung `>`):

```xml
<?xml version="1.0" encoding="utf-8" ?>
<CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
  <CodeSnippet Format="1.0.0">
    <Header>
      <Title>Dplyr pipe</Title>
      <Shortcut>&gt;</Shortcut>
      <Description>Code snippet for '%&gt;%' operator</Description>
      <Author>Microsoft Corporation</Author>
      <SnippetTypes>
        <SnippetType>Expansion</SnippetType>
       </SnippetTypes>
    </Header>
    <Snippet>
      <Code Language="R">
        <![CDATA[ %>% $end$]]>
      </Code>
    </Snippet>
  </CodeSnippet>
</CodeSnippets>
```

Die XML-Dateien für alle Codeausschnitte werden mit RTVS installiert, und das Feld **Speicherort** im **Codeausschnitt-Manager** stellt den Pfad bereit. Sie können sie auch im RTVS-Quellcode auf GitHub unter [src/Package/Impl/Snippets](https://github.com/Microsoft/RTVS/tree/master/src/Package/Impl/Snippets) finden.
