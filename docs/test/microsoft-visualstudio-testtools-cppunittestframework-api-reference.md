---
title: Microsoft.VisualStudio.TestTools.CppUnitTestFramework API
description: Dieser Artikel beschreibt die CppUnitTestFramework-Members, die Sie verwenden können, um C++-Komponententests auf Grundlage des nativen Microsoft-Frameworks für Komponententests zu schreiben.
ms.custom: SEO-VS-2020
ms.date: 09/27/2019
ms.topic: reference
ms.author: corob
manager: jmartens
ms.workload:
- multiple
author: corob-msft
ms.openlocfilehash: 355259f784d496fae574a331382d03d3fbe5bfd6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844527"
---
# <a name="microsoftvisualstudiotesttoolscppunittestframework-api-reference"></a>Referenz für die API „Microsoft.VisualStudio.TestTools.CppUnitTestFramework“

In diesem Thema werden die öffentlichen Member des Namespace `Microsoft::VisualStudio::CppUnitTestFramework` aufgeführt. Mit diesen APIs können Sie C++-Komponententests auf Grundlage des nativen Microsoft-Komponententest-Frameworks schreiben. Am Ende des Artikels finden Sie ein [Beispiel für die Verwendung](#example).

Die Header- und Bibliotheksdateien befinden sich unter *\<Visual Studio installation folder>\VC\Auxiliary\VS\UnitTest*.

Header- und Bibliothekspfade werden automatisch in einem nativen Testprojekt konfiguriert.

## <a name="in-this-topic"></a><a name="In_this_topic"></a> In diesem Thema

[CppUnitTest.h](#cppUnitTest_h)

- [Erstellen von Testklassen und Methoden](#create_test_classes_and_methods)

- [Initialisieren und Bereinigen](#Initialize_and_cleanup)

  - [Testmethoden](#test_methods)

  - [Testklassen](#test_classes)

  - [Testmodule](#test_modules)

- [Erstellen von Testattributen](#create_test_attributes)

  - [Testmethodenattribute](#test_method_attributes)

  - [Testklassenattribute](#test_class_attributes)

  - [Testmodulattribute](#test_module_attributes)

  - [Vordefinierte Attribute](#pre_defined_attributes)

    [CppUnitTestAssert.h](#cppUnitTestAssert_h)

  - [Allgemeine Assertionen](#general_asserts)

    - [Gleich](#general_are_equal)

    - [Ungleich](#general_are_not_equal)

    - [Stimmen überein](#general_are_same)

    - [Stimmen nicht überein](#general_are_not_same)

    - [Ist Null](#general_is_null)

    - [Ist nicht Null](#general_is_not_null)

    - [Ist TRUE](#general_is_True)

    - [Ist FALSE](#general_is_false)

    - [Fehler](#general_Fail)

  - [Windows-Runtime-Assertionen](#winrt_asserts)

    - [Gleich](#winrt_are_equal)

    - [Stimmen überein](#winrt_are_same)

    - [Ungleich](#winrt_are_not_equal)

    - [Stimmen nicht überein](#winrt_are_not_same)

    - [Ist Null](#winrt_is_null)

    - [Ist nicht Null](#winrt_is_not_null)

  - [Ausnahme-Assertionen](#exception_asserts)

    - [Ausnahme erwarten](#expect_exception)

      [CppUnitTestLogger.h](#cppunittestlogger_h)

    - [Protokollierung](#logger)

    - [Nachricht schreiben](#write_message)

  - [Beispiel für die Verwendung](#example)

## <a name="cppunittesth"></a><a name="cppUnitTest_h"></a> CppUnitTest.h

### <a name="create-test-classes-and-methods"></a><a name="create_test_classes_and_methods"></a> Erstellen von Testklassen und Methoden

```cpp
TEST_CLASS(className)
```

Erforderlich für jede Klasse, die Testmethoden enthält. Bezeichnet *className* als Testklasse. `TEST_CLASS` muss im Gültigkeitsbereich des Namespaces deklariert werden.

```cpp
TEST_METHOD(methodName)
{
    // test method body
}
```

Definiert *methodName* als Testmethode. `TEST_METHOD` muss im Gültigkeitsbereich der Klasse der Methode deklariert werden.

### <a name="initialize-and-cleanup"></a><a name="Initialize_and_cleanup"></a> Initialisieren und Bereinigen

#### <a name="test-methods"></a><a name="test_methods"></a> Testmethoden

```cpp
TEST_METHOD_INITIALIZE(methodName)
{
    // method initialization code
}
```

Definiert *methodName* als Methode, die vor jeder Testmethode ausgeführt wird. `TEST_METHOD_INITIALIZE` kann in einer Testklasse nur einmal definiert werden und muss im Gültigkeitsbereich der Testklasse definiert werden.

```cpp
TEST_METHOD_CLEANUP(methodName)
{
    // test method cleanup  code
}
```

Definiert *methodName* als Methode, die nach jeder Testmethode ausgeführt wird. `TEST_METHOD_CLEANUP` kann in einer Testklasse nur einmal definiert werden und muss im Gültigkeitsbereich der Testklasse definiert werden.

#### <a name="test-classes"></a><a name="test_classes"></a> Testklassen

```cpp
TEST_CLASS_INITIALIZE(methodName)
{
    // test class initialization  code
}
```

Definiert *methodName* als Methode, die vor dem Erstellen der einzelnen Testklassen ausgeführt wird. `TEST_CLASS_INITIALIZE` kann in einer Testklasse nur einmal definiert werden und muss im Gültigkeitsbereich der Testklasse definiert werden.

```cpp
TEST_CLASS_CLEANUP(methodName)
{
    // test class cleanup  code
}
```

Definiert *methodName* als Methode, die nach dem Erstellen der einzelnen Testmethoden ausgeführt wird. `TEST_CLASS_CLEANUP` kann in einer Testklasse nur einmal definiert werden und muss im Gültigkeitsbereich der Testklasse definiert werden.

#### <a name="test-modules"></a><a name="test_modules"></a> Testmodule

```cpp
TEST_MODULE_INITIALIZE(methodName)
{
    // module initialization code
}
```

Definiert die Methode *methodName*, die beim Laden eines Moduls ausgeführt wird. `TEST_MODULE_INITIALIZE` kann in einem Testmodul nur einmal definiert werden und muss im Gültigkeitsbereich des Namespace deklariert werden.

```cpp
TEST_MODULE_CLEANUP(methodName)
```

Definiert die Methode *methodName*, die beim Entladen eines Moduls ausgeführt wird. `TEST_MODULE_CLEANUP` kann in einem Testmodul nur einmal definiert werden und muss im Gültigkeitsbereich des Namespace deklariert werden.

### <a name="create-test-attributes"></a><a name="create_test_attributes"></a> Erstellen von Testattributen

#### <a name="test-method-attributes"></a><a name="test_method_attributes"></a> Testmethodenattribut

```cpp
BEGIN_TEST_METHOD_ATTRIBUTE(testMethodName)
    TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_METHOD_ATTRIBUTE()
```

Fügt die Attribute hinzu, die mit einem oder mehreren `TEST_METHOD_ATTRIBUTE`-Makros der Testmethode *testMethodName* definiert werden.

Ein `TEST_METHOD_ATTRIBUTE`-Makro definiert ein Attribut mit dem Namen *attributeName* und dem Wert *attributeValue*.

#### <a name="test-class-attributes"></a><a name="test_class_attributes"></a> Testklassenattribute

```cpp
BEGIN_TEST_CLASS_ATTRIBUTE(testClassName)
    TEST_CLASS_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_CLASS_ATTRIBUTE()
```

Fügt die Attribute hinzu, die mit einem oder mehreren `TEST_CLASS_ATTRIBUTE`-Makros der Testklasse *testClassName* definiert werden.

Ein `TEST_CLASS_ATTRIBUTE`-Makro definiert ein Attribut mit dem Namen *attributeName* und dem Wert *attributeValue*.

#### <a name="test-module-attributes"></a><a name="test_module_attributes"></a> Testmodulattribute

```cpp
BEGIN_TEST_MODULE_ATTRIBUTE(testModuleName)
    TEST_MODULE_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_MODULE_ATTRIBUTE()
```

Fügt die Attribute hinzu, die mit einem oder mehreren `TEST_MODULE_ATTRIBUTE`-Makros der Testmodule *testModuleName* definiert werden.

Ein `TEST_MODULE_ATTRIBUTE`-Makro definiert ein Attribut mit dem Namen *attributeName* und dem Wert *attributeValue*.

#### <a name="pre-defined-attributes"></a><a name="pre_defined_attributes"></a> Vordefinierte Attribute

Diese vordefinierten Attributmakros werden für gängige Fälle zur Verfügung gestellt. Sie können durch das oben beschriebene Makro `TEST_METHOD_ATTRIBUTE` ersetzt werden.

```cpp
TEST_OWNER(ownerAlias)
```

Definiert ein `TEST_METHOD_ATTRIBUTE` mit dem Namen `Owner` und dem Attributwert *ownerAlias*.

```cpp
TEST_DESCRIPTION(description)
```

Definiert ein `TEST_METHOD_ATTRIBUTE` mit dem Namen `Description` und dem Attributwert *description*.

```cpp
TEST_PRIORITY(priority)
```

Definiert ein `TEST_METHOD_ATTRIBUTE` mit dem Namen `Priority` und dem Attributwert *priority*.

```cpp
TEST_WORKITEM(workitem)
```

Definiert ein `TEST_METHOD_ATTRIBUTE` mit dem Namen `WorkItem` und dem Attributwert *workItem*.

```cpp
TEST_IGNORE()
```

Definiert ein `TEST_METHOD_ATTRIBUTE` mit dem Namen `Ignore` und dem Attributwert `true`.

## <a name="cppunittestasserth"></a><a name="cppUnitTestAssert_h"></a> CppUnitTestAssert.h

### <a name="general-asserts"></a><a name="general_asserts"></a> Allgemeine Assertionen

#### <a name="are-equal"></a><a name="general_are_equal"></a> Gleich
Überprüft, ob zwei Objekte gleich sind.

```cpp
template<typename T>
static void Assert::AreEqual(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Überprüft, ob zwei double-Elemente gleich sind.

```cpp
static void Assert::AreEqual(
    double expected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Überprüft, ob zwei float-Elemente gleich sind.

```cpp
static void Assert::AreEqual(
    float expected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Überprüft, ob zwei char*-Zeichenfolgen gleich sind.

```cpp
static void Assert::AreEqual(
    const char* expected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Überprüft, ob zwei w_char*-Zeichenfolgen gleich sind.

```cpp
static void Assert::AreEqual(
    const wchar_t* expected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-not-equal"></a><a name="general_are_not_equal"></a> Ungleich
Überprüft, ob zwei double-Elemente ungleich sind.

```cpp
static void Assert::AreNotEqual(
    double notExpected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Überprüft, ob zwei float-Elemente ungleich sind.

```cpp
static void Assert::AreNotEqual(
    float notExpected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Überprüft, ob zwei char*-Zeichenfolgen ungleich sind.

```cpp
static void Assert::AreNotEqual(
    const char* notExpected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Überprüft, ob zwei w_char*-Zeichenfolgen ungleich sind.

```cpp
static void Assert::AreNotEqual(
    const wchar_t* notExpected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Überprüft mit operator==, ob zwei Verweise ungleich sind.

```cpp
template<typename T>
static void Assert::AreNotEqual(
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-same"></a><a name="general_are_same"></a> Stimmen überein
Überprüft, ob zwei Verweise auf dieselbe Objektinstanz (Identität) verweisen.

```cpp
template<typename T>
static void Assert::AreSame(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-not-same"></a><a name="general_are_not_same"></a> Stimmen nicht überein
Überprüft, ob zwei Verweise nicht auf dieselbe Objektinstanz (Identität) verweisen.

```cpp
template<typename T>
static void Assert::AreNotSame (
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-null"></a><a name="general_is_null"></a> Ist Null
Überprüft, ob ein Zeiger NULL ist.

```cpp
template<typename T>
static void Assert::IsNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-not-null"></a><a name="general_is_not_null"></a> Ist nicht Null
Überprüft, ob ein Zeiger nicht NULL ist.

```cpp
template<typename T>
static void Assert::IsNotNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-true"></a><a name="general_is_True"></a> Ist TRUE
Überprüft, ob eine Bedingung wahr ist.

```cpp
static void Assert::IsTrue(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-false"></a><a name="general_is_false"></a> Ist FALSE
Überprüft, ob eine Bedingung falsch ist.

```cpp
static void Assert::IsFalse(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="fail"></a><a name="general_Fail"></a> Fehler
Setzt durch, dass das Ergebnis des Testfalls als Fehler zählt.

```cpp
static void Assert::Fail(
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

### <a name="windows-runtime-asserts"></a><a name="winrt_asserts"></a> Windows-Runtime-Assertionen

#### <a name="are-equal"></a><a name="winrt_are_equal"></a> Gleich
Überprüft, ob zwei Windows-Runtime-Zeiger gleich sind.

```cpp
template<typename T>
static void Assert::AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

Überprüft, ob zwei Platform::String^-Zeichenfolgen gleich sind.

```cpp
template<typename T>
static void Assert::AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-same"></a><a name="winrt_are_same"></a> Stimmen überein
Überprüft, ob zwei Windows-Runtime-Verweise auf dasselbe Objekt verweisen.

```cpp
template<typename T>
static void Assert::AreSame(
    T% expected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-not-equal"></a><a name="winrt_are_not_equal"></a> Ungleich
Überprüft, ob zwei Windows-Runtime-Zeiger ungleich sind.

```cpp
template<typename T>
static void Assert::AreNotEqual(
    T^ notExpected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

Überprüft, ob zwei Platform::String^-Zeichenfolgen ungleich sind.

```cpp
static void Assert::AreNotEqual(
    Platform::String^ notExpected,
    Platform::String^ actual,
    bool ignoreCase = false,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-not-same"></a><a name="winrt_are_not_same"></a> Stimmen nicht überein
Überprüft, ob zwei Windows-Runtime-Verweise nicht auf dasselbe Objekt verweisen.

```cpp
template<typename T>
static void Assert::AreNotSame(
    T% notExpected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="is-null"></a><a name="winrt_is_null"></a> Ist Null
Überprüft, ob ein Windows-Runtime-Zeiger ein „nullptr“ ist.

```cpp
template<typename T>
static void Assert::IsNull(
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="is-not-null"></a><a name="winrt_is_not_null"></a> Ist nicht Null
Überprüft, ob ein Windows-Runtime-Zeiger kein „nullptr“ ist.

```cpp
template<typename T>
static void Assert::IsNotNull(
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

### <a name="exception-asserts"></a><a name="exception_asserts"></a> Ausnahme-Assertionen

#### <a name="expect-exception"></a><a name="expect_exception"></a> Ausnahme erwarten
Überprüft, ob eine Funktion eine Ausnahme auslöst:

```cpp
template<typename _EXPECTEDEXCEPTION, typename _FUNCTOR>
static void Assert::ExpectException(
    _FUNCTOR functor,
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo= NULL)
```

Überprüft, ob eine Funktion eine Ausnahme auslöst:

```cpp
template<typename _EXPECTEDEXCEPTION, typename _RETURNTYPE>
    static void Assert::ExpectException(
    _RETURNTYPE (*func)(),
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo = NULL)
```

## <a name="cppunittestloggerh"></a><a name="cppunittestlogger_h"></a> CppUnitTestLogger.h

### <a name="logger"></a><a name="logger"></a> Protokollierung
Die Protokollierungsklasse enthält statische Methoden zum Schreiben in das **Ausgabefenster**.

### <a name="write-message"></a><a name="write_message"></a> Nachricht schreiben
Schreiben einer Zeichenfolge in das **Ausgabefenster**

```cpp
static void Logger::WriteMessage(const wchar_t* message)
```

```cpp
static void Logger::WriteMessage(const char* message)
```

## <a name="example"></a><a name="example"></a> Beispiel
Dieser Code veranschaulicht, wie Sie „VSCppUnit“ verwenden können. Er enthält Beispiele für Attributmetadaten, Prüfvorrichtungen, Komponententests mit Assertionsanweisungen und benutzerdefiniertem Protokollieren.

```cpp
// USAGE EXAMPLE

#include <CppUnitTest.h>

using namespace Microsoft::VisualStudio::CppUnitTestFramework;

BEGIN_TEST_MODULE_ATTRIBUTE()
    TEST_MODULE_ATTRIBUTE(L"Date", L"2010/6/12")
END_TEST_MODULE_ATTRIBUTE()

TEST_MODULE_INITIALIZE(ModuleInitialize)
{
    Logger::WriteMessage("In Module Initialize");
}

TEST_MODULE_CLEANUP(ModuleCleanup)
{
    Logger::WriteMessage("In Module Cleanup");
}

TEST_CLASS(Class1)
{

public:

    Class1()
    {
        Logger::WriteMessage("In Class1");
    }

    ~Class1()
    {
        Logger::WriteMessage("In ~Class1");
    }

    TEST_CLASS_INITIALIZE(ClassInitialize)
    {
        Logger::WriteMessage("In Class Initialize");
    }

    TEST_CLASS_CLEANUP(ClassCleanup)
    {
        Logger::WriteMessage("In Class Cleanup");
    }

    BEGIN_TEST_METHOD_ATTRIBUTE(Method1)
        TEST_OWNER(L"OwnerName")
        TEST_PRIORITY(1)
    END_TEST_METHOD_ATTRIBUTE()

    TEST_METHOD(Method1)
    {
        Logger::WriteMessage("In Method1");
        Assert::AreEqual(0, 0);
    }

    TEST_METHOD(Method2)
    {
        Assert::Fail(L"Fail");
    }
};
```

## <a name="see-also"></a>Siehe auch

- [Ausführen von Komponententests für Code](../test/unit-test-your-code.md)
- [Schreiben von Komponententests für C/C++](writing-unit-tests-for-c-cpp.md)
