---
title: 'Workflow-Designer: Gewusst wie: Hinzufügen von Aktivitäten zur Toolbox'
description: Fügen Sie der Toolbox in der Projekt Mappe Aktivitäten hinzu, indem Sie Sie aus dem aktuellen Projekt hinzufügen oder von einem anderen Projekt aus auf Sie verweisen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: b3a8a785-5928-457a-8a50-30267e29503d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d2330392ace27a913870e7c7448976d1cae46958
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94437943"
---
# <a name="how-to-add-activities-to-the-toolbox"></a>Gewusst wie: Hinzufügen von Aktivitäten zur Toolbox

Aktivitäten können auf verschiedene Arten der **Toolbox** in der Projekt Mappe hinzugefügt werden. Sie können sie innerhalb des aktuellen Projekts hinzufügen oder durch einen Verweis auf ein anderes Projekt oder eine andere Assembly.

## <a name="to-add-an-activity-from-within-your-current-project"></a>So fügen Sie innerhalb des aktuellen Projekts eine Aktivität hinzu

1. Fügen Sie dem aktuellen Workflowprojekt eine neue benutzerdefinierte Aktivität hinzu. Weitere Informationen zum Hinzufügen einer neuen benutzerdefinierten Aktivität zum Projekt finden Sie unter Gewusst [wie: Hinzufügen eines neuen Elements zu einem Workflow Projekt](../workflow-designer/how-to-add-a-new-item-to-a-workflow-project.md).

2. Fügen Sie der Aktivität benutzerdefinierte Logik hinzu.

3. Erstellen Sie das Projekt. Wenn der Buildvorgang erfolgreich war, wird eine neue Kategorie mit dem Namen "" in der **Toolbox** \<*project name*> mit der benutzerdefinierten Aktivität angezeigt, die in dieser Kategorie enthalten ist.

    > [!NOTE]
    > Wenn die Toolbox zurückgesetzt wird, werden benutzerdefinierte Aktivitäten entfernt. Dies gilt auch, wenn die Projektmappe erneut erstellt wird. Zum erneuten Auffüllen der Toolbox mit benutzerdefinierten Aktivitäten nach dem Zurücksetzen starten Sie Visual Studio neu.

    > [!NOTE]
    > Die Toolbox kann nur eine Aktivität mit einem bestimmten Namen anzeigen. Wenn zwei Aktivitäten aus verschiedenen Assemblys denselben Klassennamen haben, wird nur eine anzeigt.

    > [!NOTE]
    > Die Anwendungsdomäne wird von Editorinstanzen gemeinsam verwendet. Wenn statische Variablen verwendet werden, werden sie von den Editorinstanzen auch gemeinsam verwendet. Wenn dieses Verhalten nicht erwünscht ist, sollte ein Dienst verwendet werden, um Variableninstanzen nachzuverfolgen. Informationen zur Verwendung von Diensten innerhalb des Designers finden [Sie unter Verwenden des Kontext Bearbeitungskontexts](/dotnet/framework/windows-workflow-foundation/using-the-modelitem-editing-context) .

## <a name="to-add-an-activity-from-within-a-different-project"></a>So fügen eine Aktivität aus einem anderen Projekt hinzu

1. Öffnen Sie eine Projektmappe, die mindestens ein Workflowprojekt und entweder ein benutzerdefiniertes Aktivitätsbibliotheksprojekt oder ein anderes Workflowprojekt enthält, in dem eine benutzerdefinierte Aktivität definiert wird.

2. Erstellen Sie beide Projekte. Wenn die Builds erfolgreich waren, wird eine neue Kategorie mit dem Namen "" in der **Toolbox** \<*project name*> mit der benutzerdefinierten Aktivität angezeigt, die in dieser Kategorie enthalten ist.

## <a name="to-add-an-activity-to-the-toolbox-from-an-assembly"></a>So fügen Sie eine Aktivität aus einer Assembly der Toolbox hinzu

1. Öffnen Sie eine Workflowprojektmappe.

2. Wählen Sie **im Menü** Extras die Option **Toolbox Elemente** auswählen aus.

3. Wählen Sie im Dialogfeld **Toolbox Elemente auswählen** die Registerkarte **System. Activities-Komponenten** aus, und klicken Sie dann auf **Durchsuchen** , um zu der Assembly mit der benutzerdefinierten Aktivität zu navigieren, die Sie hinzufügen möchten.

4. Wählen Sie die Assembly aus, und klicken Sie auf **OK**. Die benutzerdefinierte Aktivitätskomponente wird der Liste der Komponenten hinzugefügt und automatisch ausgewählt.

    1. Klicken Sie auf **OK** , um das Dialogfeld zu schließen.

5. Um die Toolbox anzuzeigen, wählen Sie im Menü **Ansicht** die Option **Toolbox** aus.

6. Die benutzerdefinierte Aktivität wird in der **Toolbox** unter der Kategorie angezeigt, die sich vor dem Hinzufügen des Elements im Fokus befand. Wenn z. b. die Kategorie **Allgemein** in der **Toolbox** vor dem Hinzufügen des Toolbox Elements ausgewählt wurde, wird die Aktivität unter der Kategorie **Allgemein** angezeigt.

## <a name="see-also"></a>Siehe auch

- [Verwenden des Workflow-Designers](developing-applications-with-the-workflow-designer.md)
