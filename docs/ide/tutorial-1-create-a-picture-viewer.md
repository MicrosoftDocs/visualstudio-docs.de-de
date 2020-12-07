---
title: 'Tutorial 1: Erstellen eines Bildanzeigeprogramms'
description: Hier erfahren Sie, wie Sie eine App erstellen, die ein Bild aus einer Datei lädt und in einem Fenster anzeigt.
ms.custom: SEO-VS-2020
ms.date: 10/16/2019
ms.assetid: 3071d6df-2b2f-4e95-ab68-bef727323136
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c0eea844b04cbe8ba261fd4d65a6d21fb99aa4b
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479133"
---
# <a name="tutorial-1-create-a-picture-viewer"></a>Tutorial 1: Erstellen eines Bildanzeigeprogramms

In diesem Tutorial erstellen Sie eine App, die ein Bild aus einer Datei lädt und in einem Fenster anzeigt. Sie erfahren, wie Sie mithilfe des **Windows Forms-Designers** Steuerelemente, z. B. Schaltflächen und Bildfelder, auf das Formular ziehen, ihre Eigenschaften festlegen und mithilfe von Containern die Größe des Formulars reibungslos ändern können. Sie fangen auch an, Code zu schreiben.

> [!NOTE]
> In diesem Tutorial werden sowohl C# als auch Visual Basic behandelt. Achten Sie also auf die entsprechenden Informationen zu der Programmiersprache, die Sie verwenden.

In diesem Tutorial werden Sie durch die folgenden Aufgaben geführt:

* Erstellen Sie ein neues Projekt.

* Testen (Debuggen) einer Anwendung

* Hinzufügen grundlegender Steuerelemente, z. B. Kontrollkästchen und Schaltflächen, zu einem Formular

* Positionieren von Steuerelementen auf einem Formular mithilfe von Layouts

* Hinzufügen der Dialogfelder **Datei öffnen** und **Farbe** zu einem Formular.

* Schreiben von Code mithilfe von IntelliSense und Codeausschnitten

* Schreiben von Ereignishandlermethoden

Anschließend sollte Ihre App in etwa wie in der folgenden Abbildung aussehen:

![Picture Viewer-App, die Sie in diesem Tutorial erstellen](../ide/media/express_pictureviewerdone.png)

## <a name="tutorial-links"></a>Tutoriallinks

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[Schritt 1: Erstellen eines Windows Forms-App-Projekts](../ide/step-1-create-a-windows-forms-application-project.md)|Erstellen Sie zunächst ein Windows Forms-App-Projekt.|
|[Schritt 2: Ausführen Ihrer Picture Viewer-App](../ide/step-2-run-your-program.md)|Führen Sie das Windows Forms-App-Projekt aus, das Sie im vorherigen Schritt erstellt haben.|
|[Schritt 3: Festlegen der Formulareigenschaften](../ide/step-3-set-your-form-properties.md)|Ändern Sie das Aussehen des Formulars mit dem **Eigenschaftenfenster**.|
|[Schritt 4: Erstellen eines Layouts für das Formular mit einem TableLayoutPanel-Steuerelement](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)|Fügen Sie Ihrem Formular ein `TableLayoutPanel`-Steuerelement hinzu.|
|[Schritt 5: Hinzufügen von Steuerelementen zum Formular](../ide/step-5-add-controls-to-your-form.md)|Fügen Sie dem Formular Steuerelemente hinzu, z.B. ein `PictureBox`-Steuerelement und ein `CheckBox`-Steuerelement. Fügen Sie dem Formular Schaltflächen hinzu.|
|[Schritt 6: Benennen der Schaltflächen-Steuerelemente](../ide/step-6-name-your-button-controls.md)|Benennen Sie die Schaltflächen um, damit die Namen aussagekräftiger sind.|
|[Schritt 7: Hinzufügen von Dialogfeldkomponenten zum Formular](../ide/step-7-add-dialog-components-to-your-form.md)|Fügen Sie dem Formular jeweils eine der Komponenten `OpenFileDialog` und `ColorDialog` hinzu.|
|[Schritt 8: Schreiben von Code für den Ereignishandler der Schaltfläche „Bild anzeigen“](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)|Schreiben Sie Code mit dem IntelliSense-Tool.|
|[Schritt 9: Überprüfen, Kommentieren und Testen des Codes](../ide/step-9-review-comment-and-test-your-code.md)|Prüfen und testen Sie den Code. Fügen Sie bei Bedarf Kommentare hinzu.|
|[Schritt 10: Schreiben von Code für zusätzliche Schaltflächen und ein Kontrollkästchen](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)|Schreiben Sie mithilfe von IntelliSense Code, damit andere Schaltflächen und ein Kontrollkästchen funktionieren.|
|[Schritt 11: Ausführen der App und Ausprobieren weiterer Features](../ide/step-11-run-your-program-and-try-other-features.md)|Führen Sie Ihre App aus, und legen Sie die Hintergrundfarbe fest. Probieren Sie andere Funktionen aus. Ändern Sie z. B. Farben, Schriftarten und Rahmen.|

Es stehen auch umfangreiche kostenlose Videoschulungen zur Verfügung. Weitere Informationen zum Programmieren in C# finden Sie unter [C#-Grundlagen: Development for absolute beginners (C#-Grundlagen: Entwicklung für Anfänger)](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners). Weitere Informationen zum Programmieren in Visual Basic finden Sie unter [Visual Basic fundamentals: Development for absolute beginners (Visual Basic-Grundlagen: Entwicklung für Anfänger)](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners).

## <a name="next-steps"></a>Nächste Schritte

Beginnen Sie das Tutorial mit **[Schritt 1: Erstellen eines Windows Forms-Anwendungsprojekts](../ide/step-1-create-a-windows-forms-application-project.md)** .

## <a name="see-also"></a>Siehe auch

* [Weitere C#-Tutorials](../get-started/csharp/index.yml)
* [Visual Basic-Tutorials](../get-started/visual-basic/index.yml)
* [C++-Tutorials](/cpp/get-started/tutorial-console-cpp)