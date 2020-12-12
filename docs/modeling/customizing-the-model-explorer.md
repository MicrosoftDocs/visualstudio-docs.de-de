---
title: Anpassen des Modell-Explorers
description: Erfahren Sie, wie Sie die Darstellung und das Verhalten des Explorers für Ihren domänenspezifischen sprach Designer ändern können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.explorerbehavior
helpviewer_keywords:
- Domain-Specific Language Tools, Domain-Specific Language Explorer
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d4bdfcea6cbc54fd620e9aacbdc6250493ca426
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362889"
---
# <a name="customizing-the-model-explorer"></a>Anpassen des Modell-Explorers
Sie können das Aussehen und Verhalten des Explorers für Ihren domänenspezifischen sprach Designer wie folgt ändern:

- Ändern Sie den Fenstertitel.

- Ändern Sie das Registerkarten Symbol.

- Ändern Sie die Symbole für Knoten.

- Knoten ausblenden.

## <a name="changing-the-window-title"></a>Ändern des Fenster Titels
 Um den Fenstertitel des generierten Explorers zu ändern, wählen Sie im DSL- **Explorer** **Explorer-Verhalten** aus, und legen Sie dann im **Eigenschaften** Fenster die **Title** -Eigenschaft auf den gewünschten Titel fest.

## <a name="changing-the-tab-icon"></a>Ändern des Registerkarten Symbols
 Um das Registerkarten Symbol für den Explorer zu ändern, verwenden Sie ein 16x16-Pixel-Symbol in einer BMP-Datei. Fügen Sie die Symbol Datei in den Ordner \dslpackage\resources\ ein, und ändern Sie dann den Dateinamen in **ModelExplorerToolWindowBitmaps.bmp**. Beispielsweise können Sie die Visual Studio-Symbol Datei "Setup. ico" in das BMP-Format ändern und in " **DSLLanguageName\DslPackage\Resources\ModelExplorerToolWindowBitmaps.bmp**" umbenennen. Der generierte Designer zeigt dieses Symbol auf der Registerkarte Ihres Explorers an, wenn es mit **Projektmappen-Explorer** angedockt wird.

## <a name="setting-custom-icons-on-explorer-nodes"></a>Festlegen von benutzerdefinierten Symbolen auf Explorer-Knoten
 Sie können Knoten im Explorer anpassen, indem Sie die Einstellungen für den Explorer-Knoten verwenden. Im folgenden Verfahren wird gezeigt, wie ein Symbol einem Knoten hinzugefügt wird.

#### <a name="to-add-an-icon-to-an-explorer-node"></a>So fügen Sie einem Explorer-Knoten ein Symbol hinzu

1. Erstellen Sie eine Projekt Mappe [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] mithilfe der Lösungs Vorlage für den Task Fluss.

2. Fügen Sie eine BMP-Datei mit einem 16x16-Pixel-Symbol im Ordner " **dsl\resources** " in der Projekt Mappe ein.

3. Klicken Sie im **DSL-Explorer** mit der rechten Maustaste auf Explorer- **Verhalten** und dann auf **neue Explorer-Knoten Einstellungen hinzufügen**.

    Der Knoten **explorernodesettings** wird unter dem Knoten **Einstellungen für benutzerdefinierte Knoten** angezeigt.

4. Wählen Sie **explorernodesettings** aus, und legen Sie dann im Fenster **Eigenschaften** die **Klasse** auf **Actor** fest.

5. Legen **Sie das Symbol fest,** das auf dem Pfad der Symbol Datei angezeigt werden soll.

6. Transformieren Sie alle Vorlagen, und erstellen Sie die Projekt Mappe, und führen Sie Sie aus.

7. Öffnen Sie im generierten Designer das Beispiel Diagramm.

    Im Explorer sollten drei **Actor** -Knoten mit dem Symbol angezeigt werden.

> [!NOTE]
> Wenn Sie für ein beliebiges Element, das im generierten Explorer angezeigt wird, ein Knoten Symbol festgelegt haben, wird in allen Explorer-Knoten das Symbol angezeigt. Wenn kein Symbol festgelegt wurde, wird auf den Knoten das Standard Symbol angezeigt.

