---
title: Häufige schnelle Aktionen
description: Die beliebtesten Schnellaktionen für C# und Visual Basic sind unter anderem das Bearbeiten falsch geschriebener Schlüsselwörter oder falscher Symbole, das Lösen von Mergekonflikten, das Entfernen nötiger Importe, das Generieren von Typen, die Einführung lokaler Variablen usw.
ms.date: 03/28/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: d24b03bc79c32c32c570d26b7607d1ba36c1c1df
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970906"
---
# <a name="common-quick-actions"></a>Häufige schnelle Aktionen

Die Abschnitte in diesem Thema enthalten einige der häufig vorkommenden **Schnellen Aktionen**, die sowohl für C#- als auch für Visual Basic-Code gültig sind. Diese Aktionen stellen *Codefehlerbehebungen* für Compilerdiagnosen oder die integrierten [.NET Compiler Platform Analyzer](../code-quality/roslyn-analyzers-overview.md) in Visual Studio dar.

## <a name="actions-that-fix-errors"></a>Aktionen, die Fehler korrigieren

Über die schnellen Aktionen in diesem Abschnitt werden Fehler in Code behoben, durch die der Build fehlschlagen würde. Wenn schnelle Aktionen zur Behebung eines Fehlers auf einer Codezeile verfügbar sind, wird am Rand oder unterhalb der roten Wellenlinie eine Glühbirne mit einem roten „x“ angezeigt.

![Fehlersymbol und Menü für schnelle Aktionen](media/error-light-bulb-with-code.png)

### <a name="correct-misspelled-symbol-or-keyword"></a>Richtige falsch geschriebenes Symbol oder Schlüsselwort

Wenn Sie versehentlich einen Typ oder ein Schlüsselwort in Visual Studio falsch schreiben, korrigiert diese schnelle Aktion diesen Fehler für Sie. Diese Elemente werden im Fehlerbehebungsmenü als **"Change '\<misspelled word>' to '\<correct word>'"** angezeigt. Beispiel:

```csharp
// Before
private viod MyMethod()
{
}

// Change 'viod' to 'void'

// After
private void MyMethod()
{
}
```

```vb
' Before
Function MyFunction as Intger
End Function

' Change 'Intger' to 'Integer'

' After
Function MyFunction as Integer
End Function
```

| Fehler-ID | Anzuwendende Sprachen |
| - | - |
| CS0103, BC30002 | C# und Visual Basic |

### <a name="resolve-git-merge-conflict"></a>Lösen von Git-Mergekonflikten

Diese schnellen Aktionen ermöglichen das Auflösen von Mergekonflikten durch das „Vornehmen einer Änderung“, wodurch der in Konflikt stehende Code und die Marker entfernt werden.

```csharp
// Before
private void MyMethod()
{
    if (false)
    {

    }
}

// Take changes from 'HEAD'

// After
private void MyMethod()
{
    if (true)
    {

    }
}
```

| Fehler-ID | Anzuwendende Sprachen | Unterstützte Version |
| ------- | -------------------- | ---------------- |
| CS8300, BC37284 | C# und Visual Basic | Visual Studio 2017, Version 15.3 und höher |

## <a name="actions-that-remove-unnecessary-code"></a>Aktionen, die nicht benötigten Code entfernen

### <a name="remove-unnecessary-usingsimports"></a>Nicht benötigte Using- und Import-Anweisungen entfernen

Die schnelle Aktion **Nicht benötigte Using-/Import-Anweisungen entfernen** entfernt jede nicht benötigte `using`- und `Import`-Anweisung aus der aktuellen Datei. Wenn Sie dieses Element auswählen, werden nicht benötigte import-Anweisungen des Namespaces entfernt.

| Anzuwendende Sprachen | Unterstützte Version |
| - | - |
| C# und Visual Basic | Visual Studio 2015 und höher |

### <a name="remove-unnecessary-cast"></a>Nicht benötigte Umwandlung entfernen

