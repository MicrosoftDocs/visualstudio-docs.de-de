---
title: 'Gewusst wie: Anpassen von Klassendiagrammen (Klassen-Designer)'
description: Lernen Sie, die Art zu ändern, in der Klassendiagramme Informationen anzeigen, und das gesamte Diagramm oder die einzelnen Typen auf der Entwurfsoberfläche anzupassen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- class diagrams, customizing
- shapes, removing type from class diagrams
- type shapes, removing from class diagrams
- class diagrams, removing type shapes
ms.assetid: e9030aea-c77d-4cc1-b8f6-b6ca469b692d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 768c61ab525d03a7b9a1a80481b84b492d6bd0c6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919637"
---
# <a name="how-to-customize-class-diagrams"></a>Vorgehensweise: Anpassen von Klassendiagrammen

Sie können die Art und Weise ändern, in der in Klassendiagrammen Informationen angezeigt werden. Sie können das gesamte Diagramm oder die einzelnen Typen auf der Entwurfsoberfläche anpassen.

Beispielsweise können Sie den Zoomfaktor eines gesamten Klassendiagramms einstellen, die Gruppierung und Sortierung einzelner Typmember ändern, Beziehungen anzeigen oder ausblenden, und einzelne Typen oder mehrere Typen gemeinsam an eine beliebige Position auf dem Diagramm verschieben.

> [!NOTE]
> Durch das Anpassen der Art und Weise, wie Formen im Diagramm angezeigt werden, wird der zugrunde liegende Code für die im Diagramm angezeigten Typen nicht geändert.

Abschnitte, die Typmembers enthalten (z.B. der Abschnitt **Eigenschaften** einer Klasse) werden als „Depots“ bezeichnet. Sie können einzelne Depots und Typmember anzeigen oder ausblenden.

## <a name="zoom-in-and-out-of-the-class-diagram"></a>Vergrößern und Verkleinern der Ansicht des Klassendiagramms

1. Wählen Sie eine Klassendiagrammdatei im **Klassen-Designer** aus, und öffnen Sie diese.

2. Klicken Sie auf der Symbolleiste des **Klassen-Designers** auf die Schaltfläche **Vergrößern** oder **Verkleinern**, um den Zoomfaktor der Designer-Oberfläche zu ändern.

     oder

     Geben Sie einen bestimmten Zoomwert an. Sie können die Dropdownliste **Zoom** verwenden oder einen gültigen Zoomfaktor eingeben (der gültige Bereich liegt bei 10 % bis 400 %).

    > [!NOTE]
    > Das Ändern des Zoomfaktors wirkt sich nicht auf die Skalierung des ausgedruckten Klassendiagramms aus.

## <a name="customize-grouping-and-sorting-of-type-members"></a>Anpassen der Gruppierung und Sortierung von Typmembern

1. Wählen Sie eine Klassendiagrammdatei im **Klassen-Designer** aus, und öffnen Sie diese.

2. Klicken Sie mit der rechten Maustaste auf einen leeren Bereich auf der Entwurfsoberfläche, und zeigen Sie auf **Member gruppieren**.

3. Wählen Sie eine der verfügbaren Optionen aus:

    - **Nach Art gruppieren** unterteilt einzelne Typmember in eine gruppierte Liste von Eigenschaften, Methoden, Ereignissen und Feldern. Die einzelnen Gruppen hängen von der Entitätendefinition ab: Beispielsweise wird in einer Klasse keine Gruppe von Ereignissen angezeigt, wenn noch keine Ereignisse für diese Klasse definiert sind.

    - **Nach Zugriff gruppieren** unterteilt einzelne Typmember auf der Grundlage der Zugriffsmodifizierer des Members in eine gruppierte Liste. Beispiel: Public und Private.

    - **Alphabetisch sortieren** zeigt die Elemente, aus denen eine Entität besteht, als einzelne, alphabetisch sortierte Liste an. Die Liste ist in aufsteigender Reihenfolge sortiert.

## <a name="hide-compartments-on-a-type"></a>Ausblenden von Depots für einen Typ

1. Wählen Sie eine Klassendiagrammdatei im **Klassen-Designer** aus, und öffnen Sie diese.