## <a name="changing-the-name-displayed-on-an-explorer-node"></a>Ändern des auf einem Explorer-Knoten angezeigten Namens
 Sie können ändern, wie die Namen von Modellelementen im Explorer angezeigt werden. Im folgenden Verfahren wird gezeigt, wie der Name der **Aufgabe** angezeigt wird, auf die von einem **Kommentar** im Kommentar Knoten verwiesen wird.

#### <a name="to-display-a-property"></a>So zeigen Sie eine Eigenschaft an

1. Öffnen Sie die Projekt Mappe, die Sie im vorherigen Verfahren erstellt haben.

2. Stellen Sie sicher, dass der **Kommentar** nur auf eine einzelne Domänen Klasse verweist, indem Sie die Multiplizität der Rolle mit den Eigenschafts namens **Subjekten** auf 0.. 1 festlegen. Der Eigenschaftsname sollte **Betreff** lauten, und der Beziehungs Name sollte **commentreferencessubject** werden.

3. Klicken Sie im **DSL-Explorer** mit der rechten Maustaste auf Explorer- **Verhalten** und dann auf **neue Explorer-Knoten Einstellungen hinzufügen**.

     Der Knoten **explorernodesettings** wird unter dem Knoten **Einstellungen für benutzerdefinierte Knoten** angezeigt.

4. Wählen Sie **explorernodesettings** aus, und legen Sie dann im Fenster **Eigenschaften** die **Klasse** auf **comment** fest.

5. Klicken Sie mit der rechten Maustaste auf den **Kommentar** Knoten, und klicken Sie dann auf **neuen Eigenschaften Pfad hinzufügen**.

     Ein neuer Knoten mit dem Namen " **Eigenschaft**" wird angezeigt.

6. Wählen Sie die **angezeigte Eigenschaft** aus, und klicken Sie dann im Fenster **Eigenschaften** auf das Feld Wert von **Pfad zur Eigenschaft**. Wählen Sie **comment** und dann **commentreferencessubject** und dann **flowelements** aus. Der resultierende Pfad sollte " **commentreferencessubject. Subject/!" ähneln. Betreff**.

7. Wählen Sie im Feld Wert der **Eigenschaft** **Name** aus.

8. Transformieren Sie alle Vorlagen, und erstellen Sie die Projekt Mappe, und führen Sie Sie aus.

9. Öffnen Sie im generierten Designer das Beispiel Diagramm.

10. Zeichnen Sie einen **kommentarconnector** zwischen dem comment-Element und dem **task1** -Element im Diagramm.

     Im Explorer-Knoten sollte der Kommentar als **task1** angezeigt werden.

## <a name="hiding-nodes"></a>Ausblenden von Knoten
 Sie können einen Knoten im Explorer ausblenden, indem Sie dessen Pfad zum Knoten **verborgene Knoten** des DSL- **Explorers** hinzufügen. Im folgenden Verfahren wird gezeigt, wie Sie **Kommentar** Knoten ausblenden können.

#### <a name="to-hide-an-explorer-node"></a>So blenden Sie einen Explorer-Knoten aus

1. Öffnen Sie die Projekt Mappe, die Sie im vorherigen Verfahren erstellt haben.

2. Klicken Sie im **DSL-Explorer** mit der rechten Maustaste auf Explorer- **Verhalten** und dann auf **neuen Domänen Pfad hinzufügen**.

     Ein **Domänen Pfad** Knoten wird unter **verborgene Knoten** angezeigt.

3. Wählen Sie **Domänen Pfad** aus, und klicken Sie dann im Fenster **Eigenschaften** auf das Feld Wert der **path-Definition**. Wählen Sie **flowgraph** und dann **flowgraphhascomments** aus. Der resultierende Pfad sollte " **flowgraphhascomments. comments** " ähneln.

4. Transformieren Sie alle Vorlagen, und erstellen Sie die Projekt Mappe, und führen Sie Sie aus.

5. Öffnen Sie im generierten Designer das Beispiel Diagramm.

     Im Explorer sollte nur ein **Actors** -Knoten angezeigt werden, und der Knoten **comments** sollte nicht angezeigt werden.

## <a name="see-also"></a>Siehe auch

- [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](/previous-versions/bb126564(v=vs.100))