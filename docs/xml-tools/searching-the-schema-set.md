---
title: XML-Schema-Explorer – Durchsuchen des Schemasets
description: In diesem Artikel erfahren Sie, wie Sie eine Schlüsselwortsuche und eine schemaspezifische Suche des Schemasets im XML-Schema-Explorer durchführen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c73af4f40abddaaba15e3b2cc785ab412e8884e4
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351517"
---
# <a name="search-the-schema-set"></a>Durchsuchen des Schemasets

Im **XML-Schema-Explorer** stehen Ihnen die folgenden Methoden zum Durchsuchen des Schemasets zur Verfügung:

- Schlüsselwortsuche

- Schemaspezifische Suche

## <a name="keyword-search"></a>Schlüsselwortsuche

Geben Sie zum Ausführen einer Schlüsselwortsuche eine Teilzeichenfolge in das Textfeld **Schemaset suchen** auf der **XML-Schema-Explorer**-Symbolleiste ein.

![Schlüsselwortsuche im XML-Schema-Explorer](../xml-tools/media/schemaexplorersearch.gif)

Der **XML-Schema-Explorer** durchsucht das Schemaset nach folgenden Attributen:

- Alle `name`- oder `ref`-Attribute, die mit dem angegebenen Schlüsselwort übereinstimmen. Sie können anhand des Namens nach Elementen, Attributen, Typen usw. suchen.

- Die `schemaLocation`-Attribute von Include-Anweisungen.

- Die `namespace`-Attribute von Import-Anweisungen.

## <a name="schema-specific-search"></a>Schemaspezifische Suche

Der **XML-Schema-Explorer** enthält auch integrierte Suchfunktionen, auf die Sie über das Kontextmenü (rechts klicken) des **XML-Schema-Explorers** zugreifen. Weitere Informationen zu verfügbaren Kontextmenüs finden Sie unter [Kontextmenüs](../xml-tools/context-menus-xml-schema-explorer.md). Sie können auch eine schemaspezifische Suche in der Ausgangsansicht ausführen. Weitere Informationen dazu finden Sie im Abschnitt „Details zum Schemaset“ im Thema [Ausgangsansicht](../xml-tools/start-view.md).

## <a name="display-and-navigate-search-results"></a>Anzeigen von und Navigieren in Suchergebnissen

Nach der Suche wird der Symbolleiste ein Bereich mit der Ergebniszusammenfassung der Suche hinzugefügt. Die Suchergebnisse werden auch im **XML-Schema-Explorer** hervorgehoben und auf der vertikalen Bildlaufleiste durch Teilstriche markiert. Sie können wie folgt in den Suchergebnissen navigieren: Klicken Sie auf der **XML-Schema-Explorer**-Symbolleiste im Bereich mit den Zusammenfassungsergebnissen auf die Schaltflächen **Zum nächsten Suchergebnis** und **Zum vorherigen Suchergebnis**, drücken Sie die Tasten **F3** und **UMSCHALT**+**F3**, oder klicken Sie auf die Teilstriche in der Bildlaufleiste.

Sie können die Suchergebnisse dem Arbeitsbereich hinzufügen, indem Sie im Bereich mit der Ergebniszusammenfassung auf die Schaltfläche **Hervorgehobene Knoten zu Arbeitsbereich hinzufügen** klicken.

![Suchergebnis im XML-Schema-Explorer](../xml-tools/media/schemaexplorersearchresult.gif)

## <a name="clear-search-results"></a>Suchergebnisse löschen

Klicken Sie auf der **XML-Schema-Explorer**-Suchsymbolleiste im Bereich mit der Ergebniszusammenfassung auf die Schaltfläche **x**, um die Suchergebnisse zu löschen.

## <a name="see-also"></a>Siehe auch

- [XML-Schema-Explorer](../xml-tools/xml-schema-explorer.md)
