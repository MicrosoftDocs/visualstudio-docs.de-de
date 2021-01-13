---
title: Umschließen, Einziehen und Ausrichten von Refactorings
description: Erfahren Sie, wie Sie Ketten von Methodenaufrufen umschließen und ausrichten.
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: d8a98ebd1fa1e8a9ec937cf4e0965d804a8a9387
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/24/2020
ms.locfileid: "97761224"
---
# <a name="wrap-indent-and-align-refactorings"></a>Umschließen, Einziehen und Ausrichten von Refactorings

## <a name="wrap-and-align-call-chains"></a>Umschließen und Ausrichten von Aufrufketten

Dieses Refactoring gilt für:

- C#

- Visual Basic

**Beschreibung:** Ermöglicht das Umschließen und Ausrichten von Ketten von Methodenaufrufen.

**Hintergrund:** Sie verwenden eine lange Kette, die aus mehreren Methodenaufrufen in einer Anweisung besteht.

**Vorteile**: Eine lange Liste ist einfacher zu lesen, wenn sie den Benutzereinstellungen entsprechend umschlossen oder eingezogen ist.

### <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie den Cursor in einer beliebigen Aufrufkette.
2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.
3. Wählen Sie **Aufrufkette umbrechen** oder **Aufrufkette umbrechen und ausrichten** aus, um das Refactoring zu akzeptieren.

   ![Screeenshot: Menü „Schnellaktionen und Refactorings“ in Visual Studio mit Auswahl von „Aufrufkette umbrechen“ und C#-Codeänderungen](media/wrap-call-chain.png)

## <a name="wrap-indent-and-align-parameters-or-arguments"></a>Umschließen, Einziehen und Ausrichten von Parametern und Argumenten

Dieses Refactoring gilt für:

- C#

- Visual Basic

**Beschreibung:** Ermöglicht das Umschließen, Einziehen und Ausrichten von Parametern und Argumenten.

**Hintergrund:** Sie verfügen über eine Methodendeklaration oder einen Aufruf mit mehreren Parametern oder Argumenten.

**Vorteile**: Eine lange Liste mit Parametern oder Argumenten ist einfacher zu lesen, wenn sie den Benutzereinstellungen entsprechend umschlossen oder eingezogen sind.

### <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie Ihren Cursor auf einer Parameterliste.
2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.

   ![Umschließen, Einziehen und Ausrichten von Parametern](media/wrap-parameters.png)

3. Wählen Sie **Alle Parameter umschließen** aus, um das Refactoring zu akzeptieren.

## <a name="wrap-binary-expressions"></a>Zeilenumbruch bei binären Ausdrücken

Dieses Refactoring gilt für:

- C#

- Visual Basic

**Beschreibung:** Hiermit können Sie binäre Ausdrücke umschließen.

**Hintergrund:** Verwenden Sie dieses Refactoring, wenn Sie über einen binären Ausdruck verfügen.

**Vorteile**: Dies erleichtert das Lesen eines binären Ausdrucks, wenn dieser gemäß der Benutzereinstellungen umschlossen ist.

### <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie Ihren Cursor im binären Ausdruck.
2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.
3. Wählen Sie **Ausdruck umschließen** aus, um das Refactoring zu akzeptieren.

   ![Screeenshot: Menü „Schnellaktionen und Refactorings“ in Visual Studio mit Auswahl von „Ausdruck umschließen“ und C#-Codeänderungen](media/wrap-binary-expression.png)

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
