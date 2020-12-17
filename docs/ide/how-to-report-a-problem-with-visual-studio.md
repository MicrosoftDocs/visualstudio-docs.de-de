---
title: Melden eines Problems mit Visual Studio
description: Erfahren Sie, wie Sie ein Problem mit Visual Studio melden.
ms.date: 03/11/2018
ms.topic: how-to
ms.assetid: bee01179-cde5-4419-9095-190ee0ba5902
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2956372882d4449345d026e691a12afb2988054a
ms.sourcegitcommit: 6ef4e46c786c5bbcc52cd9c30e5ddfca12ea8b3c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "97050825"
---
# <a name="how-to-report-a-problem-with-visual-studio-or-visual-studio-installer"></a>Melden eines Problems mit Visual Studio oder Visual Studio-Installer

> [!NOTE]
> Informationen zu Visual Studio für Mac finden Sie unter[Melden eines Problems in Visual Studio für Mac](/visualstudio/mac/report-a-problem).

Sie können ein Problem aus Visual Studio oder aus dem Installationsprogramm melden. Mit dem integrierten Feedbacktool können Sie problemlos Diagnoseinformationen hinzufügen, die den Visual Studio-Teams helfen, Probleme zu diagnostizieren und zu beheben. Im Folgenden finden Sie die Schritte zum Melden eines Problems.

1. Wählen Sie in **Visual Studio** das Feedback-Symbol in der oberen rechten Ecke und dann „Ein Problem melden“ aus. Sie können das Feedback-Tool auch aus dem Menü **Hilfe** > **Feedback senden** > **Ein Problem melden** aufrufen.
![Popupfenster „Problem melden“ auf der Visual Studio Developer Community-Website ](media/feedback-button.png)Alternativ können Sie ein Problem im **Visual Studio-Installer** melden, wenn Sie Visual Studio nicht installieren können oder nicht auf das Feedback-Tool in Visual Studio zugreifen können.  Wählen Sie im Installer das Feedback-Symbol in der oberen rechten Ecke und dann „Ein Problem melden“ aus.
![Popupelement „Problem melden“ auf der Visual Studio Developer Community-Website](media/installer.png)

1. Wenn Sie auf **Problem melden** klicken, wird Ihr Standardbrowser geöffnet, und Sie werden mit demselben Konto angemeldet, das Sie für die Anmeldung bei Visual Studio verwenden.

   ![Anmelden zum Melden eines Problems](../ide/media/feedback-browser-top.png)

1. Beginnen Sie mit der Eingabe des beschreibenden Titels des Fehlerberichts. Er muss mindestens 25 Zeichen lang sein.

    ![Problem melden](../ide/media/feedback-report.png)

1. Sobald Sie mit der Eingabe beginnen, werden im Feld „Titel“ mögliche Duplikate angezeigt.

    ![Suchen nach Duplikaten](../ide/media/feedback-search.png)

1. Wählen Sie die möglichen Fehlerberichtduplikate aus, um zu ermitteln, ob einer der Berichte zu Ihrem eigenen Problem passt. Wenn dies der Fall ist, stimmen Sie für diesen Bericht, anstatt ein eigenes Ticket zu erstellen.

    ![Zustimmen zu Duplikaten](../ide/media/feedback-duplicate.png)

2. Wenn keine Duplikate gefunden wurden, fahren Sie fort, indem Sie eine Beschreibung des Problems eingeben. Es ist wichtig, sich so klar wie möglich auszudrücken, um die Chancen zu erhöhen, dass wir in der Lage sind, den Fehler zu reproduzieren. Stellen Sie sicher, dass Sie klare Reproduktionsschritte beschreiben.

3. Falls für den Fehlerbericht relevant, erstellen Sie einen Screenshot, indem Sie das Kontrollkästchen *Visual Studio-Screenshot einschließen* aktivieren.

    ![Erstellen eines Screenshots](../ide/media/feedback-screenshot.png) *Nur Microsoft-Techniker können den Screenshot sehen*

    Sie können den Screenshot sogar direkt im Browser zuschneiden, um alle sensiblen oder nicht relevanten Elemente zu entfernen.

