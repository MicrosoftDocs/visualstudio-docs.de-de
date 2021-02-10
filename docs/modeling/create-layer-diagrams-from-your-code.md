---
title: Erstellen von Abhängigkeitsdiagrammen aus dem Code
description: Erfahren Sie, wie Sie in Visual Studio ein Abhängigkeits Diagramm erstellen können, um die allgemeine logische Architektur des Software Systems visuell darzustellen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 38e357ca4aa715861839f7f5ca168eafdc66f5ed
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957438"
---
# <a name="create-dependency-diagrams-from-your-code"></a>Erstellen von Abhängigkeitsdiagrammen aus dem Code

Erstellen Sie ein *Abhängigkeits Diagramm* in Visual Studio, um die allgemeine logische Architektur des Software Systems visuell darzustellen. Überprüfen Sie den Code mit einem Abhängigkeits Diagramm, um sicherzustellen, dass der Code mit dem Entwurf konsistent bleibt. Sie können Abhängigkeits Diagramme für Visual c#-und Visual Basic-Projekte erstellen. Welche Visual Studio-Editionen dieses Feature unterstützen, erfahren Sie unter [Edition-Unterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#edition-support-for-architecture-and-modeling-tools).

![Erstellen eines Abhängigkeits Diagramms](../modeling/media/layerdiagramvisualizecode.png)

Mit einem Abhängigkeits Diagramm können Sie Visual Studio-Projektmappenelemente in logischen, abstrakten Gruppen mit dem Namen *Ebenen* organisieren. Sie können die Ebenen zum Beschreiben der Hauptaufgaben, die von diesen Artefakten ausgeführt werden, oder zum Beschreiben der Hauptkomponenten des Systems verwenden. Jede Ebene kann andere Ebenen enthalten, die ausführlichere Aufgaben beschreiben. Sie können auch die vorgesehenen oder vorhandenen *Abhängigkeiten* zwischen Ebenen angeben. Diese als Pfeile dargestellten Abhängigkeiten geben an, welche Ebenen die Funktionen verwenden können bzw. welche Ebenen die Funktionen derzeit verwenden, die durch andere Ebenen dargestellt werden. Geben Sie die beabsichtigten Abhängigkeiten im Diagramm an, um die Architektursteuerung für den Code beizubehalten, und überprüfen Sie anschließend den Code anhand des Diagramms.

[Video: Überprüfen der Architekturabhängigkeiten in Echtzeit](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)

## <a name="create-a-dependency-diagram"></a><a name="CreateDiagram"></a> Erstellen eines Abhängigkeits Diagramms

Bevor Sie ein Abhängigkeits Diagramm erstellen, stellen Sie sicher, dass die Projekt Mappe über ein Modellierungsprojekt verfügt.

> [!IMPORTANT]
> Fügen Sie ein vorhandenes Abhängigkeits Diagramm aus einem Modellierungsprojekt nicht in ein anderes Modellierungsprojekt oder an eine andere Stelle in der Projekt Mappe ein, ziehen oder kopieren Sie es nicht. Dadurch werden die Verweise des ursprünglichen Diagramms beibehalten, auch wenn Sie das Diagramm ändern. Dies verhindert auch das ordnungsgemäße Funktionieren der Ebenenvalidierung und verursacht möglicherweise andere Probleme, z. B. fehlende Elemente oder andere Fehler beim Versuch, das Diagramm zu öffnen.
>
> Fügen Sie dem Modellierungsprojekt stattdessen ein neues Abhängigkeits Diagramm hinzu. Kopieren Sie die Elemente aus dem Quelldiagramm in das neue Diagramm. Speichern Sie sowohl das Modellierungsprojekt als auch das neue Abhängigkeits Diagramm.

### <a name="add-a-new-dependency-diagram-to-a-modeling-project"></a>Hinzufügen eines neuen Abhängigkeits Diagramms zu einem Modellierungsprojekt

> [!NOTE]
> Abhängigkeits Diagramme für .net Core-Projekte werden ab Visual Studio 2019 Version 16,2 unterstützt.

1. Wählen Sie im Menü **Architektur** die Option **Neues Abhängigkeits Diagramm** aus.

2. Wählen Sie unter **Vorlagen** die Option **Abhängigkeits Diagramm** aus.

3. Benennen Sie das Diagramm.

