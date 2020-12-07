---
title: Testtools
description: Hier erfahren Sie, wie Visual Studio-Testtools Sie und Ihr Team dabei unterstützen können, hochwertigen Code zu entwickeln und diesen Standard einzuhalten.
ms.custom: SEO-VS-2020
ms.date: 03/16/2018
ms.topic: conceptual
helpviewer_keywords:
- testing tools [Visual Studio]
- unit tests [Visual Studio]
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: f5eff2257988a4210e7f4cd8a8a37c66c57c185d
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2020
ms.locfileid: "96328690"
---
# <a name="first-look-at-testing-tools-in-visual-studio"></a>Einführung zu Testtools in Visual Studio

Die Visual Studio-Testtools können Sie und Ihr Team dabei unterstützen, hochwertigen Code zu entwickeln und diesen Standard einzuhalten.

> [!NOTE]
> Komponententests sind in allen Editionen von Visual Studio verfügbar. Andere Testtools wie Live Unit Testing, IntelliTest und Tests der programmierten UI sind nur in Visual Studio Enterprise verfügbar. Weitere Informationen zu den Editionen finden Sie unter [Visual Studio 2017-IDEs im Vergleich](https://visualstudio.microsoft.com/vs/compare/).

## <a name="test-explorer"></a>Test-Explorer

Das Fenster **Test-Explorer** hilft Entwicklern beim Erstellen, Verwalten und Ausführen von Komponententests. Sie können entweder das Microsoft-Komponententest-Framework oder ein Drittanbieter- oder Open-Source-Framework verwenden.

::: moniker range="vs-2017"
![Visual Studio Team Explorer](media/devtest-testexplorer.png)
::: moniker-end

::: moniker range="vs-2019"
![Visual Studio Test Explorer 16.2](media/vs-2019/test-explorer-16-2.PNG)
::: moniker-end

* [Erste Schritte mit Unittests](unit-test-your-code.md)
* [Ausführen von Komponententests mit dem Test-Explorer](run-unit-tests-with-test-explorer.md)
* [Häufig gestellte Fragen zum Test-Explorer](test-explorer-faq.md)
* [Installieren von Frameworks für Komponententests von Drittanbietern](install-third-party-unit-test-frameworks.md)

Visual Studio kann auch erweitert werden und ermöglicht Kompontenentestadapter von Drittanbietern wie NUnit und xUnit.net. Zusätzlich geht die Codeklonfunktion mit der Bereitstellung hochwertiger Software einher. Mit ihr können Sie Blöcke semantisch ähnlichen Codes identifizieren, die Kandidaten für gängige Fehlerbehebungen und Refactoring sein können.

![Integrationspakete von Drittanbietern](media/devtest-thirdparty.png)

## <a name="live-unit-testing"></a>Live Unit Testing

[Live Unit Testing](../test/live-unit-testing.md) führt automatisch Komponententests im Hintergrund aus und stellt die Code Coverage und die Testergebnisse im Code-Editor von Visual Studio grafisch dar.

## <a name="intellitest"></a>IntelliTest

IntelliTest generiert automatisch Komponententests und Testdaten für verwalteten Code. Mit IntelliTest wird die Abdeckung verbessert und der Aufwand zum Erstellen und Verwalten von Komponententests für neuen oder vorhandenen Code drastisch verringert.

![IntelliTest im Einsatz](media/devtest-intellitest.png)

* [Generieren von Komponententests für Code mit IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [IntelliTest – One Test to rule them all (IntelliTest – Ein Test für alle)](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/)
* [IntelliTest reference manual (IntelliTest-Referenzhandbuch)](intellitest-manual/index.md)

## <a name="code-coverage"></a>Codeabdeckung

Die [Code Coverage](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) ermittelt, wie groß der Anteil des Projektcodes ist, der in codierten Tests wie Komponententests tatsächlich getestet wird. Um sich effektiv vor Fehlern zu schützen, sollten Sie die Tests für den Großteil Ihres Codes ausführen bzw. diesen „abdecken“.

Die Code Coverage-Analyse kann sowohl in verwaltetem als auch in nicht verwaltetem (nativem) Code angewendet werden.

Sie sollten die Codeabdeckung verwenden, wenn Sie Testmethoden mit dem Test-Explorer ausführen. In der Ergebnistabelle wird der Prozentsatz des Codes angegeben, der in den einzelnen Assemblys, Klassen und Methoden ausgeführt wurde. Außerdem wird im Quellcode-Editor angezeigt, welcher Code getestet wurde.

* [Bestimmen des Umfangs des zu testenden Codes mithilfe von Code Coverage](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Unittest, Code Coverage und Codeklonanalyse mit Visual Studio (Lab)](https://www.boost.org/doc/libs/1_71_0/libs/test/doc/html/index.html)
* [Anpassen der Code Coverage-Analyse](customizing-code-coverage-analysis.md)

## <a name="microsoft-fakes"></a>Microsoft Fakes

Mit [Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md) isolieren Sie den zu testenden Code, indem Sie andere Teile der Anwendung durch Stubs oder Shims ersetzen.

## <a name="user-interface-testing-with-coded-ui-and-selenium"></a>Testen der Benutzeroberfläche mit programmierter UI und Selenium

Tests für programmierte UI bieten die Möglichkeit, vollautomatisierte Tests zu erstellen, um die Funktionalität und das Verhalten der Benutzeroberfläche Ihrer Anwendung zu überprüfen. Sie können Benutzeroberflächentests für eine Vielzahl von Technologien automatisieren, so z.B. für XAML-basierte UWP-Apps, Browser-Apps und SharePoint-Apps.

Egal, ob Sie sich für branchenführende Tests für programmierte UI oder für generische, browserbasierte UI-Tests mit Selenium entscheiden: Visual Studio stellt Ihnen alle Tools bereit, die Sie benötigen.

![Benutzeroberflächentests mit programmierter UI](media/devtest-codeduitest.png)

* [Verwenden der Benutzeroberflächenautomatisierung zum Testen des Codes](use-ui-automation-to-test-your-code.md)
* [Erstellen, Bearbeiten und Verwalten von Tests der programmierten UI](walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
* [Testen von UWP-Apps mit Tests der programmierten UI](test-uwp-app-with-coded-ui-test.md)
* [Introduction to Creating Coded UI Tests with Visual Studio Enterprise (Einführung in die Erstellung von Tests der programmierter UI mit Visual Studio Enterprise)](https://www.boost.org/doc/libs/1_71_0/libs/test/doc/html/index.html)

## <a name="load-testing"></a>Auslastungstests

[Auslastungstests](../test/quickstart-create-a-load-test-project.md) simulieren die Auslastung einer Serveranwendung durch Ausführen von Komponententests und Webleistungstests.

## <a name="related-scenarios"></a>Ähnliche Szenarios

* [Exploratory & Manual Testing (Azure Test Plans) (Explorative und manuelle Tests (Azure Test Plans))](/azure/devops/test/index?view=vsts&preserve-view=true)
* [Load testing (Azure Test Plans) (Auslastungstest (Azure Test Plans))](/azure/devops/test/load-test/index?view=vsts&preserve-view=true)
* [Continuous testing (Azure Test Plans) (Fortlaufende Tests (Azure Test Plans))](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts&preserve-view=true)
* [Codeanalysetools](../code-quality/code-analysis-for-managed-code-overview.md)
