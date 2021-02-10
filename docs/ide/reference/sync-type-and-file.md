---
title: Umbenennen eines Dateinamens entsprechend eines Typs
description: Hier erfahren Sie, wie Sie das Menü „Schnellaktionen und Refactorings…“ verwenden, um einen Typ so umzubenennen, dass er mit dem Dateinamen übereinstimmt, oder einen Dateinamen so umzubenennen, dass er dem Typ entspricht, der darin enthalten ist.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: c02135074ee4a4907bb9c4ee235655fc3908a64c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838595"
---
# <a name="sync-a-type-to-a-filename-or-a-filename-to-a-type-refactoring"></a>Refactoring des Synchronisierens eines Typs mit einem Dateinamen oder eines Dateinamens mit einem Typ

Dieses Refactoring gilt für:

- C#

- Visual Basic

**Beschreibung**: Hiermit können Sie einen Typ entsprechend des Dateinamens umbenennen oder einen Dateinamen entsprechend des darin enthaltenen Typs umbenennen.

**Hintergrund**: Sie haben eine Datei oder einen Typ umbenannt und noch nicht die entsprechende Datei oder den entsprechenden Typ aktualisiert.

**Vorteile**: Das Platzieren eines Typs in eine Datei mit einem anderen Namen oder umgekehrt erschwert die Suche nach den gewünschten Elementen. Durch das Umbenennen des Typs oder des Dateinamens wird der Code besser lesbar und einfacher zu navigieren.

> [!NOTE]
> Dieses Refactoring ist für Projekte in .NET Standard und .NET Core noch nicht verfügbar.

## <a name="how-to"></a>Vorgehensweise

1. Markieren Sie den Namen des zu synchronisierenden Typs, oder platzieren Sie den Textcursor in den Namen:

   - C#:

       ![Hervorgehobener Code – C#](media/synctype-highlight-cs.png)

   - Visual Basic:

       ![Hervorgehobener Code – Visual Basic](media/synctype-highlight-vb.png)

2. Führen Sie dann eine der folgenden Aktionen aus:

   - **Tastatur**
      - Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen. Wählen Sie dann im Popupvorschaufenster die Option **Datei in *TypeName*.cs umbenennen** aus, wobei *TypeName* für den Namen des ausgewählten Typs steht.
      - Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen. Wählen Sie dann im Popupvorschaufenster die Option **Typ in _Filename_ umbenennen** aus, wobei *Filename* für den Namen der aktuellen Datei steht.
   - **Maus**
      - Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie das Menü **Schnellaktionen und Refactorings** aus. Wählen Sie dann im Popupvorschaufenster die Option **Datei in *TypeName*.cs umbenennen** aus, wobei *TypeName* für den Namen des ausgewählten Typs steht.
      - Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie das Menü **Schnellaktionen und Refactorings** aus. Wählen Sie dann im Popupvorschaufenster die Option **Typ in _Filename_ umbenennen** aus, wobei *Filename* für den Namen der aktuellen Datei steht.

   Der Typ oder die Datei wird umbenannt.

   - C#: Im nachfolgenden Beispiel wurde die Datei **MyClass.cs** entsprechend des Typnamens in **MyNewClass.cs** umbenannt.

       ![Ergebnis des Inlinevorgangs in C#](media/synctype-result-cs.png)

   - Visual Basic: Im nachfolgenden Beispiel wurde die Datei **Employee.vb** entsprechend des Typnamens in **Person.vb** umbenannt.

       ![Ergebnis des Inlinevorgangs in Visual Basic](media/synctype-result-vb.png)

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
