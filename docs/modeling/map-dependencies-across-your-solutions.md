---
title: Codezuordnungen
description: Erfahren Sie, wie Code Maps Ihnen helfen, zu sehen, wie der Code passt, ohne dass Dateien und Codezeilen gelesen werden.
ms.custom: SEO-VS-2020
ms.date: 05/16/2018
ms.topic: how-to
f1_keywords:
- vs.progression.codemap
- vs.progression.standardgraphsdialog
helpviewer_keywords:
- DGML
- graph documents
- code visualization [Visual Studio]
- dependencies, visualizing
- dependency graphs
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39b34bb124d663d81769c6d3086d6b36803d60eb
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362235"
---
# <a name="map-dependencies-with-code-maps"></a>Zuordnen von Abhängigkeiten zu Code Maps

Sie können Abhängigkeiten im gesamten Code visualisieren, indem Sie eine Code Map erstellen. Mithilfe von Code Maps sehen Sie, wie der Code passt, ohne dass Dateien und Codezeilen gelesen werden.

![Anzeigen von Abhängigkeiten mit Code Maps in Visual Studio](../modeling/media/codemapsmainintro.png)

Zum Erstellen und Bearbeiten von Code Maps benötigen Sie Visual Studio Enterprise Edition. In den Editionen von Visual Studio Community und Professional können Sie Diagramme öffnen, die in der Enterprise Edition generiert wurden, Sie können Sie jedoch nicht bearbeiten.

> [!NOTE]
> Bevor Sie in Visual Studio Enterprise erstellte Zuordnungen für andere Personen freigeben, die Visual Studio Professional verwenden, stellen Sie sicher, dass alle Elemente auf der Karte (z. b. ausgeblendete Elemente, erweiterte Gruppen und gruppenübergreifende Links) sichtbar sind.

Codeabhängigkeiten können in folgenden Sprachen durch Code Maps dargestellt werden:

- Visual c# oder Visual Basic in einer Projekt Mappe oder in Assemblys (*dll* -oder *exe*-Datei)

- Nativer oder verwalteter C-oder C++-Code in Visual C++ Projekten, Header Dateien (*. h* oder `#include` ) oder Binärdateien

- Aus .NET-Modulen für Microsoft Dynamics AX erstellte X++-Projekte und X++-Assemblydateien

> [!NOTE]
> Für andere Projekte als c# oder Visual Basic gibt es weniger Optionen zum Starten einer Code Map oder zum Hinzufügen von Elementen zu einer vorhandenen Code map. Beispielweise können Sie nicht mit der rechten Maustaste auf ein Objekt im Text-Editor eines C++-Projekts klicken, es einer Code Map hinzuzufügen. Sie können jedoch einzelne Code Elemente oder Dateien aus **Projektmappen-Explorer**, **Klassenansicht** und **Objektkatalog** ziehen und ablegen.

## <a name="install-code-map-and-live-dependency-validation"></a>Installieren von Code Map und Live-Abhängigkeits Validierung

Um in Visual Studio eine Code Map zu erstellen, installieren Sie zunächst die Komponenten **Code Map** und **Live-Abhängigkeits** Überprüfung:

1. Öffnen Sie **Visual Studio-Installer**. Sie können Sie über das Windows-Startmenü oder in Visual Studio öffnen, indem Sie **Tools Tools**  >  **und Features** auswählen auswählen.

1. Wählen Sie die Registerkarte **Einzelne Komponenten** aus.

1. Scrollen Sie nach unten zum Abschnitt **Code Tools** , und wählen Sie **Code Map** und **Live-Abhängigkeits** Überprüfung aus.

   ![Komponenten der Code Map-und Live-Abhängigkeits Validierung in Visual Studio-Installer](media/modeling-components.png)

1. Klicken Sie auf **Ändern**.

   Die Komponenten **Code Map** und **Live-Abhängigkeits Validierung** beginnen mit der Installation von. Möglicherweise werden Sie aufgefordert, Visual Studio zu schließen.

