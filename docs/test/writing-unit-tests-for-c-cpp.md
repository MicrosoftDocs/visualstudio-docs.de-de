---
title: Schreiben von Komponententests für C/C++
description: Schreiben von C++-Komponententests in Visual Studio mit verschiedenen Testframeworks wie CTest, Boost.Test und Google Test
ms.date: 02/08/2020
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: cf6287ebdb4c2df6145a0e60e22ac1197a517fde
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729365"
---
# <a name="write-unit-tests-for-cc-in-visual-studio"></a>Schreiben von Komponententests für C/C++ in Visual Studio

Sie können C++-Komponententests über das Fenster **Test-Explorer** schreiben und ausführen. Es funktioniert genauso wie bei anderen Sprachen. Weitere Informationen zur Verwendung des **Test-Explorers** finden Sie unter [Ausführen von Komponententests mit dem Test-Explorer](run-unit-tests-with-test-explorer.md).

> [!NOTE]
> Einige Funktionen wie Live Unit Testing, Tests der programmierten UI und IntelliTest werden für C++ nicht unterstützt.

Visual Studio umfasst diese C++-Testframeworks ohne zusätzliche erforderliche Downloads:

- Microsoft-Komponententest-Framework für C++
- Google Test
- Boost.Test
- CTest

Zusätzlich zu diesen installierten Testframeworks können Sie auch Testadapter für jedes andere Framework schreiben, das Sie in Visual Studio verwenden möchten. Ein Testadapter kann Komponententests in das Fenster **Test-Explorer** integrieren. Im [Visual Studio Marketplace](https://marketplace.visualstudio.com) sind einige Adapter von Drittanbietern verfügbar. Weitere Informationen finden Sie unter [Installieren von Frameworks für Komponententests von Drittanbietern](install-third-party-unit-test-frameworks.md).

**Visual Studio 2017 und höher (Professional und Enterprise)**

C++-Komponententestprojekte unterstützen [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md).

**Visual Studio 2017 und höher (alle Editionen)**

- Der **Google Test-Adapter** ist als Standardkomponente in der Workload **Desktop Development mit C++** enthalten. Er verfügt über eine Projektvorlage, die Sie einer Projektmappe hinzufügen können. Öffnen Sie dazu im **Projektmappen-Explorer **mit einem Rechtsklick auf den Projektmappenknoten das Kontextmenü, und klicken Sie auf** Neues Projekt hinzufügen**. Zusätzlich bietet er Optionen, die Sie unter **Tools** > **Optionen** konfigurieren können. Weitere Informationen finden Sie unter [Vorgehensweise: Verwenden von Google Test in Visual Studio](how-to-use-google-test-for-cpp.md).

- **Boost.Test** ist als Standardkomponente in der Workload **Desktop Development mit C++** enthalten. Sie ist in den **Test-Explorer** integriert, verfügt aber zurzeit nicht über eine Projektvorlage. Diese muss manuell konfiguriert werden. Weitere Informationen finden Sie unter [Vorgehensweise: Verwenden von Boost.Test in Visual Studio](how-to-use-boost-test-for-cpp.md).

- Die Komponente **C++ CMake tools**, die Teil der Workload **Desktop Development mit C++** ist, umfasst die Unterstützung von **CTest**. Weitere Informationen finden Sie unter [Vorgehensweise: Verwenden von CTest in Visual Studio](how-to-use-ctest-for-cpp.md).

**Visual Studio 2015 und frühere Versionen**

Die Erweiterungen für die Adapter Google-Test und Boost.Test können Sie im Visual Studio Marketplace herunterladen. Suchen Sie einfach nach [Test adapter for Boost.Test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforBoostTest) und nach [Test adapter for Google Test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforGoogleTest).

## <a name="basic-test-workflow"></a>Grundlegender Testworkflow

Im folgenden Abschnitt werden die grundlegenden ersten Schritte für C++-Komponententests dargestellt. Die Basiskonfigurationen für die Microsoft- und Google Test-Frameworks sind ähnlich. Für Boost.Test müssen Sie ein Testprojekt manuell erstellen.

::: moniker range="vs-2019"

### <a name="create-a-test-project-in-visual-studio-2019"></a>Erstellen eines Testprojekts in Visual Studio 2019

Sie definieren Tests und führen sie in einem oder mehreren Testprojekten aus. Sie erstellen die Projekte und den Code, den Sie testen wollen, in derselben Projektmappe. Klicken Sie zuerst im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projektmappenknoten, um einer bestehenden Projektmappe ein neues Testprojekt hinzuzufügen. Klicken Sie dann im Popupmenü auf **Hinzufügen** > **Neues Projekt**. Legen Sie **Sprache** auf C++ fest, und geben Sie „test“ in das Suchfeld ein. In der folgenden Abbildung werden Testprojekte dargestellt, auf die Sie zugreifen können, wenn die Workloads **Desktopentwicklung mit C++** und **Entwicklung für die universelle Windows-Plattform** installiert sind:

![C++-Testprojekte in Visual Studio 2019](media/vs-2019/cpp-new-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

### <a name="create-a-test-project-in-visual-studio-2017"></a>Erstellen eines Testprojekts in Visual Studio 2017

Sie definieren Tests und führen sie in einem oder mehreren Testprojekten aus. Sie erstellen die Projekte und den Code, den Sie testen wollen, in derselben Projektmappe. Um ein neues Testprojekt hinzuzufügen, klicken Sie mit der rechten Maustaste im **Projektmappen-Explorer** auf den Projektmappenknoten, und wählen Sie anschließend **Hinzufügen** > **Neues Projekt** aus. Klicken Sie im linken Bereich auf **Visual C++ Test** (Visual C++-Test). Wählen Sie dann im mittleren Bereich einen der Projekttypen aus. In der folgenden Abbildung werden Testprojekte dargestellt, auf die Sie zugreifen können, wenn die Workload **Desktop Development mit C++** installiert ist:

![C++-Testprojekte](media/cpp-new-test-project.png)

::: moniker-end

### <a name="create-references-to-other-projects-in-the-solution"></a>Erstellen von Verweisen auf andere Projekte in der Projektmappe

Fügen Sie im Testprojekt einen Verweis auf das Projekt hinzu, um den Zugriff auf die Funktionen im zu testenden Projekt zu aktivieren. Klicken Sie im **Projektmappen-Explorer** zunächst mit der rechten Maustaste auf den Knoten für das Testprojekt. Wählen Sie **Hinzufügen** > **Verweis** aus. Wählen Sie im Dialogfeld „Verweis hinzufügen“ das Projekt bzw. die Projekte aus, das bzw. die Sie testen möchten.

![Verweis hinzufügen](media/cpp-add-ref-test-project.png)

### <a name="link-to-object-or-library-files"></a>Verknüpfen mit Objekt- oder Bibliotheksdateien

Wenn der Testcode die Funktionen, die Sie testen möchten, nicht exportiert, können Sie die OBJ- oder LIB-Ausgabedateien zu den Abhängigkeiten des Testprojekts hinzufügen. Weitere Informationen finden Sie unter [To link the tests to the object or library files](how-to-use-microsoft-test-framework-for-cpp.md#object_files) (Verknüpfen des Tests mit Objekt- oder Bibliotheksdateien).

### <a name="add-include-directives-for-header-files"></a>Hinzufügen von #include-Direktiven für Headerdateien

Fügen Sie als Nächstes in der *CPP*-Datei in Ihrem Komponententest eine `#include`-Direktive für sämtliche Headerdateien hinzu, die die Typen und Funktionen deklarieren, die Sie testen möchten. Geben Sie `#include "` ein, um IntelliSense zu aktivieren, damit es Ihnen bei der Auswahl hilft. Wiederholen Sie diesen Vorgang für alle zusätzlichen Header.

![Screenshot des Projektmappen-Explorers, in dem gezeigt wird, wie eine #include-Anweisung hinzugefügt wird, wobei IntelliSense eine einzuschließende Headerdatei hervorhebt.](media/cpp-add-includes-test-project.png)

Um nicht in jede include-Anweisung in der Quelldatei den vollständigen Pfad eingeben zu müssen, können Sie die erforderlichen Ordner unter **Projekt** > **Eigenschaften** > **C/C++**  > **Allgemein** > **Zusätzliche Includeverzeichnisse** hinzufügen.

### <a name="write-test-methods"></a>Schreiben von Testmethoden

> [!NOTE]
> In diesem Abschnitt wird die Syntax von Microsoft Unittest-Frameworks für C/C++ dargestellt. Die entsprechende Dokumentation finden Sie hier: [Referenz für die API „Microsoft.VisualStudio.TestTools.CppUnitTestFramework“](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md) Die Dokumentation zu Google Test finden Sie unter [Google Test Primer (Einführung in Google Test)](https://github.com/google/googletest/blob/master/googletest/docs/primer.md). Die Dokumentation zu Boost.Test finden Sie unter [Boost Test Library: The Unit Test Framework (Boost Test-Bibliothek: Das Framework für Komponententests).](https://www.boost.org/doc/libs/1_46_0/libs/test/doc/html/utf.html)

Die *.cpp*-Datei im Testprojekt enthält eine Stubklasse und eine Methode, die für Sie definiert sind. Sie zeigen ein Beispiel für das Schreiben von Testcode. Die Signaturen nutzen die Makros TEST_CLASS und TEST_METHOD. Deshalb können Sie die Methoden über das Fenster **Test-Explorer** finden.

![Screenshot des Fensters „Test-Explorer“, in dem die Codedatei „unittest1.cpp“ gezeigt wird, die eine Stubklasse und -methode enthält, die die Makros TEST_CLASS und TEST_METHOD verwenden.](media/cpp-write-test-methods.png)

TEST_CLASS und TEST_METHOD sind Teil des [nativen Microsoft-Testframeworks](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). Der **Test-Explorer** erkennt Testmethoden in anderen unterstützten Frameworks auf dieselbe Weise.

Das Makro TEST_METHOD gibt „Void“ zurück. Verwenden Sie die statische Methode in der `Assert`-Klasse, um die tatsächlichen Ergebnisse im Vergleich zu den erwarteten Ergebnissen zu vergleichen und um ein Testergebnis zu erzeugen. Im folgenden Beispiel wird angenommen, dass `MyClass` über einen Konstruktor verfügt, der einen `std::string` akzeptiert. Es kann getestet werden, ob der Konstruktor die Klasse wie erwartet initialisiert:

```cpp
TEST_METHOD(TestClassInit)
{
    std::string name = "Bill";
    MyClass mc(name);
    Assert::AreEqual(name, mc.GetName());
}
```

Im vorstehenden Beispiel bestimmt das Ergebnis des Aufrufs `Assert::AreEqual`, ob der Test erfolgreich ausgeführt werden kann oder fehlschlägt. Die Assert-Klasse enthält einige andere Methoden zum Vergleichen der erwarteten Ergebnisse mit den tatsächlichen Ergebnissen.

Sie können Testmethoden *Merkmale* hinzufügen, um den Testbesitzer, die Priorität und andere Informationen anzugeben. Sie können diese Werte verwenden, um Tests im **Test-Explorer** zu sortieren und in Gruppen zu unterteilen. Weitere Informationen finden Sie unter [Run unit tests with Test Explorer (Ausführen von Komponententests mit dem Test-Explorer)](run-unit-tests-with-test-explorer.md).

### <a name="run-the-tests"></a>Tests ausführen

1. Klicken Sie im Menü **Test** auf **Windows** > **Test-Explorer**. In der folgenden Abbildung wird ein Testprojekt dargestellt, für das noch keine Tests ausgeführt wurden.

   ![Der Test-Explorer vor dem Ausführen von Tests](media/cpp-test-explorer.png)

   > [!NOTE]
   > Die CTest-Integration für den **Test-Explorer** ist noch nicht verfügbar. Führen Sie CTest-Tests über das Hauptmenü von CMake aus.

1. Wenn nicht alle Ihre Tests im Fenster angezeigt werden, erstellen Sie das Testprojekt, indem Sie mit der rechten Maustaste auf dessen Knoten im **Projektmappen-Explorer** klicken und **Erstellen** oder **Neu erstellen** auswählen.

1. Klicken Sie im **Test-Explorer** auf **Alle ausführen**, oder wählen Sie die Tests aus, die Sie ausführen möchten. Klicken Sie für weitere Optionen, einschließlich des Ausführens im Debugmodus mit aktivierten Breakpoints, mit der rechten Maustaste auf einen Test. Wenn alle Tests ausgeführt wurden, wird in dem Fenster dargestellt, welche Tests erfolgreich waren und welche fehlgeschlagen sind:

![Test-Explorer nach dem Ausführen von Tests](media/cpp-test-explorer-passed.png)

Bei fehlgeschlagenen Tests werden in einer Meldung Details angezeigt, die Ihnen dabei helfen sollen, den Grund für das Problem zu finden. Klicken Sie mit der rechten Maustaste auf den fehlgeschlagenen Test, damit ein Popupmenü angezeigt wird. Wählen Sie **Ausgewählte Tests debuggen** aus, um die Funktion zu durchlaufen, bei der der Fehler aufgetreten ist.

Weitere Informationen zur Verwendung des **Test-Explorers** finden Sie unter [Ausführen von Komponententests mit dem Test-Explorer](run-unit-tests-with-test-explorer.md).

Weitere Informationen zu Komponententests finden Sie unter [Grundlagen zum Komponententest](unit-test-basics.md).

## <a name="use-codelens"></a>Verwenden von CodeLens

**Visual Studio 2017 und höher (Editionen Professional und Enterprise)**

Mit [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) können Sie sich den Status eines Komponententests ansehen, ohne dazu den Code-Editor verlassen zu müssen.

Sie können CodeLens für ein C++-Komponententestprojekt mit jeder der folgenden Möglichkeiten initialisieren:

- Bearbeiten und erstellen Sie Ihr Testprojekt oder Ihre -projektmappe.
- Erstellen Sie Ihr Projekt oder die Projektmappe erneut.
- Führen Sie Tests im Fenster **Test-Explorer** aus.

Nachdem es initialisiert wurde, werden Statussymbole zu jedem Komponententest angezeigt.

![C++ CodeLens-Symbole](media/cpp-test-codelens-icons.png)

Klicken Sie auf das Symbol, um weitere Informationen zu erhalten oder den Komponententest auszuführen oder zu debuggen:

![Ausführen und Debuggen von C++ CodeLens](media/cpp-test-codelens-run-debug.png)

## <a name="see-also"></a>Siehe auch

- [Ausführen von Komponententests für Code](unit-test-your-code.md)
