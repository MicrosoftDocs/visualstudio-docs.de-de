---
title: Erste Schritte mit Unittests
description: Verwenden Sie Visual Studio zum Definieren und Ausführen von Komponententests, um die Integrität des Codes zu gewährleisten, und zum Erkennen von Fehlern, bevor diese sich auf Ihre Kunden auswirken.
ms.custom: SEO-VS-2020
ms.date: 04/07/2020
ms.topic: tutorial
helpviewer_keywords:
- unit testing, create unit test plans
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c83b13b852b9ae53bd2218a62b6681478369df1b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970516"
---
# <a name="get-started-with-unit-testing"></a>Erste Schritte mit Unittests

Verwenden Sie Visual Studio, um Komponententests zu definieren und auszuführen, um die Integrität Ihres Codes zu gewährleisten, Code Coverage sicherzustellen und Fehler zu finden, bevor diese von Ihren Kunden erkannt werden. Führen Sie Ihre Komponententests regelmäßig durch, um sicherzustellen, dass Ihr Core ordnungsgemäß funktioniert.

Für den Code und die Beispiele in diesem Artikel wird C# verwenden. Die Konzepte und Features gelten jedoch auch für .NET-Sprachen, C++, Python, JavaScript und TypeScript.

## <a name="create-unit-tests"></a>Erstellen von Komponententests

In diesem Abschnitt wird beschrieben, wie Sie ein Komponententestprojekt erstellen.

1. Öffnen Sie das Projekt, das Sie in Visual Studio testen möchten.

   In diesem Artikel wird ein einfaches „Hallo Welt“-Projekt in C# namens **HelloWorldCore** getestet, um einen Beispielkomponententest zu demonstrieren. Der Beispielcode für ein solches Projekt lautet wie folgt:

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

1. Suchen Sie im Dialogfeld „Neues Projekt“ nach einer Komponententestprojektvorlage für das Testframework, das Sie verwenden möchten (z. B. „MSTest“), und wählen Sie sie aus.

   Ab Version 14.8 von Visual Studio 2017 umfassen die .NET-Sprachen integrierte Vorlagen für „NUnit“ und „xUnit“. Für C++ müssen Sie ein Testframework auswählen, das von der Sprache unterstützt wird. Informationen zum Einrichten Ihres Testprojekts mit Python finden Sie unter [Einrichten von Komponententests in Python-Code](../python/unit-testing-python-in-visual-studio.md).

   > [!TIP]
   > Für C# können Sie Komponententestprojekte mithilfe einer schnelleren Methode aus Code erstellen. Weitere Informationen finden Sie unter [Erstellen von Komponententestprojekten und Testmethoden](../test/unit-test-basics.md#create-unit-test-projects-and-test-methods). Für die Verwendung dieser Methode mit .NET Core oder .NET Standard ist Visual Studio 2019 erforderlich.

   In der folgenden Abbildung wird ein MSTest-Komponententest veranschaulicht, der in .NET unterstützt wird.

   ::: moniker range=">=vs-2019"

   ![Komponententestprojektvorlage in Visual Studio 2019](media/vs-2019/add-new-test-project.png)

   Klicken Sie auf **Weiter**, wählen Sie einen Namen für das Testprojekt aus, und klicken Sie dann auf **Erstellen**.

   ::: moniker-end

   ::: moniker range="vs-2017"

   ![Komponententestprojektvorlage in Visual Studio 2019](media/mstest-test-project-template.png)

   Wählen Sie einen Namen für das Testprojekt aus (z. B. „HelloWorldTests“), und klicken Sie dann auf **OK**.

   ::: moniker-end

   Das Projekt wird Ihrer Projektmappe hinzugefügt.

   ![Wählen Sie das Unittestprojekt im Projektmappen-Explorer aus.](media/vs-2019/solution-explorer.png)

1. Fügen Sie im Komponententestprojekt einen Verweis auf das Projekt hinzu, das Sie testen möchten, indem Sie mit der rechten Maustaste auf **Verweise** oder auf **Abhängigkeiten** klicken und dann die Option **Verweis hinzufügen** auswählen.

1. Wählen Sie das Projekt aus, das den Code enthält, den Sie testen möchten, und klicken Sie auf **OK**.

   ![Screenshot: Hinzufügen eines Projektverweises in Visual Studio](media/vs-2019/reference-manager.png)