## <a name="add-a-code-map"></a>Hinzufügen einer Code Map

Sie können eine leere Code Map erstellen und Elemente auf diese ziehen, einschließlich Assemblyverweise, Dateien und Ordner, oder Sie können eine Code Map für die gesamte Projekt Mappe oder einen Teil der Projekt Mappe generieren.

So fügen Sie eine leere Code Map hinzu:

1. Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü für den Projektmappenknoten auf oberster Ebene. Wählen Sie  >  **Neues Element** hinzufügen aus.

2. Wählen Sie im Dialogfeld **Neues Element hinzufügen** unter **installiert** die Kategorie **Allgemein** aus.

3. Wählen Sie die Vorlage **gerichtetes Diagramm Dokument (. dgml)** aus, und klicken Sie dann auf **Hinzufügen**.

   > [!TIP]
   > Diese Vorlage wird möglicherweise nicht alphabetisch angezeigt. führen Sie einen Bildlauf zum Ende der Vorlagenliste durch, wenn Sie nicht angezeigt wird.

   Im Ordner Projektmappenelemente der Projekt  Mappe wird eine leere Karte angezeigt.

Auf ähnliche Weise können Sie eine neue Code Map Datei erstellen, ohne Sie der Projekt Mappe hinzuzufügen, indem Sie **Architektur**  >  **neue Code Map** oder **Datei**  >  **neue**  >  **Datei** auswählen.

## <a name="generate-a-code-map-for-your-solution"></a>Generieren eines Code Map für die Lösung

So zeigen Sie alle Abhängigkeiten in der Projekt Mappe an:

1. Wählen Sie in der Menüleiste **Architektur**  >  **Code Map für Projekt Mappe generieren aus**. Wenn sich der Code seit der letzten Erstellung nicht geändert hat, können Sie **Architektur**  >  **Code Map für** Projekt Mappe generieren auswählen, ohne stattdessen zu erstellen.

   ![Generieren eines Code Map-Befehls](../modeling/media/codemapsarchitecturemenu.png)

   Es wird eine Karte generiert, die die Assemblys der obersten Ebene und aggregierte Verknüpfungen zwischen Ihnen anzeigt. Desto größer die Aggregatsverbindung, desto mehr Abhängigkeiten stellt sie dar.

2. Mit der Schaltfläche **Legende** auf der Symbolleiste der Code Map können Sie die Liste der Projekttypsymbole (z. B. Test, Web und Phone-Projekt), der Codeelemente (z. B. Klassen, Methoden und Eigenschaften) sowie der Beziehungstypen (z. B. Erbt von, Implementiert und Aufrufe) anzeigen oder ausblenden.

   ![Assembly-Abhängigkeitsdiagramm der ersten Ebene](../modeling/media/dependencygraph_toplevelassemblies.png)

   Diese Beispielprojektmappe enthält Projektmappenordner (**Tests** und **Komponenten**), Testprojekte, Webprojekte und Assemblys. Standardmäßig werden alle Einschlussbeziehungen als *Gruppen* dargestellt, die Sie erweitern und reduzieren können. Die Gruppe **Extern** enthält alle Elemente außerhalb der Projektmappe, einschließlich Plattformabhängigkeiten. Für externe Assemblys werden nur die Elemente angezeigt, die verwendet werden. Standardmäßig werden Systembasistypen auf der Code Map ausgeblendet, um die Übersichtlichkeit zu verbessern.

3. Um einen Drilldown in der Code Map durchzuführen, erweitern Sie die Gruppen, die Projekte und Assemblys darstellen. Sie können alle Gruppen erweitern, indem Sie durch Drücken von **STRG + A** alle Knoten auswählen und dann **Gruppe**, **Erweitern** im Kontextmenü auswählen.

   ![Erweitern aller Gruppen in einer Code Map](../modeling/media/codemapsexpandallgroups.png)

