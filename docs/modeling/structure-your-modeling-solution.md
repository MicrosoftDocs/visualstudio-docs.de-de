---
title: Strukturieren der Modellierungslösung
description: Erlernen Sie ein Modellierungs Schema, um die Anwendung in verschiedene Teile aufzuteilen, die den Ebenen in einem allgemeinen ebenendiagramm entsprechen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d2f865cf66da0bb4496a3d754a49d1f4dcc70ff
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363730"
---
# <a name="structure-your-modeling-solution"></a>Strukturieren der Modellierungslösung

Um Modelle in einem Entwicklungsprojekt effizient zu verwenden, müssen die Teammitglieder gleichzeitig an Modellen aus verschiedenen Teilen des Projekts arbeiten können. In diesem Thema wird ein Schema zum Aufteilen der Anwendung in verschiedene Teile vorgeschlagen, die den Ebenen in einem allgemeinen Ebenendiagramm entsprechen.

Um schnell mit einem Projekt oder Unterprojekt beginnen zu können, ist es hilfreich, über eine Projektvorlage zu verfügen,die der gewählten Projektstruktur folgt. In diesem Thema wird beschrieben, wie eine solche Vorlage erstellt und verwendet wird.

In diesem Thema wird davon ausgegangen, dass Sie an einem Projekt arbeiten, das so groß ist, dass mehrere Teammitglieder erforderlich sind, und an dem möglicherweise mehrere Teams beteiligt sind. Der Code und die Modelle des Projekts sind in einem Quellcodeverwaltungssystem wie z. B. [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] gespeichert. Zumindest einige Teammitglieder verwenden Visual Studio zum Entwickeln von Modellen, und andere Teammitglieder können die Modelle mit anderen Versionen von Visual Studio anzeigen.

