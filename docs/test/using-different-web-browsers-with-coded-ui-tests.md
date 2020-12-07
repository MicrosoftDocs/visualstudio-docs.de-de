---
title: Verwenden verschiedener Webbrowser mit Tests der programmierten UI
description: Hier erfahren Sie, wie Sie Ihren Test anpassen und mit verschiedenen Browsern für Ihre Webanwendungen wiedergeben.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 6baddaeac3fdea3d27f60722e728df209bfd768d
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2020
ms.locfileid: "96330029"
---
# <a name="use-different-web-browsers-with-coded-ui-tests"></a>Verwenden verschiedener Webbrowser mit Tests der programmierten UI

Tests der programmierten UI können Tests für Webanwendungen durch Aufzeichnen Ihrer Tests mit Internet Explorer automatisieren. Sie können den Test anschließend anpassen und diesen entweder mit Internet Explorer oder anderen Browsertypen für diese Webanwendungen wiedergeben.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

Installieren Sie die [Selenium components for Coded UI Cross Browser (Selenium-Komponenten für browserübergreifende Tests der programmierten UI)](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting).

## <a name="whats-supported-across-all-web-browsers"></a>Folgendes wird auf allen Webbrowsern unterstützt:

- [Hinzufügen von benutzerdefiniertem Code für Steuerfunktionen](https://devblogs.microsoft.com/devops/coded-ui-test-configuring-search-properties-while-recording-on-internet-explorer/) wie Eigenschaften, Suche und Playback-Waiter

- Popups und Dialogfelder

- [Ausführen von einfachem JavaScript ohne Rückgabetyp](https://devblogs.microsoft.com/devops/introducing-javascript-execution-on-internetexplorer-and-crossbrowser-in-coded-ui-test/)

- Flexibilität der Suche (mithilfe der intelligenten Übereinstimmung) und [Leistungsverbesserungen](https://devblogs.microsoft.com/devops/guidelines-on-improving-performance-of-coded-ui-test-playback/)

## <a name="why-should-i-use-coded-ui-tests-across-multiple-web-browser-types"></a>Warum sollte ich Tests der programmierten UI in mehreren Webbrowsertypen durchführen?

Durch das Testen der Webanwendung in verschiedenen Webbrowsertypen können Sie die UI-Benutzerfreundlichkeit besser für Benutzer emulieren, die möglicherweise andere Browser verwenden. Zum Beispiel könnte die Anwendung Steuerelemente oder Code in Internet Explorer enthalten, die nicht mit anderen Webbrowsern kompatibel sind. Indem Sie Coded UI-Tests mit anderen Browsern ausführen, können Sie Probleme erkennen und korrigieren, bevor sich diese auf Ihre Kunden auswirken.

## <a name="how-do-i-record-and-play-back-coded-ui-tests-on-web-applications-using-the-supported-web-browsers"></a>Wie kann ich Tests der programmierten UI zu Webanwendungen, in denen die unterstützten Webbrowser verwendet werden, aufzeichnen und wiedergeben?

**Aufzeichnung:** Sie müssen den Coded UI-Test-Generator verwenden, um den Webanwendungstest mit Internet Explorer aufzuzeichnen. Optional können Sie den getesteten Steuerelementen Validierungscode und benutzerdefinierten Code mit einem vordefinierten Satz von Eigenschaften hinzufügen, wie Sie dies normalerweise für Tests der programmierten UI tun. Weitere Informationen finden Sie unter [Verwenden von Benutzeroberflächenautomatisierung zum Testen des Codes](../test/use-ui-automation-to-test-your-code.md).

> [!NOTE]
> Tests der programmierten UI können nicht mit den Browsern Google Chrome oder Mozilla Firefox aufgezeichnet werden.

**Wiedergabe mit Internet Explorer:** Wird kein Browser explizit angegeben, werden Tests standardmäßig in Internet Explorer ausgeführt. Sie können den zu verwendenden Browser explizit angeben, indem Sie die **BrowserWindow.CurrentBrowser**-Eigenschaft im Testcode festlegen. Zur Verwendung von Internet Explorer sollte diese Eigenschaft auf **IE** oder **Internet Explorer** festgelegt werden.

**Wiedergabe mit anderen Webbrowsern als Internet Explorer:** Ändern Sie die Eigenschaft „BrowserWindow.CurrentBrowser“ im Testcode auf **Firefox** oder **Chrome** zur Wiedergabe mit anderen Webbrowsern als Internet Explorer.

Um Tests auf Nicht-IE-Webbrowser wiederzugeben, müssen Sie die **Selenium-Komponenten für browserübergreifende Coded UI-Tests**.

### <a name="install-selenium-components"></a>Installieren von Selenium-Komponenten

::: moniker range="vs-2017"

1. Wählen Sie im Menü **Tools****Erweiterungen und Updates** aus.

2. Suchen Sie im Dialogfeld **Erweiterungen und Updates** nach `Selenium components for Cross Browser Testing`.

::: moniker-end

::: moniker range=">=vs-2019"

1. Wählen Sie im Menü **Erweiterungen** die Option **Erweiterungen verwalten** aus.

2. Suchen Sie im Dialogfeld **Erweiterungen verwalten** nach `Selenium components for Cross Browser Testing`.

::: moniker-end

3. Heben Sie die Erweiterung hervor, und wählen Sie **Herunterladen** aus.

    > [!TIP]
    > Sie können die Selenium-Komponenten für browserübergreifende Coded UI-Tests [hier](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting) herunterladen.

Weitere Informationen zum Erstellen und Verwenden von Tests der programmierten UI finden Sie unter [Erstellen von Tests der programmierten UI](../test/use-ui-automation-to-test-your-code.md).

### <a name="enable-debugging"></a>Aktivieren des Debuggings

Um das Debuggen der Webanwendung zu aktivieren, müssen Sie die folgenden Konfigurationsoptionen ausführen:

1. Nur meinen Code aktivieren:

    1. Klicken Sie im Menü **Tools** auf **Optionen**, und wählen Sie dann **Debuggen** aus.

    2. Wählen Sie **Nur meinen Code aktivieren** aus.

2. Deaktivieren der CLR-Ausnahmen:

    1. Wählen Sie im Menü **Debuggen** die Option **Ausnahmen** aus.

    2. Deaktivieren Sie in den **Common Language Runtime-Ausnahmen** die Option **Vom Benutzercode unbehandelt**.

Wenn die Option zum Ändern von `BrowserWindow.CurrentBrowser` im Test der programmierten UI nicht angezeigt wird, kann es sein, dass Sie eine Version von Visual Studio verwenden, die Tests der programmierten UI mit verschiedenen Browsern nicht unterstützt. Sie müssen Visual Studio Enterprise Edition verwenden, um solche Tests der programmierten UI verwenden zu können.

Im Folgenden finden Sie weitere wichtige Informationen:

- Der Webbrowser Apple Safari wird nicht unterstützt.

- Die Aktion zum Starten des Webbrowsers muss Teil des Coded UI-Tests sein.

   Wenn Sie einen Webbrowser bereits geöffnet haben und Schritte darin ausführen möchten, schlägt die Wiedergabe fehl, sofern Sie nicht Internet Explorer verwenden. Eine bewährte Methode ist daher, den Start des Webbrowsers in die Tests der programmierten UI einzubinden.

- Das Automatisieren von browserspezifischen UI-Aktionen, wie Maximieren, Minimieren und Wiederherstellen wird nicht unterstützt.

## <a name="tips"></a>Tipps

Sie können die Ausgabe so konfigurieren, dass Screenshots in den Coded UI-Protokollen enthalten sind. Hierzu müssen einige Konfigurationseinstellungen in der Datei *QTAgent32.exe.config* festgelegt werden. Standardmäßig wird diese Datei an folgendem Speicherort installiert:

*%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*

Legen Sie die folgenden Werte fest:

- `EqtTraceLevel` im Abschnitt `system.diagnostics`.

- `<add name="EqtTraceLevel" value="4" />`

   Durch Festlegen des Werts auf 3 oder höher werden für jede Aktion Screenshots aufgezeichnet. Wenn der Wert auf 1 oder 2 festgelegt ist, werden Screenshots nur für Fehleraktionen aufgezeichnet.

Weitere Informationen finden Sie unter [Analysieren von Tests der programmierten UI mithilfe der Testprotokolle der programmierten UI](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).

## <a name="video-resources"></a>Videoressourcen

[Record on IE and playback everywhere (Aufzeichnen mit IE und unabhängige Wiedergabe)](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!183&authkey=!ANqaLtCZbtJrImU)

[Author cross browser tests with coded UI test builder (Erstellen von browserübergreifenden Tests mit dem Coded UI-Test-Generator)](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!184&authkey=!AKG8CSow_qmeTq8)

[Erstellen von browserübergreifenden Tests mit einfacher Handcodierung ohne UI-Zuordnung](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!186&authkey=!AJaEvxJnsefyAT4)

[Sequenzielles Ausführen von browserübergreifenden Tests auf mehreren Browsern](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!187&authkey=!ADI8eCQkxHnpOR8)

[Beheben von Fehlern in browserübergreifenden Tests](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!182&authkey=!AEpS48i295B49FI)

## <a name="see-also"></a>Siehe auch

- [Verwenden der Benutzeroberflächenautomatisierung zum Testen des Codes](../test/use-ui-automation-to-test-your-code.md)
- [Unterstützte Konfigurationen und Plattformen für Tests der programmierten UI und Aktionsaufzeichnungen](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [Analysieren von Tests der programmierten UI mithilfe der Testprotokolle der programmierten UI](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md)
