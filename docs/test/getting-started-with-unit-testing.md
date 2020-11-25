---
title: Erste Schritte mit Unittests
description: Verwenden Sie Visual Studio, um Komponententests zu definieren und auszuführen, um die Integrität Ihres Codes zu gewährleisten, Code Coverage sicherzustellen und Fehler zu finden, bevor diese von Ihren Kunden erkannt werden.
ms.custom: SEO-VS-2020
ms.date: 04/07/2020
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit test plans
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3daff1a7b7c2e62b4ca4a508c5c8dd31261a40dd
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "95441780"
---
# <a name="get-started-with-unit-testing"></a>Erste Schritte mit Unittests

Verwenden Sie Visual Studio, um Komponententests zu definieren und auszuführen, um die Integrität Ihres Codes zu gewährleisten, Code Coverage sicherzustellen und Fehler zu finden, bevor diese von Ihren Kunden erkannt werden. Führen Sie Ihre Komponententests regelmäßig durch, um sicherzustellen, dass Ihr Core ordnungsgemäß funktioniert.

## <a name="create-unit-tests"></a>Erstellen von Komponententests

In diesem Abschnitt wird beschrieben, wie Sie ein Komponententestprojekt erstellen.

1. Öffnen Sie das Projekt, das Sie in Visual Studio testen möchten.

   In diesem Artikel wird ein einfaches „Hallo Welt“-Projekt namens **HelloWorldCore** getestet, um einen Beispielkomponententest zu demonstrieren. Der Beispielcode für ein solches Projekt lautet wie folgt:

   ```csharp
   namespace HelloWorldCore

      public class Program
      {
         public static void Main()
         {
            Console.WriteLine("Hello World!");
         }
      }
   ```

1. Wählen Sie im **Projektmappen-Explorer** den Projektmappenknoten aus. Wählen Sie dann in der oberen Menüleiste **Datei** > **Hinzufügen** > **Neues Projekt** aus.

1. Suchen Sie im Dialogfeld „Neues Projekt“ nach einer Komponententestprojektvorlage für das Testframework, das Sie verwenden möchten, und wählen Sie sie aus.

   ::: moniker range=">=vs-2019"

   ![Komponententestprojektvorlage in Visual Studio 2019](media/vs-2019/add-new-test-project.png)

   Klicken Sie auf **Weiter**, wählen Sie einen Namen für das Testprojekt aus, und klicken Sie dann auf **Erstellen**.

   ::: moniker-end

   ::: moniker range="vs-2017"

   ![Komponententestprojektvorlage in Visual Studio 2019](media/mstest-test-project-template.png)

   Wählen Sie einen Namen für das Testprojekt aus, und klicken Sie dann auf **OK**.

   ::: moniker-end

   Das Projekt wird Ihrer Projektmappe hinzugefügt.

   ![Wählen Sie das Unittestprojekt im Projektmappen-Explorer aus.](media/vs-2019/solution-explorer.png)

1. Fügen Sie im Komponententestprojekt einen Verweis auf das Projekt hinzu, das Sie testen möchten, indem Sie mit der rechten Maustaste auf **Verweise** oder auf **Abhängigkeiten** klicken und dann die Option **Verweis hinzufügen** auswählen.

1. Wählen Sie das Projekt aus, das den Code enthält, den Sie testen möchten, und klicken Sie auf **OK**.

   ![Screenshot: Hinzufügen eines Projektverweises in Visual Studio](media/vs-2019/reference-manager.png)

1. Fügen Sie der Komponententestmethode Code hinzu.

   Für ein MSTest-Projekt können Sie beispielsweise den folgenden Code verwenden.

   ```csharp
   using Microsoft.VisualStudio.TestTools.UnitTesting;
   using System.IO;
   using System;

   namespace HelloWorldTests
   {
      [TestClass]
      public class UnitTest1
      {
         private const string Expected = "Hello World!";
         [TestMethod]
         public void TestMethod1()
         {
            using (var sw = new StringWriter())
            {
               Console.SetOut(sw);
               HelloWorldCore.Program.Main();

               var result = sw.ToString().Trim();
               Assert.AreEqual(Expected, result);
            }
         }
      }
   }
   ```

   Für ein NUnit-Projekt können Sie den folgenden Code verwenden.

   ```csharp
   using NUnit.Framework;
   using System.IO;
   using System;

   namespace HelloWorldTests
   {
      public class Tests
      {
         private const string Expected = "Hello World!";

         [SetUp]
         public void Setup()
         {
         }
         [Test]
         public void TestMethod1()
         {
            using (var sw = new StringWriter())
            {
               Console.SetOut(sw);
               HelloWorldCore.Program.Main();

               var result = sw.ToString().Trim();
               Assert.AreEqual(Expected, result);
            }
         }
      }
   }
   ```

