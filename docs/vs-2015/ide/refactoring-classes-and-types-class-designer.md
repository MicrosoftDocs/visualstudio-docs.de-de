---
title: Refactoring von Klassen und Typen (Klassen-Designer) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
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
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5803b720ae1271d8319310820d1f0dc159db8bf9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670272"
---
# <a name="refactoring-classes-and-types-class-designer"></a>Refactoring von Klassen und Typen (Klassen-Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie einen Code umgestalten, ist er leichter zu verstehen, zu verwalten und effizienter durch die Änderung seiner internen Struktur und die Art, wie seine Objekte entworfen werden, nicht aber sein externes Verhalten. Verwenden Sie den Klassen-Designer und im Klassendetail-Fenster, um die Arbeit, die Sie erledigen müssen, und die Wahrscheinlichkeit der Einführung von Fehlern beim Umgestalten von Visual C# .NET, Visual Basic .NET oder C++-Code im Visual Studio-Projekt  zu reduzieren.

> [!NOTE]
> Die Dateien eines Projekts sind möglicherweise schreibgeschützt, da das Projekt unter Quellcodeverwaltung steht und nicht ist ausgecheckt ist; auf das Projekt verwiesen wird oder die Dateien auf dem Datenträger als schreibgeschützt markiert sind. Bei der Arbeit an einem Projekt in einem dieser Zustände werden verschiedene Möglichkeiten zum Speichern Ihrer Arbeit je nach Zustand des Projekts angezeigt. Dies gilt für die Umgestaltung eines Codes und für einen Code, den Sie auf andere Weise ändern, z. B. indem Sie ihn direkt bearbeiten. Weitere Informationen finden Sie unter [Anzeige schreibgeschützter Informationen (Klassen-Designer)](https://msdn.microsoft.com/33e2d3a9-1668-4d10-ae56-fa09b3156e0a).

## <a name="common-tasks"></a>Allgemeine Aufgaben

|Aufgabe|Hilfreiche Themen|
|----------|------------------------|
|**Umgestaltung von Klassen:** Sie können Umgestaltungsvorgänge zum Aufteilen eine Klasse in Teilklassen oder zur Implementierung einer abstrakten Klasse verwenden.|-   [Gewusst wie: Aufteilen einer Klasse in partielle Klassen (Klassen-Designer)](../ide/how-to-split-a-class-into-partial-classes-class-designer.md)|
|**Arbeiten mit Schnittstellen:** Im Klassen-Designer Sie können eine Schnittstelle im Klassendiagramm implementieren, indem Sie es an eine Klasse anhängen, die einen Code für die Schnittstellenmethoden vorsieht.|-   [Vorgehensweise: Implementieren einer Schnittstelle (Klassen-Designer)](../ide/how-to-implement-an-interface-class-designer.md)|
|**Umgestaltung von Typen, Typmembern und Parametern:** Über den Klassen-Designer können Sie Typen umbenennen, Typmember überschreiben oder Typmember aus einem Typ in einen anderen verschieben. Außerdem können Sie Nullable-Typen erstellen.|-   [Umbenennen von Typen und Typmembern](../ide/refactoring-classes-and-types-class-designer.md#RenamingTypesAndMembers)<br />-   [Verschieben von Typmembern von einem Typ in einen anderen](../ide/refactoring-classes-and-types-class-designer.md#MovingTypeMembers)<br />-   [Vorgehensweise: Erstellen eines Typs, der NULL-Werte zulässt (Klassen-Designer)](../ide/how-to-create-a-nullable-type-class-designer.md)|

### <a name="renaming-types-and-type-members"></a><a name="RenamingTypesAndMembers"></a> Umbenennen von Typen und Typmembern
 Im Klassen-Designer können Sie einen Typ oder einen Member eines Typs im Klassendiagramm oder im Eigenschaftenfenster umbenennen. Im Fenster Klassendetails können Sie den Namen eines Members, aber keinen Typ ändern. Die Umbenennung eines Typs oder Typmember wird an alle Fenster und Codepositionen übergeben, in denen der alte Name auftrat.

##### <a name="to-rename-a-name-in-the-class-designer"></a>Um einen Namen im Klassen-Designer umzubenennen,

1. Wählen Sie im Klassendiagramm den Typ oder Member aus, und klicken Sie auf den Namen.

     Der Name des Members kann jetzt bearbeitet werden.

2. Geben Sie den neuen Namen für den Typ oder Typmember ein

##### <a name="to-rename-a-name-in-the-class-details-window"></a>Um einen Namen im Fenster Klassendetails umzubenennen,

1. Um das Fenster Klassendetails anzuzeigen, klicken Sie mit der rechten Maustaste auf den Typ oder den Typmember und dann auf **Klassendetails**.

     Das Fenster Klassendetails wird angezeigt.

2. Ändern Sie in der Spalte **Name** den Namen des Typmembers.

3. Drücken **Sie die Eingabe** Taste, oder klicken Sie auf die Zelle, um den Fokus von der Zelle zu entfernen.

    > [!NOTE]
    > Im Fenster Klassendetails können Sie den Namen eines Members, aber keinen Typ ändern.

##### <a name="to-rename-a-name-in-the-properties-window"></a>Um einen Namen im Eigenschaftenfenster zu ändern

1. Rechtsklicken Sie im Klassendiagramm oder im Fenster Klassendetails  auf Typ oder Member und klicken Sie dann auf **Eigenschaften**.

     Das Fenster Eigenschaften wird angezeigt und zeigt die Eigenschaften für den Typ oder Typmember an.

2. In der Eigenschaft **Name** ändern Sie den Namen des Typs bzw. Typmembers.

     Der neue Name wird an alle Fenster und Codepositionen im aktuellen Projekt übertragen, in dem der alte Name auftrat.

### <a name="moving-type-members-from-one-type-to-another"></a><a name="MovingTypeMembers"></a> Verschieben von Typmembern von einem Typ in einen anderen
 Mit dem **Klassen-Designer**können Sie einen Typmember von einem Typ in einen anderen Typ verschieben, wenn beide Typen im aktuellen Klassendiagramm sichtbar sind.

##### <a name="to-move-a-type-member-from-one-type-to-another"></a>Um einen Typmember von einem Typ in einen anderen zu verschieben.

1. Rechtsklicken Sie in einem Typ, der auf der Entwurfsoberfläche angezeigt wird, auf den Member, den Sie in einen anderen Typ verschieben möchten, und klicken Sie dann auf **Aussschneiden**.

2. Rechtsklicken Sie auf den Zieltyp und klicken Sie dann auf **Einfügen**.

     Die Eigenschaft wird aus dem Quelltyp entfernt und im Zieltyp angezeigt wird.

## <a name="related-topics"></a>Verwandte Themen

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[Anzeigen von Typen und Beziehungen (Klassen-Designer)](../ide/viewing-types-and-relationships-class-designer.md)||
|[Entwerfen von Klassen und Typen (Klassen-Designer)](../ide/designing-classes-and-types-class-designer.md)||
