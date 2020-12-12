---
title: Durchsuchen und Neuanordnen von Code Maps
description: Erfahren Sie, wie Sie Elemente in Code Maps neu anordnen können, um Sie leichter lesbar zu machen und die Leistung zu verbessern.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.progression.dgmlgraph.layouthelp
- vs.progression.graphdocument
- vs.progression.dgmlgraph.message.notUlt.noexpandgroup
- vs.progression.colorsetpicker
- vs.progression.iconsetpicker
helpviewer_keywords:
- Visual Studio Ultimate, dependency graphs
- code visualization [Visual Studio ALM]
- graph documents, browsing
- Visual Studio ALM, dependency graphs
- code visualization
- Visual Studio ALM, graph documents
- Visual Studio Ultimate, graph documents
- dependency graphs, browsing
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ace2095e98bc7d7425f518249a754fcbed07a02
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363613"
---
# <a name="browse-and-rearrange-code-maps"></a>Durchsuchen und Neuanordnen von Code Maps

Ordnen Sie Elemente in Codeübersichten neu an, damit sie leichter zu lesen sind und ihre Leistung gesteigert wird.

Sie können Codeübersichten ohne Auswirkungen auf den zugrunde liegenden Code in einer Projektmappe anpassen. Dies ist hilfreich, wenn Sie sich auf wichtige Elemente konzentrieren oder Ideen zum Code kommunizieren möchten. Um beispielsweise interessante Bereiche hervorzuheben, können Sie Codeelemente in der Übersicht auswählen und filtern, den Stil von Codeelemente und Links ändern, Codeelemente ausblenden oder löschen und Codeelemente mithilfe von Eigenschaften, Kategorien oder Gruppen organisieren.

 **Anforderungen**

- Um Codeübersichten erstellen zu können, müssen Sie über Visual Studio Enterprise verfügen.

- In Visual Studio Professional können Sie Codeübersichten anzeigen und diese im begrenzten Maße bearbeiten.

## <a name="get-started-working-with-code-maps"></a><a name="ManageLargeGraphs"></a> Einstieg in die Arbeit mit Code Maps

Erstellen Sie eine Code Map (Weitere Informationen finden Sie unterzuordnen von [Abhängigkeiten in ihren Lösungen](../modeling/map-dependencies-across-your-solutions.md) ). Wenn Sie nicht warten möchten, bis die Zuordnung abgeschlossen ist, klicken Sie jederzeit auf den Link **Abbrechen** , um den Generierungs Vorgang zu beenden. Allerdings werden in diesem Fall nicht die Details aller Abhängigkeiten und Links angezeigt.

Nachdem Sie die Übersicht generiert haben, beginnen Sie mit diesen Tipps zum Überprüfen des Codes:

- Achten Sie auf die natürlichen Abhängigkeitscluster im Code. Wählen Sie auf der Symbolleiste der Symbolleiste **Layout** **, schnell Cluster-** ![ Schaltfläche schnell Cluster auf der Diagramm Symbolleiste ](../modeling/media/quickclustersicon.gif) . Weitere Informationen finden Sie [unter Ändern des Kartenlayouts](#Selecting).

     ![Abhängigkeits Diagramm &#45; Layout für schnelle Cluster](../modeling/media/dependencygraph_quickclusters.png)

- Organisieren Sie die Übersicht in kleinere Bereiche, indem Sie verwandte Knoten gruppieren. Reduzieren Sie diese Gruppen, um nur die Abhängigkeiten zwischen den Gruppen zu sehen, die automatisch angezeigt werden. Siehe [Gruppenknoten](#OrganizeGroups).

- Verwenden Sie Filter, um die Übersicht zu vereinfachen und den Schwerpunkt auf die Typen von Knoten oder Links zu legen, an denen Sie interessiert sind. Weitere Informationen finden Sie unter [Filter Knoten und Links](#FilterNodes).

- Maximieren Sie die Leistung von großen Übersichten. Weitere Informationen finden Sie unterzuordnen von [Abhängigkeiten in ihren Lösungen](../modeling/map-dependencies-across-your-solutions.md) . Aktivieren Sie z. b. die Option **Build überspringen** auf der Kartensymbol Leiste, damit Visual Studio die Projekt Mappe nicht neu erstellt, wenn Sie Elemente auf der Karte aktualisieren.

## <a name="change-the-map-layout"></a><a name="Selecting"></a> Ändern des Kartenlayouts

|**An**|**Auszuführende Schritte**|
|-|-|
|Ordnen Sie den Abhängigkeitsverlauf für die gesamte Übersicht in einer bestimmten Richtung an. Dies kann Ihnen helfen, Architekturebenen im Code zu finden.|Wählen Sie auf der Kartensymbol Leiste **Layout** aus, und klicken Sie dann auf:<br /><br /> -   **Von oben nach unten** ![ Schaltfläche "oben nach unten" Diagramm](../modeling/media/topbottomgraphbutton.gif)<br />-   **Unten nach oben** ![ Schaltfläche "unten zum oberen Diagramm"](../modeling/media/bottomtopgraphbutton.gif)<br />-   **Von links nach rechts** ![ Layout-Schaltfläche von links nach rechts](../modeling/media/leftrightgraphbutton.gif)<br />-   **Von rechts nach links** ![ Schaltfläche "rechts nach links" Diagramm](../modeling/media/rightleftgraphbutton.gif)|
|Zeigen Sie natürliche Abhängigkeitscluster im Code an, wobei die Knoten mit den meisten Abhängigkeiten in der Mitte der Cluster und die Knoten mit den wenigsten Abhängigkeiten an der Außenseite der Cluster angezeigt werden.|Wählen Sie auf der Übersichts Symbolleiste **Layout** und dann auf der Diagramm Symbolleiste **schnell Cluster-** ![ Schaltfläche schnell Cluster aus ](../modeling/media/quickclustersicon.gif) .|
|Wählen Sie mindestens einen Knoten in der Übersicht aus.|Klicken Sie auf einen Knoten, um ihn auszuwählen. Halten Sie beim Klicken auf die **STRG** -Taste gedrückt, um mehrere Knoten auszuwählen oder zu deaktivieren.<br /><br /> Tastatur: Drücken Sie die **Tab** -Taste, oder verwenden Sie die Pfeiltasten, um das gepunktete Fokus Rechteck auf einen Knoten zu verschieben, und drücken Sie die **Taste** Drücken Sie die **STRG**  +  -**Taste** , um die Knoten mehrfach auszuwählen oder zu deaktivieren.|
|Verschieben Sie bestimmte Knoten in der Übersicht.|Ziehen Sie die Knoten, um sie zu verschieben. Zum Verschieben anderer Knoten und Links beim Ziehen von Knoten halten Sie die **UMSCHALT** Taste gedrückt.<br /><br /> Tastatur: halten Sie **STRG** gedrückt, und drücken Sie die Pfeiltasten.|
|Ändern Sie das Layout in einer Gruppe unabhängig von den anderen Knoten und Gruppen in der Übersicht.|Wählen Sie einen Knoten aus, und öffnen Sie das Kontextmenü. Wählen Sie **Layout** aus, und wählen Sie eine layoutart<br /><br /> - oder -<br /><br /> Wählen Sie einen Knoten, und erweitern Sie, um die untergeordneten Knoten angezeigt. Klicken Sie auf den Knoten Titel, um die Popup Symbolleiste der Gruppe anzuzeigen, und öffnen Sie die **layoutart des Gruppen** ![ Abhängigkeits Diagramms &#45; Gruppensymbol Leiste &#45; ](../modeling/media/dependencygraph_grouptoolbar.gif) Layoutliste. Wählen Sie eine der Struktur Layouts, **schnell Cluster** oder **Listenansicht** (die den Inhalt der Gruppe in einer Liste anordnet) aus.<br /><br /> Weitere Informationen finden Sie unter [Gruppenknoten](#OrganizeGroups) .|
|Machen Sie eine Aktion in der Übersicht rückgängig.|Drücken Sie **STRG**  +  **Z** , oder verwenden Sie den Visual Studio-Befehl **Rückgängig** .|

## <a name="browse-the-map"></a><a name="Explore"></a> Karte durchsuchen

|**An**|**Auszuführende Schritte**|
|-|-|
|Überprüfen Sie die Übersicht.|Ziehen Sie die Übersicht mithilfe der Maus in eine beliebige Richtung.<br /><br /> - oder -<br /><br /> Halten Sie die **UMSCHALT** Taste gedrückt, und drehen Sie das Mausrad, um horizontal Halten   +   Sie die UMSCHALTTASTE gedrückt, und drehen Sie das Mausrad, um horizontal zu scrollen|
|Vergrößern oder verkleinern Sie die Übersicht.|Drehen Sie das Mausrad.<br /><br /> - oder -<br /><br /> Verwenden Sie die Dropdown Liste **Zoom** auf der Code Map Symbolleiste.<br /><br /> - oder -<br /><br /> Verwenden Sie die Tastenkombinationen. Drücken Sie zum Vergrößern **STRG + UMSCHALT +.** (Punkt). Drücken Sie zum Vergrößern **STRG + UMSCHALT +,** (Komma).|
|Vergrößern Sie mit der Maus einen bestimmten Bereich.|Halten Sie die rechte Maustaste gedrückt, während Sie in diesem Bereich ein Rechteck um den für Sie interessanten Bereich aufziehen.|
|Ändern Sie die Größe der Übersicht, und passen Sie sie auf die Fenstergröße an.|Wählen Sie in der Code Map Symbolleiste in der Liste **Zoom** den Wert **Zoom** aus.<br /><br /> - oder -<br /><br /> Klicken Sie auf der Symbolleiste Code Map **auf das Symbol** Zoom Symbol Zoom auf der Symbolleiste Symbol ![ Leiste ](../modeling/media/almcodemapzoomicon.png) . Tastatur: Drücken Sie **STRG + 0** (null).|
|Suchen Sie anhand des Namens einen Knoten in der Übersicht. **Tipp:**  Dies funktioniert nur für Elemente in der Zuordnung. Um Elemente in der Projekt Mappe, aber nicht in der Zuordnung zu suchen, suchen Sie Sie in **Projektmappen-Explorer**, und ziehen Sie Sie dann auf die Karte. (Ziehen Sie Ihre Auswahl, oder klicken Sie auf der Symbolleiste **Projektmappen-Explorer** auf **in Code Map anzeigen**).|1. Klicken Sie **auf der Symbol** Leiste Code Map auf das Symbol Suche Symbol suchen auf der Symbolleiste der Symbolleiste ![ ](../modeling/media/almcodemapfindicon.png) (Tastatur: Drücken Sie **STRG + F**), um das Suchfeld in der oberen rechten Ecke der Karte anzuzeigen.<br />2. Geben Sie den Elementnamen ein, **und drücken Sie** die EINGABETASTE, oder klicken Sie auf das Bildschirm Symbol. Das erste Element, das mit dem Suchbegriff übereinstimmt, wird in der Übersicht hervorgehoben.<br />3. Öffnen Sie die Dropdown Liste, und wählen Sie eine Suchoption aus, um die Suche anzupassen. Die Optionen lauten **weiter** suchen, **Vorheriges suchen** und **Alles auswählen**. Klicken Sie auf die entsprechende Schaltfläche neben dem Textfeld „Suchen“.<br />     ![Dropdown&#45;Dropdown Liste "Suchoptionen"](../modeling/media/almcodemapssearchdropdown.png)<br />     Verwenden Sie alternativ die Tastatur: Drücken Sie **F3** , um den nächsten übereinstimmenden Knoten auszuwählen, oder **UMSCHALT + F3** , um den vorherigen übereinstimmenden Knoten auszuwählen.<br />4. Wählen Sie eine der Optionen aus, die angeben, wie Suchbegriffe behandelt werden, indem Sie auf die Symbole unter dem Such Textfeld klicken.<br />     ![Übereinstimmungsoptionen für Suche](../modeling/media/almcodemapssearchmatchicons.png)<br />     Die Optionen sind (von links nach rechts) für die Übereinstimmung unter Berücksichtigung der Groß-/Kleinschreibung, für die Übereinstimmung mit ganzem Wort, für die Verwendung der normalen .NET-Ausdruckssyntax und für das automatische Erweitern von Gruppen, um Übereinstimmungen für eingeschlossene Elemente anzuzeigen. **Wichtig:**  Sie können das Suchfeld verwenden, um Übereinstimmungen in reduzierten Gruppen nur zu suchen, wenn diese Gruppen zuvor erweitert wurden. Wählen Sie diese Option unter dem Suchfeld aus, um diese Übereinstimmungen zu suchen und ihre übergeordneten Gruppen automatisch zu erweitern.|
|Wählen Sie alle nicht markierten Knoten aus.|Öffnen Sie das Kontextmenü für die ausgewählten Knoten. Wählen Sie **auswählen**, **Auswahl umkehren** aus.|
|Wählen Sie weitere Knoten aus, die Links zu den ausgewählten Knoten aufweisen.|Öffnen Sie das Kontextmenü für die ausgewählten Knoten. Wählen **Sie auswählen** und eine der folgenden Optionen aus:<br /><br /> -Wählen Sie **eingehende Abhängigkeiten** aus, um zusätzliche Knoten auszuwählen, die direkt mit dem ausgewählten Knoten verknüpft sind.<br />-Wählen Sie **ausgehende Abhängigkeiten** aus, um weitere Knoten auszuwählen, die direkt aus dem ausgewählten Knoten verknüpft sind.<br />-Wählen Sie **beide** aus, um zusätzliche Knoten auszuwählen, die direkt zum bzw. aus dem ausgewählten Knoten verknüpft sind.<br />-Wählen Sie **verbundenes unter Diagramm** aus, um alle Knoten auszuwählen, die mit dem ausgewählten Knoten verknüpft sind.<br />-Wählen Sie untergeordnete Elemente aus, um alle untergeordneten Elemente des ausgewählten Knotens **auszuwählen.**|

## <a name="filter-nodes-and-links"></a><a name="FilterNodes"></a> Knoten und Verknüpfungen Filtern

|**An**|**Auszuführende Schritte**|
|-|-|
|Blenden Sie den Filterbereich ein oder aus.|Wählen Sie auf der Code Map Symbolleiste die Schaltfläche **Filter** aus. Der Bereich **Filter** wird standardmäßig als Seite im Registerkarten Format in **Projektmappen-Explorer** angezeigt.|
|Filtern Sie die Typen von Knoten, die in der Übersicht angezeigt werden.|Legen Sie die Kontrollkästchen in der Liste **Code Elemente** im Bereich Filter fest, oder deaktivieren Sie diese.|
|Filtern Sie die Typen von Links, die in der Übersicht angezeigt werden.|Legen Sie die Kontrollkästchen in der Liste **Beziehungen** im Bereich Filter fest, oder deaktivieren Sie diese.|
|Blenden Sie Testprojektknoten in der Übersicht ein oder aus.|Aktivieren oder deaktivieren Sie das Kontrollkästchen **Test Objekte** im Bereich Filter in der Liste **Verschiedenes** .|

Die im Bereich „Legende“ der Übersicht angezeigten Symbole spiegeln die von Ihnen in der Liste vorgenommenen Einstellungen wider. Um den Bereich Legende anzuzeigen oder auszublenden, klicken Sie auf der Code Map Symbolleiste auf die Schaltfläche **Legende** .

## <a name="examine-nodes-and-links"></a><a name="Inspect"></a> Knoten und Links überprüfen

In Codeübersichten werden die folgenden Arten von Links angezeigt:

- Ein einzelner Link stellt eine einzelne Beziehung zwischen zwei Knoten dar.

- Ein gruppenübergreifender Link stellt eine Beziehung zwischen zwei Knoten in unterschiedlichen Gruppen dar.

- Ein Aggregatlink stellt alle gleichgerichteten Beziehungen zwischen zwei Gruppen dar.

> [!TIP]
> Gruppenübergreifende Links werden in der Übersicht standardmäßig nur für ausgewählte Knoten angezeigt. Wenn Sie dieses Verhalten ändern möchten, um aggregierte Verknüpfungen zwischen Gruppen anzuzeigen oder auszublenden, klicken Sie auf der Code Map Symbolleiste auf **Layout** , wählen Sie **erweitert** und dann **alle gruppenübergreifenden Links anzeigen** aus, oder **blenden Sie alle gruppenübergreifenden Links** aus. Weitere Informationen finden Sie unter [Ausblenden oder Anzeigen von Knoten und Links](#HidingShowing) .

|**An**|**Auszuführende Schritte**|
|-|-|
|Zeigen Sie weitere Informationen zu einem Knoten oder Link an.|Bewegen Sie den Mauszeiger auf den Knoten oder Link, bis eine QuickInfo angezeigt wird.<br /><br /> Die QuickInfo eines Aggregatlinks enthält eine Liste der einzelnen Abhängigkeiten, die der Link darstellt.<br /><br /> - oder -<br /><br /> Öffnen Sie das Kontextmenü für den Knoten oder den Link. Wählen Sie **Bearbeiten**, **Eigenschaften** aus.|
|Zeigen Sie den Inhalt einer Gruppe an oder blenden Sie ihn aus.|-Um eine Gruppe zu erweitern, öffnen Sie das Kontextmenü für den Knoten, und wählen Sie **Gruppe**, **erweitern** aus.<br />     - oder -<br />     Bewegen Sie den Mauszeiger auf den Knoten, bis die Chevronschaltfläche (Pfeil nach unten) angezeigt wird. Klicken Sie auf diese Schaltfläche, um die Gruppe zu erweitern. Tastatur: Drücken Sie zum Erweitern oder reduzieren der ausgewählten Gruppe die **plus** -Taste ( **+** ) oder die **minus** -Taste ( **-** ).<br />-Um eine Gruppe zu reduzieren, öffnen Sie das Kontextmenü für den **Knoten, und** wählen Sie **Gruppe**, reduzieren aus.<br />     - oder -<br />     Bewegen Sie den Mauszeiger auf eine Gruppe, bis die Chevronschaltfläche (Pfeil nach oben) angezeigt wird. Klicken Sie auf diese Schaltfläche, um die Gruppe zu reduzieren.<br />-Um alle Gruppen zu erweitern, drücken Sie **STRG**  +  **A** , um alle Knoten auszuwählen. Öffnen Sie das Kontextmenü für die Karte, und wählen Sie **Gruppe**, **erweitern** aus. **Hinweis:**      Dieser Befehl ist nicht verfügbar, wenn das Erweitern aller Gruppen zu einer nicht verwendbaren Zuordnung oder zu Speicherproblemen führt. Es wird empfohlen, die Übersicht nur bis zu der Detailstufe zu erweitern, die Sie interessiert.<br />-Um alle Gruppen zu reduzieren, öffnen Sie das Kontextmenü für einen Knoten oder für die Karte. Wählen Sie **Gruppe** und dann **alle** reduzieren aus.|
|Zeigen Sie die Codedefinition für einen Namespace, einen Typ oder einen Member an.|Öffnen Sie das Kontextmenü für den Knoten, und wählen Sie **Gehe zu Definition** aus.<br /><br /> Oder<br /><br /> Doppelklicken Sie auf den Knoten. Doppelklicken Sie bei erweiterten Gruppen auf den Header für die Gruppe.<br /><br /> Oder<br /><br /> Wählen Sie den Knoten aus, und drücken Sie **F12**.<br /><br /> Zum Beispiel:<br /><br /> -Bei einem Namespace, der eine Klasse enthält, wird die Codedatei für die Klasse geöffnet, um die Definition dieser Klasse anzuzeigen. In anderen Fällen zeigt das Fenster " **Symbol Ergebnisse suchen** " eine Liste von Code Dateien an. **Hinweis:**      Wenn Sie diese Aufgabe für einen Visual Basic Namespace ausführen, wird die Codedatei hinter dem Namespace nicht geöffnet. Dieses Problem tritt auch auf, wenn Sie diese Aufgabe für eine Gruppe ausgewählter Knoten ausführen, die einen Visual Basic Namespace enthalten. Sie können dieses Problem umgehen, indem Sie manuell zu der Codedatei hinter dem Namespace navigieren oder den Knoten für den Namespace nicht in die Auswahl einbeziehen.<br />-Bei einer Klasse oder einer partiellen Klasse wird die Codedatei für diese Klasse geöffnet, um die Klassendefinition anzuzeigen.<br />-Bei einer Methode wird die Codedatei für die übergeordnete Klasse geöffnet, um die Methoden Definition anzuzeigen.|
|Überprüfen Sie die Abhängigkeiten und Elemente, die Teil eines Aggregatlinks sind.|Wählen Sie die gewünschten Links aus, und öffnen Sie das Kontextmenü für Ihre Auswahl. Wählen Sie zugehörige **Verknüpfungen anzeigen**  oder zugehörige **Links auf neuer Code Map anzeigen aus**.<br /><br /> Visual Studio erweitert die Gruppen an beiden Enden des Links und zeigt nur die Elemente und Abhängigkeiten an, die zu dem Link gehören. **Hinweis:**  Wenn Sie Abhängigkeiten zwischen Elementen in partiellen Gruppen überprüfen, wird dieses Verhalten möglicherweise angezeigt: <ul><li>Links zu Elementen, die nicht an der Überprüfung teilnehmen, verschwinden in der Zuordnung, auch wenn diese Links weiterhin vorhanden sind.</li><li>Angenommen, Sie überprüfen einen Link zu einem Element in einer partiellen Gruppe und überprüfen später einen anderen Link zum selben Element. Während der zweiten Überprüfung werden in der partiellen Gruppe des Ziels nur Elemente der ersten Prüfung angezeigt. Links und Ziel Elemente, die nicht an ihrer ersten Prüfung beteiligt waren, aber an ihrer zweiten Prüfung teilnehmen, werden nicht angezeigt.</li></ul> Wenn Sie fehlende Elemente aus einer Gruppe anzeigen möchten **, wählen Sie** untergeordnete Elemente erneut abrufen aus ![ ](../modeling/media/dependencygraph_deletednodesicon.png) . (Dies bedeutet, dass nicht alle Mitglieder einer Gruppe auf der Karte angezeigt werden). Sie können auch versuchen, die Aktionen zu wiederholen (Tastatur: Drücken Sie **STRG + Z**), und überprüfen Sie die Abhängigkeiten auf einer neuen Karte.|
|Überprüfen Sie die Abhängigkeiten zwischen mehreren Knoten in unterschiedlichen Gruppen.|Erweitern Sie die Gruppen, sodass alle untergeordneten Elemente angezeigt werden. Wählen Sie alle für Sie interessanten Knoten aus – einschließlich der untergeordneten Elemente. In der Übersicht werden die gruppenübergreifenden Links zwischen den ausgewählten Knoten angezeigt.<br /><br /> Wenn Sie alle Knoten in einer Gruppe auswählen möchten, halten Sie die **UMSCHALT** Taste und die linke Maustaste gedrückt, während Sie ein Rechteck um diese Gruppe zeichnen. Drücken Sie **STRG** a, um alle Knoten auf einer Karte auszuwählen + . **Tipp:**  Wenn Sie gruppenübergreifende Links jederzeit anzeigen möchten, klicken Sie auf der Kartensymbol Leiste auf **Layout** , **erweitert**, **alle gruppenübergreifenden Links anzeigen**.|
|Zeigen Sie die Elemente an, auf die von einem Knoten oder Link verwiesen wird.|Öffnen Sie das Kontextmenü für den Knoten, und wählen Sie **alle Verweise suchen** aus. **Hinweis:**  Dies gilt nur, wenn das `Reference` -Attribut für den Knoten oder den Link in der dgml-Datei der Zuordnung festgelegt ist. Informationen zum Hinzufügen von Verweisen auf Elemente von Knoten oder Links finden Sie unter [Anpassen von Code Maps durch Bearbeiten der dgml-Dateien](../modeling/customize-code-maps-by-editing-the-dgml-files.md).|

## <a name="hide-or-show-nodes-and-links"></a><a name="HidingShowing"></a> Ausblenden oder Anzeigen von Knoten und Links

Wenn Knoten ausgeblendet werden, werden sie von Layoutalgorithmen nicht berücksichtigt. Gruppenübergreifende Links werden standardmäßig ausgeblendet. Gruppenübergreifende Links sind einzelne Links, durch die Knoten über Gruppen hinweg verbunden sind. Beim Reduzieren von Gruppen werden alle gruppenübergreifenden Links in der Übersicht zu einzelnen Links zwischen Gruppen aggregiert. Wenn Sie eine Gruppe erweitern und Knoten in der Gruppe auswählen, werden gruppenübergreifende Links angezeigt, die die Abhängigkeiten in dieser Gruppe darstellen.

> [!CAUTION]
> Vergewissern Sie sich, dass alle Knoten bzw. gruppenübergreifenden Links, die andere Benutzer sehen sollen, eingeblendet sind, bevor Sie eine Übersicht für Benutzer von Visual Studio Professional freigeben, die in Visual Studio Enterprise erstellt wurde. Andernfalls können diese Benutzer diese Elemente nicht einblenden.

### <a name="to-hide-or-show-nodes"></a>So blenden Sie Knoten ein oder aus

|**An**|**Auszuführende Schritte**|
|-|-|
|Blenden Sie die ausgewählten Knoten aus.|1. Wählen Sie die Knoten aus, die Sie ausblenden möchten.<br />2. Öffnen Sie das Kontextmenü für die ausgewählten Knoten oder für die Karte. Wählen Sie **auswählen** und dann **ausgewählte ausblenden** aus.|
|Blenden Sie nicht ausgewählte Knoten aus.|1. Wählen Sie die Knoten aus, die sichtbar bleiben sollen.<br />2. Öffnen Sie das Kontextmenü für die ausgewählten Knoten oder für die Karte. Wählen Sie **auswählen** und dann **nicht ausgewählt ausblenden** aus.|
|Zeigen Sie ausgeblendete Knoten an.|-Um alle ausgeblendeten Knoten in einer Gruppe anzuzeigen, stellen Sie zunächst sicher, dass die Gruppe erweitert ist. Öffnen Sie das Kontextmenü, und wählen **Sie auswählen**, untergeordnete Elemente **Einblenden** aus.<br />     - oder -<br />     Klicken Sie  ![ in der oberen linken Ecke der Gruppe auf das Symbol für untergeordnete Elemente für untergeordnete Elemente einblenden ](../modeling/media/dependencygraph_filtericon_hiddennodes.gif) (dieses ist nur sichtbar, wenn verborgene untergeordnete Knoten vorhanden sind).<br />-Um alle ausgeblendeten Knoten anzuzeigen, öffnen Sie das Kontextmenü für die Karte oder einen Knoten, und wählen Sie **auswählen**, **Alle einblenden** aus.|

### <a name="to-hide-or-show-links"></a>So blenden Sie Links ein oder aus

|**An**|**Wählen Sie auf der Übersichtssymbolleiste Layout, Erweitert und dann Folgendes aus:**|
|-|-|
|Dauerhaftes Anzeigen gruppenübergreifender Links.|**Alle gruppenübergreifenden Links anzeigen**. Bei Auswahl dieser Option werden Aggregatlinks zwischen Gruppen ausgeblendet.|
|Dauerhaftes ausblenden gruppenübergreifender Links.|**Alle gruppenübergreifenden Links ausblenden**|
|Anzeigen ausschließlich gruppenübergreifender Links für ausgewählte Knoten.|**Gruppenübergreifende Links für ausgewählte Knoten anzeigen**|
|Alle Links ausblenden.|**Alle Links ausblenden**. Wählen Sie eine der oben aufgeführten Optionen aus, um Links erneut anzuzeigen.|

## <a name="group-nodes"></a><a name="OrganizeGroups"></a> Knoten gruppieren

|**An**|**Auszuführende Schritte**|
|-|-|
|Zeigen Sie Containerknoten als Gruppen- oder Blattknoten an.|So zeigen Sie Container Knoten als Blattknoten an: Wählen Sie die Knoten aus, öffnen Sie das Kontextmenü für Ihre Auswahl, und wählen Sie **Gruppe**, **in Blatt konvertieren** aus.<br /><br /> So zeigen Sie Container Knoten als Gruppenknoten an: Wählen Sie die Knoten aus, öffnen Sie das Kontextmenü für Ihre Auswahl, und wählen Sie **Gruppe**, **in Gruppe konvertieren** aus.|
|Ändern Sie das Layout in einer Gruppe.|Wählen Sie die Gruppe aus, öffnen Sie das Kontextmenü, wählen Sie **Layout** aus, und wählen Sie die gewünschte layoutart aus.<br /><br /> - oder -<br /><br /> 1. Wählen Sie die Gruppe aus, und stellen Sie sicher, dass Sie erweitert ist.<br />2. Klicken Sie erneut auf den Gruppen Header, und die Gruppensymbol Leiste wird angezeigt.<br />     ![Abhängigkeits Diagramm &#45; Gruppensymbol Leiste](../modeling/media/dependencygraph_group.png)<br />3. Öffnen Sie die **layoutart des Gruppen** Listen- ![ Abhängigkeits Diagramms &#45; Gruppensymbol Leiste &#45; Layout, ](../modeling/media/dependencygraph_grouptoolbar.gif) und wählen Sie die gewünschte layoutart aus.<br /><br /> In der **Listenansicht** werden die Mitglieder der Gruppe in der Liste neu angeordnet. **Graph default** setzt das Gruppen Layout auf das Karten Standardlayout zurück. Weitere Optionen finden Sie unter [Ändern des Kartenlayouts](#Selecting).|
|Fügen Sie einen Knoten zu einer Gruppe hinzu.|Ziehen Sie den Knoten auf die Gruppe.<br /><br /> Während Sie den Knoten ziehen, wird von Visual Studio durch einen Indikator angezeigt, dass Sie den Knoten verschieben.<br /><br /> Sie können Knoten auch aus einer Gruppe herausziehen.|
|Fügen Sie einen Knoten zu einem Knoten hinzu, der zu keiner Gruppe gehört.|Ziehen Sie den Knoten auf den Zielknoten. Sie können beliebige Zielknoten in eine Gruppe konvertieren, indem Sie ihm Knoten hinzufügen.|
|Gruppieren Sie ausgewählte Knoten.|1. Wählen Sie die Knoten aus, die Sie gruppieren möchten. Über dem zuletzt ausgewählten Knoten wird eine Popupsymbolleiste angezeigt.<br />     ![Abhängigkeitsdiagramm-Symbolleiste](../modeling/media/depedencygraph_toolbar.png)<br />2. Wählen Sie auf der Symbolleiste das vierte Symbol **Gruppieren der ausgewählten Knoten** aus (wenn der Knoten erweitert ist, werden fünf anstelle von vier Symbolen angezeigt). Geben Sie den Namen für die neue Gruppe ein, und drücken Sie **Return**.<br />     - oder -<br />     Wählen Sie die zu gruppierenden Knoten aus, und öffnen Sie das Kontextmenü für Ihre Auswahl. Wählen Sie **Gruppe**, über **geordnete Gruppe hinzufügen** aus, geben Sie den Namen für die neue Gruppe ein, und drücken Sie **zurück**.<br /><br /> Sie können eine Gruppe umbenennen. Öffnen Sie das Kontextmenü für die Gruppe, und wählen Sie **Bearbeiten**, **Eigenschaften** aus, um die Visual Studio-Eigenschaftenfenster zu öffnen. Benennen Sie die Gruppe in der Eigenschaft **Bezeichnung** nach Bedarf um.|
|Entfernen Sie Gruppen.|Wählen Sie die Gruppe oder die Gruppen aus, die Sie entfernen möchten. Öffnen Sie das Kontextmenü für Ihre Auswahl, und wählen Sie **Gruppe**, **Gruppe entfernen** aus.|
|Entfernen Sie Knoten aus der übergeordneten Gruppe.|Wählen Sie die Knoten aus, die Sie verschieben möchten. Öffnen Sie das Kontextmenü für Ihre Auswahl, und wählen Sie **Gruppe**, aus übergeordnetem Element **Entfernen aus**. Dadurch werden Knoten bis zur zweiten übergeordneten Ebene oder außerhalb der Gruppe entfernt, wenn keine zweite übergeordnete Ebene vorhanden ist.<br /><br /> - oder -<br /><br /> Wählen Sie die Knoten aus, und ziehen Sie sie aus der Gruppe.|

## <a name="add-remove-or-rename-nodes-links-and-comments"></a><a name="AddRemoveNodesLinks"></a> Hinzufügen, entfernen oder Umbenennen von Knoten, Links und Kommentaren

Sie können in einer Übersicht mehr oder weniger Elemente anzeigen, um Detailinformationen einzublenden oder die Übersicht zu vereinfachen. Sie können Elemente auch entfernen und ihnen Kommentare hinzufügen.

> [!CAUTION]
> Vergewissern Sie sich vor dem Freigeben einer mit Visual Studio Enterprise erstellten Übersicht für Benutzer von Visual Studio Professional, dass alle Codeelemente in der Übersicht angezeigt werden, die für andere angezeigt werden sollen. Andernfalls können diese Benutzer gelöschte Codeelemente nicht abrufen.

### <a name="add-a-node-for-a-code-element"></a>Hinzufügen eines Knotens für ein Codeelement

|**An**|**Auszuführende Schritte**|
|-|-|
|Fügen Sie einen neuen generischen Knoten an der aktuellen Position des Mauszeigers hinzu.|1. bewegen Sie den Mauszeiger an die Stelle auf der Karte, an der Sie das neue Code Element platzieren möchten, und drücken Sie **Einfügung**.<br />     - oder -<br />     Öffnen Sie das Kontextmenü für die Karte, und wählen Sie **Bearbeiten**, **Hinzufügen**, **generischer Knoten** aus.<br />2. Geben Sie den Namen für den neuen Knoten ein, **und drücken Sie** die EINGABETASTE.|
|Fügen Sie eine bestimmte Art von Codeelementknoten an der aktuellen Position des Mauszeigers ein.|1. bewegen Sie den Mauszeiger an die Stelle auf der Karte, an der Sie das neue Code Element platzieren möchten, und öffnen Sie das Kontextmenü für die Karte.<br />2. Wählen Sie **Bearbeiten**, **Hinzufügen** aus, und wählen Sie den Typ des gewünschten Knotens aus.<br />3. Geben Sie den Namen für den neuen Knoten ein, **und drücken Sie** die EINGABETASTE.|
|Fügen Sie einen generischen oder eine bestimmte Art von Codeelementknoten zu einer Gruppe hinzu.|1. Wählen Sie den Gruppenknoten aus, und öffnen Sie das Kontextmenü.<br />2. Wählen Sie **Bearbeiten**, **Hinzufügen** aus, und wählen Sie den Typ des gewünschten Knotens aus.<br />3. Geben Sie den Namen für den neuen Knoten ein, **und drücken Sie** die EINGABETASTE.|
|Fügen Sie einen neuen Knoten desselben Typs hinzu, der mit einem vorhandenen Knoten verknüpft ist.|1. Wählen Sie das Code Element aus. Darüber wird eine Popupsymbolleiste angezeigt.<br />     ![Abhängigkeitsdiagramm-Symbolleiste](../modeling/media/depedencygraph_toolbar.png)<br />2. Wählen Sie auf der Symbolleiste das zweite Symbol aus, **und erstellen Sie einen Knoten mit derselben Kategorie wie dieser Knoten, und fügen Sie ihm einen neuen Link hinzu**.<br />3. Wählen Sie eine Position auf der Karte aus, um das neue Code Element zu platzieren, und klicken Sie auf die linke Maustaste.<br />4. Geben Sie den Namen für den neuen Knoten ein, **und drücken Sie** die EINGABETASTE.|
|Fügen Sie einen neuen generischen Knoten hinzu, der mit einem vorhandenen Codeleement verknüpft ist, das über den Fokus verfügt.|1. Drücken Sie mithilfe der Tastatur die **Tab** -Taste, bis das Code Element, mit dem verknüpft werden soll, den Fokus hat (gepunktetes Rechteck)<br />2. Drücken Sie **alt** + **Einfügung**.<br />3. Geben Sie den Namen für den neuen Knoten ein, **und drücken Sie** die EINGABETASTE.|
|Fügen Sie einen neuen generischen Knoten hinzu, der mit einem vorhandenen Codeleement verknüpft ist, das über den Fokus verfügt.|1. Drücken Sie mithilfe der Tastatur die **Tab** -Taste, bis das Code Element, mit dem verknüpft werden soll, den Fokus hat (gepunktetes Rechteck)<br />2. Drücken Sie die UMSCHALTTASTE **alt** + **UMSCHALT** + .<br />3. Geben Sie den Namen für den neuen Knoten ein, **und drücken Sie** die EINGABETASTE.|

|**So fügen Sie Codeelemente hinzu für**|**Auszuführende Schritte**|
|-|-|
|Codeelemente in der Projektmappe.|1. Suchen Sie das Code-Element in **Projektmappen-Explorer**. Verwenden Sie das Suchfeld **Projektmappen-Explorer** , oder Durchsuchen Sie die Projekt Mappe. **Tipp:**      Öffnen Sie zum Suchen von Code Elementen, die Abhängigkeiten von einem Typ oder Member aufweisen, das Kontextmenü für den Typ oder den Member in **Projektmappen-Explorer**. Wählen Sie die Beziehung aus, die Sie interessiert. In **Projektmappen-Explorer** werden nur die Code Elemente mit den angegebenen Abhängigkeiten angezeigt.<br />2. ziehen Sie die Code Elemente, die Sie interessieren, auf die Zuordnungs Oberfläche. Sie können Codeelemente auch aus der Klassenansicht oder dem Objektkatalog ziehen.<br />     - oder -<br />     Wählen Sie in **Projektmappen-Explorer** die Code Elemente aus, die Sie zuordnen möchten. Klicken Sie dann auf der Symbolleiste **Projektmappen-Explorer** auf **in Code Map anzeigen**.<br /><br /> Standardmäßig wird die übergeordnete Containerhierarchie für die neuen Codeelemente in der Übersicht angezeigt. Verwenden Sie die Schaltfläche übergeordnete Elemente **einschließen** auf der Code Map Symbolleiste, um dieses Verhalten zu ändern Wenn diese Option deaktiviert ist, wird nur das Codeelement zur Übersicht hinzugefügt. Wenn Sie dieses Verhalten nur für eine Drag & Drop-Aktion umkehren möchten, halten Sie die **STRG** -Taste gedrückt, während Sie die Code Elemente in die Karte ziehen.<br /><br /> Von Visual Studio werden Codeelemente für die Codeelemente der obersten Ebene in der Auswahl hinzugefügt. Bewegen Sie den Mauszeiger über dem Anfang des Codeelements, sodass das Chevron (Pfeil nach unten) angezeigt wird, um zu prüfen, ob ein Codeelement andere Codeelemente enthält. Wählen Sie das Chevron aus, um das Codeelement zu erweitern. Wenn Sie alle Code Elemente erweitern möchten, drücken Sie **STRG** + **A** , um alle Elemente auszuwählen, öffnen Sie das Kontextmenü für die Karte, und wählen Sie **Gruppe**, **erweitern** aus. Dieser Befehl ist nicht verfügbar, wenn das Erweitern aller Gruppen zu einer nicht verwendbaren Übersicht oder zu Speicherproblemen führt.|
|Auf Codeelemente in der Übersicht bezogene Codeelemente.|Klicken Sie auf der Code Map Symbolleiste auf die Schaltfläche **Verwandte anzeigen** , und wählen Sie den Typ verwandter Elemente aus, die Sie interessieren.<br /><br /> - oder -<br /><br /> Öffnen Sie das Kontextmenü für das Codeelement. Wählen Sie je nach Art der Beziehung, die Sie interessiert, eines der Elemente **anzeigen...** im Menü aus. Beispielsweise können Sie Elemente, auf die das aktuelle Element verweist, Elemente, die auf das aktuelle Element verweisen, Basis- und abgeleitete Typen für Klassen, Methodenaufrufer und die enthaltenden Klassen, Namespaces sowie Assemblys anzeigen.<br /><br /> Weitere Informationen finden Sie in [diesem Thema](../modeling/map-dependencies-across-your-solutions.md).|
|Kompilierte .NET-Assemblys (DLL oder EXE) oder Binärdateien.|Ziehen Sie die Assemblys oder Binärdateien, die sich außerhalb von Visual Studio befinden, in eine Übersicht.<br /><br /> Das Ziehen aus Windows-Explorer oder Datei-Explorer ist nur möglich, wenn der betreffende Explorer und Visual Studio auf der gleichen Berechtigungsstufe der Benutzerkontensteuerung (User Account Control, UAC) ausgeführt werden. Beispiel: Wenn Sie Visual Studio bei aktivierter UAC als Administrator ausführen, wird der Ziehvorgang von Windows-Explorer oder Datei-Explorer blockiert.|

### <a name="AddNodes"></a>

#### <a name="add-a-link-between-existing-code-elements"></a>Hinzufügen von Links zwischen vorhandenen Codeelementen

1. Wählen Sie das Quellcodeelement aus. Über dem Codeelement wird eine Symbolleiste angezeigt.

    ![Abhängigkeitsdiagramm-Symbolleiste](../modeling/media/depedencygraph_toolbar.png)

2. Wählen Sie auf der Symbolleiste das erste Symbol aus, und erstellen Sie einen **neuen Link von diesem Knoten zu dem Knoten, auf den Sie als nächstes klicken**.

3. Wählen Sie das Zielcodeelement aus. Zwischen den beiden Codeelementen wird ein Link angezeigt.

**OR**

1. Wählen Sie das Quellcodeelement in der Übersicht aus.

2. Wenn Sie eine Maus installiert haben, bewegen Sie den Mauszeiger außerhalb der Begrenzungen der Übersicht.

3. Öffnen Sie das Kontextmenü des Code Elements, und wählen Sie **Bearbeiten**  >    >  **generischen Link** hinzufügen aus.

4. Wechseln Sie mithilfe der TABULATORTASTE zum Zielknotenelement für den Link.

5. Drücken Sie die **EINGABETASTE**.

### <a name="AddComments"></a>

#### <a name="add-a-comment-to-an-existing-node-on-the-map"></a>Hinzufügen eines Kommentars zu einem vorhandenen Knoten in der Übersicht

1. Wählen Sie das Codeelement aus. Darüber wird eine Symbolleiste angezeigt.

     ![Abhängigkeitsdiagramm-Symbolleiste](../modeling/media/depedencygraph_toolbar.png)

2. Wählen Sie auf der Symbolleiste das dritte Symbol aus, und **Erstellen Sie einen neuen Kommentar Knoten mit einem neuen Link zum ausgewählten Knoten**.

     \- oder -

     Öffnen Sie das Kontextmenü für das Code Element, und wählen Sie  >  **neuen Kommentar** bearbeiten aus.

3. Geben Sie Ihre Kommentare ein. Drücken Sie **UMSCHALT** Taste, um eine neue Zeile einzugeben  +  .

#### <a name="add-a-comment-to-the-map-itself"></a>Hinzufügen eines Kommentars zur Übersicht

1. Öffnen Sie das Kontextmenü für die Karte, und wählen Sie  >  **neuen Kommentar** bearbeiten aus.

2. Geben Sie Ihre Kommentare ein. Drücken Sie **UMSCHALT** Taste, um eine neue Zeile einzugeben  +  .

### <a name="RenameNodes"></a>

#### <a name="rename-a-code-element-or-link"></a>Umbenennen eines Codeelements oder Links

1. Wählen Sie das Codeelement oder den Link aus, das bzw. der umbenannt werden soll.

2. Drücken Sie **F2**, oder öffnen Sie das Kontextmenü, und wählen Sie   >  **Umbenennen** bearbeiten aus.

3. Wenn das Eingabefeld in der Übersicht angezeigt wird, benennen Sie das Codeelement oder den Link um.

**OR**

1. Öffnen Sie das Kontextmenü, und wählen Sie  >  **Eigenschaften** bearbeiten aus.

2. Bearbeiten Sie die Eigenschaft **Bezeichnung** in der Visual Studio-Eigenschaftenfenster.

#### <a name="remove-a-code-element-or-link-from-the-map"></a>Entfernen eines Codeelements oder Links aus der Übersicht

1. Wählen Sie das Code Element oder den Link, und drücken Sie die ENTF **-Taste.**

     \- oder -

     Öffnen **Sie das** Kontextmenü für das Code Element oder den Link, und wählen Sie "  >  **Entfernen**" aus.

2. Wenn das Element oder der Link Teil einer Gruppe ist, wird die Schaltfläche untergeordnete Elemente erneut **Abrufen** ![ ](../modeling/media/dependencygraph_deletednodesicon.png) in der Gruppe angezeigt. Klicken Sie auf diese Option, um fehlende Elemente und Links abzurufen.

- Sie können Codeelemente und Links ohne Auswirkungen auf den zugrunde liegenden Code aus einer Übersicht entfernen. Wenn Sie diese löschen, werden die zugehörigen Definitionen aus der DGML-Datei (.dgml) entfernt.

- Die über die DGML-Datei durch Hinzufügen nicht definierter Codeelemente oder durch Verwenden früherer Versionen von Visual Studio erstellten Übersichten unterstützen diese Funktion nicht.

#### <a name="flag-a-code-element-for-follow-up"></a>Kennzeichnen eines Codeelements zur Nachverfolgung

1. Wählen Sie das Codeelement oder den Link aus, das bzw. den Sie zur Nachverfolgung kennzeichnen möchten.

2. Öffnen Sie das Kontextmenü, und wählen Sie Flag **Bearbeiten**  >  **für Nachverfolgung aus**.

- Das Codeelement erhält standardmäßig einen roten Hintergrund. [Fügen Sie einen Kommentar hinzu](#AddComments) , der die entsprechenden nach Verfolgungs Informationen bietet.

- Ändern Sie die Hintergrundfarbe des Elements, oder löschen Sie das nach Verfolgungs Flag, indem Sie  >  **andere Flag-Farben** bearbeiten auswählen.

## <a name="change-the-style-of-a-code-element-or-link"></a><a name="ChangeStyleCodeOrLink"></a> Ändern des Stils eines Code Elements oder Links

Sie können die Symbole für Codeelemente und die Farben von Codeelementen und Links mithilfe vordefinierter Symbole und Farben ändern. Sie können z. B. eine Farbe auswählen, um Codeelemente und Links hervorzuheben, die eine bestimmte Kategorie oder Eigenschaft aufweisen. Dadurch können Sie bestimmte Bereiche der Übersicht kennzeichnen und sich auf diese Bereiche konzentrieren. Sie können benutzerdefinierte Symbole und Farben angeben, indem Sie die dgml-Datei der Karte bearbeiten. Informationen finden Sie [unter Anpassen von Code Maps durch Bearbeiten der dgml-Dateien](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

### <a name="to-apply-a-predefined-color-or-icon-to-code-elements-or-links-with-a-certain-category-or-property"></a>So wenden Sie eine vordefinierte Farbe oder ein vordefiniertes Symbol auf Codelemente oder Links mit einer bestimmten Kategorie oder Eigenschaft an

1. Wählen Sie auf der Symbolleiste der Karte **Legende** aus.

2. Überprüfen Sie im Feld **Legende** , ob die Kategorie oder Eigenschaft des Code Elements bereits in der Liste angezeigt wird.

3. Wenn die Kategorie oder Eigenschaft nicht in der Liste enthalten ist, wählen Sie **+** im Feld **Legende** aus, und wählen Sie dann **Knoten Eigenschaft**, **Knoten Kategorie**, Verknüpfungs **Eigenschaft** oder Verknüpfungs **Kategorie** aus. Wählen Sie dann die Eigenschaft oder Kategorie aus. Die Kategorie oder Eigenschaft wird jetzt im Feld **Legende** angezeigt.

    > [!NOTE]
    > Um einem Code Element eine Kategorie oder eine Eigenschaft zu erstellen und zuzuweisen, können Sie die dgml-Datei der Karte bearbeiten. Informationen finden Sie [unter Anpassen von Code Maps durch Bearbeiten der dgml-Dateien](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

4. Klicken Sie im Feld **Legende** auf das Symbol neben der Kategorie oder Eigenschaft, die Sie hinzugefügt haben oder die Sie ändern möchten.

5. Orientieren Sie sich beim Auswählen des zu ändernden Stils an der folgenden Tabelle:

    |**Zu änderndes Merkmal**|**Auswählen**|
    |-|-|
    |Hintergrundfarbe|**Hintergrund**|
    |Konturfarbe|**Stellung**|
    |Textfarbe (der Buchstabe "f" wird angezeigt, um das Ergebnis anzuzeigen)|**Vordergrund**|
    |Symbol|**Symbole**|

     Das Dialogfeld **Farbsatz** Auswahl oder **Symbolsatz** Auswahl wird angezeigt, damit Sie eine Farbe oder ein Symbol auswählen können.

6. Führen Sie im Dialogfeld **Farbsatz** **Auswahl oder Symbolsatz Auswahl** einen der folgenden Schritte aus:

    |**Anzuwendendes Merkmal**|**Auszuführende Schritte**|
    |-|-|
    |Farbsatz oder Symbolsatz|Öffnen Sie die Liste Farbe (oder **Symbol** **Satz** ) **auswählen** . Wählen Sie einen Farbsatz oder Symbolsatz aus.|
    |Bestimmte Farbe oder bestimmtes Symbol|Öffnen Sie die Liste für Kategorie- bzw. Eigenschaftswerte. Wählen Sie eine Farbe oder ein Symbol aus.|

    > [!NOTE]
    > Im Feld **Legende** können Stile neu angeordnet, gelöscht oder vorübergehend deaktiviert werden. Weitere Informationen finden Sie [unter Edit the Legend Box](#ModifyLegend).

## <a name="edit-the-legend-box"></a><a name="ModifyLegend"></a> Bearbeiten des Felds "Legende"

Im Feld **Legende** können Stile neu angeordnet, gelöscht oder vorübergehend deaktiviert werden:

1. Öffnen Sie das Kontextmenü für einen Stil im Feld **Legende** .

2. Führen Sie eine der folgenden Aufgaben aus:

    |**An**|**Auswählen**|
    |-|-|
    |Deaktivieren des Codeelements|**Deaktivieren**|
    |Löschen des Codeelements|**Löschen**|
    |Verschieben des Stils nach oben|**Nach oben**|
    |Verschieben des Codeelements nach unten|**Nach unten**|

## <a name="copy-styles-from-one-map-to-another"></a><a name="CopyLegend"></a> Kopieren von Stilen aus einer Zuordnung in eine andere

1. Stellen Sie sicher, dass das Feld **Legende** in der Quell Zuordnung angezeigt wird. Wenn Sie nicht angezeigt wird, klicken Sie auf der Symbolleiste der Zuordnung auf **Legende**.

2. Öffnen Sie das Kontextmenü für das Feld **Legende** . Wählen Sie **Legende kopieren** aus.

3. Fügen Sie die Legende in der Zielübersicht ein.

## <a name="merge-code-maps"></a><a name="MergeMaps"></a> Zusammenführen von Code Maps

Sie können Übersichten durch Kopieren und Einfügen von Codeelementen zwischen Übersichten zusammenführen. Wenn die Codeelementbezeichner übereinstimmen, entspricht das Einfügen von Codeelementen einem Zusammenführungsvorgang. Sie können diese Aufgabe vereinfachen, indem Sie alle zu visualisierenden Assemblys oder Binärdateien im selben Ordner ablegen, damit der vollständige Pfad jeder Assembly oder Binärdatei für jede Übersicht, die Sie zusammenführen möchten, gleich ist.

Alternativ können Sie diese Assemblys oder Binärdateien aus diesem Ordner in dieselbe Übersicht ziehen.

## <a name="see-also"></a>Siehe auch

- [Projektmappenübergreifendes Zuordnen von Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md)
- [Verwenden von Code Maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md)
- [Ermitteln potenzieller Probleme mithilfe von Code Map-Analyzern](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Anpassen von Code Maps durch Bearbeiten der DGML-Dateien](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
- [Referenz zur Directed Graph Markup Language (DGML)](../modeling/directed-graph-markup-language-dgml-reference.md)