4. Navigieren Sie unter **zu Modellierungsprojekt hinzufügen** zu einem vorhandenen Modellierungsprojekt in der Projekt Mappe, und wählen Sie es aus.

     - oder -

     Wählen Sie **Neues Modellierungsprojekt erstellen** aus, um der Projekt Mappe ein neues Modellierungsprojekt hinzuzufügen.

    > [!NOTE]
    > Das Abhängigkeits Diagramm muss in einem Modellierungsprojekt vorhanden sein. Sie können es allerdings mit Elementen an einer beliebigen Stelle in der Projektmappe verknüpfen.

5. Stellen Sie sicher, dass Sie sowohl das Modellierungsprojekt als auch das Abhängigkeits Diagramm speichern.

## <a name="drag-and-drop-or-copy-and-paste-from-a-code-map"></a>Drag & Drop (kopieren und Einfügen) aus einer Code Map

1. Generieren Sie eine Code Map für die Projekt Mappe über das Menü **Architektur** .

2. Sie können einen Code Zuordnungs Filter anwenden, um Projektmappenordner und "testassets" zu entfernen, wenn Sie nur Abhängigkeiten im Produkt Code erzwingen möchten.

3. Entfernen Sie auf der generierten Code Map den Knoten "extern", oder erweitern Sie ihn, um externe Assemblys anzuzeigen, je nachdem, ob Sie Namespace Abhängigkeiten erzwingen möchten, und löschen Sie nicht erforderliche Assemblys aus der Code map.

4. Erstellen eines neuen Abhängigkeits Diagramms für die Lösung mit dem Menü " **Architektur** "

