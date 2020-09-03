---
title: Erstellen von UML-Modellierungs Projekten und-Diagrammen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.addnewdiagramdialog
- vs.teamarch.createnewmodelingprojectdialog
helpviewer_keywords:
- projects [Visual Studio ALM], modeling
- diagrams - modeling, modeling
- modeling diagrams
- projects, UML
- UML, deleting diagrams
- UML
- UML diagrams, adding
- UML, projects
- Visual Studio ALM, modeling projects
- modeling projects
- UML diagrams
- projects, modeling
ms.assetid: c178b04b-4fd2-4bed-97e3-d793dae8649c
caps.latest.revision: 50
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 52c55b2cfdf000d91a83071b53e8e9450187b720
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75852023"
---
# <a name="create-uml-modeling-projects-and-diagrams"></a>Erstellen von UML-Modellierungsprojekten und -diagrammen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML-Modelle helfen Ihnen, Softwaresysteme zu verstehen, zu besprechen und zu entwerfen. Visual Studio stellt Vorlagen für fünf der am häufigsten verwendeten UML-Diagramme bereit: Aktivität, Klasse, Komponente, Sequenz und Anwendungsfall. Darüber hinaus können Sie Ebenendiagramme erstellen, mit deren Hilfe Sie die Struktur des Systems definieren.

 UML-Modellierungsdiagramme und Ebenendiagramme können nur in einem Modellierungsprojekt vorhanden sein. Jedes Modellierungsprojekt enthält ein freigegebenes UML-Modell und mehrere UML-Diagramme. Jedes Diagramm ist eine Teilansicht des Modells. Das UML-Modell enthält alle Elemente der UML-Diagramme und kann mit dem UML-Modell-Explorer angezeigt werden. Informationen zu Modellen und deren Beziehung zu Diagrammen finden Sie unter [Bearbeiten von UML-Modellen und-Diagrammen](../modeling/edit-uml-models-and-diagrams.md). Informationen zum Modellieren von Projekten unter Versionskontrolle finden Sie [unter Verwalten von Modellen und Diagrammen unter Versionskontrolle](../modeling/manage-models-and-diagrams-under-version-control.md) und [strukturieren der Modellierungs Lösung](../modeling/structure-your-modeling-solution.md) .

