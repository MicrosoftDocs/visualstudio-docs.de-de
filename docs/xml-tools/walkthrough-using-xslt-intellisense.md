---
title: 'Exemplarische Vorgehensweise: Verwenden von XSLT IntelliSense'
description: Hier erfahren Sie, wie Sie IntelliSense für XSLT verwenden, um die Werte einiger Attribute automatisch zu vervollständigen, indem Sie die Schritte in dieser exemplarischen Vorgehensweise ausführen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 079d95ac-2eaf-4ae1-9cd3-2c81a961a942
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ad3bb4024c4545dfaae7cdb9faa5d6484a66cd3e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875028"
---
# <a name="walkthrough-using-xslt-intellisense"></a>Exemplarische Vorgehensweise: Verwenden von XSLT IntelliSense

In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie XSLT-IntelliSense verwendet wird, um die Werte einiger Attribute automatisch zu vervollständigen.

## <a name="to-use-intellisense-in-the-name-attribute-of-xslwith-param-and-xslcall-template-elements"></a>So verwenden Sie IntelliSense im name-Attribut von xsl:with-param- und xsl:call-template-Elementen

1. Erstellen Sie eine neue XSLT-Datei, und kopieren Sie den folgenden Code in die Datei:

    ```xml
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
    <!-- These 2 elements effectively assign
         $messages = resources/en.xml/<messages>,
         then $messages is used in the "localized-message" template.  -->
    <xsl:param name="lang">en</xsl:param>
    <xsl:variable name="messages"
          select="document(concat('resources/', $lang, '.xml'))/messages"/>

    <xsl:template name="msg23" match="msg23">
    </xsl:template>

    <xsl:template name="localized-message">
      <xsl:param name="msgcode"/>
      <!-- Show message string. -->
      <xsl:message terminate="yes">
        <xsl:value-of select="$messages/message[@name=$msgcode]"/>
      </xsl:message>
    </xsl:template>
    </xsl:stylesheet>
    ```

2. Platzieren Sie den Cursor hinter `<xsl:template name="msg23" match="msg23">`, und drücken Sie die **EINGABETASTE**. Geben Sie dann das folgende `xsl:call-template`-Element ein:

    ```xml
    <xsl:call-template name="localized-message">
    </xsl:call-template>
    ```

     Während der Eingabe wird die Liste der Vorlagennamen im `name=""`-Attribut des `xsl:call-template`-Elements angezeigt.

3. Platzieren Sie den Cursor hinter `<xsl:call-template name="localized-message">`, und drücken Sie die **EINGABETASTE**. Geben Sie dann das folgende `xsl:with-param`-Element ein:

    ```xml
    <xsl:with-param name="msgcode">msg23</xsl:with-param>
    ```

     Die Liste der Parameternamen wird im `name=""`-Attribut des `xsl:with-param`-Elements angezeigt.

## <a name="to-use-intellisense-in-the-mode-attribute-of-an-xslapply-templates-element"></a>So verwenden Sie IntelliSense im mode-Attribut eines xsl:apply-templates-Elements

1. Erstellen Sie eine neue XSLT-Datei, und kopieren Sie den folgenden Code in die Datei:

    ```xml
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
      <xsl:template match="/">
        <HTML>
          <BODY>
            <TABLE>
              <xsl:apply-templates select="customers/customer">
                <xsl:sort select="state"/>
                <xsl:sort select="name"/>
              </xsl:apply-templates>
            </TABLE>
          </BODY>
        </HTML>
      </xsl:template>
      <xsl:template match="customer">
        <TR>
          <xsl:apply-templates select="name" />
          <xsl:apply-templates select="address" />
          <xsl:apply-templates select="phone" />
        </TR>
      </xsl:template>
      <xsl:template match="name">
        <TD STYLE="font-size:14pt font-family:serif">
          <xsl:apply-templates />
        </TD>
      </xsl:template>
      <xsl:template match="address">
        <TD>
          <xsl:apply-templates />
        </TD>
      </xsl:template>
      <xsl:template match="phone">
        <TD>
          <xsl:apply-templates />
        </TD>
      </xsl:template>
      <xsl:template match="phone" mode="accountNumber">
        <xsl:param name="Area_Code"/>
        <TD STYLE="font-style:italic">
          1-<xsl:value-of select="."/>-001
        </TD>
      </xsl:template>
    </xsl:stylesheet>
    ```

2. Platzieren Sie den Cursor hinter `<xsl:apply-templates select="phone" />`, und drücken Sie die **EINGABETASTE**. Geben Sie dann das folgende `xsl: apply-templates`-Element ein:

    ```xml
    <xsl:apply-templates select="phone"  mode="accountNumber">
    ```

     Die Liste der Vorlagenmodi wird im `mode=""`-Attribut des `xsl:apply-templates`-Elements angezeigt.

## <a name="to-use-intellisense-in-the-stylesheet-prefix-and-result-prefix-attributes-of-an-xslnamespace-alias-element"></a>So verwenden Sie IntelliSense in den stylesheet-prefix- und result-prefix-Attributen eines xsl:namespace-Alias-Elements

1. Erstellen Sie eine neue XSLT-Datei, und kopieren Sie den folgenden Code in die Datei:

    ```xml
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:alt="http://www.w3.org/1999/XSL/Transform-alternate"
    version="1.0">
      <xsl:param name="browser" select="'InternetExplorer'"/>
      <xsl:template match="/">
        <alt:stylesheet>
          <xsl:choose>
            <xsl:when test="$browser='InternetExplorer'">
              <alt:import href="IERoutines.xsl"/>
              <alt:template match="/">
                <div>
                  <alt:call-template name="showTable"/>
                </div>
              </alt:template>
            </xsl:when>
            <xsl:otherwise>
              <alt:import href="OtherBrowserRoutines.xsl"/>
              <alt:template match="/">
                <div>
                  <alt:call-template name="showTable"/>
                </div>
              </alt:template>
            </xsl:otherwise>
          </xsl:choose>
        </alt:stylesheet>
      </xsl:template>
    </xsl:stylesheet>
    ```

2. Platzieren Sie den Cursor hinter `<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:alt="http://www.w3.org/1999/XSL/Transform-alternate" version="1.0">`, und drücken Sie die **EINGABETASTE**. Geben Sie dann das folgende `xsl:namespace-alias`-Element ein:

    ```xml
    <xsl:namespace-alias stylesheet-prefix="alt" result-prefix="xsl"/>
    ```

     Die Liste der Präfixe wird in den `stylesheet-prefix`- und `result-prefix`-Attributen des `xsl:namespace-alias`-Elements angezeigt.

## <a name="see-also"></a>Siehe auch

- [IntelliSense-Features des XML-Editors](../xml-tools/xml-editor-intellisense-features.md)
