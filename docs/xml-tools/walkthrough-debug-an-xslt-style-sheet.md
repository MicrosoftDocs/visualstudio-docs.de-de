---
title: Debuggen von XSLT-Stylesheets
description: In diesem Artikel erfahren Sie, wie Sie den XSLT-Debugger in Visual Studio verwenden, um ein XSLT-Stylesheet zu debuggen, indem Sie die Schritte in dieser exemplarischen Vorgehensweise ausführen.
ms.custom: SEO-VS-2020
ms.date: 03/05/2019
ms.topic: how-to
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c69f93aca88cb8e83417a370de7113640d3ae38c
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351335"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>Exemplarische Vorgehensweise: Debuggen eines XSLT-Stylesheets

Anhand der Schritte in dieser exemplarischen Vorgehensweise wird die Verwendung des XSLT-Debuggers veranschaulicht. Zu den Schritten gehören das Anzeigen von Variablen, das Festlegen von Haltepunkten und das schrittweise Ausführen des Codes. Mithilfe des Debuggers können Sie Code zeilenweise ausführen.

Als Vorbereitung für diese exemplarische Vorgehensweise kopieren Sie zunächst die beiden [Beispieldateien](#sample-files) auf Ihren lokalen Computer. Eine der Dateien ist das Stylesheet, die andere die XML-Datei, die wir als Eingabe für das Stylesheet verwenden werden. In dieser exemplarischen Vorgehensweise findet das verwendete Stylesheet alle Bücher, deren Kosten unter dem durchschnittlichen Buchpreis liegen.

> [!NOTE]
> Der XSLT-Debugger ist nur in der Enterprise Edition von Visual Studio verfügbar.

## <a name="start-debugging"></a>Debugging starten

1. Wählen Sie im Menü **Datei** den Pfad **Öffnen** > **Datei** aus.

2. Suchen Sie die Datei *below-average.xsl*, und wählen Sie **Öffnen** aus.

   Das Stylesheet wird im XML-Editor geöffnet.

3. Klicken Sie im Dokumenteigenschaftenfenster im Feld **Eingabe** auf die Schaltfläche zum Durchsuchen ( **...** ). (Wenn das Fenster **Eigenschaften** nicht angezeigt wird, klicken Sie mit der rechten Maustaste auf eine beliebige Stelle in der geöffneten Datei im Editor, und wählen Sie dann **Eigenschaften** aus.)

4. Suchen Sie die Datei *books.xml*, und wählen Sie dann **Öffnen** aus.

   Damit legen Sie die Quelldokumentdatei fest, die für die XSLT-Transformation verwendet wird.

5. Legen Sie einen [Haltepunkt](../debugger/using-breakpoints.md) in Zeile 12 der Datei *below-average.xsl* fest. Hierfür gibt es mehrere Möglichkeiten:

   - Klicken Sie in Zeile 12 auf den Rand des Editors.

   - Klicken Sie auf eine beliebige Stelle in Zeile 12, und drücken Sie dann **F9**.

   - Klicken Sie mit der rechten Maustaste auf das `xsl:if`-Starttag, und wählen Sie dann **Haltepunkt** > **Haltepunkt einfügen** aus.

      ![Haltepunkt in XSL-Datei in Visual Studio einfügen](media/insert-breakpoint.PNG)

6. Wählen Sie auf der Menüleiste **XML** > **XSLT-Debugging starten** aus (oder drücken Sie **ALT**+**F5**).

   Der Debugprozess wird gestartet.

   Im Editor befindet sich der Debugger auf dem `xsl:if`-Element des Stylesheets. Eine weitere Datei mit dem Namen *below-average.xml* wird im Editor geöffnet. Dies ist die Ausgabedatei, die aufgefüllt wird, während die einzelnen Knoten in der Eingabedatei *books.xml* verarbeitet werden.

   Die Fenster **Auto**, **Lokal** und **Überwachen 1** werden unten im Visual Studio-Fenster angezeigt. Im Fenster **Lokal** werden alle lokalen Variablen mit ihren aktuellen Werten angezeigt. Das schließt die im Stylesheet definierten Variablen sowie Variablen ein, anhand derer der Debugger die Knoten verfolgt, die sich derzeit im Kontext befinden.

## <a name="watch-window"></a>Überwachungsfenster

Wir fügen dem Fenster **Überwachen 1** zwei Variablen hinzu, damit wir ihre Werte überprüfen können, wenn die Eingabedatei verarbeitet wird. (Sie können auch das Fenster **Lokal** verwenden, um Werte zu überprüfen, wenn die zu überwachenden Variablen bereits vorhanden sind.)

1. Wählen Sie im Menü **Debuggen** den Pfad **Fenster** > **Überwachung** > **Überwachen 1** aus.

   Das Fenster **Überwachen 1** wird angezeigt.

2. Geben Sie `$bookAverage` in das Feld **Name** ein, und drücken Sie dann die **EINGABETASTE**.

   Der Wert der Variablen `$bookAverage` wird im Feld **Wert** angezeigt.

3. Geben Sie in der nächsten Zeile `self::node()` in das Feld **Name** ein, und drücken Sie dann die **EINGABETASTE**.

   `self::node()` ist ein XPath-Ausdruck, der den aktuellen Kontextknoten auswertet. Der Wert des `self::node()`-XPath-Ausdrucks ist der erste book-Knoten. Dieser ändert sich im Laufe der Transformation.

4. Erweitern Sie den Knoten `self::node()`, und erweitern Sie dann den Knoten mit dem Wert `price`.

   ![Überwachungsfenster während des XSLT-Debuggens in Visual Studio](media/xslt-debugging-watch-window.png)

   Sie können den Wert des Buchpreises für den aktuellen Buchknoten anzeigen und ihn mit dem Wert `$bookAverage` vergleichen. Da der Buchpreis unter dem Durchschnitt liegt, sollte die `xsl:if`-Bedingung erfüllt sein, wenn Sie den Debugvorgang fortsetzen.

## <a name="step-through-the-code"></a>Schrittweises Ausführen des Codes

1. Drücken Sie **F5**, um fortzufahren.

   Da der erste Buchknoten die `xsl:if`-Bedingung erfüllt, wird der Buchknoten zur Ausgabedatei *below-average.xml* hinzugefügt. Der Debugger setzt die Ausführung fort, bis er sich wieder am `xsl:if`-Element im Stylesheet befindet. Der Debugger befindet sich jetzt am zweiten Buchkonten in der Datei *books.xml*.

   Im Fenster **Überwachen 1** ändert sich der Wert `self::node()` in den zweiten Buchknoten. Durch Auswertung des Werts für das Preiselement können Sie feststellen, dass der Preis über dem Durchschnitt liegt und folglich die `xsl:if`-Bedingung fehlschlägt.

2. Drücken Sie **F5**, um fortzufahren.

   Da der zweite Buchknoten nicht die `xsl:if`-Bedingung erfüllt, wird der Buchknoten nicht zur Ausgabedatei *below-average.xml* hinzugefügt. Der Debugger setzt die Ausführung fort, bis er sich wieder am `xsl:if`-Element im Stylesheet befindet. Der Debugger befindet sich jetzt am dritten `book`-Knoten in der Datei *books.xml*.

   Im Fenster **Überwachen 1** wird der `self::node()`-Wert in den dritten Buchknoten geändert. Durch Auswertung des Werts für das `price`-Element können Sie feststellen, dass der Preis unter dem Durchschnitt liegt. Die `xsl:if`-Bedingung sollte erfüllt sein.

3. Drücken Sie **F5**, um fortzufahren.

   Da die `xsl:if`-Bedingung erfüllt war, wird das dritte Buch zur Ausgabedatei *below-average.xml* hinzugefügt. Alle Bücher im XML-Dokument wurden verarbeitet, und der Debugger wird beendet.

## <a name="sample-files"></a>Beispieldateien

Bei der exemplarischen Vorgehensweise werden die folgenden zwei Dateien verwendet.

### <a name="below-averagexsl"></a>below-average.xsl

```xml
<?xml version='1.0'?>
<xsl:stylesheet version="1.0"
      xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:output method="xml" encoding="utf-8"/>
  <xsl:template match="/">
    <xsl:variable name="bookCount" select="count(/bookstore/book)"/>
    <xsl:variable name="bookTotal" select="sum(/bookstore/book/price)"/>
    <xsl:variable name="bookAverage" select="$bookTotal div $bookCount"/>
    <books>
      <!--Books That Cost Below Average-->
      <xsl:for-each select="/bookstore/book">
        <xsl:if test="price &lt; $bookAverage">
          <xsl:copy-of select="."/>
        </xsl:if>
      </xsl:for-each>
    </books>
  </xsl:template>
</xsl:stylesheet>
```

### <a name="booksxml"></a>books.xml

```xml
<?xml version='1.0'?>
<!-- This file represents a fragment of a book store inventory database -->
<bookstore>
  <book genre="autobiography" publicationdate="1981" ISBN="1-861003-11-0">
    <title>The Autobiography of Benjamin Franklin</title>
    <author>
      <first-name>Benjamin</first-name>
      <last-name>Franklin</last-name>
    </author>
    <price>8.99</price>
  </book>
  <book genre="novel" publicationdate="1967" ISBN="0-201-63361-2">
    <title>The Confidence Man</title>
    <author>
      <first-name>Herman</first-name>
      <last-name>Melville</last-name>
    </author>
    <price>11.99</price>
  </book>
  <book genre="philosophy" publicationdate="1991" ISBN="1-861001-57-6">
    <title>The Gorgias</title>
    <author>
      <name>Plato</name>
    </author>
    <price>9.99</price>
  </book>
</bookstore>
```

## <a name="see-also"></a>Siehe auch

- [Debuggen von XSLT](../xml-tools/debugging-xslt.md)
