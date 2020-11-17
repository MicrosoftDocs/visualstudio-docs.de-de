---
title: XML-Editor und XML-Schema-Designer
description: In diesem Artikel erfahren Sie mehr über die Tools in Visual Studio für das XML-, XSLT- und XML-Schema, einschließlich des XML-Editors, des XML-Schema-Designers und des XSLT-Debuggers.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
f1_keywords:
- vb.xmldesigner
helpviewer_keywords:
- XML [Visual Studio], resources
- Enterprise Templates, XML and
- discovery files, XML
- server controls, XML and
- Web server controls, XML
- XSL
- XML [Visual Studio], data sources
- XML schemas
- XML [Visual Studio], SGML relationship to
- CSS, style sheets for XML
- XML [Visual Studio], .NET classes
- data [Visual Studio], XML
- classes [Visual Studio], XML
- style sheets, for XML
- Web services
- SGML, XML
- XML [Visual Studio]
- datasets [Visual Basic], XML Schemas
- XSD schemas
- XSL, style sheets
- XMLDataDocument class
ms.assetid: 1fd5de47-2d61-4180-9539-c2c4bf9ab768
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc8cac3e16e06c23d0d51ee4483bcf5fb8abfb05
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351283"
---
# <a name="overview-of-xml-tools-in-visual-studio"></a>Übersicht: XML-Tools in Visual Studio

*Extensible Markup Language (XML)* ist eine Markupsprache, die ein Format bereitstellt, mit dem Daten beschrieben werden können. XML trennt die Daten und deren Präsentation durch Verwendung zugeordneter Stylesheets wie Extensible Stylesheet Language (XSL) und Cascading Style Sheets (CSS). Visual Studio enthält Tools und Funktionen, die das Arbeiten mit XML, XSLT und XML-Schemas vereinfachen.

## <a name="xml-editor"></a>XML-Editor

Der [XML-Editor](xml-editor.md) dient zum Bearbeiten von XML-Dokumenten. Er bietet eine vollständige Syntaxüberprüfung für XML, die Schemavalidierung beim Eingeben, Farbcodierung und IntelliSense. Wenn ein Schema oder eine DTD (Dokumenttypdefinition) bereitgestellt wird, werden von IntelliSense damit die zulässigen Elemente und Attribute aufgelistet.

Folgende zusätzlichen Funktionen sind verfügbar:

- Unterstützung von XML-Ausschnitten, einschließlich schemagenerierter Ausschnitte

- Gliedern von Dokumenten, sodass Elemente erweitert und reduziert werden können

- Ausführen von XSL-Transformationen und Anzeigen der Ergebnisse als Text, XML oder HTML

- Generieren von XSD-Schemas (XML-Schemadefinitionssprache) aus dem XML-Instanzdokument

- Unterstützung für das Bearbeiten von XSLT-Stylesheets, einschließlich IntelliSense-Unterstützung

- XML-Schema-Explorer

## <a name="xml-schema-designer"></a>XML-Schema-Designer

Der [XML-Schema-Designer](xml-schema-designer.md) ist in Visual Studio und den XML-Editor integriert, um die Arbeit mit XSD-Schemas (XML-Schemadefinitionssprache) zu ermöglichen.

## <a name="xslt-debugging"></a>Debuggen von XSLT-Code

Visual Studio unterstützt das [Debuggen von XSLT-Stylesheets](../xml-tools/debugging-xslt.md). Mithilfe des Debuggers können Sie Haltepunkte in einem XSLT-Stylesheet festlegen, den Code in einem XSLT-Stylesheet schrittweise ausführen usw.

> [!NOTE]
> Der XSLT-Debugger ist nur in der Enterprise Edition von Visual Studio verfügbar.

## <a name="see-also"></a>Siehe auch

- <xref:System.Xml?displayProperty=fullName>
- [XSLT-Transformationen](/dotnet/standard/data/xml/xslt-transformations)
- [Verarbeiten von XML-Daten mithilfe des XPath-Datenmodells](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model)
- [XML-Dokumentobjektmodell (DOM)](/dotnet/standard/data/xml/xml-document-object-model-dom)
- [XML Schema Object Model (SOM) (XML-Schemaobjektmodell (SOM))](/dotnet/standard/data/xml/xml-schema-object-model-som)
