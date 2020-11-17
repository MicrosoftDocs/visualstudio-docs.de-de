---
title: Testtools für Visual Studio für Mac
description: Dieser Artikel befasst sich mit dem Erstellen und Ausführen von Tests mit Visual Studio für Mac.
ms.date: 11/09/2020
ms.topic: conceptual
helpviewer_keywords:
- testing tools [Visual Studio for Mac]
- unit tests [Visual Studio for Mac]
ms.author: jomatthi
author: jmatthiesen
ms.openlocfilehash: 3956c3158fd4ec1ad32b76882ac3f9d4cf1ea9bf
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493386"
---
# <a name="testing-tools-in-visual-studio-for-mac"></a>Testtools in Visual Studio für Mac

Die Visual Studio-Testtools für Mac können Sie und Ihr Team dabei unterstützen, hochwertigen Code zu entwickeln und diesen Standard einzuhalten. Komponententests können mithilfe des Microsoft-Komponententestframeworks (MSTest), xUnit oder NUnit geschrieben und ausgeführt werden.

## <a name="creating-tests"></a>Erstellen von Tests
Um mit dem Testen zu beginnen, können Sie ein neues Testprojekt in Ihrer Projektmappe erstellen, indem Sie mit der rechten Maustaste auf Ihre Projektmappe klicken und das Menü **Hinzufügen > Neues Projekt...** auswählen. Wählen Sie dann eine der Testkategorien auf der linken Seite des Dialogfelds (z. B. die Kategorie **Web und Konsole > Tests**) aus. Wählen Sie den Typ des Testprojekts aus, das Sie erstellen möchten, und klicken Sie auf „Weiter“. Folgen Sie den Anweisungen in den angezeigten Dialogfeldern, dann wird Ihrer Projektmappe ein neues Testprojekt hinzugefügt.

![Dialogfeld „Neues Projekt“ mit ausgewähltem Abschnitt „Web und Konsole > Tests“ und angezeigten xUnit-, MSTest- und NUnit-Projekten](media/create-new-test-project.PNG)

> [!NOTE]
> Weitere Informationen zu Komponententests Ihrer .NET Core-Anwendungen und zur Auswahl von Komponententestframeworks finden Sie in der Dokumentation [Komponententests in .NET Core und .NET Standard](/dotnet/core/testing/?pivots=xunit).

## <a name="running-tests"></a>Ausführen von Tests
Das Fenster **Komponententests** wird zum Ausführen von Komponententests verwendet und über das Menü **Ansicht > Tests** geöffnet. Komponententests in der Projektmappe werden automatisch erkannt und in diesem Fenster angezeigt, in dem Sie alle Tests oder eine Teilmenge von Tests ausführen können, die Sie ausgewählt haben.

![Testfenster mit einer Liste von Komponententests und einer Symbolleiste zum Ausführen oder Beenden von Tests.](media/test-window.PNG)

Beim Bearbeiten einer C#-Klasse, die Komponententests enthält, können Sie Tests ausführen, indem Sie mit der rechten Maustaste auf die Testklasse oder eine Testmethode klicken und das Menü **Test(s) ausführen** oder **Test(s) debuggen** auswählen. Wenn Sie das Menüelement **Test(s) ausführen** auswählen, werden die Tests im Testfenster ausgeführt. Dies geschieht auch bei der Auswahl von **Test(s) debuggen**, aber der Debugger wird angefügt, damit Sie Problembehandlung für Ihren Code ausführen können.

![Kontextmenü des Editors mit den Optionen zum Ausführen und Debuggen von Tests](media/run-tests-context-menu.PNG)

Beim Ausführen von Tests wird ein Fenster **Testergebnisse** angezeigt, sodass Sie erfolgreiche oder fehlgeschlagene Tests und die Ausgabe der Ausführung dieser Tests überprüfen können.

![Testergebnisfenster zeigt einen fehlgeschlagenen Test sowie 21 bestandenen Tests und einen fehlgeschlagenen Test an.](media/test-results-window.PNG)

## <a name="see-also"></a>Weitere Informationen

- [Komponententests in .NET Core und .NET Standard](/dotnet/core/testing)
- [Erste Schritte mit Komponententests (Visual Studio unter Windows)](/visualstudio/test/getting-started-with-unit-testing)
- [Grundlagen von Komponententests (Visual Studio unter Windows)](/visualstudio/test/unit-test-basics)