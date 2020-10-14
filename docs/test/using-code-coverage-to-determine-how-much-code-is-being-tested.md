---
title: Code Coverage-Tests
ms.date: 07/23/2019
ms.topic: conceptual
helpviewer_keywords:
- code coverage
dev_langs:
- CSharp
- VB
- CPP
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2d1b51661d9fc9a5492d123bdacd6c49d241ed87
ms.sourcegitcommit: 3e05bd4bfac6f0b8b3534d8c013388f67e288651
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2020
ms.locfileid: "91959774"
---
# <a name="use-code-coverage-to-determine-how-much-code-is-being-tested"></a>Bestimmen des Umfangs des zu testenden Codes mithilfe von Code Coverage

Wenn Sie den Anteil des Projektcodes ermitteln möchten, der in codierten Tests wie Komponententests tatsächlich getestet wird, verwenden Sie die Code Coverage-Funktion von Visual Studio. Um sich effektiv vor Fehlern zu schützen, sollten Sie die Tests für den Großteil Ihres Codes ausführen bzw. diesen "abdecken".

Die Codeabdeckungsanalyse kann sowohl in verwaltetem (CLI) als auch in nicht verwaltetem (systemeigenen) Code angewendet werden.

Sie sollten die Codeabdeckung verwenden, wenn Sie Testmethoden mit dem Test-Explorer ausführen. In der Ergebnistabelle wird der Prozentsatz des Codes angegeben, der in den einzelnen Assemblys, Klassen und Methoden ausgeführt wurde. Außerdem wird im Quellcode-Editor angezeigt, welcher Code getestet wurde.

::: moniker range="vs-2017"

![Codeabdeckungsergebnisse mit Färbung](../test/media/codecoverage1.png)

::: moniker-end

## <a name="requirements"></a>Anforderungen

Das Code Coverage-Feature ist nur in der Visual Studio Enterprise-Edition verfügbar.

## <a name="analyze-code-coverage"></a>Analysieren von Code Coverage

::: moniker range="vs-2017"

1. Wählen Sie im Menü **Test** die Option **Code Coverage analysieren** aus.

::: moniker-end

::: moniker range=">=vs-2019"

1. Wählen Sie im Menü **Test** die Option **Code Coverage für alle Tests analysieren** aus.

   ![Menüoption „Code Coverage analysieren“ in VS 2019](../test/media/vs-2019/analyze-code-coverage.png)

   Sie können Code Coverage auch aus dem Test-Explorer-Toolfenster ausführen.

::: moniker-end

2. Wählen Sie nach der Ausführung der Tests im Fenster **Code Coverage-Ergebnisse** das ![Symbol „Code Coverage-Färbung anzeigen“](../test/media/codecoverage-showcoloringicon.png) **Code Coverage-Färbung anzeigen** aus. Der von Tests abgedeckte Code wird standardmäßig hellblau hervorgehoben.

   > [!TIP]
   > Zum Ändern der Farben oder zum Verwenden von Fettdruck wählen Sie **Extras** > **Optionen** > **Umgebung** > **Schriftarten und Farben** > **Einstellungen anzeigen für: Text-Editor** aus. Passen Sie unter **Elemente anzeigen** die Einstellungen der Elemente für „Coverage“ an, z. B. **Von Code Coverage nicht verwendeter Bereich**.
   >
   > ![Schriftarten und Farben für Code Coverage](media/vs-2019/coverage-fonts-and-colors.png)

3. Wenn die Ergebnisse eine niedrige Abdeckung anzeigen, untersuchen Sie, welche Teile des Codes nicht ausgeführt werden, und schreiben Sie weitere Tests, um diese abzudecken. Entwicklungsteams streben normalerweise eine Codeabdeckung von ca. 80 % an. In einigen Situationen ist eine geringere Abdeckung akzeptabel. Beispielsweise ist eine geringere Abdeckung akzeptabel, wenn ein Teil des Codes aus einer Standardvorlage generiert wird.

> [!TIP]
> - Deaktivieren Sie die Compileroptimierung.
> - Verwenden Sie ein Debugbuild, wenn Sie mit nicht verwaltetem (nativem) Code arbeiten.
> - Erstellen Sie PDB-Dateien (Symboldateien) für jede Assembly.

Sollten Sie nicht die erwarteten Ergebnisse erhalten, finden Sie weitere Informationen unter [Problembehandlung bei der Code Coverage](../test/troubleshooting-code-coverage.md).

Vergessen Sie nicht, die Code Coverage nach Aktualisierung des Codes erneut auszuführen. Abdeckungsergebnisse und Codefarbe werden nach Änderung des Codes oder der Ausführung von nicht automatisch aktualisiert.

## <a name="report-in-blocks-or-lines"></a>Berichterstellung in Blöcken oder in Zeilen

