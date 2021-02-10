---
title: Refactoringoptionen für statische lokale Funktionen
description: Hier erfahren Sie, wie Sie das Menü „Schnellaktionen und Refactorings…“ verwenden, um eine lokale Funktion in eine statische umzuwandeln und außerhalb der Funktion definierte Variablen an die Deklaration und die Aufrufe der Funktion zu übergeben.
ms.custom: SEO-VS-2020
ms.date: 02/10/2020
ms.topic: reference
author: governesss
ms.author: midumont
manager: jmartens
f1_keywords:
- vs.csharp.refactoring.make.local.function.static
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 050ce5e90d9141892ff65602ca560d0add83da5d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967188"
---
# <a name="static-local-function-refactorings-and-quick-actions"></a>Statische lokale Funktionen: Refactorings und schnelle Aktionen

In diesem Artikel werden zwei Produktivitätsfeatures in Zusammenhang mit statischen lokalen Funktionen vorgestellt. Ein Feature ist ein Refactoring, das eine lokale Funktion in eine statische Funktion konvertiert. Das andere ist eine schnelle Aktion, die Code generiert, um Variablen an eine statische lokale Funktion zu übergeben.

## <a name="make-local-function-static"></a>Lokale Funktion in statische Funktion konvertieren

Dieses Refactoring gilt für:

- C#

**Beschreibung:** Dieses Feature konvertiert eine lokale Funktion in eine statische Funktion und übergibt Variablen, die außerhalb der Funktion definiert wurden, an die Funktionsdeklaration und -aufrufe.

**Hintergrund:** Ihre lokale Funktion soll statisch sein, und alle Variablen sollen im Bereich der Funktion definiert sein.

**Vorteile**: Statische lokale Funktionen verbessern die Lesbarkeit: Wenn Sie wissen, dass bestimmter Code isoliert ist, lässt sich der Code einfacher lesen, verstehen und wiederverwenden. Statische lokale Funktionen bieten auch eine Bereichsauswahl, um zu verhindern, dass eine statische Funktion, die nur in einer einzigen Methode aufgerufen wird, in eine Klasse eingefügt wird.

### <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie die Einfügemarke auf dem Namen der lokalen Funktion.

2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.

   ![Lokale Funktion in statische Funktion konvertieren](media/make-local-function-static.png)

3. Wählen Sie **Lokale Funktion in statische Funktion konvertieren** aus.

## <a name="pass-variable-explicitly-in-a-static-local-function"></a>Variable explizit an statische lokale Funktion übergeben

Diese schnelle Aktion gilt für:

- C#

**Beschreibung:** Übergibt eine Variable explizit an eine statische lokale Funktion.

**Hintergrund:** Sie möchten eine lokale Funktion als statische Funktion einrichten, aber dennoch Variablen verwenden, die außerhalb der Funktion initialisiert werden.

**Vorteile**: Die Verwendung statischer lokaler Funktionen bietet Klarheit für Leser, weil diese wissen, dass eine solche Funktion nur in einem bestimmten Kontext des Programms deklariert und aufgerufen werden kann. Gleichzeitig bieten solche Funktionen die Flexibilität, Variablen außerhalb dieses Kontexts definieren und dennoch als Argumente an die statische lokale Funktion übergeben zu können.

### <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie die Einfügemarke auf die Variable an der Stelle, an der sie in der lokalen statischen Funktion verwendet wird.

2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.

   ![Variable explizit an statische lokale Funktion übergeben](media/pass-variable-explicitly-static-local-function.png)

3. Wählen Sie **Pass variable explicitly in local static function** (Variable explizit an lokale statische Funktion übergeben) aus.

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)