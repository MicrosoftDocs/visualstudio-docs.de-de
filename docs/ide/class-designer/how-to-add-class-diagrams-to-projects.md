---
title: Hinzufügen von Klassendiagrammen zu Projekten (Klassen-Designer)
description: Lernen Sie, Klassen und andere Typen zu entwerfen, zu bearbeiten und umzugestalten und Ihrem C#-, Visual Basic- oder C++-Projekt ein Klassendiagramm hinzuzufügen.
ms.custom: SEO-VS-2020
ms.date: 05/08/2018
ms.topic: how-to
helpviewer_keywords:
- class diagrams, creating
- Class Designer [Visual Studio], opening
ms.assetid: 0eac1b54-2711-4e4b-9654-a0c429c08c8f
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a27f5ae8320e942d5167fcc8260179f8cec96e37
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99850281"
---
# <a name="how-to-add-class-diagrams-to-projects"></a>Vorgehensweise: Hinzufügen von Klassendiagrammen zu Projekten

Fügen Sie Ihrem Projekt in C#, Visual Basic oder C++ ein Klassendiagramm hinzu, damit Sie Klassen und andere Typen entwerfen, bearbeiten und umgestalten können. Sie können verschiedene Teile des Codes in einem Projekt visualisieren, indem Sie dem Projekt mehrere Klassendiagramme hinzufügen.

Sie können Klassendiagramme nicht aus Projekten erstellen, deren Code in mehreren Apps verwendet wird. Informationen zum Erstellen von UML-Klassendiagrammen finden Sie unter [Erstellen von UML-Modellierungsprojekten und -Diagrammen](../../modeling/what-s-new-for-design-in-visual-studio.md).

## <a name="install-the-class-designer-component"></a>Installieren der Klassen-Designer-Komponente

Wenn Sie die Komponente **Klassen-Designer** nicht installiert haben, befolgen Sie die nachstehenden Schritte, um sie zu installieren.

1. Öffnen Sie den **Visual Studio-Installer** über das Windows-Startmenü der durch Auswahl von **Extras** > **Get Tools and Features** (Tools und Features abrufen) über die Menüleiste in Visual Studio.

   Der **Visual Studio-Installer** wird geöffnet.

1. Wählen Sie die Registerkarte **Einzelne Komponenten** aus, und scrollen Sie nach unten zur Kategorie **Codetools**.

1. Wählen Sie den **Klassen-Designer** aus, und klicken Sie anschließend auf **Ändern**.

   ![Klassen-Designer-Komponente im Visual Studio-Installer](media/class-designer-component.png)

   Die **Klassen-Designer**-Komponente wird daraufhin installiert.

## <a name="add-a-blank-class-diagram-to-a-project"></a>Hinzufügen eines leeren Klassendiagramms zu einem Projekt

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projektknoten und dann auf **Hinzufügen** > **Neues Element**. Drücken Sie alternativ auf **STRG**+**UMSCHALT**+**A**.

   Das Dialogfeld **Neues Element hinzufügen** wird geöffnet.

2. Erweitern Sie **Gemeinsame Elemente** > **Allgemein**, und wählen Sie dann aus der Vorlagenliste **Klassendiagramm** aus. Suchen Sie für Visual C++-Projekte in der Kategorie **Hilfsprogramm** nach der Vorlage **Klassendiagramm**.

   > [!NOTE]
   > Wenn Sie die Vorlage **Klassendiagramm** nicht sehen, [befolgen Sie diese Schritte](#install-the-class-designer-component), um die Komponente **Klassen-Designer** für Visual Studio zu installieren.

   Das Klassendiagramm wird im Klassen-Designer geöffnet. Im **Projektmappen-Explorer** wird es als Datei mit der Erweiterung *.cd* angezeigt. Sie können Formen und Linien aus der **Toolbox** in das Diagramm ziehen.

Wiederholen Sie diese Schritte, um weitere Klassendiagramme hinzuzufügen.

## <a name="add-a-class-diagram-based-on-existing-types"></a>Hinzufügen eines auf vorhandenen Typen basierenden Klassendiagramms

Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü der Klassendatei (durch Rechtsklick), und klicken Sie anschließend auf **Klassendiagramm anzeigen**.

\- oder -

Öffnen Sie in **Klassenansicht** das Kontextmenü für den Namespace oder Typ, und wählen Sie anschließend **Klassendiagramm anzeigen** aus.

> [!TIP]
> Wenn die **Klassenansicht** nicht geöffnet ist, öffnen Sie **Klassenansicht** über das Menü **Ansicht**.

## <a name="to-display-the-contents-of-a-complete-project-in-a-class-diagram"></a>So zeigen Sie alle Inhalte eines Projekts in einem Klassendiagramm an

Klicken Sie im **Projektmappen-Explorer** oder in der Klassenansicht mit der rechten Maustaste auf das Projekt, und klicken Sie auf **Anzeigen** und anschließend auf **Klassendiagramm anzeigen**.

Daraufhin wird ein automatisch aufgefülltes Klassendiagramm erstellt.

> [!NOTE]
> Der Klassen-Designer ist in .NET Core-Projekten nicht verfügbar.

## <a name="see-also"></a>Weitere Informationen

- [Vorgehensweise: Erstellen von Typen mit dem Klassen-Designer](how-to-create-types.md)
- [Vorgehensweise: Anzeigen von vorhandenen Typen](how-to-view-existing-types.md)
- [Entwerfen und Anzeigen von Klassen und Typen](designing-and-viewing-classes-and-types.md)
