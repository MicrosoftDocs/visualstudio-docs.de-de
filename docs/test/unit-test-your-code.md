---
title: Komponententesttools und -aufgaben
description: Hier erfahren Sie mehr über die Tools für Komponententests, die Entwicklern und Testern die Möglichkeit geben, schnell nach logischen Fehlern in Ihrem Code zu suchen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 718f5560176f287f237d54a89bd44c831c7f03ca
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962612"
---
# <a name="unit-test-tools-and-tasks"></a>Komponententesttools und -aufgaben

Mit Komponententests können Entwickler und Tester die Methoden der Klassen in C#-, Visual Basic- und C++-Projekten schnell auf logische Fehler überprüfen.

Zu den Komponententest-Tools gehören:

* **Test-Explorer**&mdash;Mit dem **Test-Explorer** führen Sie Komponententests aus und zeigen ihre Ergebnisse an. Dabei können Sie jedes Komponententest-Framework verwenden, auch Frameworks von Drittanbietern, das über einen Adapter für den **Test-Explorer** verfügt.

* **Microsoft-Komponententest-Framework für verwalteten Code**&mdash;Das Microsoft-Komponententest-Framework für verwalteten Code wird mit Visual Studio installiert und stellt ein Framework zum Testen von .NET-Code bereit.

* **Microsoft-Komponententest-Framework für C++** &mdash;Das Microsoft-Komponententest-Framework für C++ wird als Teil der Workload **Desktopentwicklung mit C++** installiert. Es stellt ein Framework zum Testen von nativem Code bereit. Google Test-, Boost.Test- und CTest-Frameworks sind ebenfalls integriert, und Adapter von Drittanbietern sind für zusätzliche Testframeworks verfügbar. Weitere Informationen finden Sie unter [Schreiben von Komponententests für C/C++ ](../test/writing-unit-tests-for-c-cpp.md).

* **Code Coverage-Tools**&mdash;Sie können die Menge an Produktcode bestimmen, die Ihre Komponententests nach der Eingabe eines Befehls im Test-Explorer prüfen.

* **Microsoft Fakes-Isolationsframework**: Das Microsoft Fakes-Isolationsframework kann Ersatzklassen und Methoden für den .NET-Code für die Produktion und das System erstellen, mit dem Abhängigkeiten im getesteten Code erstellt werden. Durch die Implementierung von Fakedelegaten für eine Funktion können Sie das Verhalten und die Ausgabe des Abhängigkeitsobjekts steuern.

Für .NET können Sie auch [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) verwenden, um Ihren Code zu untersuchen und Testdaten sowie eine Sammlung von Komponententests zu generieren. Für jede Anweisung im Code wird eine Testeingabe generiert, die die betreffende Anweisung ausführt. Für jede bedingte Verzweigung im Code wird eine Fallanalyse ausgeführt.

## <a name="key-tasks"></a>Hauptaufgaben

Lesen Sie folgende Artikel, um Komponententests besser zu verstehen und sie zu erstellen:

|Aufgaben|Verwandte Themen|
|-|-----------------------|
|**Schnellstarts und exemplarische Vorgehensweisen:** Erfahren Sie mehr über Komponententests in Visual Studio anhand von Codebeispielen.|- [Exemplarische Vorgehensweise: Erstellen und Ausführen von Komponententests für .NET-Code](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />- [Exemplarische Vorgehensweise: Testgesteuerte Entwicklung mit dem Test-Explorer](../test/quick-start-test-driven-development-with-test-explorer.md)<br />- [Vorgehensweise: Hinzufügen von Komponententests zu C++-Apps](../test/how-to-use-microsoft-test-framework-for-cpp.md)|
|**Komponententest mit Test-Explorer:** Erfahren Sie, wie Sie Test-Explorer unterstützen kann, produktivere und effizientere Komponententests zu erstellen.|- [Grundlagen zu Komponententest](../test/unit-test-basics.md)<br />- [Ein Komponententestprojekt erstellen](../test/create-a-unit-test-project.md)<br />- [Ausführen von Komponententests mit dem Test-Explorer](../test/run-unit-tests-with-test-explorer.md)<br />- [Installieren von Frameworks für Komponententests von Drittanbietern](../test/install-third-party-unit-test-frameworks.md)|
|**Komponententest von C++-Code**|- [Schreiben von Komponententests für C/C++](../test/writing-unit-tests-for-c-cpp.md)|
|**Verwenden Sie Code Coverage, um zu identifizieren, welcher Teil des Projektcodes getestet wird:** Erfahren Sie mehr über das Code Coverage-Feature der Visual Studio-Testtools.|- [Bestimmen des Umfangs des zu testenden Codes mithilfe von Code Coverage](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|
|**Isolation von Komponententests**|- [Isolieren von .NET-Code mithilfe von Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)|
|**Durchführen von Belastungs- und Leistungsanalysen mithilfe von Auslastungstests:** Erfahren Sie, wie Auslastungstests erstellt werden, um Leistungs- und Auslastungsprobleme in der Anwendung zu isolieren. (veraltet)|- [Schnellstart: Erstellen eines Auslastungstestprojekts](../test/quickstart-create-a-load-test-project.md)<br />- [Load testing (Azure Test Plans and TFS) (Auslastungstest (Azure Test Plans und TFS))](/azure/devops/test/load-test/index?view=vsts&preserve-view=true)|
|**Festlegen von Quality Gates:** Erfahren Sie, wie Quality Gates erstellt werden, um zu erzwingen, dass vor dem Einchecken oder Zusammenführen von Code Tests ausgeführt werden.|- [Check-In-Richtlinien (Azure Repos TFVC)](/azure/devops/repos/tfvc/add-check-policies?view=vsts&preserve-view=true)|
|**Festlegen von Testoptionen:** Erfahren Sie, wie Testoptionen konfiguriert werden, beispielsweise, wo Testergebnisse gespeichert werden.|[Konfigurieren von Komponententests mithilfe einer .runsettings-Datei](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|

## <a name="api-reference-documentation"></a>API-Referenzdokumentation

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting> beschreibt den UnitTesting-Namespace, der Attribute, Ausnahmen, Assert-Vorgänge und andere Klassen bereitstellt, die Komponententests unterstützen.
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web> beschreibt den UnitTesting.Web-Namespace, der den UnitTesting-Namespace durch die Unterstützung für ASP.NET- und Webdienst-Komponententests erweitert.

## <a name="see-also"></a>Siehe auch

- [Verbessern der Codequalität](../test/improve-code-quality.md)