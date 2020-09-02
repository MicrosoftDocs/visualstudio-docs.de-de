---
title: Verknüpfen von Modellelementen und Arbeits Elementen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.common.removeworkitemsdialog
- vs.teamarch.common.linkworkitemsdialog
helpviewer_keywords:
- UML - extending, linking to TFS work items
- UML - extending, linking work items
- work items, creating from UML models
- UML model, creating work items
- work items, linking to UML models
- UML model, linking work items
ms.assetid: e687a490-0f93-412c-a1ff-eea83cf7ba07
caps.latest.revision: 49
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ee4fea9e3fb1d5b4d27b1d520ac2ab036747f73d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657629"
---
# <a name="link-model-elements-and-work-items"></a>Verknüpfen von Modellelementen und Arbeitselemente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Verfolgen Sie Aufgaben, Testfälle, Fehler, Anforderungen, Probleme und andere Arbeiten, die mit dem Modell verknüpft sind, indem Sie Modellelemente in Visual Studio und Arbeitselemente in Team Foundation Server oder Visual Studio Team Services miteinander verknüpfen. Fügen Sie Dokumente an verknüpfte Arbeitselemente an, um sie Modellelementen zuzuordnen.

 Welche Versionen von Visual Studio dieses Feature unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> Sie müssen Team Explorer zum Erstellen und Öffnen von Links verwenden. Vergewissern Sie sich, dass das Modellierungsprojekt und die Diagramme in die Versionskontrolle eingecheckt werden, damit andere Benutzer verknüpfte Diagramme öffnen können.

 Sie können unter anderem Folgendes verknüpfen:

- Ein User Story-Arbeitselement mit einem Aktivitätsdiagramm, um zu zeigen, wie die Story als Sequenz von Vorgängen implementiert werden kann.

- Ein Anwendungsfall in einem Anwendungsfalldiagramm und Testfallarbeitselemente, um sicherstellen, dass der Anwendungsfall ordnungsgemäß implementiert wird.

- Ein Attribut in einer Klasse in einem UML-Klassendiagramm mit einem Fehlerarbeitselement, um einen Fehler in der Implementierung des Attributs aufzuzeigen.

- Eine Komponente in einem Komponentendiagramm mit einem aufgabenbezogenen Arbeitselement, um die Entwicklung der Komponente nachzuverfolgen. Eine solche Aufgabe ist normalerweise in kleinere Aufgaben aufgeteilt.

  Sie können Arbeitselemente mit jedem Element verknüpfen, das Sie in den Modellierungsdiagrammen oder im UML-Modell-Explorer auswählen können, wie zum Beispiel folgende Elemente:

- Alle Elemente in UML-Modellen, z. B. UML-Klassen, Lebenslinien, Anwendungsfälle, Subsysteme, Aktivitäten, Objektknoten, Komponenten, Schnittstellen

- Alle Beziehungen in UML-Modellen, z. B. Zuordnungen, Verallgemeinerungen, Abhängigkeiten, Flüsse, Meldungen

- Teile von Elementen, z. B. die Attribute und Vorgänge von Klassen, die Ausführungen von Lebenslinien, die Eingabe- und Ausgabepins von Aktivitäten sowie die Teile und Ports von Komponenten

- Ebenen und Ebenenabhängigkeiten

- Kommentare und Kommentarlinks

- Diagramme. Wählen Sie einen leeren Bereich des Diagramms aus, um ein Diagramm auszuwählen.

> [!WARNING]
> Sie müssen bereits mit der TFS-Quellcodeverwaltung verbunden sein, um ein Arbeitselement zu erstellen oder zu verknüpfen. Wenn Sie versuchen, eine Verbindung mit einer anderen TFS-Quellcodeverwaltung herzustellen, schließt Visual Studio automatisch die aktuelle Projektmappe. Stellen Sie sicher, dass Sie bereits mit der richtigen Quellcodeverwaltung verbunden sind, bevor Sie versuchen, ein Arbeitselement zu erstellen oder zu verknüpfen. In höheren Versionen von Visual Studio stehen die Menübefehle nicht zur Verfügung, wenn Sie mit keiner Quellcodeverwaltung verbunden sind.

