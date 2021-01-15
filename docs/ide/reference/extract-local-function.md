---
title: Extrahieren einer lokalen Funktion
description: In diesem Artikel erfahren Sie, wie Sie ein Codefragment in eine eigenständige Funktion umwandeln, indem Sie den Code auswählen und dann STRG+R und STRG+M drücken.
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e007246b85671a0f4606bbdb3d1e9c4e0dc83541
ms.sourcegitcommit: cd7f122c6850cf442a4ca42d51d05c7a8fe9038d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/12/2021
ms.locfileid: "98129457"
---
# <a name="extract-local-function-refactoring"></a>Refactoring des Extrahierens einer lokalen Funktion

Dieses Refactoring gilt für:

- C#

**Beschreibung:** Hiermit können Sie ein Codefragment aus einer vorhandenen Methode in eine lokale Funktion konvertieren.

**Hintergrund:** Wenn Sie über ein vorhandenes Codefragment in einer Methode verfügen, die von einer lokalen Funktion aufgerufen werden muss.

**Vorteile**: Sie könnten diesen Code kopieren und einfügen, dies würde jedoch zu einer Duplizierung führen. Eine bessere Lösung besteht darin, dieses Fragment in eine eigene lokale Funktion umzugestalten.

## <a name="how-to"></a>Vorgehensweise

1. Markieren Sie den zu extrahierenden Code.

2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen. 

3. Klicken Sie auf **Lokale Funktion extrahieren**.

    ![Screenshot: Visual Studio Code-Fenster mit einer hervorgehobenen Zeile, dem Menü „Schnellaktionen und Refactorings“ geöffnet und der Option „Lokale Funktion extrahieren“ ausgewählt](media/extract-local-function.png)

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
- [Vorschau der Änderungen](../../ide/preview-changes.md)
