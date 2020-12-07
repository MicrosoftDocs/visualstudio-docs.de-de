---
title: Live Unit Testing
description: Hier erfahren Sie mehr über Live Unit Testing während der Anwendungsentwicklung, einschließlich unterstützter Frameworks und der Konfiguration von Live Unit Testing.
ms.custom: SEO-VS-2020
ms.date: 04/07/2020
ms.topic: how-to
helpviewer_keywords:
- Live Unit Testing
author: mikejo5000
ms.author: mikejo
ms.workload:
- dotnet
ms.openlocfilehash: 82ed41514109887d32f38faf4f965c923864ae32
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329353"
---
# <a name="how-to-configure-and-use-live-unit-testing"></a>Konfigurieren und Verwenden von Live Unit Testing

Live Unit Testing führt automatisch alle betroffenen Komponententests im Hintergrund aus, und zeigt die Ergebnisse und Code Coverage in Echtzeit an, während Sie eine Anwendung entwickeln. Wenn Sie Ihren Code ändern, bietet Live Unit Testing Feedback dazu, welche Auswirkungen Ihre Änderungen auf vorhandene Tests haben und ob der neue von Ihnen hinzugefügte Code von einem oder mehreren vorhandenen Tests abgedeckt wird. So werden Sie daran erinnert, Komponententests zu schreiben, während Sie Fehler beheben oder neue Funktionen hinzufügen.

> [!NOTE]
> Live Unit Testing steht für C#- und Visual Basic-Projekte zur Verfügung, die auf .NET Core bzw. .NET Framework in der Enterprise-Edition von Visual Studio ausgerichtet sind.

Wenn Sie Live Unit Testing für Ihre Tests verwenden, werden Daten zum Status Ihrer Tests beibehalten. Da bei Live Unit Testing persistente Daten verwendet werden können, bietet es eine überragende Leistung bei der dynamischen Ausführung Ihrer Tests in Bezug auf Codeänderungen.

## <a name="supported-test-frameworks"></a>Unterstützte Testframeworks

Live Unit Testing kann mit den drei gängigen Frameworks für Komponententests verwendet werden, die in der folgenden Tabelle aufgeführt sind. Die unterstützte Mindestversion der Adapter und Frameworks ist ebenfalls aufgeführt. Die Frameworks für Komponententests sind auf „NuGet.org“ verfügbar.

|Testframework  |Mindestversion des Visual Studio-Adapters  |Mindestversion des Frameworks  |
|---------|---------|---------|
|xUnit.net |xunit.runner.visualstudio, Version 2.2.0-beta3-build1187 |xUnit 1.9.2 |
|NUnit |NUnit3TestAdapter, Version 3.5.1 |NUnit, Version 3.5.0 |
|MSTest |MSTest.TestAdapter 1.1.4-preview |MSTest.TestFramework 1.0.5-preview |

Wenn Sie ältere auf MSTest-basierende Testprojekte haben, die sich auf Microsoft.VisualStudio.QualityTools.UnitTestFramework beziehen, und Sie nicht auf die neueren MSTest-NuGet-Pakete umsteigen möchten, sollten Sie auf Visual Studio 2019 oder Visual Studio 2017 upgraden.

In einigen Fällen müssen Sie explizit die NuGet-Pakete wiederherstellen, auf die ein Projekt in der Projektmappe verweist, damit Live Unit Testing funktioniert. Hierzu können Sie entweder die Projektmappe explizit erstellen (wählen Sie im obersten Visual Studio-Menü **Build** > **Projektmappe neu erstellen** aus) oder Pakete in der Projektmappe wiederherstellen (klicken Sie mit der rechten Maustaste auf die Projektmappe, und wählen Sie **NuGet-Pakete wiederherstellen** aus).

## <a name="configure"></a>Konfigurieren

Konfigurieren Sie Live Unit Testing, indem Sie in der obersten Visual Studio-Menüleiste **Extras** > **Optionen** und anschließend im Dialogfeld **Optionen** im linken Bereich **Live Unit Testing** auswählen.

