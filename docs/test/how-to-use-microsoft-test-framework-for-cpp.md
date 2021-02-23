---
title: Verwenden des Microsoft-Komponententest-Frameworks für C++
description: Verwenden Sie das Microsoft-Komponententestframework für C++, um Komponententests für Ihren C++-Code zu erstellen.
ms.date: 02/16/2021
ms.topic: how-to
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: a76c6ac83956cd1e6514ff958278d0b4cbcf0d2f
ms.sourcegitcommit: cc8547eb211c43b67b8123d1211b80b5642e3b18
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/17/2021
ms.locfileid: "100563431"
---
# <a name="use-the-microsoft-unit-testing-framework-for-c-in-visual-studio"></a>Verwenden des Microsoft-Komponententest-Frameworks für C++ in Visual Studio

Das Microsoft-Komponententest-Framework für C++ ist standardmäßig in der Workload **Desktopentwicklung mit C++** enthalten.

## <a name="to-write-unit-tests-in-a-separate-project"></a><a name="separate_project"></a> Schreiben von Komponententests in einem separaten Projekt

In der Regel führen Sie Ihren Testcode in einem eigenen Projekt in derselben Projektmappe aus, in der sich der Code befindet, den Sie testen möchten. Weitere Informationen zum Einrichten und Konfigurieren eines neuen Testprojekts finden Sie unter [Writing Unit Tests for C/C++ (Schreiben von Komponententests für C/C++)](writing-unit-tests-for-c-cpp.md).

## <a name="to-write-unit-tests-in-the-same-project"></a><a name="same_project"></a> Schreiben von Komponententests im gleichen Projekt

In einigen Fällen (z.B. beim Testen von nicht exportierten Funktionen in einer DLL) sollten Sie die Tests im gleichen Projekt wie das Programm erstellen, das Sie testen. So schreiben Sie Komponententests im gleichen Projekt:

1. Ändern Sie die Projekteigenschaften, um die Header und Bibliotheksdateien einzuschließen, die für die Komponententests erforderlich sind.

   1. Öffnen Sie im Projektmappen-Explorer das Kontextmenü für das zu testende Projekt, und klicken Sie auf **Eigenschaften**. Das Fenster mit den Projekteigenschaften wird geöffnet.

   1. Klicken Sie im Dialogfeld „Eigenschaftenseiten“ auf **Konfigurationseigenschaften** > **VC++-Verzeichnisse**.

   1. Klicken Sie in den folgenden Zeilen auf den Pfeil nach unten, und wählen Sie **\<Edit>** aus. Fügen Sie diese Pfade ein:

      | Verzeichnis | Eigenschaft |
      |-| - |
      | **Includeverzeichnisse** | **$(VCInstallDir)Auxiliary\VS\UnitTest\include** |
      | **Bibliotheksverzeichnisse** | **$(VCInstallDir)Auxiliary\VS\UnitTest\lib** |

1. Fügen Sie eine C++-Komponententestdatei hinzu:

   1. Klicken Sie erst mit der rechten Maustaste auf den Projektknoten im **Projektmappen-Explorer**, und wählen Sie **Hinzufügen** > **Neues Element** aus.

   1. Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option **C++-Datei (.cpp)** aus, geben Sie dieser einen geeigneten Namen, und klicken Sie auf **Hinzufügen**.

## <a name="to-link-the-tests-to-the-object-or-library-files"></a><a name="object_files"></a> So verknüpfen Sie die Tests mit den Objekt- oder Bibliotheksdateien

Wenn der zu testende Code nicht die Funktionen exportiert, die Sie testen möchten, können Sie die Ausgabedatei ( *.obj*- oder *.lib*) zu den Abhängigkeiten des Testprojekts hinzufügen. Ändern Sie die Eigenschaften des Testprojekts, um die Header und die Bibliotheks- oder Objektdateien einzuschließen, die für die Komponententests erforderlich sind.

1. Öffnen Sie im Projektmappen-Explorer das Kontextmenü für das Testprojekt, und wählen Sie **Eigenschaften** aus. Das Fenster mit den Projekteigenschaften wird geöffnet.

1. Rufen Sie die Seite **Konfigurationseigenschafen** > **Linker** > **Eingabe** auf, und wählen Sie **Zusätzliche Abhängigkeiten** aus.

   Wählen Sie **Bearbeiten** aus, und fügen Sie dann die Namen der *.obj*- oder *.lib*-Dateien hinzu. Verwenden Sie nicht die vollständigen Pfadnamen.

1. Rufen Sie die Seite **Konfigurationseigenschaften** > **Linker** > **Allgemein** auf, und wählen Sie **Zusätzliche Bibliotheksverzeichnisse** aus.

   Wählen Sie **Bearbeiten** aus, und fügen Sie den Verzeichnispfad der *.obj*- oder *.lib*-Dateien hinzu. Der Pfad befindet sich normalerweise im Buildordner des zu testenden Projekts.

