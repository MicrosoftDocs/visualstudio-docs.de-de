---
title: Refactoring des Extrahierens einer Schnittstelle
description: Hier erfahren Sie, wie Sie über das Menü „Schnellaktionen und Refactorings...“ mit vorhandenen Membern einer Klasse, Struktur oder Schnittstelle eine Schnittstelle erstellen.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 13e9b684c81abf491b5836c96190c6a89bdc0643
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617395"
---
# <a name="extract-an-interface-refactoring"></a>Refactoring des Extrahierens einer Schnittstelle

Dieses Refactoring gilt für:

- C#

- Visual Basic

**Beschreibung:** Hiermit können Sie eine Schnittstelle mit vorhandenen Membern einer Klasse, Struktur oder Schnittstelle erstellen.

**Hintergrund:** Eine Klasse, Struktur oder Schnittstelle enthält Member, die von anderen Klassen, Strukturen oder Schnittstellen geerbt werden können.

**Vorteile**: Schnittstellen stellen hervorragende Konstrukte für objektorientierte Entwürfe dar. Stellen Sie sich vor, es gäbe Klassen für verschiedene Tiere (Hunde, Katzen, Vögel) mit häufig verwendeten Methoden wie Fressen, Trinken und Schlafen. Mit einer Schnittstelle wie IAnimal würden Hunden, Katzen und Vögeln eine gemeinsame „Signatur“ für diese Methoden zugewiesen werden.

## <a name="extract-an-interface-refactoring"></a>Refactoring des Extrahierens einer Schnittstelle

1. Platzieren Sie Ihren Cursor auf dem Klassenname.

   - C#:

       ![Hervorgehobener Code – C#](media/extractinterface-highlight-cs.png)

   - Visual Basic:

       ![Hervorgehobener Code – Visual Basic](media/extractinterface-highlight-vb.png)

2. Führen Sie anschließend eine der folgenden Aktionen aus:

   - **Tastatur**
      - Drücken Sie **STRG+R** und dann **STRG+I**. (Ihre Tastenkombination weicht je nach dem gewählten Profil möglicherweise ab.)
      - Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen, und wählen Sie im Popupvorschaufenster **Schnittstelle extrahieren** aus.
   - **Maus**
      - Wählen Sie **Bearbeiten > Umgestalten > Schnittstelle extrahieren** aus.
      - Klicken Sie mit der rechten Maustaste auf den Namen der Klasse, und wählen Sie das Menü **Schnellaktionen und Refactorings** sowie im Popupvorschaufenster **Schnittstelle extrahieren** aus.

3. Geben Sie im angezeigten Dialogfeld **Schnittstelle extrahieren** die erforderlichen Informationen ein:

   ![Schnittstelle extrahieren](media/extractinterface-dialog-same-file.png)

   | Feld | Beschreibung |
   | - | - |
   | **Name der neuen Schnittstelle** | Der Name der zu erstellenden Schnittstelle. Dieser Name ist standardmäßig I *ClassName*, wobei *ClassName* der Name der von Ihnen oben ausgewählten Klasse ist. |
   | **Neuer Dateiname** | Der Name der generierten Datei, die die Schnittstelle enthalten wird. Wie beim Namen der Schnittstelle ist dies standardmäßig I *ClassName*, wobei *ClassName* der Name der von Ihnen oben ausgewählten Klasse ist. Sie können für die Option auch **Add to current file** (Aktueller Datei hinzufügen) auswählen. |
   | **Öffentliche Member zum Bilden einer Schnittstelle auswählen** | Die in der Schnittstelle zu extrahierenden Elemente. Sie können beliebig viele Elemente auswählen. |

4. Klicken Sie auf **OK**.

   Die Schnittstelle wird in der Datei mit dem angegebenen Namen erstellt. Darüber hinaus implementiert die ausgewählte Klasse diese Schnittstelle.

   - C#:

      ![Resultierende Klasse: C#](media/extractinterface-class-cs.png)

      ![Resultierende Schnittstelle: C#](media/extractinterface-interface-cs.png)

   - Visual Basic:

      ![Resultierende Klasse: Visual Basic](media/extractinterface-class-vb.png)

      ![Resultierende Schnittstelle: Visual Basic](media/extractinterface-interface-vb.png)

## <a name="see-also"></a>Weitere Informationen

- [Refactoring](../refactoring-in-visual-studio.md)
- [Tipps für .NET-Entwickler](../csharp-developer-productivity.md)
