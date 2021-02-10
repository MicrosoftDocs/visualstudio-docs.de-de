---
title: Exemplarische Vorgehensweise für die testgesteuerte Entwicklung
description: Hier erfahren Sie, wie Sie eine getestete Methode unter Verwendung des Microsoft-Testframeworks, das unkompliziert an andere Sprachen oder Testframeworks wie NUnit angepasst werden kann, in C# entwickeln.
ms.custom: SEO-VS-2020
ms.date: 07/24/2019
ms.topic: conceptual
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 56bfe2b00efc4af71ca562672ad01423778edecd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943730"
---
# <a name="walkthrough-test-driven-development-using-test-explorer"></a>Exemplarische Vorgehensweise: Testgesteuerte Entwicklung mit dem Test-Explorer

Erstellen Sie Komponententests, damit Ihr Code während inkrementellen Codeänderungen ordnungsgemäß funktioniert. Es gibt mehrere Frameworks, die Sie nutzen können, um Komponententests zu schreiben, darunter auch einige von Drittanbietern. Einige Testframeworks wurden speziell zum Testen in verschiedenen Sprachen oder Plattformen entwickelt. Der Test-Explorer stellt eine zentrale Oberfläche für Komponententests in einem dieser Frameworks bereit. Weitere Informationen zum **Test-Explorers** finden Sie unter [Ausführen von Komponententests mit dem Test-Explorer](run-unit-tests-with-test-explorer.md) und [Visual Studio-Test-Explorer – häufig gestellte Fragen](test-explorer-faq.md).

In dieser exemplarische Vorgehensweise wird veranschaulicht, wie eine getestete Methode in C# mithilfe des Microsoft-Testframeworks (MSTest) entwickelt wird. Sie können es für andere Sprachen und andere Testframeworks wie NUnit anpassen. Weitere Informationen finden Sie unter [Installieren von Frameworks für Komponententests von Drittanbietern](install-third-party-unit-test-frameworks.md).

## <a name="create-a-test-and-generate-code"></a>Erstellen eines Tests und Generieren von Code

1. Erstellen Sie ein C#-Projekt für eine **Klassenbibliothek (.NET Standard)**. Dieses Projekt enthält den Code, den Sie testen möchten. Geben Sie dem Projekt den Namen **MyMath**.

2. Fügen Sie in derselben Projektmappe ein neues **MSTest-Testprojekt (.NET Core)** hinzu. Geben Sie dem Testprojekt den Namen **MathTests**.

   ![Neue Code- und Testprojekte](../test/media/test-driven-development-ide.png)

3. Schreiben Sie eine einfache Testmethode, die das Ergebnis überprüft, das für eine bestimmte Eingabe abgerufen wurde. Fügen Sie der `UnitTest1`-Klasse den folgenden Code hinzu:

   ```csharp
   [TestMethod]
   public void BasicRooterTest()
   {
     // Create an instance to test:
     Rooter rooter = new Rooter();
     // Define a test input and output value:
     double expectedResult = 2.0;
     double input = expectedResult * expectedResult;
     // Run the method under test:
     double actualResult = rooter.SquareRoot(input);
     // Verify the result:
     Assert.AreEqual(expectedResult, actualResult, delta: expectedResult / 100);
   }
   ```

4. Generieren Sie einen Typ aus dem Testcode.

   1. Platzieren Sie den Cursor auf `Rooter`, und wählen Sie dann über das Glühbirnenmenü **Typ „Rooter“ generieren** > **Neuen Typ generieren** aus.

      ![Schnellaktion: neuen Typ generieren](media/test-driven-development-generate-new-type.png)

   2. Legen Sie im Dialogfeld **Typ generieren** das **Projekt** auf **MyMath** (das Klassenbibliotheksprojekt) fest, und klicken Sie auf **OK**.

      ![Dialogfeld „Typ generieren“ in Visual Studio 2019](media/test-driven-development-generate-type-dialog.png)

5. Generieren Sie eine Methode aus dem Testcode. Platzieren Sie den Cursor auf `SquareRoot`, und wählen Sie dann über das Glühbirnenmenü **Methode „Rooter.SquareRoot“ generieren** aus.

6. Führen Sie den Komponententest aus.

   1. Klicken Sie im Menü **Test** auf **Fenster** > **Test-Explorer**, um den **Test-Explorer** zu öffnen.

   2. Klicken Sie im **Test-Explorer** auf **Alle ausführen**, um den Test auszuführen.

   Die Projektmappe wird erstellt, und der Test wird ausgeführt und schlägt fehl.

7. Wählen Sie den Namen des Tests aus.

   Die Details des Tests werden im Bereich **Zusammenfassung der Testdetails** angezeigt.

   ![Zusammenfassung der Testdetails im Test-Explorer](media/test-driven-development-test-detail-summary.png)

8. Klicken Sie auf den obersten Link unter **Stapelüberwachung**, um zu der Position zu springen, an der der Test fehlgeschlagen ist.

Sie haben jetzt einen Test und einen Stub erstellt, die Sie ändern können, damit der Test erfolgreich verläuft.

## <a name="verify-a-code-change"></a>Überprüfen einer Codeänderung

1. Verbessern Sie in der Datei *Class1.cs* den Code von `SquareRoot`:

    ```csharp
    public double SquareRoot(double input)
    {
        return input / 2;
    }
    ```

