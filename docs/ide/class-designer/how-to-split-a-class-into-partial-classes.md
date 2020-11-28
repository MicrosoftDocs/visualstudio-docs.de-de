---
title: 'Vorgehensweise: Aufteilen einer Klasse in partielle Klassen (Klassen-Designer)'
description: Lernen Sie, die Deklaration einer Klasse oder Struktur mit dem Schlüsselwort „partial“ auf mehrere Deklarationen aufzuteilen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Class Designer, partial classes
- partial classes, Class Designer
ms.assetid: 6f6b0b30-3996-4569-9200-20482b3adf90
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: ac0726851aec0d86223c2d95027b92137682c8a9
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94901348"
---
# <a name="how-to-split-a-class-into-partial-classes-in-class-designer"></a>Vorgehensweise: Aufteilen einer Klasse in partielle Klassen im Klassen-Designer

Sie können die Deklaration einer Klasse oder Struktur auf mehrere Deklarationen aufteilen, indem Sie das `partial`-Schlüsselwort (`Partial` in Visual Basic) verwenden. Sie können beliebig viele partielle Deklarationen verwenden.

Die Deklarationen können sich in einer oder in mehreren Quelldateien befinden. Alle Deklarationen müssen jedoch in derselben Assembly und im selben Namespace enthalten sein.

Partielle Klassen sind in vielen Situationen nützlich. Bei einem großen Projekt wird durch das Aufteilen einer Klasse in mehrere Dateien beispielsweise ermöglicht, dass mehr als ein Programmierer gleichzeitig am Projekt arbeiten kann. Wenn Sie mit Code arbeiten, der von Visual Studio erstellt wird, können Sie die Klasse ändern, ohne die Quelldatei erneut erstellen zu müssen. (Beispiele für Code, der von Visual Studio erstellt wird, sind u.A. Windows Forms-Code und Webdienst-Wrappercode.) Sie können deshalb Code erstellen, der diese automatisch generierte Klassen verwendet, ohne die von Visual Studio erstellte Datei ändern zu müssen.

Es gibt zwei Arten von partiellen Methoden. In C# werden Sie deklarierende und implementierende Methoden genannt. In Visual Basic heißen sie Deklaration und Implementierung.

Der **Klassen-Designer** unterstützt partielle Klassen und Methoden. Die Typform im Klassendiagramm bezieht sich auf einen einzelnen Deklarationsort für die partielle Klasse. Wenn die partielle Klasse in mehreren Dateien definiert ist, können Sie angeben, welchen Deklarationsort der **Klassen-Designer** verwenden wird, indem Sie die Eigenschaft **Speicherort** für neue Members im Fenster **Eigenschaften** festlegen. Wenn Sie doppelt auf eine Klassenform klicken, wechselt der **Klassen-Designer** also zur Quelldatei, die die Klassendeklaration enthält, die von der Eigenschaft **Speicherort für neue Members** identifiziert wird. Wenn Sie doppelt auf eine partielle Methode in einer Klassenform klicken, wechselt der **Klassen-Designer** zur Deklaration der partiellen Methode. Im Fenster **Eigenschaften** bezieht sich die Eigenschaft **Dateiname** ebenso auf den Speicherort der Deklaration. Für partielle Klassen führt der **Dateiname** alle Dateien auf, die Deklarations- und Implementierungscode für diese Klasse enthalten. Für partielle Methoden listet der **Dateiname** jedoch nur die Datei auf, die die Deklaration der partiellen Methode enthält.

In den folgenden Beispielen wird die Definition der `Employee`-Klasse auf zwei Deklarationen aufgeteilt, die jeweils eine andere Prozedur definieren. Die beiden partiellen Definitionen aus dem Beispiel können in einer Quelldatei oder in zwei unterschiedlichen Quelldateien enthalten sein.

> [!NOTE]
> Visual Basic verwendet partielle Klassendefinitionen, um generierten Code von Visual Studio von Code zu trennen, der vom Benutzer erstellt wurde. Der Code wird in diskrete Quelldateien aufgeteilt. Zum Beispiel definiert der **Windows Form-Designer** partielle Klassen für Steuerelemente, z.B. `Form`. Sie sollten den generierten Code in diesen Steuerelementen nicht ändern.

Weitere Informationen über partielle Typen in Visual Basic finden Sie unter [Partial (Partiell)](/dotnet/visual-basic/language-reference/modifiers/partial).

## <a name="example"></a>Beispiel

Verwenden Sie zum Aufteilen einer Klassendefinition wie in folgendem Beispiel dargestellt das Schlüsselwort `partial` (`Partial` in Visual Basic):

```csharp
// First part of class definition.
public partial class Employee
{
    public void CalculateWorkHours()
    {
    }
}

// Second part of class definition.
public partial class Employee
{
    public void CalculateTaxes()
    {
    }
}
```

```vb
' First part of class definition.
Partial Public Class Employee
    Public Sub CalculateWorkHours()
    End Sub
End Class

' Second part of class definition.
Partial Public Class Employee
    Public Sub CalculateTaxes()
    End Sub
End Class
```

## <a name="see-also"></a>Weitere Informationen

- [Partielle Klassen und Methoden](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)
- [partial (Typ) (C#-Referenz)](/dotnet/csharp/language-reference/keywords/partial-type)
- [partial (Methode) (C#-Referenz)](/dotnet/csharp/language-reference/keywords/partial-method)
- [Partial (Visual Basic)](/dotnet/visual-basic/language-reference/modifiers/partial)
