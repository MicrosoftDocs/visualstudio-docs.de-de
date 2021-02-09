---
title: Analysieren und Modellieren der Architektur
description: Erfahren Sie, wie Sie mit Visual Studio-Architektur- und Modellierungstools Ihre App entwerfen und modellieren können, um sicherzustellen, dass Ihre App architektonische Anforderungen erfüllt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- diagrams - modeling
- architecture
- code visualization
- application design
- code exploration
- modeling
- application architecture
- architecture [Visual Studio ALM], modeling
- application modeling
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7364da54179b742dc3cbfcd94622308f5c13b483
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861913"
---
# <a name="analyze-and-model-your-architecture"></a>Analysieren und Modellieren der Architektur

Stellen Sie sicher, dass Ihre App die Architekturanforderungen erfüllt, indem Sie die Visual Studio-Architektur und -Modellierungstools zum Entwerfen und Modellieren Ihrer App verwenden.

* Wenn Sie Visual Studio zum Visualisieren von Codestruktur, -verhalten und -beziehungen verwenden, können Sie vorhandenen Programmcode besser verstehen.

* Informieren Sie Ihr Team über die Notwendigkeit, architektonische Abhängigkeiten zu berücksichtigen.

* Im Rahmen des Entwicklungsprozesses können Sie Modelle unterschiedlichen Detaillierungsgrads während des gesamten Lebenszyklus der Anwendung erstellen.

Weitere Informationen finden Sie unter [Szenario: Ändern des Designs mithilfe von Visualisierung und Modellierung](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).

## <a name="article-reference"></a>Artikelreferenz

|Szenario|Artikel|
|-|-|
|**Visualisieren von Code**:<br /><br />Durch Erstellen von Code Maps können Sie die Organisation und Beziehungen des Codes nachvollziehen. Sie können Abhängigkeiten zwischen Assemblys, Namespaces, Klassen, Methoden usw. visualisieren.<br />Zeigen Sie die Klassenstruktur und -member für ein bestimmtes Projekt an, indem Sie Klassendiagramme aus Code erstellen.<br />Suchen Sie Konflikte zwischen dem Code und dem Entwurf, indem Sie Abhängigkeitsdiagramme zum Überprüfen von Code erstellen.|- [Visualisieren von Code](../modeling/visualize-code.md)<br />- [Arbeiten mit Klassen und anderen Typen (Klassen-Designer)](../ide/class-designer/designing-and-viewing-classes-and-types.md)<br />- [Video: Nachvollziehen des Codeentwurfs mit Visual Studio 2015 Code Maps](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)<br />- [Video: Überprüfen der Architekturabhängigkeiten in Echtzeit](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)|
|**Definieren der Architektur**:<br /><br />Definieren und erzwingen Sie Einschränkungen für die Abhängigkeiten zwischen Komponenten des Codes, indem Sie Abhängigkeitsdiagramme erstellen.|- [Video: Überprüfen von Architekturabhängigkeiten mit Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|
|**Überprüfen des Systems anhand der Anforderungen und des beabsichtigten Entwurfs:**<br /><br />Überprüfen Sie Codeabhängigkeiten mit Abhängigkeitsdiagrammen, die die beabsichtigte Architektur beschreiben und Änderungen verhindern, die einen Konflikt mit dem Entwurf verursachen könnten.|- [Video: Überprüfen von Architekturabhängigkeiten mit Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|
|**Anpassen von Modellen und Diagrammen**:<br /><br />Erstellen Sie eigene domänenspezifische Sprachen.|- [Modellierungs-SDK für Visual Studio – Domänenspezifische Sprachen](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|
|**Generieren Sie Text mithilfe von T4-Vorlagen**:<br /><br />Verwenden Sie Textblöcke und Steuerelementlogik in Vorlagen, um textbasierte Dateien zu generieren.<br /> T4-Vorlagenbuild mit in Visual Studio enthaltenem MSBuild|- [Codegenerierung und T4-Textvorlagen](../modeling/code-generation-and-t4-text-templates.md)|
|**Freigeben von Modellen und Code Maps mithilfe der Team Foundation-Versionskontrolle**:<br /><br />Unterziehen Sie Code Maps, Projekte und Abhängigkeitsdiagramme der Team Foundation-Versionskontrolle, damit Sie diese freigeben können.| |

Welche Visual Studio-Editionen die einzelnen Features unterstützen, erfahren Sie unter [Edition-Unterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="types-of-models-and-typical-uses"></a>Typen von Modellen und deren typische Anwendungsmöglichkeiten

### <a name="code-maps"></a>Codezuordnungen

Mit Code Maps können Sie die Organisation und die Beziehungen im Code anzeigen.

**Typische Anwendungsmöglichkeiten**:

- Überprüfen Sie Programmcode, um sich mit der Struktur, den Abhängigkeiten sowie dem Aktualisieren vertraut zu machen und um die Kosten für vorgeschlagene Änderungen einschätzen zu können.

**Weitere Informationen:**

- [Projektmappenübergreifendes Zuordnen von Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md)
- [Verwenden von Code Maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md)
- [Ermitteln potenzieller Probleme mithilfe von Code Map-Analyzern](../modeling/find-potential-problems-using-code-map-analyzers.md)

### <a name="dependency-diagrams"></a>Abhängigkeitsdiagramme

Anhand von Abhängigkeitsdiagrammen können Sie die Struktur einer Anwendung als einen Satz von Ebenen oder Blöcken mit expliziten Abhängigkeiten definieren. Die Livevalidierung zeigt Konflikte zwischen Abhängigkeiten im Code und den in einem Abhängigkeitsdiagramm beschriebenen Abhängigkeiten.

**Typische Anwendungsmöglichkeiten**:

- Stabilisieren der Struktur der Anwendung anhand zahlreicher Änderungen während der gesamten Lebensdauer.
- Ermitteln Sie unbeabsichtigte Abhängigkeitskonflikte, bevor Sie Änderungen am Code einchecken.

**Weitere Informationen:**

- [Erstellen von Abhängigkeitsdiagrammen aus dem Code](../modeling/create-layer-diagrams-from-your-code.md)
- [Abhängigkeitsdiagramme: Referenz](../modeling/layer-diagrams-reference.md)
- [Überprüfen von Code mit Abhängigkeitsdiagrammen](../modeling/validate-code-with-layer-diagrams.md)

### <a name="domain-specific-language-dsl"></a>Domänenspezifische Sprache (DSL)

Eine DSL ist eine Notation, die für einen bestimmten Zweck entworfen wird. In Visual Studio ist sie normalerweise eine grafische Darstellung.

**Typische Anwendungsmöglichkeiten**:

- Generieren oder Konfigurieren von Teilen einer Anwendung. Es ist ein wenig Aufwand erforderlich, um die Notation und die Tools zu entwickeln. Dadurch können Sie jedoch meist eine bessere Anpassung an die Domäne als bei einer UML-Anpassung erreichen.
- Bei großen Projekten oder bei Produktlinien, bei denen die Investitionen in die Entwicklung DSL und deren Tools sich deshalb lohnen, weil die DSL für mehrere Projekte verwendet werden kann.

**Weitere Informationen:**

- [Modellierungs-SDK für Visual Studio - Domänenspezifische Sprachen](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

## <a name="see-also"></a>Weitere Informationen

- [Neues bei der Modellierung in Visual Studio 2017](../modeling/what-s-new-for-design-in-visual-studio.md)
- [DevOps und Anwendungslebenszyklus-Verwaltung](/azure/devops/user-guide/devops-alm-overview)