> [!TIP]
> Weitere Informationen zum Erstellen von Komponententests finden Sie unter [Erstellen und Ausführen von Komponententests für verwalteten Code](walkthrough-creating-and-running-unit-tests-for-managed-code.md).

## <a name="run-unit-tests"></a>Komponententests ausführen

1. Öffnen Sie den [Test-Explorer](../test/run-unit-tests-with-test-explorer.md).

   ::: moniker range=">=vs-2019"
   Klicken Sie oben in der Menüleiste auf **Test** > **Test-Explorer**, um den Test-Explorer zu öffnen.
   ::: moniker-end
   ::: moniker range="vs-2017"
   Klicken Sie oben in der Menüleiste auf **Test** > **Windows** > **Test-Explorer**, um den Test-Explorer zu öffnen.
   ::: moniker-end

1. Die Komponententests führen Sie aus, indem Sie auf **Alle ausführen** klicken.

   ![Ausführen von Komponententests im Test-Explorer](media/vs-2019/test-explorer-run-all.png)

   Wenn die Tests ausgeführt wurden, zeigt ein grünes Häkchen an, dass ein Test bestanden wurde. Ein rotes „x“-Symbol zeigt an, dass ein Test nicht erfolgreich war.

   ![Überprüfen der Unittestsergebnisse im Test-Explorer](media/vs-2019/unit-test-passed.png)

> [!TIP]
> Sie können den [Test-Explorer](../test/run-unit-tests-with-test-explorer.md) verwenden, um im integrierten Testframework (MSTest) oder in Testframeworks von Drittanbietern Komponententests auszuführen. Sie können die Tests auch in Kategorien gruppieren, Filter auf die Testliste anwenden, und Wiedergabelisten von Tests erstellen, speichern und ausführen. Zudem können Sie Tests debuggen und die Leistung und Codeabdeckung von Tests analysieren.

## <a name="view-live-unit-test-results"></a>Anzeigen der Ergebnisse von Liveunittests

Wenn Sie die Testframeworks MSTest, xUnit oder NUnit in Visual Studio 2017 oder höher verwenden, werden Live-Ergebnisse Ihrer Komponententests angezeigt.

> [!NOTE]
> Live Unit Testing ist nur in der Enterprise-Edition verfügbar.

1. Das Feature „Live Unit Testing“ aktivieren Sie im Menü **Testen**, indem Sie **Testen** > **Live Unit Testing** > **Starten** auswählen.

   ::: moniker range="vs-2017"

   ![Aktivieren der Liveunittests](media/live-test-results-start.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Starten von Live Unit Testing in Visual Studio 2019](media/vs-2019/start-live-unit-testing.png)

   ::: moniker-end

1. Schauen Sie sich die Ergebnisse der Tests im Fenster des Code-Editors an, während Sie Code schreiben und diesen bearbeiten.

   ![Überprüfen der Ergebnisse der Tests](media/vs-2019/live-unit-testing-results.png)

1. Klicken Sie auf einen Testergebnisindikator, damit weitere Informationen angezeigt werden, z.B. die Namen der Tests, die diese Methode abdecken.

   ![Auswählen der Testergebnisindikatoren](media/vs-2019/live-unit-testing-details.png)

Weitere Informationen zu Live Unit Testing finden Sie unter [Einführung in Live Unit Testing](../test/live-unit-testing-intro.md).

## <a name="generate-unit-tests-with-intellitest"></a>Generieren von Unittests mit IntelliTest

