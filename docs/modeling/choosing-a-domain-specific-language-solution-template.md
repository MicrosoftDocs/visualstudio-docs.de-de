---
title: Auswählen einer Lösungsvorlage für eine domänenspezifische Sprache
description: Erfahren Sie, wie Sie eine domänenspezifische Sprachlösung erstellen, indem Sie eine der Lösungs Vorlagen auswählen, die im Domain-Specific-sprach-Designer-Assistenten verfügbar sind.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, solution templates
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e2e0c96c93e3583a7d2877a5f4f7bd70561b650b
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363535"
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>Auswählen einer Lösungsvorlage für eine domänenspezifische Sprache
Um eine domänenspezifische Sprachlösung zu erstellen, wählen Sie eine der Lösungs Vorlagen aus, die im Domain-Specific-sprach-Designer-Assistenten verfügbar sind. Indem Sie die Vorlage auswählen, die der Sprache am ehesten ähnelt, die Sie erstellen möchten, können Sie die Änderungen minimieren, die Sie an der Start Lösung vornehmen müssen.

 Die folgenden Lösungs Vorlagen sind im Domain-Specific-sprach-Designer-Assistenten verfügbar.

|Vorlage|Features|Beschreibung|
|-|-|-|
|Klassendiagramme|-Depot-Formen<br />-Klassen Vererbung<br />-Beziehungs Vererbung<br />-Shape-Vererbung<br />-Beziehungs Eigenschaften|Verwenden Sie diese Lösungs Vorlage, wenn Ihre domänenspezifische Sprache Entitäten und Beziehungen enthält, die über Eigenschaften verfügen. Mit dieser Vorlage wird eine domänenspezifische Sprache erstellt, die UML-Klassendiagrammen ähnelt. Die Haupt Entitäten sind Klassen und Schnittstellen, zusammen mit Zuordnungs-, Generalisierungs-und Implementierungs Beziehungen. Eine Klasse oder Schnittstelle wird als Feld angezeigt, das eine Liste von Attributen enthält.|
|Komponenten Diagramme|-Ports|Verwenden Sie diese Lösungs Vorlage, wenn Ihre domänenspezifische Sprache Komponenten enthält, d. h. Teile eines Software Systems. Mit dieser Vorlage wird eine domänenspezifische Sprache erstellt, die UML-Komponenten Diagrammen ähnelt. Die Haupt Entitäten sind Komponenten und Ports, die auf der Außenseite der Komponenten als kleine Formen angezeigt werden.|
|Task Flussdiagramme|-Bild-und Geometrie Formen<br />-   *Verantwortlichkeits Bereiche*|Verwenden Sie diese Lösungs Vorlage, wenn Ihre domänenspezifische Sprache Workflows, Zustände oder Sequenzen umfasst. Mit dieser Vorlage wird eine domänenspezifische Sprache erstellt, die UML-Aktivitäts Diagrammen ähnelt. Die Haupt Entität ist eine Aktivität, und die Haupt Beziehung ist ein Übergang zwischen Aktivitäten. Die Vorlage enthält mehrere weitere Elemente, wie z. b. Startstatus, Endzustand und eine Synchronisierungs Leiste.|
|Minimal Language (Einfache Version der Sprache)|-Eine Klasse und eine Form<br />-Eine Beziehung und ein Connector|Verwenden Sie diese Lösungs Vorlage, wenn Ihre domänenspezifische Sprache nicht den anderen Vorlagen ähnelt. Mit dieser Vorlage wird eine domänenspezifische Sprache erstellt, die zwei Klassen und eine Beziehung aufweist, die in der **Toolbox** als **Box** und **Line** dargestellt werden. Die-Klasse und die-Beziehung verfügen jeweils über eine Beispiel Zeichenfolgen-Eigenschaft.|
|Minimaler WinForm-Designer|: Ein kleines Modell.<br />-Ein Windows Form, in dem das Modell angezeigt wird.|Verwenden Sie diese Vorlage, wenn Sie eine Anwendung erstellen möchten, in der eine DSL anstelle eines grafischen Designers an ein Windows Form gebunden ist.<br /><br /> Das Formular, das als Benutzeroberfläche für die Sprache fungiert, befindet sich im Ordner "dsl\ui".<br /><br /> Sie sollten das Projekt erstellen, bevor Sie den Formular-Designer öffnen.<br /><br /> Weitere Informationen finden Sie unter [Erstellen einer Windows Forms-Based Domain-Specific Sprache](../modeling/creating-a-windows-forms-based-domain-specific-language.md).|
|Minimaler WPF-Designer|-Ein kleines Modell<br />-Eine Windows Presentation Foundation Benutzeroberfläche, auf der das Modell angezeigt wird.|Verwenden Sie diese Vorlage, wenn Sie eine Anwendung erstellen möchten, in der eine DSL anstelle eines grafischen Designers an eine WPF-Benutzeroberfläche gebunden ist.<br /><br /> Der Designer für die Benutzeroberfläche befindet sich im Ordner "dsl\ui".<br /><br /> Sie sollten das Projekt erstellen, bevor Sie den UI-Designer öffnen.<br /><br /> Weitere Informationen finden Sie unter [Erstellen einer WPF-Based Domain-Specific Sprache](../modeling/creating-a-wpf-based-domain-specific-language.md).|
|DSL-Bibliothek|-Eine minimale Bibliothek|Verwenden Sie diese Vorlage, wenn Sie eine partielle DSL-Definition erstellen möchten, die in andere DSL-Definitionen importiert werden kann.|

## <a name="see-also"></a>Weitere Informationen

- [Übersicht über domänenspezifische Sprachtools](../modeling/overview-of-domain-specific-language-tools.md)
