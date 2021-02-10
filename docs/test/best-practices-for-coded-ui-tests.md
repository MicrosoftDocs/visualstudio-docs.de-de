---
title: Empfohlene Vorgehensweisen für Tests der programmierten UI
description: Hier erhalten Sie einige Empfehlungen für die Entwicklung von Tests der programmierten UI. Die folgenden Richtlinien erleichtern Ihnen, einen flexiblen Test der programmierten UI zu erstellen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, best practices
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 23b959f693e2deb6fd1ee4bdbe2e4158ee6ac13e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964640"
---
# <a name="best-practices-for-coded-ui-tests"></a>Bewährte Methoden für Tests der programmierten UI

In diesem Thema werden einige Empfehlungen für die Entwicklung von Tests der programmierten UI beschrieben.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="best-practices"></a>Bewährte Methoden

Halten Sie sich an die folgenden Richtlinien, um einen flexiblen Test der programmierten UI zu erstellen.

- Verwenden Sie wenn möglich den **Test-Generator der programmierten UI**.

- Ändern Sie die Datei *UIMap.Designer.cs* nicht direkt. Wenn Sie Datei ändern, werden die an der Datei vorgenommenen Änderungen überschrieben.

- Erstellen Sie den Test als Sequenz aufgezeichneter Methoden. Weitere Informationen über die Aufzeichnung einer Methode finden Sie unter [Erstellen von Tests der programmierten UI](../test/use-ui-automation-to-test-your-code.md).

- Jede aufgezeichnete Methode sollte auf eine einzelne Seite, ein einzelnes Formular oder Dialogfeld einwirken. Erstellen Sie eine neue Testmethode für jede neue Seite, jedes neue Formular oder Dialogfeld.

- Wenn Sie eine Methode erstellen, verwenden Sie statt des Standardnamens einen aussagekräftigen Methodennamen. Ein aussagekräftiger Name hilft dabei, den Zweck der Methode zu erkennen.

- Beschränken Sie jede aufgezeichnete Methode wenn möglich auf weniger als 10 Aktionen. Dieser modulare Ansatz erleichtert es, eine Methode zu ersetzen, wenn sich die Benutzeroberfläche ändert.

- Erstellen Sie jede Assertion mithilfe des **Generators für Tests der programmierten UI**, der automatisch eine Assertionsmethode zur *UIMap.Designer.cs*-Datei hinzufügt.

- Wenn sich die Benutzeroberfläche (User Interface, UI) ändert, zeichnen Sie die Testmethoden oder die Assertionsmethoden erneut auf, oder zeichnen Sie die betroffenen Abschnitte einer vorhandenen Testmethode erneut auf.

- Erstellen Sie eine separate [UIMap](/previous-versions/dd580454(v=vs.140))-Datei für jedes Modul in der getesteten Anwendung. Weitere Informationen finden Sie unter [Testing a Large Application with Multiple UI Maps (Testen einer großen Anwendung mit mehreren UI-Zuordnungen)](../test/testing-a-large-application-with-multiple-ui-maps.md).

- Verwenden Sie in der getesteten Anwendung aussagekräftige Namen, wenn Sie Benutzeroberflächen-Steuerelemente erstellen. Aussagekräftige Namen schaffen mehr Klarheit und Benutzerfreundlichkeit für die automatisch generierten Steuerelementnamen.

- Wenn Sie Assertionen durch Codierung mit der API erstellen, erstellen Sie eine Methode für jede Assertion in dem Teil der [UIMap](/previous-versions/dd580454(v=vs.140))-Klasse, der sich in der *UIMap.cs*-Datei befindet. Rufen Sie diese Methode aus der Testmethode auf, um die Assertion auszuführen.

- Wenn Sie direkt mit der API codieren, verwenden Sie so oft wie möglich die Eigenschaften und Methoden in den Klassen, die in der *UIMap.Designer.cs*-Datei in Ihrem Code generiert wurden. Diese Klassen machen Ihre Arbeit einfacher und zuverlässiger und helfen Ihnen, produktiver zu sein.