1. Fügen Sie der Komponententestmethode Code hinzu.

   Sie können beispielsweise den folgenden Code verwenden, indem Sie die richtige Dokumentationsregisterkarte auswählen, die mit Ihrem Testframework übereinstimmt: MSTest, NUnit oder xUnit (werden nur in .NET unterstützt).

   # <a name="mstest"></a>[MSTest](#tab/mstest)

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

   # <a name="nunit"></a>[NUnit](#tab/nunit)

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

    # <a name="xunit"></a>[xUnit](#tab/xunit)

    ```csharp
    using System;
    using Xunit;
    using System.IO;
    
    namespace HelloWorldTests
    {
        public class UnitTest1
        {
            private const string Expected = "Hello World!";
            [Fact]
            public void Test1()
            {
                using (var sw = new StringWriter())
                {
                    Console.SetOut(sw);
                    HelloWorldCore.Program.Main();
    
                    var result = sw.ToString().Trim();
                    Assert.Equal(Expected, result);
                }
            }
        }
    }
    ```

## <a name="run-unit-tests"></a>Komponententests ausführen

1. Öffnen Sie den [Test-Explorer](../test/run-unit-tests-with-test-explorer.md).

   ::: moniker range=">=vs-2019"
   Wählen Sie oben in der Menüleiste **Test** > **Test-Explorer** aus, oder drücken Sie **STRG** + **E**, **T**, um den Test-Explorer zu öffnen.
   ::: moniker-end
   ::: moniker range="vs-2017"
   Klicken Sie oben in der Menüleiste auf **Test** > **Windows** > **Test-Explorer**, um den Test-Explorer zu öffnen.
   ::: moniker-end

1. Führen Sie die Komponententests aus, indem Sie **Alle ausführen** auswählen oder **STRG** + **R**, **V** drücken.

   ![Ausführen von Komponententests im Test-Explorer](media/vs-2019/test-explorer-run-all.png)

   Wenn die Tests ausgeführt wurden, zeigt ein grünes Häkchen an, dass ein Test bestanden wurde. Ein rotes „x“-Symbol zeigt an, dass ein Test nicht erfolgreich war.

   ![Überprüfen der Unittestsergebnisse im Test-Explorer](media/vs-2019/unit-test-passed.png)

> [!TIP]
> Sie können den [Test-Explorer](../test/run-unit-tests-with-test-explorer.md) verwenden, um im integrierten Testframework (MSTest) oder in Testframeworks von Drittanbietern Komponententests auszuführen. Sie können die Tests auch in Kategorien gruppieren, Filter auf die Testliste anwenden, und Wiedergabelisten von Tests erstellen, speichern und ausführen. Zudem können Sie Tests debuggen und die Leistung und Codeabdeckung von Tests analysieren.

## <a name="view-live-unit-test-results-visual-studio-enterprise"></a>Anzeigen von Echtzeitergebnissen von Komponententests (Visual Studio Enterprise)

Wenn Sie die Testframeworks MSTest, xUnit oder NUnit in Visual Studio 2017 oder höher verwenden, werden Live-Ergebnisse Ihrer Komponententests angezeigt.

> [!NOTE]
> Für die Ausführung dieser Schritte ist Visual Studio Enterprise erforderlich.

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

## <a name="use-a-third-party-test-framework"></a>Verwenden des Testframeworks eines Drittanbieters

Je nachdem, welche Programmiersprache Sie verwenden, können Sie Komponententests in Visual Studio auch über Testframeworks von Drittanbietern wie Boost, Google und NUnit ausführen. So verwenden Sie ein Framework eines Drittanbieters:

- Verwenden Sie den **NuGet-Paket-Manager**, um das NuGet-Paket für das Framework Ihrer Wahl zu installieren.

- (.NET) Ab Version 14.6 von Visual Studio 2017 sind vorkonfigurierte Testprojektvorlagen für NUnit- und xUnit-Testframeworks in Visual Studio enthalten. Die Vorlagen enthalten außerdem die erforderlichen NuGet-Pakete zum Aktivieren der Unterstützung.

- (C++) In Visual Studio 2017 und höheren Versionen sind einige Frameworks wie Boost bereits enthalten. Weitere Informationen finden Sie unter [Schreiben von Komponententests für C/C++ in Visual Studio](../test/writing-unit-tests-for-c-cpp.md).

So fügen Sie ein Komponententestprojekt hinzu:

1. Öffnen Sie die Projektmappe, die den Code enthält, den Sie testen möchten.

2. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Projektmappe, und wählen Sie anschließend **Hinzufügen** > **Neues Projekt** aus.

3. Wählen Sie eine Vorlage für ein Komponententestprojekt aus.

   Wählen Sie für dieses Beispiel die Vorlage [NUnit](https://nunit.org/) aus.

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

6. Führen Sie den Test über den **Test-Explorer** aus, oder klicken Sie mit der rechten Maustaste auf den Testcode, und wählen Sie die Option **Tests ausführen** aus (oder drücken Sie **STRG** + **R**, **T**).

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Grundlagen zu Komponententest](../test/unit-test-basics.md)

> [!div class="nextstepaction"]
> [Erstellen und Ausführen von Komponententests für verwalteten Code](walkthrough-creating-and-running-unit-tests-for-managed-code.md)
