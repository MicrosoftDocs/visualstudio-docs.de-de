---
title: C++Klassen in Klassen-Designer
description: Erfahren Sie mehr über C++-Klassen, wie sie unterstützt werden und im Klassen-Designer über mehrere Vererbungsbeziehungen verfügen können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.inheritancelinelabel
helpviewer_keywords:
- Class Designer [Visual Studio], classes
ms.assetid: 75e56f8c-11ef-42a3-b7ec-3d2cf25c581b
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 593ca8ba3edc3c779a0440a35551bf870f20c831
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94901205"
---
# <a name="c-classes-in-class-designer"></a>C++Klassen in Klassen-Designer

Der **Klassen-Designer** unterstützt C++-Klassen und visualisiert native C++-Klassen auf die gleiche Weise wie Visual Basic- und C#-Klassenformen, mit Ausnahme, dass C++-Klassen über mehrere Vererbungsbeziehungen verfügen können. Sie können die Klassenform erweitern, um mehr Felder und Methoden in der Klasse anzuzeigen, oder sie aus Platzgründen reduzieren.

> [!NOTE]
> Der **Klassen-Designer** unterstützt keine Unions (eine spezielle Klasse, bei der der zugeordnete Arbeitsspeicher nur so groß wie der größte Datenmember der Union ist).

## <a name="simple-inheritance"></a>Einfache Vererbung

Wenn Sie mehr als eine Klasse in ein Klassendiagramm ziehen, und die Klassen verfügen über eine Klassenvererbungsbeziehung, werden sie durch einen Pfeil verbunden. Der Pfeil zeigt in Richtung der Basisklasse. Wenn z.B. die folgenden Klassen in einem Klassendiagramm angezeigt werden, werden sie durch einen Pfeil verbunden, der von B nach A zeigt:

```cpp
class A {};
class B : A {};
```

Sie können auch nur Klasse B in das Klassendiagramm ziehen: Klicken Sie mit der rechten Maustaste auf die Klassenform für B, und klicken Sie dann auf **Basisklassen anzeigen**. Dadurch wird die Basisklasse angezeigt: A.

## <a name="multiple-inheritance"></a>Mehrfachvererbung

Der **Klassen-Designer** unterstützt die Visualisierung der Vererbungsbeziehungen mehrerer Klassen. *Mehrfache Vererbung* wird verwendet, wenn eine abgeleitete Klasse Attribute von mehr als einer Basisklasse hat. Es folgt ein Beispiel für mehrfache Vererbung:

```cpp
class Bird {};
class Swimmer {};
class Penguin : public Bird, public Swimmer {};
```

Wenn Sie mehr als eine Klasse in das Klassendiagramm ziehen, und die Klassen verfügen über eine Vererbungsbeziehung mehrerer Klassen, werden sie durch einen Pfeil verbunden. Der Pfeil zeigt in Richtung der Basisklassen.

Durch einen Rechtsklick auf eine Klassenform und anschließend durch Klicken auf **Basisklassen anzeigen**, wird die Basisklasse für die ausgewählte Klasse angezeigt,

> [!NOTE]
> Der Befehl **Abgeleitete Klassen anzeigen** wird für C++-Code nicht unterstützt. Sie können abgeleitete Klassen anzeigen, indem Sie zur **Klassenansicht** wechseln, den Typknoten erweitern, den Unterordner **Abgeleitete Typen** erweitern und anschließend diese Typen in das Klassendiagramm ziehen.

Weitere Informationen über die Vererbung von mehreren Klasse finden Sie unter [Mehrfachvererbung](/previous-versions/6td5yws2(v=vs.140)) und [Mehrere Basisklassen](/cpp/cpp/multiple-base-classes).

## <a name="abstract-classes"></a>Abstrakte Klassen

Der **Klassen-Designer** unterstützt abstrakte Klassen (auch als „abstrakte Basisklassen“ bezeichnet). Dies sind Klassen, die nicht instanziiert, aber von denen andere Klassen abgeleitet werden können. Wenn Sie ein Beispiel aus „Mehrfachvererbungs“ weiter oben in diesem Dokument verwenden, können Sie womöglich die `Bird`-Klasse als einzelne Objekte wie folgt instanziieren:

```cpp
int main()
{
   Bird sparrow;
   Bird crow;
   Bird eagle;
}
```

