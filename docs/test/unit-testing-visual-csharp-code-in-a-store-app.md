---
title: Komponententests in Visual C#-Code
description: Hier lernen Sie, wie Sie Komponententests für eine C#-Klasse in einer UWP-App erstellen. Dieser Artikel veranschaulicht die testgesteuerte Entwicklung.
ms.custom: SEO-VS-2020
ms.date: 09/27/2019
ms.topic: conceptual
ms.author: mikejo
author: mikejo5000
manager: jmartens
ms.workload:
- uwp
ms.openlocfilehash: e0267fb31515d842f7c9b6591d412e454c803bdb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962547"
---
# <a name="unit-test-c-code"></a>Komponententest von C#-Code

In diesem Artikel wird eine Möglichkeit zum Erstellen von Komponententests für eine C#-Klasse in einer UWP-App beschrieben.

Die Klasse **Rooter** – die hier für den Test verwendet wird – implementiert eine Funktion, die den ungefähren Wert für die Quadratwurzel einer angegebenen Zahl berechnet.

Dieser Artikel veranschaulicht die *testgesteuerte Entwicklung*. Bei dieser Vorgehensweise schreiben Sie zuerst einen Test, der ein bestimmtes Verhalten in dem von Ihnen getesteten System überprüft. Anschließend schreiben Sie den Code, der im Test erfolgreich ist.

## <a name="create-the-solution-and-the-unit-test-project"></a>Erstellen Sie die Projektmappe und das Komponententestprojekt.

1. Wählen Sie im Menü **Datei** die Optionsfolge **Neu** > **Projekt** aus.

2. Suchen Sie die Projektvorlage **Leere App (universelles Windows)**, und wählen Sie sie aus.

3. Nennen Sie das Projekt **Maths**.

4. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Projektmappe, und wählen Sie dann **Hinzufügen** > **Neues Projekt** aus.

5. Suchen Sie die Projektvorlage **Komponententest-App (Universelles Windows)**, und wählen Sie sie aus.

6. Nennen Sie das Testprojekt **RooterTests**.

## <a name="verify-that-the-tests-run-in-test-explorer"></a>Stellen Sie sicher, dass die Tests im Test-Explorer ausgeführt werden.

1. Fügen Sie in der Datei *UnitTest.cs* in **TestMethod1** Testcode hinzu:

   ```csharp
   [TestMethod]
   public void TestMethod1()
   {
       Assert.AreEqual(0, 0);
   }
   ```

   Die <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> Klasse stellt mehrere statische Methoden zur Verfügung, mit denen Sie Ergebnisse in Testmethoden überprüfen können.

::: moniker range="vs-2017"

2. Klicken Sie im Menü **Test** auf **Alle Tests** > **ausführen**.

::: moniker-end

::: moniker range=">=vs-2019"

2. Klicken Sie im Menü **Test** auf **Alle Tests ausführen**.

::: moniker-end

   Das Testprojekt wird erstellt und ausgeführt. Gedulden Sie sich ein wenig, dieser Vorgang kann einige Zeit in Anspruch nehmen. Das Fenster **Test-Explorer** wird angezeigt, und der Test wird unter **Bestandene Tests** aufgeführt. Unten im Fenster im Bereich **Zusammenfassung** werden weitere Informationen zum ausgewählten Test angezeigt.

## <a name="add-the-rooter-class-to-the-maths-project"></a>Fügen Sie die Klasse "Rooter" zu dem Projekt "Mathematik" hinzu.

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt **Maths** und dann auf **Hinzufügen** > **Klasse**.

2. Geben Sie der Klassendatei den Namen *Rooter.cs*.

3. Fügen Sie der **Rooter**-Klassendatei *Rooter.cs* den folgenden Code hinzu:

   ```csharp
   public Rooter()
   {
   }

   // estimate the square root of a number
   public double SquareRoot(double x)
   {
       return 0.0;
   }
   ```

   Die **Rooter**-Klasse deklariert einen Konstruktor und die **SquareRoot**-Schätzmethode. Die **SquareRoot**-Methode ist nur eine minimale Implementierung, die gerade ausreicht, um die Grundstruktur des Testsetups zu testen.