Die Codeabdeckung wird in *Blöcken* gezählt. Ein Block ist ein Stück Code mit genau einem Einstiegs- und Endpunkt.  Wenn die Ablaufsteuerung des Programms einen Block während eines Testlaufs durchläuft, wird dieser Block als abgedeckt gezählt. Wie oft der Block verwendet wird, hat keinen Einfluss auf das Ergebnis.

Die Ergebnisse können auch auf Zeilen bezogen angezeigt werden, wenn Sie in der Tabellenkopfzeile **Spalten hinzufügen/entfernen** auswählen. Manche Benutzer bevorzugen die Zählung in Zeilen, da die Prozentsätze genauer der Größe der Fragmente entsprechen, die im Quellcode angezeigt werden. Ein langer Block mit Berechnungen zählt als ein einzelner Block, selbst wenn er viele Zeilen einnimmt.

> [!TIP]
> Eine Codezeile kann mehr als einen Codeblock enthalten. Wenn dies der Fall ist und der Testlauf alle Codeblöcke in der Zeile trainiert, wird sie als eine Zeile gezählt. Wenn nur manche Codeblöcke in der Zeile ausgeführt werden, wird sie als Teilzeile gezählt.

## <a name="manage-code-coverage-results"></a>Verwalten von Code Coverage-Ergebnissen

Im Fenster **Code Coverage-Ergebnisse** wird normalerweise das Ergebnis der letzten Ausführung angezeigt. Die Ergebnisse ändern sich, wenn Sie die Testdaten ändern oder jeweils nur einige Tests ausführen.

Das Fenster "Codeabdeckung" kann auch zur Anzeige von vorherigen Ergebnissen oder von Ergebnissen verwendet werden, die über andere Computer abgerufen wurden.

Sie können die Ergebnisse aus mehreren Testläufen zusammenführen, zum Beispiel aus Testläufen, in denen unterschiedliche Testdaten verwendet werden.

- **Um ein vorheriges Resultset aufzurufen**, wählen Sie dieses aus dem Dropdownmenü aus. Das Menü enthält eine temporäre Liste, die gelöscht wird, wenn Sie eine neue Projektmappe öffnen.

- **Zum Aufrufen von Ergebnissen aus einer vorherigen Sitzung** müssen Sie auf **Code Coverage-Ergebnisse importieren** klicken, zum Ordner **TestResults** in Ihrer Projektmappe navigieren und eine *COVERAGE*-Datei importieren.

   Die Code Coverage-Färbung ist möglicherweise falsch, wenn der Quellcode nach Generieren der *COVERAGE*-Datei geändert wurde.

- **Um die Ergebnisse als Text lesbar zu machen**, wählen Sie **Codeabdeckungsergebnisse exportieren** aus. Dadurch wird eine lesbare *COVERAGEXML*-Datei generiert, die mit anderen Tools verarbeitet oder problemlos in einer E-Mail gesendet werden kann.

- **Wenn Sie Ergebnisse an eine andere Person senden möchten**, müssen Sie entweder eine *COVERAGE*-Datei oder eine exportierte *COVERAGEXML*-Datei senden. Die Datei kann dann importiert werden. Verfügt die andere Person über dieselbe Version des Quellcodes, kann sie die Abdeckungsfärbung sehen.

## <a name="merge-results-from-different-runs"></a>Zusammenführen von Ergebnissen aus verschiedenen Ausführungen

In einigen Situationen werden abhängig von den Testdaten andere Blöcke im Code verwendet. Daher sollten Sie die Ergebnisse aus verschiedenen Testläufen kombinieren.

Bei einem Test mit der Eingabe "2 " stellen Sie beispielsweise fest, dass 50 % einer bestimmten Funktion abgedeckt werden. Wenn Sie den Test ein zweites Mal mit der Eingabe „-2“ ausführen, sehen Sie in der Ansicht der Code Coverage-Färbung, dass die anderen 50 % der Funktion abgedeckt werden. Führen Sie nun die Ergebnisse aus den zwei Testläufen zusammen. Die Berichtsansicht und die Ansicht der Abdeckungsfärbung zeigen nun an, dass 100 % der Funktion ausgeführt wurden.

Verwenden Sie dazu ![Symbol für die Schaltfläche „Zusammenführen“ im Fenster „Code Coverage“](../test/media/codecoverage-mergeicon.png) **Code Coverage-Ergebnisse zusammenführen**. Sie können eine beliebige Kombinationen aus den letzten Testläufen oder aus importierten Ergebnissen auswählen. Wenn Sie exportierte Ergebnisse kombinieren möchten, müssen Sie diese zuerst importieren.

Speichern Sie die Ergebnisse eines Zusammenführungsvorgangs mithilfe der Option **Export Code Coverage Results** (Codeabdeckungsergebnisse exportieren).