1. Rufen Sie die Seite **Konfigurationseigenschaften** > **VC++-Verzeichnisse** auf, und wählen Sie **Includeverzeichnisse** aus.

   Wählen Sie **Bearbeiten** aus, und fügen Sie dann das Headerverzeichnis des zu testenden Projekts hinzu.

## <a name="write-the-tests"></a>Schreiben der Tests

*CPP*-Dateien mit Testklassen müssen „CppUnitTest.h“ und eine using-Anweisung für `using namespace Microsoft::VisualStudio::CppUnitTestFramework` enthalten. Das Testprojekt ist bereits für Sie konfiguriert. Es enthält ebenfalls eine Namespacedefinition und eine TEST_CLASS mit einer TEST_METHOD für Ihre ersten Schritte. Sie können den Namespacenamen und die Namen ändern, die bei den Klassen- und Methodenmakros in Klammern stehen.

Das Testframework definiert spezielle Makros für die Initialisierung von Testmodulen, Klassen und Methoden sowie für das Bereinigen von Ressourcen nach Abschluss der Tests. Diese Makros generieren Code, der vor dem ersten Zugriff auf eine Klasse oder Methode und nach Abschluss des letzten Tests ausgeführt wird. Weitere Informationen finden Sie unter [Initialize and cleanup (Initialisieren und Bereinigen)](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#Initialize_and_cleanup).

Verwenden Sie die statischen Methoden der [Assert](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#general_asserts)-Klasse, um Testbedingungen zu definieren. Verwenden Sie die [Logger](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#logger)-Klasse, um Nachrichten in das **Ausgabefenster** zu schreiben. Hinzufügen von Attributen zu den Testmethoden

## <a name="run-the-tests"></a>Tests ausführen

1. Klicken Sie im Menü **Test** auf **Windows** > **Test-Explorer**.

1. Wenn nicht alle Ihre Tests im Fenster angezeigt werden, erstellen Sie das Testprojekt, indem Sie mit der rechten Maustaste auf dessen Knoten im **Projektmappen-Explorer** klicken und **Erstellen** oder **Neu erstellen** auswählen.

1. Klicken Sie im **Test-Explorer** auf **Alle ausführen**, oder wählen Sie die Tests aus, die Sie ausführen möchten. Klicken Sie für weitere Optionen, einschließlich des Ausführens im Debugmodus mit aktivierten Breakpoints, mit der rechten Maustaste auf einen Test.

1. Wählen Sie **Tests** aus dem Dropdownmenü im **Ausgabefenster** aus, um sich die von der `Logger`-Klasse geschriebenen Meldungen anzeigen zu lassen:

   ![Testmeldungen im C++-Ausgabefenster](media/cpp-test-output-window.png)

## <a name="define-traits-to-enable-grouping"></a>Definieren von Merkmalen für das Aktivieren der Gruppierung

Sie können Merkmale für Testmethoden definieren, um Tests im **Test-Explorer** zu kategorisieren und zu gruppieren. Verwenden Sie zum Definieren eines Merkmals das `TEST_METHOD_ATTRIBUTE` -Makro. Beispiel – Definieren eines Merkmals mit dem Namen `TEST_MY_TRAIT`:

```cpp
#define TEST_MY_TRAIT(traitValue) TEST_METHOD_ATTRIBUTE(L"MyTrait", traitValue)
```

Verwenden des definierten Merkmals in den Komponententests:

```cpp
BEGIN_TEST_METHOD_ATTRIBUTE(Method1)
    TEST_OWNER(L"OwnerName")
    TEST_PRIORITY(1)
    TEST_MY_TRAIT(L"thisTraitValue")
END_TEST_METHOD_ATTRIBUTE()

TEST_METHOD(Method1)
{
    Logger::WriteMessage("In Method1");
    Assert::AreEqual(0, 0);
}
```

### <a name="c-trait-attribute-macros"></a>C++-Merkmalsattributmakros

Die folgenden vordefinierten Merkmale befinden sich in *`CppUnitTest.h`* . Weitere Informationen finden Sie unter [Referenz für die C++-API „Microsoft.VisualStudio.TestTools.CppUnitTestFramework“](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md).

|Makro|Beschreibung|
|-|-----------------|
|`TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)`|Verwenden Sie zum Definieren eines Merkmals das TEST_METHOD_ATTRIBUTE-Makro.|
|`TEST_OWNER(ownerAlias)`|Verwenden Sie das vordefinierte Merkmal "Besitzer", um einen Besitzer der Testmethode anzugeben.|
|`TEST_PRIORITY(priority)`|Verwenden Sie das vordefinierte Merkmal "Priorität", um den Testmethoden relative Prioritäten zuzuweisen.|

## <a name="see-also"></a>Siehe auch

- [Schnellstart: Testgesteuerte Entwicklung mit dem Test-Explorer](../test/quick-start-test-driven-development-with-test-explorer.md)
