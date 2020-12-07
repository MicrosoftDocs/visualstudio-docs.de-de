---
title: 'Schritt 2: Hinzufügen eines zufällig ausgewählten Objekts und einer Liste von Symbolen'
description: Hier lernen Sie, wie Sie einige übereinstimmende Symbole für das Spiel erstellen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 95faea28-eddc-4cfa-95fb-3b34b5a976d7
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1018b390f6ebbf67fab88554aa85fe6a8ecec88d
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480693"
---
# <a name="step-2-add-a-random-object-and-a-list-of-icons"></a>Schritt 2: Hinzufügen eines zufällig ausgewählten Objekts und einer Liste von Symbolen

In diesem Schritt erstellen Sie einen Satz übereinstimmender Symbole für das Spiel. Jedes Symbol wird zwei zufällig ausgewählten Zellen im TableLayoutPanel auf dem Formular hinzugefügt. Sie verwenden zwei `new`-Anweisungen, um zwei Objekte zu erstellen. Das erste Objekt ist ein <xref:System.Random>-Objekt, wie Sie es auch im Mathematik-Quiz verwendet haben. Es wird in diesem Code verwendet, um Zellen im TableLayoutPanel zufällig auszuwählen. Das zweite Objekt ist möglicherweise neu für Sie – es ist ein <xref:System.Collections.Generic.List%601>-Objekt, das verwendet wird, um die zufällig ausgewählten Symbole zu speichern.

## <a name="to-add-a-random-object-and-a-list-of-icons"></a>So fügen Sie ein zufällig ausgewähltes Objekt und eine Liste von Symbolen hinzu

1. Wählen Sie *Form1.cs* im **Projektmappen-Explorer** aus, wenn Sie C# verwenden, oder *Form1.vb*, wenn Sie Visual Basic verwenden. Klicken Sie dann in der Menüleiste auf **Ansicht** > **Code**. Alternativ können Sie die Taste **F7** drücken oder im **Projektmappen-Explorer** auf **Form1** doppelklicken.

     Dadurch wird das Codemodul für Form1 angezeigt.