2. Wählen Sie im **Test-Explorer** die Option **Alle ausführen** aus.

   Die Projektmappe wird erstellt, und der Test wird erfolgreich ausgeführt.

   ![Erfolgreicher Test im Test-Explorer](../test/media/test-driven-development-passed-test.png)

## <a name="extend-the-range-of-inputs"></a>Erweitern des Eingabebereichs

Sie können die Wahrscheinlichkeit erhöhen, dass Ihr Code in allen Fällen funktioniert, indem Sie Tests hinzufügen, die einen größeren Bereich an Eingabewerten testen.

> [!TIP]
> Vermeiden Sie, vorhandene erfolgreiche Tests zu ändern. Fügen Sie stattdessen lieber neue Tests hinzu. Ändern Sie vorhandene Tests nur, wenn sich die Benutzeranforderungen ändern. Dieses Vorgehen hilft sicherzustellen, dass durch die Erweiterung des Codes keine vorhandene Funktionalität verloren geht.

1. Fügen Sie in der Testklasse den folgenden Test hinzu, der einen Bereich von Eingabewerten testet:

    ```csharp
    [TestMethod]
    public void RooterValueRange()
    {
        // Create an instance to test.
        Rooter rooter = new Rooter();

        // Try a range of values.
        for (double expected = 1e-8; expected < 1e+8; expected *= 3.2)
        {
            RooterOneValue(rooter, expected);
        }
    }

    private void RooterOneValue(Rooter rooter, double expectedResult)
    {
        double input = expectedResult * expectedResult;
        double actualResult = rooter.SquareRoot(input);
        Assert.AreEqual(expectedResult, actualResult, delta: expectedResult / 1000);
    }
    ```

2. Wählen Sie im **Test-Explorer** die Option **Alle ausführen** aus.

   Der neue Test schlägt fehl, obwohl der erste Test weiterhin erfolgreich verläuft. Sie können die Fehlerquelle ermitteln, indem Sie den fehlgeschlagenen Test auswählen und die Details im Bereich **Zusammenfassung der Testdetails** anzeigen.

3. Überprüfen Sie die zu testende Methode, um zu sehen, was falsch sein könnte. Ändern Sie den Code von `SquareRoot` folgendermaßen:

    ```csharp
    public double SquareRoot(double input)
    {
      double result = input;
      double previousResult = -input;
      while (Math.Abs(previousResult - result) > result / 1000)
      {
        previousResult = result;
        result = result - (result * result - input) / (2 * result);
      }
      return result;
    }
    ```

4. Wählen Sie im **Test-Explorer** die Option **Alle ausführen** aus.

   Beide Tests sind nun erfolgreich.

## <a name="add-tests-for-exceptional-cases"></a>Hinzufügen von Tests für Sonderfälle

1. Fügen Sie einen neuen Test für negative Eingaben hinzu:

    ```csharp
    [TestMethod]
    public void RooterTestNegativeInputx()
    {
        Rooter rooter = new Rooter();
        try
        {
            rooter.SquareRoot(-10);
        }
        catch (System.ArgumentOutOfRangeException)
        {
            return;
        }
        Assert.Fail();
    }
    ```

2. Wählen Sie im **Test-Explorer** die Option **Alle ausführen** aus.

   Die zu testende Methode bildet eine Schleife und muss manuell abgebrochen werden.

3. Klicken Sie auf der Symbolleiste des **Test-Explorers** auf **Abbrechen**.

   Die Ausführung des Tests wird beendet.

4. Korrigieren Sie den Code von `SquareRoot`, indem Sie folgende `if`-Anweisung am Anfang der Methode hinzufügen:

    ```csharp
    public double SquareRoot(double input)
    {
        if (input <= 0.0)
        {
            throw new ArgumentOutOfRangeException();
        }
        ...
    ```

5. Wählen Sie im **Test-Explorer** die Option **Alle ausführen** aus.

   Alle Tests sind erfolgreich.

## <a name="refactor-the-code-under-test"></a>Umgestalten des zu testenden Codes

Führen Sie ein Refactoring für den Code durch, ohne die Tests zu ändern.

> [!TIP]
> Ein *Refactoring* ist eine Änderung, die vorgenommen wird, damit der Code besser funktioniert oder verständlicher wird. Eine Umgestaltung sieht nicht vor, das Verhalten des Codes zu ändern. Deshalb werden die Tests nicht geändert.
>
> Es wird empfohlen, die Schritte der Umgestaltung separat von den Schritten auszuführen, die die Funktionalität erweitern. Wenn Sie die Tests nicht ändern, können Sie sichergehen, dass während der Umgestaltung nicht versehentlich Fehler eingebaut wurden.

1. Ändern Sie die Zeile, die `result` in der `SquareRoot`-Methode berechnet, folgendermaßen:

    ```csharp
    public double SquareRoot(double input)
    {
        if (input <= 0.0)
        {
            throw new ArgumentOutOfRangeException();
        }

        double result = input;
        double previousResult = -input;
        while (Math.Abs(previousResult - result) > result / 1000)
        {
            previousResult = result;
            result = (result + input / result) / 2;
            //was: result = result - (result * result - input) / (2*result);
        }
        return result;
    }
    ```

2. Klicken Sie auf **Alle ausführen**, und überprüfen Sie, ob alle Tests weiterhin erfolgreich ausgeführt werden.

   ![Drei erfolgreiche Tests im Test-Explorer](../test/media/test-driven-development-three-passed-tests.png)
