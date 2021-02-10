---
title: 'Vorgehensweise: Erstellen eines Typs, der NULL-Werte zulässt (Klassen-Designer)'
description: Lernen Sie, einen Typ im Klassen-Designer zu erstellen, der NULL-Werte zulässt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- nullable types, Class Designer
- Class Designer [Visual Studio], nullable types
ms.assetid: 84673a89-3f6d-4668-919e-1c0f56182fe5
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: de87e78b6f7ea14643df1070faf731e92d7a5767
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99850216"
---
# <a name="how-to-create-a-nullable-type-in-class-designer"></a>Vorgehensweise: Erstellen eines Typs im Klassen-Designer, der NULL-Werte zulässt

Bestimmte Werttypen verfügen nicht immer über einen definierten Wert oder benötigen keinen. Dies ist in Datenbanken üblich, in denen möglicherweise einigen Feldern kein Wert zugewiesen wird. Sie können z.B. einem Datenbankfeld einen NULL-Wert zuweisen, um zu zeigen, dass noch kein Wert zugewiesen wurde.

Ein *Nullable-Typ* ist ein Werttyp, den Sie erweitern, sodass der normale Wertebereich für diesen Typ als auch ein NULL-Wert benötigt werden. Ein Nullable von `Int32`, auch bezeichnet als Nullable\<Int32>, kann beispielsweise einem Wert im Bereich von –2147483648 bis 2147483647 oder einem NULL-Wert zugewiesen werden. Einem Nullable\<bool> können die Werte `True`, `False`, oder NULL (überhaupt kein Wert) zugewiesen werden.

Auf NULL festlegbare Typen sind Instanzen der <xref:System.Nullable%601>-Struktur. Jede Instanz eines Nullable-Typs hat zwei öffentliche schreibgeschützte Eigenschaften `HasValue` und `Value`:

- `HasValue` ist vom Typ `bool` und gibt an, ob die Variable einen definierten Wert enthält. `True` bedeutet, dass die Variable einen nicht-NULL-Wert enthält. Sie können mithilfe einer Anweisung wie `if (x.HasValue)` oder `if (y != null)` auf einen definierten Wert testen.

- `Value` hat denselben Typ wie der zugrunde liegende Typ. Wenn `HasValue``True` ist, enthält `Value` einen sinnvollen Wert. Wenn `HasValue``False` ist, wird der Zugriff auf `Value` eine ungültige Operationsausnahme auslösen.

Beim Deklarieren einer Variablen als Nullable-Typ verfügt sie standardmäßig über keinen definierten Wert (`HasValue` ist `False`) als der Standardwert des ihr zugrunde liegenden Werttyps.

Der Klassen-Designer zeigt einen Nullable-Typ so an wie den zugrunde liegenden Typ.

Weitere Informationen zu Typen in C#, die NULL-Werte zulassen, finden Sie unter [Nullable-Typen (C#-Programmierhandbuch)](/dotnet/csharp/programming-guide/nullable-types/index). Weitere Informationen zu Nullable-Typen in Visual Basic finden Sie unter [Auf NULL festlegbare Werttypen](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types).

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="to-add-a-nullable-type-by-using-the-class-designer"></a>Hinzufügen eines Nullable-Typs mithilfe des Klassen-Designers

1. Erweitern Sie im Klassendiagramm eine vorhandene Klasse, oder erstellen Sie eine neue Klasse.

2. Klicken Sie im Menü **Klassendiagramm** auf **Hinzufügen** > **Klasse hinzufügen**, um dem Projekt eine Klasse hinzuzufügen.

3. Klicken Sie im Menü **Klassendiagramm** auf **Erweitern**, um die Klassenform zu erweitern.

4. Wählen Sie die Klassenform aus. Klicken Sie im Menü **Klassendiagramm** auf **Hinzufügen** > **Feld**. Ein neues Feld mit den Standardnamen **Feld** wird in der Klassenform und auch im Fenster **Klassendetails** angezeigt.

5. Ändern Sie in der Spalte **Name** im Fenster **Klassendetails** (oder in der Klassenform selbst) den Namen des neuen Felds in einen gültigen und aussagekräftigen Namen.

6. Deklarieren Sie den Typ in der Spalte **Typ** im Fenster **Klassendetails** wie im Folgenden dargestellt als Nullable-Typ:

    - `int?` (Visual C#)
    - `Nullable(Of Integer)` (Visual Basic)

## <a name="to-add-a-nullable-type-by-using-the-code-editor"></a>Hinzufügen eines Nullable-Typs mithilfe des Code-Editors

1. Fügen Sie dem Projekt eine Klasse hinzu. Wählen Sie im **Projektmappen-Explorer** einen Projektknoten aus und klicken Sie dann im Menü **Projekt** auf **Klasse hinzufügen**.

2. Fügen Sie in der CS- oder VB-Datei für die neue Klasse eine oder mehrere Nullable-Typen in der Klassendeklaration hinzu.

    ```csharp
    // Declare a nullable type in Visual C#:
    class Test
    {
       int? building_number = 5;
    }
    ```

    ```vb
    ' Declare a nullable type in Visual Basic:
    Class Test
       Dim buildingNumber As Nullable(Of Integer) = 5
    End Class
    ```

3. Ziehen Sie das Klassensymbol in der Klassenansicht zur Entwurfsoberfläche des Klassen-Designers. Eine Klassenform wird im Klassendiagramm angezeigt.

4. Erweitern Sie die Details für die Klassenform, und bewegen Sie den Mauszeiger über die Klassenmember. Die QuickInfo zeigt die Deklaration der einzelnen Member.

5. Klicken Sie mit der rechten Maustaste auf Klassenform und auf **Klassendetails**. Sie können die Eigenschaften des neuen Typs im Fenster **Klassendetails** anzeigen oder ändern.

## <a name="see-also"></a>Siehe auch

- <xref:System.Nullable%601>
- [Typen mit Nullwert](/dotnet/csharp/programming-guide/nullable-types/index)
- [Verwenden von Typen mit Nullwert](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types)
- [How to: Identifizieren eines Typs, der NULL-Werte zulässt](/dotnet/csharp/programming-guide/nullable-types/how-to-identify-a-nullable-type)
- [Auf NULL festlegbare Werttypen](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)