Wenn Sie einen Typ in einen anderen Typ umwandeln, der keine Umwandlung benötigt, entfernt das Element der schnellen Aktion **Remove Unnecessary Cast** (Nicht benötigte Umwandlung entfernen) die nicht benötigte Umwandlung.

```csharp
// before
int number = (int)3;

// Remove Unnecessary Cast

// after
int number = 3;
```

```vb
' Before
Dim number as Integer = CType(3, Integer)

' Remove Unnecessary Cast

' After
Dim number as Integer = 3
```

| Diagnose-ID | Anzuwendende Sprachen | Unterstützte Version |
| ------- | -------------------- | ---------------- |
| IDE0004 | C# und Visual Basic | Visual Studio 2015 und höher |

### <a name="remove-unused-variables"></a>Entfernen nicht verwendeter Variablen

Diese schnelle Aktion ermöglicht Ihnen das Entfernen von Variablen, die zwar deklariert, aber nie in Ihrem Code verwendet wurden.

```csharp
// Before
public MyMethod()
{
    var unused = 8;
    var used = 1;
    return DoStuff(used);
}

// Remove unused variables

// After
public MyMethod()
{
    var used = 1;
    return DoStuff(used);
}
```

| Diagnose-ID | Anzuwendende Sprachen | Unterstützte Version |
| ------- | -------------------- | ---------------- |
| CS0219, BC42024 | C# und Visual Basic | Visual Studio 2017, Version 15.3 und höher |

### <a name="remove-type-from-default-value-expression"></a>Entfernen des Typs aus dem default-Wertausdruck