2. Fügen Sie im vorhandenen Code den folgenden Code hinzu.

     [!code-csharp[VbExpressTutorial4Step2_3_4#1](../ide/codesnippet/CSharp/step-2-add-a-random-object-and-a-list-of-icons_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#1](../ide/codesnippet/VisualBasic/step-2-add-a-random-object-and-a-list-of-icons_1.vb)]

      > [!IMPORTANT]
      > Verwenden Sie das Programmiersprachensteuerelement oben rechts auf dieser Seite, um entweder den C#-Codeausschnitt oder den Visual Basic-Codeausschnitt anzuzeigen.<br><br>![Programmiersprachensteuerelement auf docs.microsoft.com](../ide/media/docs-programming-language-control.png)

      Achten Sie bei der Verwendung von C#-Code darauf, dass Sie den Code nach der öffnenden geschweiften Klammer und direkt nach der Klassendeklaration (`public partial class Form1 : Form`) einfügen. Sofern Sie Visual Basic verwenden, müssen Sie den Code direkt nach der Klassendeklaration (`Public Class Form1`) einfügen.

3. Beim Hinzufügen des Listenobjekts öffnet sich das **IntelliSense**-Fenster. Das folgende Beispiel ist ein C#-Beispiel, aber es wird ein ähnlicher Text angezeigt, wenn Sie eine Liste unter Visual Basic hinzufügen.

     ![Anzeige des Click-Ereignisses im Eigenschaftenfenster](../ide/media/express_listintellisense.png)<br/>**_IntelliSense_*-Fenster*

    > [!NOTE]
    > Das IntelliSense-Fenster wird nur angezeigt, wenn Sie Code manuell eingeben. Beim Einfügen von kopiertem Code wird es nicht angezeigt.

     Der Code (samt Kommentar) ist einfacher zu verstehen, wenn Sie sich diesen in kleinen Abschnitten ansehen. Sie können Listenobjekte in Programmen verwenden, um viele verschiedene Elementtypen im Auge zu behalten. Eine Liste kann Zahlen, Wahr/Falsch-Werte, Text oder andere Objekte enthalten. Sie können auch ein Listenobjekt verwenden, das andere Listenobjekte enthält. Die Bestandteile der Liste werden als „Elemente“ bezeichnet, und jede Liste enthält nur einen Typ von Element. Eine Liste für Zahlen kann somit nur Zahlen enthalten. Sie können einer solchen Liste keinen Text hinzufügen. Ebenso ist es nicht möglich, einer Liste mit Wahr/Falsch-Werten Zahlen hinzuzufügen.

     Wenn Sie ein `List`-Objekt mit einer `new`-Anweisung erstellen, müssen Sie die Art von Daten angeben, die in der Liste gespeichert werden soll. Aus diesem Grund zeigt die QuickInfo oben im **IntelliSense**-Fenster den Typ der Elemente in der Liste an. Dies bedeuten auch `List<string>` (in C#) und `List(Of String)` (in Visual Basic): Hierbei handelt es sich um ein `List`-Objekt, das Elemente des Datentyps `string` enthält. Das Programm speichert Text als Zeichenfolge. Diese Information steht in der QuickInfo rechts im **IntelliSense**-Fenster.

4. Überlegen Sie, warum in Visual Basic zuerst ein temporäres Array erstellt werden muss, während die Liste in C# mit einer Anweisung erstellt werden kann. Der Grund ist, dass die Sprache C# über *Auflistungsinitialisierer* verfügt, mit deren Hilfe die Liste zur Aufnahme von Werten vorbereitet wird. In Visual Basic können Sie einen Auflistungsinitialisierer verwenden. Um jedoch die Kompatibilität mit der früheren Version von Visual Basic sicherzustellen, empfiehlt sich die Verwendung des oben angegebenen Codes.

     Wenn Sie einen Auflistungsinitialisierer mit einer `new`-Anweisung verwenden, füllt das Programm das neue Listenobjekt nach seiner Erstellung mit dem Inhalt, der zwischen den geschweiften Klammern angegeben ist. In diesem Fall erhalten Sie eine Liste mit Zeichenfolgen namens „icons“ (Symbole). Diese Liste wird so initialisiert, dass sie 16 Zeichenfolgen enthält. Jede dieser Zeichenfolgen ist ein einzelner Buchstabe. Die Buchstaben entsprechen jeweils den Symbolen, die unter den Bezeichnungen angezeigt werden. Das Spiel verfügt also über ein Paar Ausrufezeichen, ein Paar von N-Buchstaben, ein Paar Kommas usw. (Wenn für diese Zeichen die Schriftart Webdings festgelegt wird, werden sie als Symbole dargestellt, beispielsweise als Bus, Fahrrad, Spinne usw.) Das Listenobjekt verfügt insgesamt über 16 Zeichenfolgen, eine für jede Zelle im TableLayoutPanel-Steuerelement.

    > [!NOTE]
    > In Visual Basic erhalten Sie das gleiche Ergebnis, aber die Zeichenfolgen werden zuerst in ein temporäres Array eingefügt, das dann in ein Listenobjekt konvertiert wird. Ein Array ähnelt einer Liste, aber Arrays werden z. B. mit einer festen Größe erstellt. Listen können kürzer oder länger werden, was für dieses Programm wichtig ist.

## <a name="to-continue-or-review"></a>So fahren Sie fort oder überprüfen die Angaben

- Den nächsten Schritt des Tutorials finden Sie unter [**Schritt 3: Zuweisen eines zufälligen Symbols zu jeder Bezeichnung**](../ide/step-3-assign-a-random-icon-to-each-label.md).

- Den vorherigen Schritt des Tutorials finden Sie unter [Schritt 1: Erstellen eines Projekts und Hinzufügen einer Tabelle zum Formular](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md).