4. Eine der besten Möglichkeiten, dem Visual Studio-Engineeringteam bei der Lösung des Problems zu helfen, ist die Bereitstellung von Stapelüberwachungs- und Heap-Abbilddateien, die das Team untersuchen kann. Dies lässt sich problemlos erreichen, indem die Schritte aufgezeichnet werden, die zu dem Fehler geführt haben.

    ![Aufzeichnen Ihrer Aktionen](../ide/media/feedback-recording.png) *Nur Microsoft-Techniker können die Aufzeichnung sehen*

5. Überprüfen Sie die angefügten Dateien, und laden Sie zusätzliche Dateien hoch, wenn Sie glauben, dass dies bei der Diagnose des Problems helfen könnte.

    ![Angefügte Dateien](../ide/media/feedback-attachments.png) *Nur Microsoft-Technikern können die angefügten Dateien sehen*

6. Der letzte Schritt besteht darin, auf die Schaltfläche **Senden** zu klicken. Wenn Sie den Bericht übermitteln, wird er direkt an das interne Visual Studio-Fehlerberichterstattungssystem gesendet und wartet dort auf eine Beurteilung.

## <a name="when-further-information-is-needed"></a>Wenn weitere Informationen erforderlich sind

Wenn bei einem Issue wichtige Informationen fehlen, weisen wir den Status **Needs More Info** (Mehr Info nötig) zu. Wir schreiben einen Kommentar zum Issue mit den genauen erforderlichen Informationen, und Sie erhalten eine Benachrichtigung per E-Mail. Wenn wir die Informationen nicht innerhalb von sieben Tagen erhalten, schicken wir Ihnen eine Erinnerung. Nach weiteren 14 Tagen ohne Aktivität schließen wir das Ticket.

1. Folgen Sie dem Link in der E-Mail zum Problembericht, oder navigieren Sie zur Startseite, um alle Berichte im Status **Weitere Informationen erforderlich** anzuzeigen.

    ![Mein Feedback](../ide/media/feedback-my-feedback.png)

1. Wenn Sie den Link „Weitere Informationen bereitstellen“ im Problembericht auswählen, erfolgt die Navigation zu einem neuen Bildschirm. Von dort aus können Sie sehen, welche Informationen angefordert werden.

   ![Mein Feedback](../ide/media/feedback-need-more-info.png)

1. Sie können durch das Hinzufügen von Kommentaren oder Anlagen und das Aufzeichnen von Schritten weitere Informationen bereitstellen. Dies funktioniert ähnlich wie das Melden neuer Probleme oder das Bereitstellen zusätzlicher Informationen beim Abstimmen für ein Problem.

1. Der anfordernde Microsoft-Techniker empfängt eine Benachrichtigung über die bereitgestellten zusätzlichen Informationen. Wenn sie über ausreichend Informationen verfügen, um das Problem zu untersuchen, wird der Problemstatus geändert. Anderenfalls fordert der Techniker erneut weitere Informationen an.

Sie können diese Anforderungen auf dem Bildschirm **Mein Feedback** zusammen mit all Ihren anderen **Problemen** und **Vorschlägen** anzeigen.

## <a name="search-for-solutions-or-provide-feedback"></a>Suchen nach Lösungen oder Geben von Feedback

Wenn Sie ein Problem nicht über Visual Studio melden möchten oder können, wurde es möglicherweise bereits gemeldet und eine Lösung auf der Website [Visual Studio Developer Community](https://developercommunity.visualstudio.com/) veröffentlicht.

Wenn Sie kein Problem melden, sondern ein Feature vorschlagen möchten, besteht auch dazu eine Möglichkeit. Weitere Informationen finden Sie auf der Seite [Suggest a feature (Vorschlagen eines Features)](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).

## <a name="see-also"></a>Siehe auch

* [Richtlinien für die Entwicklercommunity](./developer-community-guidelines.md)
* [Visual Studio-Feedbackoptionen](../ide/feedback-options.md)
* [Vorgehensweise: Melden eines Problems mit Visual Studio für Mac](/visualstudio/mac/report-a-problem)
* [Melden eines Problems mit dem Visual C++-Toolset oder der -Dokumentation](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Visual Studio Developer Community](https://developercommunity.visualstudio.com/)
* [Developer Community data privacy (Datenschutz in der Entwicklercommunity)](developer-community-privacy.md)