4. Fügen Sie der **Rooter**-Klassendeklaration das Schlüsselwort `public` hinzu, sodass der Testcode darauf zugreifen kann.

   ```csharp
   public class Rooter
   ```

## <a name="add-a-project-reference"></a>Hinzufügen eines Projektverweises

1. Fügen Sie der Maths-App einen Verweis aus dem RooterTests-Projekt hinzu.

    1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt **RooterTests**, und wählen Sie anschließend **Hinzufügen** > **Verweis** aus.

    2. Erweitern Sie im Dialogfeld **Verweis hinzufügen - RooterTests** den Eintrag **Projektmappe**, und wählen Sie **Projekte** aus. Wählen Sie das Projekt **Maths** aus.

        ![Einen Verweis zum Projekt "Maths" hinzufügen](../test/media/ute_cs_windows_addreference.png)

2. Fügen Sie der Datei *UnitTest.cs* eine `using`-Anweisung hinzu:

    1. Öffnen Sie *UnitTest.cs*.

    2. Fügen Sie diesen Code unter der Zeile `using Microsoft.VisualStudio.TestTools.UnitTesting;` hinzu:

       ```csharp
       using Maths;
       ```

3. Fügen Sie einen Test hinzu, der die Funktion **Rooter** verwendet. Fügen Sie folgenden Code zu *UnitTest.cs* hinzu:

   ```csharp
   [TestMethod]
   public void BasicTest()
   {
       Maths.Rooter rooter = new Rooter();
       double expected = 0.0;
       double actual = rooter.SquareRoot(expected * expected);
       double tolerance = .001;
       Assert.AreEqual(expected, actual, tolerance);
   }
   ```

   Der neue Test wird im **Test-Explorer** im Knoten **Nicht ausgeführte Tests** angezeigt.

4. Um den Fehler „Die Nutzlast enthält mehrere Dateien mit dem gleichen Zielpfad“ zu vermeiden, erweitern Sie im **Projektmappen-Explorer** unterhalb des Projekts **Maths** den Knoten **Eigenschaften**, und löschen Sie die Datei *Default.rd.xml*.

::: moniker range="vs-2017"

6. Wählen Sie im **Test-Explorer** die Option **Alle ausführen** aus.

   Die Projektmappe wird erstellt, und die Tests werden erfolgreich ausgeführt.

   ![Grundlegender Test in Test-Explorer erfolgreich ausgeführt](../test/media/ute_cpp_testexplorer_basictest.png)

::: moniker-end

::: moniker range=">=vs-2019"

6. Wählen Sie im **Test-Explorer** die Option **Alle Tests ausführen** aus.

   Die Projektmappe wird erstellt, und die Tests werden erfolgreich ausgeführt.

   ![Grundlegender Test in Test-Explorer erfolgreich ausgeführt](../test/media/vs-2019/test-explorer-uwp-app.png)

::: moniker-end

Sie haben die Test- und App-Projekte eingerichtet und überprüft, ob Sie Tests ausführen können, die Funktionen im App-Projekt aufrufen. Jetzt können Sie beginnen, echte Tests und Code zu schreiben.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a>Die Tests iterativ steigern und erfolgreich abschließen

1. Fügen Sie einen neuen Test namens **RangeTest** hinzu:

   ```csharp
   [TestMethod]
   public void RangeTest()
   {
       Rooter rooter = new Rooter();
       for (double v = 1e-6; v < 1e6; v = v * 3.2)
       {
           double expected = v;
           double actual = rooter.SquareRoot(v*v);
           double tolerance = expected/1000;
           Assert.AreEqual(expected, actual, tolerance);
       }
   }
   ```

   > [!TIP]
   > Es wird empfohlen, keine Tests zu ändern, die erfolgreich abgeschlossen wurden. Fügen Sie stattdessen einen neuen Test hinzu.

