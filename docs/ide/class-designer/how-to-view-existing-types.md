---
title: 'Gewusst wie: Anzeigen von vorhandenen Typen (Klassen-Designer)'
description: Lernen Sie, einen vorhandenen Typ und die zugehörigen Member anzuzeigen, indem Sie seine Form einem Klassendiagramm hinzufügen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.classdesigner.CannotShowBaseType
helpviewer_keywords:
- types [Visual Studio], visualizing
- types [Visual Studio], class diagrams
- class diagrams, types
ms.assetid: de110a4e-5b51-4a40-9dee-615df4d8f999
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d5249102013aaf72a48c7137b415636952ed1d0d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951809"
---
# <a name="how-to-view-existing-types-in-class-designer"></a>Vorgehensweise: Anzeigen von vorhandenen Typen im Klassen-Designer

Um einen vorhandenen Typ und die zugehörigen Member anzuzeigen, fügen Sie seine Form einem Klassendiagramm hinzu.

Es werden lokale und referenzierte Typen angezeigt. Ein lokaler Typ ist im aktuell geöffneten Projekt vorhanden und kann sowohl gelesen als auch geschrieben werden. Ein Typ, auf den verwiesen wird, ist in einem anderen Projekt oder einer Assembly, auf die verwiesen wird, enthalten und ist schreibgeschützt.

Informationen zum Erstellen neuer Typen in Klassendiagrammen finden Sie unter [Vorgehensweise: Erstellen von Typen im Klassen-Designer](how-to-create-types.md).

## <a name="to-see-types-in-a-project-on-a-class-diagram"></a>So zeigen Sie Typen aus einem Projekt in einem Klassendiagramm an

1. Öffnen Sie in einem Projekt im **Projektmappen-Explorer** eine Klassendiagrammdatei (CD-Datei). Falls kein Klassendiagramm vorhanden ist, fügen Sie dem Projekt ein neues Klassendiagramm hinzu. Weitere Informationen finden Sie unter [How to: Add Class Diagrams to Projects (Vorgehensweise: Hinzufügen von Klassendiagrammen zu Projekten)](how-to-add-class-diagrams-to-projects.md).

2. Ziehen Sie vom Projekt im **Projektmappen-Explorer** eine Quellcodedatei in das Klassendiagramm.

    > [!NOTE]
    > Wenn Ihre Projektmappe ein Projekt mit Code enthält, der für mehrere Apps freigegeben ist, können Sie Dateien oder Code nur aus folgenden Quellen in ein Klassendiagramm ziehen:
    >
    > - Das App-Projekt, welches das Diagramm enthält
    > - Ein freigegebenes Projekt, das vom App-Projekt importiert wurde
    > - Ein referenziertes Projekt
    > - Eine Assembly

    Daraufhin werden die Formen, die die in der Quellcodedatei definierten Typen darstellen, im Diagramm an der Stelle angezeigt, an die Sie die Datei gezogen haben.

Sie können im Projekt enthaltene Typen auch anzeigen, indem Sie einen oder mehrere Typen vom Projektknoten in der **Klassenansicht** in das Klassendiagramm ziehen.

> [!TIP]
> Wenn die **Klassenansicht** nicht geöffnet ist, öffnen Sie **Klassenansicht** über das Menü **Ansicht**.

Wählen Sie in der **Klassenansicht** einen oder mehrere Typen aus, klicken Sie mit der rechten Maustaste auf die ausgewählten Typen, und wählen Sie **Klassendiagramm anzeigen** aus, um Typen im Diagramm an den Standardorten anzuzeigen.

> [!NOTE]
> Enthält das Projekt bereits ein geschlossenes Klassendiagramm mit dem Typ, wird das Klassendiagramm mit der Typform geöffnet. Ist in dem Projekt hingegen kein Klassendiagramm mit dem Typ enthalten, erstellt der **Klassen-Designer** im Projekt ein neues Klassendiagramm und öffnet dieses mit dem Typ.

Wenn Sie einen Typ in einem Diagramm zum ersten Mal anzeigen, wird die Form standardmäßig reduziert angezeigt. Sie können die Form erweitern, um ihren Inhalt anzuzeigen.

### <a name="to-display-the-contents-of-a-project-in-a-class-diagram"></a>So zeigen Sie den Inhalt eines Projekts in einem Klassendiagramm an

Klicken Sie im **Projektmappen-Explorer** oder in der **Klassenansicht** mit der rechten Maustaste auf das Projekt, und wählen Sie **Anzeigen** und anschließend **Klassendiagramm anzeigen** aus. Daraufhin wird ein automatisch ausgefülltes Klassendiagramm erstellt.

## <a name="see-also"></a>Weitere Informationen

- [Vorgehensweise: Anzeigen der Vererbung zwischen Typen](how-to-view-inheritance-between-types.md)
- [Vorgehensweise: Anpassen von Klassendiagrammen](how-to-customize-class-diagrams.md)
- [Anzeigen von Typen und Beziehungen](designing-and-viewing-classes-and-types.md)