Welche Versionen von Visual Studio die einzelnen Tools und Modellierungsfunktionen unterstützen, erfahren Sie unter [Versions Unterstützung für Architektur-und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="solution-structure"></a>Projektmappenstruktur

In einem mittleren oder großen Projekt basiert die Struktur des Teams auf der Struktur der Anwendung. Jedes Team verwendet eine Visual Studio-Projektmappe.

### <a name="to-divide-an-application-into-layers"></a>So unterteilen Sie eine Anwendung in Ebenen

1. Lassen Sie die Struktur Ihrer Projektmappen auf der Struktur der Anwendung basieren, etwa einer Webanwendung, Dienstanwendung oder Desktopanwendung. Eine Reihe von gängigen Architekturen finden Sie im [Leitfaden zur Microsoft-Anwendungsarchitektur unter Anwendungs-archetypes](/previous-versions/msp-n-p/ee658107(v=pandp.10)).

2. Erstellen Sie eine Visual Studio-Projekt Mappe, die wir als Architektur Lösung bezeichnen. Diese Projektmappe wird zur Erstellung des allgemeinen Entwurfs des Systems verwendet. Es enthält Modelle, jedoch keinen Code.

   Fügen Sie dieser Projekt Mappe ein Abhängigkeits Diagramm hinzu. Zeichnen Sie im Abhängigkeits Diagramm die Architektur, die Sie für Ihre Anwendung ausgewählt haben. Das Diagramm kann beispielsweise die folgenden Ebenen und die Abhängigkeiten zwischen ihnen zeigen: Präsentation, Geschäftslogik und Daten.

4. Erstellen Sie eine separate Visual Studio-Projekt Mappe für jede Ebene im Architektur Abhängigkeits Diagramm.

   Diese Projektmappen werden verwendet, um den Code für die Ebenen zu entwickeln.

5. Erstellen Sie Modelle, die die Entwürfe der Ebenen und die Konzepte darstellen, die allen Ebenen gemeinsam sind. Ordnen Sie die Modelle so an, dass alle Modelle in der Architektur-Projektmappe und die relevanten Modelle in den einzelnen Ebenen angezeigt werden können.

   Sie können dies mit einem der folgenden Verfahren erreichen. Bei der ersten Alternative wird für jede Ebene ein separates Modellierungsprojekt erstellt, und bei der zweiten wird ein einzelnes Modellierungsprojekt erstellt, das von den Ebenen gemeinsam genutzt wird.

#### <a name="use-a-separate-modeling-project-for-each-layer"></a>Verwenden Sie für jede Ebene ein separates Modellierungsprojekt.

1. Erstellen Sie in jeder Ebenenprojektmappe ein Modellierungsprojekt.

   Dieses Modell enthält Diagramme, in denen die Anforderungen und der Entwurf dieser Ebene beschrieben werden. Sie kann auch Abhängigkeits Diagramme enthalten, die für die Anzeige von Ebenen stehen.

   Sie verfügen jetzt über ein Modell für jede Ebene sowie über ein Modell für die Anwendungsarchitektur. Jedes Modell ist in einer eigenen Projektmappe enthalten. Dies ermöglicht es Teammitgliedern, gleichzeitig an den Ebenen zu arbeiten.

2. Fügen Sie der Architektur-Projektmappe das Modellierungsprojekt jeder Ebenenprojektmappe hinzu. Öffnen Sie hierzu die Architektur-Projektmappe. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf den Lösungs Knoten, zeigen Sie auf Hinzufügen, und klicken Sie dann auf **vorhandenes Projekt**. Navigieren Sie zum Modellierungsprojekt (.modelproj) in einer Ebenenprojektmappe.

   Jedes Modell wird jetzt in zwei Projektmappen angezeigt: der Start-Projektmappe und der Architektur-Projektmappe.

3. Fügen Sie dem Modellierungsprojekt jeder Ebene ein Abhängigkeits Diagramm hinzu. Beginnen Sie mit einer Kopie des Architektur Abhängigkeits Diagramms. Sie können Teile löschen, die keine Abhängigkeiten vom Abhängigkeits Diagramm sind.

   Sie können auch Abhängigkeits Diagramme hinzufügen, die die detaillierte Struktur dieser Ebene darstellen.

   Diese Diagramme werden verwendet, um den Code zu überprüfen, der in dieser Ebene entwickelt wird.

4. Bearbeiten Sie in der Architektur-Projektmappe die Anforderungen und die Entwurfsmodelle für alle Ebenen mit Visual Studio.

   Entwickeln Sie in jeder Ebenenprojektmappe den Code für diese Ebene, der auf das Modell verweist. Wenn Sie die Entwicklung durchführen möchten, ohne den gleichen Computer zum Aktualisieren des Modells zu verwenden, können Sie das Modell lesen und Code entwickeln, indem Sie Versionen von Visual Studio verwenden, die keine Modelle erstellen können. Sie können Code auch aus dem Modell in diesen Versionen generieren.

   Diese Methode stellt sicher, dass keine Störungen von Entwicklern verursacht werden, die die Ebenenmodelle zur gleichen Zeit bearbeiten.

   Da die Modelle getrennt sind, ist es jedoch schwierig, auf allgemeine Konzepte zu verweisen. Jedes Modell muss eine eigene Kopie der Elemente aufweisen, von denen es über andere Ebenen und die Architektur abhängig ist. Das Abhängigkeits Diagramm in jeder Ebene muss mit dem Architektur Abhängigkeits Diagramm synchron gehalten werden. Es ist schwierig, die Synchronisierung beizubehalten, wenn sich diese Elemente ändern, obwohl Sie zu diesem Zweck Tools entwickeln könnten.

#### <a name="use-a-separate-package-for-each-layer"></a>Verwenden Sie für jede Ebene ein separates Paket.

1. Fügen Sie in der Projektmappe für jede Ebene das Architektur-Modellierungsprojekt hinzu. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf den Lösungs Knoten, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **vorhandenes Projekt**. Das einzelne Modellierungsprojekt kann nun aus allen Projektmappen aufgerufen werden: das Projekt für die Architektur und das Entwicklungsprojekt für jede Ebene.

2. Erstellen Sie im freigegebenen Modell ein Paket für jede Ebene: Wählen Sie in **Projektmappen-Explorer** das Modellierungsprojekt aus. Klicken Sie im **UML-Modell-Explorer** mit der rechten Maustaste auf den Modell Stamm Knoten, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Paket**

   Jedes Paket enthält Diagramme, in denen die Anforderungen und der Entwurf der entsprechenden Ebene beschrieben werden.

3. Fügen Sie bei Bedarf lokale Abhängigkeits Diagramme für die interne Struktur jeder Ebene hinzu.

   Diese Methode ermöglicht es, dass die Entwurfselemente der einzelnen Ebenen direkt auf die der Ebenen und gemeinsame Architektur verweisen, von denen sie abhängen.

   Obwohl das gleichzeitige Arbeiten an verschiedenen Paketen Konflikte verursachen kann, sind sie relativ einfach zu lösen, da die Pakete in separaten Dateien gespeichert werden.

## <a name="create-architecture-templates"></a>Erstellen von Architektur Vorlagen

In der Praxis erstellen Sie nicht all Ihre Visual Studio-Projektmappen gleichzeitig, sondern fügen Sie hinzu, wenn das Projekt fortschreitet. Sie verwenden wahrscheinlich auch die gleiche Lösungs Struktur in zukünftigen Projekten. Um schnell neue Projektmappen erstellen zu können, können Sie eine Projektmappen- oder Projektvorlage erstellen. Sie können die Vorlage in einer Visual Studio Integration Extension (VSIX) erfassen, damit Sie sie einfach verteilen und auf anderen Computern installieren können.

Wenn Sie beispielsweise häufig Projektmappen mit Präsentations-, Geschäfts- und Datenebenen verwenden, können Sie eine Vorlage konfigurieren, die neue Projektmappen mit dieser Struktur erstellt.

### <a name="to-create-a-solution-template"></a>So erstellen Sie ein Projektmappenvorlage

1. [Herunterladen und Installieren des Assistenten zum Exportieren von Vorlagen](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ExportTemplateWizard)

2. Erstellen Sie die Projektmappenstruktur, die Sie als Ausgangspunkt für zukünftige Projekte verwenden möchten.

3. Klicken Sie im Menü **Datei** auf **Vorlage als VSIX exportieren**.

   Der **Assistent "Vorlage als VSIX exportieren** " wird geöffnet.

4. Folgen Sie den Anweisungen im Assistenten und wählen Sie die Projekte aus, die in die Vorlage aufgenommen werden sollen, geben Sie einen Namen und eine Beschreibung für die Vorlage an, und geben Sie einen Ausgabespeicherort an.

## <a name="watch-a-video"></a>Video ansehen

[Organisieren und Verwalten von Modellen](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-9-organizing-and-managing-your-models)

## <a name="see-also"></a>Siehe auch

- [Verwenden von Modellen im Entwicklungsprozess](../modeling/use-models-in-your-development-process.md)
- [Visual Studio Architecture Tooling Guidance](../modeling/visual-studio-architecture-tooling-guidance.md)
