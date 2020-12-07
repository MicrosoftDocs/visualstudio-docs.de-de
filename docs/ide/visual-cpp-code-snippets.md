---
title: Visual C#-Codeausschnitte
description: Hier erfahren Sie, wie Sie Codeausschnitte zum Hinzufügen von häufig verwendetem Code zu den C++-Codedateien verwenden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: corob-msft
ms.author: corob
manager: markl
dev_langs:
- CPP
ms.workload:
- cplusplus
ms.openlocfilehash: e5cde2be817c49344e02ff06030022f99790a7a2
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "96478808"
---
# <a name="visual-c-code-snippets"></a>Visual C#-Codeausschnitte

In Visual Studio können Sie Codeausschnitte zum Hinzufügen von häufig verwendetem Code zu denC++-Codedateien verwenden. Im Allgemeinen können Sie Codeausschnitte auf gleiche Weise wie in C# verwenden, aber der Satz der Standard-Codeausschnitten ist anders.

Sie können einen Codeausschnitt an einer bestimmten Stelle im Code hinzufügen (Einfügung) oder ausgewählten Code mit einem Codeausschnitt umschließen.

## <a name="insert-a-code-snippet"></a>Einfügen eines Codeausschnitts

Öffnen Sie zum Einfügen eines Codeausschnitts eine C++-Codedatei ( *.cpp* oder *.h*), klicken Sie auf eine beliebige Stelle in der Datei, und führen Sie eine der folgenden Aktionen aus:

- Klicken Sie mit der rechten Maustaste, um im Kontextmenü **Ausschnitt einfügen** auszuwählen.

- Wählen Sie im Menü **Bearbeiten/IntelliSense** die Option **Ausschnitt einfügen** aus.

- Verwenden Sie folgenden Tastaturbefehl: **STRG**+**K**+**X**

Es sollte eine Liste mit Auswahlmöglichkeiten beginnend mit **#if** angezeigt werden. Bei der Auswahl von **#if** sollte der folgende Code in die Datei eingefügt werden:

```cpp
#if 0

#endif // 0
```

Sie können dann **0** durch die richtige Bedingung ersetzen.

## <a name="use-a-code-snippet-to-surround-selected-code"></a>Verwenden eines Codeausschnitts zum Umschließen von ausgewähltem Code

Um einen Codeausschnitt zum Umschließen des ausgewählten Codes zu verwenden, wählen Sie eine Zeile (oder mehrere Zeilen) aus, und führen Sie eine der folgenden Aktionen aus:

- Klicken Sie mit der rechten Maustaste, um im Kontextmenü **Umschließen mit** auszuwählen.

- Wählen Sie im Menü **Bearbeiten** > **IntelliSense** die Option **Umschließen mit** aus.

- Drücken Sie auf der Tastatur die Tasten: **STRG**+**K**+**S**

Wählen Sie **#if** aus. Die Ausgabe sollte in etwa wie folgt aussehen:

```cpp
#if 0
#include "pch.h"  // or whatever line you had selected
#endif // 0
```

Sie können dann 0 durch die richtige Bedingung ersetzen.

## <a name="where-can-i-find-a-complete-list-of-the-c-code-snippets"></a>Wo finde ich eine vollständige Liste der C++-Codeausschnitte?

Sie finden die vollständige Liste der C++-Codeausschnitte durch das Aufrufen des **Codeausschnitt-Managers** (im Menü **Extras**) und durch das Festlegen der **Sprache** auf **Visual C++**. Erweitern Sie im Fenster darunter **Visual C++**. Sie sollte die Namen aller C++-Codeausschnitte in alphabetischer Reihenfolge sehen.

Die Namen der meisten Codeausschnitte sind selbsterklärend, doch einige Namen sind möglicherweise verwirrend.

## <a name="class-vs-classi"></a>Class im Vergleich zu classi

Der **class**-Ausschnitt stellt die Definition einer Klasse namens `MyClass` mit dem entsprechenden Standardkonstruktor und -destruktor bereit, wo sich die Definitionen von Konstruktor und Destruktor außerhalb der Klasse befinden:

```cpp
class MyClass
{
public:
    MyClass();
    ~MyClass();

private:

};

MyClass::MyClass()
{
}

MyClass::~MyClass()
{
}
```

Der Codeausschnitt **classi** stellt auch die Definition einer Klasse namens `MyClass` bereit, aber der Standardkonstruktor und -destruktor werden innerhalb der Klassendefinition definiert:

```cpp
class MyClass
{
public:
    MyClass()
    {
    }

    ~MyClass()
    {
    }

private:

};
```

## <a name="for-vs-forr-vs-rfor"></a>„for“, „forr“ und „rfor“ im Vergleich

Es gibt drei verschiedene **for**-Ausschnitte, die verschiedene Arten von `for`-Schleifen bereitstellen.

Der **rfor**-Ausschnitt stellt eine [bereichsbasierte](/cpp/cpp/range-based-for-statement-cpp) „for“-Schleife (Link) bereit. Dieses Konstrukt wird gegenüber indexbasierten `for`-Schleifen bevorzugt.

```cpp
for (auto& i : v)
{

}
```

Der **for**-Ausschnitt stellt eine `for`-Schleife bereit, bei der die Bedingung auf der Länge (in `size_t`) eines Objekts basiert.

```cpp
for (size_t i = 0; i < length; i++)
{

}
```

Der **forr**-Ausschnitt stellt eine umgekehrte `for`-Schleife bereit, bei der die Bedingung auf der Länge (in ganzen Zahlen) eines Objekts basiert:

```cpp
for (int i = length - 1; i >= 0; i--)
{

}
```

## <a name="the-destructor-snippet-"></a>Der Destruktor-Ausschnitt (~)

Der Destruktor-Ausschnitt ( **~** ) zeigt unterschiedliches Verhalten in unterschiedlichen Kontexten. Wenn Sie diesen Ausschnitt innerhalb einer Klasse einfügen, stellt er einen Destruktor für diese Klasse bereit. Betrachten Sie beispielsweise den folgenden Code:

```cpp
class SomeClass {

};
```

Wenn Sie den Destruktor-Ausschnitt einfügen, wird einen Destruktor für `SomeClass` bereitgestellt:

```cpp
class SomeClass {
    ~SomeClass()
    {

    }
};
```

Wenn Sie versuchen, den Destruktor-Ausschnitt außerhalb einer Klasse einzufügen, wird ein Destruktor mit einem Platzhalternamen bereitgestellt:

```cpp
~TypeNamePlaceholder()
{
```

## <a name="see-also"></a>Siehe auch

- [Codeausschnitte](../ide/code-snippets.md)