Sie können jedoch nicht die `Swimmer`-Klasse als einzelnes Objekt instanziieren. Sie können nur andere Tierklassen davon ableiten, z.B. `Penguin`, `Whale` und `Fish`. In diesem Fall müssten Sie die `Swimmer`-Klasse als eine abstrakte Basisklasse deklarieren.

Um eine Klasse als abstrakt zu deklarieren, können Sie das Schlüsselwort `abstract` verwenden. Als abstrakt markierte Member oder Member in einer abstrakten Klasse sind virtuell und müssen von Klassen, die von der abstrakten Klasse abgeleitet wurden, implementiert werden.

```cpp
class Swimmer abstract
{
   virtual void swim();
   void dive();
};
```

Eine Klasse kann auch als abstrakt deklariert werden, indem mindestens eine rein virtuelle Funktion eingeschlossen wird:

```cpp
class Swimmer
{
   virtual void swim() = 0;
   void dive();
};
```

Beim Anzeigen dieser Deklarationen in einem Klassendiagramm werden der Klassenname `Swimmer` und dessen rein virtuelle Funktion `swim` als kursiv in einer abstrakten Klassenform zusammen mit der Bezeichnung **Abstrakte Klasse** angezeigt. Beachten Sie, dass die Typform der abstrakten Klasse identisch mit einer normalen Klasse ist, außer dass der Rahmen eine gepunktete Linie ist.

Eine von einer abstrakten Klasse abgeleitete Klasse muss jede rein virtuelle Funktion in der Basisklasse überschreiben, oder die abgeleitete Klasse kann nicht instanziiert werden. In diesem Fall muss z.B. bei der Ableitung einer `Fish`-Klasse von der `Swimmer`-Klasse, `Fish` die `swim`-Methode überschreiben:

```cpp
class Fish : public Swimmer
{
   void swim(int speed);
};

int main()
{
   Fish guppy;
}
```

Wenn dieser Code in einem Klassendiagramm angezeigt wird, zeichnet der **Klassen-Designer** eine Vererbungslinie von `Fish` zu `Swimmer`.

## <a name="anonymous-classes"></a>Anonyme Klassen

Der **Klassen-Designer** unterstützt anonyme Klassen. *Anonyme Klassentypen* sind Klassen, die ohne Bezeichner deklariert werden. Sie können keinen Konstruktor oder Destruktor besitzen, können nicht als Argumente oder Funktionen übergeben werden und können nicht als Rückgabewerte von Funktionen zurückgegeben werden. Sie können eine anonyme Klasse verwenden, um einen Klassennamen durch einen TypeDef-Namen wie im folgenden Beispiel zu ersetzen:

```cpp
typedef struct
{
    unsigned x;
    unsigned y;
} POINT;
```

Strukturen können auch anonym sein. Im **Klassen-Designer** werden anonyme Klassen und Strukturen auf die gleiche Weise wie der entsprechende Typ angezeigt. Obwohl Sie anonyme Klassen und Strukturen deklarieren und anzeigen können, verwendet der **Klassen-Designer** nicht den von Ihnen angegebenen Tagnamen. Es wird der Name verwendet, der von der Klassenansicht generiert wird. Die Klasse oder Struktur wird in der Klassenansicht und im **Klassen-Designer** als ein Element namens **__unnamed** angezeigt.

Weitere Informationen zu anonymen Klassen finden Sie unter [Anonyme Klassentypen](/cpp/cpp/anonymous-class-types).

## <a name="template-classes"></a>Vorlagenklassen

Der **Klassen-Designer** unterstützt die Visualisierung von Vorlagenklassen. Geschachtelte Deklarationen werden unterstützt. Die folgende Tabelle zeigt einige Standarddeklarationen.

| Codeelement | Ansicht „Klassen-Designer“ |
| - | - |
| `template <class T>`<br /><br /> `class A {};` | `A<T>`<br /><br /> Vorlagenklasse |
| `template <class T, class U>`<br /><br /> `class A {};` | `A<T, U>`<br /><br /> Vorlagenklasse |
| `template <class T, int i>`<br /><br /> `class A {};` | `A<T, i>`<br /><br /> Vorlagenklasse |
| `template <class T, template <class K> class U>`<br /><br /> `class A {};` | `A<T, U>`<br /><br /> Vorlagenklasse |

Die folgende Tabelle zeigt einige Beispiele für die teilweise Spezialisierung.