> [!TIP]
> Nach der Aktivierung von Live Unit Testing (siehe nächster Abschnitt [Starten, Anhalten und Beenden von Live Unit Testing](#start-pause-and-stop)) können Sie auch das Dialogfeld **Optionen** öffnen, indem Sie **Test** > **Live Unit Testing** > **Optionen** auswählen.

Die folgende Abbildung zeigt die im Dialogfeld verfügbaren Konfigurationsoptionen für Live Unit Testing:

![Konfigurationsoptionen für Live Unit Testing](./media/lut-options.png)

Die konfigurierbaren Optionen umfassen Folgendes:

- Ob Live Unit Testing angehalten wird, wenn eine Projektmappe erstellt und ein Debugging durchgeführt wird.

- Ob Live Unit Testing angehalten wird, wenn die Akkuleistung des Systems unter einen bestimmten Schwellenwert sinkt.

- Ob Live Unit Testing automatisch ausgeführt wird, wenn eine Projektmappe geöffnet wird.

- Ob das Debugsymbol und die Kommentargenerierung für die XML-Dokumentation aktiviert ist.

- Das Verzeichnis, in dem persistente Daten gespeichert werden sollen.

- Die Fähigkeit, alle persistenten Daten zu löschen. Dies ist hilfreich, wenn sich Live Unit Testing auf unvorhersehbare oder unerwartete Weise verhält, was darauf hinweist, dass die persistenten Daten beschädigt wurden.

- Das Intervall, nach dem eine Zeitüberschreitung für einen Testfall auftritt. Der Standardwert ist 30 Sekunden.

- Die maximale Anzahl der Testläufe, die Live Unit Testing erstellt.

- Die maximale Arbeitsspeichermenge, die Live Unit Testing-Prozesse belegen können.

- Den Umfang an Informationen, der in das Live Unit Testing-Fenster **Ausgabe** geschrieben wird.

   Mögliche Optionen sind: Keine Protokollierung (**Keine**), nur Fehlermeldungen (**Fehler**), Fehler- und Informationsmeldungen (**Info**, die Standardeinstellung) oder alle Details (**Ausführlich**).

   Sie können auch eine ausführlichen Ausgabe im Live Unit Testing-Fenster **Ausgabe** anzeigen, indem Sie einer Umgebungsvariablen auf Benutzerebene mit dem Namen `VS_UTE_DIAGNOSTICS` den Wert „1“ zuweisen und dann Visual Studio neu starten.

   Um detaillierte MSBuild-Protokollmeldungen von Live Unit Testing in einer Datei aufzuzeichnen, legen Sie die `LiveUnitTesting_BuildLog`-Umgebungsvariable auf Benutzerebene auf den Namen der Datei fest, die das Protokoll enthalten soll.

## <a name="start-pause-and-stop"></a>Starten, Anhalten und Beenden

Um Live Unit Testing zu aktivieren, klicken Sie im obersten Visual Studio-Menü auf **Test** > **Live Unit Testing** > **Starten**. Wenn Live Unit Testing aktiviert ist, ändern sich die verfügbaren Optionen im **Live Unit Testing**-Menü von dem einzelnen Element **Starten** zu **Anhalten** und **Beenden**:

- **Anhalten**: Unterbricht Live Unit Testing vorübergehend.

  Wenn Live Unit Testing angehalten wird, wird die Abdeckungsvisualisierung nicht im Editor dargestellt, aber alle gesammelten Daten bleiben erhalten. Um Live Unit Testing fortzusetzen, wählen Sie im Live Unit Testing-Menü **Weiter** aus. Live Unit Testing führt die notwendigen Schritte aus, um alle Änderungen nachzuholen, die vorgenommen wurden, während Live Unit Testing angehalten war, und aktualisiert die Glyphen entsprechend.

- **Beenden**: Beendet Live Unit Testing vollständig. Live Unit Testing verwirft alle Daten, die gesammelt wurden.

> [!NOTE]
> Wenn Sie Live Unit Testing in einer Projektmappe starten, die kein Komponententestprojekt enthält, erscheinen zwar die Optionen **Anhalten** und **Beenden** im **Live Unit Testing**-Menü, Live Unit Testing wird jedoch nicht gestartet. Das **Ausgabe**-Fenster zeigt eine Nachricht, die mit „No supported test adapters are referenced by this solution...“ (Diese Projektmappe bezieht sich auf keine unterstützten Testadapter...) beginnt.

Sie können Live Unit Testing jederzeit vorübergehend anhalten oder vollständig beenden. Sie könnten sich beispielsweise dann dazu entschließen, wenn Sie gerade ein Refactoring ausführen und wissen, dass die Tests für eine Weile gestört sind.

## <a name="view-coverage-visualization"></a>Anzeigen der Abdeckungsvisualisierung

Nach der Aktivierung aktualisiert Live Unit Testing alle Codezeilen im Visual Studio-Editor, um Ihnen zu zeigen, ob der Code, den Sie schreiben, von Komponententests abgedeckt ist, und ob die Tests, die ihn abdecken, erfolgreich sind. Die folgende Abbildung zeigt Codezeilen mit erfolgreichen und nicht erfolgreichen Tests sowie Codezeilen, die nicht durch Tests abgedeckt sind. Zeilen mit einem grünen „✓“ werden nur durch bestandene Tests abgedeckt, Zeilen mit einem roten „x“ werden von einem oder mehreren nicht bestandenen Tests abgedeckt, und Zeilen mit einem blauen „➖“ werden von keinem Test abgedeckt.

![Code Coverage in Visual Studio](./media/lut-codewindow.png)

Die Abdeckungsvisualisierung von Live Unit Testing wird sofort aktualisiert, wenn Sie Code im Code-Editor ändern. Während der Verarbeitung der Änderungen wird die Visualisierung geändert, um anzugeben, dass die Daten nicht auf dem neuesten Stand sind. Dazu wird ein rundes Uhrensymbol unterhalb der Symbole für erfolgreiche, nicht erfolgreiche und nicht abgedeckte Tests angezeigt, wie in der folgenden Abbildung dargestellt.

![Code Coverage in Visual Studio mit Timersymbol](./media/lut-codeupdating.png)

## <a name="get-information-about-test-status"></a>Abrufen von Informationen über den Teststatus

Wenn Sie den Mauszeiger im Codefenster über das Symbol für erfolgreiche oder fehlgeschlagene Tests bewegen, können Sie sehen, wie viele Tests diese Zeile betreffen. Um den Status der einzelnen Tests anzuzeigen, wählen Sie das Symbol aus:

![Teststatus für ein Symbol in Visual Studio](./media/lut-failedinfo.png)

Neben der Angabe der Namen und Testergebnisse können Sie mithilfe der QuickInfo die Gruppe von Tests erneut ausführen oder debuggen. Wenn Sie einen oder mehrere Tests in der QuickInfo auswählen, können Sie diese Tests auch ausführen oder debuggen. Auf diese Weise können Sie Ihre Tests debuggen, ohne das Codefenster verlassen zu müssen. Wenn der Debugger eine <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>-Methode ausführt, die ein unerwartetes Ergebnis zurückgibt, wird die Programmausführung bei der Überwachung aller eventuell festgelegten Haltepunkte und zusätzlich beim Debuggen angehalten.

Wenn Sie den Mauszeiger über einen nicht bestandenen Test in der QuickInfo bewegen, wird sie erweitert, und es werden zusätzliche Informationen zum jeweiligen Fehler bereitgestellt, wie in der folgenden Abbildung dargestellt wird. Um direkt zu einem nicht erfolgreichen Test zu navigieren, doppelklicken Sie in der QuickInfo darauf.

![QuickInfo zu einem nicht erfolgreichen Test in Visual Studio](./media/lut-failedmsg.png)

Wenn Sie zu einem nicht erfolgreichen Test navigieren, zeigt Live Unit Testing in der Methodensignatur die Tests an, für die Folgendes gilt:

- erfolgreich (angezeigt durch ein halb volles Becherglas zusammen mit einem grünen „✓“)
- nicht erfolgreich (angezeigt durch ein halb volles Becherglas zusammen mit einem roten „🞩“)
- nicht an Live Unit Testing beteiligt (angezeigt durch ein halb volles Becherglas zusammen mit einem blauen „➖“)

Methoden, die keine Testmethoden darstellen, sind nicht mit einem Symbol versehen. Die folgende Abbildung zeigt alle vier Arten von Methoden.

![Testmethoden in Visual Studio mit dem Symbol für „erfolgreich“ oder „nicht erfolgreich“](media/lut-testsource.png)

## <a name="diagnose-and-correct-test-failures"></a>Diagnostizieren und Beheben von Testfehlern

Über den nicht erfolgreichen Test können Sie problemlos den Produktcode debuggen, ihn bearbeiten und die Entwicklung Ihrer Anwendung fortsetzen. Da Live Unit Testing im Hintergrund ausgeführt wird, müssen Sie Live Unit Testing beim Debuggen, Bearbeiten und Fortsetzen des Zyklus nicht beenden und neu starten.

Beispiel: Der in der obigen Abbildung dargestellte nicht bestandene Test wurde durch die falsche Annahme in der Testmethode verursacht, dass nicht alphabetische Zeichen `true` zurückgeben, wenn sie an die <xref:System.Char.IsLower%2A?displayProperty=fullName>-Methode übergeben werden. Nachdem Sie die Testmethode korrigiert haben, sollten alle Tests bestanden werden. Sie müssen Live Unit Testing nicht vorübergehend anhalten oder beenden.

::: moniker range="vs-2017"
## <a name="test-explorer"></a>Test-Explorer

Der **Test-Explorer** stellt eine Schnittstelle bereit, mit der Sie Tests ausführen und debuggen und Testergebnisse analysieren können. Live Unit Testing ist in den **Test-Explorer** integriert. Wenn Live Unit Testing nicht aktiviert ist oder beendet wurde, zeigt der **Test-Explorer** den Status von Komponententests an, als zuletzt ein Test ausgeführt wurde. Änderungen am Quellcode erfordern, dass Sie die Tests erneut ausführen. Wenn Live Unit Testing dagegen aktiviert ist, wird der Status der Komponententests im **Test-Explorer** sofort aktualisiert. Sie müssen die Komponententests nicht explizit ausführen.

> [!TIP]
> Öffnen Sie **Live Unit Testing**, indem Sie im obersten Visual Studio-Menü **Test** > **Windows** > **Test-Explorer** auswählen.

Möglicherweise ist Ihnen ausgefallen, dass im **Test-Explorer**-Fenster einige Tests als verblasst angezeigt werden. Beispiel: Wenn Sie Live Unit Testing aktivieren, nachdem Sie ein zuvor gespeichertes Projekt geöffnet haben, sind im **Test-Explorer**-Fenster alle Tests mit Ausnahme des nicht bestandenen ausgeblendet, wie die folgende Abbildung zeigt. In diesem Fall hat Live Unit Testing den nicht bestandenen Test erneut ausgeführt, die erfolgreichen Tests jedoch nicht erneut ausgeführt. Dies liegt daran, dass die beibehaltenen Daten von Live Unit Testing darauf hindeuten, dass seit der letzten erfolgreichen Durchführung der Tests keine Änderungen vorgenommen wurden.

![Nicht erfolgreicher Test im Test-Explorer](media/lut-test-explorer.png)

Sie können alle ausgeblendeten Tests erneut ausführen, indem Sie im **Test-Explorer**-Menü die Optionen **Alle ausführen** oder **Ausführen** auswählen. Wählen Sie alternativ im Menü **Test-Explorer** einen oder mehrere Tests aus, klicken Sie mit der rechten Maustaste, und wählen Sie dann **Ausgewählte Tests ausführen** oder **Ausgewählte Tests debuggen** im Popupmenü aus. Tests, die ausgeführt werden, werden oben angezeigt.

Es gibt einige Unterschiede zwischen dem automatischen Ausführen und Aktualisieren der Testergebnisse durch Live Unit Testing und dem expliziten Ausführen von Tests im **Test-Explorer**. Zu diesen Unterschieden zählen Folgende:

- Beim Ausführen oder Debuggen von Tests im Test-Explorer-Fenster werden reguläre Binärdateien ausgeführt. Live Unit Testing führt dagegen instrumentierte Binärdateien aus.
- Live Unit Testing erstellt keine neue Anwendungsdomäne zum Ausführen von Tests, sondern führt Tests mit der Standarddomäne aus. Tests, die über das **Test-Explorer**-Fenster ausgeführt werden, erstellen eine neue Anwendungsdomäne.
- Live Unit Testing führt Tests in allen Testassemblys nacheinander aus. Im Fenster **Test-Explorer** können Sie auswählen, mehrere Tests parallel auszuführen.
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="live-unit-testing-window"></a>Live Unit Testing-Fenster

Ähnlich wie der **Test-Explorer** stellt **Live Unit Testing** eine Schnittstelle bereit, mit der Sie Tests ausführen und debuggen sowie Testergebnisse analysieren können. Wenn Live Unit Testing aktiviert ist, wird der Status der Komponententests im **Test-Explorer** sofort aktualisiert. Sie müssen die Komponententests nicht explizit ausführen. Wenn Live Unit Testing nicht aktiviert ist oder beendet wurde, zeigt **Live Unit Testing** den Status von Komponententests an, als zuletzt ein Test ausgeführt wurde. Nachdem Sie Live Unit Testing neu gestartet haben, müssen Sie eine Änderung am Quellcode vornehmen, um die Tests nochmal auszuführen.

> [!TIP]
> Starten Sie Live Unit Testing, indem Sie im obersten Menü von Visual Studio auf **Test** > **Live Unit Testing** > **Starten** klicken. Sie können das Fenster **Live Unit Testing** über **Ansicht** > **Andere Fenster** > **Live Unit Testing-Fenster** öffnen.

Möglicherweise ist Ihnen ausgefallen, dass im Fenster **Live Unit Testing** einige Tests verblasst angezeigt werden. Wenn Sie Live Unit Testing beenden und neu starten, werden beispielsweise alle Tests im Fenster **Live Unit Testing** wie in der folgenden Abbildung gezeigt verblasst angezeigt. Verblasste Testergebnisse weisen darauf hin, dass der jeweilige Test nicht im Rahmen der letzten Ausführung von Live Unit Testing stattfand. Tests werden nur ausgeführt, wenn eine Änderung am Test oder den Abhängigkeiten des Tests erkannt wird. Wenn es keine Änderungen gibt, wird eine unnötige Ausführung des Tests vermieden. In diesem Fall ist das ausgegraute Testergebnis weiterhin aktuell, obwohl der Test nicht in der letzten Ausführung enthalten war.

![Verblasste Tests im Test-Explorer](media/vs-2019/lut-test-explorer.png)

Sie können Tests, die verblasst angezeigt werden, noch mal ausführen, indem Sie eine Änderung am Code vornehmen.

Es gibt einige Unterschiede zwischen dem automatischen Ausführen und Aktualisieren der Testergebnisse durch Live Unit Testing und dem expliziten Ausführen von Tests im **Test-Explorer**. Zu diesen Unterschieden zählen Folgende:

- Beim Ausführen oder Debuggen von Tests im Test-Explorer-Fenster werden reguläre Binärdateien ausgeführt. Live Unit Testing führt dagegen instrumentierte Binärdateien aus.
- Live Unit Testing erstellt keine neue Anwendungsdomäne zum Ausführen von Tests, sondern führt Tests mit der Standarddomäne aus. Tests, die über das **Test-Explorer**-Fenster ausgeführt werden, erstellen eine neue Anwendungsdomäne.
- Live Unit Testing führt Tests in allen Testassemblys nacheinander aus. Im Fenster **Test-Explorer** können Sie auswählen, mehrere Tests parallel auszuführen.
::: moniker-end

## <a name="large-solutions"></a>Große Projektmappen

Wenn Ihre Projektmappe über mindestens 10 Projekte verfügt, zeigt Visual Studio das folgende Dialogfeld an, wenn Sie Folgendes ausführen:

- Starten von Live Unit Testing, ohne dass persistente Daten vorhanden sind
- Auswählen von **Tools** > **Optionen** > **Live Unit Testing** > **Beibehaltene Daten löschen**

![Live Unit Testing-Dialogfeld für große Projekte](media/lut-large-project.png)

Im Dialogfeld werden Sie gewarnt, dass die dynamische Ausführung einer großen Anzahl von Tests in großen Projekten die Leistung erheblich beeinträchtigen kann. Wenn Sie auf **OK** klicken, führt Live Unit Testing alle Tests in der Projektmappe aus. Bei Auswahl von **Abbrechen** können Sie wählen, welche Tests ausgeführt werden. Im folgenden Abschnitt wird erläutert, wie dies erfolgt.

## <a name="include-and-exclude-test-projects-and-test-methods"></a>Einschließen und Ausschließen von Testprojekten und Testmethoden

Bei Projektmappen mit vielen Testprojekten können Sie steuern, welche Projekte und welche einzelnen Methoden in einem Projekt von Live Unit Testing berücksichtigt werden. Wenn Sie z.B. eine Projektmappe mit Hunderten von Testprojekten haben, können Sie eine bestimmte Reihe von Testprojekten für Live Unit Testing auswählen. Hierfür stehen eine Reihe von Möglichkeiten zur Verfügung, je nachdem, ob Sie alle Tests im Projekt oder in der Projektmappe ausschließen, einen Großteil der Tests ein- oder ausschließen oder einzelne Tests ausschließen möchten. Live Unit Testing speichert den Status für das Einschließen/Ausschließen als Benutzereinstellung, wenn eine Projektmappe geschlossen und erneut geöffnet wird.

### <a name="exclude-all-tests-in-a-project-or-solution"></a>Ausschließen aller Tests in einem Projekt oder einer Projektmappe

Um die einzelnen Projekte in Komponententests auszuwählen, gehen Sie nach dem Start von Live Unit Testing wie folgt vor:

1. Klicken Sie mit der rechten Maustaste im **Projektmappen-Explorer** auf die Projektmappe, und wählen Sie **Live Unit Testing** > **Ausschließen** aus, um die gesamte Projektmappe auszuschließen.
1. Klicken Sie mit der rechten Maustaste auf jedes Testprojekt, das Sie in die Tests einschließen möchten, und wählen Sie **Live Unit Testing** > **Einschließen** aus.

### <a name="exclude-individual-tests-from-the-code-editor-window"></a>Ausschließen von einzelnen Tests im Code-Editor-Fenster

Im Code-Editor-Fenster können Sie einzelne Testmethoden ein- oder ausschließen. Klicken Sie mit der rechten Maustaste auf die Signatur der Testmethode im Code-Editor-Fenster, und wählen Sie eine der folgenden Optionen aus:

- **Live Unit Testing** > **Einschließen \<selected method>**
- **Live Unit Testing** > **Ausschließen \<selected method>**
- **Live Unit Testing** > **Alle ausschließen außer \<selected method>**

### <a name="exclude-tests-programmatically"></a>Programmgesteuertes Ausschließen von Tests

Sie können auch das <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute>-Attribut anwenden, damit Methoden, Klassen oder Strukturen ihre Abdeckung nicht programmgesteuert in Live Unit Testing ausgeschlossen werden.

Schließen Sie mithilfe der folgenden Attribute einzelne Methoden von Live Unit Testing aus:

- Für xUnit: `[Trait("Category", "SkipWhenLiveUnitTesting")]`
- Für NUnit: `[Category("SkipWhenLiveUnitTesting")]`
- Für MSTest: `[TestCategory("SkipWhenLiveUnitTesting")]`

Schließen Sie mithilfe der folgenden Attribute eine gesamte Assembly von Live Unit Testing aus:

- Für xUnit: `[assembly: AssemblyTrait("Category", "SkipWhenLiveUnitTesting")]`
- Für NUnit: `[assembly: Category("SkipWhenLiveUnitTesting")]`
- Für MSTest: `[assembly: TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>Siehe auch

- [Testtools für Code](https://visualstudio.microsoft.com/vs/testing-tools/)
- [Live Unit Testing-Blog](https://devblogs.microsoft.com/visualstudio/live-unit-testing-in-visual-studio-2017-enterprise/)
- [Live-Komponententests – Häufig gestellte Fragen](live-unit-testing-faq.md)
- [Channel 9-Video: Live Unit Testing in Visual Studio](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105)