2. Klicken Sie mit der rechten Maustaste auf die Memberkategorie in dem Typ, die Sie anpassen möchten (wählen Sie z.B. den Knoten **Methoden** in einer Klasse aus).

3. Klicken Sie auf **Depot ausblenden**.

     Das ausgewählte Depot wird im Typcontainer ausgeblendet.

## <a name="hide-individual-members-on-a-type"></a>Ausblenden einzelner Member für einen Typ

1. Wählen Sie eine Klassendiagrammdatei im **Klassen-Designer** aus, und öffnen Sie diese.

2. Klicken Sie mit der rechten Maustaste in dem Typ auf den Member, den Sie ausblenden möchten.

3. Klicken Sie auf **Ausblenden**.

     Der ausgewählte Member wird im Typcontainer ausgeblendet.

## <a name="show-hidden-compartments-and-members-on-a-type"></a>Anzeigen ausgeblendeter Depots und Member für einen Typ

1. Wählen Sie eine Klassendiagrammdatei im **Klassen-Designer** aus, und öffnen Sie diese.

2. Klicken Sie mit der rechten Maustaste auf den Namen des Typs mit dem ausgeblendeten Depot.

3. Klicken Sie auf **Alle Member anzeigen**.

     Alle ausgeblendeten Depots und Member werden im Typcontainer angezeigt.

## <a name="hide-relationships"></a>Ausblenden von Beziehungen

1. Wählen Sie eine Klassendiagrammdatei im **Klassen-Designer** aus, und öffnen Sie diese.

2. Klicken Sie mit der rechten Maustaste auf die Zuordnungs- oder Vererbungszeile, die Sie ausblenden möchten.

3. Klicken Sie für Zuordnungszeilen auf **Ausblenden**, und klicken Sie für Vererbungszeilen auf **Vererbungszeile ausblenden**.

4. Klicken Sie auf **Alle Member anzeigen**.

     Alle ausgeblendeten Depots und Member werden im Typcontainer angezeigt.

## <a name="show-hidden-relationships"></a>Anzeigen ausgeblendeter Beziehungen

1. Wählen Sie eine Klassendiagrammdatei im **Klassen-Designer** aus, und öffnen Sie diese.

2. Klicken Sie mit der rechten Maustaste auf den Typ mit der ausgeblendeten Zuordnung oder Vererbung.

   Klicken Sie für Zuordnungszeilen auf **Alle Member anzeigen**, und klicken Sie für Vererbungszeilen auf **Basisklasse anzeigen** oder **Abgeleitete Klassen anzeigen**.

## <a name="remove-a-shape-from-a-class-diagram"></a>Entfernen einer Typform aus einem Klassendiagramm
Sie können eine Typform aus dem Klassendiagramm entfernen, ohne dass dies Auswirkungen auf den zugrunde liegenden Code des Typs hat. Das Entfernen von Typformen aus einem Klassendiagramm wirkt sich nur auf das jeweilige Diagramm aus. Der zugrunde liegende Code, der den Typ definiert, und andere Diagramme, die den Typ anzeigen, sind nicht betroffen.

1. Wählen Sie im Klassendiagramm die aus dem Diagramm zu entfernende Typform aus.

2. Klicken Sie im Menü **Bearbeiten** auf **Aus Diagramm entfernen**.

     Die Typform und sämtliche mit der Form verbundene Assoziations- oder Vererbungslinien werden aus dem Diagramm entfernt.

## <a name="delete-a-type-shape-and-its-underlying-code"></a>Löschen einer Typform und des zugrunde liegenden Codes

1. Klicken Sie auf der Entwurfsoberfläche mit der rechten Maustaste auf die Form.

2. Wählen Sie im Kontextmenü die Option **Code löschen** aus.

     Die Form wird aus dem Diagramm entfernt, und der zugrunde liegende Code wird aus dem Projekt gelöscht.

## <a name="see-also"></a>Weitere Informationen

- [Vorgehensweise: Wechseln zwischen Member- und Zuordnungsnotation](how-to-change-between-member-notation-and-association-notation.md)
- [Vorgehensweise: Anzeigen von vorhandenen Typen](how-to-view-existing-types.md)
- [Anzeigen von Typen und Beziehungen](designing-and-viewing-classes-and-types.md)
