---
title: 'Exemplarische Vorgehensweise: Verwenden der XSLT-Hierarchie'
description: Hier erfahren Sie, wie Sie ein Stylesheet, auf das verwiesen wird, mit dem XSLT-Hierarchietool in Visual Studio debuggen, indem Sie die Schritte in dieser exemplarischen Vorgehensweise ausführen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 68018c625c5e406e2ba0d7fbfb138b05c53fff9c
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351322"
---
# <a name="walkthrough-use-xslt-hierarchy"></a>Exemplarische Vorgehensweise: Verwenden der XSLT-Hierarchie

Das XSLT-Hierarchietool vereinfacht viele XML-Entwicklungsaufgaben. In einem XSLT-Stylesheet werden oft `includes`- und `imports`-Anweisungen verwendet. Die Kompilierung beginnt mit dem Hauptstylesheet. Wenn in Folge der Kompilierung eines XSLT-Stylesheets ein Fehler angezeigt wird, kann dieser jedoch aus einer anderen Quelle als dem Hauptstylesheet stammen. Zum Beheben des Fehlers oder Bearbeiten des Stylesheets müssen Sie möglicherweise auf eingeschlossene oder importierte Stylesheets zugreifen. Beim schrittweisen Ausführen des Stylesheets im Debugger werden ggf. eingeschlossene und importierte Stylesheets geöffnet, und Sie können einen Haltepunkt in den eingeschlossenen Stylesheets hinzufügen.

Ein anderes Szenario, in dem das XSLT-Hierarchietool nützlich sein kann, ist das Einfügen von Haltepunkten in den integrierten Vorlagenregeln. Vorlagenregeln sind spezielle, für jeden Modus des Stylesheets generierte Vorlagen, die von `xsl:apply-templates` aufgerufen werden, wenn keine andere Vorlage dem Knoten entspricht. Der XSLT-Debugger generiert die Datei mit den Regeln im temporären Ordner und kompiliert sie zusammen mit dem Hauptstylesheet, um das Debugging in integrierten Vorlagenregeln zu implementieren. Ohne einen Einzelschritt von `xsl:apply-template` in den Code kann es schwierig sein, im Hauptstylesheet enthaltene Stylesheets zu finden oder das Stylesheet mit den integrierten Vorlagenregeln zu finden und zu öffnen.

Im Beispiel in diesem Thema wird das Debugging in einem referenzierten Stylesheet veranschaulicht.

## <a name="to-debug-in-a-referenced-style-sheet"></a>So debuggen Sie in einem referenzierten Stylesheet

1. Öffnen Sie in Visual Studio ein XML-Dokument. In diesem Beispiel wird das folgende Dokument verwendet:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <?xml-stylesheet type="text/xsl" href="xslinclude.xsl"?>
    <COLLECTION>
      <BOOK>
        <TITLE>Lover Birds</TITLE>
        <AUTHOR>Cynthia Randall</AUTHOR>
        <PUBLISHER>Lucerne Publishing</PUBLISHER>
      </BOOK>
      <BOOK>
        <TITLE>The Sundered Grail</TITLE>
        <AUTHOR>Eva Corets</AUTHOR>
        <PUBLISHER>Lucerne Publishing</PUBLISHER>
      </BOOK>
      <BOOK>
        <TITLE>Splish Splash</TITLE>
        <AUTHOR>Paula Thurman</AUTHOR>
        <PUBLISHER>Scootney</PUBLISHER>
      </BOOK>
    </COLLECTION>
    ```

1. Fügen Sie die folgende Datei *xslincludefile.xsl* hinzu:

    ```xml
    <?xml version='1.0'?>
    <xsl:stylesheet version="1.0"
          xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
          xml:space="preserve">

    <xsl:template match="TITLE">
       Title - <xsl:value-of select="."/><BR/>
    </xsl:template>

    <xsl:template match="AUTHOR">
       Author - <xsl:value-of select="."/><BR/>
    </xsl:template>

    <xsl:template match="PUBLISHER">
       Publisher - <xsl:value-of select="."/><BR/><!-- removed second <BR/> -->
    </xsl:template>

    </xsl:stylesheet>
    ```

3. Fügen Sie die folgende Datei *xslinclude.xsl* hinzu:

    ```xml
    <?xml version='1.0'?>
    <xsl:stylesheet version="1.0"
          xmlns:xsl="http://www.w3.org/1999/XSL/Transform">

      <xsl:output method="xml" omit-xml-declaration="yes"/>

      <xsl:template match="/">
        <xsl:for-each select="COLLECTION/BOOK">
          <xsl:apply-templates select="TITLE"/>
          <xsl:apply-templates select="AUTHOR"/>
          <xsl:apply-templates select="PUBLISHER"/>
          <BR/>
          <!-- add this -->
        </xsl:for-each>
      </xsl:template>

      <!-- The following template rule will not be called,
      because the related template in the including stylesheet
      is called. If we move this template so that
      it follows the xsl:include instruction, this one
      will be called instead.-->
      <xsl:template match="TITLE">
        <DIV STYLE="color:blue">
          Title: <xsl:value-of select="."/>
        </DIV>
      </xsl:template>

      <xsl:include href="xslincludefile.xsl" />
    </xsl:stylesheet>
    ```

4. Fügen Sie einen Haltepunkt bei der Anweisung `<xsl:include href="xslincludefile.xsl" />` hinzu.

5. Beginnen Sie mit dem Debuggen.

6. Klicken Sie auf die Schaltfläche **Einzelschritt**, wenn der Debugger bei der `<xsl:include href="xslincludefile.xsl" />`-Anweisung anhält. Das Debugging kann im referenzierten Stylesheet fortgesetzt werden. Die Hierarchie ist sichtbar, und im Designer wird der richtige Pfad angezeigt.

## <a name="see-also"></a>Siehe auch

- [XSLT-Profiler](../xml-tools/xslt-profiler.md)