Diese schnelle Aktion entfernt den Werttyp aus einem Standardwertausdruck und verwendet das [Standardliteral](/dotnet/csharp/language-reference/operators/default#default-literal), wenn der Compiler den Typ des Ausdrucks ableiten kann.

```csharp
// Before
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }

// Simplify default expression

// After
void DoWork(CancellationToken cancellationToken = default) { ... }
```

| Diagnose-ID | Anzuwendende Sprachen | Unterstützte Version |
| ------- | -------------------- | ---------------- |
| IDE0034 | C# 7.1+ | Visual Studio 2017, Version 15.3 und höher |

## <a name="actions-that-add-missing-code"></a>Aktionen, die fehlenden Code hinzufügen

### <a name="add-usingsimports-for-types-in-reference-assemblies-nuget-packages-or-other-types-in-your-solution"></a>Hinzufügen von Using- und Import-Anweisungen für Typen in Verweisassemblys, NuGet-Paketen oder anderen Typen in Ihrer Projektmappe

Using-Typen in anderen Projekten in Ihrer Projektmappe zeigen die schnelle Aktion automatisch an; allerdings müssen alle anderen auf der Registerkarte **Tools > Options > C#** (Tools > Optionen > C#) oder **Basic > Advanced** (Basic > Erweitert) aktiviert werden:

- Usings/Imports für Typen in Verweisassemblys vorschlagen
- Usings/Imports für Typen in NuGet-Paketen vorschlagen

Wenn dies aktiviert ist, wird die using- oder import-Anweisung erstellt, wenn Sie einen Typ in einem Namespace verwenden, der zu diesem Zeitpunkt nicht importiert ist, aber in einer Verweisassembly oder einem NuGet-Paket vorhanden ist.

```csharp
// Before
Debug.WriteLine("Hello");

// using System.Diagnostics;

// After
using System.Diagnostics;

Debug.WriteLine("Hello");
```

```vb
' Before
Debug.WriteLine("Hello")

' Imports System.Diagnostics

' After
Imports System.Diagnostics

Debug.WriteLine("Hello")
```

| Diagnose-ID | Anzuwendende Sprachen |
| - | - |
| CS0103, BC30451 | C# und Visual Basic|

### <a name="add-missing-casesdefault-caseboth"></a>Fügen Sie fehlende Fälle/einen Standardfall/beides hinzu

Wenn Sie eine `switch`-Anweisung in C# oder eine `Select Case`-Anweisung in Visual Basic erstellen, können Sie mit einer Codeaktion automatisch fehlende Fallelemente, eine Standardfallanweisung oder beides hinzufügen.

Betrachten Sie die folgende Enumeration und die leere Anweisung `switch` oder `Select Case`:

```csharp
enum MyEnum
{
    Item1,
    Item2,
    Item3
}

...

MyEnum myEnum = MyEnum.Item1;

switch(myEnum)
{
}
```

```vb
Enum MyEnum
    Item1
    Item2
    Item3
End Enum

...

Dim myEnum as MyEnum = MyEnum.Item1

Select Case myEnum
End Select
```

Mithilfe der schnellen Aktion **Beide hinzufügen** werden fehlende Fälle ausgefüllt, und ein Standardfall wird hinzugefügt:

```csharp
switch(myEnum)
{
    case MyEnum.Item1:
        break;
    case MyEnum.Item2:
        break;
    case MyEnum.Item3:
        break;
    default:
        break;
}
```

```vb
Select Case myEnum
    Case MyEnum.Item1
        Exit Select
    Case MyEnum.Item2
        Exit Select
    Case Else
        Exit Select
End Select
```

| Diagnose-ID | Anzuwendende Sprachen | Unterstützte Version |
| ------- | -------------------- | ---------------- |
| IDE0010 | C# und Visual Basic| Visual Studio 2017, Version 15.3 und höher |

### <a name="add-null-checks-for-parameters"></a>Hinzufügen von Überprüfungen auf NULL für Parameter

Diese schnelle Aktion ermöglicht Ihnen das Hinzufügen einer Prüfung zu Ihrem Code, um zu ermitteln, ob ein Parameter NULL ist.

```csharp
// Before
class MyClass
{
    public string MyProperty { get; set; }

    public MyClass(string myProperty) // cursor inside myProperty
    {
        MyProperty = myProperty;
    }
}

// Add null check

// After
class MyClass
{
    public string MyProperty { get; set; }

    public MyClass(string myProperty)
    {
        MyProperty = myProperty ?? throw new ArgumentNullException(nameof(myProperty));
    }
}
```

| Anzuwendende Sprachen | Unterstützte Version |
| -------------------- | ---------------- |
| C# und Visual Basic| Visual Studio 2017, Version 15.3 und höher |

### <a name="add-argument-name"></a>Hinzufügen des Argumentnamens

```csharp
// Before
var date = new DateTime(1997, 7, 8);

// Include argument name 'year' (include trailing arguments)

// After
var date = new DateTime(year: 1997, month: 7, day: 8);
```

| Anzuwendende Sprachen | Unterstützte Version |
| -------------------- | ---------------- |
| C# und Visual Basic| Visual Studio 2017, Version 15.3 und höher |

### <a name="add-braces"></a>Hinzufügen von geschweiften Klammern

Die schnelle Aktion „Geschweifte Klammern hinzufügen“ umschließt einzeilige `if`-Anweisungen mit geschweiften Klammern.

```csharp
// Before
if (true)
    return "hello,world";

// Add braces

// After
if (true)
{
    return "hello,world";
}
```

| Diagnose-ID | Anzuwendende Sprachen | Unterstützte Version |
| ------- | -------------------- | ---------------- |
| IDE0011 | C# | Visual Studio 2017 und höher |

### <a name="add-and-order-modifiers"></a>Hinzufügen und Sortieren von Modifizierern

Diese schnellen Aktionen unterstützen Sie beim Organisieren von Modifizieren, indem es Ihnen ermöglicht wird, vorhandene Zugriffsmodifizierer zu sortieren und fehlende hinzuzufügen.

```csharp
// Before
enum Color
{
    Red, White, Blue
}

// Add accessibility modifiers

// After
internal enum Color
{
    Red, White, Blue
}
```

```csharp
// Before
static private int thisFieldIsPublic;

// Order modifiers

// After
private static int thisFieldIsPublic;
```

| Diagnose-ID | Anzuwendende Sprachen | Unterstützte Version |
| ------- | -------------------- | ---------------- |
| IDE0036 | C# und Visual Basic| Visual Studio 2017, Version 15.5 und höher |
| IDE0040 | C# und Visual Basic| Visual Studio 2017, Version 15.5 und höher |

## <a name="code-transformations"></a>Codetransformationen

### <a name="convert-if-construct-to-switch"></a>Konvertieren von if-Konstrukten in switch-Konstrukte

Mit dieser schnellen Aktionen können Sie ein **if-then-else**-Konstrukt in ein **switch**-Konstrukt konvertieren.

```csharp
// Before
if (obj is string s)
{
  Console.WriteLine("obj is a string: " + s);
}

else if (obj is int i && i > 10)
{
  Console.WriteLine("obj is an int greater than 10");
}

// Convert to switch

// After
switch (obj)
{
  case string s:
    Console.WriteLine("Obj is a string: " + s);
    break;
  case int i when i > 10:
    Console.WriteLine("obj is an int greater than 10");
    break;
}
```

```vb
' Before
If TypeOf obj Is String s Then
    Console.WriteLine("obj is a string: " + s)
Else If TypeOf obj Is Integer i And i > 10 Then
    Console.WriteLine("obj is an int greater than 10")
End If

' Convert to switch

' After
Select Case obj
  Case String s
    Console.WriteLine("Obj is a string: " + s)
    Exit Sub
  Case Integer i when i > 10
    Console.WriteLine("obj is an int greater than 10")
    Exit Sub
End Select
```

| Anzuwendende Sprachen | Unterstützte Version |
| -------------------- | ---------------- |
| C# und Visual Basic| Visual Studio 2017, Version 15.3 und höher |

### <a name="convert-to-interpolated-string"></a>Konvertieren in eine interpolierte Zeichenfolge

[Interpolierte Zeichenfolgen](/dotnet/csharp/language-reference/keywords/interpolated-strings) sind eine einfache Möglichkeit, Zeichenfolgen mit eingebetteten Variablen auszudrücken, ähnlich wie mit der **[String.Format](/dotnet/api/system.string.format#overloads)** -Methode.  Diese schnelle Aktion erkennt Fälle, in denen Zeichenfolgen verkettet sind oder **String.Format** verwenden, und ändert die Verwendung in eine interpolierte Zeichenfolge.

```csharp
// Before
int num = 3;
string s = string.Format("My string with {0} in the middle", num);

// Convert to interpolated string

// After
int num = 3;
string s = $"My string with {num} in the middle";
```

```vb
' Before
Dim num as Integer = 3
Dim s as String = String.Format("My string with {0} in the middle", num)

' Convert to interpolated string

' After
Dim num as Integer = 3
Dim s As String = $"My string with {num} in the middle"
```

| Anzuwendende Sprachen | Unterstützte Version |
| -------------------- | ---------------- |
| C# 6.0+ und Visual Basic 14+ | Visual Studio 2017 und höher |

### <a name="use-object-initializers"></a>Verwenden des Objektinitialisierers

Durch diese Schnellaktion können Sie den [Objektinitialisierer](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers) verwenden, anstatt den Konstruktor aufzurufen. Dadurch müssen Sie keine zusätzlichen Zeilen mit Zuweisungsanweisungen erstellen.

```csharp
// Before
var c = new Customer();
c.Age = 21;

// Object initialization can be simplified

// After
var c = new Customer() { Age = 21 };
```

```vb
' Before
Dim c = New Customer()
c.Age = 21

' Object initialization can be simplified

' After
Dim c = New Customer() With {.Age = 21}
```

| Diagnose-ID | Anzuwendende Sprachen | Unterstützte Version |
| ------- | -------------------- | ---------------- |
| IDE0017 | C# und Visual Basic | Visual Studio 2017 und höher |

### <a name="use-collection-initializers"></a>Verwenden des Auflistungsinitialisierers

Durch diese schnelle Aktion können Sie den [Auflistungsinitialisierer](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers) statt mehrerer Aufrufe der `Add`-Methode Ihrer Klasse verwenden.

```csharp
// Before
var list = new List<int>();
list.Add(1);
list.Add(2);
list.Add(3);

// Collection initialization can be simplified

// After
var list = new List<int> { 1, 2, 3 };
```

```vb
' Before
Dim list = New List(Of Integer)
list.Add(1)
list.Add(2)
list.Add(3)

' Collection initialization can be simplified

' After
Dim list = New List(Of Integer) From {1, 2, 3}
```

| Diagnose-ID | Anzuwendende Sprachen | Unterstützte Version |
| ------- | -------------------- | ---------------- |
| IDE0028 | C# und Visual Basic | Visual Studio 2017 und höher |

### <a name="convert-auto-property-to-full-property"></a>Konvertieren der Auto-Eigenschaft in eine vollständige Eigenschaft

Durch diese schnelle Aktion können Sie eine Auto-Eigenschaft in eine vollständige Eigenschaft (und umgekehrt) konvertieren.

```csharp
// Before
private int MyProperty { get; set; }

// Convert to full property

// After
private int MyProperty
{
    get { return _myProperty; }
    set { _myProperty = value; }
}
```

```vb
' Before
Public Property Name As String

' Convert to full property

' After
Private _Name As String

Public Property Name As String
    Get
        Return _Name
    End Get
    Set
        _Name = Value
    End Set
End Property
```

| Anzuwendende Sprachen | Unterstützte Version |
| -------------------- | ---------------- |
| C# und Visual Basic | Visual Studio 2017, Version 15.5 und höher |

### <a name="convert-block-body-to-expression-bodied-member"></a>Konvertieren des Blocktexts in Ausdruckskörpermembers

Durch diese schnelle Aktion können Sie Blocktexte in Ausdruckskörpermembers für Methoden, Konstruktoren, Operatoren, Eigenschaften, Indexer und Accessoren konvertieren.

```csharp
//Before
class MyClass4
{
    private int _myProperty;

    public int MyProperty
    {
        get { return _myProperty; }
        set
        {
            _myProperty = value;
        }
    }

    public MyClass4(int myProperty)
    {
        MyProperty = myProperty;
    }

    public void PrintProperty()
    {
        Console.WriteLine(MyProperty);
    }
}

// Use expression body for accessors/constructors/methods

// After
class MyClass4
{
    private int _myProperty;

    public int MyProperty
    {
        get => _myProperty;
        set => _myProperty = value;
    }

    public MyClass4(int myProperty) => MyProperty = myProperty;

    public void PrintProperty() => Console.WriteLine(MyProperty);
}
```

| Diagnose-ID | Anzuwendende Sprachen | Unterstützte Version |
| ------- | -------------------- | ---------------- |
| IDE0021-27 | C# 6.0 und höher | Visual Studio 2017 und höher |

### <a name="convert-anonymous-function-to-local-function"></a>Konvertieren von anonymen Funktionen in lokale Funktionen

Diese schnelle Aktion konvertiert anonyme Funktionen in lokale Funktionen.

```csharp
// Before
Func<int, int> fibonacci = null;
fibonacci = (int n) =>
{
    return n <= 1 ? 1 : fibonacci(n - 1) + fibonacci(n - 2);
};

// Use local function

// After
int fibonacci(int n)
{
    return n <= 1 ? 1 : fibonacci(n-1) + fibonacci(n-2);
}
```

### <a name="convert-referenceequals-to-is-null"></a>Konvertieren von „ReferenceEquals“ in „IS NULL“

| Diagnose-ID | Anzuwendende Sprachen | Unterstützte Version |
| ------- | -------------------- | ---------------- |
| IDE0041 | C# 7.0 und höher | Visual Studio 2017, Version 15.5 und höher |

Diese schnelle Aktion schlägt nach Möglichkeit die Verwendung des [Musterabgleichs](/dotnet/csharp/pattern-matching) statt dem ```ReferenceEquals```-Codierungsmuster vor.

```csharp
// Before
var value = "someString";
if (object.ReferenceEquals(value, null))
{
    return;
}

// Use 'is null' check

// After
var value = "someString";
if (value is null)
{
    return;
}
```

| Diagnose-ID | Anzuwendende Sprachen | Unterstützte Version |
| ------- | -------------------- | ---------------- |
| IDE0039 | C# 7.0 und höher | Visual Studio 2017, Version 15 und höher |

### <a name="introduce-pattern-matching"></a>Einführen des Musterabgleichs

Diese schnelle Aktion schlägt die Verwendung des [Musterabgleichs](/dotnet/csharp/pattern-matching) mit Umwandlungen und NULL-Überprüfungen in C# vor.

```csharp
// Before
if (o is int)
{
    var i = (int)o;
    ...
}

// Use pattern matching

// After
if (o is int i)
{
    ...
}
```

```csharp
// Before
var s = o as string;
if (s != null)
{
    ...
}

// Use pattern matching

// After
if (o is string s)
{
    ...
}
```

| Diagnose-ID | Anzuwendende Sprachen | Unterstützte Version |
| ------- | -------------------- | ---------------- |
| IDE0020 | C# 7.0 und höher | Visual Studio 2017 und höher |
| IDE0019 | C# 7.0 und höher | Visual Studio 2017 und höher |

### <a name="change-base-for-numeric-literals"></a>Ändern der Basis für numerische Literale

Mithilfe dieser schnellen Aktion können Sie ein numerisches Literal von einem numerischen Basissystem in ein anderes konvertieren. Beispielsweise können Sie eine Zahl in das hexadezimale oder binäre Format ändern.

```csharp
// Before
int countdown = 2097152;

// Convert to hex

// After
int countdown = 0x200000;
```

```vb
' Before
Dim countdown As Integer = 2097152

' Convert to hex

' After
Dim countdown As Integer = &H200000
```

| Anzuwendende Sprachen | Unterstützte Version |
| ------- | -------------------- | ---------------- |
| C# 7.0 und höher und Visual Basic 14 und höher | Visual Studio 2017, Version 15.3 und höher |

### <a name="insert-digit-separators-into-literals"></a>Einfügen von Zifferntrennzeichen in Literale

Mithilfe dieser schnellen Aktion können Sie Zifferntrennzeichen in Literale einfügen.

```csharp
// Before
int countdown = 1000000;

// Separate thousands

// After
int countdown = 1_000_000;
```

```vb
' Before
Dim countdown As Integer = 1000000

' Separate thousands

' After
Dim countdown As Integer = 1_000_000
```

| Anzuwendende Sprachen | Unterstützte Version |
| ------- | -------------------- | ---------------- |
| C# 7.0 und höher und Visual Basic 14 und höher | Visual Studio 2017, Version 15.3 und höher |

### <a name="use-explicit-tuple-names"></a>Verwenden expliziter Tupelnamen

Diese schnelle Aktion identifiziert Bereiche, in denen Tupelnamen statt Item1, Item2 usw. verwendet werden können.

```csharp
// Before
(string name, int age) customer = GetCustomer();
var name = customer.Item1;

// Use explicit tuple name

// After
(string name, int age) customer = GetCustomer();
var name = customer.name;
```

```vb
' Before
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.Item1

' Use explicit tuple name

' After
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.name
```

| Diagnose-ID | Anzuwendende Sprachen | Unterstützte Version |
| ------- | -------------------- | ---------------- |
| IDE0033 | C# 7.0 und höher und Visual Basic 15 und höher | Visual Studio 2017 und höher |

### <a name="use-inferred-names"></a>Verwenden von abgeleiteten Namen

Diese schnelle Aktion zeigt auf, wenn der Code vereinfacht werden kann, damit abgeleitete Membernamen in anonymen Typen oder abgeleitete Elementnamen in Tupeln verwendet werden.

```csharp
// Before
var anon = new { age = age, name = name };

// Use inferred member name

// After
var anon = new { age, name };
```

```csharp
// Before
var tuple = (age: age, name: name);

// Use inferred tuple element name

// After
var tuple = (age, name);
```

| Diagnose-ID | Anzuwendende Sprachen | Unterstützte Version |
| ------- | -------------------- | ---------------- |
| IDE0037 | C# | Visual Studio 2017, Version 15.5 und höher |
| IDE0037 | C# 7.1+ | Visual Studio 2017, Version 15.5 und höher |

### <a name="deconstruct-tuple-declaration"></a>Dekonstruieren der Tupeldeklaration

Durch diese schnelle Aktion können Sie Variablendeklarationen von Tupeln dekonstruieren.

```csharp
// Before
var person = GetPersonTuple();
Console.WriteLine($"{person.name} {person.age}");

(int x, int y) point = GetPointTuple();
Console.WriteLine($"{point.x} {point.y}");

//Deconstruct variable declaration

// After
var (name, age) = GetPersonTuple();
Console.WriteLine($"{name} {age}");

(int x, int y) = GetPointTuple();
Console.WriteLine($"{x} {y}");
```

| Diagnose-ID | Anzuwendende Sprachen | Unterstützte Version |
| ------- | -------------------- | ---------------- |
| IDE0042 | C# 7.0 und höher | Visual Studio 2017, Version 15.5 und höher |

### <a name="make-method-synchronous"></a>Methode als synchron deklarieren

Wenn Sie das Schlüsselwort `async` oder `Async` für eine Methode verwenden, wird erwartet, dass das Schlüsselwort `await` oder `Await` ebenfalls in der Methode verwendet wird. Sollte dies nicht der Fall sein, erscheint eine schnelle Aktion, die die Methode als synchron deklariert, indem das Schlüsselwort `async` oder `Async` entfernt und der Rückgabetyp geändert wird. Verwenden Sie die Option **Make Method Synchronous** (Methode als synchron deklarieren) aus dem Menü für schnelle Aktionen.

```csharp
// Before
async Task<int> MyAsyncMethod()
{
    return 3;
}

// Make method synchronous

// After
int MyAsyncMethod()
{
    return 3;
}
```

```vb
' Before
Async Function MyAsyncMethod() As Task(Of Integer)
    Return 3
End Function

' Make method synchronous

' After
Function MyAsyncMethod() As Integer
    Return 3
End Function
```

| Fehler-ID | Anzuwendende Sprachen |
| ------- | -------------------- |
| CS1998, BC42356 | C# und Visual Basic |

### <a name="make-method-asynchronous"></a>Methode als asynchron deklarieren

Wenn Sie das Schlüsselwort `await` oder `Await` innerhalb einer Methode verwenden, wird erwartet, dass die Methode mit dem Schlüsselwort `async` oder `Async` gekennzeichnet ist. Sollte dies allerdings nicht der Fall sein, wird eine Schnellaktion angezeigt, die die Methode als asynchron deklariert. Verwenden Sie die Option **Make method/Function asynchronous** (Methode/Funktion als asynchron deklarieren) aus dem Menü für schnelle Aktionen.

```csharp
// Before
int MyAsyncMethod()
{
    return await Task.Run(...);
}

// Make method asynchronous

// After
async Task<int> MyAsyncMethod()
{
    return await Task.Run(...);
}
```

```vb
' Before
Function MyAsyncMethod() as Integer
    Return  Await Task.Run(...)
End Function

' Make method asynchronous

' After
Async Function MyAsyncMethod() As Task(Of Integer)
    Return Await Task.Run(...)
End Function
```

| Fehler-ID | Anzuwendende Sprachen | Unterstützte Version |
| ------- | -------------------- | ---------------- |
| CS4032, BC37057 | C# und Visual Basic | Visual Studio 2017 und höher |

## <a name="see-also"></a>Weitere Informationen

- [Schnelle Aktionen](../ide/quick-actions.md)