> [!NOTE]
> Es gibt eine andere Art von Diagramm, das .NET Klassendiagramm, das verwendet wird, um Programmcode visuell darzustellen. Weitere Informationen finden Sie unter [Entwerfen und Anzeigen von Klassen und Typen](https://msdn.microsoft.com/library/ab7aty24.aspx).

## <a name="create-a-diagram-in-a-modeling-project"></a><a name="CreatingModelingDiagrams"></a> Erstellen eines Diagramms in einem Modellierungsprojekt
 Welche Versionen von Visual Studio dieses Feature unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

#### <a name="to-create-a-diagram-and-add-it-to-a-project"></a>So erstellen Sie ein Diagramm und fügen es zu einem Projekt hinzu

1. Wählen Sie im Menü **Architektur** die Option **neues UML-oder ebenendiagramm**aus.

2. Klicken Sie im Dialogfeld **Neues Diagramm hinzufügen** auf den gewünschten Modellierungs Diagrammtyp.

    ![Dialogfeld "Neues Diagramm hinzufügen"](../modeling/media/uml-adddiagram.png "UML_AddDiagram")

3. Geben Sie einen Namen für das neue Diagramm ein.

4. Im Feld **zu Modellierungsprojekt hinzufügen** :

   - Wählen Sie ein Modellierungsprojekt aus, das bereits in der Projekt Mappe vorhanden ist, und klicken Sie dann auf **OK**.

     \- oder -

   1. Wählen Sie **Neues Modellierungsprojekt erstellen**aus, und klicken Sie dann auf **OK**.

   2. Geben Sie im Dialogfeld **Neues Modellierungsprojekt erstellen** einen Namen und einen Speicherort für das neue Projekt ein, und klicken Sie dann auf **OK**.

        ![Dialogfeld "Neues Modellierungsprojekt erstellen"](../modeling/media/uml-createmodel.png "UML_CreateModel")

        Wenn die Projektmappe geöffnet ist, wird das neue Projekt hinzugefügt. Wenn Sie keine Projektmappe geöffnet haben, können Sie einen Namen für eine neue Projektmappe eingeben.

   Wenn Sie bereits ein Modellierungsprojekt haben, können Sie auch das folgende Verfahren einsetzen.

#### <a name="to-add-a-diagram-to-an-existing-modeling-project"></a>Einem vorhandenen Modellierungsprojekt ein Diagramm hinzufügen

1. Klicken Sie in **Projektmappen-Explorer**auf den Modellierungsprojekt Knoten.

    > [!NOTE]
    > Das Modellierungsprojekt enthält einen Modell Definitions Ordner mit dem Namen **Model Definition**.

2. Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.

3. Klicken Sie im Dialogfeld **Neues Element hinzufügen** *\<project name>* unter **Vorlagen**auf den Modellierungs Diagrammtyp, z. b. **UML-Komponenten Diagramm**.

4. Geben Sie einen Namen für das Diagramm ein, und klicken Sie dann auf **Hinzufügen**.

     Das Modellierungsdiagramm wird geöffnet und im Modellierungsprojekt angezeigt.

    > [!CAUTION]
    > Vorhandene Diagrammdateien dürfen nicht hinzugefügt, kopiert oder zu anderen Modellierungsprojekten oder anderen Speicherorten in der Projektmappe gezogen werden. Dies bewirkt, dass Elemente aus den kopierten Diagrammen ausgeblendet werden oder Fehler auftreten, wenn Sie die Diagramme öffnen. Die Diagrammdatei muss im Modellierungsprojekt geöffnet werden, in dem es erstellt wurde. Ein UML-Diagramm ist eine Ansicht des Modells, das zum zum zugehörigen Modellierungsprojekt gehört. Um eine Diagrammdatei zu kopieren, erstellen Sie ein neues Diagramm, und kopieren Sie die Elemente des Quelldiagramms in das neue Diagramm. Weitere Informationen finden Sie unter [Problembehandlung bei Modellierungs Projekten und-Diagrammen](#TroubleshootingModelingProjects).

#### <a name="to-create-a-blank-modeling-project"></a>So erstellen Sie ein leeres Modellierungsprojekt

1. Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.

2. Klicken Sie im Dialogfeld **Neues Projekt** unter **installierte Vorlagen**auf **Modellierungs Projekte**.

3. Klicken Sie im mittleren Fenster auf **Modellierungsprojekt**.

4. Benennen Sie das Projekt, und geben Sie einen Speicherort in den Feldern **Name** und **Speicherort** an.

5. Wählen Sie **im Feldprojekt Mappe die Option** zu Projekt Mappe **Hinzufügen** aus, um das neue Projekt zu einer bereits geöffneten Projekt Mappe hinzuzufügen. oder **Erstellen** Sie eine neue Projekt Mappe, um eine beliebige geöffnete Projekt Mappe zu schließen und das Projekt einer neuen Projekt Mappe hinzuzufügen

## <a name="removing-modeling-diagrams-from-a-project"></a><a name="RemovingModelingDiagrams"></a> Entfernen von Modellierungs Diagrammen aus einem Projekt
 Sie können ein Diagramm dauerhaft löschen, oder Sie können vorübergehend ein Diagramm aus einem Projekt ausschließen und dann wiederherstellen.

#### <a name="to-permanently-delete-a-diagram-from-a-project"></a>Dauerhaftes Löschen ein Diagramms aus einem Projekt

- Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf die Hauptdatei, die das Diagramm darstellt, und klicken Sie dann auf **Löschen**.

     Das Diagramm wird aus dem Projekt und dem Dateisystem entfernt. Die Elemente, die im Diagramm angezeigt werden, werden nicht aus dem **UML-Modell-Explorer**entfernt.

    > [!NOTE]
    > Jedes Diagramm weist zwei Dateien auf, von denen eine der anderen untergeordnet ist. Wenn Sie z. B. ein Komponentendiagramm mit dem Namen `CD1` haben, sollten Sie die Datei mit dem Namen `CD1.componentdiagram` löschen. Die untergeordnete Datei mit dem Namen `CD1.componentdiagram.layout` wird automatisch gelöscht.

#### <a name="to-temporarily-exclude-a-diagram-from-a-project"></a>Vorübergehendes Ausschließen eines Diagramms aus einem Projekt

- Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf die Diagramm Datei, und klicken Sie dann auf **aus Projekt ausschließen**.

     Das Diagramm wird aus dem Projekt entfernt. Es wird nicht aus dem Dateisystem entfernt.

    > [!NOTE]
    > Die Elemente, die im Diagramm angezeigt werden, werden nicht aus dem **UML-Modell-Explorer**entfernt.

#### <a name="to-restore-a-temporarily-excluded-diagram-to-a-project"></a>Ein vorübergehend ausgeschlossenes Diagramm in einem Projekt wiederherstellen

1. Klicken Sie in **Projektmappen-Explorer**auf den Modellierungsprojekt Knoten.

    > [!NOTE]
    > Das Modellierungsprojekt enthält einen Modell Definitions Ordner mit dem Namen **Model Definition**.

2. Klicken Sie im Menü **Projekt** auf **Vorhandenes Element hinzufügen**.

3. Suchen Sie im Dialogfeld **Vorhandenes Element hinzufügen** nach der Diagramm Datei, wählen Sie die Datei aus, und klicken Sie dann auf **Hinzufügen**.

     Das Modellierungsdiagramm wird geöffnet und im Modellierungsprojekt angezeigt.

    > [!NOTE]
    > Jedes Diagramm verfügt über ein Paar von Dateien im Dateisystem. Wählen Sie keine Datei mit der Erweiterung `.layout`. Darüber hinaus bietet Visual Studio keine Unterstützung für das Hinzufügen vorhandener UML-Diagramme zu mehreren Modellierungsprojekten. Jede Diagrammdatei muss im Modellierungsprojekt geöffnet werden, in dem sie erstellt wurde. Ein UML-Diagramm ist eine Ansicht eines Modells, das zum zum zugehörigen Modellierungsprojekt gehört.

## <a name="diagrams-that-do-not-require-modeling-projects"></a><a name="NonModelDiagrams"></a> Diagramme, die keine Modellierungs Projekte erfordern
 Die folgenden Arten von Diagrammen sind nicht Teil eines Modellierungsprojekts:

- Klassendiagramme, die als Ansichten des Quellcodes erstellt werden. Diese beziehen sich nicht auf UML-Klassendiagramme. Weitere Informationen finden Sie unter [Entwerfen und Anzeigen von Klassen und Typen](../ide/designing-and-viewing-classes-and-types.md).

- Code Maps. Siehe [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md).

- Diagramme, die keine UML-Diagramme oder Ebenendiagramme sind, z. B. domänenspezifische Sprachen.

## <a name="troubleshooting-modeling-projects-and-diagrams"></a><a name="TroubleshootingModelingProjects"></a> Problembehandlung bei Modellierungs Projekten und-Diagrammen
 In der folgende Tabelle werden Probleme, die mit Modellierungsprojekten oder Diagrammen und deren Behebung auftreten können, beschrieben:

|**Problem**|**Ursachen**|**Auflösung**|
|---------------|----------------|--------------------|
|Das Modellierungsprojekt kann nicht geöffnet oder in der Projektmappe geladen werden.<br /><br /> Die folgende Meldung wird angezeigt:<br /><br /> "Ein oder mehrere Projekte in der Projektmappe wurden nicht ordnungsgemäß geladen. Details finden Sie im Ausgabefenster."<br /><br /> Im Ausgabefenster wird die folgende Meldung angezeigt:<br /><br /> "*Modelingprojectfile ameandpath*. modelproj: Error: Unbekanntes GUID-Format".|Ein Modellierungsprojekt enthält Verweise auf Projekte, die den gleichen Namen haben und in der gleichen Projektmappe vorkommen.<br /><br /> Beispielsweise ist eine Ebene mit Projekten verknüpft, die den gleichen Namen haben und in der gleichen Projektmappe vorhanden sind.|Verwenden Sie einen Text-Editor, öffnen Sie die Datei, entfernen Sie die Verweise, und versuchen Sie erneut, das Modellierungsprojekt zu öffnen.<br /><br /> Um dieses Problem zu vermeiden, fügen Sie keine Verweise auf Projekte hinzu, die den gleichen Namen haben. Stellen Sie sicher, dass Projekte über eindeutige Namen verfügen.|
|Es fehlen Elemente aus Diagrammen, die hinzugefügt, kopiert oder zu anderen Modellierungsprojekten oder anderen Speicherorten in der Projektmappe gezogen werden.<br /><br /> - oder -<br /><br /> Wenn Sie versuchen, ein Diagramm zu öffnen, werden die folgenden Meldungen angezeigt:<br /><br /> "Einige Formen oder Connectors im Diagramm fehlen, weil ihre Definitionen in diesem Projekt nicht vorhanden sind. Entweder die Definitionen wurden aus dem Modell gelöscht, während das Diagramm geschlossen war, oder das Diagramm wurde in ein anderes Projekt kopiert, das diese Definitionen nicht enthält."<br /><br /> - oder -<br /><br /> -"Dieses Dokument wird von einem anderen Projekt geöffnet."|Die Diagrammdatei wurde hinzugefügt, gezogen oder aus einem Modellierungsprojekt in ein anderes Modellierungsprojekt oder an einen anderen Speicherort in der Projektmappe kopiert.|Um eine Diagrammdatei zu kopieren, erstellen Sie ein neues Diagramm, und kopieren Sie die Elemente des Quelldiagramms in das neue Diagramm.|

## <a name="see-also"></a>Weitere Informationen
 [Bearbeiten von UML-Modellen und-Diagrammen](../modeling/edit-uml-models-and-diagrams.md) [strukturieren der Modellierungs Lösung](../modeling/structure-your-modeling-solution.md)