|Codeelement|Ansicht „Klassen-Designer“|
|------------------| - |
|`template<class T, class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Vorlagenklasse|
|`template<class T>`<br /><br /> `class A<T, T> {};`|`A<T, T>`<br /><br /> Vorlagenklasse|
|`template <class T>`<br /><br /> `class A<T, int> {};`|`A<T, int>`<br /><br /> Vorlagenklasse|
|`template <class T1, class T2>`<br /><br /> `class A<T1*, T2*> {};`|`A<T1*, T2*>`<br /><br /> Vorlagenklasse|

Die folgende Tabelle zeigt einige Beispiele der Vererbung in der partiellen Spezialisierung.

|Codeelement|Ansicht „Klassen-Designer“|
|------------------| - |
|`template <class T, class U>`<br /><br /> `class A {};`<br /><br /> `template <class TC>`<br /><br /> `class A<T, int> {};`<br /><br /> `class B : A<int, float>`<br /><br /> `{};`<br /><br /> `class C : A<int, int>`<br /><br /> `{};`|`A<T, U>`<br /><br /> Vorlagenklasse<br /><br /> `B`<br /><br /> Klasse<br /><br /> (zeigt auf Klasse A)<br /><br /> `C`<br /><br /> Klasse<br /><br /> (zeigt auf Klasse A)|

Die folgende Tabelle zeigt einige Beispiele für die partielle Spezialisierung von Vorlagenfunktionen.

|Codeelement|Ansicht „Klassen-Designer“|
|------------------| - |
|`class A`<br /><br /> `{`<br /><br /> `template <class T, class U>`<br /><br /> `void func(T a, U b);`<br /><br /> `template <class T>`<br /><br /> `void func(T a, int b);`<br /><br /> `};`|`A`<br /><br /> func\<T, U> (+ 1 Überladung)|
|`template <class T1>`<br /><br /> `class A {`<br /><br /> `template <class T2>`<br /><br /> `class B {};`<br /><br /> `};`<br /><br /> `template<> template<>`<br /><br /> `class A<type>::B<type> {};`|`A<T1>`<br /><br /> Vorlagenklasse<br /><br /> `B<T2>`<br /><br /> Vorlagenklasse<br /><br /> (B ist in Klasse A unter **geschachtelte Typen** enthalten)|
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `class A : C<int> {};`|`A`<br /><br /> Klasse<br /><br /> -> C\<int><br /><br /> `C<T>`<br /><br /> Vorlagenklasse|

Die folgende Tabelle zeigt einige Beispiele der Vorlagenvererbung.

|Codeelement|Ansicht „Klassen-Designer“|
|------------------| - |
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {`<br /><br /> `class B {};`<br /><br /> `}`<br /><br /> `class A : C<int>::B {};`|`A`<br /><br /> Klasse<br /><br /> ->B<br /><br /> `C<int>`<br /><br /> Klasse<br /><br /> (B ist in Klasse C unter **geschachtelte Typen** enthalten )<br /><br /> `C<T>`<br /><br /> Vorlagenklasse|

Die folgende Tabelle zeigt einige Beispiele der kanonischen spezialisierten Klassenverbindung.

|Codeelement|Ansicht „Klassen-Designer“|
|------------------| - |
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {};`<br /><br /> `class A : C<int> {};`<br /><br /> `class D : C<float> {};`|`A`<br /><br /> Klasse<br /><br /> ->C\<int><br /><br /> `C<int>`<br /><br /> Klasse<br /><br /> `C<T>`<br /><br /> Vorlagenklasse<br /><br /> `D`<br /><br /> Klasse<br /><br /> ->C\<float>|
|`class B {`<br /><br /> `template <class T>`<br /><br /> `T min (const T &a, const T &b);`<br /><br /> `};`|`B`<br /><br /> min \<T>|

## <a name="see-also"></a>Weitere Informationen

- [Arbeiten mit C++-Code](working-with-visual-cpp-code.md)
- [Klassen und Strukturen](/cpp/cpp/classes-and-structs-cpp)
- [Anonyme Klassentypen](/cpp/cpp/anonymous-class-types)
- [Mehrfachvererbung](/previous-versions/6td5yws2(v=vs.140))
- [Mehrere Basisklassen](/cpp/cpp/multiple-base-classes)
- [Vorlagen](/cpp/cpp/templates-cpp)