5. Wählen Sie alle Knoten in der Code Map aus (verwenden Sie _STRG_  +  _A_, oder verwenden Sie die Option "Gummi Band", indem Sie die _UMSCHALT_ Taste drücken, bevor Sie auf klicken, ziehen und freigeben klicken.

6. Ziehen Sie die ausgewählten Elemente per Drag & Drop oder durch Kopieren und Einfügen in das neue Abhängigkeits Validierungs Diagramm.

7. Dies zeigt die aktuelle App-Architektur. Entscheiden Sie, welche Architektur Sie möchten, und ändern Sie das Abhängigkeits Diagramm entsprechend.

![Abhängigkeits Diagramm, das aus einer Code map generiert wurde](media/dependency-validation-01.png)

## <a name="create-layers-from-artifacts"></a><a name="CreateLayers"></a> Erstellen von Ebenen aus Artefakten
 Ebenen können aus Visual Studio-Projektmappenelementen erstellt werden, z. B. Projekte, Codedateien, Namespaces, Klassen und Methoden. Dabei werden Verknüpfungen zwischen den Ebenen und den Elementen automatisch erstellt und im Ebenenvalidierungsprozess berücksichtigt.

 Sie können Ebenen auch mit den Elementen verknüpfen, die die Validierung nicht unterstützen, wie Word-Dokumente oder PowerPoint-Präsentationen, sodass Sie eine Ebene Spezifikationen oder Plänen zuordnen können. Außerdem können Sie Ebenen mit Dateien in Projekten verknüpfen, die für mehrere Apps freigegeben sind. Im Validierungsprozess werden diese Ebenen, die mit generischen Namen wie "Layer 1" und "Layer 2" angezeigt werden, jedoch nicht berücksichtigt.

 Um festzustellen, ob ein verknüpftes Element die Validierung unterstützt, öffnen Sie den **ebenenexplorer** , und überprüfen Sie die Eigenschaft **unterstützt Validation** Siehe [Verwalten von Links zu Artefakten](#Managing).

|**An**|Führen Sie **diese Schritte** aus.|
|-|-|
|Erstellen einer Ebene für ein einzelnes Artefakt|<ol><li>Ziehen Sie das Element aus den folgenden Quellen in das Abhängigkeits Diagramm:<br /><br /> <ul><li>**Projektmappen-Explorer**<br /><br />         Beispiele: Dateien oder Projekte.</li><li>Codezuordnungen<br /><br />         Siehe Zuordnen von [Abhängigkeiten für Ihre](../modeling/map-dependencies-across-your-solutions.md) Projektmappen und [Verwenden von Code Maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md).</li><li>**Klassenansicht** oder **Objektkatalog**</li></ul><br />     Im Diagramm wird eine Ebene angezeigt und mit dem Artefakt verknüpft.</li><li>Ändern Sie den Namen der Ebene, um die Aufgaben des zugeordneten Codes oder der Artefakte widerzuspiegeln.</li></ol> **Wichtig:**  Beim Ziehen von Binärdateien in das Abhängigkeits Diagramm werden Ihre Verweise nicht automatisch zum Modellierungsprojekt hinzugefügt. Sie müssen die Binärdateien manuell hinzufügen, die Sie für das Modellierungsprojekt überprüfen möchten. **So fügen Sie dem Modellierungsprojekt Binärdateien hinzu** <ol><li>Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für das Modellierungsprojekt, und wählen Sie dann **Vorhandenes Element hinzufügen** aus.</li><li>Navigieren Sie im Dialogfeld **Vorhandenes Element hinzufügen** zu den Binärdateien, wählen Sie Sie aus, und klicken Sie dann auf **OK**.     Die Binärdateien werden im Modellierungsprojekt angezeigt.</li><li>Wählen Sie in **Projektmappen-Explorer** eine Binärdatei aus, die Sie hinzugefügt haben, und drücken Sie dann **F4** , um das **Eigenschaften** Fenster zu öffnen.</li><li>Legen Sie die Eigenschaft **Buildaktion** für jede Binärdatei auf **Validate** fest.</li></ol>|
|Erstellen einer einzelnen Ebene für alle ausgewählten Artefakte|Ziehen Sie alle Artefakte gleichzeitig in das Abhängigkeits Diagramm.<br /><br /> Im Diagramm wird eine Ebene angezeigt und mit allen Artefakten verknüpft.|
|Erstellen einer Ebene für jedes ausgewählte Artefakt|Halten Sie die **UMSCHALT** Taste gedrückt, während Sie alle Artefakte gleichzeitig in das Abhängigkeits Diagramm ziehen. **Hinweis:**  Wenn Sie mithilfe der **UMSCHALT** Taste einen Bereich von Elementen auswählen, geben Sie den Schlüssel nach dem Auswählen der Artefakte frei. Halten Sie sie anschließend erneut gedrückt, wenn Sie die Artefakte in das Diagramm ziehen. <br /><br /> Im Diagramm wird für jedes Artefakt eine Ebene angezeigt und mit den einzelnen Artefakten verknüpft.|
|Hinzufügen eines Artefakts zu einer Ebene|Ziehen Sie das Artefakt auf die Ebene.|
|Erstellen einer neuen, nicht verknüpften Ebene|Erweitern Sie in der **Toolbox** den Abschnitt **Abhängigkeits Diagramm** , und ziehen Sie dann eine **Ebene** in das Abhängigkeits Diagramm.<br /><br /> Doppelklicken Sie zum Erstellen mehrerer Ebenen auf das Tool. Wenn Sie fertig sind, wählen Sie das **Zeiger** Werkzeug aus, oder drücken Sie die **ESC** -Taste.<br /><br /> - oder -<br /><br /> Öffnen Sie das Kontextmenü für das Abhängigkeits Diagramm, und wählen Sie **Hinzufügen** und dann **Ebene** aus.|
|Erstellen geschachtelter Ebenen|Ziehen Sie eine vorhandene Ebene auf eine andere Ebene.<br /><br /> - oder -<br /><br /> Öffnen Sie das Kontextmenü für eine Ebene, und wählen Sie **Hinzufügen** und dann **Ebene** aus.|
|Erstellen einer neuen Ebene, die mehrere vorhandene Ebenen enthält|Wählen Sie die Ebenen aus, öffnen Sie das Kontextmenü für Ihre Auswahl, und wählen Sie dann **Gruppe** aus.|
|Ändern der Farbe einer Ebene|Legen Sie die **Color** -Eigenschaft auf die gewünschte Farbe fest.|
|Angeben, dass einer Ebene zugeordnete Artefakte nicht zu den angegebenen Namespaces gehören dürfen|Geben Sie die Namespaces in die Eigenschaft für unzulässige **Namespaces** der Ebene ein. Verwenden Sie zum Trennen der Namespaces ein Semikolon (**;**).|
|Angeben, dass einer Ebene zugeordnete Artefakte nicht von den angegebenen Namespaces abhängen dürfen|Geben Sie die Namespaces in die Eigenschaft für unzulässige **Namespace Abhängigkeiten** der Ebene ein. Verwenden Sie zum Trennen der Namespaces ein Semikolon (**;**).|
|Angeben, dass einer Ebene zugeordnete Artefakte zu einem der angegebenen Namespaces gehören müssen|Geben Sie den Namespace in die Eigenschaft **erforderliche Namespaces** der Ebene ein. Verwenden Sie zum Trennen der Namespaces ein Semikolon (**;**).|

 Die Zahl auf einer Ebene gibt die Anzahl von Artefakten an, die mit der Ebene verknüpft sind. Beachten Sie jedoch Folgendes, wenn Sie diese Zahl lesen:

- Wenn eine Ebene mit einem Artefakt verknüpft ist, das andere Artefakte enthält, die Ebene jedoch nicht direkt mit den anderen Artefakten verknüpft ist, umfasst die Zahl nur das verknüpfte Artefakt. Die anderen Artefakte werden jedoch während der Ebenenvalidierung für die Analyse berücksichtigt.

     Ist z. B. eine Ebene mit einem einzelnen Namespace verknüpft, ist die Anzahl der verknüpften Artefakte 1, auch wenn der Namespace Klassen enthält. Wenn die Ebene auch mit den einzelnen Klassen im Namespace verknüpft ist, umfasst die Zahl die verknüpften Klassen.

- Wenn eine Ebene andere Ebenen enthält, die mit Artefakten verknüpft sind, ist die Containerebene ebenfalls mit diesen Artefakten verknüpft, obwohl in der Zahl auf der Containerebene diese Artefakte nicht berücksichtigt sind.

## <a name="manage-links-between-layers-and-artifacts"></a><a name="Managing"></a> Verwalten von Links zwischen Ebenen und Artefakten

1. Öffnen Sie im Abhängigkeits Diagramm das Kontextmenü für die Ebene, und wählen Sie dann **Verknüpfungen anzeigen** aus.

     **Ebenenexplorer** zeigt die artefaktlinks für die ausgewählte Ebene an.

2. Verwenden Sie zum Verwalten dieser Links die folgenden Aufgaben:

|**An**|**Im Ebenen-Explorer**|
|-|-|
|Löschen des Links zwischen der Ebene und einem Artefakt|Öffnen Sie das Kontextmenü für den artefaktlink, und wählen Sie dann **Löschen** aus.|
|Verschieben des Links von einer Ebene auf eine andere Ebene|Ziehen Sie den Artefaktlink auf eine Ebene im Diagramm.<br /><br /> - oder -<br /><br /> 1. Öffnen Sie das Kontextmenü für den artefaktlink, und wählen Sie dann **Ausschneiden** aus.<br />2. Öffnen Sie im Abhängigkeits Diagramm das Kontextmenü für die Ebene, und wählen Sie dann **Einfügen** aus.|
|Kopieren des Links von einer Ebene auf eine andere Ebene|1. Öffnen Sie das Kontextmenü für den artefaktlink, und wählen Sie dann **Kopieren** aus.<br />2. Öffnen Sie im Abhängigkeits Diagramm das Kontextmenü für die Ebene, und wählen Sie dann **Einfügen** aus.|
|Erstellen einer neuen Ebene aus einem vorhandenen Artefaktlink|Ziehen Sie den Artefaktlink in einen leeren Bereich des Diagramms.|
|Überprüfen Sie, ob ein verknüpftes Element die Validierung für das Abhängigkeits Diagramm unterstützt|Sehen Sie sich die Spalte **unterstützt die Validierung** für den artefaktlink an.|

## <a name="reverse-engineer-existing-dependencies"></a><a name="Discovering"></a> Vorhandene Abhängigkeiten umkehren
 Eine Abhängigkeit ist überall dort vorhanden, wo ein Artefakt, das einer Ebene zugeordnet ist, einen Verweis auf ein Artefakt enthält, das einer anderen Ebene zugeordnet ist. Beispiel: Eine Klasse in einer Ebene deklariert eine Variable, deren Klasse sich auf einer anderen Ebene befindet. Bei vorhandenen Abhängigkeiten von Artefakten, die mit Ebenen des Diagramms verknüpft sind, ist eine Rückentwicklung möglich.

> [!NOTE]
> Bei bestimmten Arten von Artefakten ist kein Reverse Engineering der Abhängigkeiten möglich. So kann beispielsweise bei einer Ebene, die mit einer Textdatei verknüpft ist, keinerlei Rückentwicklung der Abhängigkeiten vorgenommen werden. Öffnen Sie das Kontextmenü für eine oder mehrere Ebenen, und klicken Sie dann **auf Links anzeigen**, um zu sehen, welche Artefakte Abhängigkeiten aufweisen, die Sie rückgängig machen können. Überprüfen Sie im **Ebenen-Explorer** die Spalte **unterstützt die Validierung** . Abhängigkeiten werden nicht für Artefakte, für die diese Spalte **false** anzeigt, in umgekehrter Reihenfolge entwickelt.

- Wählen Sie eine oder mehrere Ebenen aus, öffnen Sie das Kontextmenü für eine ausgewählte Ebene, und wählen Sie dann **Abhängigkeiten generieren** aus.

  In der Regel sind einige unerwünschte Abhängigkeiten vorhanden. Diese Abhängigkeiten können bearbeitet werden, um sie mit dem geplanten Entwurf in Einklang zu bringen.

## <a name="edit-layers-and-dependencies-to-show-the-intended-design"></a><a name="EditDependencies"></a> Bearbeiten von Ebenen und Abhängigkeiten, um den beabsichtigten Entwurf anzuzeigen
 Bearbeiten Sie das Abhängigkeits Diagramm, um die Änderungen zu beschreiben, die Sie an Ihrem System oder der vorgesehenen Architektur vornehmen möchten:

|**An**|**Auszuführende Schritte**|
|-|-|
|Ändern oder Einschränken der Richtung einer Abhängigkeit|Legen Sie die Eigenschaft **Richtung** fest.|
|Erstellen von neuen Abhängigkeiten|Verwenden Sie die **Abhängigkeits** -und **bidirektionalen Abhängigkeits** Tools<br /><br /> Doppelklicken Sie zum Zeichnen mehrerer Abhängigkeiten auf das Tool. Wenn Sie fertig sind, wählen Sie das **Zeiger** Werkzeug aus, oder drücken Sie die **ESC** -Taste.|
|Angeben, dass einer Ebene zugeordnete Artefakte nicht von den angegebenen Namespaces abhängen dürfen|Geben Sie die Namespaces in die Eigenschaft für unzulässige **Namespace Abhängigkeiten** der Ebene ein. Verwenden Sie zum Trennen der Namespaces ein Semikolon (**;**).|
|Angeben, dass einer Ebene zugeordnete Artefakte nicht zu den angegebenen Namespaces gehören dürfen|Geben Sie die Namespaces in die Eigenschaft für unzulässige **Namespaces** der Ebene ein. Verwenden Sie zum Trennen der Namespaces ein Semikolon (**;**).|
|Angeben, dass einer Ebene zugeordnete Artefakte zu einem der angegebenen Namespaces gehören müssen|Geben Sie den Namespace in die Eigenschaft **erforderliche Namespaces** der Ebene ein. Verwenden Sie zum Trennen der Namespaces ein Semikolon (**;**).|

## <a name="change-how-elements-appear-on-the-diagram"></a><a name="EditLayout"></a> Ändern, wie Elemente im Diagramm angezeigt werden
 Sie können die Größe, Form, Farbe und Position von Ebenen oder die Farbe von Abhängigkeiten ändern, indem Sie ihre Eigenschaften bearbeiten.

## <a name="discover-patterns-and-dependencies-on-a-code-map"></a><a name="Codemaps"></a> Erkennen von Mustern und Abhängigkeiten auf einem Code Map
 Beim Erstellen von Abhängigkeits Diagrammen können Sie auch **Code Maps** erstellen. Diese Diagramme können Ihnen helfen, Muster und Abhängigkeiten zu ermitteln, während Sie den Code untersuchen. Mithilfe von Projektmappen-Explorer, Klassenansicht oder Objektkatalog können Assemblys, Namespaces und Klassen untersucht werden, die häufig den vorhandenen Ebenen entsprechen. Weitere Informationen zu Codezuordnungen finden Sie unter den folgenden Themen:

- [Projektmappenübergreifendes Zuordnen von Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md)

- [Verwenden von Code Maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md)

- [Ermitteln potenzieller Probleme mithilfe von Code Map-Analyzern](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="see-also"></a>Weitere Informationen

- [Editions Unterstützung für Architektur-und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#edition-support-for-architecture-and-modeling-tools)
- [Video: Überprüfen der Architekturabhängigkeiten in Echtzeit](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)
- [Abhängigkeitsdiagramme: Referenz](../modeling/layer-diagrams-reference.md)
- [Abhängigkeitsdiagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md)
- [Überprüfen von Code mit Abhängigkeitsdiagrammen](../modeling/validate-code-with-layer-diagrams.md)
- [Visualisieren von Code](../modeling/visualize-code.md)