### <a name="limitations-in-merging"></a>Einschränkungen beim Zusammenführen

- Wenn Sie Abdeckungsdaten aus verschiedenen Versionen desselben Codes zusammenführen, werden die Ergebnisse separat dargestellt und sind nicht kombiniert. Um vollständig kombinierte Ergebnisse zu erhalten, verwenden Sie denselben Build des Codes, und ändern Sie nur die Testdaten.

- Wenn Sie eine Ergebnisdatei zusammenführen, die exportiert und anschließend importiert wurde, können Sie die Ergebnisse nur nach Zeilen und nicht nach Blöcken anzeigen. Verwenden Sie den Befehl **Spalten hinzufügen/entfernen**, um die Zeilendaten anzuzeigen.

- Wenn Sie Ergebnisse aus Tests für ein ASP.NET-Projekt zusammenführen, werden die Ergebnisse für die separaten Tests angezeigt und sind nicht kombiniert. Dies gilt nur für ASP.NET-Artefakte selbst: Die Ergebnisse für alle anderen Assemblys werden kombiniert dargestellt.

## <a name="exclude-elements-from-the-code-coverage-results"></a>Ausschließen von Elementen aus den Code Coverage-Ergebnissen

Sie können bestimmte Elemente im Code aus den Abdeckungsergebnissen ausschließen, zum Beispiel, wenn der Code aus einer Textvorlage generiert wird. Fügen Sie das <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName>-Attribut zu einem der folgenden Codeelemente hinzu: Klasse, Struktur, Methode, Eigenschaft-Setter oder -Getter oder Ereignis.

> [!TIP]
> Durch das Ausschließen einer Klasse werden deren abgeleitete Klassen nicht ausgeschlossen.

Zum Beispiel:

```csharp
using System.Diagnostics.CodeAnalysis;
...
public class ExampleClass1
{
    [ExcludeFromCodeCoverage]
    void ExampleMethod() {...}

    [ExcludeFromCodeCoverage] // exclude property
    int ExampleProperty1
    { get {...} set{...}}

    int ExampleProperty2
    {
        get
        {
            ...
        }
        [ExcludeFromCodeCoverage] // exclude setter
        set
        {
            ...
        }
    }

}
[ExcludeFromCodeCoverage]
class ExampleClass2 { ... }
```

```vb
Imports System.Diagnostics.CodeAnalysis

Class ExampleClass1
    <ExcludeFromCodeCoverage()>
    Public Sub ExampleSub1()
        ...
    End Sub

    ' Exclude property
    < ExcludeFromCodeCoverage()>
    Property ExampleProperty1 As Integer
        ...
    End Property

    ' Exclude setter
    Property ExampleProperty2 As Integer
        Get
            ...
        End Get
        <ExcludeFromCodeCoverage()>
        Set(ByVal value As Integer)
            ...
        End Set
    End Property
End Class

<ExcludeFromCodeCoverage()>
Class ExampleClass2
...
End Class
```

```cpp
// A .cpp file compiled as managed (CLI) code.
using namespace System::Diagnostics::CodeAnalysis;
...
public ref class ExampleClass1
{
  public:
    [ExcludeFromCodeCoverage]
    void ExampleFunction1() { ... }

    [ExcludeFromCodeCoverage]
    property int ExampleProperty2 {...}

    property int ExampleProperty2 {
      int get() { ... }
     [ExcludeFromCodeCoverage]
      void set(int value) { ...  }
   }
}

[ExcludeFromCodeCoverage]
public ref class ExampleClass2
{ ... }
```

### <a name="exclude-elements-in-native-c-code"></a>Ausschließen von Elementen im nativen C++-Code

So schließen Sie nicht verwaltete (systemeigene) Elemente im C++-Code aus:

```cpp
#include <CodeCoverage\CodeCoverage.h>
...

// Exclusions must be compiled as unmanaged (native):
#pragma managed(push, off)

// Exclude a particular function:
ExcludeFromCodeCoverage(Exclusion1, L"MyNamespace::MyClass::MyFunction");

// Exclude all the functions in a particular class:
ExcludeFromCodeCoverage(Exclusion2, L"MyNamespace::MyClass2::*");

// Exclude all the functions generated from a particular template:
ExcludeFromCodeCoverage(Exclusion3, L"*::MyFunction<*>");

// Exclude all the code from a particular .cpp file:
ExcludeSourceFromCodeCoverage(Exclusion4, L"*\\unittest1.cpp");

// After setting exclusions, restore the previous managed/unmanaged state:
#pragma managed(pop)
```

Verwenden Sie folgende Makros:

`ExcludeFromCodeCoverage(` *ExclusionName* `, L"` *FunctionName* `");`

`ExcludeSourceFromCodeCoverage(` *ExclusionName* `, L"` *SourceFilePath* `");`

