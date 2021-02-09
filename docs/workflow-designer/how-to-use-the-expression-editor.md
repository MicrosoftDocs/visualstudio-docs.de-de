---
title: 'Workflow-Designer: Gewusst wie: Verwenden des Ausdrucks-Editors'
description: Erfahren Sie, wie der Ausdrucks-Editor ein Workflow-Designer Steuerelement ist, das Sie in vielen Workflow Aktivitäten zum eingeben und Auswerten von Ausdrücken verwenden können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 192418439bc25e6ac1b969483c0c48a030caa024
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894074"
---
# <a name="how-to-use-the-expression-editor"></a>Vorgehensweise: Verwenden des Ausdrucks-Editors

Der Ausdrucks-Editor ist ein Workflow-Designer Steuerelement, das in vielen Workflow Aktivitäten zum eingeben und Auswerten von Ausdrücken verwendet wird. Der Ausdrucks-Editor bietet eine vollständige IDE-Bearbeitungsumgebung, einschließlich IntelliSense, farbige Farbgebung, paramInfo, Fehler Wellenlinien, zu anderen Features. Der Compiler überprüft den Ausdruck, nachdem er eingegeben wurde. Wenn der Ausdruck ungültig ist, wird ein Fehlersymbol angezeigt. Der Editor kann auch als Dialogfeld **Ausdrucks-Editor** geöffnet werden.

Ausdrücke sind an Argumente oder Eigenschaften gebundene literale Werte oder Visual Basic-Code. Sie enthalten Wert Elemente (z. b. Variablen, Konstanten, Literale, Eigenschaften), die mit Vorgängen kombiniert werden, um einen neuen Wert zu erhalten. Ausdrücke werden mit VB.NET-Syntax geschrieben, auch wenn sie in einem in C# geschriebenen Programm verwendet werden. Dies bedeutet, dass die Groß-/Kleinschreibung keine Rolle spielt, dass der Vergleich mit einem einzelnen Gleichheitszeichen ("=" anstelle von "= =") erfolgt. die booleschen Operatoren sind die Wörter "and" und "or" anstelle der Symbole "&&" und "| |", und anstelle von **null** wird **nichts** verwendet. Weitere Informationen zu Ausdrücken und Operatoren in Visual Basic und einige Beispiele finden Sie unter [Operatoren und Ausdrücke in Visual Basic](/previous-versions/visualstudio/visual-studio-2010/a1w3te48(v=vs.100)).

Der **Ausdrucks-Editor** verhält sich wie folgt:

- Wenn der Ausdrucks-Editor nicht im Fokus ist, sieht er wie ein reguläres TextBlock-Steuerelement aus.

- Sobald der Fokus auf dem Ausdrucks-Editor ist, sieht er wie das Ausdrucks-Editor-Steuerelement aus und verhält sich wie dieses. Nachdem der Fokus verloren ist, sieht der Ausdrucks-Editor wieder wie ein regulärer TextBlock aus.

- Wenn Sie in einem neu gehosteten Workflow-Designer den Fokus auf den Ausdrucks-Editor legen, dann verhält er sich wie ein Textfeld. Wenn der Ausdrucks-Editor im neu gehosteten Workflow-Designer den Fokus verliert, sieht er wieder wie ein regulärer TextBlock aus.

> [!NOTE]
> IntelliSense für den Ausdrucks-Editor ist nur in Visual Studio verfügbar. Sowohl in den Visual Studio-als auch in den neu gehosteten Szenarien überprüft der Compiler den Ausdruck, nachdem er eingegeben wurde, und der Ausdrucks-Editor zeigt ein Fehler Symbol an, wenn der Ausdruck ungültig ist.

## <a name="use-the-expression-editor"></a>Verwenden des Ausdrucks-Editors

1. Öffnen Sie in Visual Studio ein neues oder vorhandenes Workflow Projekt.

2. Fügen Sie dem Workflow z. B. die <xref:System.Activities.Statements.Assign>-Aktivität hinzu.

    > [!NOTE]
    > Mehrere Workflowaktivitäten verfügen über Ausdrucks-Editoren. Ausdrucks-TextBlock-Steuerelemente werden auch im Variablen-Designer, Argument-Designer und dem dynamischen Argument-Designer angezeigt. Die <xref:System.Activities.Statements.Assign>-Aktivität wird als Beispiel verwendet.

3. Klicken Sie im Aktivitätsdesigner für die <xref:System.Activities.Statements.Assign>-Aktivität auf den linken Ausdrucks-Editor.

     Die grauen Wasserzeichen Zeichenfolgen **\<To>** und **\<Enter a VB Expression>** sind die Standardtext Zeichenfolgen für Ausdrucks-Editoren in der- <xref:System.Activities.Statements.Assign> Aktivität.

4. Geben Sie einen Ausdruck ein. Wenn Sie eine Zeichenfolge eingeben, setzen Sie diese unbedingt in Anführungszeichen. Wenn Sie das Ausdrucksargument an eine Variable zu binden, lassen Sie die Anführungszeichen weg.

     Wenn Sie fertig sind, wählen Sie eine Region oder einen Bereich außerhalb des Ausdrucks-Editors aus, um den Fokus auf einen anderen Teil des Designers zu verschieben. Das Verschieben des Fokus bewirkt, dass der Compiler den Ausdruck wie zuvor beschrieben überprüft.

     Eine alternative Möglichkeit, einen Ausdruck einzugeben oder zu bearbeiten, ist das Klicken auf die Auslassungs Punkte neben dem Eigenschaftsnamen im Eigenschaften Raster. Durch Auswahl der Auslassungs Punkte wird der **Ausdrucks-Editor** als Dialogfeld geöffnet.

## <a name="see-also"></a>Weitere Informationen

- <xref:System.Activities.Presentation.View.ExpressionTextBox>