Tests der codierten UI werden automatisch an zahlreiche Änderungen in der Benutzeroberfläche angepasst. Wenn z. B. ein Benutzeroberflächenelement Position oder Farbe geändert hat, wird beim Test der programmierten UI in den meisten Fällen dennoch das richtige Element gefunden.

Während eines Testlaufs werden die UI-Steuerelemente mithilfe mehrerer Sucheigenschaften vom Testframework gesucht. Die Sucheigenschaften gelten für jede Steuerelementklasse in den vom **Generator für Tests der programmierten UI** in der *UIMap.Designer.cs*-Datei erstellten Definitionen. Die Sucheigenschaften enthalten Name-Wert-Paare von Eigenschaftennamen und Eigenschaftenwerte, die verwendet werden können, um das Steuerelement zu identifizieren, z. B. die <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.FriendlyName%2A>-, <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.Name%2A>- und <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.ControlType%2A>-Eigenschaften des Steuerelements. Wenn die Sucheigenschaften unverändert sind, findet der Test der programmierten UI erfolgreich das Steuerelement in der Benutzeroberfläche. Wenn die Sucheigenschaften geändert wurden, wendet ein intelligenter Vergleichsalgorithmus der Tests der programmierten UI Heuristik an, um Steuerelemente und Fenster in der Benutzeroberfläche zu finden. Wenn die Benutzeroberfläche geändert wurde, können Sie möglicherweise die Sucheigenschaften von zuvor identifizierten Elementen ändern, um sicherstellen, dass sie gefunden werden.

## <a name="if-your-user-interface-changes"></a>Vorgehensweise bei geänderter Benutzeroberfläche

Benutzeroberflächen werden während der Entwicklung häufig geändert. Nachfolgend finden Sie einige Möglichkeiten, um die Auswirkungen dieser Änderungen zu reduzieren:

- Suchen Sie die aufgezeichnete Methode, die auf dieses Steuerelement verweist, und verwenden Sie den **Test-Generator der programmierten UI**, um die Aktionen für diese Methode erneut aufzuzeichnen. Sie können den gleichen Namen für die Methode verwenden, um die vorhandenen Aktionen zu überschreiben.

- Wenn ein Steuerelement über eine Assertion verfügt, die nicht mehr gültig ist:

  - Löschen Sie die Methode, die die Assertion enthält.

  - Entfernen Sie den Aufruf dieser Methode aus der Testmethode.

  - Fügen Sie eine neue Assertion hinzu, indem Sie die Fadenkreuz-Schaltfläche auf das UI-Steuerelement ziehen, die UI-Zuordnung öffnen und die neue Assertion hinzufügen.

Weitere Informationen über das Aufzeichnen von Tests der programmierten UI finden Sie unter [Verwenden von Benutzeroberflächenautomatisierung zum Testen des Codes ](../test/use-ui-automation-to-test-your-code.md).

## <a name="if-a-background-process-needs-to-complete-before-the-test-can-continue"></a>Vorgehensweise, wenn ein Hintergrundprozess abgeschlossen werden muss, bevor der Test fortgesetzt werden kann

Möglicherweise müssen Sie warten, bis ein Prozess beendet wird, bevor Sie mit der nächsten Benutzeroberflächen-Aktion fortfahren können. Hierzu können Sie wie im folgenden Beispiel <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyLevel%2A> verwenden, um zu warten, bevor der Test fortgesetzt wird:

```csharp
// Set the playback to wait for all threads to finish
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.AllThreads;

// Press the submit button
this.UIMap.ClickSubmit();

// Reset the playback to wait only for the UI thread to finish
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.UIThreadOnly;
```

## <a name="see-also"></a>Weitere Informationen

- [UIMap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UITesting>
- [Verwenden der Benutzeroberflächenautomatisierung zum Testen des Codes](../test/use-ui-automation-to-test-your-code.md)
- [Erstellen von Tests der programmierten UI](../test/use-ui-automation-to-test-your-code.md)
- [Testing a Large Application with Multiple UI Maps (Testen einer großen Anwendung mit mehreren UI-Zuordnungen)](../test/testing-a-large-application-with-multiple-ui-maps.md)
- [Unterstützte Konfigurationen und Plattformen für Tests der programmierten UI und Aktionsaufzeichnungen](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