4. Allerdings ist dieses Verfahren für große Projektmappen nicht unbedingt hilfreich. Tatsächlich können Sie bei komplexen Projektmappen aufgrund von Speicherbeschränkungen möglicherweise nicht alle Gruppen erweitern. Erweitern Sie in diesem Fall einen einzelnen Knoten, um seinen Inhalt anzuzeigen. Bewegen Sie den Mauszeiger auf einen Knoten, und klicken Sie dann auf das Chevron (Abwärtspfeil), wenn es angezeigt wird.

   ![Erweitern eines Knotens in einer Code Map](../modeling/media/dependencygraph_containment.png)

   Sie können auch die Tastatur verwenden, indem Sie das Element auswählen und dann die Plus-Taste drücken ( **+** ). Gehen Sie bei Namespaces, Typen und Mitglieder genauso vor, um tiefere Ebenen des Codes untersuchen.

   > [!TIP]
   > Weitere Informationen zum Arbeiten mit Code Maps mithilfe der Maus, der Tastatur und der Fingereingabe finden Sie unter [Durchsuchen und Neuanordnen von Code Maps](../modeling/browse-and-rearrange-code-maps.md).

5. Um die Code Map zu vereinfachen und sich auf einzelne Teile zu konzentrieren, wählen Sie **Filter** auf der Symbolleiste der Code Map aus, und wählen Sie dann nur die Knoten- und Linktypen aus, die für Sie von Interesse sind. Beispielsweise können Sie alle Projektmappenordner und Assemblycontainer ausblenden.

   ![Vereinfachen der Zuordnung durch Filtern der Container](../modeling/media/codemapsfilterfoldersassemblies.png)

   Sie können die Code Map auch vereinfachen, indem Sie einzelne Gruppen und Elemente ausblenden oder aus der Code Map entfernen, ohne dass sich dies auf den zugrunde liegenden Projektmappencode auswirkt.

6. Um die Beziehungen zwischen Elementen anzuzeigen, wählen Sie die Elemente in der Code Map aus. Die Farben der Links zeigen die Beziehungstypen an, wie im Bereich **Legende** dargestellt.

   ![Projektmappenübergreifendes Anzeigen von Abhängigkeiten](../modeling/media/codemapsmainintro.png)

   In diesem Beispiel sind die violetten Links Aufrufe, die gepunkteten Links sind Verweise, und die hellblauen Links sind Feldzugriffe. Grüne Links können Vererbung darstellen, oder es kann sich um *Aggregatlinks* handeln, die mehrere Beziehungstypen (oder *Kategorien*) angeben.

   > [!TIP]
   > Wenn ein grüner Link angezeigt wird, muss dies nicht bedeuten, dass nur eine Vererbungsbeziehung besteht. Möglicherweise gibt es auch Methodenaufrufe, aber diese sind durch die Vererbungsbeziehung ausgeblendet. Um bestimmte Linktypen anzuzeigen, können Sie mit den Kontrollkästchen im Bereich **Filter** die Typen ausblenden, die für Sie nicht von Interesse sind.

7. Weitere Informationen zu einem Element oder einem Link erhalten Sie, indem Sie den Mauszeiger darauf bewegen und warten, bis eine QuickInfo angezeigt wird. Diese enthält Details zu einem Codeelement oder den Kategorien, die ein Link darstellt.

   ![Anzeigen der Kategorien einer Beziehung](../modeling/media/codemapsshowlinkcatgories.png)

8. Wählen Sie zum Untersuchen von Elementen und Abhängigkeiten, die durch einen Aggregatlink dargestellt werden, zunächst den Link aus, und öffnen Sie dann das zugehörige Kontextmenü. Wählen Sie **Zugehörige Links anzeigen** (oder **Zugehörige Links auf neuer Code Map anzeigen**) aus. Hierdurch werden die Gruppen an beiden Enden des Links erweitert und nur die Elemente und Abhängigkeiten angezeigt, die zu dem Link gehören.