2. Führen Sie den **RangeTest** aus, und vergewissern Sie sich, dass die Ausführung nicht erfolgreich ist.

   ![Fehler beim RangeTest](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

   > [!TIP]
   > Führen Sie einen Test sofort nach dem Schreiben aus, um sich zu vergewissern, dass er nicht erfolgreich ausgeführt wird. Dadurch können Sie vermeiden, dass Sie einen Test schreiben, bei dessen Ausführung nie ein Fehler auftritt.

3. Erweitern Sie den Code unter dem Test, damit der neue Test erfolgreich ist. Ändern Sie die **SquareRoot**-Funktion in *Rooter.cs* in Folgendes:

   ```csharp
   public double SquareRoot(double x)
   {
       double estimate = x;
       double diff = x;
       while (diff > estimate / 1000)
       {
           double previousEstimate = estimate;
           estimate = estimate - (estimate * estimate - x) / (2 * estimate);
           diff = Math.Abs(previousEstimate - estimate);
       }
       return estimate;
   }
   ```

::: moniker range="vs-2017"

4. Wählen Sie im **Test-Explorer** die Option **Alle ausführen** aus.

::: moniker-end

::: moniker range=">=vs-2019"

4. Wählen Sie im **Test-Explorer** die Option **Alle Tests ausführen** aus.

::: moniker-end

   Alle drei Tests sind jetzt erfolgreich.

> [!TIP]
> Entwickeln Sie Code, indem Sie währenddessen Tests hinzufügen. Stellen Sie sicher, dass alle Tests nach jeder Iteration erfolgreich sind.

## <a name="refactor-the-code"></a>Gestalten Sie den Code um.

In diesem Abschnitt gestalten Sie sowohl den App- als auch den Testcode um und führen die Tests erneut aus, um sicherzustellen, dass sie weiterhin erfolgreich sind.

### <a name="simplify-the-square-root-estimation"></a>Vereinfachen der Quadratwurzelschätzung

1. Vereinfachen Sie die zentrale Berechnung in der **SquareRoot**-Funktion, indem Sie nur eine einzige Codezeile wie folgt ändern:

    ```csharp
    // Old code
    //estimate = estimate - (estimate * estimate - x) / (2 * estimate);

    // New code
    estimate = (estimate + x/estimate) / 2.0;
    ```

2. Führen Sie alle Tests aus, um sich zu vergewissern, dass keine Regression eingebaut wurde. Alle Tests sollten erfolgreich sein.

> [!TIP]
> Mit einem stabilen Satz guter Komponententests haben Sie mehr Gewissheit, dass Sie beim Ändern des Codes keine Fehler eingeführt haben.

### <a name="eliminate-duplicated-code"></a>Eliminieren von dupliziertem Code

Der Nenner der Variablen *tolerance*, die an die <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>-Methode übergeben wird, wird durch die **RangeTest**-Methode hartcodiert. Wenn Sie zusätzliche Tests hinzufügen möchten, in denen die gleiche Toleranzberechnung zur Anwendung kommt, lässt sich der Code schwerer verwalten, wenn ein hartcodierter Wert an mehreren Speicherorten verwendet wird.

1. Fügen Sie der **UnitTest1**-Klasse eine private Hilfsmethode hinzu, um den Toleranzwert zu berechnen, und rufen Sie anschließend diese Methode aus **RangeTest** auf.

    ```csharp
    private double ToleranceHelper(double expected)
    {
        return expected / 1000;
    }

    ...

    [TestMethod]
    public void RangeTest()
    {
        ...
        // Old code
        // double tolerance = expected/1000;

        // New code
        double tolerance = ToleranceHelper(expected);
    }
    ...
    ```

2. Führen Sie **RangeTest** aus, um sicherzustellen, dass der Test weiterhin erfolgreich ist.

> [!TIP]
> Wenn Sie einer Testklasse eine Hilfsmethode hinzufügen, die nicht im **Test-Explorer** angezeigt werden soll, fügen Sie der Methode nicht das <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>-Attribut hinzu.

## <a name="see-also"></a>Siehe auch

- [Exemplarische Vorgehensweise: Testgesteuerte Entwicklung mit dem Test-Explorer](quick-start-test-driven-development-with-test-explorer.md)