- *ExclusionName* ist ein eindeutiger Name.

- *FunctionName* ist ein vollqualifizierter Funktionsname. Er enthält möglicherweise Platzhalter. Um beispielsweise alle Funktionen einer Klasse auszuschließen, schreiben Sie `MyNamespace::MyClass::*`

- *SourceFilePath* ist der lokale oder UNC-Pfad einer CPP-Datei. Er enthält möglicherweise Platzhalter. Im folgenden Beispiel werden alle Dateien in einem bestimmten Verzeichnis ausgeschlossen: `\\MyComputer\Source\UnitTests\*.cpp`

- `#include <CodeCoverage\CodeCoverage.h>`

- Platzaufrufe zu den Ausschlussmakros im globalen Namespace, nicht innerhalb eines Namespace oder einer Klasse.

- Sie können die Ausschlüsse entweder in der Komponententestcodedatei oder in der Anwendungscodedatei platzieren.

- Die Ausschlüsse müssen als nicht verwalteter (systemeigener) Code kompiliert werden, indem Sie entweder die Compileroption festlegen oder `#pragma managed(off)` verwenden.

> [!NOTE]
> Um Funktionen in C++/CLI-Code auszuschließen, wenden Sie das Attribut `[System::Diagnostics::CodeAnalysis::ExcludeFromCodeCoverage]` auf die Funktion an. Dasselbe gilt für C#.

### <a name="include-or-exclude-additional-elements"></a>Ein- oder Ausschließen von zusätzlichen Elementen

Die Code Coverage-Analyse wird nur in Assemblys durchgeführt, die geladen wurden und für die im selben Verzeichnis eine *PDB*-Datei verfügbar ist, in dem auch die *DLL*- oder *EXE*-Datei enthalten ist. Daher können Sie in bestimmten Fällen die enthaltenen Assemblys erweitern, indem Sie Kopien der entsprechenden *PDB*-Dateien abrufen.

Sie können besser steuern, welche Assemblys und Elemente für die Code Coverage-Analyse ausgewählt werden, indem Sie eine *RUNSETTINGS*-Datei schreiben. Beispielsweise können Sie Assemblys bestimmter Arten ausschließen, ohne deren Klassen Attribute hinzuzufügen. Weitere Informationen finden Sie unter [Anpassen der Code Coverage-Analyse](../test/customizing-code-coverage-analysis.md).

## <a name="analyze-code-coverage-in-azure-pipelines"></a>Analysieren von Code Coverage in Azure Pipelines

Wenn Sie Code einchecken, werden Ihre Tests zusammen mit Tests von anderen Teammitgliedern auf dem Buildserver ausgeführt. Es ist hilfreich, die Code Coverage in Azure Pipelines zu analysieren, um das aktuellste und umfassendste Bild der Code Coverage für das gesamte Projekt zu erhalten. Dazu gehören auch automatisierte Systemtests und andere codierte Tests, die Sie normalerweise nicht auf Entwicklungscomputern ausführen. Weitere Informationen finden Sie unter [Run unit tests with your builds (Ausführen von Komponententests mit Ihren Builds)](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts&preserve-view=true).

## <a name="analyze-code-coverage-from-the-command-line"></a>Analysieren von Code Coverage über die Befehlszeile

Verwenden Sie *vstest.console.exe*, um Tests über die Befehlszeile auszuführen. Code Coverage ist eine Option des Hilfsprogramms *vstest.console.exe*.

1. Starten Sie die Developer-Eingabeaufforderung für Visual Studio:

   ::: moniker range="vs-2017"

   Wählen Sie im Windows **Startmenü** **Visual Studio 2017** > **Developer Command Prompt for VS 2017** (Eingabeaufforderung für Entwickler für VS 2017) aus.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   Wählen Sie im Windows **Startmenü** **Visual Studio 2019** > **Developer Command Prompt for VS 2019** (Eingabeaufforderung für Entwickler für VS 2019) aus.

   ::: moniker-end

2. Führen Sie an der Eingabeaufforderung folgenden Befehl aus:

   ```shell
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage
   ```

Weitere Informationen finden Sie unter [Befehlszeilenoptionen von „VSTest.Console.exe“](vstest-console-options.md).

## <a name="troubleshoot"></a>Problembehandlung

Wenn keine Code Coverage-Ergebnisse angezeigt werden, lesen Sie den Artikel [Problembehandlung bei der Code Coverage](../test/troubleshooting-code-coverage.md).

## <a name="see-also"></a>Siehe auch

- [Anpassen der Code Coverage-Analyse](../test/customizing-code-coverage-analysis.md)
- [Problembehandlung bei der Code Coverage](../test/troubleshooting-code-coverage.md)
- [Ausführen von Komponententests für Code](../test/unit-test-your-code.md)