9. Um sich auf bestimmte Teile der Zuordnung zu konzentrieren, können Sie weiterhin Elemente entfernen, an denen Sie nicht interessiert sind. Wenn Sie z. B. einen Drillinto für die Klassen- und Memberansicht ausführen möchten, filtern Sie einfach alle Namespaceknoten im Bereich **Filter** .

   ![Drilldown auf Klassen- und Memberebene](../modeling/media/dependencygraph_expandedselectedgroups_2012.png)

10. Eine andere Methode zum Fokussieren einer Code Map einer komplexen Projektmappe besteht darin, eine neue Code Map zu generieren, die ausgewählte Elemente aus einer vorhandenen Code Map enthält. Halten Sie **STRG** gedrückt, während Sie die Elemente auswählen, auf die Sie sich konzentrieren möchten, öffnen Sie das Kontextmenü, und wählen Sie **Neues Diagramm aus Auswahl**

    ![Anzeigen der ausgewählten Elemente in einer neuen Code Map](../modeling/media/codemapsshowonnewmap.png)

11. Der enthaltende Kontext wird in die neue Code Map übernommen. Blenden Sie Projektmappenordner und andere Container, die nicht angezeigt werden sollen, mithilfe des Bereichs **Filter** aus.

    ![Filtern der Container zum Vereinfachen der Ansicht](../modeling/media/codemapsexpandnewgroups.png)

12. Erweitern Sie die Gruppen, und wählen Sie Elemente in der Code Map aus, um die Beziehungen anzuzeigen.

    ![Auswählen der Elemente für die Anzeige der Beziehungen](../modeling/media/codemapsviewnewrelationships.png)

Siehe auch:

- [Durchsuchen und Neuanordnen von Code Maps](../modeling/browse-and-rearrange-code-maps.md)
- [Anpassen von Code Maps durch Bearbeiten der DGML-Dateien](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
- Ermitteln potenzieller Probleme im Code durch [Ausführen einer Analyse](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="view-specific-dependencies-in-a-code-map"></a>Anzeigen bestimmter Abhängigkeiten in einer Code Map

Angenommen, Sie verfügen über einen Code Review, der in einigen Dateien mit ausstehenden Änderungen durchgeführt werden muss. Um die Abhängigkeiten in diesen Änderungen anzuzeigen, können Sie eine Code Map aus diesen Dateien erstellen.

   ![Anzeigen bestimmter Abhängigkeiten in Codeübersichten](../modeling/media/codemapsspecificdependenciesintro.png)

1. Wählen Sie in **Projektmappen-Explorer** die Projekte, Assemblyverweise, Ordner, Dateien, Typen oder Member aus, die Sie zuordnen möchten.

   ![Auswählen der Elemente, die Sie zuordnen möchten](../modeling/media/codemapsselectinsolutionexplorer.png)

1. Wählen Sie auf der Symbolleiste **Projektmappen-Explorer** **in Code Map** die ![ Schaltfläche Neues Diagramm aus ausgewählten Knoten erstellen die Option anzeigen aus ](../modeling/media/createnewgraphfromselectedbutton.gif) . Oder öffnen Sie das Kontextmenü für eine oder eine Gruppe von Elementen, und wählen Sie **auf Code Map anzeigen** aus.

   Sie können auch Elemente aus **Projektmappen-Explorer**, **Klassenansicht** oder **Objektkatalog** in eine [neue](#add-a-code-map) oder vorhandene Code Map ziehen. Um die übergeordnete Hierarchie für die Elemente einzuschließen, halten Sie die **STRG** -Taste gedrückt, während Sie Elemente ziehen, oder verwenden Sie die Schaltfläche übergeordnete Elemente **einschließen** auf der Code Map Symbolleiste, um die Standardaktion anzugeben. Sie können Assemblydateien auch von außerhalb von Visual Studio ziehen, z. b. aus **Windows-Explorer**.

   > [!NOTE]
   > Wenn Sie Elemente aus einem Projekt hinzufügen, das von mehreren apps gemeinsam verwendet wird, z. b. Windows Phone oder Microsoft Store, werden diese Elemente in der Zuordnung mit dem derzeit aktiven App-Projekt angezeigt. Wenn Sie den Kontext für ein anderes App-Projekt ändern und mehrere Elemente aus dem freigegebenen Projekt hinzufügen, werden diese Elemente nun mit dem neuen aktiven App-Projekt angezeigt. Vorgänge, die Sie mit einem Element in der Zuordnung ausführen, gelten nur für solche Elemente, die denselben Kontext gemeinsam verwenden.

3. Die Code Map zeigt die ausgewählten Elemente in ihren enthaltenden Assemblys.

   ![Anzeigen der ausgewählten Elemente als Gruppen in der Zuordnung](../modeling/media/codemapsshowitemsfromsolnexplorer.png)

4. Um Elemente zu untersuchen, erweitern Sie diese. Bewegen Sie den Mauszeiger auf ein Element, und klicken Sie dann auf das Chevron (Abwärtspfeil), wenn es angezeigt wird.

   ![Erweitern eines Knotens in einer Code Map](../modeling/media/dependencygraph_containment.png)

   Um alle Elemente zu erweitern, wählen Sie diese mithilfe von **STRG** + **A** aus, öffnen Sie dann das Kontextmenü für die Karte, und wählen Sie **Gruppe**  >  **erweitern** aus. Diese Option ist jedoch nicht verfügbar, wenn das Erweitern aller Gruppen zu einer nicht verwendbaren Code Map oder zu Speicherproblemen führt.

5. Erweitern Sie bei Bedarf weitere Elemente, an denen Sie interessiert sind, und klicken Sie auf die Klassen-und Element Ebene.

   ![Erweitern von Gruppen auf Klassen- und Memberebene](../modeling/media/codemapsexpandtoclassandmember.png)

   Wenn Sie Elemente anzeigen möchten, die sich im Code befinden, aber nicht in der Zuordnung angezeigt werden, klicken Sie auf das Symbol untergeordnete Elemente **erneut abrufen** ![ ](../modeling/media/dependencygraph_deletednodesicon.png) in der oberen linken Ecke einer Gruppe.

6. Um weitere Elemente im Zusammenhang mit den auf der Code Map dargestellten anzuzeigen, wählen Sie ein Element aus, wählen Sie **Verwandte anzeigen** auf der Symbolleiste der Code Map aus, und wählen Sie dann den Typ verwandter Elemente aus, die der Code Map hinzugefügt werden sollen. Wählen Sie alternativ ein oder mehrere Elemente aus, öffnen Sie das Kontextmenü, und wählen Sie dann die Option **anzeigen** für den Typ verwandter Elemente aus, die der Karte hinzugefügt werden sollen. Zum Beispiel:

    Für eine **Assembly** wählen Sie Folgendes aus:

    |Option|Beschreibung|
    |-|-|
    |**Assemblys anzeigen, auf die verwiesen wird**|Fügt Assemblys hinzu, auf die diese Assembly verweist. Externe Assemblys werden in der Gruppe **Extern** angezeigt.|
    |**Assemblys anzeigen, die auf diese Funktion verweisen**|Fügt Assemblys in der Projektmappe hinzu, die auf diese Assembly verweisen.|

    Für einen **Namespace** wählen Sie **Enthaltende Assembly anzeigen** aus, falls sie nicht sichtbar ist.

    Für eine **Klasse** oder **Schnittstelle** wählen Sie Folgendes aus:

    |Option|Beschreibung|
    |-|-|
    |**Basistypen anzeigen**|Fügt einer Klasse die Basisklasse und die implementierten Schnittstellen hinzu.<br /><br /> Fügt einer Schnittstelle die Basisschnittstellen hinzu.|
    |**Abgeleitete Typen anzeigen**|Fügt bei einer Klasse die abgeleiteten Klassen hinzu.<br /><br /> Fügt bei einer Schnittstelle die abgeleiteten Schnittstellen und die implementierenden Klassen oder Strukturen hinzu.|
    |**Typen anzeigen, auf die verwiesen wird**|Fügt alle Klassen und deren Mitglieder hinzu, die diese Klasse verwendet.|
    |**Typen anzeigen, die auf diese Funktion verweisen**|Fügt alle Klassen und deren Mitglieder hinzu, die diese Klasse verwenden.|
    |**Enthaltenden Namespace anzeigen**|Fügt den übergeordneten Namespace hinzu.|
    |**Enthaltende/n Namespace und Assembly anzeigen**|Fügt die übergeordnete Containerhierarchie hinzu.|
    |**Alle Basistypen anzeigen**|Fügt die Basisklasse oder die Schnittstellenhierarchie rekursiv hinzu.|
    |**Alle abgeleiteten Typen anzeigen**|Fügt bei einer Klasse alle abgeleiteten Klassen rekursiv hinzu.<br /><br /> Fügt bei einer Schnittstelle alle abgeleiteten Schnittstellen und die implementierenden Klassen oder Strukturen rekursiv hinzu.|

     Für eine **Methode** wählen Sie Folgendes aus:

    |Option|Beschreibung|
    |-|-|
    |**Methode anzeigen, die aufruft**|Fügt die Methoden hinzu, die diese Methode aufruft.|
    |**Felder anzeigen, auf die verwiesen wird**|Fügt die Felder hinzu, auf die diese Methode verweist.|
    |**Enthaltenden Typ anzeigen**|Fügt den übergeordneten Typ hinzu.|
    |**Enthaltende/n Typ, Namespace und Assembly anzeigen**|Fügt die übergeordnete Containerhierarchie hinzu.|
    |**Überschriebene Methoden anzeigen**|Fügt bei einer Methode, die andere Methoden überschreibt oder die Methode einer Schnittstelle implementiert, alle abstrakten oder virtuellen Methoden in Basisklassen, die überschrieben werden, und ggf. die Methode der Schnittstelle, die implementiert wird, hinzu.|

     Für ein **Feld** oder eine **Eigenschaft** wählen Sie Folgendes aus:

    |Option|Beschreibung|
    |-|-|
    |**Enthaltenden Typ anzeigen**|Fügt den übergeordneten Typ hinzu.|
    |**Enthaltende/n Typ, Namespace und Assembly anzeigen**|Fügt die übergeordnete Containerhierarchie hinzu.|

    ![Anzeigen der durch dieses Member aufgerufenen Methoden](../modeling/media/codemapsshowrelatedmethods.png)

7. Die Beziehungen werden auf der Code Map angezeigt. In diesem Beispiel zeigt die Karte die von der-Methode aufgerufenen Methoden `Find` und ihre Position in der Projekt Mappe oder extern.

   ![Anzeigen bestimmter Abhängigkeiten in Codeübersichten](../modeling/media/codemapsspecificdependenciesintro.png)

8. Um die Code Map zu vereinfachen und sich auf einzelne Teile zu konzentrieren, wählen Sie **Filter** auf der Symbolleiste der Code Map aus, und wählen Sie dann nur die Knoten- und Linktypen aus, die für Sie von Interesse sind. Deaktivieren Sie z. B. die Anzeige von Projektmappenordnern, Assemblys und Namespaces.

   ![Verwenden des Filterbereichs zum Vereinfachen der Anzeige](../modeling/media/almcodemapfilterpane.png)

## <a name="see-also"></a>Siehe auch

- [Video: Nachvollziehen des Codeentwurfs mit Visual Studio 2015 Code Maps](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)
- [Verwenden von Code Maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md)
- [Zuordnen von Methoden in der Aufrufliste beim Debuggen](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
- [Ermitteln potenzieller Probleme mithilfe von Code Map-Analyzern](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Durchsuchen und Neuanordnen von Code Maps](../modeling/browse-and-rearrange-code-maps.md)
- [Anpassen von Code Maps durch Bearbeiten der DGML-Dateien](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
