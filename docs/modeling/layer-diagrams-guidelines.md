---
title: 'Abhängigkeitsdiagramme: Richtlinien'
description: Erfahren Sie, wie Sie die Architektur Ihrer APP auf hoher Ebene beschreiben, indem Sie Abhängigkeits Diagramme in Visual Studio erstellen.
ms.custom: SEO-VS-2020
ms.date: 09/28/2018
ms.topic: conceptual
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5bfef2f9397fbe8dfeceaa8789cf8d118315b26d
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363964"
---
# <a name="dependency-diagrams-guidelines"></a>Abhängigkeits Diagramme: Richtlinien

Beschreiben Sie die Architektur Ihrer APP auf hoher Ebene, indem Sie *Abhängigkeits Diagramme* in Visual Studio erstellen. Stellen Sie sicher, dass Ihr Code mit diesem Entwurf konsistent bleibt, indem Sie den Code mit einem Abhängigkeits Diagramm validieren. Sie können auch eine Ebenenvalidierung im Buildprozess einschließen. Siehe [Channel 9-Video: Entwerfen und validieren ihrer Architektur mithilfe von Abhängigkeits Diagrammen](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture).

Welche Visual Studio-Editionen dieses Feature unterstützen, erfahren Sie unter [Edition-Unterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> Abhängigkeits Diagramme für .net Core-Projekte werden ab Visual Studio 2019 Version 16,2 unterstützt.

## <a name="what-is-a-dependency-diagram"></a>Was ist ein Abhängigkeits Diagramm?

Wie ein herkömmliches Architektur Diagramm identifiziert ein Abhängigkeits Diagramm die Hauptkomponenten oder Funktionseinheiten des Entwurfs und deren Abhängigkeiten. Jeder Knoten im Diagramm, der als *Schicht* bezeichnet wird, stellt eine logische Gruppe von Namespaces, Projekten oder anderen Artefakten dar. Sie können die Abhängigkeiten zeichnen, die im Entwurf vorhanden sein sollen. Anders als bei einem herkömmlichen Architekturdiagramm können Sie überprüfen, ob die tatsächlichen Abhängigkeiten im Quellcode den gewünschten Abhängigkeiten entsprechen, die Sie angegeben haben. Indem Sie die Validierung zu einem Bestandteil eines regulären Buildvorgangs in [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] machen, stellen Sie sicher, dass der Programmcode auch in zukünftigen Änderungen mit der Architektur des Systems übereinstimmt. Siehe [Abhängigkeits Diagramme: Referenz](../modeling/layer-diagrams-reference.md).

## <a name="how-to-design-or-update-your-app-with-dependency-diagrams"></a>Entwerfen oder Aktualisieren Ihrer APP mit Abhängigkeits Diagrammen

Die folgenden Schritte bieten einen Überblick über die Verwendung von Abhängigkeits Diagrammen im Entwicklungsprozess. In späteren Abschnitten dieses Themas werden die einzelnen Schritte ausführlicher beschrieben. Wenn Sie einen neuen Entwurf entwickeln, lassen Sie die Schritte aus, die sich auf vorhandenen Code beziehen.

> [!NOTE]
> Die Schritte entsprechen ungefähr der tatsächlichen Reihenfolge. Wahrscheinlich werden Sie die Aufgaben überlappend ausführen, die Reihenfolge Ihrer eigenen Situation anpassen und am Anfang jeder Iteration im Projekt nochmals auf die Beschreibung der Schritte zurückkommen.

1. [Erstellen Sie ein Abhängigkeits Diagramm](#Create) für die gesamte Anwendung oder für eine Ebene darin.

2. [Definieren Sie Ebenen, die primäre funktionale Bereiche oder Komponenten](#CreateLayers) der Anwendung darstellen. Benennen Sie diese Ebenen nach ihrer Funktion, z. B. "Präsentation" oder "Dienste". Wenn Sie über eine Visual Studio-Projekt Mappe verfügen, können Sie jeder Ebene eine Auflistung von *Artefakten* zuordnen, wie z. b. Projekte, Namespaces, Dateien usw.

3. Erkennen [Sie die vorhandenen Abhängigkeiten](#Generate) zwischen Ebenen.

4. [Bearbeiten Sie die Ebenen und Abhängigkeiten](#EditArchitecture) , um den aktualisierten Entwurf anzuzeigen, den der Code reflektieren soll.

5. [Entwerfen Sie neue Bereiche der Anwendung](#NewAreas) , indem Sie Ebenen zur Darstellung der wichtigsten Architektur Blöcke oder Komponenten erstellen und Abhängigkeiten definieren, um anzuzeigen, wie die einzelnen Ebenen die anderen Ebenen verwenden.

6. [Bearbeiten Sie das Layout und die Darstellung des Diagramms](#EditLayout) , um Sie bei der Erörterung mit Kollegen zu unterstützen.

7. Überprüfen Sie [den Code anhand des Abhängigkeits Diagramms](#Validate) , um die Konflikte zwischen dem Code und der von Ihnen benötigten Architektur hervorzuheben.

8. [Aktualisieren Sie den Code, damit er der neuen Architektur entspricht](#UpdateCode). Führen Sie die Entwicklung und Umgestaltung von Code in Iterationen durch, bis bei der Validierung keine Konflikte auftreten.

9. [Schließen Sie ebenenvalidierung in den Buildprozess](#BuildValidation) ein, um sicherzustellen, dass der Code weiterhin ihrem Entwurf entspricht.

## <a name="create-a-dependency-diagram"></a><a name="Create"></a> Erstellen eines Abhängigkeits Diagramms

Ein Abhängigkeits Diagramm muss in einem Modellierungsprojekt erstellt werden. Sie können einem vorhandenen Modellierungsprojekt ein neues Abhängigkeits Diagramm hinzufügen, ein neues Modellierungsprojekt für das Abhängigkeits Diagramm erstellen oder ein vorhandenes Abhängigkeits Diagramm innerhalb desselben Modellierungs Projekts kopieren.

> [!IMPORTANT]
> Fügen Sie ein vorhandenes Abhängigkeits Diagramm aus einem Modellierungsprojekt nicht zu einem anderen Modellierungsprojekt oder einem anderen Speicherort in der Projekt Mappe hinzu, ziehen oder kopieren Sie es nicht. Ein Abhängigkeits Diagramm, das auf diese Weise kopiert wird, hat die gleichen Verweise wie das ursprüngliche Diagramm, auch wenn Sie das Diagramm ändern. Dies verhindert das ordnungsgemäße Funktionieren der Ebenenvalidierung und verursacht möglicherweise andere Probleme, z. B. fehlende Elemente oder andere Fehler beim Versuch, das Diagramm zu öffnen.

Siehe [Erstellen von Abhängigkeits Diagrammen aus Ihrem Code](../modeling/create-layer-diagrams-from-your-code.md).

## <a name="define-layers-to-represent-functional-areas-or-components"></a><a name="CreateLayers"></a> Definieren von Ebenen zur Darstellung funktionaler Bereiche oder Komponenten

Ebenen stellen logische Gruppen von *Artefakten* dar, z. b. Projekte, Code Dateien, Namespaces, Klassen und Methoden. Sie können Ebenen aus Artefakten aus Visual c#-und Visual Basic-Projekten erstellen, oder Sie können Spezifikationen oder Pläne an eine Ebene anfügen, indem Sie Dokumente verknüpfen, wie z. b. Word-Dateien oder PowerPoint-Präsentationen. Jede Ebene wird im Diagramm als Rechteck angezeigt und gibt Aufschluss über die Anzahl der mit ihr verknüpften Artefakte. Eine Ebene kann geschachtelte Ebenen enthalten, um spezielle Aufgaben zu beschreiben.

Benennen Sie als allgemeine Richtlinie Ebenen nach ihrer Funktion, z. B. "Präsentation" oder "Dienste". Fügen Sie Artefakte in der gleichen Ebene ein, wenn zwischen ihnen eine enge Abhängigkeit besteht. Wenn die Artefakte getrennt voneinander aktualisiert oder in separaten Anwendungen verwendet werden können, sollten sie auf unterschiedlichen Ebenen eingefügt werden. Weitere Informationen zu ebenenmustern finden Sie auf der Seite Patterns & Practices unter [http://go.microsoft.com/fwlink/?LinkId=145794](https://archive.codeplex.com/?p=apparch) .

> [!TIP]
> Es gibt bestimmte Typen von Artefakten, die Sie mit Ebenen verknüpfen können, die die Validierung für das Abhängigkeits Diagramm jedoch nicht unterstützen. Um festzustellen, ob das Element die Validierung unterstützt, öffnen Sie den **ebenenexplorer** , um die **unterstützte Validierungs** Eigenschaft des artefaktlinks zu Weitere Informationen finden [Sie unter ermitteln vorhandener Abhängigkeiten zwischen Ebenen](#Generate).

Bei der Aktualisierung einer nicht vertrauten Anwendung können Sie auch Codezuordnungen erstellen. Diese Diagramme können Ihnen helfen, Muster und Abhängigkeiten zu ermitteln, während Sie den Code untersuchen. Mithilfe des Projektmappen-Explorers können Namespaces und Klassen untersucht werden, die häufig den vorhandenen Ebenen entsprechen. Weisen Sie diese Code Artefakte den Ebenen zu, indem Sie Sie aus Projektmappen-Explorer in Abhängigkeits Diagramme ziehen. Anschließend können Sie Abhängigkeits Diagramme verwenden, um den Code zu aktualisieren und mit dem Entwurf konsistent zu halten.

Siehe:

- [Erstellen von Abhängigkeitsdiagrammen aus dem Code](../modeling/create-layer-diagrams-from-your-code.md)

- [Verwenden von Code Maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md)

- [Projektmappenübergreifendes Zuordnen von Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md)

## <a name="discover-existing-dependencies-between-layers"></a><a name="Generate"></a> Vorhandene Abhängigkeiten zwischen Ebenen ermitteln

Eine Abhängigkeit ist überall dort vorhanden, wo ein Artefakt, das einer Ebene zugeordnet ist, einen Verweis auf ein Artefakt enthält, das einer anderen Ebene zugeordnet ist. Beispiel: Eine Klasse in einer Ebene deklariert eine Variable, deren Klasse sich auf einer anderen Ebene befindet. Vorhandene Abhängigkeiten können mittels Reverse Engineering (Zurückentwicklung) ermittelt werden.

> [!NOTE]
> Bei bestimmten Arten von Artefakten ist kein Reverse Engineering der Abhängigkeiten möglich. So kann beispielsweise bei einer Ebene, die mit einer Textdatei verknüpft ist, keinerlei Rückentwicklung der Abhängigkeiten vorgenommen werden. Klicken Sie mit der rechten Maustaste auf eine oder mehrere Ebenen, und klicken Sie dann auf **Links anzeigen**, um zu sehen, welche Artefakte Abhängigkeiten aufweisen, die Sie rückgängig machen können. Überprüfen Sie im **Ebenen-Explorer** die Spalte **unterstützt die Validierung** . Abhängigkeiten werden nicht für Artefakte, für die diese Spalte **false** anzeigt, in umgekehrter Reihenfolge entwickelt.

### <a name="to-reverse-engineer-existing-dependencies-between-layers"></a>So entwickeln Sie vorhandene Abhängigkeiten zwischen Ebenen zurück

Wählen Sie eine Ebene oder mehrere Ebenen aus, klicken Sie mit der rechten Maustaste auf eine ausgewählte Ebene, und klicken Sie dann auf **Abhängigkeiten generieren**.

In der Regel sind einige unerwünschte Abhängigkeiten vorhanden. Diese Abhängigkeiten können bearbeitet werden, um sie mit dem geplanten Entwurf in Einklang zu bringen.

## <a name="edit-layers-and-dependencies-to-show-the-intended-design"></a><a name="EditArchitecture"></a> Bearbeiten von Ebenen und Abhängigkeiten, um den beabsichtigten Entwurf anzuzeigen

Um die Änderungen zu beschreiben, die Sie an Ihrem System oder der vorgesehenen Architektur vornehmen möchten, verwenden Sie die folgenden Schritte, um das Abhängigkeits Diagramm zu bearbeiten. Sie können vor dem Erweitern des Codes ggf. auch einige Refactoringänderungen vornehmen, um die Codestruktur zu verbessern. Siehe [verbessern der Struktur des Codes](#Improving).

|**An**|**Auszuführende Schritte**|
|-|-|
|Löschen einer unerwünschten Abhängigkeit|Klicken Sie auf die Abhängigkeit, und **drücken Sie** dann ENTF.|
|Ändern oder Einschränken der Richtung einer Abhängigkeit|Legen Sie die Eigenschaft **Richtung** fest.|
|Erstellen von neuen Abhängigkeiten|Verwenden Sie die **Abhängigkeits** -und **bidirektionalen Abhängigkeits** Tools<br /><br /> Doppelklicken Sie zum Zeichnen mehrerer Abhängigkeiten auf das Tool. Wenn Sie fertig sind, klicken Sie auf das Tool **Zeiger** , oder drücken Sie die **ESC** -Taste.|
|Angeben, dass einer Ebene zugeordnete Artefakte nicht von den angegebenen Namespaces abhängen dürfen|Geben Sie die Namespaces in die Eigenschaft für unzulässige **Namespace Abhängigkeiten** der Ebene ein. Verwenden Sie zum Trennen der Namespaces ein Semikolon (**;**).|
|Angeben, dass einer Ebene zugeordnete Artefakte nicht zu den angegebenen Namespaces gehören dürfen|Geben Sie die Namespaces in die Eigenschaft für unzulässige **Namespaces** der Ebene ein. Verwenden Sie zum Trennen der Namespaces ein Semikolon (**;**).|
|Angeben, dass einer Ebene zugeordnete Artefakte zu einem der angegebenen Namespaces gehören müssen|Geben Sie den Namespace in die Eigenschaft **erforderliche Namespaces** der Ebene ein. Verwenden Sie zum Trennen der Namespaces ein Semikolon (**;**).|

### <a name="improving-the-structure-of-the-code"></a><a name="Improving"></a> Verbessern der Struktur des Codes

Umgestaltungsänderungen sind Verbesserungen, die das Verhalten der Anwendung nicht ändern, jedoch zukünftige Änderungen und Erweiterungen des Codes erleichtern. Gut strukturierter Code verfügt über einen Entwurf, der leicht in ein Abhängigkeits Diagramm abstrahiert werden kann.

Wenn Sie z. B. eine Ebene für jeden Namespace im Code erstellen und die Abhängigkeiten dann zurück entwickeln, sollte die Anzahl unidirektionaler Abhängigkeiten zwischen den Ebenen minimal sein. Wenn Sie ein detailliertes Diagramm mit Klassen oder Methoden als Ebenen zeichnen, sollte das Ergebnis dieselben Merkmale aufweisen.

Wenn dies nicht der Fall ist, ist es schwieriger, den Code während der gesamten Lebensdauer zu ändern, und er ist für die Validierung mithilfe von Abhängigkeits Diagrammen weniger geeignet.

## <a name="design-new-areas-of-your-application"></a><a name="NewAreas"></a> Entwerfen neuer Bereiche Ihrer Anwendung

Wenn Sie mit der Entwicklung eines neuen Projekts oder eines neuen Bereichs in einem neuen Projekt beginnen, können Sie Ebenen und Abhängigkeiten zeichnen, um die Hauptkomponenten zu identifizieren, bevor Sie mit dem Entwickeln des Codes beginnen.

- Zeigen Sie nach Möglichkeit **identifizierbare Architekturmuster** in den Abhängigkeits Diagrammen an. Ein Abhängigkeits Diagramm, das eine Desktop Anwendung beschreibt, kann z. b. Ebenen wie Präsentation, Domänen Logik und Datenspeicher enthalten. Ein Abhängigkeits Diagramm, das eine einzelne Funktion in einer Anwendung abdeckt, kann über Ebenen wie Modell, Ansicht und Controller verfügen. Weitere Informationen zu solchen Mustern finden Sie unter [Muster & Praktiken: Anwendungsarchitektur](https://archive.codeplex.com/?p=apparch).

- **Erstellen Sie ein Code Element für jede Ebene** , z. b. einen Namespace, eine Klasse oder eine Komponente. Dies vereinfacht das Verfolgen des Codes und das Verknüpfen der Codeartefakte mit den Ebenen. Verknüpfen Sie jedes Artefakt mit der entsprechenden Ebene, sobald Sie das Artefakt erstellen.

- **Sie müssen die meisten Klassen und andere Artefakte nicht mit Ebenen verknüpfen** , da Sie in größere Artefakte, wie z. b. Namespaces, die Sie bereits mit Ebenen verknüpft haben, liegen.

- **Erstellen Sie ein neues Diagramm für ein neues Feature**. In der Regel gibt es mindestens ein Abhängigkeits Diagramm, in dem die gesamte Anwendung beschrieben wird. Wenn Sie eine neue Funktion in der Anwendung entwerfen, ändern Sie nicht die vorhandenen Diagramme, und fügen Sie ihnen keine Elemente hinzu. Erstellen Sie stattdessen ein eigenes Diagramm, das die neuen Teile des Codes wiedergibt. Das neue Diagramm kann beispielsweise Ebenen für die Präsentation, Domänenlogik und Datenbank der neuen Funktion enthalten.

     Wenn Sie die Anwendung erstellen, wird der Code sowohl anhand des allgemeinen Diagramms als auch anhand des ausführlicheren Funktionsdiagramms überprüft.

## <a name="edit-the-layout-for-presentation-and-discussion"></a><a name="EditLayout"></a> Layout für Präsentation und Diskussion bearbeiten

Bearbeiten Sie Darstellung und Layout des Diagramms, um die Suche nach Ebenen und Abhängigkeiten sowie Diskussionen mit Teammitgliedern zu vereinfachen. Führen Sie hierzu die folgenden Schritte aus:

- Ändern der Größe, Formen und Positionen von Ebenen

- Ändern der Farben von Ebenen und Abhängigkeiten

  - Wählen Sie eine oder mehrere Ebenen oder Abhängigkeiten aus, klicken Sie mit der rechten Maustaste, und klicken Sie dann auf **Eigenschaften**. Bearbeiten Sie im **Eigenschaften** Fenster die **Color** -Eigenschaft.

## <a name="validate-the-code-against-the-diagram"></a><a name="Validate"></a> Überprüfen Sie den Code anhand des Diagramms.

Wenn Sie das Diagramm bearbeitet haben, können Sie es jederzeit oder automatisch bei jedem Buildvorgang mit dem Code überprüfen.

Siehe:

- [Überprüfen von Code mit Abhängigkeitsdiagrammen](../modeling/validate-code-with-layer-diagrams.md)

- [Einschließen von Ebenenvalidierung in den Buildvorgang](#BuildValidation)

## <a name="update-the-code-to-conform-to-the-new-architecture"></a><a name="UpdateCode"></a> Aktualisieren Sie den Code, damit er der neuen Architektur entspricht.

In der Regel werden Fehler angezeigt, wenn Sie Code zum ersten Mal anhand eines aktualisierten Abhängigkeits Diagramms validieren. Diese Fehler können mehrere Ursachen haben:

- Ein Artefakt wurde der falschen Ebene zugewiesen. Verschieben Sie in diesem Fall das Artefakt.

- Von einem Artefakt (beispielsweise einer Klasse) wird eine andere Klasse auf eine Weise verwendet, die einen Konflikt mit der Architektur zur Folge hat. Gestalten Sie in diesem Fall den Code um, um die Abhängigkeit zu entfernen.

Aktualisieren Sie zum Beheben dieser Fehler den Code, bis bei der Validierung keine Fehler mehr angezeigt werden. Dies ist normalerweise ein iterativer Vorgang. Weitere Informationen zu diesen Fehlern finden Sie unter Überprüfen von [Code mit Abhängigkeits Diagrammen](../modeling/validate-code-with-layer-diagrams.md).

> [!NOTE]
> Wenn Sie den Code entwickeln oder umgestalten, verfügen Sie möglicherweise über neue Artefakte, die mit dem Abhängigkeits Diagramm verknüpft werden können. Dies ist jedoch möglicherweise nicht erforderlich, wenn Ebenen z. B. vorhandene Namespaces darstellen und diesen Namespaces mit dem neuen Code lediglich weitere Elemente hinzugefügt werden.

Während des Entwicklungsprozesses können Sie ggf. einige der Konflikte unterdrücken, die während der Validierung gemeldet werden. Beispielsweise können Sie Fehler unterdrücken, die Sie bereits behandeln oder die für das spezifische Szenario nicht relevant sind. Wenn Sie einen Fehler unterdrücken, empfiehlt es sich, ein Arbeits Element in Team Foundation zu protokollieren. Informationen zum Ausführen dieser Aufgabe finden Sie unter Überprüfen [von Code mit Abhängigkeits Diagrammen](../modeling/validate-code-with-layer-diagrams.md).

## <a name="include-layer-validation-in-the-build-process"></a><a name="BuildValidation"></a> Ebenenvalidierung in den Buildprozess einschließen

Um sicherzustellen, dass zukünftige Änderungen im Code den Abhängigkeits Diagrammen entsprechen, schließen Sie ebenenvalidierung in den Standardbuildprozess ihrer Projekt Mappe ein. Wenn andere Teammitglieder die Projekt Mappe erstellen, werden alle Unterschiede zwischen den Abhängigkeiten im Code und dem Abhängigkeits Diagramm als Buildfehler gemeldet. Weitere Informationen zum Einschließen der ebenenvalidierung in den Buildprozess finden Sie unter Überprüfen von [Code mit Abhängigkeits Diagrammen](../modeling/validate-code-with-layer-diagrams.md).

## <a name="see-also"></a>Siehe auch

- [Abhängigkeitsdiagramme: Referenz](../modeling/layer-diagrams-reference.md)
- [Erstellen von Abhängigkeitsdiagrammen aus dem Code](../modeling/create-layer-diagrams-from-your-code.md)
