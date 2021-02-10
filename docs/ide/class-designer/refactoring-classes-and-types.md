---
title: Umbenennen und verschieben von Klassen und Typen im Klassen-Designer
description: Lernen Sie, Klassen und Typen mithilfe des Klassen-Designers und Klassendetailsfensters umzubenennen und zu verschieben.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.ClassDesigner.OverrideMembersDialog
helpviewer_keywords:
- members, overriding
- overriding members
- classes [Visual Studio], refactoring
- type members, overriding
- refactoring, types
- types [Visual Studio], refactoring
- Class Designer [Visual Studio], refactoring classes
- refactoring, classes
ms.assetid: dcf07bb4-fa3b-4224-9dec-566fd924a8ce
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2f7941b3a2c9c3fe71119e3a4413ad97f56b6290
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969853"
---
# <a name="refactor-classes-and-types-in-class-designer"></a>Umgestalten von Klassen und Typen im Klassen-Designer

Wenn Sie einen Code umgestalten, ist er leichter zu verstehen, zu verwalten und effizienter durch die Änderung seiner internen Struktur und die Art, wie seine Objekte entworfen werden, nicht aber sein externes Verhalten. Verwenden Sie den Klassen-Designer und im Klassendetailsfenster, um die durchzuführenden Aufgaben und die Wahrscheinlichkeit der Einführung von Fehlern beim Umgestalten von C#-, Visual Basic- oder C++-Code im Visual Studio-Projekt zu reduzieren.

> [!NOTE]
> Die Dateien eines Projekts sind möglicherweise schreibgeschützt, da das Projekt unter Quellcodeverwaltung steht und nicht ausgecheckt ist, auf das Projekt verwiesen wird oder die Dateien auf dem Datenträger als schreibgeschützt markiert sind. Bei der Arbeit an einem Projekt in einem dieser Zustände werden verschiedene Möglichkeiten zum Speichern Ihrer Arbeit je nach Zustand des Projekts angezeigt. Dies gilt für die Umgestaltung eines Codes und für einen Code, den Sie auf andere Weise ändern, z. B. indem Sie ihn direkt bearbeiten.

## <a name="common-tasks"></a>Allgemeine Aufgaben

|Aufgabe|Hilfreiche Themen|
|----------| - |
|**Umgestaltung von Klassen:** Sie können Umgestaltungsvorgänge zum Aufteilen eine Klasse in Teilklassen oder zur Implementierung einer abstrakten Klasse verwenden.|-   [Vorgehensweise: Aufteilen einer Klasse in partielle Klassen (Klassen-Designer)](how-to-split-a-class-into-partial-classes.md)|
|**Arbeiten mit Schnittstellen:** Im Klassen-Designer Sie können eine Schnittstelle im Klassendiagramm implementieren, indem Sie es an eine Klasse anhängen, die einen Code für die Schnittstellenmethoden vorsieht.|-   [How to: Implement an Interface (Class Designer) (Vorgehensweise: Implementieren einer Schnittstelle (Klassen-Designer))](how-to-implement-an-interface.md)|
|**Umgestaltung von Typen, Typmembern und Parametern:** Über den Klassen-Designer können Sie Typen umbenennen, Typmember überschreiben oder Typmember aus einem Typ in einen anderen verschieben. Außerdem können Sie Nullable-Typen erstellen.|-   [Umbenennen von Typen und Typmembern](#rename-types-and-type-members)<br />-   [Verschieben von Typmembern von einem Typ in einen anderen](#move-type-members-from-one-type-to-another)<br />-   [How to: Create a Nullable Type (Class Designer) (Vorgehensweise: Erstellen eines Nullable-Typs (Klassen-Designer))](how-to-create-a-nullable-type.md)|

## <a name="rename-types-and-type-members"></a>Umbenennen von Typen und Typmembern

Im Klassen-Designer können Sie einen Typ oder einen Member eines Typs im Klassendiagramm oder im Fenster **Eigenschaften** umbenennen. Im Fenster **Klassendetails** können Sie zwar den Namen eines Members, aber nicht den Typ ändern. Die Umbenennung eines Typs oder Typmember wird an alle Fenster und Codepositionen übergeben, in denen der alte Name auftrat.

### <a name="rename-in-the-class-designer"></a>Im Klassen-Designer umbenennen

1. Klicken Sie im Klassendiagramm auf den Typ oder Member und den Namen.

     Der Name des Members kann jetzt bearbeitet werden.

2. Geben Sie den neuen Namen für den Typ oder Typmember ein

### <a name="rename-in-the-class-details-window"></a>Im Fenster „Klassendetails“ umbenennen

1. Um das Fenster **Klassendetails** anzuzeigen, klicken Sie mit der rechten Maustaste erst auf den Typ oder den Typmember und dann mit der linken auf **Klassendetails**.

     Das Fenster **Klassendetails** wird angezeigt.

2. Ändern Sie in der Spalte **Name** den Namen des Typmembers.

3. Um den Fokus von der Zelle zu verschieben, drücken Sie die **EINGABETASTE**, oder klicken Sie außerhalb der Zelle.

    > [!NOTE]
    > Im Fenster **Klassendetails** können Sie zwar den Namen eines Members, aber nicht den Typ ändern.

### <a name="rename-in-the-properties-window"></a>Im Fenster „Eigenschaften“ umbenennen

1. Rechtsklicken Sie im Klassendiagramm oder im Fenster **Klassendetails** auf den Typ oder Member, und klicken Sie dann auf **Eigenschaften**.

     Das Fenster **Eigenschaften** wird angezeigt und zeigt die Eigenschaften für den Typ oder Typmember an.

2. In der Eigenschaft **Name** ändern Sie den Namen des Typs bzw. Typmembers.

     Der neue Name wird an alle Fenster und Codepositionen im aktuellen Projekt übertragen, in dem der alte Name auftrat.

## <a name="move-type-members-from-one-type-to-another"></a>Verschieben von Typmembern von einem Typ in einen anderen

Mit dem **Klassen-Designer** können Sie einen Typmember von einem Typ in einen anderen Typ verschieben. Dafür müssen beide Typen im aktuellen Klassendiagramm sichtbar sein.

1. Rechtsklicken Sie in einem Typ, der auf der Entwurfsoberfläche angezeigt wird, auf den Member, den Sie in einen anderen Typ verschieben möchten, und klicken Sie dann auf **Ausschneiden**.

2. Rechtsklicken Sie auf den Zieltyp, und klicken Sie dann auf **Einfügen**.

     Die Eigenschaft wird aus dem Quelltyp entfernt und im Zieltyp angezeigt wird.

## <a name="see-also"></a>Weitere Informationen

- [Entwerfen von Klassen und Typen](designing-and-viewing-classes-and-types.md)
