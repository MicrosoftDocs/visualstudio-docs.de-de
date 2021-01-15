---
title: Unterstützte Codeänderungen (C# und Visual Basic) | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, welche Codeänderungen unterstützt werden, wenn Sie das Feature „Bearbeiten und fortfahren“ beim Debuggen eines C#- oder Visual Basic-Projekts in Visual Studio verwenden.
ms.custom: SEO-VS-2020
ms.date: 10/11/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], supported code changes
- Edit and Continue [Visual Basic], supported code changes
ms.assetid: c7a48ea9-5a7f-4328-a9d7-f0e76fac399d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 267d9097ebe53b4074bed6c5caf4077006c946eb
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149208"
---
# <a name="supported-code-changes-c-and-visual-basic"></a>Unterstützte Codeänderungen (C# und Visual Basic)
Die Funktion "Bearbeiten und Fortfahren" behandelt die meisten Arten von Codeänderungen in Methodentexten. Die meisten Änderungen außerhalb von Methodentexten sowie einige Änderungen in Methodentexten können jedoch während des Debuggens nicht übernommen werden. Wenn Sie diese nicht unterstützten Änderungen übernehmen möchten, müssen Sie das Debuggen beenden und mit einer neuen Version des Codes erneut starten.

## <a name="supported-changes-to-code"></a>Unterstützte Änderungen an Code

In der folgenden Tabelle sind die Änderungen aufgeführt, die während einer Debugsitzung ohne Neustart der Sitzung an C#- und Visual Basic-Code vorgenommen werden können.

|Sprachelement/Feature|Unterstützter Bearbeitungsvorgang|Einschränkungen|
|-|-|-|
|Typen|Hinzufügen von Methoden, Feldern, Konstruktoren usw.|[Ja](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)|
|Iterators|Hinzufügen oder ändern|Nein|
|async-/await-Ausdrücke|Hinzufügen oder ändern|[Ja](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)|
|Dynamische Objekte|Hinzufügen oder ändern|Nein|
|Lambdaausdrücke|Hinzufügen oder ändern|[Ja](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)|
|LINQ-Ausdrücke|Hinzufügen oder ändern|[Wie bei Lambdaausdrücken](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)|

> [!NOTE]
> Neuere Sprachfeatures wie Zeichenfolgeninterpolation und NULL-bedingte Operatoren werden von „Bearbeiten und Fortfahren“ in der Regel unterstützt. Aktuelle Informationen finden Sie auf der Seite [Von „Bearbeiten und Fortfahren“ unterstützte Bearbeitungsvorgänge](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md).

## <a name="unsupported-changes-to-code"></a>Nicht unterstützte Änderungen an Code
 Folgende Änderungen am C#- und Visual Basic-Code können während einer Debugsitzung nicht übernommen werden:

- Änderungen an der aktuellen Anweisung oder einer beliebigen anderen aktiven Anweisung.

     Aktive Anweisungen umfassen alle Anweisungen in Funktionen der Aufrufliste, die aufgerufen wurden, um zur aktuellen Anweisung zu gelangen.

     Die aktuelle Anweisung wird im Quellcodefenster durch einen gelben Hintergrund gekennzeichnet. Andere aktive Anweisungen werden durch einen schattierten Hintergrund gekennzeichnet und sind schreibgeschützt. Diese Standardfarben können im Dialogfeld **Optionen** geändert werden.

- Die folgende Tabelle enthält nicht unterstützte Änderungen am Code nach Sprachelement.

|Sprachelement/Feature|Nicht unterstützter Bearbeitungsvorgang|
|-|-|
|Alle Codeelemente|Umbenennen|
|Namespaces|Hinzufügen|
|Namespaces, Typen, Member|Löschen|
|Generics|Hinzufügen oder ändern|
|Schnittstellen|Ändern|
|Typen|Hinzufügen abstrakter oder virtueller Member, Hinzufügen von Außerkraftsetzung (siehe [Details](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md))|
|Typen|Destruktor hinzufügen|
|Member|Ändern eines Members, der auf einen eingebetteten Interoptyp verweist|
|Member|Ändern eines statischen Members, nachdem darauf durch Ausführen von Code bereits zugegriffen wurde|
|Member (Visual Basic)|Ändern eines Members mit On Error- oder Resume-Anweisung|
|Member (Visual Basic)|Ändern eines Members, der eine LINQ-Abfrageklausel vom Typ „Aggregate“, „Group By“, „Simple Join“ oder „Group Join“ enthält|
|Methoden|Ändern von Signaturen|
|Methoden|Festlegen einer abstrakten Methode als nicht abstrakte Methode durch Hinzufügen eines Methodenkörpers|
|Methoden|Löschen eines Methodenkörpers|
|Attribute|Hinzufügen oder ändern|
|Ereignisse oder Eigenschaften|Ändern eines Typparameters, Basistyps, Delegattyps oder Rückgabetyps |
|Operatoren oder Indexer|Ändern eines Typparameters, Basistyps, Delegattyps oder Rückgabetyps |
|catch-Blöcke|Ändern, wenn eine aktive Anweisung enthalten ist|
|Blöcke vom Typ „try-catch-finally“|Ändern, wenn eine aktive Anweisung enthalten ist|
|Using-Anweisungen|Hinzufügen|
|Async-Methoden oder -Lambdaausdrücke|Ändern einer Async-Methode oder eines Async-Lambdaausdrucks in einem Projekt für .NET Framework 4 und niedrigere Versionen (siehe [Details](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md))|
|Iterators|Ändern eines Iterators in einem Projekt für .NET Framework 4 und niedrigere Versionen (siehe [Details](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md))|

## <a name="unsafe-code"></a>Unsicherer Code
 Änderungen an unsicherem Code unterliegen denselben Einschränkungen wie Änderungen an sicherem Code, allerdings mit einer zusätzlichen Einschränkung: Die Funktion „Bearbeiten und Fortfahren“ unterstützt keine Änderungen an unsicherem Code, der sich innerhalb einer Methode mit dem `stackalloc`-Operator befindet.

## <a name="unsupported-app-scenarios"></a>Nicht unterstützte App-Szenarien

Nicht unterstützte Apps und Plattformen sind u. a. ASP.NET 5, Silverlight 5 und Windows 8.1.

> [!NOTE]
> Zu den unterstützten Apps zählen UWP-Apps in Windows 10 sowie x86- und x64-Apps, die für die Desktopversion von .NET Framework 4.6 oder höhere Versionen vorgesehen sind. (.NET Framework ist nur als Desktopversion verfügbar.)

## <a name="unsupported-scenarios"></a>Nicht unterstützte Szenarien
 Bearbeiten und Fortfahren steht in den folgenden Debugszenarios nicht zur Verfügung:

- Debuggen im gemischten Modus (systemeigen/verwaltet).

- SQL-Debuggen.

- Debuggen einer Dr. Watson-Sicherungskopie.

- Debuggen einer eingebetteten Laufzeitanwendung.

- Debuggen einer Anwendung mit „An Prozess anhängen“ (**Debuggen > An Prozess anhängen**), anstatt die Anwendung durch Auswählen von **Start** im Menü **Debuggen** auszuführen

- Debuggen von optimiertem Code.

- Debuggen einer alten Version des Codes, wenn eine neue Version aufgrund von Buildfehlern nicht erstellt werden konnte.

## <a name="see-also"></a>Siehe auch
- [Bearbeiten und Fortfahren (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)
- [How to: Verwenden von „Bearbeiten und fortfahren“ (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)