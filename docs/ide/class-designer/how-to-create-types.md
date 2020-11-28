---
title: 'Gewusst wie: Erstellen von Typen mit dem Klassen-Designer'
description: Lernen Sie, neue Typen für Projekte in C# und Visual Basic zu entwerfen, indem Sie sie in einem Klassendiagramm erstellen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- VS.Clr.ClrAttributesDialog
helpviewer_keywords:
- custom attributes, applying
- class diagrams, creating types
- classes [Visual Studio], creating with Class Designer
- Class Designer [Visual Studio], creating classes
- types [Visual Studio], class diagrams
- attributes [Visual Studio], applying custom
ms.assetid: 94458c31-28bc-40e2-9737-85868788a0e5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac6e59f4dc6fa68962ac061132e3fab90ec8e955
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94901439"
---
# <a name="how-to-create-types-by-using-class-designer"></a>Vorgehensweise: Erstellen von Typen mit dem Klassen-Designer

Um neue Typen für Projekte in C# und Visual Basic zu entwerfen, erstellen Sie sie in einem Klassendiagramm. Vorhandene Typen finden Sie unter [How to: View Existing Types (Class Designer) (Vorgehensweise: Anzeigen von vorhandenen Typen (Klassen-Designer))](how-to-view-existing-types.md).

## <a name="create-a-new-type"></a><a name="CreateType"></a> Erstellen eines neuen Typs

1. Ziehen Sie in der **Toolbox** unter **Klassen-Designer** eines der folgenden Elemente in ein Klassendiagramm:

    - **Klasse** oder **Abstrakte Klasse**

    - **Enum**

    - **Interface**

    - **Struktur** (VB) oder **Struct** (C#)

    - **Delegat**

    - **Modul** (nur VB)

2. Benennen Sie den Typ. Wählen Sie dann seine Zugriffsebene aus.

3. Wählen Sie die Datei aus, in der Sie den anfänglichen Code für den Typ hinzufügen möchten:

    - Wählen Sie **Neue Datei erstellen aus**, um eine neue Klassendatei zu erstellen und dem aktuellen Projekt hinzuzufügen, und benennen Sie die Datei.

    - Um Code für eine vorhandene Datei hinzuzufügen, wählen Sie **Zu vorhandener Datei hinzufügen** aus.

         Wenn Ihre Projektmappe ein Projekt enthält, das Code über mehrere App hinweg freigibt, können Sie einem Klassendiagramm in dem App-Projekt einen neuen Typ hinzufügen, jedoch nur, wenn die entsprechende Klassendatei im gleichen App-Projekt ist oder im freigegebenen Projekt enthalten ist.

4. Fügen Sie jetzt andere Elemente hinzu, um den Typ zu definieren:

    |**For**|**Add**|
    |-|-|
    |Klassen, abstrakte Klassen, Strukturen oder Structs|Methoden, Eigenschaften, Felder, Ereignisse, Konstruktoren (Methode), Destruktoren (Methode) und Konstanten, die den Typ definieren|
    |Enumerationen|Feldwerte, die die Enumeration bilden|
    |Schnittstellen|Methoden, Eigenschaften und Ereignisse, die die Schnittstelle bilden|
    |Delegat|Parameter, die den Delegaten definieren|
    |Modul|Methoden, Eigenschaften, Felder, Ereignisse, Konstruktoren (Methode) und Konstanten, die das Modul definieren|

     Weitere Informationen finden Sie unter [Erstellen von Membern](creating-and-configuring-type-members.md#create-members).

## <a name="apply-a-custom-attribute-to-a-type"></a><a name="CustAttributeType"></a> Anwenden eines benutzerdefinierten Attributs auf einen Typ

1. Klicken Sie in einem Klassendiagramm auf die Form des Typs.

2. Klicken Sie unter **Eigenschaften** neben der Eigenschaft **Benutzerdefinierte Attribute** für den Typ auf die Schaltfläche mit dem Auslassungszeichen (…).

3. Fügen Sie ein oder mehrere benutzerdefinierte Attribute hinzu (eines pro Zeile). Schließen Sie sie nicht in Klammern ein.

   Die benutzerdefinierten Attribute werden auf den Typ angewendet.

## <a name="apply-a-custom-attribute-to-a-type-member"></a><a name="CustAttributeMember"></a> Anwenden eines benutzerdefinierten Attributs auf einen Typmember

1. Klicken Sie in einem Klassendiagramm in der Form des entsprechenden Typs auf den Namen des Members oder im Klassendetailsfenster auf die entsprechende Zeile.

2. Suchen Sie unter **Eigenschaften** die Eigenschaft **Benutzerdefinierte Attribute** für den Member.

3. Fügen Sie ein oder mehrere benutzerdefinierte Attribute hinzu (eines pro Zeile). Schließen Sie sie nicht in Klammern ein.

   Die benutzerdefinierten Attribute werden auf den Typ angewendet.

## <a name="see-also"></a>Weitere Informationen

- [Vorgehensweise: Erstellen einer Vererbungsbeziehung zwischen Typen](how-to-create-inheritance-between-types.md)
- [Vorgehensweise: Erstellen von Zuordnungen zwischen Typen](how-to-create-associations-between-types.md)
- [Erstellen und Konfigurieren von Typmembern](creating-and-configuring-type-members.md)
- [Entwerfen von Klassen und Typen](designing-and-viewing-classes-and-types.md)
