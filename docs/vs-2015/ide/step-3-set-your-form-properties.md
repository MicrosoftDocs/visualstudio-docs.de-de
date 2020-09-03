---
title: 'Schritt 3: Festlegen der Formulareigenschaften | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 634ef037-1525-48c8-ac7f-abf04be69376
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f05e91c13b1a9c52b5afad6942e5847643aa9490
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851551"
---
# <a name="step-3-set-your-form-properties"></a>Schritt 3: Festlegen der Formulareigenschaften
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Als Nächstes verwenden Sie das **Eigenschaftenfenster**, um das Aussehen des Formulars zu ändern.

 ![Link zu Video](../data-tools/media/playvideo.gif "Wiedergeben") Eine videoversion dieses Themas finden Sie im Video 1 zum [Tutorial 1: Erstellen eines Bild Anzeige Programms in Visual Basic-Video 1](https://msdn.microsoft.com/vbasic/gg315352.aspx) oder [Tutorial 1: Erstellen eines Bild Anzeige Programms in c#](https://msdn.microsoft.com/vcsharp/gg278409.aspx). Diese Videos verwenden eine frühere Version von Visual Studio, sodass Menübefehle und andere Benutzeroberflächenelemente geringfügig abweichen können. Allerdings funktionieren die Konzepte und Prozeduren in der aktuellen Version von Visual Studio auf ähnliche Weise.

### <a name="to-set-your-form-properties"></a>So legen Sie die Formulareigenschaften fest

1. Stellen Sie sicher, dass Sie den Windows Forms-Designer anschauen. Wählen Sie in der integrierten Entwicklungsumgebung (IDE) von Visual Studio die Registerkarte **Form1.cs [Design]** (oder die Registerkarte **Form1.vb [Design]** in Visual Basic) aus.

2. Wählen Sie im Formular **Form1** eine beliebige Stelle, um es auszuwählen. Betrachten Sie das **Eigenschaftenfenster**, das jetzt die Eigenschaften für das Formular enthalten sollte. Formulare verfügen über verschiedene Eigenschaften. Sie können z. B. die Vordergrund- und Hintergrundfarbe, den Titeltext, der oben im Formular erscheint, die Größe des Formulars und andere Eigenschaften festlegen.

   > [!NOTE]
   > Wenn das **Eigenschaftenfenster** nicht angezeigt wird, beenden Sie das Programm, indem Sie auf der Symbolleiste die quadratische Schaltfläche **Debuggen beenden** auswählen, oder schließen Sie das Fenster einfach. Wenn das Programm beendet wird und das **Eigenschaftenfenster** immer noch nicht angezeigt wird, wählen Sie in der Menüleiste **Ansicht**, **Eigenschaftenfenster** aus.

3. Suchen Sie nach dem Auswählen des Formulars die Eigenschaft **Text** im Fenster **Eigenschaften**. Je nachdem, wie die Liste sortiert wird, müssen Sie möglicherweise einen Bildlauf nach unten durchführen. Wählen Sie **Text** aus, geben Sie **Picture Viewer** ein, und wählen Sie dann die EINGABETASTE aus.  In der Titelleiste des Formulars sollte jetzt der Text **Picture Viewer** angezeigt werden, und das **Eigenschaftenfenster** sollte wie im folgenden Bild aussehen.

    ![Eigenschaftenfenster](../ide/media/express-edittextproperty.png "Express_EditTextProperty") Eigenschaftenfenster

   > [!NOTE]
   > Eigenschaften können in einer kategorisierten oder alphabetischen Ansicht angeordnet sein. Sie können mit den Schaltflächen im **Eigenschaftenfenster** zwischen diesen beiden Ansichten umschalten. In diesem Lernprogramm ist es einfacher, in der alphabetischen Ansicht nach Eigenschaften zu suchen.

4. Kehren Sie zum Windows Forms-Designer zurück. Wählen Sie unten rechts den Ziehpunkt des Formulars aus. Dies ist ein kleines, weißes Quadrat, das wie folgt aussieht.

    ![Ziehpunkt](../ide/media/express-bottomrt-drag.png "Express_BottomRT_Drag") Ziehpunkt

    Ziehen Sie am Ziehpunkt, um die Größe des Formulars so zu ändern, dass es breiter und ein bisschen größer ist.

5. Im **Eigenschaftenfenster** können Sie feststellen, dass sich der Wert der Eigenschaft **Size** geändert hat. Die Eigenschaft **Size** ändert sich jedes Mal, wenn Sie die Größe des Formulars ändern. Versuchen Sie, die Formulargröße durch Ziehen am Ziehpunkt in eine Größe von ca. 550, 350 zu ändern (muss nicht exakt sein). Diese Größe eignet sich gut für dieses Projekt. Alternativ können Sie die Werte direkt in der Eigenschaft **Size** eingeben und dann die EINGABETASTE auswählen.

6. Führen Sie das Programm erneut aus. Denken Sie daran, dass Sie eine der folgenden Methoden verwenden können, um das Programm auszuführen.

   - Drücken Sie die Taste **F5**.

   - Klicken Sie in der Menüleiste auf **Debuggen** und dann auf **Debuggen starten**.

   - Wählen Sie auf der Symbolleiste die Schaltfläche **Debuggen starten** aus, die wie folgt aussieht.

      ![Symbolleisten Schaltfläche "Debugging](../ide/media/express-icondebug.png "Express_IconDebug") Symbolleisten Schaltfläche "Debugging

     Wie bereits zuvor geschehen, erstellt die IDE das Programm und führt es aus, und ein Fenster wird angezeigt.

7. Bevor Sie mit dem nächsten Schritt fortfahren, beenden Sie das Programm, da die IDE Änderungen an einem ausgeführten Programm nicht zulässt. Denken Sie daran, dass Sie eine der folgenden Methoden verwenden können, um das Programm zu beenden.

   - Wählen Sie auf der Symbolleiste die Schaltfläche **Debuggen beenden** aus.

   - Wählen Sie auf der Menüleiste **Debuggen** und dann **Debuggen beenden** aus.

   - Schließen Sie das **Form1**-Fenster, indem Sie auf das X in der oberen rechten Ecke des Fensters klicken.

### <a name="to-continue-or-review"></a>So fahren Sie fort oder überprüfen die Angaben

- Klicken Sie auf [Schritt 4: Erstellen des Layouts für das Formular mit einem TableLayoutPanel-Steuerelement](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md), um mit dem nächsten Schritt des Tutorials fortzufahren.

- Wie Sie zum vorherigen Schritt des Tutorials zurückzukehren, erfahren Sie unter [Schritt 2: Ausführen des Programms](../ide/step-2-run-your-program.md).
