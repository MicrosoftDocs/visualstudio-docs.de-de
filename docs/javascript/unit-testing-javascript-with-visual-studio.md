---
title: Komponententests für JavaScript und TypeScript
description: Visual Studio bietet Unterstützung zum Durchführen von Komponententests für JavaScript- und TypeScript Code mithilfe der Node.js-Tools für Visual Studio.
ms.date: 07/06/2020
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: e10f9b628d1d9fbbdb2911977fe7e63b1a7b6d57
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957477"
---
# <a name="unit-testing-javascript-and-typescript-in-visual-studio"></a>Komponententests für JavaScript und TypeScript in Visual Studio

Mithilfe der Node.js-Tools für Visual Studio können Sie Komponententests mit gängigen JavaScript-Frameworks schreiben und ausführen, ohne zu einer Eingabeaufforderung wechseln zu müssen.

Folgende Frameworks werden unterstützt:
* Mocha ([mochajs.org](https://mochajs.org/))
* Jasmine ([Jasmine.github.io](https://jasmine.github.io/))
* Tape ([github.com/substack/tape](https://github.com/substack/tape))
* Jest ([jestjs.io](https://jestjs.io/))
* Export Runner (dieses Framework bezieht sich speziell auf Node.js-Tools für Visual Studio)

Wenn Ihr bevorzugtes Framework nicht unterstützt wird, finden Sie unter [Add support for a unit test framework (Hinzufügen der Unterstützung für ein Komponententest-Framework)](#addingFramework) Informationen zum Hinzufügen der Unterstützung.

## <a name="write-unit-tests"></a>Schreiben von Komponententests

Stellen Sie vor dem Hinzufügen von Komponententests zu Ihrem Projekt sicher, dass das Framework, das Sie verwenden möchten, lokal in Ihrem Projekt installiert ist. Mit dem [NPM-Paketinstallationsfenster](npm-package-management.md#npmInstallWindow) lässt sich das ganz einfach bewerkstelligen.

Vorzugsweise sollten Sie Komponententests hinzufügen, indem Sie in Ihrem Projekt einen *Testordner* erstellen und diesen Ordner in den Projekteigenschaften als Teststamm festlegen. Ferner müssen Sie das Testframework auswählen, das Sie verwenden möchten.

![Festlegen von Teststamm und Testframework](../javascript/media/unit-test-project-properties.png)

Über das Dialogfeld **Neues Element hinzufügen** können Sie Ihrem Projekt einfache leere Tests hinzufügen. JavaScript und TypeScript werden in einem Projekt unterstützt.

![Hinzufügen eines neuen Komponententests](../javascript/media/unit-test-add-new-item.png)

Verwenden Sie für einen Mocha-Komponententest folgenden Code:

```javascript
var assert = require('assert');

describe('Test Suite 1', function() {
    it('Test 1', function() {
        assert.ok(true, "This shouldn't fail");
    })

    it('Test 2', function() {
        assert.ok(1 === 1, "This shouldn't fail");
        assert.ok(false, "This should fail");
    })
})
```

Wenn Sie die Komponententestoptionen in den Projekteigenschaften nicht festgelegt haben, müssen Sie sicherstellen, dass für die Eigenschaft **Testframework** im Fenster **Eigenschaften** das richtige Testframework für Ihre Komponententestdateien festgelegt wurde. Dies geschieht automatisch durch die Vorlagen der Komponententestdatei.

![Testframework](../javascript/media/UnitTestsFrameworkMocha.png)

> [!Note]
> Die Komponententestoptionen haben Vorrang vor den Einstellungen für einzelne Dateien.

Nach dem Öffnen des Test-Explorers (wählen Sie **Test** > **Windows** > **Test-Explorer** aus), erkennt Visual Studio Tests und zeigt diese an. Wenn zunächst keine Tests angezeigt werden, erstellen Sie das Projekt neu, um die Liste zu aktualisieren.

![Test-Explorer](../javascript/media/UnitTestsDiscoveryMocha.png)

> [!NOTE]
> Verwenden Sie für TypeScript nicht die Optionen `outdir` und `outfile` in *tsconfig.json*, da der Test-Explorer Ihre Komponententests nicht finden würde.

## <a name="run-tests"></a>Tests durchführen

Tests können in Visual Studio oder über die Befehlszeile ausgeführt werden.

### <a name="run-tests-in-visual-studio"></a>Ausführen von Tests in Visual Studio

::: moniker range=">=vs-2019"
Sie können die Tests durchführen, indem Sie im Test-Explorer auf den Link **Alle ausführen** klicken. Alternativ können Sie Tests ausführen, indem Sie mindestens einen Test oder eine Gruppe auswählen, mit der rechten Maustaste klicken und im Kontextmenü auf **Ausführen** klicken. Tests werden im Hintergrund ausgeführt, und der Test-Explorer aktualisiert die Ergebnisse automatisch und zeigt diese an. Darüber hinaus können Sie auch ausgewählte Tests debuggen, indem Sie auf **Debuggen** klicken.
::: moniker-end
::: moniker range="vs-2017"
Sie können die Tests durchführen, indem Sie im Test-Explorer auf den Link **Alle ausführen** klicken. Alternativ können sie Tests ausführen, indem Sie mindestens einen Test oder eine Gruppe auswählen, mit der rechten Maustaste klicken und im Kontextmenü die Option **Ausgewählte Tests ausführen** auswählen. Tests werden im Hintergrund ausgeführt, und der Test-Explorer aktualisiert die Ergebnisse automatisch und zeigt diese an. Darüber hinaus können Sie auch ausgewählte Tests debuggen, indem Sie **Ausgewählte Tests debuggen** auswählen.
::: moniker-end

Für TypeScript werden Komponententests für den generierten JavaScript-Code ausgeführt.

> [!NOTE]
> In den meisten TypeScript-Szenarios können Sie einen Komponententest debuggen, indem Sie einen Haltepunkt im TypeScript-Code festlegen, mit der rechten Maustaste auf einen Test im Test-Explorer klicken und auf **Debuggen** klicken. In komplexeren Szenarios, wenn z. B. Quellzuordnungen verwendet werden, kann es schwierig sein, Haltepunkte im TypeScript-Code zu erreichen. Verwenden Sie zur Umgehung dieses Problems das Schlüsselwort `debugger`.

> [!NOTE]
> Die Profilerstellung bei Tests und Code Coverage wird derzeit nicht unterstützt.

### <a name="run-tests-from-the-command-line"></a>Ausführen von Tests über die Befehlszeile

Sie können die Tests über die [Developer-Eingabeaufforderung](/dotnet/framework/tools/developer-command-prompt-for-vs) für Visual Studio mithilfe des folgenden Befehls ausführen:

```
vstest.console.exe <path to project file>\NodejsConsoleApp23.njsproj /TestAdapterPath:<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter
```

Dieser Befehl erzeugt eine Ausgabe ähnlich der folgenden:

```
Microsoft (R) Test Execution Command Line Tool Version 15.5.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
Processing: NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js
  Creating TestCase:NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js::Test Suite 1 Test 1::mocha
  Creating TestCase:NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js::Test Suite 1 Test 2::mocha
Processing finished for framework of Mocha
Passed   Test Suite 1 Test 1
Standard Output Messages:
 Using default Mocha settings
 1..2
 ok 1 Test Suite 1 Test 1

Failed   Test Suite 1 Test 2
Standard Output Messages:
 not ok 1 Test Suite 1 Test 2
   AssertionError [ERR_ASSERTION]: This should fail
       at Context.<anonymous> (NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js:10:16)

Total tests: 2. Passed: 1. Failed: 1. Skipped: 0.
Test Run Failed.
Test execution time: 1.5731 Seconds
```

> [!NOTE]
> Wenn eine Fehlermeldung angezeigt wird, die besagt, dass *vstest.console.exe* nicht gefunden werden kann, prüfen Sie, ob Sie tatsächlich die Developer-Eingabeaufforderung und nicht nur eine gewöhnliche Eingabeaufforderung geöffnet haben.

## <a name="add-support-for-a-unit-test-framework"></a><a name="addingFramework"></a>Hinzufügen der Unterstützung für ein Komponententest-Framework

Sie können die Unterstützung für weitere Testframeworks hinzufügen, indem Sie die Erkennungs- und Ausführungslogik mit JavaScript implementieren. Hierzu fügen Sie einen Ordner mit dem Namen des Testframeworks an folgender Stelle hinzu:

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks`

Dieser Ordner muss eine JavaScript-Datei mit demselben Namen enthalten, die die folgenden beiden Funktionen exportiert:

* `find_tests`
* `run_tests`

Ein gutes Beispiel für die Implementierungen von `find_tests` und `run_tests` finden Sie in der Implementierung für das Mocha-Komponententestframework unter:

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks\mocha\mocha.js`

Verfügbare Testframeworks werden beim Start von Visual Studio ermittelt. Wenn ein Framework hinzugefügt wird, während Visual Studio ausgeführt wird, muss Visual Studio neu gestartet werden, damit das Framework erkannt wird. Wenn Sie an der Implementierung Änderungen vornehmen, müssen Sie jedoch keinen Neustart durchführen.

## <a name="unit-tests-in-other-project-types"></a>Komponententests in anderen Projekttypen
Beim Schreiben von Komponententests sind Sie nicht nur auf Ihre Node.js-Projekte beschränkt. Wenn Sie die Eigenschaften „TestFramework“ und „TestRoot“ zu einem C#- oder Visual Basic-Projekt hinzufügen, werden die Tests aufgelistet, und Sie können sie über das Fenster „Test-Explorer“ ausführen.

Klicken Sie dazu im Projektmappen-Explorer mit der rechten Maustaste auf den Projektknoten, klicken Sie auf **Projekt entladen**, und wählen Sie dann **Edit Project** (Projekt bearbeiten) aus. Fügen Sie anschließend in der Projektdatei die folgenden zwei Elemente zu einer Eigenschaftengruppe hinzu.

> [!NOTE]
> Stellen Sie sicher, dass für die Eigenschaftengruppe, zu der Sie die Elemente hinzufügen, keine Bedingung angegeben ist.
> Dies kann zu unerwartetem Verhalten führen.

```xml
<PropertyGroup>
    <JavaScriptTestRoot>tests\</JavaScriptTestRoot>
    <JavaScriptTestFramework>Tape</JavaScriptTestFramework>
</PropertyGroup>
```

Als Nächstes fügen Sie die Tests in den Teststammordner ein, den Sie angegeben haben, woraufhin sie im Fenster „Test-Explorer“ ausgeführt werden. Sollten sie anfänglich nicht angezeigt werden, müssen Sie das Projekt neu erstellen.

### <a name="unit-test-net-core-and-net-standard"></a>Komponententests in .NET Core und .NET Standard
Zusätzlich zu den oben genannten Eigenschaften müssen Sie auch das NuGet-Paket [Microsoft.JavaScript.UnitTest](https://www.nuget.org/packages/Microsoft.JavaScript.UnitTest/) installieren und die Eigenschaft festlegen:

```xml
<PropertyGroup>
    <GenerateProgramFile>false</GenerateProgramFile>
</PropertyGroup>
```

Einige Testframeworks erfordern möglicherweise zusätzliche npm-Pakete zur Testerkennung. Für „jest“ beispielsweise ist das npm-Paket „jest-editor-support“ erforderlich. Sehen Sie sich ggf. die Dokumentation zum jeweiligen Framework an.