- [Stellen Sie eine Verbindung mit einem Teamprojekt her.](#ConnectTFS)

- [Verknüpfen eines Modellelements mit einem neuen Arbeitselement](#LinkNew)

- [Verknüpfen eines Modellelements mit einem vorhandenen Arbeitselement](#LinkExisting)

- [Anzeigen eines mit einem Modellelement verknüpften Arbeitselements](#OpenWorkItem)

- [Anzeigen der mit einem Arbeitselement verknüpften Modellelemente](#ViewLinkedModels)

- [Löschen von Verknüpfungen zwischen Modellelementen und Arbeitselementen](#RemoveLinks)

- [Problembehandlung](#Troubleshooting)

## <a name="connect-to-a-team-project"></a><a name="ConnectTFS"></a> Herstellen einer Verbindung mit einem Teamprojekt
 Sie müssen zuerst eine Verbindung mit Ihrem Teamprojekt herstellen, um Verknüpfungen zu erstellen, anzuzeigen oder zu entfernen.

1. Wählen Sie zum Anzeigen des Team Explorer-Fensters im Menü **Team****Verbindungen verwalten** aus

2. Wenn das richtige Projekt nicht in Team Explorer angezeigt wird, wählen Sie **Verbindungen verwalten** , und wählen Sie dann **Verbindung mit Teamprojekt herstellen**. Wählen Sie dann die richtigen Projekte oder ggf. die richtigen Server aus.

3. Wählen Sie in **Team Explorer**das Projekt aus, in dem Sie Arbeitselemente erstellen, verknüpfen oder anzeigen möchten.

## <a name="link-a-model-element-to-a-new-work-item"></a><a name="LinkNew"></a> Verknüpfen eines Modell Elements mit einer neuen Arbeitsaufgabe

1. Vergewissern Sie sich, dass Sie mit der TFS-Instanz verbunden sind, die Sie verwenden möchten.

2. Öffnen Sie das Kontextmenü für das Modellelement auf dem Modellierungsdiagramm oder im **UML-Modell-Explorer**.

3. Wählen Sie die Option **Arbeitselement erstellen** und den zu erstellenden Arbeitselementtyp aus.

4. Füllen Sie die Felder im Arbeitselementformular aus. Wählen Sie **Arbeitselement speichern**.

     Visual Studio verknüpft das Modellelement mit dem neuen Arbeitselement. Ein Symbol wird auf dem Modellelement oder in seiner Nähe angezeigt.

> [!WARNING]
> Sie müssen bereits mit der TFS-Quellcodeverwaltung verbunden sein, um ein Arbeitselement zu erstellen oder zu verknüpfen. Wenn Sie versuchen, eine Verbindung mit einer anderen TFS-Quellcodeverwaltung herzustellen, schließt Visual Studio automatisch die aktuelle Projektmappe. Stellen Sie sicher, dass Sie bereits mit der richtigen Quellcodeverwaltung verbunden sind, bevor Sie versuchen, ein Arbeitselement zu erstellen oder zu verknüpfen. In höheren Versionen von Visual Studio stehen die Menübefehle nicht zur Verfügung, wenn Sie mit keiner Quellcodeverwaltung verbunden sind.

## <a name="link-a-model-element-to-an-existing-work-item"></a><a name="LinkExisting"></a> Verknüpfen eines Modell Elements mit einer vorhandenen Arbeitsaufgabe
 Wenn Sie Modellelemente mit Arbeitselementen verknüpfen, beginnen Sie beim Modellelement, nicht beim Arbeitselement.

1. Vergewissern Sie sich, dass Sie mit der TFS-Instanz verbunden sind, die Sie verwenden möchten.

2. Öffnen Sie das Kontextmenü für das Modellelement auf dem Modellierungsdiagramm oder im **UML-Modell-Explorer**. Wählen Sie **Mit Arbeitselement verknüpfen** aus. Wählen Sie dann das Projekt im Feld **Projekt** aus.

3. Wählen Sie mit einem der folgenden Schritte eine oder mehrere Arbeitselemente aus, die mit dem Modellelement verknüpft werden sollen:

    - Wählen Sie in **Gespeicherte Abfrage**eine Abfrage aus.

    - Geben Sie in **IDs**die IDs für eines oder mehrere Arbeitselemente durch Leerzeichen getrennt ein.

    - Geben Sie in **Titel enthält**ein Wort oder einen Ausdruck ein.

4. Wählen Sie **Suchen**aus.

5. Wählen Sie in der Arbeitselementliste die Arbeitselemente aus, die Sie verknüpfen möchten.

     Nach der Verknüpfung weist die Eigenschaft **Arbeitselemente** des Modellelements eine größere Zahl als zuvor auf. Es wird auch ein Symbol auf dem Modellelement oder in seiner Nähe angezeigt.

> [!WARNING]
> Sie müssen bereits mit der TFS-Quellcodeverwaltung verbunden sein, um ein Arbeitselement zu erstellen oder zu verknüpfen. Wenn Sie versuchen, eine Verbindung mit einer anderen TFS-Quellcodeverwaltung herzustellen, schließt Visual Studio automatisch die aktuelle Projektmappe. Stellen Sie sicher, dass Sie bereits mit der richtigen Quellcodeverwaltung verbunden sind, bevor Sie versuchen, ein Arbeitselement zu erstellen oder zu verknüpfen. In höheren Versionen von Visual Studio stehen die Menübefehle nicht zur Verfügung, wenn Sie mit keiner Quellcodeverwaltung verbunden sind.

## <a name="view-work-items-linked-to-a-model-element"></a><a name="OpenWorkItem"></a> Anzeigen von mit einem Modellelement verknüpften Arbeits Elementen

1. Vergewissern Sie sich in **Team Explorer**, dass eine Verbindung mit dem Teamprojekt hergestellt wurde, in dem die Arbeitselemente mit dem Modellelement verknüpft sind.

2. Öffnen Sie das Kontextmenü für das Modellelement auf dem Modellierungsdiagramm oder im **UML-Modell-Explorer**. Wählen Sie die Option **Arbeitselemente anzeigen** aus, um die Liste verknüpfter Arbeitselemente anzuzeigen.

    > [!NOTE]
    > Es werden nur die Arbeitselemente vom aktuell verbundenen Server angezeigt. Wenn keine Arbeitselemente angezeigt werden, müssen Sie sich vergewissern, dass Sie in **Team Explorer**mit dem richtigen Server verbunden sind.

## <a name="view-model-elements-linked-to-a-work-item"></a><a name="ViewLinkedModels"></a> Anzeigen von Modellelementen, die mit einem Arbeits Element verknüpft sind
 Sie können Modellierungsdiagramme und Elemente anzeigen, die in Visual Studio Team Services und in Team Foundation Server 2012 oder höher mit einen Arbeitselement verknüpft sind. Beispielsweise könnte ein Arbeitselement mit Klassenmodellen verknüpft sein, um den Entwurf der neuen zu implementierenden Klassen zu veranschaulichen.

1. Vergewissern Sie sich in **Team Explorer**, dass eine Verbindung mit dem Teamprojekt hergestellt wurde, in dem die Modellelemente mit dem Arbeitselement verknüpft sind.

    > [!NOTE]
    > Sie können nur Team Explorer und nicht Team Web Access zum Anzeigen verknüpfter Modellelemente verwenden. Vergewissern Sie sich, dass der Arbeitsbereich dem Modellierungsprojekt zugeordnet wird, das die Modellierungsdiagramme oder -elemente enthält. Wenn Sie noch über keinen Arbeitsbereich verfügen, müssen Sie ihn erstellen. Weitere Informationen finden Sie unter [Problembehandlung](#Troubleshooting) und [Erstellen und Verwenden von Arbeitsbereichen](https://msdn.microsoft.com/library/1d7f6ed8-ec7c-48f8-86da-9aea55a90d5a).

2. Öffnen Sie das Arbeitselement, und wählen Sie **Links** aus. Öffnen Sie unter **Modelllink**das Kontextmenü für das verknüpfte Modellelement. Wählen Sie **Verknüpftes Element öffnen**aus.

     ![Verknüpftes Modellelement in einem Arbeitselement öffnen](../modeling/media/workitem-openlinkedmodelelement.png "WorkItem_OpenLinkedModelElement")

## <a name="delete-links-between-model-elements-and-work-items"></a><a name="RemoveLinks"></a> Löschen von Verknüpfungen zwischen Modellelementen und Arbeits Elementen
 Entfernen Sie ein verknüpftes Arbeitselement, indem Sie beim Modellelement beginnen. Hierdurch wird die reziproke Verknüpfung zu diesem Modellelement ordnungsgemäß aus dem Arbeitselement entfernt. Wenn Sie mit dem Arbeitselement beginnen, wird die reziproke Verknüpfung des Modellelements mit dem Arbeitselement andernfalls nicht gelöscht.

1. Öffnen Sie das Kontextmenü für das Modellelement auf dem Modellierungsdiagramm oder im **UML-Modell-Explorer**.

2. Wählen Sie **Arbeitselemente entfernen**.

     \- oder -

    1. Wählen Sie **Eigenschaften**und dann **Arbeitselemente** aus, wobei die Anzahl von verknüpften Arbeitselemente angezeigt wird.

    2. Wählen Sie in der Eigenschaft **Arbeitselemente** die Schaltfläche mit den Auslassungszeichen **[…]**.

        > [!NOTE]
        > Es werden nur die Arbeitselemente auf dem aktuellen Server angezeigt. Wenn die Liste leer ist, die Anzahl von Arbeitselementen jedoch nicht 0 ist, überprüfen Sie, ob in **Team Explorer**eine Verbindung mit dem richtigen Server besteht.

3. Deaktivieren Sie unter der Option für **Links zu Arbeitselementen entfernen**die ausgewählten Elemente, deren Verknüpfung Sie aufheben möchten. Klicken Sie auf **OK**.

## <a name="troubleshooting"></a><a name="Troubleshooting"></a> Problembehandlung

|**Problem**|**Mögliche Ursache**|**Auflösung**|
|---------------|------------------------|--------------------|
|Das Modellelement, das Sie verknüpfen möchten, kann nicht gefunden werden.|Das Element könnte sich in einem Diagramm eines Modellierungsprojekts in [!INCLUDE[esprscc](../includes/esprscc-md.md)]befinden. Sie verfügen möglicherweise über keinen Arbeitsbereich, der dem Diagramm zugeordnet ist.|Ordnen Sie den Arbeitsbereich dem Modellierungsprojekt und dem Diagramm zu. Wenn Sie noch über keinen Arbeitsbereich verfügen, müssen Sie ihn erstellen.<br /><br /> Die für dieses Problem angezeigte Fehlermeldung enthält den Pfad, mit dem Sie den Arbeitsbereich zuordnen können.<br /><br /> Siehe [Erstellen und Verwenden von Arbeitsbereichen](https://msdn.microsoft.com/library/1d7f6ed8-ec7c-48f8-86da-9aea55a90d5a).|
|Das verknüpfte Modellelement kann nicht gefunden werden.|Das verknüpfte Element könnte sich in einem Diagramm befinden, das verschoben, umbenannt oder gelöscht wurde.|1. löschen Sie in der Arbeitsaufgabe den Link zum Modellelement.<br />2. Erstellen Sie einen neuen Link aus dem Arbeits Element zum Modellelement.|
|Das Arbeitselement umfasst nicht die von Ihnen erwarteten verknüpften Modellelemente.|Ein Arbeitselement zeigt ein verknüpftes Ebenenelement nur an, wenn der Link vom Arbeitselement aus erstellt wurde. Wenn das Team [!INCLUDE[esprscc](../includes/esprscc-md.md)]nicht verwendet, wird der lokale Pfad der Diagramme zum Erstellen der Links verwendet. Wenn sich das Modellierungsprojekt und seine Diagramme in [!INCLUDE[esprscc](../includes/esprscc-md.md)]befinden, können alle Teammitglieder, die auf das Projekt zugreifen können, verknüpfte Elemente in Arbeitselementen anzeigen.|Versuchen Sie, das Arbeitselement zu aktualisieren.|
|Durch das Löschen eines Links von einem Arbeitselement zu einem Modellelement wird der Link vom Modellelement zum Arbeitselement nicht entfernt.||Löschen Sie den Link zum Arbeitselement ausgehend vom Modellelement.|

## <a name="see-also"></a>Weitere Informationen
 [Bearbeiten von UML-Modellen und-Diagrammen](../modeling/edit-uml-models-and-diagrams.md) [Erstellen von Modellen für Ihre APP](../modeling/create-models-for-your-app.md)
