---
title: Visualisieren von Code | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
ms.assetid: 0dd7d438-393a-4cd3-b417-9bf37379e1b0
caps.latest.revision: 49
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 665dc76126eac964f405be06605c40b5b30cc9a5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85532937"
---
# <a name="visualize-code"></a>Visualisieren von Code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die Visualisierungs- und Modellierungstools in Visual Studio verwenden, damit diese Ihnen dabei helfen, vorhandenen Code zu verstehen und Ihre Anwendung zu beschreiben. Dies lässt Sie visuell erfahren, wie sich die Änderungen auf den Code auswirken, und Sie können die Arbeit und die Risiken bewerten, die sich von den Änderungen ergeben. Beispiel:

- Ordnen Sie Beziehungen visuell zu, um diese Beziehungen in Ihrem Code besser zu verstehen.

- Um die Architektur des Systems zu beschreiben und den Code konsistent mit dem Entwurf zu halten, erstellen Sie Ebenendiagramme und prüfen den Code gegen diese Diagramme.

- Erstellen Sie Klassendiagramme, um Klassenstrukturen zu beschreiben.

- Zeichnen Sie UML-Diagramme (Unified Modeling Language), um verschiedene Aspekte des Systems zu modellieren und zu kommunizieren. Beispielsweise können Sie die Komponenten, Typen, Interaktionen und Prozesse eines Systems modellieren.

  Diese Tools erleichtern auch die Kommunikation mit anderen Projektbeteiligten. Mithilfe von UML-Klassendiagrammen können Sie z. B. ein allgemeines Glossar zur Erörterung des Systems mit Projektbeteiligten, Benutzern und Teammitgliedern erstellen.

  Informationen dazu, welche Versionen von Visual Studio die einzelnen Features unterstützen, finden Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="what-do-you-want-to-do"></a>Wie möchten Sie vorgehen?

|Szenario|Artikel|
|-|-|
|**Verstehen von Code und seinen Beziehungen:**<br /><br /> Ordnen Sie Beziehungen zwischen bestimmten Codesegmenten zu.<br /><br /> Zeigen Sie eine Übersicht über die Beziehungen im Code für die gesamte Projektmappe an.<br /><br /> **Hinweis**: In dieser Version von Visual Studio wird der Begriff *Code Map* anstelle von *Abhängigkeitsdiagramm*verwendet.|-   [Projektmappenübergreifendes Zuordnen von Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Verwenden von Code Maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Ermitteln potenzieller Probleme mithilfe von Code Map-Analysen](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />-   [Zuordnen von Methoden in der aufrufsstapel beim Debugging](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|
|**Verstehen von Klassenstrukturen:**<br /><br /> Visualisieren Sie die Struktur von Klassen in einem Projekt, indem Sie aus dem Code Klassendiagramme erstellen.|[Gewusst wie: Hinzufügen von Klassendiagrammen zu Projekten (Klassen-Designer)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)|
|**Beschreiben Sie den allgemeinen Systementwurf, und überprüfen Sie den Code anhand dieses Entwurfs:**<br /><br /> Beschreiben Sie den allgemeinen Systementwurf und die beabsichtigten Abhängigkeiten, indem Sie Ebenendiagramme erstellen. Überprüfen Sie Code anhand dieses Entwurfs, um sicherzustellen, dass die Abhängigkeiten im Code konsistent zum Entwurf verlaufen.|-   [Erstellen von ebenendiagrammen aus dem Code](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Ebenendiagramme: Referenz](../modeling/layer-diagrams-reference.md)<br />-   [Ebenendiagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md)<br />-   [Überprüfen von Code mit ebenendiagrammen](../modeling/validate-code-with-layer-diagrams.md)|
|**Kommunizieren Sie die Benutzeranforderungen und die Architektur:**<br /><br /> Modellieren Sie die Benutzeranforderungen und die Architektur des Softwaresystems, indem Sie die folgenden UML-Diagramme zeichnen: Aktivität, Komponente, Klasse, Sequenz und Anwendungsfall.|-   [Erstellen von Modellen für Ihre APP](../modeling/create-models-for-your-app.md)<br />-   [Modell Benutzer Anforderungen](../modeling/model-user-requirements.md)<br />-   [Modellieren der Architektur Ihrer APP](../modeling/model-your-app-s-architecture.md)|

## <a name="external-resources"></a>Externe Ressourcen

|**Kategorie**|**Links**|
|------------------|---------------|
|**Foren**|-   [Visual Studio-Visualisierungs- & Modellierungstools](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [Visual Studio Visualization & Modeling SDK (DSL Tools)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|
|**Blogs**|[Visual Studio ALM + Team Foundation Server Blog](https://devblogs.microsoft.com/devops/welcome-to-the-visual-studio-alm-team-foundation-server-blog/)|
|**Technische Artikel und Journale**|[MSDN Architecture-Forum](https://msdn.microsoft.com/architecture/default.aspx)|

## <a name="see-also"></a>Weitere Informationen
 [Szenario: Ändern des Entwurfs mithilfe von Visualisierung und Modellierung](../modeling/scenario-change-your-design-using-visualization-and-modeling.md) [analysieren und modellieren](../modeling/analyze-and-model-your-architecture.md) [von Modellen Erstellen von Modellen für das App](../modeling/create-models-for-your-app.md) - [Modell Benutzer Anforderungen](../modeling/model-user-requirements.md) [Modell Ihrer APP-Architektur verwenden von](../modeling/model-your-app-s-architecture.md) [Modellen im Entwicklungsprozess](../modeling/use-models-in-your-development-process.md)
