---
title: Dialogfeld „Zeichenfolgenschnellansicht“ | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie während des Debuggens in Visual Studio Zeichenfolgen mit dem integrierten Dialogfeld „Zeichenfolgenschnellansicht“ anzeigen.
ms.date: 10/10/2018
ms.custom: seoapril2019, SEO-VS-2020
ms.topic: reference
f1_keywords:
- vs.debug.stringviewer
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JavaScript
helpviewer_keywords:
- string visualizer
- visualizers, string
ms.assetid: 080fd8f1-72b0-461f-8451-3c84d5dc51df
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c33459312cb0c5c4dd4be3bc043956ccb33a6e1
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150274"
---
# <a name="string-visualizer-dialog-box"></a>Dialogfeld „Zeichenfolgen-Schnellansicht“

Beim Debuggen in Visual Studio können Sie Zeichenfolgen mit der integrierten Zeichenfolgenschnellansicht anzeigen. In der Zeichenfolgenschnellansicht werden Zeichenfolgen angezeigt, die zu lang für einen Datentipp oder ein Debuggerfenster sind. Sie kann auch dabei helfen, falsch formatierte Zeichenfolgen zu ermitteln.

Die integrierte Zeichenfolgenschnellansicht beinhaltet Optionen für Nur-Text, XML, HTML und JSON. Über das Fenster **Auto** oder andere Debuggerfenster können Sie auch integrierte Schnellansichten für einige andere Typen (z. B. [DataSet-, DataTable- und DataView-Objekte](../debugger/dataset-visualizer-dialog-box.md)) öffnen.

> [!NOTE]
> Informationen zum Überprüfen von XAML- oder WPF-Benutzeroberflächenelemente in einer Schnellansicht finden Sie unter [Überprüfen von XAML-Eigenschaften beim Debuggen](../xaml-tools/inspect-xaml-properties-while-debugging.md) oder [Verwenden der WPF-Strukturschnellansicht](../debugger/how-to-use-the-wpf-tree-visualizer.md).

Das Debuggen muss pausiert sein, wenn Sie die Zeichenfolgenschnellansicht öffnen möchten. Zeigen Sie auf eine Variable mit einem Nur-Text-, XML-, HTML- oder JSON-Zeichenfolgenwert, und wählen Sie das Lupensymbol ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Symbol der Schnellansicht") aus.

## <a name="uielement-list"></a>UIElement-Liste

Das Feld **Ausdruck** zeigt die Variable oder den Ausdruck an, auf die oder den Sie zeigen.

Das Feld **Wert** zeigt den Zeichenfolgenwert an. Ist **Wert** leer, bedeutet das, dass die ausgewählte Schnellansicht die Zeichenfolge nicht erkennen kann. In der **XML-Schnellansicht** wird beispielsweise ein leerer **Wert** für eine Textzeichenfolge ohne XML-Tags oder für eine JSON-Zeichenfolge angezeigt. Wählen Sie stattdessen die **Text-Schnellansicht** aus, um Zeichenfolgen anzuzeigen, die von der ausgewählten Schnellansicht nicht erkannt werden. Von der **Text-Schnellansicht** wird Nur-Text angezeigt.

### <a name="json-string-data"></a>JSON-Zeichenfolgendaten

Eine wohlgeformte JSON-Zeichenfolge ähnelt der unten gezeigten Abbildung in der JSON-Schnellansicht. Für eine falsch formatierte JSON-Zeichenfolge wird unter Umständen ein Fehlersymbol (oder bei Nichterkennung ein leerer Wert) angezeigt. Kopieren Sie die Zeichenfolge, und fügen Sie sie in ein Tool für JSON-Linting (etwa [JSLint](https://www.jslint.com/)) ein, um den JSON-Fehler zu identifizieren.

![JSON-Zeichenfolgenschnellansicht](../debugger/media/dbg-tips-string-visualizer-json.png "JSON-Zeichenfolgenschnellansicht")

### <a name="xml-string-data"></a>XML-Zeichenfolgendaten

Eine wohlgeformte XML-Zeichenfolge ähnelt der unten gezeigten Abbildung in der XML-Schnellansicht. Eine falsch formatierte XML-Zeichenfolge wird möglicherweise ohne XML-Tags oder bei Nichterkennung als leerer Wert angezeigt.

![XML-Zeichenfolgenschnellansicht](../debugger/media/dbg-string-visualizers-xml.png "XML-Zeichenfolgenschnellansicht")

### <a name="html-string-data"></a>HTML-Zeichenfolgendaten

Eine wohlgeformte HTML-Zeichenfolge wird wie beim Rendern im Browser angezeigt, wie in der folgenden Abbildung dargestellt. Eine falsch formatierte HTML-Zeichenfolge wird möglicherweise als Nur-Text angezeigt.

![HTML-Zeichenfolgenschnellansicht](../debugger/media/dbg-string-visualizers-html.png "HTML-Zeichenfolgenschnellansicht")

## <a name="see-also"></a>Siehe auch

- [Erstellen von benutzerdefinierten Datenschnellansichten](../debugger/create-custom-visualizers-of-data.md)
- [Datenvisualisierungen](/visualstudio/mac/data-visualizations)