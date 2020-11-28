---
title: Hinzufügen des Attributs DebuggerDisplay
description: Lernen Sie, das DebuggerDisplay-Attribut hinzuzufügen, um zu steuern, wie im Debuggervariablenfenster ein Objekt, eine Eigenschaft oder ein Feld angezeigt wird.
ms.custom: SEO-VS-2020
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: fa6baa6e104fca2d3a3b45cac343fd1ceb086271
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871118"
---
# <a name="add-debuggerdisplay-attribute"></a>Hinzufügen des Attributs DebuggerDisplay

Diese Codegenerierung gilt für:

- C#

**Beschreibung:** Das [Attribut DebuggerDisplay](../../debugger/using-the-debuggerdisplay-attribute.md) steuert die Anzeige von Objekten, Eigenschaften oder Feldern in den Variablenfenstern des Debuggers.

**Hintergrund:** Sie möchten im Debugger [Eigenschaften programmgesteuert in Ihrem Code anheften](../../debugger/view-data-values-in-data-tips-in-the-code-editor.md#pin-properties-in-datatips).

**Vorteile**: Das Anheften von Eigenschaften ermöglicht Ihnen, Objekte schnell anhand ihrer Eigenschaften zu untersuchen, indem Sie diese Eigenschaft im Debugger an den Anfang der Eigenschaftsliste des Objekts setzen. 

## <a name="how-to"></a>Vorgehensweise

1. Positionieren Sie den Cursor entweder auf einem Typ, Delegaten, einer Eigenschaft oder einem Feld. 

2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen. Wählen Sie **Attribut DebuggerDisplay hinzufügen** aus.

    ![Vergleichsoperatoren generieren](media/add-debugger-display-attribute.png)

3. Das Attribut DebuggerDisplay wird zusammen mit einer Auto-Methode hinzugefügt, die standardmäßig ToString() zurückgibt. 

## <a name="see-also"></a>Siehe auch

- [Codegenerierung](../code-generation-in-visual-studio.md)
- [Vorschau der Änderungen](../../ide/preview-changes.md)