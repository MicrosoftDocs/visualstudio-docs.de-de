---
title: Sicherheitsaspekte beim Arbeiten mit XML-Daten
description: Hier erfahren Sie mehr über Sicherheitsüberlegungen beim Arbeiten mit XML-Daten im XML-Editor oder XSLT-Debugger.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fce2b708-1aef-454f-be59-52b76f359351
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d9e98e18e3e01f53afa6b0a9ea3bdec94f2186f
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351348"
---
# <a name="security-considerations-when-working-with-xml-data"></a>Sicherheitsaspekte beim Arbeiten mit XML-Daten

In diesem Thema werden Sicherheitsaspekte erörtert, mit denen Sie beim Arbeiten mit dem XML-Editor oder dem XSLT-Debugger vertraut sein müssen.

## <a name="xml-editor"></a>XML-Editor

Der XML-Editor basiert auf dem Texteditor von Visual Studio. Er beruht auf der <xref:System.Xml>-Klasse und der <xref:System.Xml.Xsl>-Klasse zum Behandeln vieler XML-Prozesse.

- XSLT-Transformationen werden in einer neuen Anwendungsdomäne ausgeführt. Die XSLT-Transformationen sind *sandboxed*. Das heißt, dass mithilfe der Sicherheitsrichtlinie für den Codezugriff Ihres Computers die eingeschränkten Berechtigungen anhand des Speicherorts des XSLT-Stylesheets bestimmt werden. Stylesheets von einem Internetspeicherort weisen die am stärksten eingeschränkten Berechtigungen auf, während auf die Festplatte kopierte Stylesheets mit voller Vertrauenswürdigkeit ausgeführt werden.

- Mithilfe der <xref:System.Xml.Xsl.XslCompiledTransform>-Klasse wird XSLT in die Microsoft Intermediate Language (MSIL) kompiliert, um eine höhere Leistung bei der Ausführung zu erzielen.

- Schemata, die auf einen externen Speicherort in der Katalogdatei zeigen, werden beim ersten Laden des XML-Editors automatisch heruntergeladen. Mithilfe der <xref:System.Xml.Schema.XmlSchemaSet>-Klasse werden Schemata kompiliert. Die mit dem XML-Editor gelieferte Katalogdatei weist keine Links zu externen Schemata auf. Bevor der XML-Editor die Schemadatei herunterlädt, muss der Benutzer explizit einen Verweis auf das externe Schema hinzufügen. Über die Seite **Verschiedenes – Extras – Optionen** können für den XML-Editor HTTP-Downloads deaktiviert werden.

- Der XML-Editor verwendet die <xref:System.Net>-Klassen für Downloads von Schemata.

## <a name="xslt-debugger"></a>XSLT-Debugger

Der XSLT-Debugger verwendet aus Visual Studio die verwaltete Debug-Engine und die verwalteten Klassen aus dem <xref:System.Xml>-Namespace und dem <xref:System.Xml.Xsl>-Namespace.

- Der XSLT-Debugger führt jede XSLT-Transformation in einer Sandbox-Anwendungsdomäne aus. Mithilfe der Sicherheitsrichtlinie für den Codezugriff Ihres Computers werden die eingeschränkten Berechtigungen anhand des Speicherorts des XSLT-Stylesheets ermittelt. Stylesheets von einem Internetspeicherort weisen die am stärksten eingeschränkten Berechtigungen auf, während auf die Festplatte kopierte Stylesheets mit voller Vertrauenswürdigkeit ausgeführt werden.

- Das XSLT-Stylesheet wird mithilfe der <xref:System.Xml.Xsl.XslCompiledTransform>-Klasse kompiliert.

- Die XSLT-Ausdrucksauswertung wird von der verwalteten Debug-Engine geladen. Die verwaltete Debug-Engine geht davon aus, dass der gesamte Code auf dem lokalen Computer des Benutzers ausgeführt wird. Daher lädt die <xref:System.Xml.Xsl.XslCompiledTransform>-Klasse die XSLT-Datei auf den lokalen Computer des Benutzers. Die Möglichkeit einer Anhebung der Ausführungsberechtigung wird dadurch minimiert, dass alle XSLT-Transformationen in einer neuen Anwendungsdomäne mit eingeschränkten Berechtigungen ausgeführt werden.

## <a name="see-also"></a>Siehe auch

- [Anwendungsdomänen](/dotnet/framework/app-domains/application-domains)