Wenn Sie IntelliTest ausführen, erkennen Sie, welche Tests zu einem Fehler führen, und können den erforderlichen Code hinzufügen, um die Fehler zu beseitigen. Sie können wählen, welche der generierten Tests in einem Testprojekt gespeichert werden sollen, um eine Regressionsreihe zu erstellen. Wenn Sie den Code ändern, führen Sie IntelliTest erneut aus, damit die generierten Tests mit den Codeänderungen synchronisiert werden. Weitere Informationen finden Sie unter [Generieren von Komponententests für Code mit IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md).

> [!TIP]
> IntelliTest ist nur für verwalteten Code verfügbar, der das .NET Framework unterstützt.

![Erzeugen von Unittests mit IntelliTest](media/intellitest.png)

## <a name="analyze-code-coverage"></a>Analysieren von Code Coverage

Wenn Sie den Anteil des Projektcodes ermitteln möchten, der in codierten Tests wie Komponententests tatsächlich getestet wird, verwenden Sie die Code Coverage-Funktion von Visual Studio. Um sich effektiv vor Fehlern zu schützen, sollten Sie die Tests für den Großteil Ihres Codes ausführen. Weitere Informationen finden Sie unter [Bestimmen des Umfangs des zu testenden Codes mithilfe von Code Coverage](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="use-a-third-party-test-framework"></a>Verwenden des Testframeworks eines Drittanbieters

Sie können Komponententests in Visual Studio auch über Testframeworks von Drittanbietern wie Boost, Google und NUnit ausführen. Verwenden Sie den **NuGet-Paket-Manager**, um das NuGet-Paket für das Framework Ihrer Wahl zu installieren. Als Alternative beinhaltet Visual Studio für die Frameworks NUnit und xUnit vorkonfigurierte Testprojektvorlagen, die die erforderlichen NuGet-Pakete beinhalten.

So erstellen Sie Komponententest für das Framework [NUnit](https://nunit.org/):

1. Öffnen Sie die Projektmappe, die den Code enthält, den Sie testen möchten.

2. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Projektmappe, und wählen Sie anschließend **Hinzufügen** > **Neues Projekt** aus.

3. Wählen Sie die Projektvorlage **NUnit-Testprojekt** aus.

   ::: moniker range=">=vs-2019"

   ![NUnit-Testprojektvorlage in Visual Studio 2019](media/vs-2019/nunit-test-project-template.png)

   Klicken Sie auf **Weiter**, benennen Sie das Projekt, und klicken Sie dann auf **Erstellen**.

   ::: moniker-end

   ::: moniker range="vs-2017"

   Benennen Sie das Projekt, und klicken Sie auf **OK**, um es zu erstellen.

   ::: moniker-end

   Die Projektvorlage beinhaltet NuGet-Verweise auf NUnit und auf NUnit3TestAdapter.

   ![NUnit-NuGet-Abhängigkeiten im Projektmappen-Explorer](media/vs-2019/nunit-nuget-dependencies.png)

4. Fügen Sie dem Projekt, das den Code enthält, den Sie testen möchten, einen Verweis aus dem Testprojekt hinzu.

   Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie anschließend **Hinzufügen** > **Verweis** aus. (Sie können einen Verweis auch über das Kontextmenü des Knotens **Verweise** oder **Abhängigkeiten** hinzufügen.)

5. Fügen Sie Ihrer Testmethode Code hinzu.

   ![Hinzufügen von Code zur Codedatei für Ihren Komponententest](media/vs-2019/unit-test-method.png)

6. Führen Sie den Test über den **Test-Explorer** aus, oder, indem Sie mit der rechten Maustaste auf den Testcode klicken und die Option **Tests ausführen** auswählen.

## <a name="see-also"></a>Weitere Informationen

* [Exemplarische Vorgehensweise: Erstellen und Ausführen von Komponententests für verwalteten Code](walkthrough-creating-and-running-unit-tests-for-managed-code.md)
* [Befehl „Komponententests erstellen“](create-unit-tests-menu.md)
* [Generieren von Komponententests für Code mit IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [Ausführen von Komponententests mit dem Test-Explorer](run-unit-tests-with-test-explorer.md)
* [Bestimmen des Umfangs des zu testenden Codes mithilfe von Code Coverage](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
