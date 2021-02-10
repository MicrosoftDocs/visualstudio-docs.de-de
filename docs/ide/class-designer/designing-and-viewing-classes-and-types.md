---
title: Verwenden des Klassen-Designers
description: Erfahren Sie mehr über Design, Visualisierung und Refactoring von Klassen und anderen Typen in Ihrem Code mit dem Klassen-Designer in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 05/08/2018
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.diagram
- vs.classdesigner.enum
helpviewer_keywords:
- Class Designer [Visual Studio]
- Class Designer, about Class Designer
- types [Visual Studio], viewing
- classes [Visual Studio], viewing
- class designer
ms.assetid: 40ed2c9d-0ce0-4b95-ad78-5dec2065ccea
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 236efe20ee652e2690cedf36843d539bf8a9cc46
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99850294"
---
# <a name="design-and-view-classes-and-types-with-class-designer"></a>Entwerfen und Anzeigen von Klassen und Typen mit dem Klassen-Designer

Mit dem **Klassen-Designer** in Visual Studio können Sie Klassen und andere Typen in Ihrem Code entwerfen, visualisieren und Refactorings für diese durchführen. Verwenden Sie Klassendiagramme, um Klassen in Ihrem C#-, Visual Basic- oder C++-Projekt zu erstellen und zu bearbeiten. Sie können Klassendiagramme ebenfalls verwenden, um die Struktur Ihres Projekts besser nachvollziehen zu können oder um Ihren Code umzustrukturieren.

## <a name="what-you-can-do-with-class-diagrams"></a>Möglichkeiten mit Klassendiagrammen

- **Entwerfen**: Bearbeiten Sie den Code Ihres Projekts, indem Sie das Klassendiagramm bearbeiten. Neue Elemente hinzufügen und unerwünschte Elemente löschen. Die Änderungen werden im Code wiedergegeben.

- **Visualisieren**: Erhalten Sie Einblick in die Struktur des Projekts, indem Sie sich die Klassen in Ihrem Projekt in einem Diagramm ansehen. Passen Sie Ihr Diagramm so an, dass Sie sich auf die Projektdetails konzentrieren können, die Sie am meisten interessieren. Speichern Sie das Diagramm später zu Demonstrations- oder Dokumentationszwecken.

- **Umgestalten**: Überschreiben Sie Methoden, benennen Sie Bezeichner um, gestalten Sie Parameter um und implementieren Sie Schnittstellen sowie abstrakte Klassen.

## <a name="view-types-and-relationships"></a>Anzeigen von Typen und Beziehungen

Klassendiagramme informieren Sie über Typdetails wie etwa zugehörige Members und deren Beziehungen zueinander. Die Visualisierung dieser Entitäten stellt eine dynamische Codeansicht dar. Dies bedeutet, dass Sie Typen im Klassen-Designer bearbeiten können und sich diese Änderungen im Quellcode der Entität anzeigen lassen können. Analog dazu wird das Klassendiagramm mit Änderungen synchronisiert, die Sie in Codedateien vornehmen.

> [!NOTE]
> Wenn das Projekt ein Klassendiagramm enthält und auf einen Typ verweist, der sich in einem anderen Projekt befindet, wird der referenzierte Typ erst dann im Klassendiagramm angezeigt, wenn Sie das Projekt für diesen Typ erstellen. Außerdem werden im Diagramm Änderungen am Code der externen Entität erst dann angezeigt, wenn Sie das Projekt für diese Entität neu erstellen.

## <a name="class-diagram-workflow"></a>Workflow des Klassendiagramms

Klassendiagramme können Ihnen dabei helfen, die Klassenstruktur von Projekten zu verstehen. Diese Projekte wurde womöglich von anderen Entwicklern erstellt, oder Sie benötigen einfach nur eine Auffrischung für ein Projekte, das Sie selbst erstellt haben. Sie können Klassendiagramme zur Anpassung, gemeinsamen Nutzung und zum Präsentieren von Projektinformationen mit anderen verwenden.

Der erste Schritt beim Präsentieren von Projektinformationen ist das Erstellen eines Klassendiagramms, das anzeigt, was Sie anzeigen möchten. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen von Klassendiagrammen zu Projekten (Klassen-Designer)](how-to-add-class-diagrams-to-projects.md). Sie können für ein Projekt mehrere Klassendiagramme erstellen, mit denen eine andere Ansicht des Projekts, eine ausgewählte Teilmenge der Projekttypen oder eine ausgewählte Teilmenge der Mitgliedstypen angezeigt werden.

Neben der Definition der einzelnen Klassendiagramme, können Sie auch die Art ändern, mit der die Informationen präsentiert werden. Weitere Informationen finden Sie unter [Vorgehensweise: Anpassen von Klassendiagrammen](how-to-customize-class-diagrams.md).

Nach dem Tunen eines oder mehrerer Klassendiagramme können Sie sie in Microsoft Office-Dokumente kopieren und drucken oder als Bilddateien exportieren. Weitere Informationen finden Sie unter [Vorgehensweise: Kopieren von Klassendiagrammelementen in ein Microsoft Office-Dokument](how-to-copy-class-diagram-elements-to-a-microsoft-office-document.md), [Vorgehensweise: Drucken von Klassendiagrammen](how-to-print-class-diagrams.md) und [Vorgehensweise: Exportieren von Klassendiagrammen als Bilder (Klassen-Designer)](how-to-export-class-diagrams-as-images.md).

> [!NOTE]
> Klassen-Designer verfolgt nicht den Speicherort der Quelldateien, so dass die Änderung der Projektstruktur oder verschobenen Quelldateien im Projekt dazu führen kann, dass der Klassen-Designer den Typ, insbesondere den Quelltyp eines TypeDef-, Basisklassen oder Zuordnungstypen verliert. Es wird möglicherweise ein Fehler angezeigt, z.B. **Dieser Typ kann im Klassen-Designer nicht angezeigt werden**. In diesem Fall ziehen Sie den geänderten oder verschobenen Quellcode in das Klassendiagramm, um ihn erneut anzuzeigen.

## <a name="see-also"></a>Siehe auch

- [Features des Code-Editors](../writing-code-in-the-code-and-text-editor.md)
- [Projektmappenübergreifendes Zuordnen von Abhängigkeiten](../../modeling/map-dependencies-across-your-solutions.md)
