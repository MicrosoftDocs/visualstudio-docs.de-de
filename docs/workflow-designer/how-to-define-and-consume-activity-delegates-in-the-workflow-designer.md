---
title: Definieren und Nutzen von Aktivitätsdelegaten
description: In Workflow-Designer erfahren Sie, wie .NET Framework 4,5 einen Out-of-Box-Designer für die invokedelegataktivität enthält, die Sie zum Definieren und Verarbeiten von Aktivitäts Delegaten verwenden können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: 48cab69de11ce006792e0fda72245048c6897acf
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "96993275"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>Vorgehensweise: Definieren und Verarbeiten von Aktivitätsdelegaten im Workflow-Designer

.NET Framework 4,5 enthält einen Out-of-Box-Designer für die- <xref:System.Activities.Statements.InvokeDelegate> Aktivität. Der Designer kann verwendet werden, um der Aktivität Delegate zuzuweisen, die von <xref:System.Activities.ActivityDelegate>, z. B. <xref:System.Activities.ActivityAction> oder <xref:System.Activities.ActivityFunc%601>, abgeleitet werden.

## <a name="define-an-activity-delegate"></a>Definieren eines Aktivitätsdelegaten

1. Erstellen Sie ein neues Projekt für eine **Workflow Konsolenanwendung** .

   > [!NOTE]
   > Wenn die **Workflow** -Projektvorlagen nicht angezeigt werden, installieren Sie zunächst die **Windows Workflow Foundation** Komponente von Visual Studio. Ausführliche Anweisungen finden Sie unter [install Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

3. Klicken Sie mit der rechten Maustaste auf das Projekt in **Projektmappen-Explorer** und wählen Sie   >  **Neues Element** hinzufügen aus. Wählen Sie die Kategorie **Workflow** aus, und wählen Sie dann die Vorlage **Aktivitäts** Element aus. Nennen Sie die neue Aktivität **myforeach. XAML** , und wählen Sie dann **OK** aus.

   Die-Aktivität wird im Workflow-Designer geöffnet.

4. Klicken Sie im Workflow-Designer auf die Registerkarte **Argumente** .

5. Klicken Sie auf **Argument erstellen**. Benennen Sie die neuen Argument **Elemente**.

6. Wählen Sie in der Spalte **Argumenttyp** die Option **Array von [T] aus**.

7. Wählen Sie im Typbrowser **Objekt** aus, und klicken Sie dann auf **OK**.

8. Klicken Sie erneut auf **Argument erstellen** . Benennen Sie den neuen Argument **Text**. Wählen Sie in der Spalte **Richtung** für das neue Argument **Eigenschaft** aus.

9. Wählen Sie in der Spalte Argumenttyp die Option **nach Typen suchen aus** .

10. Geben Sie im Typbrowser im Feld **Typname den Namen** **ActivityAction** ein. Wählen Sie **ActivityAction \<T>** in der Strukturansicht aus. Wählen Sie in der Dropdown Liste die Option **Objekt** aus, die den Typ **ActivityAction \<Object>** dem Argument zuweist.

11. Ziehen Sie eine- <xref:System.Activities.Statements.While> Aktivität aus dem Abschnitt Ablauf **Steuerung** der Toolbox auf die Designer Oberfläche.

12. Wählen Sie die <xref:System.Activities.Statements.While> Aktivität aus, und klicken Sie auf die Registerkarte **Variablen** .

13. Wählen Sie **Variable erstellen** aus. Benennen Sie den neuen Variablen **Index**.

14. Wählen Sie in der Spalte **Variablentyp** die Option **Int32** aus. Belassen Sie den Gültigkeits **Bereich** als **while**, und die **Standard** Spalte ist leer.

15. Legen Sie die **Condition** -Eigenschaft der- <xref:System.Activities.Statements.While> Aktivität auf **Index < Items. length;** fest.

16. Ziehen <xref:System.Activities.Statements.InvokeDelegate> Sie eine Aktivität aus dem Abschnitt **primitive** der Toolbox in den **Text** der- <xref:System.Activities.Statements.While> Aktivität.

17. Wählen Sie in der Dropdown-Dropdown-Auflistung **Text** aus.

18. Klicken Sie im **Eigenschaften** Raster für die- <xref:System.Activities.Statements.InvokeDelegate> Aktivität auf die Schaltfläche **...** in der Eigenschaft Delegatargumente. 

19. Geben Sie in der Spalte **Wert** des Arguments mit dem Namen **Argument** den Wert **Items [index]** ein. Klicken Sie auf **OK** , um das Dialogfeld **delegatearguments** zu schließen.

20. Ziehen Sie eine <xref:System.Activities.Statements.Assign>-Aktivität auf die horizontale Linie unterhalb der <xref:System.Activities.Statements.InvokeDelegate>-Aktivität. Die  <xref:System.Activities.Statements.Assign> -Aktivität wird erstellt, und <xref:System.Activities.Statements.Sequence> es wird automatisch eine-Aktivität erstellt, die die beiden Aktivitäten im **Body** -Abschnitt der **myforeach** -Aktivität enthält. Die Sequenz wird benötigt, da der **Text** Abschnitt nur eine einzelne Aktivität enthalten kann. Das automatische Erstellen einer neuen <xref:System.Activities.Statements.Sequence> Aktivität ist ein neues Feature von .NET Framework 4,5.

21. Legen Sie die Eigenschaft **to** der <xref:System.Activities.Statements.Assign> Aktivität auf **Index** fest. Legen Sie die **value** -Eigenschaft der **assign** -Aktivität auf **Index + 1** fest.

    Die benutzerdefinierte **myforeach** -Aktivität ruft eine beliebige Aktivität einmal für jeden Wert auf, der über die **Items** -Auflistung an Sie übermittelt wird, wobei die Werte in der Auflistung als Eingaben für die Aktivität angegeben werden.

## <a name="use-the-custom-activity-in-a-workflow"></a>Verwenden der benutzerdefinierten Aktivität in einem Workflow

1. Erstellen Sie das Projekt, indem Sie **STRG** + **UMSCHALT** + **B** drücken.

2. Öffnen Sie **Workflow1. XAML** in **Projektmappen-Explorer** im Designer.

3. Ziehen Sie eine **myforeach** -Aktivität aus der Toolbox auf die Designer Oberfläche. Die-Aktivität befindet sich in einem Abschnitt der Toolbox mit dem gleichen Namen wie das Projekt.

4. Legen Sie die **Items** -Eigenschaft der **myforeach** -Aktivität auf **New Object [] {1, "ABC"}** fest.

5. Ziehen Sie eine- <xref:System.Activities.Statements.WriteLine> Aktivität aus dem Abschnitt **primitive** der Toolbox in den Abschnitt Delegat **: Body** der **myforeach** -Aktivität.

6. Legen Sie die **Text** -Eigenschaft der- <xref:System.Activities.Statements.WriteLine> Aktivität auf **Argument.-Zeichenfolge ()** fest.

Beim Ausführen des Workflows wird in der-Konsole die folgende Ausgabe angezeigt:

**1** 
 **ABC**
