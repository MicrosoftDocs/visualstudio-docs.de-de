---
title: Kontextoperator im Debugger ( C++ ) | Microsoft-Dokumentation
description: Möglicherweise müssen Sie einen Kontext für einen C++-Namen angeben, der sich außerhalb des Gültigkeitsbereichs befindet und durch einen lokalen Namen verborgen wird. Hier erfahren Sie, wie Sie hierfür den Kontextoperator verwenden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.operators
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- expressions [C++], native debugger
- evaluation
- format specifiers, expressions
- context operator, in expressions
- debugging [C++], expressions
- native expression evaluator
ms.assetid: 73cc9afe-f4a4-474e-bb89-5a33fb5e570c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 619162bc4237c71c44f960f7ca1e4337a54f3dd5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857713"
---
# <a name="context-operator-in-the-visual-studio-debugger-c"></a>Kontextoperator im Visual Studio-Debugger (C++)
Sie können den Kontextoperator in C++ zur Kennzeichnung von Haltepunktpositionen, Variablennamen oder Ausdrücken verwenden. Der Kontextoperator eignet sich für die Angabe eines Namens außerhalb des Gültigkeitsbereichs, der andernfalls durch einen lokalen Namen verborgen würde.

## <a name="syntax"></a><a name="BKMK_Using_context_operators_to_specify_a_symbol"></a> Syntax
 Es gibt zwei Methoden zum Angeben von Kontext:

1. {,,[*module*] } *expression*

     Die Klammern müssen zwei Kommas und den Modulnamen (ausführbare Datei oder DLL) oder den vollständigen Pfad enthalten.

     Um z. B. in der `SomeFunction` -Funktion von EXAMPLE.dll einen Haltepunkt festlegen, gehen Sie wie folgt vor:

    ```C++
    {,,EXAMPLE.dll}SomeFunction
    ```

2. *module*!*expression*

    ```C++
    EXAMPLE.dll!SomeFunction
    ```

- *module* ist der Name eines Moduls. Sie können einen vollständigen Pfad verwenden, um zwischen Modulen mit demselben Namen zu unterscheiden.

   Wenn der *module* -Pfad ein Komma, ein eingebettetes Leerzeichen oder eine geschweifte Klammer enthält, müssen Sie den Pfad in doppelte Anführungszeichen einschließen, damit die Zeichenfolge vom Kontextparser richtig erkannt wird. Einfache Anführungszeichen werden als Teil eines Windows-Dateinamens betrachtet. Daher sollten stets doppelte Anführungszeichen verwendet werden. Ein auf ein Objekt angewendeter

  ```C++
  {,,"a long, long, library name.dll"} g_Var
  ```

- *expression* ist ein beliebiger gültiger C++-Ausdruck, der zu einem gültigen Ziel, z. B. einem Funktionsnamen, einem Variablennamen oder einer Zeigeradresse in *module* aufgelöst wird.

  Wenn die Ausdrucksauswertung in einem Ausdruck auf ein Symbol trifft, wird in der folgenden Reihenfolge danach gesucht:

1. Beginnend mit dem aktuellen Block (in geschweifte Klammern eingeschlossene Anweisungsreihe) vom lexikalischen Gültigkeitsbereich nach außen und weiter zum äußeren, umschließenden Block. Der aktuelle Block entspricht dem Code mit der aktuellen Position (der Adresse des Anweisungszeigers).

2. Gültigkeitsbereich der Funktion. Die aktuelle Funktion.

3. Gültigkeitsbereich der Klasse, sofern sich die aktuelle Position innerhalb einer C++-Memberfunktion befindet. Der Klassengültigkeitsbereich umfasst alle Basisklassen. Von der Ausdrucksauswertung werden die normalen Dominanzregeln verwendet.

4. Globale Symbole im aktuellen Modul.

5. Öffentliche Symbole im aktuellen Programm.