---
title: Verschieben eines Typs in ein entsprechendes Dateirefactoring
description: Verschieben Sie einen Typ in eine separate Datei mit demselben Namen. Klicken Sie mit der rechten Maustaste auf den Typ, wählen Sie Schnellaktionen und Refactorings aus, und klicken Sie auf „Typ in <TypeName>.cs verschieben“.
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
ms.openlocfilehash: 728b9e176a40d2bfd7ae36a329409cb27f80fc86
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927955"
---
# <a name="move-a-type-to-a-matching-file-refactoring"></a>Verschieben eines Typs in ein entsprechendes Dateirefactoring

Dieses Refactoring gilt für:

- C#

- Visual Basic

**Beschreibung**: Hiermit können Sie den ausgewählten Typ in eine separate Datei mit demselben Namen verschieben.

**Hintergrund**: Es sind mehrere Klassen, Strukturen, Schnittstellen usw. in der gleichen Datei vorhanden, die Sie trennen möchten.

**Vorteile**: Das Platzieren mehrerer Typen in die gleiche Datei kann die Suche nach diesen Typen erschweren. Durch das Verschieben von Typen in Dateien mit demselben Namen wird der Code besser lesbar und ist einfacher zu navigieren.

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie den Cursor innerhalb des Namens des Typs, wo dieser definiert wird. Beispiel:

   ```csharp
   class Person
   ```

   ```vb
   Class Person
   ```

2. Führen Sie dann eine der folgenden Aktionen aus:

   - Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** ,
   - Klicken Sie mit der rechten Maustaste auf den Typnamen, und wählen Sie **Schnellaktionen und Refactorings** aus.

1. Wählen Sie **Typ verschieben in *TypeName* cs** aus dem Menü aus. Dabei ist *TypeName* der Name des Typs, den Sie ausgewählt haben.

   Der Typ wird in eine neue Datei im Projekt verschoben, die den gleichen Namen wie der Typ aufweist.

   - C#:

      ![Ergebnis des Inlinevorgangs in C#](media/movetype-result-cs.png)

   - Visual Basic:

      ![Ergebnis des Inlinevorgangs in Visual Basic](media/movetype-result-vb.png)

## <a name="see-also"></a>Weitere Informationen

- [Refactoring](../refactoring-in-visual-studio.md)
