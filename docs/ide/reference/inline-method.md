---
title: Inlinemethode
description: Erfahren Sie, wie Sie das Menü „Schnellaktionen und Refactorings“ in Visual Studio verwenden, um Inlinemethodendeklarationen umzugestalten und eine klarere Syntax bereitzustellen.
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 655c6dad03b05b257aec3d92199321a0e0e93d22
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/24/2020
ms.locfileid: "97761419"
---
# <a name="inline-method"></a>Inlinemethode

Dieses Refactoring gilt für:

- C#

- Visual Basic

**Beschreibung:** Hierbei handelt es sich um ein Refactoring von Inlinemethoden. 

**Hintergrund:** Sie möchten die Nutzungen einer statischen Methode, einer Instanzmethode und einer Erweiterungsmethode in einem einzelnen Anweisungstext durch eine Option zum Entfernen der ursprünglichen Methodendeklaration ersetzen.

**Vorteile**:  Dieses Refactoring sorgt für eine deutlichere Syntax.

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie Ihr Caretzeichen auf der Methodennutzung.

2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.

3. Wählen Sie eine der folgenden Optionen aus: 
    
   Klicken Sie auf **Inline `<QualifiedMethodName>`** , um die Inlinemethodendeklaration zu entfernen: 

    ![Screeenshot des Menüs „Schnellaktionen und Refactorings“ in Visual Studio mit ausgewähltem „Inline CreateWidget() konvertieren“ und angezeigten C#-Codeänderungen.](media/inline-method-remove-declaration.png)

   Klicken Sie auf **`<QualifiedMethodName>` inline einbinden und beibehalten**, um die ursprüngliche Methodendeklaration beizubehalten: 

    ![Screeenshot des Menüs „Schnellaktionen und Refactorings“ in Visual Studio mit ausgewähltem „Inline und behalten CreateWidget() konvertieren“ und angezeigten C#-Codeänderungen.](media/inline-method-preserve-declaration.png)

## <a name="see-also"></a>Weitere Informationen

- [Refactoring](../refactoring-in-visual-studio.md)
