---
title: Komponententest für Code | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.assetid: c191de3e-3f3b-471e-b828-29ec24e80e2c
caps.latest.revision: 64
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7a8b9a4b52fce5fb838c12ccf057fd0e80619cd7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851261"
---
# <a name="unit-test-your-code"></a>Komponententest für Code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit Komponententests können Entwickler und Tester die Methoden der Klassen in [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)]-, [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)]- und [!INCLUDE[cpp_current_short](../includes/cpp-current-short-md.md)]-Projekten schnell auf logische Fehler überprüfen.

 Zu den Komponententest-Tools gehören:

1. **Test-Explorer.** Mit dem Test-Explorer können Sie Komponententests ausführen und deren Ergebnisse anzeigen. Der Test-Explorer erlaubt die Verwendung jedes Komponententest-Frameworks, auch Frameworks von Drittanbietern, die über einen Adapter für den Explorer verfügen.

2. **Microsoft-Komponententest-Framework für verwalteten Code.** Das Microsoft-Komponententest-Framework für verwalteten Code wird mit Visual Studio installiert und stellt ein Framework zum Testen von .NET-Code bereit.

3. **Microsoft-Komponententest-Framework für C++.** Das Microsoft-Komponententest-Framework für C++ wird mit Visual Studio installiert und stellt ein Framework zum Testen von nativem Code bereit.

4. **Codeabdeckungstools.** Sie können die Menge an Produktcode bestimmen, die Ihre Komponententests nach der Eingabe eines Befehls im Test-Explorer prüfen.

5. **Microsoft Fakes-Isolationsframework.** Das Microsoft Fakes-Isolationsframework kann Ersatzklassen und Methoden für Produktions- und Systemcode erstellen, der Abhängigkeiten im getesteten Code erstellt. Durch die Implementierung von Fakedelegaten für eine Funktion können Sie das Verhalten und die Ausgabe des Abhängigkeitsobjekts steuern.

   Sie können auch [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) verwenden, um Ihren .NET-Code zum Generieren von Testdaten und einer Sammlung von Komponententests zu untersuchen. Für jede Anweisung im Code wird eine Testeingabe generiert, die die betreffende Anweisung ausführt. Für jede bedingte Verzweigung im Code wird eine Fallanalyse ausgeführt.

## <a name="key-tasks"></a>Hauptaufgaben
 Lesen Sie folgende Themen, um Komponententests besser zu verstehen und sie zu erstellen:

|Aufgaben|Verwandte Themen|
|-----------|-----------------------|
|**Schnellstarts und exemplarische Vorgehensweisen:** Erfahren Sie in den folgenden Themen ausgehend von Codebeispielen, wie Komponententests in Visual Studio durchgeführt werden.|-   [Exemplarische Vorgehensweise: Erstellen und Ausführen von Komponenten Tests für verwalteten Code](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />-   [Schnellstart: Test gestützte Entwicklung mit dem Test-Explorer](../test/quick-start-test-driven-development-with-test-explorer.md)<br />-   [Hinzufügen von Komponententests zu vorhandenen C++-Anwendungen](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)<br />-   [Komponententests für nativen Code mit dem Test-Explorer](https://msdn.microsoft.com/8a09d6d8-3613-49d8-9ffe-11375ac4736c)|
|**Komponententest mit Test-Explorer:** Erfahren Sie, wie Sie Test-Explorer unterstützen kann, produktivere und effizientere Komponententests zu erstellen.|-   [Grundlagen zu Komponententests](../test/unit-test-basics.md)<br />-   [Erstellen eines Komponenten Testprojekts](../test/create-a-unit-test-project.md)<br />-   [Ausführen von Komponententests mit dem Test-Explorer](../test/run-unit-tests-with-test-explorer.md)<br />-   [Installieren von Frameworks für Komponententests von Drittanbietern](../test/install-third-party-unit-test-frameworks.md)<br />-   [Upgrade der Komponententests von Visual Studio 2010](https://msdn.microsoft.com/9bb75856-f68a-4de2-a084-b08a947a1172)|
|**Komponententests von verwaltetem Code:**|-   [Schreiben von Komponenten Tests für die .NET Framework mit dem Microsoft-Komponenten Test-Framework für verwalteten Code](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)|
|**Komponententests von C++-Code**|-   [Schreiben von Komponententests für C/C++ mit dem Microsoft-Komponenten Test-Framework für C++](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)|
|**Isolation von Komponententests**|-   [Isolieren von zu testenden Code mit Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)|
|**Verwenden Sie die Codeabdeckung, um zu identifizieren, welcher Teil des Projektcodes mit Komponententests getestet wird:** Erfahren Sie mehr über die Codeabdeckungsfunktion der [!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)]-Testtools.|-   [Verwenden der Codeabdeckung, um zu bestimmen, wie viel Code getestet wird](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|
|**Führen Sie die Belastungs- und Leistungsanalyse mithilfe von Auslastungstests für die Komponententests aus:** Sie können einen Auslastungstest erstellen und diesem die Komponententests hinzufügen, um die Leistungs- und Auslastungsprobleme in der Anwendung isolieren zu können. **Hinweis:**  Zum Erstellen und Verwenden von Auslastungstests ist Visual Studio Enterprise erforderlich.|-   [Erstellen und Bearbeiten von Auslastungstests](https://msdn.microsoft.com/e2985d15-60a7-4177-93b4-f986c2936337)<br />-   [Vorgehensweise: Hinzufügen von Webleistungstests und Komponententests zu einem Auslastungstestszenario](https://msdn.microsoft.com/03cc073e-9bdf-4530-ae46-504a51884594)<br />-   [Vorgehensweise: Entfernen von Webleistungstests und Komponententests aus einem Auslastungstestszenario](https://msdn.microsoft.com/3d6128d2-82b0-42fc-bda2-23a8aa03be07)|
|**Legen Sie Quality Gates fest und erzwingen Sie diese:** Sie können Quality Gates erstellen, um zu erzwingen, dass vor dem Einchecken von Code Tests ausgeführt werden. Auf diese Weise können Sie die Qualität des Codes sicherstellen.|-   [Festlegen und Erzwingen von Quality Gates](https://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)|
|**Erweitern Sie den Komponententesttyp:** Sie können den Tests Funktionen hinzufügen, die im Komponententest-Framework möglicherweise nicht enthalten sind. Sie können z. B. eine Testeigenschaft hinzufügen, die angibt, ob ein Test als normaler Benutzer ausgeführt werden soll. Sie können das Framework auch erweitern, indem Sie einer Methode Zeilenattribute hinzufügen und die Daten in dieser Zeile im Test verwenden.|Beispielcode zum Erweitern des Komponententestframeworks finden Sie auf der [Microsoft-Website](https://msdn.microsoft.com/vstudio/ff420671.aspx).|
|**Festlegen von Testoptionen:** Sie können beispielsweise angeben, an welchem Ort die Testergebnisse gespeichert werden.|[Konfigurieren von Komponententests mithilfe einer RUNSETTINGS-Datei](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|

## <a name="related-tasks"></a>Zugehörige Aufgaben
 [Prüfen von Testergebnissen in Microsoft Test Manager](https://msdn.microsoft.com/9fb3e429-78df-4fe2-89ed-0ad1db0738f4)

 Beschreibt Testergebnisse und verschiedene Arten, mit diesen zu arbeiten, darunter das Anzeigen, Speichern und Löschen dieser Ergebnisse.

 [Ausführen von System Tests mit Microsoft Visual Studio](https://msdn.microsoft.com/library/19fae5c4-5798-4c4c-b531-3e8f901b1130)

 Enthält Links zu Informationen zum Ausführen automatisierter Tests mithilfe von Visual Studio anstelle von [!INCLUDE[TCMext](../includes/tcmext-md.md)].

## <a name="reference"></a>Verweis
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting> Beschreibt den UnitTesting-Namespace, der Attribute, Ausnahmen, Bestätigungen und andere Klassen bereitstellt, die Komponententests unterstützen.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web> Beschreibt den UnitTesting. Web-Namespace, der den UnitTesting-Namespace durch Bereitstellen von Unterstützung für [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] und Webdienst-Komponententests erweitert.

## <a name="external-resources"></a>Externe Ressourcen

### <a name="videos"></a>Videos
 [Channel 9: Unit testing your Windows Store apps built using XAML (Durchführen von Komponententests für Ihre mit XAML erstellten Windows Store-Apps)](https://channel9.msdn.com/Events/BUILD/BUILD2011/TOOL-529T)

### <a name="forums"></a>Foren
 [Visual Studio-Komponententest](https://social.msdn.microsoft.com/Forums/en/vsunittest/threads)

### <a name="guidance"></a>Anleitungen
 [Tests für fortlaufende Übermittlung mit Visual Studio 2012 – Kapitel 2: Komponententests – Interne Tests](https://msdn.microsoft.com/library/jj159340.aspx)

### <a name="reference"></a>Verweis
 [Inhaltsverzeichnis für Komponententests](https://blogs.msdn.com/b/mathew_aniyan/archive/2012/05/17/content-index-for-unit-test.aspx)

## <a name="see-also"></a>Weitere Informationen
 [Verbessern der Code Qualität](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945) [Testen der Anwendung](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)
