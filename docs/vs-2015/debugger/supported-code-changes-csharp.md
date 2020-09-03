---
title: Unterstützte Code Änderungen (c#) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], supported code changes
ms.assetid: c7a48ea9-5a7f-4328-a9d7-f0e76fac399d
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6fc02c11a4ebceea431fc06a1bd1cfdb1063097d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "67823535"
---
# <a name="supported-code-changes-c"></a>Unterstützte Codeänderungen (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Funktion "Bearbeiten und Fortfahren" behandelt die meisten Arten von Codeänderungen in Methodentexten. Die meisten Änderungen außerhalb von Methodentexten sowie einige Änderungen in Methodentexten können jedoch während des Debuggens nicht übernommen werden. Wenn Sie diese nicht unterstützten Änderungen übernehmen möchten, müssen Sie das Debuggen beenden und mit einer neuen Version des Codes erneut starten.  
  
 Folgende Änderungen am C#-Code können während einer Debugsitzung nicht übernommen werden:  
  
- Änderungen an der aktuellen Anweisung oder einer beliebigen anderen aktiven Anweisung.  
  
     Aktive Anweisungen umfassen alle Anweisungen in Funktionen der Aufrufliste, die aufgerufen wurden, um zur aktuellen Anweisung zu gelangen.  
  
     Die aktuelle Anweisung wird im Quellcodefenster durch einen gelben Hintergrund gekennzeichnet. Andere aktive Anweisungen werden durch einen schattierten Hintergrund gekennzeichnet und sind schreibgeschützt. Diese Standardfarben können im Dialogfeld **Optionen** geändert werden.  
  
- Ändern der Signatur eines Typs.  
  
- Hinzufügen einer anonymen Methode, die eine bisher noch nicht erfasste Variable erfasst.  
  
- Hinzufügen, Entfernen oder Ändern von Attributen.  
  
- Hinzufügen, Entfernen oder Ändern von `using`-Anweisungen.  
  
- Hinzufügen von `foreach`, `using` oder `lock` zu der aktiven Anweisung.  
  
## <a name="unsafe-code"></a>Unsicherer Code  
 Änderungen an unsicherem Code unterliegen denselben Einschränkungen wie Änderungen an sicherem Code, allerdings mit einer zusätzlichen Einschränkung: Die Funktion „Bearbeiten und Fortfahren“ unterstützt keine Änderungen an unsicherem Code, der sich innerhalb einer Methode mit dem `stackalloc`-Operator befindet.  
  
## <a name="exceptions"></a>Ausnahmen  
 „Bearbeiten und Fortfahren“ unterstützt Änderungen an `catch`- und `finally`-Blöcken, und zwar mit der Ausnahme, dass das Hinzufügen eines `catch`- oder `finally`-Blocks um die aktive Anweisung herum nicht zulässig ist.  
  
## <a name="unsupported-scenarios"></a>Nicht unterstützte Szenarien  
 Bearbeiten und Fortfahren steht in den folgenden Debugszenarios nicht zur Verfügung:  
  
- Debuggen von LINQ-Code unter bestimmten Umständen. Weitere Informationen finden Sie unter [Debuggen von LINQ](../debugger/debugging-linq.md).  
  
  - Erfassen einer zuvor noch nicht erfassten Variablen.  

  - Ändern des Typs des Abfrage Ausdrucks (z. b. Select a => Select New {a = a};)  

  - Entfernen einer `where`-Klausel, die eine aktive Anweisung enthält.  

  - Entfernen einer `let`-Klausel, die eine aktive Anweisung enthält.  

  - Entfernen einer `join`-Klausel, die eine aktive Anweisung enthält.  

  - Entfernen einer `orderby`-Klausel, die eine aktive Anweisung enthält.  
  
- Debuggen im gemischten Modus (systemeigen/verwaltet).  
  
- SQL-Debuggen.  
  
- Debuggen einer Dr. Watson-Sicherungskopie.  
  
- Bearbeiten von Code nach einer nicht behandelten Ausnahme, wenn die Option "**aufrufsstapel bei nicht behandelten Ausnahmen**entladen" nicht ausgewählt ist.  
  
- Debuggen einer eingebetteten Laufzeitanwendung.  
  
- Debuggen einer Anwendung, die an angefügt ist, anstatt die Anwendung durch Auswahl von starten im Menü **Debuggen** **zu** **starten** .  
  
- Debuggen von optimiertem Code.  
  
- Debuggen einer alten Version des Codes, wenn eine neue Version aufgrund von Buildfehlern nicht erstellt werden konnte.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bearbeiten und Fortfahren (Visual c#)](../debugger/edit-and-continue-visual-csharp.md)   
 [How to: Verwenden von „Bearbeiten und fortfahren“ (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)
